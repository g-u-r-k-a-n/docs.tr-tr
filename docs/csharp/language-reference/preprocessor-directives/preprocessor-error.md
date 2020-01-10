---
title: '#hata- C# başvuru'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 7203e1271da66e78bfbd70717b0f5e536a7ebd86
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712526"
---
# <a name="error-c-reference"></a><span data-ttu-id="e8b38-102">#error (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e8b38-102">#error (C# Reference)</span></span>
<span data-ttu-id="e8b38-103">`#error`, kodunuzda belirli bir konumdan [CS1029](../compiler-messages/cs1029.md) Kullanıcı tanımlı bir hata oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8b38-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="e8b38-104">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e8b38-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="e8b38-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e8b38-105">Remarks</span></span>  
 <span data-ttu-id="e8b38-106">`#error` ortak bir kullanımı koşullu yönergedir.</span><span class="sxs-lookup"><span data-stu-id="e8b38-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="e8b38-107">[#Warning](./preprocessor-warning.md)ile Kullanıcı tanımlı bir uyarı oluşturmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="e8b38-107">It is also possible to generate a user-defined warning with [#warning](./preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8b38-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="e8b38-108">Example</span></span>  
  
```csharp
// preprocessor_error.cs  
// CS1029 expected  
#define DEBUG  
class MainClass   
{  
    static void Main()   
    {  
#if DEBUG  
#error DEBUG is defined  
#endif  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e8b38-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8b38-109">See also</span></span>

- [<span data-ttu-id="e8b38-110">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="e8b38-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e8b38-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e8b38-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e8b38-112">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e8b38-112">C# Preprocessor Directives</span></span>](./index.md)
