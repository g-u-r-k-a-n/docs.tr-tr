---
title: .NET ' te özel bir günlüğe kaydetme sağlayıcısı uygulama
description: .NET uygulamalarınızda özel bir günlüğe kaydetme sağlayıcısı uygulamayı öğrenin.
author: IEvangelist
ms.author: dapine
ms.date: 04/07/2021
ms.topic: how-to
ms.openlocfilehash: 56dd3aa9962d2cdaf13df85960a99aab7b050477
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255135"
---
# <a name="implement-a-custom-logging-provider-in-net"></a>.NET ' te özel bir günlüğe kaydetme sağlayıcısı uygulama

Ortak günlük gereksinimlerine yönelik birçok [günlük sağlayıcısı](logging-providers.md) mevcuttur. <xref:Microsoft.Extensions.Logging.ILoggerProvider>Kullanılabilir sağlayıcılardan biri uygulama gereksinimlerinize uygun olmadığında bir özel uygulamanız gerekebilir. Bu makalede, konsolundaki günlükleri renklendirmeye yönelik olarak kullanılabilecek özel bir günlüğe kaydetme sağlayıcısını nasıl uygulayacağınızı öğreneceksiniz.

### <a name="sample-custom-logger-configuration"></a>Örnek özel günlükçü yapılandırması

Örnek, aşağıdaki yapılandırma türünü kullanarak günlük düzeyi ve olay KIMLIĞI başına farklı renk konsolu girdileri oluşturur:

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerConfiguration.cs":::

Yukarıdaki kod, varsayılan düzeyi olarak `Information` , rengine `Green` ve, `EventId` örtülü olarak ayarlanır `0` .

### <a name="create-the-custom-logger"></a>Özel günlükçü oluşturma

`ILogger`Uygulama kategorisi adı genellikle günlük kaynağıdır. Örneğin, günlükçü 'nin oluşturulduğu tür:

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs":::

Yukarıdaki kod:

- Kategori adı başına bir günlükçü örneği oluşturur.
- İade `_config.LogLevels.ContainsKey(logLevel)` eder `IsEnabled` , her birinin `logLevel` benzersiz bir günlükçü vardır. Günlükçüler aynı zamanda tüm daha yüksek günlük seviyeleri için de etkinleştirilmelidir:

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs" range="16-17":::

## <a name="custom-logger-provider"></a>Özel günlükçü sağlayıcısı

`ILoggerProvider`Nesne, günlükçü örnekleri oluşturmaktan sorumludur. Kategori başına bir günlükçü örneği oluşturmak gerekli değildir, ancak bu, NLog veya Log4net gibi bazı Günlükçüler için mantıklı olur. Bunu yaptığınızda, gerekirse kategori başına farklı günlüğe kaydetme çıkış hedeflerini de seçebilirsiniz:

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerProvider.cs":::

Yukarıdaki kodda, <xref:Microsoft.Build.Logging.LoggerDescription.CreateLogger%2A> Kategori başına adının tek bir örneğini oluşturur `ColorConsoleLogger` ve içinde depolar [`ConcurrentDictionary<TKey,TValue>`](/dotnet/api/system.collections.concurrent.concurrentdictionary-2) . Ayrıca, <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> temel nesnede yapılan değişiklikleri güncelleştirmek için arabirimi gereklidir `ColorConsoleLoggerConfiguration` .

## <a name="usage-and-registration-of-the-custom-logger"></a>Özel günlükçü kullanımı ve kaydı

Özel günlüğe kaydetme sağlayıcısını ve karşılık gelen günlükçüsü eklemek için, öğesinden bir ile öğesine ekleyin <xref:Microsoft.Extensions.Logging.ILoggerProvider> <xref:Microsoft.Extensions.Logging.ILoggingBuilder> <xref:Microsoft.Extensions.Hosting.HostingHostBuilderExtensions.ConfigureLogging(Microsoft.Extensions.Hosting.IHostBuilder,System.Action{Microsoft.Extensions.Logging.ILoggingBuilder})?displayProperty=nameWithType> :

:::code language="csharp" source="snippets/configuration/console-custom-logging/Program.cs" range="23-33":::

, `ILoggingBuilder` Bir veya daha fazla `ILogger` örnek oluşturur. `ILogger`Örnekler, bilgileri günlüğe kaydetmek için Framework tarafından kullanılır.

Kurala göre, üzerindeki genişletme yöntemleri `ILoggingBuilder` özel sağlayıcıyı kaydetmek için kullanılır:

:::code language="csharp" source="snippets/configuration/console-custom-logging/Extensions/ColorConsoleLoggerExtensions.cs":::

Bu basit uygulamayı çalıştırmak, renk çıkışını konsol penceresinde aşağıdaki görüntüye benzer şekilde işleyecek:

:::image type="content" source="media/color-console-logger.png" alt-text="Renk konsolu günlükçüsü örnek çıkışı":::

## <a name="see-also"></a>Ayrıca bkz.

- [.NET oturumu açma](logging.md)
- [.NET 'te günlüğe kaydetme sağlayıcıları](logging-providers.md)
- [.NET 'e bağımlılık ekleme](dependency-injection.md)
- [.NET 'te yüksek performanslı günlüğe kaydetme](high-performance-logging.md)
