---
title: UriTemplate Örneği
ms.date: 03/30/2017
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
ms.openlocfilehash: e08333235b22e3c24fc6f4855fec43ef8b95fa5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183278"
---
# <a name="uritemplate-sample"></a><span data-ttu-id="7633c-102">UriTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="7633c-102">UriTemplate Sample</span></span>
<span data-ttu-id="7633c-103">Sınıf, <xref:System.UriTemplate> ortak bir yapıyı paylaşan URI kümeleriyle çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7633c-103">The <xref:System.UriTemplate> class provides methods for working with sets of URIs that share a common structure.</span></span> <span data-ttu-id="7633c-104">Bu örnek, aşağıdaki temel kavramları `UriTemplate`göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="7633c-104">This sample demonstrates the following key concepts relating to `UriTemplate`:</span></span>  
  
- <span data-ttu-id="7633c-105">Şablon oluşturmak için sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="7633c-105">Syntax for creating templates.</span></span>  
  
- <span data-ttu-id="7633c-106">ÜrI'leri `UriTemplate` kullanarak <xref:System.UriTemplate.BindByName%2A> anlık ve <xref:System.UriTemplate.BindByPosition%2A>.</span><span class="sxs-lookup"><span data-stu-id="7633c-106">Instantiating URIs from a `UriTemplate` using <xref:System.UriTemplate.BindByName%2A> and <xref:System.UriTemplate.BindByPosition%2A>.</span></span>  
  
- <span data-ttu-id="7633c-107"><xref:System.UriTemplateTable.Match%2A>, ters çalışma `BindByName` ve `BindByPosition`.</span><span class="sxs-lookup"><span data-stu-id="7633c-107"><xref:System.UriTemplateTable.Match%2A>, which is the inverse operation of `BindByName` and `BindByPosition`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7633c-108">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="7633c-108">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7633c-109">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="7633c-109">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="7633c-110">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="7633c-110">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7633c-111">Örnekler bilgisayarınıza zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="7633c-111">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7633c-112">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7633c-112">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="7633c-113">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="7633c-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7633c-114">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="7633c-114">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a><span data-ttu-id="7633c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7633c-115">See also</span></span>

- [<span data-ttu-id="7633c-116">UriTemplate Tablosu</span><span class="sxs-lookup"><span data-stu-id="7633c-116">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="7633c-117">UriTemplate Tablosu Dağıtıcısı</span><span class="sxs-lookup"><span data-stu-id="7633c-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
