---
description: 'Daha fazla bilgi edinin: değişken ve bağımsız değişken Izleme'
title: Değişken ve Bağımsız Değişken İzleme
ms.date: 03/30/2017
ms.assetid: 8f3d9d30-d899-49aa-b7ce-a8d0d32c4ff0
ms.openlocfilehash: f2663e585ca280739f9c4ec176c31cf1d7c30657
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754985"
---
# <a name="variable-and-argument-tracking"></a>Değişken ve Bağımsız Değişken İzleme

Bir iş akışının yürütülmesi izlenirken, verileri ayıklamak genellikle yararlı olur. Bu, bir izleme kaydına erişirken yürütme sonrası ek bağlam sağlar. ' De [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] , izleme kullanarak bir iş akışındaki herhangi bir etkinliğin kapsamındaki görünür herhangi bir değişkeni veya bağımsız değişkeni ayıklayabilirsiniz. İzleme profilleri, verileri ayıklamayı kolaylaştırır.  
  
## <a name="variables-and-arguments"></a>Değişkenler ve Bağımsız Değişkenler  

 Bir etkinlik bir ActivityStateRecord yayar olduğunda değişkenler ve bağımsız değişkenler ayıklanır.  Değişken, yalnızca etkinliğin kapsamı içindeyse, ayıklama için kullanılabilir. Bir etkinlik içinde Ayıklanacak bir değişken aşağıdaki şekilde belirtilir:  
  
- Değişken adıyla bir değişken belirtilmişse, izleme geçerli etkinliğin içinde ve üst etkinliklerdeki değişkeni arar. Değişken geçerli etkinlik kapsamında ve üst kapsamda aranır.  
  
- Ayıklanacak değişkenler Name = "" kullanılarak belirtilmişse \* , izlenen geçerli etkinliğin içindeki tüm değişkenler ayıklanır. Bu durumda, kapsamdaki ancak üst etkinliklerde tanımlanan değişkenler ayıklanmaz.  
  
 Bağımsız değişkenler ayıklanırken, ayıklanan bağımsız değişkenler etkinliğin durumuna bağlıdır. Etkinliğin durumu yürütürken yalnızca, `InArguments` ayıklama için kullanılabilir. Diğer etkinlik durumları (kapalı, hatalı, Iptal edildi) için, tüm bağımsız değişkenler, hem InArguments hem de OutArguments, ayıklama için kullanılabilir.  
  
 Aşağıdaki örnekte, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterilmektedir. Değişkenler ve bağımsız değişkenler yalnızca ile ayıklanabilir <xref:System.Activities.Tracking.ActivityStateRecord> ve bu nedenle kullanılarak bir izleme profili içinde abone olunmuş olur <xref:System.Activities.Tracking.ActivityStateQuery> .  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="protecting-information-stored-within-variables-and-arguments"></a>Değişkenler ve bağımsız değişkenler Içinde depolanan bilgileri koruma  

 İzlenen bir değişken veya bağımsız değişken varsayılan olarak WF çalışma zamanı tarafından görünür hale getirilir. Bir iş akışı geliştiricisi, aşağıdaki adımları uygulayarak bu BT 'nin erişmesini koruyabilir:  
  
1. Bir değişkenin değerini şifreleyin.  
  
2. Bir değişkenin veya bağımsız değişkenin ayıklanmasını engellemek için bir izleme profili yazmayı denetleyin.  
  
3. Özel izleme katılımcıları için, WF kodunun değişkenlerde veya bağımsız değişkenlerde depolanan hassas bilgileri açıklamadığından emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Server App Fabric Izleme](/previous-versions/appfabric/ee677251(v=azure.10))
- [App Fabric ile uygulamaları izleme](/previous-versions/appfabric/ee677276(v=azure.10))
