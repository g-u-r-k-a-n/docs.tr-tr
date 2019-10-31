---
title: Hata Ayıklama, İzleme ve Profil Oluşturma
ms.date: 03/30/2017
helpviewer_keywords:
- debugging [.NET Framework]
- .NET Framework application configuration, debugging
- debugging [.NET Framework], .NET Framework application debugging
- troubleshooting applications [.NET Framework], profiling
- application development [.NET Framework], debugging
- .NET Framework application configuration, profiling
- profiling applications
- troubleshooting applications [.NET Framework], debugging
- troubleshooting applications [.NET Framework]
- application development [.NET Framework], profiling
ms.assetid: 4a04863e-2475-46f4-bc3f-3c11510c2a4b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 43e9438ed2c1cd82bb4d89ff082545021b2d543e
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73195348"
---
# <a name="debugging-tracing-and-profiling"></a><span data-ttu-id="30103-102">Hata Ayıklama, İzleme ve Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="30103-102">Debugging, Tracing, and Profiling</span></span>
<span data-ttu-id="30103-103">.NET Framework bir uygulamada hata ayıklamak için, derleyici ve çalışma zamanı ortamı, bir hata ayıklayıcının uygulamaya iliştirmesine ve mümkünse hem semboller hem de çizgi haritaları (mümkünse, uygulama ve karşılık gelen Microsoft ara Dil (MSIL).</span><span class="sxs-lookup"><span data-stu-id="30103-103">To debug a .NET Framework application, the compiler and runtime environment must be configured to enable a debugger to attach to the application and to produce both symbols and line maps, if possible, for the application and its corresponding Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="30103-104">Yönetilen bir uygulamanın hatası ayıklandıktan sonra, performansı artırmak için profili oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="30103-104">After a managed application has been debugged, it can be profiled to boost performance.</span></span> <span data-ttu-id="30103-105">Profil oluşturma, en sık yürütülen kodu oluşturan kaynak kodu satırlarını ve bunların yürütülmesi için ne kadar zaman harcanduğunu değerlendirir ve tanımlar.</span><span class="sxs-lookup"><span data-stu-id="30103-105">Profiling evaluates and describes the lines of source code that generate the most frequently executed code, and how much time it takes to execute them.</span></span>  
  
 <span data-ttu-id="30103-106">.NET Framework uygulamalar, birçok yapılandırma ayrıntılarını işleyen Visual Studio kullanılarak kolayca hata ayıklamalıdır.</span><span class="sxs-lookup"><span data-stu-id="30103-106">.NET Framework applications are easily debugged by using Visual Studio, which handles many of the configuration details.</span></span> <span data-ttu-id="30103-107">Visual Studio yüklü değilse, .NET Framework <xref:System.Diagnostics> ad alanındaki hata ayıklama sınıflarını kullanarak .NET Framework uygulamalarının performansını inceleyebilir ve geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30103-107">If Visual Studio is not installed, you can examine and improve the performance of .NET Framework applications by using the debugging classes in the .NET Framework <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="30103-108">Bu ad alanı, yürütme akışını izlemek için <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>ve <xref:System.Diagnostics.TraceSource> sınıflarını ve profil oluşturma kodu için <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>ve <xref:System.Diagnostics.PerformanceCounter> sınıflarını içerir.</span><span class="sxs-lookup"><span data-stu-id="30103-108">This namespace includes the <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, and <xref:System.Diagnostics.TraceSource> classes for tracing execution flow, and the <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, and <xref:System.Diagnostics.PerformanceCounter> classes for profiling code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="30103-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="30103-109">In This Section</span></span>  
 [<span data-ttu-id="30103-110">JIT-Ekleme Hata Ayıklamayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="30103-110">Enabling JIT-Attach Debugging</span></span>](enabling-jit-attach-debugging.md)  
 <span data-ttu-id="30103-111">Bir .NET Framework uygulamasına bir hata ayıklama altyapısını JıT olarak eklemek için kayıt defterinin nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="30103-111">Shows how to configure the registry to JIT-attach a debug engine to a .NET Framework application.</span></span>  
  
 [<span data-ttu-id="30103-112">Görüntüde Hata Ayıklamayı Kolaylaştırma</span><span class="sxs-lookup"><span data-stu-id="30103-112">Making an Image Easier to Debug</span></span>](making-an-image-easier-to-debug.md)  
 <span data-ttu-id="30103-113">Derlemeyi hata ayıklamanın daha kolay hale getirmek için JıT izlemenin açık ve en iyi duruma getirme özelliğini nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="30103-113">Shows how to turn JIT tracking on and optimization off to make an assembly easier to debug.</span></span>  
  
 [<span data-ttu-id="30103-114">İzleme ve İşaretleme Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="30103-114">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)  
 <span data-ttu-id="30103-115">Uygulamasının çalışırken nasıl yapıldığını ve ne kadar iyi bir şeyin yanlış geçmiş olduğunu görüntülemek için nasıl ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="30103-115">Describes how to monitor the execution of your application while it is running, and how to instrument it to display how well it is performing or whether something has gone wrong.</span></span>  
  
 [<span data-ttu-id="30103-116">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="30103-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)  
 <span data-ttu-id="30103-117">Çalışma zamanı durumu hakkında bilgi sağlamak için ortak dil çalışma zamanı (CLR) ile birlikte çalışan hata ayıklama yardımlarından oluşan yönetilen hata ayıklama yardımcıları 'nı (MDAs) açıklar.</span><span class="sxs-lookup"><span data-stu-id="30103-117">Describes managed debugging assistants (MDAs), which are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span>  
  
 [<span data-ttu-id="30103-118">Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme</span><span class="sxs-lookup"><span data-stu-id="30103-118">Enhancing Debugging with the Debugger Display Attributes</span></span>](enhancing-debugging-with-the-debugger-display-attributes.md)  
 <span data-ttu-id="30103-119">Bir tür geliştiricisinin bir hata ayıklayıcıda görüntülendiğinde ne tür görüneceğini nasıl belirtbileceklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="30103-119">Describes how the developer of a type can specify what that type will look like when it is displayed in a debugger.</span></span>  
  
 [<span data-ttu-id="30103-120">Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="30103-120">Performance Counters</span></span>](performance-counters.md)  
 <span data-ttu-id="30103-121">Bir uygulamanın performansını izlemek için kullanabileceğiniz sayaçları açıklar.</span><span class="sxs-lookup"><span data-stu-id="30103-121">Describes the counters that you can use to track the performance of an application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="30103-122">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="30103-122">Related Sections</span></span>  
 [<span data-ttu-id="30103-123">Visual Studio 'da ASP.NET veya ASP.NET Core uygulamalarında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="30103-123">Debug ASP.NET or ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications)  
 <span data-ttu-id="30103-124">Geliştirme sırasında veya dağıtımdan sonra bir ASP.NET uygulamasında hata ayıklama için önkoşul ve yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="30103-124">Provides prerequisites and instructions for how to debug an ASP.NET application during development or after deployment.</span></span>  
  
 [<span data-ttu-id="30103-125">Geliştirme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="30103-125">Development Guide</span></span>](../development-guide.md)  
 <span data-ttu-id="30103-126">Dinamik programlama, birlikte çalışabilirlik, genişletilebilirlik, bellek yönetimi ve iş parçacığı oluşturma hakkında uygulama ve bilgilerinizi oluşturma, yapılandırma, hatasını ayıklama, güvenliğini sağlama ve dağıtma gibi, uygulama geliştirmesine yönelik tüm temel teknoloji alanları ve görevleri için kılavuz sağlar.</span><span class="sxs-lookup"><span data-stu-id="30103-126">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
