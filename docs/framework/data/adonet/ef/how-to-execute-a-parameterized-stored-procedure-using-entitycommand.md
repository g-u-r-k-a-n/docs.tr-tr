---
description: 'Daha fazla bilgi edinin: nasıl yapılır: EntityCommand kullanarak parametreli saklı yordam yürütme'
title: 'Nasıl yapılır: EntityCommand Kullanarak Parametreli Saklı Yordam Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4f5639bf-bb7f-4982-bb1d-c7caa4348888
ms.openlocfilehash: a45c9a276cc33037a4d353e05d1174c9748aab82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650696"
---
# <a name="how-to-execute-a-parameterized-stored-procedure-using-entitycommand"></a>Nasıl yapılır: EntityCommand Kullanarak Parametreli Saklı Yordam Yürütme

Bu konu, sınıfını kullanarak parametreli saklı yordamın nasıl yürütüleceğini gösterir <xref:System.Data.EntityClient.EntityCommand> .  
  
### <a name="to-run-the-code-in-this-example"></a>Bu örnekteki kodu çalıştırmak için  
  
1. [Okul modelini](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) projenize ekleyin ve projenizi Entity Framework kullanacak şekilde yapılandırın. Daha fazla bilgi için bkz. [nasıl yapılır: varlık veri modeli Sihirbazı 'Nı kullanma](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
2. Uygulamanızın kod sayfasında, aşağıdaki `using` deyimleri ekleyin ( `Imports` Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. `GetStudentGrades`Saklı yordamı içeri aktarın ve `CourseGrade` varlık dönüş türü olarak belirtin. Saklı yordamı içeri aktarma hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir saklı yordamı Içeri aktarma](/previous-versions/dotnet/netframework-4.0/bb896231(v=vs.100)).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, `GetStudentGrades` `StudentId` gerekli bir parametre olan saklı yordamı yürütür. Sonuçlar daha sonra bir ile okunurdur <xref:System.Data.EntityClient.EntityDataReader> .  
  
 [!code-csharp[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#storedprocwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#storedprocwithentitycommand)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity Framework için EntityClient Sağlayıcısı](entityclient-provider-for-the-entity-framework.md)
