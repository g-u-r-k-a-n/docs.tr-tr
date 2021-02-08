---
description: 'İçin: öğesi hakkında daha fazla bilgi <appSettings><configuration>'
title: <configuration> için <appSettings> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
ms.openlocfilehash: 74a25bb0dffd97057cda45575745b6f51ad2a675
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802495"
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="282de-103">\<configuration> için \<appSettings> öğesi</span><span class="sxs-lookup"><span data-stu-id="282de-103">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="282de-104">Özel uygulama ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="282de-104">Contains custom application settings.</span></span> <span data-ttu-id="282de-105">Bu, .NET Framework tarafından sunulan önceden tanımlanmış bir yapılandırma bölümüdür.</span><span class="sxs-lookup"><span data-stu-id="282de-105">This is a predefined configuration section provided by the .NET Framework.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<appSettings>**

## <a name="syntax"></a><span data-ttu-id="282de-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="282de-106">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="282de-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="282de-107">Attribute</span></span>

|           | <span data-ttu-id="282de-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="282de-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="282de-109">**dosyasýný**</span><span class="sxs-lookup"><span data-stu-id="282de-109">**file**</span></span>  | <span data-ttu-id="282de-110">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="282de-110">Optional attribute.</span></span><br><br><span data-ttu-id="282de-111">Özel uygulama yapılandırma ayarlarını içeren bir dış dosyanın göreli yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="282de-111">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="282de-112">Belirtilen dosya,, ve öğelerinde belirtilen tür ayarları içerir **\<add>** **\<remove>** **\<clear>** ve bu öğelerle aynı anahtar/değer çifti biçimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="282de-112">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="282de-113">Belirtilen yol, ana yapılandırma dosyasına göredir.</span><span class="sxs-lookup"><span data-stu-id="282de-113">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="282de-114">Windows Forms bir uygulama için, bu, uygulama yapılandırma dosyasının konumunu değil, ikili klasördür (örneğin, */bin/Debug*).</span><span class="sxs-lookup"><span data-stu-id="282de-114">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="282de-115">Web Forms uygulamalar için yol, *web.config* dosyasının bulunduğu uygulama köküne göredir.</span><span class="sxs-lookup"><span data-stu-id="282de-115">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="282de-116">Belirtilen dosya bulunamazsa çalışma zamanı özniteliği yoksayar.</span><span class="sxs-lookup"><span data-stu-id="282de-116">The runtime ignores the attribute if the specified file can't be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="282de-117">Üst öğe</span><span class="sxs-lookup"><span data-stu-id="282de-117">Parent element</span></span>

|     | <span data-ttu-id="282de-118">Description</span><span class="sxs-lookup"><span data-stu-id="282de-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="282de-119">**\<configuration>** Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="282de-119">**\<configuration>** Element</span></span>](../configuration-element.md) | <span data-ttu-id="282de-120">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="282de-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="282de-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="282de-121">Child elements</span></span>

|     | <span data-ttu-id="282de-122">Description</span><span class="sxs-lookup"><span data-stu-id="282de-122">Description</span></span> |
| --- | ----------- |
| [**\<add>**](add-element-for-appsettings.md) | <span data-ttu-id="282de-123">Özel bir uygulama ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="282de-123">Adds a custom application setting.</span></span> |
| [**\<clear>**](clear-element-for-appsettings.md) | <span data-ttu-id="282de-124">Önceden tanımlanmış tüm uygulama ayarlarını temizler.</span><span class="sxs-lookup"><span data-stu-id="282de-124">Clears all previously defined application settings.</span></span> |
| [**\<remove>**](remove-element-for-appsettings.md) | <span data-ttu-id="282de-125">Önceden tanımlanmış bir uygulama ayarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="282de-125">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="282de-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="282de-126">Remarks</span></span>

<span data-ttu-id="282de-127">**\<appSettings>** Öğesi, veritabanı bağlantı dizeleri, dosya yolları, XML Web hizmeti URL 'leri veya bir uygulama için başka özel yapılandırma bilgileri gibi özel uygulama yapılandırma bilgilerini depolar.</span><span class="sxs-lookup"><span data-stu-id="282de-127">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="282de-128">Öğesinde belirtilen anahtar/değer çiftlerine **\<appSettings>** sınıfı kullanılarak kodda erişilir <xref:System.Configuration.ConfigurationSettings> .</span><span class="sxs-lookup"><span data-stu-id="282de-128">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="282de-129"> **\<appSettings>** *Web.config* ve uygulama yapılandırma dosyalarının öğesinde dosya özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="282de-129">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="282de-130">Bu öznitelik, ek ayarlar sağlayan veya öğesinde belirtilen ayarları geçersiz kılan bir yapılandırma dosyasını belirtir **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="282de-130">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="282de-131">**Dosya** özniteliği, bir Kullanıcı bir uygulama yapılandırma dosyasında belirtilen proje ayarlarını geçersiz kılmak istediğinde olduğu gibi, kaynak denetimi takım geliştirme senaryolarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="282de-131">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="282de-132">**Dosya** özniteliği tarafından belirtilen yapılandırma dosyaları yerine kök düğümüne sahip olmalıdır **\<appSettings>** **\<configuration>** .</span><span class="sxs-lookup"><span data-stu-id="282de-132">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="282de-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="282de-133">Example</span></span>

<span data-ttu-id="282de-134">Aşağıdaki örnek, bir özel uygulama ayarı tanımlayan bir dış uygulama ayarları dosyası (*custom.config*) göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="282de-134">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="282de-135">Aşağıdaki örnek, dış ayarlar dosyasında ayarı tüketen ve kendi uygulama ayarını ayarlayan bir uygulama yapılandırma dosyasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="282de-135">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="282de-136">Yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="282de-136">Configuration file</span></span>

<span data-ttu-id="282de-137">Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine.config*) ve uygulama dizini düzeyinde olmayan *Web.config* dosyalarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="282de-137">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="282de-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="282de-138">See also</span></span>

- [<span data-ttu-id="282de-139">.NET Framework için yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="282de-139">Configuration file schema for the .NET Framework</span></span>](../index.md)
