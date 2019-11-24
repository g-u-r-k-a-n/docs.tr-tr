---
title: ISymENCUnmanagedMethod::GetLineFromOffset Yöntemi
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetLineFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type:
- apiref
ms.openlocfilehash: 94a571a4bc01b805387aebe5a6e23bad0b735313
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448644"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a><span data-ttu-id="4b81c-102">ISymENCUnmanagedMethod::GetLineFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b81c-102">ISymENCUnmanagedMethod::GetLineFromOffset Method</span></span>
<span data-ttu-id="4b81c-103">Gets the line information associated with an offset.</span><span class="sxs-lookup"><span data-stu-id="4b81c-103">Gets the line information associated with an offset.</span></span> <span data-ttu-id="4b81c-104">If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.</span><span class="sxs-lookup"><span data-stu-id="4b81c-104">If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b81c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4b81c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b81c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4b81c-106">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="4b81c-107">[in] A `ULONG32` that contains the offset.</span><span class="sxs-lookup"><span data-stu-id="4b81c-107">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `pline`  
 <span data-ttu-id="4b81c-108">[out] A pointer to a `ULONG32` that receives the line.</span><span class="sxs-lookup"><span data-stu-id="4b81c-108">[out] A pointer to a `ULONG32` that receives the line.</span></span>  
  
 `pcolumn`  
 <span data-ttu-id="4b81c-109">[out] A pointer to a `ULONG32` that receives the column.</span><span class="sxs-lookup"><span data-stu-id="4b81c-109">[out] A pointer to a `ULONG32` that receives the column.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="4b81c-110">[out] A pointer to a `ULONG32` that receives the end line.</span><span class="sxs-lookup"><span data-stu-id="4b81c-110">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
 `pendColumn`  
 <span data-ttu-id="4b81c-111">[out] A pointer to a `ULONG32` that receives the end column.</span><span class="sxs-lookup"><span data-stu-id="4b81c-111">[out] A pointer to a `ULONG32` that receives the end column.</span></span>  
  
 `pdwStartOffset`  
 <span data-ttu-id="4b81c-112">[out] A pointer to a `ULONG32` that receives the associated sequence point.</span><span class="sxs-lookup"><span data-stu-id="4b81c-112">[out] A pointer to a `ULONG32` that receives the associated sequence point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b81c-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4b81c-113">Return Value</span></span>  
 <span data-ttu-id="4b81c-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="4b81c-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b81c-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4b81c-115">Requirements</span></span>  
 <span data-ttu-id="4b81c-116">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4b81c-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b81c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b81c-117">See also</span></span>

- [<span data-ttu-id="4b81c-118">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b81c-118">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
