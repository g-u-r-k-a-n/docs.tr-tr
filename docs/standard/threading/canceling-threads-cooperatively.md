---
title: İş parçacıklarını işbirliği ile iptal etme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threads, cancellation
ms.assetid: d2d6d5fd-e263-4fa0-847b-2fc3e0d82337
ms.openlocfilehash: 1d1433ecf39974bf9e68fe07b9d0818ac16fb544
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138123"
---
# <a name="canceling-threads-cooperatively"></a>İş parçacıklarını işbirliği ile iptal etme

.NET Framework 4'ten önce,.NET Framework başlatıldıktan sonra bir iş parçacığının birlikte iptal ilerleilmesi için yerleşik bir yol sağlamaz. Ancak, .NET Framework 4'ten başlayarak, nesneleri veya PLINQ sorgularını <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> iptal etmek için kullanabileceğiniz gibi, iş parçacıklarını iptal etmek için de a <xref:System.Threading.CancellationToken?displayProperty=nameWithType> kullanabilirsiniz. <xref:System.Threading.Thread?displayProperty=nameWithType> Sınıf iptal belirteçleri için yerleşik destek sunmasa da, <xref:System.Threading.ParameterizedThreadStart> temsilci alan oluşturucuyu <xref:System.Threading.Thread> kullanarak iş parçacığı yordamına bir belirteç geçirebilirsiniz. Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Parçacığı ve İş Parçacığı kullanma](using-threads-and-threading.md)
