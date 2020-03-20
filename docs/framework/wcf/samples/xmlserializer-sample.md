---
title: XMLSerializer Örneği
ms.date: 03/30/2017
ms.assetid: 7d134453-9a35-4202-ba77-9ca3a65babc3
ms.openlocfilehash: c6d10a74a00bf534000f79457f2c80b0a9361230
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143349"
---
# <a name="xmlserializer-sample"></a><span data-ttu-id="b63d1-102">XMLSerializer Örneği</span><span class="sxs-lookup"><span data-stu-id="b63d1-102">XMLSerializer Sample</span></span>
<span data-ttu-id="b63d1-103">Bu örnek, <xref:System.Xml.Serialization.XmlSerializer>'ile uyumlu türleri serihale ve deserialize nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="b63d1-103">This sample demonstrates how to serialize and deserialize types that are compatible with the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="b63d1-104">Varsayılan Windows Communication Foundation (WCF) <xref:System.Runtime.Serialization.DataContractSerializer> madde sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="b63d1-104">The default Windows Communication Foundation (WCF) formatter is the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span> <span data-ttu-id="b63d1-105">Sınıf <xref:System.Xml.Serialization.XmlSerializer> kullanılamadığında <xref:System.Runtime.Serialization.DataContractSerializer> sınıf türleri serihale getirmek ve deserialize etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b63d1-105">The <xref:System.Xml.Serialization.XmlSerializer> class can be used to serialize and deserialize types when the <xref:System.Runtime.Serialization.DataContractSerializer> class cannot be used.</span></span> <span data-ttu-id="b63d1-106">XML üzerinde hassas denetim gerektiğinde bu genellikle durumdur - örneğin, bir veri parçası xml özniteliği değil, Bir XML özniteliği olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b63d1-106">This is often the case when precise control over the XML is required - for example, if a piece of data must be an XML attribute and not an XML element.</span></span> <span data-ttu-id="b63d1-107">Ayrıca, <xref:System.Xml.Serialization.XmlSerializer> WCF olmayan hizmetler için istemci oluştururken genellikle otomatik olarak seçilir.</span><span class="sxs-lookup"><span data-stu-id="b63d1-107">Also, the <xref:System.Xml.Serialization.XmlSerializer> often gets automatically selected when creating clients for non-WCF services.</span></span>  
  
 <span data-ttu-id="b63d1-108">Bu örnekte, istemci bir konsol uygulamasıdır (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="b63d1-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b63d1-109">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="b63d1-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b63d1-110">Ve <xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.XmlSerializerFormatAttribute> aşağıdaki örnek kodda gösterildiği gibi arabirime uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b63d1-110">The <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.XmlSerializerFormatAttribute> must be applied to the interface as shown in the following sample code.</span></span>  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"), XmlSerializerFormat]  
public interface IXmlSerializerCalculator  
{  
    [OperationContract]  
    ComplexNumber Add(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2);  
}  
```  
  
 <span data-ttu-id="b63d1-111">`ComplexNumber` Sınıfın ortak üyeleri XML <xref:System.Xml.Serialization.XmlSerializer> öznitelikleri olarak serihale edilir.</span><span class="sxs-lookup"><span data-stu-id="b63d1-111">The public members of `ComplexNumber` class are serialized by <xref:System.Xml.Serialization.XmlSerializer> as XML attributes.</span></span> <span data-ttu-id="b63d1-112">Bu <xref:System.Runtime.Serialization.DataContractSerializer> tür Bir XML örneği oluşturmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b63d1-112">The <xref:System.Runtime.Serialization.DataContractSerializer> cannot be used to create this kind of XML instance.</span></span>  
  
```csharp  
public class ComplexNumber  
{  
    private double real;  
    private double imaginary;  
  
    [XmlAttribute]  
    public double Real  
    {  
        get { return real; }  
        set { real = value; }  
    }  
  
    [XmlAttribute]  
    public double Imaginary  
    {  
        get { return imaginary; }  
        set { imaginary = value; }  
    }  
  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
    public ComplexNumber()  
    {  
        this.Real = 0;  
        this.Imaginary = 0;  
    }  
  
}  
```  
  
 <span data-ttu-id="b63d1-113">Hizmet uygulaması, `ComplexNumber` türün kabul ve iade değerlerini uygun sonucu hesaplar ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="b63d1-113">The service implementation calculates and returns the appropriate result—accepting and returning values of the `ComplexNumber` type.</span></span>  
  
```csharp  
public class XmlSerializerCalculatorService : IXmlSerializerCalculator  
{  
    public ComplexNumber Add(ComplexNumber n1, ComplexNumber n2)  
    {  
        return new ComplexNumber(n1.Real + n2.Real, n1.Imaginary +  
                                                      n2.Imaginary);  
    }  
    …  
}  
```  
  
 <span data-ttu-id="b63d1-114">İstemci uygulaması karmaşık sayılar da kullanır.</span><span class="sxs-lookup"><span data-stu-id="b63d1-114">The client implementation also uses complex numbers.</span></span> <span data-ttu-id="b63d1-115">Hizmet meta verilerinden [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından oluşturulan generatedClient.cs kaynak dosyasında hem hizmet sözleşmesi hem de veri türleri tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="b63d1-115">Both the service contract and the data types are defined in the generatedClient.cs source file, which was generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from service metadata.</span></span> <span data-ttu-id="b63d1-116">Svcutil.exe, bir sözleşmenin <xref:System.Runtime.Serialization.DataContractSerializer> seri olarak ne zaman seri hale edilemediğini algılayabilir ve bu durumda yayan `XmlSerializable` türlere geri döner.</span><span class="sxs-lookup"><span data-stu-id="b63d1-116">Svcutil.exe can detect when a contract is not serializable by the <xref:System.Runtime.Serialization.DataContractSerializer> and reverts to emitting `XmlSerializable` types in this case.</span></span> <span data-ttu-id="b63d1-117">Eğer kullanmak zorlamak istiyorsanız <xref:System.Xml.Serialization.XmlSerializer>, Svcutil.exe aracına /serializer:XmlSerializer (XmlSerializer kullanın) komut seçeneğini geçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b63d1-117">If you want to force the use of the <xref:System.Xml.Serialization.XmlSerializer>, you can pass the /serializer:XmlSerializer (use XmlSerializer) command option to the Svcutil.exe tool.</span></span>  
  
```csharp  
// Create a client.  
XmlSerializerCalculatorClient client = new  
                         XmlSerializerCalculatorClient();  
  
// Call the Add service operation.  
ComplexNumber value1 = new ComplexNumber();  
value1.Real = 1;  
value1.Imaginary = 2;  
ComplexNumber value2 = new ComplexNumber();  
value2.Real = 3;  
value2.Imaginary = 4;  
ComplexNumber result = client.Add(value1, value2);  
Console.WriteLine("Add({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
    value1.Real, value1.Imaginary, value2.Real, value2.Imaginary,
    result.Real, result.Imaginary);  
    …  
}  
```  
  
 <span data-ttu-id="b63d1-118">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b63d1-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="b63d1-119">İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b63d1-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(1 + 2i, 3 + 4i) = 4 + 6i  
Subtract(1 + 2i, 3 + 4i) = -2 + -2i  
Multiply(2 + 3i, 4 + 7i) = -13 + 26i  
Divide(3 + 7i, 5 + -2i) = 0.0344827586206897 + 1.41379310344828i  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b63d1-120">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="b63d1-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b63d1-121">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="b63d1-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b63d1-122">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="b63d1-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b63d1-123">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="b63d1-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b63d1-124">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="b63d1-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b63d1-125">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b63d1-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b63d1-126">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="b63d1-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b63d1-127">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="b63d1-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\Interop\XmlSerializer`  
