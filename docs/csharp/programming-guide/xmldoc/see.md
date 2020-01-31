---
title: <see> C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: 17d1d344b9a27ffd4995fa4849ee6d5ce7f90f29
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789697"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="ccf63-102">\<bkz. >C# (Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ccf63-102">\<see> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="ccf63-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ccf63-103">Syntax</span></span>

```xml
<see cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="ccf63-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ccf63-104">Parameters</span></span>

- <span data-ttu-id="ccf63-105">cref = "`member`"</span><span class="sxs-lookup"><span data-stu-id="ccf63-105">cref = " `member`"</span></span>

  <span data-ttu-id="ccf63-106">Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="ccf63-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="ccf63-107">Derleyici verilen kod öğesinin var olduğunu denetler ve çıkış XML dosyasında öğe adına `member` geçirir.</span><span class="sxs-lookup"><span data-stu-id="ccf63-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="ccf63-108">*Üyeyi* çift tırnak işareti ("") içine koyun.</span><span class="sxs-lookup"><span data-stu-id="ccf63-108">Place *member* within double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="ccf63-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ccf63-109">Remarks</span></span>

<span data-ttu-id="ccf63-110">\<bkz. > etiketi, metnin içinden bir bağlantı belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ccf63-110">The \<see> tag lets you specify a link from within text.</span></span> <span data-ttu-id="ccf63-111">Metnin Ayrıca See de bir bölümüne yerleştirilmesi gerektiğini belirtmek için [\<see>](./seealso.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="ccf63-111">Use [\<seealso>](./seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="ccf63-112">Kod öğeleri için belge sayfalarına iç köprüler oluşturmak üzere [cref özniteliğini](./cref-attribute.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="ccf63-112">Use the [cref Attribute](./cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span>

<span data-ttu-id="ccf63-113">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="ccf63-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="ccf63-114">Aşağıdaki örnek bir Özet bölümü içinde bir \<> etiketini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ccf63-114">The following example shows a \<see> tag within a summary section.</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a><span data-ttu-id="ccf63-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ccf63-115">See also</span></span>

- [<span data-ttu-id="ccf63-116">C#Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ccf63-116">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="ccf63-117">Belge açıklamaları için önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="ccf63-117">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
