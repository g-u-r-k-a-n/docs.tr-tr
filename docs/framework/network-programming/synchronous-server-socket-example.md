---
title: Zaman Uyumlu Sunucu Yuvası Örneği
description: Bu örnek .NET Framework program, zaman uyumlu bir yuva kullanarak istemcilerden bağlantı alan bir sunucu oluşturur. Bir dizeyi alır ve yankılar.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronous server sockets
- sockets, code examples
- sockets, synchronous server sockets
ms.assetid: 5916c764-879f-4716-99fb-1d21c6237f1c
ms.openlocfilehash: 49646a71c979eda04f8bf932a3dbfac11677a8e0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239529"
---
# <a name="synchronous-server-socket-example"></a>Zaman Uyumlu Sunucu Yuvası Örneği

Aşağıdaki örnek program istemcilerden gelen bağlantı isteklerini alan bir sunucu oluşturur. Sunucu, zaman uyumlu bir yuva ile oluşturulmuştur, bu nedenle sunucu uygulamasının yürütülmesi istemciden bir bağlantı beklerken askıya alınır. Uygulama istemciden bir dize alır, bu dizeyi konsolda görüntüler ve ardından dizeyi istemciye geri yankılar. İstemciden alınan dize, \<EOF> iletinin sonuna işaret etmek için "" dizesini içermelidir.  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Sockets  
Imports System.Text  
Imports Microsoft.VisualBasic  
  
Public Class SynchronousSocketListener  
  
    ' Incoming data from the client.  
    Public Shared data As String = Nothing  
  
    Public Shared Sub Main()  
        ' Data buffer for incoming data.  
        Dim bytes() As Byte = New [Byte](1024) {}  
  
        ' Establish the local endpoint for the socket.  
        ' Dns.GetHostName returns the name of the
        ' host running the application.  
        Dim ipHostInfo As IPHostEntry = Dns.GetHostEntry(Dns.GetHostName())  
        Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
        Dim localEndPoint As New IPEndPoint(ipAddress, 11000)  
  
        ' Create a TCP/IP socket.  
        Dim listener As New Socket(ipAddress.AddressFamily, _  
            SocketType.Stream, ProtocolType.Tcp)  
  
        ' Bind the socket to the local endpoint and
        ' listen for incoming connections.  
  
        listener.Bind(localEndPoint)  
        listener.Listen(10)  
  
        ' Start listening for connections.  
        While True  
            Console.WriteLine("Waiting for a connection...")  
            ' Program is suspended while waiting for an incoming connection.  
            Dim handler As Socket = listener.Accept()  
            data = Nothing  
  
            ' An incoming connection needs to be processed.  
            While True  
                Dim bytesRec As Integer = handler.Receive(bytes)  
                data += Encoding.ASCII.GetString(bytes, 0, bytesRec)  
                If data.IndexOf("<EOF>") > -1 Then  
                    Exit While  
                End If  
            End While  
            ' Show the data on the console.  
            Console.WriteLine("Text received : {0}", data)  
            ' Echo the data back to the client.  
            Dim msg As Byte() = Encoding.ASCII.GetBytes(data)  
            handler.Send(msg)  
            handler.Shutdown(SocketShutdown.Both)  
            handler.Close()  
        End While  
    End Sub  
  
End Class 'SynchronousSocketListener  
```  
  
```csharp  
using System;  
using System.Net;  
using System.Net.Sockets;  
using System.Text;  
  
public class SynchronousSocketListener {  
  
    // Incoming data from the client.  
    public static string data = null;  
  
    public static void StartListening() {  
        // Data buffer for incoming data.  
        byte[] bytes = new Byte[1024];  
  
        // Establish the local endpoint for the socket.  
        // Dns.GetHostName returns the name of the
        // host running the application.  
        IPHostEntry ipHostInfo = Dns.GetHostEntry(Dns.GetHostName());  
        IPAddress ipAddress = ipHostInfo.AddressList[0];  
        IPEndPoint localEndPoint = new IPEndPoint(ipAddress, 11000);  
  
        // Create a TCP/IP socket.  
        Socket listener = new Socket(ipAddress.AddressFamily,  
            SocketType.Stream, ProtocolType.Tcp );  
  
        // Bind the socket to the local endpoint and
        // listen for incoming connections.  
        try {  
            listener.Bind(localEndPoint);  
            listener.Listen(10);  
  
            // Start listening for connections.  
            while (true) {  
                Console.WriteLine("Waiting for a connection...");  
                // Program is suspended while waiting for an incoming connection.  
                Socket handler = listener.Accept();  
                data = null;  
  
                // An incoming connection needs to be processed.  
                while (true) {  
                    int bytesRec = handler.Receive(bytes);  
                    data += Encoding.ASCII.GetString(bytes,0,bytesRec);  
                    if (data.IndexOf("<EOF>") > -1) {  
                        break;  
                    }  
                }  
  
                // Show the data on the console.  
                Console.WriteLine( "Text received : {0}", data);  
  
                // Echo the data back to the client.  
                byte[] msg = Encoding.ASCII.GetBytes(data);  
  
                handler.Send(msg);  
                handler.Shutdown(SocketShutdown.Both);  
                handler.Close();  
            }  
  
        } catch (Exception e) {  
            Console.WriteLine(e.ToString());  
        }  
  
        Console.WriteLine("\nPress ENTER to continue...");  
        Console.Read();  
  
    }  
  
    public static int Main(String[] args) {  
        StartListening();  
        return 0;  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Zaman Uyumlu İstemci Yuvası Örneği](synchronous-client-socket-example.md)
- [Zaman Uyumlu Sunucu Yuvası Kullanma](using-a-synchronous-server-socket.md)
- [Yuva Kod Örnekleri](socket-code-examples.md)
