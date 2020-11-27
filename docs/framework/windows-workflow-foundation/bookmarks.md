---
title: Yer işaretleri-WF
ms.date: 03/30/2017
ms.assetid: 9b51a346-09ae-455c-a70a-e2264ddeb9e2
ms.openlocfilehash: 7a52823ff68d8f09895bb3a9323a57d3abccd823
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289119"
---
# <a name="bookmarks"></a>Yer işaretleri

Yer işaretleri, bir etkinliğin bir iş akışı iş parçacığına sahip olmadan giriş için büyük bir süre beklemesini sağlayan mekanizmadır. Bir etkinlik, Stimulus için beklediğini işaret eder, bir yer işareti oluşturabilir. Bu, şu anda yürütülmekte olan Yöntem (tarafından oluşturulan) tarafından döndürülen çalışma zamanına etkinlik yürütmenin tamamlanma kabul edilmesi gerektiğini gösterir <xref:System.Activities.Bookmark> .  
  
## <a name="bookmark-basics"></a>Yer işareti temelleri  

 Bir <xref:System.Activities.Bookmark> iş akışı örneği içinde yürütmenin sürdürülebilecek (ve hangi girişin teslim edileceği) bir noktayı temsil eder. Genellikle, bir <xref:System.Activities.Bookmark> ad ve dış (konak veya uzantı) kodu, yer işaretinin ilgili verilerle sürdürülmesinden sorumludur. Bir <xref:System.Activities.Bookmark> devam edildiğinde, iş akışı çalışma zamanı, <xref:System.Activities.BookmarkCallback> oluşturma sırasında ilişkili temsilciyi zamanlar <xref:System.Activities.Bookmark> .  
  
## <a name="bookmark-options"></a>Yer işareti seçenekleri  

 <xref:System.Activities.BookmarkOptions>Sınıf, oluşturulmakta olan türünü belirtir <xref:System.Activities.Bookmark> . Birbirini dışlayan olası olmayan değerler <xref:System.Activities.BookmarkOptions.None> , ve ' dir <xref:System.Activities.BookmarkOptions.MultipleResume> <xref:System.Activities.BookmarkOptions.NonBlocking> . <xref:System.Activities.BookmarkOptions.None> <xref:System.Activities.Bookmark> Tam olarak bir kez sürdürülmeleri beklenen, oluşturma işlemi varsayılan olan ' ı kullanın. <xref:System.Activities.BookmarkOptions.MultipleResume> <xref:System.Activities.Bookmark> Birden çok kez devam ettirilebilecek bir oluşturma sırasında kullanın. <xref:System.Activities.BookmarkOptions.NonBlocking> <xref:System.Activities.Bookmark> Hiçbir zaman sürdürülmeyebilir bir oluşturma sırasında kullanın. Varsayılan değer kullanılarak oluşturulan yer işaretlerinin aksine <xref:System.Activities.BookmarkOptions> , <xref:System.Activities.BookmarkOptions.NonBlocking> yer işaretleri bir etkinliğin tamamlanmasını engellemez.  
  
## <a name="bookmark-resumption"></a>Yer işareti sürdürme  

 Yer işaretleri, aşırı yüklerden birini kullanan bir iş akışı dışındaki kodla devam edebilir <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> . Bu örnekte, bir `ReadLine` etkinlik oluşturulur. Yürütüldüğünde, `ReadLine` etkinlik bir oluşturur, bir <xref:System.Activities.Bookmark> geri çağırma kaydeder ve <xref:System.Activities.Bookmark> devam etmek için bekler. Devam edildiğinde `ReadLine` etkinlik, ile geçilen verileri <xref:System.Activities.Bookmark> <xref:System.Activities.Activity%601.Result%2A> bağımsız değişkenine atar.  
  
```csharp  
public sealed class ReadLine : NativeActivity<string>  
{  
    [RequiredArgument]  
    public  InArgument<string> BookmarkName { get; set; }  
  
    protected override void Execute(NativeActivityContext context)  
    {  
        // Create a Bookmark and wait for it to be resumed.  
        context.CreateBookmark(BookmarkName.Get(context),
            new BookmarkCallback(OnResumeBookmark));  
    }  
  
    // NativeActivity derived activities that do asynchronous operations by calling
    // one of the CreateBookmark overloads defined on System.Activities.NativeActivityContext
    // must override the CanInduceIdle property and return true.  
    protected override bool CanInduceIdle  
    {  
        get { return true; }  
    }  
  
    public void OnResumeBookmark(NativeActivityContext context, Bookmark bookmark, object obj)  
    {  
        // When the Bookmark is resumed, assign its value to  
        // the Result argument.  
        Result.Set(context, (string)obj);  
    }  
}  
```  
  
 Bu örnekte, `ReadLine` etkinliğin Kullanıcı adını toplayıp konsol penceresinde görüntülemesi için etkinliğini kullanan bir iş akışı oluşturulur. Ana bilgisayar uygulaması, giriş toplama işini gerçekleştirir ve devam ederek iş akışına geçirir <xref:System.Activities.Bookmark> .  
  
```csharp  
Variable<string> name = new Variable<string>  
{  
    Name = "name"  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        name  
    },  
    Activities =  
    {  
        new WriteLine()  
        {  
            Text = "What is your name?"  
        },  
        new ReadLine()  
        {  
            BookmarkName = "UserName",  
            Result = name  
        },  
        new WriteLine()  
        {  
            Text = new InArgument<string>((env) => "Hello, " + name.Get(env))  
        }  
    }  
};  
  
AutoResetEvent syncEvent = new AutoResetEvent(false);  
  
// Create the WorkflowApplication using the desired  
// workflow definition.  
WorkflowApplication wfApp = new WorkflowApplication(wf);  
  
// Handle the desired lifecycle events.  
wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
{  
    // Signal the host that the workflow is complete.  
    syncEvent.Set();  
};  
  
// Start the workflow.  
wfApp.Run();  
  
// Collect the user's name and resume the bookmark.  
// Bookmark resumption only occurs when the workflow  
// is idle. If a call to ResumeBookmark is made and the workflow  
// is not idle, ResumeBookmark blocks until the workflow becomes  
// idle before resuming the bookmark.  
wfApp.ResumeBookmark("UserName", Console.ReadLine());  
  
// Wait for Completed to arrive and signal that  
// the workflow is complete.  
syncEvent.WaitOne();  
```  
  
 `ReadLine`Etkinlik yürütüldüğünde, <xref:System.Activities.Bookmark> adlandırılmış bir adı oluşturur `UserName` ve sonra yer işaretinin sürdürülmesini bekler. Konak, istenen verileri toplar ve ardından devam ettirir <xref:System.Activities.Bookmark> . İş akışı devam eder, adı görüntüler ve sonra tamamlar. Yer işaretinin sürdürülmeye devam ettiğine ilişkin hiçbir eşitleme kodu gerekmediğini unutmayın. <xref:System.Activities.Bookmark>Yalnızca iş akışı boşta kaldığında devam edebilir ve iş akışı boşta değilse <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> iş akışı boşta olana kadar blokları çağırır.  
  
## <a name="bookmark-resumption-result"></a>Yer işareti sürdürme sonucu  

 <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A><xref:System.Activities.BookmarkResumptionResult>Bookmark sürdürme isteğinin sonuçlarını göstermek için bir sabit listesi değeri döndürür. Olası dönüş değerleri <xref:System.Activities.BookmarkResumptionResult.Success> , ve ' dir <xref:System.Activities.BookmarkResumptionResult.NotReady> <xref:System.Activities.BookmarkResumptionResult.NotFound> . Konaklar ve uzantılar, devam etmek için bu değeri kullanabilir.
