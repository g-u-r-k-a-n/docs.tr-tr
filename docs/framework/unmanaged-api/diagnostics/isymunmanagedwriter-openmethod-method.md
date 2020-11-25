---
title: ISymUnmanagedWriter::OpenMethod Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type:
- apiref
ms.openlocfilehash: deb3a28ffb73754b4c03496a6a72325418f1a4fc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722914"
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="cecbd-102">ISymUnmanagedWriter::OpenMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cecbd-102">ISymUnmanagedWriter::OpenMethod Method</span></span>

<span data-ttu-id="cecbd-103">Sembol bilgisinin yayıldığını bir yöntem açar.</span><span class="sxs-lookup"><span data-stu-id="cecbd-103">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="cecbd-104">Verilen yöntem, dizi noktalarını, parametreleri ve sözcük temelli kapsamları tanımlamak için çağrılar için geçerli yöntem haline gelir.</span><span class="sxs-lookup"><span data-stu-id="cecbd-104">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="cecbd-105">Tüm yöntem etrafında örtük bir sözcük temelli kapsam vardır.</span><span class="sxs-lookup"><span data-stu-id="cecbd-105">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="cecbd-106">Daha önce kapatılan bir yöntemi yeniden açmak, bu yöntem için önceden tanımlanmış tüm sembolleri siler.</span><span class="sxs-lookup"><span data-stu-id="cecbd-106">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="cecbd-107">Tek seferde yalnızca bir açık yöntem olabilir.</span><span class="sxs-lookup"><span data-stu-id="cecbd-107">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cecbd-108">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="cecbd-108">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cecbd-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cecbd-109">Parameters</span></span>  

 `method`  
 <span data-ttu-id="cecbd-110">'ndaki Açılacak yöntemin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="cecbd-110">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cecbd-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cecbd-111">Return Value</span></span>  

 <span data-ttu-id="cecbd-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="cecbd-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cecbd-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cecbd-113">Requirements</span></span>  

 <span data-ttu-id="cecbd-114">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="cecbd-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cecbd-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cecbd-115">See also</span></span>

- [<span data-ttu-id="cecbd-116">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cecbd-116">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="cecbd-117">CloseMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cecbd-117">CloseMethod Method</span></span>](isymunmanagedwriter-closemethod-method.md)
- [<span data-ttu-id="cecbd-118">OpenMethod2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cecbd-118">OpenMethod2 Method</span></span>](isymunmanagedwriter3-openmethod2-method.md)
