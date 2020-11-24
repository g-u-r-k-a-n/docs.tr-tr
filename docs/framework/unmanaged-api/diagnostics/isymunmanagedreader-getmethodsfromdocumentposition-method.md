---
title: ISymUnmanagedReader::GetMethodsFromDocumentPosition Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodsFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodsFromDocumentPosition
helpviewer_keywords:
- GetMethodsFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodsFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 83605f1e-e4f3-49e6-859b-f13cad68bb54
topic_type:
- apiref
ms.openlocfilehash: 5298dd0f53693d96b748f6c839660838fdfad4ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689556"
---
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a><span data-ttu-id="8137e-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8137e-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition Method</span></span>

<span data-ttu-id="8137e-103">Her biri bir belgede verilen konumdaki kesme noktasını içeren bir yöntem dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="8137e-103">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8137e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8137e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodsFromDocumentPosition (  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32 line,  
    [in]  ULONG32 column,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is (cMethod),  
        length_is (*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8137e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8137e-105">Parameters</span></span>  

 `document`  
 <span data-ttu-id="8137e-106">'ndaki Belirtilen belge.</span><span class="sxs-lookup"><span data-stu-id="8137e-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="8137e-107">'ndaki Belirtilen belgenin satırı.</span><span class="sxs-lookup"><span data-stu-id="8137e-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="8137e-108">'ndaki Belirtilen belgenin sütunu.</span><span class="sxs-lookup"><span data-stu-id="8137e-108">[in] The column of the specified document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="8137e-109">'ndaki `pRetVal` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="8137e-109">[in] The size of the `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="8137e-110">dışı Dizide döndürülen öğelerin sayısını alan bir değişken işaretçisi `pRetVal` .</span><span class="sxs-lookup"><span data-stu-id="8137e-110">[out] A pointer to a variable that receives the number of elements returned in the `pRetVal` array.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="8137e-111">dışı Her biri, kesme noktasını içeren bir yöntemi temsil eden bir [ıstreamunmanagedmethod](isymunmanagedmethod-interface.md) nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="8137e-111">[out] An array of pointers, each of which points to an [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) object that represents a method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8137e-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8137e-112">Return Value</span></span>  

 <span data-ttu-id="8137e-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="8137e-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8137e-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8137e-114">Requirements</span></span>  

 <span data-ttu-id="8137e-115">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8137e-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8137e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8137e-116">See also</span></span>

- [<span data-ttu-id="8137e-117">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8137e-117">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
