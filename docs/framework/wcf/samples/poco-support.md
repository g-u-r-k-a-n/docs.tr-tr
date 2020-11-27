---
title: POCO Desteği
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: d416f37e0add99fbe3d60982fd2298748ff78556
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96259973"
---
# <a name="poco-support"></a><span data-ttu-id="fc6b8-102">POCO Desteği</span><span class="sxs-lookup"><span data-stu-id="fc6b8-102">POCO Support</span></span>

<span data-ttu-id="fc6b8-103">Bu örnek, işaretsiz türler için serileştirme desteğini gösterir; diğer bir deyişle, bazı durumlarda düz eski CLR nesne (POCO) türleri olarak da adlandırılan serileştirme özniteliklerinin uygulanmadığı türler.</span><span class="sxs-lookup"><span data-stu-id="fc6b8-103">This sample demonstrates the serialization support for unmarked types; that is, types to which serialization attributes have not been applied, sometimes referred to as Plain Old CLR Object (POCO) types.</span></span> <span data-ttu-id="fc6b8-104">, <xref:System.Runtime.Serialization.DataContractSerializer> Parametresiz oluşturucusu olan tüm genel işaretsiz türler için bir veri sözleşmesi olduğunu anlar.</span><span class="sxs-lookup"><span data-stu-id="fc6b8-104">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract for all public unmarked types that have a parameterless constructor.</span></span> <span data-ttu-id="fc6b8-105">Veri sözleşmeleri, yapılandırılmış verileri hizmetlere ve hizmetlerden geçirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc6b8-105">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="fc6b8-106">İşaretsiz türler hakkında daha fazla bilgi için bkz. [serileştirilebilir türler](../feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="fc6b8-106">For more information about unmarked types, see [Serializable Types](../feature-details/serializable-types.md).</span></span>  
  
 <span data-ttu-id="fc6b8-107">Bu örnek [Başlarken](getting-started-sample.md)' i temel alır, ancak basit sayısal türler yerine karmaşık sayılar kullanır.</span><span class="sxs-lookup"><span data-stu-id="fc6b8-107">This sample is based on the [Getting Started](getting-started-sample.md), but uses complex numbers instead of primitive numeric types.</span></span> <span data-ttu-id="fc6b8-108">Ayrıca, ve özniteliklerinin kullanılmadığı durumlar dışında [temel veri sözleşmesi](basic-data-contract.md) örneğine de benzer <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> .</span><span class="sxs-lookup"><span data-stu-id="fc6b8-108">It is also similar to the [Basic Data Contract](basic-data-contract.md) sample, except that the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes are not used.</span></span>  
  
 <span data-ttu-id="fc6b8-109">Hizmet Internet Information Services (IIS) tarafından barındırılır ve istemci bir konsol uygulaması (. exe).</span><span class="sxs-lookup"><span data-stu-id="fc6b8-109">The service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc6b8-110">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="fc6b8-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="fc6b8-111">`ComplexNumber`Sınıfı ' de kullanılır `ServiceContract` .</span><span class="sxs-lookup"><span data-stu-id="fc6b8-111">The `ComplexNumber` class is used in the `ServiceContract`.</span></span> <span data-ttu-id="fc6b8-112">`ComplexNumber`Türü, <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> Aşağıdaki örnek kodda gösterildiği gibi, ve özniteliklerine sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="fc6b8-112">The `ComplexNumber` type does not have the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes, as shown in the following sample code.</span></span> <span data-ttu-id="fc6b8-113">Varsayılan olarak, tüm ortak özellikler ve alanlar serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="fc6b8-113">By default, all public properties and fields are serialized.</span></span>  
  
```csharp
public class ComplexNumber  
{  
    public double Real;  
    public double Imaginary;  
    public ComplexNumber()  
    {  
        Real = double.MinValue;  
        Imaginary = double.MinValue;  
    }  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fc6b8-114">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="fc6b8-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="fc6b8-115">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="fc6b8-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="fc6b8-116">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="fc6b8-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="fc6b8-117">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="fc6b8-117">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fc6b8-118">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="fc6b8-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fc6b8-119">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="fc6b8-119">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="fc6b8-120">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="fc6b8-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fc6b8-121">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="fc6b8-121">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a><span data-ttu-id="fc6b8-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc6b8-122">See also</span></span>

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [<span data-ttu-id="fc6b8-123">Seri Hale Getirilebilir Türler</span><span class="sxs-lookup"><span data-stu-id="fc6b8-123">Serializable Types</span></span>](../feature-details/serializable-types.md)
