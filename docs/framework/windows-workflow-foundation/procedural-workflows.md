---
title: Yordam İş Akışları
description: Workflow Foundation 'da, yordamsal iş akışları, yordamsal dillerde bulunanlara benzer akış denetimi yöntemlerini kullanır.
ms.date: 03/30/2017
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
ms.openlocfilehash: 13d1b5e55b84687e2a78db1a94317b8b1e33328c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96246036"
---
# <a name="procedural-workflows"></a>Yordam İş Akışları

Yordamsal iş akışları, yordamsal dillerde bulunanlara benzer akış denetimi yöntemlerini kullanır. Bu yapılar `While` ve içerir `If` . Bu iş akışları, ve gibi diğer akış denetimi etkinlikleri kullanılarak serbestçe oluşturulabilir <xref:System.Activities.Statements.Flowchart> <xref:System.Activities.Statements.Sequence> .  
  
## <a name="controlling-execution-flow"></a>Yürütme akışını denetleme  

 İş akışı etkinlik kitaplığı, yordamsal dillerde kullanılan akış denetimi yöntemlerinin çoğunu modellemeye yönelik etkinlikleri içerir. Bunlar:  
  
- <xref:System.Activities.Statements.While>  
  
- <xref:System.Activities.Statements.DoWhile>  
  
- <xref:System.Activities.Statements.ForEach%601>  
  
- <xref:System.Activities.Statements.Parallel>  
  
- <xref:System.Activities.Statements.ParallelForEach%601>  
  
- <xref:System.Activities.Statements.If>  
  
- <xref:System.Activities.Statements.Switch%601>  
  
- <xref:System.Activities.Statements.Pick>  
  
 Flow denetim etkinliklerini kullanmak için, onları **etkinlik** araç kutusundan Tasarımcı penceresinin içindeki bir bileşik etkinliğe sürükleyip bırakın.  
  
> [!NOTE]
> Web çiftliğinde iş akışlarını barındırmak için Windows Server AppFabric barındırma özelliklerini kullanıyorsanız, AppFabric örnekleri farklı bir AppFabric sunucuları arasında taşıyacaktır. Bu, kaynakların tüm düğümler arasında paylaşılabilmesi için gereklidir.  Varsayılan NET 4 iş akışı etkinliklerinin hiçbiri, yerel kaynaklara erişen işlemler içermez. AppFabric bir iş akışını taşınabilir olarak işaretlemek için herhangi bir mekanizma sunmadığından, bir geliştirici bir iş akışı taşındığında başarısız olan özel etkinlikler oluşturmamalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Akış Çizelgesi İş Akışları](flowchart-workflows.md)
