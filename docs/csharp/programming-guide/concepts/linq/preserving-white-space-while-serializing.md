---
title: Serializing3 sırasında boşluk koruma
description: XElement ve XDocument sınıflarında yöntemleri kullanarak bir XML ağacını serileştirilirken boşluk denetimini nasıl denetleyeceğinizi öğrenin.
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 01e68671e2fde1a2b5b1d0bc429841077ba0205f
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303419"
---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="4ce00-103">Serileştirirken Boşlukları Koruma</span><span class="sxs-lookup"><span data-stu-id="4ce00-103">Preserving White Space While Serializing</span></span>
<span data-ttu-id="4ce00-104">Bu konu, bir XML ağacı serileştirilirken boşluk denetimini nasıl denetleyebileceğinizi açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="4ce00-104">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="4ce00-105">Yaygın bir senaryo, girintili XML 'yi okumak, boşluk metin düğümleri olmadan bellek içi XML ağacı oluşturmaktır (diğer bir deyişle, beyaz alanı korumadan), XML üzerinde bazı işlemler gerçekleştirir ve ardından XML 'i girintilemeli olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="4ce00-105">A common scenario is to read indented XML, create an in-memory XML tree without any white-space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="4ce00-106">XML 'yi biçimlendirme ile serileştirçalıştığınızda, XML ağacında yalnızca önemli boşluk korunur.</span><span class="sxs-lookup"><span data-stu-id="4ce00-106">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="4ce00-107">Bu varsayılan davranıştır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4ce00-107">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="4ce00-108">Diğer bir yaygın senaryo, daha önce kasıtlı olarak girintili olan XML 'i okuyup değiştirmektir.</span><span class="sxs-lookup"><span data-stu-id="4ce00-108">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="4ce00-109">Bu Girintiyi istediğiniz şekilde değiştirmek istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ce00-109">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="4ce00-110">Bunu yapmak için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , XML 'i yüklediğinizde veya ayrıştırdığınızda veya XML 'yi seri hale alırken biçimlendirmeyi devre dışı bıraktığınızda boşluğu koruyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ce00-110">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="4ce00-111">XML ağaçlarını seri hale getirme yöntemlerinin beyaz boşluk davranışı</span><span class="sxs-lookup"><span data-stu-id="4ce00-111">White-Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="4ce00-112"><xref:System.Xml.Linq.XElement>Ve sınıflarında aşağıdaki yöntemler <xref:System.Xml.Linq.XDocument> bir xml ağacını serileştirin.</span><span class="sxs-lookup"><span data-stu-id="4ce00-112">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="4ce00-113">Bir XML ağacını bir dosyaya, a 'ya veya bir dosyasına seri hale getirebilirsiniz <xref:System.IO.TextReader> <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="4ce00-113">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="4ce00-114">`ToString`Yöntemi bir dizeye seri hale getirir.</span><span class="sxs-lookup"><span data-stu-id="4ce00-114">The `ToString` method serializes to a string.</span></span>  
  
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
- [<span data-ttu-id="4ce00-115">XElement. ToString ()</span><span class="sxs-lookup"><span data-stu-id="4ce00-115">XElement.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
- [<span data-ttu-id="4ce00-116">XDocument. ToString ()</span><span class="sxs-lookup"><span data-stu-id="4ce00-116">XDocument.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
 <span data-ttu-id="4ce00-117">Yöntem <xref:System.Xml.Linq.SaveOptions> bir bağımsız değişken olarak kullanmıyorsa, yöntemi SERILEŞTIRILMIŞ XML 'i biçimlendirir (girintili).</span><span class="sxs-lookup"><span data-stu-id="4ce00-117">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="4ce00-118">Bu durumda, XML ağacındaki tüm önemli boşluklar atılır.</span><span class="sxs-lookup"><span data-stu-id="4ce00-118">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="4ce00-119">Yöntemi <xref:System.Xml.Linq.SaveOptions> bir bağımsız değişken olarak ele alıyorsa, yöntemin SERILEŞTIRILMIŞ XML 'yi biçimlendirme (girintileme) seçeneğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ce00-119">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="4ce00-120">Bu durumda, XML ağacındaki tüm boşluklar korunur.</span><span class="sxs-lookup"><span data-stu-id="4ce00-120">In this case, all white space in the XML tree is preserved.</span></span>  
