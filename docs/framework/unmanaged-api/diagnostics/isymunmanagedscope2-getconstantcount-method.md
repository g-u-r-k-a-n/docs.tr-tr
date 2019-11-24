---
title: ISymUnmanagedScope2::GetConstantCount Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstantCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstantCount
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstantCount method [.NET Framework debugging]
- GetConstantCount method [.NET Framework debugging]
ms.assetid: 1e1f0be6-c4e8-4d6c-98cd-d5fa9f686e87
topic_type:
- apiref
ms.openlocfilehash: f795147bdcd822db90106c7f2171eb1771b1126f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446247"
---
# <a name="isymunmanagedscope2getconstantcount-method"></a><span data-ttu-id="f0cf4-102">ISymUnmanagedScope2::GetConstantCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0cf4-102">ISymUnmanagedScope2::GetConstantCount Method</span></span>
<span data-ttu-id="f0cf4-103">Gets a count of the constants defined within this scope.</span><span class="sxs-lookup"><span data-stu-id="f0cf4-103">Gets a count of the constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0cf4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0cf4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConstantCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0cf4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f0cf4-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="f0cf4-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span><span class="sxs-lookup"><span data-stu-id="f0cf4-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0cf4-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f0cf4-107">Return Value</span></span>  
 <span data-ttu-id="f0cf4-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="f0cf4-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0cf4-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0cf4-109">Requirements</span></span>  
 <span data-ttu-id="f0cf4-110">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f0cf4-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0cf4-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0cf4-111">See also</span></span>

- [<span data-ttu-id="f0cf4-112">ISymUnmanagedScope2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0cf4-112">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
