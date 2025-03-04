---
title: .NET Framework sürümünde sürüm uyumluluğu
description: Geriye dönük uyumluluk ve yan yana yürütme dahil olmak üzere .NET Framework sürümleri arasında uyumluluk hakkında bilgi edinin.
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, version compatibility
- .NET Framework, compatibility with earlier versions
- .NET Framework versions, compatibility
ms.assetid: 2f25e522-456a-48c3-8a53-e5f39275649f
ms.openlocfilehash: 2be9c4e12d6a613e7f1062ec7492b0b99203f39d
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400702"
---
# <a name="version-compatibility"></a>Sürüm uyumluluğu

Geriye dönük uyumluluk, bir platformun belirli bir sürümü için geliştirilen bir uygulamanın o platformun sonraki sürümlerinde çalışacağı anlamına gelir. .NET Framework, geriye dönük uyumluluğu en üst düzeye çıkarmaya çalışır: bir .NET Framework sürümü için yazılan kaynak kodu .NET Framework sonraki sürümlerinde derlenmelidir ve .NET Framework bir sürümünde çalışan ikililer, .NET Framework sonraki sürümlerinde aynı şekilde davranmalıdır.

## <a name="version-compatibility-for-apps"></a><a name="Apps"></a> Uygulamalar için sürüm uyumluluğu

Varsayılan olarak, bir uygulama için derlenildiği .NET Framework sürümü üzerinde çalışır. Bu sürüm yoksa ve uygulama yapılandırma dosyası desteklenen sürümleri tanımlamıyorsa, bir .NET Framework başlatma hatası oluşabilir. Bu durumda, uygulamayı çalıştırma denemesi başarısız olur.

Uygulamanızın çalıştırıldığı belirli sürümleri tanımlamak için, uygulamanızın yapılandırma dosyasına bir veya daha fazla [\<supportedRuntime>](../configure-apps/file-schema/startup/supportedruntime-element.md) öğe ekleyin. Her `<supportedRuntime>` öğe, ilk olarak en çok tercih edilen sürümü ve en son tercih edilen sürümü belirterek, çalışma zamanının desteklenen bir sürümünü listeler.

```xml
<configuration>
   <startup>
      <supportedRuntime version="v2.0.50727" />
      <supportedRuntime version="v4.0" />
   </startup>
</configuration>
```

Daha fazla bilgi için bkz. [nasıl yapılır: uygulama yapılandırma .NET Framework 4 veya 4. x](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md).

## <a name="version-compatibility-for-components"></a>Bileşenler için sürüm uyumluluğu

Bir uygulama, üzerinde çalıştığı .NET Framework sürümünü denetleyebilir, ancak bir bileşen olamaz. Bileşenler ve sınıf kitaplıkları belirli bir uygulama bağlamında yüklenir ve bu nedenle uygulamanın üzerinde çalıştığı .NET Framework sürümünde otomatik olarak çalışır.

Bu kısıtlama nedeniyle, uyumluluk garantisi özellikle bileşenler için önemlidir. .NET Framework 4 ' ten başlayarak, bileşeni bu bileşene uygulayarak bir bileşenin birden çok sürüm arasında ne kadar uyumlu kalması beklendiğine yönelik dereceyi belirtebilirsiniz <xref:System.Runtime.Versioning.ComponentGuaranteesAttribute?displayProperty=nameWithType> . Araçlar bu özniteliği, bir bileşenin gelecekteki sürümlerindeki uyumluluk garantisinin olası ihlallerini algılamak için kullanabilir.

## <a name="backward-compatibility"></a>Geriye dönük uyumluluk

.NET Framework 4,5 ve üzeri sürümler, .NET Framework önceki sürümleriyle oluşturulmuş uygulamalarla geriye dönük olarak uyumludur. Diğer bir deyişle, önceki sürümlerle oluşturulan uygulamalar ve bileşenler .NET Framework 4,5 ve sonraki sürümlerde değişiklik yapılmadan çalışacaktır. Ancak, uygulamalar geliştirildiği ortak dil çalışma zamanının sürümünde çalışır, bu nedenle uygulamanızın .NET Framework 4,5 veya sonraki sürümlerde çalışmasını sağlamak için bir yapılandırma dosyası sağlamanız gerekebilir. Daha fazla bilgi için bu makalenin önceki kısımlarında [uygulamalar Için sürüm uyumluluğu](#Apps) bölümüne bakın.

Uygulamada, bu uyumluluk .NET Framework ve programlama tekniklerindeki değişiklikler tarafından bozulabilir. Örneğin, .NET Framework 4,5 ' deki performans geliştirmeleri, önceki sürümlerde gerçekleşmeyen bir yarış durumu sunabilir. Benzer şekilde, derlemeler .NET Framework için sabit kodlanmış bir yol kullanma, .NET Framework belirli bir sürümüyle eşitlik karşılaştırması gerçekleştirme ve yansıma kullanarak özel bir alanın değerini alma, geriye dönük olarak uyumlu uygulamalar değildir. Ayrıca, .NET Framework her sürümü, bazı uygulamaların ve bileşenlerin uyumluluğunu etkileyebilecek hata düzeltmeleri ve güvenlikle ilgili değişiklikler içerir.

Uygulamanız veya bileşeniniz .NET Framework 4,5 ' de beklendiği gibi çalışmazsa (kendi nokta sürümleri, .NET Framework 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 veya 4,8), aşağıdaki denetim listelerini kullanın:

- Uygulamanız .NET Framework 4,0 ' den başlayarak .NET Framework herhangi bir sürümünde çalışacak şekilde geliştirildiyse, hedeflenen .NET Framework sürümünüz ve uygulamanızın üzerinde çalıştığı sürüm arasındaki değişikliklerin listesini oluşturmak için [uygulama uyumluluğu](application-compatibility.md) ' na bakın.

- .NET Framework 3,5 uygulamanız varsa Ayrıca bkz. [.NET Framework 4 geçiş sorunları](net-framework-4-migration-issues.md).

- .NET Framework 2,0 uygulamanız varsa, [.NET Framework 3,5 SP1 'Deki değişikliklere](/previous-versions/dotnet/articles/dd310284(v=msdn.10))de bakın.

- .NET Framework 1,1 uygulamanız varsa, [.NET Framework 2,0 ' deki değişikliklere](/previous-versions/aa570326(v=msdn.10))de bakın.

- Var olan kaynak kodu .NET Framework 4,5 ' de veya onun noktası sürümlerinde çalışacak şekilde yeniden derliyorsanız veya mevcut bir kaynak kod tabanından .NET Framework 4,5 ya da noktası sürümlerini hedefleyen bir uygulamanın veya bileşenin yeni bir sürümünü geliştiriyorsanız, artık kullanılmayan türler ve Üyeler için [sınıf kitaplığında nelerin eski olduğunu](../whats-new/whats-obsolete.md) denetleyin ve açıklanan geçici çözümü uygulayın. (Önceden derlenen kod, eski olarak işaretlenen türlere ve üyelere karşı çalışmaya devam edecektir.)

- .NET Framework 4,5 ' deki bir değişikliğin uygulamanızı bozmadığını belirlerseniz, önceki davranışı geri yüklemek için uygulamanızın yapılandırma dosyasında bir çalışma zamanı ayarı kullanıp kullanmayacağınızı öğrenmek için [çalışma zamanı ayarları şemasını](../configure-apps/file-schema/runtime/index.md)ve özellikle [ \<AppContextSwitchOverrides> öğesini](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)kontrol edin.

- Belgelenmemiş bir sorunla karşılaşırsanız, [.net Için Developer Community sitesinde](https://aka.ms/feedback/report?space=61) bir sorun açın veya [Microsoft/DotNet GitHub](https://github.com/microsoft/dotnet/issues)deposunda bir sorun açın.

## <a name="side-by-side-execution"></a>Yan yana yürütme

Sorununuz için uygun bir geçici çözüm bulamazsanız, .NET Framework 4,5 ' nin (veya bir nokta yayınlarından birinin) 1,1, 2,0 ve 3,5 sürümleriyle yan yana çalıştığını ve sürüm 4 ' ün yerini alan bir yerinde güncelleştirme olduğunu unutmayın. 1,1, 2,0 ve 3,5 sürümlerini hedefleyen uygulamalar için, uygulamayı en iyi ortamında çalıştırmak amacıyla hedef makineye .NET Framework uygun sürümünü yükleyebilirsiniz. Yan yana yürütme hakkında daha fazla bilgi için bkz. yan [yana yürütme](../deployment/side-by-side-execution.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Yenilikler](../whats-new/index.md)
- [Sınıf Kitaplığı'nda Artık Kullanılmayanlar](../whats-new/whats-obsolete.md)
- [Uygulama uyumluluğu](application-compatibility.md)
- [.NET Framework resmi destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [.NET Framework 4 geçiş sorunları](net-framework-4-migration-issues.md)
