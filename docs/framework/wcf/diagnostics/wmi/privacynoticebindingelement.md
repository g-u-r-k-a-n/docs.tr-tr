---
description: 'Hakkında daha fazla bilgi edinin: PrivacyNoticeBindingElement'
title: PrivacyNoticeBindingElement
ms.date: 03/30/2017
ms.assetid: 0cf110b1-e25b-4d67-986b-10cb04dc4826
ms.openlocfilehash: ece6687f12c4ece45254b1acddb9598e4a10cbb8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743888"
---
# <a name="privacynoticebindingelement"></a>PrivacyNoticeBindingElement

PrivacyNoticeBindingElement  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class PrivacyNoticeBindingElement : BindingElement  
{  
  sint32 PrivacyNoticeVersion;  
  string Url;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 PrivacyNoticeBindingElement sınıfı herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 PrivacyNoticeBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="privacynoticeversion"></a>PrivacyNoticeVersion  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Gizlilik bildirimi sürümü.  
  
### <a name="url"></a>Url  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Gizlilik bildiriminin bulunduğu URL.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
