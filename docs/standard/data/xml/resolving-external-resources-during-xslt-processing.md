---
title: XSLT İşleme Sırasında Dış Kaynakları Çözümleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
ms.openlocfilehash: 5d50711eda266cecdb817c778f04aa845fa4c342
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686650"
---
# <a name="resolving-external-resources-during-xslt-processing"></a><span data-ttu-id="a281a-102">XSLT İşleme Sırasında Dış Kaynakları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="a281a-102">Resolving External Resources During XSLT Processing</span></span>

<span data-ttu-id="a281a-103">Dış kaynakları çözmeniz gerekebilmeniz için bir XSLT dönüştürmesi sırasında birkaç zaman vardır.</span><span class="sxs-lookup"><span data-stu-id="a281a-103">There are several times during an XSLT transformation when you may need to resolve external resources.</span></span>  
  
## <a name="using-the-xmlresolver-class"></a><span data-ttu-id="a281a-104">XmlResolver sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="a281a-104">Using the XmlResolver Class</span></span>  

 <span data-ttu-id="a281a-105"><xref:System.Xml.XmlResolver>Sınıfı, dış kaynakları çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a281a-105">The <xref:System.Xml.XmlResolver> class is used to resolve external resources.</span></span> <span data-ttu-id="a281a-106">Aşağıdaki tabloda <xref:System.Xml.XmlResolver> XSLT işleme sırasında ne zaman dahil olduğu açıklanır.</span><span class="sxs-lookup"><span data-stu-id="a281a-106">The following table describes when the <xref:System.Xml.XmlResolver> becomes involved during XSLT processing.</span></span>  
  
|<span data-ttu-id="a281a-107">XSLT görevi</span><span class="sxs-lookup"><span data-stu-id="a281a-107">XSLT task</span></span>|<span data-ttu-id="a281a-108">İçin XmlResolver kullanılma</span><span class="sxs-lookup"><span data-stu-id="a281a-108">What the XmlResolver is used for</span></span>|  
|---------------|--------------------------------------|  
|<span data-ttu-id="a281a-109">Stil sayfasını derleyin.</span><span class="sxs-lookup"><span data-stu-id="a281a-109">Compile the style sheet.</span></span>|<span data-ttu-id="a281a-110">Stil sayfasının URI 'sini çözümleyin.</span><span class="sxs-lookup"><span data-stu-id="a281a-110">Resolve the URI of the style sheet.</span></span><br /><br /> <span data-ttu-id="a281a-111">'</span><span class="sxs-lookup"><span data-stu-id="a281a-111">-and-</span></span><br /><br /> <span data-ttu-id="a281a-112">Herhangi bir veya öğesinde URI başvurularını çözümleyin `xsl:import` `xsl:include` .</span><span class="sxs-lookup"><span data-stu-id="a281a-112">Resolve URI references in any `xsl:import` or `xsl:include` elements.</span></span>|  
|<span data-ttu-id="a281a-113">Stil sayfasını yürütün.</span><span class="sxs-lookup"><span data-stu-id="a281a-113">Execute the style sheet.</span></span>|<span data-ttu-id="a281a-114">Bağlam belgesinin URI 'sini çözümleyin.</span><span class="sxs-lookup"><span data-stu-id="a281a-114">Resolve the URI of the context document.</span></span><br /><br /> <span data-ttu-id="a281a-115">'</span><span class="sxs-lookup"><span data-stu-id="a281a-115">-and-</span></span><br /><br /> <span data-ttu-id="a281a-116">Tüm XSLT işlevlerinde URI başvurularını çözümleyin `document()` .</span><span class="sxs-lookup"><span data-stu-id="a281a-116">Resolve URI references in any XSLT `document()` functions.</span></span>|  
  
 <span data-ttu-id="a281a-117"><xref:System.Xml.Xsl.XslCompiledTransform.Load%2A>Ve <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemleri, <xref:System.Xml.XmlResolver> bağımsız değişkenlerinden biri olarak bir nesne alan aşırı yüklemeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a281a-117">The <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> and <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> methods include overloads that take an <xref:System.Xml.XmlResolver> object as one of its arguments.</span></span> <span data-ttu-id="a281a-118"><xref:System.Xml.XmlResolver>Belirtilmemişse, <xref:System.Xml.XmlUrlResolver> kimlik bilgileri olmayan bir varsayılan kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a281a-118">If an <xref:System.Xml.XmlResolver> is not specified, a default <xref:System.Xml.XmlUrlResolver> with no credentials is used.</span></span>  
  
 <span data-ttu-id="a281a-119">Aşağıdaki listede bir nesne belirtmek isteyebileceğiniz zaman açıklanmaktadır <xref:System.Xml.XmlResolver> :</span><span class="sxs-lookup"><span data-stu-id="a281a-119">The following list describes when you may want to specify an <xref:System.Xml.XmlResolver> object:</span></span>  
  
- <span data-ttu-id="a281a-120">XSLT işleminin kimlik doğrulaması gerektiren bir ağ kaynağına erişmesi gerekiyorsa, <xref:System.Xml.XmlResolver> gerekli kimlik bilgileriyle bir kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a281a-120">If the XSLT process needs to access a network resource that requires authentication, you can use an <xref:System.Xml.XmlResolver> with the necessary credentials.</span></span>  
  
- <span data-ttu-id="a281a-121">XSLT işleminin erişebileceği kaynakları kısıtlamak istiyorsanız, <xref:System.Xml.XmlSecureResolver> doğru izin kümesiyle bir kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a281a-121">If you want to restrict the resources that the XSLT process can access, you can use an <xref:System.Xml.XmlSecureResolver> with the correct permission set.</span></span> <span data-ttu-id="a281a-122"><xref:System.Xml.XmlSecureResolver>Denetlediğiniz veya güvenilmeyen bir kaynağı açmanız gerekiyorsa sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="a281a-122">Use the <xref:System.Xml.XmlSecureResolver> class if you need to open a resource that you do not control, or that is untrusted.</span></span>  
  
- <span data-ttu-id="a281a-123">Davranışı özelleştirmek istiyorsanız kendi <xref:System.Xml.XmlResolver> sınıfınızı uygulayabilir ve kaynakları çözümlemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a281a-123">If you want to customize behavior, you can implement your own <xref:System.Xml.XmlResolver> class and use it to resolve resources.</span></span>  
  
- <span data-ttu-id="a281a-124">Hiçbir dış kaynağa erişilmemesini sağlamak istiyorsanız `null` <xref:System.Xml.XmlResolver> bağımsız değişkeni için belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a281a-124">If you want to ensure that no external resources are accessed, you can specify `null` for the <xref:System.Xml.XmlResolver> argument.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a281a-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="a281a-125">Example</span></span>  

 <span data-ttu-id="a281a-126">Aşağıdaki örnek, bir ağ kaynağında depolanan bir stil sayfasını derler.</span><span class="sxs-lookup"><span data-stu-id="a281a-126">The following example compiles a style sheet that is stored on a network resource.</span></span> <span data-ttu-id="a281a-127">Bir <xref:System.Xml.XmlUrlResolver> nesne, stil sayfasına erişmek için gereken kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a281a-127">An <xref:System.Xml.XmlUrlResolver> object specifies the credentials necessary to access the style sheet.</span></span>  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="a281a-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a281a-128">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- <xref:System.Xml.Xsl.XsltSettings>
- [<span data-ttu-id="a281a-129">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="a281a-129">XSLT Transformations</span></span>](xslt-transformations.md)
