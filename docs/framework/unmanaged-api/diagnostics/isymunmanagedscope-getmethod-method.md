---
title: ISymUnmanagedScope::GetMethod Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetMethod method [.NET Framework debugging]
ms.assetid: a61866ee-221a-45b9-a1b7-395825b77872
topic_type:
- apiref
ms.openlocfilehash: 75d5638a6f01ba9569a03e5255a7217371c9d177
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725943"
---
# <a name="isymunmanagedscopegetmethod-method"></a><span data-ttu-id="6dd6f-102">ISymUnmanagedScope::GetMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6dd6f-102">ISymUnmanagedScope::GetMethod Method</span></span>

<span data-ttu-id="6dd6f-103">Bu kapsamı içeren yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="6dd6f-103">Gets the method that contains this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dd6f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6dd6f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethod(  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6dd6f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6dd6f-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="6dd6f-106">dışı Döndürülen [ıdimunmanagedmethod](isymunmanagedmethod-interface.md) arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6dd6f-106">[out] A pointer to the returned [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6dd6f-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6dd6f-107">Return Value</span></span>  

 <span data-ttu-id="6dd6f-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="6dd6f-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dd6f-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6dd6f-109">Requirements</span></span>  

 <span data-ttu-id="6dd6f-110">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="6dd6f-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dd6f-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6dd6f-111">See also</span></span>

- [<span data-ttu-id="6dd6f-112">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6dd6f-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
