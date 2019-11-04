---
title: 'Nasıl yapılır: Görünümde Veri Filtreleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- views [WPF], filtering data
- filtering data in views [WPF]
- data binding [WPF], filtering data in views
ms.assetid: c76e8606-4cc4-45a8-9110-e2ec66dc6afd
ms.openlocfilehash: ea49897ca5e9cb6b639cf7d98ff05bd287c51761
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453475"
---
# <a name="how-to-filter-data-in-a-view"></a><span data-ttu-id="26b69-102">Nasıl yapılır: Görünümde Veri Filtreleme</span><span class="sxs-lookup"><span data-stu-id="26b69-102">How to: Filter Data in a View</span></span>
<span data-ttu-id="26b69-103">This example shows how to filter data in a view.</span><span class="sxs-lookup"><span data-stu-id="26b69-103">This example shows how to filter data in a view.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26b69-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="26b69-104">Example</span></span>  
 <span data-ttu-id="26b69-105">To create a filter, define a method that provides the filtering logic.</span><span class="sxs-lookup"><span data-stu-id="26b69-105">To create a filter, define a method that provides the filtering logic.</span></span> <span data-ttu-id="26b69-106">The method is used as a callback and accepts a parameter of type `object`.</span><span class="sxs-lookup"><span data-stu-id="26b69-106">The method is used as a callback and accepts a parameter of type `object`.</span></span> <span data-ttu-id="26b69-107">The following method returns all the `Order` objects with the `filled` property set to "No", filtering out the rest of the objects.</span><span class="sxs-lookup"><span data-stu-id="26b69-107">The following method returns all the `Order` objects with the `filled` property set to "No", filtering out the rest of the objects.</span></span>  
  
 [!code-csharp[SortFilter#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#2)]
 [!code-vb[SortFilter#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#2)]  
  
 <span data-ttu-id="26b69-108">You can then apply the filter, as shown in the following example.</span><span class="sxs-lookup"><span data-stu-id="26b69-108">You can then apply the filter, as shown in the following example.</span></span> <span data-ttu-id="26b69-109">In this example, `myCollectionView` is a <xref:System.Windows.Data.ListCollectionView> object.</span><span class="sxs-lookup"><span data-stu-id="26b69-109">In this example, `myCollectionView` is a <xref:System.Windows.Data.ListCollectionView> object.</span></span>  
  
 [!code-csharp[SortFilter#Filter](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#filter)]
 [!code-vb[SortFilter#Filter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#filter)]  
  
 <span data-ttu-id="26b69-110">To undo filtering, you can set the <xref:System.Windows.Data.CollectionView.Filter%2A> property to `null`:</span><span class="sxs-lookup"><span data-stu-id="26b69-110">To undo filtering, you can set the <xref:System.Windows.Data.CollectionView.Filter%2A> property to `null`:</span></span>  
  
 [!code-csharp[SortFilter#Unfilter](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#unfilter)]
 [!code-vb[SortFilter#Unfilter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#unfilter)]  
  
 <span data-ttu-id="26b69-111">For information about how to create or obtain a view, see [Get the Default View of a Data Collection](how-to-get-the-default-view-of-a-data-collection.md).</span><span class="sxs-lookup"><span data-stu-id="26b69-111">For information about how to create or obtain a view, see [Get the Default View of a Data Collection](how-to-get-the-default-view-of-a-data-collection.md).</span></span> <span data-ttu-id="26b69-112">For the complete example, see [Sorting and Filtering Items in a View Sample](https://go.microsoft.com/fwlink/?LinkID=160040).</span><span class="sxs-lookup"><span data-stu-id="26b69-112">For the complete example, see [Sorting and Filtering Items in a View Sample](https://go.microsoft.com/fwlink/?LinkID=160040).</span></span>  
  
 <span data-ttu-id="26b69-113">If your view object comes from a <xref:System.Windows.Data.CollectionViewSource> object, you apply filtering logic by setting an event handler for the <xref:System.Windows.Data.CollectionViewSource.Filter> event.</span><span class="sxs-lookup"><span data-stu-id="26b69-113">If your view object comes from a <xref:System.Windows.Data.CollectionViewSource> object, you apply filtering logic by setting an event handler for the <xref:System.Windows.Data.CollectionViewSource.Filter> event.</span></span> <span data-ttu-id="26b69-114">In the following example, `listingDataView` is an instance of <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="26b69-114">In the following example, `listingDataView` is an instance of <xref:System.Windows.Data.CollectionViewSource>.</span></span>  
  
 [!code-csharp[DataBindingLab#10](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 <span data-ttu-id="26b69-115">The following shows the implementation of the example `ShowOnlyBargainsFilter` filter event handler.</span><span class="sxs-lookup"><span data-stu-id="26b69-115">The following shows the implementation of the example `ShowOnlyBargainsFilter` filter event handler.</span></span> <span data-ttu-id="26b69-116">This event handler uses the <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> property to filter out `AuctionItem` objects that have a `CurrentPrice` of $25 or greater.</span><span class="sxs-lookup"><span data-stu-id="26b69-116">This event handler uses the <xref:System.Windows.Data.FilterEventArgs.Accepted%2A> property to filter out `AuctionItem` objects that have a `CurrentPrice` of $25 or greater.</span></span>  
  
 [!code-csharp[DataBindingLab#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="26b69-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26b69-117">See also</span></span>

- <xref:System.Windows.Data.CollectionView.CanFilter%2A>
- <xref:System.Windows.Data.BindingListCollectionView.CustomFilter%2A>
- [<span data-ttu-id="26b69-118">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="26b69-118">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="26b69-119">Görünümde Verileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="26b69-119">Sort Data in a View</span></span>](how-to-sort-data-in-a-view.md)
- [<span data-ttu-id="26b69-120">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="26b69-120">How-to Topics</span></span>](data-binding-how-to-topics.md)
