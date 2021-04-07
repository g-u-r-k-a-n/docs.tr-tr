---
description: Başvuru türleri-C# başvurusu
title: Başvuru türleri-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: ab8eb426a3f65fd2c59920e6baa9a67bdccad82c
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498561"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="1e210-103">Başvuru türleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1e210-103">Reference types (C# Reference)</span></span>

<span data-ttu-id="1e210-104">C#'de iki çeşit tür vardır: başvuru türleri ve değer türleri.</span><span class="sxs-lookup"><span data-stu-id="1e210-104">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="1e210-105">Başvuru türlerinin değişkenleri başvuruları kendi verilerine (nesneler) depolarken, değer türlerinin değişkenleri kendi verilerini doğrudan içerir.</span><span class="sxs-lookup"><span data-stu-id="1e210-105">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="1e210-106">Başvuru türleri ile, iki değişken aynı nesneye başvurabilir; bu nedenle, bir değişken üzerinde yapılan işlemler diğer değişkenin başvurduğu nesneyi etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="1e210-106">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="1e210-107">Değer türleriyle, her değişken kendi verilerinin kopyasına sahiptir ve bir değişkende diğer işlemler (ın, ref ve out parametre değişkenleri hariç) için bir değişken üzerinde işlemler yapılamaz; bkz. [ın](in-parameter-modifier.md), [ref](ref.md) ve [Out](out-parameter-modifier.md) parametre değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="1e210-107">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](in-parameter-modifier.md), [ref](ref.md) and [out](out-parameter-modifier.md) parameter modifier).</span></span>

 <span data-ttu-id="1e210-108">Aşağıdaki anahtar sözcükler, başvuru türlerini bildirmek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="1e210-108">The following keywords are used to declare reference types:</span></span>

- [<span data-ttu-id="1e210-109">sınıfı</span><span class="sxs-lookup"><span data-stu-id="1e210-109">class</span></span>](class.md)

- [<span data-ttu-id="1e210-110">arayüz</span><span class="sxs-lookup"><span data-stu-id="1e210-110">interface</span></span>](interface.md)

- [<span data-ttu-id="1e210-111">ğini</span><span class="sxs-lookup"><span data-stu-id="1e210-111">delegate</span></span>](../builtin-types/reference-types.md)
- [<span data-ttu-id="1e210-112">kayıtlar</span><span class="sxs-lookup"><span data-stu-id="1e210-112">record</span></span>](../builtin-types/reference-types.md)

 <span data-ttu-id="1e210-113">C# ayrıca aşağıdaki yerleşik başvuru türlerini de sağlar:</span><span class="sxs-lookup"><span data-stu-id="1e210-113">C# also provides the following built-in reference types:</span></span>

- [<span data-ttu-id="1e210-114">dynamic</span><span class="sxs-lookup"><span data-stu-id="1e210-114">dynamic</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="1e210-115">nesne</span><span class="sxs-lookup"><span data-stu-id="1e210-115">object</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="1e210-116">string</span><span class="sxs-lookup"><span data-stu-id="1e210-116">string</span></span>](../builtin-types/reference-types.md)

## <a name="see-also"></a><span data-ttu-id="1e210-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e210-117">See also</span></span>

- [<span data-ttu-id="1e210-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="1e210-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1e210-119">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="1e210-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1e210-120">İşaretçi türleri</span><span class="sxs-lookup"><span data-stu-id="1e210-120">Pointer types</span></span>](../unsafe-code.md#pointer-types)
- [<span data-ttu-id="1e210-121">Değer türleri</span><span class="sxs-lookup"><span data-stu-id="1e210-121">Value types</span></span>](../builtin-types/value-types.md)
