---
title: 'Risk azaltma: havuz engelleme süresi'
ms.date: 03/30/2017
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
ms.openlocfilehash: 98396d4254975d1806a8477cbcd2380cb52ceaf3
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457850"
---
# <a name="mitigation-pool-blocking-period"></a><span data-ttu-id="0cd2d-102">Risk azaltma: havuz engelleme süresi</span><span class="sxs-lookup"><span data-stu-id="0cd2d-102">Mitigation: Pool Blocking Period</span></span>
<span data-ttu-id="0cd2d-103">Bağlantı havuzu engelleme süresi Azure SQL veritabanlarına bağlantılar için kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0cd2d-103">The connection pool blocking period has been removed for connections to Azure SQL databases.</span></span>  
  
## <a name="additional-description"></a><span data-ttu-id="0cd2d-104">Ek açıklama</span><span class="sxs-lookup"><span data-stu-id="0cd2d-104">Additional description</span></span>  
 <span data-ttu-id="0cd2d-105">.NET Framework 4.6.1 ve önceki sürümlerde, bir uygulama bir veritabanına bağlanırken geçici bir bağlantı hatasıyla karşılaştığında bağlantı girişimi hızlı bir şekilde yeniden denenemez, çünkü bağlantı havuzu hatayı önbelleğe alır ve 5 saniye ile 1 ' e yeniden atar Min. Daha fazla bilgi için bkz. [SQL Server bağlantı havuzu (ADO.net)](../data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="0cd2d-105">In the .NET Framework 4.6.1 and earlier versions, when an app encounters a transient connection failure when connecting to a database, the connection attempt cannot be retried quickly, because the connection pool caches the error and re-throws it for 5 seconds to 1 min. For more information, see [SQL Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).</span></span> <span data-ttu-id="0cd2d-106">Bu davranış, genellikle birkaç saniye içinde kurtarılan geçici hatalarla başarısız olan Azure SQL veritabanlarına bağlantı için sorunlu olur.</span><span class="sxs-lookup"><span data-stu-id="0cd2d-106">This behavior is problematic for connections to Azure SQL databases, which often fail with transient errors that are typically recovered from within a few seconds.</span></span> <span data-ttu-id="0cd2d-107">Bağlantı havuzu engelleme özelliği, uygulamanın veritabanı kullanılabilir olsa bile kapsamlı bir süre için veritabanına bağlanamamasıdır.</span><span class="sxs-lookup"><span data-stu-id="0cd2d-107">The connection pool blocking feature means that the app cannot connect to the database for an extensive period, even though the database is available.</span></span> <span data-ttu-id="0cd2d-108">Bu davranış, Azure SQL veritabanlarına bağlanan ve birkaç saniye içinde işlenmesi gereken Web uygulamaları için özellikle sorunlu olur.</span><span class="sxs-lookup"><span data-stu-id="0cd2d-108">This behavior is particularly problematic for web apps that connect to Azure SQL databases and that need to render within a few seconds.</span></span>  
  
 <span data-ttu-id="0cd2d-109">.NET Framework 4.6.2 ile başlayarak, bilinen Azure SQL veritabanlarına yönelik bağlantı açık istekleri (\*. database.windows.net, \*. database.chinacloudapi.cn, \*. database.usgovcloudapi.net, \*. database.cloudapi.de), bağlantı Açık hatalar önbelleğe alınmaz.</span><span class="sxs-lookup"><span data-stu-id="0cd2d-109">Starting with the .NET Framework 4.6.2, for connection open requests to known Azure SQL databases (\*.database.windows.net, \*.database.chinacloudapi.cn, \*.database.usgovcloudapi.net, \*.database.cloudapi.de), connection open errors are not cached.</span></span> <span data-ttu-id="0cd2d-110">Diğer tüm bağlantı girişimleri için, bağlantı havuzu engelleme süresi zorlanmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="0cd2d-110">For all other connection attempts, the connection pool blocking period continues to be enforced.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="0cd2d-111">Etki</span><span class="sxs-lookup"><span data-stu-id="0cd2d-111">Impact</span></span>  
 <span data-ttu-id="0cd2d-112">Bu değişiklik, bağlantı açma denemesinin Azure SQL veritabanları için hemen yeniden denenmeye olanak tanır ve böylece bulut özellikli uygulamaların performansını geliştirir.</span><span class="sxs-lookup"><span data-stu-id="0cd2d-112">This change allows the connection open attempt to be retried immediately for Azure SQL databases, thereby improving the performance of cloud-enabled apps.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="0cd2d-113">Azaltma</span><span class="sxs-lookup"><span data-stu-id="0cd2d-113">Mitigation</span></span>  
 <span data-ttu-id="0cd2d-114">Bu değişiklikten olumsuz etkilenen uygulamalar için, bağlantı havuzu engelleme süresi yeni <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> özelliği ayarlanarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="0cd2d-114">For apps that are adversely affected by this change, the connection pool blocking period can be configured by setting the new <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="0cd2d-115">Özelliğinin değeri, üç değerden birini alan <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> numaralandırmanın bir üyesidir:</span><span class="sxs-lookup"><span data-stu-id="0cd2d-115">The value of the property is a member of the <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> enumeration that can take either of three values:</span></span>  
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.Auto?displayProperty=nameWithType>
  
- <xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock?displayProperty=nameWithType>
  
 <span data-ttu-id="0cd2d-116">Önceki davranış <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> özelliği <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>olarak ayarlanarak geri yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="0cd2d-116">The previous behavior can be restored by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> property to <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cd2d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cd2d-117">See also</span></span>

- [<span data-ttu-id="0cd2d-118">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="0cd2d-118">Application compatibility</span></span>](application-compatibility.md)
