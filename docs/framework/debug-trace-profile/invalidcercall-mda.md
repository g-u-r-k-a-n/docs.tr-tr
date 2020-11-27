---
title: invalidCERCall MDA
description: Kısıtlanmış yürütme bölgesi (CER) grafiğinde geçersiz bir çağrı varsa etkinleştirilen ınvalidcercall yönetilen hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin.
ms.date: 03/30/2017
helpviewer_keywords:
- invalid CER calls
- InvalidCERCall MDA
- MDAs (managed debugging assistants), CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: c4577410-602e-44e5-9dab-fea7c55bcdfe
ms.openlocfilehash: 6f0d9d8e3059729098975080224999d0c0fac46e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272663"
---
# <a name="invalidcercall-mda"></a><span data-ttu-id="f47d9-103">invalidCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="f47d9-103">invalidCERCall MDA</span></span>

<span data-ttu-id="f47d9-104">`invalidCERCall`Yönetilen hata ayıklama Yardımcısı (MDA), güvenilirlik sözleşmesi olmayan bir yönteme veya aşırı derecede zayıf bir sözleşmeye sahip olan kısıtlı yürütme bölgesi (cer) grafiğinde bir çağrı olduğunda etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f47d9-104">The `invalidCERCall` managed debugging assistant (MDA) is activated when there is a call within the constrained execution region (CER) graph to a method that has no reliability contract or an excessively weak contract.</span></span> <span data-ttu-id="f47d9-105">Zayıf bir sözleşme, en kötü durum durumu bozulmasının çağrıya geçirilen örnekten daha büyük kapsam olduğunu bildiren bir sözleşmedir, yani <xref:System.AppDomain> veya işlem durumu bozulabilir veya BIR cer içinde çağrıldığında her zaman kesin bir şekilde oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="f47d9-105">A weak contract is a contract that declares that the worst case state corruption is of greater scope than the instance passed to the call, that is, the <xref:System.AppDomain> or process state may become corrupted or that its result is not always deterministically computable when called within a CER.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f47d9-106">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="f47d9-106">Symptoms</span></span>  

 <span data-ttu-id="f47d9-107">Bir CER 'de kod yürütürken beklenmedik sonuçlar.</span><span class="sxs-lookup"><span data-stu-id="f47d9-107">Unexpected results when executing code in a CER.</span></span> <span data-ttu-id="f47d9-108">Belirtiler özel değildir.</span><span class="sxs-lookup"><span data-stu-id="f47d9-108">The symptoms are not specific.</span></span> <span data-ttu-id="f47d9-109"><xref:System.OutOfMemoryException> <xref:System.Threading.ThreadAbortException> Bu, çalışma zamanı bir süre önce hazırlanmadığından veya çalışma zamanında özel durumlarla korunmadığından, güvenilir olmayan yönteme yapılan çağrıda beklenmedik, bir veya başka bir özel durum olabilir <xref:System.Threading.ThreadAbortException> .</span><span class="sxs-lookup"><span data-stu-id="f47d9-109">They could be an unexpected <xref:System.OutOfMemoryException>, a <xref:System.Threading.ThreadAbortException>, or other exceptions at the call into the unreliable method because the runtime did not prepare it ahead of time or protect it from <xref:System.Threading.ThreadAbortException> exceptions at run time.</span></span> <span data-ttu-id="f47d9-110">Daha büyük bir tehdit, çalışma zamanında yönteminden kaynaklanan herhangi bir özel durumun <xref:System.AppDomain> veya işlemin BIR cer hedefi olan kararsız bir durumda kalmasını sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="f47d9-110">A greater threat is that any exception resulting from the method at run time could leave the <xref:System.AppDomain> or process in an unstable state, which is contrary to the objective of a CER.</span></span> <span data-ttu-id="f47d9-111">Bir CER 'nin oluşturulma nedeni, bu gibi durum bozukluklarının önüne girmaktır.</span><span class="sxs-lookup"><span data-stu-id="f47d9-111">The reason a CER is created is to avoid state corruptions such as this.</span></span> <span data-ttu-id="f47d9-112">Tutarlı durumun tanımı uygulamalar arasında farklı olduğundan, bozuk durum belirtileri uygulamaya özgüdür.</span><span class="sxs-lookup"><span data-stu-id="f47d9-112">The symptoms of corrupt state are application specific because the definition of consistent state is different between applications.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f47d9-113">Nedeni</span><span class="sxs-lookup"><span data-stu-id="f47d9-113">Cause</span></span>  

 <span data-ttu-id="f47d9-114">Bir CER içindeki kod, bir işlev olmadan veya bir <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> cer 'de çalışan ile uyumlu olmayan zayıf bir işlevi çağırıyor.</span><span class="sxs-lookup"><span data-stu-id="f47d9-114">Code within a CER is calling a function with no <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> or with a weak <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> that is not compatible with running in a CER.</span></span>  
  
 <span data-ttu-id="f47d9-115">Güvenilirlik sözleşmesi sözdizimi açısından, zayıf bir sözleşme, bir <xref:System.Runtime.ConstrainedExecution.Consistency> numaralandırma değeri belirtmeyen veya <xref:System.Runtime.ConstrainedExecution.Consistency> , ya da değerini belirten bir anlaşmadır <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess> <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain> <xref:System.Runtime.ConstrainedExecution.Cer.None> .</span><span class="sxs-lookup"><span data-stu-id="f47d9-115">In terms of reliability contract syntax, a weak contract is a contract that does not specify a <xref:System.Runtime.ConstrainedExecution.Consistency> enumeration value or specifies a <xref:System.Runtime.ConstrainedExecution.Consistency> value of <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>, <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>, or <xref:System.Runtime.ConstrainedExecution.Cer.None>.</span></span> <span data-ttu-id="f47d9-116">Bu koşullardan herhangi biri, olarak adlandırılan kodun, CER 'deki diğer kodun çalışmalarını, tutarlı durum sağlamak üzere engelleyebileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f47d9-116">Any of these conditions indicates that the code called may impede the efforts of the other code in the CER to maintain consistent state.</span></span>  <span data-ttu-id="f47d9-117">CERs, kodun hataları çok belirleyici bir şekilde ele almasını sağlar, böylece uygulama için önemli olan iç ınvaryantları koruyun ve bellek dışı özel durumlar gibi geçici hatalar halinde çalışmaya devam etmesine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="f47d9-117">CERs allow code to treat errors in a very deterministic manner, maintaining internal invariants that are important to the application and allowing it to continue running in the face of transient errors such as out-of-memory exceptions.</span></span>  
  
 <span data-ttu-id="f47d9-118">Bu MDA ' ın etkinleştirilmesi, CER 'de çağrılan yöntemin çağırıcının beklemediği veya bozulan ya da kurtarılamayan veya kurtarılamaz bir şekilde başarısız olmasına neden olduğunu gösterir <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="f47d9-118">The activation of this MDA indicates a possibility the method being called in the CER can fail in a way that the caller did not expect or that leaves the <xref:System.AppDomain> or process state corrupted or unrecoverable.</span></span> <span data-ttu-id="f47d9-119">Kuşkusuz, çağrılan kod doğru şekilde yürütülemeyebilir ve sorun yalnızca eksik bir anlaşmada olur.</span><span class="sxs-lookup"><span data-stu-id="f47d9-119">Of course, the called code might execute correctly and the problem is simply a missing contract.</span></span> <span data-ttu-id="f47d9-120">Ancak, güvenilir kod yazma ile ilgili sorunlar hafif ve bir sözleşmenin yokluğu iyi bir göstergedir ve kod doğru bir şekilde yürütülmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="f47d9-120">However, the issues involved in writing reliable code are subtle and the absence of a contract is a good indicator the code might not execute correctly.</span></span> <span data-ttu-id="f47d9-121">Sözleşmeler, programcının güvenilir bir şekilde kodlandığı ve ayrıca bu garantilere kodun gelecekteki düzeltmeleri içinde değişmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="f47d9-121">The contracts are indicators that the programmer has coded reliably and also promises that these guarantees will not change in future revisions of the code.</span></span>  <span data-ttu-id="f47d9-122">Diğer bir deyişle, sözleşmelerin yalnızca uygulama ayrıntıları değil, amaç bildirimleri vardır.</span><span class="sxs-lookup"><span data-stu-id="f47d9-122">That is, the contracts are declarations of intent and not just implementation details.</span></span>  
  
 <span data-ttu-id="f47d9-123">Zayıf veya varolmayan bir sözleşmeye sahip herhangi bir yöntem potansiyel olarak çok sayıda öngörülemeyen şekilde başarısız olabileceğinden, çalışma zamanı, yavaş JıT derleme, genel türler sözlüğü popülasyonu veya iş parçacığı arızalarıyla tanıtılan yöntemden kendi öngörülemeyen hatalarından hiçbirini kaldırmaya çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="f47d9-123">Because any method with a weak or nonexistent contract can potentially fail in many unpredictable ways, the runtime does not attempt to remove any of its own unpredictable failures from the method  that are introduced by lazy JIT-compiling, generics dictionary population, or thread aborts, for example.</span></span> <span data-ttu-id="f47d9-124">Diğer bir deyişle, bu MDA etkin olduğunda, çalışma zamanının tanımlanmakta olan CER 'ye çağrılan yöntemi içermediğini belirtir; Bu alt ağacı hazırlamaya devam etmek olası hatayı maskelemek için bu düğümde çağrı grafı sonlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="f47d9-124">That is, when this MDA is activated, it indicates that the runtime did not include the called method in the CER being defined; the call graph was terminated at this node because continuing to prepare this subtree would help mask the potential error.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="f47d9-125">Çözüm</span><span class="sxs-lookup"><span data-stu-id="f47d9-125">Resolution</span></span>  

 <span data-ttu-id="f47d9-126">İşleve geçerli bir güvenilirlik sözleşmesi ekleyin veya bu işlev çağrısını kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="f47d9-126">Add a valid reliability contract to the function or avoid using that function call.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f47d9-127">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="f47d9-127">Effect on the Runtime</span></span>  

 <span data-ttu-id="f47d9-128">Bir CER 'den zayıf bir sözleşmeyi çağırma etkisi, işlemlerini tamamlamaya yönelik CER hatası olabilir.</span><span class="sxs-lookup"><span data-stu-id="f47d9-128">The effect of calling a weak contract from a CER could be the CER failure to complete its operations.</span></span> <span data-ttu-id="f47d9-129">Bu işlem durumu bozulmasına yol açabilir <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="f47d9-129">This could lead to corruption of the <xref:System.AppDomain> process state.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f47d9-130">Çıkış</span><span class="sxs-lookup"><span data-stu-id="f47d9-130">Output</span></span>  

 <span data-ttu-id="f47d9-131">Bu MDA 'ın örnek çıktısı aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f47d9-131">The following is sample output from this MDA.</span></span>  
  
 `Method 'MethodWithCer', while executing within a constrained execution region, makes a call at IL offset 0x000C to 'MethodWithWeakContract', which does not have a sufficiently strong reliability contract and might cause non-deterministic results.`  
  
## <a name="configuration"></a><span data-ttu-id="f47d9-132">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f47d9-132">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f47d9-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f47d9-133">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution>
- [<span data-ttu-id="f47d9-134">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="f47d9-134">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
