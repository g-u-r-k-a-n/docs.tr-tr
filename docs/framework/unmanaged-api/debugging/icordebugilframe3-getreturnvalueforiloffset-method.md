---
title: ICorDebugILFrame3::GetReturnValueForILOffset Yöntemi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
api_name:
- ICorDebugILFrame3.GetReturnValueForILOffset
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 06522727-5f64-4391-9331-11386883c352
topic_type:
- apiref
ms.openlocfilehash: 11207298b071527151535144330790df767c2101
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725007"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a><span data-ttu-id="16cf1-102">ICorDebugILFrame3::GetReturnValueForILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="16cf1-102">ICorDebugILFrame3::GetReturnValueForILOffset Method</span></span>

<span data-ttu-id="16cf1-103">Bir işlevin dönüş değerini kapsülleyen bir "ICorDebugValue" nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="16cf1-103">Gets an "ICorDebugValue" object that encapsulates the return value of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16cf1-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="16cf1-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16cf1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="16cf1-105">Parameters</span></span>  

 `ILOffset`  
 <span data-ttu-id="16cf1-106">Il kayması.</span><span class="sxs-lookup"><span data-stu-id="16cf1-106">The IL offset.</span></span> <span data-ttu-id="16cf1-107">Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="16cf1-107">See the Remarks section.</span></span>  
  
 `ppReturnValue`  
 <span data-ttu-id="16cf1-108">Bir işlev çağrısının dönüş değeri hakkında bilgi sağlayan bir "ICorDebugValue" arabirim nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="16cf1-108">A pointer to the address of an "ICorDebugValue" interface object that provides information about the return value of a function call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16cf1-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16cf1-109">Remarks</span></span>  

 <span data-ttu-id="16cf1-110">Bu yöntem, bir yöntemin dönüş değerini almak için [ICorDebugCode3:: Getreturnvaluelivesapmayı](icordebugcode3-getreturnvalueliveoffset-method.md) yöntemi ile birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="16cf1-110">This method is used along with the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method to get the return value of a method.</span></span> <span data-ttu-id="16cf1-111">Aşağıdaki iki kod örneğinde olduğu gibi, dönüş değerleri yok sayılan Yöntemler söz konusu olduğunda özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="16cf1-111">It is particularly useful in the case of methods whose return values are ignored, as in the following two code examples.</span></span> <span data-ttu-id="16cf1-112">İlk örnek <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> yöntemini çağırır, ancak yöntemin dönüş değerini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="16cf1-112">The first example calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method, but ignores the method's return value.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 <span data-ttu-id="16cf1-113">İkinci örnek, hata ayıklama sırasında çok daha yaygın bir sorunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="16cf1-113">The second example illustrates a much more common problem in debugging.</span></span> <span data-ttu-id="16cf1-114">Yöntemi bir yöntem çağrısında bağımsız değişken olarak kullanıldığından, dönüş değeri yalnızca hata ayıklayıcı çağrılan yöntem boyunca adım adım erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="16cf1-114">Because a method is used as an argument in a method call, its return value is accessible only when the debugger steps through the called method.</span></span> <span data-ttu-id="16cf1-115">Çoğu durumda, özellikle çağrılan yöntem bir dış kitaplıkta tanımlandığında, bu mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="16cf1-115">In many cases, particularly when the called method is defined in an external library, that is not possible.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 <span data-ttu-id="16cf1-116">[ICorDebugCode3:: Getreturnvalueliveuzaklık](icordebugcode3-getreturnvalueliveoffset-method.md) metodunu bir işlev ÇAĞRıSı sitesine Il uzaklığına geçirirseniz, bir veya daha fazla yerel uzaklık döndürür.</span><span class="sxs-lookup"><span data-stu-id="16cf1-116">If you pass the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method an IL offset to a function call site, it returns one or more native offsets.</span></span> <span data-ttu-id="16cf1-117">Hata ayıklayıcı daha sonra işlevdeki bu yerel kaydırmalar üzerinde kesme noktaları ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="16cf1-117">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="16cf1-118">Hata ayıklayıcı kesme noktalarından birine geçtiğinde, dönüş değerini almak için bu yönteme geçirdiğiniz Il sapmasını geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16cf1-118">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to get the return value.</span></span> <span data-ttu-id="16cf1-119">Hata ayıklayıcı daha sonra, ayarlandığı tüm kesme noktalarını temizlemelidir.</span><span class="sxs-lookup"><span data-stu-id="16cf1-119">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="16cf1-120">[ICorDebugCode3:: Getreturnvaluelivesapmayı yöntemi](icordebugcode3-getreturnvalueliveoffset-method.md) ve `ICorDebugILFrame3::GetReturnValueForILOffset` yöntemleri yalnızca başvuru türleri için dönüş değeri bilgilerini almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="16cf1-120">The [ICorDebugCode3::GetReturnValueLiveOffset Method](icordebugcode3-getreturnvalueliveoffset-method.md) and `ICorDebugILFrame3::GetReturnValueForILOffset` methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="16cf1-121">Değer türlerinden dönüş değeri bilgileri alma (yani, öğesinden türetilen tüm türler <xref:System.ValueType> ) desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="16cf1-121">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="16cf1-122">Parametresi tarafından belirtilen Il uzaklığında `ILOffset` bir işlev çağrı sitesinde olması gerekir ve hata ayıklanan aynı Il uzaklığında, [ICorDebugCode3:: Getreturnvaluelivesapmayı](icordebugcode3-getreturnvalueliveoffset-method.md) yöntemi tarafından döndürülen yerel uzaklığında ayarlanan bir kesme noktasında durdurulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="16cf1-122">The IL offset specified by the `ILOffset` parameter should be at a function call site, and the debuggee should be stopped at a breakpoint set at the native offset returned by the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method for the same IL offset.</span></span> <span data-ttu-id="16cf1-123">Hata ayıklanan, belirtilen Il uzaklığında doğru konumda durdurulmamışsa, API başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="16cf1-123">If the debuggee is not stopped at the correct location for the specified IL offset, the API will fail.</span></span>  
  
 <span data-ttu-id="16cf1-124">İşlev çağrısı bir değer döndürmezse, API başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="16cf1-124">If the function call doesn't return a value, the API will fail.</span></span>  
  
 <span data-ttu-id="16cf1-125">`ICorDebugILFrame3::GetReturnValueForILOffset`Yöntemi yalnızca x86 tabanlı ve AMD64 sistemlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="16cf1-125">The `ICorDebugILFrame3::GetReturnValueForILOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16cf1-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="16cf1-126">Requirements</span></span>  

 <span data-ttu-id="16cf1-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16cf1-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16cf1-128">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="16cf1-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16cf1-129">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="16cf1-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16cf1-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16cf1-130">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16cf1-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16cf1-131">See also</span></span>

- [<span data-ttu-id="16cf1-132">GetReturnValueLiveOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="16cf1-132">GetReturnValueLiveOffset Method</span></span>](icordebugcode3-getreturnvalueliveoffset-method.md)
- [<span data-ttu-id="16cf1-133">ICorDebugILFrame3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="16cf1-133">ICorDebugILFrame3 Interface</span></span>](icordebugilframe3-interface.md)
