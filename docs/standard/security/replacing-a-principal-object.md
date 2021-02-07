---
description: 'Hakkında daha fazla bilgi edinin: asıl nesneyi değiştirme'
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
ms.openlocfilehash: 3f413a3b0824cef9f28454bf109d40556f61c26b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684990"
---
# <a name="replacing-a-principal-object"></a>Asıl Nesneyi Değiştirme

Kimlik doğrulama hizmetleri sağlayan uygulamalar,  <xref:System.Security.Principal.IPrincipal> belirli bir Iş parçacığı için Principal nesnesinin () değiştirilmesini sağlamalıdır. Ayrıca, güvenlik sistemi, kötü amaçlı olarak eklenmiş, yanlış bir **asıl öğe** , doğru olmayan bir kimlik veya rol belirterek uygulamanızın güvenliğini tehlikeye atarak **asıl** nesneleri değiştirme özelliğini korumaya yardımcı olmalıdır. Bu nedenle, **asıl** nesneleri değiştirme olanağına sahip olan uygulamalara <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> asıl denetim nesnesi verilmelidir. (Rol tabanlı güvenlik denetimleri gerçekleştirmek veya **asıl** nesneler oluşturmak için bu iznin gerekli olmadığını unutmayın.)  
  
Şu görevleri gerçekleştirerek geçerli **asıl** nesne değiştirilebilir:  
  
1. Yeni bir **asıl** nesne ve ilişkili **Identity** nesnesi oluşturun.  
  
2. Yeni **Principal** nesnesini çağrı bağlamına ekleyin.  
  
## <a name="example"></a>Örnek

Aşağıdaki örnek, bir genel Principal nesnesinin nasıl oluşturulduğunu ve bir iş parçacığının asıl öğesini ayarlamak için nasıl kullanılacağını gösterir.  
  
[!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
[!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>
- [Asıl ve Kimlik Nesneleri](principal-and-identity-objects.md)
- [ASP.NET Core güvenliği](/aspnet/core/security/)
