---
description: 'Hakkında daha fazla bilgi edinin: ICorProfilerInfo2::D oStackSnapshot yöntemi'
title: ICorProfilerInfo2::DoStackSnapshot Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.DoStackSnapshot
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::DoStackSnapshot
helpviewer_keywords:
- ICorProfilerInfo2::DoStackSnapshot method [.NET Framework profiling]
- DoStackSnapshot method [.NET Framework profiling]
ms.assetid: 287b11e9-7c52-4a13-ba97-751203fa97f4
topic_type:
- apiref
ms.openlocfilehash: e30e11dfe04da1e7a5adfef004036507b724963d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753256"
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a><span data-ttu-id="050a8-103">ICorProfilerInfo2::DoStackSnapshot Yöntemi</span><span class="sxs-lookup"><span data-stu-id="050a8-103">ICorProfilerInfo2::DoStackSnapshot Method</span></span>

<span data-ttu-id="050a8-104">Belirtilen iş parçacığı için yığındaki yönetilen çerçevelere kılavuzluk eder ve geri çağırma yoluyla profil oluşturucuya bilgi gönderir.</span><span class="sxs-lookup"><span data-stu-id="050a8-104">Walks the managed frames on the stack for the specified thread, and sends information to the profiler through a callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="050a8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="050a8-105">Syntax</span></span>  
  
```cpp  
HRESULT DoStackSnapshot(  
    [in] ThreadID thread,  
    [in] StackSnapshotCallback *callback,  
    [in] ULONG32 infoFlags,  
    [in] void *clientData,  
    [in, size_is(contextSize), length_is(contextSize)] BYTE context[],  
    [in] ULONG32 contextSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="050a8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="050a8-106">Parameters</span></span>  

 `thread`  
 <span data-ttu-id="050a8-107">'ndaki Hedef iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="050a8-107">[in] The ID of the target thread.</span></span>  
  
 <span data-ttu-id="050a8-108">İçinde null geçirme `thread` , geçerli iş parçacığının bir anlık görüntüsünü verir.</span><span class="sxs-lookup"><span data-stu-id="050a8-108">Passing null in `thread` yields a snapshot of the current thread.</span></span> <span data-ttu-id="050a8-109">Farklı bir `ThreadID` iş parçacığından biri geçirilirse, ortak dil çalışma zamanı (CLR) bu iş parçacığını askıya alır, anlık görüntüyü gerçekleştirir ve sürdürür.</span><span class="sxs-lookup"><span data-stu-id="050a8-109">If a `ThreadID` of a different thread is passed, the common language runtime (CLR) suspends that thread, performs the snapshot, and resumes.</span></span>  
  
 `callback`  
 <span data-ttu-id="050a8-110">'ndaki Profil oluşturucuyu, yönetilen her çerçeve ve her yönetilmeyen çerçeve çalıştırması hakkında bilgi sağlamak için CLR tarafından çağrılan [StackSnapshotCallback](stacksnapshotcallback-function.md) yönteminin uygulamasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="050a8-110">[in] A pointer to the implementation of the [StackSnapshotCallback](stacksnapshotcallback-function.md) method, which is called by the CLR to provide the profiler with information on each managed frame and each run of unmanaged frames.</span></span>  
  
 <span data-ttu-id="050a8-111">`StackSnapshotCallback`Yöntemi profil oluşturucu yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="050a8-111">The `StackSnapshotCallback` method is implemented by the profiler writer.</span></span>  
  
 `infoFlags`  
 <span data-ttu-id="050a8-112">'ndaki Tarafından her çerçeve için geri geçirilecek veri miktarını belirten [COR_PRF_SNAPSHOT_INFO](cor-prf-snapshot-info-enumeration.md) numaralandırması değeri `StackSnapshotCallback` .</span><span class="sxs-lookup"><span data-stu-id="050a8-112">[in] A value of the [COR_PRF_SNAPSHOT_INFO](cor-prf-snapshot-info-enumeration.md) enumeration, which specifies the amount of data to be passed back for each frame by `StackSnapshotCallback`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="050a8-113">'ndaki İstemci verilerine yönelik bir işaretçi, `StackSnapshotCallback` geri çağırma işlevine doğrudan geçirilir.</span><span class="sxs-lookup"><span data-stu-id="050a8-113">[in] A pointer to the client data, which is passed straight through to the `StackSnapshotCallback` callback function.</span></span>  
  
 `context`  
 <span data-ttu-id="050a8-114">'ndaki `CONTEXT` Yığın ilerlemesini temel almak için kullanılan Win32 yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="050a8-114">[in] A pointer to a Win32 `CONTEXT` structure, which is used to seed the stack walk.</span></span> <span data-ttu-id="050a8-115">Win32 `CONTEXT` yapısı, CPU yazmaçlarının değerlerini içerir ve zaman içinde belirli bir anda CPU 'nun durumunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="050a8-115">The Win32 `CONTEXT` structure contains values of the CPU registers and represents the state of the CPU at a particular moment in time.</span></span>  
  
 <span data-ttu-id="050a8-116">Çekirdek, yığının en üstünde yönetilmeyen yardımcı kod olması halinde CLR 'nin yığın ilerleme durumunu belirlemesine yardımcı olur. Aksi takdirde, çekirdek yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="050a8-116">The seed helps the CLR determine where to begin the stack walk, if the top of the stack is unmanaged helper code; otherwise, the seed is ignored.</span></span> <span data-ttu-id="050a8-117">Zaman uyumsuz bir ilerleme için çekirdek sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="050a8-117">A seed must be supplied for an asynchronous walk.</span></span> <span data-ttu-id="050a8-118">Zaman uyumlu bir adım yapıyorsanız, hiçbir çekirdek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="050a8-118">If you are doing a synchronous walk, no seed is necessary.</span></span>  
  
 <span data-ttu-id="050a8-119">`context`Parametresi yalnızca COR_PRF_SNAPSHOT_CONTEXT bayrağı parametreye geçirilmemişse geçerlidir `infoFlags` .</span><span class="sxs-lookup"><span data-stu-id="050a8-119">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in the `infoFlags` parameter.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="050a8-120">'ndaki `CONTEXT` Parametrenin başvurduğu yapının boyutu `context` .</span><span class="sxs-lookup"><span data-stu-id="050a8-120">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="050a8-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="050a8-121">Remarks</span></span>  

 <span data-ttu-id="050a8-122">İçin null geçirme `thread` , geçerli iş parçacığının bir anlık görüntüsünü verir.</span><span class="sxs-lookup"><span data-stu-id="050a8-122">Passing null for `thread` yields a snapshot of the current thread.</span></span> <span data-ttu-id="050a8-123">Yalnızca hedef iş parçacığı zaman askıya alınırsa, anlık görüntüler diğer iş parçacıklarından alınabilir.</span><span class="sxs-lookup"><span data-stu-id="050a8-123">Snapshots can be taken of other threads only if the target thread is suspended at the time.</span></span>  
  
 <span data-ttu-id="050a8-124">Profil Oluşturucu yığına ilerlemek istediğinde, çağırır `DoStackSnapshot` .</span><span class="sxs-lookup"><span data-stu-id="050a8-124">When the profiler wants to walk the stack, it calls `DoStackSnapshot`.</span></span> <span data-ttu-id="050a8-125">CLR Bu çağrıdan geri dönüşden önce, `StackSnapshotCallback` yığın üzerinde her yönetilen çerçeve (veya yönetilmeyen çerçeveler) için birkaç kez bir kez çağrı yapılır.</span><span class="sxs-lookup"><span data-stu-id="050a8-125">Before the CLR returns from that call, it calls your `StackSnapshotCallback` several times, once for each managed frame (or run of unmanaged frames) on the stack.</span></span> <span data-ttu-id="050a8-126">Yönetilmeyen çerçevelerle karşılaşıldığında, bunları kendiniz yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="050a8-126">When unmanaged frames are encountered, you must walk them yourself.</span></span>  
  
 <span data-ttu-id="050a8-127">Yığının hangi sıraya gönderildiği sırası, çerçevelerin yığına nasıl itileceği, ana (ilk itilmiş) çerçevenin en sonda yer aldığı sıra.</span><span class="sxs-lookup"><span data-stu-id="050a8-127">The order in which the stack is walked is the reverse of how the frames were pushed onto the stack: leaf (last-pushed) frame first, main (first-pushed) frame last.</span></span>  
  
 <span data-ttu-id="050a8-128">Profil oluşturucunun yönetilen yığınları izlenecek şekilde programlamanın nasıl yapılacağı hakkında daha fazla bilgi için, bkz. [.NET Framework 2,0: temel bilgiler ve daha fazlası Için Profiler Stack](/previous-versions/dotnet/articles/bb264782(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="050a8-128">For more information about how to program the profiler to walk managed stacks, see [Profiler Stack Walking in the .NET Framework 2.0: Basics and Beyond](/previous-versions/dotnet/articles/bb264782(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="050a8-129">Aşağıdaki bölümlerde açıklandığı gibi bir yığın adım zaman uyumlu veya zaman uyumsuz olabilir.</span><span class="sxs-lookup"><span data-stu-id="050a8-129">A stack walk can be synchronous or asynchronous, as explained in the following sections.</span></span>  
  
## <a name="synchronous-stack-walk"></a><span data-ttu-id="050a8-130">Zaman uyumlu yığın Ilerleme</span><span class="sxs-lookup"><span data-stu-id="050a8-130">Synchronous Stack Walk</span></span>  

 <span data-ttu-id="050a8-131">Zaman uyumlu bir yığın, geri çağırmaya yanıt olarak geçerli iş parçacığının yığınını yürüter.</span><span class="sxs-lookup"><span data-stu-id="050a8-131">A synchronous stack walk involves walking the stack of the current thread in response to a callback.</span></span> <span data-ttu-id="050a8-132">Dengeli dağıtım veya askıya alma gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="050a8-132">It does not require seeding or suspending.</span></span>  
  
 <span data-ttu-id="050a8-133">Profil oluşturucunun [ICorProfilerCallback](icorprofilercallback-interface.md) (veya [ICorProfilerCallback2](icorprofilercallback2-interface.md)) yöntemlerinden birini çağıran clr 'ye yanıt olarak, `DoStackSnapshot` geçerli iş parçacığının yığınını göstermek için çağırdığınız zaman zaman uyumlu bir çağrı yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="050a8-133">You make a synchronous call when, in response to the CLR calling one of your profiler's [ICorProfilerCallback](icorprofilercallback-interface.md) (or [ICorProfilerCallback2](icorprofilercallback2-interface.md)) methods, you call `DoStackSnapshot` to walk the stack of the current thread.</span></span> <span data-ttu-id="050a8-134">Bu, yığının [ICorProfilerCallback:: Objectalkonumlandırılan](icorprofilercallback-objectallocated-method.md)gibi bir bildirimde nasıl göründüğünü görmek istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="050a8-134">This is useful when you want to see what the stack looks like at a notification such as [ICorProfilerCallback::ObjectAllocated](icorprofilercallback-objectallocated-method.md).</span></span> <span data-ttu-id="050a8-135">Yalnızca `DoStackSnapshot` yönteminizin içinden çağrı `ICorProfilerCallback` yapın, ve parametrelerinde null değeri geçirerek `context` `thread` .</span><span class="sxs-lookup"><span data-stu-id="050a8-135">You just call `DoStackSnapshot` from within your `ICorProfilerCallback` method, passing null in the `context` and `thread` parameters.</span></span>  
  
## <a name="asynchronous-stack-walk"></a><span data-ttu-id="050a8-136">Zaman uyumsuz yığın Ilerleme</span><span class="sxs-lookup"><span data-stu-id="050a8-136">Asynchronous Stack Walk</span></span>  

 <span data-ttu-id="050a8-137">Zaman uyumsuz bir yığın, farklı bir iş parçacığının yığınını yürüyerek veya geçerli iş parçacığının yığınını yürüyerek geri çağırmaya yanıt vermez, ancak geçerli iş parçacığının yönerge işaretçisini ele alarak.</span><span class="sxs-lookup"><span data-stu-id="050a8-137">An asynchronous stack walk entails walking the stack of a different thread, or walking the stack of the current thread, not in response to a callback, but by hijacking the current thread's instruction pointer.</span></span> <span data-ttu-id="050a8-138">Zaman uyumsuz bir izlenecek yol, yığının en üstünde platform Invoke (PInvoke) veya COM çağrısının bir parçası olmayan yönetilmeyen kod ise ve CLR 'nin kendisindeki yardımcı kod ise çekirdek gerektirir.</span><span class="sxs-lookup"><span data-stu-id="050a8-138">An asynchronous walk requires a seed if the top of the stack is unmanaged code that is not part of a platform invoke (PInvoke) or COM call, but helper code in the CLR itself.</span></span> <span data-ttu-id="050a8-139">Örneğin, tam zamanında (JıT) derleme veya çöp toplama yapan kod yardımcı koddur.</span><span class="sxs-lookup"><span data-stu-id="050a8-139">For example, code that does just-in-time (JIT) compiling or garbage collection is helper code.</span></span>  
  
 <span data-ttu-id="050a8-140">Hedef iş parçacığını doğrudan askıya alarak ve en üstteki yönetilen çerçeveyi bulana kadar kendi yığınını yürüyerek bir çekirdek elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="050a8-140">You obtain a seed by directly suspending the target thread and walking its stack yourself, until you find the topmost managed frame.</span></span> <span data-ttu-id="050a8-141">Hedef iş parçacığı askıya alındıktan sonra, hedef iş parçacığının geçerli kayıt bağlamını alın.</span><span class="sxs-lookup"><span data-stu-id="050a8-141">After the target thread is suspended, get the target thread's current register context.</span></span> <span data-ttu-id="050a8-142">Sonra, YAZMAÇ bağlamının [ICorProfilerInfo:: GetFunctionFromIP](icorprofilerinfo-getfunctionfromip-method.md) öğesini çağırarak yönetilmeyen koda işaret ettiğini ve `FunctionID` sıfıra eşit bir değere döndürürse, çerçevenin yönetilmeyen kod olduğunu saptayın.</span><span class="sxs-lookup"><span data-stu-id="050a8-142">Next, determine whether the register context points to unmanaged code by calling [ICorProfilerInfo::GetFunctionFromIP](icorprofilerinfo-getfunctionfromip-method.md) — if it returns a `FunctionID` equal to zero, the frame is unmanaged code.</span></span> <span data-ttu-id="050a8-143">Şimdi, ilk yönetilen çerçeveye ulaşana kadar yığına ilerleme uygulayın ve ardından bu çerçeveye ait yazmaç bağlamına göre çekirdek bağlamını hesaplayın.</span><span class="sxs-lookup"><span data-stu-id="050a8-143">Now, walk the stack until you reach the first managed frame, and then calculate the seed context based on the register context for that frame.</span></span>  
  
 <span data-ttu-id="050a8-144">`DoStackSnapshot`Zaman uyumsuz yığın Yürüme başlamak için çekirdek bağlamınıza çağrı yapın.</span><span class="sxs-lookup"><span data-stu-id="050a8-144">Call `DoStackSnapshot` with your seed context to begin the asynchronous stack walk.</span></span> <span data-ttu-id="050a8-145">Bir çekirdek sağlamadıysanız, `DoStackSnapshot` yığının en üstünde yönetilen çerçeveleri atlayabilir ve sonuç olarak size tamamlanmamış bir yığın yürüme olanağı verecektir.</span><span class="sxs-lookup"><span data-stu-id="050a8-145">If you do not supply a seed, `DoStackSnapshot` might skip managed frames at the top of the stack and, consequently, will give you an incomplete stack walk.</span></span> <span data-ttu-id="050a8-146">Çekirdek sağlarsanız, JıT ile derlenen veya yerel görüntü Oluşturucu (Ngen.exe) tarafından oluşturulan kodu işaret etmelidir; Aksi takdirde, `DoStackSnapshot` CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX hata kodunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="050a8-146">If you do supply a seed, it must point to JIT-compiled or Native Image Generator (Ngen.exe)-generated code; otherwise, `DoStackSnapshot` returns the failure code, CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX.</span></span>  
  
 <span data-ttu-id="050a8-147">Bu yönergeleri izlemeden zaman uyumsuz yığın, kilitlenmeleri veya erişim ihlallerine kolayca yol açabilir:</span><span class="sxs-lookup"><span data-stu-id="050a8-147">Asynchronous stack walks can easily cause deadlocks or access violations, unless you follow these guidelines:</span></span>  
  
- <span data-ttu-id="050a8-148">İş parçacıklarını doğrudan askıya aldığınızda, yalnızca yönetilen kodu çalıştırmayan bir iş parçacığının başka bir iş parçacığını askıya alamayacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="050a8-148">When you directly suspend threads, remember that only a thread that has never run managed code can suspend another thread.</span></span>  
  
- <span data-ttu-id="050a8-149">[ICorProfilerCallback:: threadnot](icorprofilercallback-threaddestroyed-method.md) , iş parçacığının yığın yürüme tamamlanana kadar geri çağırmada her zaman engellenir.</span><span class="sxs-lookup"><span data-stu-id="050a8-149">Always block in your [ICorProfilerCallback::ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md) callback until that thread's stack walk is complete.</span></span>  
  
- <span data-ttu-id="050a8-150">Profiler, bir atık toplamayı tetikleyebilen bir CLR işlevine çağrı yaparken bir kilit tutmayın.</span><span class="sxs-lookup"><span data-stu-id="050a8-150">Do not hold a lock while your profiler calls into a CLR function that can trigger a garbage collection.</span></span> <span data-ttu-id="050a8-151">Yani, sahip iş parçacığı çöp toplamayı tetikleyen bir çağrı yapamadığında bir kilit tutmayın.</span><span class="sxs-lookup"><span data-stu-id="050a8-151">That is, do not hold a lock if the owning thread might make a call that triggers a garbage collection.</span></span>  
  
 <span data-ttu-id="050a8-152">Ayrıca, `DoStackSnapshot` profil oluşturucunun oluşturduğu bir iş parçacığından çağırdığınızda, ayrı bir hedef iş parçacığının yığınına yol gösterecek bir kilitlenme riski de vardır.</span><span class="sxs-lookup"><span data-stu-id="050a8-152">There is also a risk of deadlock if you call `DoStackSnapshot` from a thread that your profiler has created so that you can walk the stack of a separate target thread.</span></span> <span data-ttu-id="050a8-153">Oluşturduğunuz iş parçacığı bazı `ICorProfilerInfo*` yöntemlere (dahil `DoStackSnapshot` ) GIRDIĞINDE, clr bu iş parçacığında iş parçacığı BAŞıNA, clr 'ye özgü başlatma işlemini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="050a8-153">The first time the thread you created enters certain `ICorProfilerInfo*` methods (including `DoStackSnapshot`), the CLR will perform per-thread, CLR-specific initialization on that thread.</span></span> <span data-ttu-id="050a8-154">Profil oluşturucunuz, yığınına kılavuzluk eden hedef iş parçacığını askıya alıyorsa ve bu hedef iş parçacığı bu iş parçacığı başına başlatmayı gerçekleştirmek için gerekli bir kilide gerçekleştiyse, bir kilitlenme meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="050a8-154">If your profiler has suspended the target thread whose stack you are trying to walk, and if that target thread happened to own a lock necessary for performing this per-thread initialization, a deadlock will occur.</span></span> <span data-ttu-id="050a8-155">Bu kilitlenmeyi önlemek için, `DoStackSnapshot` Profil Oluşturucu oluşturulmuş iş parçacığından, ayrı bir hedef iş parçacığı için bir ilk çağrı yapın, ancak önce hedef iş parçacığını askıya alın.</span><span class="sxs-lookup"><span data-stu-id="050a8-155">To avoid this deadlock, make an initial call into `DoStackSnapshot` from your profiler-created thread to walk a separate target thread, but do not suspend the target thread first.</span></span> <span data-ttu-id="050a8-156">Bu ilk çağrı, iş parçacığı başına başlatmanın kilitlenme olmadan tamamlanmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="050a8-156">This initial call ensures that the per-thread initialization can complete without deadlock.</span></span> <span data-ttu-id="050a8-157">`DoStackSnapshot`Başarılı olursa ve en az bir çerçeve bildirirse, bu noktadan sonra herhangi bir hedef iş parçacığını askıya almak ve `DoStackSnapshot` Bu hedef iş parçacığı yığınını göstermek için çağırmak üzere, profil oluşturucu tarafından oluşturulan iş parçacığı için güvenli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="050a8-157">If `DoStackSnapshot` succeeds and reports at least one frame, after that point, it will be safe for that profiler-created thread to suspend any target thread and call `DoStackSnapshot` to walk the stack of that target thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="050a8-158">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="050a8-158">Requirements</span></span>  

 <span data-ttu-id="050a8-159">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="050a8-159">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="050a8-160">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="050a8-160">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="050a8-161">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="050a8-161">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="050a8-162">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="050a8-162">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="050a8-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="050a8-163">See also</span></span>

- [<span data-ttu-id="050a8-164">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="050a8-164">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="050a8-165">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="050a8-165">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
