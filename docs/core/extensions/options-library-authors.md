---
title: .NET kitaplığı yazarları için seçenekler model Kılavuzu
author: IEvangelist
description: Seçenekler deseninin .NET 'teki kitaplık yazarı olarak nasıl kullanıma sunulacağınızı öğrenin.
ms.author: dapine
ms.date: 04/12/2021
ms.openlocfilehash: 7e1bfeadff92f5d0d979ef2d7da11d7c1b47c58d
ms.sourcegitcommit: bbc724b72fb6c978905ac715e4033efa291f84dc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107369627"
---
# <a name="options-pattern-guidance-for-net-library-authors"></a>.NET kitaplığı yazarları için seçenekler model Kılavuzu

Bağımlılık ekleme yardımı ile hizmetlerinizi kaydetme ve ilgili yapılandırmaların, *Seçenekler deseninin* kullanımını sağlayabilirsiniz. Seçenekler stili, kitaplığınızdaki tüketicilere (ve hizmetlerinizde), Seçenekler sınıfınız olduğu durumlarda [seçenek arayüzlerinin](options.md#options-interfaces) örneklerinin olmasını sağlar `TOptions` . Kesin olarak belirlenmiş nesneler aracılığıyla yapılandırma seçeneklerini kullanmak tutarlı değer gösterimi sağlanmasına yardımcı olur ve dize değerlerini el ile ayrıştırma yükünü ortadan kaldırır. Kitaplığınızın kullanacağı tüketicilere yönelik birçok [yapılandırma sağlayıcısı](configuration-providers.md) vardır. Bu sağlayıcılar sayesinde, müşteriler kitaplığınızı birçok şekilde yapılandırabilir.

.NET kitaplığı yazarı olarak, kitaplığınızdaki tüketicilere seçenekler deseninin doğru bir şekilde kullanıma sunulmasına ilişkin genel rehberlik öğreneceksiniz. Aynı şeyi gerçekleştirmenin çeşitli yolları ve yapmanız gereken birkaç nokta vardır.

## <a name="naming-conventions"></a>Adlandırma kuralları

Kurala göre, hizmetlerin kaydolmasından sorumlu uzantı yöntemleri adlandırılır `Add{Service}` ; burada `{Service}` anlamlı ve açıklayıcı bir addır. Pakete bağlı olarak, hizmet kaydına `Use{Service}` Uzantı yöntemleri eşlik edebilir. `Use{Service}`Uzantı yöntemleri [ASP.NET Core](/aspnet).

✔️ diğer tekliflerden hizmetinizi ayırt eden adları göz önünde bulundurun.

❌ Resmi Microsoft paketlerinde .NET ekosisteminin zaten bir parçası olan adlar kullanmayın.

✔️ Uzantı yöntemlerini kullanıma sunan statik sınıfların `{Type}Extensions` `{Type}` adlandırılırsınız, burada, genişletmenin türü.

### <a name="namespace-guidance"></a>Ad alanı Kılavuzu

Microsoft paketleri `Microsoft.Extensions.DependencyInjection` çeşitli hizmet tekliflerinin kaydını yapmak için ad alanını kullanır.

✔️, paket teklifinizi açıkça tanımlayan bir ad alanı düşünün.

❌`Microsoft.Extensions.DependencyInjection`Resmi olmayan Microsoft paketleri için ad alanını kullanmayın.

## <a name="parameterless"></a>İçermeyen

Hizmetiniz en az bir açık yapılandırma olmadan veya açık yapılandırma olmadan çalışacağından parametresiz bir genişletme yöntemi düşünün.

:::code language="csharp" source="snippets/configuration/options-noparams/ServiceCollectionExtensions.cs" highlight="10-14":::

Yukarıdaki kodda `AddMyLibraryService` :

- Bir örneğini genişletir <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>
- <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType>Tür parametresine sahip çağrılar`LibraryOptions`
- <xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A>Varsayılan seçenek değerlerini belirten öğesine bir çağrısını zincirler

## <a name="iconfiguration-parameter"></a>`IConfiguration` parametresinin

Tüketiciler için çok sayıda seçenek sunan bir kitaplık yazdığınızda bir `IConfiguration` parametre genişletme yöntemi yapmayı düşünmek isteyebilirsiniz. Beklenen `IConfiguration` örnek, işlevini kullanarak yapılandırmanın adlandırılmış bir bölümüne kapsam içermelidir <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A?displayProperty=nameWithType> .

:::code language="csharp" source="snippets/configuration/options-configparam/ServiceCollectionExtensions.cs" highlight="10,12-14":::

Yukarıdaki kodda `AddMyLibraryService` :

- Bir örneğini genişletir <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>
- Bir <xref:Microsoft.Extensions.Configuration.IConfiguration> parametreyi tanımlar `namedConfigurationSection`
- <xref:Microsoft.Extensions.DependencyInjection.OptionsConfigurationServiceCollectionExtensions.Configure%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection,Microsoft.Extensions.Configuration.IConfiguration)>Öğesinin genel tür parametresini `LibraryOptions` ve `namedConfigurationSection` yapılandırılacak örneği geçen çağrılar

Bu düzendeki tüketiciler, `IConfiguration` adlandırılmış bölümün kapsamlı örneğini sağlar:

:::code language="csharp" source="snippets/configuration/options-configparam/Program.cs" highlight="22-23":::

Çağrısı `.AddMyLibraryService` <xref:Microsoft.Extensions.Hosting.IHostBuilder.ConfigureServices%2A> yönteminde yapılır. Aynı değer, bir `Startup` sınıfı kullanırken, kaydedilecek hizmetlerin eklenmesi ' de gerçekleşir `ConfigureServices` .

Kitaplık yazarı olarak varsayılan değerleri belirtmek size ait olur.

> [!NOTE]
> Yapılandırma bir seçenek örneğine bağlamak mümkündür. Ancak, ad çakışmalarının bir riski vardır; bu, hatalara neden olur. Ayrıca, bu şekilde el ile bağlama yaparken, seçenek deseninin kullanımını-bir kez olacak şekilde sınırlayabilirsiniz. Bu tür müşteriler [ıoptionsmonitor](options.md#ioptionsmonitor) arabirimini kullanamayacak şekilde ayarlarda yapılan değişiklikler yeniden bağlanmayacak.
>
> ```csharp
> services.AddOptions<LibraryOptions>()
>     .Configure<IConfiguration>(
>         (options, configuration) =>
>             configuration.GetSection("LibraryOptions").Bind(options));
> ```

## <a name="actiontoptions-parameter"></a>`Action<TOptions>` parametresinin

Kitaplığınızın tüketicileri, seçenek sınıfınızın bir örneğini veren bir lambda ifadesi sağlamaya yönelik olabilir. Bu senaryoda, `Action<LibraryOptions>` uzantı yönteminizin bir parametresini tanımlarsınız.

:::code language="csharp" source="snippets/configuration/options-action/ServiceCollectionExtensions.cs" highlight="10,12":::

Yukarıdaki kodda `AddMyLibraryService` :

- Bir örneğini genişletir <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>
- Bir <xref:System.Action%601> WHERE `T` `LibraryOptions` parametresi tanımlar `configureOptions`
- <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A>Eyleme verilen çağrılar `configureOptions`

Bu düzendeki tüketiciler bir lambda ifadesi (veya parametresini karşılayan bir temsilci `Action<LibraryOptions>` ) sağlar:

:::code language="csharp" source="snippets/configuration/options-action/Program.cs" highlight="22-26":::

## <a name="options-instance-parameter"></a>Seçenek örneği parametresi

Kitaplığınızın tüketicileri satır içine alınmış seçenekler örneği sağlamayı tercih edebilir. Bu senaryoda, Seçenekler nesnenizin bir örneğini alan bir genişletme yöntemi kullanıma sunacaksınız `LibraryOptions` .

:::code language="csharp" source="snippets/configuration/options-object/ServiceCollectionExtensions.cs" highlight="9,11-17":::

Yukarıdaki kodda `AddMyLibraryService` :

- Bir örneğini genişletir <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>
- <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType>Tür parametresine sahip çağrılar`LibraryOptions`
- <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A>Belirtilen örnekten geçersiz kılınabilen varsayılan seçenek değerlerini belirten öğesine bir çağrısını zincirler `userOptions`

Bu düzendeki tüketiciler `LibraryOptions` , istenen özellik değerlerini satır içi olarak tanımlayarak sınıfının bir örneğini sağlar:

:::code language="csharp" source="snippets/configuration/options-object/Program.cs" highlight="22-26":::

## <a name="post-configuration"></a>Yapılandırma sonrası

Tüm yapılandırma seçeneği değerleri bağlandıktan veya belirtilmişse, yapılandırma sonrası işlevselliği kullanılabilir. Daha önce ayrıntılanmış aynı [ `Action<TOptions>` parametreyi](#actiontoptions-parameter) açığa çıkarmak için aramayı seçebilirsiniz <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A> . Tüm çağrılardan sonra son yapılandırma çalıştırmaları `.Configure` .

:::code language="csharp" source="snippets/configuration/options-postconfig/ServiceCollectionExtensions.cs" highlight="10,12":::

Yukarıdaki kodda `AddMyLibraryService` :

- Bir örneğini genişletir <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>
- Bir <xref:System.Action%601> WHERE `T` `LibraryOptions` parametresi tanımlar `configureOptions`
- <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A>Eyleme verilen çağrılar `configureOptions`

Bu düzendeki tüketiciler `Action<LibraryOptions>` , `Action<TOptions>` Post olmayan bir yapılandırma senaryosunda bir lambda ifadesi (veya parametreyi karşılayan bir temsilci) sağlar:

:::code language="csharp" source="snippets/configuration/options-postconfig/Program.cs" highlight="22-26":::

## <a name="see-also"></a>Ayrıca bkz.

- [.NET 'teki seçenek kalıbı](options.md)
- [.NET 'e bağımlılık ekleme](dependency-injection.md)
- [Bağımlılık ekleme yönergeleri](dependency-injection-guidelines.md)
