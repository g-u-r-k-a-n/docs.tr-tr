---
title: NetworkInformation
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
ms.openlocfilehash: bc0604fd33d06521727c9aa0302ed313d8a2305f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428239"
---
# <a name="networkinformation"></a><span data-ttu-id="85640-102">NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="85640-102">NetworkInformation</span></span>
<span data-ttu-id="85640-103">The <xref:System.Net.NetworkInformation> namespace enables you to gather information about network events, changes, statistics, and properties.</span><span class="sxs-lookup"><span data-stu-id="85640-103">The <xref:System.Net.NetworkInformation> namespace enables you to gather information about network events, changes, statistics, and properties.</span></span> <span data-ttu-id="85640-104">You can also determine whether a remote host is reachable by using the <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> class.</span><span class="sxs-lookup"><span data-stu-id="85640-104">You can also determine whether a remote host is reachable by using the <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> class.</span></span>  
  
## <a name="network-availability-and-events"></a><span data-ttu-id="85640-105">Network Availability and Events</span><span class="sxs-lookup"><span data-stu-id="85640-105">Network Availability and Events</span></span>  
 <span data-ttu-id="85640-106">The <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> class enables you to determine whether the network address or availability has changed.</span><span class="sxs-lookup"><span data-stu-id="85640-106">The <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> class enables you to determine whether the network address or availability has changed.</span></span> <span data-ttu-id="85640-107">To use this class, create an event handler to process the change, and associate it with a <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> or a <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="85640-107">To use this class, create an event handler to process the change, and associate it with a <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> or a <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>.</span></span> <span data-ttu-id="85640-108">For more information, see [How to: Detect Network Availability and Address Changes](how-to-detect-network-availability-and-address-changes.md).</span><span class="sxs-lookup"><span data-stu-id="85640-108">For more information, see [How to: Detect Network Availability and Address Changes](how-to-detect-network-availability-and-address-changes.md).</span></span>  
  
## <a name="network-statistics-and-properties"></a><span data-ttu-id="85640-109">Network Statistics and Properties</span><span class="sxs-lookup"><span data-stu-id="85640-109">Network Statistics and Properties</span></span>  
 <span data-ttu-id="85640-110">You can gather network statistics and properties on an interface or protocol basis.</span><span class="sxs-lookup"><span data-stu-id="85640-110">You can gather network statistics and properties on an interface or protocol basis.</span></span> <span data-ttu-id="85640-111">The <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType>, and <xref:System.Net.NetworkInformation.PhysicalAddress> classes give information about a particular network interface, while the <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics>, and <xref:System.Net.NetworkInformation.UdpStatistics> classes give information about layer 3 and layer 4 packets.</span><span class="sxs-lookup"><span data-stu-id="85640-111">The <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType>, and <xref:System.Net.NetworkInformation.PhysicalAddress> classes give information about a particular network interface, while the <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics>, and <xref:System.Net.NetworkInformation.UdpStatistics> classes give information about layer 3 and layer 4 packets.</span></span> <span data-ttu-id="85640-112">For more information, see [How to: Get Interface and Protocol Information](how-to-get-interface-and-protocol-information.md).</span><span class="sxs-lookup"><span data-stu-id="85640-112">For more information, see [How to: Get Interface and Protocol Information](how-to-get-interface-and-protocol-information.md).</span></span>  
  
## <a name="determine-if-a-remote-host-is-reachable"></a><span data-ttu-id="85640-113">Determine if a Remote Host is Reachable</span><span class="sxs-lookup"><span data-stu-id="85640-113">Determine if a Remote Host is Reachable</span></span>  
 <span data-ttu-id="85640-114">You can use the <xref:System.Net.NetworkInformation.Ping> class to determine whether a Remote Host is up, on the network, and reachable.</span><span class="sxs-lookup"><span data-stu-id="85640-114">You can use the <xref:System.Net.NetworkInformation.Ping> class to determine whether a Remote Host is up, on the network, and reachable.</span></span> <span data-ttu-id="85640-115">For more information, see [How to: Ping a Host](how-to-ping-a-host.md).</span><span class="sxs-lookup"><span data-stu-id="85640-115">For more information, see [How to: Ping a Host](how-to-ping-a-host.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85640-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85640-116">See also</span></span>

- [<span data-ttu-id="85640-117">Ağ Programlama Örnekleri</span><span class="sxs-lookup"><span data-stu-id="85640-117">Network Programming Samples</span></span>](network-programming-samples.md)

<!-- to-do: review sample links
- [Network Information Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Network%20Information)
- [NetStat Tool Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=NetStat%20Tool)
- [Ping Client Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Ping%20Client)
-->
