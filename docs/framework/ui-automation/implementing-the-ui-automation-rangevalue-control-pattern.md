---
title: UI Otomasyon RangeValue Denetim Düzeni Uygulama
description: UI otomasyonunda RangeValue denetim deseninin uygulanması için yönergeleri ve kuralları gözden geçirin. IRangeValueProvider arabirimi için gereken üyelere bakın.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: ccb6aeb5f8451975d7e2e9649bbb82c0c3ae23d5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164085"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="84987-104">UI Otomasyon RangeValue Denetim Düzeni Uygulama</span><span class="sxs-lookup"><span data-stu-id="84987-104">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="84987-105">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="84987-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="84987-106">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="84987-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="84987-107">Bu konu <xref:System.Windows.Automation.Provider.IRangeValueProvider> , olaylar ve özellikler hakkında bilgiler de dahil olmak üzere uygulama yönergelerini ve kurallarını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="84987-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="84987-108">Ek başvuruların bağlantıları konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="84987-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="84987-109"><xref:System.Windows.Automation.RangeValuePattern>Denetim deseninin bir Aralık içindeki bir değere ayarlanabilir denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="84987-109">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="84987-110">Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="84987-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="84987-111">Uygulama kılavuzları ve kuralları</span><span class="sxs-lookup"><span data-stu-id="84987-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="84987-112">Aralık değeri denetim modelini uygularken, aşağıdaki kılavuz ve kurallara göz önünde aklınızda olmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="84987-112">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="84987-113">Denetimler, yerel ayar veya kullanıcı tercihlerine göre desteklenen özelliklerinin yeniden yüklenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="84987-113">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="84987-114">Bunun bir örneği, sıcaklığın Fahrenveya santigrat cinsinden gösterilmesi için ayarlanabilir bir termometre denetimidir.</span><span class="sxs-lookup"><span data-stu-id="84987-114">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
- <span data-ttu-id="84987-115">İlerleme çubukları veya kaydırıcılar gibi belirsiz Aralık değerlerine sahip denetimler bu değerlerin normalleştirilmesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="84987-115">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="84987-116">![İlerleme çubuğu.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="84987-116">![Progress bar.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="84987-117">Değerin tamsayı türünde ve en düşük ve en yüksek özellik değerlerinin, sırasıyla 0 ve 100 olarak normalleştirilme Ilerleme çubuğu örneği</span><span class="sxs-lookup"><span data-stu-id="84987-117">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="84987-118">IRangeValueProvider için gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="84987-118">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="84987-119">Gerekli üye</span><span class="sxs-lookup"><span data-stu-id="84987-119">Required member</span></span>|<span data-ttu-id="84987-120">Üye türü</span><span class="sxs-lookup"><span data-stu-id="84987-120">Member type</span></span>|<span data-ttu-id="84987-121">Notlar</span><span class="sxs-lookup"><span data-stu-id="84987-121">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="84987-122">Özellik</span><span class="sxs-lookup"><span data-stu-id="84987-122">Property</span></span>|<span data-ttu-id="84987-123">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="84987-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="84987-124">Özellik</span><span class="sxs-lookup"><span data-stu-id="84987-124">Property</span></span>|<span data-ttu-id="84987-125">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="84987-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="84987-126">Özellik</span><span class="sxs-lookup"><span data-stu-id="84987-126">Property</span></span>|<span data-ttu-id="84987-127">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="84987-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="84987-128">Özellik</span><span class="sxs-lookup"><span data-stu-id="84987-128">Property</span></span>|<span data-ttu-id="84987-129">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="84987-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="84987-130">Özellik</span><span class="sxs-lookup"><span data-stu-id="84987-130">Property</span></span>|<span data-ttu-id="84987-131">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="84987-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="84987-132">Özellik</span><span class="sxs-lookup"><span data-stu-id="84987-132">Property</span></span>|<span data-ttu-id="84987-133">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="84987-133">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="84987-134">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="84987-134">Methods</span></span>|<span data-ttu-id="84987-135">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="84987-135">None</span></span>|  
  
 <span data-ttu-id="84987-136">Bu denetim deseninin ilişkili olayları yok.</span><span class="sxs-lookup"><span data-stu-id="84987-136">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="84987-137">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="84987-137">Exceptions</span></span>  
 <span data-ttu-id="84987-138">Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="84987-138">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="84987-139">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="84987-139">Exception type</span></span>|<span data-ttu-id="84987-140">Koşul</span><span class="sxs-lookup"><span data-stu-id="84987-140">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="84987-141"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>değerinden büyük veya bundan küçük bir değerle çağırılır <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty> .</span><span class="sxs-lookup"><span data-stu-id="84987-141"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="84987-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84987-142">See also</span></span>

- [<span data-ttu-id="84987-143">UI Otomasyon Denetim Düzenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="84987-143">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="84987-144">UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="84987-144">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="84987-145">İstemciler İçin UI Otomasyon Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="84987-145">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="84987-146">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="84987-146">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="84987-147">UI Otomasyonda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="84987-147">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
