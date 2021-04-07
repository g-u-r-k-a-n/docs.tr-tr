---
title: "Son değişiklik: Microsoft.AspNetCore.App Shared Framework 'ten kaldırılan derlemeler"
description: Microsoft.AspNetCore.App paylaşılan çerçevesinden kaldırılan bazı derlemelerin ASP.NET Core 6,0 ' deki Son değişiklik hakkında bilgi edinin.
ms.date: 04/02/2021
ms.openlocfilehash: 0db8af4690b0558b1ceae2881b45ce78cb23782b
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106499103"
---
# <a name="assemblies-removed-from-microsoftaspnetcoreapp-shared-framework"></a>Microsoft.AspNetCore.App paylaşılan çerçevesinden kaldırılan derlemeler

Aşağıdaki iki derleme ASP.NET Core hedefleme paketinden kaldırılmıştır:

- System. Security. Permissions
- System. Windows. Extensions

Ayrıca, aşağıdaki derlemeler ASP.NET Core çalışma zamanı paketinden kaldırılmıştır:

- Microsoft.Win32.SystemEvents
- System. Drawing. Common
- System. Security. Permissions
- System. Windows. Extensions

## <a name="version-introduced"></a>Sunulan sürüm

6.0

## <a name="old-behavior"></a>Eski davranış

Uygulamalar, [Microsoft.AspNetCore.app](/aspnet/core/fundamentals/metapackage-app) paylaşılan çerçevesine başvurarak bu kitaplıklar tarafından sunulan API 'leri kullanabilir.

## <a name="new-behavior"></a>Yeni davranış

Etkilenen derlemelerden API 'Leri, proje dosyanızda [Packagereference](../../../project-sdk/msbuild-props.md#packagereference) olmadan kullanırsanız, çalışma zamanı hataları görebilirsiniz. Örneğin, pakete açık bir başvuru eklemeden bu derlemelerden birindeki API 'Lere erişmek için yansıma kullanan bir uygulama, çalışma zamanı hatalarına sahip olur. , `PackageReference` Derlemelerin uygulama çıktısının bir parçası olarak mevcut olmasını sağlar.

## <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, ASP.NET Core paylaşılan çerçevesinin boyutunu azaltmak için sunulmuştur.

## <a name="recommended-action"></a>Önerilen eylem

Bu API 'Leri projenizde kullanmaya devam etmek için bir [Packagereference](../../../project-sdk/msbuild-props.md#packagereference)ekleyin. Örnek:

```xml
<PackageReference Include="System.Security.Permissions" Version="6.0.0" />
```

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Permissions?displayProperty=fullName>
- <xref:System.Media?displayProperty=fullName>
- <xref:System.Security.Cryptography.X509Certificates.X509Certificate2UI?displayProperty=fullName>
- <xref:System.Xaml.Permissions.XamlAccessLevel?displayProperty=fullName>

<!--

## Category

ASP.NET Core

## Affected APIs

- `N:System.Security.Permissions`
- `N:System.Media`
- `N:System.Security.Cryptography.X509Certificates.X509Certificate2UI`
- `N:System.Xaml.Permissions.XamlAccessLevel`

-->
