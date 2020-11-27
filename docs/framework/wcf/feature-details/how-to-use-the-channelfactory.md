---
title: 'Nasıl yapılır: ChannelFactory Kullanma'
description: WCF istemcisi kullanarak hizmetlere erişmek için birden fazla kanal oluşturmak üzere bir kanal fabrikası oluşturmayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: dd767443fefb16ebc02300bffa4264357f12c3ae
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280591"
---
# <a name="how-to-use-the-channelfactory"></a><span data-ttu-id="847e0-103">Nasıl yapılır: ChannelFactory Kullanma</span><span class="sxs-lookup"><span data-stu-id="847e0-103">How to: Use the ChannelFactory</span></span>

<span data-ttu-id="847e0-104">Genel sınıf, birden <xref:System.ServiceModel.ChannelFactory%601> fazla kanal oluşturmak için kullanılabilecek bir kanal fabrikası oluşturulmasını gerektiren Gelişmiş senaryolarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="847e0-104">The generic <xref:System.ServiceModel.ChannelFactory%601> class is used in advanced scenarios that require the creation of a channel factory that can be used to create more than one channel.</span></span>  
  
### <a name="to-create-and-use-the-channelfactory-class"></a><span data-ttu-id="847e0-105">ChannelFactory sınıfını oluşturmak ve kullanmak için</span><span class="sxs-lookup"><span data-stu-id="847e0-105">To create and use the ChannelFactory class</span></span>  
  
1. <span data-ttu-id="847e0-106">Windows Communication Foundation (WCF) hizmetini derleyin ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="847e0-106">Build and run an Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="847e0-107">Daha fazla bilgi için bkz. [Hizmetleri tasarlama ve uygulama](../designing-and-implementing-services.md), [Hizmetleri yapılandırma](../configuring-services.md)ve [barındırma hizmetleri](../hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="847e0-107">For more information, see [Designing and Implementing Services](../designing-and-implementing-services.md), [Configuring Services](../configuring-services.md), and [Hosting Services](../hosting-services.md).</span></span>  
  
2. <span data-ttu-id="847e0-108">İstemci için sözleşme (arabirim) oluşturmak üzere [ServiceModel meta veri yardımcı programı aracını (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="847e0-108">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the contract (interface) for the client.</span></span>  
  
3. <span data-ttu-id="847e0-109">İstemci kodunda, <xref:System.ServiceModel.ChannelFactory%601> birden fazla uç nokta dinleyicisi oluşturmak için sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="847e0-109">In the client code, use the <xref:System.ServiceModel.ChannelFactory%601> class to create multiple endpoint listeners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="847e0-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="847e0-110">Example</span></span>  

 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
