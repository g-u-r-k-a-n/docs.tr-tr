---
description: Hakkında daha fazla bilgi <mscorlib> için bkz. şifreleme ayarları için öğesi
title: Şifreleme Ayarları için <mscorlib> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
ms.openlocfilehash: 7606cdd1349c7594b5303832eed59ac51c1ddfe6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698901"
---
# <a name="mscorlib-element-for-cryptography-settings"></a><span data-ttu-id="dce4b-103">Şifreleme Ayarları için \<mscorlib> Öğesi</span><span class="sxs-lookup"><span data-stu-id="dce4b-103">\<mscorlib> Element for Cryptography Settings</span></span>

<span data-ttu-id="dce4b-104">[ \<cryptographySettings> Öğesini](cryptographysettings-element.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="dce4b-104">Contains the [\<cryptographySettings> element](cryptographysettings-element.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<mscorlib>**  
  
## <a name="syntax"></a><span data-ttu-id="dce4b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="dce4b-105">Syntax</span></span>  
  
```xml  
      <mscorlib>
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dce4b-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dce4b-106">Attributes and Elements</span></span>  

 <span data-ttu-id="dce4b-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dce4b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dce4b-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dce4b-108">Attributes</span></span>  

 <span data-ttu-id="dce4b-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="dce4b-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dce4b-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dce4b-110">Child Elements</span></span>  
  
|<span data-ttu-id="dce4b-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="dce4b-111">Element</span></span>|<span data-ttu-id="dce4b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dce4b-112">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="dce4b-113">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="dce4b-113">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dce4b-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dce4b-114">Parent Elements</span></span>  
  
|<span data-ttu-id="dce4b-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="dce4b-115">Element</span></span>|<span data-ttu-id="dce4b-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dce4b-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="dce4b-117">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="dce4b-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="dce4b-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="dce4b-118">Example</span></span>  

 <span data-ttu-id="dce4b-119">Aşağıdaki örnek, **\<mscorlib>** bir şifreleme sınıfına başvurmak ve çalışma zamanını yapılandırmak için öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="dce4b-119">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="dce4b-120">Daha sonra "RSA" dizesini <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemine geçirebilir ve <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodunu kullanarak bir `MyCryptoRSAClass` nesne döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dce4b-120">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dce4b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dce4b-121">See also</span></span>

- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>
- <xref:System.Security.Cryptography>
- [<span data-ttu-id="dce4b-122">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="dce4b-122">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="dce4b-123">Şifreleme ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="dce4b-123">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="dce4b-124">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="dce4b-124">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="dce4b-125">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="dce4b-125">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
