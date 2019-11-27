---
title: UI Otomasyon Denetim Türlerine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
ms.openlocfilehash: ec2dd3635f09144985df278be1d53ead675d3080
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442632"
---
# <a name="ui-automation-control-types-overview"></a>UI Otomasyon Denetim Türlerine Genel Bakış
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] denetim türleri, Birleşik giriş kutusu ya da düğme gibi belirli bir öğenin ne tür bir denetimin temsil ettiğini göstermek için kullanılabilecek iyi bilinen tanımlayıcılardır.  
  
 İyi bilinen bir tanımlayıcıya sahip olmak, yardımcı teknoloji cihazlarının [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] hangi tür denetimlerin kullanılabilir olduğunu ve denetimlerle nasıl etkileşime gireceğini belirlemenizi kolaylaştırır.  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a>UI Otomasyonu Denetim türü gereksinimleri  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] denetim türleri, sağlayıcıların karşılaması gereken koşullar kümesini sağlar. Bu koşullar karşılandığında denetim, belirli denetim türü adını kullanabilir. Her denetim türü aşağıdakiler için koşullara sahiptir:  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Denetim desenleri — hangi denetim desenlerinin desteklenmelidir, hangi Denetim desenleri isteğe bağlıdır ve hangi denetim desenlerinin denetim tarafından desteklenmemelidir.  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri — hangi özellik değerlerini destekler.  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı — denetim için gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı.  
  
 Bir denetim belirli bir denetim türünün koşullarını karşılıyorsa, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> Özellik değeri bu denetim türünü gösterir.  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a>Geçerli UI Otomasyon Denetim türleri  
 Aşağıdaki liste, geçerli [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] denetim türleri kümesini içerir:  
  
- [Button Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-button-control-type.md)  
  
- [Calendar Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-calendar-control-type.md)  
  
- [CheckBox Denetim Türü için UI Otomasyonu Desteği](ui-automation-support-for-the-checkbox-control-type.md)  
  
- [ComboBox Denetim Türü için UI Otomasyonu Desteği](ui-automation-support-for-the-combobox-control-type.md)  
  
- [DataGrid Denetim Türü için UI Otomasyonu Desteği](ui-automation-support-for-the-datagrid-control-type.md)  
  
- [DataItem Denetim Türü için UI Otomasyonu Desteği](ui-automation-support-for-the-dataitem-control-type.md)  
  
- [Document Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-document-control-type.md)  
  
- [Edit Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-edit-control-type.md)  
  
- [Group Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-group-control-type.md)  
  
- [Header Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-header-control-type.md)  
  
- [HeaderItem Denetim Türü için UI Otomasyonu Desteği](ui-automation-support-for-the-headeritem-control-type.md)  
  
- [Hyperlink Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-hyperlink-control-type.md)  
  
- [Image Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-image-control-type.md)  
  
- [List Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-list-control-type.md)  
  
- [ListItem Denetim Türü için UI Otomasyonu Desteği](ui-automation-support-for-the-listitem-control-type.md)  
  
- [Menu Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-menu-control-type.md)  
  
- [MenuBar Denetim Türü için UI Otomasyonu Desteği](ui-automation-support-for-the-menubar-control-type.md)  
  
- [MenuItem Denetim Türü için UI Otomasyonu Desteği](ui-automation-support-for-the-menuitem-control-type.md)  
  
- [Pane Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-pane-control-type.md)  
  
- [ProgressBar Denetim Türü için UI Otomasyonu Desteği](ui-automation-support-for-the-progressbar-control-type.md)  
  
- [RadioButton Denetim Türü için UI Otomasyonu Desteği](ui-automation-support-for-the-radiobutton-control-type.md)  
  
- [ScrollBar Denetim Türü için UI Otomasyonu Desteği](ui-automation-support-for-the-scrollbar-control-type.md)  
  
- [Separator Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-separator-control-type.md)  
  
- [Slider Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-slider-control-type.md)  
  
- [Spinner Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-spinner-control-type.md)  
  
- [SplitButton Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-splitbutton-control-type.md)  
  
- [StatusBar Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-statusbar-control-type.md)  
  
- [Tab Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-tab-control-type.md)  
  
- [TabItem Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-tabitem-control-type.md)  
  
- [Table Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-table-control-type.md)  
  
- [Text Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-text-control-type.md)  
  
- [Thumb Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-thumb-control-type.md)  
  
- [TitleBar Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-titlebar-control-type.md)  
  
- [ToolBar Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-toolbar-control-type.md)  
  
- [ToolTip Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-tooltip-control-type.md)  
  
- [Tree Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-tree-control-type.md)  
  
- [TreeItem Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-treeitem-control-type.md)  
  
- [Window Denetim Türü İçin UI Otomasyonu Desteği](ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType>
