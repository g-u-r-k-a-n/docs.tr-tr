---
title: 'Nasıl yapılır: Kodda İstemci Bağlama Belirtme'
description: Kodda bir WCF istemci imperatively için bağlamayı belirtmeyi öğrenin. İstemci bu örnekteki bir hizmete erişir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: f9a56c631d841fe60923c05a19bdec9db989ac60
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236578"
---
# <a name="how-to-specify-a-client-binding-in-code"></a>Nasıl yapılır: Kodda İstemci Bağlama Belirtme

Bu örnekte, bir Hesaplayıcı hizmeti kullanmak için bir istemci oluşturulur ve bu istemci için bağlama kodda imperatively belirtilir. İstemci, `CalculatorService` arabirimini uygulayan öğesine erişir `ICalculator` ve hem hizmet hem de istemci <xref:System.ServiceModel.BasicHttpBinding> sınıfını kullanır.  
  
 Bu yordam, hesap makinesi hizmetinin çalıştığını varsayar. Hizmeti oluşturma hakkında bilgi için bkz. [nasıl yapılır: yapılandırmada hizmet bağlaması belirtme](how-to-specify-a-service-binding-in-configuration.md). Ayrıca, istemci bileşenlerini otomatik olarak oluşturmak için [ServiceModel meta veri yardımcı programı aracı 'nı (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)WINDOWS COMMUNICATION FOUNDATION (WCF) kullanır. Araç, hizmete erişmek için istemci kodunu üretir.  
  
 İstemci iki bölümde oluşturulmuştur. Svcutil.exe, `ClientCalculator` arabirimini uygulayan öğesini oluşturur `ICalculator` . Bu istemci uygulaması daha sonra bir örneği `ClientCalculator` oluşturup ardından kodda hizmet için bağlama ve adres belirtilerek oluşturulur.  
  
 Bu örneğin kaynak kopyası için bkz. [BasicBinding](./samples/basicbinding.md) örneği.  
  
### <a name="to-specify-a-custom-binding-in-code"></a>Kodda özel bir bağlama belirtmek için  
  
1. Hizmet meta verilerinden kod oluşturmak için komut satırından Svcutil.exe kullanın.  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. Oluşturulan istemci, `ICalculator` istemci uygulamasının karşılaması gereken hizmet sözleşmesini tanımlayan arabirimi içerir.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. Oluşturulan istemci, uygulamasını da içerir `ClientCalculator` .  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. `ClientCalculator`Bir istemci uygulamasında sınıfını kullanan öğesinin bir örneğini oluşturun <xref:System.ServiceModel.BasicHttpBinding> ve ardından belirtilen adresteki hizmet işlemlerini çağırın.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. İstemcisini derleyin ve çalıştırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](using-bindings-to-configure-services-and-clients.md)
