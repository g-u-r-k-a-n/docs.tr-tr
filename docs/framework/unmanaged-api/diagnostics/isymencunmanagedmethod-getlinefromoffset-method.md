---
title: ISymENCUnmanagedMethod::GetLineFromOffset Yöntemi
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetLineFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type:
- apiref
ms.openlocfilehash: 196993df9058d3eb8167e0144255c5fe366c54f8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707366"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a><span data-ttu-id="3dcb9-102">ISymENCUnmanagedMethod::GetLineFromOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3dcb9-102">ISymENCUnmanagedMethod::GetLineFromOffset Method</span></span>

<span data-ttu-id="3dcb9-103">Bir uzaklığa ilişkin satır bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="3dcb9-103">Gets the line information associated with an offset.</span></span> <span data-ttu-id="3dcb9-104">Eğer fark parametresi ( `dwOffset` ) bir sıra noktası değilse, bu yöntem önceki uzaklığa ilişkin satır bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="3dcb9-104">If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dcb9-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3dcb9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dcb9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3dcb9-106">Parameters</span></span>  

 `dwOffset`  
 <span data-ttu-id="3dcb9-107">'ndaki `ULONG32` Bu, sapmayı içeren bir.</span><span class="sxs-lookup"><span data-stu-id="3dcb9-107">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `pline`  
 <span data-ttu-id="3dcb9-108">dışı Satırı alan bir işaretçisi `ULONG32` .</span><span class="sxs-lookup"><span data-stu-id="3dcb9-108">[out] A pointer to a `ULONG32` that receives the line.</span></span>  
  
 `pcolumn`  
 <span data-ttu-id="3dcb9-109">dışı Sütununu alan öğesine yönelik bir işaretçi `ULONG32` .</span><span class="sxs-lookup"><span data-stu-id="3dcb9-109">[out] A pointer to a `ULONG32` that receives the column.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="3dcb9-110">dışı `ULONG32` Bitiş satırını alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3dcb9-110">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
 `pendColumn`  
 <span data-ttu-id="3dcb9-111">dışı Bitiş sütununu alan öğesine yönelik bir işaretçi `ULONG32` .</span><span class="sxs-lookup"><span data-stu-id="3dcb9-111">[out] A pointer to a `ULONG32` that receives the end column.</span></span>  
  
 `pdwStartOffset`  
 <span data-ttu-id="3dcb9-112">dışı `ULONG32` İlişkili dizi noktasını alan öğesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3dcb9-112">[out] A pointer to a `ULONG32` that receives the associated sequence point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3dcb9-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3dcb9-113">Return Value</span></span>  

 <span data-ttu-id="3dcb9-114">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="3dcb9-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dcb9-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3dcb9-115">Requirements</span></span>  

 <span data-ttu-id="3dcb9-116">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3dcb9-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dcb9-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3dcb9-117">See also</span></span>

- [<span data-ttu-id="3dcb9-118">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3dcb9-118">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
