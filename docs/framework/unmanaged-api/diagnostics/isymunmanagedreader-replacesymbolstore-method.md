---
title: ISymUnmanagedReader::ReplaceSymbolStore Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.ReplaceSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::ReplaceSymbolStore
helpviewer_keywords:
- ReplaceSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::ReplaceSymbolStore method [.NET Framework debugging]
ms.assetid: 43257761-8cb1-4eaf-8fb5-1f3980cb66cd
topic_type:
- apiref
ms.openlocfilehash: 60c3537a80c39f758f46e6f2f0a5f2bcd27350b5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445727"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="a443f-102">ISymUnmanagedReader::ReplaceSymbolStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a443f-102">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>
<span data-ttu-id="a443f-103">Var olan sembol deposunu bir Delta sembol deposu ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="a443f-103">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="a443f-104">Bu yöntem [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) yöntemine benzerdir, ancak verilen Delta bir güncelleştirme yerine tam bir değişiklik olarak hareket eder.</span><span class="sxs-lookup"><span data-stu-id="a443f-104">This method is similar to the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a443f-105">`filename` veya `pIStream` parametrelerinden yalnızca birini belirtmeniz gerekir, ikisi birden değil.</span><span class="sxs-lookup"><span data-stu-id="a443f-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="a443f-106">`filename` belirtilirse, sembol deposu bu dosyadaki simgelerle güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a443f-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="a443f-107">`pIStream` belirtilirse mağaza, <xref:System.Runtime.InteropServices.ComTypes.IStream>verilerle güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a443f-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a443f-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a443f-108">Syntax</span></span>  
  
```cpp  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a443f-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a443f-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="a443f-110">'ndaki Sembol deposunu içeren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="a443f-110">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="a443f-111">'ndaki `filename` parametresine alternatif olarak kullanılan dosya akışı.</span><span class="sxs-lookup"><span data-stu-id="a443f-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a443f-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a443f-112">Return Value</span></span>  
 <span data-ttu-id="a443f-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="a443f-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a443f-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a443f-114">Requirements</span></span>  
 <span data-ttu-id="a443f-115">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a443f-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a443f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a443f-116">See also</span></span>

- [<span data-ttu-id="a443f-117">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a443f-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
