---
title: Zaman Uyumsuz İstemci Yuvası Kullanma
description: Bu örnek, zaman uyumsuz bir istemci yuvasını gösterir. .NET Framework zaman uyumsuz programlama, bir bağlantıyı işlerken uygulamanın çalışmaya devam etmesine olanak tanır.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- asynchronous client sockets
- Socket class, asynchronous client sockets
- requesting data from Internet, sockets
- sockets, asynchronous client sockets
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- client sockets
ms.assetid: fd85bc88-e06c-467d-a30d-9fd7cffcfca1
ms.openlocfilehash: af5379533e51e7488d673359dc24268c6329c082
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265225"
---
# <a name="using-an-asynchronous-client-socket"></a>Zaman Uyumsuz İstemci Yuvası Kullanma

Zaman uyumsuz bir istemci yuvası, ağ işlemlerinin tamamlanmasını beklerken uygulamayı askıya almaz. Bunun yerine, uygulama orijinal iş parçacığında çalışmaya devam ederken bir iş parçacığında ağ bağlantısını işlemek için standart .NET Framework zaman uyumsuz programlama modelini kullanır. Zaman uyumsuz yuvalar, ağı yoğun şekilde kullanan veya devam etmeden önce ağ işlemlerinin tamamlanmasını bekleyemez uygulamalar için uygundur.  
  
 <xref:System.Net.Sockets.Socket>Sınıfı, zaman uyumsuz metotlar için .NET Framework adlandırma düzeniyle uyar; Örneğin, zaman uyumlu <xref:System.Net.Sockets.Socket.Receive%2A> Yöntem zaman uyumsuz <xref:System.Net.Sockets.Socket.BeginReceive%2A> ve yöntemlere karşılık gelir <xref:System.Net.Sockets.Socket.EndReceive%2A> .  
  
 Zaman uyumsuz işlemler işlemin sonucunu döndürmek için bir geri çağırma yöntemi gerektirir. Uygulamanızın sonucu bilmeleri gerekmiyorsa, geri arama yöntemi gerekli değildir. Bu bölümdeki örnek kod, bir ağ cihazına bağlanmaya başlamak için bir yöntem ve bağlantıyı tamamlamaya yönelik bir geri çağırma yöntemi, gönderimi tamamlamaya yönelik bir yöntem ve gönderme yöntemi ile verileri almaya başlamak için bir yöntem ve geri çağırma yöntemi kullanmayı göstermektedir.  
  
 Zaman uyumsuz yuvalar, ağ bağlantılarını işlemek için sistem iş parçacığı havuzundan birden çok iş parçacığı kullanır. Bir iş parçacığı, verilerin gönderilmesini veya alınmasını başlatmaktan sorumludur; diğer iş parçacıkları ağ cihazına bağlantıyı tamamlar ve verileri gönderir veya alır. Aşağıdaki örneklerde, sınıfının örnekleri, <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> yürütme devam edebilme durumunda ana iş parçacığı ve sinyalin yürütülmesini askıya almak için kullanılır.  
  
 Aşağıdaki örnekte, bir ağ cihazına zaman uyumsuz bir yuva bağlamak için `Connect` yöntemi bir **yuva** başlatır ve sonra, <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> ağ cihazını temsil eden bir uzak uç nokta, Connect callback yöntemi ve zaman uyumsuz çağrılar arasında durum bilgilerini geçirmek için kullanılan bir durum nesnesi (istemci **yuvası**) geçirerek yöntemi çağırır. Örnek, `Connect` belirtilen **yuvayı** belirtilen uç noktaya bağlamak için yöntemini uygular. Adında genel bir **ManualResetEvent** olduğunu varsayar `connectDone` .  
  
```vb  
Public Shared Sub Connect(remoteEP As EndPoint, client As Socket)  
    client.BeginConnect(remoteEP, _  
       AddressOf ConnectCallback, client)  
  
    connectDone.WaitOne()  
End Sub 'Connect  
```  
  
```csharp  
public static void Connect(EndPoint remoteEP, Socket client) {  
    client.BeginConnect(remoteEP,
        new AsyncCallback(ConnectCallback), client );  
  
   connectDone.WaitOne();  
}  
```  
  
 Connect callback yöntemi `ConnectCallback` <xref:System.AsyncCallback> temsilciyi uygular. Uzak cihaz kullanılabilir olduğunda uzak cihaza bağlanır ve ardından **ManualResetEvent** ayarlanarak bağlantının tamamlandığını uygulamanın iş parçacığına bildirir `connectDone` . Aşağıdaki kod `ConnectCallback` yöntemini uygular.  
  
```vb  
Private Shared Sub ConnectCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the socket from the state object.  
        Dim client As Socket = CType(ar.AsyncState, Socket)  
  
        ' Complete the connection.  
        client.EndConnect(ar)  
  
        Console.WriteLine("Socket connected to {0}", _  
            client.RemoteEndPoint.ToString())  
  
        ' Signal that the connection has been made.  
        connectDone.Set()  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'ConnectCallback  
```  
  
```csharp  
private static void ConnectCallback(IAsyncResult ar) {  
    try {  
        // Retrieve the socket from the state object.  
        Socket client = (Socket) ar.AsyncState;  
  
        // Complete the connection.  
        client.EndConnect(ar);  
  
        Console.WriteLine("Socket connected to {0}",  
            client.RemoteEndPoint.ToString());  
  
        // Signal that the connection has been made.  
        connectDone.Set();  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 Örnek yöntem, `Send` ASCII biçiminde belirtilen dize verilerini kodlar ve belirtilen yuva tarafından temsil edilen ağ cihazına zaman uyumsuz olarak gönderir. Aşağıdaki örnek `Send` yöntemini uygular.  
  
```vb  
Private Shared Sub Send(client As Socket, data As [String])  
    ' Convert the string data to byte data using ASCII encoding.  
    Dim byteData As Byte() = Encoding.ASCII.GetBytes(data)  
  
    ' Begin sending the data to the remote device.  
    client.BeginSend(byteData, 0, byteData.Length, SocketFlags.None, _  
        AddressOf SendCallback, client)  
End Sub 'Send  
```  
  
```csharp  
private static void Send(Socket client, String data) {  
    // Convert the string data to byte data using ASCII encoding.  
    byte[] byteData = Encoding.ASCII.GetBytes(data);  
  
    // Begin sending the data to the remote device.  
    client.BeginSend(byteData, 0, byteData.Length, SocketFlags.None,  
        new AsyncCallback(SendCallback), client);  
}  
```  
  
 Geri arama gönder yöntemi `SendCallback` temsilciyi uygular <xref:System.AsyncCallback> . Ağ aygıtı almaya hazırsa verileri gönderir. Aşağıdaki örnek yönteminin uygulamasını gösterir `SendCallback` . Adında genel bir **ManualResetEvent** olduğunu varsayar `sendDone` .  
  
```vb  
Private Shared Sub SendCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the socket from the state object.  
        Dim client As Socket = CType(ar.AsyncState, Socket)  
  
        ' Complete sending the data to the remote device.  
        Dim bytesSent As Integer = client.EndSend(ar)  
        Console.WriteLine("Sent {0} bytes to server.", bytesSent)  
  
        ' Signal that all bytes have been sent.  
        sendDone.Set()  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'SendCallback  
```  
  
```csharp  
private static void SendCallback(IAsyncResult ar) {  
    try {  
        // Retrieve the socket from the state object.  
        Socket client = (Socket) ar.AsyncState;  
  
        // Complete sending the data to the remote device.  
        int bytesSent = client.EndSend(ar);  
        Console.WriteLine("Sent {0} bytes to server.", bytesSent);  
  
        // Signal that all bytes have been sent.  
        sendDone.Set();  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 İstemci yuvalarından veri okuma, zaman uyumsuz çağrılar arasında değer geçiren bir durum nesnesi gerektirir. Aşağıdaki sınıf, bir istemci yuvasından veri almak için örnek bir durum nesnesidir. İstemci yuvası için bir alan, alınan veriler için bir arabellek ve <xref:System.Text.StringBuilder> gelen veri dizesini tutacak bir alanı içerir. Bu alanların durum nesnesine yerleştirilmesi, değerlerinin istemci yuvasında verileri okumak için birden çok çağrıda saklanması sağlar.  
  
```vb  
Public Class StateObject  
    ' Client socket.  
    Public workSocket As Socket = Nothing
    ' Size of receive buffer.  
    Public BufferSize As Integer = 256  
    ' Receive buffer.  
    Public buffer(256) As Byte
    ' Received data string.  
    Public sb As New StringBuilder()  
End Class 'StateObject  
```  
  
```csharp  
public class StateObject {  
    // Client socket.  
    public Socket workSocket = null;  
    // Size of receive buffer.  
    public const int BufferSize = 256;  
    // Receive buffer.  
    public byte[] buffer = new byte[BufferSize];  
    // Received data string.  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 Örnek `Receive` Yöntem, durum nesnesini ayarlar ve ardından, istemci yuvasından zaman uyumsuz olarak veri okumak Için **BeginReceive** yöntemini çağırır. Aşağıdaki örnek `Receive` yöntemini uygular.  
  
```vb  
Private Shared Sub Receive(client As Socket)  
    Try  
        ' Create the state object.  
        Dim state As New StateObject()  
        state.workSocket = client  
  
        ' Begin receiving the data from the remote device.  
        client.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf ReceiveCallback, state)  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'Receive  
```  
  
```csharp  
private static void Receive(Socket client) {  
    try {  
        // Create the state object.  
        StateObject state = new StateObject();  
        state.workSocket = client;  
  
        // Begin receiving the data from the remote device.  
        client.BeginReceive( state.buffer, 0, StateObject.BufferSize, 0,  
            new AsyncCallback(ReceiveCallback), state);  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 Alma geri çağırma yöntemi `ReceiveCallback` , **AsyncCallback** temsilcisini uygular. Ağ cihazından verileri alır ve bir ileti dizesi oluşturur. Ağ üzerinden veri arabelleğine bir veya daha fazla bayt okur ve ardından istemci tarafından gönderilen veriler tamamlanana kadar **BeginReceive** metodunu yeniden çağırır. Tüm veriler istemciden okunduktan sonra, `ReceiveCallback` **ManualResetEvent** ayarlanarak, verilerin tamamlandığını uygulamanın iş parçacığına bildirir `sendDone` .  
  
 Aşağıdaki örnek kod `ReceiveCallback` yöntemi uygular. `response`Alınan dizeyi ve genel **ManualResetEvent** 'i tutan adlı bir genel dizeyi kabul eder `receiveDone` . Ağ oturumunu sonlandırmak için sunucu istemci yuvasını sorunsuz bir şekilde kapatması gerekir.  
  
```vb  
Private Shared Sub ReceiveCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the state object and the client socket
        ' from the asynchronous state object.  
        Dim state As StateObject = CType(ar.AsyncState, StateObject)  
        Dim client As Socket = state.workSocket  
  
        ' Read data from the remote device.  
        Dim bytesRead As Integer = client.EndReceive(ar)  
  
        If bytesRead > 0 Then  
            ' There might be more data, so store the data received so far.  
            state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, _  
                bytesRead))  
  
            '  Get the rest of the data.  
            client.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
                AddressOf ReceiveCallback, state)  
        Else  
            ' All the data has arrived; put it in response.  
            If state.sb.Length > 1 Then  
                response = state.sb.ToString()  
            End If  
            ' Signal that all bytes have been received.  
            receiveDone.Set()  
        End If  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'ReceiveCallback  
```  
  
```csharp  
private static void ReceiveCallback( IAsyncResult ar ) {  
    try {  
        // Retrieve the state object and the client socket
        // from the asynchronous state object.  
        StateObject state = (StateObject) ar.AsyncState;  
        Socket client = state.workSocket;  
        // Read data from the remote device.  
        int bytesRead = client.EndReceive(ar);  
        if (bytesRead > 0) {  
            // There might be more data, so store the data received so far.  
            state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,bytesRead));  
                //  Get the rest of the data.  
            client.BeginReceive(state.buffer,0,StateObject.BufferSize,0,  
                new AsyncCallback(ReceiveCallback), state);  
        } else {  
            // All the data has arrived; put it in response.  
            if (state.sb.Length > 1) {  
                response = state.sb.ToString();  
            }  
            // Signal that all bytes have been received.  
            receiveDone.Set();  
        }  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Zaman Uyumlu İstemci Yuvası Kullanma](using-a-synchronous-client-socket.md)
- [Yuvalarla Dinleme](listening-with-sockets.md)
- [Zaman Uyumsuz İstemci Yuvası Örneği](asynchronous-client-socket-example.md)
