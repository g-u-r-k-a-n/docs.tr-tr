---
title: 'Nasıl yapılır: Nesne Serileştirme'
description: Bu makalede bir nesnenin serileştirilme yöntemi gösterilmektedir. XML akışının, akış olarak veya dosya olarak depolandığı bir aktarım biçimi seçin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.assetid: a1207d05-32b2-4953-8582-959607991227
ms.openlocfilehash: ce8510a987f75ed4110a44ffa9f2ac813d36a5be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678902"
---
# <a name="how-to-serialize-an-object"></a>Nasıl yapılır: Nesne Serileştirme

Bir nesneyi serileştirmek için önce sıralanabilir ve ortak özelliklerini ve alanları ayarlamak için olan nesne oluşturun. Bunu yapmak için, XML akışının, akış olarak veya dosya olarak depolanacağı aktarım biçimini belirlemelisiniz. Örneğin, XML akışının kalıcı bir biçimde kaydedilmesi gerekiyorsa, bir <xref:System.IO.FileStream> nesne oluşturun.  
  
> [!NOTE]
> XML serileştirme hakkında daha fazla örnek için bkz. [XML serileştirme örnekleri](examples-of-xml-serialization.md).  
  
### <a name="to-serialize-an-object"></a>Bir nesneyi serileştirmek için  
  
1. Nesne oluşturun ve kendi ortak alanları ve özelliklerini ayarlayın.  
  
2. <xref:System.Xml.Serialization.XmlSerializer>Nesnesinin türünü kullanarak bir oluşturun. Daha fazla bilgi için bkz <xref:System.Xml.Serialization.XmlSerializer> . sınıf oluşturucuları.  
  
3. <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A>BIR XML akışı veya nesnenin ortak özelliklerinin ve alanlarının dosya gösterimini oluşturmak için yöntemini çağırın. Aşağıdaki örnek, bir dosya oluşturur.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Serileştirmeye Giriş](introducing-xml-serialization.md)
- [Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma](how-to-deserialize-an-object.md)
