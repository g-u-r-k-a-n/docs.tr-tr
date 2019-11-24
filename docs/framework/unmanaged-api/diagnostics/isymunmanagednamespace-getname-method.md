---
title: ISymUnmanagedNamespace::GetName Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetName
helpviewer_keywords:
- ISymUnmanagedNamespace::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 657bf91d-005a-4ea4-9298-04d1291c0bc3
topic_type:
- apiref
ms.openlocfilehash: 43f32ac85bebc12d0a9253205aae3f1de0dc9e5b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433966"
---
# <a name="isymunmanagednamespacegetname-method"></a><span data-ttu-id="607dc-102">ISymUnmanagedNamespace::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="607dc-102">ISymUnmanagedNamespace::GetName Method</span></span>
<span data-ttu-id="607dc-103">Gets the name of this namespace.</span><span class="sxs-lookup"><span data-stu-id="607dc-103">Gets the name of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="607dc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="607dc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="607dc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="607dc-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="607dc-106">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="607dc-106">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="607dc-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span><span class="sxs-lookup"><span data-stu-id="607dc-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="607dc-108">[out] A pointer to a buffer that contains the namespace name.</span><span class="sxs-lookup"><span data-stu-id="607dc-108">[out] A pointer to a buffer that contains the namespace name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="607dc-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="607dc-109">Return Value</span></span>  
 <span data-ttu-id="607dc-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="607dc-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="607dc-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="607dc-111">Requirements</span></span>  
 <span data-ttu-id="607dc-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="607dc-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="607dc-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="607dc-113">See also</span></span>

- [<span data-ttu-id="607dc-114">ISymUnmanagedNamespace Arabirimi</span><span class="sxs-lookup"><span data-stu-id="607dc-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
