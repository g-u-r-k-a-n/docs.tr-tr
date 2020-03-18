---
title: <value> - C# programlama kılavuzu
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 120805346672738e614743ab8c98388b8dbac0f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793347"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="d03b4-102">\<değer> (C# programlama kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="d03b4-102">\<value> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="d03b4-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d03b4-103">Syntax</span></span>

```xml
<value>property-description</value>
```

## <a name="parameters"></a><span data-ttu-id="d03b4-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d03b4-104">Parameters</span></span>

- `property-description`

  <span data-ttu-id="d03b4-105">Mülk için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="d03b4-105">A description for the property.</span></span>

## <a name="remarks"></a><span data-ttu-id="d03b4-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d03b4-106">Remarks</span></span>

<span data-ttu-id="d03b4-107">Etiket \<> değer, bir özelliğin temsil ettiği değeri açıklamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d03b4-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="d03b4-108">Visual Studio .NET geliştirme ortamında kod sihirbazı aracılığıyla bir özellik eklediğinizde, yeni özellik için [ \<bir özet>](./summary.md) etiketi ekleyeceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d03b4-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="d03b4-109">Daha sonra, özelliğin \<temsil ettiği değeri açıklamak için el ile bir değer> etiketi eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d03b4-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>

<span data-ttu-id="d03b4-110">Belge yorumlarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derle.</span><span class="sxs-lookup"><span data-stu-id="d03b4-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="d03b4-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="d03b4-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a><span data-ttu-id="d03b4-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d03b4-112">See also</span></span>

- [<span data-ttu-id="d03b4-113">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d03b4-113">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="d03b4-114">Belge açıklamaları için önerilen etiketler</span><span class="sxs-lookup"><span data-stu-id="d03b4-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
