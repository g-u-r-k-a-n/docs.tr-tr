---
description: 'Daha fazla bilgi edinin: Izlenecek yol: Ilişkiler genelinde sorgulama (C#)'
title: 'İzlenecek yol: İlişkilerde Sorgulama (C#)'
ms.date: 03/30/2017
ms.assetid: 552abeb1-18f2-4e93-a9c6-ef7b2db30c32
ms.openlocfilehash: 35811043ddd7ecc9aca5e1bd87a370abebf90853
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729451"
---
# <a name="walkthrough-querying-across-relationships-c"></a>İzlenecek yol: İlişkilerde Sorgulama (C#)

Bu izlenecek yol, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veritabanındaki yabancı anahtar ilişkilerini temsil etmek için *ilişkilerin* kullanımını gösterir.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Bu izlenecek yol, Visual C# geliştirme ayarları kullanılarak yazılmıştır.  
  
## <a name="prerequisites"></a>Önkoşullar  

 Gözden geçirmeyi tamamlamış olmanız gerekir [: basit nesne modeli ve sorgu (C#)](walkthrough-simple-object-model-and-query-csharp.md). Bu izlenecek yol, c:\linqtest5' teki kuzeydoğu. mdf dosyasının varlığı da dahil olmak üzere bunun üzerine oluşturulur.  
  
## <a name="overview"></a>Genel Bakış  

 Bu izlenecek yol üç ana görevden oluşur:  
  
- Örnek Northwind veritabanındaki Orders tablosunu temsil eden bir varlık sınıfı ekleme.  
  
- `Customer`Ve sınıfları arasındaki ilişkiyi iyileştirmek için sınıfa ek açıklamalar eklemek `Customer` `Order` .  
  
- Sınıfını kullanarak bilgi edinmeyi test etmek için bir sorgu oluşturma ve çalıştırma `Order` `Customer` .  
  
## <a name="mapping-relationships-across-tables"></a>Tablolar arasında Ilişkileri eşleme  

 `Customer`Sınıf tanımından sonra, `Order` `Order.Customer` bir yabancı anahtar olarak ilişkili olduğunu gösteren aşağıdaki kodu içeren varlık sınıfı tanımını oluşturun `Customer.CustomerID` .  
  
### <a name="to-add-the-order-entity-class"></a>Order Entity sınıfını eklemek için  
  
- Aşağıdaki kodu sınıftan sonra yazın veya yapıştırın `Customer` :  
  
     [!code-csharp[DLinqWalk2CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#1)]  
  
## <a name="annotating-the-customer-class"></a>Müşteri sınıfına açıklama ekleme  

 Bu adımda, sınıfıyla `Customer` ilişkisini göstermek için sınıfına açıklama ekleyin `Order` . (Bu ekleme kesinlikle gerekli değildir, çünkü ilişkinin iki yönde tanımlanması bağlantıyı oluşturmak için yeterlidir. Ancak bu ek açıklamanın eklenmesi, nesneleri her iki yönde kolayca gezinmenizi sağlar.)  
  
### <a name="to-annotate-the-customer-class"></a>Müşteri sınıfına açıklama eklemek için  
  
- Aşağıdaki kodu sınıfına yazın veya yapıştırın `Customer` :  
  
     [!code-csharp[DLinqWalk2CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a>Customer-Order Ilişkisi genelinde sorgu oluşturma ve çalıştırma  

 Artık `Order` nesnelere doğrudan `Customer` nesnelerden veya ters sırada erişebilirsiniz. Müşteriler ve siparişler arasında açık bir *birleşime* gerek yoktur.  
  
### <a name="to-access-order-objects-by-using-customer-objects"></a>Müşteri nesnelerini kullanarak sıralama nesnelerine erişim  
  
1. Yöntemine `Main` aşağıdaki kodu yazarak veya yapıştırarak yöntemi değiştirin:  
  
     [!code-csharp[DLinqWalk2CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#3)]  
  
2. Uygulamanızda hata ayıklamak için F5 tuşuna basın.  
  
    > [!NOTE]
    > Konsol penceresinde SQL kodunu, açıklama ekleyerek ortadan kaldırabilirsiniz `db.Log = Console.Out;` .  
  
3. Hata ayıklamayı durdurmak için konsol penceresinde ENTER tuşuna basın.  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a>Veritabanınızın kesin türü belirtilmiş bir görünümünü oluşturma  

 Veritabanınızın kesin türü belirtilmiş bir görünümüyle başlamak çok daha kolay. Nesneyi kesin olarak yazarak <xref:System.Data.Linq.DataContext> , ' a çağrı gerekmez <xref:System.Data.Linq.DataContext.GetTable%2A> . Kesin olarak belirlenmiş nesneyi kullandığınızda tüm sorgularınızda kesin türü belirtilmiş tabloları kullanabilirsiniz <xref:System.Data.Linq.DataContext> .  
  
 Aşağıdaki adımlarda, `Customers` veritabanında müşteriler tablosuyla eşleşen türü kesin belirlenmiş bir tablo olarak oluşturacaksınız.  
  
### <a name="to-strongly-type-the-datacontext-object"></a>DataContext nesnesini kesin olarak yazmak için  
  
1. Aşağıdaki kodu sınıf bildiriminin üstüne ekleyin `Customer` .  
  
     [!code-csharp[DLinqWalk2CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#4)]  
  
2. Yöntemi, `Main` türü kesin belirlenmiş olarak kullanmak için <xref:System.Data.Linq.DataContext> aşağıdaki gibi değiştirin:  
  
     [!code-csharp[DLinqWalk2CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#5)]  
  
3. Uygulamanızda hata ayıklamak için F5 tuşuna basın.  
  
     Konsol penceresi çıkışı:  
  
     `ID=WHITC`  
  
4. Hata ayıklamayı durdurmak için konsol penceresinde ENTER tuşuna basın.  
  
## <a name="next-steps"></a>Sonraki Adımlar  

 Sonraki izlenecek yol ([Izlenecek yol: verileri düzenleme (C#)](walkthrough-manipulating-data-csharp.md)), verilerin nasıl değiştirileceğini gösterir. Bu izlenecek yol, zaten tamamladığınız bu serideki iki izlenecek yolu kaydetmenizi gerektirmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek Yollarla Öğrenme](learning-by-walkthroughs.md)
