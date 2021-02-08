---
description: 'Daha fazla bilgi: nasıl yapılır: Visual Basic Kullanıcı ayarlarını değiştirme'
title: 'Nasıl yapılır: Kullanıcı Ayarlarını Değiştirme'
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: 3877c9fadbf1b5b79470dc9ad41fbaf8123e6770
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797867"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Değiştirme

Nesnenin nesne üzerindeki özelliğine yeni bir değer atayarak, bir kullanıcı ayarını değiştirebilirsiniz `My.Settings` .  
  
 `My.Settings`Nesnesi her ayarı bir özellik olarak gösterir. Özellik adı, ayar adıyla aynıdır ve özellik türü ayar türüyle aynıdır. Ayarın **kapsamı** özelliğin salt okunurdur olduğunu belirler: bir **uygulama** kapsamı ayarının özelliği salt okunurdur, ancak **Kullanıcı** kapsamı ayarı özelliği okuma-yazma olur. Daha fazla bilgi için bkz [. My. Settings nesnesi](../../../language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> Çalışma zamanında kullanıcı kapsamı ayarlarının değerlerini değiştirebilir ve kaydedebilirsiniz, ancak uygulama kapsamı ayarları salt okunurdur ve program aracılığıyla değiştirilemez. Uygulamayı **Proje tasarımcısını** kullanarak oluştururken veya uygulamanın yapılandırma dosyasını düzenleyerek, uygulama kapsamı ayarlarını değiştirebilirsiniz. Daha fazla bilgi için bkz. [uygulama ayarlarını yönetme (.net)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Örnek  

 Bu örnek, Kullanıcı ayarının değerini değiştirir `Nickname` .  
  
 [!code-vb[VbVbalrMyResources#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#7)]  
  
 Bu örneğin çalışması için, uygulamanızın `Nickname` türünde bir Kullanıcı ayarı olması gerekir `String` .  
  
 Uygulama kapandığında uygulama kullanıcı ayarlarını kaydeder. Ayarları hemen kaydetmek için `My.Settings.Save` yöntemini çağırın. Daha fazla bilgi için bkz. [nasıl yapılır: Kullanıcı ayarlarını Visual Basic kalıcı hale](how-to-persist-user-settings.md)getirme.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My.Settings Nesnesi](../../../language-reference/objects/my-settings-object.md)
- [Nasıl Yapılır: Visual Basic'te Uygulama Ayarlarını Okuma](how-to-read-application-settings.md)
- [Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarlarını Kalıcı Yapma](how-to-persist-user-settings.md)
- [Nasıl Yapılır: Visual Basic'te Kullanıcı Ayarları için Özellik Kılavuzu Oluşturma](how-to-create-property-grids-for-user-settings.md)
- [Uygulama Ayarlarını Yönetme](/visualstudio/ide/managing-application-settings-dotnet)
