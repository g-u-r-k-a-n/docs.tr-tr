---
title: Koordinat Sistemi Türleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], page
- unit of measure
- world coordinate system
- page coordinate system
- page transformation
- device coordinate system
- world transformation
- coordinate systems
- transformations [Windows Forms], world
ms.assetid: c61ff50a-eb1d-4e6c-83cd-f7e9764cfa9f
ms.openlocfilehash: bbb0d4908d4a281499336d262c653d7b72f3ccdc
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159812"
---
# <a name="types-of-coordinate-systems"></a>Koordinat Sistemi Türleri
GDI+ üç koordinat alanı kullanır: Dünya, sayfa ve cihaz. Dünya koordinatları, belirli bir grafik dünyasını modellemek için kullanılan koordinatlardır ve .NET Framework yöntemlere geçirdiğiniz koordinatlardır. Sayfa koordinatları, bir form veya denetim gibi bir çizim yüzeyi tarafından kullanılan koordinat sistemine başvurur. Cihaz koordinatları, bir ekran veya kağıt sayfası gibi, üzerine çizilmiş fiziksel cihaz tarafından kullanılan koordinatlardır. `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`çağrısı yaptığınızda, <xref:System.Drawing.Graphics.DrawLine%2A> yöntemine geçirdiğiniz noktaları —`(0, 0)` ve `(160, 80)`— dünya koordinat alanında olur. GDI+, ekranda çizgi çizmeden önce koordinatları bir dizi dönüşümden geçer. Dünya dönüşümü olarak adlandırılan bir dönüşüm, dünya koordinatlarını sayfa koordinatlarına dönüştürür ve sayfa dönüşümü olarak adlandırılan başka bir dönüşüm, sayfa koordinatlarını cihaz koordinatlarına dönüştürür.  
  
## <a name="transforms-and-coordinate-systems"></a>Sistemleri dönüştürür ve koordine et  
 Sol üst köşede değil, istemci alanının gövdesinde kaynağına sahip bir koordinat sistemiyle çalışmak istediğinizi varsayalım. Örneğin, kaynağın, istemci alanının sol kenarından 100 piksel olmasını istediğinizi ve istemci alanının en üstünde 50 pikseli olduğunu varsayalım. Aşağıdaki çizimde bu tür bir koordinat sistemi gösterilmektedir.  
  
 ![Koordinat sistemi](./media/aboutgdip05-art01.gif "AboutGdip05_art01")  
  
 `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`çağrısı yaptığınızda aşağıdaki çizimde gösterilen satırı alırsınız.  
  
 ![Koordinat sistemi](./media/aboutgdip05-art02.gif "AboutGdip05_art02")  
  
 Üç koordinat alanındaki satırlarınızın uç noktaların koordinatları aşağıdaki gibidir:  
  
|||  
|-|-|  
|Dünya|(0, 0)-(160, 80)|  
|Sayfasında|(100, 50)-(260, 130)|  
|Cihaz|(100, 50)-(260, 130)|  
  
 Sayfa koordinat alanının, istemci alanının sol üst köşesinde bulunan kaynağı olduğunu unutmayın; Bu durum her zaman olur. Ayrıca, ölçü birimi piksel olduğundan, cihaz koordinatları sayfa koordinatlarıyla aynı olduğunu unutmayın. Ölçü birimini piksel dışında bir değere ayarlarsanız (örneğin, inç), cihaz koordinatları sayfa koordinatlarından farklı olacaktır.  
  
 Dünya koordinatlarını sayfa koordinatlarına eşleyen dünya dönüştürmesi, <xref:System.Drawing.Graphics> sınıfının <xref:System.Drawing.Graphics.Transform%2A> özelliğinde tutulur. Yukarıdaki örnekte, World Transformation, y yönünde x Direction ve 50 birimlerindeki çeviri 100 birimleridir. Aşağıdaki örnek, bir <xref:System.Drawing.Graphics> nesnesinin dünya dönüşümünü ayarlar ve ardından bu <xref:System.Drawing.Graphics> nesnesini kullanarak önceki şekilde gösterilen satırı çizer:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 Sayfa dönüştürme sayfa koordinatlarını cihaz koordinatlarına eşler. <xref:System.Drawing.Graphics> sınıfı, sayfa dönüşümünü işlemek için <xref:System.Drawing.Graphics.PageUnit%2A> ve <xref:System.Drawing.Graphics.PageScale%2A> özellikleri sağlar. <xref:System.Drawing.Graphics> sınıfı ayrıca, görüntüleme cihazının yatay ve dikey noktaların incelenmesiyle ilgili <xref:System.Drawing.Graphics.DpiX%2A> ve <xref:System.Drawing.Graphics.DpiY%2A>iki salt okuma özelliği de sağlar.  
  
 <xref:System.Drawing.Graphics> sınıfının <xref:System.Drawing.Graphics.PageUnit%2A> özelliğini kullanarak, pikselden farklı bir ölçü birimi belirtebilirsiniz.  
  
> [!NOTE]
> Bu fiziksel bir birim olmadığından ve bir özel duruma neden olacağı için <xref:System.Drawing.Graphics.PageUnit%2A> özelliğini <xref:System.Drawing.GraphicsUnit.World>ayarlayamazsınız.  
  
 Aşağıdaki örnek (0, 0) ile (2, 1) arasında bir çizgi çizer, burada nokta (2, 1), nokta (0, 0) ile sağ ve 1 inç arasında 2 ' dir:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
> Kaleminizi oluştururken bir kalem genişliği belirtmezseniz, yukarıdaki örnek bir inç genişliğinde bir çizgi çizer. <xref:System.Drawing.Pen> oluşturucusuna ikinci bağımsız değişkende kalem genişliğini belirtebilirsiniz:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 Görüntü cihazının yatay yönde 96 nokta ve dikey yönde 96 nokta/inç olduğunu varsaydığımızda, önceki örnekteki satırın uç noktaları üç koordinat alanında aşağıdaki koordinatlara sahiptir:  
  
|||  
|-|-|  
|Dünya|(0, 0)-(2, 1)|  
|Sayfasında|(0, 0)-(2, 1)|  
|Cihaz|(0, 0)-(192, 96)|  
  
 Dünya koordinat alanının kaynağı istemci alanının sol üst köşesinde olduğundan, sayfa koordinatları dünyanın koordinatlarıyla aynı olur.  
  
 Çeşitli etkilere ulaşmak için dünya ve sayfa dönüştürmelerini birleştirebilirsiniz. Örneğin, ölçü birimi olarak inç kullanmak istediğinizi ve koordinat sisteminizin kaynağının, istemci alanının sol kenarından 2 cm ve istemci alanının en üstünden 1/2 inç olmasını istediğinizi varsayalım. Aşağıdaki örnek, bir <xref:System.Drawing.Graphics> nesnesinin dünya ve sayfa dönüştürmelerini ayarlar ve (0, 0) öğesinden (2, 1) bir çizgi çizer:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 Aşağıdaki çizimde çizgi ve koordinat sistemi gösterilmektedir.  
  
 ![Koordinat sistemi](./media/aboutgdip05-art03.gif "AboutGdip05_art03")  
  
 Görüntü cihazının yatay yönde 96 nokta ve dikey yönde 96 nokta/inç olduğunu varsaydığımızda, önceki örnekteki satırın uç noktaları üç koordinat alanında aşağıdaki koordinatlara sahiptir:  
  
|||  
|-|-|  
|Dünya|(0, 0)-(2, 1)|  
|Sayfasında|(2, 0,5)-(4, 1,5)|  
|Cihaz|(192, 48)-(384, 144)|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Koordinat Sistemleri ve Dönüştürmeler](coordinate-systems-and-transformations.md)
- [Dönüşümlerin Matrisle Temsili](matrix-representation-of-transformations.md)
