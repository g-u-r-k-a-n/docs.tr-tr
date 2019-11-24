---
title: ISymUnmanagedDocumentWriter::SetSource Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetSource
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetSource method [.NET Framework debugging]
- SetSource method [.NET Framework debugging]
ms.assetid: ea5b9d9f-ff06-4bd3-8de5-6435343aba59
topic_type:
- apiref
ms.openlocfilehash: ff18f95bd6b4cfde5aaa4d3f6f68b58fd37c04b3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449075"
---
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="b86b8-102">ISymUnmanagedDocumentWriter::SetSource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b86b8-102">ISymUnmanagedDocumentWriter::SetSource Method</span></span>
<span data-ttu-id="b86b8-103">Sets embedded source for a document that is being written.</span><span class="sxs-lookup"><span data-stu-id="b86b8-103">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b86b8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b86b8-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b86b8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b86b8-105">Parameters</span></span>  
 `sourceSize`  
 <span data-ttu-id="b86b8-106">[in] A `ULONG32` that contains the size of the `source` buffer.</span><span class="sxs-lookup"><span data-stu-id="b86b8-106">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="b86b8-107">[in] The buffer that stores the embedded source.</span><span class="sxs-lookup"><span data-stu-id="b86b8-107">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b86b8-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b86b8-108">Return Value</span></span>  
 <span data-ttu-id="b86b8-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="b86b8-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b86b8-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b86b8-110">Requirements</span></span>  
 <span data-ttu-id="b86b8-111">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b86b8-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b86b8-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b86b8-112">See also</span></span>

- [<span data-ttu-id="b86b8-113">ISymUnmanagedDocumentWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b86b8-113">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
