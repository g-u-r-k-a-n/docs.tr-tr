---
title: 'Nasıl yapılır: Bir Denetim için Araç Kutusu Bit Eşlemi Sağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Toolbox [Windows Forms], adding bitmaps for custom controls
- custom controls [Windows Forms], Toolbox bitmaps
- bitmaps [Windows Forms], custom controls
ms.assetid: 0ed0840a-616d-41ba-a27d-3573241932ad
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 61f60aaeab904dff80408a1dc46c2882fb5e22b9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458316"
---
# <a name="how-to-provide-a-toolbox-bitmap-for-a-control"></a>Nasıl yapılır: Bir Denetim için Araç Kutusu Bit Eşlemi Sağlama

Denetiminizin Visual Studio **araç kutusunda** görünmesi için özel bir simge olmasını istiyorsanız, <xref:System.Drawing.ToolboxBitmapAttribute>kullanarak belirli bir görüntüyü belirtebilirsiniz. Bu sınıf, diğer sınıflara iliştirebilmeniz için özel bir sınıf türü olan bir *özniteliktir*. Öznitelikler hakkında daha fazla bilgi için bkz C#. Visual Basic veya [öznitelikleri (C#)](../../../csharp/programming-guide/concepts/attributes/index.md) için [özniteliklere genel bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md) .

<xref:System.Drawing.ToolboxBitmapAttribute>kullanarak 16 x 16 piksellik bit eşlem için yolu ve dosya adını belirten bir dize belirtebilirsiniz. Bu bit eşlem daha sonra **araç kutusuna**eklendiğinde denetiminizin yanında görüntülenir. Ayrıca, bir <xref:System.Type>belirtebilirsiniz, bu durumda bu tür ile ilişkili bit eşlem yüklenir. Hem <xref:System.Type> hem de bir dize belirtirseniz, denetim, <xref:System.Type> parametresi tarafından belirtilen türü içeren derlemede dize parametresi tarafından belirtilen ada sahip bir görüntü kaynağı arar.

## <a name="to-specify-a-toolbox-bitmap-for-your-control"></a>Denetiminiz için araç kutusu bit eşlemi belirtmek için

1. Visual Basic için `Class` anahtar sözcüğünden önce ve Visual C#için sınıf bildiriminin üstüne <xref:System.Drawing.ToolboxBitmapAttribute>, denetiminizin sınıf bildirimine ekleyin.

    ```vb
    ' Specifies the bitmap associated with the Button type.
    <ToolboxBitmap(GetType(Button))> Class MyControl1
    ' Specifies a bitmap file.
    End Class
    <ToolboxBitmap("C:\Documents and Settings\Joe\MyPics\myImage.bmp")> _
       Class MyControl2
    End Class
    ' Specifies a type that indicates the assembly to search, and the name
    ' of an image resource to look for.
    <ToolboxBitmap(GetType(MyControl), "MyControlBitmap")> Class MyControl
    End Class
    ```

    ```csharp
    // Specifies the bitmap associated with the Button type.
    [ToolboxBitmap(typeof(Button))]
    class MyControl1 : UserControl
    {
    }
    // Specifies a bitmap file.
    [ToolboxBitmap(@"C:\Documents and Settings\Joe\MyPics\myImage.bmp")]
    class MyControl2 : UserControl
    {
    }
    // Specifies a type that indicates the assembly to search, and the name
    // of an image resource to look for.
    [ToolboxBitmap(typeof(MyControl), "MyControlBitmap")]
    class MyControl : UserControl
    {
    }
    ```

2. Projeyi yeniden derleyin.

    > [!NOTE]
    > Bit eşlem, otomatik olarak oluşturulan denetimler ve bileşenler için araç kutusunda görünmez. Bit eşlemi görmek için **araç kutusu öğelerini Seç** iletişim kutusunu kullanarak denetimi yeniden yükleyin. Daha fazla bilgi için bkz. [Izlenecek yol: araç kutusunu özel bileşenlerle otomatik olarak doldurma](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.ToolboxBitmapAttribute>
- [İzlenecek yol: Araç Kutusunu Otomatik Olarak Özel Bileşenlerle Doldurma](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [Tasarım Zamanında Windows Forms Denetimleri Geliştirme](developing-windows-forms-controls-at-design-time.md)
- [Özniteliklere genel bakış (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Öznitelikler (C#)](../../../csharp/programming-guide/concepts/attributes/index.md)
