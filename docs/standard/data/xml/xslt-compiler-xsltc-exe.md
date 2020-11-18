---
title: XSLT Derleyicisi (xsltc.exe)
ms.date: 03/30/2017
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
ms.openlocfilehash: cfeebc3ac0c0259c975439dc93c3c5f003b60c40
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818329"
---
# <a name="xslt-compiler-xsltcexe"></a><span data-ttu-id="17ab0-102">XSLT Derleyicisi (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="17ab0-102">XSLT Compiler (xsltc.exe)</span></span>
<span data-ttu-id="17ab0-103">XSLT derleyicisi (xsltc.exe) XSLT stil sayfalarını derler ve bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="17ab0-103">The XSLT compiler (xsltc.exe) compiles XSLT style sheets and generates an assembly.</span></span> <span data-ttu-id="17ab0-104">Derlenmiş stil sayfası daha sonra doğrudan <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> yöntemine geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="17ab0-104">The compiled style sheet can then be passed directly into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="17ab0-105">xsltc.exe ile imzalı derlemeler oluşturamazsınız.</span><span class="sxs-lookup"><span data-stu-id="17ab0-105">You cannot generate signed assemblies with xsltc.exe.</span></span>  
  
 <span data-ttu-id="17ab0-106">xsltc.exe aracı Visual Studio 'Ya dahildir.</span><span class="sxs-lookup"><span data-stu-id="17ab0-106">The xsltc.exe tool is included with Visual Studio.</span></span> <span data-ttu-id="17ab0-107">Daha fazla bilgi için bkz. [Visual Studio İndirmeleri](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span><span class="sxs-lookup"><span data-stu-id="17ab0-107">For more information, see the [Visual Studio Downloads](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17ab0-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="17ab0-108">Syntax</span></span>  
  
```console  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a><span data-ttu-id="17ab0-109">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="17ab0-109">Argument</span></span>  
  
|<span data-ttu-id="17ab0-110">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="17ab0-110">Argument</span></span>|<span data-ttu-id="17ab0-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="17ab0-111">Description</span></span>|  
|--------------|-----------------|  
|`sourceFile`|<span data-ttu-id="17ab0-112">Stil sayfasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="17ab0-112">Specifies the name of the style sheet.</span></span> <span data-ttu-id="17ab0-113">Stil sayfası yerel bir dosya olmalıdır veya intranette bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="17ab0-113">The style sheet must be a local file or be located on the intranet.</span></span>|  
  
## <a name="options"></a><span data-ttu-id="17ab0-114">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="17ab0-114">Options</span></span>  
  
|<span data-ttu-id="17ab0-115">Seçenek</span><span class="sxs-lookup"><span data-stu-id="17ab0-115">Option</span></span>|<span data-ttu-id="17ab0-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="17ab0-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="17ab0-117">`/c[lass]:` `name`</span><span class="sxs-lookup"><span data-stu-id="17ab0-117">`/c[lass]:` `name`</span></span>|<span data-ttu-id="17ab0-118">Aşağıdaki stil sayfası için sınıfın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="17ab0-118">Specifies the name of the class for the following style sheet.</span></span> <span data-ttu-id="17ab0-119">Sınıf adı tam olarak nitelenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="17ab0-119">The class name can be fully qualified.</span></span><br /><br /> <span data-ttu-id="17ab0-120">Sınıf adı varsayılan olarak stil sayfasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="17ab0-120">The class name defaults to the name of the style sheet.</span></span> <span data-ttu-id="17ab0-121">Örneğin, Customers. xsl stil sayfası derlenmişse, varsayılan sınıf adı müşteriler olur.</span><span class="sxs-lookup"><span data-stu-id="17ab0-121">For example, if the style sheet customers.xsl is compiled, the default class name is customers.</span></span>|  
|<span data-ttu-id="17ab0-122">`/debug[`+&#124;-`]`</span><span class="sxs-lookup"><span data-stu-id="17ab0-122">`/debug[`+&#124;-`]`</span></span>|<span data-ttu-id="17ab0-123">Hata ayıklama bilgilerinin oluşturulup oluşturulmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="17ab0-123">Specifies whether to generate debugging information.</span></span><br /><br /> <span data-ttu-id="17ab0-124">`+`Veya belirtildiğinde `/debug` , derleyicinin hata ayıklama bilgileri oluşturmasına ve bir program VERITABANı (pdb) dosyasına yerleştirmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="17ab0-124">Specifying `+` or `/debug`, causes the compiler to generate debugging information and put it in a program database (PDB) file.</span></span> <span data-ttu-id="17ab0-125">Oluşturulan PDB dosyasının adı `assemblyName` . pdb 'dir.</span><span class="sxs-lookup"><span data-stu-id="17ab0-125">The name of the generated PDB file is `assemblyName`.pdb.</span></span><br /><br /> <span data-ttu-id="17ab0-126">`-`Belirtmiyorsanız geçerli olan öğesini belirtme `/debug` , hiçbir hata ayıklama bilgisinin oluşturulmasına neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="17ab0-126">Specifying `-`, which is in effect if you do not specify `/debug`, causes no debug information to be created.</span></span> <span data-ttu-id="17ab0-127">Bir perakende derlemesi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="17ab0-127">A retail assembly is generated.</span></span> <span data-ttu-id="17ab0-128">**Note:**  Hata ayıklama modunda derleme, XSLT performansını önemli ölçüde etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="17ab0-128">**Note:**  Compiling in debug mode can affect XSLT performance significantly.</span></span>|  
|`/help`|<span data-ttu-id="17ab0-129">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="17ab0-129">Displays command syntax and options for the tool.</span></span>|  
|`/nologo`|<span data-ttu-id="17ab0-130">Derleyicinin telif hakkı iletisinin görüntülenmesini önler.</span><span class="sxs-lookup"><span data-stu-id="17ab0-130">Suppresses the compiler copyright message from displaying.</span></span>|  
|<span data-ttu-id="17ab0-131">`/platform:` `string`</span><span class="sxs-lookup"><span data-stu-id="17ab0-131">`/platform:` `string`</span></span>|<span data-ttu-id="17ab0-132">Derlemenin çalıştırılabilen platformları belirtir.</span><span class="sxs-lookup"><span data-stu-id="17ab0-132">Specifies the platforms that the assembly can be run on.</span></span> <span data-ttu-id="17ab0-133">Geçerli platform değerlerini aşağıda açıklanmıştır:</span><span class="sxs-lookup"><span data-stu-id="17ab0-133">The following describes the valid platform values:</span></span><br /><br /> <span data-ttu-id="17ab0-134">`x86` derlemenizi 32 bit, x86 uyumlu ortak dil çalışma zamanı tarafından çalıştırılacak şekilde derler</span><span class="sxs-lookup"><span data-stu-id="17ab0-134">`x86` compiles your assembly to be run by the 32-bit, x86-compatible common language runtime</span></span><br /><br /> <span data-ttu-id="17ab0-135">`x64` , derlemenizi AMD64 veya EM64T yönerge kümesini destekleyen bir bilgisayarda 64 bitlik ortak dil çalışma zamanı tarafından çalıştırılacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="17ab0-135">`x64` compiles your assembly to be run by the 64-bit common language runtime on a computer that supports the AMD64 or EM64T instruction set.</span></span><br /><br /> <span data-ttu-id="17ab0-136">Itanium, derlemenizi Itanium işlemcisine sahip bir bilgisayarda 64 bitlik ortak dil çalışma zamanı tarafından çalıştırılacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="17ab0-136">Itanium compiles your assembly to be run by the 64-bit common language runtime on a computer that has an Itanium processor.</span></span><br /><br /> <span data-ttu-id="17ab0-137">`anycpu` derlemenizi herhangi bir platformda çalışacak şekilde derler.</span><span class="sxs-lookup"><span data-stu-id="17ab0-137">`anycpu` compiles your assembly to run on any platform.</span></span> <span data-ttu-id="17ab0-138">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="17ab0-138">This is the default.</span></span>|  
|<span data-ttu-id="17ab0-139">`/out:` `assemblyName`</span><span class="sxs-lookup"><span data-stu-id="17ab0-139">`/out:` `assemblyName`</span></span>|<span data-ttu-id="17ab0-140">Çıktı olan derlemenin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="17ab0-140">Specifies the name of the assembly that is output.</span></span> <span data-ttu-id="17ab0-141">Birden çok stil sayfası varsa, derleme adı varsayılan olarak ana stil sayfasının adı veya ilk stil sayfası olur.</span><span class="sxs-lookup"><span data-stu-id="17ab0-141">The assembly name defaults to the name of the main style sheet or the first style sheet if multiple style sheets are present.</span></span><br /><br /> <span data-ttu-id="17ab0-142">Stil sayfası betikler içeriyorsa, betikler ayrı bir derlemeye kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="17ab0-142">If the style sheet contains scripts, the scripts are saved to a separate assembly.</span></span> <span data-ttu-id="17ab0-143">Betik derleme adları ana derleme adından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="17ab0-143">Script assembly names are generated from the main assembly name.</span></span> <span data-ttu-id="17ab0-144">Örneğin, derleme adınız için CustOrders.dll belirttiyseniz, ilk betik derlemesi CustOrders_Script1.dll olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="17ab0-144">For example, if you specified CustOrders.dll for your assembly name, the first script assembly is named CustOrders_Script1.dll.</span></span>|  
|<span data-ttu-id="17ab0-145">`/settings:` `document+-, script+-, DTD+-,`</span><span class="sxs-lookup"><span data-stu-id="17ab0-145">`/settings:` `document+-, script+-, DTD+-,`</span></span>|<span data-ttu-id="17ab0-146">`document()`Stil sayfasında işlevlere, XSLT betiğine veya belge türü tanımına (DTD) izin verilip verilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="17ab0-146">Specifies whether to allow `document()` functions, XSLT script, or document type definition (DTD) in the style sheet.</span></span><br /><br /> <span data-ttu-id="17ab0-147">Varsayılan davranış DTD, `document()` işlev ve komut dosyası desteğini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="17ab0-147">The default behavior disables support for DTD, the `document()` function and scripting.</span></span>|  
|<span data-ttu-id="17ab0-148">`@` `file`</span><span class="sxs-lookup"><span data-stu-id="17ab0-148">`@` `file`</span></span>|<span data-ttu-id="17ab0-149">Derleyici seçeneklerini içeren bir dosya belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="17ab0-149">Lets you specify a file that contains the compiler options.</span></span>|  
|`?`|<span data-ttu-id="17ab0-150">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="17ab0-150">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17ab0-151">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="17ab0-151">Remarks</span></span>  
 <span data-ttu-id="17ab0-152">XSLT çözümleri, birden çok stil sayfası modülünden oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="17ab0-152">XSLT solutions can consist of multiple style sheet modules.</span></span> <span data-ttu-id="17ab0-153">xsltc.exe Aracı, stil sayfalarından derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="17ab0-153">The xsltc.exe tool generates assemblies from style sheets.</span></span> <span data-ttu-id="17ab0-154">Daha sonra derlemeler <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> yöntemine geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="17ab0-154">The assemblies can then be passed into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="17ab0-155">Bu, bazı XSLT dağıtım senaryolarında performans maliyetlerinin azaltılmasına yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="17ab0-155">This can help decrease performance costs in some XSLT deployment scenarios.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="17ab0-156">Derlenen derlemeyi uygulamanıza başvuru olarak da dahil etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="17ab0-156">You must also include the compiled assembly as a reference in your application.</span></span>  
  
 <span data-ttu-id="17ab0-157">xsltc.exe Aracı, Sınıf ( `/class:` *ad*) veya derleme ( `/out:` *AssemblyName*) adlarını doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="17ab0-157">The xsltc.exe tool does not validate the class (`/class:`*name*) or assembly (`/out:`*assemblyName*) names.</span></span> <span data-ttu-id="17ab0-158">Adlar geçerli değilse, ortak dil çalışma zamanı tarafından hatalar oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="17ab0-158">Errors are thrown by the common language runtime if the names are not valid.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="17ab0-159">Örnekler</span><span class="sxs-lookup"><span data-stu-id="17ab0-159">Examples</span></span>  
 <span data-ttu-id="17ab0-160">Aşağıdaki komut, stil sayfasını derler ve booksort.dll adlı bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="17ab0-160">The following command compiles the style sheet and creates an assembly named booksort.dll.</span></span>  
  
```console  
xsltc booksort.xsl  
```  
  
 <span data-ttu-id="17ab0-161">Aşağıdaki komut stil sayfasını derler ve sırasıyla booksort.dll ve booksort. pdb adlı bir derleme ve PDB dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="17ab0-161">The following command compiles the style sheet and creates an assembly and PDB file that are named booksort.dll and booksort.pdb respectively.</span></span>  
  
```console  
xsltc booksort.xsl /debug  
```  
  
 <span data-ttu-id="17ab0-162">Aşağıdaki komut bir msxsl: script öğesi içeren bir stil sayfasını derler ve calc.dll ve calc_Script1.dll adlı iki derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="17ab0-162">The following command compiles a style sheet that contains an msxsl:script element and creates two assemblies named calc.dll and calc_Script1.dll.</span></span>  
  
```console  
xsltc /settings:script+ calc.xsl  
```  
  
 <span data-ttu-id="17ab0-163">Aşağıdaki komut DTD işleme ve betik desteğini sunar ve myTest.dll ve myTest_Script1.dll adlı iki derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="17ab0-163">The following command enables DTD processing and script support and creates two assemblies named myTest.dll and myTest_Script1.dll.</span></span>  
  
```console  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 <span data-ttu-id="17ab0-164">Aşağıdaki komut iki stil sayfası modülünü derler ve booksort.dll adlı tek bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="17ab0-164">The following command compiles two style sheet modules and creates a single assembly named booksort.dll.</span></span>  
  
```console  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a><span data-ttu-id="17ab0-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17ab0-165">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="17ab0-166">Nasıl yapılır: Derleme Kullanarak XSLT Dönüşümü Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="17ab0-166">How to: Perform an XSLT Transformation by Using an Assembly</span></span>](how-to-perform-an-xslt-transformation-by-using-an-assembly.md)
- [<span data-ttu-id="17ab0-167">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="17ab0-167">XSLT Transformations</span></span>](xslt-transformations.md)
