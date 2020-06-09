---
title: 'Nasıl yapılır: Hizmet Uç Noktalarından Meta Verileri Dışa Aktarma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b6c4dfd0-f270-43ec-961a-e16eb6af2f2c
ms.openlocfilehash: 58e86e5566775048e081bfb4ac217a7747b98a35
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579416"
---
# <a name="how-to-export-metadata-from-service-endpoints"></a><span data-ttu-id="e68e8-102">Nasıl yapılır: Hizmet Uç Noktalarından Meta Verileri Dışa Aktarma</span><span class="sxs-lookup"><span data-stu-id="e68e8-102">How to: Export Metadata from Service Endpoints</span></span>
<span data-ttu-id="e68e8-103">Bu konuda, hizmet uç noktalarından meta verilerin nasıl dışarı aktarılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e68e8-103">This topic explains how to export metadata from service endpoints.</span></span>  
  
### <a name="to-export-metadata-from-service-endpoints"></a><span data-ttu-id="e68e8-104">Meta verileri hizmet uç noktalarından dışarı aktarmak için</span><span class="sxs-lookup"><span data-stu-id="e68e8-104">To export metadata from service endpoints</span></span>  
  
1. <span data-ttu-id="e68e8-105">Yeni bir Visual Studio konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e68e8-105">Create a new Visual Studio Console App Project.</span></span> <span data-ttu-id="e68e8-106">Main () yönteminde oluşturulan Program.cs dosyasına aşağıdaki adımlarda gösterilen kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e68e8-106">Add the code shown in the following steps in the generated Program.cs file within the main() method.</span></span>  
  
2. <span data-ttu-id="e68e8-107">Oluşturun <xref:System.ServiceModel.Description.WsdlExporter> .</span><span class="sxs-lookup"><span data-stu-id="e68e8-107">Create a <xref:System.ServiceModel.Description.WsdlExporter>.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#1)]
     [!code-vb[S_UEWsdlExporter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#1)]  
  
3. <span data-ttu-id="e68e8-108"><xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A>Özelliğini Numaralandırmadaki değerlerden birine ayarlayın <xref:System.ServiceModel.Description.PolicyVersion> .</span><span class="sxs-lookup"><span data-stu-id="e68e8-108">Set the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to one of the values from the <xref:System.ServiceModel.Description.PolicyVersion> enumeration.</span></span> <span data-ttu-id="e68e8-109">Bu örnek, <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> WS-Policy 1,5 öğesine karşılık gelen değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e68e8-109">This sample sets the value to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> which corresponds to WS-Policy 1.5.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#2)]
     [!code-vb[S_UEWsdlExporter#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#2)]  
  
4. <span data-ttu-id="e68e8-110">Nesne dizisi oluşturun <xref:System.ServiceModel.Description.ServiceEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="e68e8-110">Create an array of <xref:System.ServiceModel.Description.ServiceEndpoint> objects.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#3)]
     [!code-vb[S_UEWsdlExporter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#3)]  
  
5. <span data-ttu-id="e68e8-111">Her hizmet uç noktası için meta verileri dışarı aktarın.</span><span class="sxs-lookup"><span data-stu-id="e68e8-111">Export metadata for each service endpoint.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#4)]
     [!code-vb[S_UEWsdlExporter#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#4)]  
  
6. <span data-ttu-id="e68e8-112">Dışarı aktarma işlemi sırasında bir hata olmadığından emin olun ve meta verileri alın.</span><span class="sxs-lookup"><span data-stu-id="e68e8-112">Check to make sure no errors occurred during the export process and retrieve the metadata.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#5)]
     [!code-vb[S_UEWsdlExporter#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#5)]  
  
7. <span data-ttu-id="e68e8-113">Artık, yöntemini çağırarak bir dosyaya yazmak gibi meta verileri kullanabilirsiniz <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> .</span><span class="sxs-lookup"><span data-stu-id="e68e8-113">You can now use the metadata, such as write it to a file by calling the <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e68e8-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="e68e8-114">Example</span></span>  
 <span data-ttu-id="e68e8-115">Bu örnek için tam kod listesi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e68e8-115">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[S_UEWsdlExporter#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#0)]
 [!code-vb[S_UEWsdlExporter#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e68e8-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e68e8-116">Compiling the Code</span></span>  
 <span data-ttu-id="e68e8-117">Program.cs Reference System. ServiceModel. dll derlenirken.</span><span class="sxs-lookup"><span data-stu-id="e68e8-117">When compiling Program.cs reference System.ServiceModel.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e68e8-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e68e8-118">See also</span></span>

- [<span data-ttu-id="e68e8-119">Meta Veri Mimarisi Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e68e8-119">Metadata Architecture Overview</span></span>](metadata-architecture-overview.md)
- [<span data-ttu-id="e68e8-120">Meta Verileri Kullanma</span><span class="sxs-lookup"><span data-stu-id="e68e8-120">Using Metadata</span></span>](using-metadata.md)
- [<span data-ttu-id="e68e8-121">Uç Noktalar: Adresler, Bağlamalar ve Anlaşmalar</span><span class="sxs-lookup"><span data-stu-id="e68e8-121">Endpoints: Addresses, Bindings, and Contracts</span></span>](endpoints-addresses-bindings-and-contracts.md)
