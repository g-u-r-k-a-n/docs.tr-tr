---
title: Örnek Derleme Komut Satırları
ms.date: 03/13/2018
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
ms.openlocfilehash: 496627d3b77b0382ae7d15c8225a6fbd41f1db73
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403128"
---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="875c6-102">Örnek derleme komut satırları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="875c6-102">Sample compilation command lines (Visual Basic)</span></span>

<span data-ttu-id="875c6-103">Visual Studio içinden Visual Basic programları derlemeye alternatif olarak, çalıştırılabilir (. exe) dosyalar veya dinamik bağlantı kitaplığı (. dll) dosyaları oluşturmak için komut satırından derleme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="875c6-103">As an alternative to compiling Visual Basic programs from within Visual Studio, you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>

<span data-ttu-id="875c6-104">Visual Basic komut satırı derleyicisi, giriş ve çıkış dosyalarını, derlemeleri ve hata ayıklama ve Önişlemci seçeneklerini denetleyen tam bir seçenek kümesini destekler.</span><span class="sxs-lookup"><span data-stu-id="875c6-104">The Visual Basic command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="875c6-105">Her seçenek, iki değiştirilebilir formda mevcuttur: `-option` ve `/option` .</span><span class="sxs-lookup"><span data-stu-id="875c6-105">Each option is available in two interchangeable forms: `-option` and `/option`.</span></span> <span data-ttu-id="875c6-106">Bu belgede yalnızca form gösterilmektedir `-option` .</span><span class="sxs-lookup"><span data-stu-id="875c6-106">This documentation shows only the `-option` form.</span></span>

<span data-ttu-id="875c6-107">Aşağıdaki tabloda, kendi kullanımı için değiştirebileceğiniz bazı örnek komut satırları listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="875c6-107">The following table lists some sample command lines you can modify for your own use.</span></span>

|<span data-ttu-id="875c6-108">Alıcı</span><span class="sxs-lookup"><span data-stu-id="875c6-108">To</span></span>|<span data-ttu-id="875c6-109">Kullanım</span><span class="sxs-lookup"><span data-stu-id="875c6-109">Use</span></span>|
|--------|---------|
|<span data-ttu-id="875c6-110">Dosya. vb dosyasını derleyin ve File. exe oluşturun</span><span class="sxs-lookup"><span data-stu-id="875c6-110">Compile File.vb and create File.exe</span></span>|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|
|<span data-ttu-id="875c6-111">File. vb dosyasını derleyin ve File. dll dosyasını oluşturun</span><span class="sxs-lookup"><span data-stu-id="875c6-111">Compile File.vb and create File.dll</span></span>|`vbc -target:library File.vb`|
|<span data-ttu-id="875c6-112">Dosya. vb 'yi derleyin ve My. exe dosyasını oluşturun</span><span class="sxs-lookup"><span data-stu-id="875c6-112">Compile File.vb and create My.exe</span></span>|`vbc -out:My.exe File.vb`|
|<span data-ttu-id="875c6-113">File. vb derleyin ve hem bir kitaplık hem de File. dll adlı bir başvuru derlemesi oluşturun</span><span class="sxs-lookup"><span data-stu-id="875c6-113">Compile File.vb and create both a library and a reference assembly named File.dll</span></span>|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|<span data-ttu-id="875c6-114">Geçerli dizindeki tüm Visual Basic dosyalarını, iyileştirmeler açık ve `DEBUG` tanımlanan sembolle derleyin, dosya2. exe dosyasını üretir</span><span class="sxs-lookup"><span data-stu-id="875c6-114">Compile all Visual Basic files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|
|<span data-ttu-id="875c6-115">Logo veya uyarıları görüntülemeden dosya2. dll ' nin hata ayıklama sürümünü üreten geçerli dizindeki tüm Visual Basic dosyalarını derleyin</span><span class="sxs-lookup"><span data-stu-id="875c6-115">Compile all Visual Basic files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|
|<span data-ttu-id="875c6-116">Geçerli dizindeki tüm Visual Basic dosyalarını bir. dll dosyasına derle</span><span class="sxs-lookup"><span data-stu-id="875c6-116">Compile all Visual Basic files in the current directory to Something.dll</span></span>|`vbc -target:library -out:Something.dll *.vb`|

> [!TIP]
> <span data-ttu-id="875c6-117">Visual Studio IDE kullanarak bir proje oluşturduğunuzda, ilişkili **vbc** komutuyla ilgili bilgileri çıkış penceresinde derleyici seçenekleriyle birlikte görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="875c6-117">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="875c6-118">Bu bilgileri göstermek için, [Seçenekler Iletişim kutusu, projeler ve çözümler ' i açın ve çalıştırın](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), sonra **MSBuild proje yapı çıkış ayrıntı** düzeyini **normal** veya daha yüksek ayrıntı düzeyi olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="875c6-118">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span>

## <a name="see-also"></a><span data-ttu-id="875c6-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="875c6-119">See also</span></span>

- [<span data-ttu-id="875c6-120">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="875c6-120">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="875c6-121">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="875c6-121">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)
