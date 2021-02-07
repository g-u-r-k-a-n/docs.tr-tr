---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir uygulama için Location-Based önbellek Ilkesi ayarlama'
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
ms.openlocfilehash: d86e40e24eacb6ce3107e50213941c1169191943
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662786"
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a>Nasıl yapılır: Uygulama için Konum Temelli Önbellek İlkesi Ayarlama

Konum tabanlı önbellek ilkeleri, bir uygulamanın, istenen kaynağın konumuna göre önbelleğe alma davranışını açıkça tanımlamasına olanak tanır. Bu konuda, önbellek ilkesinin programlı olarak ayarlanması gösterilmektedir. Yapılandırma dosyalarını kullanarak bir uygulama için ilke ayarlama hakkında daha fazla bilgi için bkz. [ \<requestCaching> öğesi (ağ ayarları)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a>Bir uygulama için konum tabanlı önbellek ilkesi ayarlamak için  
  
1. Bir <xref:System.Net.Cache.RequestCachePolicy> veya <xref:System.Net.Cache.HttpRequestCachePolicy> nesnesi oluşturun.  
  
2. İlke nesnesini, uygulama etki alanı için varsayılan olarak ayarlayın.  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a>Bir önbellekten istenen kaynakları alan bir ilke ayarlamak için  
  
- Varsa, bir önbellekten istenen kaynakları alan bir ilke oluşturun ve aksi takdirde, önbellek düzeyini olarak ayarlayarak sunucuya istek gönderir <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable> . İstek, uzak önbellekler dahil olmak üzere istemci ve sunucu arasındaki herhangi bir önbellekte yerine kullanılabilir.  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a>Herhangi bir önbelleğin kaynakları almasını önleyen bir ilke ayarlamak için  
  
- Önbellek düzeyini olarak ayarlayarak herhangi bir önbelleğin istenen kaynakları almasını önleyen bir ilke oluşturun <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore> . Bu ilke düzeyi, varsa kaynağı yerel önbellekten kaldırır ve ayrıca uzak önbelleklerin kaynağı kaldırması gerektiğini gösterir.  
  
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
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a>Yalnızca yerel önbellekte olduklarında, istenen kaynakları döndüren bir ilke ayarlamak için  
  
- İstenen kaynakları, yalnızca önbellek düzeyini olarak ayarlayarak yerel önbellekte olduklarında döndüren bir ilke oluşturun <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly> . İstenen kaynak önbellekte değilse, bir <xref:System.Net.WebException> özel durum oluşturulur.  
  
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
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a>Yerel önbelleğin kaynakları almasını önleyen bir ilke ayarlamak için  
  
- Önbellek düzeyini olarak ayarlayarak yerel önbelleğin istenen kaynakları almasını önleyen bir ilke oluşturun <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh> . İstenen kaynak bir ara önbellekte ise ve başarıyla yeniden doğrulandıktan sonra, ara önbellek istenen kaynağı sağlayabilir.  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a>Herhangi bir önbelleğin istenen kaynakları almasını önleyen bir ilke ayarlamak için  
  
- Önbellek düzeyini olarak ayarlayarak herhangi bir önbelleğin istenen kaynakları almasını önleyen bir ilke oluşturun <xref:System.Net.Cache.HttpRequestCacheLevel.Reload> . Sunucu tarafından döndürülen kaynak önbellekte depolanabilir.  
  
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
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a>Sunucudaki kaynak önbelleğe alınmış kopyadan daha yeni değilse, herhangi bir önbelleğin istenen kaynakları sağlamasına izin veren bir ilke ayarlamak için  
  
- Sunucudaki kaynak önbellek düzeyini olarak ayarlayarak, sunucudaki kaynağın önbelleğe alınmış kopyadan daha yeni olmaması durumunda, istenen kaynakları sağlamasına izin veren bir ilke oluşturun <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate> .  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Uygulamaları için Önbellek Yönetimi](cache-management-for-network-applications.md)
- [Önbellek İlkesi](cache-policy.md)
- [Konum Temelli Önbellek İlkeleri](location-based-cache-policies.md)
- [Saat Temelli Önbellek İlkeleri](time-based-cache-policies.md)
- [\<requestCaching> Öğesi (ağ ayarları)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
