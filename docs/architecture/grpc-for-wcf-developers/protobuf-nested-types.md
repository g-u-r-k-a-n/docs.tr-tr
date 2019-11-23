---
title: Prototipsiz iç içe türler-WCF geliştiricileri için gRPC
description: Prototip ve gRPC 'de iç içe geçmiş ileti türleri hakkında bilgi edinin ve bunların içinde C#nasıl oluşturulduğunu öğrenin.
ms.date: 09/09/2019
ms.openlocfilehash: bbc7ed41516d29f867bbc9da5b258f6a3c9ff261
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967397"
---
# <a name="protobuf-nested-types"></a><span data-ttu-id="a20c1-103">Protobuf iç içe türleri</span><span class="sxs-lookup"><span data-stu-id="a20c1-103">Protobuf nested types</span></span>

<span data-ttu-id="a20c1-104">Benzer C# şekilde, diğer sınıfların içindeki sınıfları bildirmenize olanak tanır, protoarabellek ileti tanımlarını diğer iletiler içinde iç içe almanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a20c1-104">Just like C# allows you to declare classes inside other classes, Protobuf allows you to nest message definitions within other messages.</span></span> <span data-ttu-id="a20c1-105">Aşağıdaki örnek, iç içe geçmiş ileti türlerinin nasıl oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="a20c1-105">The following example shows how to create nested message types:</span></span>

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

<span data-ttu-id="a20c1-106">Oluşturulan C# kodda, `Inner` türü `HelloRequest` sınıfı içindeki iç içe statik `Types` sınıfında bildirilecektir:</span><span class="sxs-lookup"><span data-stu-id="a20c1-106">In the generated C# code, the `Inner` type will be declared in a nested static `Types` class within the `HelloRequest` class:</span></span>

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
><span data-ttu-id="a20c1-107">[Önceki](protobuf-data-types.md)
>[İleri](protobuf-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="a20c1-107">[Previous](protobuf-data-types.md)
[Next](protobuf-repeated.md)</span></span>
