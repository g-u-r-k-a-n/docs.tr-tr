---
title: "İzlenecek yol: C#'de Sorgu Yazma (LINQ)"
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
ms.openlocfilehash: f2135c6c3649ba2fc87e3b49770439688a58269b
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418062"
---
# <a name="walkthrough-writing-queries-in-c-linq"></a><span data-ttu-id="fa190-102">İzlenecek yol: C#'de Sorgu Yazma (LINQ)</span><span class="sxs-lookup"><span data-stu-id="fa190-102">Walkthrough: Writing Queries in C# (LINQ)</span></span>
<span data-ttu-id="fa190-103">Bu izlenecek yol, C# LINQ sorgu ifadeleri yazmak için kullanılan dil özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa190-103">This walkthrough demonstrates the C# language features that are used to write LINQ query expressions.</span></span>  
  
## <a name="create-a-c-project"></a><span data-ttu-id="fa190-104">Bir C# Projesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fa190-104">Create a C# Project</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fa190-105">Aşağıdaki yönergeler Visual Studio içindir.</span><span class="sxs-lookup"><span data-stu-id="fa190-105">The following instructions are for Visual Studio.</span></span> <span data-ttu-id="fa190-106">Farklı bir geliştirme ortamı kullanıyorsanız, System. Core. dll başvurusu ve <xref:System.Linq?displayProperty=nameWithType> ad alanı için bir `using` yönergesine sahip bir konsol projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fa190-106">If you are using a different development environment, create a console project with a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
#### <a name="to-create-a-project-in-visual-studio"></a><span data-ttu-id="fa190-107">Visual Studio 'da bir proje oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fa190-107">To create a project in Visual Studio</span></span>  
  
1. <span data-ttu-id="fa190-108">Visual Studio 'Yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="fa190-108">Start Visual Studio.</span></span>  
  
2. <span data-ttu-id="fa190-109">Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="fa190-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="fa190-110">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="fa190-110">The **New Project** dialog box opens.</span></span>  
  
3. <span data-ttu-id="fa190-111">**Yüklü**' i genişletin, **Şablonlar**' ı genişletin, **C#görsel**' i genişletin ve **konsol uygulaması**' nı</span><span class="sxs-lookup"><span data-stu-id="fa190-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4. <span data-ttu-id="fa190-112">**Ad** metin kutusuna, farklı bir ad girin veya varsayılan adı kabul edin ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="fa190-112">In the **Name** text box, enter a different name or accept the default name, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="fa190-113">Yeni proje **Çözüm Gezgini**görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fa190-113">The new project appears in **Solution Explorer**.</span></span>  
  
5. <span data-ttu-id="fa190-114">Projenizin System. Core. dll dosyasına ve <xref:System.Linq?displayProperty=nameWithType> ad alanı için bir `using` yönergesine başvurduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="fa190-114">Notice that your project has a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="create-an-in-memory-data-source"></a><span data-ttu-id="fa190-115">Bellek İçi Veri Kaynağı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fa190-115">Create an in-Memory Data Source</span></span>  
 <span data-ttu-id="fa190-116">Sorgular için veri kaynağı `Student` nesnelerinin basit bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="fa190-116">The data source for the queries is a simple list of `Student` objects.</span></span> <span data-ttu-id="fa190-117">Her `Student` kaydı, sınıf içindeki test puanlarını temsil eden bir ad, soyadı ve bir tamsayılar dizisi içerir.</span><span class="sxs-lookup"><span data-stu-id="fa190-117">Each `Student` record has a first name, last name, and an array of integers that represents their test scores in the class.</span></span> <span data-ttu-id="fa190-118">Bu kodu projenize kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="fa190-118">Copy this code into your project.</span></span> <span data-ttu-id="fa190-119">Aşağıdaki özelliklere göz önünde edin:</span><span class="sxs-lookup"><span data-stu-id="fa190-119">Note the following characteristics:</span></span>  
  
- <span data-ttu-id="fa190-120">`Student` sınıfı otomatik uygulanan özelliklerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="fa190-120">The `Student` class consists of auto-implemented properties.</span></span>  
  
- <span data-ttu-id="fa190-121">Listedeki her öğrenci bir nesne başlatıcısı ile başlatılır.</span><span class="sxs-lookup"><span data-stu-id="fa190-121">Each student in the list is initialized with an object initializer.</span></span>  
  
- <span data-ttu-id="fa190-122">Listenin kendisi bir koleksiyon başlatıcısı ile başlatılır.</span><span class="sxs-lookup"><span data-stu-id="fa190-122">The list itself is initialized with a collection initializer.</span></span>  
  
 <span data-ttu-id="fa190-123">Bu bütün veri yapısı, herhangi bir oluşturucuya veya açık üye erişimine açık çağrılar olmadan başlatılır ve oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fa190-123">This whole data structure will be initialized and instantiated without explicit calls to any constructor or explicit member access.</span></span> <span data-ttu-id="fa190-124">Bu yeni özellikler hakkında daha fazla bilgi için bkz. [Otomatik uygulanan özellikler](../../classes-and-structs/auto-implemented-properties.md) ve [nesne ve koleksiyon başlatıcıları](../../classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="fa190-124">For more information about these new features, see [Auto-Implemented Properties](../../classes-and-structs/auto-implemented-properties.md) and [Object and Collection Initializers](../../classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="fa190-125">Veri kaynağını eklemek için</span><span class="sxs-lookup"><span data-stu-id="fa190-125">To add the data source</span></span>  
  
- <span data-ttu-id="fa190-126">`Student` sınıfını ve başlatılan öğrenciler listesini projenizdeki `Program` sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fa190-126">Add the `Student` class and the initialized list of students to the `Program` class in your project.</span></span>  
  
     [!code-csharp[CsLinqGettingStarted#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#11)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="fa190-127">Öğrenciler listesine yeni bir Öğrenci eklemek için</span><span class="sxs-lookup"><span data-stu-id="fa190-127">To add a new Student to the Students list</span></span>  
  
1. <span data-ttu-id="fa190-128">`Students` listesine yeni bir `Student` ekleyin ve tercih ettiğiniz bir ad ve test puanlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="fa190-128">Add a new `Student` to the `Students` list and use a name and test scores of your choice.</span></span> <span data-ttu-id="fa190-129">Nesne başlatıcısının sözdizimini daha iyi öğrenmek için tüm yeni öğrenci bilgilerini yazmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="fa190-129">Try typing all the new student information in order to better learn the syntax for the object initializer.</span></span>  
  
## <a name="create-the-query"></a><span data-ttu-id="fa190-130">Sorgu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fa190-130">Create the Query</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="fa190-131">Basit bir sorgu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fa190-131">To create a simple query</span></span>  
  
- <span data-ttu-id="fa190-132">Uygulamanın `Main` yönteminde, ilk testteki puanı 90 'den büyük olan tüm öğrencilerin bir listesini üretecek basit bir sorgu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fa190-132">In the application's `Main` method, create a simple query that, when it is executed, will produce a list of all students whose score on the first test was greater than 90.</span></span> <span data-ttu-id="fa190-133">`Student` nesnesinin tamamı seçili olduğundan, sorgunun türü `IEnumerable<Student>`.</span><span class="sxs-lookup"><span data-stu-id="fa190-133">Note that because the whole `Student` object is selected, the type of the query is `IEnumerable<Student>`.</span></span> <span data-ttu-id="fa190-134">Kod aynı zamanda [var](../../../language-reference/keywords/var.md) anahtar sözcüğünü kullanarak örtük yazma da kullanabilir, ancak sonuçları açıkça göstermek için açık yazma kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fa190-134">Although the code could also use implicit typing by using the [var](../../../language-reference/keywords/var.md) keyword, explicit typing is used to clearly illustrate results.</span></span> <span data-ttu-id="fa190-135">(`var`hakkında daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](../../classes-and-structs/implicitly-typed-local-variables.md).)</span><span class="sxs-lookup"><span data-stu-id="fa190-135">(For more information about `var`, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).)</span></span>  
  
     <span data-ttu-id="fa190-136">Ayrıca, sorgunun Aralık değişkeni `student`, kaynaktaki her bir `Student` başvuru işlevi görür ve her nesne için üye erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa190-136">Note also that the query's range variable, `student`, serves as a reference to each `Student` in the source, providing member access for each object.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#12)]  
  
## <a name="execute-the-query"></a><span data-ttu-id="fa190-137">Sorguyu Yürütme</span><span class="sxs-lookup"><span data-stu-id="fa190-137">Execute the Query</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="fa190-138">Sorguyu yürütmek için</span><span class="sxs-lookup"><span data-stu-id="fa190-138">To execute the query</span></span>  
  
1. <span data-ttu-id="fa190-139">Şimdi sorgunun yürütülmesine neden olacak `foreach` döngüsünü yazın.</span><span class="sxs-lookup"><span data-stu-id="fa190-139">Now write the `foreach` loop that will cause the query to execute.</span></span> <span data-ttu-id="fa190-140">Kod hakkında aşağıdakilere göz önünde edin:</span><span class="sxs-lookup"><span data-stu-id="fa190-140">Note the following about the code:</span></span>  
  
    - <span data-ttu-id="fa190-141">Döndürülen dizideki her öğeye, `foreach` döngüsünde yineleme değişkeni üzerinden erişilir.</span><span class="sxs-lookup"><span data-stu-id="fa190-141">Each element in the returned sequence is accessed through the iteration variable in the `foreach` loop.</span></span>  
  
    - <span data-ttu-id="fa190-142">Bu değişkenin türü `Student`ve sorgu değişkeninin türü uyumlu, `IEnumerable<Student>`.</span><span class="sxs-lookup"><span data-stu-id="fa190-142">The type of this variable is `Student`, and the type of the query variable is compatible, `IEnumerable<Student>`.</span></span>  
  
2. <span data-ttu-id="fa190-143">Bu kodu ekledikten sonra, sonuçları **konsol** penceresinde görmek için uygulamayı derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fa190-143">After you have added this code, build and run the application to see the results in the **Console** window.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#13)]  
  
#### <a name="to-add-another-filter-condition"></a><span data-ttu-id="fa190-144">Başka bir filtre koşulu eklemek için</span><span class="sxs-lookup"><span data-stu-id="fa190-144">To add another filter condition</span></span>  
  
1. <span data-ttu-id="fa190-145">Bir sorguyu daha da belirginleştirmek için `where` yan tümcesinde birden çok Boolean koşulu birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa190-145">You can combine multiple Boolean conditions in the `where` clause in order to further refine a query.</span></span> <span data-ttu-id="fa190-146">Aşağıdaki kod, sorgunun ilk puanı 90 üzerinde olan ve son puanı 80 ' den az olan bu öğrencileri döndüren bir koşul ekler.</span><span class="sxs-lookup"><span data-stu-id="fa190-146">The following code adds a condition so that the query returns those students whose first score was over 90 and whose last score was less than 80.</span></span> <span data-ttu-id="fa190-147">`where` yan tümcesi aşağıdaki koda benzemelidir.</span><span class="sxs-lookup"><span data-stu-id="fa190-147">The `where` clause should resemble the following code.</span></span>  
  
    ```csharp
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     <span data-ttu-id="fa190-148">Daha fazla bilgi için bkz. [WHERE yan tümcesi](../../../language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="fa190-148">For more information, see [where clause](../../../language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="modify-the-query"></a><span data-ttu-id="fa190-149">Sorguyu Değiştirme</span><span class="sxs-lookup"><span data-stu-id="fa190-149">Modify the Query</span></span>  
  
#### <a name="to-order-the-results"></a><span data-ttu-id="fa190-150">Sonuçları sıralamak için</span><span class="sxs-lookup"><span data-stu-id="fa190-150">To order the results</span></span>  
  
1. <span data-ttu-id="fa190-151">Belirli bir sıra türünde olmaları durumunda sonuçların taranması daha kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="fa190-151">It will be easier to scan the results if they are in some kind of order.</span></span> <span data-ttu-id="fa190-152">Döndürülen sırayı, kaynak öğelerde erişilebilir olan herhangi bir alana göre sıraya alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa190-152">You can order the returned sequence by any accessible field in the source elements.</span></span> <span data-ttu-id="fa190-153">Örneğin, aşağıdaki `orderby` yan tümcesi sonuçları alfabetik sırada her öğrencinin son adına göre bir ile Z 'ye sıralar.</span><span class="sxs-lookup"><span data-stu-id="fa190-153">For example, the following `orderby` clause orders the results in alphabetical order from A to Z according to the last name of each student.</span></span> <span data-ttu-id="fa190-154">Sorgunuz için aşağıdaki `orderby` yan tümcesini, `where` deyiminize ve `select` deyimden önce ekleyin:</span><span class="sxs-lookup"><span data-stu-id="fa190-154">Add the following `orderby` clause to your query, right after the `where` statement and before the `select` statement:</span></span>  
  
    ```csharp
    orderby student.Last ascending  
    ```  
  
2. <span data-ttu-id="fa190-155">Şimdi `orderby` yan tümcesini, en yüksek puanın en düşük puanına kadar ilk testteki puana göre ters sırada sipariş verecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fa190-155">Now change the `orderby` clause so that it orders the results in reverse order according to the score on the first test, from the highest score to the lowest score.</span></span>  
  
    ```csharp
    orderby student.Scores[0] descending  
    ```  
  
3. <span data-ttu-id="fa190-156">Puanları görebilmeniz için `WriteLine` biçim dizesini değiştirin:</span><span class="sxs-lookup"><span data-stu-id="fa190-156">Change the `WriteLine` format string so that you can see the scores:</span></span>  
  
    ```csharp
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     <span data-ttu-id="fa190-157">Daha fazla bilgi için bkz. [OrderBy tümcesi](../../../language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="fa190-157">For more information, see [orderby clause](../../../language-reference/keywords/orderby-clause.md).</span></span>  
  
#### <a name="to-group-the-results"></a><span data-ttu-id="fa190-158">Sonuçları gruplandırmak için</span><span class="sxs-lookup"><span data-stu-id="fa190-158">To group the results</span></span>  
  
1. <span data-ttu-id="fa190-159">Gruplandırma, sorgu ifadelerinde güçlü bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="fa190-159">Grouping is a powerful capability in query expressions.</span></span> <span data-ttu-id="fa190-160">Group yan tümcesi içeren bir sorgu bir grup sırası üretir ve her bir grubun kendisi bir `Key` ve bu grubun tüm üyelerinden oluşan bir dizi içerir.</span><span class="sxs-lookup"><span data-stu-id="fa190-160">A query with a group clause produces a sequence of groups, and each group itself contains a `Key` and a sequence that consists of all the members of that group.</span></span> <span data-ttu-id="fa190-161">Aşağıdaki yeni sorgu, en son adının ilk harfini anahtar olarak kullanarak öğrencileri gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="fa190-161">The following new query groups the students by using the first letter of their last name as the key.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#14)]  
  
2. <span data-ttu-id="fa190-162">Sorgu türünün artık değiştiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fa190-162">Note that the type of the query has now changed.</span></span> <span data-ttu-id="fa190-163">Artık anahtar olarak `char` türüne ve `Student` nesne dizisine sahip bir grup sırası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fa190-163">It now produces a sequence of groups that have a `char` type as a key, and a sequence of `Student` objects.</span></span> <span data-ttu-id="fa190-164">Sorgunun türü değiştiği için aşağıdaki kod `foreach` yürütme döngüsünü de değiştirir:</span><span class="sxs-lookup"><span data-stu-id="fa190-164">Because the type of the query has changed, the following code changes the `foreach` execution loop also:</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#15)]  
  
3. <span data-ttu-id="fa190-165">Uygulamayı çalıştırın ve sonuçları **konsol** penceresinde görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="fa190-165">Run the application and view the results in the **Console** window.</span></span>  
  
     <span data-ttu-id="fa190-166">Daha fazla bilgi için bkz. [Group yan tümcesi](../../../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="fa190-166">For more information, see [group clause](../../../language-reference/keywords/group-clause.md).</span></span>  
  
#### <a name="to-make-the-variables-implicitly-typed"></a><span data-ttu-id="fa190-167">Değişkenlerin dolaylı olarak yazılmasını sağlamak için</span><span class="sxs-lookup"><span data-stu-id="fa190-167">To make the variables implicitly typed</span></span>  
  
1. <span data-ttu-id="fa190-168">`IGroupings` `IEnumerables` açıkça kodlanması hızla sıkıcı hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="fa190-168">Explicitly coding `IEnumerables` of `IGroupings` can quickly become tedious.</span></span> <span data-ttu-id="fa190-169">`var`kullanarak aynı sorgu ve `foreach` döngüsünü çok daha kolay bir şekilde yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa190-169">You can write the same query and `foreach` loop much more conveniently by using `var`.</span></span> <span data-ttu-id="fa190-170">`var` anahtar sözcüğü, nesnelerinizin türlerini değiştirmez; yalnızca derleyiciye tür çıkarması talimatını verir.</span><span class="sxs-lookup"><span data-stu-id="fa190-170">The `var` keyword does not change the types of your objects; it just instructs the compiler to infer the types.</span></span> <span data-ttu-id="fa190-171">`studentQuery` türünü ve `group` yineleme değişkenini `var` olarak değiştirin ve sorguyu yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fa190-171">Change the type of `studentQuery` and the iteration variable `group` to `var` and rerun the query.</span></span> <span data-ttu-id="fa190-172">Inner `foreach` döngüsünde, yineleme değişkeninin hala `Student`olarak yazıldığı ve sorgunun daha önce olduğu gibi çalıştığından emin olmanız gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fa190-172">Note that in the inner `foreach` loop, the iteration variable is still typed as `Student`, and the query works just as before.</span></span> <span data-ttu-id="fa190-173">`s` yineleme değişkenini `var` olarak değiştirip sorguyu yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fa190-173">Change the `s` iteration variable to `var` and run the query again.</span></span> <span data-ttu-id="fa190-174">Tam olarak aynı sonuçları elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="fa190-174">You see that you get exactly the same results.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#16)]  
  
     <span data-ttu-id="fa190-175">[Var](../../../language-reference/keywords/var.md)hakkında daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](../../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="fa190-175">For more information about [var](../../../language-reference/keywords/var.md), see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
#### <a name="to-order-the-groups-by-their-key-value"></a><span data-ttu-id="fa190-176">Grupları anahtar değerlerine göre sıralamak için</span><span class="sxs-lookup"><span data-stu-id="fa190-176">To order the groups by their key value</span></span>  
  
1. <span data-ttu-id="fa190-177">Önceki sorguyu çalıştırdığınızda grupların alfabetik sırada olmadığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="fa190-177">When you run the previous query, you notice that the groups are not in alphabetical order.</span></span> <span data-ttu-id="fa190-178">Bunu değiştirmek için, `group` yan tümcesinden sonra bir `orderby` yan tümcesi sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fa190-178">To change this, you must provide an `orderby` clause after the `group` clause.</span></span> <span data-ttu-id="fa190-179">Ancak, bir `orderby` yan tümcesi kullanmak için, önce `group` yan tümcesi tarafından oluşturulan gruplara başvuru olarak hizmet veren bir tanımlayıcıya ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="fa190-179">But to use an `orderby` clause, you first need an identifier that serves as a reference to the groups created by the `group` clause.</span></span> <span data-ttu-id="fa190-180">Tanımlayıcıyı, aşağıdaki gibi `into` anahtar sözcüğünü kullanarak sağlarsınız:</span><span class="sxs-lookup"><span data-stu-id="fa190-180">You provide the identifier by using the `into` keyword, as follows:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#17)]  
  
     <span data-ttu-id="fa190-181">Bu sorguyu çalıştırdığınızda, grupların artık alfabetik sırada sıralanacağını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="fa190-181">When you run this query, you will see the groups are now sorted in alphabetical order.</span></span>  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a><span data-ttu-id="fa190-182">Bir tanımlayıcıyı let kullanarak tanıtmak için</span><span class="sxs-lookup"><span data-stu-id="fa190-182">To introduce an identifier by using let</span></span>  
  
1. <span data-ttu-id="fa190-183">Sorgu ifadesindeki herhangi bir ifade sonucu için bir tanımlayıcı tanıtmak üzere `let` anahtar sözcüğünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa190-183">You can use the `let` keyword to introduce an identifier for any expression result in the query expression.</span></span> <span data-ttu-id="fa190-184">Bu tanımlayıcı, aşağıdaki örnekte olduğu gibi kolaylık olabilir veya bir ifadenin sonuçlarını birden çok kez hesaplanmak zorunda kalmayacak şekilde depolayarak performansı geliştirebilir.</span><span class="sxs-lookup"><span data-stu-id="fa190-184">This identifier can be a convenience, as in the following example, or it can enhance performance by storing the results of an expression so that it does not have to be calculated multiple times.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#18)]  
  
     <span data-ttu-id="fa190-185">Daha fazla bilgi için bkz. [Let yan tümcesi](../../../language-reference/keywords/let-clause.md).</span><span class="sxs-lookup"><span data-stu-id="fa190-185">For more information, see [let clause](../../../language-reference/keywords/let-clause.md).</span></span>  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a><span data-ttu-id="fa190-186">Bir sorgu ifadesinde yöntem sözdizimini kullanmak için</span><span class="sxs-lookup"><span data-stu-id="fa190-186">To use method syntax in a query expression</span></span>  
  
1. <span data-ttu-id="fa190-187">[Sorgu söz dizimi ve LINQ 'Teki yöntem sözdiziminde](./query-syntax-and-method-syntax-in-linq.md)açıklandığı gibi, bazı sorgu işlemleri yalnızca Yöntem sözdizimi kullanılarak ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="fa190-187">As described in [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md), some query operations can only be expressed by using method syntax.</span></span> <span data-ttu-id="fa190-188">Aşağıdaki kod, kaynak dizideki her bir `Student` için toplam puanı hesaplar ve sonra sınıfın ortalama Puanını hesaplamak için bu sorgunun sonuçlarında `Average()` yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="fa190-188">The following code calculates the total score for each `Student` in the source sequence, and then calls the `Average()` method on the results of that query to calculate the average score of the class.</span></span>
  
     [!code-csharp[csLINQGettingStarted#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#19)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a><span data-ttu-id="fa190-189">Select yan tümcesinde dönüştürmek ya da planlamak için</span><span class="sxs-lookup"><span data-stu-id="fa190-189">To transform or project in the select clause</span></span>  
  
1. <span data-ttu-id="fa190-190">Bir sorgu için, öğeleri kaynak dizideki öğelerden farklı olan bir sıra üretmek çok yaygındır.</span><span class="sxs-lookup"><span data-stu-id="fa190-190">It is very common for a query to produce a sequence whose elements differ from the elements in the source sequences.</span></span> <span data-ttu-id="fa190-191">Önceki sorgunuzu ve yürütme döngünüzü silin veya bir yorum yapın ve aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fa190-191">Delete or comment out your previous query and execution loop, and replace it with the following code.</span></span> <span data-ttu-id="fa190-192">Sorgunun bir dizi dizeyi (`Students`değil) döndürdüğünü ve bu olguyu `foreach` döngüsünde yansıtıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fa190-192">Note that the query returns a sequence of strings (not `Students`), and this fact is reflected in the `foreach` loop.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#20)]  
  
2. <span data-ttu-id="fa190-193">Bu kılavuzda daha önce bahsedilen kod, Ortalama sınıf puanının yaklaşık 334 olduğunu gösterdi.</span><span class="sxs-lookup"><span data-stu-id="fa190-193">Code earlier in this walkthrough indicated that the average class score is approximately 334.</span></span> <span data-ttu-id="fa190-194">Toplam puanı, `Student ID`olan ve ortalamasının `Students` bir dizisini oluşturmak için `select` deyimindeki anonim bir tür kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fa190-194">To produce a sequence of `Students` whose total score is greater than the class average, together with their `Student ID`, you can use an anonymous type in the `select` statement:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#21)]  
  
## <a name="next-steps"></a><span data-ttu-id="fa190-195">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="fa190-195">Next Steps</span></span>  
 <span data-ttu-id="fa190-196">İçindeki C#sorgularla çalışmanın temel yönleri hakkında bilgi sahibi olduktan sonra, ilgilendiğiniz LINQ sağlayıcısı türü için belge ve örnekleri okumaya hazırsınızdır:</span><span class="sxs-lookup"><span data-stu-id="fa190-196">After you are familiar with the basic aspects of working with queries in C#, you are ready to read the documentation and samples for the specific type of LINQ provider you are interested in:</span></span>  
  
 [<span data-ttu-id="fa190-197">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="fa190-197">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [<span data-ttu-id="fa190-198">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="fa190-198">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [<span data-ttu-id="fa190-199">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="fa190-199">LINQ to XML (C#)</span></span>](./linq-to-xml-overview.md)  
  
 [<span data-ttu-id="fa190-200">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="fa190-200">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="fa190-201">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa190-201">See also</span></span>

- [<span data-ttu-id="fa190-202">Dil ile tümleşik sorgu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="fa190-202">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
- [<span data-ttu-id="fa190-203">LINQ sorgu Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="fa190-203">LINQ Query Expressions</span></span>](../../../linq/index.md)
