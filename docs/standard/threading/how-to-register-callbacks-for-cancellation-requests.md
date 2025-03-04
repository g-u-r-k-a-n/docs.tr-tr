---
description: 'Daha fazla bilgi edinin: iptal istekleri için geri çağırmaları kaydetme'
title: İptal istekleri için geri çağırmaları Kaydet
ms.date: 08/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
ms.openlocfilehash: a791338fc7c39e3d259f90bc4c4723079eac4236
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666777"
---
# <a name="register-callbacks-for-cancellation-requests"></a>İptal istekleri için geri çağırmaları Kaydet

Bir özellik doğru olduğunda çağrılacak bir temsilciyi nasıl kaydedeceğinizi öğrenin <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> . Belirteci oluşturan nesne üzerinde yapılan bir çağrı yapıldığında değer false olarak değişir <xref:System.Threading.CancellationTokenSource.Cancel%2A> . Birleşik iptal çerçevesini yerel olarak desteklemeyen ve zaman uyumsuz bir işlemin tamamlanmasını bekleyen yöntemlerin engellemesini kaldırma işlemlerinde bu tekniği kullanın.

> [!NOTE]
> "Yalnızca kendi kodum" etkinleştirildiğinde, bazı durumlarda Visual Studio özel durumu oluşturan satıra kesilir ve "özel durum Kullanıcı kodu tarafından işlenmiyor" yazan bir hata mesajı görüntüler. Bu hata zararsız. <kbd>F5</kbd> tuşuna basarak bu uygulamadan devam edebilir ve aşağıdaki örneklerde gösterilen özel durum işleme davranışına bakabilirsiniz. Visual Studio 'Nun ilk hatada kesilmesini engellemek için **Araçlar, Seçenekler, hata ayıklama, genel** altında "yalnızca kendi kodum" onay kutusunun işaretini kaldırmanız yeterlidir.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, <xref:System.Net.WebClient.CancelAsync%2A> yöntemi iptal belirteci aracılığıyla iptal istendiğinde çağrılacak yöntem olarak kaydedilir.

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb":::

Geri çağırma kaydedildiğinde iptal işlemi zaten isteniyorsa, geri aramanın çağrılması garanti edilir. Bu durumda, <xref:System.Net.WebClient.CancelAsync%2A> zaman uyumsuz bir işlem devam ederken yöntem hiçbir şey yapmaz, bu nedenle yöntemi çağırmak her zaman güvenlidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacıklarında İptal](cancellation-in-managed-threads.md)
- <xref:System.Net.WebClient.DownloadStringTaskAsync(System.String)?displayProperty=nameWithType>
