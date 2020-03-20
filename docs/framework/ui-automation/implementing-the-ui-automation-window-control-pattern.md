---
title: UI Otomasyonu Pencere Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
ms.openlocfilehash: dd677ca9f610d463acc7c69f99767bd7b8781589
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180040"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a><span data-ttu-id="9533a-102">UI Otomasyonu Pencere Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="9533a-102">Implementing the UI Automation Window Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="9533a-103">Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9533a-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="9533a-104">Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="9533a-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="9533a-105">Bu konu, özellikler, yöntemler ve <xref:System.Windows.Automation.Provider.IWindowProvider>olaylar hakkında <xref:System.Windows.Automation.WindowPattern> bilgiler de dahil olmak üzere uygulama yönergeleri ve kuralları sunar.</span><span class="sxs-lookup"><span data-stu-id="9533a-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IWindowProvider>, including information about <xref:System.Windows.Automation.WindowPattern> properties, methods, and events.</span></span> <span data-ttu-id="9533a-106">Ek başvurulara bağlantılar konunun sonunda listelenir.</span><span class="sxs-lookup"><span data-stu-id="9533a-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="9533a-107">Denetim <xref:System.Windows.Automation.WindowPattern> deseni, geleneksel grafik kullanıcı arabirimi (GUI) içinde temel pencere tabanlı işlevsellik sağlayan denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9533a-107">The <xref:System.Windows.Automation.WindowPattern> control pattern is used to support controls that provide fundamental window-based functionality within a traditional graphical user interface (GUI).</span></span> <span data-ttu-id="9533a-108">Bu denetim deseni uygulaması gereken denetimlere örnek olarak üst düzey uygulama pencereleri, çoklu belge arabirimi (MDI) alt pencereleri, yeniden boyutlandırılabilir bölme denetimleri, modal iletişim kutuları ve balon yardım pencereleri verilebilir.</span><span class="sxs-lookup"><span data-stu-id="9533a-108">Examples of controls that must implement this control pattern include top-level application windows, multiple-document interface (MDI) child windows, resizable split pane controls, modal dialogs and balloon help windows.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="9533a-109">Uygulama Yönergeleri ve Sözleşmeleri</span><span class="sxs-lookup"><span data-stu-id="9533a-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="9533a-110">Pencere denetim deseni uygulanırken aşağıdaki yönergeleri ve kuralları not edin:</span><span class="sxs-lookup"><span data-stu-id="9533a-110">When implementing the Window control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="9533a-111">UI Automation kullanarak hem pencere boyutunu hem de ekran konumunu <xref:System.Windows.Automation.Provider.ITransformProvider> değiştirme yeteneğini <xref:System.Windows.Automation.Provider.IWindowProvider>desteklemek için, bir denetimin ek olarak uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9533a-111">To support the ability to modify both window size and screen position using UI Automation, a control must implement <xref:System.Windows.Automation.Provider.ITransformProvider> in addition to <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="9533a-112">Denetimin taşınmasını, yeniden boyutlandırılmasını, en üst düzeye çıkarılmasını, en aza indirilmesini veya <xref:System.Windows.Automation.Provider.IWindowProvider>kapatılmasını sağlayan başlık çubukları ve başlık çubuğu öğeleri içeren denetimlerin uygulanması genellikle gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9533a-112">Controls that contain title bars and title bar elements that enable the control to be moved, resized, maximized, minimized, or closed are typically required to implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="9533a-113">Araç ucu açılır pencereleri ve açılan kutu veya menü açılır pencereleri <xref:System.Windows.Automation.Provider.IWindowProvider>gibi denetimler genellikle uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="9533a-113">Controls such as tooltip pop-ups and combo box or menu drop-downs do not typically implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
- <span data-ttu-id="9533a-114">Balon yardım pencereleri, pencere benzeri Kapat düğmesi nin sağlanmasıyla temel araç ucu açılır pencerelerinden ayırt edilir.</span><span class="sxs-lookup"><span data-stu-id="9533a-114">Balloon help windows are differentiated from basic tooltip pop-ups by the provision of a window-like Close button.</span></span>  
  
- <span data-ttu-id="9533a-115">Bir uygulamaya özel özellik olduğundan ve tipik bir pencere davranışı olmadığı için tam ekran modu IWindowProvider tarafından desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="9533a-115">Full-screen mode is not supported by IWindowProvider as it is feature-specific to an application and is not typical window behavior.</span></span>  
  
<a name="Required_Members_for_IWindowProvider"></a>
## <a name="required-members-for-iwindowprovider"></a><span data-ttu-id="9533a-116">IWindowProvider için Gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="9533a-116">Required Members for IWindowProvider</span></span>  
 <span data-ttu-id="9533a-117">IWindowProvider arabirimi için aşağıdaki özellikler, yöntemler ve olaylar gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9533a-117">The following properties, methods, and events are required for the IWindowProvider interface.</span></span>  
  
|<span data-ttu-id="9533a-118">Gerekli üye</span><span class="sxs-lookup"><span data-stu-id="9533a-118">Required member</span></span>|<span data-ttu-id="9533a-119">Üye tipi</span><span class="sxs-lookup"><span data-stu-id="9533a-119">Member type</span></span>|<span data-ttu-id="9533a-120">Notlar</span><span class="sxs-lookup"><span data-stu-id="9533a-120">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|<span data-ttu-id="9533a-121">Özellik</span><span class="sxs-lookup"><span data-stu-id="9533a-121">Property</span></span>|<span data-ttu-id="9533a-122">None</span><span class="sxs-lookup"><span data-stu-id="9533a-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|<span data-ttu-id="9533a-123">Özellik</span><span class="sxs-lookup"><span data-stu-id="9533a-123">Property</span></span>|<span data-ttu-id="9533a-124">None</span><span class="sxs-lookup"><span data-stu-id="9533a-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|<span data-ttu-id="9533a-125">Özellik</span><span class="sxs-lookup"><span data-stu-id="9533a-125">Property</span></span>|<span data-ttu-id="9533a-126">None</span><span class="sxs-lookup"><span data-stu-id="9533a-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|<span data-ttu-id="9533a-127">Özellik</span><span class="sxs-lookup"><span data-stu-id="9533a-127">Property</span></span>|<span data-ttu-id="9533a-128">None</span><span class="sxs-lookup"><span data-stu-id="9533a-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|<span data-ttu-id="9533a-129">Özellik</span><span class="sxs-lookup"><span data-stu-id="9533a-129">Property</span></span>|<span data-ttu-id="9533a-130">None</span><span class="sxs-lookup"><span data-stu-id="9533a-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|<span data-ttu-id="9533a-131">Özellik</span><span class="sxs-lookup"><span data-stu-id="9533a-131">Property</span></span>|<span data-ttu-id="9533a-132">None</span><span class="sxs-lookup"><span data-stu-id="9533a-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|<span data-ttu-id="9533a-133">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9533a-133">Method</span></span>|<span data-ttu-id="9533a-134">None</span><span class="sxs-lookup"><span data-stu-id="9533a-134">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|<span data-ttu-id="9533a-135">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9533a-135">Method</span></span>|<span data-ttu-id="9533a-136">None</span><span class="sxs-lookup"><span data-stu-id="9533a-136">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|<span data-ttu-id="9533a-137">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9533a-137">Method</span></span>|<span data-ttu-id="9533a-138">None</span><span class="sxs-lookup"><span data-stu-id="9533a-138">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|<span data-ttu-id="9533a-139">Olay</span><span class="sxs-lookup"><span data-stu-id="9533a-139">Event</span></span>|<span data-ttu-id="9533a-140">None</span><span class="sxs-lookup"><span data-stu-id="9533a-140">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|<span data-ttu-id="9533a-141">Olay</span><span class="sxs-lookup"><span data-stu-id="9533a-141">Event</span></span>|<span data-ttu-id="9533a-142">None</span><span class="sxs-lookup"><span data-stu-id="9533a-142">None</span></span>|  
|<xref:System.Windows.Automation.WindowInteractionState>|<span data-ttu-id="9533a-143">Olay</span><span class="sxs-lookup"><span data-stu-id="9533a-143">Event</span></span>|<span data-ttu-id="9533a-144">Olduğu garanti edilmez<xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span><span class="sxs-lookup"><span data-stu-id="9533a-144">Is not guaranteed to be <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span></span>|  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="9533a-145">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="9533a-145">Exceptions</span></span>  
 <span data-ttu-id="9533a-146">Sağlayıcılar aşağıdaki özel durumları atmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9533a-146">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="9533a-147">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="9533a-147">Exception type</span></span>|<span data-ttu-id="9533a-148">Koşul</span><span class="sxs-lookup"><span data-stu-id="9533a-148">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> <span data-ttu-id="9533a-149">- Denetim istenen davranışı desteklemediğinde.</span><span class="sxs-lookup"><span data-stu-id="9533a-149">-   When a control does not support a requested behavior.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> <span data-ttu-id="9533a-150">- Parametre geçerli bir sayı olmadığında.</span><span class="sxs-lookup"><span data-stu-id="9533a-150">-   When the parameter is not a valid number.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9533a-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9533a-151">See also</span></span>

- [<span data-ttu-id="9533a-152">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9533a-152">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="9533a-153">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="9533a-153">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="9533a-154">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="9533a-154">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="9533a-155">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9533a-155">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="9533a-156">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="9533a-156">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
