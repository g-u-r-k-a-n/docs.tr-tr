---
title: .NET 'teki iyi bilinen EventCounters
description: .NET çalışma zamanı ve kitaplıkları tarafından yayınlanan EventCounters 'i gözden geçirin.
ms.topic: reference
ms.date: 12/17/2020
ms.openlocfilehash: fc07ace22f1580d547c33b897bcd1bb9a1de15c3
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106496728"
---
# <a name="well-known-eventcounters-in-net"></a>.NET 'teki iyi bilinen EventCounters

.NET çalışma zamanı ve kitaplıkları, [`EventCounter`](./event-counters.md) çeşitli performans sorunlarını tanımlamak ve tanılamak için kullanılabilecek birkaç tane uygular ve yayımlar. Bu belge, sağlayıcıları ve açıklamalarını izlemek için kullanılabilecek bir başvurudur `EventCounters` .

## <a name="systemruntime-counters"></a>System. Runtime sayaçları

Aşağıdaki sayaçlar .NET çalışma zamanının (CoreCLR) bir parçası olarak yayımlanır ve içinde tutulur [`RuntimeEventSource.cs`](https://github.com/dotnet/runtime/blob/main/src/libraries/System.Private.CoreLib/src/System/Diagnostics/Tracing/RuntimeEventSource.cs) .

| Sayaç | Açıklama |
|--|--|
| :::no-loc text="% Time in GC since last GC"::: (`time-in-gc`) | Son GC 'den bu yana GC 'deki sürenin yüzdesi |
| :::no-loc text="Allocation Rate"::: (`alloc-rate`) | Her güncelleştirme aralığı için ayrılan bayt sayısı |
| :::no-loc text="CPU Usage"::: (`cpu-usage`) | İşlemin CPU kullanımının tüm sistem CPU kaynaklarıyla ilişkili yüzdesi |
| :::no-loc text="Exception Count"::: (`exception-count`) | Oluşan özel durumların sayısı |
| :::no-loc text="GC Heap Size"::: (`gc-heap-size`) | Temel alınarak ayrılan bayt sayısı <xref:System.GC.GetTotalMemory(System.Boolean)?displayProperty=nameWithType> |
| :::no-loc text="Gen 0 GC Count"::: (`gen-0-gc-count`) | Güncelleştirme aralığı başına Gen 0 için GC 'nin kaç kez gerçekleştiği |
| :::no-loc text="Gen 0 Size"::: (`gen-0-size`) | Gen 0 GC için bayt sayısı |
| :::no-loc text="Gen 1 GC Count"::: (`gen-1-gc-count`) | Her güncelleştirme aralığı için Gen 1 için GC oluşma sayısı |
| :::no-loc text="Gen 1 Size"::: (`gen-1-size`) | Gen 1 GC için bayt sayısı |
| :::no-loc text="Gen 2 GC Count"::: (`gen-2-gc-count`) | Her güncelleştirme aralığı için Gen 2 için GC 'nin kaç kez gerçekleştiği |
| :::no-loc text="Gen 2 Size"::: (`gen-2-size`) | Gen 2 GC için bayt sayısı |
| :::no-loc text="LOH Size"::: (`loh-size`) | Büyük nesne yığını için bayt sayısı |
| :::no-loc text="POH Size"::: (`poh-size`) | Sabitlenmiş nesne yığını için bayt sayısı (.NET 5 ve sonraki sürümlerinde kullanılabilir) |
| :::no-loc text="GC Fragmentation"::: (`gc-fragmentation`) | GC yığın parçalanması (.NET 5 ve sonraki sürümlerde kullanılabilir) |
| :::no-loc text="Monitor Lock Contention Count"::: (`monitor-lock-contention-count`) | Monitöre göre izleyicinin kilidini almaya çalışırken çekişmenin sayısı <xref:System.Threading.Monitor.LockContentionCount?displayProperty=nameWithType> |
| :::no-loc text="Number of Active Timers"::: (`active-timer-count`) | <xref:System.Threading.Timer>Şu anda etkin olan örneklerin sayısı<xref:System.Threading.Timer.ActiveCount?displayProperty=nameWithType> |
| :::no-loc text="Number of Assemblies Loaded"::: (`assembly-count`) | <xref:System.Reflection.Assembly>Bir zaman noktasındaki bir işleme yüklenen örnek sayısı |
| :::no-loc text="ThreadPool Completed Work Item Count"::: (`threadpool-completed-items-count`) | Şu ana kadar işlenen iş öğelerinin sayısı <xref:System.Threading.ThreadPool> |
| :::no-loc text="ThreadPool Queue Length"::: (`threadpool-queue-length`) | Şu anda içinde işlenmek üzere sıraya alınan iş öğelerinin sayısı <xref:System.Threading.ThreadPool> |
| :::no-loc text="ThreadPool Thread Count"::: (`threadpool-thread-count`) | Üzerinde şu anda mevcut olan iş parçacığı havuzu iş parçacıklarının sayısı <xref:System.Threading.ThreadPool><xref:System.Threading.ThreadPool.ThreadCount?displayProperty=nameWithType> |
| :::no-loc text="Working Set"::: (`working-set`) | Zaman tabanında bir noktada işlem bağlamına eşlenen fiziksel bellek miktarı <xref:System.Environment.WorkingSet?displayProperty=nameWithType> |
| :::no-loc text="IL Bytes Jitted"::: (`il-bytes-jitted`) | JıT olarak derlenen ve bayt cinsinden (.NET 5 ve sonraki sürümlerde kullanılabilir) Toplam ILS boyutu |
| :::no-loc text="Method Jitted Count"::: (`method-jitted-count`) | JıT olarak derlenen yöntemlerin sayısı (.NET 5 ve sonraki sürümlerinde kullanılabilir) |
| :::no-loc text="GC Committed Bytes"::: (`gc-committed-bytes`) | GC tarafından kaydedilen bayt sayısı (.NET 6 ve sonraki sürümlerinde kullanılabilir) |

## <a name="microsoftaspnetcorehosting-counters"></a>"Microsoft. AspNetCore. Hosting" sayaçları

Aşağıdaki sayaçlar [ASP.NET Core](/aspnet/core) bir parçası olarak yayımlanır ve içinde tutulur [`HostingEventSource.cs`](https://github.com/dotnet/aspnetcore/blob/main/src/Hosting/Hosting/src/Internal/HostingEventSource.cs) .

| Sayaç | Açıklama |
|--|--|
| :::no-loc text="Current Requests"::: (`current-requests`) | Başlatılmış ancak henüz durdurulmamış isteklerin toplam sayısı |
| :::no-loc text="Failed Requests"::: (`failed-requests`) | Uygulamanın ömrü boyunca oluşan başarısız isteklerin toplam sayısı |
| :::no-loc text="Request Rate"::: (`requests-per-second`) | Güncelleştirme aralığı başına oluşan isteklerin sayısı |
| :::no-loc text="Total Requests"::: (`total-requests`) | Uygulamanın ömrü boyunca oluşan isteklerin toplam sayısı |

## <a name="microsoftaspnetcorehttpconnections-counters"></a>"Microsoft. AspNetCore. http. Connections" sayaçları

Aşağıdaki sayaçlar [ASP.NET Core SignalR](/aspnet/core/signalr/introduction) 'nin bir parçası olarak yayımlanır ve içinde tutulur [`HttpConnectionsEventSource.cs`](https://github.com/dotnet/aspnetcore/blob/main/src/SignalR/common/Http.Connections/src/Internal/HttpConnectionsEventSource.cs) .

| Sayaç | Açıklama |
|--|--|
| :::no-loc text="Average Connection Duration"::: (`connections-duration`) | Bir bağlantının ortalama süresi (milisaniye cinsinden) |
| :::no-loc text="Current Connections"::: (`current-connections`) | Başlatılmış ancak henüz durdurulmamış etkin bağlantı sayısı |
| :::no-loc text="Total Connections Started"::: (`connections-started`) | Başlatılan toplam bağlantı sayısı |
| :::no-loc text="Total Connections Stopped"::: (`connections-stopped`) | Durdurulan toplam bağlantı sayısı |
| :::no-loc text="Total Connections Timed Out"::: (`connections-timed-out`) | Zaman aşımına uğrayan toplam bağlantı sayısı |

## <a name="microsoft-aspnetcore-server-kestrel-counters"></a>"Microsoft-AspNetCore-Server-Kestrel" sayaçları

Aşağıdaki sayaçlar [ASP.NET Core Kestrel Web sunucusunun](/aspnet/core/fundamentals/servers/kestrel) bir parçası olarak yayımlanır ve içinde tutulur [`KestrelEventSource.cs`](https://github.com/dotnet/aspnetcore/blob/main/src/Servers/Kestrel/Core/src/Internal/Infrastructure/KestrelEventSource.cs) .

| Sayaç | Açıklama |
|--|--|
| :::no-loc text="Connection Queue Length"::: (`connection-queue-length`) | Bağlantı sırasının geçerli uzunluğu |
| :::no-loc text="Connection Rate"::: (`connections-per-second`) | Web sunucusuna güncelleştirme aralığı başına bağlantı sayısı |
| :::no-loc text="Current Connections"::: (`current-connections`) | Web sunucusuna etkin bağlantıların geçerli sayısı |
| :::no-loc text="Current TLS Handshakes"::: (`current-tls-handshakes`) | Geçerli TLS el sıkışma sayısı |
| :::no-loc text="Current Upgraded Requests (WebSockets)"::: (`current-upgraded-requests`) | Yükseltilen isteklerin geçerli sayısı (WebSockets) |
| :::no-loc text="Failed TLS Handshakes"::: (`failed-tls-handshakes`) | Toplam başarısız TLS el sıkışmaları sayısı |
| :::no-loc text="Request Queue Length"::: (`request-queue-length`) | İstek sırasının geçerli uzunluğu |
| :::no-loc text="TLS Handshake Rate"::: (`tls-handshakes-per-second`) | Güncelleştirme aralığı başına TLS el sıkışma sayısı |
| :::no-loc text="Total Connections"::: (`total-connections`) | Web sunucusuna yönelik toplam bağlantı sayısı |
| :::no-loc text="Total TLS Handshakes"::: (`total-tls-handshakes`) | Web sunucusu ile toplam TLS el sıkışma sayısı |

## <a name="systemnethttp-counters"></a>"System .net. http" sayaçları

Aşağıdaki sayaçlar HTTP yığını tarafından yayımlanır.  Bu sayaçlar yalnızca .NET 5 ve sonraki sürümlerde kullanılabilir.

| Sayaç | Açıklama |
|--|--|
| :::no-loc text="Requests Started"::: (`requests-started`) | İşlemin başlatılmasından bu yana başlatılan istek sayısı |
| :::no-loc text="Requests Started Rate"::: (`requests-started-rate`) | Güncelleştirme aralığı başına başlatılan istek sayısı |
| :::no-loc text="Requests Failed"::: (`requests-failed`) | İşlemin başlatılmasından bu yana başarısız olan istek sayısı |
| :::no-loc text="Requests Failed Rate"::: (`requests-failed-rate`) | Güncelleştirme aralığı başına başarısız istek sayısı |
| :::no-loc text="Current Requests"::: (`current-requests`) | Başlatılmış ancak henüz tamamlanmamış veya başarısız olan etkin HTTP isteklerinin geçerli sayısı |
| :::no-loc text="Current HTTP 1.1 Connections"::: (`http11-connections-current-total`) | Başlatılmış ancak henüz tamamlanmamış veya başarısız olan HTTP 1,1 bağlantılarının geçerli sayısı |
| :::no-loc text="Current HTTP 2.0 Connections"::: (`http20-connections-current-total`) | Başlatılmış ancak henüz tamamlanmamış veya başarısız olan HTTP 2,0 bağlantılarının geçerli sayısı |
| :::no-loc text="HTTP 1.1 Requests Queue Duration"::: (`http11-requests-queue-duration`) | İstek kuyruğunda harcanan HTTP 1,1 isteklerinin ortalama süresi |
| :::no-loc text="HTTP 2.0 Requests Queue Duration"::: (`http20-requests-queue-duration`) | İstek kuyruğunda harcanan HTTP 2,0 isteklerinin ortalama süresi |

## <a name="systemnetnameresolution-counters"></a>"System .net. NameResolution" sayaçları

Aşağıdaki sayaçlar DNS aramalarıyla ilgili ölçümleri izler. Bu sayaçlar yalnızca .NET 5 ve sonraki sürümlerde kullanılabilir.

| Sayaç | Açıklama |
|--|--|
| :::no-loc text="DNS Lookups Requested"::: (`dns-lookups-requested`) | İşlemin başlatılmasından bu yana istenen DNS arama sayısı |
| :::no-loc text="Average DNS Lookup Duration"::: (`dns-lookups-duration`) | Bir DNS araması için geçen ortalama süre |

## <a name="systemnetsecurity-counters"></a>"System .net. Security" sayaçları

Aşağıdaki sayaçlar, aktarım katmanı güvenlik protokolü ile ilgili ölçümleri izler.  Bu sayaçlar yalnızca .NET 5 ve sonraki sürümlerde kullanılabilir.

| Sayaç | Açıklama |
|--|--|
| :::no-loc text="TLS handshakes completed"::: (`tls-handshake-rate`) | Güncelleştirme aralığı başına tamamlanan TLS el sıkışmaları sayısı |
| :::no-loc text="Total TLS handshakes completed"::: (`total-tls-handshakes`) | İşlem başladıktan sonra tamamlanan TLS el sıkışmaları toplam sayısı |
| :::no-loc text="Current TLS handshakes"::: (`current-tls-handshakes`) | Başlatılmış ancak henüz tamamlanmamış olan TLS el sıkışmalarının geçerli sayısı |
| :::no-loc text="Total TLS handshakes failed"::: (`failed-tls-handshakes`) | İşlemin başlatılmasından bu yana başarısız olan TLS el sıkışmaları toplam sayısı |
| :::no-loc text="All TLS Sessions Active"::: (`all-tls-sessions-open`) | Herhangi bir sürümdeki etkin TLS oturumlarının sayısı |
| :::no-loc text="TLS 1.0 Sessions Active"::: (`tls10-sessions-open`) | Etkin TLS 1,0 oturumlarının sayısı |
| :::no-loc text="TLS 1.1 Sessions Active"::: (`tls11-sessions-open`) | Etkin TLS 1,1 oturumlarının sayısı |
| :::no-loc text="TLS 1.2 Sessions Active"::: (`tls12-sessions-open`) | Etkin TLS 1,2 oturumlarının sayısı |
| :::no-loc text="TLS 1.3 Sessions Active"::: (`tls13-sessions-open`) | Etkin TLS 1,3 oturumlarının sayısı |
| :::no-loc text="TLS Handshake Duration"::: (`all-tls-handshake-duration`) | Tüm TLS el sıkışmaları ortalama süresi |
| :::no-loc text="TLS 1.0 Handshake Duration"::: (`tls10-handshake-duration`) | TLS 1,0 el sıkışmaları ortalama süresi |
| :::no-loc text="TLS 1.1 Handshake Duration"::: (`tls11-handshake-duration`) | TLS 1,1 el sıkışmaları ortalama süresi |
| :::no-loc text="TLS 1.2 Handshake Duration"::: (`tls12-handshake-duration`) | TLS 1,2 el sıkışmaları ortalama süresi |
| :::no-loc text="TLS 1.3 Handshake Duration"::: (`tls13-handshake-duration`) | TLS 1,3 el sıkışmaları ortalama süresi |

## <a name="systemnetsockets-counters-available-on-net-5-and-later-versions"></a>"System .net. Sockets" sayaçları (.NET 5 ve sonraki sürümlerinde kullanılabilir)

Aşağıdaki sayaçlar ile ilgili ölçümleri izler <xref:System.Net.Sockets.Socket> .

| Sayaç | Açıklama |
|--|--|
| :::no-loc text="Outgoing Connections Established"::: (`outgoing-connections-established`) | İşlemin başlatılmasından bu yana kurulan giden bağlantıların toplam sayısı |
| :::no-loc text="Incoming Connections Established"::: (`incoming-connections-established`) | İşlemin başlatılmasından bu yana kurulan gelen bağlantıların toplam sayısı |
| :::no-loc text="Bytes Received"::: (`bytes-received`) | İşlemin başlatılmasından bu yana alınan toplam bayt sayısı |
| :::no-loc text="Bytes Sent"::: (`bytes-sent`) | İşlemin başlatılmasından bu yana gönderilen toplam bayt sayısı |
| :::no-loc text="Datagrams Received"::: (`datagrams-received`) | İşlemin başlatılmasından bu yana alınan toplam veri birimi sayısı |
| :::no-loc text="Datagrams Sent"::: (`datagrams-sent`) | İşlemin başlatılmasından bu yana gönderilen toplam veri birimi sayısı |
