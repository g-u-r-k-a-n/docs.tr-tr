---
title: 'Nasıl yapılır: X.509 Sertifikalarına Tutarlı Olarak Başvuru Yapma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], referencing X.509 certificates
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
ms.openlocfilehash: b5be8990384178c1954834204c23c0b9cf4a5ad9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257281"
---
# <a name="how-to-consistently-reference-x509-certificates"></a>Nasıl yapılır: X.509 Sertifikalarına Tutarlı Olarak Başvuru Yapma

Sertifikayı çeşitli yollarla tanımlayabilirsiniz: sertifikanın karması ile, veren ve seri numarası veya konu anahtar tanımlayıcısı (kayak). Kayak, sertifikanın konu ortak anahtarı için benzersiz bir kimlik sağlar ve genellikle XML dijital imzalama ile çalışırken kullanılır. Kayak değeri genellikle x. 509.440 sertifikasının *x. 509.440 sertifika uzantısı* olarak bir parçasıdır. Windows Communication Foundation (WCF), Kayak uzantısı sertifikada yoksa veren ve seri numarasını kullanan bir varsayılan *başvuru stiline* sahiptir. Sertifika Kayak uzantısını içeriyorsa, varsayılan başvuru stili sertifikayı işaret etmek için kayak kullanır. Bir uygulamanın geliştirilmesi ile ilgili olarak, Kayak uzantısını kullanmayan sertifikaları Kayak uzantısını kullanan sertifikalara geçiş yaparsanız, WCF tarafından oluşturulan iletilerde kullanılan başvuru stili de değişir.  
  
 Kayak Extension varlığından bağımsız olarak tutarlı bir başvuru stili gerekliyse, istenen başvuru stilini aşağıdaki kodda gösterildiği gibi yapılandırmak mümkündür.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, tek bir tutarlı başvuru stili, verenin adı ve seri numarası kullanan özel bir güvenlik bağlama öğesi oluşturur.  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  

 Kodu derlemek için aşağıdaki ad alanları gereklidir:  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
- <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sertifikalarla Çalışma](working-with-certificates.md)
