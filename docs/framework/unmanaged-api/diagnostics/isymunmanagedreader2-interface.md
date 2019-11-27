---
title: ISymUnmanagedReader2 Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2
helpviewer_keywords:
- ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type:
- apiref
ms.openlocfilehash: a07c75e14244fb5bdf72ff2b0d344ae27672ef89
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448272"
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="67c26-102">ISymUnmanagedReader2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="67c26-102">ISymUnmanagedReader2 Interface</span></span>
<span data-ttu-id="67c26-103">Bir sembol deposu içindeki belgelere, yöntemlere ve değişkenlere erişim sağlayan bir sembol okuyucuyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="67c26-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="67c26-104">Bu arabirim [ıstreamunmanagedreader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="67c26-104">This interface extends the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="67c26-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="67c26-105">Methods</span></span>  
  
|<span data-ttu-id="67c26-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="67c26-106">Method</span></span>|<span data-ttu-id="67c26-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67c26-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="67c26-108">GetMethodByVersionPreRemap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="67c26-108">GetMethodByVersionPreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="67c26-109">Bir yöntem belirteci ve bir Düzenle ve devam et sürüm numarası verilen bir sembol okuyucu yöntemi alın.</span><span class="sxs-lookup"><span data-stu-id="67c26-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="67c26-110">GetMethodsInDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="67c26-110">GetMethodsInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="67c26-111">Belirtilen belgede satır bilgilerine sahip her yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="67c26-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="67c26-112">GetSymAttributePreRemap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="67c26-112">GetSymAttributePreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="67c26-113">Özel bir özniteliği adına göre alır.</span><span class="sxs-lookup"><span data-stu-id="67c26-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="67c26-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67c26-114">Requirements</span></span>  
 <span data-ttu-id="67c26-115">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="67c26-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67c26-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67c26-116">See also</span></span>

- [<span data-ttu-id="67c26-117">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="67c26-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="67c26-118">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="67c26-118">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
