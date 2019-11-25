---
title: <httpListener> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 0054be3d2002e4ea5247f25d8094386ac7242422
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088385"
---
# <a name="httplistener-element-network-settings"></a><span data-ttu-id="75f56-102">\<httpListener > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="75f56-102">\<httpListener> Element (Network Settings)</span></span>
<span data-ttu-id="75f56-103"><xref:System.Net.HttpListener> sınıfı tarafından kullanılan parametreleri özelleştirir.</span><span class="sxs-lookup"><span data-stu-id="75f56-103">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  

<span data-ttu-id="75f56-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="75f56-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="75f56-105">[**System. net >\<** ](system-net-element-network-settings.md) &nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="75f56-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="75f56-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ayarları >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="75f56-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>\
<span data-ttu-id="75f56-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<httpListener >**</span><span class="sxs-lookup"><span data-stu-id="75f56-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpListener>**</span></span>

## <a name="syntax"></a><span data-ttu-id="75f56-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75f56-108">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="75f56-109">Tür</span><span class="sxs-lookup"><span data-stu-id="75f56-109">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75f56-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="75f56-110">Attributes and Elements</span></span>  
 <span data-ttu-id="75f56-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="75f56-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75f56-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="75f56-112">Attributes</span></span>  
  
|<span data-ttu-id="75f56-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="75f56-113">Attribute</span></span>|<span data-ttu-id="75f56-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75f56-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="75f56-115">unescapeRequestUrl 'Si</span><span class="sxs-lookup"><span data-stu-id="75f56-115">unescapeRequestUrl</span></span>|<span data-ttu-id="75f56-116">Bir <xref:System.Net.HttpListener> örneğinin, dönüştürülmüş URI yerine ham unatsız URI kullanıp kullanmadığını gösteren bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="75f56-116">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75f56-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="75f56-117">Child Elements</span></span>  
 <span data-ttu-id="75f56-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="75f56-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="75f56-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="75f56-119">Parent Elements</span></span>  
  
|<span data-ttu-id="75f56-120">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="75f56-120">**Element**</span></span>|<span data-ttu-id="75f56-121">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="75f56-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="75f56-122">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="75f56-122">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="75f56-123"><xref:System.Net> ad alanı için temel ağ seçeneklerini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="75f56-123">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75f56-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75f56-124">Remarks</span></span>  
 <span data-ttu-id="75f56-125">**UnescapeRequestUrl** özniteliği, <xref:System.Net.HttpListener> yüzde kodlamalı değerlerin dönüştürüldüğü ve diğer normalleştirme adımlarının alındığı dönüştürülmüş URI yerine ham unatsız URI 'yi kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="75f56-125">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="75f56-126">Bir <xref:System.Net.HttpListener> örneği `http.sys` hizmeti üzerinden bir istek aldığında, `http.sys`tarafından sağlanmış URI dizesinin bir örneğini oluşturur ve bunu <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> özelliği olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="75f56-126">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="75f56-127">`http.sys` hizmeti iki istek URI dizesi kullanıma sunar:</span><span class="sxs-lookup"><span data-stu-id="75f56-127">The `http.sys` service exposes two request URI strings:</span></span>  
  
- <span data-ttu-id="75f56-128">Ham URI</span><span class="sxs-lookup"><span data-stu-id="75f56-128">Raw URI</span></span>  
  
- <span data-ttu-id="75f56-129">Dönüştürülmüş URI</span><span class="sxs-lookup"><span data-stu-id="75f56-129">Converted URI</span></span>  
  
 <span data-ttu-id="75f56-130">Ham URI, HTTP isteğinin istek satırında belirtilen <xref:System.Uri?displayProperty=nameWithType> ' dır:</span><span class="sxs-lookup"><span data-stu-id="75f56-130">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="75f56-131">Yukarıda bahsedilen istek için `http.sys` tarafından belirtilen ham URI, "/path/" dir.</span><span class="sxs-lookup"><span data-stu-id="75f56-131">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="75f56-132">Bu, ağ üzerinden gönderilen HTTP fiilini izleyen dizeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="75f56-132">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="75f56-133">`http.sys` hizmeti, isteğin iletilmesi gereken kaynak sunucuyu belirleyebilmek için HTTP istek satırında ve ana bilgisayar üstbilgisinde belirtilen URI 'yi kullanarak istekte belirtilen bilgilerden dönüştürülmüş bir URI oluşturur.</span><span class="sxs-lookup"><span data-stu-id="75f56-133">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="75f56-134">Bu, istekten gelen bilgileri kayıtlı bir URI önekleri kümesiyle karşılaştırarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="75f56-134">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="75f56-135">HTTP sunucusu SDK belgeleri, bu dönüştürülmüş URI 'yi HTTP_COOKED_URL yapısı olarak ifade eder.</span><span class="sxs-lookup"><span data-stu-id="75f56-135">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="75f56-136">İsteği kayıtlı URI önekleriyle karşılaştırabilmek için, isteğin bazı normalleştirilmesi yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="75f56-136">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="75f56-137">Yukarıdaki örnek için, dönüştürülmüş URI aşağıdaki gibi olacaktır:</span><span class="sxs-lookup"><span data-stu-id="75f56-137">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="75f56-138">`http.sys` hizmeti, dönüştürülmüş bir URI oluşturmak için <xref:System.Uri.Host%2A?displayProperty=nameWithType> özellik değerini ve istek satırındaki dizeyi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="75f56-138">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="75f56-139">Ayrıca, `http.sys` ve <xref:System.Uri?displayProperty=nameWithType> sınıfı şunları da yapar:</span><span class="sxs-lookup"><span data-stu-id="75f56-139">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
- <span data-ttu-id="75f56-140">Tüm kodlanmış değerleri iptal eder.</span><span class="sxs-lookup"><span data-stu-id="75f56-140">Un-escapes all percent encoded values.</span></span>  
  
- <span data-ttu-id="75f56-141">Yüzde kodlamalı ASCII olmayan karakterleri UTF-16 karakter temsiline dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="75f56-141">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="75f56-142">UTF-8 ve ANSI/DBCS karakterlerinin desteklendiğine ve Unicode karakterler (% uXXXX biçimi kullanılarak Unicode kodlaması) gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="75f56-142">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
- <span data-ttu-id="75f56-143">Yol sıkıştırması gibi diğer normalleştirme adımlarını yürütür.</span><span class="sxs-lookup"><span data-stu-id="75f56-143">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="75f56-144">İstek, yüzde kodlamalı değerler için kullanılan kodlama hakkında herhangi bir bilgi içermediğinden, yalnızca yüzde kodlamalı değerleri ayrıştırarak doğru kodlamayı tespit etmek mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="75f56-144">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="75f56-145">Bu nedenle `http.sys` işlemi değiştirmek için iki kayıt defteri anahtarı sağlar:</span><span class="sxs-lookup"><span data-stu-id="75f56-145">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="75f56-146">Kayıt Defteri Anahtarı</span><span class="sxs-lookup"><span data-stu-id="75f56-146">Registry Key</span></span>|<span data-ttu-id="75f56-147">Varsayılan Değer</span><span class="sxs-lookup"><span data-stu-id="75f56-147">Default Value</span></span>|<span data-ttu-id="75f56-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75f56-148">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="75f56-149">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="75f56-149">EnableNonUTF8</span></span>|<span data-ttu-id="75f56-150">1\.</span><span class="sxs-lookup"><span data-stu-id="75f56-150">1</span></span>|<span data-ttu-id="75f56-151">Sıfır ise, `http.sys` yalnızca UTF-8 kodlu URL 'Leri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="75f56-151">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="75f56-152">Sıfır olmayan `http.sys`, istekler içinde ANSI kodlamalı veya DBCS kodlu URL 'Leri de kabul eder.</span><span class="sxs-lookup"><span data-stu-id="75f56-152">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="75f56-153">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="75f56-153">FavorUTF8</span></span>|<span data-ttu-id="75f56-154">1\.</span><span class="sxs-lookup"><span data-stu-id="75f56-154">1</span></span>|<span data-ttu-id="75f56-155">Sıfır olmayan `http.sys`, her zaman ilk olarak bir URL 'YI UTF-8 olarak çözmeye çalışır; Bu dönüştürme başarısız olursa ve EnableNonUTF8 sıfır olmayan bir değer ise, http. sys daha sonra ANSI veya DBCS olarak kodunu çözmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="75f56-155">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="75f56-156">Sıfır (ve EnableNonUTF8 sıfır olmayan) ise, `http.sys`, ANSI veya DBCS olarak kod çözmeye çalışır; Bu başarılı olmazsa, UTF-8 dönüşümü çalışır.</span><span class="sxs-lookup"><span data-stu-id="75f56-156">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="75f56-157"><xref:System.Net.HttpListener> bir istek aldığında, <xref:System.Net.HttpListenerRequest.Url%2A> özelliğine girdi olarak `http.sys` dönüştürülmüş URI kullanır.</span><span class="sxs-lookup"><span data-stu-id="75f56-157">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="75f56-158">URI 'Ler içindeki karakter ve sayıların yanı sıra karakterleri destekleme gereksinimi vardır.</span><span class="sxs-lookup"><span data-stu-id="75f56-158">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="75f56-159">"1/3812" müşteri numarası için müşteri bilgilerini almak üzere kullanılan aşağıdaki URI bir örnektir:</span><span class="sxs-lookup"><span data-stu-id="75f56-159">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="75f56-160">URI (% 2F) içindeki yüzde kodlamalı eğik çizgiye göz önünde edin.</span><span class="sxs-lookup"><span data-stu-id="75f56-160">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="75f56-161">Bu, bu durumda, eğik çizgi karakteri bir yol sınırlayıcısı değil verileri temsil ettiğinden bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="75f56-161">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="75f56-162">Dizenin URI oluşturucusuna geçirilmesi şu URI 'ye neden olur:</span><span class="sxs-lookup"><span data-stu-id="75f56-162">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="75f56-163">Yolun segmentlerine bölünmesi aşağıdaki öğelerin oluşmasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="75f56-163">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="75f56-164">Bu, istek göndericisinin amacı değildir.</span><span class="sxs-lookup"><span data-stu-id="75f56-164">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="75f56-165">**UnescapeRequestUrl** özniteliği **false**olarak ayarlandıysa <xref:System.Net.HttpListener> bir istek aldığında, <xref:System.Net.HttpListenerRequest.Url%2A> özelliğine GIRIŞ olarak `http.sys` dönüştürülmüş URI yerine ham URI kullanır.</span><span class="sxs-lookup"><span data-stu-id="75f56-165">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="75f56-166">**UnescapeRequestUrl** özniteliği için varsayılan değer **true**'dur.</span><span class="sxs-lookup"><span data-stu-id="75f56-166">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="75f56-167"><xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> özelliği, ilgili yapılandırma dosyalarından **unescapeRequestUrl** özniteliğinin geçerli değerini almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="75f56-167">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75f56-168">Örnek</span><span class="sxs-lookup"><span data-stu-id="75f56-168">Example</span></span>  
 <span data-ttu-id="75f56-169">Aşağıdaki örnek <xref:System.Net.HttpListenerRequest.Url%2A> özelliğine girdi olarak `http.sys` dönüştürülmüş URI yerine ham URI kullanma isteği aldığında <xref:System.Net.HttpListener> sınıfının nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="75f56-169">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpListener  
        unescapeRequestUrl="false"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="75f56-170">Öğe Bilgisi</span><span class="sxs-lookup"><span data-stu-id="75f56-170">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="75f56-171">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="75f56-171">Namespace</span></span>|<span data-ttu-id="75f56-172">System.Net</span><span class="sxs-lookup"><span data-stu-id="75f56-172">System.Net</span></span>|  
|<span data-ttu-id="75f56-173">Şema adı</span><span class="sxs-lookup"><span data-stu-id="75f56-173">Schema Name</span></span>||  
|<span data-ttu-id="75f56-174">Doğrulama dosyası</span><span class="sxs-lookup"><span data-stu-id="75f56-174">Validation File</span></span>||  
|<span data-ttu-id="75f56-175">Boş olabilir</span><span class="sxs-lookup"><span data-stu-id="75f56-175">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="75f56-176">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75f56-176">See also</span></span>

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [<span data-ttu-id="75f56-177">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="75f56-177">Network Settings Schema</span></span>](index.md)
