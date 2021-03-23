---
title: "C 'de varsayılan arabirim yöntemlerini kullanarak arabirimleri güvenli bir şekilde Güncelleştir #"
description: Bu gelişmiş öğreticide, var olan arabirim tanımlarına, bu arabirimi uygulayan tüm sınıfları ve yapıları bozmadan nasıl güvenli bir şekilde yeni yetenekler ekleyebileceğiniz açıklanır.
ms.date: 05/06/2019
ms.technlogy: csharp-advanced-concepts
ms.custom: mvc
ms.openlocfilehash: 43af25cee765ba18543b0c7bfe0069542a90e0e5
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104879070"
---
# <a name="tutorial-update-interfaces-with-default-interface-methods-in-c-80"></a>Öğretici: C# 8,0 ' de varsayılan arabirim yöntemleriyle arabirimleri güncelleştirme

.NET Core 3,0 ' de C# 8,0 ' den başlayarak bir arabirimin üyesini bildirdiğinizde bir uygulama tanımlayabilirsiniz. En yaygın senaryo, önceden yayınlanan ve kullanılmayan istemciler tarafından kullanılan bir arabirime güvenli bir şekilde üye eklemektir.

Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:

> [!div class="checklist"]
>
> * Uygulamalarla yöntemler ekleyerek arabirimleri güvenli bir şekilde genişletin.
> * Daha fazla esneklik sağlamak için parametreli uygulamalar oluşturun.
> * Bir geçersiz kılma biçiminde daha belirli bir uygulama sağlamak için uygulayıcıları etkinleştirin.

## <a name="prerequisites"></a>Önkoşullar

C# 8,0 derleyicisi dahil olmak üzere makinenizi .NET Core çalıştıracak şekilde ayarlamanız gerekir. C# 8,0 derleyicisi, [Visual Studio 2019 sürüm 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download)ile başlayarak kullanılabilir.

## <a name="scenario-overview"></a>Senaryoya genel bakış

Bu öğretici, bir müşteri ilişkisi kitaplığının 1. sürümüyle başlar. [GitHub 'daki örnek](https://github.com/dotnet/samples/tree/main/csharp/tutorials/default-interface-members-versions/starter/customer-relationship)depolarımızda başlangıç uygulamasını edinebilirsiniz. Bu kitaplığın, kütüphanesini benimsemesini sağlayan, mevcut uygulamalarla müşterileri hedefleyen Şirket. Bunlar, kütüphanesinin kullanıcıları için en az sayıda arabirim tanımı sağladık. Müşterinin arabirim tanımı aşağıda verilmiştir:

[!code-csharp[InitialCustomerInterface](~/samples/snippets/csharp/tutorials/default-interface-members-versions/starter/customer-relationship/ICustomer.cs?name=SnippetICustomerVersion1)]

Sıralamayı temsil eden ikinci bir arabirim tanımlarlar:

[!code-csharp[InitialOrderInterface](~/samples/snippets/csharp/tutorials/default-interface-members-versions/starter/customer-relationship/IOrder.cs?name=SnippetIorderVersion1)]

Bu arabirimlerde, takım kullanıcılarına müşterilerine daha iyi bir deneyim oluşturmak için bir kitaplık oluşturabilir. Bu kişilerin hedefi, mevcut müşterilerle daha derin bir ilişki oluşturmak ve yeni müşterilerle ilişkilerini geliştirmektir.

Şimdi, bir sonraki sürüm için kitaplığı yükseltmeniz zaman atalım. İstenen özelliklerden biri, çok sayıda siparişi olan müşteriler için bağlılık programı indirimi sunar. Bu yeni bağlılık programı indirimi, bir müşteri sipariş yaptığında uygulanır. Belirli indirim, her müşterinin bir özelliğidir. Her bir uygulama `ICustomer` , bağlılık programı indirimi için farklı kurallar ayarlayabilir.

Bu işlevi eklemenin en doğal yolu, `ICustomer` arabirimi herhangi bir bağlılık programı indirimi uygulamak için bir yöntemle geliştirmektir. Bu tasarım önerisi, deneyimli geliştiriciler arasında sorun oluşmasına neden oldu: "arabirimler yayımlandıklarında sabittir! Bu bir son değişiklik! " C# 8,0, arabirimleri yükseltmek için *varsayılan arabirim uygulamalarını* ekler. Kitaplık yazarları arabirime yeni üyeler ekleyebilir ve bu üyeler için varsayılan bir uygulama sağlar.

Varsayılan arabirim uygulamaları, geliştiricilerin bu uygulamayı geçersiz kılmak için herhangi bir uygulamayı etkinleştirirken bir arabirimi yükseltmesini sağlar. Kitaplığın kullanıcıları, varsayılan uygulamayı kırılmamış bir değişiklik olarak kabul edebilir. İş kuralları farklıysa, geçersiz kılınabilir.

## <a name="upgrade-with-default-interface-methods"></a>Varsayılan arabirim yöntemleriyle yükselt

Takım, en olası varsayılan uygulamada anlaşmıştır: müşteriler için bağlılık programı indirimi.

Yükseltme, iki özellik ayarlama işlevini sağlamalıdır: indirimle uygun olması gereken siparişlerin sayısı ve indirimin yüzdesi. Bu, varsayılan arabirim yöntemlerine yönelik kusursuz bir senaryo sağlar. Arabirime bir yöntem ekleyebilir `ICustomer` ve en olası uygulamayı sağlayabilirsiniz. Tüm mevcut ve tüm yeni uygulamalar varsayılan uygulamayı kullanabilir veya kendi özelliklerini sağlayabilir.

İlk olarak, yönteminin gövdesi dahil olmak üzere arabirime yeni yöntemi ekleyin:

[!code-csharp[InitialOrderInterface](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetLoyaltyDiscountVersionOne)]

Kitaplık yazarı, uygulamayı denetlemek için bir ilk test yazdı:

[!code-csharp[TestDefaultImplementation](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetTestDefaultImplementation)]

Testin aşağıdaki kısmına dikkat edin:

[!code-csharp[TestDefaultImplementation](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetHighlightCast)]

' Den ' `SampleCustomer` ye atama `ICustomer` gereklidir. `SampleCustomer`Sınıfın `ComputeLoyaltyDiscount` , arabirimi tarafından sağlanmış olan bir uygulama sağlaması gerekmez `ICustomer` . Ancak, `SampleCustomer` sınıfı, arabirimlerinden üyeleri almıyor. Bu kural değiştirilmedi. Arabirimde bildirildiği ve uygulanan herhangi bir yöntemi çağırmak için, bu örnekte değişkenin türü olmalıdır `ICustomer` .

## <a name="provide-parameterization"></a>Parametreleştirme sağlama

Bu iyi bir başlangıç. Ancak, varsayılan uygulama çok kısıtlayıcıdır. Bu sistemin pek çok tüketicisi, satın alma sayısı, farklı üyelik uzunluğu veya farklı bir yüzde indirimi için farklı eşikler seçebilirler. Bu parametreleri ayarlamak için bir yol sağlayarak daha fazla müşteri için daha iyi bir yükseltme deneyimi sağlayabilirsiniz. Varsayılan uygulamayı denetleyen bu üç parametreyi ayarlayan statik bir yöntem ekleyelim:

[!code-csharp[VersionTwoImplementation](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetLoyaltyDiscountVersionTwo)]

Bu küçük kod parçasında gösterilen birçok yeni dil özelliği vardır. Arabirimler artık alanlar ve yöntemler dahil statik üyeleri içerebilir. Farklı erişim değiştiricileri de etkinleştirilir. Ek alanlar özeldir, yeni yöntem geneldir. Arabirim üyelerinde değiştiricilerin herhangi birine izin verilir.

Bağlılık programı iskontosunu hesaplamak için genel formülü kullanan uygulamalar, ancak farklı parametreler, özel bir uygulama sağlanması gerekmez; bağımsız değişkenleri statik bir yöntem aracılığıyla ayarlayabilirler. Örneğin, aşağıdaki kod, birden fazla aya ait üyeliğe sahip herhangi bir müşteriyi yeniden karşılayan bir "müşteri değer artırma" ayarlıyor:

[!code-csharp[SetLoyaltyThresholds](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetSetLoyaltyThresholds)]

## <a name="extend-the-default-implementation"></a>Varsayılan uygulamayı genişletme

Şimdiye kadar eklemiş olduğunuz kod, kullanıcıların varsayılan uygulama gibi bir şey istediği veya ilgisiz bir kural kümesi sağladığı senaryolar için uygun bir uygulama sağladı. Son bir özellik için, kullanıcıların varsayılan uygulamada derlemek isteyebileceğiniz senaryolara olanak tanımak için kodu bir bit yeniden düzenleyin.

Yeni müşterileri çekmek isteyen bir başlatma düşünün. Yeni bir müşterinin ilk siparişi için %50 indirim sağlar. Aksi halde, mevcut müşteriler standart iskontoyu alır. Kitaplık yazarının varsayılan uygulamayı bir yönteme taşıması gerekir, `protected static` böylece bu arabirimi uygulayan herhangi bir sınıf kendi uygulamalarında kodu yeniden kullanabilir. Arabirim üyesinin varsayılan uygulanması, bu paylaşılan yöntemi de çağırır:

[!code-csharp[VersionTwoImplementation](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetFinalVersion)]

Bu arabirimi uygulayan bir sınıfın uygulamasında, geçersiz kılma statik yardımcı yöntemini çağırabilir ve "yeni müşteri" indirimi sağlamak için bu mantığı genişletebilir:

[!code-csharp[VersionTwoImplementation](~/samples/snippets/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/SampleCustomer.cs?name=SnippetOverrideAndExtend)]

Tüm tamamlanmış kodu [GitHub 'daki örnek](https://github.com/dotnet/samples/tree/main/csharp/tutorials/default-interface-members-versions/finished/customer-relationship)depoımızda görebilirsiniz. [GitHub 'daki örnek](https://github.com/dotnet/samples/tree/main/csharp/tutorials/default-interface-members-versions/starter/customer-relationship)depolarımızda başlangıç uygulamasını edinebilirsiniz.

Bu yeni özellikler, bu yeni üyeler için makul bir varsayılan uygulama olduğunda arabirimlerin güvenli bir şekilde güncelleştirilemeyeceği anlamına gelir. Birden çok sınıf tarafından uygulanabilen tek işlevsel fikirlerin hızlı bir şekilde tasarlanması. Bu, aynı işlevsel fikir için yeni gereksinimler bulunduğunda bu arabirim tanımlarını yükseltmeyi kolaylaştırır.
