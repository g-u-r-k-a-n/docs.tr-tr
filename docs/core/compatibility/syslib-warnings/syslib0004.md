---
title: SYSLIB0004 uyarısı
description: Derleme zamanı uyarı SYSLIB0004 üreten kullanım dışı meler hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 03be8bb54f71f74ed94ee2c3f8489397ae1e99b5
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596561"
---
# <a name="syslib0004-the-constrained-execution-region-cer-feature-is-not-supported"></a><span data-ttu-id="5511c-103">SYSLIB0004: kısıtlanmış yürütme bölgesi (CER) özelliği desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="5511c-103">SYSLIB0004: The constrained execution region (CER) feature is not supported</span></span>

<span data-ttu-id="5511c-104">[Kısıtlı yürütme bölgeleri (cer)](../../../framework/performance/constrained-execution-regions.md) özelliği yalnızca .NET Framework desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5511c-104">The [Constrained execution regions (CER)](../../../framework/performance/constrained-execution-regions.md) feature is supported only in .NET Framework.</span></span> <span data-ttu-id="5511c-105">Bu nedenle, CER ile ilgili çeşitli API 'Ler, .NET 5,0 ' den itibaren kullanılmıyor olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="5511c-105">As such, various CER-related APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="5511c-106">Bu API 'Lerin kullanılması, `SYSLIB0004` derleme zamanında uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5511c-106">Using these APIs generates warning `SYSLIB0004` at compile time.</span></span>

<span data-ttu-id="5511c-107">Aşağıdaki CER ile ilgili API 'Ler artık kullanılmıyor:</span><span class="sxs-lookup"><span data-stu-id="5511c-107">The following CER-related APIs are obsolete:</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup(System.Runtime.CompilerServices.RuntimeHelpers.TryCode,System.Runtime.CompilerServices.RuntimeHelpers.CleanupCode,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegionsNoOP?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareContractedDelegate(System.Delegate)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ProbeForSufficientStack?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Cer?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Consistency?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="5511c-108">Geçici Çözümler</span><span class="sxs-lookup"><span data-stu-id="5511c-108">Workarounds</span></span>

- <span data-ttu-id="5511c-109">Bir metoda bir CER özniteliği uyguladıysanız, özniteliğini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="5511c-109">If you have applied a CER attribute to a method, remove the attribute.</span></span> <span data-ttu-id="5511c-110">Bu özniteliklerin, .NET 5,0 ve sonraki sürümlerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="5511c-110">These attributes have no effect in .NET 5.0 and later versions.</span></span>

  ```csharp
  // REMOVE the attribute below.
  [ReliabilityContract(Consistency.WillNotCorruptState, Cer.Success)]
  public void DoSomething()
  {
  }

  // REMOVE the attribute below.
  [PrePrepareMethod]
  public void DoSomething()
  {
  }
  ```

- <span data-ttu-id="5511c-111">Veya öğesini çağırıyorsanız `RuntimeHelpers.ProbeForSufficientStack` `RuntimeHelpers.PrepareContractedDelegate` , çağrıyı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="5511c-111">If you are calling `RuntimeHelpers.ProbeForSufficientStack` or `RuntimeHelpers.PrepareContractedDelegate`, remove the call.</span></span> <span data-ttu-id="5511c-112">Bu çağrıların, .NET 5,0 ve sonraki sürümlerde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="5511c-112">These calls have no effect in .NET 5.0 and later versions.</span></span>

  ```csharp
  public void DoSomething()
  {
      // REMOVE the call below.
      RuntimeHelpers.ProbeForSufficientStack();

      // (Remainder of your method logic here.)
  }
  ```

- <span data-ttu-id="5511c-113">Öğesini çağırıyorsanız `RuntimeHelpers.PrepareConstrainedRegions` , çağrıyı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="5511c-113">If you are calling `RuntimeHelpers.PrepareConstrainedRegions`, remove the call.</span></span> <span data-ttu-id="5511c-114">Bu çağrının, .NET 5,0 ve sonraki sürümlerde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="5511c-114">This call has no effect in .NET 5.0 and later versions.</span></span>

  ```csharp
  public void DoSomething_Old()
  {
      // REMOVE the call below.
      RuntimeHelpers.PrepareConstrainedRegions();
      try
      {
          // try code
      }
      finally
      {
          // cleanup code
      }
  }

  public void DoSomething_Corrected()
  {
      // There is no call to PrepareConstrainedRegions. It's a normal try / finally block.

      try
      {
          // try code
      }
      finally
      {
          // cleanup code
      }
  }
  ```

- <span data-ttu-id="5511c-115">Öğesini çağırıyorsanız `RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup` , çağrıyı standart bir _try/catch/finally_ bloğu ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5511c-115">If you are calling `RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup`, replace the call with a standard _try / catch / finally_ block.</span></span>

  ```csharp
  // The sample below produces warning SYSLIB0004.
  public void DoSomething_Old()
  {
      RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup(MyTryCode, MyCleanupCode, null);
  }
  public void MyTryCode(object state) { /* try code */ }
  public void MyCleanupCode(object state, bool exceptionThrown) { /* cleanup code */ }

  // The corrected sample below does not produce warning SYSLIB0004.
  public void DoSomething_Corrected()
  {
      try
      {
          // try code
      }
      catch (Exception ex)
      {
          // exception handling code
      }
      finally
      {
          // cleanup code
      }
  }
  ```

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="5511c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5511c-116">See also</span></span>

- [<span data-ttu-id="5511c-117">Kısıtlı yürütme bölgeleri</span><span class="sxs-lookup"><span data-stu-id="5511c-117">Constrained execution regions</span></span>](../../../framework/performance/constrained-execution-regions.md)
