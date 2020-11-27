---
title: Dinamik dil çalışma zamanına genel bakış | Microsoft Docs
description: .NET 'teki dinamik dil çalışma zamanına (DLR) genel bir bakış konusunu okuyun. DLR, CLR 'ye dinamik diller için bir hizmet kümesi ekleyen bir çalışma zamanı ortamıdır.
ms.date: 03/30/2017
helpviewer_keywords:
- dynamic language runtime
- IronPython
- DLR
- IronRuby
ms.assetid: f769a271-8aff-4bea-bfab-6160217ce23d
ms.openlocfilehash: a36d6704b36b5006f19e21932797f21af849e55a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266837"
---
# <a name="dynamic-language-runtime-overview"></a>Dinamik Dil Çalışma Zamanına Genel Bakış

*Dinamik dil çalışma zamanı* (DLR), ortak dil çalışma zamanına (CLR) dinamik diller için bir hizmet kümesi ekleyen bir çalışma zamanı ortamıdır. DLR, .NET Framework çalıştırmak ve statik olarak belirlenmiş dillere dinamik özellikler eklemek için dinamik dillerin geliştirmeyi kolaylaştırır.

Dinamik diller, çalışma zamanında bir nesnenin türünü tanımlayabilir, ancak C# ve Visual Basic gibi statik olarak yazılmış dillerde (kullandığınızda `Option Explicit On` ), tasarım zamanında nesne türlerini belirtmeniz gerekir. Dinamik dillere örnek olarak, Lizp, Smalltalk, JavaScript, PHP, Ruby, Python, ColdFusion, Lua, Coköşeli ve groovy verilebilir.

Çoğu dinamik dil, geliştiriciler için aşağıdaki avantajları sağlar:

- Hızlı geri bildirim döngüsü (REPL veya Read-değerlendir-PRINT döngüsü) kullanma özelliği. Bu, birkaç deyim girmenize ve sonuçları görmek için hemen yürütmenize imkan tanır.

- Hem yukarıdan aşağıya geliştirme hem de daha geleneksel en düşük geliştirme desteği. Örneğin, yukarıdan aşağı bir yaklaşım kullandığınızda henüz uygulanmayan işlevleri çağırabilir ve ardından ihtiyacınız olduğunda temel alınan uygulamaları ekleyebilirsiniz.

- Kod genelinde statik tür bildirimlerini değiştirmeniz gerekli olmadığından, daha kolay yeniden düzenleme ve kod değişiklikleri.

Dinamik diller mükemmel betik dilleri yapar. Müşteriler, dinamik diller kullanılarak oluşturulan uygulamaları yeni komutlar ve işlevlerle kolayca genişletebilir. Dinamik diller, Web siteleri oluşturmak ve test gücünden, sunucu gruplarını korumak, çeşitli yardımcı programlar geliştirmek ve veri dönüştürmeleri gerçekleştirmek için de sık kullanılır.

DLCı r 'nin amacı, dinamik dillerin bir sisteminin .NET Framework çalışmasına ve .NET birlikte çalışabilirliğine izin vermektir. DLR, bu dillerdeki dinamik davranışı desteklemek ve dinamik dillerle birlikte çalışabilirliği etkinleştirmek için C# ve Visual Basic dinamik nesneleri ekler.

DLCı, dinamik işlemleri destekleyen kitaplıklar oluşturmanıza de yardımcı olur. Örneğin, XML veya JavaScript Nesne Gösterimi (JSON) nesneleri kullanan bir kitaplığınız varsa, nesneleriniz DLR kullanan dillere dinamik nesneler olarak görünebilir. Bu, kitaplık kullanıcılarının nesnelerle çalışma ve nesne üyelerine erişme için sözdizimsel olarak daha basit ve daha doğal kodlar yazmasına olanak sağlar.

Örneğin, C# ' de XML 'deki bir sayacı artırmak için aşağıdaki kodu kullanabilirsiniz.

`Scriptobj.SetProperty("Count", ((int)GetProperty("Count")) + 1);`

DLCı 'yi kullanarak, aynı işlem için bunun yerine aşağıdaki kodu kullanabilirsiniz.

`scriptobj.Count += 1;`

CLR gibi, DLR .NET Framework bir parçasıdır ve .NET Framework ve Visual Studio yükleme paketleriyle birlikte sağlanır. DLR 'nin açık kaynaklı sürümü, GitHub 'daki [ıronlanguages/DLR](https://github.com/IronLanguages/dlr) deposunda da indirilebilir.

> [!NOTE]
> DLCı r 'nin açık kaynak sürümü, Visual Studio 'Ya ve .NET Framework dahil olan DLCı r 'nin tüm özelliklerine sahiptir. Ayrıca dil uygulayıcıları için ek destek sağlar. Daha fazla bilgi için GitHub 'daki [ıronlanguages/DLR](https://github.com/IronLanguages/dlr) deposu ile ilgili belgelere bakın.

DLCı 'ler kullanılarak geliştirilmiş dillerin örnekleri şunları içerir:

- IronPython. [GitHub](https://github.com/IronLanguages/ironpython2) Web sitesinden açık kaynaklı yazılım olarak kullanılabilir.

- IronRuby. [IronRuby](http://ironruby.net/) Web sitesinden açık kaynaklı yazılım olarak kullanılabilir.

## <a name="primary-dlr-advantages"></a>Birincil DLR avantajları

 DLR aşağıdaki avantajları sağlar.

### <a name="simplifies-porting-dynamic-languages-to-the-net-framework"></a>.NET Framework dinamik dillerin taşıma işlemini basitleştirir

 DLCı 'ler, dil uygulayıcıları, çözümleyiciler, semantik çözümleyiciler, kod oluşturucuları ve geleneksel olarak kendilerini oluşturmak zorunda oldukları diğer araçları oluşturmanızı önler. DLR 'yi kullanmak için bir dilin ağaç şeklinde bir yapıda, çalışma zamanı Yardımcısı yordamlarında ve arabirimi uygulayan isteğe bağlı dinamik nesnelerde dil düzeyi kodu temsil eden *ifade ağaçları* üretmesi gerekir <xref:System.Dynamic.IDynamicMetaObjectProvider> . DLR ve .NET Framework, çok sayıda kod analizi ve kod oluşturma görevini otomatikleştirin. Bu, dil uygulayıcıları 'nın benzersiz dil özelliklerine odaklanmalarını sağlar.

### <a name="enables-dynamic-features-in-statically-typed-languages"></a>Statik olarak belirlenmiş dillerdeki dinamik özellikleri sunar

 C# ve Visual Basic gibi mevcut .NET Framework diller, dinamik nesneler oluşturabilir ve bunları statik olarak yazılmış nesnelerle birlikte kullanabilir. Örneğin, C# ve Visual Basic HTML, Belge Nesne Modeli (DOM) ve .NET yansıma için dinamik nesneler kullanabilir.

### <a name="provides-future-benefits-of-the-dlr-and-net-framework"></a>DLCı r ve .NET Framework gelecek avantajları sağlar

 DLCı 'ler kullanılarak uygulanan diller, gelecekteki DLCı 'ler ve .NET Framework geliştirmelerinden faydalanabilir. Örneğin, .NET Framework geliştirilmiş bir çöp toplayıcısı veya daha hızlı derleme yükleme süresi içeren yeni bir sürüm yayımlarsa, DLR kullanılarak uygulanan diller hemen aynı avantajı alır. DLR, daha iyi derleme gibi iyileştirmeler eklerse, performans da DLCı r kullanılarak uygulanan tüm diller için de geliştirilir.

### <a name="enables-sharing-of-libraries-and-objects"></a>Kitaplıkların ve nesnelerin paylaşılmasını sunar

 Tek bir dilde uygulanan nesneler ve kitaplıklar diğer diller tarafından kullanılabilir. DLCı, statik olarak yazılmış ve dinamik diller arasında birlikte çalışabilirliği de sunar. Örneğin, C# dinamik bir dilde yazılmış bir kitaplığı kullanan dinamik bir nesne bildirebilir. Aynı zamanda, dinamik diller .NET Framework kitaplıklarını kullanabilir.

### <a name="provides-fast-dynamic-dispatch-and-invocation"></a>Hızlı dinamik dağıtım ve çağırma sağlar

 DLR, gelişmiş polimorfik önbelleğe almayı destekleyerek dinamik işlemlerin hızlı bir şekilde yürütülmesini sağlar. DLR, nesneleri gerekli çalışma zamanı uygulamalarına kullanan bağlama işlemleri için kurallar oluşturur ve ardından aynı türdeki nesne türlerinde aynı kodun ardışık yürütmeleri sırasında kaynak tüketmeyi önlemek için bu kuralları önbelleğe alır.

## <a name="dlr-architecture"></a>DLR mimarisi

 Aşağıdaki çizimde, dinamik dil çalışma zamanının mimarisi gösterilmektedir.

 ![Dinamik dil çalışma zamanı mimarisine genel bakış](./media/dlr-archoverview.png "DLR_ArchOverview") DLR mimarisi

 DLR, dinamik dilleri daha iyi desteklemek için CLR 'ye bir hizmet kümesi ekler. Bu hizmetler şunları içerir:

- İfade ağaçları. DLR, dil semantiğini temsil etmek için ifade ağaçları kullanır. Bu amaçla, DLR, denetim akışını, atamayı ve diğer dil modelleme düğümlerini dahil etmek için LINQ ifade ağaçları genişletmiştir. Daha fazla bilgi için bkz. [Expression ağaçlar (C#)](../../csharp/programming-guide/concepts/expression-trees/index.md) veya [ifade ağaçları (Visual Basic)](../../visual-basic/programming-guide/concepts/expression-trees/index.md).

- Site önbelleğe alma çağrısı yapın. *Dinamik bir çağrı sitesi* , kodda `a + b` veya dinamik nesnelerde olduğu gibi bir işlem gerçekleştirdiğiniz bir yerdir `a.b()` . DLR, `a` ve `b` (genellikle bu nesnelerin türleri) özelliklerini ve işlemle ilgili bilgileri önbelleğe alır. Bu tür bir işlem daha önce gerçekleştirilirse, DLR hızlı dağıtım için önbellekten tüm gerekli bilgileri alır.

- Dinamik nesne birlikte çalışabilirliği. DLR, dinamik nesneleri ve işlemleri temsil eden bir sınıf ve arabirim kümesi sağlar ve dinamik kitaplıkların dil uygulayıcıları ve yazarları tarafından kullanılabilir. Bu sınıflar ve arabirimler,,, <xref:System.Dynamic.IDynamicMetaObjectProvider> <xref:System.Dynamic.DynamicMetaObject> ve içerir <xref:System.Dynamic.DynamicObject> <xref:System.Dynamic.ExpandoObject> .

DLR, yalnızca .NET Framework değil, ancak Silverlight ve COM dahil olmak üzere diğer altyapılarla ve hizmetlerle iletişim kurmak için çağıran sitelerde ciltler kullanır. Ciltler bir dilin semantiğini kapsüller ve ifade ağaçları kullanarak bir çağrı sitesinde nasıl işlem yapılacağını belirtir. Bu, bir DLR kullanan dinamik ve statik olarak belirlenmiş dillerin kitaplıklarını paylaşmak ve DLR 'nin desteklediği tüm teknolojiler için erişim elde etmenizi sağlar.

## <a name="dlr-documentation"></a>DLR belgeleri

 Bir dile dinamik davranış eklemek için DLR 'nin açık kaynak sürümünü kullanma hakkında daha fazla bilgi için veya .NET Framework ile dinamik bir dilin kullanımını etkinleştirme hakkında daha fazla bilgi için GitHub 'daki [ıronlanguages/DLR](https://github.com/IronLanguages/dlr/tree/master/Docs) deposunun belgelerine bakın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Dynamic.ExpandoObject>
- <xref:System.Dynamic.DynamicObject>
- [Ortak Dil Çalışma Zamanı](../../standard/clr.md)
- [İfade ağaçları (C#)](../../csharp/programming-guide/concepts/expression-trees/index.md)
- [İfade ağaçları (Visual Basic)](../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [İzlenecek yol: dinamik nesneler oluşturma ve kullanma](../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
