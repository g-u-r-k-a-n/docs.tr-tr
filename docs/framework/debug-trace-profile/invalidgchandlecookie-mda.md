---
title: invalidGCHandleCookie MDA
description: Geçersiz bir IntPtr tanımlama bilgisinden bir GCHandle dönüştürme denendiğinde etkinleştirilen ınvalidgchandtacookie yönetilen hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid cookies
- cookies, invalid
- managed debugging assistants (MDAs), invalid cookies
- InvalidGCHandleCookie MDA
- invalid cookies
ms.assetid: 613ad742-3c11-401d-a6b3-893ceb8de4f8
ms.openlocfilehash: 36806498445da78c8d9dd5c51c1903b253a39da0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272611"
---
# <a name="invalidgchandlecookie-mda"></a><span data-ttu-id="5d2dd-103">invalidGCHandleCookie MDA</span><span class="sxs-lookup"><span data-stu-id="5d2dd-103">invalidGCHandleCookie MDA</span></span>

<span data-ttu-id="5d2dd-104">`invalidGCHandleCookie`Geçersiz bir <xref:System.IntPtr> tanımlama bilgisinden öğesine dönüştürme denendiğinde yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilir <xref:System.Runtime.InteropServices.GCHandle> .</span><span class="sxs-lookup"><span data-stu-id="5d2dd-104">The `invalidGCHandleCookie` managed debugging assistant (MDA) is activated when a conversion from an invalid <xref:System.IntPtr> cookie to a <xref:System.Runtime.InteropServices.GCHandle> is attempted.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="5d2dd-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="5d2dd-105">Symptoms</span></span>  

 <span data-ttu-id="5d2dd-106">' Dan ' i kullanmaya veya almaya çalışırken erişim ihlalleri ve bellek bozulması gibi tanımsız davranışlar <xref:System.Runtime.InteropServices.GCHandle> <xref:System.IntPtr> .</span><span class="sxs-lookup"><span data-stu-id="5d2dd-106">Undefined behavior such as access violations and memory corruption while attempting to use or retrieve a <xref:System.Runtime.InteropServices.GCHandle> from an <xref:System.IntPtr>.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="5d2dd-107">Nedeni</span><span class="sxs-lookup"><span data-stu-id="5d2dd-107">Cause</span></span>  

 <span data-ttu-id="5d2dd-108">Tanımlama bilgisi büyük olasılıkla bir ' dan oluşturulmadığı için geçersiz, <xref:System.Runtime.InteropServices.GCHandle> <xref:System.Runtime.InteropServices.GCHandle> zaten serbest bırakılmış olan bir tanımlama bilgisidir, <xref:System.Runtime.InteropServices.GCHandle> farklı bir uygulama etki alanındaki bir tanımlama bilgisidir veya yerel koda bir <xref:System.Runtime.InteropServices.GCHandle> atama denendiğinde, clr 'ye geri geçirilmiş <xref:System.IntPtr> .</span><span class="sxs-lookup"><span data-stu-id="5d2dd-108">The cookie is probably invalid because it was not originally created from a <xref:System.Runtime.InteropServices.GCHandle>, represents a <xref:System.Runtime.InteropServices.GCHandle> that has already been freed, is a cookie to a <xref:System.Runtime.InteropServices.GCHandle> in a different application domain, or was marshaled to native code as a <xref:System.Runtime.InteropServices.GCHandle> but passed back into the CLR as an <xref:System.IntPtr>, where a cast was attempted.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="5d2dd-109">Çözüm</span><span class="sxs-lookup"><span data-stu-id="5d2dd-109">Resolution</span></span>  

 <span data-ttu-id="5d2dd-110">İçin geçerli bir <xref:System.IntPtr> tanımlama bilgisi belirtin <xref:System.Runtime.InteropServices.GCHandle> .</span><span class="sxs-lookup"><span data-stu-id="5d2dd-110">Specify a valid <xref:System.IntPtr> cookie for the <xref:System.Runtime.InteropServices.GCHandle>.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="5d2dd-111">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="5d2dd-111">Effect on the Runtime</span></span>  

 <span data-ttu-id="5d2dd-112">Bu MDA etkinleştirildiğinde, hata ayıklayıcı artık kök nesneleri nesnelerine geri izleyemez çünkü geri geçirilen tanımlama bilgisi değerleri, MDA etkin olmadığında döndürülmeden farklı.</span><span class="sxs-lookup"><span data-stu-id="5d2dd-112">When this MDA is enabled, the debugger is no longer able to trace the roots back to their objects because the cookie values passed back are different from the ones returned when the MDA is not enabled.</span></span>  
  
## <a name="output"></a><span data-ttu-id="5d2dd-113">Çıkış</span><span class="sxs-lookup"><span data-stu-id="5d2dd-113">Output</span></span>  

 <span data-ttu-id="5d2dd-114">Geçersiz <xref:System.IntPtr> tanımlama bilgisi değeri bildirildi.</span><span class="sxs-lookup"><span data-stu-id="5d2dd-114">The invalid <xref:System.IntPtr> cookie value is reported.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="5d2dd-115">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5d2dd-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d2dd-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d2dd-116">See also</span></span>

- <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>
- <xref:System.Runtime.InteropServices.GCHandle>
- [<span data-ttu-id="5d2dd-117">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="5d2dd-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
