---
title: Aralık değişkeni adı ancak bağımsız değişken içermeyen bir basit veya tam addan gösterilebilir
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: 63990b7d37388057ff2cdb430d29878a1c7b39ba
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162368"
---
# <a name="bc36599-range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="5b025-102">BC36599: Range değişken adı yalnızca bağımsız değişken içermeyen basit veya tam bir addan çıkarsanamıyor</span><span class="sxs-lookup"><span data-stu-id="5b025-102">BC36599: Range variable name can be inferred only from a simple or qualified name with no arguments</span></span>

<span data-ttu-id="5b025-103">Bir veya daha fazla bağımsız değişken alan bir programlama öğesi bir LINQ sorgusuna dahildir.</span><span class="sxs-lookup"><span data-stu-id="5b025-103">A programming element that takes one or more arguments is included in a LINQ query.</span></span> <span data-ttu-id="5b025-104">Derleyici, bu programlama öğesinden bir Aralık değişkeni çıkarsanamıyor.</span><span class="sxs-lookup"><span data-stu-id="5b025-104">The compiler is unable to infer a range variable from that programming element.</span></span>

<span data-ttu-id="5b025-105">**Hata kimliği:** BC36599</span><span class="sxs-lookup"><span data-stu-id="5b025-105">**Error ID:** BC36599</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="5b025-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="5b025-106">To correct this error</span></span>

<span data-ttu-id="5b025-107">Aşağıdaki kodda gösterildiği gibi, programlama öğesi için açık bir değişken adı sağlayın:</span><span class="sxs-lookup"><span data-stu-id="5b025-107">Supply an explicit variable name for the programming element, as shown in the following code:</span></span>

```vb
Dim query = From var1 In collection1
            Select VariableAlias= SampleFunction(var1), var1
```

## <a name="see-also"></a><span data-ttu-id="5b025-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b025-108">See also</span></span>

- [<span data-ttu-id="5b025-109">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="5b025-109">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="5b025-110">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="5b025-110">Select Clause</span></span>](../queries/select-clause.md)
