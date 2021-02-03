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
# <a name="order-unit-tests"></a><span data-ttu-id="d625d-103">Birim testlerini düzenleme</span><span class="sxs-lookup"><span data-stu-id="d625d-103">Order unit tests</span></span>

<span data-ttu-id="d625d-104">Bazen, birim testlerinin belirli bir sırada çalıştırılmasını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d625d-104">Occasionally, you may want to have unit tests run in a specific order.</span></span> <span data-ttu-id="d625d-105">İdeal olarak, birim testlerinin çalıştırıldığı sıra, birim testlerini  sıralamayı önlemek için [en iyi uygulamadır](unit-testing-best-practices.md) .</span><span class="sxs-lookup"><span data-stu-id="d625d-105">Ideally, the order in which unit tests run should _not_ matter, and it is [best practice](unit-testing-best-practices.md) to avoid ordering unit tests.</span></span> <span data-ttu-id="d625d-106">Ne olursa olsun, bunu yapmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="d625d-106">Regardless, there may be a need to do so.</span></span> <span data-ttu-id="d625d-107">Bu durumda, bu makalede test çalıştırmalarını sıralama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d625d-107">In that case, this article demonstrates how to order test runs.</span></span>

<span data-ttu-id="d625d-108">Kaynak koda gözatmaya tercih ediyorsanız bkz. [.NET Core birim testleri](/samples/dotnet/samples/order-unit-tests-cs) örnek deposunu sıralama.</span><span class="sxs-lookup"><span data-stu-id="d625d-108">If you prefer to browse the source code, see the [order .NET Core unit tests](/samples/dotnet/samples/order-unit-tests-cs) sample repository.</span></span>

> [!TIP]
> <span data-ttu-id="d625d-109">Bu makalede özetlenen sıralama olanaklarına ek olarak, alternatif olarak [Visual Studio ile özel çalma listeleri oluşturmayı](/visualstudio/test/run-unit-tests-with-test-explorer?view=vs-2019#create-custom-playlists) düşünün.</span><span class="sxs-lookup"><span data-stu-id="d625d-109">In addition to the ordering capabilities outlined in this article, consider [creating custom playlists with Visual Studio](/visualstudio/test/run-unit-tests-with-test-explorer?view=vs-2019#create-custom-playlists) as an alternative.</span></span>

:::zone pivot="mstest"

## <a name="order-alphabetically"></a><span data-ttu-id="d625d-110">Alfabetik olarak Sırala</span><span class="sxs-lookup"><span data-stu-id="d625d-110">Order alphabetically</span></span>

<span data-ttu-id="d625d-111">MSTest ile testler, test adları tarafından otomatik olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="d625d-111">With MSTest, tests are automatically ordered by their test name.</span></span>

> [!NOTE]
> <span data-ttu-id="d625d-112">`Test14` `Test2` Sayı şundan küçük olsa bile, adlı bir test çalışacaktır `2` `14` .</span><span class="sxs-lookup"><span data-stu-id="d625d-112">A test named `Test14` will run before `Test2` even though the number  `2` is less than `14`.</span></span> <span data-ttu-id="d625d-113">Bunun nedeni, test adı sıralaması testin metin adını kullanır.</span><span class="sxs-lookup"><span data-stu-id="d625d-113">This is because, test name ordering uses the text name of the test.</span></span>

:::code language="csharp" source="snippets/order-unit-tests/csharp/MSTest.Project/ByAlphabeticalOrder.cs":::

:::zone-end
:::zone pivot="xunit"

<span data-ttu-id="d625d-114">XUnit test çerçevesi, test çalıştırma sırası için daha fazla ayrıntı düzeyi ve denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="d625d-114">The xUnit test framework allows for more granularity and control of test run order.</span></span> <span data-ttu-id="d625d-115">`ITestCaseOrderer` `ITestCollectionOrderer` Bir sınıf veya test koleksiyonlarında test çalışmalarının sırasını denetlemek için ve arabirimlerini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="d625d-115">You implement the `ITestCaseOrderer` and `ITestCollectionOrderer` interfaces to control the order of test cases for a class, or test collections.</span></span>

## <a name="order-by-test-case-alphabetically"></a><span data-ttu-id="d625d-116">Test çalışması alfabetik olarak Sırala</span><span class="sxs-lookup"><span data-stu-id="d625d-116">Order by test case alphabetically</span></span>

<span data-ttu-id="d625d-117">Test çalışmalarını Yöntem adına göre sıralamak için, ' yi uygular `ITestCaseOrderer` ve bir sıralama mekanizması sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="d625d-117">To order test cases by their method name, you implement the `ITestCaseOrderer` and provide an ordering mechanism.</span></span>

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/Orderers/AlphabeticalOrderer.cs":::

<span data-ttu-id="d625d-118">Ardından bir test sınıfında, test çalışması sırasını ile ayarlarsınız `TestCaseOrdererAttribute` .</span><span class="sxs-lookup"><span data-stu-id="d625d-118">Then in a test class you set the test case order with the `TestCaseOrdererAttribute`.</span></span>

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/ByAlphabeticalOrder.cs":::

## <a name="order-by-collection-alphabetically"></a><span data-ttu-id="d625d-119">Koleksiyona göre sırala</span><span class="sxs-lookup"><span data-stu-id="d625d-119">Order by collection alphabetically</span></span>

<span data-ttu-id="d625d-120">Test koleksiyonlarını görünen adına göre sıralamak için, ' yi uygular `ITestCollectionOrderer` ve bir sıralama mekanizması sağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="d625d-120">To order test collections by their display name, you implement the `ITestCollectionOrderer` and provide an ordering mechanism.</span></span>

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/Orderers/DisplayNameOrderer.cs":::

<span data-ttu-id="d625d-121">Test koleksiyonları potansiyel olarak paralel şekilde çalıştığı için, koleksiyonların test paralelleştirme ile açıkça devre dışı bırakmanız gerekir `CollectionBehaviorAttribute` .</span><span class="sxs-lookup"><span data-stu-id="d625d-121">Since test collections potentially run in parallel, you must explicitly disable test parallelization of the collections with the `CollectionBehaviorAttribute`.</span></span> <span data-ttu-id="d625d-122">Ardından, için uygulamasını belirtin `TestCollectionOrdererAttribute` .</span><span class="sxs-lookup"><span data-stu-id="d625d-122">Then specify the implementation to the `TestCollectionOrdererAttribute`.</span></span>

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/ByDisplayName.cs":::

## <a name="order-by-custom-attribute"></a><span data-ttu-id="d625d-123">Özel özniteliğe göre sırala</span><span class="sxs-lookup"><span data-stu-id="d625d-123">Order by custom attribute</span></span>

<span data-ttu-id="d625d-124">Özel özniteliklerle xUnit testlerini sıralamak için öncelikle bir özniteliğe ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="d625d-124">To order xUnit tests with custom attributes, you first need an attribute to rely on.</span></span> <span data-ttu-id="d625d-125">`TestPriorityAttribute`Aşağıdaki gibi tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="d625d-125">Define a `TestPriorityAttribute` as follows:</span></span>

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/Attributes/TestPriorityAttribute.cs":::

<span data-ttu-id="d625d-126">Ardından, arabirimin aşağıdaki uygulamasını göz önünde bulundurun `PriorityOrderer` `ITestCaseOrderer` .</span><span class="sxs-lookup"><span data-stu-id="d625d-126">Next, consider the following `PriorityOrderer` implementation of the `ITestCaseOrderer` interface.</span></span>

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/Orderers/PriorityOrderer.cs":::

<span data-ttu-id="d625d-127">Ardından bir test sınıfında, ile test çalışması sırasını ayarlarsınız `TestCaseOrdererAttribute` `PriorityOrderer` .</span><span class="sxs-lookup"><span data-stu-id="d625d-127">Then in a test class you set the test case order with the `TestCaseOrdererAttribute` to the `PriorityOrderer`.</span></span>

:::code language="csharp" source="snippets/order-unit-tests/csharp/XUnit.TestProject/ByPriorityOrder.cs":::

:::zone-end
:::zone pivot="nunit"

## <a name="order-by-priority"></a><span data-ttu-id="d625d-128">Önceliğe göre sırala</span><span class="sxs-lookup"><span data-stu-id="d625d-128">Order by priority</span></span>

<span data-ttu-id="d625d-129">Testleri açıkça sıralamak için NUnit bir sağlar [`OrderAttribute`](https://github.com/nunit/docs/wiki/Order-Attribute) .</span><span class="sxs-lookup"><span data-stu-id="d625d-129">To order tests explicitly, NUnit provides an [`OrderAttribute`](https://github.com/nunit/docs/wiki/Order-Attribute).</span></span> <span data-ttu-id="d625d-130">Bu öznitelikle olan testler, test etmeden önce başlatılır.</span><span class="sxs-lookup"><span data-stu-id="d625d-130">Tests with this attribute are started before tests without.</span></span> <span data-ttu-id="d625d-131">Sıra değeri, birim testlerinin çalıştırılacağı sırayı tespit etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d625d-131">The order value is used to determined the order to run the unit tests.</span></span>

:::code language="csharp" source="snippets/order-unit-tests/csharp/NUnit.TestProject/ByOrder.cs":::

:::zone-end

## <a name="next-steps"></a><span data-ttu-id="d625d-132">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="d625d-132">Next Steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d625d-133">Birim testi kod kapsamı</span><span class="sxs-lookup"><span data-stu-id="d625d-133">Unit test code coverage</span></span>](unit-testing-code-coverage.md)
