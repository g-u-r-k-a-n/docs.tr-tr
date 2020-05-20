---
title: ISymUnmanagedMethod::GetToken Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetToken
helpviewer_keywords:
- ISymUnmanagedMethod::GetToken method [.NET Framework debugging]
- GetToken method, ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: 4effbe95-c36e-4a45-8b2a-ee21339415fb
topic_type:
- apiref
ms.openlocfilehash: 0803f0b55f19b779f5b6608a9f8200d2b085b504
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615163"
---
# <a name="isymunmanagedmethodgettoken-method"></a><span data-ttu-id="1c12d-102">ISymUnmanagedMethod::GetToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c12d-102">ISymUnmanagedMethod::GetToken Method</span></span>
<span data-ttu-id="1c12d-103">Bu yöntem için meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="1c12d-103">Returns the metadata token for this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c12d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1c12d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
   [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c12d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1c12d-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="1c12d-106">dışı `mdMethodDef`Meta verileri içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1c12d-106">[out] A pointer to a `mdMethodDef` that receives the size, in characters, of the buffer required to contain the metadata.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c12d-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1c12d-107">Return Value</span></span>  
 <span data-ttu-id="1c12d-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="1c12d-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c12d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1c12d-109">Requirements</span></span>  
 <span data-ttu-id="1c12d-110">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1c12d-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c12d-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c12d-111">See also</span></span>

- [<span data-ttu-id="1c12d-112">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c12d-112">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
