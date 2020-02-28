---
title: 'Nasıl yapılır: tanımlayıcı adlı bir derlemeye başvurma'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: adda4ed2ab5c59e3518b8e724044529a79840ad0
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156484"
---
# <a name="how-to-reference-a-strong-named-assembly"></a><span data-ttu-id="06a77-102">Nasıl yapılır: tanımlayıcı adlı bir derlemeye başvurma</span><span class="sxs-lookup"><span data-stu-id="06a77-102">How to: Reference a strong-named assembly</span></span>
<span data-ttu-id="06a77-103">Tanımlayıcı adlı bir derlemede tür veya kaynaklara başvurma işlemi genellikle saydamdır.</span><span class="sxs-lookup"><span data-stu-id="06a77-103">The process for referencing types or resources in a strong-named assembly is usually transparent.</span></span> <span data-ttu-id="06a77-104">Başvuruyu derleme zamanında (erken bağlama) veya çalışma zamanında yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06a77-104">You can make the reference either at compile time (early binding) or at run time.</span></span>  
  
<span data-ttu-id="06a77-105">Derleyiciye derlenen derlemenin başka bir derlemeye açıkça başvuruda bulunduğunu belirttiğinizde derleme zamanı başvurusu oluşur.</span><span class="sxs-lookup"><span data-stu-id="06a77-105">A compile-time reference occurs when you indicate to the compiler that the assembly to be compiled explicitly references another assembly.</span></span> <span data-ttu-id="06a77-106">Derleme zamanı başvurusu kullandığınızda, derleyici hedeflenen tanımlayıcı adlı derlemenin ortak anahtarını otomatik olarak alır ve derlenen derlemenin derleme başvurusuna koyar.</span><span class="sxs-lookup"><span data-stu-id="06a77-106">When you use compile-time referencing, the compiler automatically gets the public key of the targeted strong-named assembly and places it in the assembly reference of the assembly being compiled.</span></span>
  
> [!NOTE]
> <span data-ttu-id="06a77-107">Tanımlayıcı adlı bir derleme, yalnızca diğer tanımlayıcı adlı derlemelerden türleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="06a77-107">A strong-named assembly can only use types from other strong-named assemblies.</span></span> <span data-ttu-id="06a77-108">Aksi takdirde, tanımlayıcı adlı derlemenin güvenliği tehlikeye girebilir.</span><span class="sxs-lookup"><span data-stu-id="06a77-108">Otherwise, the security of the strong-named assembly would be compromised.</span></span>  
  
## <a name="make-a-compile-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="06a77-109">Tanımlayıcı adlı bir derlemeye derleme zamanı başvurusu yapma</span><span class="sxs-lookup"><span data-stu-id="06a77-109">Make a compile-time reference to a strong-named assembly</span></span>  

<span data-ttu-id="06a77-110">Komut isteminde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="06a77-110">At a command prompt, type the following command:</span></span>  

<span data-ttu-id="06a77-111">\<*derleyici komutu*>  **/Reference:** \<*derleme adı*></span><span class="sxs-lookup"><span data-stu-id="06a77-111">\<*compiler command*> **/reference:**\<*assembly name*></span></span>  

<span data-ttu-id="06a77-112">Bu komutta *derleyici komutu* , kullanmakta olduğunuz dilin derleyici komutu ve *derleme adı* , başvurulmakta olan tanımlayıcı adlı derlemenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="06a77-112">In this command, *compiler command* is the compiler command for the language you are using, and *assembly name* is the name of the strong-named assembly being referenced.</span></span> <span data-ttu-id="06a77-113">Ayrıca, bir kitaplık derlemesi oluşturmak için **/t: Library** seçeneği gibi diğer derleyici seçeneklerini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06a77-113">You can also use other compiler options, such as the **/t:library** option for creating a library assembly.</span></span>  

<span data-ttu-id="06a77-114">Aşağıdaki örnek, *MyAssembly.cs*adlı bir kod modülünden *myLibAssembly. dll* adlı güçlü adlı bir derlemeye başvuran *MyAssembly. dll* adlı bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="06a77-114">The following example creates an assembly called *myAssembly.dll* that references a strong-named assembly called *myLibAssembly.dll* from a code module called *myAssembly.cs*.</span></span>  

```cmd
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  

## <a name="make-a-run-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="06a77-115">Tanımlayıcı adlı bir derlemeye çalışma zamanı başvurusu yapma</span><span class="sxs-lookup"><span data-stu-id="06a77-115">Make a run-time reference to a strong-named assembly</span></span>  
  
<span data-ttu-id="06a77-116">Tanımlayıcı adlı bir derlemeye çalışma zamanı başvurusu yaptığınızda (örneğin, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> yöntemini kullanarak), başvurulan tanımlayıcı adlı derlemenin görünen adını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="06a77-116">When you make a run-time reference to a strong-named assembly, for example by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> method, you must use the display name of the referenced strong-named assembly.</span></span> <span data-ttu-id="06a77-117">Görünen adın sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="06a77-117">The syntax of a display name is as follows:</span></span>  

<span data-ttu-id="06a77-118">\<*bütünleştirilmiş kod adı*> **,** \<*sürüm numarası*> **,** \<*kültür*> **,** \<*ortak anahtar belirteci*></span><span class="sxs-lookup"><span data-stu-id="06a77-118">\<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*></span></span>  

<span data-ttu-id="06a77-119">Örnek:</span><span class="sxs-lookup"><span data-stu-id="06a77-119">For example:</span></span>  

```console
myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33
```  

<span data-ttu-id="06a77-120">Bu örnekte, `PublicKeyToken` ortak anahtar belirtecinin onaltılı biçimidir.</span><span class="sxs-lookup"><span data-stu-id="06a77-120">In this example, `PublicKeyToken` is the hexadecimal form of the public key token.</span></span> <span data-ttu-id="06a77-121">Kültür değeri yoksa `Culture=neutral`kullanın.</span><span class="sxs-lookup"><span data-stu-id="06a77-121">If there is no culture value, use `Culture=neutral`.</span></span>  

<span data-ttu-id="06a77-122">Aşağıdaki kod örneği, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemiyle bu bilgilerin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="06a77-122">The following code example shows how to use this information with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  

```cpp
Assembly^ myDll =
    Assembly::Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1");
```

```csharp
Assembly myDll =
    Assembly.Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1");
```

```vb
Dim myDll As Assembly = _
    Assembly.Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1")
```

<span data-ttu-id="06a77-123">Aşağıdaki [tanımlayıcı ad (sn. exe)](../../framework/tools/sn-exe-strong-name-tool.md) komutunu kullanarak, belirli bir derleme için ortak anahtar ve ortak anahtar belirtecinin onaltılık biçimini yazdırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="06a77-123">You can print the hexadecimal format of the public key and public key token for a specific assembly by using the following [Strong Name (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) command:</span></span>  

<span data-ttu-id="06a77-124">**sn-Tp \<** *derleme* **>**</span><span class="sxs-lookup"><span data-stu-id="06a77-124">**sn -Tp \<** *assembly* **>**</span></span>  

<span data-ttu-id="06a77-125">Ortak anahtar dosyanız varsa, bunun yerine aşağıdaki komutu kullanabilirsiniz (komut satırı seçeneğinde büyük/küçük harf farkını aklınızda bulabilirsiniz):</span><span class="sxs-lookup"><span data-stu-id="06a77-125">If you have a public key file, you can use the following command instead (note the difference in case on the command-line option):</span></span>  

<span data-ttu-id="06a77-126">**sn-tp \<** *ortak anahtar dosyası* **>**</span><span class="sxs-lookup"><span data-stu-id="06a77-126">**sn -tp \<** *public key file* **>**</span></span>  

## <a name="see-also"></a><span data-ttu-id="06a77-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06a77-127">See also</span></span>

- [<span data-ttu-id="06a77-128">Tanımlayıcı adlı derlemeler oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="06a77-128">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
