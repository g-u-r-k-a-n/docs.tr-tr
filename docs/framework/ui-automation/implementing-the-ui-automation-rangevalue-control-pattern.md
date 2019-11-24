---
title: UI Otomasyon RangeValue Denetim Düzeni Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 04db9f97ccea10cf8c65df0f0117c272a5e868dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435109"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a>UI Otomasyon RangeValue Denetim Düzeni Uygulama
> [!NOTE]
> This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace. For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties. Links to additional references are listed at the end of the topic.  
  
 The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range. For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Implementation Guidelines and Conventions  
 When implementing the Range Value control pattern, note the following guidelines and conventions:  
  
- Controls allow recalibration of their supported properties based upon locale or user preference. An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.  
  
- Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.  
  
 ![Progress bar.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")  
Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a>Required Members for IRangeValueProvider  
  
|Required member|Member type|Notlar|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|Özellik|Yok.|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|Özellik|Yok.|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|Özellik|Yok.|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|Özellik|Yok.|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|Özellik|Yok.|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|Özellik|Yok.|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|Yöntemler|Yok.|  
  
 This control pattern has no associated events.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Özel Durumlar  
 Providers must throw the following exceptions.  
  
|Özel durum türü|Koşul|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
