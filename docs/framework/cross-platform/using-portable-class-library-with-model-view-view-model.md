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
# <a name="using-portable-class-library-with-model-view-view-model"></a>Model-Görünüm-Görünüm Model ile Taşınabilir Sınıf Kitaplığı Kullanma
Model-görünüm-görünüm modeli (MVVM) modelini uygulamak ve derlemeleri birden çok platformda paylaşmak için .NET Framework [taşınabilir sınıf kitaplığını](portable-class-library.md) kullanabilirsiniz.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 MVVM, temeldeki iş mantığındaki Kullanıcı arabirimini yalıtan bir uygulama modelidir. Model ve model sınıflarını Visual Studio 2012 ' de taşınabilir bir sınıf kitaplığı projesinde uygulayabilir ve ardından farklı platformlar için özelleştirilmiş görünümler oluşturabilirsiniz. Bu yaklaşım, veri modeli ve iş mantığını yalnızca bir kez yazmanızı ve bu kodu aşağıdaki çizimde gösterildiği gibi .NET Framework, Silverlight, Windows Phone ve Windows 8. x mağaza uygulamalarından kullanmanızı sağlar.

 ![Platformlar arasında MVVM Sharing derlemelerinin bulunduğu taşınabilir sınıf kitaplığını gösterir.](./media/using-portable-class-library-with-model-view-view-model/mvvm-share-assemblies-across-platforms.png)

 Bu konu, MVVM düzeniyle ilgili genel bilgileri sağlamaz. Yalnızca taşınabilir sınıf kitaplığının, MVVM uygulamak için nasıl kullanılacağına ilişkin bilgiler sağlar. MVVM hakkında daha fazla bilgi için bkz. [WPF Için Prronizm kitaplığı 5,0 kullanılarak MVVM hızlı](/previous-versions/msp-n-p/gg430857(v=pandp.40))başlangıcı.

## <a name="classes-that-support-mvvm"></a>MVVM 'YI destekleyen sınıflar
 .NET Framework 4,5, Windows 8. x Mağazası uygulamaları, Silverlight veya Windows Phone 7,5 için, taşınabilir sınıf kitaplığı projeniz için .NET ' i hedeflediğinizde, MVVM deseninin uygulanması için aşağıdaki sınıflar mevcuttur:

- <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> sınıfı

- <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> sınıfı

- <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> sınıfı

- <xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> sınıfı

- <xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> sınıfı

- <xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> sınıfı

- <xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> sınıfı

- <xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> sınıfı

- <xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> sınıfı

- <xref:System.Windows.Input.ICommand?displayProperty=nameWithType> sınıfı

- Ad alanındaki tüm sınıflar <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType>

## <a name="implementing-mvvm"></a>MVVM uygulama
 MVVM uygulamak için, taşınabilir bir sınıf kitaplığı projesi taşınabilir olmayan bir projeye başvuramadığı için genellikle bir taşınabilir sınıf kitaplığı projesinde hem model hem de görünüm modeli oluşturursunuz. Model ve görünüm modeli aynı projede veya ayrı projelerde olabilir. Ayrı projeler kullanıyorsanız, model projesine görünüm modeli projesinden bir başvuru ekleyin.

 Modeli derleyip, model projelerini görüntülediğinizde, görünümü içeren uygulamadaki bu derlemelere başvurduktan sonra. Görünüm yalnızca görünüm modeliyle etkileşime geçtiğinde, yalnızca görünüm modelini içeren derlemeye başvurmanız gerekir.

### <a name="model"></a>Model
 Aşağıdaki örnek, taşınabilir bir sınıf kitaplığı projesinde bulunabilecek basitleştirilmiş bir model sınıfını göstermektedir.

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 Aşağıdaki örnek, taşınabilir bir sınıf Kitaplığı projesindeki verileri doldurmak, almak ve güncelleştirmek için basit bir yol gösterir. Gerçek bir uygulamada, verileri Windows Communication Foundation (WCF) hizmeti gibi bir kaynaktan elde edersiniz.

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a>Modeli görüntüle
 MVVM deseninin uygulanması sırasında görünüm modelleri için bir temel sınıf sıklıkla eklenir. Aşağıdaki örnekte bir temel sınıf gösterilmektedir.

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 Arabirim bir uygulama, <xref:System.Windows.Input.ICommand> genellikle MVVM düzeniyle birlikte kullanılır. Aşağıdaki örnek, arabiriminin bir uygulamasını gösterir <xref:System.Windows.Input.ICommand> .

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 Aşağıdaki örnekte basitleştirilmiş bir görünüm modeli gösterilmektedir.

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a>Görüntüle  
 .NET Framework 4,5 uygulaması, Windows 8. x Mağazası uygulaması, Silverlight tabanlı uygulama veya Windows Phone 7,5 uygulaması, modeli içeren derlemeye başvurabilirsiniz ve model projelerini görüntüleyin.  Daha sonra Görünüm modeliyle etkileşim kuran bir görünüm oluşturursunuz. Aşağıdaki örnekte, görünüm modelinden verileri alan ve güncelleştiren bir Basitleştirilmiş Windows Presentation Foundation (WPF) uygulaması gösterilmektedir. Silverlight, Windows Phone veya Windows 8. x Mağaza uygulamalarında benzer görünümler oluşturabilirsiniz.  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Taşınabilir Sınıf Kitaplığı](portable-class-library.md)
