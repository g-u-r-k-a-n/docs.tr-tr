---
title: -Doc (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- FileProperties.BuildAction
- /doc
helpviewer_keywords:
- comments, C# code
- XML documentation [C#], comments in source files
- doc compiler option [C#]
- Visual C#, XML documentation for
- -doc compiler option [C#]
- /doc compiler option [C#]
ms.assetid: 849eea59-c936-4311-bad8-d07404480f2a
ms.openlocfilehash: 01ea71f3de9e30abe25184e38a59f3707b54bd5a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422967"
---
# <a name="-doc-c-compiler-options"></a><span data-ttu-id="0ce16-102">-Doc (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="0ce16-102">-doc (C# Compiler Options)</span></span>
<span data-ttu-id="0ce16-103">**-Doc** seçeneği, belge AÇıKLAMALARıNı bir XML dosyasına eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ce16-103">The **-doc** option allows you to place documentation comments in an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ce16-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ce16-104">Syntax</span></span>  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="0ce16-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0ce16-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="0ce16-106">Derlemenin kaynak kodu dosyalarındaki yorumlarla doldurulan XML için çıkış dosyası.</span><span class="sxs-lookup"><span data-stu-id="0ce16-106">The output file for XML, which is populated with the comments in the source code files of the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ce16-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ce16-107">Remarks</span></span>  
 <span data-ttu-id="0ce16-108">Kaynak kodu dosyalarında, aşağıdakilerden önce gelen belge açıklamaları işlenebilir ve XML dosyasına eklenebilir:</span><span class="sxs-lookup"><span data-stu-id="0ce16-108">In source code files, documentation comments that precede the following can be processed and added to the XML file:</span></span>  
  
- <span data-ttu-id="0ce16-109">Bir [sınıf](../keywords/class.md), [temsilci](../builtin-types/reference-types.md#the-delegate-type)veya [arabirim](../keywords/interface.md) olarak Kullanıcı tanımlı türler</span><span class="sxs-lookup"><span data-stu-id="0ce16-109">Such user-defined types as a [class](../keywords/class.md), [delegate](../builtin-types/reference-types.md#the-delegate-type), or [interface](../keywords/interface.md)</span></span>  
  
- <span data-ttu-id="0ce16-110">Alan, [olay](../keywords/event.md), [özellik](../../programming-guide/classes-and-structs/using-properties.md)veya yöntem olarak bu Üyeler</span><span class="sxs-lookup"><span data-stu-id="0ce16-110">Such members as a field, [event](../keywords/event.md), [property](../../programming-guide/classes-and-structs/using-properties.md), or method</span></span>  
  
 <span data-ttu-id="0ce16-111">Main içeren kaynak kodu dosyası ilk olarak XML 'e çıktı.</span><span class="sxs-lookup"><span data-stu-id="0ce16-111">The source code file that contains Main is output first into the XML.</span></span>  
  
 <span data-ttu-id="0ce16-112">[IntelliSense](/visualstudio/ide/using-intellisense) özelliğiyle kullanılmak üzere oluşturulan. xml dosyasını kullanmak için,. xml dosyasının dosya adının desteklemek istediğiniz derlemeyle aynı olmasına izin verin ve. xml dosyasının derlemeyle aynı dizinde olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="0ce16-112">To use the generated .xml file for use with the [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the .xml file be the same as the assembly you want to support and then make sure the .xml file is in the same directory as the assembly.</span></span> <span data-ttu-id="0ce16-113">Bu nedenle, Visual Studio projesinde derlemeye başvuruluyorsa. xml dosyası da bulunur.</span><span class="sxs-lookup"><span data-stu-id="0ce16-113">Thus, when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="0ce16-114">Bkz. [kod açıklamaları sağlama](/visualstudio/ide/reference/generate-xml-documentation-comments) ve daha fazla bilgi.</span><span class="sxs-lookup"><span data-stu-id="0ce16-114">See [Supplying Code Comments](/visualstudio/ide/reference/generate-xml-documentation-comments) and for more information.</span></span>  
  
 <span data-ttu-id="0ce16-115">[-Target: Module](./target-module-compiler-option.md)ile derlenmediğiniz takdirde `file`, derlemenin çıkış dosyası için derleme bildirimini içeren dosyanın adını belirten \<bütünleştirilmiş kod >\</assembly > etiketleri içerecektir.</span><span class="sxs-lookup"><span data-stu-id="0ce16-115">Unless you compile with [-target:module](./target-module-compiler-option.md), `file` will contain \<assembly>\</assembly> tags specifying the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ce16-116">-Doc seçeneği tüm giriş dosyaları için geçerlidir; veya proje ayarları 'nda ayarlandıysa, projedeki tüm dosyalar.</span><span class="sxs-lookup"><span data-stu-id="0ce16-116">The -doc option applies to all input files; or, if set in the Project Settings, all files in the project.</span></span> <span data-ttu-id="0ce16-117">Belirli bir dosyanın veya kod bölümünün belge açıklamalarıyla ilgili uyarıları devre dışı bırakmak için [#pragma uyarı](../preprocessor-directives/preprocessor-pragma-warning.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="0ce16-117">To disable warnings related to documentation comments for a specific file or section of code, use [#pragma warning](../preprocessor-directives/preprocessor-pragma-warning.md).</span></span>  
  
 <span data-ttu-id="0ce16-118">Kodunuzda açıklamalardan belge oluşturma yolları için bkz. [belge açıklamaları Için önerilen Etiketler](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) .</span><span class="sxs-lookup"><span data-stu-id="0ce16-118">See [Recommended Tags for Documentation Comments](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="0ce16-119">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="0ce16-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="0ce16-120">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="0ce16-120">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="0ce16-121">**Derleme** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="0ce16-121">Click the **Build** tab.</span></span>  
  
3. <span data-ttu-id="0ce16-122">**XML belge dosyası** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0ce16-122">Modify the **XML documentation file** property.</span></span>  
  
 <span data-ttu-id="0ce16-123">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="0ce16-123">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ce16-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ce16-124">See also</span></span>

- [<span data-ttu-id="0ce16-125">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="0ce16-125">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="0ce16-126">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="0ce16-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
