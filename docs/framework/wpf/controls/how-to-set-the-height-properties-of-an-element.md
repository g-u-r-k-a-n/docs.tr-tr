---
title: 'Nasıl yapılır: Öğenin Yükseklik Özelliklerini Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- height properties [WPF]
- Panel control [WPF], height properties of elements
ms.assetid: 5ab9e781-dbb8-469a-a3c8-cf38ce312647
ms.openlocfilehash: 6500af3c637092820e538d79894d600d617953bf
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124292"
---
# <a name="how-to-set-the-height-properties-of-an-element"></a><span data-ttu-id="b3dd7-102">Nasıl yapılır: Öğenin Yükseklik Özelliklerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="b3dd7-102">How to: Set the Height Properties of an Element</span></span>
## <a name="example"></a><span data-ttu-id="b3dd7-103">Örnek</span><span class="sxs-lookup"><span data-stu-id="b3dd7-103">Example</span></span>  
 <span data-ttu-id="b3dd7-104">Bu örnek, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]' deki yükseklik ile ilgili dört özellik arasındaki işleme davranışının farklarını görsel olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3dd7-104">This example visually shows the differences in rendering behavior among the four height-related properties in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="b3dd7-105"><xref:System.Windows.FrameworkElement> sınıfı, bir öğenin yükseklik özelliklerini tanımlayan dört özellik sunar.</span><span class="sxs-lookup"><span data-stu-id="b3dd7-105">The <xref:System.Windows.FrameworkElement> class exposes four properties that describe the height characteristics of an element.</span></span> <span data-ttu-id="b3dd7-106">Bu dört Özellik çakışabilir ve ne zaman, öncelik veren değer aşağıdaki şekilde belirlenir: <xref:System.Windows.FrameworkElement.MinHeight%2A> değeri <xref:System.Windows.FrameworkElement.MaxHeight%2A> değerine göre önceliklidir ve bu da <xref:System.Windows.FrameworkElement.Height%2A> değerinden önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="b3dd7-106">These four properties can conflict, and when they do, the value that takes precedence is determined as follows: the <xref:System.Windows.FrameworkElement.MinHeight%2A> value takes precedence over the <xref:System.Windows.FrameworkElement.MaxHeight%2A> value, which in turn takes precedence over the <xref:System.Windows.FrameworkElement.Height%2A> value.</span></span> <span data-ttu-id="b3dd7-107">Dördüncü özellik <xref:System.Windows.FrameworkElement.ActualHeight%2A>, salt okunurdur ve düzen işlemiyle etkileşimler tarafından belirlendiği şekilde gerçek yüksekliği raporlar.</span><span class="sxs-lookup"><span data-stu-id="b3dd7-107">A fourth property, <xref:System.Windows.FrameworkElement.ActualHeight%2A>, is read-only, and reports the actual height as determined by interactions with the layout process.</span></span>  
  
 <span data-ttu-id="b3dd7-108">Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnekler, <xref:System.Windows.Controls.Canvas>alt öğesi olarak bir <xref:System.Windows.Shapes.Rectangle> öğesi (`rect1`) çizer.</span><span class="sxs-lookup"><span data-stu-id="b3dd7-108">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples draw a <xref:System.Windows.Shapes.Rectangle> element (`rect1`) as a child of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="b3dd7-109"><xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>ve <xref:System.Windows.FrameworkElement.Height%2A>özellik değerlerini temsil eden bir dizi <xref:System.Windows.Controls.ListBox> öğesi kullanarak bir <xref:System.Windows.Shapes.Rectangle> 'ın yükseklik özelliklerini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3dd7-109">You can change the height properties of a <xref:System.Windows.Shapes.Rectangle> by using a series of <xref:System.Windows.Controls.ListBox> elements that represent the property values of <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="b3dd7-110">Bu şekilde, her bir özelliğin önceliği görsel olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b3dd7-110">In this manner, the precedence of each property is visually displayed.</span></span>  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="b3dd7-111">Aşağıdaki arka plan kod örnekleri <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> olayının harekete geçirme olaylarını işler.</span><span class="sxs-lookup"><span data-stu-id="b3dd7-111">The following code-behind examples handle the events that the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event raises.</span></span> <span data-ttu-id="b3dd7-112">Her işleyici <xref:System.Windows.Controls.ListBox>girişi alır, değeri bir <xref:System.Double>ayrıştırır ve değeri belirtilen yükseklik ile ilgili özelliğe uygular.</span><span class="sxs-lookup"><span data-stu-id="b3dd7-112">Each handler takes the input from the <xref:System.Windows.Controls.ListBox>, parses the value as a <xref:System.Double>, and applies the value to the specified height-related property.</span></span> <span data-ttu-id="b3dd7-113">Yükseklik değerleri aynı zamanda bir dizeye dönüştürülür ve çeşitli <xref:System.Windows.Controls.TextBlock> öğelerine yazılır (Bu öğelerin tanımı seçili XAML 'de gösterilmez).</span><span class="sxs-lookup"><span data-stu-id="b3dd7-113">The height values are also converted to a string and written to various <xref:System.Windows.Controls.TextBlock> elements (definition of those elements is not shown in the selected XAML).</span></span>  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 <span data-ttu-id="b3dd7-114">Tüm örnek için bkz. [Height Properties Sample](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties).</span><span class="sxs-lookup"><span data-stu-id="b3dd7-114">For the complete sample, see [Height Properties Sample](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3dd7-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3dd7-115">See also</span></span>

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.ActualHeight%2A>
- <xref:System.Windows.FrameworkElement.MaxHeight%2A>
- <xref:System.Windows.FrameworkElement.MinHeight%2A>
- <xref:System.Windows.FrameworkElement.Height%2A>
- [<span data-ttu-id="b3dd7-116">Öğenin Genişlik Özelliklerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="b3dd7-116">Set the Width Properties of an Element</span></span>](how-to-set-the-width-properties-of-an-element.md)
- [<span data-ttu-id="b3dd7-117">Panellere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b3dd7-117">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="b3dd7-118">Yükseklik özellikleri örneği</span><span class="sxs-lookup"><span data-stu-id="b3dd7-118">Height Properties Sample</span></span>](https://github.com/microsoft/WPF-Samples/tree/master/Elements/HeightProperties)
