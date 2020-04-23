---
title: COM Bileşenlerini .NET Framework'te Gösterme
ms.date: 03/30/2017
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
ms.openlocfilehash: 914f72b5e4840555541943620ca2df1f629b0604
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123520"
---
# <a name="exposing-com-components-to-the-net-framework"></a><span data-ttu-id="8bea9-102">COM Bileşenlerini .NET Framework'te Gösterme</span><span class="sxs-lookup"><span data-stu-id="8bea9-102">Exposing COM Components to the .NET Framework</span></span>
<span data-ttu-id="8bea9-103">Bu bölümde, mevcut bir COM bileşenini yönetilen koda göstermek için gereken işlem özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="8bea9-103">This section summarizes the process needed to expose an existing COM component to managed code.</span></span> <span data-ttu-id="8bea9-104">.NET Framework ile sıkı bir şekilde tümleştirilen COM sunucularının yazılmasına ilişkin ayrıntılar için bkz. [Interoperation Için tasarım konuları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8bea9-104">For details about writing COM servers that tightly integrate with the .NET Framework, see [Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span></span>
  
 <span data-ttu-id="8bea9-105">Mevcut COM bileşenleri, yönetilen kodda orta katman iş uygulamaları veya yalıtılmış işlevler olarak değerli kaynaklardır.</span><span class="sxs-lookup"><span data-stu-id="8bea9-105">Existing COM components are valuable resources in managed code as middle-tier business applications or as isolated functionality.</span></span> <span data-ttu-id="8bea9-106">İdeal bir bileşen bir birincil birlikte çalışma derlemesine sahiptir ve COM tarafından uygulanan programlama standartlarına sıkı bir şekilde uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="8bea9-106">An ideal component has a primary interop assembly and conforms tightly to the programming standards imposed by COM.</span></span>  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a><span data-ttu-id="8bea9-107">COM bileşenlerini .NET Framework kullanıma sunmak için</span><span class="sxs-lookup"><span data-stu-id="8bea9-107">To expose COM components to the .NET Framework</span></span>  
  
1. <span data-ttu-id="8bea9-108">[Bir tür kitaplığını derleme olarak Içeri aktarın](importing-a-type-library-as-an-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="8bea9-108">[Import a type library as an assembly](importing-a-type-library-as-an-assembly.md).</span></span>  
  
     <span data-ttu-id="8bea9-109">Ortak dil çalışma zamanı, COM türleri dahil olmak üzere tüm türler için meta veriler gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8bea9-109">The common language runtime requires metadata for all types, including COM types.</span></span> <span data-ttu-id="8bea9-110">Meta veri olarak içeri aktarılan COM türlerini içeren bir derlemeyi almanın birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="8bea9-110">There are several ways to obtain an assembly containing COM types imported as metadata.</span></span>  
  
2. <span data-ttu-id="8bea9-111">[Yönetilen KODDA com türlerini kullanın](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8bea9-111">[Use COM types in managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>  
  
     <span data-ttu-id="8bea9-112">Com türlerini inceleyebilir, örnekleri etkinleştirebilir ve COM nesnesi üzerinde yöntemleri herhangi bir yönetilen tür için yaptığınız şekilde çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8bea9-112">You can inspect COM types, activate instances, and invoke methods on the COM object the same way you do for any managed type.</span></span>  
  
3. <span data-ttu-id="8bea9-113">[Birlikte çalışabilirlik projesi derleyin](compiling-an-interop-project.md).</span><span class="sxs-lookup"><span data-stu-id="8bea9-113">[Compile an interop project](compiling-an-interop-project.md).</span></span>  
  
     <span data-ttu-id="8bea9-114">Windows SDK, Visual Basic, C# ve C++ dahil olmak üzere ortak dil belirtimi (CLS) ile uyumlu birkaç dil için derleyiciler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8bea9-114">The Windows SDK provides compilers for several languages compliant with the Common Language Specification (CLS), including Visual Basic, C#, and C++.</span></span>  
  
4. <span data-ttu-id="8bea9-115">[Birlikte çalışabilirlik uygulaması dağıtın](deploying-an-interop-application.md).</span><span class="sxs-lookup"><span data-stu-id="8bea9-115">[Deploy an interop application](deploying-an-interop-application.md).</span></span>  
  
     <span data-ttu-id="8bea9-116">Birlikte çalışma uygulamaları, genel derleme önbelleğinde [tanımlayıcı adlı](../../standard/assembly/strong-named.md), imzalanmış derlemeler olarak en iyi şekilde dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="8bea9-116">Interop applications are best deployed as [strong-named](../../standard/assembly/strong-named.md), signed assemblies in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bea9-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8bea9-117">See also</span></span>

- [<span data-ttu-id="8bea9-118">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="8bea9-118">Interoperating with Unmanaged Code</span></span>](index.md)
- <span data-ttu-id="8bea9-119">[Birlikte çalışabilirlik için tasarım konuları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8bea9-119">[Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span></span>
- [<span data-ttu-id="8bea9-120">COM Birlikte Çalışma Örneği: .NET İstemcisi ve COM Sunucusu</span><span class="sxs-lookup"><span data-stu-id="8bea9-120">COM Interop Sample: .NET Client and COM Server</span></span>](com-interop-sample-net-client-and-com-server.md)
- [<span data-ttu-id="8bea9-121">Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler</span><span class="sxs-lookup"><span data-stu-id="8bea9-121">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="8bea9-122">Gacutil. exe (Genel Bütünleştirilmiş Kod Önbelleği Aracı)</span><span class="sxs-lookup"><span data-stu-id="8bea9-122">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
