---
title: 'Nasıl yapılır: Aynı Türde Birden Fazla Belirteç Kullanma'
ms.date: 03/30/2017
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
ms.openlocfilehash: 7374eebb9e42ef761b7ab8980b3eacf4d5671e6d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280708"
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="20320-102">Nasıl yapılır: Aynı Türde Birden Fazla Belirteç Kullanma</span><span class="sxs-lookup"><span data-stu-id="20320-102">How to: Use Multiple Security Tokens of the Same Type</span></span>

- <span data-ttu-id="20320-103">.NET Framework 3,0 ' de, istemci iletisi yalnızca belirli bir türün bir belirtecini içeriyordu.</span><span class="sxs-lookup"><span data-stu-id="20320-103">In .NET Framework 3.0, a client message only contained one token of any given type.</span></span> <span data-ttu-id="20320-104">Artık istemci iletileri bir tür için birden çok belirteç içerebilir.</span><span class="sxs-lookup"><span data-stu-id="20320-104">Now client messages can contain multiple tokens of a type.</span></span> <span data-ttu-id="20320-105">Bu konu başlığında, istemci iletisinde aynı türde birden fazla belirteç ekleme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="20320-105">This topic shows how to include multiple tokens of the same type in a client message.</span></span>  
  
- <span data-ttu-id="20320-106">Hizmeti bu şekilde yapılandıramayacağınızı unutmayın: bir hizmet yalnızca bir destekleme belirteci içerebilir.</span><span class="sxs-lookup"><span data-stu-id="20320-106">Note that you cannot configure a service in this way: a service can contain only one supporting token.</span></span>  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="20320-107">Aynı türde birden fazla güvenlik belirteci kullanmak için</span><span class="sxs-lookup"><span data-stu-id="20320-107">To use multiple security tokens of the same type</span></span>  
  
1. <span data-ttu-id="20320-108">Doldurulacak boş bir bağlama öğesi koleksiyonu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="20320-108">Create an empty binding element collection to be populated.</span></span>  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2. <span data-ttu-id="20320-109">Çağırarak oluşturun <xref:System.ServiceModel.Channels.SecurityBindingElement> <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A> .</span><span class="sxs-lookup"><span data-stu-id="20320-109">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> by calling <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span></span>  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3. <span data-ttu-id="20320-110">Koleksiyon oluşturun <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> .</span><span class="sxs-lookup"><span data-stu-id="20320-110">Create a <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4. <span data-ttu-id="20320-111">Koleksiyona SAML belirteçleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20320-111">Add SAML tokens to the collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5. <span data-ttu-id="20320-112">Koleksiyonunu öğesine ekleyin <xref:System.ServiceModel.Channels.SecurityBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="20320-112">Add the collection to the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6. <span data-ttu-id="20320-113">Bağlama öğesi koleksiyonuna bağlama öğeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="20320-113">Add binding elements to the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7. <span data-ttu-id="20320-114">Bağlama öğesi koleksiyonundan oluşturulan yeni bir özel bağlama döndürür.</span><span class="sxs-lookup"><span data-stu-id="20320-114">Return a new custom binding created from the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a><span data-ttu-id="20320-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="20320-115">Example</span></span>  

 <span data-ttu-id="20320-116">Aşağıda, önceki yordamda açıklanan yöntemin tamamı verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="20320-116">The following is the entire method described by the preceding procedure.</span></span>  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
