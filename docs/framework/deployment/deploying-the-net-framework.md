---
title: .NET Framework'ü dağıtma
description: .NET uygulamaları ile .net yüklemek isteyen geliştiriciler ve bir ağda .NET dağıtmak isteyen yöneticiler için .NET dağıtmayı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, deploying
- deployment [.NET Framework]
ms.assetid: 19df26c5-4008-461d-a7d7-18f4506312d2
ms.openlocfilehash: b42646b60fab91fe761a8fdef59d67be6ffa884b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242051"
---
# <a name="deploying-the-net-framework"></a><span data-ttu-id="24703-103">.NET Framework'ü dağıtma</span><span class="sxs-lookup"><span data-stu-id="24703-103">Deploying the .NET Framework</span></span>

<span data-ttu-id="24703-104">.NET Framework belgelerinin bu bölümü, .NET Framework uygulamalarına ve .NET Framework dağıtmak isteyen yöneticilere bir ağ üzerinden yüklemek isteyen geliştiriciler için bilgi sağlamaktadır.</span><span class="sxs-lookup"><span data-stu-id="24703-104">This section of the .NET Framework documentation provides information for developers who want to install the .NET Framework with their applications, and administrators who want to deploy the .NET Framework across a network.</span></span> <span data-ttu-id="24703-105">Ayrıca, dağıtım ile ilişkili etkinleştirme ve yeniden başlatma sorunlarını ve .NET Framework yüklemenizin ilerlemesini nasıl izleyeceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="24703-105">It also discusses activation and restart issues associated with deployment, and how to monitor the progress of your .NET Framework installation.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="24703-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="24703-106">In This Section</span></span>  

 [<span data-ttu-id="24703-107">Geliştiriciler için Dağıtım Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="24703-107">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)  
 <span data-ttu-id="24703-108">Geliştiricilerin kullanıcıların bilgisayarlarına uygulamalarına .NET Framework nasıl yükleyebileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="24703-108">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>  
  
 [<span data-ttu-id="24703-109">Yöneticiler için Dağıtım Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="24703-109">Deployment Guide for Administrators</span></span>](guide-for-administrators.md)  
 <span data-ttu-id="24703-110">Bir sistem yöneticisinin, Microsoft uç nokta Configuration Manager kullanarak bir ağ üzerinde .NET Framework ve sistem bağımlılıklarını nasıl dağıtabilebileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="24703-110">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using Microsoft Endpoint Configuration Manager.</span></span>  
  
 [<span data-ttu-id="24703-111">.NET Framework 4.5 Yüklemeleri Sırasında Sistem Yeniden Başlatmalarını Azaltma</span><span class="sxs-lookup"><span data-stu-id="24703-111">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](reducing-system-restarts.md)  
 <span data-ttu-id="24703-112">Mümkün olan her durumda yeniden başlatma Işlemini önleyen ve .NET Framework yükleyen uygulamaların nasıl yararlanacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="24703-112">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>  
  
 [<span data-ttu-id="24703-113">Nasıl yapılır: .NET Framework 4.5 Yükleyicisinden İlerleme Durumunu Alma</span><span class="sxs-lookup"><span data-stu-id="24703-113">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](how-to-get-progress-from-the-dotnet-installer.md)  
 <span data-ttu-id="24703-114">Kurulum ilerleme durumunun kendi görünümünü gösterirken .NET Framework kurulum işleminin sessizce nasıl başlatılmasını ve izleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="24703-114">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>  
  
 [<span data-ttu-id="24703-115">.NET Framework Başlatma Hataları: Kullanıcı Deneyimini Yönetme</span><span class="sxs-lookup"><span data-stu-id="24703-115">.NET Framework Initialization Errors: Managing the User Experience</span></span>](initialization-errors-managing-the-user-experience.md)  
 <span data-ttu-id="24703-116">.NET Framework bir uygulama, kullanıcının bilgisayarında geçersiz veya yüklü olmayan bir CLR sürümü gerektirdiğinde, bu hataların nasıl çözümleneceği ve kullanıcıya görüntülenen hata iletisinin nasıl denetleneceği hakkında ne olacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="24703-116">Explains what happens when a .NET Framework application requires a CLR version that's invalid or not installed on the user's computer, how to resolve these errors, and how to control the error message displayed to the user.</span></span>  
  
 [<span data-ttu-id="24703-117">Nasıl yapılır: CLR Etkinleştirme Sorunlarında Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="24703-117">How to: Debug CLR Activation Issues</span></span>](how-to-debug-clr-activation-issues.md)  
 <span data-ttu-id="24703-118">Uygulamanızı CLR 'nin doğru sürümüyle çalıştırmak için karşılaşabileceğiniz sorunları çözümlemek üzere CLR etkinleştirme günlüklerini nasıl görüntüleyip ayıklayabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="24703-118">Explains how you can view and debug CLR activation logs to resolve issues you may encounter in getting your application to run with the correct version of the CLR.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24703-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24703-119">See also</span></span>

- [<span data-ttu-id="24703-120">Geliştirme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="24703-120">Development Guide</span></span>](../development-guide.md)
