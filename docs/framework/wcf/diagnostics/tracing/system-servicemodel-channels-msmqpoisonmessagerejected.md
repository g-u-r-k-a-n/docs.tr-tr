---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 69da35f65e04a3cba15885c4fe6e57d63762cb1c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96260350"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a>System.ServiceModel.Channels.MsmqPoisonMessageRejected

Zarar iletisi reddedildi.  
  
## <a name="description"></a>Açıklama  

 İzleme, bir zarar iletisi ile karşılaşıldığını ve daha sonra reddedildiğini belirtir. Bu, `ReceiveErrorHandling` NetMsmqBinding veya MsmqIntegrationBinding üzerindeki özellik olarak ayarlandığında oluşur `Reject` . Reddedilen bir ileti, gönderenin teslim [edilemeyen Ileti kuyruğuna](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)geri gönderilir.  
  
 İletiler ne zaman zarar haline geldiği ve hizmetinizi uygun şekilde işleyecek şekilde yapılandırma hakkında daha fazla bilgi için bkz. [Poison-Message Handling](../../feature-details/poison-message-handling.md). Reddedilen iletinin MSMQ 'da anlamı hakkında daha fazla bilgi için bkz. [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme](index.md)
- [Uygulamanızda Sorun Giderme için İzleme Kullanma](using-tracing-to-troubleshoot-your-application.md)
- [Yönetim ve tanılama](../index.md)
- [Zehirli Ileti Işleme](../../feature-details/poison-message-handling.md)
- [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))
