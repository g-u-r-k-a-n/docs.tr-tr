---
title: UriTemplate Örneği
ms.date: 03/30/2017
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
ms.openlocfilehash: 55999167d99069a4b207f4deda42f48bf02e1bdd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294969"
---
# <a name="uritemplate-sample"></a><span data-ttu-id="af01f-102">UriTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="af01f-102">UriTemplate Sample</span></span>

<span data-ttu-id="af01f-103"><xref:System.UriTemplate>Sınıfı, ortak bir yapıyı paylaşan URI kümeleriyle çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="af01f-103">The <xref:System.UriTemplate> class provides methods for working with sets of URIs that share a common structure.</span></span> <span data-ttu-id="af01f-104">Bu örnek, ile ilgili aşağıdaki temel kavramları göstermektedir `UriTemplate` :</span><span class="sxs-lookup"><span data-stu-id="af01f-104">This sample demonstrates the following key concepts relating to `UriTemplate`:</span></span>  
  
- <span data-ttu-id="af01f-105">Şablon oluşturma sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="af01f-105">Syntax for creating templates.</span></span>  
  
- <span data-ttu-id="af01f-106">Bir `UriTemplate` using ve kullanarak URI 'leri örnekleme <xref:System.UriTemplate.BindByName%2A> <xref:System.UriTemplate.BindByPosition%2A> .</span><span class="sxs-lookup"><span data-stu-id="af01f-106">Instantiating URIs from a `UriTemplate` using <xref:System.UriTemplate.BindByName%2A> and <xref:System.UriTemplate.BindByPosition%2A>.</span></span>  
  
- <span data-ttu-id="af01f-107"><xref:System.UriTemplateTable.Match%2A>, ve ' nin ters işlemidir `BindByName` `BindByPosition` .</span><span class="sxs-lookup"><span data-stu-id="af01f-107"><xref:System.UriTemplateTable.Match%2A>, which is the inverse operation of `BindByName` and `BindByPosition`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="af01f-108">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="af01f-108">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="af01f-109">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="af01f-109">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="af01f-110">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="af01f-110">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="af01f-111">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="af01f-111">The samples may already be installed on your computer.</span></span> <span data-ttu-id="af01f-112">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="af01f-112">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="af01f-113">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="af01f-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="af01f-114">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="af01f-114">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a><span data-ttu-id="af01f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af01f-115">See also</span></span>

- [<span data-ttu-id="af01f-116">UriTemplate Tablosu</span><span class="sxs-lookup"><span data-stu-id="af01f-116">UriTemplate Table</span></span>](uritemplate-table-sample.md)
- [<span data-ttu-id="af01f-117">UriTemplate Tablosu Dağıtıcısı</span><span class="sxs-lookup"><span data-stu-id="af01f-117">UriTemplate Table Dispatcher</span></span>](uritemplate-table-dispatcher-sample.md)
