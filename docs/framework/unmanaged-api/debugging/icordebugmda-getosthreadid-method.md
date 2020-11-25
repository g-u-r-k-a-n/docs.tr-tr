---
title: ICorDebugMDA::GetOSThreadId Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetOSThreadId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetOSThreadId
helpviewer_keywords:
- ICorDebugMDA::GetOSThreadId method [.NET Framework debugging]
- GetOSThreadId method [.NET Framework debugging]
ms.assetid: 7ca7c364-ade4-4219-b434-9f6ae2359be6
topic_type:
- apiref
ms.openlocfilehash: 80248bba6d11b8af07aa0517cb41c8a4f783b5e0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710902"
---
# <a name="icordebugmdagetosthreadid-method"></a><span data-ttu-id="331fa-102">ICorDebugMDA::GetOSThreadId Metodu</span><span class="sxs-lookup"><span data-stu-id="331fa-102">ICorDebugMDA::GetOSThreadId Method</span></span>

<span data-ttu-id="331fa-103">[ICorDebugMDA](icordebugmda-interface.md) tarafından temsil edilen yönetilen hata ayıklama Yardımcısı (MDA) ' nin yürütüldüğü işletim SISTEMI (OS) iş parçacığı tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="331fa-103">Gets the operating system (OS) thread identifier upon which the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md) is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="331fa-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="331fa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="331fa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="331fa-105">Parameters</span></span>  

 `pOsTid`  
 <span data-ttu-id="331fa-106">dışı İşletim sistemi iş parçacığı tanımlayıcısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="331fa-106">[out] A pointer to the OS thread identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="331fa-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="331fa-107">Remarks</span></span>  

 <span data-ttu-id="331fa-108">İşletim sistemi iş parçacığı bir ICorDebugThread yerine, bir MDA 'ın yerel bir iş parçacığında ya da henüz yönetilen kodu girilmemiş yönetilen bir iş parçacığında tetiklenme durumlarına izin vermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="331fa-108">The OS thread is used instead of an ICorDebugThread to allow for situations in which an MDA is fired either on a native thread or on a managed thread that has not yet entered managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="331fa-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="331fa-109">Requirements</span></span>  

 <span data-ttu-id="331fa-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="331fa-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="331fa-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="331fa-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="331fa-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="331fa-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="331fa-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="331fa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="331fa-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="331fa-114">See also</span></span>

- [<span data-ttu-id="331fa-115">ICorDebugMDA Arabirimi</span><span class="sxs-lookup"><span data-stu-id="331fa-115">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="331fa-116">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="331fa-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
