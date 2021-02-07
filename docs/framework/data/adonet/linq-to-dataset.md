---
description: 'Hakkında daha fazla bilgi edinin: LINQ to DataSet'
title: LINQ - DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 74b5f97d9fecb05b1fd13e986dd0cbcc10fa1456
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681675"
---
# <a name="linq-to-dataset"></a>LINQ - DataSet

LINQ to DataSet, bir nesnede önbelleğe alınan verilerin sorgulanmasını kolaylaştırır ve daha hızlı hale getirir <xref:System.Data.DataSet> . Özellikle LINQ to DataSet, geliştiricilerin ayrı bir sorgu dili yerine programlama dilinin kendisinden sorgu yazmasını sağlayarak sorgulamayı basitleştirir. Bu özellikle Visual Studio geliştiricileri için yararlıdır. artık, derleme zamanı sözdizimi denetimi, statik yazma ve Visual Studio tarafından sorgularda sunulan IntelliSense desteğinden faydalanabilir.  
  
 LINQ to DataSet, bir veya daha fazla veri kaynağından birleştirilmiş verileri sorgulamak için de kullanılabilir. Bu, yerel olarak toplanmış verileri sorgulama ve Web uygulamalarında orta katman önbelleğe alma gibi, verilerin nasıl temsil edildiği ve işlendiği konusunda esneklik gerektiren birçok senaryoyu sağlar. Özellikle, genel raporlama, analiz ve iş zekası uygulamaları için bu işleme yöntemi gerekir.  
  
 LINQ to DataSet işlevselliği öncelikle ve sınıflarındaki uzantı yöntemleri aracılığıyla gösterilir <xref:System.Data.DataRowExtensions> <xref:System.Data.DataTableExtensions> . LINQ to DataSet, ve var olan ADO.NET mimarisini kullanır ve uygulama kodundaki ADO.NET 'in yerini almak için tasarlanmamıştır. Mevcut ADO.NET kodu bir LINQ to DataSet uygulamasında çalışmaya devam edecektir. ADO.NET ve veri deposuna LINQ to DataSet ilişkisi aşağıdaki diyagramda gösterilmiştir.  
  
 ![LINQ to DataSet, ADO.NET sağlayıcıya bağlı olduğunu gösteren diyagram.](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Başlarken](getting-started-linq-to-dataset.md)  
  
 [Programlama Kılavuzu](programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>Başvuru  

 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile tümleşik sorgu (LINQ)-C #](../../../csharp/programming-guide/concepts/linq/index.md)
- [Dil ile tümleşik sorgu (LINQ)-Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ ve ADO.NET](linq-and-ado-net.md)
- [ADO.NET](index.md)
