---
title: 'Nasıl yapılı: Derleme içeriğini görüntüleme'
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET Framework], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 179b240bb06a319ff71009e14323d5c8f2740e5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187382"
---
# <a name="how-to-view-assembly-contents"></a><span data-ttu-id="47c28-102">Nasıl yapılı: Derleme içeriğini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="47c28-102">How to: View assembly contents</span></span>

<span data-ttu-id="47c28-103">Bir dosyada Microsoft ara dili (MSIL) bilgilerini görüntülemek için [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="47c28-103">You can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in a file.</span></span> <span data-ttu-id="47c28-104">İncelenen dosya bir derleme ise, bu bilgiler derlemenin özniteliklerini ve diğer modüllere ve derlemelere yapılan başvuruları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="47c28-104">If the file being examined is an assembly, this information can include the assembly's attributes and references to other modules and assemblies.</span></span> <span data-ttu-id="47c28-105">Bu bilgiler, bir dosyanın derleme mi yoksa derlemenin bir parçası mı olduğunu ve dosyanın diğer modüllere veya derlemelere başvurup göndermeler göndermediğini belirlemede yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="47c28-105">This information can be helpful in determining whether a file is an assembly or part of an assembly and whether the file has references to other modules or assemblies.</span></span>

<span data-ttu-id="47c28-106">*Ildasm.exe*kullanarak bir derlemenin içeriğini görüntülemek için komut istemine **ildasm \<derleme adı>** girin.</span><span class="sxs-lookup"><span data-stu-id="47c28-106">To display the contents of an assembly using *Ildasm.exe*, enter **ildasm \<assembly name>** at a command prompt.</span></span> <span data-ttu-id="47c28-107">Örneğin, aşağıdaki komut *Hello.exe* derlemesini söker.</span><span class="sxs-lookup"><span data-stu-id="47c28-107">For example, the following command disassembles the *Hello.exe* assembly.</span></span>

```cmd
ildasm Hello.exe
```

<span data-ttu-id="47c28-108">Derleme bildirimi bilgilerini görüntülemek için, MSIL Sökme penceresindeki **Manifest** simgesini çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="47c28-108">To view assembly manifest information, double-click the **Manifest** icon in the MSIL Disassembler window.</span></span>

## <a name="example"></a><span data-ttu-id="47c28-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="47c28-109">Example</span></span>

<span data-ttu-id="47c28-110">Aşağıdaki örnek temel bir "Hello World" programı ile başlar.</span><span class="sxs-lookup"><span data-stu-id="47c28-110">The following example starts with a basic "Hello World" program.</span></span> <span data-ttu-id="47c28-111">Programı derledikten *sonra, Hello.exe* derlemesini sökmek ve derleme bildirimini görüntülemek için *Ildasm.exe'yi* kullanın.</span><span class="sxs-lookup"><span data-stu-id="47c28-111">After compiling the program, use *Ildasm.exe* to disassemble the *Hello.exe* assembly and view the assembly manifest.</span></span>

```cpp
using namespace System;

class MainApp
{
public:
    static void Main()
    {
        Console::WriteLine("Hello World using C++/CLI!");
    }
};

int main()
{
    MainApp::Main();
}
```

```csharp
using System;

class MainApp
{
    public static void Main()
    {
        Console.WriteLine("Hello World using C#!");
    }
}
```

```vb
Class MainApp
    Public Shared Sub Main()
        Console.WriteLine("Hello World using Visual Basic!")
    End Sub
End Class
```

<span data-ttu-id="47c28-112">*Hello.exe* derlemesinde *ildasm.exe* komutunu çalıştırmak ve MSIL Desassembler **penceresindeki Manifest** simgesine çift tıklayarak aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="47c28-112">Running the command *ildasm.exe* on the *Hello.exe* assembly and double-clicking the **Manifest** icon in the MSIL Disassembler window produces the following output:</span></span>

```output
// Metadata version: v4.0.30319
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 4:0:0:0
}
.assembly Hello
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .custom instance void [mscorlib]System.Runtime.CompilerServices.RuntimeCompatibilityAttribute::.ctor() = ( 01 00 01 00 54 02 16 57 72 61 70 4E 6F 6E 45 78   // ....T..WrapNonEx
                                                                                                             63 65 70 74 69 6F 6E 54 68 72 6F 77 73 01 )       // ceptionThrows.
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module Hello.exe
// MVID: {7C2770DB-1594-438D-BAE5-98764C39CCCA}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x00600000
```

<span data-ttu-id="47c28-113">Aşağıdaki tabloda, örnekte kullanılan *Hello.exe* derlemesinin derleme bildirimindeki her bir yönerge açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="47c28-113">The following table describes each directive in the assembly manifest of the *Hello.exe* assembly used in the example:</span></span>

|<span data-ttu-id="47c28-114">Yönergesi</span><span class="sxs-lookup"><span data-stu-id="47c28-114">Directive</span></span>|<span data-ttu-id="47c28-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47c28-115">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="47c28-116">**.assembly extern \<montaj adı>**</span><span class="sxs-lookup"><span data-stu-id="47c28-116">**.assembly extern \<assembly name>**</span></span>|<span data-ttu-id="47c28-117">Geçerli modül tarafından başvurulan öğeleri içeren başka bir derleme `mscorlib`belirtir (bu örnekte).</span><span class="sxs-lookup"><span data-stu-id="47c28-117">Specifies another assembly that contains items referenced by the current module (in this example, `mscorlib`).</span></span>|
|<span data-ttu-id="47c28-118">**.publickeytoken \<belirteci>**</span><span class="sxs-lookup"><span data-stu-id="47c28-118">**.publickeytoken \<token>**</span></span>|<span data-ttu-id="47c28-119">Başvurulan derlemenin gerçek anahtarının belirteci.</span><span class="sxs-lookup"><span data-stu-id="47c28-119">Specifies the token of the actual key of the referenced assembly.</span></span>|
|<span data-ttu-id="47c28-120">**.ver \<sürüm numarası>**</span><span class="sxs-lookup"><span data-stu-id="47c28-120">**.ver \<version number>**</span></span>|<span data-ttu-id="47c28-121">Başvurulan derlemenin sürüm numarasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="47c28-121">Specifies the version number of the referenced assembly.</span></span>|
|<span data-ttu-id="47c28-122">**.montaj \<montaj adı>**</span><span class="sxs-lookup"><span data-stu-id="47c28-122">**.assembly \<assembly name>**</span></span>|<span data-ttu-id="47c28-123">Derleme adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="47c28-123">Specifies the assembly name.</span></span>|
|<span data-ttu-id="47c28-124">**.hash \<algoritmainin int32 değeri>**</span><span class="sxs-lookup"><span data-stu-id="47c28-124">**.hash algorithm \<int32 value>**</span></span>|<span data-ttu-id="47c28-125">Kullanılan karma algoritmayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="47c28-125">Specifies the hash algorithm used.</span></span>|
|<span data-ttu-id="47c28-126">**.ver \<sürüm numarası>**</span><span class="sxs-lookup"><span data-stu-id="47c28-126">**.ver \<version number>**</span></span>|<span data-ttu-id="47c28-127">Derlemenin sürüm numarasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="47c28-127">Specifies the version number of the assembly.</span></span>|
|<span data-ttu-id="47c28-128">**.module \<dosya adı>**</span><span class="sxs-lookup"><span data-stu-id="47c28-128">**.module \<file name>**</span></span>|<span data-ttu-id="47c28-129">Montajı oluşturan modüllerin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="47c28-129">Specifies the name of the modules that make up the assembly.</span></span> <span data-ttu-id="47c28-130">Bu örnekte, derleme yalnızca bir dosyadan oluşur.</span><span class="sxs-lookup"><span data-stu-id="47c28-130">In this example, the assembly consists of only one file.</span></span>|
|<span data-ttu-id="47c28-131">**.alt \<sistem değeri>**</span><span class="sxs-lookup"><span data-stu-id="47c28-131">**.subsystem \<value>**</span></span>|<span data-ttu-id="47c28-132">Program için gerekli olan uygulama ortamını belirtir.</span><span class="sxs-lookup"><span data-stu-id="47c28-132">Specifies the application environment required for the program.</span></span> <span data-ttu-id="47c28-133">Bu örnekte, 3 değeri bu yürütülebilir bir konsoldan çalıştırılır gösterir.</span><span class="sxs-lookup"><span data-stu-id="47c28-133">In this example, the value 3 indicates that this executable is run from a console.</span></span>|
|<span data-ttu-id="47c28-134">**.corflags**</span><span class="sxs-lookup"><span data-stu-id="47c28-134">**.corflags**</span></span>|<span data-ttu-id="47c28-135">Şu anda meta verilerde ayrılmış bir alan.</span><span class="sxs-lookup"><span data-stu-id="47c28-135">Currently a reserved field in the metadata.</span></span>|

<span data-ttu-id="47c28-136">Derleme bildirimi, derlemenin içeriğine bağlı olarak bir dizi farklı yönerge içerebilir.</span><span class="sxs-lookup"><span data-stu-id="47c28-136">An assembly manifest can contain a number of different directives, depending on the contents of the assembly.</span></span> <span data-ttu-id="47c28-137">Derleme bildirimindeki yönergelerin kapsamlı bir listesi için, ecma belgelerine, özellikle "Bölüm II: Meta veri tanımı ve anlam bilimi" ve "Bölüm III: CIL Yönerge Seti"ne bakın:</span><span class="sxs-lookup"><span data-stu-id="47c28-137">For an extensive list of the directives in the assembly manifest, see the Ecma documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set":</span></span>

- [<span data-ttu-id="47c28-138">ECMA C# ve Ortak Dil Altyapı standartları</span><span class="sxs-lookup"><span data-stu-id="47c28-138">ECMA C# and Common Language Infrastructure standards</span></span>](../components.md#applicable-standards)
- [<span data-ttu-id="47c28-139">Standart ECMA-335 - Ortak Dil Altyapısı (CLI)</span><span class="sxs-lookup"><span data-stu-id="47c28-139">Standard ECMA-335 - Common Language Infrastructure (CLI)</span></span>](http://www.ecma-international.org/publications/standards/Ecma-335.htm)

## <a name="see-also"></a><span data-ttu-id="47c28-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47c28-140">See also</span></span>

- [<span data-ttu-id="47c28-141">Uygulama Etki Alanları ve derlemeler</span><span class="sxs-lookup"><span data-stu-id="47c28-141">Application domains and assemblies</span></span>](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [<span data-ttu-id="47c28-142">Uygulama etki alanları ve derlemeler nasıl konu edilir</span><span class="sxs-lookup"><span data-stu-id="47c28-142">Application domains and assemblies how-to topics</span></span>](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [<span data-ttu-id="47c28-143">Ildasm.exe (IL Ayrıştırıcı)</span><span class="sxs-lookup"><span data-stu-id="47c28-143">Ildasm.exe (IL Disassembler)</span></span>](../../framework/tools/ildasm-exe-il-disassembler.md)
