---
title: JIT-Ekleme Hata Ayıklamayı Etkinleştirme
description: Hatalarla karşılaştığınızda bir işleme hata ayıklayıcı eklemek için tam zamanında (JıT) iliştirme hata ayıklamayı etkinleştirin. Belirli yöntemler veya işlevler tarafından tetiklenebilir.
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
ms.openlocfilehash: dc1c8608b0d16e618b5ad6144d492db3302532dc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273509"
---
# <a name="enabling-jit-attach-debugging"></a><span data-ttu-id="9be70-104">JIT-Ekleme Hata Ayıklamayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="9be70-104">Enabling JIT-Attach Debugging</span></span>

<span data-ttu-id="9be70-105">JıT-Attach hata ayıklaması, hatalar ile ilgili bir hata ayıklayıcıyı bir işleme iliştirirken veya belirli yöntemler veya işlevler tarafından tetikleniyorsa kullanılan tümceciktir.</span><span class="sxs-lookup"><span data-stu-id="9be70-105">JIT-attach debugging is the phrase used to describe attaching a debugger to a process when you encounter errors, or it can be triggered by specific methods or functions.</span></span>  
  
 <span data-ttu-id="9be70-106">JıT-Attach hata ayıklaması aşağıdaki hata koşulları altında kullanılır:</span><span class="sxs-lookup"><span data-stu-id="9be70-106">JIT-attach debugging is used under the following fault conditions:</span></span>  
  
- <span data-ttu-id="9be70-107">İşlenmemiş özel durumlar (hem yerel hem de yönetilen kodda).</span><span class="sxs-lookup"><span data-stu-id="9be70-107">Unhandled exceptions (in both native and managed code).</span></span>  
  
- <span data-ttu-id="9be70-108"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> Method veya [RaiseFailFastException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raisefailfastexception) Işlevi (Windows 7 ailesi).</span><span class="sxs-lookup"><span data-stu-id="9be70-108"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> method or [RaiseFailFastException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raisefailfastexception) function (Windows 7 family).</span></span>  
  
- <span data-ttu-id="9be70-109">Çalışma zamanı önemli hataları.</span><span class="sxs-lookup"><span data-stu-id="9be70-109">Runtime fatal errors.</span></span>  
  
 <span data-ttu-id="9be70-110">JıT-Attach hata ayıklaması, aşağıdaki yöntemler ve işlevlere yapılan çağrılar tarafından da tetiklenir:</span><span class="sxs-lookup"><span data-stu-id="9be70-110">JIT-attach debugging is also triggered by calls to the following methods and functions:</span></span>  
  
- <span data-ttu-id="9be70-111"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="9be70-111"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="9be70-112"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="9be70-112"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="9be70-113">[DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) Işlevi (Win32).</span><span class="sxs-lookup"><span data-stu-id="9be70-113">[DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) function (Win32).</span></span>  
  
 <span data-ttu-id="9be70-114">.NET Framework 4 ' den önce, .NET Framework yerel ve yönetilen hata ayıklayıcıların davranışını denetlemek için ayrı kayıt defteri anahtarları sağladı.</span><span class="sxs-lookup"><span data-stu-id="9be70-114">Before the .NET Framework 4, the .NET Framework provided separate registry keys to control the behavior of native and managed debuggers.</span></span> <span data-ttu-id="9be70-115">.NET Framework 4 ' te başlayarak, Denetim tek bir kayıt defteri anahtarı altında birleştirildi: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span><span class="sxs-lookup"><span data-stu-id="9be70-115">Starting with the .NET Framework 4, control is consolidated under a single registry key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span></span> <span data-ttu-id="9be70-116">Bu anahtar için ayarlayabileceğiniz değerler, bir hata ayıklayıcının çağrılıp çağrılmadığını ve varsa Kullanıcı etkileşimi gerektiren bir iletişim kutusuyla çağrılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9be70-116">The values you can set for that key determine whether a debugger is invoked, and, if so, whether it is invoked with a dialog box that requires user interaction.</span></span> <span data-ttu-id="9be70-117">Bu kayıt defteri anahtarını ayarlama hakkında daha fazla bilgi için bkz. [otomatik hata ayıklamayı yapılandırma](/windows/win32/debug/configuring-automatic-debugging).</span><span class="sxs-lookup"><span data-stu-id="9be70-117">For information about setting this registry key, see [Configuring Automatic Debugging](/windows/win32/debug/configuring-automatic-debugging).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9be70-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9be70-118">See also</span></span>

- [<span data-ttu-id="9be70-119">Hata ayıklama, Izleme ve profil oluşturma</span><span class="sxs-lookup"><span data-stu-id="9be70-119">Debugging, Tracing, and Profiling</span></span>](index.md)
- [<span data-ttu-id="9be70-120">Görüntüde Hata Ayıklamayı Kolaylaştırma</span><span class="sxs-lookup"><span data-stu-id="9be70-120">Making an Image Easier to Debug</span></span>](making-an-image-easier-to-debug.md)
