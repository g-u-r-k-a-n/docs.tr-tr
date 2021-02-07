---
description: 'Daha fazla bilgi edinin: ISymUnmanagedWriter3:: COMMIT yöntemi'
title: ISymUnmanagedWriter3::Commit Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.Commit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::Commit
helpviewer_keywords:
- Commit method, ISymUnmanagedWriter3 interface [.NET Framework debugging]
- ISymUnmanagedWriter3::Commit method [.NET Framework debugging]
ms.assetid: f6961922-46ec-4d2c-8369-85f880731f37
topic_type:
- apiref
ms.openlocfilehash: 308f5d3a16cf60a0e77a581a318d6fd6c398b3f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761765"
---
# <a name="isymunmanagedwriter3commit-method"></a><span data-ttu-id="075ad-103">ISymUnmanagedWriter3::Commit Metodu</span><span class="sxs-lookup"><span data-stu-id="075ad-103">ISymUnmanagedWriter3::Commit Method</span></span>

<span data-ttu-id="075ad-104">Şimdiye kadar yazılı olan değişiklikleri akışa kaydeder.</span><span class="sxs-lookup"><span data-stu-id="075ad-104">Commits the changes written so far to the stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="075ad-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="075ad-105">Syntax</span></span>  
  
```cpp  
HRESULT Commit();  
```  
  
## <a name="return-value"></a><span data-ttu-id="075ad-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="075ad-106">Return Value</span></span>  

 <span data-ttu-id="075ad-107">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="075ad-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="075ad-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="075ad-108">Requirements</span></span>  

 <span data-ttu-id="075ad-109">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="075ad-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="075ad-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="075ad-110">See also</span></span>

- [<span data-ttu-id="075ad-111">ISymUnmanagedWriter3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="075ad-111">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
