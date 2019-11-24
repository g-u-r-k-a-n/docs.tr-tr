---
title: ISymUnmanagedWriter2::DefineConstant2 Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineConstant2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineConstant2
helpviewer_keywords:
- DefineConstant2 method [.NET Framework debugging]
- ISymUnmanagedWriter2::DefineConstant2 method [.NET Framework debugging]
ms.assetid: dd2bc956-7dbe-49fc-a646-daa0d267f2df
topic_type:
- apiref
ms.openlocfilehash: 6600ca7e70ac77ffba0c75812f27d388c354ece6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438323"
---
# <a name="isymunmanagedwriter2defineconstant2-method"></a><span data-ttu-id="6b3b9-102">ISymUnmanagedWriter2::DefineConstant2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6b3b9-102">ISymUnmanagedWriter2::DefineConstant2 Method</span></span>
<span data-ttu-id="6b3b9-103">Defines a name for a constant value.</span><span class="sxs-lookup"><span data-stu-id="6b3b9-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b3b9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b3b9-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant2(  
    [in] const WCHAR  *name,  
    [in] VARIANT      value,  
    [in] mdSignature  sigToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b3b9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6b3b9-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="6b3b9-106">[in] The constant name.</span><span class="sxs-lookup"><span data-stu-id="6b3b9-106">[in] The constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="6b3b9-107">[in] The value of the constant.</span><span class="sxs-lookup"><span data-stu-id="6b3b9-107">[in] The value of the constant.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="6b3b9-108">[in] The metadata token of the constant.</span><span class="sxs-lookup"><span data-stu-id="6b3b9-108">[in] The metadata token of the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b3b9-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6b3b9-109">Return Value</span></span>  
 <span data-ttu-id="6b3b9-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="6b3b9-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b3b9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6b3b9-111">Requirements</span></span>  
 <span data-ttu-id="6b3b9-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6b3b9-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b3b9-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b3b9-113">See also</span></span>

- [<span data-ttu-id="6b3b9-114">ISymUnmanagedWriter2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6b3b9-114">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="6b3b9-115">DefineConstant Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6b3b9-115">DefineConstant Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)
