---
title: UI Otomasyon Özelliklerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, properties
- properties, UI Automation
ms.assetid: a6c31d7b-b33e-49b3-b5c1-31a345f9b7c8
ms.openlocfilehash: 2f96f3c7261882af58cd10038d729c4e723d6fa0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447960"
---
# <a name="ui-automation-properties-overview"></a>UI Otomasyon Özelliklerine Genel Bakış
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 UI Otomasyon sağlayıcıları [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] öğelerinde özellikleri kullanıma sunar. Bu özellikler, UI Otomasyonu istemci uygulamalarının hem statik hem de dinamik veriler de dahil olmak üzere [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]parçaları hakkında bilgi bulmasına olanak tanır.  
  
 Bu bölüm [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] özelliklerine kapsamlı bir genel bakış sunar. Aşağıdaki konularda daha ayrıntılı bilgiler verilmiştir:  
  
- [İstemciler İçin UI Otomasyonu Özellikleri](ui-automation-properties-for-clients.md)  
  
- [Sunucu Tarafı UI Otomasyonu Sağlayıcısı Uygulama](server-side-ui-automation-provider-implementation.md)  
  
<a name="Property_Identifiers"></a>   
## <a name="property-identifiers"></a>Özellik tanımlayıcıları  
 Her özellik bir sayı ve bir ad ile tanımlanır. Özelliklerin adları yalnızca hata ayıklama ve Tanılama için kullanılır. Sağlayıcılar gelen özellik isteklerini tanımlamak için sayısal kimlikleri kullanır. Ancak, istemci uygulamaları, almak istedikleri özellikleri tanımlamak için yalnızca sayıyı ve adı kapsülleyen <xref:System.Windows.Automation.AutomationProperty>kullanır.  
  
 belirli özellikleri temsil eden <xref:System.Windows.Automation.AutomationProperty> nesneleri çeşitli sınıflarda alanlar olarak kullanılabilir. Güvenlik nedenleriyle, UI Otomasyon sağlayıcıları bu nesneleri UIAutomationTypes. dll içinde yer alan ayrı bir sınıf kümesinden alır.  
  
 Aşağıdaki tablo, <xref:System.Windows.Automation.AutomationProperty>kimliklerini içeren sınıfların özelliklerini kategorilere ayırır.  
  
|Özellik türleri|İstemcilerin kimlikleri alması|Sağlayıcılar kimlik al|  
|-------------------------|--------------------------|----------------------------|  
|Tüm öğelerde ortak olan Özellikler (aşağıdaki tablolara bakın)|<xref:System.Windows.Automation.AutomationElement>|<xref:System.Windows.Automation.AutomationElementIdentifiers>|  
|Yerleştirme penceresinin konumu|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.DockPatternIdentifiers>|  
|Genişleyebilir ve daraltılabilen bir öğenin durumu|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers>|  
|Kılavuzdaki bir öğenin özellikleri|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.GridItemPatternIdentifiers>|  
|Kılavuzun özellikleri|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.GridPatternIdentifiers>|  
|Birden çok görünümü olan bir öğenin geçerli ve desteklenen görünümü|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers>|  
|Kaydırıcı gibi bir değer aralığı üzerinde taşınan bir öğenin özellikleri|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.RangeValuePatternIdentifiers>|  
|Kaydırılan pencerenin özellikleri|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.ScrollPatternIdentifiers>|  
|Bir listede olduğu gibi, seçilebir öğenin durumu ve kapsayıcısı|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers>|  
|Seçim öğelerini içeren bir denetimin özellikleri|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.SelectionPatternIdentifiers>|  
|Tablodaki bir öğenin sütun ve satır üst bilgileri|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.TableItemPatternIdentifiers>|  
|Bir tablonun sütun ve satır başlıkları ve yönü|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.TablePatternIdentifiers>|  
|İki durumlu denetimin durumu|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.TogglePatternIdentifiers>|  
|Taşınabilecek, döndürülebilen veya yeniden boyutlandırılan bir öğenin özellikleri|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.TransformPatternIdentifiers>|  
|Değer içeren bir öğenin değeri ve okuma/yazma özellikleri|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.ValuePatternIdentifiers>|  
|Pencerenin özellikleri ve durumu|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.WindowPatternIdentifiers>|  
  
<a name="Properties_by_Category"></a>   
## <a name="properties-by-category"></a>Kategoriye göre Özellikler  
 Aşağıdaki tablolar, kimlikleri <xref:System.Windows.Automation.AutomationElement> ve <xref:System.Windows.Automation.AutomationElementIdentifiers>bulunan özellikleri sınıflandırmıştır. Bu özellikler tüm denetimlerde ortaktır. Ancak, bir kaç tane, sağlayıcı uygulamasının ömrü boyunca statik olması olasıdır; çoğu dinamik özellik denetim desenleriyle ilişkilendirilir.  
  
 **Özellik erişim** sütunu, <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> ve <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>ek olarak her bir özellik için diğer erişimcileri listeler. İstemci uygulamasında Özellikler alma hakkında daha fazla bilgi için bkz. [istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).  
  
> [!NOTE]
> Her özellik hakkında belirli bilgiler için, **özellik erişim** sütunundaki bağlantıyı izleyin.  
  
### <a name="display-characteristics"></a>Görüntü özellikleri  
  
|Özellik tanımlayıcısı|Özellik erişimi|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>|  
|<xref:System.Windows.Automation.AutomationElement.CultureProperty>|yok|  
|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsOffscreen%2A>|  
|<xref:System.Windows.Automation.AutomationElement.OrientationProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Orientation%2A>|  
  
### <a name="element-type"></a>{1&gt;Type Öğesi&lt;1}  
  
|Özellik tanımlayıcısı|Özellik erişimi|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsContentElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsControlElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LocalizedControlType%2A>|  
  
### <a name="identification"></a>İsi  
  
|Özellik tanımlayıcısı|Özellik erişimi|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClassNameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ClassName%2A>|  
|<xref:System.Windows.Automation.AutomationElement.FrameworkIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.FrameworkId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LabeledByProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LabeledBy%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ProcessIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ProcessId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.RuntimeIdProperty>|<xref:System.Windows.Automation.AutomationElement.GetRuntimeId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NativeWindowHandleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.NativeWindowHandle%2A>|  
  
### <a name="interaction"></a>Etkileşimi  
  
|Özellik tanımlayıcısı|Özellik erişimi|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AcceleratorKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AccessKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>|<xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>|  
|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HasKeyboardFocus%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsEnabled%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsKeyboardFocusable%2A>|  
  
### <a name="support-for-patterns"></a>Desenler için destek  
  
|Özellik tanımlayıcısı|Özellik erişimi|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsExpandCollapsePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsGridItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsGridPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsInvokePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsMultipleViewPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsRangeValuePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsScrollItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsScrollPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsSelectionItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsSelectionPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTableItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTablePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTogglePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTransformPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsValuePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsWindowPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
  
### <a name="miscellaneous"></a>Çeşitli  
  
|Özellik tanımlayıcısı|Özellik erişimi|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsRequiredForFormProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsRequiredForForm%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsPassword%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemStatusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemStatus%2A>|  
  
<a name="Localization"></a>   
## <a name="localization"></a>Yerelleştirme  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sağlayıcılar, işletim sisteminin dilinde aşağıdaki özellikleri sunmalıdır:  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
<a name="Properties_and_Events"></a>   
## <a name="properties-and-events"></a>Özellikler ve olaylar  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliklerle yakından birlikte, özellik değiştirme olaylarının kavramıdır. Dinamik özellikler için, istemci uygulamanın bir özellik değerinin değiştiğini bilmesi için bir yol gerekir, böylece bilgi önbelleğini güncelleştirebilir veya yeni bilgilere başka bir şekilde tepki verebilir.  
  
 Sağlayıcılar, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] değiştiğinde olayları yükseltir. Örneğin, bir onay kutusu seçiliyse veya silinirse, sağlayıcının Iki durumlu düzenin uygulamasıyla bir özellik değiştirildi olayı tetiklenir. Sağlayıcılar, herhangi bir istemcinin olayları dinleyip dinlemediğini veya belirli olayları dinlemediğine bağlı olarak olayları seçerek oluşturabilir.  
  
 Tüm özellik değişiklikleri olay oluşturmaz; Bu, öğesi için UI Otomasyon sağlayıcısının uygulamasına tamamıyla çalışır. Örneğin, liste kutuları için standart proxy sağlayıcıları <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> değiştiğinde bir olay oluşturmaz. Bu durumda, bunun yerine uygulamanın <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>dinlemesi gerekir.  
  
 İstemciler bu olaylara abone olarak olay dinler. Olaylara abone olmak, olayları işleyebilen temsilci yöntemleri oluşturma ve ardından bu yöntemler içinde yer alacak belirli olaylarla birlikte [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] yöntemleri geçirme anlamına gelir. Özellikle özellik tarafından değiştirilen olaylar için, istemcilerin <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>uygulaması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu İstemcilerinde Önbelleğe Alma](caching-in-ui-automation-clients.md)
- [İstemciler İçin UI Otomasyonu Özellikleri](ui-automation-properties-for-clients.md)
- [Sunucu Tarafı UI Otomasyonu Sağlayıcısı Uygulama](server-side-ui-automation-provider-implementation.md)
- [Özellik Koşulunu Temel Alan UI Otomasyonu Öğesi Bulma](find-a-ui-automation-element-based-on-a-property-condition.md)
- [UI Otomasyonu Sağlayıcı Dönüş Özellikleri](return-properties-from-a-ui-automation-provider.md)
- [UI Otomasyonu Sağlayıcıda Olay Tetikleme](raise-events-from-a-ui-automation-provider.md)
