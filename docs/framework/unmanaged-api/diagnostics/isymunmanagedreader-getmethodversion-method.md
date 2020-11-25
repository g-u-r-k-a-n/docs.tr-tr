---
title: ISymUnmanagedReader::GetMethodVersion Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodVersion
helpviewer_keywords:
- GetMethodVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodVersion method [.NET Framework debugging]
ms.assetid: d6f9ac84-302a-4f5e-b990-e76f4269fceb
topic_type:
- apiref
ms.openlocfilehash: b0590f93c6a4c5ef28e03fc909c1f6a1474e5fad
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720613"
---
# <a name="isymunmanagedreadergetmethodversion-method"></a><span data-ttu-id="96d46-102">ISymUnmanagedReader::GetMethodVersion Metodu</span><span class="sxs-lookup"><span data-stu-id="96d46-102">ISymUnmanagedReader::GetMethodVersion Method</span></span>

<span data-ttu-id="96d46-103">Yöntem sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="96d46-103">Gets the method version.</span></span> <span data-ttu-id="96d46-104">Yöntem sürümü 1 ' de başlar ve yöntemin her yeniden derlenmesi sırasında artırılır.</span><span class="sxs-lookup"><span data-stu-id="96d46-104">The method version starts at 1 and is incremented each time the method is recompiled.</span></span> <span data-ttu-id="96d46-105">Yeniden derleme, yöntemde değişiklik yapılmadan meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="96d46-105">Recompilation can happen without changes to the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96d46-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="96d46-106">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodVersion (  
    [in]  ISymUnmanagedMethod* pMethod,  
    [out] int* version);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96d46-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="96d46-107">Parameters</span></span>  

 `pMethod`  
 <span data-ttu-id="96d46-108">'ndaki Sürümünün alınacağı yöntem.</span><span class="sxs-lookup"><span data-stu-id="96d46-108">[in] The method for which to get the version.</span></span>  
  
 `version`  
 <span data-ttu-id="96d46-109">dışı Yöntem sürümünü alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="96d46-109">[out] A pointer to a variable that receives the method version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96d46-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="96d46-110">Return Value</span></span>  

 <span data-ttu-id="96d46-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="96d46-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96d46-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96d46-112">Requirements</span></span>  

 <span data-ttu-id="96d46-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="96d46-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96d46-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96d46-114">See also</span></span>

- [<span data-ttu-id="96d46-115">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="96d46-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
