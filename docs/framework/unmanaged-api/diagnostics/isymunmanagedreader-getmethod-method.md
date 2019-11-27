---
title: ISymUnmanagedReader::GetMethod Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedReader interface [.NET Framework debugging]
- ISymUnmanagedReader::GetMethod method [.NET Framework debugging]
ms.assetid: ae6cfb29-bc2c-4606-af86-1d32ebd31020
topic_type:
- apiref
ms.openlocfilehash: 9407942b81c5318509f2b026fa5db1cdd163e02d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448283"
---
# <a name="isymunmanagedreadergetmethod-method"></a><span data-ttu-id="1804d-102">ISymUnmanagedReader::GetMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1804d-102">ISymUnmanagedReader::GetMethod Method</span></span>
<span data-ttu-id="1804d-103">Yöntem belirteci verilen bir sembol okuyucu yöntemini alır.</span><span class="sxs-lookup"><span data-stu-id="1804d-103">Gets a symbol reader method, given a method token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1804d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1804d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethod (  
    [in]  mdMethodDef  token,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1804d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1804d-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="1804d-106">'ndaki Yöntem belirteci.</span><span class="sxs-lookup"><span data-stu-id="1804d-106">[in] The method token.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="1804d-107">dışı Döndürülen arabirime yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1804d-107">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1804d-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1804d-108">Return Value</span></span>  
 <span data-ttu-id="1804d-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="1804d-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1804d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1804d-110">Requirements</span></span>  
 <span data-ttu-id="1804d-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1804d-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1804d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1804d-112">See also</span></span>

- [<span data-ttu-id="1804d-113">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1804d-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
