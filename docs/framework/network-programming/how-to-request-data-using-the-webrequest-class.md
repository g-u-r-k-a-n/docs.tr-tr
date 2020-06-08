---
title: 'Nasıl yapılır: WebRequest sınıfını kullanarak veri ISTEME'
description: .NET Framework Web sayfası veya dosya gibi bir kaynağı sunucudan WebRequest sınıfını kullanarak bir sunucudan isteme hakkında bilgi edinin.
ms.date: 03/21/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- downloading Internet resources, steps
- requesting data from Internet, steps
- WebRequest class, receiving data
- receiving data, using WebRequest class
- Internet, requesting data
ms.assetid: 368b8d0f-dc5e-4469-a8b8-b2adbf5dd800
ms.openlocfilehash: 5dcc1a7dad226288e3f74969b86e2dd457c0eed0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502476"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a><span data-ttu-id="01ef2-103">Nasıl yapılır: WebRequest sınıfını kullanarak veri ISTEME</span><span class="sxs-lookup"><span data-stu-id="01ef2-103">How to: Request data by using the WebRequest class</span></span>

<span data-ttu-id="01ef2-104">Aşağıdaki yordam bir sunucudan bir Web sayfası veya dosya gibi bir kaynak isteme adımlarını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="01ef2-104">The following procedure describes the steps to request a resource, such as a Web page or a file, from a server.</span></span> <span data-ttu-id="01ef2-105">Kaynağın bir URI ile tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="01ef2-105">The resource must be identified by a URI.</span></span>

## <a name="to-request-data-from-a-host-server"></a><span data-ttu-id="01ef2-106">Bir konak sunucusundan veri istemek için</span><span class="sxs-lookup"><span data-stu-id="01ef2-106">To request data from a host server</span></span>

1. <span data-ttu-id="01ef2-107"><xref:System.Net.WebRequest> <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> BIR kaynağın URI 'siyle çağırarak bir örnek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="01ef2-107">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource.</span></span> <span data-ttu-id="01ef2-108">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="01ef2-108">For example:</span></span>

    ```csharp
    WebRequest request = WebRequest.Create("https://docs.microsoft.com");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("https://docs.microsoft.com")
    ```

    > [!NOTE]
    > <span data-ttu-id="01ef2-109">.NET Framework, <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> *http:*, *https:*, *FTP:* ve *Dosya:* ile başlayan URI 'ler için ve sınıflarından türetilmiş protokole özgü sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="01ef2-109">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>

    <span data-ttu-id="01ef2-110">Protokole özgü özellikleri ayarlamanız veya okumanız gerekiyorsa, <xref:System.Net.WebRequest> veya <xref:System.Net.WebResponse> nesnesini protokole özgü bir nesne türüne atamalısınız.</span><span class="sxs-lookup"><span data-stu-id="01ef2-110">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="01ef2-111">Daha fazla bilgi için bkz. [takılabilir protokolleri programlama](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="01ef2-111">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span>

2. <span data-ttu-id="01ef2-112">Nesneniz için ihtiyacınız olan herhangi bir özellik değerini ayarlayın `WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="01ef2-112">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="01ef2-113">Örneğin, kimlik doğrulamasını etkinleştirmek için, <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> özelliğini sınıfının bir örneğine ayarlayın <xref:System.Net.NetworkCredential> :</span><span class="sxs-lookup"><span data-stu-id="01ef2-113">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. <span data-ttu-id="01ef2-114">Çağırarak isteği sunucuya gönderin <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="01ef2-114">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="01ef2-115">Bu yöntem, sunucunun yanıtını içeren bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="01ef2-115">This method returns an object containing the server's response.</span></span> <span data-ttu-id="01ef2-116">Döndürülen <xref:System.Net.WebResponse> nesnenin türü, isteğin URI 'si düzenine göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="01ef2-116">The returned <xref:System.Net.WebResponse> object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="01ef2-117">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="01ef2-117">For example:</span></span>

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

4. <span data-ttu-id="01ef2-118">`WebResponse`Bir protokole özgü özellikleri okumak için nesnenizin özelliklerine erişebilir veya protokole özgü bir örneğe çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01ef2-118">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span>

    <span data-ttu-id="01ef2-119">Örneğin, HTTP 'ye özgü özelliklerine erişmek için <xref:System.Net.HttpWebResponse> , `WebResponse` nesnenizin `HttpWebResponse` başvurusunu bir başvuruya atayın.</span><span class="sxs-lookup"><span data-stu-id="01ef2-119">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an `HttpWebResponse` reference.</span></span> <span data-ttu-id="01ef2-120">Aşağıdaki kod örneği, <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> bir Yanıt ile GÖNDERILEN http 'e özgü özelliğin nasıl görüntüleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="01ef2-120">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>

    ```csharp
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)
    ```

5. <span data-ttu-id="01ef2-121">Sunucu tarafından gönderilen yanıt verilerini içeren akışı almak için <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="01ef2-121">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="01ef2-122">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="01ef2-122">For example:</span></span>

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

6. <span data-ttu-id="01ef2-123">Yanıt nesnesinden verileri okuduktan sonra, yöntemi ile kapatın <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> ya da yöntemi ile yanıt akışını kapatın <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="01ef2-123">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="01ef2-124">Yanıt nesnesini veya akışı kapatmazsanız, uygulamanız sunucu bağlantılarının tükenebilir ve ek istekleri işleyemez.</span><span class="sxs-lookup"><span data-stu-id="01ef2-124">If you don't close either the response object or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="01ef2-125">`WebResponse.Close`Yöntemi `Stream.Close` yanıtı kapattığı zaman çağırdığı için, `Close` hem yanıt hem de akış nesnelerinde çağırmak gerekli değildir, ancak bunu zararlı değildir.</span><span class="sxs-lookup"><span data-stu-id="01ef2-125">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="01ef2-126">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="01ef2-126">For example:</span></span>

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a><span data-ttu-id="01ef2-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="01ef2-127">Example</span></span>

<span data-ttu-id="01ef2-128">Aşağıdaki kod örneği, bir Web sunucusuna nasıl istek oluşturulacağını ve yanıttaki verileri nasıl okuyakullanacağınızı gösterir:</span><span class="sxs-lookup"><span data-stu-id="01ef2-128">The following code example shows how to create a request to a web server and read the data in its response:</span></span>

[!code-csharp[RequestDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/RequestDataUsingWebRequest/cs/WebRequestGetExample.cs)]
[!code-vb[RequestDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/RequestDataUsingWebRequest/vb/WebRequestGetExample.vb)]

## <a name="see-also"></a><span data-ttu-id="01ef2-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01ef2-129">See also</span></span>

- [<span data-ttu-id="01ef2-130">İnternet istekleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="01ef2-130">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="01ef2-131">Ağda akışlar kullanma</span><span class="sxs-lookup"><span data-stu-id="01ef2-131">Using Streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="01ef2-132">Bir ara sunucu üzerinden İnternet 'e erişme</span><span class="sxs-lookup"><span data-stu-id="01ef2-132">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="01ef2-133">Veri isteme</span><span class="sxs-lookup"><span data-stu-id="01ef2-133">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="01ef2-134">Nasıl yapılır: WebRequest sınıfını kullanarak veri gönderme</span><span class="sxs-lookup"><span data-stu-id="01ef2-134">How to: Send data by using the WebRequest class</span></span>](how-to-send-data-using-the-webrequest-class.md)
