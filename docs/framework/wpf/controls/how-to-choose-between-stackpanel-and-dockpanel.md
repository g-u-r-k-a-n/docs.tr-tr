---
title: 'Nasıl yapılır: StackPanel ve DockPanel Arasında Seçim Yapma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], StackPanel control compared to
- StackPanel control [WPF], DockPanel control compared to
- controls [WPF], StackPanel
ms.assetid: f9239086-451f-42e6-81f7-ef89ef349742
ms.openlocfilehash: bdf4b38e67a7856136224368e86609c135e5ad6f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976434"
---
# <a name="how-to-choose-between-stackpanel-and-dockpanel"></a>Nasıl yapılır: StackPanel ve DockPanel Arasında Seçim Yapma
Bu örnek, bir <xref:System.Windows.Controls.Panel>içerik yığdığınızda bir <xref:System.Windows.Controls.StackPanel> veya <xref:System.Windows.Controls.DockPanel> kullanma arasında nasıl seçim yapılacağını gösterir.

## <a name="example"></a>Örnek
 Alt öğeleri yığmak için <xref:System.Windows.Controls.DockPanel> ya da <xref:System.Windows.Controls.StackPanel> kullanabilirsiniz, ancak iki denetim her zaman aynı sonuçları oluşturmaz. Örneğin, alt öğeleri yerleştirdiğiniz sıra bir <xref:System.Windows.Controls.DockPanel> alt öğelerinin boyutunu etkileyebilir, ancak bir <xref:System.Windows.Controls.StackPanel>olamaz. Bu farklı davranış oluşur çünkü <xref:System.Windows.Controls.StackPanel> [Double. PositiveInfinity](xref:System.Double.PositiveInfinity)içindeki yığınlama yönünde ölçer; Ancak <xref:System.Windows.Controls.DockPanel> yalnızca kullanılabilir boyutu ölçer.

 Aşağıdaki örnek, <xref:System.Windows.Controls.DockPanel> ve <xref:System.Windows.Controls.StackPanel>arasındaki bu temel farkı gösterir.

 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.DockPanel>
- [Panellere Genel Bakış](panels-overview.md)
