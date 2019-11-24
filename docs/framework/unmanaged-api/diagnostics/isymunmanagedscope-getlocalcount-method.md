---
title: ISymUnmanagedScope::GetLocalCount Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocalCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocalCount
helpviewer_keywords:
- GetLocalCount method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocalCount method [.NET Framework debugging]
ms.assetid: 3ede8fb5-f655-4088-8e19-9c53812588a8
topic_type:
- apiref
ms.openlocfilehash: 3b5dbe875b47f48c24c5e955abddb2c6f778bcdd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446344"
---
# <a name="isymunmanagedscopegetlocalcount-method"></a><span data-ttu-id="feafe-102">ISymUnmanagedScope::GetLocalCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="feafe-102">ISymUnmanagedScope::GetLocalCount Method</span></span>
<span data-ttu-id="feafe-103">Gets a count of the local variables defined within this scope.</span><span class="sxs-lookup"><span data-stu-id="feafe-103">Gets a count of the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="feafe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="feafe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="feafe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="feafe-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="feafe-106">[out] A pointer to a `ULONG32` that receives the count of local variables.</span><span class="sxs-lookup"><span data-stu-id="feafe-106">[out] A pointer to a `ULONG32` that receives the count of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="feafe-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="feafe-107">Return Value</span></span>  
 <span data-ttu-id="feafe-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="feafe-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="feafe-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="feafe-109">Requirements</span></span>  
 <span data-ttu-id="feafe-110">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="feafe-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feafe-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="feafe-111">See also</span></span>

- [<span data-ttu-id="feafe-112">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="feafe-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
