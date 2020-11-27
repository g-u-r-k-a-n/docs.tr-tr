---
title: 'Nasıl yapılır: Aynı Türde Birden Fazla Belirteç Kullanma'
ms.date: 03/30/2017
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
ms.openlocfilehash: 7374eebb9e42ef761b7ab8980b3eacf4d5671e6d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280708"
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a>Nasıl yapılır: Aynı Türde Birden Fazla Belirteç Kullanma

- .NET Framework 3,0 ' de, istemci iletisi yalnızca belirli bir türün bir belirtecini içeriyordu. Artık istemci iletileri bir tür için birden çok belirteç içerebilir. Bu konu başlığında, istemci iletisinde aynı türde birden fazla belirteç ekleme gösterilmektedir.  
  
- Hizmeti bu şekilde yapılandıramayacağınızı unutmayın: bir hizmet yalnızca bir destekleme belirteci içerebilir.  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a>Aynı türde birden fazla güvenlik belirteci kullanmak için  
  
1. Doldurulacak boş bir bağlama öğesi koleksiyonu oluşturun.  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2. Çağırarak oluşturun <xref:System.ServiceModel.Channels.SecurityBindingElement> <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A> .  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3. Koleksiyon oluşturun <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> .  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4. Koleksiyona SAML belirteçleri ekleyin.  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5. Koleksiyonunu öğesine ekleyin <xref:System.ServiceModel.Channels.SecurityBindingElement> .  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6. Bağlama öğesi koleksiyonuna bağlama öğeleri ekleyin.  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7. Bağlama öğesi koleksiyonundan oluşturulan yeni bir özel bağlama döndürür.  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a>Örnek  

 Aşağıda, önceki yordamda açıklanan yöntemin tamamı verilmiştir.  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
