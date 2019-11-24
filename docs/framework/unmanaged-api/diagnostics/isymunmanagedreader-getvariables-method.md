---
title: ISymUnmanagedReader::GetVariables Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetVariables
helpviewer_keywords:
- ISymUnmanagedReader::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 16dc49cb-2c60-4ac8-9c35-020e9afba3f8
topic_type:
- apiref
ms.openlocfilehash: 4590d2734ea89bc1bc8a30db1c7ecac5effafd7b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429749"
---
# <a name="isymunmanagedreadergetvariables-method"></a><span data-ttu-id="b429e-102">ISymUnmanagedReader::GetVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b429e-102">ISymUnmanagedReader::GetVariables Method</span></span>
<span data-ttu-id="b429e-103">Returns a non-local variable, given its parent and name.</span><span class="sxs-lookup"><span data-stu-id="b429e-103">Returns a non-local variable, given its parent and name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b429e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b429e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVariables (  
    [in]  mdToken  parent,  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is (cVars),  
        length_is (*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b429e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b429e-105">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="b429e-106">[in] The parent of the variable.</span><span class="sxs-lookup"><span data-stu-id="b429e-106">[in] The parent of the variable.</span></span>  
  
 `cVars`  
 <span data-ttu-id="b429e-107">[in] The size of the `pVars` array.</span><span class="sxs-lookup"><span data-stu-id="b429e-107">[in] The size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="b429e-108">[out] A pointer to the variable that receives the number of variables returned in `pVars`.</span><span class="sxs-lookup"><span data-stu-id="b429e-108">[out] A pointer to the variable that receives the number of variables returned in `pVars`.</span></span>  
  
 `pVars`  
 <span data-ttu-id="b429e-109">[out] A pointer to the variable that receives the variables.</span><span class="sxs-lookup"><span data-stu-id="b429e-109">[out] A pointer to the variable that receives the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b429e-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b429e-110">Return Value</span></span>  
 <span data-ttu-id="b429e-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="b429e-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b429e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b429e-112">Requirements</span></span>  
 <span data-ttu-id="b429e-113">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b429e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b429e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b429e-114">See also</span></span>

- [<span data-ttu-id="b429e-115">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b429e-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
