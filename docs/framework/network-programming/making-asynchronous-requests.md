---
title: Zaman Uyumsuz İstekler Yapma
description: System.Net sınıflarının Internet kaynaklarına yönelik zaman uyumsuz erişim için .NET Framework standart zaman uyumsuz programlama modelini nasıl kullandığını öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Internet, asynchronous access
- Networking
- asynchronous requests, Internet resources
- Network Resources
- WebRequest class, asynchronous access
ms.assetid: 735d3fce-f80c-437f-b02c-5c47f5739674
ms.openlocfilehash: f6eba7a1f10e037f93b20c0e7016f083e3e24200
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258718"
---
# <a name="making-asynchronous-requests"></a>Zaman Uyumsuz İstekler Yapma

<xref:System.Net>Sınıflar, Internet kaynaklarına zaman uyumsuz erişim için .NET Framework standart zaman uyumsuz programlama modelini kullanır. <xref:System.Net.WebRequest.BeginGetResponse%2A>Sınıfının ve <xref:System.Net.WebRequest.EndGetResponse%2A> yöntemleri <xref:System.Net.WebRequest> bir Internet kaynağı için zaman uyumsuz istekleri başlatır ve tamamlar.  
  
> [!NOTE]
> Zaman uyumsuz geri çağırma yöntemlerinde zaman uyumlu çağrıların kullanılması ciddi performans cezalarına neden olabilir. **WebRequest** ile yapılan Internet istekleri ve alt öğeleri <xref:System.IO.Stream.BeginRead%2A?displayProperty=nameWithType> , yöntemi tarafından döndürülen akışı okumak için kullanılmalıdır <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> .  
  
 Aşağıdaki örnek kod, **WebRequest** sınıfıyla zaman uyumsuz çağrıların nasıl kullanılacağını göstermektedir. Örnek, komut satırından URI alan bir konsol programıdır, kaynağı URI üzerinde ister ve sonra verileri Internet 'ten alındığından konsola yazdırır.  
  
 Program kendi kullanımı için iki sınıf tanımlar, zaman uyumsuz çağrılarda verileri geçen **RequestState** sınıfı ve zaman uyumsuz Istekleri bir Internet kaynağına uygulayan **ClientGetAsync** sınıfı.  
  
 **RequestState** sınıfı, isteği sunan zaman uyumsuz yöntemlere yapılan çağrılar genelinde isteğin durumunu korur. **Web isteği** ve <xref:System.IO.Stream> kaynak için geçerli isteği ve yanıt olarak alınan akışı, Internet kaynağından alınan verileri içeren bir arabelleği ve <xref:System.Text.StringBuilder> tamamlanmış yanıtı içeren örnekleri içerir. *state* **RequestState** <xref:System.AsyncCallback> Yöntem **WebRequest. BeginGetResponse** ile kaydettirilirse, bir RequestState durum parametresi olarak geçirilir.  
  
 **ClientGetAsync** sınıfı bir Internet kaynağına zaman uyumsuz bir istek uygular ve sonuçta elde edilen yanıtı konsola yazar. Aşağıdaki listede açıklanan yöntemleri ve özellikleri içerir.  
  
- `allDone`Özelliği, <xref:System.Threading.ManualResetEvent> isteğin tamamlanmasına işaret eden sınıfının bir örneğini içerir.  
  
- `Main()`Yöntemi komut satırını okur ve belirtilen Internet kaynağı için isteği başlatır. **Web isteğini** `wreq` ve **RequestState** `rs` ' i oluşturur, Isteği Işlemeye başlamak için **BeginGetResponse** çağırır ve `allDone.WaitOne()` geri çağırma tamamlanana kadar uygulamanın çıkmaması için yöntemini çağırır. Yanıt Internet kaynağından okunduktan sonra `Main()` konsola yazar ve uygulama sonlanır.  
  
- `showusage()`Yöntemi konsola bir örnek komut satırı yazar. `Main()`Komut satırında HIÇBIR URI sağlanmamışsa çağrılır.  
  
- `RespCallBack()`Yöntemi, Internet isteği için zaman uyumsuz geri çağırma yöntemi uygular. Internet kaynağından gelen yanıtı içeren **WebResponse** örneğini oluşturur, yanıt akışını alır ve akıştan zaman uyumsuz olarak veri okumaya başlar.  
  
- `ReadCallBack()`Yöntemi, yanıt akışını okumak için zaman uyumsuz geri çağırma yöntemini uygular. Internet kaynağından alınan verileri **RequestState** örneğinin **ResponseData** özelliğine aktarır, daha sonra daha fazla veri döndürülünceye kadar yanıt akışının başka bir zaman uyumsuz okumasını başlatır. Tüm veriler okunduktan sonra, `ReadCallBack()` Yanıt akışını kapatır ve `allDone.Set()` yanıtın tamamının **ResponseData** içinde mevcut olduğunu göstermek için yöntemini çağırır.  
  
    > [!NOTE]
    > Tüm ağ akışlarının kapalı olması önemlidir. Her bir istek ve yanıt akışını kapatmdıysanız, uygulamanız sunucuya bağlantılar dışında çalışır ve ek istekleri işleyemez.  
  
```csharp  
using System;  
using System.Net;  
using System.Threading;  
using System.Text;  
using System.IO;  
  
// The RequestState class passes data across async calls.  
public class RequestState  
{  
   const int BufferSize = 1024;  
   public StringBuilder RequestData;  
   public byte[] BufferRead;  
   public WebRequest Request;  
   public Stream ResponseStream;  
   // Create Decoder for appropriate enconding type.  
   public Decoder StreamDecode = Encoding.UTF8.GetDecoder();  
  
   public RequestState()  
   {  
      BufferRead = new byte[BufferSize];  
      RequestData = new StringBuilder(String.Empty);  
      Request = null;  
      ResponseStream = null;  
   }
}  
  
// ClientGetAsync issues the async request.  
class ClientGetAsync
{  
   public static ManualResetEvent allDone = new ManualResetEvent(false);  
   const int BUFFER_SIZE = 1024;  
  
   public static void Main(string[] args)
   {  
      if (args.Length < 1)
      {  
         showusage();  
         return;  
      }  
  
      // Get the URI from the command line.  
      Uri httpSite = new Uri(args[0]);  
  
      // Create the request object.  
      WebRequest wreq = WebRequest.Create(httpSite);  
  
      // Create the state object.  
      RequestState rs = new RequestState();  
  
      // Put the request into the state object so it can be passed around.  
      rs.Request = wreq;  
  
      // Issue the async request.  
      IAsyncResult r = (IAsyncResult) wreq.BeginGetResponse(  
         new AsyncCallback(RespCallback), rs);  
  
      // Wait until the ManualResetEvent is set so that the application
      // does not exit until after the callback is called.  
      allDone.WaitOne();  
  
      Console.WriteLine(rs.RequestData.ToString());  
   }  
  
   public static void showusage() {  
      Console.WriteLine("Attempts to GET a URL");  
      Console.WriteLine("\r\nUsage:");  
      Console.WriteLine("   ClientGetAsync URL");  
      Console.WriteLine("   Example:");  
      Console.WriteLine("      ClientGetAsync http://www.contoso.com/");  
   }  
  
   private static void RespCallback(IAsyncResult ar)  
   {  
      // Get the RequestState object from the async result.  
      RequestState rs = (RequestState) ar.AsyncState;  
  
      // Get the WebRequest from RequestState.  
      WebRequest req = rs.Request;  
  
      // Call EndGetResponse, which produces the WebResponse object  
      //  that came from the request issued above.  
      WebResponse resp = req.EndGetResponse(ar);
  
      //  Start reading data from the response stream.  
      Stream ResponseStream = resp.GetResponseStream();  
  
      // Store the response stream in RequestState to read
      // the stream asynchronously.  
      rs.ResponseStream = ResponseStream;  
  
      //  Pass rs.BufferRead to BeginRead. Read data into rs.BufferRead  
      IAsyncResult iarRead = ResponseStream.BeginRead(rs.BufferRead, 0,
         BUFFER_SIZE, new AsyncCallback(ReadCallBack), rs);
   }  
  
   private static void ReadCallBack(IAsyncResult asyncResult)  
   {  
      // Get the RequestState object from AsyncResult.  
      RequestState rs = (RequestState)asyncResult.AsyncState;  
  
      // Retrieve the ResponseStream that was set in RespCallback.
      Stream responseStream = rs.ResponseStream;  
  
      // Read rs.BufferRead to verify that it contains data.
      int read = responseStream.EndRead( asyncResult );  
      if (read > 0)  
      {  
         // Prepare a Char array buffer for converting to Unicode.  
         Char[] charBuffer = new Char[BUFFER_SIZE];  
  
         // Convert byte stream to Char array and then to String.  
         // len contains the number of characters converted to Unicode.  
      int len =
         rs.StreamDecode.GetChars(rs.BufferRead, 0, read, charBuffer, 0);  
  
         String str = new String(charBuffer, 0, len);  
  
         // Append the recently read data to the RequestData stringbuilder  
         // object contained in RequestState.  
         rs.RequestData.Append(  
            Encoding.ASCII.GetString(rs.BufferRead, 0, read));
  
         // Continue reading data until
         // responseStream.EndRead returns –1.  
         IAsyncResult ar = responseStream.BeginRead(
            rs.BufferRead, 0, BUFFER_SIZE,
            new AsyncCallback(ReadCallBack), rs);  
      }  
      else  
      {  
         if(rs.RequestData.Length>0)  
         {  
            //  Display data to the console.  
            string strContent;
            strContent = rs.RequestData.ToString();  
         }  
         // Close down the response stream.  
         responseStream.Close();
         // Set the ManualResetEvent so the main thread can exit.  
         allDone.Set();
      }  
      return;  
   }
}  
```  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Threading  
Imports System.Text  
Imports System.IO  
  
' The RequestState class passes data across async calls.  
Public Class RequestState  
  
      Public RequestData As New StringBuilder("")  
      Public BufferRead(1024) As Byte  
      Public Request As HttpWebRequest  
      Public ResponseStream As Stream  
      ' Create Decoder for appropriate encoding type.  
      Public StreamDecode As Decoder = Encoding.UTF8.GetDecoder()  
  
      Public Sub New  
         Request = Nothing  
         ResponseStream = Nothing  
      End Sub  
End Class  
  
' ClientGetAsync issues the async request.  
Class ClientGetAsync  
   Shared allDone As New ManualResetEvent(False)  
      Const BUFFER_SIZE As Integer = 1024  
  
    Shared Sub Main()  
        Dim Args As String() = Environment.GetCommandLineArgs()  
  
        If Args.Length < 2 Then  
            ShowUsage()  
            Return  
        End If  
  
      ' Get the URI from the command line.  
        Dim HttpSite As Uri = New Uri(Args(1))  
  
      ' Create the request object.  
        Dim wreq As HttpWebRequest = _  
           CType(WebRequest.Create(HttpSite), HttpWebRequest)  
  
      ' Create the state object.  
      Dim rs As RequestState = New RequestState()  
  
      ' Put the request into the state so it can be passed around.  
      rs.Request = wreq  
  
      ' Issue the async request.  
        Dim r As IAsyncResult = _  
           CType(wreq.BeginGetResponse( _  
           New AsyncCallback(AddressOf RespCallback), rs), IAsyncResult)  
  
      ' Wait until the ManualResetEvent is set so that the application  
      ' does not exit until after the callback is called.  
        allDone.WaitOne()  
    End Sub  
  
    Shared Sub ShowUsage()  
        Console.WriteLine("Attempts to GET a URI")  
        Console.WriteLine()  
        Console.WriteLine("Usage:")  
        Console.WriteLine("ClientGetAsync URI")  
        Console.WriteLine("Examples:")  
        Console.WriteLine("ClientGetAsync http://www.contoso.com/")  
    End Sub  
  
    Shared Sub RespCallback(ar As IAsyncResult)  
       ' Get the RequestState object from the async result.  
       Dim rs As RequestState = CType(ar.AsyncState, RequestState)  
  
       ' Get the HttpWebRequest from RequestState.  
       Dim req As HttpWebRequest= rs.Request  
  
       ' Call EndGetResponse, which returns the HttpWebResponse object  
       ' that came from the request issued above.  
       Dim resp As HttpWebResponse = _  
           CType(req.EndGetResponse(ar), HttpWebResponse)  
  
       ' Start reading data from the response stream.  
       Dim ResponseStream As Stream = resp.GetResponseStream()  
  
       ' Store the reponse stream in RequestState to read  
       ' the stream asynchronously.  
       rs.ResponseStream = ResponseStream  
  
       ' Pass rs.BufferRead to BeginRead. Read data into rs.BufferRead.  
       Dim iarRead As IAsyncResult = _  
          ResponseStream.BeginRead(rs.BufferRead, 0, BUFFER_SIZE, _  
          New AsyncCallback(AddressOf ReadCallBack), rs)  
    End Sub  
  
   Shared Sub ReadCallBack(asyncResult As IAsyncResult)  
      ' Get the RequestState object from the AsyncResult.  
      Dim rs As RequestState = CType(asyncResult.AsyncState, RequestState)  
  
      ' Retrieve the ResponseStream that was set in RespCallback.  
      Dim responseStream As Stream = rs.ResponseStream  
  
      ' Read rs.BufferRead to verify that it contains data.  
      Dim read As Integer = responseStream.EndRead( asyncResult )  
      If read > 0 Then  
         ' Prepare a Char array buffer for converting to Unicode.  
         Dim charBuffer(1024) As Char  
  
         ' Convert byte stream to Char array and then String.  
         ' len contains the number of characters converted to Unicode.  
         Dim len As Integer = _  
           rs.StreamDecode.GetChars(rs.BufferRead, 0, read, charBuffer, 0)  
         Dim str As String = new String(charBuffer, 0, len)
  
         ' Append the recently read data to the RequestData stringbuilder
         ' object contained in RequestState.  
         rs.RequestData.Append( _  
            Encoding.ASCII.GetString(rs.BufferRead, 0, read))  
  
         ' Continue reading data until responseStream.EndRead  
         ' returns –1.  
         Dim ar As IAsyncResult = _  
            responseStream.BeginRead(rs.BufferRead, 0, BUFFER_SIZE, _  
            New AsyncCallback(AddressOf ReadCallBack), rs)  
      Else  
          If rs.RequestData.Length > 1 Then  
            ' Display data to the console.  
            Dim strContent As String  
            strContent = rs.RequestData.ToString()  
            Console.WriteLine(strContent)  
         End If  
  
         ' Close down the response stream.  
         responseStream.Close()  
  
         ' Set the ManualResetEvent so the main thread can exit.  
         allDone.Set()  
      End If  
  
      Return  
   End Sub  
End Class  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri İsteme](requesting-data.md)
