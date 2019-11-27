---
title: ISymUnmanagedWriter::Initialize2 Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type:
- apiref
ms.openlocfilehash: 041df959139a0be77f40d6aa5655ff15f93fb26f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427946"
---
# <a name="isymunmanagedwriterinitialize2-method"></a><span data-ttu-id="d9cb3-102">ISymUnmanagedWriter::Initialize2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d9cb3-102">ISymUnmanagedWriter::Initialize2 Method</span></span>
<span data-ttu-id="d9cb3-103">Bu yazıcının ilişkilendirileceği meta veri verici arabirimini ayarlar ve hata ayıklama simgelerinin yazılacağı çıkış dosyası adını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d9cb3-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span> <span data-ttu-id="d9cb3-104">Bu yöntem, program veritabanı (PDB) dosyasının son konumunu ayarlamanıza de olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d9cb3-104">This method also lets you set the final location of the program database (PDB) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9cb3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9cb3-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9cb3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d9cb3-106">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="d9cb3-107">'ndaki Meta veri verici arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d9cb3-107">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `tempfilename`  
 <span data-ttu-id="d9cb3-108">'ndaki Hata ayıklama simgelerinin yazıldığı dosya adını içeren `WCHAR` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d9cb3-108">[in] A pointer to a `WCHAR` that contains the file name to which the debugging symbols are written.</span></span> <span data-ttu-id="d9cb3-109">Dosya adları kullanmayan bir yazıcı için dosya adı belirtilmişse, bu parametre yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="d9cb3-109">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="d9cb3-110">'ndaki Belirtilmişse, sembol yazıcı sembolleri `filename` parametresinde belirtilen dosya yerine verilen <xref:System.Runtime.InteropServices.ComTypes.IStream> yayar.</span><span class="sxs-lookup"><span data-stu-id="d9cb3-110">[in] If specified, the symbol writer emits the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="d9cb3-111">`pIStream` parametresi isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d9cb3-111">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="d9cb3-112">[in] Bu bir tam yeniden oluşturma ise `true`; Bu, artımlı bir derleme ise `false`.</span><span class="sxs-lookup"><span data-stu-id="d9cb3-112">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
 `finalfilename`  
 <span data-ttu-id="d9cb3-113">'ndaki PDB dosyasının son konumunun yol dizesi olan bir `WCHAR` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d9cb3-113">[in] A pointer to a `WCHAR` that is the path string to the final location of the PDB file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9cb3-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d9cb3-114">Return Value</span></span>  
 <span data-ttu-id="d9cb3-115">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="d9cb3-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9cb3-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9cb3-116">Requirements</span></span>  
 <span data-ttu-id="d9cb3-117">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d9cb3-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9cb3-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9cb3-118">See also</span></span>

- [<span data-ttu-id="d9cb3-119">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9cb3-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="d9cb3-120">Initialize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d9cb3-120">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)
