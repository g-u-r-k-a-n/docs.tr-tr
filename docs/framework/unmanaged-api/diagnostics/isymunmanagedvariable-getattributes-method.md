---
title: ISymUnmanagedVariable::GetAttributes Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAttributes
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAttributes
helpviewer_keywords:
- GetAttributes method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAttributes method [.NET Framework debugging]
ms.assetid: 80f168af-a6a6-4c8f-b9e6-8a82dc834ed5
topic_type:
- apiref
ms.openlocfilehash: 1142dbb83693f6104ba6e22e174ce02fb92997a6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726905"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="c4e6a-102">ISymUnmanagedVariable::GetAttributes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4e6a-102">ISymUnmanagedVariable::GetAttributes Method</span></span>

<span data-ttu-id="c4e6a-103">Bu değişken için öznitelik bayraklarını alır.</span><span class="sxs-lookup"><span data-stu-id="c4e6a-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4e6a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c4e6a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4e6a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c4e6a-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="c4e6a-106">dışı Öznitelikleri alan öğesine yönelik bir işaretçi `ULONG32` .</span><span class="sxs-lookup"><span data-stu-id="c4e6a-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="c4e6a-107">Döndürülen değer [CorSymVarFlag](corsymvarflag-enumeration.md) numaralandırmasında tanımlanan değerlerden biri olacaktır.</span><span class="sxs-lookup"><span data-stu-id="c4e6a-107">The returned value will be one of the values defined in the [CorSymVarFlag](corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4e6a-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c4e6a-108">Return Value</span></span>  

 <span data-ttu-id="c4e6a-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="c4e6a-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4e6a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4e6a-110">Requirements</span></span>  

 <span data-ttu-id="c4e6a-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c4e6a-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4e6a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4e6a-112">See also</span></span>

- [<span data-ttu-id="c4e6a-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c4e6a-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
