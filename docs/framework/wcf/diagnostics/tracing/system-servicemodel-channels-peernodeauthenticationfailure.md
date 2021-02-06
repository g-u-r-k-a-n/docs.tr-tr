---
description: ': System. ServiceModel. Channels. PeerNodeAuthenticationFailure hakkında daha fazla bilgi edinin'
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.date: 03/30/2017
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
ms.openlocfilehash: 751202abd3e199a03fc4ee0bf1252d4a8027e0cb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99634940"
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a><span data-ttu-id="4ddb1-103">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span><span class="sxs-lookup"><span data-stu-id="4ddb1-103">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span></span>

<span data-ttu-id="4ddb1-104">Olası bir komşuyla güvenlik el sıkışması başarılı olmadı.</span><span class="sxs-lookup"><span data-stu-id="4ddb1-104">The security handshake with a potential neighbor was not successful.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4ddb1-105">Description</span><span class="sxs-lookup"><span data-stu-id="4ddb1-105">Description</span></span>  

 <span data-ttu-id="4ddb1-106">Bu izleme, güvenli bir komşu bağlantı kurmaya çalışırken oluşur.</span><span class="sxs-lookup"><span data-stu-id="4ddb1-106">This trace occurs while attempting to establish a secure neighbor connection.</span></span> <span data-ttu-id="4ddb1-107">Bu durum yetersiz veya hatalı kimlik bilgileri nedeniyle oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="4ddb1-107">This can happen due to insufficient or incorrect credentials.</span></span>  
  
 <span data-ttu-id="4ddb1-108">PeerChannel, uygulanabilen kimlik doğrulaması ve yetkilendirme türüne göre güçlü bir kimlik modeli sağlayan, güçlü tanımlama, X. 509.440 sertifikaları için tek bir belirteç türünü tanır.</span><span class="sxs-lookup"><span data-stu-id="4ddb1-108">PeerChannel recognizes a single token type for strong identification, X.509 certificates, which provide a strong identity model based on the type of authentication and authorization that can be implemented.</span></span> <span data-ttu-id="4ddb1-109">PeerChannel Ayrıca parolaların kullanımı aracılığıyla basit uygulamalar için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ddb1-109">PeerChannel also provides support for simple applications through the use of passwords.</span></span> <span data-ttu-id="4ddb1-110">Parolalar yalnızca oturum girişine izin vermek için kullanılabilir; ileti kimlik doğrulaması yapmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4ddb1-110">Passwords can be used only to allow entry to the session; they cannot be used to perform message authentication.</span></span> <span data-ttu-id="4ddb1-111">Bunun nedeni, bir eş payı grubunun paylaştığı bir simetrik belirtecin zor ve kaynak kimlik doğrulaması için kullanılmak üzere uygun olmadığı bir değer.</span><span class="sxs-lookup"><span data-stu-id="4ddb1-111">This is because a symmetric token that a group of peers share is difficult and inappropriate to use for source authentication.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="4ddb1-112">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="4ddb1-112">Troubleshooting</span></span>  

 <span data-ttu-id="4ddb1-113">Tüm komşuların uygun güvenlik kimlik bilgilerine sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="4ddb1-113">Ensure that all neighbors have the appropriate security credentials.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ddb1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ddb1-114">See also</span></span>

- [<span data-ttu-id="4ddb1-115">Eş Kanalı Güvenliği</span><span class="sxs-lookup"><span data-stu-id="4ddb1-115">Peer Channel Security</span></span>](../../feature-details/peer-channel-security.md)
- [<span data-ttu-id="4ddb1-116">İzleme</span><span class="sxs-lookup"><span data-stu-id="4ddb1-116">Tracing</span></span>](index.md)
- [<span data-ttu-id="4ddb1-117">Uygulamanızda Sorun Giderme için İzleme Kullanma</span><span class="sxs-lookup"><span data-stu-id="4ddb1-117">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="4ddb1-118">Yönetim ve tanılama</span><span class="sxs-lookup"><span data-stu-id="4ddb1-118">Administration and Diagnostics</span></span>](../index.md)
