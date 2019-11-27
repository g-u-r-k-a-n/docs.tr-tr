---
title: ISymUnmanagedReader::GetDocumentVersion Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocumentVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocumentVersion
helpviewer_keywords:
- GetDocumentVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocumentVersion method [.NET Framework debugging]
ms.assetid: a51f1f64-e084-44c5-830c-2222da5a6bbf
topic_type:
- apiref
ms.openlocfilehash: 3bc578be680951a1d41c92fb2169c860882b2e31
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448301"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a><span data-ttu-id="6a1c2-102">ISymUnmanagedReader::GetDocumentVersion Metodu</span><span class="sxs-lookup"><span data-stu-id="6a1c2-102">ISymUnmanagedReader::GetDocumentVersion Method</span></span>
<span data-ttu-id="6a1c2-103">Belirtilen belgenin belirtilen sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="6a1c2-103">Gets the specified version of the specified document.</span></span> <span data-ttu-id="6a1c2-104">Belge sürümü 1 ' de başlar ve belge [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) yöntemi kullanılarak her güncelleştirildiği zaman artırılır.</span><span class="sxs-lookup"><span data-stu-id="6a1c2-104">The document version starts at 1 and is incremented each time the document is updated using the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method.</span></span> <span data-ttu-id="6a1c2-105">`pbCurrent` parametresi `true`, bu belgenin en son sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="6a1c2-105">If the `pbCurrent` parameter is `true`, this is the latest version of the document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a1c2-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a1c2-106">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a1c2-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a1c2-107">Parameters</span></span>  
 `pDoc`  
 <span data-ttu-id="6a1c2-108">'ndaki Belirtilen belge.</span><span class="sxs-lookup"><span data-stu-id="6a1c2-108">[in] The specified document.</span></span>  
  
 `version`  
 <span data-ttu-id="6a1c2-109">dışı Belirtilen belgenin sürümünü alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6a1c2-109">[out] A pointer to a variable that receives the version of the specified document.</span></span>  
  
 `pbCurrent`  
 <span data-ttu-id="6a1c2-110">dışı Belgenin en son sürümse veya en son sürüm değilse `false` `true` alan bir değişken işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6a1c2-110">[out] A pointer to a variable that receives `true` if this is the latest version of the document, or `false` if it isn't the latest version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a1c2-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6a1c2-111">Return Value</span></span>  
 <span data-ttu-id="6a1c2-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="6a1c2-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a1c2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a1c2-113">Requirements</span></span>  
 <span data-ttu-id="6a1c2-114">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="6a1c2-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a1c2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a1c2-115">See also</span></span>

- [<span data-ttu-id="6a1c2-116">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a1c2-116">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
