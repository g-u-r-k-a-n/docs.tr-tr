---
title: ICorProfilerInfo::GetObjectSize Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetObjectSize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type:
- apiref
ms.openlocfilehash: 4abcf9f4575b32dd125fd8a00783043900993c3e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724110"
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="07da5-102">ICorProfilerInfo::GetObjectSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="07da5-102">ICorProfilerInfo::GetObjectSize Method</span></span>

<span data-ttu-id="07da5-103">Belirtilen nesnenin boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="07da5-103">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07da5-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="07da5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07da5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="07da5-105">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="07da5-106">'ndaki Nesnenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="07da5-106">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="07da5-107">dışı Nesnenin boyutunun bayt cinsinden işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="07da5-107">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07da5-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07da5-108">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="07da5-109">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="07da5-109">This method is obsolete.</span></span> <span data-ttu-id="07da5-110">64-bit platformlarda 4.000'DEN büyük nesneler için COR_E_OVERFLOW döndürür.</span><span class="sxs-lookup"><span data-stu-id="07da5-110">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="07da5-111">Bunun yerine  [ICorProfilerInfo4:: GetObjectSize2](icorprofilerinfo4-getobjectsize2-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="07da5-111">Use the  [ICorProfilerInfo4::GetObjectSize2](icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="07da5-112">Aynı türdeki farklı nesneler genellikle aynı boyutta olur.</span><span class="sxs-lookup"><span data-stu-id="07da5-112">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="07da5-113">Ancak, diziler veya dizeler gibi bazı türlerin her nesne için farklı boyutta bir boyutu olabilir.</span><span class="sxs-lookup"><span data-stu-id="07da5-113">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="07da5-114">Yöntem tarafından döndürülen boyut, `GetObjectSize` nesne çöp toplama yığınında olduktan sonra görünebilen herhangi bir hizalama dolgusu içermez.</span><span class="sxs-lookup"><span data-stu-id="07da5-114">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="07da5-115">`GetObjectSize`Çöp toplama yığınında nesnesinden nesneye ilerlemek için yöntemini kullanırsanız, gerektiğinde hizalama doldurmayı el ile ekleyin.</span><span class="sxs-lookup"><span data-stu-id="07da5-115">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
- <span data-ttu-id="07da5-116">32 bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1 ve COR_PRF_GC_GEN_2 4 baytlık hizalama kullanın ve COR_PRF_GC_LARGE_OBJECT_HEAP 8 baytlık hizalama kullanır.</span><span class="sxs-lookup"><span data-stu-id="07da5-116">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
- <span data-ttu-id="07da5-117">64 bit Windows üzerinde hizalama her zaman 8 bayttır.</span><span class="sxs-lookup"><span data-stu-id="07da5-117">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07da5-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07da5-118">Requirements</span></span>  

 <span data-ttu-id="07da5-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07da5-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07da5-120">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="07da5-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="07da5-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="07da5-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07da5-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07da5-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07da5-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07da5-123">See also</span></span>

- [<span data-ttu-id="07da5-124">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07da5-124">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
