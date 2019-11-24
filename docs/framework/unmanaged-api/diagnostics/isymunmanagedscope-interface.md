---
title: ISymUnmanagedScope Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope
helpviewer_keywords:
- ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 3db7a220-cfe9-4810-8ca8-a094bb8e0f5b
topic_type:
- apiref
ms.openlocfilehash: 8da4da38d23ed65a0fdc44a0f919ee8cad2fe18e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446270"
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="023fe-102">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="023fe-102">ISymUnmanagedScope Interface</span></span>
<span data-ttu-id="023fe-103">Represents a lexical scope within a method.</span><span class="sxs-lookup"><span data-stu-id="023fe-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="023fe-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="023fe-104">Methods</span></span>  
  
|<span data-ttu-id="023fe-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="023fe-105">Method</span></span>|<span data-ttu-id="023fe-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="023fe-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="023fe-107">GetChildren Yöntemi</span><span class="sxs-lookup"><span data-stu-id="023fe-107">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="023fe-108">Gets the children of this scope.</span><span class="sxs-lookup"><span data-stu-id="023fe-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="023fe-109">GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="023fe-109">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="023fe-110">Gets the end offset for this scope.</span><span class="sxs-lookup"><span data-stu-id="023fe-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="023fe-111">GetLocalCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="023fe-111">GetLocalCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="023fe-112">Gets a count of the local variables defined within this scope.</span><span class="sxs-lookup"><span data-stu-id="023fe-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="023fe-113">GetLocals Yöntemi</span><span class="sxs-lookup"><span data-stu-id="023fe-113">GetLocals Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="023fe-114">Gets the local variables defined within this scope.</span><span class="sxs-lookup"><span data-stu-id="023fe-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="023fe-115">GetMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="023fe-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="023fe-116">Gets the method that contains this scope.</span><span class="sxs-lookup"><span data-stu-id="023fe-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="023fe-117">GetNamespaces Yöntemi</span><span class="sxs-lookup"><span data-stu-id="023fe-117">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="023fe-118">Gets the namespaces that are being used within this scope.</span><span class="sxs-lookup"><span data-stu-id="023fe-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="023fe-119">GetParent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="023fe-119">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|<span data-ttu-id="023fe-120">Gets the parent scope of this scope.</span><span class="sxs-lookup"><span data-stu-id="023fe-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="023fe-121">GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="023fe-121">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="023fe-122">Gets the start offset for this scope.</span><span class="sxs-lookup"><span data-stu-id="023fe-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="023fe-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="023fe-123">Requirements</span></span>  
 <span data-ttu-id="023fe-124">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="023fe-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="023fe-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="023fe-125">See also</span></span>

- [<span data-ttu-id="023fe-126">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="023fe-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="023fe-127">ISymUnmanagedScope2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="023fe-127">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
