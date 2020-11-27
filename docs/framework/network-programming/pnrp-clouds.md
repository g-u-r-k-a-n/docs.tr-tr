---
title: PNRP Bulutları
ms.date: 03/30/2017
ms.assetid: a82e2bf1-62ab-4c2d-83f3-3217a6aead2e
ms.openlocfilehash: 60b6fb44116fe2d8af50fb0b310615b3b962977b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263210"
---
# <a name="pnrp-clouds"></a><span data-ttu-id="28f49-102">PNRP Bulutları</span><span class="sxs-lookup"><span data-stu-id="28f49-102">PNRP Clouds</span></span>

<span data-ttu-id="28f49-103">Bir PNRP "bulutu" ağ üzerinden birbirleriyle iletişim kurabilen bir düğüm kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="28f49-103">A PNRP "cloud" represents a set of nodes that can communicate with each other through the network.</span></span> <span data-ttu-id="28f49-104">"Cloud" terimi "eşdüzey ağ" ve "eşler arası Graf" ile eşanlamlıdır.</span><span class="sxs-lookup"><span data-stu-id="28f49-104">The term "cloud" is synonymous with "peer mesh" and "peer-to-peer graph".</span></span>  
  
 <span data-ttu-id="28f49-105">Düğümler arasındaki iletişimin asla bir buluttan diğerine çapraz olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="28f49-105">Communication between nodes should never cross from one cloud to another.</span></span> <span data-ttu-id="28f49-106"><xref:System.Net.PeerToPeer.Cloud>Örnek, büyük/küçük harfe duyarlı olan adıyla benzersiz bir şekilde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="28f49-106">A <xref:System.Net.PeerToPeer.Cloud> instance is uniquely identified by its name, which is case-sensitive.</span></span> <span data-ttu-id="28f49-107">Tek bir eş veya düğüm birden fazla buluta bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="28f49-107">A single peer or node may be connected to more than one cloud.</span></span>  
  
 <span data-ttu-id="28f49-108">Bulutlar ağ arabirimlerine çok yakın bir şekilde bağlanır.</span><span class="sxs-lookup"><span data-stu-id="28f49-108">Clouds are tied very closely to network interfaces.</span></span>  <span data-ttu-id="28f49-109">Farklı alt ağlara bağlı iki ağ kartına sahip çoklu bilgisayarlı bir makinede, üç bulut döndürülür: Arabirim başına her bir bağlantı yerel adresi için bir tane ve tek bir genel kapsam bulutu.</span><span class="sxs-lookup"><span data-stu-id="28f49-109">On a multi-homed machine with two network cards attached to different subnets, three clouds will be returned: one for each of the link local addresses per interface, and a single global scope cloud.</span></span>  
  
 <span data-ttu-id="28f49-110">PNRP, bir kapsamın birbirini bulabilen bilgisayarların gruplandırılması olduğu üç bulut "kapsamını" kullanır:</span><span class="sxs-lookup"><span data-stu-id="28f49-110">PNRP uses three cloud "scopes", in which a scope is a grouping of computers that are able to find each other:</span></span>  
  
- <span data-ttu-id="28f49-111">Genel bulut genel IPv6 adresi kapsamına ve genel adreslere karşılık gelir ve IPv6 Internet 'in tamamında tüm bilgisayarları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="28f49-111">The global cloud corresponds to the global IPv6 address scope and global addresses and represents all the computers on the entire IPv6 Internet.</span></span> <span data-ttu-id="28f49-112">Yalnızca tek bir genel bulut vardır.</span><span class="sxs-lookup"><span data-stu-id="28f49-112">There is only a single global cloud.</span></span>  
  
- <span data-ttu-id="28f49-113">Bağlantı yerel bulutu bağlantı yerel IPv6 adresi kapsamına ve bağlantı yerel adreslerine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="28f49-113">The link-local cloud corresponds to the link-local IPv6 address scope and link-local addresses.</span></span> <span data-ttu-id="28f49-114">Bağlantı yerel bulutu, genellikle yerel olarak bağlı alt ağla aynı olan belirli bir bağlantı içindir.</span><span class="sxs-lookup"><span data-stu-id="28f49-114">A link-local cloud is for a specific link, which is typically the same as the locally attached subnet.</span></span> <span data-ttu-id="28f49-115">Birden çok bağlantı yerel bulutu olabilir.</span><span class="sxs-lookup"><span data-stu-id="28f49-115">There can be multiple link-local clouds.</span></span>  
  
 <span data-ttu-id="28f49-116">Siteye özgü bulut olan üçüncü bulut, site IPv6 adresi kapsamına ve site yerel adreslerine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="28f49-116">A third cloud, the site-specific cloud, corresponds to the site IPv6 address scope and site-local addresses.</span></span> <span data-ttu-id="28f49-117">Bu bulut kullanım dışı bırakılmıştır, ancak yine de PNRP ' de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="28f49-117">This cloud has been deprecated, although it is still supported in PNRP.</span></span>  
  
## <a name="clouds"></a><span data-ttu-id="28f49-118">Bulutlar</span><span class="sxs-lookup"><span data-stu-id="28f49-118">Clouds</span></span>  

 <span data-ttu-id="28f49-119">PNRP bulutları, sınıfının örnekleriyle temsil edilir <xref:System.Net.PeerToPeer.Cloud> .</span><span class="sxs-lookup"><span data-stu-id="28f49-119">PNRP clouds are represented by instances of the <xref:System.Net.PeerToPeer.Cloud> class.</span></span> <span data-ttu-id="28f49-120">Bir eşdüzey kullanılan bulut grupları, sıralanabilir sınıfın örnekleri tarafından temsil edilir <xref:System.Net.PeerToPeer.CloudCollection> .</span><span class="sxs-lookup"><span data-stu-id="28f49-120">Groups of clouds used a peer are represented by instances of the enumerable <xref:System.Net.PeerToPeer.CloudCollection> class.</span></span> <span data-ttu-id="28f49-121">Geçerli eş tarafından bilinen PNRP bulutu koleksiyonları statik yöntem çağırarak elde edilebilir <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> .</span><span class="sxs-lookup"><span data-stu-id="28f49-121">Collections of PNRP clouds known to the current peer can be obtained by calling the static <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> method.</span></span>  
  
 <span data-ttu-id="28f49-122">Ayrı bulutlar, 256 karakter Unicode dizesi olarak temsil edilen benzersiz adlara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="28f49-122">Individual clouds have unique names, represented as a 256 character Unicode string.</span></span> <span data-ttu-id="28f49-123">Bu adlar, yukarıda bahsedilen kapsamla birlikte, bulut sınıfının benzersiz örneklerini oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="28f49-123">These names, along with the above-mentioned scope, are used to construct unique instances of the Cloud class.</span></span> <span data-ttu-id="28f49-124">Bu örnekler kalıcı kullanım için seri hale getirilebilir ve yeniden oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="28f49-124">These instances can be serialized and reconstructed for persistent usage.</span></span>  
  
 <span data-ttu-id="28f49-125">Bir bulut örneği oluşturulduktan veya alındıktan sonra, bir bilinen eşdüzey ağ oluşturmak için eş adları onunla birlikte kaydedilebilir.</span><span class="sxs-lookup"><span data-stu-id="28f49-125">Once a Cloud instance is created or obtained, peer names can be registered with it to create a mesh of known peers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28f49-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28f49-126">See also</span></span>

- <xref:System.Net.PeerToPeer.Cloud>
- [<span data-ttu-id="28f49-127">Eş Adı Çözümleme Protokolü</span><span class="sxs-lookup"><span data-stu-id="28f49-127">Peer Name Resolution Protocol</span></span>](peer-name-resolution-protocol.md)
