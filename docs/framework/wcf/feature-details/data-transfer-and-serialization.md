---
title: Veri Aktarma ve Seri Hale Getirme
ms.date: 03/30/2017
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
ms.openlocfilehash: 490c89f5cfbecd4b2cc0c0e639aa97849132a809
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261988"
---
# <a name="data-transfer-and-serialization"></a><span data-ttu-id="8b5f4-102">Veri Aktarma ve Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="8b5f4-102">Data Transfer and Serialization</span></span>

<span data-ttu-id="8b5f4-103">Bağlı bir sistemde, hizmetler ve istemciler herhangi bir görevi gerçekleştirmek için veri değişimine bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="8b5f4-103">In a connected system, services and clients depend on the exchange of data to accomplish any task.</span></span> <span data-ttu-id="8b5f4-104">Bir hizmet veya istemcinin geliştiricisi olarak, verimli ve kolay uygulamalar oluşturmak için Windows Communication Foundation (WCF) veri ve veri serileştirmesini nasıl işlediğini de anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8b5f4-104">As a developer of a service or client, you must also understand how Windows Communication Foundation (WCF) handles data and data serialization in order to create applications that are efficient and easy to maintain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8b5f4-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8b5f4-105">In This Section</span></span>  

 [<span data-ttu-id="8b5f4-106">Hizmet Sözleşmelerinde Veri Aktarımını Belirtme</span><span class="sxs-lookup"><span data-stu-id="8b5f4-106">Specifying Data Transfer in Service Contracts</span></span>](specifying-data-transfer-in-service-contracts.md)  
 <span data-ttu-id="8b5f4-107">Hizmetler 'de veri aktarımının temel kavramlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b5f4-107">Describes the basic concepts of data transfer in services.</span></span>  
  
 [<span data-ttu-id="8b5f4-108">Veri Sözleşmelerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="8b5f4-108">Using Data Contracts</span></span>](using-data-contracts.md)  
 <span data-ttu-id="8b5f4-109">Veri sözleşmelerinin ne olduğunu ve nasıl oluşturulacağını ve kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b5f4-109">Describes what data contracts are and how to create and use them.</span></span>  
  
 [<span data-ttu-id="8b5f4-110">Veri Sözleşmesi Seri Hale Getirici</span><span class="sxs-lookup"><span data-stu-id="8b5f4-110">Data Contract Serializer</span></span>](data-contract-serializer.md)  
 <span data-ttu-id="8b5f4-111">Sınıf veya sınıfın Uzantısı ile veri serileştirmesinin nasıl yapılacağını açıklar <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.XmlObjectSerializer> .</span><span class="sxs-lookup"><span data-stu-id="8b5f4-111">Describes how to accomplish serialization of data with the <xref:System.Runtime.Serialization.DataContractSerializer> class or any extension of the <xref:System.Runtime.Serialization.XmlObjectSerializer> class.</span></span>  
  
 [<span data-ttu-id="8b5f4-112">XmlSerializer Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="8b5f4-112">Using the XmlSerializer Class</span></span>](using-the-xmlserializer-class.md)  
 <span data-ttu-id="8b5f4-113">Sınıfının <xref:System.Xml.Serialization.XmlSerializer> bir alternatifi olan sınıfının nasıl ve nasıl kullanılacağını açıklar <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="8b5f4-113">Describes how and why to use the <xref:System.Xml.Serialization.XmlSerializer> class, an alternative to the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 [<span data-ttu-id="8b5f4-114">İleti Sözleşmeleri Kullanılıyor</span><span class="sxs-lookup"><span data-stu-id="8b5f4-114">Using Message Contracts</span></span>](using-message-contracts.md)  
 <span data-ttu-id="8b5f4-115">İleti sözleşmelerinin SOAP iletileri üzerinde ince denetime nasıl izin sağladığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b5f4-115">Describes how message contracts allow fine control over SOAP messages.</span></span>  
  
 [<span data-ttu-id="8b5f4-116">İleti Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="8b5f4-116">Using the Message Class</span></span>](using-the-message-class.md)  
 <span data-ttu-id="8b5f4-117">Ileti sınıfı özelliklerinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b5f4-117">Describes how to use Message class features.</span></span>  
  
 [<span data-ttu-id="8b5f4-118">Filtreleme</span><span class="sxs-lookup"><span data-stu-id="8b5f4-118">Filtering</span></span>](filtering.md)  
 <span data-ttu-id="8b5f4-119">Farklı ölçütlere göre bir iletinin ön işlemesini sağlayan filtrelemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b5f4-119">Describes filtering, which enables pre-processing of a message based on various criteria.</span></span>  
  
 [<span data-ttu-id="8b5f4-120">Büyük Veriler ve Akış Yapma</span><span class="sxs-lookup"><span data-stu-id="8b5f4-120">Large Data and Streaming</span></span>](large-data-and-streaming.md)  
 <span data-ttu-id="8b5f4-121">İkili dosya gibi büyük bir veri bloğunun nasıl gönderileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b5f4-121">Describes how to send a large block of data, such as a binary file.</span></span>  
  
 [<span data-ttu-id="8b5f4-122">Veriler için Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="8b5f4-122">Security Considerations for Data</span></span>](security-considerations-for-data.md)  
 <span data-ttu-id="8b5f4-123">Veri aktarımı ve Serileştirmeyi programlarken haberdar edilecek öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b5f4-123">Describes items to be aware of when programming data transfer and serialization.</span></span>  
  
 [<span data-ttu-id="8b5f4-124">Veri Aktarımı Mimarisi Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8b5f4-124">Data Transfer Architectural Overview</span></span>](data-transfer-architectural-overview.md)  
 <span data-ttu-id="8b5f4-125">WCF 'de veri aktarımının genel tasarımının görünümünü açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b5f4-125">Describes a view of the overall design of data transfer in WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8b5f4-126">Başvuru</span><span class="sxs-lookup"><span data-stu-id="8b5f4-126">Reference</span></span>  

 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a><span data-ttu-id="8b5f4-127">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="8b5f4-127">Related Sections</span></span>  

 [<span data-ttu-id="8b5f4-128">Kodlayıcılar ve Seri Hale Getiricileri Genişletme</span><span class="sxs-lookup"><span data-stu-id="8b5f4-128">Extending Encoders and Serializers</span></span>](../extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a><span data-ttu-id="8b5f4-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b5f4-129">See also</span></span>

- [<span data-ttu-id="8b5f4-130">En İyi Yöntemler: Veri Sözleşmesi Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8b5f4-130">Best Practices: Data Contract Versioning</span></span>](../best-practices-data-contract-versioning.md)
- [<span data-ttu-id="8b5f4-131">Hizmet Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8b5f4-131">Service Versioning</span></span>](../service-versioning.md)
