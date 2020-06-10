---
title: "Nasıl yapılır: COM+ Hizmet Modeli Yapılandırma Aracı'nı Kullanma"
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
ms.openlocfilehash: f9e761bafd84726b51a2010a932c68c67c37f899
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595290"
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a><span data-ttu-id="b8321-102">Nasıl yapılır: COM+ Hizmet Modeli Yapılandırma Aracı'nı Kullanma</span><span class="sxs-lookup"><span data-stu-id="b8321-102">How to: Use the COM+ Service Model Configuration Tool</span></span>
<span data-ttu-id="b8321-103">Uygun bir barındırma modu seçtikten sonra, Web Hizmetleri olarak kullanıma sunulacak uygulama arabirimlerini yapılandırmak için COM+ hizmet modeli yapılandırma komut satırı aracını (ComSvcConfig. exe) kullanın.</span><span class="sxs-lookup"><span data-stu-id="b8321-103">Once you have selected an appropriate hosting mode, use the COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) to configure the application interfaces that will be exposed as Web services.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8321-104">Aşağıdaki görevlerden herhangi birini gerçekleştirmek için makinede yönetici olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8321-104">You must be an administrator on the machine to perform any of the following tasks.</span></span>  
  
 <span data-ttu-id="b8321-105">Bir Web hizmetini en son hizmet modeli sürümünü (Şu anda v 4.5) kullanacak şekilde yapılandırmak için Windows 7 makinesinde ComSvcConfig. exe ' yi kullanırken aşağıdaki adımları gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="b8321-105">When using ComSvcConfig.exe on a Windows 7 machine to configure a web service to use the latest service model version (currently v4.5), perform the following steps:</span></span>  
  
1. <span data-ttu-id="b8321-106">Kayıt defteri anahtarını `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` 0x00000001 DWORD değerine ayarlayın</span><span class="sxs-lookup"><span data-stu-id="b8321-106">Set the registry key  `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` to a DWORD value of 0x00000001</span></span>  
  
2. <span data-ttu-id="b8321-107">ComSvcConfig. exe dosyasını çalıştır</span><span class="sxs-lookup"><span data-stu-id="b8321-107">Run comsvcconfig.exe</span></span>  
  
3. <span data-ttu-id="b8321-108">Adım 1 ' de eklenen kayıt defteri anahtarını özgün değerine geri dönün veya yoksa silin.</span><span class="sxs-lookup"><span data-stu-id="b8321-108">Revert the registry key added in step 1 back to its original value, or delete it if did not exist.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b8321-109">Bu kayıt defteri anahtarının geri döndürülmesi önemlidir.</span><span class="sxs-lookup"><span data-stu-id="b8321-109">Reverting this registry key is important.</span></span> <span data-ttu-id="b8321-110">Bu bir uyumluluk anahtarıdır.</span><span class="sxs-lookup"><span data-stu-id="b8321-110">This is a compatibility key.</span></span> <span data-ttu-id="b8321-111">Bu değişikliğin geri döndürülmesi, makinede çalışan diğer .NET uygulamalarıyla ilgili sorunlara neden olabilir).</span><span class="sxs-lookup"><span data-stu-id="b8321-111">Not reverting this change may cause issues with other .NET applications running on the machine).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="b8321-112">Bir Windows 8 makinesinde ComSvcConfig. exe/install kullanırken bir iletişim kutusu görüntülenir. "bilgisayarınızdaki bir uygulama şu Windows özelliğine ihtiyaç duyuyor: .NET Framework 3,5 (.NET 2,0 ve .NET 3,0 içerir) .NET Framework 3,5 yüklü değilse.</span><span class="sxs-lookup"><span data-stu-id="b8321-112">When using ComSvcConfig.exe  /install on a Windows 8 machine a dialog is displayed stating "An app on your PC needs the following Windows feature: .NET Framework 3.5 (includes .NET 2.0 and .NET 3.0" if .NET Framework 3.5 is not installed.</span></span> <span data-ttu-id="b8321-113">Bu iletişim kutusu yoksayılabilir.</span><span class="sxs-lookup"><span data-stu-id="b8321-113">This dialog may be ignored.</span></span> <span data-ttu-id="b8321-114">Alternatif olarak, OnlyUseLatestCLR kayıt defteri anahtarını 0x00000001 DWORD değerine bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8321-114">Alternatively you can sed the OnlyUseLatestCLR registry key to a DWORD value of 0x00000001</span></span>  
  
## <a name="to-add-an-interface-to-the-set-of-interfaces-exposed-as-web-services-using-the-com-hosting-mode"></a><span data-ttu-id="b8321-115">Web Hizmetleri olarak sunulan arabirimler kümesine, COM+ barındırma modunu kullanarak bir arabirim eklemek için</span><span class="sxs-lookup"><span data-stu-id="b8321-115">To add an interface to the set of interfaces exposed as Web services, using the COM+ hosting mode</span></span>  
  
- <span data-ttu-id="b8321-116">`/install`Aşağıdaki örnekte gösterildiği gibi, ve seçeneklerini kullanarak ComSvcConfig komutunu çalıştırın `/hosting:complus` .</span><span class="sxs-lookup"><span data-stu-id="b8321-116">Run ComSvcConfig using the `/install` and `/hosting:complus` options, as shown in the following example.</span></span>  
  
    ```console  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
    ```  
  
     <span data-ttu-id="b8321-117">Komut, `IFinances` `ItemOrders.IFinancial` bileşen arabirimini (ONLINESBIR com+ uygulamasından) Web Hizmetleri olarak kullanıma sunulacak arabirimler kümesine ekler.</span><span class="sxs-lookup"><span data-stu-id="b8321-117">The command adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="b8321-118">Hizmet COM+ barındırma modunu kullanır ve bu nedenle açık uygulama etkinleştirmesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b8321-118">The service uses the COM+ hosting mode and therefore requires explicit application activation.</span></span>  
  
     <span data-ttu-id="b8321-119">\*Bir Web hizmeti olarak yalnızca seçili işlevselliği göstermek isteyebileceğiniz için, joker karakter yıldız () karakteri bileşen ve arabirim için kullanılabilir ancak kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="b8321-119">While the wildcard asterisk (\*) character can be used for the component and the interface, avoid using it because you might want to expose only selected functionality as a Web service.</span></span> <span data-ttu-id="b8321-120">Bu bileşenin gelecek bir sürümüyle çalıştırırsanız, joker karakteri kullanmak, yapılandırma sözdizimi belirleniyorsa, yanlışlıkla mevcut olmayan arabirimler sunabilir.</span><span class="sxs-lookup"><span data-stu-id="b8321-120">If run with a future version of this component, using the wildcard may unintentionally expose interfaces that may not have been present when the configuration syntax was determined.</span></span>  
  
     <span data-ttu-id="b8321-121">/Verbose seçeneği, aracının hatalara ek olarak uyarıları görüntülemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8321-121">The /verbose option instructs the tool to display warnings in addition to any errors.</span></span>  
  
     <span data-ttu-id="b8321-122">Gösterilen hizmet sözleşmesi, arabirimdeki tüm yöntemleri içerir `IFinances` .</span><span class="sxs-lookup"><span data-stu-id="b8321-122">The contract for the exposed service will contain all of the methods from the `IFinances` interface.</span></span>  
  
## <a name="to-add-only-specific-methods-from-an-interface-to-the-set-of-interfaces-exposed-as-web-services-using-the-com-hosting-mode"></a><span data-ttu-id="b8321-123">Bir arabirimden, Web Hizmetleri olarak sunulan arabirimler kümesine, COM+ barındırma modunu kullanarak yalnızca belirli yöntemler eklemek için</span><span class="sxs-lookup"><span data-stu-id="b8321-123">To add only specific methods from an interface to the set of interfaces exposed as Web services, using the COM+ hosting mode</span></span>  
  
- <span data-ttu-id="b8321-124">`/install` `/hosting:complus` Aşağıdaki örnekte gösterildiği gibi, gerekli yöntemlerin açık adlandırması ile ve seçeneklerini kullanarak ComSvcConfig komutunu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b8321-124">Run ComSvcConfig using the `/install` and `/hosting:complus` options with explicit naming of the required methods, as shown in the following example.</span></span>  
  
    ```console  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose  
    ```  
  
     <span data-ttu-id="b8321-125">Komutu, `Credit` `Debit` `IFinances` sunulan hizmet sözleşmesine yalnızca işlemler olarak arabirimden ve yöntemlerini ekler.</span><span class="sxs-lookup"><span data-stu-id="b8321-125">The command adds only the `Credit` and `Debit` methods from the `IFinances` interface as operations to the exposed service contract.</span></span> <span data-ttu-id="b8321-126">Arabirimdeki diğer tüm yöntemler sözleşmede atlanacak ve Web hizmeti istemcilerinden çağrılabilir olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="b8321-126">All other methods on the interface will be omitted from the contract and will not be callable from Web service clients.</span></span>  
  
## <a name="to-add-an-interface-to-the-set-of-interfaces-exposed-as-web-services-using-the-web-hosting-mode"></a><span data-ttu-id="b8321-127">Web hizmeti olarak sunulan arabirimler kümesine Web barındırma modunu kullanarak arabirim ekleme</span><span class="sxs-lookup"><span data-stu-id="b8321-127">To add an interface to the set of interfaces exposed as Web services, using the Web hosting mode</span></span>  
  
- <span data-ttu-id="b8321-128">`/install`Aşağıdaki örnekte gösterildiği gibi seçeneğini ve seçeneğini kullanarak ComSvcConfig komutunu çalıştırın `/hosting:was` .</span><span class="sxs-lookup"><span data-stu-id="b8321-128">Run ComSvcConfig using the `/install` option and the `/hosting:was` option, as shown in the following example.</span></span>  
  
    ```console  
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose  
    ```  
  
     <span data-ttu-id="b8321-129">Bu komut, `IStockLevels` `ItemInventory.Warehouse` bileşeni bileşenini (OnlineWarehouse com+ uygulamasından) Web Hizmetleri olarak kullanıma sunulacak arabirim kümesine ekler.</span><span class="sxs-lookup"><span data-stu-id="b8321-129">The command adds the `IStockLevels` interface on the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="b8321-130">Hizmet, COM+ yerine IIS 'nin OnlineWarehouse sanal dizininde barındırılır ve bu nedenle uygulama gerektiği şekilde otomatik olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b8321-130">The service is Web hosted in the OnlineWarehouse virtual directory of IIS rather than in COM+, and thus the application is automatically activated as required.</span></span>  
  
     <span data-ttu-id="b8321-131">Web 'de barındırılan işlem içi yapılandırmayı kullanmak için COM+ uygulaması, Bileşen Hizmetleri yönetim konsolunu kullanarak bir sunucu uygulaması yerine bir kitaplık uygulaması olarak çalışacak şekilde yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b8321-131">To use the Web-hosted in-process configuration, the COM+ application must be configured to run as a Library application rather than a Server application using the Component Services administration console.</span></span> <span data-ttu-id="b8321-132">Sunucu uygulamaları olarak yapılandırılan uygulamalar, standart Web 'de barındırılan modu kullanır ve her isteği işlemek için bir işlem atlaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8321-132">Applications configured as Server applications use the standard Web-hosted mode and incur a process hop to process each request.</span></span>  
  
     <span data-ttu-id="b8321-133">`/mex`Seçeneği, hizmetten bir sözleşme tanımı almak isteyen istemcileri desteklemek için uygulamanın hizmet uç noktasıyla aynı aktarımı kullanan bir ek meta veri değişimi (MEX) hizmet uç noktası ekler.</span><span class="sxs-lookup"><span data-stu-id="b8321-133">The `/mex` option adds an additional Metadata Exchange (MEX) service endpoint that uses the same transport as the application's service endpoint to support clients that want to retrieve a contract definition from the service.</span></span>  
  
## <a name="to-remove-a-web-service-for-a-specified-interface"></a><span data-ttu-id="b8321-134">Belirtilen bir arabirim için bir Web hizmetini kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="b8321-134">To remove a Web service for a specified interface</span></span>  
  
- <span data-ttu-id="b8321-135">Aşağıdaki örnekte gösterildiği gibi seçeneğini kullanarak ComSvcConfig komutunu çalıştırın `/uninstall` .</span><span class="sxs-lookup"><span data-stu-id="b8321-135">Run ComSvcConfig using the `/uninstall` option, as shown in the following example.</span></span>  
  
    ```console  
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus  
    ```  
  
     <span data-ttu-id="b8321-136">Komut, `IFinances` Bileşen üzerindeki arabirimini kaldırır `ItemOrders.Financial` (onlines, com+ uygulamasından).</span><span class="sxs-lookup"><span data-stu-id="b8321-136">The command removes the `IFinances` interface on the `ItemOrders.Financial` component (from the OnlineStore COM+ application).</span></span>  
  
## <a name="to-list-currently-exposed-interfaces"></a><span data-ttu-id="b8321-137">Şu anda gösterilen arabirimleri listelemek için</span><span class="sxs-lookup"><span data-stu-id="b8321-137">To list currently exposed interfaces</span></span>  
  
- <span data-ttu-id="b8321-138">Aşağıdaki örnekte gösterildiği gibi seçeneğini kullanarak ComSvcConfig komutunu çalıştırın `/list` .</span><span class="sxs-lookup"><span data-stu-id="b8321-138">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>  
  
    ```console  
    ComSvcConfig.exe /list  
    ```  
  
     <span data-ttu-id="b8321-139">Bu komut, şu anda kullanıma sunulan arabirimleri ve yerel makine kapsamındaki ilgili adres ve bağlama ayrıntılarını listeler.</span><span class="sxs-lookup"><span data-stu-id="b8321-139">The command lists the currently exposed interfaces, along with the corresponding address and binding details, scoped to the local machine.</span></span>  
  
## <a name="to-list-specific-currently-exposed-interfaces"></a><span data-ttu-id="b8321-140">Şu anda kullanıma sunulan belirli arabirimleri listelemek için</span><span class="sxs-lookup"><span data-stu-id="b8321-140">To list specific currently exposed interfaces</span></span>  
  
- <span data-ttu-id="b8321-141">Aşağıdaki örnekte gösterildiği gibi seçeneğini kullanarak ComSvcConfig komutunu çalıştırın `/list` .</span><span class="sxs-lookup"><span data-stu-id="b8321-141">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>  
  
    ```console  
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
    ```  
  
     <span data-ttu-id="b8321-142">Bu komut, yerel makinedeki Onlinesbir COM+ uygulaması için ilgili adres ve bağlama ayrıntılarının yanı sıra, şu anda COM+ barındırılan arabirimlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="b8321-142">The command lists currently exposed COM+-hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
## <a name="to-display-help-on-the-options-that-can-be-used-with-the-utility"></a><span data-ttu-id="b8321-143">Yardımcı programıyla kullanılabilecek seçeneklerle ilgili yardım görüntüleme</span><span class="sxs-lookup"><span data-stu-id="b8321-143">To display help on the options that can be used with the utility</span></span>  
  
- <span data-ttu-id="b8321-144">/? Kullanarak ComSvcConfig komutunu çalıştırın</span><span class="sxs-lookup"><span data-stu-id="b8321-144">Run ComSvcConfig using the /?</span></span> <span data-ttu-id="b8321-145">seçeneğini, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="b8321-145">option, as shown in the following example.</span></span>  
  
    ```console  
    ComSvcConfig.exe /?  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b8321-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8321-146">See also</span></span>

- [<span data-ttu-id="b8321-147">COM+ uygulamaları ile tümleştirme genel bakış</span><span class="sxs-lookup"><span data-stu-id="b8321-147">Integrating with COM+ Applications Overview</span></span>](integrating-with-com-plus-applications-overview.md)
