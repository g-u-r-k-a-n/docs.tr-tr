---
title: 'Nasıl yapılır: tanımlayıcı adlı bir derlemeye başvurma'
description: Bu makalede, derleme zamanında veya çalışma zamanında tanımlayıcı adlı bir .NET derlemesinde türlerin veya kaynakların nasıl başvurulacağını gösterilmektedir.
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 919e4f4cf467e8fc28c3d007963393dad134ab57
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724058"
---
# <a name="how-to-reference-a-strong-named-assembly"></a><span data-ttu-id="b7802-103">Nasıl yapılır: tanımlayıcı adlı bir derlemeye başvurma</span><span class="sxs-lookup"><span data-stu-id="b7802-103">How to: Reference a strong-named assembly</span></span>

<span data-ttu-id="b7802-104">Tanımlayıcı adlı bir derlemede tür veya kaynaklara başvurma işlemi genellikle saydamdır.</span><span class="sxs-lookup"><span data-stu-id="b7802-104">The process for referencing types or resources in a strong-named assembly is usually transparent.</span></span> <span data-ttu-id="b7802-105">Başvuruyu derleme zamanında (erken bağlama) veya çalışma zamanında yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7802-105">You can make the reference either at compile time (early binding) or at run time.</span></span>  
  
<span data-ttu-id="b7802-106">Derleyiciye derlenen derlemenin başka bir derlemeye açıkça başvuruda bulunduğunu belirttiğinizde derleme zamanı başvurusu oluşur.</span><span class="sxs-lookup"><span data-stu-id="b7802-106">A compile-time reference occurs when you indicate to the compiler that the assembly to be compiled explicitly references another assembly.</span></span> <span data-ttu-id="b7802-107">Derleme zamanı başvurusu kullandığınızda, derleyici hedeflenen tanımlayıcı adlı derlemenin ortak anahtarını otomatik olarak alır ve derlenen derlemenin derleme başvurusuna koyar.</span><span class="sxs-lookup"><span data-stu-id="b7802-107">When you use compile-time referencing, the compiler automatically gets the public key of the targeted strong-named assembly and places it in the assembly reference of the assembly being compiled.</span></span>
  
> [!NOTE]
> <span data-ttu-id="b7802-108">Tanımlayıcı adlı bir derleme, yalnızca diğer tanımlayıcı adlı derlemelerden türleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="b7802-108">A strong-named assembly can only use types from other strong-named assemblies.</span></span> <span data-ttu-id="b7802-109">Aksi takdirde, tanımlayıcı adlı derlemenin güvenliği tehlikeye girebilir.</span><span class="sxs-lookup"><span data-stu-id="b7802-109">Otherwise, the security of the strong-named assembly would be compromised.</span></span>  
  
## <a name="make-a-compile-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="b7802-110">Tanımlayıcı adlı bir derlemeye derleme zamanı başvurusu yapma</span><span class="sxs-lookup"><span data-stu-id="b7802-110">Make a compile-time reference to a strong-named assembly</span></span>  

<span data-ttu-id="b7802-111">Komut isteminde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="b7802-111">At a command prompt, type the following command:</span></span>  

<span data-ttu-id="b7802-112">\<*compiler command*>**/Reference:**\<*assembly name*></span><span class="sxs-lookup"><span data-stu-id="b7802-112">\<*compiler command*> **/reference:**\<*assembly name*></span></span>  

<span data-ttu-id="b7802-113">Bu komutta *derleyici komutu* , kullanmakta olduğunuz dilin derleyici komutu ve *derleme adı* , başvurulmakta olan tanımlayıcı adlı derlemenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="b7802-113">In this command, *compiler command* is the compiler command for the language you are using, and *assembly name* is the name of the strong-named assembly being referenced.</span></span> <span data-ttu-id="b7802-114">Ayrıca, bir kitaplık derlemesi oluşturmak için **/t: Library** seçeneği gibi diğer derleyici seçeneklerini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7802-114">You can also use other compiler options, such as the **/t:library** option for creating a library assembly.</span></span>  

<span data-ttu-id="b7802-115">Aşağıdaki örnek, *MyAssembly.cs* adlı bir kod modülünden *myLibAssembly.dll* adlı tanımlayıcı adlı bir derlemeye başvuran *myAssembly.dll* adlı bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b7802-115">The following example creates an assembly called *myAssembly.dll* that references a strong-named assembly called *myLibAssembly.dll* from a code module called *myAssembly.cs*.</span></span>  

```cmd
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  

## <a name="make-a-run-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="b7802-116">Tanımlayıcı adlı bir derlemeye çalışma zamanı başvurusu yapma</span><span class="sxs-lookup"><span data-stu-id="b7802-116">Make a run-time reference to a strong-named assembly</span></span>  
  
<span data-ttu-id="b7802-117">Tanımlayıcı adlı bir derlemeye çalışma zamanı başvurusu yaptığınızda (örneğin, veya yöntemini kullanarak), <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> başvurulan tanımlayıcı adlı derlemenin görünen adını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7802-117">When you make a run-time reference to a strong-named assembly, for example by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> method, you must use the display name of the referenced strong-named assembly.</span></span> <span data-ttu-id="b7802-118">Görünen adın sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="b7802-118">The syntax of a display name is as follows:</span></span>  

<span data-ttu-id="b7802-119">\<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*></span><span class="sxs-lookup"><span data-stu-id="b7802-119">\<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*></span></span>  

<span data-ttu-id="b7802-120">Örnek:</span><span class="sxs-lookup"><span data-stu-id="b7802-120">For example:</span></span>  

```console
myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33
```  

<span data-ttu-id="b7802-121">Bu örnekte, `PublicKeyToken` ortak anahtar belirtecinin onaltılı biçimidir.</span><span class="sxs-lookup"><span data-stu-id="b7802-121">In this example, `PublicKeyToken` is the hexadecimal form of the public key token.</span></span> <span data-ttu-id="b7802-122">Kültür değeri yoksa kullanın `Culture=neutral` .</span><span class="sxs-lookup"><span data-stu-id="b7802-122">If there is no culture value, use `Culture=neutral`.</span></span>  

<span data-ttu-id="b7802-123">Aşağıdaki kod örneği, bu bilgileri yöntemiyle nasıl kullanacağınızı gösterir <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b7802-123">The following code example shows how to use this information with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  

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

<span data-ttu-id="b7802-124">Aşağıdaki [tanımlayıcı ad (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) komutunu kullanarak, belirli bir derleme için ortak anahtar ve ortak anahtar belirtecinin onaltılık biçimini yazdırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b7802-124">You can print the hexadecimal format of the public key and public key token for a specific assembly by using the following [Strong Name (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) command:</span></span>  

<span data-ttu-id="b7802-125">**sn-TP \<** *assembly* **>**</span><span class="sxs-lookup"><span data-stu-id="b7802-125">**sn -Tp \<** *assembly* **>**</span></span>  

<span data-ttu-id="b7802-126">Ortak anahtar dosyanız varsa, bunun yerine aşağıdaki komutu kullanabilirsiniz (komut satırı seçeneğinde büyük/küçük harf farkını aklınızda bulabilirsiniz):</span><span class="sxs-lookup"><span data-stu-id="b7802-126">If you have a public key file, you can use the following command instead (note the difference in case on the command-line option):</span></span>  

<span data-ttu-id="b7802-127">**sn-TP \<** *public key file* **>**</span><span class="sxs-lookup"><span data-stu-id="b7802-127">**sn -tp \<** *public key file* **>**</span></span>  

## <a name="see-also"></a><span data-ttu-id="b7802-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7802-128">See also</span></span>

- [<span data-ttu-id="b7802-129">Tanımlayıcı adlı derlemeler oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="b7802-129">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
