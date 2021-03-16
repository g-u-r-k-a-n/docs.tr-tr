---
title: 'Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme'
description: Bir .NET uygulamasını derlerken, Izleme ve hata ayıklama koşullu özniteliklerini koşullu olarak derlemeyi öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- trace compiler options
- trace statements
- compiling source code, trace statements
- tracing [.NET Framework], enabling or disabling
- tracing [.NET Framework], compiling conditionally
- TRACE directive
- conditional compilation, tracing code
ms.assetid: 56d051c3-012c-42c1-9a58-7270edc624aa
ms.openlocfilehash: 90c989bcf21e24cf7ccf410c9a18a44cde81233e
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103478209"
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a><span data-ttu-id="85d40-103">Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="85d40-103">How to: Compile Conditionally with Trace and Debug</span></span>

<span data-ttu-id="85d40-104">Geliştirme sırasında bir uygulamada hata ayıklarken, hem izleme hem de hata ayıklama çıkışı Visual Studio 'daki çıkış penceresine gider.</span><span class="sxs-lookup"><span data-stu-id="85d40-104">While you are debugging an application during development, both your tracing and debugging output go to the Output window in Visual Studio.</span></span> <span data-ttu-id="85d40-105">Ancak, dağıtılmış bir uygulamada izleme özelliklerini dahil etmek için, izlenen uygulamalarınızı **Trace** derleyici yönergesi etkinken derlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="85d40-105">However, to include tracing features in a deployed application, you must compile your instrumented applications with the **TRACE** compiler directive enabled.</span></span> <span data-ttu-id="85d40-106">Bu, izleme kodunun uygulamanızın yayın sürümüne derlenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="85d40-106">This allows tracing code to be compiled into the release version of your application.</span></span> <span data-ttu-id="85d40-107">**İzleme** yönergesini etkinleştirmezseniz, derleme sırasında tüm izleme kodu yok sayılır ve dağıtacağınız yürütülebilir koda dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="85d40-107">If you do not enable the **TRACE** directive, all tracing code is ignored during compilation and is not included in the executable code that you will deploy.</span></span>  
  
 <span data-ttu-id="85d40-108">Hem izleme hem de hata ayıklama yöntemlerinin ilişkili koşullu öznitelikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="85d40-108">Both the tracing and debugging methods have associated conditional attributes.</span></span> <span data-ttu-id="85d40-109">Örneğin, izlemenin koşullu özniteliği **true** ise, tüm Trace deyimleri bir derlemeye (derlenmiş bir. exe dosyası veya. dll) dahil edilir; **Trace** Conditional özniteliği **false** ise, Trace deyimleri dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="85d40-109">For example, if the conditional attribute for tracing is **true**, all trace statements are included within an assembly (a compiled .exe file or .dll); if the **Trace** conditional attribute is **false**, the trace statements are not included.</span></span>  
  
 <span data-ttu-id="85d40-110">Bir derleme veya her ikisi için de **Trace** veya **Debug** koşullu özniteliği açık olabilir ya da hiçbiri.</span><span class="sxs-lookup"><span data-stu-id="85d40-110">You can have either the **Trace** or **Debug** conditional attribute turned on for a build, or both, or neither.</span></span> <span data-ttu-id="85d40-111">Bu nedenle, dört tür derleme vardır: **hata ayıklama**, **izleme**, her ikisi de veya hiçbiri.</span><span class="sxs-lookup"><span data-stu-id="85d40-111">Thus, there are four types of build: **Debug**, **Trace**, both, or neither.</span></span> <span data-ttu-id="85d40-112">Üretim dağıtımı için bazı yayın yapıları ne içermez; Çoğu hata ayıklama derlemesi her ikisini de içerir.</span><span class="sxs-lookup"><span data-stu-id="85d40-112">Some release builds for production deployment might contain neither; most debugging builds contain both.</span></span>  
  
 <span data-ttu-id="85d40-113">Uygulamanız için derleyici ayarlarını birkaç şekilde belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="85d40-113">You can specify the compiler settings for your application in several ways:</span></span>  
  
- <span data-ttu-id="85d40-114">Özellik sayfaları</span><span class="sxs-lookup"><span data-stu-id="85d40-114">The property pages</span></span>  
  
- <span data-ttu-id="85d40-115">Komut satırı</span><span class="sxs-lookup"><span data-stu-id="85d40-115">The command line</span></span>  
  
- <span data-ttu-id="85d40-116">**#CONST** (Visual Basic için) ve **#define** (C# için)</span><span class="sxs-lookup"><span data-stu-id="85d40-116">**#CONST** (for Visual Basic) and **#define** (for C#)</span></span>  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a><span data-ttu-id="85d40-117">Özellik sayfaları iletişim kutusundan derleme ayarlarını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="85d40-117">To change compile settings from the property pages dialog box</span></span>  
  
1. <span data-ttu-id="85d40-118">**Çözüm Gezgini**' de proje düğümüne sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="85d40-118">Right-click the project node in **Solution Explorer**.</span></span>  
  
2. <span data-ttu-id="85d40-119">Kısayol menüsünden **Özellikler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="85d40-119">Choose **Properties** from the shortcut menu.</span></span>  
  
    - <span data-ttu-id="85d40-120">Visual Basic, özellik sayfasının sol bölmesindeki **Derle** sekmesine tıklayın, ardından Gelişmiş **derleyici ayarları** Iletişim kutusunu göstermek için **Gelişmiş derleme seçenekleri** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="85d40-120">In Visual Basic, click the **Compile** tab in the left pane of the property page, then click the **Advanced Compile Options** button to display the **Advanced Compiler Settings** dialog box.</span></span> <span data-ttu-id="85d40-121">Etkinleştirmek istediğiniz derleyici ayarlarının onay kutularını seçin.</span><span class="sxs-lookup"><span data-stu-id="85d40-121">Select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="85d40-122">Devre dışı bırakmak istediğiniz ayarların onay kutularını temizleyin.</span><span class="sxs-lookup"><span data-stu-id="85d40-122">Clear the check boxes for settings you want to disable.</span></span>  
  
    - <span data-ttu-id="85d40-123">C# ' de, özellik sayfasının sol bölmesindeki **derleme** sekmesine tıklayın ve ardından etkinleştirmek istediğiniz derleyici ayarlarının onay kutularını seçin.</span><span class="sxs-lookup"><span data-stu-id="85d40-123">In C#, click the **Build** tab in the left pane of the property page, then select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="85d40-124">Devre dışı bırakmak istediğiniz ayarların onay kutularını temizleyin.</span><span class="sxs-lookup"><span data-stu-id="85d40-124">Clear the check boxes for settings you want to disable.</span></span>  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a><span data-ttu-id="85d40-125">Komut satırını kullanarak belgelenmiş kodu derlemek için</span><span class="sxs-lookup"><span data-stu-id="85d40-125">To compile instrumented code using the command line</span></span>  
  
1. <span data-ttu-id="85d40-126">Komut satırında koşullu bir derleyici anahtarı ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="85d40-126">Set a conditional compiler switch on the command line.</span></span> <span data-ttu-id="85d40-127">Derleyici, yürütülebilir dosyaya izleme veya hata ayıklama kodu içerecektir.</span><span class="sxs-lookup"><span data-stu-id="85d40-127">The compiler will include trace or debug code in the executable.</span></span>  
  
     <span data-ttu-id="85d40-128">Örneğin, komut satırına girilen aşağıdaki derleyici yönergesi, derleme kodunuzu derlenmiş bir yürütülebilir dosyaya dahil eder:</span><span class="sxs-lookup"><span data-stu-id="85d40-128">For example, the following compiler instruction entered on the command line would include your tracing code in a compiled executable:</span></span>  
  
     <span data-ttu-id="85d40-129">Visual Basic için: **vbc -r:System.dll-d:TRACE = true-d:DEBUG = false MyApplication. vb**</span><span class="sxs-lookup"><span data-stu-id="85d40-129">For Visual Basic: **vbc -r:System.dll -d:TRACE=TRUE -d:DEBUG=FALSE MyApplication.vb**</span></span>  
  
     <span data-ttu-id="85d40-130">C# için: **csc -r:System.dll-d:TRACE-d:DEBUG = FALSE MyApplication.cs**</span><span class="sxs-lookup"><span data-stu-id="85d40-130">For C#: **csc -r:System.dll -d:TRACE -d:DEBUG=FALSE MyApplication.cs**</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="85d40-131">Birden fazla uygulama dosyası derlemek için dosya adları arasında boş bir boşluk bırakın; Örneğin, **MyApplication1. vb MyApplication2. vb MyApplication3. vb** veya **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span><span class="sxs-lookup"><span data-stu-id="85d40-131">To compile more than one application file, leave a blank space between the file names, for example, **MyApplication1.vb MyApplication2.vb MyApplication3.vb** or **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span></span>  
  
     <span data-ttu-id="85d40-132">Yukarıdaki örneklerde kullanılan koşullu derleme yönergelerinin anlamı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="85d40-132">The meaning of the conditional-compilation directives used in the above examples is as follows:</span></span>  
  
    |<span data-ttu-id="85d40-133">Deki</span><span class="sxs-lookup"><span data-stu-id="85d40-133">Directive</span></span>|<span data-ttu-id="85d40-134">Anlamı</span><span class="sxs-lookup"><span data-stu-id="85d40-134">Meaning</span></span>|  
    |---------------|-------------|  
    |`vbc`|<span data-ttu-id="85d40-135">Visual Basic derleyici</span><span class="sxs-lookup"><span data-stu-id="85d40-135">Visual Basic compiler</span></span>|  
    |`csc`|<span data-ttu-id="85d40-136">C# derleyici</span><span class="sxs-lookup"><span data-stu-id="85d40-136">C# compiler</span></span>|  
    |`-r:`|<span data-ttu-id="85d40-137">Bir dış derlemeye (EXE veya DLL) başvurur</span><span class="sxs-lookup"><span data-stu-id="85d40-137">References an external assembly (EXE or DLL)</span></span>|  
    |`-d:`|<span data-ttu-id="85d40-138">Koşullu derleme sembolünü tanımlar</span><span class="sxs-lookup"><span data-stu-id="85d40-138">Defines a conditional compilation symbol</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="85d40-139">Büyük harflerle TRACE veya DEBUG yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="85d40-139">You must spell TRACE or DEBUG with uppercase letters.</span></span> <span data-ttu-id="85d40-140">Koşullu derleme komutları hakkında daha fazla bilgi için, `vbc /?` komut istemine (Visual Basic için) veya `csc /?` (C# için) girin.</span><span class="sxs-lookup"><span data-stu-id="85d40-140">For more information about the conditional compilation commands, enter `vbc /?` (for Visual Basic) or `csc /?` (for C#) at the command prompt.</span></span> <span data-ttu-id="85d40-141">Daha fazla bilgi için, bkz. [komut satırından oluşturma](../../csharp/language-reference/compiler-options/index.md) (C#) veya [Command-Line derleyicisini çağırma](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="85d40-141">For more information, see [Building from the Command Line](../../csharp/language-reference/compiler-options/index.md) (C#) or [Invoking the Command-Line Compiler](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span></span>  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a><span data-ttu-id="85d40-142">#CONST veya #define kullanarak koşullu derleme gerçekleştirmek için</span><span class="sxs-lookup"><span data-stu-id="85d40-142">To perform conditional compilation using #CONST or #define</span></span>  
  
1. <span data-ttu-id="85d40-143">Kaynak kodu dosyasının en üstünde programlama diliniz için uygun olan ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="85d40-143">Type the appropriate statement for your programming language at the top of the source code file.</span></span>  
  
    |<span data-ttu-id="85d40-144">Dil</span><span class="sxs-lookup"><span data-stu-id="85d40-144">Language</span></span>|<span data-ttu-id="85d40-145">Deyim</span><span class="sxs-lookup"><span data-stu-id="85d40-145">Statement</span></span>|<span data-ttu-id="85d40-146">Sonuç</span><span class="sxs-lookup"><span data-stu-id="85d40-146">Result</span></span>|  
    |--------------|---------------|------------|  
    |<span data-ttu-id="85d40-147">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="85d40-147">**Visual Basic**</span></span>|<span data-ttu-id="85d40-148">**#CONST TRACE = true**</span><span class="sxs-lookup"><span data-stu-id="85d40-148">**#CONST TRACE = true**</span></span>|<span data-ttu-id="85d40-149">İzlemeyi etkinleştirilir</span><span class="sxs-lookup"><span data-stu-id="85d40-149">Enables tracing</span></span>|  
    ||<span data-ttu-id="85d40-150">**#CONST TRACE = false**</span><span class="sxs-lookup"><span data-stu-id="85d40-150">**#CONST TRACE = false**</span></span>|<span data-ttu-id="85d40-151">İzlemeyi devre dışı bırakır</span><span class="sxs-lookup"><span data-stu-id="85d40-151">Disables tracing</span></span>|  
    ||<span data-ttu-id="85d40-152">**#CONST DEBUG = true**</span><span class="sxs-lookup"><span data-stu-id="85d40-152">**#CONST DEBUG = true**</span></span>|<span data-ttu-id="85d40-153">Hata ayıklamayı sağlar</span><span class="sxs-lookup"><span data-stu-id="85d40-153">Enables debugging</span></span>|  
    ||<span data-ttu-id="85d40-154">**#CONST DEBUG = false**</span><span class="sxs-lookup"><span data-stu-id="85d40-154">**#CONST DEBUG = false**</span></span>|<span data-ttu-id="85d40-155">Hata ayıklamayı devre dışı bırakır</span><span class="sxs-lookup"><span data-stu-id="85d40-155">Disables debugging</span></span>|  
    |<span data-ttu-id="85d40-156">**C#**</span><span class="sxs-lookup"><span data-stu-id="85d40-156">**C#**</span></span>|<span data-ttu-id="85d40-157">**#define Izleme**</span><span class="sxs-lookup"><span data-stu-id="85d40-157">**#define TRACE**</span></span>|<span data-ttu-id="85d40-158">İzlemeyi etkinleştirilir</span><span class="sxs-lookup"><span data-stu-id="85d40-158">Enables tracing</span></span>|  
    ||<span data-ttu-id="85d40-159">**#undef Izleme**</span><span class="sxs-lookup"><span data-stu-id="85d40-159">**#undef TRACE**</span></span>|<span data-ttu-id="85d40-160">İzlemeyi devre dışı bırakır</span><span class="sxs-lookup"><span data-stu-id="85d40-160">Disables tracing</span></span>|  
    ||<span data-ttu-id="85d40-161">**hata ayıklama #define**</span><span class="sxs-lookup"><span data-stu-id="85d40-161">**#define DEBUG**</span></span>|<span data-ttu-id="85d40-162">Hata ayıklamayı sağlar</span><span class="sxs-lookup"><span data-stu-id="85d40-162">Enables debugging</span></span>|  
    ||<span data-ttu-id="85d40-163">**hata ayıklama #undef**</span><span class="sxs-lookup"><span data-stu-id="85d40-163">**#undef DEBUG**</span></span>|<span data-ttu-id="85d40-164">Hata ayıklamayı devre dışı bırakır</span><span class="sxs-lookup"><span data-stu-id="85d40-164">Disables debugging</span></span>|  
  
### <a name="to-disable-tracing-or-debugging"></a><span data-ttu-id="85d40-165">İzlemeyi veya hata ayıklamayı devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="85d40-165">To disable tracing or debugging</span></span>  
  
<span data-ttu-id="85d40-166">Derleyici yönergesini kaynak kodınızdan silin.</span><span class="sxs-lookup"><span data-stu-id="85d40-166">Delete the compiler directive from your source code.</span></span>  
  
<span data-ttu-id="85d40-167">\- veya</span><span class="sxs-lookup"><span data-stu-id="85d40-167">\- or -</span></span>  
  
<span data-ttu-id="85d40-168">Derleyici yönergesini açıklama.</span><span class="sxs-lookup"><span data-stu-id="85d40-168">Comment out the compiler directive.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="85d40-169">**Derlemeye hazırsanız derleme menüsünden** **Oluştur** ' u seçebilir veya koşullu derleme sembolleri tanımlamak için **d:** yazmadan komut satırı yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="85d40-169">When you are ready to compile, you can either choose **Build** from the **Build** menu, or use the command line method but without typing the **d:** to define conditional compilation symbols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85d40-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85d40-170">See also</span></span>

- [<span data-ttu-id="85d40-171">Uygulamaları izleme ve İşaretleme</span><span class="sxs-lookup"><span data-stu-id="85d40-171">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="85d40-172">Nasıl yapılır: İzleme Anahtarları Oluşturma ve Başlatma</span><span class="sxs-lookup"><span data-stu-id="85d40-172">How to: Create, Initialize and Configure Trace Switches</span></span>](how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="85d40-173">İzleme Anahtarları</span><span class="sxs-lookup"><span data-stu-id="85d40-173">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="85d40-174">İz Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="85d40-174">Trace Listeners</span></span>](trace-listeners.md)
- [<span data-ttu-id="85d40-175">Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="85d40-175">How to: Add Trace Statements to Application Code</span></span>](how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="85d40-176">Visual Studio Komut Satırı için ortam değişkenlerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="85d40-176">How to set environment variables for the Visual Studio Command Line</span></span>](../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="85d40-177">Nasıl yapılır: Komut Satırı Derleyicisini Çağırma</span><span class="sxs-lookup"><span data-stu-id="85d40-177">How to: Invoke the Command-Line Compiler</span></span>](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
