---
title: ISymUnmanagedWriter::CloseNamespace Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::CloseNamespace method [.NET Framework debugging]
- CloseNamespace method [.NET Framework debugging]
ms.assetid: 7f74d9c5-1377-4958-b842-6306d611cbd5
topic_type:
- apiref
ms.openlocfilehash: b29e66a4e124f6d593fc0c8aed9a63fcc660f8df
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428094"
---
# <a name="isymunmanagedwriterclosenamespace-method"></a><span data-ttu-id="145f0-102">ISymUnmanagedWriter::CloseNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="145f0-102">ISymUnmanagedWriter::CloseNamespace Method</span></span>
<span data-ttu-id="145f0-103">Closes the most recently opened namespace.</span><span class="sxs-lookup"><span data-stu-id="145f0-103">Closes the most recently opened namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="145f0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="145f0-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseNamespace();  
```  
  
## <a name="return-value"></a><span data-ttu-id="145f0-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="145f0-105">Return Value</span></span>  
 <span data-ttu-id="145f0-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="145f0-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="145f0-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="145f0-107">Requirements</span></span>  
 <span data-ttu-id="145f0-108">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="145f0-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="145f0-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="145f0-109">See also</span></span>

- [<span data-ttu-id="145f0-110">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="145f0-110">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="145f0-111">OpenNamespace Yöntemi</span><span class="sxs-lookup"><span data-stu-id="145f0-111">OpenNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)
