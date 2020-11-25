---
title: ISymUnmanagedBinder::GetReaderFromStream Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderFromStream
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderFromStream
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderFromStream method [.NET Framework debugging]
- GetReaderFromStream method [.NET Framework debugging]
ms.assetid: aa38efd4-de7e-4482-a5d3-adc152093460
topic_type:
- apiref
ms.openlocfilehash: 2d927b02b7deebecb53a2218e2ec0275a07307b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706963"
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a><span data-ttu-id="45dd5-102">ISymUnmanagedBinder::GetReaderFromStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45dd5-102">ISymUnmanagedBinder::GetReaderFromStream Method</span></span>

<span data-ttu-id="45dd5-103">Meta veri arabirimi ve sembol deposunu içeren bir akış verildiğinde, verilen sembol deposundan hata ayıklama sembollerini okuyan doğru [ıstreamunmanagedreader](isymunmanagedreader-interface.md) yapısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="45dd5-103">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45dd5-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="45dd5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45dd5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="45dd5-105">Parameters</span></span>  

 `importer`  
 <span data-ttu-id="45dd5-106">'ndaki Meta veri içeri aktarma arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="45dd5-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `pstream`  
 <span data-ttu-id="45dd5-107">'ndaki Sembol deposunu içeren akışa yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="45dd5-107">[in] A pointer to the stream that contains the symbol store.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="45dd5-108">dışı Döndürülen [ıdimunmanagedreader](isymunmanagedreader-interface.md) arabirimine ayarlanmış bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="45dd5-108">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45dd5-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="45dd5-109">Return Value</span></span>  

 <span data-ttu-id="45dd5-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="45dd5-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45dd5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="45dd5-111">Requirements</span></span>  

 <span data-ttu-id="45dd5-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="45dd5-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45dd5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45dd5-113">See also</span></span>

- [<span data-ttu-id="45dd5-114">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="45dd5-114">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
