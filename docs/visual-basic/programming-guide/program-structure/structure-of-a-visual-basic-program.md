---
description: 'Daha fazla bilgi edinin: Visual Basic programın yapısı'
title: Bir Visual Basic Programının Yapısı
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], Visual Basic
- program structure [Visual Basic], Visual Basic
- procedures [Visual Basic], structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
ms.openlocfilehash: e5941b1cbdfdc460e3e860a5449e8ccae0673612
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468206"
---
# <a name="structure-of-a-visual-basic-program"></a><span data-ttu-id="a0b4f-103">Bir Visual Basic Programının Yapısı</span><span class="sxs-lookup"><span data-stu-id="a0b4f-103">Structure of a Visual Basic Program</span></span>

<span data-ttu-id="a0b4f-104">Bir Visual Basic program standart yapı taşlarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-104">A Visual Basic program is built up from standard building blocks.</span></span> <span data-ttu-id="a0b4f-105">Bir *çözüm* bir veya daha fazla projeden oluşur.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-105">A *solution* comprises one or more projects.</span></span> <span data-ttu-id="a0b4f-106">Sırasıyla bir *Proje* , bir veya daha fazla derleme içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-106">A *project* in turn can contain one or more assemblies.</span></span> <span data-ttu-id="a0b4f-107">Her *derleme* bir veya daha fazla kaynak dosyasından derlenir.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-107">Each *assembly* is compiled from one or more source files.</span></span> <span data-ttu-id="a0b4f-108">*Kaynak dosya* , sonunda tüm kodunuzu içeren sınıfların, yapıların, modüllerin ve arabirimlerin tanımını ve uygulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-108">A *source file* provides the definition and implementation of classes, structures, modules, and interfaces, which ultimately contain all your code.</span></span>  
  
 <span data-ttu-id="a0b4f-109">Visual Basic bir programın bu yapı taşları hakkında daha fazla bilgi için bkz. [.net 'Teki](../../../standard/assembly/index.md) [çözümler ve projeler](/visualstudio/ide/solutions-and-projects-in-visual-studio) ve derlemeler.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-109">For more information about these building blocks of a Visual Basic program, see [Solutions and Projects](/visualstudio/ide/solutions-and-projects-in-visual-studio) and [Assemblies in .NET](../../../standard/assembly/index.md).</span></span>  
  
## <a name="file-level-programming-elements"></a><span data-ttu-id="a0b4f-110">File-Level programlama öğeleri</span><span class="sxs-lookup"><span data-stu-id="a0b4f-110">File-Level Programming Elements</span></span>  

 <span data-ttu-id="a0b4f-111">Bir proje veya dosya başlattığınızda ve kod düzenleyicisini açtığınızda, bazı kodları zaten yerinde ve doğru sırada görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-111">When you start a project or file and open the code editor, you see some code already in place and in the correct order.</span></span> <span data-ttu-id="a0b4f-112">Yazdığınız herhangi bir kod aşağıdaki sırayı izlemelidir:</span><span class="sxs-lookup"><span data-stu-id="a0b4f-112">Any code that you write should follow the following sequence:</span></span>  
  
1. <span data-ttu-id="a0b4f-113">`Option` deyimler</span><span class="sxs-lookup"><span data-stu-id="a0b4f-113">`Option` statements</span></span>  
  
2. <span data-ttu-id="a0b4f-114">`Imports` deyimler</span><span class="sxs-lookup"><span data-stu-id="a0b4f-114">`Imports` statements</span></span>  
  
3. <span data-ttu-id="a0b4f-115">`Namespace` deyimler ve isim uzayı düzeyi öğeleri</span><span class="sxs-lookup"><span data-stu-id="a0b4f-115">`Namespace` statements and namespace-level elements</span></span>  
  
 <span data-ttu-id="a0b4f-116">Deyimleri farklı bir sırada girerseniz, derleme hataları oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-116">If you enter statements in a different order, compilation errors can result.</span></span>  
  
 <span data-ttu-id="a0b4f-117">Bir program, koşullu derleme deyimleri de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-117">A program can also contain conditional compilation statements.</span></span> <span data-ttu-id="a0b4f-118">Bunları kaynak dosyada, önceki sıranın deyimleri arasında birbirine bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-118">You can intersperse these in the source file among the statements of the preceding sequence.</span></span>  
  
### <a name="option-statements"></a><span data-ttu-id="a0b4f-119">Seçenek deyimleri</span><span class="sxs-lookup"><span data-stu-id="a0b4f-119">Option Statements</span></span>  

 <span data-ttu-id="a0b4f-120">`Option` deyimler sonraki kod için zemin kuralları oluştururlar ve söz dizimi ve mantık hatalarını önlemeye yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-120">`Option` statements establish ground rules for subsequent code, helping prevent syntax and logic errors.</span></span> <span data-ttu-id="a0b4f-121">[Açık Ifade seçeneği](../../language-reference/statements/option-explicit-statement.md) , tüm değişkenlerin doğru şekilde bildirilmesini ve doğru yazıldığını sağlar ve bu da hata ayıklama süresini azaltır.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-121">The [Option Explicit Statement](../../language-reference/statements/option-explicit-statement.md) ensures that all variables are declared and spelled correctly, which reduces debugging time.</span></span> <span data-ttu-id="a0b4f-122">[Strict deyimleri](../../language-reference/statements/option-strict-statement.md) , farklı veri türleri değişkenleri arasında çalışırken gerçekleşebileceği mantık hatalarını ve veri kaybını en aza indirmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-122">The [Option Strict Statement](../../language-reference/statements/option-strict-statement.md) helps to minimize logic errors and data loss that can occur when you work between variables of different data types.</span></span> <span data-ttu-id="a0b4f-123">[Option Compare deyimleri](../../language-reference/statements/option-compare-statement.md) , dizelerin birbirlerine veya değerlerine göre birbirleriyle karşılaştırılacağı yöntemi belirtir `Binary` `Text` .</span><span class="sxs-lookup"><span data-stu-id="a0b4f-123">The [Option Compare Statement](../../language-reference/statements/option-compare-statement.md) specifies the way strings are compared to each other, based on either their `Binary` or `Text` values.</span></span>  
  
### <a name="imports-statements"></a><span data-ttu-id="a0b4f-124">Imports deyimleri</span><span class="sxs-lookup"><span data-stu-id="a0b4f-124">Imports Statements</span></span>  

 <span data-ttu-id="a0b4f-125">Projenizin dışında tanımlanan adları içeri aktarmak için [Imports (.net ad alanı ve türü) ifadesini](../../language-reference/statements/imports-statement-net-namespace-and-type.md) dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-125">You can include an [Imports Statement (.NET Namespace and Type)](../../language-reference/statements/imports-statement-net-namespace-and-type.md) to import names defined outside your project.</span></span> <span data-ttu-id="a0b4f-126">Bir `Imports` ifade, kodunuzun sınıflara ve içeri aktarılan ad alanında tanımlanan diğer türlere, bunları nitelendirmek gerekmeden başvurmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-126">An `Imports` statement allows your code to refer to classes and other types defined within the imported namespace, without having to qualify them.</span></span> <span data-ttu-id="a0b4f-127">`Imports`Uygun şekilde çok sayıda deyim kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-127">You can use as many `Imports` statements as appropriate.</span></span> <span data-ttu-id="a0b4f-128">Daha fazla bilgi için bkz. [Başvurular ve Imports ekstresi](references-and-the-imports-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a0b4f-128">For more information, see [References and the Imports Statement](references-and-the-imports-statement.md).</span></span>  
  
### <a name="namespace-statements"></a><span data-ttu-id="a0b4f-129">Namespace deyimleri</span><span class="sxs-lookup"><span data-stu-id="a0b4f-129">Namespace Statements</span></span>  

 <span data-ttu-id="a0b4f-130">Ad alanları, gruplama ve erişim kolaylığı için programlama öğelerinizi düzenlemenize ve sınıflandırmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-130">Namespaces help you organize and classify your programming elements for ease of grouping and accessing.</span></span> <span data-ttu-id="a0b4f-131">Belirli bir ad alanı içinde aşağıdaki deyimleri sınıflandırmak için [Namespace deyimini](../../language-reference/statements/namespace-statement.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-131">You use the [Namespace Statement](../../language-reference/statements/namespace-statement.md) to classify the following statements within a particular namespace.</span></span> <span data-ttu-id="a0b4f-132">Daha fazla bilgi için bkz. [Visual Basic ad alanları](namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="a0b4f-132">For more information, see [Namespaces in Visual Basic](namespaces.md).</span></span>  
  
### <a name="conditional-compilation-statements"></a><span data-ttu-id="a0b4f-133">Koşullu derleme deyimleri</span><span class="sxs-lookup"><span data-stu-id="a0b4f-133">Conditional Compilation Statements</span></span>  

 <span data-ttu-id="a0b4f-134">Koşullu derleme deyimleri, kaynak dosyanızda neredeyse her yerde görünebilir.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-134">Conditional compilation statements can appear almost anywhere in your source file.</span></span> <span data-ttu-id="a0b4f-135">Bunlar, belirli koşullara bağlı olarak, kodunuzun bölümlerinin derleme zamanına dahil edilmesini veya dışlanmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-135">They cause parts of your code to be included or excluded at compile time depending on certain conditions.</span></span> <span data-ttu-id="a0b4f-136">Koşullu kod yalnızca hata ayıklama modunda çalıştığı için, bunları uygulamanızda hata ayıklamak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-136">You can also use them for debugging your application, because conditional code runs in debugging mode only.</span></span> <span data-ttu-id="a0b4f-137">Daha fazla bilgi için bkz. [koşullu derleme](conditional-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="a0b4f-137">For more information, see [Conditional Compilation](conditional-compilation.md).</span></span>  
  
## <a name="namespace-level-programming-elements"></a><span data-ttu-id="a0b4f-138">Namespace-Level programlama öğeleri</span><span class="sxs-lookup"><span data-stu-id="a0b4f-138">Namespace-Level Programming Elements</span></span>  

 <span data-ttu-id="a0b4f-139">Sınıflar, yapılar ve modüller, kaynak dosyanızdaki tüm kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-139">Classes, structures, and modules contain all the code in your source file.</span></span> <span data-ttu-id="a0b4f-140">Ad alanı *düzeyindeki* öğelerdir ve bu, bir ad alanı içinde veya kaynak dosya düzeyinde görünebilir.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-140">They are *namespace-level* elements, which can appear within a namespace or at the source file level.</span></span> <span data-ttu-id="a0b4f-141">Diğer tüm programlama öğelerinin bildirimlerini tutar.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-141">They hold the declarations of all other programming elements.</span></span> <span data-ttu-id="a0b4f-142">Öğe imzalarını tanımlayan ancak uygulama sağlamayan arabirimler, modül düzeyinde de görünür.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-142">Interfaces, which define element signatures but provide no implementation, also appear at module level.</span></span> <span data-ttu-id="a0b4f-143">Modül düzeyi öğeler hakkında daha fazla bilgi için aşağıdakilere bakın:</span><span class="sxs-lookup"><span data-stu-id="a0b4f-143">For more information on the module-level elements, see the following:</span></span>  
  
- [<span data-ttu-id="a0b4f-144">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="a0b4f-144">Class Statement</span></span>](../../language-reference/statements/class-statement.md)  
  
- [<span data-ttu-id="a0b4f-145">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="a0b4f-145">Structure Statement</span></span>](../../language-reference/statements/structure-statement.md)  
  
- [<span data-ttu-id="a0b4f-146">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="a0b4f-146">Module Statement</span></span>](../../language-reference/statements/module-statement.md)  
  
- [<span data-ttu-id="a0b4f-147">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="a0b4f-147">Interface Statement</span></span>](../../language-reference/statements/interface-statement.md)  
  
 <span data-ttu-id="a0b4f-148">Ad alanı düzeyindeki veri öğeleri numaralandırmalar ve temsilcileriniz.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-148">Data elements at namespace level are enumerations and delegates.</span></span>  
  
## <a name="module-level-programming-elements"></a><span data-ttu-id="a0b4f-149">Module-Level programlama öğeleri</span><span class="sxs-lookup"><span data-stu-id="a0b4f-149">Module-Level Programming Elements</span></span>  

 <span data-ttu-id="a0b4f-150">İşlemler, işleçler, Özellikler ve olaylar çalıştırılabilir kodu tutabilecek tek programlama öğeleridir (çalışma zamanında eylem gerçekleştiren deyimler).</span><span class="sxs-lookup"><span data-stu-id="a0b4f-150">Procedures, operators, properties, and events are the only programming elements that can hold executable code (statements that perform actions at run time).</span></span> <span data-ttu-id="a0b4f-151">Programınızın *Modül düzeyi* öğeleridir.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-151">They are the *module-level* elements of your program.</span></span> <span data-ttu-id="a0b4f-152">Yordam düzeyi öğeler hakkında daha fazla bilgi için aşağıdakilere bakın:</span><span class="sxs-lookup"><span data-stu-id="a0b4f-152">For more information on the procedure-level elements, see the following:</span></span>  
  
- [<span data-ttu-id="a0b4f-153">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="a0b4f-153">Function Statement</span></span>](../../language-reference/statements/function-statement.md)  
  
- [<span data-ttu-id="a0b4f-154">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="a0b4f-154">Sub Statement</span></span>](../../language-reference/statements/sub-statement.md)  
  
- [<span data-ttu-id="a0b4f-155">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="a0b4f-155">Declare Statement</span></span>](../../language-reference/statements/declare-statement.md)  
  
- [<span data-ttu-id="a0b4f-156">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="a0b4f-156">Operator Statement</span></span>](../../language-reference/statements/operator-statement.md)  
  
- [<span data-ttu-id="a0b4f-157">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="a0b4f-157">Property Statement</span></span>](../../language-reference/statements/property-statement.md)  
  
- [<span data-ttu-id="a0b4f-158">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="a0b4f-158">Event Statement</span></span>](../../language-reference/statements/event-statement.md)  
  
 <span data-ttu-id="a0b4f-159">Modül düzeyindeki veri öğeleri, değişkenler, sabitler, numaralandırmalar ve temsilcilerle.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-159">Data elements at module level are variables, constants, enumerations, and delegates.</span></span>  
  
## <a name="procedure-level-programming-elements"></a><span data-ttu-id="a0b4f-160">Procedure-Level programlama öğeleri</span><span class="sxs-lookup"><span data-stu-id="a0b4f-160">Procedure-Level Programming Elements</span></span>  

 <span data-ttu-id="a0b4f-161">*Yordam düzeyindeki* öğelerin çoğu, programınızın çalışma zamanı kodunu oluşturan çalıştırılabilir deyimlerdir.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-161">Most of the contents of *procedure-level* elements are executable statements, which constitute the run-time code of your program.</span></span> <span data-ttu-id="a0b4f-162">Tüm yürütülebilir kodlar bazı yordamda ( `Function` , `Sub` ,,,, `Operator` `Get` `Set` `AddHandler` , `RemoveHandler` , `RaiseEvent` ,,,,) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-162">All executable code must be in some procedure (`Function`, `Sub`, `Operator`, `Get`, `Set`, `AddHandler`, `RemoveHandler`, `RaiseEvent`).</span></span> <span data-ttu-id="a0b4f-163">Daha fazla bilgi için bkz. [deyimler](../language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="a0b4f-163">For more information, see [Statements](../language-features/statements.md).</span></span>  
  
 <span data-ttu-id="a0b4f-164">Yordam düzeyindeki veri öğeleri yerel değişkenlerle ve sabitler ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-164">Data elements at procedure level are limited to local variables and constants.</span></span>  
  
## <a name="the-main-procedure"></a><span data-ttu-id="a0b4f-165">Ana yordam</span><span class="sxs-lookup"><span data-stu-id="a0b4f-165">The Main Procedure</span></span>  

 <span data-ttu-id="a0b4f-166">`Main`Yordam, uygulamanız yüklendiğinde çalıştırılacak ilk koddur.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-166">The `Main` procedure is the first code to run when your application has been loaded.</span></span> <span data-ttu-id="a0b4f-167">`Main` , uygulamanız için başlangıç noktası ve genel denetim olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-167">`Main` serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="a0b4f-168">Dört değişken vardır `Main` :</span><span class="sxs-lookup"><span data-stu-id="a0b4f-168">There are four varieties of `Main`:</span></span>  
  
- `Sub Main()`  
  
- `Sub Main(ByVal cmdArgs() As String)`  
  
- `Function Main() As Integer`  
  
- `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 <span data-ttu-id="a0b4f-169">Bu yordamın en yaygın çeşitliliği şunlardır `Sub Main()` .</span><span class="sxs-lookup"><span data-stu-id="a0b4f-169">The most common variety of this procedure is `Sub Main()`.</span></span> <span data-ttu-id="a0b4f-170">Daha fazla bilgi için bkz. [Visual Basic ana yordam](main-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="a0b4f-170">For more information, see [Main Procedure in Visual Basic](main-procedure.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0b4f-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0b4f-171">See also</span></span>

- [<span data-ttu-id="a0b4f-172">Visual Basic'de Ana Yordam</span><span class="sxs-lookup"><span data-stu-id="a0b4f-172">Main Procedure in Visual Basic</span></span>](main-procedure.md)
- [<span data-ttu-id="a0b4f-173">Visual Basic Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="a0b4f-173">Visual Basic Naming Conventions</span></span>](naming-conventions.md)
- [<span data-ttu-id="a0b4f-174">Visual Basic Sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="a0b4f-174">Visual Basic Limitations</span></span>](limitations.md)
