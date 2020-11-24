---
title: ICorDebugSymbolProvider Arabirimi
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
ms.openlocfilehash: ff1f39be3d3db43f70cfa4a0711a3f42c180bc1a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672090"
---
# <a name="icordebugsymbolprovider-interface"></a><span data-ttu-id="e83a9-102">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e83a9-102">ICorDebugSymbolProvider Interface</span></span>

<span data-ttu-id="e83a9-103">Hata ayıklama sembolü bilgilerini almak için kullanılabilecek yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e83a9-103">Provides methods that can be used to retrieve debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e83a9-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e83a9-104">Methods</span></span>  
  
|<span data-ttu-id="e83a9-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e83a9-105">Method</span></span>|<span data-ttu-id="e83a9-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e83a9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e83a9-107">GetAssemblyImageBytes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e83a9-107">GetAssemblyImageBytes Method</span></span>](icordebugsymbolprovider-getassemblyimagebytes-method.md)|<span data-ttu-id="e83a9-108">Birleştirilen derlemede göreli bir sanal adres (RVA) verilen birleştirilmiş bir derlemeden verileri okur.</span><span class="sxs-lookup"><span data-stu-id="e83a9-108">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>|  
|[<span data-ttu-id="e83a9-109">GetAssemblyImageMetadata Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e83a9-109">GetAssemblyImageMetadata Method</span></span>](icordebugsymbolprovider-getassemblyimagemetadata-method.md)|<span data-ttu-id="e83a9-110">Birleştirilmiş bir derlemeden meta verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="e83a9-110">Returns the metadata from a merged assembly.</span></span>|  
|[<span data-ttu-id="e83a9-111">GetCodeRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e83a9-111">GetCodeRange Method</span></span>](icordebugsymbolprovider-getcoderange-method.md)|<span data-ttu-id="e83a9-112">Bir yöntemde göreli bir sanal adres (RVA) verilen yöntem başlangıç adresini ve boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="e83a9-112">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>|  
|[<span data-ttu-id="e83a9-113">GetInstanceFieldSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e83a9-113">GetInstanceFieldSymbols Method</span></span>](icordebugsymbolprovider-getinstancefieldsymbols-method.md)|<span data-ttu-id="e83a9-114">TypeSpec imzasına karşılık gelen örnek alanı sembollerini alır.</span><span class="sxs-lookup"><span data-stu-id="e83a9-114">Gets the instance field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="e83a9-115">GetMergedAssemblyRecords Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e83a9-115">GetMergedAssemblyRecords Method</span></span>](icordebugsymbolprovider-getmergedassemblyrecords-method.md)|<span data-ttu-id="e83a9-116">Tüm birleştirilmiş derlemelerin sembol kayıtlarını alır.</span><span class="sxs-lookup"><span data-stu-id="e83a9-116">Gets the symbol records for all the merged assemblies.</span></span>|  
|[<span data-ttu-id="e83a9-117">GetMethodLocalSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e83a9-117">GetMethodLocalSymbols Method</span></span>](icordebugsymbolprovider-getmethodlocalsymbols-method.md)|<span data-ttu-id="e83a9-118">Yöntemin yerel sembollerini, bu yöntemin göreli sanal adresi (RVA) verildiğinde alır.</span><span class="sxs-lookup"><span data-stu-id="e83a9-118">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="e83a9-119">GetMethodParameterSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e83a9-119">GetMethodParameterSymbols Method</span></span>](icordebugsymbolprovider-getmethodparametersymbols-method.md)|<span data-ttu-id="e83a9-120">Yöntemin parametre sembollerini, bu yöntemin göreli sanal adresi (RVA) verilen şekilde alır.</span><span class="sxs-lookup"><span data-stu-id="e83a9-120">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="e83a9-121">GetMethodProps Metodu</span><span class="sxs-lookup"><span data-stu-id="e83a9-121">GetMethodProps Method</span></span>](icordebugsymbolprovider-getmethodprops-method.md)|<span data-ttu-id="e83a9-122">Yöntemin meta veri belirteci ve bu yöntemde göreli bir sanal adres (RVA) verilen genel parametreleriyle ilgili bilgiler gibi Yöntem özellikleriyle ilgili bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="e83a9-122">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>|  
|[<span data-ttu-id="e83a9-123">GetObjectSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e83a9-123">GetObjectSize Method</span></span>](icordebugsymbolprovider-getobjectsize-method.md)|<span data-ttu-id="e83a9-124">Nesnelerin TypeSpec imzasına göre nesne boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="e83a9-124">Returns the object size for an object based on its typespec signature.</span></span>|  
|[<span data-ttu-id="e83a9-125">GetStaticFieldSymbols Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e83a9-125">GetStaticFieldSymbols Method</span></span>](icordebugsymbolprovider-getstaticfieldsymbols-method.md)|<span data-ttu-id="e83a9-126">TypeSpec imzasına karşılık gelen statik alan sembollerini alır.</span><span class="sxs-lookup"><span data-stu-id="e83a9-126">Gets the static field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="e83a9-127">GetTypeProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e83a9-127">GetTypeProps Method</span></span>](icordebugsymbolprovider-gettypeprops-method.md)|<span data-ttu-id="e83a9-128">Bir vtable içindeki göreli bir sanal adres (RVA) verilen genel parametrelerinin imza sayısı gibi bir türün özellikleri hakkında bilgi döndürür.</span><span class="sxs-lookup"><span data-stu-id="e83a9-128">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e83a9-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e83a9-129">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e83a9-130">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e83a9-130">This interface is available with .NET Native only.</span></span> <span data-ttu-id="e83a9-131">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="e83a9-131">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e83a9-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e83a9-132">Requirements</span></span>  

 <span data-ttu-id="e83a9-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e83a9-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e83a9-134">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e83a9-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e83a9-135">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e83a9-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e83a9-136">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e83a9-136">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e83a9-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e83a9-137">See also</span></span>

- [<span data-ttu-id="e83a9-138">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e83a9-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e83a9-139">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e83a9-139">Debugging</span></span>](index.md)
