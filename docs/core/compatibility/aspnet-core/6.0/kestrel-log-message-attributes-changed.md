---
title: 'Son değişiklik: Kestrel: günlük iletisi öznitelikleri değiştirildi'
description: "Kestrel başlıklı ASP.NET Core 6,0 ' deki Son değişiklik hakkında bilgi edinin: günlük iletisi öznitelikleri değiştirildi"
ms.author: scaddie
ms.date: 02/01/2021
ms.openlocfilehash: daeb9ae418f343a00e9563ef3e2b5090a7f016a9
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255174"
---
# <a name="kestrel-log-message-attributes-changed"></a>Kestrel: günlük iletisi öznitelikleri değiştirildi

Kestrel günlük iletilerinde ilişkili kimlikler ve adlar vardır. Bu öznitelikler farklı türlerde günlük iletilerini benzersiz şekilde tanımlar. Bu kimliklerin ve adların bazıları yanlış yinelenmiş. Bu çoğaltma sorunu ASP.NET Core 6,0 ' de düzeltildi.

## <a name="version-introduced"></a>Sunulan sürüm

ASP.NET Core 6,0

## <a name="old-behavior"></a>Eski davranış

Aşağıdaki tabloda ASP.NET Core 6,0 ' dan önce etkilenen günlük iletilerinin durumu gösterilmektedir.

| İleti açıklaması                   | Name                    | ID |
|---------------------------------------|-------------------------|----|
| HTTP/2 bağlantısı kapalı günlük iletileri | `Http2ConnectionClosed` | 36 |
| HTTP/2 çerçeve gönderme günlüğü iletileri     | `Http2FrameReceived`    | 37 |

## <a name="new-behavior"></a>Yeni davranış

Aşağıdaki tabloda ASP.NET Core 6,0 ' de etkilenen günlük iletilerinin durumu gösterilmektedir.

| İleti açıklaması                   | Name                    | ID |
|---------------------------------------|-------------------------|----|
| HTTP/2 bağlantısı kapalı günlük iletileri | `Http2ConnectionClosed` | 48 |
| HTTP/2 çerçeve gönderme günlüğü iletileri     | `Http2FrameSending`     | 49 |

## <a name="reason-for-change"></a>Değişiklik nedeni

Farklı ileti türlerinin belirlenebilmesi için günlük kimlikleri ve adları benzersiz olmalıdır.

## <a name="recommended-action"></a>Önerilen eylem

Eski kimliklere ve adlara başvuruda bulunan kod veya yapılandırmaya sahipseniz, bu başvuruları yeni kimlikleri ve adları kullanacak şekilde güncelleştirin.

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis

-->
