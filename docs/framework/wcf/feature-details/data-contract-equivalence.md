---
description: 'Hakkında daha fazla bilgi edinin: veri sözleşmesi denklik'
title: Veri Sözleşmesi Eşitliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], equivalence
ms.assetid: f06f3c7e-c235-4ec1-b200-68142edf1ed1
ms.openlocfilehash: d47107cfaeea5093977a919df1a5edb226cb4ebc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704998"
---
# <a name="data-contract-equivalence"></a><span data-ttu-id="f3933-103">Veri Sözleşmesi Eşitliği</span><span class="sxs-lookup"><span data-stu-id="f3933-103">Data Contract Equivalence</span></span>

<span data-ttu-id="f3933-104">Bir istemcinin belirli bir türdeki verileri bir hizmete veya bir istemciye başarıyla veri göndermek için bir hizmete başarıyla göndermesini sağlamak için, gönderilen türün alma sonunda bulunması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f3933-104">For a client to successfully send data of a certain type to a service, or a service to successfully send data to a client, the sent type does not necessarily have to exist on the receiving end.</span></span> <span data-ttu-id="f3933-105">Tek gereksinim, her iki türdeki veri sözleşmelerinin de aynı olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="f3933-105">The only requirement is that the data contracts of both types be equivalent.</span></span> <span data-ttu-id="f3933-106">(Bazen, [veri anlaşması sürümü oluşturma](data-contract-versioning.md)bölümünde açıklandığı gibi katı denklik gerekli değildir.)</span><span class="sxs-lookup"><span data-stu-id="f3933-106">(Sometimes, strict equivalence is not required, as discussed in [Data Contract Versioning](data-contract-versioning.md).)</span></span>  
  
 <span data-ttu-id="f3933-107">Veri sözleşmelerinin eşdeğer olması için aynı ad alanına ve ada sahip olmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3933-107">For data contracts to be equivalent, they must have the same namespace and name.</span></span> <span data-ttu-id="f3933-108">Ayrıca, bir taraftaki her bir veri üyesinin diğer tarafta eşdeğer bir veri üyesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3933-108">Additionally, each data member on one side must have an equivalent data member on the other side.</span></span>  
  
 <span data-ttu-id="f3933-109">Veri üyelerinin eşit olması için aynı ada sahip olmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3933-109">For data members to be equivalent, they must have the same name.</span></span> <span data-ttu-id="f3933-110">Ayrıca, aynı türde verileri temsil etmelidir; diğer bir deyişle, veri sözleşmeleri eşdeğer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f3933-110">Additionally, they must represent the same type of data; that is, their data contracts must be equivalent.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f3933-111">Veri sözleşmesi adlarının ve ad alanlarının yanı sıra veri üyesi adlarının büyük/küçük harfe duyarlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f3933-111">Note that data contract names and namespaces, as well as data member names, are case-sensitive.</span></span>  
  
 <span data-ttu-id="f3933-112">Veri sözleşmesi adları ve ad alanları ve veri üyesi adları hakkında daha fazla bilgi için bkz. [veri sözleşmesi adları](data-contract-names.md).</span><span class="sxs-lookup"><span data-stu-id="f3933-112">For more information about data contract names and namespaces, as well as data member names, see [Data Contract Names](data-contract-names.md).</span></span>  
  
 <span data-ttu-id="f3933-113">Aynı tarafta (Gönderen veya alıcı) iki tür varsa ve veri sözleşmeleri eşit değildir (örneğin, farklı veri üyeleri varsa), bunlara aynı ad ve ad alanı vermemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="f3933-113">If two types exist on the same side (sender or receiver) and their data contracts are not equivalent (for example, they have different data members), you should not give them the same name and namespace.</span></span> <span data-ttu-id="f3933-114">Bunun yapılması özel durumların oluşturulmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f3933-114">Doing so may cause exceptions to be thrown.</span></span>  
  
 <span data-ttu-id="f3933-115">Aşağıdaki türler için veri sözleşmeleri eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="f3933-115">The data contracts for the following types are equivalent:</span></span>  
  
 [!code-csharp[C_DataContractNames#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#5)]
 [!code-vb[C_DataContractNames#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#5)]  
  
## <a name="data-member-order-and-data-contract-equivalence"></a><span data-ttu-id="f3933-116">Veri üyesi siparişi ve veri sözleşmesi denklik</span><span class="sxs-lookup"><span data-stu-id="f3933-116">Data Member Order and Data Contract equivalence</span></span>  

 <span data-ttu-id="f3933-117"><xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>Sınıfının özelliğinin kullanılması, <xref:System.Runtime.Serialization.DataMemberAttribute> veri sözleşmesinin denkdeğerliğine etkilenebilir.</span><span class="sxs-lookup"><span data-stu-id="f3933-117">Using the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> class may affect data contract equivalence.</span></span> <span data-ttu-id="f3933-118">Veri sözleşmeleri, eşdeğer olması için aynı sırada görünen üyelere sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f3933-118">The data contracts must have members that appear in the same order to be equivalent.</span></span> <span data-ttu-id="f3933-119">Varsayılan sıra alfabetik bir değer.</span><span class="sxs-lookup"><span data-stu-id="f3933-119">The default order is alphabetical.</span></span> <span data-ttu-id="f3933-120">Daha fazla bilgi için bkz. [veri üye sıralaması](data-member-order.md).</span><span class="sxs-lookup"><span data-stu-id="f3933-120">For more information, see [Data Member Order](data-member-order.md).</span></span>  
  
 <span data-ttu-id="f3933-121">Örneğin, aşağıdaki kod eşdeğer veri sözleşmeleri ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="f3933-121">For example, the following code results in equivalent data contracts.</span></span>  
  
 [!code-csharp[C_DataContractNames#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#6)]
 [!code-vb[C_DataContractNames#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#6)]  
  
 <span data-ttu-id="f3933-122">Ancak, aşağıdakiler eşdeğer bir veri sözleşmesine neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="f3933-122">However, the following does not result in an equivalent data contract.</span></span>  
  
 [!code-csharp[C_DataContractNames#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#7)]
 [!code-vb[C_DataContractNames#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#7)]  
  
## <a name="inheritance-interfaces-and-data-contract-equivalence"></a><span data-ttu-id="f3933-123">Devralma, arabirimler ve veri sözleşmesi denklik</span><span class="sxs-lookup"><span data-stu-id="f3933-123">Inheritance, Interfaces, and Data Contract Equivalence</span></span>  

 <span data-ttu-id="f3933-124">Denklik belirlenirken, başka bir veri sözleşmesinden devralan bir veri sözleşmesi, temel türden tüm veri üyelerini içeren yalnızca bir veri anlaşması gibi değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f3933-124">When determining equivalence, a data contract that inherits from another data contract is treated as if it is just one data contract that includes all of the data members from the base type.</span></span> <span data-ttu-id="f3933-125">Veri üyeleri sırasının eşleşmesi gerektiğini ve temel tür üyelerinin, türetilmiş tür üyelerinden önce sipariş olarak gelmesini aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="f3933-125">Keep in mind that the order of the data members must match and that base type members precede derived type members in the order.</span></span> <span data-ttu-id="f3933-126">Ayrıca, aşağıdaki kod örneğinde olduğu gibi, iki veri üyesinin aynı sıra değeri varsa, bu veri üyeleri için sıralama alfabetik bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="f3933-126">Furthermore, if, as in the following code example, two data members have the same order value, the ordering for those data members is alphabetical.</span></span> <span data-ttu-id="f3933-127">Daha fazla bilgi için bkz. [veri üye sıralaması](data-member-order.md).</span><span class="sxs-lookup"><span data-stu-id="f3933-127">For more information, see [Data Member Order](data-member-order.md).</span></span>  
  
 <span data-ttu-id="f3933-128">Aşağıdaki örnekte, türü için veri sözleşmesi, `Employee` türü için veri sözleşmesine eşdeğerdir `Worker` .</span><span class="sxs-lookup"><span data-stu-id="f3933-128">In the following example, the data contract for type `Employee` is equivalent to the data contract for the type `Worker`.</span></span>  
  
 [!code-csharp[C_DataContractNames#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#8)]
 [!code-vb[C_DataContractNames#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#8)]  
  
 <span data-ttu-id="f3933-129">Parametreler ve bir istemci ile bir hizmet arasında değer döndürerdiğinde, alıcı uç nokta türetilmiş bir sınıftan bir veri anlaşması beklerken, taban sınıftan bir veri sözleşmesi gönderilemez.</span><span class="sxs-lookup"><span data-stu-id="f3933-129">When passing parameters and return values between a client and a service, a data contract from a base class cannot be sent when the receiving endpoint expects a data contract from a derived class.</span></span> <span data-ttu-id="f3933-130">Bu, nesne odaklı programlama tenetleri 'ne uygun.</span><span class="sxs-lookup"><span data-stu-id="f3933-130">This is in accordance with object-oriented programming tenets.</span></span> <span data-ttu-id="f3933-131">Önceki örnekte, türünde bir nesne `Person` `Employee` beklendiğinde gönderilemez.</span><span class="sxs-lookup"><span data-stu-id="f3933-131">In the previous example, an object of type `Person` cannot be sent when an `Employee` is expected.</span></span>  
  
 <span data-ttu-id="f3933-132">Türetilmiş bir sınıftan veri sözleşmesi, bir temel sınıftan veri sözleşmesi beklendiğinde, ancak yalnızca ' ı kullanarak türetilmiş türün "biliyor" ise gönderilebilir <xref:System.Runtime.Serialization.KnownTypeAttribute> .</span><span class="sxs-lookup"><span data-stu-id="f3933-132">A data contract from a derived class can be sent when a data contract from a base class is expected, but only if the receiving endpoint "knows" of the derived type using the <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span></span> <span data-ttu-id="f3933-133">Daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="f3933-133">For more information, see [Data Contract Known Types](data-contract-known-types.md).</span></span> <span data-ttu-id="f3933-134">Önceki örnekte, `Employee` bir nesne `Person` beklendiğinde, ancak yalnızca alıcı kodu <xref:System.Runtime.Serialization.KnownTypeAttribute> onu bilinen türler listesine eklemek için kullanıyorsa, türü bir nesnesi gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="f3933-134">In the previous example, an object of type `Employee` can be sent when a `Person` is expected, but only if the receiver code employs the <xref:System.Runtime.Serialization.KnownTypeAttribute> to include it in the list of known types.</span></span>  
  
 <span data-ttu-id="f3933-135">Parametreler ve uygulamalar arasında dönüş değerlerini geçirdiğinde, beklenen tür bir arabirimiyorsa, tür olan beklenen tür ile eşdeğerdir <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="f3933-135">When passing parameters and return values between applications, if the expected type is an interface, it is equivalent to the expected type being of type <xref:System.Object>.</span></span> <span data-ttu-id="f3933-136">Her tür son olarak öğesinden türetildiğinden <xref:System.Object> , her ne kadar veri sözleşmesi için veri sözleşmesinden türetilir <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="f3933-136">Because every type ultimately derives from <xref:System.Object>, every data contract ultimately derives from the data contract for <xref:System.Object>.</span></span> <span data-ttu-id="f3933-137">Bu nedenle, bir arabirim beklendiğinde herhangi bir veri anlaşması türü geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f3933-137">Thus, any data contract type can be passed when an interface is expected.</span></span> <span data-ttu-id="f3933-138">Arabirimler ile başarılı bir şekilde çalışmak için ek adımlar gereklidir; daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="f3933-138">Additional steps are required to successfully work with interfaces; for more information, see [Data Contract Known Types](data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3933-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3933-139">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="f3933-140">Veri Üye Sırası</span><span class="sxs-lookup"><span data-stu-id="f3933-140">Data Member Order</span></span>](data-member-order.md)
- [<span data-ttu-id="f3933-141">Veri Sözleşmesi Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="f3933-141">Data Contract Known Types</span></span>](data-contract-known-types.md)
- [<span data-ttu-id="f3933-142">Veri Sözleşmesi Adları</span><span class="sxs-lookup"><span data-stu-id="f3933-142">Data Contract Names</span></span>](data-contract-names.md)
