---
title: Model-Görünüm-Görünüm Model ile Taşınabilir Sınıf Kitaplığı Kullanma
ms.date: 07/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Portable Class Library [.NET Framework], and MVVM
- MVVM, and Portable Class Library
ms.assetid: 41a0b9f8-15a2-431a-bc35-e310b2953b03
ms.openlocfilehash: 3ec8b8387abf0f0271bb9585d8487c98ee6a893f
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687866"
---
# <a name="using-portable-class-library-with-model-view-view-model"></a><span data-ttu-id="b8cb1-102">Model-Görünüm-Görünüm Model ile Taşınabilir Sınıf Kitaplığı Kullanma</span><span class="sxs-lookup"><span data-stu-id="b8cb1-102">Using Portable Class Library with Model-View-View Model</span></span>
<span data-ttu-id="b8cb1-103">Model-görünüm-görünüm modeli (MVVM) modelini uygulamak ve derlemeleri birden çok platformda paylaşmak için .NET Framework [taşınabilir sınıf kitaplığını](portable-class-library.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8cb1-103">You can use the .NET Framework [Portable Class Library](portable-class-library.md) to implement the Model-View-View Model (MVVM) pattern and share assemblies across multiple platforms.</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 <span data-ttu-id="b8cb1-104">MVVM, temeldeki iş mantığındaki Kullanıcı arabirimini yalıtan bir uygulama modelidir.</span><span class="sxs-lookup"><span data-stu-id="b8cb1-104">MVVM is an application pattern that isolates the user interface from the underlying business logic.</span></span> <span data-ttu-id="b8cb1-105">Model ve model sınıflarını Visual Studio 2012 ' de taşınabilir bir sınıf kitaplığı projesinde uygulayabilir ve ardından farklı platformlar için özelleştirilmiş görünümler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8cb1-105">You can implement the model and view model classes in a Portable Class Library project in Visual Studio 2012, and then create views that are customized for different platforms.</span></span> <span data-ttu-id="b8cb1-106">Bu yaklaşım, veri modeli ve iş mantığını yalnızca bir kez yazmanızı ve bu kodu aşağıdaki çizimde gösterildiği gibi .NET Framework, Silverlight, Windows Phone ve Windows 8. x mağaza uygulamalarından kullanmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8cb1-106">This approach enables you to write the data model and business logic only once, and use that code from .NET Framework, Silverlight, Windows Phone, and Windows 8.x Store apps, as shown in the following illustration.</span></span>

 ![Platformlar arasında MVVM Sharing derlemelerinin bulunduğu taşınabilir sınıf kitaplığını gösterir.](./media/using-portable-class-library-with-model-view-view-model/mvvm-share-assemblies-across-platforms.png)

 <span data-ttu-id="b8cb1-108">Bu konu, MVVM düzeniyle ilgili genel bilgileri sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="b8cb1-108">This topic does not provide general information about the MVVM pattern.</span></span> <span data-ttu-id="b8cb1-109">Yalnızca taşınabilir sınıf kitaplığının, MVVM uygulamak için nasıl kullanılacağına ilişkin bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8cb1-109">It only provides information about how to use Portable Class Library to implement MVVM.</span></span> <span data-ttu-id="b8cb1-110">MVVM hakkında daha fazla bilgi için bkz. [WPF Için Prronizm kitaplığı 5,0 kullanılarak MVVM hızlı](/previous-versions/msp-n-p/gg430857(v=pandp.40))başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="b8cb1-110">For more information about MVVM, see the [MVVM Quickstart Using the Prism Library 5.0 for WPF](/previous-versions/msp-n-p/gg430857(v=pandp.40)).</span></span>

## <a name="classes-that-support-mvvm"></a><span data-ttu-id="b8cb1-111">MVVM 'YI destekleyen sınıflar</span><span class="sxs-lookup"><span data-stu-id="b8cb1-111">Classes That Support MVVM</span></span>
 <span data-ttu-id="b8cb1-112">.NET Framework 4,5, Windows 8. x Mağazası uygulamaları, Silverlight veya Windows Phone 7,5 için, taşınabilir sınıf kitaplığı projeniz için .NET ' i hedeflediğinizde, MVVM deseninin uygulanması için aşağıdaki sınıflar mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="b8cb1-112">When you target the .NET Framework 4.5, .NET for Windows 8.x Store apps, Silverlight, or Windows Phone 7.5 for your Portable Class Library project, the following classes are available for implementing the MVVM pattern:</span></span>

- <span data-ttu-id="b8cb1-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> sınıfı</span><span class="sxs-lookup"><span data-stu-id="b8cb1-113"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="b8cb1-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> sınıfı</span><span class="sxs-lookup"><span data-stu-id="b8cb1-114"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="b8cb1-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> sınıfı</span><span class="sxs-lookup"><span data-stu-id="b8cb1-115"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="b8cb1-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> sınıfı</span><span class="sxs-lookup"><span data-stu-id="b8cb1-116"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="b8cb1-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> sınıfı</span><span class="sxs-lookup"><span data-stu-id="b8cb1-117"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="b8cb1-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> sınıfı</span><span class="sxs-lookup"><span data-stu-id="b8cb1-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="b8cb1-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> sınıfı</span><span class="sxs-lookup"><span data-stu-id="b8cb1-119"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="b8cb1-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> sınıfı</span><span class="sxs-lookup"><span data-stu-id="b8cb1-120"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="b8cb1-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> sınıfı</span><span class="sxs-lookup"><span data-stu-id="b8cb1-121"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="b8cb1-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> sınıfı</span><span class="sxs-lookup"><span data-stu-id="b8cb1-122"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="b8cb1-123">Ad alanındaki tüm sınıflar <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b8cb1-123">All classes in the <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> namespace</span></span>

## <a name="implementing-mvvm"></a><span data-ttu-id="b8cb1-124">MVVM uygulama</span><span class="sxs-lookup"><span data-stu-id="b8cb1-124">Implementing MVVM</span></span>
 <span data-ttu-id="b8cb1-125">MVVM uygulamak için, taşınabilir bir sınıf kitaplığı projesi taşınabilir olmayan bir projeye başvuramadığı için genellikle bir taşınabilir sınıf kitaplığı projesinde hem model hem de görünüm modeli oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="b8cb1-125">To implement MVVM, you typically create both the model and the view model in a Portable Class Library project, because a Portable Class Library project cannot reference a non-portable project.</span></span> <span data-ttu-id="b8cb1-126">Model ve görünüm modeli aynı projede veya ayrı projelerde olabilir.</span><span class="sxs-lookup"><span data-stu-id="b8cb1-126">The model and view model can be in the same project or in separate projects.</span></span> <span data-ttu-id="b8cb1-127">Ayrı projeler kullanıyorsanız, model projesine görünüm modeli projesinden bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b8cb1-127">If you use separate projects, add a reference from the view model project to the model project.</span></span>

 <span data-ttu-id="b8cb1-128">Modeli derleyip, model projelerini görüntülediğinizde, görünümü içeren uygulamadaki bu derlemelere başvurduktan sonra.</span><span class="sxs-lookup"><span data-stu-id="b8cb1-128">After you compile the model and view model projects, you reference those assemblies in the app that contains the view.</span></span> <span data-ttu-id="b8cb1-129">Görünüm yalnızca görünüm modeliyle etkileşime geçtiğinde, yalnızca görünüm modelini içeren derlemeye başvurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8cb1-129">If the view interacts only with the view model, you only have to reference the assembly that contains the view model.</span></span>

### <a name="model"></a><span data-ttu-id="b8cb1-130">Model</span><span class="sxs-lookup"><span data-stu-id="b8cb1-130">Model</span></span>
 <span data-ttu-id="b8cb1-131">Aşağıdaki örnek, taşınabilir bir sınıf kitaplığı projesinde bulunabilecek basitleştirilmiş bir model sınıfını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="b8cb1-131">The following example shows a simplified model class that could reside in a Portable Class Library project.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 <span data-ttu-id="b8cb1-132">Aşağıdaki örnek, taşınabilir bir sınıf Kitaplığı projesindeki verileri doldurmak, almak ve güncelleştirmek için basit bir yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="b8cb1-132">The following example shows a simple way to populate, retrieve, and update the data in a Portable Class Library project.</span></span> <span data-ttu-id="b8cb1-133">Gerçek bir uygulamada, verileri Windows Communication Foundation (WCF) hizmeti gibi bir kaynaktan elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="b8cb1-133">In a real app, you would retrieve the data from a source such as a Windows Communication Foundation (WCF) service.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a><span data-ttu-id="b8cb1-134">Modeli görüntüle</span><span class="sxs-lookup"><span data-stu-id="b8cb1-134">View Model</span></span>
 <span data-ttu-id="b8cb1-135">MVVM deseninin uygulanması sırasında görünüm modelleri için bir temel sınıf sıklıkla eklenir.</span><span class="sxs-lookup"><span data-stu-id="b8cb1-135">A base class for view models is frequently added when implementing the MVVM pattern.</span></span> <span data-ttu-id="b8cb1-136">Aşağıdaki örnekte bir temel sınıf gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b8cb1-136">The following example shows a base class.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 <span data-ttu-id="b8cb1-137">Arabirim bir uygulama, <xref:System.Windows.Input.ICommand> genellikle MVVM düzeniyle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b8cb1-137">An implementation of the <xref:System.Windows.Input.ICommand> interface is frequently used with the MVVM pattern.</span></span> <span data-ttu-id="b8cb1-138">Aşağıdaki örnek, arabiriminin bir uygulamasını gösterir <xref:System.Windows.Input.ICommand> .</span><span class="sxs-lookup"><span data-stu-id="b8cb1-138">The following example shows an implementation of the <xref:System.Windows.Input.ICommand> interface.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 <span data-ttu-id="b8cb1-139">Aşağıdaki örnekte basitleştirilmiş bir görünüm modeli gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b8cb1-139">The following example shows a simplified view model.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a><span data-ttu-id="b8cb1-140">Görüntüle</span><span class="sxs-lookup"><span data-stu-id="b8cb1-140">View</span></span>  
 <span data-ttu-id="b8cb1-141">.NET Framework 4,5 uygulaması, Windows 8. x Mağazası uygulaması, Silverlight tabanlı uygulama veya Windows Phone 7,5 uygulaması, modeli içeren derlemeye başvurabilirsiniz ve model projelerini görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="b8cb1-141">From a .NET Framework 4.5 app, Windows 8.x Store app, Silverlight-based app, or Windows Phone 7.5 app, you can reference the assembly that contains the model and view model projects.</span></span>  <span data-ttu-id="b8cb1-142">Daha sonra Görünüm modeliyle etkileşim kuran bir görünüm oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="b8cb1-142">You then create a view that interacts with the view model.</span></span> <span data-ttu-id="b8cb1-143">Aşağıdaki örnekte, görünüm modelinden verileri alan ve güncelleştiren bir Basitleştirilmiş Windows Presentation Foundation (WPF) uygulaması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b8cb1-143">The following example shows a simplified Windows Presentation Foundation (WPF) app that retrieves and updates data from the view model.</span></span> <span data-ttu-id="b8cb1-144">Silverlight, Windows Phone veya Windows 8. x Mağaza uygulamalarında benzer görünümler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8cb1-144">You could create similar views in Silverlight, Windows Phone, or Windows 8.x Store apps.</span></span>  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a><span data-ttu-id="b8cb1-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8cb1-145">See also</span></span>

- [<span data-ttu-id="b8cb1-146">Taşınabilir Sınıf Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="b8cb1-146">Portable Class Library</span></span>](portable-class-library.md)
