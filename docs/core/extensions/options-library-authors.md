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
# <a name="options-pattern-guidance-for-net-library-authors"></a><span data-ttu-id="8c36d-103">.NET kitaplığı yazarları için seçenekler model Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8c36d-103">Options pattern guidance for .NET library authors</span></span>

<span data-ttu-id="8c36d-104">Bağımlılık ekleme yardımı ile hizmetlerinizi kaydetme ve ilgili yapılandırmaların, *Seçenekler deseninin* kullanımını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c36d-104">With the help of dependency injection, registering your services and their corresponding configurations can make use of the *options pattern*.</span></span> <span data-ttu-id="8c36d-105">Seçenekler stili, kitaplığınızdaki tüketicilere (ve hizmetlerinizde), Seçenekler sınıfınız olduğu durumlarda [seçenek arayüzlerinin](options.md#options-interfaces) örneklerinin olmasını sağlar `TOptions` .</span><span class="sxs-lookup"><span data-stu-id="8c36d-105">The options pattern enables consumers of your library (and your services) to require instances of [options interfaces](options.md#options-interfaces) where `TOptions` is your options class.</span></span> <span data-ttu-id="8c36d-106">Kesin olarak belirlenmiş nesneler aracılığıyla yapılandırma seçeneklerini kullanmak tutarlı değer gösterimi sağlanmasına yardımcı olur ve dize değerlerini el ile ayrıştırma yükünü ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8c36d-106">Consuming configuration options through strongly-typed objects helps to ensure consistent value representation, and removes the burden of manually parsing string values.</span></span> <span data-ttu-id="8c36d-107">Kitaplığınızın kullanacağı tüketicilere yönelik birçok [yapılandırma sağlayıcısı](configuration-providers.md) vardır.</span><span class="sxs-lookup"><span data-stu-id="8c36d-107">There are many [configuration providers](configuration-providers.md) for consumers of your library to use.</span></span> <span data-ttu-id="8c36d-108">Bu sağlayıcılar sayesinde, müşteriler kitaplığınızı birçok şekilde yapılandırabilir.</span><span class="sxs-lookup"><span data-stu-id="8c36d-108">With these providers, consumers can configure your library in many ways.</span></span>

<span data-ttu-id="8c36d-109">.NET kitaplığı yazarı olarak, kitaplığınızdaki tüketicilere seçenekler deseninin doğru bir şekilde kullanıma sunulmasına ilişkin genel rehberlik öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="8c36d-109">As a .NET library author, you'll learn general guidance on how to correctly expose the options pattern to consumers of your library.</span></span> <span data-ttu-id="8c36d-110">Aynı şeyi gerçekleştirmenin çeşitli yolları ve yapmanız gereken birkaç nokta vardır.</span><span class="sxs-lookup"><span data-stu-id="8c36d-110">There are various ways to achieve the same thing, and several considerations to make.</span></span>

## <a name="naming-conventions"></a><span data-ttu-id="8c36d-111">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="8c36d-111">Naming conventions</span></span>

<span data-ttu-id="8c36d-112">Kurala göre, hizmetlerin kaydolmasından sorumlu uzantı yöntemleri adlandırılır `Add{Service}` ; burada `{Service}` anlamlı ve açıklayıcı bir addır.</span><span class="sxs-lookup"><span data-stu-id="8c36d-112">By convention, extension methods responsible for registering services are named `Add{Service}`, where `{Service}` is a meaningful and descriptive name.</span></span> <span data-ttu-id="8c36d-113">Pakete bağlı olarak, hizmet kaydına `Use{Service}` Uzantı yöntemleri eşlik edebilir.</span><span class="sxs-lookup"><span data-stu-id="8c36d-113">Depending on the package, the registration of services may be accompanied by `Use{Service}` extension methods.</span></span> <span data-ttu-id="8c36d-114">`Use{Service}`Uzantı yöntemleri [ASP.NET Core](/aspnet).</span><span class="sxs-lookup"><span data-stu-id="8c36d-114">The `Use{Service}` extension methods are commonplace in [ASP.NET Core](/aspnet).</span></span>

<span data-ttu-id="8c36d-115">✔️ diğer tekliflerden hizmetinizi ayırt eden adları göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="8c36d-115">✔️ CONSIDER names that disambiguate your service from other offerings.</span></span>

<span data-ttu-id="8c36d-116">❌ Resmi Microsoft paketlerinde .NET ekosisteminin zaten bir parçası olan adlar kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="8c36d-116">❌ DO NOT use names that are already part of the .NET ecosystem from official Microsoft packages.</span></span>

<span data-ttu-id="8c36d-117">✔️ Uzantı yöntemlerini kullanıma sunan statik sınıfların `{Type}Extensions` `{Type}` adlandırılırsınız, burada, genişletmenin türü.</span><span class="sxs-lookup"><span data-stu-id="8c36d-117">✔️ CONSIDER naming static classes that expose extension methods as `{Type}Extensions`, where `{Type}` is the type that you're extending.</span></span>

### <a name="namespace-guidance"></a><span data-ttu-id="8c36d-118">Ad alanı Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8c36d-118">Namespace guidance</span></span>

<span data-ttu-id="8c36d-119">Microsoft paketleri `Microsoft.Extensions.DependencyInjection` çeşitli hizmet tekliflerinin kaydını yapmak için ad alanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="8c36d-119">Microsoft packages make use of the `Microsoft.Extensions.DependencyInjection` namespace to unify the registration of various service offerings.</span></span>

<span data-ttu-id="8c36d-120">✔️, paket teklifinizi açıkça tanımlayan bir ad alanı düşünün.</span><span class="sxs-lookup"><span data-stu-id="8c36d-120">✔️ CONSIDER a namespace that clearly identifies your package offering.</span></span>

<span data-ttu-id="8c36d-121">❌`Microsoft.Extensions.DependencyInjection`Resmi olmayan Microsoft paketleri için ad alanını kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="8c36d-121">❌ DO NOT use the `Microsoft.Extensions.DependencyInjection` namespace for non-official Microsoft packages.</span></span>

## <a name="parameterless"></a><span data-ttu-id="8c36d-122">İçermeyen</span><span class="sxs-lookup"><span data-stu-id="8c36d-122">Parameterless</span></span>

<span data-ttu-id="8c36d-123">Hizmetiniz en az bir açık yapılandırma olmadan veya açık yapılandırma olmadan çalışacağından parametresiz bir genişletme yöntemi düşünün.</span><span class="sxs-lookup"><span data-stu-id="8c36d-123">If your service can work with minimal or no explicit configuration, consider a parameterless extension method.</span></span>

:::code language="csharp" source="snippets/configuration/options-noparams/ServiceCollectionExtensions.cs" highlight="10-14":::

<span data-ttu-id="8c36d-124">Yukarıdaki kodda `AddMyLibraryService` :</span><span class="sxs-lookup"><span data-stu-id="8c36d-124">In the preceding code, the `AddMyLibraryService`:</span></span>

- <span data-ttu-id="8c36d-125">Bir örneğini genişletir <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span><span class="sxs-lookup"><span data-stu-id="8c36d-125">Extends an instance of <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span></span>
- <span data-ttu-id="8c36d-126"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType>Tür parametresine sahip çağrılar`LibraryOptions`</span><span class="sxs-lookup"><span data-stu-id="8c36d-126">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType> with the type parameter of `LibraryOptions`</span></span>
- <span data-ttu-id="8c36d-127"><xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A>Varsayılan seçenek değerlerini belirten öğesine bir çağrısını zincirler</span><span class="sxs-lookup"><span data-stu-id="8c36d-127">Chains a call to <xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A>, which specifies the default option values</span></span>

## <a name="iconfiguration-parameter"></a><span data-ttu-id="8c36d-128">`IConfiguration` parametresinin</span><span class="sxs-lookup"><span data-stu-id="8c36d-128">`IConfiguration` parameter</span></span>

<span data-ttu-id="8c36d-129">Tüketiciler için çok sayıda seçenek sunan bir kitaplık yazdığınızda bir `IConfiguration` parametre genişletme yöntemi yapmayı düşünmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c36d-129">When you author a library that exposes many options to consumers, you may want to consider requiring an `IConfiguration` parameter extension method.</span></span> <span data-ttu-id="8c36d-130">Beklenen `IConfiguration` örnek, işlevini kullanarak yapılandırmanın adlandırılmış bir bölümüne kapsam içermelidir <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8c36d-130">The expected `IConfiguration` instance should be scoped to a named section of the configuration by using the <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A?displayProperty=nameWithType> function.</span></span>

:::code language="csharp" source="snippets/configuration/options-configparam/ServiceCollectionExtensions.cs" highlight="10,12-14":::

<span data-ttu-id="8c36d-131">Yukarıdaki kodda `AddMyLibraryService` :</span><span class="sxs-lookup"><span data-stu-id="8c36d-131">In the preceding code, the `AddMyLibraryService`:</span></span>

- <span data-ttu-id="8c36d-132">Bir örneğini genişletir <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span><span class="sxs-lookup"><span data-stu-id="8c36d-132">Extends an instance of <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span></span>
- <span data-ttu-id="8c36d-133">Bir <xref:Microsoft.Extensions.Configuration.IConfiguration> parametreyi tanımlar `namedConfigurationSection`</span><span class="sxs-lookup"><span data-stu-id="8c36d-133">Defines an <xref:Microsoft.Extensions.Configuration.IConfiguration> parameter `namedConfigurationSection`</span></span>
- <span data-ttu-id="8c36d-134"><xref:Microsoft.Extensions.DependencyInjection.OptionsConfigurationServiceCollectionExtensions.Configure%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection,Microsoft.Extensions.Configuration.IConfiguration)>Öğesinin genel tür parametresini `LibraryOptions` ve `namedConfigurationSection` yapılandırılacak örneği geçen çağrılar</span><span class="sxs-lookup"><span data-stu-id="8c36d-134">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsConfigurationServiceCollectionExtensions.Configure%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection,Microsoft.Extensions.Configuration.IConfiguration)> passing the generic type parameter of `LibraryOptions` and the `namedConfigurationSection` instance to configure</span></span>

<span data-ttu-id="8c36d-135">Bu düzendeki tüketiciler, `IConfiguration` adlandırılmış bölümün kapsamlı örneğini sağlar:</span><span class="sxs-lookup"><span data-stu-id="8c36d-135">Consumers in this pattern provide the scoped `IConfiguration` instance of the named section:</span></span>

:::code language="csharp" source="snippets/configuration/options-configparam/Program.cs" highlight="22-23":::

<span data-ttu-id="8c36d-136">Çağrısı `.AddMyLibraryService` <xref:Microsoft.Extensions.Hosting.IHostBuilder.ConfigureServices%2A> yönteminde yapılır.</span><span class="sxs-lookup"><span data-stu-id="8c36d-136">The call to `.AddMyLibraryService` is made in the <xref:Microsoft.Extensions.Hosting.IHostBuilder.ConfigureServices%2A> method.</span></span> <span data-ttu-id="8c36d-137">Aynı değer, bir `Startup` sınıfı kullanırken, kaydedilecek hizmetlerin eklenmesi ' de gerçekleşir `ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="8c36d-137">The same is true when using a `Startup` class, the addition of services being registered occurs in `ConfigureServices`.</span></span>

<span data-ttu-id="8c36d-138">Kitaplık yazarı olarak varsayılan değerleri belirtmek size ait olur.</span><span class="sxs-lookup"><span data-stu-id="8c36d-138">As the library author, specifying default values is up to you.</span></span>

> [!NOTE]
> <span data-ttu-id="8c36d-139">Yapılandırma bir seçenek örneğine bağlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="8c36d-139">It is possible to bind configuration to an options instance.</span></span> <span data-ttu-id="8c36d-140">Ancak, ad çakışmalarının bir riski vardır; bu, hatalara neden olur.</span><span class="sxs-lookup"><span data-stu-id="8c36d-140">However, there is a risk of name collisions - which will cause errors.</span></span> <span data-ttu-id="8c36d-141">Ayrıca, bu şekilde el ile bağlama yaparken, seçenek deseninin kullanımını-bir kez olacak şekilde sınırlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c36d-141">Additionally, when manually binding in this way, you limit the consumption of your options pattern to read-once.</span></span> <span data-ttu-id="8c36d-142">Bu tür müşteriler [ıoptionsmonitor](options.md#ioptionsmonitor) arabirimini kullanamayacak şekilde ayarlarda yapılan değişiklikler yeniden bağlanmayacak.</span><span class="sxs-lookup"><span data-stu-id="8c36d-142">Changes to settings will not be re-bound, as such consumers will not be able to use the [IOptionsMonitor](options.md#ioptionsmonitor) interface.</span></span>
>
> ```csharp
> services.AddOptions<LibraryOptions>()
>     .Configure<IConfiguration>(
>         (options, configuration) =>
>             configuration.GetSection("LibraryOptions").Bind(options));
> ```

## <a name="actiontoptions-parameter"></a><span data-ttu-id="8c36d-143">`Action<TOptions>` parametresinin</span><span class="sxs-lookup"><span data-stu-id="8c36d-143">`Action<TOptions>` parameter</span></span>

<span data-ttu-id="8c36d-144">Kitaplığınızın tüketicileri, seçenek sınıfınızın bir örneğini veren bir lambda ifadesi sağlamaya yönelik olabilir.</span><span class="sxs-lookup"><span data-stu-id="8c36d-144">Consumers of your library may be interested in providing a lambda expression that yields an instance of your options class.</span></span> <span data-ttu-id="8c36d-145">Bu senaryoda, `Action<LibraryOptions>` uzantı yönteminizin bir parametresini tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="8c36d-145">In this scenario, you define an `Action<LibraryOptions>` parameter in your extension method.</span></span>

:::code language="csharp" source="snippets/configuration/options-action/ServiceCollectionExtensions.cs" highlight="10,12":::

<span data-ttu-id="8c36d-146">Yukarıdaki kodda `AddMyLibraryService` :</span><span class="sxs-lookup"><span data-stu-id="8c36d-146">In the preceding code, the `AddMyLibraryService`:</span></span>

- <span data-ttu-id="8c36d-147">Bir örneğini genişletir <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span><span class="sxs-lookup"><span data-stu-id="8c36d-147">Extends an instance of <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span></span>
- <span data-ttu-id="8c36d-148">Bir <xref:System.Action%601> WHERE `T` `LibraryOptions` parametresi tanımlar `configureOptions`</span><span class="sxs-lookup"><span data-stu-id="8c36d-148">Defines an <xref:System.Action%601> where `T` is `LibraryOptions` parameter `configureOptions`</span></span>
- <span data-ttu-id="8c36d-149"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A>Eyleme verilen çağrılar `configureOptions`</span><span class="sxs-lookup"><span data-stu-id="8c36d-149">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A> given the `configureOptions` action</span></span>

<span data-ttu-id="8c36d-150">Bu düzendeki tüketiciler bir lambda ifadesi (veya parametresini karşılayan bir temsilci `Action<LibraryOptions>` ) sağlar:</span><span class="sxs-lookup"><span data-stu-id="8c36d-150">Consumers in this pattern provide a lambda expression (or a delegate that satisfies the `Action<LibraryOptions>` parameter):</span></span>

:::code language="csharp" source="snippets/configuration/options-action/Program.cs" highlight="22-26":::

## <a name="options-instance-parameter"></a><span data-ttu-id="8c36d-151">Seçenek örneği parametresi</span><span class="sxs-lookup"><span data-stu-id="8c36d-151">Options instance parameter</span></span>

<span data-ttu-id="8c36d-152">Kitaplığınızın tüketicileri satır içine alınmış seçenekler örneği sağlamayı tercih edebilir.</span><span class="sxs-lookup"><span data-stu-id="8c36d-152">Consumers of your library might prefer to provide an inlined options instance.</span></span> <span data-ttu-id="8c36d-153">Bu senaryoda, Seçenekler nesnenizin bir örneğini alan bir genişletme yöntemi kullanıma sunacaksınız `LibraryOptions` .</span><span class="sxs-lookup"><span data-stu-id="8c36d-153">In this scenario, you expose an extension method that takes an instance of your options object, `LibraryOptions`.</span></span>

:::code language="csharp" source="snippets/configuration/options-object/ServiceCollectionExtensions.cs" highlight="9,11-17":::

<span data-ttu-id="8c36d-154">Yukarıdaki kodda `AddMyLibraryService` :</span><span class="sxs-lookup"><span data-stu-id="8c36d-154">In the preceding code, the `AddMyLibraryService`:</span></span>

- <span data-ttu-id="8c36d-155">Bir örneğini genişletir <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span><span class="sxs-lookup"><span data-stu-id="8c36d-155">Extends an instance of <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span></span>
- <span data-ttu-id="8c36d-156"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType>Tür parametresine sahip çağrılar`LibraryOptions`</span><span class="sxs-lookup"><span data-stu-id="8c36d-156">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%60%601(Microsoft.Extensions.DependencyInjection.IServiceCollection)?displayProperty=nameWithType> with the type parameter of `LibraryOptions`</span></span>
- <span data-ttu-id="8c36d-157"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A>Belirtilen örnekten geçersiz kılınabilen varsayılan seçenek değerlerini belirten öğesine bir çağrısını zincirler `userOptions`</span><span class="sxs-lookup"><span data-stu-id="8c36d-157">Chains a call to <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.Configure%2A>, which specifies default option values that can be overridden from the given `userOptions` instance</span></span>

<span data-ttu-id="8c36d-158">Bu düzendeki tüketiciler `LibraryOptions` , istenen özellik değerlerini satır içi olarak tanımlayarak sınıfının bir örneğini sağlar:</span><span class="sxs-lookup"><span data-stu-id="8c36d-158">Consumers in this pattern provide an instance of the `LibraryOptions` class, defining desired property values inline:</span></span>

:::code language="csharp" source="snippets/configuration/options-object/Program.cs" highlight="22-26":::

## <a name="post-configuration"></a><span data-ttu-id="8c36d-159">Yapılandırma sonrası</span><span class="sxs-lookup"><span data-stu-id="8c36d-159">Post configuration</span></span>

<span data-ttu-id="8c36d-160">Tüm yapılandırma seçeneği değerleri bağlandıktan veya belirtilmişse, yapılandırma sonrası işlevselliği kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8c36d-160">After all configuration option values are bound or specified, post configuration functionality is available.</span></span> <span data-ttu-id="8c36d-161">Daha önce ayrıntılanmış aynı [ `Action<TOptions>` parametreyi](#actiontoptions-parameter) açığa çıkarmak için aramayı seçebilirsiniz <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A> .</span><span class="sxs-lookup"><span data-stu-id="8c36d-161">Exposing the same [`Action<TOptions>` parameter](#actiontoptions-parameter) detailed earlier, you could choose to call <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A>.</span></span> <span data-ttu-id="8c36d-162">Tüm çağrılardan sonra son yapılandırma çalıştırmaları `.Configure` .</span><span class="sxs-lookup"><span data-stu-id="8c36d-162">Post configure runs after all `.Configure` calls.</span></span>

:::code language="csharp" source="snippets/configuration/options-postconfig/ServiceCollectionExtensions.cs" highlight="10,12":::

<span data-ttu-id="8c36d-163">Yukarıdaki kodda `AddMyLibraryService` :</span><span class="sxs-lookup"><span data-stu-id="8c36d-163">In the preceding code, the `AddMyLibraryService`:</span></span>

- <span data-ttu-id="8c36d-164">Bir örneğini genişletir <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span><span class="sxs-lookup"><span data-stu-id="8c36d-164">Extends an instance of <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection></span></span>
- <span data-ttu-id="8c36d-165">Bir <xref:System.Action%601> WHERE `T` `LibraryOptions` parametresi tanımlar `configureOptions`</span><span class="sxs-lookup"><span data-stu-id="8c36d-165">Defines an <xref:System.Action%601> where `T` is `LibraryOptions` parameter `configureOptions`</span></span>
- <span data-ttu-id="8c36d-166"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A>Eyleme verilen çağrılar `configureOptions`</span><span class="sxs-lookup"><span data-stu-id="8c36d-166">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigure%2A> given the `configureOptions` action</span></span>

<span data-ttu-id="8c36d-167">Bu düzendeki tüketiciler `Action<LibraryOptions>` , `Action<TOptions>` Post olmayan bir yapılandırma senaryosunda bir lambda ifadesi (veya parametreyi karşılayan bir temsilci) sağlar:</span><span class="sxs-lookup"><span data-stu-id="8c36d-167">Consumers in this pattern provide a lambda expression (or a delegate that satisfies the `Action<LibraryOptions>` parameter), just as they would with the [`Action<TOptions>` parameter] in a non-post configuration scenario:</span></span>

:::code language="csharp" source="snippets/configuration/options-postconfig/Program.cs" highlight="22-26":::

## <a name="see-also"></a><span data-ttu-id="8c36d-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c36d-168">See also</span></span>

- [<span data-ttu-id="8c36d-169">.NET 'teki seçenek kalıbı</span><span class="sxs-lookup"><span data-stu-id="8c36d-169">Options pattern in .NET</span></span>](options.md)
- [<span data-ttu-id="8c36d-170">.NET 'e bağımlılık ekleme</span><span class="sxs-lookup"><span data-stu-id="8c36d-170">Dependency injection in .NET</span></span>](dependency-injection.md)
- [<span data-ttu-id="8c36d-171">Bağımlılık ekleme yönergeleri</span><span class="sxs-lookup"><span data-stu-id="8c36d-171">Dependency injection guidelines</span></span>](dependency-injection-guidelines.md)
