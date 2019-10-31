---
title: Bileşim Analiz Aracı (Mefx)
ms.date: 03/30/2017
helpviewer_keywords:
- Composition Analysis Tool [MEF]
- MEF, Composition Analysis Tool
- Mefx [MEF], Composition Analysis Tool
ms.assetid: c48a7f93-83bb-4a06-aea0-d8e7bd1502ad
ms.openlocfilehash: bb2748b16a16d7d01b076402889829f5b31a1912
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126367"
---
# <a name="composition-analysis-tool-mefx"></a><span data-ttu-id="acf41-102">Bileşim Analiz Aracı (Mefx)</span><span class="sxs-lookup"><span data-stu-id="acf41-102">Composition Analysis Tool (Mefx)</span></span>
<span data-ttu-id="acf41-103">Bileşim çözümleme aracı (Mefx), kitaplık (. dll) ve Managed Extensibility Framework (MEF) parçaları içeren uygulama (. exe) dosyalarını analiz eden bir komut satırı uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="acf41-103">The Composition Analysis Tool (Mefx) is a command-line application that analyzes library (.dll) and application (.exe) files containing Managed Extensibility Framework (MEF) parts.</span></span> <span data-ttu-id="acf41-104">Mefx 'in birincil amacı, geliştiricilere, uygulamanın kendisi için ek bir izleme kodu ekleme gereksinimi olmadan MEF uygulamalarında bileşim başarısızlıklarını tanılamaya yönelik bir yol sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="acf41-104">The primary purpose of Mefx is to provide developers a way to diagnose composition failures in their MEF applications without the requirement to add cumbersome tracing code to the application itself.</span></span> <span data-ttu-id="acf41-105">Üçüncü taraf tarafından sağlanan bir kitaplıktan parçaları anlamanıza yardımcı olmak için de kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="acf41-105">It can also be useful to help understand parts from a library provided by a third party.</span></span> <span data-ttu-id="acf41-106">Bu konu, Mefx 'in nasıl kullanılacağını açıklar ve söz dizimi için bir başvuru sağlar.</span><span class="sxs-lookup"><span data-stu-id="acf41-106">This topic describes how to use Mefx and provides a reference for its syntax.</span></span>  
  
<a name="getting_mefx"></a>   
## <a name="getting-mefx"></a><span data-ttu-id="acf41-107">Mefx alma</span><span class="sxs-lookup"><span data-stu-id="acf41-107">Getting Mefx</span></span>  
 <span data-ttu-id="acf41-108">Mefx, [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0)'de GitHub 'da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="acf41-108">Mefx is available on GitHub at [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span></span> <span data-ttu-id="acf41-109">Aracı indirmeniz ve sıkıştırmayı açmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="acf41-109">Simply download and unzip the tool.</span></span>  
  
<a name="basic_syntax"></a>   
## <a name="basic-syntax"></a><span data-ttu-id="acf41-110">Temel söz dizimi</span><span class="sxs-lookup"><span data-stu-id="acf41-110">Basic Syntax</span></span>  
 <span data-ttu-id="acf41-111">Mefx, komut satırından aşağıdaki biçimde çağrılır:</span><span class="sxs-lookup"><span data-stu-id="acf41-111">Mefx is invoked from the command line in the following format:</span></span>  
  
```console
mefx [files and directories] [action] [options]  
```  
  
 <span data-ttu-id="acf41-112">İlk bağımsız değişken kümesi, analiz için parçaların yükleneceği dosyaları ve dizinleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="acf41-112">The first set of arguments specify the files and directories from which to load parts for analysis.</span></span> <span data-ttu-id="acf41-113">`/file:` anahtarı ile bir dosya ve `/directory:` anahtarı olan bir dizin belirtin.</span><span class="sxs-lookup"><span data-stu-id="acf41-113">Specify a file with the `/file:` switch, and a directory with the `/directory:` switch.</span></span> <span data-ttu-id="acf41-114">Aşağıdaki örnekte gösterildiği gibi birden çok dosya veya dizin belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="acf41-114">You can specify multiple files or directories, as shown in the following example:</span></span>  
  
```console  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
> <span data-ttu-id="acf41-115">Her. dll veya. exe yalnızca bir kez yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="acf41-115">Each .dll or .exe should only be loaded one time.</span></span> <span data-ttu-id="acf41-116">Bir dosya birden çok kez yüklenirse araç yanlış bilgiler döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="acf41-116">If a file is loaded multiple times, the tool may return incorrect information.</span></span>  
  
 <span data-ttu-id="acf41-117">Dosya ve dizinlerin listesinden sonra, bir komut ve bu komut için herhangi bir seçeneği belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="acf41-117">After the list of files and directories, you must specify a command, and any options for that command.</span></span>  
  
<a name="listing_available_parts"></a>   
## <a name="listing-available-parts"></a><span data-ttu-id="acf41-118">Kullanılabilir bölümleri listeleme</span><span class="sxs-lookup"><span data-stu-id="acf41-118">Listing Available Parts</span></span>  
 <span data-ttu-id="acf41-119">Yüklenen dosyalarda belirtilen tüm parçaları listelemek için `/parts` eylemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="acf41-119">Use the `/parts` action to list all the parts declared in the files loaded.</span></span> <span data-ttu-id="acf41-120">Sonuç, bölüm adlarının basit bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="acf41-120">The result is a simple list of part names.</span></span>  
  
```console
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 <span data-ttu-id="acf41-121">Parçalar hakkında daha fazla bilgi için `/verbose` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="acf41-121">For more information about the parts, use the `/verbose` option.</span></span> <span data-ttu-id="acf41-122">Bu, tüm kullanılabilir parçalar için daha fazla bilgi çıktısını alacak.</span><span class="sxs-lookup"><span data-stu-id="acf41-122">This will output more information for all available parts.</span></span> <span data-ttu-id="acf41-123">Tek bir bölüm hakkında daha fazla bilgi edinmek için `/parts`yerine `/type` eylemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="acf41-123">To get more information about a single part, use the `/type` action instead of `/parts`.</span></span>  
  
```console  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>   
## <a name="listing-imports-and-exports"></a><span data-ttu-id="acf41-124">Içeri aktarmaları ve dışarı aktarmaları listeleme</span><span class="sxs-lookup"><span data-stu-id="acf41-124">Listing Imports and Exports</span></span>  
 <span data-ttu-id="acf41-125">`/imports` ve `/exports` eylemleri, tüm içeri aktarılan parçaları ve tüm aktarılmış parçaları sırasıyla listeedecektir.</span><span class="sxs-lookup"><span data-stu-id="acf41-125">The `/imports` and `/exports` actions will list all the imported parts and all the exported parts, respectively.</span></span> <span data-ttu-id="acf41-126">Ayrıca, `/importers` veya `/exporters` eylemlerini kullanarak belirli bir türü içeri veya dışarı aktarma bölümlerini de listeleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acf41-126">You can also list the parts that import or export a particular type by using the `/importers` or `/exporters` actions.</span></span>  
  
```console  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 <span data-ttu-id="acf41-127">Bu eylemlere `/verbose` seçeneğini de uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acf41-127">You can also apply the `/verbose` option to these actions.</span></span>  
  
<a name="finding_rejected_parts"></a>   
## <a name="finding-rejected-parts"></a><span data-ttu-id="acf41-128">Reddedilen parçaları bulma</span><span class="sxs-lookup"><span data-stu-id="acf41-128">Finding Rejected Parts</span></span>  
 <span data-ttu-id="acf41-129">Mevcut parçalar yüklendikten sonra, Mefx bunları oluşturmak için MEF bileşim altyapısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="acf41-129">Once it has loaded the available parts, Mefx uses the MEF composition engine to compose them.</span></span> <span data-ttu-id="acf41-130">Başarıyla birleştirilemeyen bölümler *reddedildi*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="acf41-130">Parts that cannot be successfully composed are referred to as *rejected*.</span></span> <span data-ttu-id="acf41-131">Reddedilen tüm parçaları listelemek için `/rejected` eylemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="acf41-131">To list all the rejected parts, use the `/rejected` action.</span></span>  
  
 <span data-ttu-id="acf41-132">Reddedilen bölümlerle ilgili ayrıntılı bilgileri yazdırmak için `/rejected` eylemi ile `/verbose` seçeneğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acf41-132">You can use the `/verbose` option with the `/rejected` action to print detailed information about rejected parts.</span></span> <span data-ttu-id="acf41-133">Aşağıdaki örnekte, `ClassLibrary1` DLL `MemberPart` ve `ChainOne` parçalarını içeri aktaran `AddIn` bölümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="acf41-133">In the following example, the `ClassLibrary1` DLL contains the `AddIn` part, which imports the `MemberPart` and `ChainOne` parts.</span></span> <span data-ttu-id="acf41-134">`ChainTwo`içeri aktarmalar `ChainOne`, ancak `ChainTwo` yok.</span><span class="sxs-lookup"><span data-stu-id="acf41-134">`ChainOne` imports `ChainTwo`, but `ChainTwo` does not exist.</span></span> <span data-ttu-id="acf41-135">Bu, `AddIn` reddedilmesine neden olan `ChainOne` reddedildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="acf41-135">This means that `ChainOne` is rejected, which causes `AddIn` to be rejected.</span></span>  
  
```console  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 <span data-ttu-id="acf41-136">Aşağıda, önceki komutun tüm çıktısı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="acf41-136">The following shows the complete output of the previous command:</span></span>  
  
```output
[Part] ClassLibrary1.AddIn from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] ClassLibrary1.AddIn (ContractName="ClassLibrary1.AddIn")  
  [Import] ClassLibrary1.AddIn.memberPart (ContractName="ClassLibrary1.MemberPart")  
    [SatisfiedBy] ClassLibrary1.MemberPart (ContractName="ClassLibrary1.MemberPart") from: ClassLibrary1.MemberPart from: AssemblyCatalog (Assembly="ClassLibrar  
y1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Import] ClassLibrary1.AddIn.chain (ContractName="ClassLibrary1.ChainOne")  
    [Exception] System.ComponentModel.Composition.ImportCardinalityMismatchException: No valid exports were found that match the constraint '((exportDefinition.ContractName == "ClassLibrary1.ChainOne") AndAlso (exportDefinition.Metadata.ContainsKey("ExportTypeIdentity") AndAlso "ClassLibrary1.ChainOne".Equals(exportDefinition.Metadata.get_Item("ExportTypeIdentity"))))', invalid exports may have been rejected.  
   at System.ComponentModel.Composition.Hosting.ExportProvider.GetExports(ImportDefinition definition, AtomicComposition atomicComposition)  
   at Microsoft.ComponentModel.Composition.Diagnostics.CompositionInfo.AnalyzeImportDefinition(ExportProvider host, IEnumerable`1 availableParts, ImportDefinition id)  
    [Unsuitable] ClassLibrary1.ChainOne (ContractName="ClassLibrary1.ChainOne")  
from: ClassLibrary1.ChainOne from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
      [Because] PartDefinitionIsRejected, The part providing the export is rejected because of other issues.  
  
[Part] ClassLibrary1.ChainOne from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Primary Rejection]  
  [Export] ClassLibrary1.ChainOne (ContractName="ClassLibrary1.ChainOne")  
  [Import] ClassLibrary1.ChainOne.chain (ContractName="ClassLibrary1.ChainTwo")  
    [Exception] System.ComponentModel.Composition.ImportCardinalityMismatchException: No valid exports were found that match the constraint '((exportDefinition.ContractName == "ClassLibrary1.ChainTwo") AndAlso (exportDefinition.Metadata.ContainsKey("ExportTypeIdentity") AndAlso "ClassLibrary1.ChainTwo".Equals(exportDefinition.Metadata.get_Item("ExportTypeIdentity"))))', invalid exports may have been rejected.  
   at System.ComponentModel.Composition.Hosting.ExportProvider.GetExports(ImportDefinition definition, AtomicComposition atomicComposition)  
   at Microsoft.ComponentModel.Composition.Diagnostics.CompositionInfo.AnalyzeImportDefinition(ExportProvider host, IEnumerable`1 availableParts, ImportDefinition id)  
```  
  
 <span data-ttu-id="acf41-137">İlginç bilgiler `[Exception]` ve `[Unsuitable]` sonuçlarında bulunur.</span><span class="sxs-lookup"><span data-stu-id="acf41-137">The interesting information is contained in the `[Exception]` and `[Unsuitable]` results.</span></span> <span data-ttu-id="acf41-138">`[Exception]` sonucu, bir bölümün neden reddedildiği hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="acf41-138">The `[Exception]` result provides information about why a part was rejected.</span></span> <span data-ttu-id="acf41-139">`[Unsuitable]` sonucu, bir içeri aktarmayı dolduracak şekilde başka bir şekilde eşleşen bölümün neden kullanılamayacağını belirtir; Bu durumda, bu bölümün kendisi eksik içeri aktarmalar için reddedildiği için.</span><span class="sxs-lookup"><span data-stu-id="acf41-139">The `[Unsuitable]` result indicates why an otherwise-matching part could not be used to fill an import; in this case, because that part was itself rejected for missing imports.</span></span>  
  
<a name="analyzing_primary_causes"></a>   
## <a name="analyzing-primary-causes"></a><span data-ttu-id="acf41-140">Birincil nedenler çözümleniyor</span><span class="sxs-lookup"><span data-stu-id="acf41-140">Analyzing Primary Causes</span></span>  
 <span data-ttu-id="acf41-141">Çok sayıda bölüm uzun bir bağımlılık zincirinde bağlanmışsa, en alta yakın bir bölümü içeren bir sorun, tüm zincirin reddedilmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="acf41-141">If several parts are linked in a long dependency chain, a problem involving a part near the bottom may cause the entire chain to be rejected.</span></span> <span data-ttu-id="acf41-142">Hatanın asıl nedeni her zaman açık olmadığından, bu sorunların tanılanması zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="acf41-142">Diagnosing these problems can be difficult because the root cause of the failure is not always obvious.</span></span> <span data-ttu-id="acf41-143">Sorunu gidermek için, herhangi bir geçişli reddetme kök nedenini bulmayı deneyen `/causes` eylemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acf41-143">To help with the problem, you can use the `/causes` action, which attempts to find the root cause of any cascading rejection.</span></span>  
  
 <span data-ttu-id="acf41-144">Önceki örnekte `/causes` eyleminin kullanılması, doldurulmamış içeri aktarma, `AddIn`reddedilme nedeninin asıl nedeni olan `ChainOne`için yalnızca bilgileri listeleyebilir.</span><span class="sxs-lookup"><span data-stu-id="acf41-144">Using the `/causes` action on the previous example would list only information for `ChainOne`, whose unfilled import is the root cause of the rejection of `AddIn`.</span></span> <span data-ttu-id="acf41-145">`/causes` eylemi hem normal hem de `/verbose` seçeneklerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="acf41-145">The `/causes` action can be used in both normal and `/verbose` options.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="acf41-146">Çoğu durumda, Mefx bir basamaklı hatanın kök nedenini tanılayabilir.</span><span class="sxs-lookup"><span data-stu-id="acf41-146">In most cases, Mefx will be able to diagnose the root cause of a cascading failure.</span></span> <span data-ttu-id="acf41-147">Ancak, parçaların bir kapsayıcıya programlı olarak eklendiği durumlarda, hiyerarşik kapsayıcılar içeren durumlar veya özel `ExportProvider` uygulamaları içeren durumlar için Mefx, nedeni tanılayamaz.</span><span class="sxs-lookup"><span data-stu-id="acf41-147">However, in cases where parts are added programmatically to a container, cases involving hierarchical containers, or cases involving custom `ExportProvider` implementations, Mefx will not be able to diagnose the cause.</span></span> <span data-ttu-id="acf41-148">Genel olarak, daha önce açıklanan durumlar mümkün olduğunda kaçınılması gerekir, çünkü hataların genellikle tanılanması zordur.</span><span class="sxs-lookup"><span data-stu-id="acf41-148">In general, the previously described cases should be avoided where possible, as failures are generally difficult to diagnose.</span></span>  
  
<a name="white_lists"></a>   
## <a name="white-lists"></a><span data-ttu-id="acf41-149">Beyaz listeler</span><span class="sxs-lookup"><span data-stu-id="acf41-149">White Lists</span></span>  
 <span data-ttu-id="acf41-150">`/whitelist` seçeneği, reddedilmesi beklenen bölümleri listeleyen bir metin dosyası belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="acf41-150">The `/whitelist` option enables you to specify a text file that lists parts that are expected to be rejected.</span></span> <span data-ttu-id="acf41-151">Ardından, beklenmeyen ret ler işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="acf41-151">Unexpected rejections will then be flagged.</span></span> <span data-ttu-id="acf41-152">Bu, tamamlanmamış bir kitaplığı veya bazı bağımlılıkları eksik olan bir alt kitaplığı çözümlediğinizde yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="acf41-152">This can be useful when you analyze an incomplete library, or a sub-library that is missing some dependencies.</span></span> <span data-ttu-id="acf41-153">`/whitelist` seçeneği `/rejected` veya `/causes` eylemlere uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="acf41-153">The `/whitelist` option can be applied to the `/rejected` or `/causes` actions.</span></span>  
  
 <span data-ttu-id="acf41-154">"ClassLibrary1. ChainOne" metnini içeren test. txt adlı bir dosya düşünün.</span><span class="sxs-lookup"><span data-stu-id="acf41-154">Consider a file named test.txt that contains the text "ClassLibrary1.ChainOne".</span></span> <span data-ttu-id="acf41-155">Önceki örnekte `/whitelist` seçeneğiyle `/rejected` eylemini çalıştırırsanız, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="acf41-155">If you run the `/rejected` action with the `/whitelist` option on the previous example, it will produce the following output:</span></span>  
  
```console
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
