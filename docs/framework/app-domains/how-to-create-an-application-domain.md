---
title: 'Nasıl yapılır: Uygulama Etki Alanı Oluşturma'
description: .NET içinde uygulama etki alanı oluşturma konusunu inceleyin. Kişisel olarak yönetilecek derlemeleri yüklemek için bir uygulama etki alanı oluşturabilir veya kod yürütmek için bir tane oluşturabilirsiniz.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
ms.openlocfilehash: fb022511ee395a9312e4dbaf7c0beee03c9b4569
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96264094"
---
# <a name="how-to-create-an-application-domain"></a>Nasıl yapılır: Uygulama Etki Alanı Oluşturma

Ortak dil çalışma zamanı ana bilgisayarı, gerektiğinde uygulama etki alanlarını otomatik olarak oluşturur. Bununla birlikte, kendi uygulama etki alanlarınızı oluşturabilir ve bunları kişisel olarak yönetmek istediğiniz derlemelere yükleyebilirsiniz. Ayrıca, kodu yürütebileceğiniz uygulama etki alanları da oluşturabilirsiniz.  
  
 Sınıfında aşırı yüklenmiş **CreateDomain** yöntemlerinden birini kullanarak yeni bir uygulama etki alanı oluşturursunuz <xref:System.AppDomain?displayProperty=nameWithType> . Uygulama etki alanına bir ad verebilir ve bu ada göre başvuru yapabilirsiniz.  
  
 Aşağıdaki örnek yeni bir uygulama etki alanı oluşturur, bu adı atar `MyDomain` ve ardından ana bilgisayar etki alanının adını ve yeni oluşturulan alt uygulama etki alanını konsola yazdırır.  
  
## <a name="example"></a>Örnek  

 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama etki alanlarıyla programlama](application-domains.md#programming-with-application-domains)
- [Uygulama Etki Alanlarını Kullanma](use.md)
