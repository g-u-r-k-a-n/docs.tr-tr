---
title: INotifySource2::SetNotifyFilter Yöntemi
ms.date: 03/30/2017
api_name:
- INotifySource2.SetNotifyFilter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySource2::SetNotifyFilter
helpviewer_keywords:
- INotifySource2::SetNotifyFilter method [.NET Framework debugging]
- SetNotifyFilter method [.NET Framework debugging]
ms.assetid: 6351fc92-b126-4af6-9bf3-0a8ce92845fc
topic_type:
- apiref
ms.openlocfilehash: 99bce831405d722f1f1ca0ae56e60f95f2d905e8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719937"
---
# <a name="inotifysource2setnotifyfilter-method"></a><span data-ttu-id="6e4ec-102">INotifySource2::SetNotifyFilter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e4ec-102">INotifySource2::SetNotifyFilter Method</span></span>

<span data-ttu-id="6e4ec-103">Bu kaynakla kullanılmak üzere bir bildirim filtresi atar.</span><span class="sxs-lookup"><span data-stu-id="6e4ec-103">Assigns a notification filter for use with this source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e4ec-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6e4ec-104">Syntax</span></span>  
  
```cpp  
HRESULT SetNotifyFilter  
(  
    [in]  NOTIFY_FILTER   in_NotifyFilter,  
    [in]  USER_THREAD*    in_pUserThreadFilter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e4ec-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6e4ec-105">Parameters</span></span>  

 `in_NotifyFilter`  
 <span data-ttu-id="6e4ec-106">'ndaki Hata ayıklayıcı API 'SI için geri çağırmaları tanımlayan [NOTIFY_FILTER](notify-filter-enumeration.md) numaralandırma değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="6e4ec-106">[in] A bitwise combination of the [NOTIFY_FILTER](notify-filter-enumeration.md) enumeration values that identify callbacks for the debugger API.</span></span>  
  
 `in_pUserThreadFilter`  
 <span data-ttu-id="6e4ec-107">'ndaki Hata ayıklayıcı API 'SI için iş parçacıklarını tanımlayan [USER_THREAD](user-thread-structure.md) yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6e4ec-107">[in] A pointer to a [USER_THREAD](user-thread-structure.md) structure that identifies threads for the debugger API.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e4ec-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6e4ec-108">Return Value</span></span>  

 <span data-ttu-id="6e4ec-109">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="6e4ec-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e4ec-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e4ec-110">Requirements</span></span>  

 <span data-ttu-id="6e4ec-111">**Üst bilgi:** ProtocolNotify2. IDL</span><span class="sxs-lookup"><span data-stu-id="6e4ec-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e4ec-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e4ec-112">See also</span></span>

- [<span data-ttu-id="6e4ec-113">INotifySource2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e4ec-113">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="6e4ec-114">INotifyConnection2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e4ec-114">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="6e4ec-115">INotifySink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e4ec-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
