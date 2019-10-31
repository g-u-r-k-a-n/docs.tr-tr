---
title: ISymUnmanagedAsyncMethod::GetKickoffMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
ms.openlocfilehash: 58daec30b4cbae9cfaab27d4ce76521ba839cf83
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139838"
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="56dcb-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56dcb-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="56dcb-103">Bkz. [DefineKickoffMethod Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="56dcb-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56dcb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56dcb-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56dcb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="56dcb-105">Parameters</span></span>  
  
|<span data-ttu-id="56dcb-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="56dcb-106">Parameter</span></span>|<span data-ttu-id="56dcb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56dcb-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="56dcb-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="56dcb-108">Return Value</span></span>  
 <span data-ttu-id="56dcb-109">`HRESULT`döndürür.</span><span class="sxs-lookup"><span data-stu-id="56dcb-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56dcb-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="56dcb-110">Requirements</span></span>  
 <span data-ttu-id="56dcb-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="56dcb-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56dcb-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56dcb-112">See also</span></span>

- [<span data-ttu-id="56dcb-113">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="56dcb-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
