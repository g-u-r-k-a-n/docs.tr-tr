---
title: ICorDebugILFrame Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame
helpviewer_keywords:
- ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type:
- apiref
ms.openlocfilehash: 4f34fdf9a0eeb47e027cc874afee5bd04f5bd9bc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712397"
---
# <a name="icordebugilframe-interface"></a><span data-ttu-id="e4c97-102">ICorDebugILFrame Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4c97-102">ICorDebugILFrame Interface</span></span>

<span data-ttu-id="e4c97-103">Microsoft ara dili (MSIL) kodunun yığın çerçevesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e4c97-103">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="e4c97-104">Bu arabirim, ICorDebugFrame arabiriminin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="e4c97-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e4c97-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e4c97-105">Methods</span></span>  
  
|<span data-ttu-id="e4c97-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e4c97-106">Method</span></span>|<span data-ttu-id="e4c97-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4c97-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e4c97-108">CanSetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e4c97-108">CanSetIP Method</span></span>](icordebugilframe-cansetip-method.md)|<span data-ttu-id="e4c97-109">Belirtilen konum konumuna yönerge işaretçisini ayarlamak için güvenli olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="e4c97-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="e4c97-110">EnumerateArguments Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e4c97-110">EnumerateArguments Method</span></span>](icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="e4c97-111">Bu çerçevedeki bağımsız değişkenler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="e4c97-111">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="e4c97-112">EnumerateLocalVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e4c97-112">EnumerateLocalVariables Method</span></span>](icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="e4c97-113">Bu çerçevedeki yerel değişkenler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="e4c97-113">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="e4c97-114">GetArgument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e4c97-114">GetArgument Method</span></span>](icordebugilframe-getargument-method.md)|<span data-ttu-id="e4c97-115">Bu MSIL yığın çerçevesindeki belirtilen bağımsız değişkenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="e4c97-115">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="e4c97-116">GetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e4c97-116">GetIP Method</span></span>](icordebugilframe-getip-method.md)|<span data-ttu-id="e4c97-117">Yönerge işaretçisinin değerini ve yönerge işaretçisi değerinin nasıl elde edileceğini açıklayan bit düzeyinde birleşim değerini alır.</span><span class="sxs-lookup"><span data-stu-id="e4c97-117">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="e4c97-118">GetLocalVariable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e4c97-118">GetLocalVariable Method</span></span>](icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="e4c97-119">Bu MSIL yığın çerçevesinde belirtilen yerel değişkenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="e4c97-119">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="e4c97-120">GetStackDepth Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e4c97-120">GetStackDepth Method</span></span>](icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="e4c97-121">Uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="e4c97-121">Not implemented.</span></span>|  
|[<span data-ttu-id="e4c97-122">GetStackValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e4c97-122">GetStackValue Method</span></span>](icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="e4c97-123">Uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="e4c97-123">Not implemented.</span></span>|  
|[<span data-ttu-id="e4c97-124">SetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e4c97-124">SetIP Method</span></span>](icordebugilframe-setip-method.md)|<span data-ttu-id="e4c97-125">Yönerge işaretçisini MSIL kodunda belirtilen konum konumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e4c97-125">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4c97-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e4c97-126">Remarks</span></span>  

 <span data-ttu-id="e4c97-127">`ICorDebugILFrame`Arabirim, özelleştirilmiş bir ICorDebugFrame arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="e4c97-127">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="e4c97-128">MSIL kod çerçeveleri ya da tam zamanında (JıT) derlenmiş çerçeveler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e4c97-128">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="e4c97-129">JıT ile derlenen çerçeveler hem arabirimini hem de `ICorDebugILFrame` ICorDebugNativeFrame arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="e4c97-129">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4c97-130">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="e4c97-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4c97-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e4c97-131">Requirements</span></span>  

 <span data-ttu-id="e4c97-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4c97-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4c97-133">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e4c97-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4c97-134">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e4c97-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4c97-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4c97-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4c97-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4c97-136">See also</span></span>

- [<span data-ttu-id="e4c97-137">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e4c97-137">Debugging Interfaces</span></span>](debugging-interfaces.md)
