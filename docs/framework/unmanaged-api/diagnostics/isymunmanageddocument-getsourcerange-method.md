---
title: ISymUnmanagedDocument::GetSourceRange Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceRange
helpviewer_keywords:
- ISymUnmanagedDocument::GetSourceRange method [.NET Framework debugging]
- GetSourceRange method [.NET Framework debugging]
ms.assetid: 20fefee7-1040-41ba-93dc-bd42f68b90c2
topic_type:
- apiref
ms.openlocfilehash: f5d7df60a7b9c728b73fe6592226a8b6734b1e66
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95692156"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a><span data-ttu-id="af4a3-102">ISymUnmanagedDocument::GetSourceRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="af4a3-102">ISymUnmanagedDocument::GetSourceRange Method</span></span>

<span data-ttu-id="af4a3-103">Eklenmiş kaynağın belirtilen aralığını verilen arabelleğe döndürür.</span><span class="sxs-lookup"><span data-stu-id="af4a3-103">Returns the specified range of the embedded source into the given buffer.</span></span> <span data-ttu-id="af4a3-104">Arabellek, kaynağı tutabilecek kadar büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="af4a3-104">The buffer must be large enough to hold the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af4a3-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="af4a3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceRange(  
    [in]  ULONG32  startLine,  
    [in]  ULONG32  startColumn,  
    [in]  ULONG32  endLine,  
    [in]  ULONG32  endColumn,  
    [in]  ULONG32  cSourceBytes,  
    [out] ULONG32  *pcSourceBytes,  
    [out, size_is(cSourceBytes),  
        length_is(*pcSourceBytes)] BYTE source[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af4a3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="af4a3-106">Parameters</span></span>  

 `startLine`  
 <span data-ttu-id="af4a3-107">'ndaki Geçerli belgedeki başlangıç satırı.</span><span class="sxs-lookup"><span data-stu-id="af4a3-107">[in] The starting line in the current document.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="af4a3-108">'ndaki Geçerli belgedeki başlangıç sütunu.</span><span class="sxs-lookup"><span data-stu-id="af4a3-108">[in] The starting column in the current document.</span></span>  
  
 `endLine`  
 <span data-ttu-id="af4a3-109">'ndaki Geçerli belgedeki son satır.</span><span class="sxs-lookup"><span data-stu-id="af4a3-109">[in] The final line in the current document.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="af4a3-110">'ndaki Geçerli belgedeki son sütun.</span><span class="sxs-lookup"><span data-stu-id="af4a3-110">[in] The final column in the current document.</span></span>  
  
 `cSourceBytes`  
 <span data-ttu-id="af4a3-111">'ndaki Kaynağın bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="af4a3-111">[in] The size of the source, in bytes.</span></span>  
  
 `pcSourceBytes`  
 <span data-ttu-id="af4a3-112">dışı Kaynak boyutunu alan değişken için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="af4a3-112">[out] A pointer to a variable that receives the source size.</span></span>  
  
 `source`  
 <span data-ttu-id="af4a3-113">dışı Kaynak belge için bayt cinsinden belirtilen aralığın boyutu ve uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="af4a3-113">[out] The size and length of the specified range of the source document, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af4a3-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="af4a3-114">Return Value</span></span>  

 <span data-ttu-id="af4a3-115">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="af4a3-115">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af4a3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af4a3-116">See also</span></span>

- [<span data-ttu-id="af4a3-117">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="af4a3-117">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
