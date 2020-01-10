---
title: 'Nasıl yapılır: DataGrid Denetimine Satır Ayrıntıları Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
ms.openlocfilehash: 4db414e1907d42071f7251c390077d4020fa577c
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559683"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a><span data-ttu-id="d618c-102">Nasıl yapılır: DataGrid Denetimine Satır Ayrıntıları Ekleme</span><span class="sxs-lookup"><span data-stu-id="d618c-102">How to: Add Row Details to a DataGrid Control</span></span>
<span data-ttu-id="d618c-103"><xref:System.Windows.Controls.DataGrid> denetimini kullanırken, veri sunumunu bir satır ayrıntıları bölümü ekleyerek özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d618c-103">When using the <xref:System.Windows.Controls.DataGrid> control, you can customize the data presentation by adding a row details section.</span></span> <span data-ttu-id="d618c-104">Satır ayrıntıları bölümü eklemek, bazı verileri isteğe bağlı olarak görünür veya daraltılmış bir şablonda gruplandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d618c-104">Adding a row details section enables you to group some data in a template that is optionally visible or collapsed.</span></span> <span data-ttu-id="d618c-105">Örneğin, <xref:System.Windows.Controls.DataGrid>her satır için yalnızca verilerin özetini sunan bir <xref:System.Windows.Controls.DataGrid> satır ayrıntıları ekleyebilirsiniz, ancak kullanıcı bir satır seçtiğinde daha fazla veri alanı sunar.</span><span class="sxs-lookup"><span data-stu-id="d618c-105">For example, you can add row details to a <xref:System.Windows.Controls.DataGrid> that presents only a summary of the data for each row in the <xref:System.Windows.Controls.DataGrid>, but presents more data fields when the user selects a row.</span></span> <span data-ttu-id="d618c-106"><xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> özelliğindeki satır ayrıntıları bölümünün şablonunu tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="d618c-106">You define the template for the row details section in the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property.</span></span> <span data-ttu-id="d618c-107">Aşağıdaki çizimde, bir satır ayrıntıları Bölümü örneği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d618c-107">The following illustration shows an example of a row details section.</span></span>  
  
 <span data-ttu-id="d618c-108">![Satır ayrıntılarıyla gösterilen DataGrid](./media/ndp-rowdetails.png "NDP_RowDetails")</span><span class="sxs-lookup"><span data-stu-id="d618c-108">![DataGrid shown with row details](./media/ndp-rowdetails.png "NDP_RowDetails")</span></span>  
  
 <span data-ttu-id="d618c-109">Satır ayrıntıları şablonunu satır içi XAML veya kaynak olarak tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="d618c-109">You define the row details template as either inline XAML or as a resource.</span></span> <span data-ttu-id="d618c-110">Aşağıdaki yordamlarda her iki yaklaşım da gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d618c-110">Both approaches are shown in the following procedures.</span></span> <span data-ttu-id="d618c-111">Kaynak olarak eklenen bir veri şablonu, şablonu yeniden oluşturmadan proje genelinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d618c-111">A data template that is added as a resource can be used throughout the project without re-creating the template.</span></span> <span data-ttu-id="d618c-112">Satır içi XAML olarak eklenen bir veri şablonuna yalnızca tanımlandığı denetimden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="d618c-112">A data template that is added as inline XAML is only accessible from the control where it is defined.</span></span>  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a><span data-ttu-id="d618c-113">Satır içi XAML kullanarak satır ayrıntılarını görüntüleme</span><span class="sxs-lookup"><span data-stu-id="d618c-113">To display row details by using inline XAML</span></span>  
  
1. <span data-ttu-id="d618c-114">Veri kaynağındaki verileri görüntüleyen bir <xref:System.Windows.Controls.DataGrid> oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d618c-114">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2. <span data-ttu-id="d618c-115">İçinde <xref:System.Windows.Controls.DataGrid> öğe, Ekle bir <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> öğesi.</span><span class="sxs-lookup"><span data-stu-id="d618c-115">In the <xref:System.Windows.Controls.DataGrid> element, add a <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> element.</span></span>  
  
3. <span data-ttu-id="d618c-116">Satır ayrıntıları bölümünün görünümünü tanımlayan bir <xref:System.Windows.DataTemplate> oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d618c-116">Create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="d618c-117">Aşağıdaki XAML <xref:System.Windows.Controls.DataGrid> ve <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> satır içi olarak nasıl tanımlanacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d618c-117">The following XAML shows the <xref:System.Windows.Controls.DataGrid> and how to define the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> inline.</span></span> <span data-ttu-id="d618c-118"><xref:System.Windows.Controls.DataGrid> her satırdaki üç değeri ve satır seçildiğinde üç daha fazla değeri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d618c-118">The <xref:System.Windows.Controls.DataGrid> displays three values in each row and three more values when the row is selected.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#1](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     <span data-ttu-id="d618c-119">Aşağıdaki kod, <xref:System.Windows.Controls.DataGrid>görüntülenen verileri seçmek için kullanılan sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d618c-119">The following code shows the query that is used to select the data that is displayed in the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="d618c-120">Bu örnekte sorgu, müşteri bilgilerini içeren bir varlıktan veri seçer.</span><span class="sxs-lookup"><span data-stu-id="d618c-120">In this example, the query selects data from an entity that contains customer information.</span></span>  
  
     [!code-csharp[DataGrid_RowDetails#2](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a><span data-ttu-id="d618c-121">Kaynak kullanarak satır ayrıntılarını görüntüleme</span><span class="sxs-lookup"><span data-stu-id="d618c-121">To display row details by using a resource</span></span>  
  
1. <span data-ttu-id="d618c-122">Veri kaynağındaki verileri görüntüleyen bir <xref:System.Windows.Controls.DataGrid> oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d618c-122">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2. <span data-ttu-id="d618c-123">Kök öğeye bir <xref:System.Windows.Window> denetimi veya <xref:System.Windows.Controls.Page> denetimi gibi bir <xref:System.Windows.FrameworkElement.Resources%2A> öğesi ekleyin veya App. xaml (veya Application. xaml) dosyasındaki <xref:System.Windows.Application> sınıfına bir <xref:System.Windows.Application.Resources%2A> öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d618c-123">Add a <xref:System.Windows.FrameworkElement.Resources%2A> element to the root element, such as a <xref:System.Windows.Window> control or a <xref:System.Windows.Controls.Page> control, or add a <xref:System.Windows.Application.Resources%2A> element to the <xref:System.Windows.Application> class in the App.xaml (or Application.xaml) file.</span></span>  
  
3. <span data-ttu-id="d618c-124">Resources öğesinde, satır ayrıntıları bölümünün görünümünü tanımlayan bir <xref:System.Windows.DataTemplate> oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d618c-124">In the resources element, create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="d618c-125">Aşağıdaki XAML <xref:System.Windows.Application> sınıfında tanımlanan <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> gösterir.</span><span class="sxs-lookup"><span data-stu-id="d618c-125">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> defined in the <xref:System.Windows.Application> class.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#3](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4. <span data-ttu-id="d618c-126"><xref:System.Windows.DataTemplate>, [X:Key yönergesini](../../../desktop-wpf/xaml-services/xkey-directive.md) veri şablonunu benzersiz bir şekilde tanımlayan bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d618c-126">On the <xref:System.Windows.DataTemplate>, set the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) to a value that uniquely identifies the data template.</span></span>  
  
5. <span data-ttu-id="d618c-127"><xref:System.Windows.Controls.DataGrid> öğesinde, <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> özelliğini önceki adımlarda tanımlanan kaynak olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d618c-127">In the <xref:System.Windows.Controls.DataGrid> element, set the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property to the resource defined in the previous steps.</span></span> <span data-ttu-id="d618c-128">Kaynağı bir statik kaynak olarak atayın.</span><span class="sxs-lookup"><span data-stu-id="d618c-128">Assign the resource as a static resource.</span></span>  
  
     <span data-ttu-id="d618c-129">Aşağıdaki XAML, önceki örnekteki kaynak olarak ayarlanan <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> özelliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d618c-129">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property set to the resource from the previous example.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#4](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a><span data-ttu-id="d618c-130">Görünürlük ayarlamak ve satır ayrıntıları için yatay kaydırmayı engellemek için</span><span class="sxs-lookup"><span data-stu-id="d618c-130">To set visibility and prevent horizontal scrolling for row details</span></span>  
  
1. <span data-ttu-id="d618c-131">Gerekirse <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> özelliğini bir <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> değeri olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d618c-131">If needed, set the <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> property to a <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> value.</span></span>  
  
     <span data-ttu-id="d618c-132">Varsayılan olarak, değer <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d618c-132">By default, the value is set to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>.</span></span> <span data-ttu-id="d618c-133">Tüm satırların ayrıntılarını göstermek için <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible>, tüm satırların ayrıntılarını gizlemek için <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d618c-133">You can set it to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> to show the details for all of the rows or <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> to hide the details for all rows.</span></span>  
  
2. <span data-ttu-id="d618c-134">Gerekirse, satır ayrıntıları bölümünün yatay olarak kaymasını engellemek için <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> özelliğini `true` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d618c-134">If needed, set the <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> property to `true` to prevent the row details section from scrolling horizontally.</span></span>
