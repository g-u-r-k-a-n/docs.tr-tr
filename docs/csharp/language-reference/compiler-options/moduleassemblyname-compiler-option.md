---
description: -moduleassemblyname (C# derleyici seçeneği)
title: -moduleassemblyname (C# derleyici seçeneği)
ms.date: 07/20/2015
f1_keywords:
- /moduleassemblyname
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
ms.openlocfilehash: 9131db17d767c76fe6a57f5d5353474153e0c269
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "91194095"
---
# <a name="-moduleassemblyname-c-compiler-option"></a><span data-ttu-id="a0837-103">-moduleassemblyname (C# derleyici seçeneği)</span><span class="sxs-lookup"><span data-stu-id="a0837-103">-moduleassemblyname (C# Compiler Option)</span></span>

<span data-ttu-id="a0837-104">Genel olmayan türleri bir. netmodule 'nin erişebileceği bir derlemeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0837-104">Specifies an assembly whose non-public types a .netmodule can access.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0837-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a0837-105">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="a0837-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="a0837-106">Arguments</span></span>  

 `assembly_name`  
 <span data-ttu-id="a0837-107">Genel olmayan türleri. netmodule 'nin erişebileceği derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="a0837-107">The name of the assembly whose non-public types the .netmodule can access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0837-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a0837-108">Remarks</span></span>  

 <span data-ttu-id="a0837-109">**-moduleassemblyname** bir. netmodule oluştururken ve aşağıdaki koşulların doğru olduğu durumlarda kullanılmalıdır:</span><span class="sxs-lookup"><span data-stu-id="a0837-109">**-moduleassemblyname** should be used when building a .netmodule, and where the following conditions are true:</span></span>  
  
- <span data-ttu-id="a0837-110">. Netmodule, mevcut bir derlemede ortak olmayan türlere erişim gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a0837-110">The .netmodule needs access to non-public types in an existing assembly.</span></span>  
  
- <span data-ttu-id="a0837-111">. Netmodule 'nin derolacağı derlemenin adını bilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0837-111">You know the name of the assembly into which the .netmodule will be built.</span></span>  
  
- <span data-ttu-id="a0837-112">Mevcut bütünleştirilmiş kod,. netmodule 'nin derolacağı derlemeye arkadaş derleme erişimi verdi.</span><span class="sxs-lookup"><span data-stu-id="a0837-112">The existing assembly has granted friend assembly access to the assembly into which the .netmodule will be built.</span></span>  
  
 <span data-ttu-id="a0837-113">. Netmodule oluşturma hakkında daha fazla bilgi için bkz. [-target: Module (C# derleyici seçenekleri)](./target-module-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="a0837-113">For more information on building a .netmodule, see [-target:module (C# Compiler Options)](./target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="a0837-114">Friend derlemeleri hakkında daha fazla bilgi için bkz. [arkadaş derlemeler](../../../standard/assembly/friend.md).</span><span class="sxs-lookup"><span data-stu-id="a0837-114">For more information on friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
 <span data-ttu-id="a0837-115">Bu seçenek geliştirme ortamının içinden kullanılamaz; yalnızca komut satırından derlerken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a0837-115">This option is not available from within the development environment; it is only available when compiling from the command line.</span></span>  
  
 <span data-ttu-id="a0837-116">Bu derleyici seçeneği Visual Studio 'da kullanılamaz ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="a0837-116">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0837-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0837-117">Example</span></span>  

 <span data-ttu-id="a0837-118">Bu örnek, bir özel türü olan ve csman_an_assembly adlı bir derlemeye arkadaş derleme erişimi veren bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a0837-118">This sample builds an assembly with a private type, and that gives friend assembly access to an assembly called csman_an_assembly.</span></span>  
  
```csharp  
// moduleassemblyname_1.cs  
// compile with: -target:library  
using System;  
using System.Runtime.CompilerServices;  
  
[assembly:InternalsVisibleTo ("csman_an_assembly")]  
  
class An_Internal_Class
{  
    public void Test()
    {
        Console.WriteLine("An_Internal_Class.Test called");
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="a0837-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0837-119">Example</span></span>  

 <span data-ttu-id="a0837-120">Bu örnek, moduleassemblyname_1.dll derlemede ortak olmayan bir türe erişen. netmodule 'yi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a0837-120">This sample builds a .netmodule that accesses a non-public type in the assembly moduleassemblyname_1.dll.</span></span> <span data-ttu-id="a0837-121">Bu. netmodule csman_an_assembly adlı bir derlemede derlenip,. netmodule 'nin csman_an_assembly arkadaş derleme erişimi veren bir derlemede genel olmayan türlere erişmesine izin vererek **-moduleassemblyname** belirtemez.</span><span class="sxs-lookup"><span data-stu-id="a0837-121">By knowing that this .netmodule will be built into an assembly called csman_an_assembly, we can specify **-moduleassemblyname**, allowing the .netmodule to access non-public types in an assembly that has granted friend assembly access to csman_an_assembly.</span></span>  
  
```csharp  
// moduleassemblyname_2.cs  
// compile with: -moduleassemblyname:csman_an_assembly -target:module -reference:moduleassemblyname_1.dll  
class B {  
    public void Test() {  
        An_Internal_Class x = new An_Internal_Class();  
        x.Test();  
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="a0837-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0837-122">Example</span></span>  

 <span data-ttu-id="a0837-123">Bu kod örneği, daha önce oluşturulmuş derleme ve. netmodule 'e başvurarak bütünleştirilmiş kod csman_an_assembly oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a0837-123">This code sample builds the assembly csman_an_assembly, referencing the previously-built assembly and .netmodule.</span></span>  
  
```csharp  
// csman_an_assembly.cs  
// compile with: -addmodule:moduleassemblyname_2.netmodule -reference:moduleassemblyname_1.dll  
class A {  
    public static void Main() {  
        B bb = new B();  
        bb.Test();  
    }  
}  
```  
  
<span data-ttu-id="a0837-124">**An_Internal_Class. test çağrıldı**</span><span class="sxs-lookup"><span data-stu-id="a0837-124">**An_Internal_Class.Test called**</span></span>

## <a name="see-also"></a><span data-ttu-id="a0837-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0837-125">See also</span></span>

- [<span data-ttu-id="a0837-126">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="a0837-126">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="a0837-127">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="a0837-127">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
