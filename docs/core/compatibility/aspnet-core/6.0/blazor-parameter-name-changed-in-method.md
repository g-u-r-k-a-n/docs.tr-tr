---
title: 'Son değişiklik: Blazor: parametre adı, talep Estimagefileasync yönteminde değiştirildi'
description: "Blazor başlıklı ASP.NET Core 6,0 ' deki Son değişiklik hakkında bilgi edinin: parametre adı, karşılandığından Estimagefileasync yönteminde değiştirildi"
ms.author: scaddie
ms.date: 02/09/2021
ms.openlocfilehash: 645b53e341507ffd9f369eea1b940232b7c14770
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255187"
---
# <a name="blazor-parameter-name-changed-in-requestimagefileasync-method"></a>Blazor: parametre adı, talep Estimagefileasync yönteminde değiştirildi

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
