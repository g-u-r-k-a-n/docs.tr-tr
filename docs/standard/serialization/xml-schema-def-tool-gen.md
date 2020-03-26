---
title: 'Nasıl yapılır: Sınıflar ve XML Şeması Belgeleri Oluşturmak için XML Şema Tanımı Aracını Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- generating XML classes using XML Schema Definition tool
- generating XML Schema Document using XML Schema Definition tool
- XML Schema Definition tool, using to generate classes that conform to specific schema
- XML Schema Definition tool, using to generate XML Schema Document
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
ms.openlocfilehash: 4c6996e2279693cf96c826741869d72007cf81cf
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249558"
---
# <a name="how-to-use-the-xml-schema-definition-tool-to-generate-classes-and-xml-schema-documents"></a><span data-ttu-id="b04c8-102">Nasıl yapılır: Sınıflar ve XML Şeması Belgeleri Oluşturmak için XML Şema Tanımı Aracını Kullanma</span><span class="sxs-lookup"><span data-stu-id="b04c8-102">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>
<span data-ttu-id="b04c8-103">XML şema tanımı Aracı (XSD.exe'nin), bir sınıf açıklayan bir XML şeması oluşturmak veya bir XML şeması tarafından tanımlanan sınıfı oluşturmak için sağlar.</span><span class="sxs-lookup"><span data-stu-id="b04c8-103">The XML Schema Definition tool (Xsd.exe) allows you to generate an XML schema that describes a class or to generate the class defined by an XML schema.</span></span> <span data-ttu-id="b04c8-104">Aşağıdaki yordamlar bu işlemleri gerçekleştirmek nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="b04c8-104">The following procedures show how to perform these operations.</span></span>  
  
### <a name="to-generate-classes-that-conform-to-a-specific-schema"></a><span data-ttu-id="b04c8-105">Belirli bir şemaya uygun sınıflar oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b04c8-105">To generate classes that conform to a specific schema</span></span>  
  
1. <span data-ttu-id="b04c8-106">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="b04c8-106">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="b04c8-107">XML şeması için XML Şeması, örneğin tam olarak eşleştirilir sınıf kümesi oluşturur XML şema tanımı aracı için bağımsız değişken olarak geçir:</span><span class="sxs-lookup"><span data-stu-id="b04c8-107">Pass the XML Schema as an argument to the XML Schema Definition tool, which creates a set of classes that are precisely matched to the XML Schema, for example:</span></span>  
  
    ```console  
    xsd mySchema.xsd  
    ```  
  
     <span data-ttu-id="b04c8-108">Araç yalnızca 16 Mart 2001 World Wide Web Consortium XML belirtimi başvuran şemaları işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="b04c8-108">The tool can only process schemas that reference the World Wide Web Consortium XML specification of March 16, 2001.</span></span> <span data-ttu-id="b04c8-109">Başka bir deyişle, XML Şema adhttp://www.w3.org/2001/XMLSchemaalanı aşağıdaki örnekte gösterildiği gibi " " olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b04c8-109">In other words, the XML Schema namespace must be "http://www.w3.org/2001/XMLSchema" as shown in the following example.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema" />  
    ```  
  
3. <span data-ttu-id="b04c8-110">Yöntemler, özellikler veya alanları, sınıflar gerektiği şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b04c8-110">Modify the classes with methods, properties, or fields, as necessary.</span></span> <span data-ttu-id="b04c8-111">Özniteliklerle bir sınıfı değiştirme hakkında daha fazla bilgi için bkz: [Kodlanmış SOAP Serileştirmeyi Kontrol Eden](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)Öznitelikleri ve Öznitelikleri [Kullanarak XML Serileştirmeyi Denetleme.](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)</span><span class="sxs-lookup"><span data-stu-id="b04c8-111">For more information about modifying a class with attributes, see [Controlling XML Serialization Using Attributes](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) and [Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
 <span data-ttu-id="b04c8-112">Genellikle bir sınıfın (veya sınıfların) örnekleri seri hale geldiğinde oluşturulan XML akışının şemasını incelemek yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="b04c8-112">It is often useful to examine the schema of the XML stream that is generated when instances of a class (or classes) are serialized.</span></span> <span data-ttu-id="b04c8-113">Örneğin, şemanızı başkalarının kullanması için yayımlayabilir veya uygunluk elde etmeye çalıştığınız şema ile karşılaştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b04c8-113">For example, you might publish your schema for others to use, or you might compare it to a schema with which you are trying to achieve conformity.</span></span>  
  
#### <a name="to-generate-an-xml-schema-document-from-a-set-of-classes"></a><span data-ttu-id="b04c8-114">Bir XML Şeması belge sınıfları kümesinden oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b04c8-114">To generate an XML Schema document from a set of classes</span></span>  
  
1. <span data-ttu-id="b04c8-115">Sınıf veya sınıfların bir DLL içine derleyin.</span><span class="sxs-lookup"><span data-stu-id="b04c8-115">Compile the class or classes into a DLL.</span></span>  
  
2. <span data-ttu-id="b04c8-116">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="b04c8-116">Open a command prompt.</span></span>  
  
3. <span data-ttu-id="b04c8-117">DLL bağımsız değişken olarak XSD.exe'nin için örneğin Geçir:</span><span class="sxs-lookup"><span data-stu-id="b04c8-117">Pass the DLL as an argument to Xsd.exe, for example:</span></span>  
  
    ```console  
    xsd MyFile.dll  
    ```  
  
     <span data-ttu-id="b04c8-118">Şema (veya şemaları) adı "schema0.xsd" ile başlayan yazılır.</span><span class="sxs-lookup"><span data-stu-id="b04c8-118">The schema (or schemas) will be written, beginning with the name "schema0.xsd".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b04c8-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b04c8-119">See also</span></span>

- <xref:System.Data.DataSet>
- [<span data-ttu-id="b04c8-120">XML Şema Tanımı Aracı ve XML Serileştirme</span><span class="sxs-lookup"><span data-stu-id="b04c8-120">The XML Schema Definition Tool and XML Serialization</span></span>](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)
- [<span data-ttu-id="b04c8-121">XML Serileştirmeye Giriş</span><span class="sxs-lookup"><span data-stu-id="b04c8-121">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="b04c8-122">XML şema tanımı Aracı (XSD.exe'nin)</span><span class="sxs-lookup"><span data-stu-id="b04c8-122">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="b04c8-123">Nasıl yapılır: Nesne Serileştirme</span><span class="sxs-lookup"><span data-stu-id="b04c8-123">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [<span data-ttu-id="b04c8-124">Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="b04c8-124">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
