---
title: <iriParsing> Öğesi (Uri Ayarları)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: fd617d1b4ac8e532c6f9aeaa01465e9866b059e9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698099"
---
# <a name="iriparsing-element-uri-settings"></a><span data-ttu-id="5e9f3-102">\<ıriayrıştırma > öğesi (URI ayarları)</span><span class="sxs-lookup"><span data-stu-id="5e9f3-102">\<iriParsing> Element (Uri Settings)</span></span>
<span data-ttu-id="5e9f3-103">Uluslararası kaynak tanımlayıcı (IRI) ayrıştırmanın bir <xref:System.Uri> uygulanıp uygulanmadığını ve IRI ayrıştırma kurallarının uygulanıp uygulanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e9f3-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
[<span data-ttu-id="5e9f3-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="5e9f3-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="5e9f3-105">&nbsp;&nbsp;[ **\<URI >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="5e9f3-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="5e9f3-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<ıriayrıştırma >**</span><span class="sxs-lookup"><span data-stu-id="5e9f3-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<iriParsing>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e9f3-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e9f3-107">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e9f3-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5e9f3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5e9f3-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5e9f3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e9f3-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5e9f3-110">Attributes</span></span>  
  
|<span data-ttu-id="5e9f3-111">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="5e9f3-111">**Element**</span></span>|<span data-ttu-id="5e9f3-112">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="5e9f3-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="5e9f3-113">IRI ayrıştırma özelliğinin etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e9f3-113">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="5e9f3-114">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="5e9f3-114">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e9f3-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5e9f3-115">Child Elements</span></span>  
 <span data-ttu-id="5e9f3-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="5e9f3-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5e9f3-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5e9f3-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5e9f3-118">**Öğe**</span><span class="sxs-lookup"><span data-stu-id="5e9f3-118">**Element**</span></span>|<span data-ttu-id="5e9f3-119">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="5e9f3-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5e9f3-120">uri</span><span class="sxs-lookup"><span data-stu-id="5e9f3-120">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="5e9f3-121">.NET Framework Tekdüzen Kaynak tanımlayıcıları (URI 'Ler) kullanarak ifade edilen Web adreslerini nasıl işleyeceğini belirten ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="5e9f3-121">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e9f3-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e9f3-122">Remarks</span></span>  
 <span data-ttu-id="5e9f3-123">Mevcut <xref:System.Uri> sınıfı .NET Framework 3,5 ' de genişletildi.</span><span class="sxs-lookup"><span data-stu-id="5e9f3-123">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="5e9f3-124">3,0 SP1 ve 2,0 SP1 uluslararası kaynak tanımlayıcıları (IRI) ve uluslararası etki alanı adları (ıDN) için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e9f3-124">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="5e9f3-125">IRI ve ıDN desteğini özellikle etkinleştirmedikleri takdirde geçerli kullanıcılar .NET Framework 2,0 davranışından herhangi bir değişiklik görmez.</span><span class="sxs-lookup"><span data-stu-id="5e9f3-125">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="5e9f3-126">Bu, uygulamanın .NET Framework önceki sürümleriyle uyumluluğunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e9f3-126">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="5e9f3-127">IRI desteğini etkinleştirmek için aşağıdaki iki değişiklik gereklidir:</span><span class="sxs-lookup"><span data-stu-id="5e9f3-127">To enable support for IRI, the following two changes are required:</span></span>  
  
1. <span data-ttu-id="5e9f3-128">Aşağıdaki satırı .NET Framework 2,0 dizinindeki Machine. config dosyasına ekleyin</span><span class="sxs-lookup"><span data-stu-id="5e9f3-128">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="5e9f3-129">IRI ayrıştırma kurallarının uygulanıp uygulanmayacağını belirtin.</span><span class="sxs-lookup"><span data-stu-id="5e9f3-129">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="5e9f3-130">Bu, Machine. config veya App. config dosyasında yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="5e9f3-130">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="5e9f3-131">IRI ayrıştırma (ıriayrıştırmayı etkin = `true`) etkinleştirildiğinde, RFC 3987 ' deki en son IRI kurallarına göre normalleştirme ve karakter denetimi yapılır.</span><span class="sxs-lookup"><span data-stu-id="5e9f3-131">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="5e9f3-132">Varsayılan değer `false`, RFC 2396 ve RFC 3986 ' e (IPv6 sabit değerleri için) göre normalleştirme ve karakter denetimi yapılır.</span><span class="sxs-lookup"><span data-stu-id="5e9f3-132">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="5e9f3-133">Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="5e9f3-133">Configuration Files</span></span>  
 <span data-ttu-id="5e9f3-134">Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5e9f3-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e9f3-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e9f3-135">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="5e9f3-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e9f3-136">Description</span></span>  
 <span data-ttu-id="5e9f3-137">Aşağıdaki örnekte, IRI ayrıştırma ve ıDN adlarını desteklemek için <xref:System.Uri> sınıfı tarafından kullanılan bir yapılandırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5e9f3-137">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5e9f3-138">Kod</span><span class="sxs-lookup"><span data-stu-id="5e9f3-138">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e9f3-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e9f3-139">See also</span></span>

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="5e9f3-140">Ağ Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="5e9f3-140">Network Settings Schema</span></span>](index.md)
