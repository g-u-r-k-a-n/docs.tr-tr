---
title: ISymUnmanagedWriter::OpenScope Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenScope
helpviewer_keywords:
- OpenScope method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::OpenScope method [.NET Framework debugging]
ms.assetid: dbea0644-3873-4329-90b8-624163e87467
topic_type:
- apiref
ms.openlocfilehash: 915b05d0d2ac611678fdcc94dd42bbb1962e6ceb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427901"
---
# <a name="isymunmanagedwriteropenscope-method"></a><span data-ttu-id="fb908-102">ISymUnmanagedWriter::OpenScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fb908-102">ISymUnmanagedWriter::OpenScope Method</span></span>
<span data-ttu-id="fb908-103">Opens a new lexical scope in the current method.</span><span class="sxs-lookup"><span data-stu-id="fb908-103">Opens a new lexical scope in the current method.</span></span> <span data-ttu-id="fb908-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span><span class="sxs-lookup"><span data-stu-id="fb908-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="fb908-105">Scopes must form a hierarchy.</span><span class="sxs-lookup"><span data-stu-id="fb908-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="fb908-106">Siblings are not allowed to overlap.</span><span class="sxs-lookup"><span data-stu-id="fb908-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb908-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb908-107">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb908-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fb908-108">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="fb908-109">[in] The offset of the first instruction in the lexical scope, in bytes, from the beginning of the method.</span><span class="sxs-lookup"><span data-stu-id="fb908-109">[in] The offset of the first instruction in the lexical scope, in bytes, from the beginning of the method.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="fb908-110">[out] A pointer to a `ULONG32` that receives the scope identifier.</span><span class="sxs-lookup"><span data-stu-id="fb908-110">[out] A pointer to a `ULONG32` that receives the scope identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb908-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fb908-111">Return Value</span></span>  
 <span data-ttu-id="fb908-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="fb908-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb908-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fb908-113">Remarks</span></span>  
 <span data-ttu-id="fb908-114">`ISymUnmanagedWriter::OpenScope` returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to define a scope's starting and ending offset at a later time.</span><span class="sxs-lookup"><span data-stu-id="fb908-114">`ISymUnmanagedWriter::OpenScope` returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="fb908-115">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span><span class="sxs-lookup"><span data-stu-id="fb908-115">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="fb908-116">Scope identifiers are valid only in the current method.</span><span class="sxs-lookup"><span data-stu-id="fb908-116">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb908-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fb908-117">Requirements</span></span>  
 <span data-ttu-id="fb908-118">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fb908-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb908-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb908-119">See also</span></span>

- [<span data-ttu-id="fb908-120">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb908-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
