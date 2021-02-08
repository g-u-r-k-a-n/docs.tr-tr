---
description: ': ICorProfilerCallback:: RemotingServerReceivingMessage yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::RemotingServerReceivingMessage Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerReceivingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage method [.NET Framework profiling]
- RemotingServerReceivingMessage method [.NET Framework profiling]
ms.assetid: 5604d21f-e6b7-490e-b469-42122a7568e1
topic_type:
- apiref
ms.openlocfilehash: 5efa706d934158d09796dfab40b132a334c10ffd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788897"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a><span data-ttu-id="3b5b3-103">ICorProfilerCallback::RemotingServerReceivingMessage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3b5b3-103">ICorProfilerCallback::RemotingServerReceivingMessage Method</span></span>

<span data-ttu-id="3b5b3-104">Profil oluşturucuya işlemin bir uzak yöntem çağırma veya etkinleştirme isteği aldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="3b5b3-104">Notifies the profiler that the process has received a remote method invocation or activation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b5b3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b5b3-105">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b5b3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3b5b3-106">Parameters</span></span>  

 `pCookie`  
 <span data-ttu-id="3b5b3-107">'ndaki Şu koşullarda [ICorProfilerCallback:: RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md) içinde belirtilen değere karşılık gelen bir değer:</span><span class="sxs-lookup"><span data-stu-id="3b5b3-107">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="3b5b3-108">Uzaktan iletişim GUID tanımlama bilgileri etkin.</span><span class="sxs-lookup"><span data-stu-id="3b5b3-108">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="3b5b3-109">Kanal, iletiyi iletmede başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="3b5b3-109">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="3b5b3-110">GUID tanımlama bilgileri, istemci tarafı işleminde etkindir.</span><span class="sxs-lookup"><span data-stu-id="3b5b3-110">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="3b5b3-111">Bu, uzaktan iletişim çağrılarının ve mantıksal çağrı yığınının oluşturulmasına kolay bir şekilde eşleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b5b3-111">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="3b5b3-112">'ndaki `true` Çağrının zaman uyumsuz olduğu bir değer; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="3b5b3-112">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b5b3-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b5b3-113">Remarks</span></span>  

 <span data-ttu-id="3b5b3-114">İleti isteği zaman uyumsuz ise, istek herhangi bir rastgele iş parçacığı tarafından hizmet verebilir.</span><span class="sxs-lookup"><span data-stu-id="3b5b3-114">If the message request is asynchronous, the request can be serviced by any arbitrary thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b5b3-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3b5b3-115">Requirements</span></span>  

 <span data-ttu-id="3b5b3-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b5b3-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b5b3-117">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3b5b3-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3b5b3-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3b5b3-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b5b3-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b5b3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b5b3-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b5b3-120">See also</span></span>

- [<span data-ttu-id="3b5b3-121">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3b5b3-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
