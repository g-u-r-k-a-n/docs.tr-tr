---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: EntityConnection bağlantı dizesi oluşturma'
title: 'Nasıl yapılır: Bir EntityConnection Bağlantı Dizesi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5bd1a748-3df7-4d0a-a607-14f25e3175e9
ms.openlocfilehash: 760ed9d1f362e08135586a56a6b900afcd2b13bd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650839"
---
# <a name="how-to-build-an-entityconnection-connection-string"></a>Nasıl yapılır: Bir EntityConnection Bağlantı Dizesi Oluşturma

Bu konu, oluşturma hakkında bir örnek sağlar <xref:System.Data.EntityClient.EntityConnection> .  
  
### <a name="to-run-the-code-in-this-example"></a>Bu örnekteki kodu çalıştırmak için  
  
1. Projenize [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) ekleyin ve projenizi Entity Framework kullanacak şekilde yapılandırın. Daha fazla bilgi için bkz. [nasıl yapılır: varlık veri modeli Sihirbazı 'Nı kullanma](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
2. Uygulamanızın kod sayfasında, aşağıdaki `using` deyimleri ekleyin ( `Imports` Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType> temel sağlayıcı için öğesini başlatır, sonra <xref:System.Data.EntityClient.EntityConnectionStringBuilder?displayProperty=nameWithType> nesneyi başlatır ve bu nesneyi öğesinin oluşturucusuna geçirir <xref:System.Data.EntityClient.EntityConnection> .  
  
 [!code-csharp[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#buildingconnectionstringwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#buildingconnectionstringwithentitycommand)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: bir nesne bağlamı ile EntityConnection kullanma](/previous-versions/dotnet/netframework-4.0/bb738461(v=vs.100))
- [Entity Framework için EntityClient Sağlayıcısı](entityclient-provider-for-the-entity-framework.md)
