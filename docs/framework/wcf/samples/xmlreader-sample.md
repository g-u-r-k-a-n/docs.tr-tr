---
title: XmlReader Örneği
ms.date: 03/30/2017
helpviewer_keywords:
- XML Reader
ms.assetid: 60e5848d-7d9c-4ea5-bed9-22758c9ac16c
ms.openlocfilehash: bb1cd02a60ec0ba62e1d0d9aa3560bbba0aaf668
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714535"
---
# <a name="xmlreader-sample"></a><span data-ttu-id="a82d4-102">XmlReader Örneği</span><span class="sxs-lookup"><span data-stu-id="a82d4-102">XmlReader Sample</span></span>

<span data-ttu-id="a82d4-103">XmlReader örneği bir <xref:System.Xml.XmlReader>kullanarak bir ileti gövdesinin işlenmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a82d4-103">The XmlReader sample demonstrates the processing of a message body using an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="a82d4-104">Örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md)Başlarken ' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="a82d4-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="a82d4-105">Birlikte eklenecek bir değer dizisini içeren bir iletiyi kabul eden `Sum`ek bir hizmet işlemi eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="a82d4-105">An additional service operation, `Sum`, has been added that accepts a message that contains an array of values to add together.</span></span> <span data-ttu-id="a82d4-106">Hizmet, <xref:System.Xml.XmlReader>kullanarak iletiyi okur.</span><span class="sxs-lookup"><span data-stu-id="a82d4-106">The service reads the message using an <xref:System.Xml.XmlReader>.</span></span>

> [!NOTE]
> <span data-ttu-id="a82d4-107">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="a82d4-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="a82d4-108">Hesaplayıcı arabirimi, aşağıdaki örnek kodda gösterildiği gibi <xref:System.ServiceModel.Channels.Message> parametresini kabul eden `Sum` adlı bir hizmet işlemi içerir.</span><span class="sxs-lookup"><span data-stu-id="a82d4-108">The calculator interface includes a service operation named `Sum` that accepts a <xref:System.ServiceModel.Channels.Message> parameter, as shown in the following sample code.</span></span>

```csharp
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
    [OperationContract]
    Message Sum(Message message);
}
```

<span data-ttu-id="a82d4-109">İstemci, önce bir tamsayı değerleri dizisi oluşturup sonra diziden bir ileti oluşturup sonra oluşturulan iletiyi kullanarak aşağıdaki örnek kodda gösterildiği gibi `Sum` yöntemini çağırarak `Sum` erişir.</span><span class="sxs-lookup"><span data-stu-id="a82d4-109">The client accesses `Sum` by first creating an array of integer values, then creating a message from the array, and then calling the `Sum` method using the created message, as shown in the following sample code.</span></span>

```csharp
CalculatorClient client = new CalculatorClient();
//...

// Call the Sum service operation.
int[] values = { 1, 2, 3, 4, 5 };
using (new OperationContextScope(client.InnerChannel))
{
    Message request = Message.CreateMessage(OperationContext.Current.OutgoingMessageHeaders.MessageVersion, "http://Microsoft.ServiceModel.Samples/ICalculator/Sum", values);
    Message reply = client.Sum(request);
    int sum = reply.GetBody<int>();

    Console.WriteLine("Sum(1,2,3,4,5) = {0}", sum);
}
```

<span data-ttu-id="a82d4-110">Hizmette, hizmet işleminin uygulanması `Sum` Sum değerleri arasında ilerlemek için bir <xref:System.Xml.XmlReader> nesnesi kullanarak ileti gövdesine erişir.</span><span class="sxs-lookup"><span data-stu-id="a82d4-110">In the service, the implementation of the service operation `Sum` accesses the message body using an <xref:System.Xml.XmlReader> object to iterate through the values to sum.</span></span> <span data-ttu-id="a82d4-111"><xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> yöntemi, aşağıdaki örnek kodda gösterildiği gibi ileti gövdesine erişmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a82d4-111">The <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> method is called to access the message body, as shown in the following sample code.</span></span>

```csharp
public int Sum(Message message)
{
    int sum = 0;
    string text = "";

    //The body of the message contains a list of numbers that are read
    //directly using an XmlReader.
    XmlReader body = message.GetReaderAtBodyContents ();
    while (body.Read())
    {
        text = body.ReadString().Trim();
        if (text.Length>0)
        {
            sum += Convert.ToInt32(text);
        }
    }
    body.Close();
    Message response = Message.CreateMessage(
       "http://Microsoft.ServiceModel.Samples/ICalculator/SumResponse",
       sum);
    return response;
}
```

<span data-ttu-id="a82d4-112">Örneği çalıştırdığınızda, işlemin istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a82d4-112">When you run the sample, the requests and responses of the operation are displayed in the client console window.</span></span> <span data-ttu-id="a82d4-113">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a82d4-113">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Sum(1,2,3,4,5) = 15

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a82d4-114">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a82d4-114">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="a82d4-115">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a82d4-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="a82d4-116">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a82d4-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="a82d4-117">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a82d4-117">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a82d4-118">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="a82d4-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a82d4-119">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a82d4-119">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="a82d4-120">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="a82d4-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a82d4-121">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a82d4-121">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\XmlReader`
