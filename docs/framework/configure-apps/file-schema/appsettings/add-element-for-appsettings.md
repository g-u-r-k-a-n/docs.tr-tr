---
title: <appSettings> için <add> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09864ea8f174d0c23f26db49f8cc0d43608522a0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119335"
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="c5209-102">\<appSettings için > öğesi \<ekleyin ></span><span class="sxs-lookup"><span data-stu-id="c5209-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="c5209-103">Özel bir uygulama ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="c5209-103">Adds a custom application setting.</span></span>

<span data-ttu-id="c5209-104">[ **\<yapılandırma >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="c5209-104">[**\<configuration>**](../configuration-element.md) </span></span>  
<span data-ttu-id="c5209-105">&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="c5209-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="c5209-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<ekleme >**</span><span class="sxs-lookup"><span data-stu-id="c5209-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c5209-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5209-107">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="c5209-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c5209-108">Attributes</span></span>

|           | <span data-ttu-id="c5209-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5209-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="c5209-110">**anahtar**</span><span class="sxs-lookup"><span data-stu-id="c5209-110">**key**</span></span>   | <span data-ttu-id="c5209-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c5209-111">Required attribute.</span></span><br><br><span data-ttu-id="c5209-112">Eklenecek anahtarın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5209-112">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="c5209-113">**value**</span><span class="sxs-lookup"><span data-stu-id="c5209-113">**value**</span></span> | <span data-ttu-id="c5209-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c5209-114">Required attribute.</span></span><br><br><span data-ttu-id="c5209-115">Eklenecek anahtarın değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5209-115">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="c5209-116">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="c5209-116">Parent element</span></span>

|     | <span data-ttu-id="c5209-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5209-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c5209-118"> **\<appSettings >** </span><span class="sxs-lookup"><span data-stu-id="c5209-118">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="c5209-119">Dosya yolları, XML Web hizmeti URL 'Leri veya bir uygulama için başka özel yapılandırma bilgileri gibi özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="c5209-119">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="c5209-120">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="c5209-120">Child elements</span></span>

<span data-ttu-id="c5209-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="c5209-121">None</span></span>

## <a name="example"></a><span data-ttu-id="c5209-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="c5209-122">Example</span></span>

<span data-ttu-id="c5209-123">Aşağıdaki örnek, uygulamanın adı için nasıl özel bir yapılandırma ayarı ekleneceğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="c5209-123">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

<span data-ttu-id="c5209-124">Aşağıdaki örnek, bir ASP.NET uygulamasında iki uyumluluk ayarı tanımlamak için `<add>` öğesini kullanır:</span><span class="sxs-lookup"><span data-stu-id="c5209-124">The following example uses the `<add>` element to define two compatibility settings in an ASP.NET application:</span></span>

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="c5209-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5209-125">See also</span></span>

- [<span data-ttu-id="c5209-126">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="c5209-126">Configuration file schema for the .NET Framework</span></span>](../index.md)
