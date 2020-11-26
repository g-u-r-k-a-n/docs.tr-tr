---
title: Yuvalarla Dinleme
description: Sunucu yuvasının ağ üzerinde bir bağlantı noktası açtığı ve istemcinin bu bağlantı noktasına bağlanmasını beklediği bir uzak hizmeti oluşturmayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- sockets, listening with sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- protocols, sockets
- listening with sockets
- Internet, sockets
ms.assetid: 40e426cc-13db-4371-95eb-f7388bd23ebf
ms.openlocfilehash: 4249948579384ec0159ba61072126944596c8f56
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242220"
---
# <a name="listening-with-sockets"></a><span data-ttu-id="bfd6b-103">Yuvalarla Dinleme</span><span class="sxs-lookup"><span data-stu-id="bfd6b-103">Listening with Sockets</span></span>

<span data-ttu-id="bfd6b-104">Dinleyici veya sunucu Yuvaları ağ üzerinde bir bağlantı noktası açın ve bir istemcinin bu bağlantı noktasına bağlanmasını bekleyin.</span><span class="sxs-lookup"><span data-stu-id="bfd6b-104">Listener or server sockets open a port on the network and then wait for a client to connect to that port.</span></span> <span data-ttu-id="bfd6b-105">Diğer ağ adresi aileleri ve protokolleri var olsa da, bu örnek bir TCP/IP ağı için uzak hizmetin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bfd6b-105">Although other network address families and protocols exist, this example shows how to create remote service for a TCP/IP network.</span></span>  
  
 <span data-ttu-id="bfd6b-106">TCP/IP hizmetinin benzersiz adresi, hizmet için bir uç nokta oluşturmak üzere hizmetin bağlantı noktası numarasıyla ana bilgisayarın IP adresi birleştirilerek tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="bfd6b-106">The unique address of a TCP/IP service is defined by combining the IP address of the host with the port number of the service to create an endpoint for the service.</span></span> <span data-ttu-id="bfd6b-107"><xref:System.Net.Dns>Sınıfı, yerel ağ aygıtı tarafından desteklenen ağ adresleri hakkında bilgi döndüren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="bfd6b-107">The <xref:System.Net.Dns> class provides methods that return information about the network addresses supported by the local network device.</span></span> <span data-ttu-id="bfd6b-108">Yerel ağ cihazında birden fazla ağ adresi varsa veya yerel sistem birden fazla ağ cihazını destekliyorsa, **DNS** sınıfı tüm ağ adresleriyle ilgili bilgileri döndürür ve uygulamanın hizmet için uygun adresi seçmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="bfd6b-108">When the local network device has more than one network address, or if the local system supports more than one network device, the **Dns** class returns information about all network addresses, and the application must choose the proper address for the service.</span></span> <span data-ttu-id="bfd6b-109">Internet atanmış numaralar yetkilisi (IANA), ortak hizmetler için bağlantı noktası numaralarını tanımlar; daha fazla bilgi için bkz. [hizmet adı ve Aktarım Protokolü bağlantı noktası numarası kayıt defteri](https://www.iana.org/assignments/port-numbers).</span><span class="sxs-lookup"><span data-stu-id="bfd6b-109">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services; for more information, see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="bfd6b-110">Diğer hizmetler 1.024 ile 65.535 arasında kayıt bağlantı noktası numaraları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="bfd6b-110">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="bfd6b-111">Aşağıdaki örnek, <xref:System.Net.IPEndPoint> ana bilgisayar Için **DNS** tarafından döndürülen ilk IP adresini, kayıtlı bağlantı noktası numaraları aralığından seçilen bir bağlantı noktası numarası ile birleştirerek bir sunucu için oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bfd6b-111">The following example creates an <xref:System.Net.IPEndPoint> for a server by combining the first IP address returned by **Dns** for the host computer with a port number chosen from the registered port numbers range.</span></span>  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.GetHostEntry(Dns.GetHostName())  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
Dim localEndPoint As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.GetHostEntry(Dns.GetHostName());  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
IPEndPoint localEndPoint = new IPEndPoint(ipAddress, 11000);  
```  
  
 <span data-ttu-id="bfd6b-112">Yerel uç nokta saptandıktan sonra, <xref:System.Net.Sockets.Socket> yöntemi kullanılarak bu uç noktayla ilişkilendirilmelidir <xref:System.Net.Sockets.Socket.Bind%2A> ve yöntemi kullanılarak uç noktada dinlemek üzere ayarlanır <xref:System.Net.Sockets.Socket.Listen%2A> .</span><span class="sxs-lookup"><span data-stu-id="bfd6b-112">After the local endpoint is determined, the <xref:System.Net.Sockets.Socket> must be associated with that endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> method and set to listen on the endpoint using the <xref:System.Net.Sockets.Socket.Listen%2A> method.</span></span> <span data-ttu-id="bfd6b-113">**Bağlama** , belirli bir adres ve bağlantı noktası birleşimi zaten kullanımda olduğunda bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bfd6b-113">**Bind** throws an exception if the specific address and port combination is already in use.</span></span> <span data-ttu-id="bfd6b-114">Aşağıdaki örnek, bir **yuvayı** **ipendpoint** ile ilişkilendirdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bfd6b-114">The following example demonstrates associating a **Socket** with an **IPEndPoint**.</span></span>  
  
```vb  
Dim listener As New Socket(ipAddress.AddressFamily, _  
    SocketType.Stream, ProtocolType.Tcp)
listener.Bind(localEndPoint)  
listener.Listen(100)  
```  
  
```csharp  
Socket listener = new Socket(ipAddress.AddressFamily,
    SocketType.Stream, ProtocolType.Tcp);
listener.Bind(localEndPoint);  
listener.Listen(100);  
```  
  
 <span data-ttu-id="bfd6b-115">**Dinleme** yöntemi, bağlantı istemcisine sunucu meşgul hatası döndürülmeden önce **yuva** için kaç tane bekleyen bağlantıya izin verileceğini belirten tek bir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="bfd6b-115">The **Listen** method takes a single parameter that specifies how many pending connections to the **Socket** are allowed before a server busy error is returned to the connecting client.</span></span> <span data-ttu-id="bfd6b-116">Bu durumda, 100 istemci 101 numarasına bir sunucu meşgul yanıtı döndürülmeden önce bağlantı kuyruğuna kadar istemci konur.</span><span class="sxs-lookup"><span data-stu-id="bfd6b-116">In this case, up to 100 clients are placed in the connection queue before a server busy response is returned to client number 101.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfd6b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bfd6b-117">See also</span></span>

- [<span data-ttu-id="bfd6b-118">Zaman Uyumlu Sunucu Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="bfd6b-118">Using a Synchronous Server Socket</span></span>](using-a-synchronous-server-socket.md)
- [<span data-ttu-id="bfd6b-119">Zaman Uyumsuz Sunucu Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="bfd6b-119">Using an Asynchronous Server Socket</span></span>](using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="bfd6b-120">İstemci Yuvaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="bfd6b-120">Using Client Sockets</span></span>](using-client-sockets.md)
- [<span data-ttu-id="bfd6b-121">Nasıl yapılır: Yuva Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bfd6b-121">How to: Create a Socket</span></span>](how-to-create-a-socket.md)
- [<span data-ttu-id="bfd6b-122">Yuvalar</span><span class="sxs-lookup"><span data-stu-id="bfd6b-122">Sockets</span></span>](sockets.md)
