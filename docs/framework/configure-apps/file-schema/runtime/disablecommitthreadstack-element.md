---
title: <disableCommitThreadStack> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCommitThreadStack
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCommitThreadStack
helpviewer_keywords:
- <disableCommitThreadStack> element
- disableCommitThreadStack element
ms.assetid: 3559d46a-7640-4c72-9a11-7e980768929e
ms.openlocfilehash: f717f57fe8670b126ed1468713a2114aaa772762
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198996"
---
# <a name="disablecommitthreadstack-element"></a><span data-ttu-id="3bd03-102">\<disableCommitThreadStack> Öğesi</span><span class="sxs-lookup"><span data-stu-id="3bd03-102">\<disableCommitThreadStack> Element</span></span>

<span data-ttu-id="3bd03-103">Bir iş parçacığı başlatıldığında tam iş parçacığı yığınının uygulanıp uygulanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3bd03-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCommitThreadStack>**  
  
## <a name="syntax"></a><span data-ttu-id="3bd03-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="3bd03-104">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3bd03-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3bd03-105">Attributes and Elements</span></span>  

 <span data-ttu-id="3bd03-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3bd03-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3bd03-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3bd03-107">Attributes</span></span>  
  
|<span data-ttu-id="3bd03-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3bd03-108">Attribute</span></span>|<span data-ttu-id="3bd03-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3bd03-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3bd03-110">enabled</span><span class="sxs-lookup"><span data-stu-id="3bd03-110">enabled</span></span>|<span data-ttu-id="3bd03-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3bd03-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="3bd03-112">Tüm iş parçacığı yığınının iş parçacığı başlangıcında (varsayılan davranış) devre dışı bırakılıp bırakılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3bd03-112">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3bd03-113">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3bd03-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="3bd03-114">Değer</span><span class="sxs-lookup"><span data-stu-id="3bd03-114">Value</span></span>|<span data-ttu-id="3bd03-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3bd03-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3bd03-116">0</span><span class="sxs-lookup"><span data-stu-id="3bd03-116">0</span></span>|<span data-ttu-id="3bd03-117">Ortak dil çalışma zamanının varsayılan davranışını devre dışı bırakmayın, bu, bir iş parçacığı başlatıldığında tam iş parçacığı yığınını yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3bd03-117">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="3bd03-118">1</span><span class="sxs-lookup"><span data-stu-id="3bd03-118">1</span></span>|<span data-ttu-id="3bd03-119">Ortak dil çalışma zamanının varsayılan davranışını devre dışı bırakın, bu, bir iş parçacığı başlatıldığında tam iş parçacığı yığınını yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3bd03-119">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3bd03-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3bd03-120">Child Elements</span></span>  

 <span data-ttu-id="3bd03-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="3bd03-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3bd03-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3bd03-122">Parent Elements</span></span>  
  
|<span data-ttu-id="3bd03-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="3bd03-123">Element</span></span>|<span data-ttu-id="3bd03-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3bd03-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3bd03-125">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="3bd03-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3bd03-126">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="3bd03-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3bd03-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3bd03-127">Remarks</span></span>  

 <span data-ttu-id="3bd03-128">Ortak dil çalışma zamanının varsayılan davranışı, bir iş parçacığı başlatıldığında tam iş parçacığı yığınını yürütmeniz olur.</span><span class="sxs-lookup"><span data-stu-id="3bd03-128">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="3bd03-129">Sınırlı belleği olan bir sunucuda çok sayıda iş parçacığı oluşturulması gerekiyorsa ve bu iş parçacıklarının çoğu çok az yığın alanı kullanıyorsa, ortak dil çalışma zamanı, bir iş parçacığı başlatıldığında tam iş parçacığı yığınını hemen yürütmezse sunucu daha iyi çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="3bd03-129">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3bd03-130">Yönetilmeyen konaklar, `STARTUP_DISABLE_COMMITTHREADSTACK` [startup_flags](../../../unmanaged-api/hosting/startup-flags-enumeration.md) numaralandırmasında başlangıç bayrağını kullanarak aynı sonucu elde edebilir.</span><span class="sxs-lookup"><span data-stu-id="3bd03-130">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3bd03-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="3bd03-131">Example</span></span>  

 <span data-ttu-id="3bd03-132">Aşağıdaki örnek, ortak dil çalışma zamanının varsayılan davranışının devre dışı bırakılacağını gösterir. Bu, iş parçacığı başlangıcında tam iş parçacığı yığınını yürütmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3bd03-132">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3bd03-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3bd03-133">See also</span></span>

- [<span data-ttu-id="3bd03-134">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="3bd03-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3bd03-135">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="3bd03-135">Configuration File Schema</span></span>](../index.md)
