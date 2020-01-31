---
title: Tasarımcı kullanarak DataGrid denetimini bir veri kaynağına bağlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- Windows Forms controls, data binding
- bound controls [Windows Forms]
ms.assetid: 4e96e3d0-b1cc-4de1-8774-bc9970ec4554
ms.openlocfilehash: cc0a74eca40e34f06b065980d25d922b919b0c3c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744092"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a><span data-ttu-id="76fd4-102">Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGrid Denetimini Veri Kaynağına Bağlama</span><span class="sxs-lookup"><span data-stu-id="76fd4-102">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>

> [!NOTE]
> <span data-ttu-id="76fd4-103"><xref:System.Windows.Forms.DataGridView> denetimi yerini alır ve <xref:System.Windows.Forms.DataGrid> denetimine işlevsellik ekler; Ancak, ' yi seçerseniz, <xref:System.Windows.Forms.DataGrid> denetimi hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur.</span><span class="sxs-lookup"><span data-stu-id="76fd4-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="76fd4-104">Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="76fd4-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>

 <span data-ttu-id="76fd4-105">Windows Forms <xref:System.Windows.Forms.DataGrid> denetimi, bir veri kaynağından bilgileri görüntüleyecek şekilde özel olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="76fd4-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="76fd4-106"><xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliklerini ayarlayarak veya <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemini çağırarak çalışma zamanında denetimi tasarım zamanında bağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="76fd4-106">You bind the control at design time by setting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties, or at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="76fd4-107">Çeşitli veri kaynaklarından veri görüntüleyebilirsiniz, ancak en genel kaynaklar veri kümeleri ve veri görünümleridir.</span><span class="sxs-lookup"><span data-stu-id="76fd4-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>

 <span data-ttu-id="76fd4-108">Veri kaynağı tasarım zamanında kullanılabiliyorsa — Örneğin, form bir veri kümesinin veya bir veri görünümünün örneğini içeriyorsa — tasarım zamanında Kılavuzu veri kaynağına bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76fd4-108">If the data source is available at design time—for example, if the form contains an instance of a dataset or a data view—you can bind the grid to the data source at design time.</span></span> <span data-ttu-id="76fd4-109">Ardından, verilerin kılavuzda nasıl görüneceğine ilişkin önizleme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76fd4-109">You can then preview what the data will look like in the grid.</span></span>

 <span data-ttu-id="76fd4-110">Ayrıca, çalışma zamanında Kılavuzu programlı bir şekilde bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76fd4-110">You can also bind the grid programmatically, at run time.</span></span> <span data-ttu-id="76fd4-111">Bu, çalışma zamanında aldığınız bilgilere göre bir veri kaynağı ayarlamak istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="76fd4-111">This is useful when you want to set a data source based on information you get at run time.</span></span> <span data-ttu-id="76fd4-112">Örneğin, uygulama, kullanıcının görüntülenecek tablonun adını belirtmesini sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="76fd4-112">For example, the application might let the user specify the name of a table to view.</span></span> <span data-ttu-id="76fd4-113">Veri kaynağının tasarım zamanında bulunmadığı durumlarda da gereklidir.</span><span class="sxs-lookup"><span data-stu-id="76fd4-113">It is also necessary in situations where the data source does not exist at design time.</span></span> <span data-ttu-id="76fd4-114">Bu, diziler, koleksiyonlar, türsüz veri kümeleri ve veri okuyucuları gibi veri kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="76fd4-114">This includes data sources such as arrays, collections, untyped datasets, and data readers.</span></span>

 <span data-ttu-id="76fd4-115">Aşağıdaki yordam, bir <xref:System.Windows.Forms.DataGrid> denetimi içeren bir form ile **Windows uygulama** projesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="76fd4-115">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="76fd4-116">Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma Windows Forms uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="76fd4-116">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span> <span data-ttu-id="76fd4-117">Visual Studio 2005 ' de, <xref:System.Windows.Forms.DataGrid> denetimi **araç kutusunda** varsayılan olarak değildir.</span><span class="sxs-lookup"><span data-stu-id="76fd4-117">In Visual Studio 2005, the <xref:System.Windows.Forms.DataGrid> control is not in the **Toolbox** by default.</span></span> <span data-ttu-id="76fd4-118">Ekleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: öğeleri ekleme araç kutusu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="76fd4-118">For information about adding it, see [How to: Add Items to the Toolbox](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).</span></span> <span data-ttu-id="76fd4-119">Ayrıca, Visual Studio 2005 ' de tasarım zamanı veri bağlama için **veri kaynakları** penceresini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76fd4-119">Additionally in Visual Studio 2005, you can use the **Data Sources** window for design-time data binding.</span></span> <span data-ttu-id="76fd4-120">Daha fazla bilgi için bkz. [Visual Studio 'da verileri denetimlere bağlama](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="76fd4-120">For more information see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span></span>

## <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a><span data-ttu-id="76fd4-121">DataGrid denetimini tasarımcıda tek bir tabloya veri bağlamak için</span><span class="sxs-lookup"><span data-stu-id="76fd4-121">To data-bind the DataGrid control to a single table in the designer</span></span>

1. <span data-ttu-id="76fd4-122">Denetimin <xref:System.Windows.Forms.DataGrid.DataSource%2A> özelliğini, bağlamak istediğiniz veri öğelerini içeren nesne olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="76fd4-122">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>

2. <span data-ttu-id="76fd4-123">Veri kaynağı bir veri kümesi ise, <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliğini bağlanacak tablonun adı olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="76fd4-123">If the data source is a dataset, set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the table to bind to.</span></span>

3. <span data-ttu-id="76fd4-124">Veri kaynağı bir veri kümesi veya veri kümesi tablosuna dayalı bir veri görünüminiyorsa, veri kümesini dolduracak şekilde forma kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="76fd4-124">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>

     <span data-ttu-id="76fd4-125">Kullandığınız tam kod, veri kümesinin veri alılabileceği yere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="76fd4-125">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="76fd4-126">Veri kümesi doğrudan bir veritabanından doldurulursa, genellikle bir veri bağdaştırıcısının `Fill` yöntemini, aşağıdaki kod örneğinde olduğu gibi, `DsCategories1`olarak adlandırılan bir veri kümesini dolduran şekilde çağırır:</span><span class="sxs-lookup"><span data-stu-id="76fd4-126">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following code example, which populates a dataset called `DsCategories1`:</span></span>

    ```vb
    sqlDataAdapter1.Fill(DsCategories1)
    ```

    ```csharp
    sqlDataAdapter1.Fill(DsCategories1);
    ```

    ```cpp
    sqlDataAdapter1->Fill(dsCategories1);
    ```

4. <span data-ttu-id="76fd4-127">Seçim Kılavuza uygun tablo stillerini ve sütun stillerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="76fd4-127">(Optional) Add the appropriate table styles and column styles to the grid.</span></span>

     <span data-ttu-id="76fd4-128">Tablo stili yoksa, tabloyu görürsünüz, ancak en az biçimlendirme ile ve tüm sütunları görünür olur.</span><span class="sxs-lookup"><span data-stu-id="76fd4-128">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>

## <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a><span data-ttu-id="76fd4-129">DataGrid denetimini tasarımcıda veri kümesindeki birden çok tabloya bağlamak için</span><span class="sxs-lookup"><span data-stu-id="76fd4-129">To data-bind the DataGrid control to multiple tables in a dataset in the designer</span></span>

1. <span data-ttu-id="76fd4-130">Denetimin <xref:System.Windows.Forms.DataGrid.DataSource%2A> özelliğini, bağlamak istediğiniz veri öğelerini içeren nesne olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="76fd4-130">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>

2. <span data-ttu-id="76fd4-131">Veri kümesi ilgili tabloları içeriyorsa (yani bir ilişki nesnesi içeriyorsa) <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliğini üst tablonun adı olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="76fd4-131">If the dataset contains related tables (that is, if it contains a relation object), set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the parent table.</span></span>

3. <span data-ttu-id="76fd4-132">Veri kümesini dolduracak kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="76fd4-132">Write code to fill the dataset.</span></span>

## <a name="see-also"></a><span data-ttu-id="76fd4-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76fd4-133">See also</span></span>

- [<span data-ttu-id="76fd4-134">DataGrid Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="76fd4-134">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="76fd4-135">Nasıl yapılır: Windows Forms DataGrid Denetimine Tablo ve Sütun Ekleme</span><span class="sxs-lookup"><span data-stu-id="76fd4-135">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="76fd4-136">DataGrid Denetimi</span><span class="sxs-lookup"><span data-stu-id="76fd4-136">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="76fd4-137">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="76fd4-137">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="76fd4-138">Visual Studio'da verilere erişime</span><span class="sxs-lookup"><span data-stu-id="76fd4-138">Accessing data in Visual Studio</span></span>](/visualstudio/data-tools/accessing-data-in-visual-studio)
