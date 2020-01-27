---
title: DataGridView denetiminde yazı tipi ve renk stillerini ayarlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- data grids [Windows Forms], customizing cells
- data grids [Windows Forms], font styles
- data grids [Windows Forms], color styles
ms.assetid: 588f2c57-d963-41b1-9c1d-d02d71818113
ms.openlocfilehash: f1ee9131cfc0b28a5f6263dcd6254d27a092cc62
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746750"
---
# <a name="how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="c9341-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Yazı Tipi ve Renk Stillerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="c9341-102">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="c9341-103"><xref:System.Windows.Forms.DataGridViewCellStyle> sınıfının özelliklerini ayarlayarak <xref:System.Windows.Forms.DataGridView> denetim içindeki hücrelerin görsel görünümünü belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9341-103">You can specify the visual appearance of cells within a <xref:System.Windows.Forms.DataGridView> control by setting properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> class.</span></span> <span data-ttu-id="c9341-104">Bu sınıfın örneklerini <xref:System.Windows.Forms.DataGridView> sınıfının ve yardımcı sınıflarının çeşitli özelliklerinden alabilir veya bu özelliklere atanmak üzere <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri örnekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9341-104">You can retrieve instances of this class from various properties of the <xref:System.Windows.Forms.DataGridView> class and its companion classes, or you can instantiate <xref:System.Windows.Forms.DataGridViewCellStyle> objects for assignment to these properties.</span></span>  
  
 <span data-ttu-id="c9341-105">Aşağıdaki yordamlarda <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> özelliğini kullanarak hücre görünümünün temel özelleştirmesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c9341-105">The following procedures demonstrate basic customization of cell appearance using the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> property.</span></span> <span data-ttu-id="c9341-106">Denetimdeki her hücre, sütun, satır veya hücre düzeyinde geçersiz kılınmadıkça, bu özellik ile belirtilen stilleri devralır.</span><span class="sxs-lookup"><span data-stu-id="c9341-106">Every cell in the control inherits the styles specified through this property unless they are overridden at the column, row, or cell level.</span></span> <span data-ttu-id="c9341-107">Stil devralmayla ilgili bir örnek için bkz. [nasıl yapılır: Windows Forms DataGridView denetimi Için varsayılan hücre stillerini ayarlama](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="c9341-107">For an example of style inheritance, see [How to: Set Default Cell Styles for the Windows Forms DataGridView Control](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span></span> <span data-ttu-id="c9341-108"><xref:System.Windows.Forms.DataGridViewCellStyle> sınıfının ek kullanımları hakkında daha fazla bilgi için Ayrıca bkz. bölümünde listelenen konulara bakın.</span><span class="sxs-lookup"><span data-stu-id="c9341-108">For information about additional uses of the <xref:System.Windows.Forms.DataGridViewCellStyle> class, see the topics listed in the See Also section.</span></span>  
  
 <span data-ttu-id="c9341-109">Visual Studio 'da bu görev için kapsamlı destek vardır.</span><span class="sxs-lookup"><span data-stu-id="c9341-109">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="c9341-110">Ayrıca bkz. [nasıl yapılır: Tasarımcıyı kullanarak Windows Forms DataGridView denetimi Için varsayılan hücre stillerini ve veri biçimlerini ayarlama](default-cell-styles-datagridview.md).</span><span class="sxs-lookup"><span data-stu-id="c9341-110">Also see [How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer](default-cell-styles-datagridview.md).</span></span>  
  
### <a name="to-specify-the-font-used-by-datagridview-cells"></a><span data-ttu-id="c9341-111">DataGridView hücreleri tarafından kullanılan yazı tipini belirtmek için</span><span class="sxs-lookup"><span data-stu-id="c9341-111">To specify the font used by DataGridView cells</span></span>  
  
- <span data-ttu-id="c9341-112">Bir <xref:System.Windows.Forms.DataGridViewCellStyle><xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c9341-112">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="c9341-113">Aşağıdaki kod örneği, tüm denetimin yazı tipini ayarlamak için <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c9341-113">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set the font for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#101](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#101)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#101](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#101)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-datagridview-cells"></a><span data-ttu-id="c9341-114">DataGridView hücrelerinin ön plan ve arka plan renklerini belirtmek için</span><span class="sxs-lookup"><span data-stu-id="c9341-114">To specify the foreground and background colors of DataGridView cells</span></span>  
  
- <span data-ttu-id="c9341-115"><xref:System.Windows.Forms.DataGridViewCellStyle><xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> ve <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c9341-115">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> and <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> properties of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="c9341-116">Aşağıdaki kod örneği, tüm denetimin bu stillerini ayarlamak için <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c9341-116">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set these styles for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#102](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#102)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#102](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#102)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-selected-datagridview-cells"></a><span data-ttu-id="c9341-117">Seçili DataGridView hücrelerinin ön plan ve arka plan renklerini belirtmek için</span><span class="sxs-lookup"><span data-stu-id="c9341-117">To specify the foreground and background colors of selected DataGridView cells</span></span>  
  
- <span data-ttu-id="c9341-118"><xref:System.Windows.Forms.DataGridViewCellStyle><xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A> ve <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c9341-118">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A> and <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> properties of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="c9341-119">Aşağıdaki kod örneği, tüm denetimin bu stillerini ayarlamak için <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c9341-119">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set these styles for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#103](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#103)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#103](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#103)]  
  
## <a name="example"></a><span data-ttu-id="c9341-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="c9341-120">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c9341-121">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="c9341-121">Compiling the Code</span></span>  
 <span data-ttu-id="c9341-122">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="c9341-122">This example requires:</span></span>  
  
- <span data-ttu-id="c9341-123">`dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="c9341-123">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="c9341-124"><xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="c9341-124">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c9341-125">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="c9341-125">Robust Programming</span></span>  
 <span data-ttu-id="c9341-126">En yüksek ölçeklenebilirlik için, her bir öğe için stil özelliklerini ayrı ayrı ayarlamak yerine, <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri birden çok satırda, sütunda veya aynı stilleri kullanan hücrelerde paylaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9341-126">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="c9341-127">Daha fazla bilgi için bkz. [Windows Forms DataGridView denetimini ölçeklendirme Için En Iyi uygulamalar](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="c9341-127">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9341-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9341-128">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [<span data-ttu-id="c9341-129">Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller</span><span class="sxs-lookup"><span data-stu-id="c9341-129">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="c9341-130">Windows Forms DataGridView Denetimindeki Hücre Stilleri</span><span class="sxs-lookup"><span data-stu-id="c9341-130">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
