---
title: XmlSerializer ile Özel Serileştirme Düzeni
ms.date: 03/30/2017
ms.assetid: 975abd20-2a1d-42db-aed3-e898025ccce7
ms.openlocfilehash: c5934fd0cab03f754784c8515094ff4ec5e78ba4
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490926"
---
# <a name="custom-serialization-order-with-xmlserializer"></a><span data-ttu-id="7f2b9-102">XmlSerializer ile Özel Serileştirme Düzeni</span><span class="sxs-lookup"><span data-stu-id="7f2b9-102">Custom Serialization Order With XmlSerializer</span></span>
[<span data-ttu-id="7f2b9-103">Örnek indir</span><span class="sxs-lookup"><span data-stu-id="7f2b9-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/CustomOrder.zip.exe)  
  
 <span data-ttu-id="7f2b9-104">Bu örnek, XML serileştirme için serileştirilmiş ve seri durumdan çıkarılan öğelerin sırasının nasıl kontrol edilmesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7f2b9-104">This sample shows how to control the order of serialized and deserialized elements for XML serialization.</span></span>  
  
 <span data-ttu-id="7f2b9-105">Serileştirme hakkında daha fazla bilgi için kaynak kodu ve build.proj dosyalarını yorumlarda inceleyin.</span><span class="sxs-lookup"><span data-stu-id="7f2b9-105">Review comments in the source code and build.proj files for more information on serialization.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="7f2b9-106">Komut istemi kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7f2b9-106">To build the sample using the Command Prompt</span></span>  
  
1. <span data-ttu-id="7f2b9-107">Komut istemi açın ve örnek için dile özgü alt birine gidin.</span><span class="sxs-lookup"><span data-stu-id="7f2b9-107">Open the Command Prompt window and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2. <span data-ttu-id="7f2b9-108">Komut satırına **MSBuild CustomOrder. sln** yazın.</span><span class="sxs-lookup"><span data-stu-id="7f2b9-108">Type **msbuild CustomOrder.sln** at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="7f2b9-109">Visual Studio kullanarak örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7f2b9-109">To build the sample using Visual Studio</span></span>  
  
1. <span data-ttu-id="7f2b9-110">Dosya Gezgini 'ni açın ve örnek için dile özgü alt dizinlerden birine gidin.</span><span class="sxs-lookup"><span data-stu-id="7f2b9-110">Open File Explorer and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2. <span data-ttu-id="7f2b9-111">Visual Studio'da dosyayı açmak CustomOrder.sln simgesini çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="7f2b9-111">Double-click the icon for the CustomOrder.sln to open the file in Visual Studio.</span></span>  
  
3. <span data-ttu-id="7f2b9-112">**Build** menüsünde **Build Solution**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="7f2b9-112">In the **Build** menu, select **Build Solution**.</span></span>  
  
4. <span data-ttu-id="7f2b9-113">Uygulama örneği varsayılan \bin veya \bin\debug'dır alt üzerine inşa edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7f2b9-113">The sample application is built in the default \bin or \bin\Debug subdirectory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f2b9-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f2b9-114">See also</span></span>

- [<span data-ttu-id="7f2b9-115">Temel serileştirme</span><span class="sxs-lookup"><span data-stu-id="7f2b9-115">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)
- [<span data-ttu-id="7f2b9-116">İkili serileştirme</span><span class="sxs-lookup"><span data-stu-id="7f2b9-116">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)
- [<span data-ttu-id="7f2b9-117">Öznitelikleri Kullanarak XML Serileştirmeyi Denetleme</span><span class="sxs-lookup"><span data-stu-id="7f2b9-117">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)
- [<span data-ttu-id="7f2b9-118">XML Serileştirmeye Giriş</span><span class="sxs-lookup"><span data-stu-id="7f2b9-118">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="7f2b9-119">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="7f2b9-119">Serialization</span></span>](../../../docs/standard/serialization/index.md)
- [<span data-ttu-id="7f2b9-120">XML ve SOAP serileştirme</span><span class="sxs-lookup"><span data-stu-id="7f2b9-120">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
