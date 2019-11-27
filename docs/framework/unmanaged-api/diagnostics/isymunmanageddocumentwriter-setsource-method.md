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
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="3ce41-102">ISymUnmanagedDocumentWriter::SetSource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ce41-102">ISymUnmanagedDocumentWriter::SetSource Method</span></span>
<span data-ttu-id="3ce41-103">Yazılmakta olan bir belge için gömülü kaynağı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3ce41-103">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ce41-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3ce41-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ce41-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3ce41-105">Parameters</span></span>  
 `sourceSize`  
 <span data-ttu-id="3ce41-106">'ndaki `source` arabelleğinin boyutunu içeren bir `ULONG32`.</span><span class="sxs-lookup"><span data-stu-id="3ce41-106">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="3ce41-107">'ndaki Gömülü kaynağı depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="3ce41-107">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ce41-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3ce41-108">Return Value</span></span>  
 <span data-ttu-id="3ce41-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="3ce41-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ce41-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3ce41-110">Requirements</span></span>  
 <span data-ttu-id="3ce41-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3ce41-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ce41-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ce41-112">See also</span></span>

- [<span data-ttu-id="3ce41-113">ISymUnmanagedDocumentWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3ce41-113">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
