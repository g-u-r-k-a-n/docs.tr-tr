---
title: Prototip için ayrılmış alanlar-WCF geliştiricileri için gRPC
description: Sürümler arası uyumluluk için ayrılmış alanlar hakkında bilgi edinin.
ms.date: 12/15/2020
ms.openlocfilehash: d82043d619c5b3b81091ae4ea381e4778c1cf6ba
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938526"
---
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="f4c37-103">Protobuf ayrılmış alanları</span><span class="sxs-lookup"><span data-stu-id="f4c37-103">Protobuf reserved fields</span></span>

<span data-ttu-id="f4c37-104">Protokol arabelleğindeki geri uyumluluk garantisi (Protobuffer), her zaman aynı veri öğesini temsil eden alan numaralarına dayanır.</span><span class="sxs-lookup"><span data-stu-id="f4c37-104">The backward-compatibility guarantees in Protocol Buffer (Protobuf) rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="f4c37-105">Bir alan, hizmetin yeni bir sürümündeki iletiden kaldırılırsa, bu alan numarası asla yeniden kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="f4c37-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="f4c37-106">Anahtar sözcüğünü kullanarak bu davranışı uygulayabilirsiniz `reserved` .</span><span class="sxs-lookup"><span data-stu-id="f4c37-106">You can enforce this behavior by using the `reserved` keyword.</span></span>

<span data-ttu-id="f4c37-107">`displayName`Ve `marketId` alanları `Stock` daha önce tanımlanan iletiden kaldırılmışsa, alan numaralarının aşağıdaki örnekte olduğu gibi ayrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4c37-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="f4c37-108">`reserved`Bu anahtar sözcüğünü, gelecekte eklenebilen alanlar için bir yer tutucu olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4c37-108">You can also use the `reserved` keyword as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="f4c37-109">Anahtar sözcüğünü kullanarak bitişik alan numaralarını bir Aralık olarak ifade edebilirsiniz `to` .</span><span class="sxs-lookup"><span data-stu-id="f4c37-109">You can express contiguous field numbers as a range by using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="f4c37-110">[Önceki](protobuf-repeated.md) 
> [Sonraki](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="f4c37-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
