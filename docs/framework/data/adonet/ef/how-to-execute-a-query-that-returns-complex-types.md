---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: karmaşık türler döndüren bir sorgu yürütme'
title: 'Nasıl yapılır: Karmaşık Türler Döndüren Bir Sorgu Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: 9a7fb3ea695115529b69def9f95281bac7f33273
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650683"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a>Nasıl yapılır: Karmaşık Türler Döndüren Bir Sorgu Yürütme

Bu konu [!INCLUDE[esql](../../../../../includes/esql-md.md)] , karmaşık bir türün özelliğini içeren varlık türü nesneleri döndüren bir sorgunun nasıl yürütüleceğini gösterir.  
  
### <a name="to-run-the-code-in-this-example"></a>Bu örnekteki kodu çalıştırmak için  
  
1. Projenize [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) ekleyin ve projenizi Entity Framework kullanacak şekilde yapılandırın. Daha fazla bilgi için bkz. [nasıl yapılır: varlık veri modeli Sihirbazı 'Nı kullanma](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
2. Uygulamanızın kod sayfasında, aşağıdaki `using` deyimleri ekleyin ( `Imports` Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. Modeli Entity Desisgner [model tarayıcısı penceresinde](/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) göstermek için. edmx dosyasına çift tıklayın. Entity Desisgner yüzeyinde `Email` `Phone` varlık türünün ve özelliklerini seçin `Contact` , sonra sağ tıklayıp **Yeni karmaşık türde yeniden Düzenle**' yi seçin.  
  
4. Model tarayıcıya seçili ve özelliklere sahip yeni bir karmaşık tür `Email` `Phone` eklenmiştir.  Karmaşık türe varsayılan ad verilir: Özellikler penceresinde türü olarak yeniden adlandırın `EmailPhone` .  Ayrıca, `ComplexProperty` varlık türüne yeni bir özellik eklenir `Contact` . Özelliği olarak yeniden adlandırın `EmailPhoneComplexType.`  
  
     Varlık Veri Modeli Sihirbazı 'Nı kullanarak karmaşık türleri oluşturma ve değiştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: mevcut özellikleri karmaşık bir tür özelliğinde yeniden düzenleme](/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) ve [nasıl yapılır: karmaşık türleri oluşturma ve değiştirme](/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100)).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek bir nesne koleksiyonu döndüren `Contact` ve nesnelerin iki özelliğini `Contact` `ContactID` ve karmaşık türün değerlerini görüntüleyen bir sorgu yürütür `EmailPhoneComplexType` .  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
