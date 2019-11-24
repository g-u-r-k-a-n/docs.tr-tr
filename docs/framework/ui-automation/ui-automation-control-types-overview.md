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
> This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace. For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] control types are well-known identifiers that can be used to indicate what kind of control a particular element represents, such as a combo box or a button.  
  
 Having a well-known identifier makes it easier for assistive technology devices to determine what types of controls are available in the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] and how to interact with the controls.  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a>UI Automation Control Type Requisites  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] control types provide a set of conditions that providers must meet. When these conditions are met, the control can use the specific control type name. Each control type has conditions for the following:  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] control patterns—which control patterns must be supported, which control patterns are optional, and which control patterns must not be supported by the control.  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] property values—which property values are supported.  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure—the required [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure for the control.  
  
 When a control meets the conditions for a particular control type, the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> property value will indicate that control type.  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a>Current UI Automation Control Types  
 The following list contains the current set of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] control types:  
  
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
