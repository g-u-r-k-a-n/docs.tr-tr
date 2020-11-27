---
title: 'Nasıl yapılır: Uygulama için Konum Temelli Önbellek İlkesi Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- explicitly defining cache behavior
- location-based cache policies
- local cache
- request cache policies
- cache [.NET Framework], location-based policies
ms.assetid: 683bb88e-3411-4f46-9686-3411b6ba511c
ms.openlocfilehash: 7331845c391265d72d3025fd9bf7856d83c783e9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253498"
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="b6440-102">Nasıl yapılır: Uygulama için Konum Temelli Önbellek İlkesi Ayarlama</span><span class="sxs-lookup"><span data-stu-id="b6440-102">How to: Set a Location-Based Cache Policy for an Application</span></span>

<span data-ttu-id="b6440-103">Konum tabanlı önbellek ilkeleri, bir uygulamanın, istenen kaynağın konumuna göre önbelleğe alma davranışını açıkça tanımlamasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b6440-103">Location-based cache policies allow an application to explicitly define caching behavior based on the location of the requested resource.</span></span> <span data-ttu-id="b6440-104">Bu konuda, önbellek ilkesinin programlı olarak ayarlanması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b6440-104">This topic demonstrates setting the cache policy programmatically.</span></span> <span data-ttu-id="b6440-105">Yapılandırma dosyalarını kullanarak bir uygulama için ilke ayarlama hakkında daha fazla bilgi için bkz. [ \<requestCaching> öğesi (ağ ayarları)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="b6440-105">For information on setting the policy for an application using the configuration files, see [\<requestCaching> Element (Network Settings)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span></span>  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="b6440-106">Bir uygulama için konum tabanlı önbellek ilkesi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b6440-106">To set a location-based cache policy for an application</span></span>  
  
1. <span data-ttu-id="b6440-107">Bir <xref:System.Net.Cache.RequestCachePolicy> veya <xref:System.Net.Cache.HttpRequestCachePolicy> nesnesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b6440-107">Create a <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> object.</span></span>  
  
2. <span data-ttu-id="b6440-108">İlke nesnesini, uygulama etki alanı için varsayılan olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b6440-108">Set the policy object as the default for the application domain.</span></span>  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a><span data-ttu-id="b6440-109">Bir önbellekten istenen kaynakları alan bir ilke ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b6440-109">To set a policy that takes requested resources from a cache</span></span>  
  
- <span data-ttu-id="b6440-110">Varsa, bir önbellekten istenen kaynakları alan bir ilke oluşturun ve aksi takdirde, önbellek düzeyini olarak ayarlayarak sunucuya istek gönderir <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable> .</span><span class="sxs-lookup"><span data-stu-id="b6440-110">Create a policy that takes requested resources from a cache if available, and otherwise, sends requests to the server, by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span></span> <span data-ttu-id="b6440-111">İstek, uzak önbellekler dahil olmak üzere istemci ve sunucu arasındaki herhangi bir önbellekte yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b6440-111">A request can be fulfilled by any cache between the client and server, including remote caches.</span></span>  
  
    ```csharp  
    public static void UseCacheIfAvailable()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
            (HttpRequestCacheLevel.CacheIfAvailable);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub UseCacheIfAvailable()  
        Dim policy As New HttpRequestCachePolicy _  
             (HttpRequestCacheLevel.CacheIfAvailable)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a><span data-ttu-id="b6440-112">Herhangi bir önbelleğin kaynakları almasını önleyen bir ilke ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b6440-112">To set a policy that prevents any cache from supplying resources</span></span>  
  
- <span data-ttu-id="b6440-113">Önbellek düzeyini olarak ayarlayarak herhangi bir önbelleğin istenen kaynakları almasını önleyen bir ilke oluşturun <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore> .</span><span class="sxs-lookup"><span data-stu-id="b6440-113">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span></span> <span data-ttu-id="b6440-114">Bu ilke düzeyi, varsa kaynağı yerel önbellekten kaldırır ve ayrıca uzak önbelleklerin kaynağı kaldırması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6440-114">This policy level removes the resource from the local cache if it is present and indicates to remote caches that they should also remove the resource.</span></span>  
  
    ```csharp  
    public static void DoNotUseCache()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.NoCacheNoStore);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.NoCacheNoStore)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a><span data-ttu-id="b6440-115">Yalnızca yerel önbellekte olduklarında, istenen kaynakları döndüren bir ilke ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b6440-115">To set a policy that returns requested resources only if they are in the local cache</span></span>  
  
- <span data-ttu-id="b6440-116">İstenen kaynakları, yalnızca önbellek düzeyini olarak ayarlayarak yerel önbellekte olduklarında döndüren bir ilke oluşturun <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly> .</span><span class="sxs-lookup"><span data-stu-id="b6440-116">Create a policy that returns requested resources only if they are in the local cache by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span></span> <span data-ttu-id="b6440-117">İstenen kaynak önbellekte değilse, bir <xref:System.Net.WebException> özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b6440-117">If the requested resource is not in the cache, a <xref:System.Net.WebException> exception is thrown.</span></span>  
  
    ```csharp  
    public static void OnlyUseCache()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.CacheOnly);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub OnlyUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.CacheOnly)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a><span data-ttu-id="b6440-118">Yerel önbelleğin kaynakları almasını önleyen bir ilke ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b6440-118">To set a policy that prevents the local cache from supplying resources</span></span>  
  
- <span data-ttu-id="b6440-119">Önbellek düzeyini olarak ayarlayarak yerel önbelleğin istenen kaynakları almasını önleyen bir ilke oluşturun <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh> .</span><span class="sxs-lookup"><span data-stu-id="b6440-119">Create a policy that prevents the local cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span></span> <span data-ttu-id="b6440-120">İstenen kaynak bir ara önbellekte ise ve başarıyla yeniden doğrulandıktan sonra, ara önbellek istenen kaynağı sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="b6440-120">If the requested resource is in an intermediate cache and is successfully revalidated, the intermediate cache can supply the requested resource.</span></span>  
  
    ```csharp  
    public static void DoNotUseLocalCache()  
    {  
     HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.Refresh);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseLocalCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Refresh)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a><span data-ttu-id="b6440-121">Herhangi bir önbelleğin istenen kaynakları almasını önleyen bir ilke ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b6440-121">To set a policy that prevents any cache from supplying requested resources</span></span>  
  
- <span data-ttu-id="b6440-122">Önbellek düzeyini olarak ayarlayarak herhangi bir önbelleğin istenen kaynakları almasını önleyen bir ilke oluşturun <xref:System.Net.Cache.HttpRequestCacheLevel.Reload> .</span><span class="sxs-lookup"><span data-stu-id="b6440-122">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span></span> <span data-ttu-id="b6440-123">Sunucu tarafından döndürülen kaynak önbellekte depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="b6440-123">The resource returned by the server can be stored in the cache.</span></span>  
  
    ```csharp  
    public static void SendToServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.Reload);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub SendToServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Reload)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a><span data-ttu-id="b6440-124">Sunucudaki kaynak önbelleğe alınmış kopyadan daha yeni değilse, herhangi bir önbelleğin istenen kaynakları sağlamasına izin veren bir ilke ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b6440-124">To set a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy</span></span>  
  
- <span data-ttu-id="b6440-125">Sunucudaki kaynak önbellek düzeyini olarak ayarlayarak, sunucudaki kaynağın önbelleğe alınmış kopyadan daha yeni olmaması durumunda, istenen kaynakları sağlamasına izin veren bir ilke oluşturun <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate> .</span><span class="sxs-lookup"><span data-stu-id="b6440-125">Create a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span></span>  
  
    ```csharp  
    public static void CheckServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
             (HttpRequestCacheLevel.Revalidate);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub CheckServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Revalidate)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b6440-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6440-126">See also</span></span>

- [<span data-ttu-id="b6440-127">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="b6440-127">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="b6440-128">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="b6440-128">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="b6440-129">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="b6440-129">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="b6440-130">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="b6440-130">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="b6440-131">\<requestCaching> Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="b6440-131">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
