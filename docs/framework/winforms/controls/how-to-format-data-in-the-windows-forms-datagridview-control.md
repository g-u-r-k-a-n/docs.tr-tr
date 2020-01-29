---
title: DataGridView denetiminde verileri biçimlendirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in DataGridView control
- data grids [Windows Forms], enabling wordwrap
- currency values [Windows Forms], formatting in data grids
- data grids [Windows Forms], currency values
- data grids [Windows Forms], formatting data
- data grids [Windows Forms], text alignment
- data grids [Windows Forms], date values
- cells [Windows Forms], text alignment
ms.assetid: 8c33543c-9c08-4636-a65a-fdf714a529b7
ms.openlocfilehash: 9ee2869cf4085b5acfdf1f8c440151be506dbe3e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736778"
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="7742f-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Verileri Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="7742f-102">How to: Format Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="7742f-103">Aşağıdaki yordamlarda, bir <xref:System.Windows.Forms.DataGridView> denetiminin <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> özelliğini ve bir denetimdeki belirli sütunları kullanarak hücre değerlerinin temel biçimlendirilmesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7742f-103">The following procedures demonstrate basic formatting of cell values using the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> property of a <xref:System.Windows.Forms.DataGridView> control and of specific columns in a control.</span></span> <span data-ttu-id="7742f-104">Gelişmiş veri biçimlendirme hakkında daha fazla bilgi için, bkz. [nasıl yapılır: veri biçimlendirmeyi özelleştirme Windows Forms DataGridView denetiminde](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="7742f-104">For information about advanced data formatting, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-format-currency-and-date-values"></a><span data-ttu-id="7742f-105">Para birimi ve tarih değerlerini biçimlendirmek için</span><span class="sxs-lookup"><span data-stu-id="7742f-105">To format currency and date values</span></span>  
  
- <span data-ttu-id="7742f-106">Bir <xref:System.Windows.Forms.DataGridViewCellStyle><xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7742f-106">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="7742f-107">Aşağıdaki kod örneği, sütunların <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> özelliğini kullanarak belirli sütunların biçimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7742f-107">The following code example sets the format for specific columns using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the columns.</span></span> <span data-ttu-id="7742f-108">`UnitPrice` sütunundaki değerler, parantez içine alınmış negatif değerlerle birlikte geçerli kültüre özgü para birimi biçiminde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7742f-108">Values in the `UnitPrice` column appear in the current culture-specific currency format, with negative values surrounded by parentheses.</span></span> <span data-ttu-id="7742f-109">`ShipDate` sütunundaki değerler, geçerli kültüre özgü kısa tarih biçiminde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7742f-109">Values in the `ShipDate` column appear in the current culture-specific short date format.</span></span> <span data-ttu-id="7742f-110"><xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> değerler hakkında daha fazla bilgi için bkz. [biçimlendirme türleri](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="7742f-110">For more information about <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> values, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a><span data-ttu-id="7742f-111">Null veritabanı değerlerinin görüntülenmesini özelleştirmek için</span><span class="sxs-lookup"><span data-stu-id="7742f-111">To customize the display of null database values</span></span>  
  
- <span data-ttu-id="7742f-112">Bir <xref:System.Windows.Forms.DataGridViewCellStyle><xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7742f-112">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="7742f-113">Aşağıdaki kod örneği, <xref:System.DBNull.Value?displayProperty=nameWithType>eşit değerler içeren tüm hücrelerde "No entry" göstermek için <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7742f-113">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to display "no entry" in all cells containing values equal to <xref:System.DBNull.Value?displayProperty=nameWithType>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a><span data-ttu-id="7742f-114">Metin tabanlı hücrelerde WordWrap özelliğini etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="7742f-114">To enable wordwrap in text-based cells</span></span>  
  
- <span data-ttu-id="7742f-115">Bir <xref:System.Windows.Forms.DataGridViewCellStyle> <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> özelliğini <xref:System.Windows.Forms.DataGridViewTriState> sabit listesi değerlerinden birine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7742f-115">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewTriState> enumeration values.</span></span> <span data-ttu-id="7742f-116">Aşağıdaki kod örneği, tüm denetimin Wrap modunu ayarlamak için <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7742f-116">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set the wrap mode for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a><span data-ttu-id="7742f-117">DataGridView hücrelerinin metin hizalamasını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="7742f-117">To specify the text alignment of DataGridView cells</span></span>  
  
- <span data-ttu-id="7742f-118">Bir <xref:System.Windows.Forms.DataGridViewCellStyle> <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> özelliğini <xref:System.Windows.Forms.DataGridViewContentAlignment> sabit listesi değerlerinden birine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7742f-118">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewContentAlignment> enumeration values.</span></span> <span data-ttu-id="7742f-119">Aşağıdaki kod örneği, sütunun <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> özelliğini kullanarak belirli bir sütunun hizalamasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7742f-119">The following code example sets the alignment for a specific column using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the column.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a><span data-ttu-id="7742f-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="7742f-120">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7742f-121">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="7742f-121">Compiling the Code</span></span>  
 <span data-ttu-id="7742f-122">Bu örneklerde şunlar gerekir:</span><span class="sxs-lookup"><span data-stu-id="7742f-122">These examples require:</span></span>  
  
- <span data-ttu-id="7742f-123">`UnitPrice`adlı bir sütun, `ShipDate`adlı bir sütun ve `CustomerName`adlı bir sütun içeren `dataGridView1` adlı <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="7742f-123">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `UnitPrice`, a column named `ShipDate`, and a column named `CustomerName`.</span></span>  
  
- <span data-ttu-id="7742f-124"><xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="7742f-124">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="7742f-125">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="7742f-125">Robust Programming</span></span>  
 <span data-ttu-id="7742f-126">En yüksek ölçeklenebilirlik için, her bir öğe için stil özelliklerini ayrı ayrı ayarlamak yerine birden çok satır, sütun veya hücre arasında <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri paylaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7742f-126">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="7742f-127">Daha fazla bilgi için bkz. [Windows Forms DataGridView denetimini ölçeklendirme Için En Iyi uygulamalar](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="7742f-127">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7742f-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7742f-128">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [<span data-ttu-id="7742f-129">Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller</span><span class="sxs-lookup"><span data-stu-id="7742f-129">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="7742f-130">Windows Forms DataGridView Denetimindeki Hücre Stilleri</span><span class="sxs-lookup"><span data-stu-id="7742f-130">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="7742f-131">Windows Forms DataGridView Denetiminde Veri Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="7742f-131">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="7742f-132">Nasıl yapılır: Windows Forms DataGridView Denetiminde Veri Biçimlendirmeyi Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="7742f-132">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="7742f-133">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="7742f-133">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
