---
title: 'Nasıl Yapılır: Kullanıcı Ayarlarını Kalıcı Yapma'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: b1026e400015ff7807144dca8e9ce6d72fe3d18e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74329636"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Kalıcı Yapma

Kullanıcı ayarlarındaki `My.Settings.Save` değişiklikleri sürdürmek için yöntemi kullanabilirsiniz.  
  
 Genellikle, uygulamalar kapatıldığında kullanıcı ayarlarındaki değişiklikleri sürdürmek üzere tasarlanmıştır. Bunun nedeni, ayarları kaydetmenin birkaç etkene bağlı olarak birkaç saniye sürebileceğidir.  
  
 Daha fazla bilgi için [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md)' e bakın.  
  
> [!NOTE]
> Çalışma zamanında kullanıcı kapsamı ayarlarının değerlerini değiştirip kaydedebilirsiniz, ancak uygulama kapsamı ayarları salt okunur ve programlı olarak değiştirilemez. Uygulamayı oluştururken, **Proje Tasarımcısı**aracılığıyla veya uygulamanın yapılandırma dosyasını düzenleyerek uygulama kapsamı ayarlarını değiştirebilirsiniz. Daha fazla bilgi için bkz: [Uygulama Ayarlarını Yönetme (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Örnek  

 Bu örnek, `LastChanged` kullanıcı ayarı değerini değiştirir ve `My.Settings.Save` yöntemi çağırarak bu değişikliği kaydeder.  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 Bu örneğin çalışabilmesi için, uygulamanızın bir `LastChanged` kullanıcı `Date`ayarı olması gerekir. Daha fazla bilgi için bkz: [Uygulama Ayarlarını Yönetme (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My.Settings Nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Uygulama Ayarlarını Yönetme](/visualstudio/ide/managing-application-settings-dotnet)
