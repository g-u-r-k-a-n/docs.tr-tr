---
title: Uygulama Geliştirmede PNRP
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
ms.openlocfilehash: f9a408fbd7fbbb77c0fd5208926f4b06fcf23b38
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428212"
---
# <a name="pnrp-in-application-development"></a><span data-ttu-id="6d9a8-102">Uygulama Geliştirmede PNRP</span><span class="sxs-lookup"><span data-stu-id="6d9a8-102">PNRP in Application Development</span></span>
<span data-ttu-id="6d9a8-103">In Windows Vista, networking applications can access name publication and resolution functions through a simplified PNRP application programming interface (API).</span><span class="sxs-lookup"><span data-stu-id="6d9a8-103">In Windows Vista, networking applications can access name publication and resolution functions through a simplified PNRP application programming interface (API).</span></span>  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a><span data-ttu-id="6d9a8-104">Implementing the Peer Name Resolution Protocol</span><span class="sxs-lookup"><span data-stu-id="6d9a8-104">Implementing the Peer Name Resolution Protocol</span></span>  
 <span data-ttu-id="6d9a8-105">With the simplified PNRP API, clouds are not explicitly specified to register the name and addresses; the PNRP component automatically determines the appropriate clouds to join and the addresses to publish within the clouds.</span><span class="sxs-lookup"><span data-stu-id="6d9a8-105">With the simplified PNRP API, clouds are not explicitly specified to register the name and addresses; the PNRP component automatically determines the appropriate clouds to join and the addresses to publish within the clouds.</span></span>  
  
 <span data-ttu-id="6d9a8-106">For highly simplified PNRP name resolution in Windows Vista, PNRP names are now integrated into the getaddrinfo() Windows Sockets function.</span><span class="sxs-lookup"><span data-stu-id="6d9a8-106">For highly simplified PNRP name resolution in Windows Vista, PNRP names are now integrated into the getaddrinfo() Windows Sockets function.</span></span> <span data-ttu-id="6d9a8-107">To use PNRP to resolve a name to an IPv6 address, applications can use the getaddrinfo() function to resolve the Fully Qualified Domain Name (FQDN) name.prnp.net, in which name is peer name being resolved.</span><span class="sxs-lookup"><span data-stu-id="6d9a8-107">To use PNRP to resolve a name to an IPv6 address, applications can use the getaddrinfo() function to resolve the Fully Qualified Domain Name (FQDN) name.prnp.net, in which name is peer name being resolved.</span></span> <span data-ttu-id="6d9a8-108">The pnrp.net domain is a reserved domain in Windows Vista for PNRP name resolution.</span><span class="sxs-lookup"><span data-stu-id="6d9a8-108">The pnrp.net domain is a reserved domain in Windows Vista for PNRP name resolution.</span></span>  
  
 <span data-ttu-id="6d9a8-109">Message passing between PeerToPeer applications is still handled by underlying architectures such as PeerChannel and WCF [Large Data and Streaming](../wcf/feature-details/large-data-and-streaming.md).</span><span class="sxs-lookup"><span data-stu-id="6d9a8-109">Message passing between PeerToPeer applications is still handled by underlying architectures such as PeerChannel and WCF [Large Data and Streaming](../wcf/feature-details/large-data-and-streaming.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d9a8-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d9a8-110">See also</span></span>

- <xref:System.Net.PeerToPeer>
