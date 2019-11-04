---
title: 'Performansı İyileştirme: Uygulama Kaynakları'
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF], performance
- resources [WPF], performance
- static resources [WPF]
- sharing resources [WPF]
- brushes [WPF], performance
- sharing brushes without copying [WPF]
ms.assetid: 62b88488-c08e-4804-b7de-a1c34fbe929c
ms.openlocfilehash: 59b124c28ade0a6c5119b651ff935d460bf4516d
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458563"
---
# <a name="optimizing-performance-application-resources"></a>Performansı İyileştirme: Uygulama Kaynakları
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], benzer yazılı öğelerde tutarlı bir görünüm veya davranışı destekleyebilmeniz için uygulama kaynaklarını paylaşmanıza olanak sağlar. Bu konuda, bu alanda uygulamalarınızın performansını artırmanıza yardımcı olabilecek birkaç öneri sunulmaktadır.  
  
 Kaynaklar hakkında daha fazla bilgi için bkz. [xaml kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
## <a name="sharing-resources"></a>Kaynakları paylaşma  
 Uygulamanız özel denetimler kullanıyorsa ve bir <xref:System.Windows.ResourceDictionary> (ya da XAML Kaynakları düğümünde) kaynaklarını tanımlıyorsa, kaynakları <xref:System.Windows.Application> veya <xref:System.Windows.Window> nesne düzeyinde tanımlamanız ya da bunları özel denetimler için varsayılan Temada tanımlamanız önerilir. Özel bir denetim <xref:System.Windows.ResourceDictionary> kaynak tanımlamak, bu denetimin her örneği için bir performans etkisi uygular. Örneğin, özel bir denetimin kaynak tanımının bir parçası olarak tanımlanan performans yoğunluğu olan fırça işlemleri ve özel denetimin birçok örneği varsa, uygulamanın çalışma kümesi önemli ölçüde artacaktır.  
  
 Bu noktayı göstermek için aşağıdakileri göz önünde bulundurun. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]kullanarak bir kart oyunu geliştirdiğinizi varsayalım. Çoğu kart oyunlarında, 52 farklı yüzlerle 52 kart gerekir. Bir kart özel denetimi uygulamaya karar verirsiniz ve kart özel denetiminizin kaynaklarında 52 fırçalar (her biri bir kart yüzünü temsil eder) tanımlarsınız. Ana uygulamanızda başlangıçta bu kart özel denetiminin 52 örneğini oluşturursunuz. Her bir kart özel denetimi örneği, uygulamanızda toplam 52 * 52 <xref:System.Windows.Media.Brush> nesnesi sağlayan <xref:System.Windows.Media.Brush> nesnelerinin 52 örneğini üretir. Bu fırçaları, kart özel denetim kaynakları dışına <xref:System.Windows.Application> veya <xref:System.Windows.Window> nesne düzeyine taşıyarak ya da özel denetim için varsayılan Temada tanımlayarak, 52 fırçalarını 52 arasında paylaşmakta olduğunuz için uygulamanın çalışma kümesini azaltabilirsiniz. kart denetiminin örnekleri.  
  
## <a name="sharing-a-brush-without-copying"></a>Bir fırçayı kopyalamadan paylaşma  
 Aynı <xref:System.Windows.Media.Brush> nesnesini kullanarak birden çok öğeye sahipseniz, fırçayı bir kaynak olarak tanımlayın ve XAML 'de fırça satır içi tanımlamak yerine ona başvurun. Bu yöntem bir örnek oluşturacak ve onu yeniden kullanacaktır, ancak XAML 'de fırça satır içi tanımlamak her öğe için yeni bir örnek oluşturur.  
  
 Aşağıdaki biçimlendirme örneği bu noktayı gösterir:  
  
 [!code-xaml[Performance#PerformanceSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/BrushResource.xaml#performancesnippet7)]  
  
## <a name="use-static-resources-when-possible"></a>Mümkün olduğunda statik kaynakları kullan  
 Statik bir kaynak, önceden tanımlanmış bir kaynağa bir başvuru arayarak herhangi bir XAML özellik özniteliği için bir değer sağlar. Bu kaynak için arama davranışı, derleme zamanı aramasına benzer.  
  
 Diğer yandan dinamik bir kaynak, ilk derleme sırasında geçici bir ifade oluşturur ve bu nedenle istenen kaynak değeri gerçekten bir nesne oluşturmak için gerekene kadar kaynakları aramayı erteler. Bu kaynağın arama davranışı, bir performans etkisi sağlayan çalışma zamanı aramasına benzer. Uygulamanızda mümkün olduğunda statik kaynakları, yalnızca gerektiğinde dinamik kaynakları kullanarak kullanın.  
  
 Aşağıdaki biçimlendirme örneği her iki tür kaynak kullanımını gösterir:  
  
 [!code-xaml[Performance#PerformanceSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/DynamicResource.xaml#performancesnippet8)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF Uygulama Performansını İyileştirme](optimizing-wpf-application-performance.md)
- [Uygulama Performansını Planlama](planning-for-application-performance.md)
- [Donanımdan Yararlanma](optimizing-performance-taking-advantage-of-hardware.md)
- [Düzen ve Tasarım](optimizing-performance-layout-and-design.md)
- [2B Grafikleri ve Görüntüleme](optimizing-performance-2d-graphics-and-imaging.md)
- [Nesne Davranışı](optimizing-performance-object-behavior.md)
- [Metin](optimizing-performance-text.md)
- [Veri Bağlama](optimizing-performance-data-binding.md)
- [Diğer Performans Önerileri](optimizing-performance-other-recommendations.md)
