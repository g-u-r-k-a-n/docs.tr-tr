---
title: SQL Server için Sağlayıcı İstatistikleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: 5e37a04ff731a99664d636e0d4175f99214c2646
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174517"
---
# <a name="provider-statistics-for-sql-server"></a><span data-ttu-id="3b29d-102">SQL Server için Sağlayıcı İstatistikleri</span><span class="sxs-lookup"><span data-stu-id="3b29d-102">Provider Statistics for SQL Server</span></span>
<span data-ttu-id="3b29d-103">.NET Framework sürüm 2.0 ile başlayarak, SQL Server için .NET Framework Data Provider çalışma zamanı istatistiklerini destekler.</span><span class="sxs-lookup"><span data-stu-id="3b29d-103">Starting with the .NET Framework version 2.0, the .NET Framework Data Provider for SQL Server supports run-time statistics.</span></span> <span data-ttu-id="3b29d-104">Oluşturulan geçerli bir bağlantı <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> nesnesi sonra <xref:System.Data.SqlClient.SqlConnection> nesnenin `True` özelliğini ayarlayarak istatistikleri etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3b29d-104">You must enable statistics by setting the <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object to `True` after you have a valid connection object created.</span></span> <span data-ttu-id="3b29d-105">İstatistikler etkinleştirildikten sonra, <xref:System.Collections.IDictionary> <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> <xref:System.Data.SqlClient.SqlConnection> nesnenin yöntemi yle bir başvuru alarak bunları "zaman içinde anlık görüntü" olarak gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b29d-105">After statistics are enabled, you can review them as a "snapshot in time" by retrieving an <xref:System.Collections.IDictionary> reference via the <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="3b29d-106">Listeyi ad/değer çifti sözlük girişleri kümesi olarak sıralarsınız.</span><span class="sxs-lookup"><span data-stu-id="3b29d-106">You enumerate through the list as a set of name/value pair dictionary entries.</span></span> <span data-ttu-id="3b29d-107">Bu ad/değer çiftleri sırasız.</span><span class="sxs-lookup"><span data-stu-id="3b29d-107">These name/value pairs are unordered.</span></span> <span data-ttu-id="3b29d-108">İstediğiniz zaman, sayaçları <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> sıfırlamak <xref:System.Data.SqlClient.SqlConnection> için nesnenin yöntemini arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b29d-108">At any time, you can call the <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object to reset the counters.</span></span> <span data-ttu-id="3b29d-109">İstatistik toplama etkinleştirilemediyse, bir özel durum oluşturulmadı.</span><span class="sxs-lookup"><span data-stu-id="3b29d-109">If statistic gathering has not been enabled, an exception is not generated.</span></span> <span data-ttu-id="3b29d-110">Ayrıca, önce <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> çağrılmadan <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> çağrılırsa, alınan değerler her giriş için başlangıç değerleridir.</span><span class="sxs-lookup"><span data-stu-id="3b29d-110">In addition, if <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> is called without <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> having been called first, the values retrieved are the initial values for each entry.</span></span> <span data-ttu-id="3b29d-111">İstatistikleri etkinleştiriseniz, uygulamanızı bir süre çalıştırır ve istatistikleri devre dışı bıraktığınızda, alınan değerler toplanan değerleri istatistiklerin devre dışı bırakıldığı noktaya kadar yansıtır.</span><span class="sxs-lookup"><span data-stu-id="3b29d-111">If you enable statistics, run your application for a while, and then disable statistics, the values retrieved will reflect the values collected up to the point where statistics were disabled.</span></span> <span data-ttu-id="3b29d-112">Toplanan tüm istatistiksel değerler bağlantı başına ayrı ayrıdır.</span><span class="sxs-lookup"><span data-stu-id="3b29d-112">All statistical values gathered are on a per-connection basis.</span></span>  
  
## <a name="statistical-values-available"></a><span data-ttu-id="3b29d-113">Mevcut İstatistiksel Değerler</span><span class="sxs-lookup"><span data-stu-id="3b29d-113">Statistical Values Available</span></span>  
 <span data-ttu-id="3b29d-114">Şu anda Microsoft SQL Server sağlayıcısından 18 farklı öğe mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="3b29d-114">Currently there are 18 different items available from the Microsoft SQL Server provider.</span></span> <span data-ttu-id="3b29d-115">Kullanılabilir öğelerin sayısı, '' tarafından <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>döndürülen <xref:System.Collections.IDictionary> arabirim referansının **Count** özelliği üzerinden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="3b29d-115">The number of items available can be accessed via the **Count** property of the <xref:System.Collections.IDictionary> interface reference returned by <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span></span> <span data-ttu-id="3b29d-116">Sağlayıcı istatistikleri için tüm sayaçlar, 64 <xref:System.Int64> bit genişliğinde olan ortak dil çalışma zamanı türünü (C# ve Visual Basic'te**uzun)** kullanır.</span><span class="sxs-lookup"><span data-stu-id="3b29d-116">All of the counters for provider statistics use the common language runtime <xref:System.Int64> type (**long** in C# and Visual Basic), which is 64 bits wide.</span></span> <span data-ttu-id="3b29d-117">**int64** tarafından tanımlanan int64 veri türünün maksimum **değeri. MaxValue** alanı, ((2^63)-1)).</span><span class="sxs-lookup"><span data-stu-id="3b29d-117">The maximum value of the **int64** data type, as defined by the **int64.MaxValue** field, is ((2^63)-1)).</span></span> <span data-ttu-id="3b29d-118">Sayaçların değerleri bu maksimum değere ulaştığında, artık doğru olarak kabul edilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="3b29d-118">When the values for the counters reach this maximum value, they should no longer be considered accurate.</span></span> <span data-ttu-id="3b29d-119">Bu **int64 anlamına gelir. MaxValue**-1((2^63)-2) herhangi bir istatistik için etkili bir şekilde en büyük geçerli değerdir.</span><span class="sxs-lookup"><span data-stu-id="3b29d-119">This means that **int64.MaxValue**-1((2^63)-2) is effectively the greatest valid value for any statistic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3b29d-120">Döndürülen istatistiklerin sayısı, adları ve sırası gelecekte değişebileceğinden, sağlayıcı istatistiklerini döndürmek için sözlük kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3b29d-120">A dictionary is used for returning provider statistics because the number, names and order of the returned statistics may change in the future.</span></span> <span data-ttu-id="3b29d-121">Uygulamalar sözlükte bulunan belirli bir değere dayanmamalı, bunun yerine değerin var olup olmadığını ve buna göre dallanıp dallanmadığını kontrol etmelidir.</span><span class="sxs-lookup"><span data-stu-id="3b29d-121">Applications should not rely on a specific value being found in the dictionary, but should instead check whether the value is there and branch accordingly.</span></span>  
  
 <span data-ttu-id="3b29d-122">Aşağıdaki tabloda mevcut istatistiksel değerler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3b29d-122">The following table describes the current statistical values available.</span></span> <span data-ttu-id="3b29d-123">Tek tek değerlerin anahtar adlarının Microsoft .NET Framework'ün bölgesel sürümlerinde yerelleştirilmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3b29d-123">Note that the key names for the individual values are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="3b29d-124">Anahtar Adı</span><span class="sxs-lookup"><span data-stu-id="3b29d-124">Key Name</span></span>|<span data-ttu-id="3b29d-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b29d-125">Description</span></span>|  
|--------------|-----------------|  
|`BuffersReceived`|<span data-ttu-id="3b29d-126">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra sağlayıcı tarafından SQL Server'dan alınan tabular veri akışı (TDS) paketlerinin sayısını verir.</span><span class="sxs-lookup"><span data-stu-id="3b29d-126">Returns the number of tabular data stream (TDS) packets received by the provider from SQL Server after the application has started using the provider and has enabled statistics.</span></span>|  
|`BuffersSent`|<span data-ttu-id="3b29d-127">İstatistikler etkinleştirildikten sonra sağlayıcı tarafından SQL Server'a gönderilen TDS paketlerinin sayısını verir.</span><span class="sxs-lookup"><span data-stu-id="3b29d-127">Returns the number of TDS packets sent to SQL Server by the provider after statistics have been enabled.</span></span> <span data-ttu-id="3b29d-128">Büyük komutlar birden çok arabellek gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="3b29d-128">Large commands can require multiple buffers.</span></span> <span data-ttu-id="3b29d-129">Örneğin, sunucuya büyük bir komut gönderilirse ve altı `ServerRoundtrips` paket gerektiriyorsa, `BuffersSent` bir komut uğruyla artımlanır ve altı ile artımlanır.</span><span class="sxs-lookup"><span data-stu-id="3b29d-129">For example, if a large command is sent to the server and it requires six packets, `ServerRoundtrips` is incremented by one and `BuffersSent` is incremented by six.</span></span>|  
|`BytesReceived`|<span data-ttu-id="3b29d-130">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra sağlayıcı tarafından SQL Server'dan alınan TDS paketlerindeki bayt veri sayısını verir.</span><span class="sxs-lookup"><span data-stu-id="3b29d-130">Returns the number of bytes of data in the TDS packets received by the provider from SQL Server once the application has started using the provider and has enabled statistics.</span></span>|  
|`BytesSent`|<span data-ttu-id="3b29d-131">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra TDS paketlerinde SQL Server'a gönderilen veri baytlarının sayısını verir.</span><span class="sxs-lookup"><span data-stu-id="3b29d-131">Returns the number of bytes of data sent to SQL Server in TDS packets after the application has started using the provider and has enabled statistics.</span></span>|  
|`ConnectionTime`|<span data-ttu-id="3b29d-132">İstatistikler etkinleştirildikten sonra bağlantının açıldığı süre (milisaniye cinsinden) (bağlantıyı açmadan önce istatistikler etkinleştirilmişse toplam bağlantı süresi).</span><span class="sxs-lookup"><span data-stu-id="3b29d-132">The amount of time (in milliseconds) that the connection has been opened after statistics have been enabled (total connection time if statistics were enabled before opening the connection).</span></span>|  
|`CursorOpens`|<span data-ttu-id="3b29d-133">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra imleç bağlantı üzerinden kaç kez açık olduğunu verir.</span><span class="sxs-lookup"><span data-stu-id="3b29d-133">Returns the number of times a cursor was open through the connection once the application has started using the provider and has enabled statistics.</span></span><br /><br /> <span data-ttu-id="3b29d-134">SELECT deyimleri tarafından döndürülen salt/forward sonuçlarının imleç olarak kabul edilmeyeceğini ve bu nedenle bu sayacı etkilemediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3b29d-134">Note that read-only/forward-only results returned by SELECT statements are not considered cursors and thus do not affect this counter.</span></span>|  
|`ExecutionTime`|<span data-ttu-id="3b29d-135">İstatistikler etkinleştirildikten sonra sağlayıcının işlemek için harcadığı kümülatif süreyi (milisaniye cinsinden) sunucudan gelen yanıtları beklerken harcanan süre ve sağlayıcının kendi içinde kodu yürütmek için harcanan süre de dahil olmak üzere döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b29d-135">Returns the cumulative amount of time (in milliseconds) that the provider has spent processing once statistics have been enabled, including the time spent waiting for replies from the server as well as the time spent executing code in the provider itself.</span></span><br /><br /> <span data-ttu-id="3b29d-136">Zamanlama kodu içeren sınıflar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3b29d-136">The classes that include timing code are:</span></span><br /><br /> <span data-ttu-id="3b29d-137">Sqlconnection</span><span class="sxs-lookup"><span data-stu-id="3b29d-137">SqlConnection</span></span><br /><br /> <span data-ttu-id="3b29d-138">Sqlcommand</span><span class="sxs-lookup"><span data-stu-id="3b29d-138">SqlCommand</span></span><br /><br /> <span data-ttu-id="3b29d-139">Sqldatareader</span><span class="sxs-lookup"><span data-stu-id="3b29d-139">SqlDataReader</span></span><br /><br /> <span data-ttu-id="3b29d-140">Sqldataadapter</span><span class="sxs-lookup"><span data-stu-id="3b29d-140">SqlDataAdapter</span></span><br /><br /> <span data-ttu-id="3b29d-141">Sqltransaction</span><span class="sxs-lookup"><span data-stu-id="3b29d-141">SqlTransaction</span></span><br /><br /> <span data-ttu-id="3b29d-142">Sqlcommandbuilder</span><span class="sxs-lookup"><span data-stu-id="3b29d-142">SqlCommandBuilder</span></span><br /><br /> <span data-ttu-id="3b29d-143">Performans açısından kritik üyeleri mümkün olduğunca küçük tutmak için aşağıdaki üyelere zaman landırılmaz:</span><span class="sxs-lookup"><span data-stu-id="3b29d-143">To keep performance-critical members as small as possible, the following members are not timed:</span></span><br /><br /> <span data-ttu-id="3b29d-144">Sqldatareader</span><span class="sxs-lookup"><span data-stu-id="3b29d-144">SqlDataReader</span></span><br /><br /> <span data-ttu-id="3b29d-145">bu[] işleci (tüm aşırı yüklemeler)</span><span class="sxs-lookup"><span data-stu-id="3b29d-145">this[] operator (all overloads)</span></span><br /><br /> <span data-ttu-id="3b29d-146">GetBoolean</span><span class="sxs-lookup"><span data-stu-id="3b29d-146">GetBoolean</span></span><br /><br /> <span data-ttu-id="3b29d-147">Getchar</span><span class="sxs-lookup"><span data-stu-id="3b29d-147">GetChar</span></span><br /><br /> <span data-ttu-id="3b29d-148">GetDateTime</span><span class="sxs-lookup"><span data-stu-id="3b29d-148">GetDateTime</span></span><br /><br /> <span data-ttu-id="3b29d-149">GetOncimal</span><span class="sxs-lookup"><span data-stu-id="3b29d-149">GetDecimal</span></span><br /><br /> <span data-ttu-id="3b29d-150">Getdouble</span><span class="sxs-lookup"><span data-stu-id="3b29d-150">GetDouble</span></span><br /><br /> <span data-ttu-id="3b29d-151">GetFloat</span><span class="sxs-lookup"><span data-stu-id="3b29d-151">GetFloat</span></span><br /><br /> <span data-ttu-id="3b29d-152">GetGuid</span><span class="sxs-lookup"><span data-stu-id="3b29d-152">GetGuid</span></span><br /><br /> <span data-ttu-id="3b29d-153">GetInt16</span><span class="sxs-lookup"><span data-stu-id="3b29d-153">GetInt16</span></span><br /><br /> <span data-ttu-id="3b29d-154">GetInt32</span><span class="sxs-lookup"><span data-stu-id="3b29d-154">GetInt32</span></span><br /><br /> <span data-ttu-id="3b29d-155">GetInt64</span><span class="sxs-lookup"><span data-stu-id="3b29d-155">GetInt64</span></span><br /><br /> <span data-ttu-id="3b29d-156">GetName</span><span class="sxs-lookup"><span data-stu-id="3b29d-156">GetName</span></span><br /><br /> <span data-ttu-id="3b29d-157">Getordinal</span><span class="sxs-lookup"><span data-stu-id="3b29d-157">GetOrdinal</span></span><br /><br /> <span data-ttu-id="3b29d-158">GetSqlBinary</span><span class="sxs-lookup"><span data-stu-id="3b29d-158">GetSqlBinary</span></span><br /><br /> <span data-ttu-id="3b29d-159">GetSqlBoolean</span><span class="sxs-lookup"><span data-stu-id="3b29d-159">GetSqlBoolean</span></span><br /><br /> <span data-ttu-id="3b29d-160">SqlByte'ı Alın</span><span class="sxs-lookup"><span data-stu-id="3b29d-160">GetSqlByte</span></span><br /><br /> <span data-ttu-id="3b29d-161">GetSqlDateTime</span><span class="sxs-lookup"><span data-stu-id="3b29d-161">GetSqlDateTime</span></span><br /><br /> <span data-ttu-id="3b29d-162">GetSqlDecimal</span><span class="sxs-lookup"><span data-stu-id="3b29d-162">GetSqlDecimal</span></span><br /><br /> <span data-ttu-id="3b29d-163">GetSqlDouble</span><span class="sxs-lookup"><span data-stu-id="3b29d-163">GetSqlDouble</span></span><br /><br /> <span data-ttu-id="3b29d-164">GetSqlGuid</span><span class="sxs-lookup"><span data-stu-id="3b29d-164">GetSqlGuid</span></span><br /><br /> <span data-ttu-id="3b29d-165">SqlInt16'yı alın</span><span class="sxs-lookup"><span data-stu-id="3b29d-165">GetSqlInt16</span></span><br /><br /> <span data-ttu-id="3b29d-166">SqlInt32'yi alın</span><span class="sxs-lookup"><span data-stu-id="3b29d-166">GetSqlInt32</span></span><br /><br /> <span data-ttu-id="3b29d-167">SqlInt64'i alın</span><span class="sxs-lookup"><span data-stu-id="3b29d-167">GetSqlInt64</span></span><br /><br /> <span data-ttu-id="3b29d-168">GetSqlMoney</span><span class="sxs-lookup"><span data-stu-id="3b29d-168">GetSqlMoney</span></span><br /><br /> <span data-ttu-id="3b29d-169">GetSqlSingle</span><span class="sxs-lookup"><span data-stu-id="3b29d-169">GetSqlSingle</span></span><br /><br /> <span data-ttu-id="3b29d-170">GetSqlString</span><span class="sxs-lookup"><span data-stu-id="3b29d-170">GetSqlString</span></span><br /><br /> <span data-ttu-id="3b29d-171">GetString</span><span class="sxs-lookup"><span data-stu-id="3b29d-171">GetString</span></span><br /><br /> <span data-ttu-id="3b29d-172">ısdbnull</span><span class="sxs-lookup"><span data-stu-id="3b29d-172">IsDBNull</span></span>|  
|`IduCount`|<span data-ttu-id="3b29d-173">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bağlantı üzerinden yürütülen INSERT, DELETE ve UPDATE deyimlerinin toplam sayısını verir.</span><span class="sxs-lookup"><span data-stu-id="3b29d-173">Returns the total number of INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`IduRows`|<span data-ttu-id="3b29d-174">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bağlantı üzerinden yürütülen INSERT, DELETE ve UPDATE deyimlerinden etkilenen toplam satır sayısını verir.</span><span class="sxs-lookup"><span data-stu-id="3b29d-174">Returns the total number of rows affected by INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`NetworkServerTime`|<span data-ttu-id="3b29d-175">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra sağlayıcının sunucudan gelen yanıtları beklemek için harcadığı kümülatif süreyi (milisaniye cinsinden) döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b29d-175">Returns the cumulative amount of time (in milliseconds) that the provider spent waiting for replies from the server once the application has started using the provider and has enabled statistics.</span></span>|  
|`PreparedExecs`|<span data-ttu-id="3b29d-176">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bağlantı üzerinden yürütülen hazırlanan komutların sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b29d-176">Returns the number of prepared commands executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`Prepares`|<span data-ttu-id="3b29d-177">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bağlantı üzerinden hazırlanan deyim sayısını verir.</span><span class="sxs-lookup"><span data-stu-id="3b29d-177">Returns the number of statements prepared through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`SelectCount`|<span data-ttu-id="3b29d-178">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bağlantı üzerinden yürütülen SELECT deyimlerinin sayısını verir.</span><span class="sxs-lookup"><span data-stu-id="3b29d-178">Returns the number of SELECT statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="3b29d-179">Bu imleçlerden satır almak için GETIR deyimleri içerir ve SELECT deyimleri için <xref:System.Data.SqlClient.SqlDataReader> sayı bir sonuna ulaşıldığında güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3b29d-179">This includes FETCH statements to retrieve rows from cursors, and the count for SELECT statements is updated when the end of a <xref:System.Data.SqlClient.SqlDataReader> is reached.</span></span>|  
|`SelectRows`|<span data-ttu-id="3b29d-180">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra seçilen satır sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b29d-180">Returns the number of rows selected once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="3b29d-181">Bu sayaç, SQL deyimleri tarafından oluşturulan tüm satırları, hatta arayan tarafından gerçekten tüketilemeyen satırları yansıtır.</span><span class="sxs-lookup"><span data-stu-id="3b29d-181">This counter reflects all the rows generated by SQL statements, even those that were not actually consumed by the caller.</span></span> <span data-ttu-id="3b29d-182">Örneğin, tüm sonuç kümesini okumadan önce bir veri okuyucuyu kapatmak sayımı etkilemez.</span><span class="sxs-lookup"><span data-stu-id="3b29d-182">For example, closing a data reader before reading the entire result set would not affect the count.</span></span> <span data-ttu-id="3b29d-183">Bu, imleçlerden FETCH deyimleri aracılığıyla alınan satırları içerir.</span><span class="sxs-lookup"><span data-stu-id="3b29d-183">This includes the rows retrieved from cursors through FETCH statements.</span></span>|  
|`ServerRoundtrips`|<span data-ttu-id="3b29d-184">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bağlantının komutları sunucuya kaç kez gönderdiğini ve yanıtını geri aldığı sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b29d-184">Returns the number of times the connection sent commands to the server and got a reply back once the application has started using the provider and has enabled statistics.</span></span>|  
|`SumResultSets`|<span data-ttu-id="3b29d-185">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra kullanılan sonuç kümelerinin sayısını verir.</span><span class="sxs-lookup"><span data-stu-id="3b29d-185">Returns the number of result sets that have been used once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="3b29d-186">Örneğin, bu istemciye döndürülen herhangi bir sonuç kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="3b29d-186">For example this would include any result set returned to the client.</span></span> <span data-ttu-id="3b29d-187">İmleçler için, her getirme veya engelleme işlemi bağımsız bir sonuç kümesi olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="3b29d-187">For cursors, each fetch or block-fetch operation is considered an independent result set.</span></span>|  
|`Transactions`|<span data-ttu-id="3b29d-188">Uygulama sağlayıcıyı kullanmaya başladıktan ve geri almalar da dahil olmak üzere istatistikleri etkinleştirdikten sonra başlatılan kullanıcı hareketleri sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b29d-188">Returns the number of user transactions started once the application has started using the provider and has enabled statistics, including rollbacks.</span></span> <span data-ttu-id="3b29d-189">Otomatik commit ile çalışan bir bağlantı varsa, her komut bir işlem olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="3b29d-189">If a connection is running with auto commit on, each command is considered a transaction.</span></span><br /><br /> <span data-ttu-id="3b29d-190">Bu sayaç, işlemin kaydedilip işlenmediğine veya daha sonra geri alınıp alınmayacağına bakılmaksızın, BEGIN TRAN deyimi yürütülür yürütülür çalıştırılmaz hareket sayısını da yukarıya doğru şarampole bırakır.</span><span class="sxs-lookup"><span data-stu-id="3b29d-190">This counter increments the transaction count as soon as a BEGIN TRAN statement is executed, regardless of whether the transaction is committed or rolled back later.</span></span>|  
|`UnpreparedExecs`|<span data-ttu-id="3b29d-191">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bağlantı üzerinden yürütülen hazırlıksız deyimlerin sayısını verir.</span><span class="sxs-lookup"><span data-stu-id="3b29d-191">Returns the number of unprepared statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
  
### <a name="retrieving-a-value"></a><span data-ttu-id="3b29d-192">Bir Değer Alma</span><span class="sxs-lookup"><span data-stu-id="3b29d-192">Retrieving a Value</span></span>  
 <span data-ttu-id="3b29d-193">Aşağıdaki konsol uygulaması, bir bağlantıdaki istatistikleri nasıl etkinleştireceklerini, dört ayrı istatistik değerini nasıl alsüreceğini ve bunları konsol penceresine nasıl yazarak yazacaklarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b29d-193">The following console application shows how to enable statistics on a connection, retrieve four individual statistic values, and write them out to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3b29d-194">Aşağıdaki örnek, SQL Server ile birlikte verilen örnek **AdventureWorks** veritabanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="3b29d-194">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="3b29d-195">Örnek kodda sağlanan bağlantı dizesi, veritabanının yüklenmiş ve yerel bilgisayarda kullanılabilir olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="3b29d-195">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="3b29d-196">Bağlantı dizesini ortamınız için gerektiği gibi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3b29d-196">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      ' Retrieve a few individual values  
      ' related to the previous command.  
      Dim bytesReceived As Long = _  
          CLng(currentStatistics.Item("BytesReceived"))  
      Dim bytesSent As Long = _  
          CLng(currentStatistics.Item("BytesSent"))  
      Dim selectCount As Long = _  
          CLng(currentStatistics.Item("SelectCount"))  
      Dim selectRows As Long = _  
          CLng(currentStatistics.Item("SelectRows"))  
  
      Console.WriteLine("BytesReceived: " & bytesReceived.ToString())  
      Console.WriteLine("BytesSent: " & bytesSent.ToString())  
      Console.WriteLine("SelectCount: " & selectCount.ToString())  
      Console.WriteLine("SelectRows: " & selectRows.ToString())  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetValue  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =
          new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
          awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
          currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        // Retrieve a few individual values  
        // related to the previous command.  
        long bytesReceived =  
            (long) currentStatistics["BytesReceived"];  
        long bytesSent =  
            (long) currentStatistics["BytesSent"];  
        long selectCount =  
            (long) currentStatistics["SelectCount"];  
        long selectRows =  
            (long) currentStatistics["SelectRows"];  
  
        Console.WriteLine("BytesReceived: " +  
            bytesReceived.ToString());  
        Console.WriteLine("BytesSent: " +  
            bytesSent.ToString());  
        Console.WriteLine("SelectCount: " +  
            selectCount.ToString());  
        Console.WriteLine("SelectRows: " +  
            selectRows.ToString());  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a><span data-ttu-id="3b29d-197">Tüm Değerleri Alma</span><span class="sxs-lookup"><span data-stu-id="3b29d-197">Retrieving All Values</span></span>  
 <span data-ttu-id="3b29d-198">Aşağıdaki konsol uygulaması, bir bağlantıdaki istatistikleri nasıl etkinleştireceklerini, kullanılabilir tüm istatistik değerlerini sayısallaştırıcıyı kullanarak nasıl alsüreceğini ve konsol penceresine nasıl yazarak yazacaklarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b29d-198">The following console application shows how to enable statistics on a connection, retrieve all available statistic values using the enumerator, and write them to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3b29d-199">Aşağıdaki örnek, SQL Server ile birlikte verilen örnek **AdventureWorks** veritabanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="3b29d-199">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="3b29d-200">Örnek kodda sağlanan bağlantı dizesi, veritabanının yüklenmiş ve yerel bilgisayarda kullanılabilir olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="3b29d-200">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="3b29d-201">Bağlantı dizesini ortamınız için gerektiği gibi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3b29d-201">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      Console.WriteLine("Key Name and Value")  
  
      ' Note the entries are unsorted.  
      For Each entry As DictionaryEntry In currentStatistics  
        Console.WriteLine(entry.Key.ToString() & _  
            ": " & entry.Value.ToString())  
      Next  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetAll  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =  
            new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
            awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
            currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        Console.WriteLine("Key Name and Value");  
  
        // Note the entries are unsorted.  
        foreach (DictionaryEntry entry in currentStatistics)  
        {  
          Console.WriteLine(entry.Key.ToString() +  
              ": " + entry.Value.ToString());  
        }  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b29d-202">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b29d-202">See also</span></span>

- [<span data-ttu-id="3b29d-203">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3b29d-203">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="3b29d-204">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3b29d-204">ADO.NET Overview</span></span>](../ado-net-overview.md)
