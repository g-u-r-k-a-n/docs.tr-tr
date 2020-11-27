---
title: <Directives> Öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: 524c30872e218f6428491507bbfb4ca54b6061b1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251106"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="6ff56-102">\<Directives> Öğesi (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="6ff56-102">\<Directives> Element (.NET Native)</span></span>

<span data-ttu-id="6ff56-103">.NET Native için her çalışma zamanı yönergeleri dosyasında kök öğe.</span><span class="sxs-lookup"><span data-stu-id="6ff56-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">`
  
## <a name="syntax"></a><span data-ttu-id="6ff56-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="6ff56-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="6ff56-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6ff56-105">Attributes</span></span>  
  
|<span data-ttu-id="6ff56-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6ff56-106">Attribute</span></span>|<span data-ttu-id="6ff56-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6ff56-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="6ff56-108">XML ad alanı.</span><span class="sxs-lookup"><span data-stu-id="6ff56-108">The XML namespace.</span></span> <span data-ttu-id="6ff56-109">Değeri her zaman `http://schemas.microsoft.com/netfx/2013/01/metadata` .</span><span class="sxs-lookup"><span data-stu-id="6ff56-109">Its value is always `http://schemas.microsoft.com/netfx/2013/01/metadata`.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="6ff56-110">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="6ff56-110">Child elements</span></span>  
  
|<span data-ttu-id="6ff56-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="6ff56-111">Element</span></span>|<span data-ttu-id="6ff56-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6ff56-112">Description</span></span>|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|<span data-ttu-id="6ff56-113">Uygulama genelinde türler için bir kapsayıcı görevi görür ve meta verileri yansıma için kullanılabilen tür üyeleri.</span><span class="sxs-lookup"><span data-stu-id="6ff56-113">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[\<Library>](library-element-net-native.md)|<span data-ttu-id="6ff56-114">Alt türleri ve tür üyeleri çalışma zamanında meta veri gerektiren derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6ff56-114">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ff56-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6ff56-115">Remarks</span></span>  

 <span data-ttu-id="6ff56-116">Her çalışma zamanı yönergeleri dosyası yalnızca bir `<Directives>` öğe içerebilir.</span><span class="sxs-lookup"><span data-stu-id="6ff56-116">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="6ff56-117">`<Directives>`Öğesi sıfır veya bir [\<Application>](application-element-net-native.md) öğe, sıfır, bir veya daha fazla öğe içerebilir [\<Library>](library-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="6ff56-117">The `<Directives>` element can contain zero or one [\<Application>](application-element-net-native.md) element, and zero, one, or more [\<Library>](library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ff56-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ff56-118">See also</span></span>

- [<span data-ttu-id="6ff56-119">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6ff56-119">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="6ff56-120">Çalışma Zamanı Yönerge Öğeleri</span><span class="sxs-lookup"><span data-stu-id="6ff56-120">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
