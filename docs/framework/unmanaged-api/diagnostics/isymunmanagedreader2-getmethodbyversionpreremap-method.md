---
title: ISymUnmanagedReader2::GetMethodByVersionPreRemap Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodByVersionPreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodByVersionPreRemap
helpviewer_keywords:
- GetMethodByVersionPreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetMethodByVersionPreRemap method [.NET Framework debugging]
ms.assetid: 0d144ed4-bdb0-4cac-960c-cb90f4dca173
topic_type:
- apiref
ms.openlocfilehash: 2063856389b122b150a2d2744169a4a567592287
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446441"
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a><span data-ttu-id="09e4d-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap Metodu</span><span class="sxs-lookup"><span data-stu-id="09e4d-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap Method</span></span>
<span data-ttu-id="09e4d-103">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span><span class="sxs-lookup"><span data-stu-id="09e4d-103">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span></span> <span data-ttu-id="09e4d-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span><span class="sxs-lookup"><span data-stu-id="09e4d-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09e4d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="09e4d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09e4d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="09e4d-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="09e4d-107">[in] The method metadata token.</span><span class="sxs-lookup"><span data-stu-id="09e4d-107">[in] The method metadata token.</span></span>  
  
 `version`  
 <span data-ttu-id="09e4d-108">[in] The method version.</span><span class="sxs-lookup"><span data-stu-id="09e4d-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="09e4d-109">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="09e4d-109">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09e4d-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="09e4d-110">Return Value</span></span>  
 <span data-ttu-id="09e4d-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="09e4d-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09e4d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="09e4d-112">Requirements</span></span>  
 <span data-ttu-id="09e4d-113">**Header:** CorSym.idl.</span><span class="sxs-lookup"><span data-stu-id="09e4d-113">**Header:** CorSym.idl.</span></span> <span data-ttu-id="09e4d-114">CorSym.h</span><span class="sxs-lookup"><span data-stu-id="09e4d-114">CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09e4d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09e4d-115">See also</span></span>

- [<span data-ttu-id="09e4d-116">ISymUnmanagedReader2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="09e4d-116">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
