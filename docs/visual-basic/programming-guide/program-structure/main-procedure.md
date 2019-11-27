---
title: Main Yordamı
ms.date: 07/20/2015
f1_keywords:
- vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
ms.openlocfilehash: 61cd397b82b4bb9a8b24a1a7d30eaea68e37368f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347353"
---
# <a name="main-procedure-in-visual-basic"></a><span data-ttu-id="d9bfe-102">Visual Basic'de Ana Yordam</span><span class="sxs-lookup"><span data-stu-id="d9bfe-102">Main Procedure in Visual Basic</span></span>
<span data-ttu-id="d9bfe-103">Her Visual Basic uygulaması `Main`adlı bir yordam içermelidir.</span><span class="sxs-lookup"><span data-stu-id="d9bfe-103">Every Visual Basic application must contain a procedure called `Main`.</span></span> <span data-ttu-id="d9bfe-104">Bu yordam, uygulamanız için başlangıç noktası ve genel denetim görevi görür.</span><span class="sxs-lookup"><span data-stu-id="d9bfe-104">This procedure serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="d9bfe-105">.NET Framework, uygulamanızı yüklemiş ve denetimi geçirmeye hazırsa `Main` yordamınız çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d9bfe-105">The .NET Framework calls your `Main` procedure when it has loaded your application and is ready to pass control to it.</span></span> <span data-ttu-id="d9bfe-106">Bir Windows Forms uygulaması oluşturmadıkça, kendi kendilerine çalışan uygulamalar için `Main` yordamını yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d9bfe-106">Unless you are creating a Windows Forms application, you must write the `Main` procedure for applications that run on their own.</span></span>

 <span data-ttu-id="d9bfe-107">`Main` ilk olarak çalışan kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="d9bfe-107">`Main` contains the code that runs first.</span></span> <span data-ttu-id="d9bfe-108">`Main`, program başlatıldığında ilk olarak hangi formun yükleneceğini belirleyebilirsiniz, uygulamanızın bir kopyasının sistemde zaten çalışmakta olup olmadığını bulabilir, uygulamanız için bir dizi değişken oluşturabilir veya uygulamanın gerektirdiği bir veritabanını açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9bfe-108">In `Main`, you can determine which form is to be loaded first when the program starts, find out if a copy of your application is already running on the system, establish a set of variables for your application, or open a database that the application requires.</span></span>

## <a name="requirements-for-the-main-procedure"></a><span data-ttu-id="d9bfe-109">Ana yordamın gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="d9bfe-109">Requirements for the Main Procedure</span></span>
 <span data-ttu-id="d9bfe-110">Kendi üzerinde çalışan bir dosya (genellikle uzantısı. exe) bir `Main` yordamı içermelidir.</span><span class="sxs-lookup"><span data-stu-id="d9bfe-110">A file that runs on its own (usually with extension .exe) must contain a `Main` procedure.</span></span> <span data-ttu-id="d9bfe-111">Bir kitaplık (örneğin,. dll uzantılı) kendi üzerinde çalışmaz ve `Main` yordamı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="d9bfe-111">A library (for example with extension .dll) does not run on its own and does not require a `Main` procedure.</span></span> <span data-ttu-id="d9bfe-112">Oluşturabileceğiniz farklı proje türleri için gereksinimler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d9bfe-112">The requirements for the different types of projects you can create are as follows:</span></span>

- <span data-ttu-id="d9bfe-113">Konsol uygulamaları kendi üzerinde çalışır ve en az bir `Main` yordamı sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d9bfe-113">Console applications run on their own, and you must supply at least one `Main` procedure.</span></span>

- <span data-ttu-id="d9bfe-114">Windows Forms uygulamalar kendi kendilerine çalışır.</span><span class="sxs-lookup"><span data-stu-id="d9bfe-114">Windows Forms applications run on their own.</span></span> <span data-ttu-id="d9bfe-115">Ancak, Visual Basic derleyici bu uygulama için otomatik olarak bir `Main` yordamı oluşturur ve bir tane yazmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d9bfe-115">However, the Visual Basic compiler automatically generates a `Main` procedure in such an application, and you do not need to write one.</span></span>

- <span data-ttu-id="d9bfe-116">Sınıf kitaplıkları `Main` yordam gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="d9bfe-116">Class libraries do not require a `Main` procedure.</span></span> <span data-ttu-id="d9bfe-117">Bunlar Windows Denetim kitaplıklarını ve Web denetim kitaplıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="d9bfe-117">These include Windows Control Libraries and Web Control Libraries.</span></span> <span data-ttu-id="d9bfe-118">Web uygulamaları, sınıf kitaplıkları olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="d9bfe-118">Web applications are deployed as class libraries.</span></span>

## <a name="declaring-the-main-procedure"></a><span data-ttu-id="d9bfe-119">Ana yordamı bildirme</span><span class="sxs-lookup"><span data-stu-id="d9bfe-119">Declaring the Main Procedure</span></span>
 <span data-ttu-id="d9bfe-120">`Main` yordamı belirtmenin dört yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="d9bfe-120">There are four ways to declare the `Main` procedure.</span></span> <span data-ttu-id="d9bfe-121">Bağımsız değişkenler alabilir veya içermez ve bir değer döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="d9bfe-121">It can take arguments or not, and it can return a value or not.</span></span>

> [!NOTE]
> <span data-ttu-id="d9bfe-122">Bir sınıfta `Main` bildirirseniz `Shared` anahtar sözcüğünü kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d9bfe-122">If you declare `Main` in a class, you must use the `Shared` keyword.</span></span> <span data-ttu-id="d9bfe-123">Bir modülde, `Main` `Shared`olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d9bfe-123">In a module, `Main` does not need to be `Shared`.</span></span>

- <span data-ttu-id="d9bfe-124">En basit yol, bağımsız değişken almaz veya bir değer döndürmemelidir `Sub` yordamı bildirmenin bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="d9bfe-124">The simplest way is to declare a `Sub` procedure that does not take arguments or return a value.</span></span>

    ```vb
    Module mainModule
        Sub Main()
            MsgBox("The Main procedure is starting the application.")
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```

- <span data-ttu-id="d9bfe-125">`Main`, işletim sisteminin programınız için çıkış kodu olarak kullandığı bir `Integer` değeri de döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="d9bfe-125">`Main` can also return an `Integer` value, which the operating system uses as the exit code for your program.</span></span> <span data-ttu-id="d9bfe-126">Diğer programlar Windows ERRORLEVEL değerini inceleyerek bu kodu test edebilir.</span><span class="sxs-lookup"><span data-stu-id="d9bfe-126">Other programs can test this code by examining the Windows ERRORLEVEL value.</span></span> <span data-ttu-id="d9bfe-127">Çıkış kodu döndürmek için, `Main` `Sub` yordamı yerine `Function` yordamı olarak bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d9bfe-127">To return an exit code, you must declare `Main` as a `Function` procedure instead of a `Sub` procedure.</span></span>

    ```vb
    Module mainModule
        Function Main() As Integer
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' Insert call to appropriate starting place in your code.
            ' On return, assign appropriate value to returnValue.
            ' 0 usually means successful completion.
            MsgBox("The application is terminating with error level " &
                 CStr(returnValue) & ".")
            Return returnValue
        End Function
    End Module
    ```

- <span data-ttu-id="d9bfe-128">`Main`, bir `String` dizisini bağımsız değişken olarak da alabilir.</span><span class="sxs-lookup"><span data-stu-id="d9bfe-128">`Main` can also take a `String` array as an argument.</span></span> <span data-ttu-id="d9bfe-129">Dizideki her dize, programınızı çağırmak için kullanılan komut satırı bağımsız değişkenlerinden birini içerir.</span><span class="sxs-lookup"><span data-stu-id="d9bfe-129">Each string in the array contains one of the command-line arguments used to invoke your program.</span></span> <span data-ttu-id="d9bfe-130">Değerlerine bağlı olarak farklı eylemler gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9bfe-130">You can take different actions depending on their values.</span></span>

    ```vb
    Module mainModule
        Function Main(ByVal cmdArgs() As String) As Integer
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
            End If
            ' Insert call to appropriate starting place in your code.
            ' On return, assign appropriate value to returnValue.
            ' 0 usually means successful completion.
            MsgBox("The application is terminating with error level " &
                 CStr(returnValue) & ".")
            Return returnValue
        End Function
    End Module
    ```

- <span data-ttu-id="d9bfe-131">Komut satırı bağımsız değişkenlerini incelemek için `Main` bildirebilirsiniz, ancak aşağıdaki gibi bir çıkış kodu döndürmez.</span><span class="sxs-lookup"><span data-stu-id="d9bfe-131">You can declare `Main` to examine the command-line arguments but not return an exit code, as follows.</span></span>

    ```vb
    Module mainModule
        Sub Main(ByVal cmdArgs() As String)
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
            End If
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```
  
## <a name="see-also"></a><span data-ttu-id="d9bfe-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9bfe-132">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>
- <xref:System.Array.Length%2A>
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="d9bfe-133">Visual Basic programın yapısı</span><span class="sxs-lookup"><span data-stu-id="d9bfe-133">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="d9bfe-134">-main</span><span class="sxs-lookup"><span data-stu-id="d9bfe-134">-main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)
- [<span data-ttu-id="d9bfe-135">Shared</span><span class="sxs-lookup"><span data-stu-id="d9bfe-135">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="d9bfe-136">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="d9bfe-136">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="d9bfe-137">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="d9bfe-137">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="d9bfe-138">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="d9bfe-138">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="d9bfe-139">String Veri Türü</span><span class="sxs-lookup"><span data-stu-id="d9bfe-139">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
