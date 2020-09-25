---
description: '#Uyarı-C# başvurusu'
title: '#Uyarı-C# başvurusu'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 9ade723bdca17597dcd56240f506e60f2debf6be
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186425"
---
# <a name="warning-c-reference"></a><span data-ttu-id="52022-103">#warning (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="52022-103">#warning (C# Reference)</span></span>

<span data-ttu-id="52022-104">`#warning` kodunuzda belirli bir konumdan bir [CS1030](../../misc/cs1030.md) düzeyinde bir derleyici uyarısı oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="52022-104">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="52022-105">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="52022-105">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="52022-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52022-106">Remarks</span></span>

 <span data-ttu-id="52022-107">Öğesinin yaygın kullanımı `#warning` koşullu bir yönergedir.</span><span class="sxs-lookup"><span data-stu-id="52022-107">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="52022-108">[#Error](./preprocessor-error.md)ile Kullanıcı tanımlı bir hata oluşturmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="52022-108">It is also possible to generate a user-defined error with [#error](./preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="52022-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="52022-109">Example</span></span>  

```csharp
// preprocessor_warning.cs  
// CS1030 expected  
#define DEBUG  
class MainClass
{  
    static void Main()
    {  
#if DEBUG  
#warning DEBUG is defined  
#endif  
    }  
}  
```  

## <a name="see-also"></a><span data-ttu-id="52022-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52022-110">See also</span></span>

- [<span data-ttu-id="52022-111">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="52022-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="52022-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="52022-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="52022-113">C# Önişlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="52022-113">C# Preprocessor Directives</span></span>](./index.md)
