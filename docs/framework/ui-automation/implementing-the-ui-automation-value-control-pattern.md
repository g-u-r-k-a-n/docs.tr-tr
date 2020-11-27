---
title: UI Otomasyonu Değer Denetim Düzenini Uygulama
description: Kullanıcı Arabirimi Otomasyonu 'nda değer denetim deseninin uygulanması için yönergeleri ve kuralları gözden geçirin. IValueProvider arabirimi için gerekli üyeleri öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
ms.openlocfilehash: b4fea39088064751ff559bd236554255d43ba2a2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265667"
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a><span data-ttu-id="ab6fb-104">UI Otomasyonu Değer Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="ab6fb-104">Implementing the UI Automation Value Control Pattern</span></span>

> [!NOTE]
> <span data-ttu-id="ab6fb-105">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="ab6fb-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="ab6fb-106">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="ab6fb-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="ab6fb-107">Bu konu <xref:System.Windows.Automation.Provider.IValueProvider> , olaylar ve özellikler hakkında bilgiler de dahil olmak üzere uygulama yönergelerini ve kurallarını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IValueProvider>, including information on events and properties.</span></span> <span data-ttu-id="ab6fb-108">Ek başvuruların bağlantıları konunun sonunda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="ab6fb-109"><xref:System.Windows.Automation.ValuePattern>Denetim stili, bir aralığa yayılmayan ve dize olarak gösterilebilen bir iç değere sahip denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-109">The <xref:System.Windows.Automation.ValuePattern> control pattern is used to support controls that have an intrinsic value not spanning a range and that can be represented as a string.</span></span> <span data-ttu-id="ab6fb-110">Bu dize, denetime ve ayarlarına bağlı olarak düzenlenebilir.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-110">This string can be editable, depending on the control and its settings.</span></span> <span data-ttu-id="ab6fb-111">Bu kalıbı uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="ab6fb-111">For examples of controls that implement this pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="ab6fb-112">Uygulama kılavuzları ve kuralları</span><span class="sxs-lookup"><span data-stu-id="ab6fb-112">Implementation Guidelines and Conventions</span></span>  

 <span data-ttu-id="ab6fb-113">Değer denetim modelini uygularken, aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ab6fb-113">When implementing the Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="ab6fb-114">Ve gibi denetimler <xref:System.Windows.Automation.ControlType.ListItem> , <xref:System.Windows.Automation.ControlType.TreeItem> <xref:System.Windows.Automation.ValuePattern> denetimin geçerli düzenleme modundan bağımsız olarak, öğelerin herhangi birinin değeri düzenlenebilir ise, desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-114">Controls such as <xref:System.Windows.Automation.ControlType.ListItem> and <xref:System.Windows.Automation.ControlType.TreeItem> must support <xref:System.Windows.Automation.ValuePattern> if the value of any of the items is editable, regardless of the current edit mode of the control.</span></span> <span data-ttu-id="ab6fb-115">Alt öğelerin düzenlenebilir olması durumunda üst denetim de desteklemelidir <xref:System.Windows.Automation.ValuePattern> .</span><span class="sxs-lookup"><span data-stu-id="ab6fb-115">The parent control must also support <xref:System.Windows.Automation.ValuePattern> if the child items are editable.</span></span>  
  
 <span data-ttu-id="ab6fb-116">![Düzenlenebilir liste öğesi.](./media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")</span><span class="sxs-lookup"><span data-stu-id="ab6fb-116">![Editable list item.](./media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")</span></span>  
<span data-ttu-id="ab6fb-117">Düzenlenebilir liste öğesi örneği</span><span class="sxs-lookup"><span data-stu-id="ab6fb-117">Example of an Editable List Item</span></span>  
  
- <span data-ttu-id="ab6fb-118">Tek satırlık düzenleme denetimleri, uygulayarak içeriğine programlı erişimi destekler <xref:System.Windows.Automation.Provider.IValueProvider> .</span><span class="sxs-lookup"><span data-stu-id="ab6fb-118">Single-line edit controls support programmatic access to their contents by implementing <xref:System.Windows.Automation.Provider.IValueProvider>.</span></span> <span data-ttu-id="ab6fb-119">Ancak, çok satırlı düzenleme denetimleri uygulamaz <xref:System.Windows.Automation.Provider.IValueProvider> ; bunun yerine kendi içeriğine erişim sağlar <xref:System.Windows.Automation.Provider.ITextProvider> .</span><span class="sxs-lookup"><span data-stu-id="ab6fb-119">However, multi-line edit controls do not implement <xref:System.Windows.Automation.Provider.IValueProvider>; instead they provide access to their content by implementing <xref:System.Windows.Automation.Provider.ITextProvider>.</span></span>  
  
- <span data-ttu-id="ab6fb-120">Çok satırlı bir düzenleme denetiminin metin içeriğini almak için, denetimin uygulanması gerekir <xref:System.Windows.Automation.Provider.ITextProvider> .</span><span class="sxs-lookup"><span data-stu-id="ab6fb-120">To retrieve the textual contents of a multi-line edit control, the control must implement <xref:System.Windows.Automation.Provider.ITextProvider>.</span></span> <span data-ttu-id="ab6fb-121">Ancak, <xref:System.Windows.Automation.Provider.ITextProvider> bir denetimin değerini ayarlamayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-121">However, <xref:System.Windows.Automation.Provider.ITextProvider> does not support setting the value of a control.</span></span>  
  
- <span data-ttu-id="ab6fb-122"><xref:System.Windows.Automation.Provider.IValueProvider> biçimlendirme bilgilerinin veya alt dize değerlerinin alınmasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-122"><xref:System.Windows.Automation.Provider.IValueProvider> does not support the retrieval of formatting information or substring values.</span></span> <span data-ttu-id="ab6fb-123"><xref:System.Windows.Automation.Provider.ITextProvider>Bu senaryolarda uygulayın.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-123">Implement <xref:System.Windows.Automation.Provider.ITextProvider> in these scenarios.</span></span>  
  
- <span data-ttu-id="ab6fb-124"><xref:System.Windows.Automation.Provider.IValueProvider> , bir renk değeri (örneğin, "sarı") ve eşdeğer iç RGB yapısı arasındaki dize eşlemesini destekleyen Microsoft Word 'den (aşağıda gösterildiği gibi) **renk seçici** seçim denetimi gibi denetimler tarafından uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-124"><xref:System.Windows.Automation.Provider.IValueProvider> must be implemented by controls such as the **Color Picker** selection control from Microsoft Word (illustrated below), which supports string mapping between a color value (for example, "yellow") and an equivalent internal RGB structure.</span></span>  
  
 <span data-ttu-id="ab6fb-125">![Sarı vurgulanmış şekilde renk seçici.](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")</span><span class="sxs-lookup"><span data-stu-id="ab6fb-125">![Color picker with yellow highlighted.](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")</span></span>  
<span data-ttu-id="ab6fb-126">Renk örneği dize eşlemesi örneği</span><span class="sxs-lookup"><span data-stu-id="ab6fb-126">Example of Color Swatch String Mapping</span></span>  
  
- <span data-ttu-id="ab6fb-127">Bir denetimin öğesine, <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> `true` <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> `false` çağrısına izin vermeden önce, olarak ayarlanmış olması gerekir <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A> .</span><span class="sxs-lookup"><span data-stu-id="ab6fb-127">A control should have its <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> set to `true` and its <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> set to `false` before allowing a call to <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>.</span></span>  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-ivalueprovider"></a><span data-ttu-id="ab6fb-128">IValueProvider için gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="ab6fb-128">Required Members for IValueProvider</span></span>  

 <span data-ttu-id="ab6fb-129">Uygulamak için aşağıdaki özellikler ve Yöntemler gereklidir <xref:System.Windows.Automation.Provider.IValueProvider> .</span><span class="sxs-lookup"><span data-stu-id="ab6fb-129">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IValueProvider>.</span></span>  
  
|<span data-ttu-id="ab6fb-130">Gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="ab6fb-130">Required members</span></span>|<span data-ttu-id="ab6fb-131">Üye türü</span><span class="sxs-lookup"><span data-stu-id="ab6fb-131">Member type</span></span>|<span data-ttu-id="ab6fb-132">Notlar</span><span class="sxs-lookup"><span data-stu-id="ab6fb-132">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>|<span data-ttu-id="ab6fb-133">Özellik</span><span class="sxs-lookup"><span data-stu-id="ab6fb-133">Property</span></span>|<span data-ttu-id="ab6fb-134">Yok</span><span class="sxs-lookup"><span data-stu-id="ab6fb-134">None</span></span>|  
|<xref:System.Windows.Automation.ValuePattern.ValueProperty>|<span data-ttu-id="ab6fb-135">Özellik</span><span class="sxs-lookup"><span data-stu-id="ab6fb-135">Property</span></span>|<span data-ttu-id="ab6fb-136">Yok</span><span class="sxs-lookup"><span data-stu-id="ab6fb-136">None</span></span>|  
|<xref:System.Windows.Automation.ValuePattern.SetValue%2A>|<span data-ttu-id="ab6fb-137">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ab6fb-137">Method</span></span>|<span data-ttu-id="ab6fb-138">Yok</span><span class="sxs-lookup"><span data-stu-id="ab6fb-138">None</span></span>|  
  
<a name="Exceptions"></a>

## <a name="exceptions"></a><span data-ttu-id="ab6fb-139">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="ab6fb-139">Exceptions</span></span>  

 <span data-ttu-id="ab6fb-140">Sağlayıcılar aşağıdaki özel durumları oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-140">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="ab6fb-141">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="ab6fb-141">Exception type</span></span>|<span data-ttu-id="ab6fb-142">Koşul</span><span class="sxs-lookup"><span data-stu-id="ab6fb-142">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> <span data-ttu-id="ab6fb-143">-Yerel ayara özgü bilgiler hatalı biçimlendirilmiş bir tarih gibi yanlış biçimde bir denetime geçirildiyse.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-143">-   If locale-specific information is passed to a control in an incorrect format such as an incorrectly formatted date.</span></span>|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> <span data-ttu-id="ab6fb-144">-Yeni bir değer bir dizeden denetimin tanıdığı biçime dönüştürülemez.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-144">-   If a new value cannot be converted from a string to a format the control recognizes.</span></span>|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> <span data-ttu-id="ab6fb-145">-Etkin olmayan bir denetimi işlemek için bir girişimde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-145">-   When an attempt is made to manipulate a control that is not enabled.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab6fb-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab6fb-146">See also</span></span>

- [<span data-ttu-id="ab6fb-147">UI Otomasyon Denetim Düzenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ab6fb-147">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="ab6fb-148">UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="ab6fb-148">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="ab6fb-149">İstemciler İçin UI Otomasyon Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="ab6fb-149">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="ab6fb-150">Valuemodel metin ekleme örneği</span><span class="sxs-lookup"><span data-stu-id="ab6fb-150">ValuePattern Insert Text Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [<span data-ttu-id="ab6fb-151">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ab6fb-151">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="ab6fb-152">UI Otomasyonda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="ab6fb-152">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
