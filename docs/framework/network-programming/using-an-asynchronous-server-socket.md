---
title: Zaman Uyumsuz Sunucu Yuvası Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- Socket class, asynchronous server sockets
- data requests, sockets
- sockets, asynchronous server sockets
- requesting data from Internet, sockets
- server sockets
- receiving data, sockets
- asynchronous server sockets
- protocols, sockets
- Internet, sockets
ms.assetid: 813489a9-3efd-41b6-a33f-371d55397676
ms.openlocfilehash: 467804e685d800643c421ed1aad040a842b42886
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180628"
---
# <a name="using-an-asynchronous-server-socket"></a><span data-ttu-id="424cb-102">Zaman Uyumsuz Sunucu Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="424cb-102">Using an Asynchronous Server Socket</span></span>
<span data-ttu-id="424cb-103">Asynchronous sunucu soketleri ağ hizmeti isteklerini işlemek için .NET Framework asynchronous programlama modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="424cb-103">Asynchronous server sockets use the .NET Framework asynchronous programming model to process network service requests.</span></span> <span data-ttu-id="424cb-104">Sınıf <xref:System.Net.Sockets.Socket> standart .NET Framework asynchronous adlandırma deseni izler; örneğin, senkron <xref:System.Net.Sockets.Socket.Accept%2A> yöntem asynchronous <xref:System.Net.Sockets.Socket.BeginAccept%2A> ve <xref:System.Net.Sockets.Socket.EndAccept%2A> yöntemleri karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="424cb-104">The <xref:System.Net.Sockets.Socket> class follows the standard .NET Framework asynchronous naming pattern; for example, the synchronous <xref:System.Net.Sockets.Socket.Accept%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginAccept%2A> and <xref:System.Net.Sockets.Socket.EndAccept%2A> methods.</span></span>  
  
 <span data-ttu-id="424cb-105">Asynchronous sunucu soketi, ağdan bağlantı isteklerini kabul etmeye başlamak için bir yöntem, bağlantı isteklerini işlemek ve ağdan veri almaya başlamak için bir geri arama yöntemi ve verileri almayı sona erdirmek için bir geri arama yöntemi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="424cb-105">An asynchronous server socket requires a method to begin accepting connection requests from the network, a callback method to handle the connection requests and begin receiving data from the network, and a callback method to end receiving the data.</span></span> <span data-ttu-id="424cb-106">Tüm bu yöntemler bu bölümde daha fazla ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="424cb-106">All these methods are discussed further in this section.</span></span>  
  
 <span data-ttu-id="424cb-107">Aşağıdaki örnekte, ağdan bağlantı isteklerini kabul `StartListening` etmeye başlamak için, yöntem **Soketi** başlatır ve ardından yeni bağlantıları kabul etmeye başlamak için **BeginAccept** yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="424cb-107">In the following example, to begin accepting connection requests from the network, the method `StartListening` initializes the **Socket** and then uses the **BeginAccept** method to start accepting new connections.</span></span> <span data-ttu-id="424cb-108">Yuvada yeni bir bağlantı isteği alındığı zaman geri aramayı kabul etme yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="424cb-108">The accept callback method is called when a new connection request is received on the socket.</span></span> <span data-ttu-id="424cb-109">Bağlantıyı işleyecek **Soket** örneğini almaktan ve bu **Soketi** isteği işleyecek iş parçacığına teslim etmeden sorumludur.</span><span class="sxs-lookup"><span data-stu-id="424cb-109">It is responsible for getting the **Socket** instance that will handle the connection and handing that **Socket** off to the thread that will process the request.</span></span> <span data-ttu-id="424cb-110">Geri aramayı kabul et <xref:System.AsyncCallback> yöntemi temsilciyi uygular; bir boşluk döndürür ve türünden <xref:System.IAsyncResult>tek bir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="424cb-110">The accept callback method implements the <xref:System.AsyncCallback> delegate; it returns a void and takes a single parameter of type <xref:System.IAsyncResult>.</span></span> <span data-ttu-id="424cb-111">Aşağıdaki örnek, geri arama kabul yönteminin kabuğudur.</span><span class="sxs-lookup"><span data-stu-id="424cb-111">The following example is the shell of an accept callback method.</span></span>  
  
```vb  
Sub AcceptCallback(ar As IAsyncResult)  
    ' Add the callback code here.  
End Sub 'AcceptCallback  
```  
  
```csharp  
void AcceptCallback(IAsyncResult ar)
{  
    // Add the callback code here.  
}  
```  
  
 <span data-ttu-id="424cb-112">**BeginAccept** yöntemi iki parametre alır, geri çağırma yı kabul etme yöntemini işaret eden bir **AsyncCallback** temsilcisi ve durum bilgilerini geri arama yöntemine aktarmak için kullanılan bir nesne.</span><span class="sxs-lookup"><span data-stu-id="424cb-112">The **BeginAccept** method takes two parameters, an **AsyncCallback** delegate that points to the accept callback method and an object that is used to pass state information to the callback method.</span></span> <span data-ttu-id="424cb-113">Aşağıdaki örnekte, dinleme **Soketi** *durum* parametresi aracılığıyla geri arama yöntemine aktarılır.</span><span class="sxs-lookup"><span data-stu-id="424cb-113">In the following example, the listening **Socket** is passed to the callback method through the *state* parameter.</span></span> <span data-ttu-id="424cb-114">Bu örnek bir **AsyncCallback** temsilcisi oluşturur ve ağdan bağlantıları kabul etmeye başlar.</span><span class="sxs-lookup"><span data-stu-id="424cb-114">This example creates an **AsyncCallback** delegate and starts accepting connections from the network.</span></span>  
  
```vb  
listener.BeginAccept( _  
    New AsyncCallback(SocketListener.AcceptCallback),_  
    listener)  
```  
  
```csharp  
listener.BeginAccept(new AsyncCallback(SocketListener.AcceptCallback), listener);  
```  
  
 <span data-ttu-id="424cb-115">Asynchronous soketleri gelen bağlantıları işlemek için sistem iş parçacığı havuzundan iş parçacığı kullanır.</span><span class="sxs-lookup"><span data-stu-id="424cb-115">Asynchronous sockets use threads from the system thread pool to process incoming connections.</span></span> <span data-ttu-id="424cb-116">Bir iş parçacığı bağlantıları kabul etmekten sorumludur, gelen her bağlantıyı işlemek için başka bir iş parçacığı kullanılır ve başka bir iş parçacığı bağlantıdan veri almaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="424cb-116">One thread is responsible for accepting connections, another thread is used to handle each incoming connection, and another thread is responsible for receiving data from the connection.</span></span> <span data-ttu-id="424cb-117">Bunlar, iş parçacığı havuzu tarafından atanan iş parçacığına bağlı olarak aynı iş parçacığı olabilir.</span><span class="sxs-lookup"><span data-stu-id="424cb-117">These could be the same thread, depending on which thread is assigned by the thread pool.</span></span> <span data-ttu-id="424cb-118">Aşağıdaki örnekte, <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> sınıf ana iş parçacığının yürütülmesini askıya adakalır ve yürütmenin ne zaman devam edebileceği sinyalleri iletamama.</span><span class="sxs-lookup"><span data-stu-id="424cb-118">In the following example, the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class suspends execution of the main thread and signals when execution can continue.</span></span>  
  
 <span data-ttu-id="424cb-119">Aşağıdaki örnek, yerel bilgisayarda eşzamanlı bir TCP/IP soketi oluşturan ve bağlantıları kabul etmeye başlayan bir eşzamanlı yöntem gösterir.</span><span class="sxs-lookup"><span data-stu-id="424cb-119">The following example shows an asynchronous method that creates an asynchronous TCP/IP socket on the local computer and begins accepting connections.</span></span> <span data-ttu-id="424cb-120">Bu, adında genel bir **ManualResetEvent** olduğunu `allDone`varsayar, yöntem adlı `SocketListener`bir sınıfın üyesi olduğunu `AcceptCallback` , ve adlı bir geri arama yöntemi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="424cb-120">It assumes that there is a global **ManualResetEvent** named `allDone`, that the method is a member of a class named `SocketListener`, and that a callback method named `AcceptCallback` is defined.</span></span>  
  
```vb  
Public Sub StartListening()  
    Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
    Dim localEP = New IPEndPoint(ipHostInfo.AddressList(0), 11000)  
  
    Console.WriteLine($"Local address and port : {localEP.ToString()}")  
  
    Dim listener As New Socket(localEP.Address.AddressFamily, _  
       SocketType.Stream, ProtocolType.Tcp)  
  
    Try  
        listener.Bind(localEP)  
        listener.Listen(10)  
  
        While True  
            allDone.Reset()  
  
            Console.WriteLine("Waiting for a connection...")  
            listener.BeginAccept(New _  
                AsyncCallback(SocketListener.AcceptCallback), _  
                listener)  
  
            allDone.WaitOne()  
        End While  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
    Console.WriteLine("Closing the listener...")  
End Sub 'StartListening  
```  
  
```csharp  
public void StartListening()
{  
    IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
    IPEndPoint localEP = new IPEndPoint(ipHostInfo.AddressList[0], 11000);  
  
    Console.WriteLine($"Local address and port : {localEP.ToString()}");  
  
    Socket listener = new Socket(localEP.Address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);  
  
    try
    {  
        listener.Bind(localEP);  
        listener.Listen(10);  
  
        while (true)
        {  
            allDone.Reset();  
  
            Console.WriteLine("Waiting for a connection...");  
            listener.BeginAccept(new AsyncCallback(SocketListener.AcceptCallback), listener);  
  
            allDone.WaitOne();  
        }  
    }
    catch (Exception e)
    {  
        Console.WriteLine(e.ToString());  
    }  
  
    Console.WriteLine("Closing the listener...");  
}  
```  
  
 <span data-ttu-id="424cb-121">Geri aramayı kabul`AcceptCallback` etme yöntemi (önceki örnekte) ana uygulama iş parçacığının işlemedevam etmesi için sinyal verme, istemciyle bağlantı kurma ve istemciden gelen verilerin eşzamanlı okumasını başlatmaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="424cb-121">The accept callback method (`AcceptCallback` in the preceding example) is responsible for signaling the main application thread to continue processing, establishing the connection with the client, and starting the asynchronous read of data from the client.</span></span> <span data-ttu-id="424cb-122">Aşağıdaki örnek, `AcceptCallback` yöntemin uygulanmasının ilk bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="424cb-122">The following example is the first part of an implementation of the `AcceptCallback` method.</span></span> <span data-ttu-id="424cb-123">Yöntemin bu bölümü, işleme devam etmek için ana uygulama iş parçacığı sinyalleri ve istemciye bağlantı kurar.</span><span class="sxs-lookup"><span data-stu-id="424cb-123">This section of the method signals the main application thread to continue processing and establishes the connection to the client.</span></span> <span data-ttu-id="424cb-124">Bu adlı `allDone`genel bir **ManualResetEvent** varsayar.</span><span class="sxs-lookup"><span data-stu-id="424cb-124">It assumes a global **ManualResetEvent** named `allDone`.</span></span>  
  
```vb  
Public Sub AcceptCallback(ar As IAsyncResult)  
    allDone.Set()  
  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Additional code to read data goes here.  
End Sub 'AcceptCallback  
```  
  
```csharp  
public void AcceptCallback(IAsyncResult ar)
{  
    allDone.Set();  
  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Additional code to read data goes here.
}  
```  
  
 <span data-ttu-id="424cb-125">İstemci yuvasından veri okuma, eşsenkronize çağrılar arasında değerleri geçen bir durum nesnesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="424cb-125">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="424cb-126">Aşağıdaki örnek, uzak istemciden bir dize almak için bir durum nesnesi uygular.</span><span class="sxs-lookup"><span data-stu-id="424cb-126">The following example implements a state object for receiving a string from the remote client.</span></span> <span data-ttu-id="424cb-127">İstemci yuvası için alanlar, veri almak için bir <xref:System.Text.StringBuilder> veri arabelleği ve istemci tarafından gönderilen veri dizesini oluşturmak için bir alan içerir.</span><span class="sxs-lookup"><span data-stu-id="424cb-127">It contains fields for the client socket, a data buffer for receiving data, and a <xref:System.Text.StringBuilder> for creating the data string sent by the client.</span></span> <span data-ttu-id="424cb-128">Bu alanların durum nesnesine yerleştirilmesi, istemci yuvasından gelen verileri okumak için değerlerinin birden çok çağrı arasında korunmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="424cb-128">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
```vb  
Public Class StateObject  
    Public workSocket As Socket = Nothing  
    Public BufferSize As Integer = 1024  
    Public buffer(BufferSize) As Byte  
    Public sb As New StringBuilder()  
End Class 'StateObject  
```  
  
```csharp  
public class StateObject
{  
    public Socket workSocket = null;  
    public const int BufferSize = 1024;  
    public byte[] buffer = new byte[BufferSize];  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 <span data-ttu-id="424cb-129">Yöntemin `AcceptCallback` istemci soketinden veri almaya başlayan bölümü önce `StateObject` sınıfın bir örneğini başlatır ve ardından istemci soketinden verileri eşzamanlı olarak okumaya başlamak için <xref:System.Net.Sockets.Socket.BeginReceive%2A> yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="424cb-129">The section of the `AcceptCallback` method that starts receiving the data from the client socket first initializes an instance of the `StateObject` class and then calls the <xref:System.Net.Sockets.Socket.BeginReceive%2A> method to start reading the data from the client socket asynchronously.</span></span>  
  
 <span data-ttu-id="424cb-130">Aşağıdaki örnek, tam `AcceptCallback` yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="424cb-130">The following example shows the complete `AcceptCallback` method.</span></span> <span data-ttu-id="424cb-131">`StateObject` **ManualResetEvent** `ReadCallback` Sınıfın tanımlandığını ve yöntemin . `SocketListener` `allDone,`</span><span class="sxs-lookup"><span data-stu-id="424cb-131">It assumes that there is a global **ManualResetEvent** named `allDone,` that the `StateObject` class is defined, and that the `ReadCallback` method is defined in a class named `SocketListener`.</span></span>  
  
```vb  
Public Shared Sub AcceptCallback(ar As IAsyncResult)  
    ' Get the socket that handles the client request.  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Signal the main thread to continue.  
    allDone.Set()  
  
    ' Create the state object.  
    Dim state As New StateObject()  
    state.workSocket = handler  
    handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
        AddressOf AsynchronousSocketListener.ReadCallback, state)  
End Sub 'AcceptCallback  
```  
  
```csharp  
public static void AcceptCallback(IAsyncResult ar)
{  
    // Get the socket that handles the client request.  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Signal the main thread to continue.  
    allDone.Set();  
  
    // Create the state object.  
    StateObject state = new StateObject();  
    state.workSocket = handler;  
    handler.BeginReceive(state.buffer, 0, StateObject.BufferSize, 0,  
        new AsyncCallback(AsynchronousSocketListener.ReadCallback), state);  
}  
```  
  
 <span data-ttu-id="424cb-132">Asynchronous soket sunucusu için uygulanması gereken son yöntem, istemci tarafından gönderilen verileri döndüren okuma geri arama yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="424cb-132">The final method that needs to be implemented for the asynchronous socket server is the read callback method that returns the data sent by the client.</span></span> <span data-ttu-id="424cb-133">Geri aramayı kabul et yöntemi gibi, okuma geri arama yöntemi de bir **AsyncCallback** temsilcisidir.</span><span class="sxs-lookup"><span data-stu-id="424cb-133">Like the accept callback method, the read callback method is an **AsyncCallback** delegate.</span></span> <span data-ttu-id="424cb-134">Bu yöntem, istemci yuvasından veri arabelleği içine bir veya daha fazla bayt okur ve istemci tarafından gönderilen veriler tamamlanana kadar **BeginReceive** yöntemini yeniden çağırır.</span><span class="sxs-lookup"><span data-stu-id="424cb-134">This method reads one or more bytes from the client socket into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="424cb-135">İletinin tamamı istemciden okunduktan sonra, dize konsolda görüntülenir ve istemciye bağlantı işleyen sunucu soketi kapatılır.</span><span class="sxs-lookup"><span data-stu-id="424cb-135">Once the entire message has been read from the client, the string is displayed on the console and the server socket handling the connection to the client is closed.</span></span>  
  
 <span data-ttu-id="424cb-136">Aşağıdaki örnek `ReadCallback` yöntemi uygular.</span><span class="sxs-lookup"><span data-stu-id="424cb-136">The following sample implements the `ReadCallback` method.</span></span> <span data-ttu-id="424cb-137">`StateObject` Sınıfın tanımlandığını varsayar.</span><span class="sxs-lookup"><span data-stu-id="424cb-137">It assumes that the `StateObject` class is defined.</span></span>  
  
```vb  
Public Shared Sub ReadCallback(ar As IAsyncResult)  
    Dim state As StateObject = CType(ar.AsyncState, StateObject)  
    Dim handler As Socket = state.workSocket  
  
    ' Read data from the client socket.
    Dim read As Integer = handler.EndReceive(ar)  
  
    ' Data was read from the client socket.  
    If read > 0 Then  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, read))  
        handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf ReadCallback, state)  
    Else  
        If state.sb.Length > 1 Then  
            ' All the data has been read from the client;  
            ' display it on the console.  
            Dim content As String = state.sb.ToString()  
            Console.WriteLine($"Read {content.Length} bytes from socket. {ControlChars.Cr} Data : {content}")  
        End If  
    End If  
End Sub 'ReadCallback  
```  
  
```csharp  
public static void ReadCallback(IAsyncResult ar)
{  
    StateObject state = (StateObject) ar.AsyncState;  
    Socket handler = state.WorkSocket;  
  
    // Read data from the client socket.  
    int read = handler.EndReceive(ar);  
  
    // Data was read from the client socket.  
    if (read > 0)
    {  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,read));  
        handler.BeginReceive(state.buffer, 0, StateObject.BufferSize, 0,  
            new AsyncCallback(ReadCallback), state);  
    }
    else
    {  
        if (state.sb.Length > 1)
        {  
            // All the data has been read from the client;  
            // display it on the console.  
            string content = state.sb.ToString();  
            Console.WriteLine($"Read {content.Length} bytes from socket.\n Data : {content}");
        }  
        handler.Close();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="424cb-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="424cb-138">See also</span></span>

- [<span data-ttu-id="424cb-139">Zaman Uyumlu Sunucu Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="424cb-139">Using a Synchronous Server Socket</span></span>](using-a-synchronous-server-socket.md)
- [<span data-ttu-id="424cb-140">Zaman Uyumsuz Sunucu Yuvası Örneği</span><span class="sxs-lookup"><span data-stu-id="424cb-140">Asynchronous Server Socket Example</span></span>](asynchronous-server-socket-example.md)
- [<span data-ttu-id="424cb-141">İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="424cb-141">Threading</span></span>](../../standard/threading/index.md)
- [<span data-ttu-id="424cb-142">Yuvalarla Dinleme</span><span class="sxs-lookup"><span data-stu-id="424cb-142">Listening with Sockets</span></span>](listening-with-sockets.md)
