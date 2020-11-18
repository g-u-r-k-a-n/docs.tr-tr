---
title: Asıl Nesneyi Değiştirme
ms.date: 07/15/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- principal objects, replacing
- security [.NET], replacing principal objects
- security [.NET], principals
ms.assetid: c323687e-b196-487b-beba-f38f9b3f961b
ms.openlocfilehash: b8f7a8fbd3b9c65126d6a3a65a5f6722f2ad93de
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824180"
---
# <a name="replacing-a-principal-object"></a><span data-ttu-id="b07cf-102">Asıl Nesneyi Değiştirme</span><span class="sxs-lookup"><span data-stu-id="b07cf-102">Replacing a Principal Object</span></span>

<span data-ttu-id="b07cf-103">Kimlik doğrulama hizmetleri sağlayan uygulamalar, **Principal** <xref:System.Security.Principal.IPrincipal> belirli bir Iş parçacığı için Principal nesnesinin () değiştirilmesini sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b07cf-103">Applications that provide authentication services must be able to replace the **Principal** object (<xref:System.Security.Principal.IPrincipal>) for a given thread.</span></span> <span data-ttu-id="b07cf-104">Ayrıca, güvenlik sistemi, kötü amaçlı olarak eklenmiş, yanlış bir **asıl öğe** , doğru olmayan bir kimlik veya rol belirterek uygulamanızın güvenliğini tehlikeye atarak **asıl** nesneleri değiştirme özelliğini korumaya yardımcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b07cf-104">Furthermore, the security system must help protect the ability to replace **Principal** objects because a maliciously attached, incorrect **Principal** compromises the security of your application by claiming an untrue identity or role.</span></span> <span data-ttu-id="b07cf-105">Bu nedenle, **asıl** nesneleri değiştirme olanağına sahip olan uygulamalara <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> asıl denetim nesnesi verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="b07cf-105">Therefore, applications that require the ability to replace **Principal** objects must be granted the <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> object for principal control.</span></span> <span data-ttu-id="b07cf-106">(Rol tabanlı güvenlik denetimleri gerçekleştirmek veya **asıl** nesneler oluşturmak için bu iznin gerekli olmadığını unutmayın.)</span><span class="sxs-lookup"><span data-stu-id="b07cf-106">(Note that this permission is not required for performing role-based security checks or for creating **Principal** objects.)</span></span>  
  
<span data-ttu-id="b07cf-107">Şu görevleri gerçekleştirerek geçerli **asıl** nesne değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="b07cf-107">The current **Principal** object can be replaced by performing the following tasks:</span></span>  
  
1. <span data-ttu-id="b07cf-108">Yeni bir **asıl** nesne ve ilişkili **Identity** nesnesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b07cf-108">Create the replacement **Principal** object and associated **Identity** object.</span></span>  
  
2. <span data-ttu-id="b07cf-109">Yeni **Principal** nesnesini çağrı bağlamına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b07cf-109">Attach the new **Principal** object to the call context.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b07cf-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="b07cf-110">Example</span></span>

<span data-ttu-id="b07cf-111">Aşağıdaki örnek, bir genel Principal nesnesinin nasıl oluşturulduğunu ve bir iş parçacığının asıl öğesini ayarlamak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b07cf-111">The following example shows how to create a generic principal object and use it to set the principal of a thread.</span></span>  
  
[!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
[!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b07cf-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b07cf-112">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>
- [<span data-ttu-id="b07cf-113">Asıl ve Kimlik Nesneleri</span><span class="sxs-lookup"><span data-stu-id="b07cf-113">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
- [<span data-ttu-id="b07cf-114">ASP.NET Core güvenliği</span><span class="sxs-lookup"><span data-stu-id="b07cf-114">ASP.NET Core Security</span></span>](/aspnet/core/security/)
