---
title: 'Nasıl yapılır: Veri CollectionView İçindeki Nesneler Aracılığıyla Gezinme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CollectionView [WPF], navigating through objects
- data binding [WPF], navigating through objects in data CollectionView
- navigating through objects in data CollectionView [WPF]
ms.assetid: fcd37590-bce1-4ac9-8b74-3b96c7458b8a
ms.openlocfilehash: 5ca386db89dcaa66d364d2ed7169c67393cebead
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459710"
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a><span data-ttu-id="9dd98-102">Nasıl yapılır: Veri CollectionView İçindeki Nesneler Aracılığıyla Gezinme</span><span class="sxs-lookup"><span data-stu-id="9dd98-102">How to: Navigate Through the Objects in a Data CollectionView</span></span>
<span data-ttu-id="9dd98-103">Görünümler aynı veri koleksiyonunun sıralamaya, filtrelemeye veya gruplandırmaya bağlı olarak farklı şekillerde görüntülenmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="9dd98-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping.</span></span> <span data-ttu-id="9dd98-104">Görünümler aynı zamanda geçerli bir kayıt işaretçisi kavramı sağlar ve işaretçinin taşınmasını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="9dd98-104">Views also provide a current record pointer concept and enable moving the pointer.</span></span> <span data-ttu-id="9dd98-105">Bu örnek, <xref:System.Windows.Data.CollectionView> sınıfında sunulan işlevleri kullanarak, geçerli nesnenin nasıl alınacağını ve bir veri koleksiyonundaki nesneler arasında nasıl gezinilin olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9dd98-105">This example shows how to get the current object as well as navigate through the objects in a data collection using the functionality provided in the <xref:System.Windows.Data.CollectionView> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9dd98-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="9dd98-106">Example</span></span>  
 <span data-ttu-id="9dd98-107">Bu örnekte, `myCollectionView`, bağlantılı bir koleksiyon üzerinde bir görünüm olan <xref:System.Windows.Data.CollectionView> nesnesidir.</span><span class="sxs-lookup"><span data-stu-id="9dd98-107">In this example, `myCollectionView` is a <xref:System.Windows.Data.CollectionView> object that is a view over a bound collection.</span></span>  
  
 <span data-ttu-id="9dd98-108">Aşağıdaki örnekte `OnButton`, bir uygulamadaki `Previous` ve `Next` düğmeleri için bir olay işleyicisidir ve kullanıcının veri koleksiyonunda gezinmelerini sağlayan düğmelerdir.</span><span class="sxs-lookup"><span data-stu-id="9dd98-108">In the following example, `OnButton` is an event handler for the `Previous` and `Next` buttons in an application, which are buttons that allow the user to navigate the data collection.</span></span> <span data-ttu-id="9dd98-109"><xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> ve <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> özelliklerinin, <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> ve <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> uygun şekilde çağrılabilmesi için, geçerli kayıt işaretçisinin listenin başına ve sonuna gelip gelmediğini raporlamayacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9dd98-109">Note that the <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> and <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> properties report whether the current record pointer has come to the beginning and the end of the list respectively so that <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> and <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> can be called as appropriately.</span></span>  
  
 <span data-ttu-id="9dd98-110">Görünümün <xref:System.Windows.Data.CollectionView.CurrentItem%2A> özelliği, koleksiyondaki geçerli sıra öğesini döndürmek için bir `Order` olarak dönüştürüldü.</span><span class="sxs-lookup"><span data-stu-id="9dd98-110">The <xref:System.Windows.Data.CollectionView.CurrentItem%2A> property of the view is cast as an `Order` to return the current order item in the collection.</span></span>  
  
 [!code-csharp[CollectionView#OnButton](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a><span data-ttu-id="9dd98-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9dd98-111">See also</span></span>

- [<span data-ttu-id="9dd98-112">Veri Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9dd98-112">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="9dd98-113">Görünümde Verileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="9dd98-113">Sort Data in a View</span></span>](how-to-sort-data-in-a-view.md)
- [<span data-ttu-id="9dd98-114">Görünümde Veri Filtreleme</span><span class="sxs-lookup"><span data-stu-id="9dd98-114">Filter Data in a View</span></span>](how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="9dd98-115">XAML İçerisinde bir Görüntü Kullanarak Verileri Sıralama ve Gruplama</span><span class="sxs-lookup"><span data-stu-id="9dd98-115">Sort and Group Data Using a View in XAML</span></span>](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [<span data-ttu-id="9dd98-116">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="9dd98-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
