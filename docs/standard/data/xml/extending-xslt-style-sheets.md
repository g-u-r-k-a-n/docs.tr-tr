---
title: XSLT Stil Sayfalarını Genişletme
ms.date: 03/30/2017
ms.assetid: df4ba2bf-a99e-4d22-bbf3-04fc67669dbc
ms.openlocfilehash: e598cb497ba1d415a3ccb53f1583352eba4ccdbb
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94831240"
---
# <a name="extending-xslt-style-sheets"></a><span data-ttu-id="8ed4c-102">XSLT Stil Sayfalarını Genişletme</span><span class="sxs-lookup"><span data-stu-id="8ed4c-102">Extending XSLT Style Sheets</span></span>
<span data-ttu-id="8ed4c-103">Bu bölümde XSLT işlevlerini genişletmek için farklı yöntemler açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8ed4c-103">This section describes the different methods of extending the XSLT functionality.</span></span> <span data-ttu-id="8ed4c-104">Sınıfını kullanarak uzantı nesneleri veya parametreler ekleyebilirsiniz <xref:System.Xml.Xsl.XsltArgumentList> .</span><span class="sxs-lookup"><span data-stu-id="8ed4c-104">You can add extension objects or parameters using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="8ed4c-105">Uzantı nesneleri veya parametreler daha sonra stil sayfasından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="8ed4c-105">The extension objects or parameters can then be called from the style sheet.</span></span> <span data-ttu-id="8ed4c-106">Ayrıca, öğesini kullanarak komut dosyası bloklarını stil sayfasına ekleyebilirsiniz `msxsl:script` .</span><span class="sxs-lookup"><span data-stu-id="8ed4c-106">In addition, you can also embed script blocks into the style sheet by using the `msxsl:script` element.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8ed4c-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8ed4c-107">In This Section</span></span>  
 [<span data-ttu-id="8ed4c-108">XSLT Genişletme Nesneleri</span><span class="sxs-lookup"><span data-stu-id="8ed4c-108">XSLT Extension Objects</span></span>](xslt-extension-objects.md)  
 <span data-ttu-id="8ed4c-109"><xref:System.Xml.Xsl.XsltArgumentList>XSLT uzantı nesnelerini işlemek için sınıfının kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8ed4c-109">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT extension objects.</span></span>  
  
 [<span data-ttu-id="8ed4c-110">XSLT Parametreleri</span><span class="sxs-lookup"><span data-stu-id="8ed4c-110">XSLT Parameters</span></span>](xslt-parameters.md)  
 <span data-ttu-id="8ed4c-111"><xref:System.Xml.Xsl.XsltArgumentList>XSLT parametrelerini işlemek için sınıfının kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8ed4c-111">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT parameters.</span></span>  
  
 [<span data-ttu-id="8ed4c-112">msxsl:script Kullanan Betik Blokları</span><span class="sxs-lookup"><span data-stu-id="8ed4c-112">Script Blocks Using msxsl:script</span></span>](script-blocks-using-msxsl-script.md)  
 <span data-ttu-id="8ed4c-113">Öğesinin kullanımını açıklar `msxsl:script` .</span><span class="sxs-lookup"><span data-stu-id="8ed4c-113">Discusses using the `msxsl:script` element.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8ed4c-114">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="8ed4c-114">Related Sections</span></span>  
 [<span data-ttu-id="8ed4c-115">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="8ed4c-115">XSLT Transformations</span></span>](xslt-transformations.md)
