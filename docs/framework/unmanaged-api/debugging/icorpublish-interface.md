---
title: ICorPublish Arabirimi
ms.date: 03/30/2017
api_name:
- ICorPublish
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish
helpviewer_keywords:
- ICorPublish interface [.NET Framework debugging]
ms.assetid: 87c4fcb2-7703-4a2e-afb6-42973381b960
topic_type:
- apiref
ms.openlocfilehash: 3ff4efe8b3e2932da7f65246bf4ad614a4dd86cd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95694418"
---
# <a name="icorpublish-interface"></a><span data-ttu-id="cb89a-102">ICorPublish Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb89a-102">ICorPublish Interface</span></span>

<span data-ttu-id="cb89a-103">, Bu süreçlerdeki uygulama etki alanlarıyla ilgili süreçler ve bilgiler hakkında bilgi yayımlamak için genel arabirim görevi görür.</span><span class="sxs-lookup"><span data-stu-id="cb89a-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cb89a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cb89a-104">Methods</span></span>  
  
|<span data-ttu-id="cb89a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cb89a-105">Method</span></span>|<span data-ttu-id="cb89a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb89a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cb89a-107">EnumProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb89a-107">EnumProcesses Method</span></span>](icorpublish-enumprocesses-method.md)|<span data-ttu-id="cb89a-108">Bu bilgisayarda çalışan yönetilen işlemlerin bulunduğu bir [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="cb89a-108">Gets an [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="cb89a-109">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb89a-109">GetProcess Method</span></span>](icorpublish-getprocess-method.md)|<span data-ttu-id="cb89a-110">Belirtilen tanımlayıcıya sahip işlemi temsil eden bir [ICorPublishProcess](icorpublishprocess-interface.md) örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="cb89a-110">Gets an [ICorPublishProcess](icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cb89a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb89a-111">Requirements</span></span>  

 <span data-ttu-id="cb89a-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb89a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb89a-113">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="cb89a-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="cb89a-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cb89a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb89a-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb89a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb89a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb89a-116">See also</span></span>

- [<span data-ttu-id="cb89a-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cb89a-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="cb89a-118">CorpubPublish Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="cb89a-118">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
