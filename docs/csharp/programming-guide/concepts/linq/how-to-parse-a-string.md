---
title: Bir dizeyi ayrıştırma (C#)
description: C# ' de bir XML ağacı oluşturmak için bir dizeyi ayrıştırmayı öğrenin. Ayrıştırılmış XML 'inizdeki belirli verilere nasıl erişebileceğinizi öğrenin.
ms.date: 07/20/2015
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: a4664e090b6a44c52c519e61b66ccdc5d59a71f1
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104811"
---
# <a name="how-to-parse-a-string-c"></a>Bir dizeyi ayrıştırma (C#)

Bu konu başlığı altında, C# ' de bir XML ağacı oluşturmak için bir dizeyi ayrıştırma gösterilmektedir.

## <a name="example"></a>Örnek

Aşağıdaki C# kodu bir XML dizesinin nasıl ayrıştıralınacağını gösterir:

```csharp
XElement contacts = XElement.Parse(
    @"<Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone Type=""home"">206-555-0144</Phone>
            <Phone Type=""work"">425-555-0145</Phone>
            <Address>
            <Street1>123 Main St</Street1>
            <City>Mercer Island</City>
            <State>WA</State>
            <Postal>68042</Postal>
            </Address>
            <NetWorth>10</NetWorth>
        </Contact>
        <Contact>
            <Name>Gretchen Rivas</Name>
            <Phone Type=""mobile"">206-555-0163</Phone>
            <Address>
            <Street1>123 Main St</Street1>
            <City>Mercer Island</City>
            <State>WA</State>
            <Postal>68042</Postal>
            </Address>
            <NetWorth>11</NetWorth>
        </Contact>
    </Contacts>");
Console.WriteLine(contacts);
```

Kök `Contacts` düğümün iki düğümü vardır `Contact` . Ayrıştırılmış XML 'inizdeki bazı belirli verilere erişmek için, bu örnekte kök düğümün alt öğelerini döndüren [XElement. Elements ()](xref:System.Xml.Linq.XContainer.Elements) yöntemini kullanın `Contacts` . Aşağıdaki örnek, `Contact` konsola ilk düğümü yazdırır:

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```

## <a name="see-also"></a>Ayrıca bkz.

- [Belirli bir özniteliğe sahip bir öğe bulma (C#)](how-to-find-an-element-with-a-specific-attribute.md)
