---
title: Güvenli Oturumlar
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
ms.openlocfilehash: fd8406af0c37981b2ddc7ab8ddb0c82c63cbc0b1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288568"
---
# <a name="secure-sessions"></a><span data-ttu-id="72a83-102">Güvenli Oturumlar</span><span class="sxs-lookup"><span data-stu-id="72a83-102">Secure Sessions</span></span>

<span data-ttu-id="72a83-103">Windows Communication Foundation (WCF) özelliği, iletilerin gönderildikleri sırada alınabileceğini garanti eden güvenilir oturumlardır.</span><span class="sxs-lookup"><span data-stu-id="72a83-103">A feature of Windows Communication Foundation (WCF) is reliable sessions that guarantee messages are received in the order they were sent.</span></span> <span data-ttu-id="72a83-104">Bu bölümdeki konularda, güvenilir bir oturum oluştururken dikkate alınması gereken güvenlik etkileri ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="72a83-104">The topics in this section discuss the security implications to consider when creating a reliable session.</span></span> <span data-ttu-id="72a83-105">Güvenilir oturumlar hakkında daha fazla bilgi için bkz. [oturumları kullanma](../using-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="72a83-105">For more information about reliable sessions, see [Using Sessions](../using-sessions.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="72a83-106">Windows XP 'de kimliğe bürünme özelliği gerekli olduğunda, durum bilgisi olan güvenlik bağlamı belirteci (SCT) olmadan güvenli bir oturum kullanın.</span><span class="sxs-lookup"><span data-stu-id="72a83-106">When impersonation is required on Windows XP, use a secure session without a stateful security context token (SCT).</span></span> <span data-ttu-id="72a83-107">Durum bilgisi olan SCN 'ler kimliğe bürünme ile kullanıldığında bir oluşturulur <xref:System.InvalidOperationException> .</span><span class="sxs-lookup"><span data-stu-id="72a83-107">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="72a83-108">Daha fazla bilgi için bkz. [desteklenmeyen senaryolar](unsupported-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="72a83-108">For more information, see [Unsupported Scenarios](unsupported-scenarios.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="72a83-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="72a83-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="72a83-110">Güvenli İletişimler ve Güvenli Oturumlar</span><span class="sxs-lookup"><span data-stu-id="72a83-110">Secure Conversations and Secure Sessions</span></span>](secure-conversations-and-secure-sessions.md)|<span data-ttu-id="72a83-111">Güvenli konuşmalar ve güvenli oturumlar eşanlamlı olarak anlamlıdır.</span><span class="sxs-lookup"><span data-stu-id="72a83-111">Secure conversations and secure sessions are synonymous.</span></span> <span data-ttu-id="72a83-112">Bu konuda, güvenli bir konuşmanın çalışma şekli ve düzenin ne zaman ve neden kullanıldığı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="72a83-112">This topic explains the way a secure conversation works, and when and why to use the pattern.</span></span>|  
|[<span data-ttu-id="72a83-113">Nasıl yapılır: Güvenli Oturum Oluşturma</span><span class="sxs-lookup"><span data-stu-id="72a83-113">How to: Create a Secure Session</span></span>](how-to-create-a-secure-session.md)|<span data-ttu-id="72a83-114">Güvenli bir oturum oluşturma hakkındaki temel bilgileri adım adım açıklar.</span><span class="sxs-lookup"><span data-stu-id="72a83-114">Walks through of the basics of creating a secure session.</span></span>|  
|[<span data-ttu-id="72a83-115">Nasıl yapılır: Güvenli Bir Oturum için Güvenlik Bağlamı Belirteci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="72a83-115">How to: Create a Security Context Token for a Secure Session</span></span>](how-to-create-a-security-context-token-for-a-secure-session.md)|<span data-ttu-id="72a83-116">İstemcilerle durum ve oturumları koruyacak bir Web grubu oluşturma adımlarında size yol gösterir.</span><span class="sxs-lookup"><span data-stu-id="72a83-116">Walks through the steps of creating a Web farm that will maintain state and sessions with clients.</span></span>|  
|[<span data-ttu-id="72a83-117">Güvenli Oturumlar için Güvenlikli İlgili Önemli Noktalar</span><span class="sxs-lookup"><span data-stu-id="72a83-117">Security Considerations for Secure Sessions</span></span>](security-considerations-for-secure-sessions.md)|<span data-ttu-id="72a83-118">Güvenli oturumlar için özel konuları açıklar.</span><span class="sxs-lookup"><span data-stu-id="72a83-118">Describes special considerations for secure sessions.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="72a83-119">Başvuru</span><span class="sxs-lookup"><span data-stu-id="72a83-119">Reference</span></span>  

 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="72a83-120">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="72a83-120">Related Sections</span></span>  

 [<span data-ttu-id="72a83-121">Oturumlar, Örnek Oluşturma ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="72a83-121">Sessions, Instancing, and Concurrency</span></span>](sessions-instancing-and-concurrency.md)  
  
 [<span data-ttu-id="72a83-122">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="72a83-122">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="72a83-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72a83-123">See also</span></span>

- [<span data-ttu-id="72a83-124">Nasıl yapılır: İleti Yeniden Yürütme Algılamayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="72a83-124">How to: Enable Message Replay Detection</span></span>](how-to-enable-message-replay-detection.md)
- [<span data-ttu-id="72a83-125">Yeniden Yürütme Saldırıları</span><span class="sxs-lookup"><span data-stu-id="72a83-125">Replay Attacks</span></span>](replay-attacks.md)
- [<span data-ttu-id="72a83-126">Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="72a83-126">How to: Create a Service That Requires Sessions</span></span>](how-to-create-a-service-that-requires-sessions.md)
