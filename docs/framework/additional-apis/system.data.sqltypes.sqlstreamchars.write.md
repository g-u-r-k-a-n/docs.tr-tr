---
title: SqlStreamChars. Write (Char [], Int32, Int32) yöntemi (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Write
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 9d952041122ceb3824712bd81cab7ce4789c9db8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395582"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a><span data-ttu-id="0a859-102">SqlStreamChars. Write (Char [], Int32, Int32) yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a859-102">SqlStreamChars.Write(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="0a859-103">Türetilmiş bir sınıfta geçersiz kılınırsa, geçerli akışa bir karakter dizisi yazar ve yazılan karakter sayısına göre bu akış içindeki geçerli konumu ilerletir.</span><span class="sxs-lookup"><span data-stu-id="0a859-103">When overridden in a derived class, writes a sequence of characters to the current stream and advances the current position within this stream by the number of characters written.</span></span> <span data-ttu-id="0a859-104">Bu yöntemi içeren derlemenin SQLAccess. dll ile bir arkadaş ilişkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="0a859-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="0a859-105">SQL Server tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0a859-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="0a859-106">Diğer veritabanları için, bu veritabanı tarafından sunulan barındırma mekanizmasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="0a859-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="0a859-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0a859-107">Parameters</span></span>

`buffer`  
<span data-ttu-id="0a859-108">Yazılacak bir Char dizisi.</span><span class="sxs-lookup"><span data-stu-id="0a859-108">A char array to write.</span></span>

`offset`  
<span data-ttu-id="0a859-109">Kaynağa göre bir göreli konum.</span><span class="sxs-lookup"><span data-stu-id="0a859-109">An offset relative to origin.</span></span>

`count`  
<span data-ttu-id="0a859-110">Geçerli akışa yazılacak karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="0a859-110">The number of characters to be written to the current stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="0a859-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0a859-111">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="0a859-112">@No__t-0 Yöntemi özeldir ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0a859-112">The `SqlStreamChars.Write` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="0a859-113">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında yazma kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0a859-113">Microsoft does not support the use of this method write in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="0a859-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a859-114">Requirements</span></span>

<span data-ttu-id="0a859-115">**Ad alanı:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="0a859-115">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="0a859-116">**Bütünleştirilmiş kod:** System. Data (System. Data. dll dosyasında)</span><span class="sxs-lookup"><span data-stu-id="0a859-116">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="0a859-117">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0a859-117">**.NET Framework versions:** Available since 2.0.</span></span>
