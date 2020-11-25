---
title: ISymUnmanagedVariable::GetAddressField1 Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField1
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField1
helpviewer_keywords:
- GetAddressField1 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField1 method [.NET Framework debugging]
ms.assetid: 25788ed1-0ce3-4b97-96fc-88f8997812a3
topic_type:
- apiref
ms.openlocfilehash: e3ea3c0fd65750d52c0cfb10edbe18b1512f724b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729024"
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="2b25a-102">ISymUnmanagedVariable::GetAddressField1 Metodu</span><span class="sxs-lookup"><span data-stu-id="2b25a-102">ISymUnmanagedVariable::GetAddressField1 Method</span></span>

<span data-ttu-id="2b25a-103">Bu değişken için ilk adres alanını alır.</span><span class="sxs-lookup"><span data-stu-id="2b25a-103">Gets the first address field for this variable.</span></span> <span data-ttu-id="2b25a-104">Bunun anlamı, adresin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2b25a-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b25a-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2b25a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b25a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2b25a-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="2b25a-107">dışı `ULONG32` İlk adres alanını alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="2b25a-107">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b25a-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2b25a-108">Return Value</span></span>  

 <span data-ttu-id="2b25a-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="2b25a-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b25a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2b25a-110">Requirements</span></span>  

 <span data-ttu-id="2b25a-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2b25a-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b25a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b25a-112">See also</span></span>

- [<span data-ttu-id="2b25a-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2b25a-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="2b25a-114">GetAddressField2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2b25a-114">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="2b25a-115">GetAddressField3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2b25a-115">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="2b25a-116">GetAddressKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2b25a-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
