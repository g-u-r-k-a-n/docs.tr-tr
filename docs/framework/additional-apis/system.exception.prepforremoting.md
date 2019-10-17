---
title: Exception. PrepForRemoting yöntemi (sistem)
author: mairaw
ms.author: mairaw
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: 057390d64f70d3cb8eba7d4b29b94570fdca77e3
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72405034"
---
# <a name="exceptionprepforremoting-method"></a><span data-ttu-id="5ab87-102">Exception.PrepForRemoting Metodu</span><span class="sxs-lookup"><span data-stu-id="5ab87-102">Exception.PrepForRemoting Method</span></span>

<span data-ttu-id="5ab87-103">Özel durum istemci çağrı sitesinde yeniden oluşturulmadan önce iletiye ekleyerek sunucu tarafı yığın izlemesini korur.</span><span class="sxs-lookup"><span data-stu-id="5ab87-103">Preserves the server-side stack trace by appending it to the message before the exception is rethrown at the client call site.</span></span>

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a><span data-ttu-id="5ab87-104">Döndürür</span><span class="sxs-lookup"><span data-stu-id="5ab87-104">Returns</span></span>

<xref:System.Exception>  
<span data-ttu-id="5ab87-105">Bu <xref:System.Exception> örneği.</span><span class="sxs-lookup"><span data-stu-id="5ab87-105">This <xref:System.Exception> instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ab87-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ab87-106">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="5ab87-107">@No__t-0 yöntemi dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5ab87-107">The `Exception.PrepForRemoting` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="5ab87-108">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="5ab87-108">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="5ab87-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ab87-109">Requirements</span></span>

<span data-ttu-id="5ab87-110">**Ad alanı:** <xref:System></span><span class="sxs-lookup"><span data-stu-id="5ab87-110">**Namespace:** <xref:System></span></span>

<span data-ttu-id="5ab87-111">**Bütünleştirilmiş kod:** mscorlib. dll (mscorlib. dll içinde)</span><span class="sxs-lookup"><span data-stu-id="5ab87-111">**Assembly:** mscorlib.dll (in mscorlib.dll)</span></span>

<span data-ttu-id="5ab87-112">**.NET Framework sürümleri:** 1,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5ab87-112">**.NET Framework versions:** Available since 1.0.</span></span>
