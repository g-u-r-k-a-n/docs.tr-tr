---
title: 'Nasıl yapılır: bir nesneyi seri hale getirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.assetid: a1207d05-32b2-4953-8582-959607991227
ms.openlocfilehash: 3e24d890d47747c51086214530073fc551321079
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159890"
---
# <a name="how-to-serialize-an-object"></a><span data-ttu-id="64865-102">Nasıl yapılır: bir nesneyi seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="64865-102">How to: Serialize an Object</span></span>
<span data-ttu-id="64865-103">Bir nesneyi serileştirmek için önce sıralanabilir ve ortak özelliklerini ve alanları ayarlamak için olan nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="64865-103">To serialize an object, first create the object that is to be serialized and set its public properties and fields.</span></span> <span data-ttu-id="64865-104">Bunu yapmak için, XML akışının, akış olarak veya dosya olarak depolanacağı aktarım biçimini belirlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="64865-104">To do this, you must determine the transport format in which the XML stream is to be stored, either as a stream or as a file.</span></span> <span data-ttu-id="64865-105">Örneğin, XML akışının kalıcı bir biçimde kaydedilmesi gerekiyorsa <xref:System.IO.FileStream> nesnesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="64865-105">For example, if the XML stream must be saved in a permanent form, create a <xref:System.IO.FileStream> object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="64865-106">XML serileştirme hakkında daha fazla örnek için bkz. [XML serileştirme örnekleri](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="64865-106">For more examples of XML serialization, see [Examples of XML Serialization](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object"></a><span data-ttu-id="64865-107">Bir nesneyi serileştirmek için</span><span class="sxs-lookup"><span data-stu-id="64865-107">To serialize an object</span></span>  
  
1. <span data-ttu-id="64865-108">Nesne oluşturun ve kendi ortak alanları ve özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="64865-108">Create the object and set its public fields and properties.</span></span>  
  
2. <span data-ttu-id="64865-109">Nesnenin türünü kullanarak bir <xref:System.Xml.Serialization.XmlSerializer> oluşturun.</span><span class="sxs-lookup"><span data-stu-id="64865-109">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object.</span></span> <span data-ttu-id="64865-110">Daha fazla bilgi için <xref:System.Xml.Serialization.XmlSerializer> Sınıf oluşturucuları ' ne bakın.</span><span class="sxs-lookup"><span data-stu-id="64865-110">For more information, see the <xref:System.Xml.Serialization.XmlSerializer> class constructors.</span></span>  
  
3. <span data-ttu-id="64865-111">Nesnenin ortak özelliklerinin ve alanlarının bir XML akışını veya bir dosya gösterimini oluşturmak için <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="64865-111">Call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> method to generate either an XML stream or a file representation of the object's public properties and fields.</span></span> <span data-ttu-id="64865-112">Aşağıdaki örnek, bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="64865-112">The following example creates a file.</span></span>  
  
    ```vb  
    Dim myObject As MySerializableClass = New MySerializableClass()  
    ' Insert code to set properties and fields of the object.  
    Dim mySerializer As XmlSerializer = New XmlSerializer(GetType(MySerializableClass))  
    ' To write to a file, create a StreamWriter object.  
    Dim myWriter As StreamWriter = New StreamWriter("myFileName.xml")  
    mySerializer.Serialize(myWriter, myObject)  
    myWriter.Close()  
    ```  
  
    ```csharp  
    MySerializableClass myObject = new MySerializableClass();  
    // Insert code to set properties and fields of the object.  
    XmlSerializer mySerializer = new
    XmlSerializer(typeof(MySerializableClass));  
    // To write to a file, create a StreamWriter object.  
    StreamWriter myWriter = new StreamWriter("myFileName.xml");  
    mySerializer.Serialize(myWriter, myObject);  
    myWriter.Close();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="64865-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64865-113">See also</span></span>

- [<span data-ttu-id="64865-114">XML Serileştirmeye Giriş</span><span class="sxs-lookup"><span data-stu-id="64865-114">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="64865-115">Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="64865-115">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
