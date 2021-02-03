---
title: Birim testlerini düzenleme
description: .NET Core ile birim testlerini sipariş etme hakkında bilgi edinin.
author: IEvangelist
ms.author: dapine
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.openlocfilehash: a7b6b66e4cc865d4ec6b7cfc31ac79767935df2f
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506389"
---
# <a name="order-unit-tests"></a>Birim testlerini düzenleme

Bazen, birim testlerinin belirli bir sırada çalıştırılmasını isteyebilirsiniz. İdeal olarak, birim testlerinin çalıştırıldığı sıra, birim testlerini  sıralamayı önlemek için [en iyi uygulamadır](unit-testing-best-practices.md) . Ne olursa olsun, bunu yapmanız gerekebilir. Bu durumda, bu makalede test çalıştırmalarını sıralama gösterilmektedir.

Kaynak koda gözatmaya tercih ediyorsanız bkz. [.NET Core birim testleri](/samples/dotnet/samples/order-unit-tests-cs) örnek deposunu sıralama.

> [!TIP]
> Bu makalede özetlenen sıralama olanaklarına ek olarak, alternatif olarak [Visual Studio ile özel çalma listeleri oluşturmayı](/visualstudio/test/run-unit-tests-with-test-explorer?view=vs-2019#create-custom-playlists) düşünün.

:::zone pivot="mstest"

## <a name="order-alphabetically"></a>Alfabetik olarak Sırala

MSTest ile testler, test adları tarafından otomatik olarak sıralanır.

> [!NOTE]
> `Test14` `Test2` Sayı şundan küçük olsa bile, adlı bir test çalışacaktır `2` `14` . Bunun nedeni, test adı sıralaması testin metin adını kullanır.

:::code language="csharp" source="snippets/order-unit-tests/csharp/MSTest.Project/ByAlphabeticalOrder.cs":::

:::zone-end
:::zone pivot="xunit"

XUnit test çerçevesi, test çalıştırma sırası için daha fazla ayrıntı düzeyi ve denetim sağlar. `ITestCaseOrderer` `ITestCollectionOrderer` Bir sınıf veya test koleksiyonlarında test çalışmalarının sırasını denetlemek için ve arabirimlerini uygulayın.

## <a name="order-by-test-case-alphabetically"></a>Test çalışması alfabetik olarak Sırala

Test çalışmalarını Yöntem adına göre sıralamak için, ' yi uygular `ITestCaseOrderer` ve bir sıralama mekanizması sağlarsınız.

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/Orderers/AlphabeticalOrderer.cs":::

Ardından bir test sınıfında, test çalışması sırasını ile ayarlarsınız `TestCaseOrdererAttribute` .

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/ByAlphabeticalOrder.cs":::

## <a name="order-by-collection-alphabetically"></a>Koleksiyona göre sırala

Test koleksiyonlarını görünen adına göre sıralamak için, ' yi uygular `ITestCollectionOrderer` ve bir sıralama mekanizması sağlarsınız.

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/Orderers/DisplayNameOrderer.cs":::

Test koleksiyonları potansiyel olarak paralel şekilde çalıştığı için, koleksiyonların test paralelleştirme ile açıkça devre dışı bırakmanız gerekir `CollectionBehaviorAttribute` . Ardından, için uygulamasını belirtin `TestCollectionOrdererAttribute` .

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/ByDisplayName.cs":::

## <a name="order-by-custom-attribute"></a>Özel özniteliğe göre sırala

Özel özniteliklerle xUnit testlerini sıralamak için öncelikle bir özniteliğe ihtiyacınız vardır. `TestPriorityAttribute`Aşağıdaki gibi tanımlayın:

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/Attributes/TestPriorityAttribute.cs":::

Ardından, arabirimin aşağıdaki uygulamasını göz önünde bulundurun `PriorityOrderer` `ITestCaseOrderer` .

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/Orderers/PriorityOrderer.cs":::

Ardından bir test sınıfında, ile test çalışması sırasını ayarlarsınız `TestCaseOrdererAttribute` `PriorityOrderer` .

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/ByPriorityOrder.cs":::

:::zone-end
:::zone pivot="nunit"

## <a name="order-by-priority"></a>Önceliğe göre sırala

Testleri açıkça sıralamak için NUnit bir sağlar [`OrderAttribute`](https://github.com/nunit/docs/wiki/Order-Attribute) . Bu öznitelikle olan testler, test etmeden önce başlatılır. Sıra değeri, birim testlerinin çalıştırılacağı sırayı tespit etmek için kullanılır.

:::code language="csharp" source="snippets/order-unit-tests/csharp/NUnit.TestProject/ByOrder.cs":::

:::zone-end

## <a name="next-steps"></a>Sonraki Adımlar

> [!div class="nextstepaction"]
> [Birim testi kod kapsamı](unit-testing-code-coverage.md)
