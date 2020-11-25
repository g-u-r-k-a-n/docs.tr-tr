---
title: InitDbgTransportManager İşlevi
ms.date: 03/30/2017
api_name:
- InitDbgTransportManager
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- InitDbgTransportManager
helpviewer_keywords:
- remote debugging API [Silverlight]
- InitDbgTransportManager function
- Silverlight, remote debugging
ms.assetid: a30102ff-c52e-48c9-b3a9-aa14286a42b2
topic_type:
- apiref
ms.openlocfilehash: a5b4783eadb8045733b9ebd6d10c4e31f7829498
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716687"
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="cf6ef-102">InitDbgTransportManager İşlevi</span><span class="sxs-lookup"><span data-stu-id="cf6ef-102">InitDbgTransportManager Function</span></span>

<span data-ttu-id="cf6ef-103">İşlem ve çalışma zamanı numaralandırması için uzak hedefe bağlanmak üzere aktarım yöneticisini başlatır.</span><span class="sxs-lookup"><span data-stu-id="cf6ef-103">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf6ef-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="cf6ef-104">Syntax</span></span>  
  
```cpp  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="cf6ef-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cf6ef-105">Return Value</span></span>  

 <span data-ttu-id="cf6ef-106">S_OK</span><span class="sxs-lookup"><span data-stu-id="cf6ef-106">S_OK</span></span>  
 <span data-ttu-id="cf6ef-107">Başarılı.</span><span class="sxs-lookup"><span data-stu-id="cf6ef-107">Success.</span></span>  
  
 <span data-ttu-id="cf6ef-108">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="cf6ef-108">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="cf6ef-109">İşlev, bir taşıma yöneticisi için bellek ayıramadı.</span><span class="sxs-lookup"><span data-stu-id="cf6ef-109">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="cf6ef-110">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="cf6ef-110">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="cf6ef-111">Diğer sorunlar.</span><span class="sxs-lookup"><span data-stu-id="cf6ef-111">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf6ef-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf6ef-112">Requirements</span></span>  

 <span data-ttu-id="cf6ef-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf6ef-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf6ef-114">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="cf6ef-114">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="cf6ef-115">**Kitaplık:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="cf6ef-115">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="cf6ef-116">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="cf6ef-116">**.NET Framework Versions:** 3.5 SP1</span></span>
