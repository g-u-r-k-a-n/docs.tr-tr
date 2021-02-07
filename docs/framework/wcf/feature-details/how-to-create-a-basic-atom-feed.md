---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: temel bir Atom akışı oluşturma'
title: 'Nasıl yapılır: Temel Bir Atom Akışı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6e0cacc1-9b11-4665-adb7-577a62626fd6
ms.openlocfilehash: 4f4fa6e5b4e2b6935fb51cbc200e5ed9e03843ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734795"
---
# <a name="how-to-create-a-basic-atom-feed"></a>Nasıl yapılır: Temel Bir Atom Akışı Oluşturma

Windows Communication Foundation (WCF), bir dağıtım akışı sunan bir hizmet oluşturmanıza olanak sağlar. Bu konuda, bir Atom dağıtım akışını kullanıma sunan bir dağıtım hizmeti oluşturma konusu ele alınmaktadır.  
  
### <a name="to-create-a-basic-syndication-service"></a>Temel bir dağıtım hizmeti oluşturmak için  
  
1. Özniteliği ile işaretlenmiş bir arabirim kullanarak bir hizmet sözleşmesi tanımlayın <xref:System.ServiceModel.Web.WebGetAttribute> . Bir dağıtım akışı olarak sunulan her işlem bir <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> nesne döndürmelidir.  
  
     [!code-csharp[htAtomBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#0)]
     [!code-vb[htAtomBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#0)]  
  
    > [!NOTE]
    > ' İ uygulayan tüm hizmet işlemleri <xref:System.ServiceModel.Web.WebGetAttribute> http get isteklerine eşlenir. İşleminizi farklı bir HTTP yöntemiyle eşlemek için, <xref:System.ServiceModel.Web.WebInvokeAttribute> bunun yerine kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: temel BIR WCF Web http hizmeti oluşturma](how-to-create-a-basic-wcf-web-http-service.md).  
  
2. Hizmet sözleşmesini uygulayın.  
  
     [!code-csharp[htAtomBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#1)]
     [!code-vb[htAtomBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#1)]  
  
3. Bir <xref:System.ServiceModel.Syndication.SyndicationFeed> nesne oluşturun ve yazar, kategori ve açıklama ekleyin.  
  
     [!code-csharp[htAtomBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#2)]
     [!code-vb[htAtomBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#2)]  
  
4. Birkaç <xref:System.ServiceModel.Syndication.SyndicationItem> nesne oluşturun.  
  
     [!code-csharp[htAtomBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#3)]
     [!code-vb[htAtomBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#3)]  
  
5. <xref:System.ServiceModel.Syndication.SyndicationItem>Nesneleri akışa ekleyin.  
  
     [!code-csharp[htAtomBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#4)]
     [!code-vb[htAtomBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#4)]  
  
6. Akışı döndürün.  
  
     [!code-csharp[htAtomBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#5)]
     [!code-vb[htAtomBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a>Hizmeti barındırmak için  
  
1. Bir <xref:System.ServiceModel.Web.WebServiceHost> nesne oluşturun.  
  
     [!code-csharp[htAtomBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#6)]
     [!code-vb[htAtomBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#6)]  
  
2. Hizmet konağını açın, hizmetten akışı yükleyin, akışı görüntüleyin ve kullanıcının ENTER tuşuna basması için bekleyin.  
  
     [!code-csharp[htAtomBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#8)]
     [!code-vb[htAtomBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a>HTTP GET ile GetBlog () çağırmak için  
  
1. Internet Explorer 'ı açın, aşağıdaki URL 'yi yazın ve ENTER tuşuna basın: `http://localhost:8000/BlogService/GetBlog`  
  
     URL, hizmetin temel adresini ( `http://localhost:8000/BlogService` ), bitiş noktasının göreli adresini ve çağrılacak hizmet işlemini içerir.  
  
### <a name="to-call-getblog-from-code"></a>Koddan GetBlog () çağırmak için  
  
1. <xref:System.Xml.XmlReader>Temel adresi ve aradığınız yöntemi içeren bir oluşturun.  
  
     [!code-csharp[htAtomBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#9)]
     [!code-vb[htAtomBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#9)]  
  
2. <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29>Yeni oluşturduğunuz ' ı geçirerek statik yöntemi çağırın <xref:System.Xml.XmlReader> .  
  
     [!code-csharp[htAtomBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#10)]
     [!code-vb[htAtomBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#10)]  
  
     Bu, hizmet işlemini çağırır ve <xref:System.ServiceModel.Syndication.SyndicationFeed> hizmet işleminden döndürülen biçimlendirici ile yeni bir doldurur.  
  
3. Akış nesnesine erişin.  
  
     [!code-csharp[htAtomBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#11)]
     [!code-vb[htAtomBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#11)]  
  
## <a name="example"></a>Örnek  

 Bu örnek için tam kod listesi aşağıda verilmiştir.  
  
 [!code-csharp[htAtomBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#12)]
 [!code-vb[htAtomBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#12)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  

 Önceki kodu derlerken, başvuru System.ServiceModel.dll ve System.ServiceModel.Web.dll.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
