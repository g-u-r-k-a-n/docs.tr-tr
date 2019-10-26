---
title: "Nasıl yapılır: XML Sorgu Sonuçları için XDocument, XElement veya LINQ'ya Bağlama"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to XDocument
- data binding [WPF], binding to XElement
ms.assetid: 6a629a49-fe1c-465d-b76a-3dcbf4307b64
ms.openlocfilehash: 070f67f30613d4522a48e08fd1c208fbe5887525
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920120"
---
# <a name="how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results"></a><span data-ttu-id="ce272-102">Nasıl yapılır: XML Sorgu Sonuçları için XDocument, XElement veya LINQ'ya Bağlama</span><span class="sxs-lookup"><span data-stu-id="ce272-102">How to: Bind to XDocument, XElement, or LINQ for XML Query Results</span></span>

<span data-ttu-id="ce272-103">Bu örnek, <xref:System.Xml.Linq.XDocument>kullanarak bir <xref:System.Windows.Controls.ItemsControl> XML verilerinin nasıl bağlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce272-103">This example demonstrates how to bind XML data to an <xref:System.Windows.Controls.ItemsControl> using <xref:System.Xml.Linq.XDocument>.</span></span>

## <a name="example"></a><span data-ttu-id="ce272-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ce272-104">Example</span></span>

<span data-ttu-id="ce272-105">Aşağıdaki XAML kodu bir <xref:System.Windows.Controls.ItemsControl> tanımlar ve `http://planetsNS` XML ad alanında `Planet` türündeki veriler için bir veri şablonu içerir.</span><span class="sxs-lookup"><span data-stu-id="ce272-105">The following XAML code defines an <xref:System.Windows.Controls.ItemsControl> and includes a data template for data of type `Planet` in the `http://planetsNS` XML namespace.</span></span> <span data-ttu-id="ce272-106">Bir ad alanını kaplayan bir XML veri türü, küme ayracı içine ad alanını içermelidir ve bir XAML biçimlendirme uzantısının görünebileceği yerde görünürse, ad alanından önce ayraç kaçış dizisi ile önce gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="ce272-106">An XML data type that occupies a namespace must include the namespace in braces, and if it appears where a XAML markup extension could appear, it must precede the namespace with a brace escape sequence.</span></span> <span data-ttu-id="ce272-107">Bu kod, <xref:System.Xml.Linq.XElement> sınıfının <xref:System.Xml.Linq.XContainer.Element%2A> ve <xref:System.Xml.Linq.XElement.Attribute%2A> yöntemlerine karşılık gelen dinamik özelliklere bağlanır.</span><span class="sxs-lookup"><span data-stu-id="ce272-107">This code binds to dynamic properties that correspond to the <xref:System.Xml.Linq.XContainer.Element%2A> and <xref:System.Xml.Linq.XElement.Attribute%2A> methods of the <xref:System.Xml.Linq.XElement> class.</span></span> <span data-ttu-id="ce272-108">Dinamik özellikler, XAML 'nin yöntemlerin adlarını paylaşan dinamik özelliklere bağlamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce272-108">Dynamic properties enable XAML to bind to dynamic properties that share the names of methods.</span></span> <span data-ttu-id="ce272-109">Daha fazla bilgi için bkz. [LINQ to XML dinamik özellikler](linq-to-xml-dynamic-properties.md).</span><span class="sxs-lookup"><span data-stu-id="ce272-109">To learn more, see [LINQ to XML dynamic properties](linq-to-xml-dynamic-properties.md).</span></span> <span data-ttu-id="ce272-110">XML için varsayılan ad alanı bildiriminin öznitelik adlarına nasıl uygulanmadığından dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="ce272-110">Notice how the default namespace declaration for the XML does not apply to attribute names.</span></span>

[!code-xaml[XLinqExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]
[!code-xaml[XLinqExample#ItemsControl](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]

<span data-ttu-id="ce272-111">Aşağıdaki C# kod<xref:System.Xml.Linq.XDocument.Load%2A>çağırır ve yığın paneli veri BAĞLAMıNı`http://planetsNS`XML ad alanındaki`SolarSystemPlanets`adlı öğenin tüm alt öğeleri olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ce272-111">The following C# code calls <xref:System.Xml.Linq.XDocument.Load%2A> and sets the stack panel data context to all subelements of the element named `SolarSystemPlanets` in the `http://planetsNS` XML namespace.</span></span>

[!code-csharp[XLinqExample#LoadDCFromFile](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
[!code-vb[XLinqExample#LoadDCFromFile](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]

<span data-ttu-id="ce272-112">XML verileri, <xref:System.Windows.Data.ObjectDataProvider>kullanarak bir XAML kaynağı olarak depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="ce272-112">XML data can be stored as a XAML resource using <xref:System.Windows.Data.ObjectDataProvider>.</span></span> <span data-ttu-id="ce272-113">Tüm örnek için bkz [. L2DBForm. xaml kaynak kodu](l2dbform-xaml-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="ce272-113">For a complete example, see  [L2DBForm.xaml source code](l2dbform-xaml-source-code.md).</span></span> <span data-ttu-id="ce272-114">Aşağıdaki örnek, kodun veri bağlamını bir nesne kaynağına nasıl ayarlayagösterdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce272-114">The following sample shows how code can set the data context to an object resource.</span></span>

[!code-csharp[XLinqExample#LoadDCFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
[!code-vb[XLinqExample#LoadDCFromXAML](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]

<span data-ttu-id="ce272-115"><xref:System.Xml.Linq.XContainer.Element%2A> ve <xref:System.Xml.Linq.XElement.Attribute%2A> eşlenen dinamik özellikler XAML içinde esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce272-115">The dynamic properties that map to <xref:System.Xml.Linq.XContainer.Element%2A> and <xref:System.Xml.Linq.XElement.Attribute%2A> provide flexibility within XAML.</span></span> <span data-ttu-id="ce272-116">Kodunuz Ayrıca bir LINQ for XML sorgusu sonuçlarına bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="ce272-116">Your code can also bind to the results of a LINQ for XML query.</span></span> <span data-ttu-id="ce272-117">Bu örnek, bir öğe değeri tarafından sıralanan sorgu sonuçlarına bağlanır.</span><span class="sxs-lookup"><span data-stu-id="ce272-117">This example binds to query results ordered by an element value.</span></span>

[!code-csharp[XLinqExample#BindToResults](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
[!code-vb[XLinqExample#BindToResults](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]

## <a name="see-also"></a><span data-ttu-id="ce272-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce272-118">See also</span></span>

- [<span data-ttu-id="ce272-119">Bağlama Kaynaklarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ce272-119">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="ce272-120">LINQ to XML ile WPF Verilerini Bağlamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ce272-120">WPF Data Binding with LINQ to XML Overview</span></span>](wpf-data-binding-with-linq-to-xml-overview.md)
- [<span data-ttu-id="ce272-121">LINQ to XML Kullanarak WPF Verilerini Bağlama Örneği</span><span class="sxs-lookup"><span data-stu-id="ce272-121">WPF Data Binding Using LINQ to XML Example</span></span>](linq-to-xml-data-binding-sample.md)
- [<span data-ttu-id="ce272-122">LINQ to XML Dinamik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="ce272-122">LINQ to XML Dynamic Properties</span></span>](linq-to-xml-dynamic-properties.md)
