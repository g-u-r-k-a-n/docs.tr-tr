---
title: Ilasm.exe (IL Derleyici)
description: Il assembler Ilasm.exe kullanmaya başlayın. Bu araç, ara dil (IL) derlemesinden taşınabilir bir çalıştırılabilir (PE) dosyası oluşturur.
ms.date: 03/30/2017
helpviewer_keywords:
- MSIL generators
- metadata, MSIL Assembler
- MSIL Assembler
- portable executable files, MSIL Assembler
- PE files, MSIL Assembler
- MSIL
- Ilasm.exe
- verifying MSIL performance
ms.assetid: 4ca3a4f0-4400-47ce-8936-8e219961c76f
ms.openlocfilehash: 50dbb0688a75d8588cb6d8679410a4a07abc6b50
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100584266"
---
# <a name="ilasmexe-il-assembler"></a><span data-ttu-id="9e8cf-104">Ilasm.exe (IL Derleyici)</span><span class="sxs-lookup"><span data-stu-id="9e8cf-104">Ilasm.exe (IL Assembler)</span></span>

<span data-ttu-id="9e8cf-105">Il Assembler, ara dil (IL) derlemesinden taşınabilir bir çalıştırılabilir (PE) dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-105">The IL Assembler generates a portable executable (PE) file from intermediate language (IL) assembly.</span></span> <span data-ttu-id="9e8cf-106">(Il hakkında daha fazla bilgi için bkz. [yönetilen yürütme işlemi](../../standard/managed-execution-process.md).) Il 'nin beklenen şekilde yapılıp yapılmayacağını anlamak için Il ve gerekli meta verileri içeren elde edilen yürütülebilir dosyayı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-106">(For more information on IL, see [Managed Execution Process](../../standard/managed-execution-process.md).) You can run the resulting executable, which contains IL and the required metadata, to determine whether the IL performs as expected.</span></span>

<span data-ttu-id="9e8cf-107">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="9e8cf-108">Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-108">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="9e8cf-109">Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="9e8cf-109">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="9e8cf-110">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="9e8cf-110">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="9e8cf-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9e8cf-111">Syntax</span></span>

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a><span data-ttu-id="9e8cf-112">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9e8cf-112">Parameters</span></span>

| <span data-ttu-id="9e8cf-113">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="9e8cf-113">Argument</span></span> | <span data-ttu-id="9e8cf-114">Description</span><span class="sxs-lookup"><span data-stu-id="9e8cf-114">Description</span></span> |
| -------- | ----------- |
|`filename`|<span data-ttu-id="9e8cf-115">.il kaynak dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-115">The name of the .il source file.</span></span> <span data-ttu-id="9e8cf-116">Bu dosya meta veri bildirim yönergeleri ve simgesel IL yönergelerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-116">This file consists of metadata declaration directives and symbolic IL instructions.</span></span> <span data-ttu-id="9e8cf-117">*Ilasm.exe* ile tek bir PE dosyası oluşturmak için birden çok kaynak dosya bağımsız değişkeni sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-117">Multiple source file arguments can be supplied to produce a single PE file with *Ilasm.exe*.</span></span> <span data-ttu-id="9e8cf-118">**Note:** . Il kaynak dosyasındaki son kod satırının sonunda boşluk veya satır sonu karakteri bulunduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-118">**Note:** Ensure that the last line of code in the .il source file has either trailing white space or an end-of-line character.</span></span>|

| <span data-ttu-id="9e8cf-119">Seçenek</span><span class="sxs-lookup"><span data-stu-id="9e8cf-119">Option</span></span> | <span data-ttu-id="9e8cf-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e8cf-120">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="9e8cf-121">**/32bittercihli**</span><span class="sxs-lookup"><span data-stu-id="9e8cf-121">**/32bitpreferred**</span></span>|<span data-ttu-id="9e8cf-122">32 bit tercih edilen bir görüntü (PE32) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-122">Creates a 32-bit-preferred image (PE32).</span></span>|
|<span data-ttu-id="9e8cf-123">**/hizalaması:**`integer`</span><span class="sxs-lookup"><span data-stu-id="9e8cf-123">**/alignment:** `integer`</span></span>|<span data-ttu-id="9e8cf-124">NT Isteğe bağlı üstbilgisinde dosya hizalamasını belirtilen değere ayarlar `integer` .</span><span class="sxs-lookup"><span data-stu-id="9e8cf-124">Sets FileAlignment to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="9e8cf-125">Eğer .alignment IL yönergesi dosyada belirtiliyorsa, bu seçenek onu geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-125">If the .alignment IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="9e8cf-126">**/APPCONTAINER**</span><span class="sxs-lookup"><span data-stu-id="9e8cf-126">**/appcontainer**</span></span>|<span data-ttu-id="9e8cf-127">Çıkış olarak Windows Uygulama kapsayıcısında çalışan bir *. dll* veya *. exe* dosyası üretir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-127">Produces a *.dll* or *.exe* file that runs in the Windows app container, as output.</span></span>|
|<span data-ttu-id="9e8cf-128">**/ARM**</span><span class="sxs-lookup"><span data-stu-id="9e8cf-128">**/arm**</span></span>|<span data-ttu-id="9e8cf-129">Hedef işlemci olarak Gelişmiş RISC Makinesi (ARM) belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-129">Specifies the Advanced RISC Machine (ARM) as the target processor.</span></span><br /><br /> <span data-ttu-id="9e8cf-130">Hiçbir görüntü bit durumu belirtilmemişse, varsayılan olarak **/32bittercih** edilir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-130">If no image bitness is specified, the default is **/32bitpreferred**.</span></span>|
|<span data-ttu-id="9e8cf-131">**/Base:**`integer`</span><span class="sxs-lookup"><span data-stu-id="9e8cf-131">**/base:** `integer`</span></span>|<span data-ttu-id="9e8cf-132">ImageBase 'i `integer` NT Isteğe bağlı üst bilgisinde belirtilen değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-132">Sets ImageBase to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="9e8cf-133">Eğer .imagebase IL yönergesi dosyada belirtiliyorsa, bu seçenek onu geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-133">If the .imagebase IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="9e8cf-134">**/Saat**</span><span class="sxs-lookup"><span data-stu-id="9e8cf-134">**/clock**</span></span>|<span data-ttu-id="9e8cf-135">Belirtilen .il kaynak dosyası için aşağıdaki derleme sürelerini milisaniye cinsinden ölçer ve raporlar:</span><span class="sxs-lookup"><span data-stu-id="9e8cf-135">Measures and reports the following compilation times in milliseconds for the specified .il source file:</span></span><br /><br /> <span data-ttu-id="9e8cf-136">**Toplam çalıştırma**: izleyen tüm belirli işlemleri gerçekleştirmek için harcanan toplam süre.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-136">**Total Run**: The total time spent performing all the specific operations that follow.</span></span><br /><br /> <span data-ttu-id="9e8cf-137">**Başlangıç**: dosyayı yükleme ve açma.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-137">**Startup**: Loading and opening the file.</span></span><br /><br /> <span data-ttu-id="9e8cf-138">**Md 'Yi yayma**: meta verileri yayma.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-138">**Emitting MD**: Emitting metadata.</span></span><br /><br /> <span data-ttu-id="9e8cf-139">**Ref-def çözümleme**: dosyadaki tanımlara başvuruları çözümleme.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-139">**Ref to Def Resolution**: Resolving references to definitions in the file.</span></span><br /><br /> <span data-ttu-id="9e8cf-140">**Cee dosyası oluşturma**: bellekte dosya görüntüsü oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-140">**CEE File Generation**: Generating the file image in memory.</span></span><br /><br /> <span data-ttu-id="9e8cf-141">**PE dosyası yazma**: görüntüyü bir pe dosyasına yazma.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-141">**PE File Writing**: Writing the image to a PE file.</span></span>|
|<span data-ttu-id="9e8cf-142">**/Debug**[:**Impl**&#124;**opt**]</span><span class="sxs-lookup"><span data-stu-id="9e8cf-142">**/debug**[:**IMPL**&#124;**OPT**]</span></span>|<span data-ttu-id="9e8cf-143">Hata ayıklama bilgisi içerir (yerel değişken ve bağımsız değişken adları ve satır numaraları).</span><span class="sxs-lookup"><span data-stu-id="9e8cf-143">Includes debug information (local variable and argument names, and line numbers).</span></span> <span data-ttu-id="9e8cf-144">Bir PDB dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-144">Creates a PDB file.</span></span><br /><br /> <span data-ttu-id="9e8cf-145">ek değer içermeyen **/Debug** JIT iyileştirmesini devre dışı bırakır ve pdb dosyasından sıra noktalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-145">**/debug** with no additional value disables JIT optimization and uses sequence points from the PDB file.</span></span><br /><br /> <span data-ttu-id="9e8cf-146">**IMPL** JIT iyileştirmesini devre dışı bırakır ve örtük sıra noktaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-146">**IMPL** disables JIT optimization and uses implicit sequence points.</span></span><br /><br /> <span data-ttu-id="9e8cf-147">**Opt** için JIT İyileştirmesi etkinleştirilir ve örtülü sıra noktalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-147">**OPT** enables JIT optimization and uses implicit sequence points.</span></span>|
|<span data-ttu-id="9e8cf-148">**/dll**</span><span class="sxs-lookup"><span data-stu-id="9e8cf-148">**/dll**</span></span>|<span data-ttu-id="9e8cf-149">Çıktı olarak bir *. dll* dosyası üretir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-149">Produces a *.dll* file as output.</span></span>|
|<span data-ttu-id="9e8cf-150">**/enc:**`file`</span><span class="sxs-lookup"><span data-stu-id="9e8cf-150">**/enc:** `file`</span></span>|<span data-ttu-id="9e8cf-151">Belirtilen kaynak dosyasından Düzenle ve Devam Et deltaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-151">Creates Edit-and-Continue deltas from the specified source file.</span></span><br /><br /> <span data-ttu-id="9e8cf-152">Bu bağımsız değişken yalnızca akademik amaçlıdır ve ticari kullanım için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-152">This argument is for academic use only and is not supported for commercial use.</span></span>|
|<span data-ttu-id="9e8cf-153">**/exe**</span><span class="sxs-lookup"><span data-stu-id="9e8cf-153">**/exe**</span></span>|<span data-ttu-id="9e8cf-154">Çıktı olarak bir yürütülebilir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-154">Produces an executable file as output.</span></span> <span data-ttu-id="9e8cf-155">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-155">This is the default.</span></span>|
|<span data-ttu-id="9e8cf-156">**/Flags:**`integer`</span><span class="sxs-lookup"><span data-stu-id="9e8cf-156">**/flags:** `integer`</span></span>|<span data-ttu-id="9e8cf-157">ImageFlags öğesini `integer` ortak dil çalışma zamanı üst bilgisinde belirtilen değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-157">Sets ImageFlags to the value specified by `integer` in the common language runtime header.</span></span> <span data-ttu-id="9e8cf-158">Eğer .corflags IL yönergesi dosyada belirtiliyorsa, bu seçenek onu geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-158">If the .corflags IL directive is specified in the file, this option overrides it.</span></span> <span data-ttu-id="9e8cf-159">*Tamsayı* için geçerli değerler listesi için bkz. CorHdr. h, COMIMAGE_FLAGS.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-159">See CorHdr.h, COMIMAGE_FLAGS for a list of valid values for *integer*.</span></span>|
|<span data-ttu-id="9e8cf-160">**/Katlama**</span><span class="sxs-lookup"><span data-stu-id="9e8cf-160">**/fold**</span></span>|<span data-ttu-id="9e8cf-161">Eşdeğer metot gövdelerini tek bir gövde olarak katlar.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-161">Folds identical method bodies into one.</span></span>|
|<span data-ttu-id="9e8cf-162">/**highentropyva**</span><span class="sxs-lookup"><span data-stu-id="9e8cf-162">/**highentropyva**</span></span>|<span data-ttu-id="9e8cf-163">Yüksek entropili adres alanı düzenini (ASLR) destekleyen bir çıktı çalıştırılabilir dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-163">Produces an output executable that supports high-entropy address space layout randomization (ASLR).</span></span> <span data-ttu-id="9e8cf-164">( **/APPCONTAINER** için varsayılan.)</span><span class="sxs-lookup"><span data-stu-id="9e8cf-164">(Default for **/appcontainer**.)</span></span>|
|<span data-ttu-id="9e8cf-165">**/include:**`includePath`</span><span class="sxs-lookup"><span data-stu-id="9e8cf-165">**/include:** `includePath`</span></span>|<span data-ttu-id="9e8cf-166">İçinde yer alan dosyaları aramak için bir yol belirler `#include` .</span><span class="sxs-lookup"><span data-stu-id="9e8cf-166">Sets a path to search for files included with `#include`.</span></span>|
|<span data-ttu-id="9e8cf-167">**/Itanium**</span><span class="sxs-lookup"><span data-stu-id="9e8cf-167">**/itanium**</span></span>|<span data-ttu-id="9e8cf-168">Hedef işlemci olarak Intel Itanium belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-168">Specifies Intel Itanium as the target processor.</span></span><br /><br /> <span data-ttu-id="9e8cf-169">Hiçbir görüntü bit durumu belirtilmemişse, varsayılan değer **/pe64**' dir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-169">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="9e8cf-170">**/Key:**`keyFile`</span><span class="sxs-lookup"><span data-stu-id="9e8cf-170">**/key:** `keyFile`</span></span>|<span data-ttu-id="9e8cf-171">`filename`, İçinde bulunan özel anahtarı kullanarak güçlü bir imzayla derlenir `keyFile` .</span><span class="sxs-lookup"><span data-stu-id="9e8cf-171">Compiles `filename` with a strong signature using the private key contained in `keyFile`.</span></span>|
|<span data-ttu-id="9e8cf-172">**/Key** @`keySource`</span><span class="sxs-lookup"><span data-stu-id="9e8cf-172">**/key:** @`keySource`</span></span>|<span data-ttu-id="9e8cf-173">`filename`Öğesinde oluşturulan özel anahtarı kullanarak güçlü bir imzayla derlenir `keySource` .</span><span class="sxs-lookup"><span data-stu-id="9e8cf-173">Compiles `filename` with a strong signature using the private key produced at `keySource`.</span></span>|
|<span data-ttu-id="9e8cf-174">**/listeleme**</span><span class="sxs-lookup"><span data-stu-id="9e8cf-174">**/listing**</span></span>|<span data-ttu-id="9e8cf-175">Standart çıktıda bir listeleme dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-175">Produces a listing file on the standard output.</span></span> <span data-ttu-id="9e8cf-176">Eğer bu seçeneği koymazsanız, listeleme dosyası oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-176">If you omit this option, no listing file is produced.</span></span><br /><br /> <span data-ttu-id="9e8cf-177">Bu parametre .NET Framework 2.0 ve sonrasında desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-177">This parameter is not supported in the .NET Framework 2.0 or later.</span></span>|
|<span data-ttu-id="9e8cf-178">**/MDV:**`versionString`</span><span class="sxs-lookup"><span data-stu-id="9e8cf-178">**/mdv:** `versionString`</span></span>|<span data-ttu-id="9e8cf-179">Meta veri sürümü dizesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-179">Sets the metadata version string.</span></span>|
|<span data-ttu-id="9e8cf-180">**/MSV:** `major` .`minor`</span><span class="sxs-lookup"><span data-stu-id="9e8cf-180">**/msv:** `major`.`minor`</span></span>|<span data-ttu-id="9e8cf-181">Meta veri akışı sürümünü, burada `major` ve tamsayılar olarak ayarlar `minor` .</span><span class="sxs-lookup"><span data-stu-id="9e8cf-181">Sets the metadata stream version, where `major` and `minor` are integers.</span></span>|
|<span data-ttu-id="9e8cf-182">**/nooto Inherit**</span><span class="sxs-lookup"><span data-stu-id="9e8cf-182">**/noautoinherit**</span></span>|<span data-ttu-id="9e8cf-183">Hiçbir temel sınıf belirtilmediğinde varsayılan devralmayı devre dışı bırakır <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="9e8cf-183">Disables default inheritance from <xref:System.Object> when no base class is specified.</span></span>|
|<span data-ttu-id="9e8cf-184">**/nocorstub**</span><span class="sxs-lookup"><span data-stu-id="9e8cf-184">**/nocorstub**</span></span>|<span data-ttu-id="9e8cf-185">CORExeMain taslağının oluşturulmasını bastırır.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-185">Suppresses generation of the CORExeMain stub.</span></span>|
|<span data-ttu-id="9e8cf-186">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="9e8cf-186">**/nologo**</span></span>|<span data-ttu-id="9e8cf-187">Microsoft başlangıç başlığı görüntüsünü bastırır.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-187">Suppresses the Microsoft startup banner display.</span></span>|
|<span data-ttu-id="9e8cf-188">**/output:**`file.ext`</span><span class="sxs-lookup"><span data-stu-id="9e8cf-188">**/output:** `file.ext`</span></span>|<span data-ttu-id="9e8cf-189">Çıktı dosyası adını ve uzantısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-189">Specifies the output file name and extension.</span></span> <span data-ttu-id="9e8cf-190">Varsayılan olarak, çıktı dosyası adı ilk kaynak dosyasının adıyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-190">By default, the output file name is the same as the name of the first source file.</span></span> <span data-ttu-id="9e8cf-191">Varsayılan uzantı *. exe*' dir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-191">The default extension is *.exe*.</span></span> <span data-ttu-id="9e8cf-192">**/DLL** seçeneğini belirtirseniz, varsayılan uzantı *. dll*' dir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-192">If you specify the **/dll** option, the default extension is *.dll*.</span></span> <span data-ttu-id="9e8cf-193">**Note:** **/Output**:myfile.dll belirtildiğinde **/DLL** seçeneği ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-193">**Note:** Specifying **/output**:myfile.dll does not set the **/dll** option.</span></span> <span data-ttu-id="9e8cf-194">**/DLL** belirtmezseniz, sonuç *myfile.dll* adlı yürütülebilir bir dosya olur.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-194">If you do not specify **/dll**, the result will be an executable file named *myfile.dll*.</span></span>|
|<span data-ttu-id="9e8cf-195">**/optimize**</span><span class="sxs-lookup"><span data-stu-id="9e8cf-195">**/optimize**</span></span>|<span data-ttu-id="9e8cf-196">Uzun yönergeleri kısa olarak iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-196">Optimizes long instructions to short.</span></span> <span data-ttu-id="9e8cf-197">Örneğin, `br` `br.s` .</span><span class="sxs-lookup"><span data-stu-id="9e8cf-197">For example, `br` to `br.s`.</span></span>|
|<span data-ttu-id="9e8cf-198">**/pe64**</span><span class="sxs-lookup"><span data-stu-id="9e8cf-198">**/pe64**</span></span>|<span data-ttu-id="9e8cf-199">64 bitlik bir görüntü oluşturur (PE32+).</span><span class="sxs-lookup"><span data-stu-id="9e8cf-199">Creates a 64-bit image (PE32+).</span></span><br /><br /> <span data-ttu-id="9e8cf-200">Hedef işlemci belirtilmemişse, varsayılan olur `/itanium` .</span><span class="sxs-lookup"><span data-stu-id="9e8cf-200">If no target processor is specified, the default is `/itanium`.</span></span>|
|<span data-ttu-id="9e8cf-201">**/pdb**</span><span class="sxs-lookup"><span data-stu-id="9e8cf-201">**/pdb**</span></span>|<span data-ttu-id="9e8cf-202">Hata ayıklama bilgisi izlemeyi etkinleştirmeden bir PDB dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-202">Creates a PDB file without enabling debug information tracking.</span></span>|
|<span data-ttu-id="9e8cf-203">**/**</span><span class="sxs-lookup"><span data-stu-id="9e8cf-203">**/quiet**</span></span>|<span data-ttu-id="9e8cf-204">Sessiz modu belirtir; hiçbir derleme ilerlemesini bildirmez.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-204">Specifies quiet mode; does not report assembly progress.</span></span>|
|<span data-ttu-id="9e8cf-205">**/Kaynak:**`file.res`</span><span class="sxs-lookup"><span data-stu-id="9e8cf-205">**/resource:** `file.res`</span></span>|<span data-ttu-id="9e8cf-206">\*Elde edilen *. exe* veya *. dll* dosyasında belirtilen kaynak dosyasını. res biçiminde içerir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-206">Includes the specified resource file in \*.res format in the resulting *.exe* or *.dll* file.</span></span> <span data-ttu-id="9e8cf-207">**/Resource** seçeneğiyle yalnızca bir. res dosyası belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-207">Only one .res file can be specified with the **/resource** option.</span></span>|
|<span data-ttu-id="9e8cf-208">**/ssver:** `int` .`int`</span><span class="sxs-lookup"><span data-stu-id="9e8cf-208">**/ssver:** `int`.`int`</span></span>|<span data-ttu-id="9e8cf-209">NT isteğe bağlı üst bilgisinde alt sistem sürümünü ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-209">Sets the subsystem version number in the NT optional header.</span></span> <span data-ttu-id="9e8cf-210">**/APPCONTAINER** ve **/ARM** için en düşük sürüm numarası 6,02 ' dir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-210">For **/appcontainer** and **/arm** the minimum version number is 6.02.</span></span>|
|<span data-ttu-id="9e8cf-211">**/Stack:**`stackSize`</span><span class="sxs-lookup"><span data-stu-id="9e8cf-211">**/stack:** `stackSize`</span></span>|<span data-ttu-id="9e8cf-212">NT Isteğe bağlı üst bilgisindeki SizeOfStackReserve değerini olarak ayarlar `stackSize` .</span><span class="sxs-lookup"><span data-stu-id="9e8cf-212">Sets the SizeOfStackReserve value in the NT Optional header to `stackSize`.</span></span>|
|<span data-ttu-id="9e8cf-213">**/çabapreloc**</span><span class="sxs-lookup"><span data-stu-id="9e8cf-213">**/stripreloc**</span></span>|<span data-ttu-id="9e8cf-214">Temel yeniden konumlandırmanın gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-214">Specifies that no base relocations are needed.</span></span>|
|<span data-ttu-id="9e8cf-215">**/Subsystem:**`integer`</span><span class="sxs-lookup"><span data-stu-id="9e8cf-215">**/subsystem:** `integer`</span></span>|<span data-ttu-id="9e8cf-216">Alt sistemi `integer` , NT Isteğe bağlı üst bilgisinde tarafından belirtilen değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-216">Sets subsystem to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="9e8cf-217">Eğer .subsystem IL yönergesi dosyada belirtiliyorsa, bu komut onu geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-217">If the .subsystem IL directive is specified in the file, this command overrides it.</span></span> <span data-ttu-id="9e8cf-218">İçin geçerli değerler listesi için bkz. Winnt. h, IMAGE_SUBSYSTEM `integer` .</span><span class="sxs-lookup"><span data-stu-id="9e8cf-218">See winnt.h, IMAGE_SUBSYSTEM for a list of valid values for `integer`.</span></span>|
|<span data-ttu-id="9e8cf-219">**/x64**</span><span class="sxs-lookup"><span data-stu-id="9e8cf-219">**/x64**</span></span>|<span data-ttu-id="9e8cf-220">Hedef işlemci olarak bir 64 bitlik AMD işlemci belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-220">Specifies a 64-bit AMD processor as the target processor.</span></span><br /><br /> <span data-ttu-id="9e8cf-221">Hiçbir görüntü bit durumu belirtilmemişse, varsayılan değer **/pe64**' dir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-221">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="9e8cf-222">**/?**</span><span class="sxs-lookup"><span data-stu-id="9e8cf-222">**/?**</span></span>|<span data-ttu-id="9e8cf-223">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-223">Displays command syntax and options for the tool.</span></span>|

> [!NOTE]
> <span data-ttu-id="9e8cf-224">Tüm *Ilasm.exe* seçenekleri büyük/küçük harfe duyarlıdır ve ilk üç harf tarafından tanınır.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-224">All options for *Ilasm.exe* are case-insensitive and recognized by the first three letters.</span></span> <span data-ttu-id="9e8cf-225">Örneğin, **/Lis** , **/Listeleme** ve **/res**: myresfile. res ile eşdeğerdir. res, **/Resource**: myresfile. res ile eşdeğerdir. Bağımsız değişkenleri belirten seçenekler iki nokta işaretini kabul eder (:) ya da bir eşittir işareti (=), seçeneği ve bağımsız değişkeni arasında ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-225">For example, **/lis** is equivalent to **/listing** and **/res**:myresfile.res is equivalent to **/resource**:myresfile.res. Options that specify arguments accept either a colon (:) or an equal sign (=) as the separator between the option and the argument.</span></span> <span data-ttu-id="9e8cf-226">Örneğin, **/output**:*File. ext* , **/output** = *File. ext* ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-226">For example, **/output**:*file.ext* is equivalent to **/output**=*file.ext*.</span></span>

## <a name="remarks"></a><span data-ttu-id="9e8cf-227">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e8cf-227">Remarks</span></span>

<span data-ttu-id="9e8cf-228">IL Derleyicisi araç satıcılarına IL oluşturucuları tasarlamaları ve uygulamaları için yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-228">The IL Assembler helps tool vendors design and implement IL generators.</span></span> <span data-ttu-id="9e8cf-229">*Ilasm.exe*, araç ve derleyici GELIŞTIRICILERI, PE dosya biçiminde Il yayılmasından ENDIŞE duymadan Il ve meta veri oluşturmaya odaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-229">Using *Ilasm.exe*, tool and compiler developers can concentrate on IL and metadata generation without being concerned with emitting IL in the PE file format.</span></span>

<span data-ttu-id="9e8cf-230">C# ve Visual Basic gibi çalışma zamanını hedefleyen diğer derleyicilere benzer şekilde, *Ilasm.exe* ara nesne dosyalarını oluşturmaz ve bir PE dosyası oluşturmak için bağlama aşamasına gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-230">Similar to other compilers that target the runtime, such as C# and Visual Basic, *Ilasm.exe* does not produce intermediate object files and does not require a linking stage to form a PE file.</span></span>

<span data-ttu-id="9e8cf-231">IL Derleyicisi, çalışma zamanını hedef alan programlama dillerinin tüm varolan meta veri ve IL özelliklerini ifade edebilir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-231">The IL Assembler can express all the existing metadata and IL features of the programming languages that target the runtime.</span></span> <span data-ttu-id="9e8cf-232">Bu, bu programlama dillerinde yazılan yönetilen kodun Il derleyiciden yeterince ifade edilmesi ve *Ilasm.exe* ile derlenmesi için izin verir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-232">This allows managed code written in any of these programming languages to be adequately expressed in IL Assembler and compiled with *Ilasm.exe*.</span></span>

> [!NOTE]
> <span data-ttu-id="9e8cf-233">Eğer .il kaynak dosyasının son kod satırında bir boşluk veya satır sonu karakteri yoksa derleme başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-233">Compilation might fail if the last line of code in the .il source file does not have either trailing white space or an end-of-line character.</span></span>

<span data-ttu-id="9e8cf-234">[*Ildasm.exe*](ildasm-exe-il-disassembler.md)yardımcı aracı ile birlikte *Ilasm.exe* kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-234">You can use *Ilasm.exe* in conjunction with its companion tool, [*Ildasm.exe*](ildasm-exe-il-disassembler.md).</span></span> <span data-ttu-id="9e8cf-235">*Ildasm.exe* IL kodu IÇEREN bir PE dosyasını alır ve *Ilasm.exe* giriş olarak uygun bir metin dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-235">*Ildasm.exe* takes a PE file that contains IL code and creates a text file suitable as input to *Ilasm.exe*.</span></span> <span data-ttu-id="9e8cf-236">Bu örneğin, tüm çalışma zamanı meta veri özniteliklerini desteklemeyen bir programlama dilinde kod derlerken kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-236">This is useful, for example, when compiling code in a programming language that does not support all the runtime metadata attributes.</span></span> <span data-ttu-id="9e8cf-237">Kodu derleyip ve çıktıyı *Ildasm.exe* aracılığıyla çalıştırdıktan sonra, elde edilen Il metin dosyası, eksik öznitelikleri eklemek için el ile düzenlenebilir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-237">After compiling the code and running the output through *Ildasm.exe*, the resulting IL text file can be hand-edited to add the missing attributes.</span></span> <span data-ttu-id="9e8cf-238">Ardından, son yürütülebilir bir dosya oluşturmak için bu metin dosyasını *Ilasm.exe* aracılığıyla çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-238">You can then run this text file through the *Ilasm.exe* to produce a final executable file.</span></span>

<span data-ttu-id="9e8cf-239">Bu tekniği kullanarak ayrı derleyiciler tarafından üretilen çeşitli PE dosyalarından tek bir PE dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-239">You can also use this technique to produce a single PE file from several PE files originally generated by different compilers.</span></span>

> [!NOTE]
> <span data-ttu-id="9e8cf-240">Şu anda, bu tekniği gömülü yerel kod içeren (örneğin, Visual C++ tarafından üretilen PE dosyaları) PE dosyaları ile kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-240">Currently, you cannot use this technique with PE files that contain embedded native code (for example, PE files produced by Visual C++).</span></span>

<span data-ttu-id="9e8cf-241">Bu *Ildasm.exe* ve *Ilasm.exe* mümkün olduğunca doğru şekilde kullanmasını sağlamak için, varsayılan olarak Assembler, Il kaynaklarınıza yazmış olabileceğiniz (veya başka bir derleyici tarafından yayılan) uzun sürelerle ilgili kısa kodlamalar yerine getirir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-241">To make this combined use of *Ildasm.exe* and *Ilasm.exe* as accurate as possible, by default the assembler does not substitute short encodings for long ones you might have written in your IL sources (or that might be emitted by another compiler).</span></span> <span data-ttu-id="9e8cf-242">Mümkün olan yerlerde kısa kodlamaları yerine koymak için **/optimize** et seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-242">Use the **/optimize** option to substitute short encodings wherever possible.</span></span>

> [!NOTE]
> <span data-ttu-id="9e8cf-243">*Ildasm.exe* yalnızca diskteki dosyalar üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-243">*Ildasm.exe* only operates on files on disk.</span></span> <span data-ttu-id="9e8cf-244">Genel bütünleştirilmiş kod önbelleğine yüklü olan dosyalar üzerinde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-244">It does not operate on files installed in the global assembly cache.</span></span>

<span data-ttu-id="9e8cf-245">Il 'nin dilbilgisini hakkında daha fazla bilgi için, Windows SDK The asmpari. Grammar dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-245">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="version-information"></a><span data-ttu-id="9e8cf-246">Sürüm Bilgileri</span><span class="sxs-lookup"><span data-stu-id="9e8cf-246">Version Information</span></span>

<span data-ttu-id="9e8cf-247">4,5 .NET Framework başlayarak, aşağıdakine benzer bir kod kullanarak bir arabirim uygulamasına özel bir öznitelik ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9e8cf-247">Starting with the .NET Framework 4.5, you can attach a custom attribute to an interface implementation by using code similar to the following:</span></span>

```il
.class interface public abstract auto ansi IMyInterface
{
  .method public hidebysig newslot abstract virtual
    instance int32 method1() cil managed
  {
  } // end of method IMyInterface::method1
} // end of class IMyInterface
.class public auto ansi beforefieldinit MyClass
  extends [mscorlib]System.Object
  implements IMyInterface
  {
    .interfaceimpl type IMyInterface
    .custom instance void
      [mscorlib]System.Diagnostics.DebuggerNonUserCodeAttribute::.ctor() = ( 01 00 00 00 )
      …
```

<span data-ttu-id="9e8cf-248">4,5 .NET Framework başlayarak, aşağıdaki kodda gösterildiği gibi, ham ikili gösterimini kullanarak rastgele bir sıralama Blobu (ikili büyük nesne) belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9e8cf-248">Starting with the .NET Framework 4.5, you can specify an arbitrary marshal BLOB (binary large object) by using its raw binary representation, as shown in the following code:</span></span>

```il
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

<span data-ttu-id="9e8cf-249">Il 'nin dilbilgisini hakkında daha fazla bilgi için, Windows SDK The asmpari. Grammar dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-249">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="9e8cf-250">Örnekler</span><span class="sxs-lookup"><span data-stu-id="9e8cf-250">Examples</span></span>

<span data-ttu-id="9e8cf-251">Aşağıdaki komut, *MYTESTFILE.Il* Il dosyasını ayrıştırır ve çalıştırılabilir *myTestFile.exe* üretir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-251">The following command assembles the IL file *myTestFile.il* and produces the executable *myTestFile.exe*.</span></span>

```console
ilasm myTestFile
```

<span data-ttu-id="9e8cf-252">Aşağıdaki komut, *MYTESTFILE.Il* Il dosyasını ayrıştırır ve *. dll* dosyasını *myTestFile.dll* üretir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-252">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll
```

<span data-ttu-id="9e8cf-253">Aşağıdaki komut, *MYTESTFILE.Il* Il dosyasını ayrıştırır ve *. dll* dosyasını *myNewTestFile.dll* üretir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-253">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myNewTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

<span data-ttu-id="9e8cf-254">Aşağıdaki kod örneğinde, "Merhaba Dünya!" görüntüleyen son derece basit bir uygulama gösterilmektedir</span><span class="sxs-lookup"><span data-stu-id="9e8cf-254">The following code example shows an extremely simple application that displays "Hello World!"</span></span> <span data-ttu-id="9e8cf-255">metnini görüntülemelidir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-255">to the console.</span></span> <span data-ttu-id="9e8cf-256">Bu kodu derleyebilir ve ardından [*Ildasm.exe*](ildasm-exe-il-disassembler.md) ARACıNı kullanarak Il dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-256">You can compile this code and then use the [*Ildasm.exe*](ildasm-exe-il-disassembler.md) tool to generate an IL file.</span></span>

```csharp
using System;

public class Hello
{
    public static void Main(String[] args)
    {
        Console.WriteLine("Hello World!");
    }
}
```

<span data-ttu-id="9e8cf-257">Aşağıdaki IL kod örneği önceki C# kod örneğine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-257">The following IL code example corresponds to the previous C# code example.</span></span> <span data-ttu-id="9e8cf-258">Bu kodu Il assembler aracını kullanarak bir derlemede derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-258">You can compile this code into an assembly using the IL Assembler tool.</span></span> <span data-ttu-id="9e8cf-259">Hem Il hem de C# kod örnekleri "Merhaba Dünya!" görüntüler</span><span class="sxs-lookup"><span data-stu-id="9e8cf-259">Both IL and C# code examples display "Hello World!"</span></span> <span data-ttu-id="9e8cf-260">metnini görüntülemelidir.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-260">to the console.</span></span>

```il
// Metadata version: v2.0.50215
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 2:0:0:0
}
.assembly sample
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module sample.exe
// MVID: {A224F460-A049-4A03-9E71-80A36DBBBCD3}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x02F20000

// =============== CLASS MEMBERS DECLARATION ===================

.class public auto ansi beforefieldinit Hello
       extends [mscorlib]System.Object
{
  .method public hidebysig static void  Main(string[] args) cil managed
  {
    .entrypoint
    // Code size       13 (0xd)
    .maxstack  8
    IL_0000:  nop
    IL_0001:  ldstr      "Hello World!"
    IL_0006:  call       void [mscorlib]System.Console::WriteLine(string)
    IL_000b:  nop
    IL_000c:  ret
  } // end of method Hello::Main

  .method public hidebysig specialname rtspecialname
          instance void  .ctor() cil managed
  {
    // Code size       7 (0x7)
    .maxstack  8
    IL_0000:  ldarg.0
    IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
    IL_0006:  ret
  } // end of method Hello::.ctor

} // end of class Hello
```

## <a name="see-also"></a><span data-ttu-id="9e8cf-261">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e8cf-261">See also</span></span>

- [<span data-ttu-id="9e8cf-262">Araçlar</span><span class="sxs-lookup"><span data-stu-id="9e8cf-262">Tools</span></span>](index.md)
- [<span data-ttu-id="9e8cf-263">*Ildasm.exe* (Il ayırıcı)</span><span class="sxs-lookup"><span data-stu-id="9e8cf-263">*Ildasm.exe* (IL Disassembler)</span></span>](ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="9e8cf-264">Yönetilen yürütme Işlemi</span><span class="sxs-lookup"><span data-stu-id="9e8cf-264">Managed Execution Process</span></span>](../../standard/managed-execution-process.md)
- [<span data-ttu-id="9e8cf-265">Komut Istemleri</span><span class="sxs-lookup"><span data-stu-id="9e8cf-265">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
