---
title: DomainUpDown Denetimlerine Programlı Olarak Öğe Ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- spin button control [Windows Forms], adding items
- DomainUpDown control [Windows Forms], adding items to
ms.assetid: fd31d314-33eb-4181-90f8-d32ed0c4e072
ms.openlocfilehash: 2e9f51fa051bf9b62e95f289db97bffd83450036
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745587"
---
# <a name="how-to-add-items-to-windows-forms-domainupdown-controls-programmatically"></a>Nasıl yapılır: Windows Forms DomainUpDown Denetimlerine Programlı Olarak Öğe Ekleme
Kodda Windows Forms <xref:System.Windows.Forms.DomainUpDown> denetimine öğe ekleyebilirsiniz. Denetimin <xref:System.Windows.Forms.DomainUpDown.Items%2A> özelliğine öğe eklemek için <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> sınıfının <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> veya <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> yöntemini çağırın. <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> yöntemi bir koleksiyonun sonuna bir öğe ekler, ancak <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> yöntemi belirtilen konuma bir öğe ekler.  
  
### <a name="to-add-a-new-item"></a>Yeni bir öğe eklemek için  
  
1. Öğe listesinin sonuna bir öğe eklemek için <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> yöntemini kullanın.  
  
    ```vb  
    DomainUpDown1.Items.Add("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Add("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Add("noodles");  
    ```  
  
     veya  
  
2. Belirli bir konumdaki listeye bir öğe eklemek için <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> yöntemini kullanın.  
  
    ```vb  
    ' Inserts an item at the third position in the list  
    DomainUpDown1.Items.Insert(2, "rice")  
    ```  
  
    ```csharp  
    // Inserts an item at the third position in the list  
    domainUpDown1.Items.Insert(2, "rice");  
    ```  
  
    ```cpp  
    // Inserts an item at the third position in the list  
    domainUpDown1->Items->Insert(2, "rice");  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DomainUpDown>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A?displayProperty=nameWithType>
- <xref:System.Collections.ArrayList.Insert%2A?displayProperty=nameWithType>
- [DomainUpDown Denetimi](domainupdown-control-windows-forms.md)
- [DomainUpDown Denetimine Genel Bakış](domainupdown-control-overview-windows-forms.md)
