---
title: 'Nasıl yapılır: Kodda Hizmet Bağlama Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 67ab5dd8-79c1-4e62-aa75-828ea918a53a
ms.openlocfilehash: 7cf54754661182dca1e91c75b158d9b0a34a1f5e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236487"
---
# <a name="how-to-specify-a-service-binding-in-code"></a>Nasıl yapılır: Kodda Hizmet Bağlama Belirtme

Bu örnekte, bir `ICalculator` anlaşma Hesaplayıcı hizmeti için tanımlanmıştır, hizmet `CalculatorService` sınıfında uygulanır ve ardından uç noktası kodda tanımlanır ve burada hizmetin sınıfını kullanması gerektiği belirtilir <xref:System.ServiceModel.BasicHttpBinding> .  
  
 Genellikle, bağlama ve adres bilgilerini, kod içinde imperatively yerine bildirimli olarak yapılandırmaya göre belirlemek en iyi uygulamadır. Dağıtılmış bir hizmetin bağlamaları ve adresleri genellikle hizmet geliştirildiğinde kullanılanlardan farklı olduğundan, koddaki uç noktaların tanımlanması genellikle pratik değildir. Daha genel olarak, bağlama ve adresleme bilgilerini koddan tutmanın, uygulamayı yeniden derlemek veya yeniden dağıtmak zorunda kalmadan değiştirilmesine izin verir.  
  
 Bu hizmetin kod yerine yapılandırma öğelerini kullanarak nasıl yapılandırılacağı hakkında bir açıklama için bkz. [nasıl yapılır: yapılandırmada hizmet bağlaması belirtme](how-to-specify-a-service-binding-in-configuration.md).  
  
### <a name="to-specify-in-code-to-use-the-basichttpbinding-for-the-service"></a>Hizmet için BasicHttpBinding 'in kullanılacağı kodu belirtmek için  
  
1. Hizmet türü için bir hizmet sözleşmesi tanımlayın.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2. Hizmet sözleşmesini bir hizmet sınıfına uygulayın.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3. Barındırma uygulamasında, hizmet için temel adresi ve hizmetle birlikte kullanılacak bağlamayı oluşturun.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4. Hizmet için konak oluşturun, uç noktayı ekleyin ve ardından Konağı açın.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#4)]
     [!code-vb[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#4)]  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a>Bağlama özelliklerinin varsayılan değerlerini değiştirmek için  
  
1. Sınıfının varsayılan özellik değerlerinden birini değiştirmek için <xref:System.ServiceModel.BasicHttpBinding> , Konağı oluşturmadan önce bağlamasındaki özellik değerini yeni değere ayarlayın. Örneğin, varsayılan açık ve kapalı zaman aşımı değerlerini 1 dakika ila 2 dakika olarak değiştirmek için aşağıdakileri kullanın.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#5)]
     [!code-vb[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](using-bindings-to-configure-services-and-clients.md)
- [Bir Uç Noktası Adresi Belirtme](specifying-an-endpoint-address.md)
