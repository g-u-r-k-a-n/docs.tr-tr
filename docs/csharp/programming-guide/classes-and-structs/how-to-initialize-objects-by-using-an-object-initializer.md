---
title: Nesne Başlatıcısı kullanarak nesneleri başlatma-C# Programlama Kılavuzu
description: Nesne başlatıcılarının, bir Oluşturucu çağırmadan C# dilinde tür nesnelerini başlatmak için nasıl kullanılacağını öğrenin. Anonim bir tür tanımlamak için bir nesne başlatıcısı kullanın.
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 0c2d38713a1fdefd922234a02e23518c0f00add5
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512788"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="1cdfd-104">Nesne Başlatıcısı kullanarak nesneleri başlatma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="1cdfd-104">How to initialize objects by using an object initializer (C# Programming Guide)</span></span>

<span data-ttu-id="1cdfd-105">Tür nesnelerini, tür için açıkça bir Oluşturucu çağırmadan, bildirime dayalı olarak başlatmak için nesne başlatıcıları ' nı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cdfd-105">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
<span data-ttu-id="1cdfd-106">Aşağıdaki örneklerde, adlandırılmış nesneler ile nesne başlatıcılarının nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1cdfd-106">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="1cdfd-107">Derleyici, önce parametresiz örnek oluşturucusuna erişerek ve sonra üye başlatmaları işleyerek nesne başlatıcıları işler.</span><span class="sxs-lookup"><span data-stu-id="1cdfd-107">The compiler processes object initializers by first accessing the parameterless instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="1cdfd-108">Bu nedenle, parametresiz Oluşturucu sınıfında olarak bildirilirse `private` , genel erişim gerektiren nesne başlatıcıları başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="1cdfd-108">Therefore, if the parameterless constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>
  
<span data-ttu-id="1cdfd-109">Anonim bir tür tanımlıyorsanız bir nesne Başlatıcısı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1cdfd-109">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="1cdfd-110">Daha fazla bilgi için bkz. [bir sorgudaki öğe özelliklerinin alt kümelerini döndürme](how-to-return-subsets-of-element-properties-in-a-query.md).</span><span class="sxs-lookup"><span data-stu-id="1cdfd-110">For more information, see [How to return subsets of element properties in a query](how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1cdfd-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="1cdfd-111">Example</span></span>  

<span data-ttu-id="1cdfd-112">Aşağıdaki örnekte, nesne başlatıcıları kullanarak yeni bir türün nasıl başlatıldığı gösterilmektedir `StudentName` .</span><span class="sxs-lookup"><span data-stu-id="1cdfd-112">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span> <span data-ttu-id="1cdfd-113">Bu örnek, türündeki özellikleri ayarlar `StudentName` :</span><span class="sxs-lookup"><span data-stu-id="1cdfd-113">This example sets properties in the `StudentName` type:</span></span>
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

<span data-ttu-id="1cdfd-114">Nesne başlatıcıları, bir nesnedeki Dizin oluşturucuyu ayarlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1cdfd-114">Object initializers can be used to set indexers in an object.</span></span> <span data-ttu-id="1cdfd-115">Aşağıdaki örnek, `BaseballTeam` farklı konumlarda oynatıcı almak ve ayarlamak için bir dizin oluşturucu kullanan bir sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1cdfd-115">The following example defines a `BaseballTeam` class that uses an indexer to get and set players at different positions.</span></span> <span data-ttu-id="1cdfd-116">Başlatıcı, konum kısaltmasını veya her bir konum için kullanılan her bir konum için kullanılan sayıyı temel alarak oyuncuları atayabilir:</span><span class="sxs-lookup"><span data-stu-id="1cdfd-116">The initializer can assign players, based on the abbreviation for the position, or the number used for each position baseball scorecards:</span></span>

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a><span data-ttu-id="1cdfd-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1cdfd-117">See also</span></span>

- [<span data-ttu-id="1cdfd-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1cdfd-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1cdfd-119">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="1cdfd-119">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
