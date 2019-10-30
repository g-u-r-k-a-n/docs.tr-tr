---
title: TCP Hizmetleri Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- requesting data from Internet, TCP
- receiving data, TCP
- TcpClient class, about TcpClient class
- data requests, TCP
- application protocols, TCP
- network resources, TCP
- sending data, TCP
- TCP
- protocols, TCP
- Internet, TCP
ms.assetid: d2811830-3bcb-495c-b82d-cda9cf919aad
ms.openlocfilehash: 3678586647dcf9c47b4494197fbf56cab865b3d3
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039485"
---
# <a name="using-tcp-services"></a><span data-ttu-id="f3752-102">TCP Hizmetleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="f3752-102">Using TCP Services</span></span>

<span data-ttu-id="f3752-103"><xref:System.Net.Sockets.TcpClient> sınıfı, TCP kullanarak bir Internet kaynağından veri ister.</span><span class="sxs-lookup"><span data-stu-id="f3752-103">The <xref:System.Net.Sockets.TcpClient> class requests data from an Internet resource using TCP.</span></span> <span data-ttu-id="f3752-104">**TcpClient** yöntemleri ve ÖZELLIKLERI, TCP kullanarak veri istemek ve almak için <xref:System.Net.Sockets.Socket> oluşturma ayrıntılarını soyutlar.</span><span class="sxs-lookup"><span data-stu-id="f3752-104">The methods and properties of **TcpClient** abstract the details for creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using TCP.</span></span> <span data-ttu-id="f3752-105">Uzak cihazla bağlantı bir akış olarak temsil ettiğinden, veriler .NET Framework akış işleme teknikleriyle okunabilir ve yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="f3752-105">Because the connection to the remote device is represented as a stream, data can be read and written with .NET Framework stream-handling techniques.</span></span>

<span data-ttu-id="f3752-106">TCP protokolü, uzak bir uç nokta ile bağlantı kurar ve ardından bu bağlantıyı veri paketleri göndermek ve almak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="f3752-106">The TCP protocol establishes a connection with a remote endpoint and then uses that connection to send and receive data packets.</span></span> <span data-ttu-id="f3752-107">TCP, veri paketlerinin uç noktaya gönderilmesini ve ulaştığında doğru sırada derlenmesinden emin olmanın sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="f3752-107">TCP is responsible for ensuring that data packets are sent to the endpoint and assembled in the correct order when they arrive.</span></span>

<span data-ttu-id="f3752-108">TCP bağlantısı kurmak için, ihtiyacınız olan hizmeti barındıran ağ cihazının adresini bilmeniz ve hizmetin iletişim kurmak için kullandığı TCP bağlantı noktasını bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3752-108">To establish a TCP connection, you must know the address of the network device hosting the service you need and you must know the TCP port that the service uses to communicate.</span></span> <span data-ttu-id="f3752-109">Internet atanmış numaralar yetkilisi (IANA), ortak hizmetler için bağlantı noktası numaralarını tanımlar (bkz. [hizmet adı ve Aktarım Protokolü bağlantı noktası numarası kayıt defteri](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span><span class="sxs-lookup"><span data-stu-id="f3752-109">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="f3752-110">IANA listesinde bulunmayan hizmetler 1.024-65.535 aralığında bağlantı noktası numaralarına sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="f3752-110">Services not on the Iana list can have port numbers in the range 1,024 to 65,535.</span></span>

<span data-ttu-id="f3752-111">Aşağıdaki örnek, TCP bağlantı noktası 13 ' te bir zaman sunucusuna bağlanmak için bir **TcpClient** ayarlamayı göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="f3752-111">The following example demonstrates setting up a **TcpClient** to connect to a time server on TCP port 13:</span></span>

```vb
Imports System.Net.Sockets
Imports System.Text

Public Class TcpTimeClient
    Private const portNum As Integer = 13
    Private const hostName As String = "host.contoso.com"

    ' Entry point  that delegates to C-style main Private Function.
    Public Overloads Shared Sub Main()
        System.Environment.ExitCode = _
            Main(System.Environment.GetCommandLineArgs())
    End Sub

    Overloads Public Shared Function Main(args As String()) As Integer
        Try
            Dim client As New TcpClient(hostName, portNum)

            Dim ns As NetworkStream = client.GetStream()

            Dim bytes(1024) As Byte
            Dim bytesRead As Integer = ns.Read(bytes, 0, bytes.Length)

            Console.WriteLine(Encoding.ASCII.GetString(bytes, 0, bytesRead))

        Catch e As Exception
            Console.WriteLine(e.ToString())
        End Try

        client.Close()

        Return 0
    End Function
End Class
```

```csharp
using System;
using System.Net.Sockets;
using System.Text;

public class TcpTimeClient
{
    private const int portNum = 13;
    private const string hostName = "host.contoso.com";

    public static int Main(String[] args)
    {
        try
        {
            var client = new TcpClient(hostName, portNum);

            NetworkStream ns = client.GetStream();

            byte[] bytes = new byte[1024];
            int bytesRead = ns.Read(bytes, 0, bytes.Length);

            Console.WriteLine(Encoding.ASCII.GetString(bytes,0,bytesRead));

            client.Close();

        }
        catch (Exception e)
        {
            Console.WriteLine(e.ToString());
        }

        return 0;
    }
}
```

<span data-ttu-id="f3752-112"><xref:System.Net.Sockets.TcpListener>, gelen istekler için bir TCP bağlantı noktasını izlemek ve ardından istemciyle bağlantıyı yöneten bir **yuva** ya da **TcpClient** oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f3752-112"><xref:System.Net.Sockets.TcpListener> is used to monitor a TCP port for incoming requests and then create either a **Socket** or a **TcpClient** that manages the connection to the client.</span></span> <span data-ttu-id="f3752-113"><xref:System.Net.Sockets.TcpListener.Start%2A> yöntemi dinlemeyi etkinleştirilir ve <xref:System.Net.Sockets.TcpListener.Stop%2A> yöntemi bağlantı noktasında dinlemeyi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="f3752-113">The <xref:System.Net.Sockets.TcpListener.Start%2A> method enables listening, and the <xref:System.Net.Sockets.TcpListener.Stop%2A> method disables listening on the port.</span></span> <span data-ttu-id="f3752-114"><xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> yöntemi gelen bağlantı isteklerini kabul eder ve isteği işlemek için bir **TcpClient** oluşturur ve <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> yöntemi gelen bağlantı isteklerini kabul eder ve isteği işlemek Için bir **yuva** oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f3752-114">The <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> method accepts incoming connection requests and creates a **TcpClient** to handle the request, and the <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> method accepts incoming connection requests and creates a **Socket** to handle the request.</span></span>

<span data-ttu-id="f3752-115">Aşağıdaki örnek, TCP bağlantı noktası 13 ' ü izlemek için bir **TcpListener** kullanarak bir ağ zaman sunucusu oluşturmayı göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="f3752-115">The following example demonstrates creating a network time server using a **TcpListener** to monitor TCP port 13.</span></span> <span data-ttu-id="f3752-116">Gelen bir bağlantı isteği kabul edildiğinde, sunucu, ana bilgisayar sunucusundan geçerli tarih ve saat ile yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="f3752-116">When an incoming connection request is accepted, the time server responds with the current date and time from the host server.</span></span>

```vb
Imports System.Net
Imports System.Net.Sockets
Imports System.Text

Public Class TcpTimeServer

    Private const portNum As Integer = 13

    ' Entry point that delegates to C-style main Private Function.
    Public Overloads Shared Sub Main()
        System.Environment.ExitCode = _
            Main(System.Environment.GetCommandLineArgs())
    End Sub

    Overloads Public Shared Function Main(args As String()) As Integer
        Dim done As Boolean = False

        Dim listener As New TcpListener(IPAddress.Any, portNum)

        listener.Start()

        While Not done
            Console.Write("Waiting for connection...")
            Dim client As TcpClient = listener.AcceptTcpClient()

            Console.WriteLine("Connection accepted.")
            Dim ns As NetworkStream = client.GetStream()

            Dim byteTime As Byte() = _
                Encoding.ASCII.GetBytes(DateTime.Now.ToString())

            Try
                ns.Write(byteTime, 0, byteTime.Length)
                ns.Close()
                client.Close()
            Catch e As Exception
                Console.WriteLine(e.ToString())
            End Try
        End While

        listener.Stop()

        Return 0
    End Function
End Class
```

```csharp
using System;
using System.Net;
using System.Net.Sockets;
using System.Text;

public class TcpTimeServer
{

    private const int portNum = 13;

    public static int Main(String[] args)
    {
        bool done = false;

        var listener = new TcpListener(IPAddress.Any, portNum);

        listener.Start();

        while (!done)
        {
            Console.Write("Waiting for connection...");
            TcpClient client = listener.AcceptTcpClient();

            Console.WriteLine("Connection accepted.");
            NetworkStream ns = client.GetStream();

            byte[] byteTime = Encoding.ASCII.GetBytes(DateTime.Now.ToString());

            try
            {
                ns.Write(byteTime, 0, byteTime.Length);
                ns.Close();
                client.Close();
            }
            catch (Exception e)
            {
                Console.WriteLine(e.ToString());
            }
        }

        listener.Stop();

        return 0;
    }

}
```
