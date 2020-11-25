---
title: ISymUnmanagedScope::GetParent Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetParent
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetParent
helpviewer_keywords:
- GetParent method [.NET Framework debugging]
- ISymUnmanagedScope::GetParent method [.NET Framework debugging]
ms.assetid: c7963c87-6ec5-49b3-a5cd-e0fe0c43f9b4
topic_type:
- apiref
ms.openlocfilehash: db7fb5f2c1b5d1fa8be1328852ca4402538396f3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725904"
---
# <a name="isymunmanagedscopegetparent-method"></a><span data-ttu-id="08030-102">ISymUnmanagedScope::GetParent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08030-102">ISymUnmanagedScope::GetParent Method</span></span>

<span data-ttu-id="08030-103">Bu kapsamın üst kapsamını alır.</span><span class="sxs-lookup"><span data-stu-id="08030-103">Gets the parent scope of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08030-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="08030-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParent(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08030-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="08030-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="08030-106">dışı Döndürülen [ıdimunmanagedscope](isymunmanagedscope-interface.md) arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="08030-106">[out] A pointer to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08030-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="08030-107">Return Value</span></span>  

 <span data-ttu-id="08030-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="08030-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08030-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08030-109">Requirements</span></span>  

 <span data-ttu-id="08030-110">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="08030-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08030-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08030-111">See also</span></span>

- [<span data-ttu-id="08030-112">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08030-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="08030-113">GetChildren Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08030-113">GetChildren Method</span></span>](isymunmanagedscope-getchildren-method.md)
