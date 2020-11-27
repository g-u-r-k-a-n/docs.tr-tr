---
title: NativeActivity Temel Sınıfı
ms.date: 03/30/2017
ms.assetid: 254a4c50-425b-426d-a32f-0f7234925bac
ms.openlocfilehash: d875f62dacadb2baf6b5d7e93ddb2933aed9cdb0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274965"
---
# <a name="nativeactivity-base-class"></a>NativeActivity Temel Sınıfı

<xref:System.Activities.NativeActivity> , korumalı Oluşturucusu olan soyut bir sınıftır. Benzer şekilde <xref:System.Activities.CodeActivity> , <xref:System.Activities.NativeActivity> bir yöntemi uygulayarak kesinlik davranışı yazmak için kullanılır <xref:System.Activities.NativeActivity.Execute%2A> . Aksine <xref:System.Activities.CodeActivity> , <xref:System.Activities.NativeActivity> yöntemine geçirilen nesne aracılığıyla iş akışı çalışma zamanının tüm sunulan özelliklerine erişimi vardır <xref:System.Activities.NativeActivityContext> <xref:System.Activities.NativeActivity.Execute%2A> .

## <a name="using-nativeactivitycontext"></a>NativeActivityContext kullanma

 İş akışı çalışma zamanının özelliklerine <xref:System.Activities.NativeActivity.Execute%2A> , türünün ' nin üyelerini kullanarak yönteminin içinden erişilebilir `context` <xref:System.Activities.NativeActivityContext> . Aracılığıyla kullanılabilen özellikler şunları <xref:System.Activities.NativeActivityContext> içerir:

- Bağımsız değişkenlerin ve değişkenlerin alınması ve ayarlanması.

- İle alt etkinlikleri zamanlama <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>

- Kullanılarak Etkinlik yürütme durduruluyor <xref:System.Activities.NativeActivityContext.Abort%2A> .

- Ve kullanarak alt yürütme iptal ediliyor <xref:System.Activities.NativeActivityContext.CancelChild%2A> <xref:System.Activities.NativeActivityContext.CancelChildren%2A> .

- , Ve gibi yöntemler kullanılarak etkinlik yer işaretlerine <xref:System.Activities.NativeActivityContext.CreateBookmark%2A> erişin <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A> <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A> .

- Kullanarak özel izleme özellikleri <xref:System.Activities.CodeActivityContext.Track%2A> .

- Ve kullanarak etkinliğin yürütme özelliklerine ve değer özelliklerine erişin <xref:System.Activities.CodeActivityContext.GetProperty%2A> <xref:System.Activities.NativeActivityContext.GetValue%2A> .

- Ve kullanarak etkinlik eylemlerini ve işlevleri <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> zamanlama <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A> .

### <a name="to-create-a-custom-activity-that-inherits-from-nativeactivity"></a>NativeActivity 'den devralan özel etkinlik oluşturmak için

1. OpenVisual Studio 2010.

2. **Dosya**, **Yeni** ve ardından **Proje**' yi seçin. **Proje türleri** penceresinde **Visual C#** altında **iş akışı 4,0** ' i seçin ve **v2010** düğümünü seçin. **Şablonlar** penceresinde **etkinlik kitaplığı** ' nı seçin. Yeni proje Merhaba etkinliğini adlandırın.

3. Merhaba etkinlik projesinde Activity1. xaml öğesine sağ tıklayın ve **Sil**' i seçin.

4. Merhaba etkinlik projesine sağ tıklayın ve **Ekle**' yi ve ardından **sınıf**' ı seçin. Yeni sınıfı HelloActivity.cs olarak adlandırın.

5. HelloActivity.cs dosyasında aşağıdaki `using` yönergeleri ekleyin.

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. <xref:System.Activities.NativeActivity>Sınıf bildirimine bir temel sınıf ekleyerek yeni sınıfın öğesinden devralmasını sağlayın.

    ```csharp
    class HelloActivity : NativeActivity
    ```

7. Bir yöntem ekleyerek sınıfa işlevsellik ekleyin <xref:System.Activities.NativeActivity.Execute%2A> .

    ```csharp
    protected override void Execute(NativeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. Yöntemi geçersiz kılın <xref:System.Activities.NativeActivity.CacheMetadata%2A> ve iş akışı çalışma zamanının özel etkinliğin değişkenleri, bağımsız değişkenleri, alt öğeleri ve Temsilciler hakkında bilgi almasına izin vermek için uygun ekleme yöntemini çağırın. Daha fazla bilgi için <xref:System.Activities.NativeActivityMetadata> sınıfına bakın.

9. <xref:System.Activities.NativeActivityContext>Bir yer işareti zamanlamak için nesnesini kullanın. <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A>Bir yer işaretinin oluşturulması, zamanlanzamanlaması ve sürdürülmesine ilişkin ayrıntılar için bkz..

    ```csharp
    protected override void Execute(NativeActivityContext context)
        {
            // Create a Bookmark and wait for it to be resumed.
            context.CreateBookmark(BookmarkName.Get(context),
                new BookmarkCallback(OnResumeBookmark));
        }
    ```
