---
title: UI Otomasyonu Dönüştürme Denetim Düzenini Uygulama
description: Kullanıcı Arabirimi Otomasyonu 'nda dönüşüm denetim deseninin uygulanması için yönergeleri ve kuralları gözden geçirin. Iransformprovider arabirimi için gerekli üyeleri öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Transform
- Transform control pattern
- UI Automation, Transform control pattern
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
ms.openlocfilehash: fc47170a08ff08f6cd8f67996ef8fbf19c40f819
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265654"
---
# <a name="implementing-the-ui-automation-transform-control-pattern"></a><span data-ttu-id="13883-104">UI Otomasyonu Dönüştürme Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="13883-104">Implementing the UI Automation Transform Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="13883-105">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="13883-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="13883-106">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="13883-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="13883-107">Bu konuda <xref:System.Windows.Automation.Provider.ITransformProvider> Özellikler, Yöntemler ve olaylar hakkında bilgiler de dahil olmak üzere uygulama yönergeleri ve kuralları tanıtılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="13883-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITransformProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="13883-108">Ek başvuruların bağlantıları konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="13883-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="13883-109"><xref:System.Windows.Automation.TransformPattern>Denetim stili, iki boyutlu bir boşluk içinde taşınabilecek, yeniden boyutlandırılabileceğini veya döndürülebilen denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="13883-109">The <xref:System.Windows.Automation.TransformPattern> control pattern is used to support controls that can be moved, resized, or rotated within a two-dimensional space.</span></span> <span data-ttu-id="13883-110">Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="13883-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="13883-111">Uygulama kılavuzları ve kuralları</span><span class="sxs-lookup"><span data-stu-id="13883-111">Implementation Guidelines and Conventions</span></span>  

 <span data-ttu-id="13883-112">Dönüşüm denetim modelini uygularken, aşağıdaki kılavuz ve kurallara göz önünde aklınızda olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="13883-112">When implementing the Transform control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="13883-113">Bu denetim deseninin desteği masaüstündeki nesnelerle sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="13883-113">Support for this control pattern is not limited to objects on the desktop.</span></span> <span data-ttu-id="13883-114">Bu denetim deseninin ayrıca alt öğeler, kapsayıcının sınırları içinde taşınabileceği, yeniden boyutlandırılabileceği veya serbest bir şekilde döndürülebilen bir kapsayıcı nesnesinin alt öğeleri tarafından desteklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="13883-114">This control pattern must also be supported by the children of a container object if the children can be moved, resized, or rotated freely within the boundaries of the container.</span></span>  
  
- <span data-ttu-id="13883-115">Bir nesne, sonuçta elde edilen ekran konumunun kendi kapsayıcısının koordinatları dışında ve bu nedenle klavye veya fareye erişilemeyen (örneğin, üst düzey bir pencere ekrandan taşındığında veya bir alt nesne kapsayıcının Görünüm penceresinin sınırları dışına taşındığında), yeniden boyutlandırılıp döndürülemez.</span><span class="sxs-lookup"><span data-stu-id="13883-115">An object cannot be moved, resized, or rotated such that its resulting screen location would be completely outside the coordinates of its container and therefore inaccessible to the keyboard or mouse (for example, when a top-level window is moved off-screen or a child object is moved outside the boundaries of the container's viewport).</span></span> <span data-ttu-id="13883-116">Bu gibi durumlarda, nesne, kapsayıcı sınırları dahilinde olacak şekilde geçersiz kılınan üstteki veya soldaki koordinatlarla mümkün olduğunca istenen ekran koordinatlarına yakın şekilde yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="13883-116">In these cases, the object is placed as close to the requested screen coordinates as possible with the top or left coordinates overridden to be within the container boundaries.</span></span>  
  
- <span data-ttu-id="13883-117">Çoklu izleyici sistemlerinde, bir nesne birleştirilmiş masaüstü ekran koordinatları dışında taşındığında, yeniden boyutlandırılırsa veya döndürülürse, nesne birincil monitöre istenen koordinatlara yakın şekilde yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="13883-117">For multi-monitor systems, if an object is moved, resized, or rotated completely outside the combined desktop screen coordinates, the object is placed on the primary monitor as close to the requested coordinates as possible.</span></span>  
  
- <span data-ttu-id="13883-118">Tüm parametreler ve özellik değerleri mutlak ve yerel ayardan bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="13883-118">All parameters and property values are absolute and independent of locale.</span></span>  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-itransformprovider"></a><span data-ttu-id="13883-119">Iransformprovider için gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="13883-119">Required Members for ITransformProvider</span></span>  

 <span data-ttu-id="13883-120">Uygulamak için aşağıdaki özellikler ve Yöntemler gereklidir <xref:System.Windows.Automation.Provider.ITransformProvider> .</span><span class="sxs-lookup"><span data-stu-id="13883-120">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.ITransformProvider>.</span></span>  
  
|<span data-ttu-id="13883-121">Gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="13883-121">Required members</span></span>|<span data-ttu-id="13883-122">Üye türü</span><span class="sxs-lookup"><span data-stu-id="13883-122">Member type</span></span>|<span data-ttu-id="13883-123">Notlar</span><span class="sxs-lookup"><span data-stu-id="13883-123">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanMove%2A>|<span data-ttu-id="13883-124">Özellik</span><span class="sxs-lookup"><span data-stu-id="13883-124">Property</span></span>|<span data-ttu-id="13883-125">Yok</span><span class="sxs-lookup"><span data-stu-id="13883-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanResize%2A>|<span data-ttu-id="13883-126">Özellik</span><span class="sxs-lookup"><span data-stu-id="13883-126">Property</span></span>|<span data-ttu-id="13883-127">Yok</span><span class="sxs-lookup"><span data-stu-id="13883-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanRotate%2A>|<span data-ttu-id="13883-128">Özellik</span><span class="sxs-lookup"><span data-stu-id="13883-128">Property</span></span>|<span data-ttu-id="13883-129">Yok</span><span class="sxs-lookup"><span data-stu-id="13883-129">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A>|<span data-ttu-id="13883-130">Yöntem</span><span class="sxs-lookup"><span data-stu-id="13883-130">Method</span></span>|<span data-ttu-id="13883-131">Yok</span><span class="sxs-lookup"><span data-stu-id="13883-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A>|<span data-ttu-id="13883-132">Yöntem</span><span class="sxs-lookup"><span data-stu-id="13883-132">Method</span></span>|<span data-ttu-id="13883-133">Yok</span><span class="sxs-lookup"><span data-stu-id="13883-133">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A>|<span data-ttu-id="13883-134">Yöntem</span><span class="sxs-lookup"><span data-stu-id="13883-134">Method</span></span>|<span data-ttu-id="13883-135">Yok</span><span class="sxs-lookup"><span data-stu-id="13883-135">None</span></span>|  
  
 <span data-ttu-id="13883-136">Bu denetim deseninin ilişkili olayları yok.</span><span class="sxs-lookup"><span data-stu-id="13883-136">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="13883-137">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="13883-137">Exceptions</span></span>  

 <span data-ttu-id="13883-138">Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="13883-138">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="13883-139">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="13883-139">Exception Type</span></span>|<span data-ttu-id="13883-140">Koşul</span><span class="sxs-lookup"><span data-stu-id="13883-140">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> <span data-ttu-id="13883-141">- <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> False ise.</span><span class="sxs-lookup"><span data-stu-id="13883-141">-   If the <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> is false.</span></span>|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> <span data-ttu-id="13883-142">- <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> False ise.</span><span class="sxs-lookup"><span data-stu-id="13883-142">-   If the <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> is false.</span></span>|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> <span data-ttu-id="13883-143">- <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> False ise.</span><span class="sxs-lookup"><span data-stu-id="13883-143">-   If the <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> is false.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="13883-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13883-144">See also</span></span>

- [<span data-ttu-id="13883-145">UI Otomasyon Denetim Düzenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="13883-145">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="13883-146">UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="13883-146">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="13883-147">İstemciler İçin UI Otomasyon Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="13883-147">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="13883-148">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="13883-148">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="13883-149">UI Otomasyonda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="13883-149">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
