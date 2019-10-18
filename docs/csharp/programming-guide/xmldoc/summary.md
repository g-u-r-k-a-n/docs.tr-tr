---
title: <summary> - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: f0e67ca248e5c94318032c8769410d4fd4c9d3a9
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523301"
---
# <a name="summary-c-programming-guide"></a><span data-ttu-id="1b556-102">\<summary > (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="1b556-102">\<summary> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="1b556-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b556-103">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b556-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1b556-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="1b556-105">Nesnenin Özeti.</span><span class="sxs-lookup"><span data-stu-id="1b556-105">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b556-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b556-106">Remarks</span></span>  
 <span data-ttu-id="1b556-107">@No__t_0summary > etiketi bir tür veya tür üyesini tanımlamakta kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1b556-107">The \<summary> tag should be used to describe a type or a type member.</span></span> <span data-ttu-id="1b556-108">Bir tür açıklamasına ek bilgi eklemek için [\<remarks >](./remarks.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="1b556-108">Use [\<remarks>](./remarks.md) to add supplemental information to a type description.</span></span> <span data-ttu-id="1b556-109">Kod öğeleri için belge sayfalarına iç köprüler oluşturmak üzere [Docfx](https://dotnet.github.io/docfx/) ve [sandrole](https://github.com/EWSoftware/SHFB) gibi belge araçlarını etkinleştirmek için [cref özniteliğini](./cref-attribute.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="1b556-109">Use the [cref Attribute](./cref-attribute.md) to enable documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="1b556-110">@No__t_0summary > etiketinin metni, IntelliSense 'deki türle ilgili tek bilgi kaynağıdır ve ayrıca Nesne Tarayıcısı penceresinde de görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1b556-110">The text for the \<summary> tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser Window.</span></span>  
  
 <span data-ttu-id="1b556-111">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="1b556-111">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span> <span data-ttu-id="1b556-112">Derleyici tarafından oluşturulan dosyayı temel alan son belgeleri oluşturmak için özel bir araç oluşturabilir veya [Docfx](https://dotnet.github.io/docfx/) veya [sandrole](https://github.com/EWSoftware/SHFB)gibi bir araç kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b556-112">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b556-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="1b556-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]  
  
 <span data-ttu-id="1b556-114">Önceki örnek aşağıdaki XML dosyasını üretir.</span><span class="sxs-lookup"><span data-stu-id="1b556-114">The previous example produces the following XML file.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:DotNetEvents.TestClass">  
            text for class TestClass  
        </member>  
        <member name="M:DotNetEvents.TestClass.DoWork(System.Int32)">  
            <summary>DoWork is a method in the TestClass class.  
            <para>Here's how you could make a second paragraph in a description. <see cref="M:System.Console.WriteLine(System.String)"/> for information about output statements.</para>  
            <seealso cref="M:DotNetEvents.TestClass.Main"/>  
            </summary>  
        </member>  
        <member name="M:DotNetEvents.TestClass.Main">  
            text for Main  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="example"></a><span data-ttu-id="1b556-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="1b556-115">Example</span></span>  
 <span data-ttu-id="1b556-116">Aşağıdaki örnek, genel bir türe `cref` başvurusunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b556-116">The following example shows how to make a `cref` reference to a generic type.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#11)]  
  
 <span data-ttu-id="1b556-117">Önceki örnek aşağıdaki XML dosyasını üretir.</span><span class="sxs-lookup"><span data-stu-id="1b556-117">The previous example produces the following XML file.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:ExtensionMethodsDemo1.A">  
            <summary cref="T:ExtensionMethodsDemo1.C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.B">  
            <summary cref="T:C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.C`1">  
            <summary cref="T:ExtensionMethodsDemo1.A">  
            </summary>  
            <typeparam name="T"></typeparam>  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1b556-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b556-118">See also</span></span>

- [<span data-ttu-id="1b556-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1b556-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1b556-120">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="1b556-120">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
