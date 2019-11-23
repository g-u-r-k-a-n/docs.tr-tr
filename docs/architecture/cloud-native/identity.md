---
title: Kimlik
description: Azure için Cloud Native .NET uygulamaları tasarlama | IDENTITY
ms.date: 09/23/2019
ms.openlocfilehash: 4cc7c04bf323d2589777df466321f6801f511b6f
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183051"
---
# <a name="identity"></a><span data-ttu-id="178f8-103">Kimlik</span><span class="sxs-lookup"><span data-stu-id="178f8-103">Identity</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="178f8-104">Çoğu yazılım uygulamasının, bunları çağıran kullanıcı veya işlemle ilgili bazı bilgileri olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="178f8-104">Most software applications need to have some knowledge of the user or process that is calling them.</span></span> <span data-ttu-id="178f8-105">Bir uygulamayla etkileşim kuran kullanıcı veya işlem güvenlik sorumlusu olarak bilinir ve bu sorumluların kimlik doğrulama ve yetkilendirme süreci kimlik yönetimi veya yalnızca *kimlik*olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="178f8-105">The user or process interacting with an application is known as a security principal, and the process of authenticating and authorizing these principals is known as identity management, or simply *identity*.</span></span> <span data-ttu-id="178f8-106">Basit uygulamalar uygulama içindeki tüm kimlik yönetimini içerebilir, ancak bu yaklaşım birçok uygulamayla ve birçok güvenlik sorumlusu ile iyi ölçeklenmez.</span><span class="sxs-lookup"><span data-stu-id="178f8-106">Simple applications may include all of their identity management within the application, but this approach doesn't scale well with many applications and many kinds of security principals.</span></span> <span data-ttu-id="178f8-107">Windows, merkezi kimlik doğrulaması ve yetkilendirme sağlamak için Active Directory kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="178f8-107">Windows supports the use of Active Directory to provide centralized authentication and authorization.</span></span>

<!-- (insert figure showing Windows AD auth model) -->

<span data-ttu-id="178f8-108">Bu çözüm kurumsal ağlarda geçerli olsa da, AD etki alanı dışındaki kullanıcılar veya uygulamalar tarafından kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="178f8-108">While this solution is effective within corporate networks, it isn't designed for use by users or applications that are outside of the AD domain.</span></span> <span data-ttu-id="178f8-109">Internet tabanlı uygulamaların büyümesi ve bulut Yerel uygulamalarının yüksei sayesinde güvenlik modelleri geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="178f8-109">With the growth of Internet-based applications and the rise of cloud-native apps, security models have evolved.</span></span>

<span data-ttu-id="178f8-110">Bugünün bulutta yerel kimlik modelinde, mimarinin dağıtılması varsayılır.</span><span class="sxs-lookup"><span data-stu-id="178f8-110">In today's cloud-native identity model, architecture is assumed to be distributed.</span></span> <span data-ttu-id="178f8-111">Uygulamalar her yerde dağıtılabilir ve diğer uygulamalarla her yerde iletişim kurabilir.</span><span class="sxs-lookup"><span data-stu-id="178f8-111">Apps can be deployed anywhere and may communicate with other apps anywhere.</span></span> <span data-ttu-id="178f8-112">İstemciler bu uygulamalarla her yerden iletişim kurabilir ve aslında istemciler platformların ve cihazların herhangi bir birleşimini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="178f8-112">Clients may communicate with these apps from anywhere, and in fact, clients may consist of any combination of platforms and devices.</span></span> <span data-ttu-id="178f8-113">Bulutta yerel kimlik çözümleri, istemcilerden güvenli uygulama erişimi elde etmek için açık standartlardan yararlanır.</span><span class="sxs-lookup"><span data-stu-id="178f8-113">Cloud-native identity solutions leverage open standards to achieve secure application access from clients.</span></span> <span data-ttu-id="178f8-114">Bu istemciler PC veya telefonlardaki insan kullanıcılarından, her yerde barındırılan diğer uygulamalara, dünyanın herhangi bir yerindeki herhangi bir yazılım platformunu çalıştıran en üst kutular ve ıOT cihazlarına göre değişir.</span><span class="sxs-lookup"><span data-stu-id="178f8-114">These clients range from human users on PCs or phones, to other apps hosted anywhere online, to set-top boxes and IOT devices running any software platform anywhere in the world.</span></span>

<span data-ttu-id="178f8-115">Modern bulutla yerel kimlik çözümleri, genellikle bir güvenli belirteç hizmeti/sunucusu (STS) tarafından kimlik saptandıktan sonra bir güvenlik sorumlusu tarafından verilen erişim belirteçlerine faydalanır.</span><span class="sxs-lookup"><span data-stu-id="178f8-115">Modern cloud-native identity solutions typically leverage access tokens that are issued by a secure token service/server (STS) to a security principal once their identity is determined.</span></span> <span data-ttu-id="178f8-116">Erişim belirteci, genellikle bir JSON Web Token (JWT), güvenlik sorumlusu hakkında *talepler* içerir.</span><span class="sxs-lookup"><span data-stu-id="178f8-116">The access token, typically a JSON Web Token (JWT), includes *claims* about the security principal.</span></span> <span data-ttu-id="178f8-117">Bu talepler, kullanıcının kimliğini en düşük düzeyde içerir, ancak aynı zamanda, sorumlu vermek için erişim düzeyini belirlemede uygulamalar tarafından kullanılabilecek ek talepler de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="178f8-117">These claims will minimally include the user's identity but may also include additional claims that can be used by applications to determine the level of access to grant the principal.</span></span>

<!-- (insert figure showing basic handshake involving a principal, an STS, and an app) -->

<span data-ttu-id="178f8-118">Genellikle STS yalnızca Sorumlunun kimliğini doğrulamaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="178f8-118">Typically, the STS is only responsible for authenticating the principal.</span></span> <span data-ttu-id="178f8-119">Kaynaklara erişim düzeyini belirleme, uygulamanın diğer bölümlerine bırakılır.</span><span class="sxs-lookup"><span data-stu-id="178f8-119">Determining their level of access to resources is left to other parts of the application.</span></span>

## <a name="references"></a><span data-ttu-id="178f8-120">Referanslar</span><span class="sxs-lookup"><span data-stu-id="178f8-120">References</span></span>

- [<span data-ttu-id="178f8-121">Microsoft Identity platformu</span><span class="sxs-lookup"><span data-stu-id="178f8-121">Microsoft identity platform</span></span>](https://docs.microsoft.com/azure/active-directory/develop/)

>[!div class="step-by-step"]
><span data-ttu-id="178f8-122">[Önceki](azure-monitor.md)
>[İleri](authentication-authorization.md)</span><span class="sxs-lookup"><span data-stu-id="178f8-122">[Previous](azure-monitor.md)
[Next](authentication-authorization.md)</span></span>
