---
title: DataGrid denetimini bir veri kaynağına bağlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- bound controls [Windows Forms], DataGrid control
- Windows Forms controls, data binding
- bound controls [Windows Forms]
- data-bound controls [Windows Forms], DataGrid
ms.assetid: 128cdb07-dfd3-4d60-9d6a-902847667c36
ms.openlocfilehash: 2634a6bd8ace36bcf7a49120162474a8c04b2b83
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746693"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a><span data-ttu-id="4db1b-102">Nasıl yapılır: Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama</span><span class="sxs-lookup"><span data-stu-id="4db1b-102">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>
> [!NOTE]
> <span data-ttu-id="4db1b-103"><xref:System.Windows.Forms.DataGridView> denetimi yerini alır ve <xref:System.Windows.Forms.DataGrid> denetimine işlevsellik ekler; Ancak, ' yi seçerseniz, <xref:System.Windows.Forms.DataGrid> denetimi hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur.</span><span class="sxs-lookup"><span data-stu-id="4db1b-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="4db1b-104">Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="4db1b-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="4db1b-105">Windows Forms <xref:System.Windows.Forms.DataGrid> denetimi, bir veri kaynağından bilgileri görüntüleyecek şekilde özel olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4db1b-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="4db1b-106"><xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemini çağırarak denetimi çalışma zamanında bağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="4db1b-106">You bind the control at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="4db1b-107">Çeşitli veri kaynaklarından veri görüntüleyebilirsiniz, ancak en genel kaynaklar veri kümeleri ve veri görünümleridir.</span><span class="sxs-lookup"><span data-stu-id="4db1b-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a><span data-ttu-id="4db1b-108">DataGrid denetimini programlama yoluyla veri bağlama</span><span class="sxs-lookup"><span data-stu-id="4db1b-108">To data-bind the DataGrid control programmatically</span></span>  
  
1. <span data-ttu-id="4db1b-109">Veri kümesini dolduracak kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="4db1b-109">Write code to fill the dataset.</span></span>  
  
     <span data-ttu-id="4db1b-110">Veri kaynağı bir veri kümesi veya veri kümesi tablosuna dayalı bir veri görünüminiyorsa, veri kümesini dolduracak şekilde forma kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4db1b-110">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>  
  
     <span data-ttu-id="4db1b-111">Kullandığınız tam kod, veri kümesinin veri alılabileceği yere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="4db1b-111">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="4db1b-112">Veri kümesi doğrudan bir veritabanından doldurulursa, genellikle `DsCategories1`adlı bir veri kümesini dolduran aşağıdaki örnekte olduğu gibi bir veri bağdaştırıcısının `Fill` yöntemini çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4db1b-112">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following example, which populates a dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     <span data-ttu-id="4db1b-113">Veri kümesi bir XML Web hizmetinden doldurulduysa, genellikle kodunuzda hizmetin bir örneğini oluşturun ve ardından bir veri kümesi döndürmek için yöntemlerinden birini çağırın.</span><span class="sxs-lookup"><span data-stu-id="4db1b-113">If the dataset is being filled from an XML Web service, you typically create an instance of the service in your code and then call one of its methods to return a dataset.</span></span> <span data-ttu-id="4db1b-114">Daha sonra veri kümesini XML Web hizmetinden yerel veri kümeniz ile birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4db1b-114">You then merge the dataset from the XML Web service into your local dataset.</span></span> <span data-ttu-id="4db1b-115">Aşağıdaki örnek, `CategoriesService`adlı bir XML Web hizmetinin örneğini nasıl oluşturabileceğiniz, `GetCategories` metodunu çağırabilmeniz ve elde edilen veri kümesini `DsCategories1`adlı yerel bir veri kümesinde birleştirebilmeniz gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="4db1b-115">The following example shows how you can create an instance of an XML Web service called `CategoriesService`, call its `GetCategories` method, and merge the resulting dataset into a local dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    Dim ws As New MyProject.localhost.CategoriesService()  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials  
    DsCategories1.Merge(ws.GetCategories())  
    ```  
  
    ```csharp  
    MyProject.localhost.CategoriesService ws = new MyProject.localhost.CategoriesService();  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials;  
    DsCategories1.Merge(ws.GetCategories());  
    ```  
  
    ```cpp  
    MyProject::localhost::CategoriesService^ ws =   
       new MyProject::localhost::CategoriesService();  
    ws->Credentials = System::Net::CredentialCache::DefaultCredentials;  
    dsCategories1->Merge(ws->GetCategories());  
    ```  
  
2. <span data-ttu-id="4db1b-116"><xref:System.Windows.Forms.DataGrid> denetiminin <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodunu çağırın, veri kaynağını ve bir veri üyesini geçirerek.</span><span class="sxs-lookup"><span data-stu-id="4db1b-116">Call the <xref:System.Windows.Forms.DataGrid> control's <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method, passing it the data source and a data member.</span></span> <span data-ttu-id="4db1b-117">Bir veri üyesini açıkça geçirmeniz gerekmiyorsa boş bir dize geçirin.</span><span class="sxs-lookup"><span data-stu-id="4db1b-117">If you do not need to explicitly pass a data member, pass an empty string.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4db1b-118">Kılavuzu ilk kez bağlıyorsanız, denetimin <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliklerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4db1b-118">If you are binding the grid for the first time, you can set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties.</span></span> <span data-ttu-id="4db1b-119">Ancak, ayarlandıklarında bu özellikleri sıfırlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="4db1b-119">However, you cannot reset these properties once they have been set.</span></span> <span data-ttu-id="4db1b-120">Bu nedenle, <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemini her zaman kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="4db1b-120">Therefore, it is recommended that you always use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span>  
  
     <span data-ttu-id="4db1b-121">Aşağıdaki örnek, `DsCustomers1`adlı bir veri kümesindeki Customers tablosuna programlı bir şekilde nasıl bağlayacağınız gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="4db1b-121">The following example shows how you can programmatically bind to the Customers table in a dataset called `DsCustomers1`:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     <span data-ttu-id="4db1b-122">Veri kümesindeki tek tablo müşteriler tablosu ise bu şekilde kılavuza bağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4db1b-122">If the Customers table is the only table in the dataset, you could alternatively bind the grid this way:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. <span data-ttu-id="4db1b-123">Seçim Kılavuza uygun tablo stillerini ve sütun stillerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4db1b-123">(Optional) Add the appropriate table styles and column styles to the grid.</span></span> <span data-ttu-id="4db1b-124">Tablo stili yoksa, tabloyu görürsünüz, ancak en az biçimlendirme ile ve tüm sütunları görünür olur.</span><span class="sxs-lookup"><span data-stu-id="4db1b-124">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4db1b-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4db1b-125">See also</span></span>

- [<span data-ttu-id="4db1b-126">DataGrid Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4db1b-126">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="4db1b-127">Nasıl yapılır: Windows Forms DataGrid Denetimine Tablo ve Sütun Ekleme</span><span class="sxs-lookup"><span data-stu-id="4db1b-127">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="4db1b-128">DataGrid Denetimi</span><span class="sxs-lookup"><span data-stu-id="4db1b-128">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="4db1b-129">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="4db1b-129">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
