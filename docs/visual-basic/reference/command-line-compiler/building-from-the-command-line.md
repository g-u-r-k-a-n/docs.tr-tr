---
description: 'Hakkında daha fazla bilgi edinin: komut satırından oluşturma (Visual Basic)'
title: Komut Satırından Derleme
ms.date: 07/20/2015
helpviewer_keywords:
- builds [Visual Basic], command-line
- Visual Basic compiler, about Visual Basic compiler
- command line [Visual Basic], compilers
- command line [Visual Basic], building from
- command line [Visual Basic], builds
- compilers [Visual Basic], invoking from command line
- command-line builds
- compiling source code
- command-line compilers [Visual Basic], Visual Basic
- command line [Visual Basic], Visual Basic
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
ms.openlocfilehash: 5f0f8dd61bd5b79987cc1e59dcf4bfd8071a925e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468271"
---
# <a name="building-from-the-command-line-visual-basic"></a><span data-ttu-id="8156d-103">Komut Satırından Derleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8156d-103">Building from the Command Line (Visual Basic)</span></span>

<span data-ttu-id="8156d-104">Bir Visual Basic projesi bir veya daha fazla ayrı kaynak dosyadan oluşur.</span><span class="sxs-lookup"><span data-stu-id="8156d-104">A Visual Basic project is made up of one or more separate source files.</span></span> <span data-ttu-id="8156d-105">Derleme olarak bilinen işlem sırasında, bu dosyalar tek bir pakette birlikte getirilir; bir uygulama olarak çalıştırılabilen tek bir yürütülebilir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="8156d-105">During the process known as compilation, these files are brought together into one package—a single executable file that can be run as an application.</span></span>

<span data-ttu-id="8156d-106">Visual Basic, Visual Studio tümleşik geliştirme ortamı (IDE) içinden program derlemeye alternatif olarak bir komut satırı derleyicisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8156d-106">Visual Basic provides a command-line compiler as an alternative to compiling programs from within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="8156d-107">Komut satırı derleyicisi, IDE 'de tam özellik kümesine gerek olmayan (örneğin, sınırlı sistem belleği veya depolama alanı olan bilgisayarlar için kullanırken veya yazarken) gerekli durumlar için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8156d-107">The command-line compiler is designed for situations in which you do not require the full set of features in the IDE—for example, when you are using or writing for computers with limited system memory or storage space.</span></span>

<span data-ttu-id="8156d-108">Visual Studio IDE içinden kaynak dosyalarını derlemek için, **Derle** menüsünde **Build** komutunu seçin.</span><span class="sxs-lookup"><span data-stu-id="8156d-108">To compile source files from within the Visual Studio IDE, choose the **Build** command from the **Build** menu.</span></span>

> [!TIP]
> <span data-ttu-id="8156d-109">Visual Studio IDE 'yi kullanarak proje dosyaları oluşturduğunuzda, ilişkili **vbc** komutu ve bu dosyanın anahtarları hakkında bilgileri çıkış penceresinde görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8156d-109">When you build project files by using the Visual Studio IDE, you can display information about the associated **vbc** command and its switches in the output window.</span></span> <span data-ttu-id="8156d-110">Bu bilgileri göstermek için, [Seçenekler Iletişim kutusu, projeler ve çözümler ' i açın ve çalıştırın](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), sonra **MSBuild proje yapı çıkış ayrıntı** düzeyini **normal** veya daha yüksek ayrıntı düzeyi olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8156d-110">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="8156d-111">Daha fazla bilgi için bkz. [nasıl yapılır: yapı günlüğü dosyalarını görüntüleme, kaydetme ve yapılandırma](/visualstudio/ide/how-to-view-save-and-configure-build-log-files).</span><span class="sxs-lookup"><span data-stu-id="8156d-111">For more information, see [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files).</span></span>

<span data-ttu-id="8156d-112">MSBuild kullanarak, bir komut isteminde proje (. vbproj) dosyalarını derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8156d-112">You can compile project (.vbproj) files at a command prompt by using MSBuild.</span></span> <span data-ttu-id="8156d-113">Daha fazla bilgi için bkz. [komut satırı başvurusu](/visualstudio/msbuild/msbuild-command-line-reference) ve [Izlenecek yol: MSBuild kullanma](/visualstudio/msbuild/walkthrough-using-msbuild).</span><span class="sxs-lookup"><span data-stu-id="8156d-113">For more information, see [Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) and [Walkthrough: Using MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="8156d-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8156d-114">In This Section</span></span>

<span data-ttu-id="8156d-115">[Nasıl yapılır: Command-Line derleyicisini çağırma](how-to-invoke-the-command-line-compiler.md) </span><span class="sxs-lookup"><span data-stu-id="8156d-115">[How to: Invoke the Command-Line Compiler](how-to-invoke-the-command-line-compiler.md) </span></span>\
<span data-ttu-id="8156d-116">Komut satırı derleyicisinin MS-DOS isteminde veya belirli bir alt dizinden nasıl çağırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8156d-116">Describes how to invoke the command-line compiler at the MS-DOS prompt or from a specific subdirectory.</span></span>

<span data-ttu-id="8156d-117">[Örnek derleme komut satırları](sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="8156d-117">[Sample Compilation Command Lines](sample-compilation-command-lines.md) </span></span>\
<span data-ttu-id="8156d-118">Kendi kullanımı için değiştirebileceğiniz örnek komut satırlarının bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8156d-118">Provides a list of sample command lines that you can modify for your own use.</span></span>

## <a name="related-sections"></a><span data-ttu-id="8156d-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="8156d-119">Related Sections</span></span>

<span data-ttu-id="8156d-120">[Visual Basic Command-Line derleyicisi](index.md) </span><span class="sxs-lookup"><span data-stu-id="8156d-120">[Visual Basic Command-Line Compiler](index.md) </span></span>\
<span data-ttu-id="8156d-121">Alfabetik olarak veya amacına göre düzenlenmiş derleyici seçeneklerinin listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8156d-121">Provides lists of compiler options, organized alphabetically or by purpose.</span></span>

<span data-ttu-id="8156d-122">[Koşullu derleme](../../programming-guide/program-structure/conditional-compilation.md) </span><span class="sxs-lookup"><span data-stu-id="8156d-122">[Conditional Compilation](../../programming-guide/program-structure/conditional-compilation.md) </span></span>\
<span data-ttu-id="8156d-123">Kodun belirli bölümlerinin nasıl derlenebileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="8156d-123">Describes how to compile particular sections of code.</span></span>

<span data-ttu-id="8156d-124">[Visual Studio 'da projeler ve çözümler oluşturma ve Temizleme](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) </span><span class="sxs-lookup"><span data-stu-id="8156d-124">[Building and Cleaning Projects and Solutions in Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) </span></span>\
<span data-ttu-id="8156d-125">Farklı yapılarda nelerin ekleneceğini nasıl düzenleyebileceğinizi, proje özellikleri ' ni seçmenizi ve projelerin doğru sırada oluşturulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8156d-125">Describes how to organize what will be included in different builds, choose project properties, and ensure that projects build in the correct order.</span></span>
