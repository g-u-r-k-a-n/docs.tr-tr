---
title: .NET ' te bağımlılık ekleme 'yi kullanma
description: .NET uygulamalarınıza bağımlılık ekleme işlemini nasıl kullanacağınızı öğrenin.
author: IEvangelist
ms.author: dapine
ms.date: 11/13/2020
ms.topic: tutorial
no-loc:
- Transient
- Scoped
- Singleton
- Example
ms.openlocfilehash: b1e84685ad95372c4b2038e913199f7283135b71
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634520"
---
# <a name="tutorial-use-dependency-injection-in-net"></a>Öğretici: .NET 'te bağımlılık ekleme kullanma

Bu öğreticide [, .net 'te bağımlılık ekleme (dı)](dependency-injection.md)'nin nasıl kullanılacağı gösterilmektedir. *Microsoft uzantıları* ile,, hizmetlerin bir içinde eklendiği ve yapılandırıldığı birinci sınıf bir vatandaşlık <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> . <xref:Microsoft.Extensions.Hosting.IHost>Arabirim, <xref:System.IServiceProvider> Tüm kayıtlı hizmetlerin kapsayıcısı olarak davranan örneği kullanıma sunar.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
>
> - Bağımlılık ekleme 'yi kullanan bir .NET konsol uygulaması oluşturma
> - [Genel bir konak](generic-host.md) oluşturma ve yapılandırma
> - Çeşitli arabirimler ve ilgili uygulamalar yazın
> - Dı için hizmet ömrünü ve kapsamını kullanma

## <a name="prerequisites"></a>Önkoşullar

- [.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core) veya üzeri.
- Yeni .NET uygulamaları oluşturma ve NuGet paketleri yükleme hakkında benzerlik.

## <a name="create-a-new-console-application"></a>Yeni bir konsol uygulaması oluşturma

[DotNet New](../tools/dotnet-new.md) komutunu ya da IDE yeni proje sihirbazını kullanarak **Example consoledi** adlı yeni bir .NET konsol uygulaması oluşturun. Projeye [Microsoft. Extensions. Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet paketini ekleyin.

## <a name="add-interfaces"></a>Arabirim Ekle

Aşağıdaki arayüzleri proje kök dizinine ekleyin:

*IOperation.cs*

:::code language="csharp" source="snippets/configuration/console-di/IOperation.cs":::

`IOperation`Arabirim tek bir özelliği tanımlar `OperationId` .

*I Transient Operation.cs*

::: Code Language = "CSharp" Source = "parçacıklar/Configuration/Console-dı/ı Transient Operation.cs":::

*I Scoped Operation.cs*

::: Code Language = "CSharp" Source = "parçacıklar/Configuration/Console-dı/ı Scoped Operation.cs":::

*I Singleton Operation.cs*

::: Code Language = "CSharp" Source = "parçacıklar/Configuration/Console-dı/ı Singleton Operation.cs":::

Tüm alt arabirimlerin `IOperation` amaçlanan hizmet ömrünü adlandırın. Örneğin, " Transient " veya " Singleton ".

## <a name="add-default-implementation"></a>Varsayılan uygulama ekle

Çeşitli işlemler için aşağıdaki varsayılan uygulamayı ekleyin:

*DefaultOperation.cs*

:::code language="csharp" source="snippets/configuration/console-di/DefaultOperation.cs":::

, `DefaultOperation` Tüm adlandırılmış işaret arabirimlerini uygular ve `OperationId` Yeni bir genel benzersiz TANıMLAYıCıNıN (GUID) son dört karakterine özelliği başlatır.

## <a name="add-service-that-requires-di"></a>DI gerektiren hizmet ekleyin

Konsol uygulamasına bir hizmet olarak davranan aşağıdaki işlem günlükçüsü nesnesini ekleyin:

*OperationLogger.cs*

:::code language="csharp" source="snippets/configuration/console-di/OperationLogger.cs":::

,, Ve ' nin `OperationLogger` her birini gerektiren bir oluşturucu tanımlar, yani, `ITransientOperation` `IScopedOperation` ve `ISingletonOperation` . Nesnesi, tüketicinin belirli bir parametreyle işlemleri günlüğe açmasını sağlayan tek bir yöntem sunar `scope` . Çağrıldığında, `LogOperations` yöntemi her bir işlemin benzersiz tanımlayıcısını kapsam dizesi ve iletisiyle günlüğe kaydeder.

## <a name="register-services-for-di"></a>Dı için Hizmetleri Kaydet

Aşağıdaki kodla *program.cs* güncelleştirin:

:::code language="csharp" source="snippets/configuration/console-di/Program.cs" range="1-18,35-60" highlight="22-26":::

> Her `services.Add{SERVICE_NAME}` genişletme yöntemi, hizmetlerini ekler ve potansiyel olarak yapılandırır. Uygulamaların bu kuralı izlemesini öneririz. <xref:Microsoft.Extensions.DependencyInjection?displayProperty=fullName>Hizmet kaydı gruplarını kapsüllemek için uzantı yöntemlerini ad alanına yerleştirin. Dı uzantısı yöntemlerine ilişkin ad alanı bölümü de dahil olmak üzere `Microsoft.Extensions.DependencyInjection` :
>
> - Ek blokları eklemeden [IntelliSense](/visualstudio/ide/using-intellisense) 'de görüntülenmesine izin verir `using` .
> - `using` `Program` `Startup` Bu uzantı yöntemlerinin genellikle çağrıldığı, veya sınıflarında aşırı deyimleri engeller.

Uygulama:

- <xref:Microsoft.Extensions.Hosting.IHostBuilder> [Varsayılan bağlayıcı ayarlarına](generic-host.md#default-builder-settings)sahip bir örnek oluşturur.
- Hizmetleri yapılandırır ve bunlara karşılık gelen hizmet ömrüne ekler.
- <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build>Bir örneğini çağırır ve atar <xref:Microsoft.Extensions.Hosting.IHost> .
- Çağrılar `ExemplifyScoping` , öğesini geçirme <xref:Microsoft.Extensions.Hosting.IHost.Services?displayProperty=nameWithType> .

## <a name="conclusion"></a>Sonuç

Uygulama, aşağıdaki örneğe benzer bir çıktı görüntüler:

```console
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): ITransientOperation [ 80f4...Always different        ]
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): IScopedOperation    [ c878...Changes only with scope ]
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
...
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): ITransientOperation [ f3c0...Always different        ]
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): IScopedOperation    [ c878...Changes only with scope ]
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]

Scope 2-Call 1 .GetRequiredService<OperationLogger>(): ITransientOperation [ f9af...Always different        ]
Scope 2-Call 1 .GetRequiredService<OperationLogger>(): IScopedOperation    [ 2bd0...Changes only with scope ]
Scope 2-Call 1 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
...
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): ITransientOperation [ fa65...Always different        ]
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): IScopedOperation    [ 2bd0...Changes only with scope ]
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
```

Uygulama çıktısından aşağıdakileri görebilirsiniz:

- Transient işlemler her zaman farklıdır, hizmetin her alımı ile yeni bir örnek oluşturulur.
- Scoped işlemler yalnızca yeni bir kapsamla değiştirilir, ancak bir kapsam içinde aynı örneğidir.
- Singleton işlemler her zaman aynıdır, yeni bir örnek yalnızca bir kez oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

* [Bağımlılık ekleme yönergeleri](dependency-injection-guidelines.md)
* [ASP.NET Core bağımlılık ekleme](/aspnet/core/fundamentals/dependency-injection)
