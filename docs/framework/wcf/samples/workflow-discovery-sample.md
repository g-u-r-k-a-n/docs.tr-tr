---
title: İş Akışı Keşif Örneği
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: 44d1fed74782051a926ced95c49f3e3cb14f2b9e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263808"
---
# <a name="workflow-discovery-sample"></a><span data-ttu-id="c7200-102">İş Akışı Keşif Örneği</span><span class="sxs-lookup"><span data-stu-id="c7200-102">Workflow Discovery Sample</span></span>

<span data-ttu-id="c7200-103">Bu örnek, bir iş akışı hizmetinin nasıl keşfedilebilir olduğunu ve belirli bir hizmeti arayan özel kod etkinliğinin nasıl yazıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7200-103">This sample demonstrates how to make a workflow service discoverable and how to author a custom code activity that searches for a particular service.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="c7200-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="c7200-104">Demonstrates</span></span>  

 <span data-ttu-id="c7200-105">Keşif bul etkinliği ve Iş akışı kullanımı</span><span class="sxs-lookup"><span data-stu-id="c7200-105">Discovery Find Activity and Workflow Usage</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="c7200-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="c7200-106">Discussion</span></span>  

 <span data-ttu-id="c7200-107">Örneğin ilk bölümünde, yapılandırma kullanılarak bir iş akışı hizmeti bulunabilir hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="c7200-107">In the first part of the sample, a workflow service is made discoverable using configuration.</span></span> <span data-ttu-id="c7200-108">Yapılandırma ayrıca, hizmeti özel meta veriler (kapsamlar gibi) ile uygun şekilde uygulamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c7200-108">Configuration can also be used to apply the service appropriately with custom metadata (such as scopes).</span></span> <span data-ttu-id="c7200-109">İstemcide, örnek, belirli bir sözleşmeyle eşleşen bir hizmeti aramak için bulma kullanan özel bir kod etkinliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="c7200-109">On the client, the sample uses a custom code activity, which uses Discovery to search for a service matching a particular contract.</span></span> <span data-ttu-id="c7200-110">Kod etkinliği, daha sonra bir gönderme etkinliği tarafından kullanılan bir URI 'ye çıktı.</span><span class="sxs-lookup"><span data-stu-id="c7200-110">The code activity outputs a URI, which is later used by a send activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c7200-111">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="c7200-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c7200-112">Bu örnek, çalıştırmak için uygun URL ACL 'Leri olması gereken HTTP uç noktalarını kullanır (Ayrıntılar için bkz. [http ve https 'Yi yapılandırma](../feature-details/configuring-http-and-https.md) ).</span><span class="sxs-lookup"><span data-stu-id="c7200-112">This sample uses HTTP endpoints, which must have proper URL ACLs to run (see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md) for details).</span></span> <span data-ttu-id="c7200-113">Yükseltilmiş bir komut isteminde aşağıdaki komutu yürütmek uygun ACL 'Leri eklememelidir.</span><span class="sxs-lookup"><span data-stu-id="c7200-113">Executing the following command at an elevated command prompt should add the appropriate ACLs.</span></span> <span data-ttu-id="c7200-114">Kabuğunuz değişken biçimini anlamaz, etki alanınızı ve Kullanıcı adınızı aşağıdaki bağımsız değişkenler için değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c7200-114">If your shell does not understand the variable format, substitute your Domain and Username for the following arguments.</span></span>  
  
    `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`
  
> [!IMPORTANT]
> <span data-ttu-id="c7200-115">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7200-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c7200-116">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c7200-116">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c7200-117">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c7200-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c7200-118">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c7200-118">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
