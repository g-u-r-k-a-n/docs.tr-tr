---
title: virtualCERCall MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- virtualCERCall MDA
- virtual CER calls
- constrained execution regions
- CER calls
- managed debugging assistants (MDAs), CER calls
ms.assetid: 1eb18c7a-f5e0-443f-80fb-67bfbb047da2
ms.openlocfilehash: a2112baed863b1035cbee4e956c1b6e271ff6e3c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181718"
---
# <a name="virtualcercall-mda"></a><span data-ttu-id="25e63-102">virtualCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="25e63-102">virtualCERCall MDA</span></span>
<span data-ttu-id="25e63-103">Yönetilen `virtualCERCall` hata ayıklama yardımcısı (MDA), kısıtlı bir yürütme bölgesi (CER) çağrı grafiği içindeki bir çağrı sitesinin sanal bir hedefe, yani son sanal olmayan bir yönteme veya arabirim kullanan bir çağrıya sanal çağrı anlamına geldiğini belirten bir uyarı olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="25e63-103">The `virtualCERCall` managed debugging assistant (MDA) is activated as a warning indicating that a call site within a constrained execution region (CER) call graph refers to a virtual target, that is, a virtual call to a non-final virtual method or a call using an interface.</span></span> <span data-ttu-id="25e63-104">Ortak dil çalışma süresi (CLR), bu çağrıların hedef yöntemini yalnızca ara dilden ve meta veri çözümlemesi ile tahmin edemez.</span><span class="sxs-lookup"><span data-stu-id="25e63-104">The common language runtime (CLR) cannot predict the destination method of these calls from the intermediate language and metadata analysis alone.</span></span> <span data-ttu-id="25e63-105">Sonuç olarak, çağrı ağacı CER grafiğinin bir parçası olarak hazırlanamaz ve bu alt ağaçtaki iş parçacığı iptalleri otomatik olarak engellenemez.</span><span class="sxs-lookup"><span data-stu-id="25e63-105">As a result, the call tree cannot be prepared as part of the CER graph and thread aborts in that subtree cannot be automatically blocked.</span></span> <span data-ttu-id="25e63-106">Bu MDA, arama hedefini hesaplamak için gereken ek bilgiler <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> çalışma zamanında bilindiğinde yönteme açık çağrılar kullanılarak CER'in genişletilmesi gerekebileceği durumlar konusunda uyarır.</span><span class="sxs-lookup"><span data-stu-id="25e63-106">This MDA warns of cases where a CER might need to be extended by using explicit calls to the <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> method once the additional information required to compute the call target is known at run time.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="25e63-107">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="25e63-107">Symptoms</span></span>  
 <span data-ttu-id="25e63-108">İş parçacığı iptal edildiğinde veya uygulama etki alanı kaldırılınca çalışmayan CER'ler.</span><span class="sxs-lookup"><span data-stu-id="25e63-108">CERs that do not run when a thread is aborted or an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="25e63-109">Nedeni</span><span class="sxs-lookup"><span data-stu-id="25e63-109">Cause</span></span>  
 <span data-ttu-id="25e63-110">CER, otomatik olarak hazırlanamayan sanal bir yönteme çağrı içerir.</span><span class="sxs-lookup"><span data-stu-id="25e63-110">A CER contains a call to a virtual method that cannot be prepared automatically.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="25e63-111">Çözüm</span><span class="sxs-lookup"><span data-stu-id="25e63-111">Resolution</span></span>  
 <span data-ttu-id="25e63-112">Sanal <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> yöntem için arayın.</span><span class="sxs-lookup"><span data-stu-id="25e63-112">Call <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A> for the virtual method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="25e63-113">Çalışma Süresi üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="25e63-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="25e63-114">Bu MDA'nın CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="25e63-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="25e63-115">Çıktı</span><span class="sxs-lookup"><span data-stu-id="25e63-115">Output</span></span>  
  
```output
Method 'MethodWithCer', while executing within a constrained execution region, makes a call  
at IL offset 0x0024 to 'VirtualMethod', which is virtual and cannot be prepared automatically  
at compile time. The caller must ensure this method is prepared explicitly at  
runtime before entering the constrained execution region.  
method name="VirtualMethod"  
declaringType name="VirtualCERCall+MyClass"  
  declaringModule name="mda"  
    callsite name="MethodWithCer" offset="0x0024"  
```  
  
## <a name="configuration"></a><span data-ttu-id="25e63-116">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="25e63-116">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <VirtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="25e63-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="25e63-117">Example</span></span>  
  
```csharp
class MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    virtual void VirtualMethod()  
    {  
        ...  
    }  
}  
  
class MyDerivedClass : MyClass  
{  
    [ReliabilityContract(Consistency.MayCorruptProcess, CER.None)]  
    override void VirtualMethod()  
    {  
        ...  
    }  
}  
  
void MethodWithCer(MyClass object)  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    try  
    {  
        ...  
    }  
    finally  
    {  
        // Start of the CER.  
  
        // Cannot tell at analysis time whether object is a MyClass  
        // or a MyDerivedClass, so we do not know which version of
        // VirtualMethod we are going to call.  
        object.VirtualMethod();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="25e63-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25e63-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="25e63-119">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="25e63-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="25e63-120">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="25e63-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
