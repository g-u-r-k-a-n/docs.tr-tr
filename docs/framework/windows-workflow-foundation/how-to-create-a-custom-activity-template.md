---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: özel etkinlik şablonu oluşturma'
title: 'Nasıl yapılır: Özel Etkinlik Şablonu Oluşturma'
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: 06fda953110e36e46a91fda8697aadbcd6e6bf59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742114"
---
# <a name="how-to-create-a-custom-activity-template"></a>Nasıl yapılır: Özel Etkinlik Şablonu Oluşturma

Özel Birleşik etkinlikler dahil olmak üzere etkinliklerin yapılandırmalarını özelleştirmek için özel etkinlik şablonları kullanılır. böylece, kullanıcılar her bir etkinliği ayrı ayrı oluşturmak ve özelliklerini ve diğer ayarlarını el ile yapılandırmak zorunda kalmayacak. Bu özel şablonlar Windows İş Akışı Tasarımcısı **araç kutusunda** veya yeniden barındırılan bir tasarımcıdan, kullanıcıların bunları önceden yapılandırılmış tasarım yüzeyine sürükleyebileceği şekilde kullanılabilir hale getirilebilir. İş Akışı Tasarımcısı, Bu şablonların iyi örnekleri ile birlikte gelir: [Ileti etkinliği tasarımcıları](/visualstudio/workflow-designer/messaging-activity-designers) kategorisindeki [SendAndReceiveReply şablon Tasarımcısı](/visualstudio/workflow-designer/sendandreceivereply-template-designer) ve [ReceiveAndSendReply şablon Tasarımcısı](/visualstudio/workflow-designer/receiveandsendreply-template-designer) .

 Bu konudaki ilk yordamda, bir **gecikme** etkinliği için özel etkinlik şablonunun nasıl oluşturulduğu ve ikinci yordamın, özel şablonun çalıştığını doğrulamak için bir iş akışı Tasarımcısı nasıl kullanılabilir hale kullanılacağı kısaca açıklanmaktadır.

 Özel etkinlik şablonlarının uygulaması gerekir <xref:System.Activities.Presentation.IActivityTemplateFactory> . Arabirimin, <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> şablonda kullanılan etkinlik örneklerini oluşturabileceğiniz ve yapılandırabileceği tek bir yöntemi vardır.

## <a name="to-create-a-template-for-the-delay-activity"></a>Gecikme etkinliğine yönelik bir şablon oluşturmak için

1. Visual Studio 2010 ' i başlatın.

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' yi seçin.

     **Yeni proje** iletişim kutusu açılır.

3. **Proje türleri** bölmesinde, dil tercihlerinize göre **Visual C#** projelerinden veya **Visual Basic** gruplamalarından **iş akışı** ' nı seçin.

4. **Şablonlar** bölmesinde **etkinlik kitaplığı**' nı seçin.

5. **Ad** kutusuna girin `DelayActivityTemplate` .

6. **Konum** ve **çözüm adı** metin kutularındaki varsayılan değerleri kabul edin ve ardından **Tamam**' a tıklayın.

7. **Çözüm Gezgini** ' de DelayActivityTemplate projesinin başvurular dizinine sağ tıklayın **ve başvuru Ekle iletişim kutusunu** açmak için **Başvuru Ekle** ' yi seçin.

8. **.Net** sekmesine gidin ve soldaki **bileşen adı** sütunundan **presentationframework** ' ü seçin ve PresentationFramework.dll dosyasına bir başvuru eklemek için **Tamam** ' ı tıklatın.

9. System.Activities.Presentation.dll ve WindowsBase.dll dosyalarına başvurular eklemek için bu yordamı tekrarlayın.

10. **Çözüm Gezgini** ' de DelayActivityTemplate projesine sağ tıklayın ve **Ekle** ' yi ve **Yeni öğe** ' yi seçerek **Yeni öğe Ekle** iletişim kutusunu açın.

11. **Sınıf** şablonunu seçin, MyDelayTemplate olarak adlandırın ve ardından **Tamam**' a tıklayın.

12. MyDelayTemplate.cs dosyasını açın ve aşağıdaki deyimlerini ekleyin.

    ```csharp
    //Namespaces added
    using System.Activities;
    using System.Activities.Statements;
    using System.Activities.Presentation;
    using System.Windows;
    ```

13. <xref:System.Activities.Presentation.IActivityTemplateFactory> `MyDelayActivity` Aşağıdaki kod ile sınıfını ile uygulayın. Bu, gecikme süresini 10 saniyeye sahip olacak şekilde yapılandırır.

    ```csharp
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
    ```

14. DelayActivityTemplate.dll dosyasını oluşturmak için **derleme** menüsünden **çözüm oluştur** ' u seçin.

### <a name="to-make-the-template-available-in-a-workflow-designer"></a>Şablonu bir İş Akışı Tasarımcısı kullanılabilir hale getirmek için

1. **Çözüm Gezgini** ' de DelayActivityTemplate çözümüne sağ tıklayın ve **Ekle** ' yi ve ardından **Yeni proje** ' yi seçerek **Yeni Proje Ekle** iletişim kutusunu açın.

2. **Iş akışı konsol uygulaması** şablonunu seçin, adlandırın `CustomActivityTemplateApp` ve ardından **Tamam**' a tıklayın.

3. **Çözüm Gezgini** ' de CustomActivityTemplateApp projesinin başvurular dizinine sağ tıklayın **ve başvuru Ekle iletişim kutusunu** açmak için **Başvuru Ekle** ' yi seçin.

4. **Projeler** sekmesine gidin ve soldaki **Proje adı** sütunundan **DelayActivityTemplate** öğesini seçin ve ilk yordamda oluşturduğunuz DelayActivityTemplate.dll dosyasına bir başvuru eklemek için **Tamam** ' a tıklayın.

5. **Çözüm Gezgini** ' de CustomActivityTemplateApp projesine sağ tıklayın ve uygulamayı derlemek için **Oluştur** ' u seçin.

6. **Çözüm Gezgini** ' de CustomActivityTemplateApp projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.

7. **Hata ayıklama** menüsünde **hata ayıklama olmadan Başlat** ' ı seçin ve cmd.exe penceresinden sorulduğunda devam etmek için herhangi bir tuşa basın.

8. Workflow1. xaml dosyasını açın ve **araç kutusunu** açın.

9. **DelayActivityTemplate** kategorisinde **MyDelayActivity** şablonunu bulun. Tasarım yüzeyine sürükleyin. **Özellikler** penceresinde, `Duration` özelliğin 10 saniyeye ayarlandığını onaylayın.

## <a name="example"></a>Örnek

 MyDelayActivity.cs dosyası aşağıdaki kodu içermelidir.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

//Namespaces added
using System.Activities;
using System.Activities.Statements;
using System.Activities.Presentation;
using System.Windows;

namespace DelayActivityTemplate
{
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Activities.Presentation.IActivityTemplateFactory>
- [İş Akışı Tasarım Deneyimini Özelleştirme](customizing-the-workflow-design-experience.md)
