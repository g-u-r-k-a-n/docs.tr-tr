---
title: 'Son değişiklik: Blazor : parametre adı, talep Estimagefileasync yönteminde değiştirildi'
description: "ASP.NET Core 6,0 ' deki Son değişiklik hakkında bilgi edinin Blazor : talep tahmini Gefileasync yönteminde parametre adı değiştirildi"
no-loc:
- Blazor
ms.author: scaddie
ms.date: 02/09/2021
ms.openlocfilehash: 06fe2b0cff17630e09da3f80c506684f1b26e9d4
ms.sourcegitcommit: fdfa01f6cd3aa4c36b6e8a1830693ff22d35aeea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107292281"
---
# <a name="blazor-parameter-name-changed-in-requestimagefileasync-method"></a>Blazor: Parametre adı, karşılandığından Estimagefileasync yönteminde değiştirildi

`RequestImageFileAsync`Yöntemin `maxWith` parametresi olarak yeniden adlandırıldı `maxWith` `maxWidth` .

## <a name="version-introduced"></a>Sunulan sürüm

ASP.NET Core 6,0 Preview 1

## <a name="old-behavior"></a>Eski davranış

Parametre adı yazılmış `maxWith` .

## <a name="new-behavior"></a>Yeni davranış

Parametre adı yazılmış `maxWidth` .

## <a name="reason-for-change"></a>Değişiklik nedeni

Özgün parametre adı bir yazım hatası idi.

## <a name="recommended-action"></a>Önerilen eylem

API 'de adlandırılmış parametreler kullanıyorsanız `RequestImageFile` , `maxWith` parametre adını olarak güncelleştirin `maxWidth` . Aksi takdirde, hiçbir değişiklik gerekli değildir.

## <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Components.Forms.BrowserFileExtensions.RequestImageFileAsync%2A?displayProperty=nameWithType>

<!--

## Category

ASP.NET Core

## Affected APIs

`Overload:Microsoft.AspNetCore.Components.Forms.BrowserFileExtensions.RequestImageFileAsync`

-->
