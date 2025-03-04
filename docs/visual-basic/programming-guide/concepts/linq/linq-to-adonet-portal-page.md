---
description: 'Hakkında daha fazla bilgi edinin: LINQ to ADO.NET (portal sayfası)'
title: ADO.NET'e LINQ (Portal Sayfası)
ms.date: 07/20/2015
ms.assetid: bbbd7c76-2981-4b91-b8d2-437547181f52
ms.openlocfilehash: 5fe670be0bb87fb9a18ee73b3c3ea341d787b13e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100426757"
---
# <a name="linq-to-adonet-portal-page"></a>ADO.NET'e LINQ (Portal Sayfası)

LINQ to ADO.NET, Language-Integrated Query (LINQ) programlama modelini kullanarak ADO.NET içinde herhangi bir numaralandırılabilir nesne üzerinde sorgulama yapmanızı sağlar.  
  
> [!NOTE]
> LINQ to ADO.NET belge .NET Framework SDK: [LINQ ve ADO.net](../../../../framework/data/adonet/linq-and-ado-net.md)' nin ADO.net bölümünde bulunur.
  
 Üç ayrı ADO.NET Language-Integrated Query (LINQ) teknolojisi vardır: LINQ to DataSet, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] ve LINQ to Entities. LINQ to DataSet üzerinde daha zengin, iyileştirilmiş sorgulama sağlar <xref:System.Data.DataSet> , [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] SQL Server veritabanı şemalarını doğrudan sorgulayabilir ve LINQ to Entities varlık veri modeli sorgulamanızı sağlar.  
  
## <a name="linq-to-dataset"></a>LINQ - DataSet  

 , <xref:System.Data.DataSet> ADO.net ' deki en yaygın olarak kullanılan bileşenlerden biridir ve ADO.net 'in üzerinde oluşturulduğu, bağlantısı kesilen programlama modelinin temel öğesidir. Ancak, bu kadar belirgin olsa da, <xref:System.Data.DataSet> sınırlı sorgu yeteneklerine sahiptir.  
  
 LINQ to DataSet, <xref:System.Data.DataSet> diğer birçok veri kaynağı için kullanılabilen aynı sorgu işlevini kullanarak ' ye daha zengin sorgu özellikleri oluşturmanızı sağlar.  
  
 Daha fazla bilgi için bkz. [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ to SQL  

 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] ilişkisel verileri nesne olarak yönetmeye yönelik bir çalışma zamanı altyapısı sağlar. [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]' De, bir ilişkisel veritabanının veri modeli, geliştiricinin programlama dilinde ifade edilen bir nesne modeliyle eşleştirilir. Uygulamayı yürüttüğünüzde, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] nesne modelindeki dil ile tümleşik SORGULARı SQL 'e çevirir ve yürütmek üzere veritabanına gönderir. Veritabanı sonuçları döndürdüğünde, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] bunları işleyebileceğiniz nesnelere geri çevirir.  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] , veritabanında saklı yordamlar ve Kullanıcı tanımlı işlevler ve nesne modelinde devralma için destek içerir.  
  
 Daha fazla bilgi için bkz. [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ - Varlıklar  

 Varlık Veri Modeli, ilişkisel veriler .NET ortamında nesneler olarak sunulur. Bu, nesne katmanını LINQ desteği için ideal bir hedef haline getirir ve geliştiricilerin iş mantığını oluşturmak için kullanılan dilden sorguları veritabanına göre formüllemesini sağlar. Bu yetenek LINQ to Entities olarak bilinir. Daha fazla bilgi için bkz. [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)
- [Dil ile tümleşik sorgu (LINQ) (Visual Basic)](index.md)
