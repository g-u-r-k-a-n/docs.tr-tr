---
description: 'Hakkında daha fazla bilgi edinin: 110-CustomTrackingRecordWarning'
title: 110 - CustomTrackingRecordWarning
ms.date: 03/30/2017
ms.assetid: 3bc093de-be47-4ed0-983f-05b4246446fc
ms.openlocfilehash: d127b0fbf8fa4f2d7285068486a900452685346d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667609"
---
# <a name="110---customtrackingrecordwarning"></a>110 - CustomTrackingRecordWarning

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Id|110|  
|Anahtar sözcükler|Kullanıcıetkinlikleri, EndToEndMonitoring, sorun giderme, HealthMonitoring, WFTracking|  
|Level|Uyarı|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Bu olay, bir iş akışı örneği içindeki bir etkinlik, düzey uyarısı olan CustomTrackingRecord ' i yayıyorsa ETW izleme katılımcısı tarafından yayılır  
  
## <a name="message"></a>İleti  

 TrackRecord = CustomTrackingRecord, InstanceId = %1, RecordNumber = %2, EventTime = %3, ad = %4, ActivityName = %5, ActivityID = %6, ActivityInstanceId = %7, ActivityTypeName = %8, veri = %9, ek açıklamalar = %10, ProfileName = %11  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs: GUID|İş akışının örnek kimliği|  
|RecordNumber|xs: Long|Yayınlanan kaydın sıra numarası|  
|EventTime|xs: dateTime|Olayın yayılışında UTC olarak zaman|  
|Name|xs: String|CustomTrackingRecord adı|  
|Özelliğinde|xs: String|CustomTrackingRecord ' a yayılan etkinliğin adı|  
|ActivityId|xs: String|CustomTrackingRecord öğesini oluşturan etkinliğin kimliği|  
|ActivityInstanceId|xs: String|CustomTrackingRecord öğesini oluşturan etkinliğin örnek kimliği|  
|ActivityTypeName|xs: String|CustomTrackingRecord ' a yayılan etkinliğin adı|  
|Veriler|xs: String|Bu olayla izlenen veriler.  Değerler, dataValue biçimindeki bir XML öğesinde depolanır \<items> \< item  name = "dataName" type="System.String"> \</item> \</items> .  Hiçbir veri izlenmediyse dize içerir \<items/> . ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yük ile sınırlıdır. Olayın boyutu ETW sınırlarını aşarsa, ek açıklamaları bırakarak ve veri değeri \<items> .. \</items> . ile değiştirilerek olay kesilir.  Aşağıdaki türler, ToString () tarafından döndürülen değerleri olarak depolanır. dize, Char, bool, int, Short, Long, uint, ushort, ulong, System. Single, float, Double, System. Guid, System. DateTimeOffset, System. DateTime.  Tüm diğer türler System. Runtime. Serialization. NetDataContractSerializer kullanılarak serileştirilir.|  
|Ek Açıklamalar|xs: String|Bu olaya eklenen ek açıklamalar.  Değerler, \<items> \< item  name = "annotationName" type="System.String"> annotationValue biçiminde bir XML öğesinde depolanır \</item> \</items> .  Ek açıklama belirtilmemişse dize içerir \<items/> . ETW olay boyutu ETW arabellek boyutu veya bir ETW olayı için en fazla yük ile sınırlıdır. Olayın boyutu ETW sınırlarını aşarsa, ek açıklamaları bırakarak ve ek açıklama değeri... ile değiştirilerek olay kesilir \<items> \</items> .|  
|ProfileName|xs: String|Bu olayla sonuçlanan ad veya izleme profili|  
|HostReference|xs: String|Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.  Biçim, ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' örneği olarak tanımlanmıştır: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
