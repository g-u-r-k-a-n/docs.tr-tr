---
title: 'Nasıl yapılır: Metinle Düzgünleştirme Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [Windows Forms], smoothing drawn
- antialiasing [Windows Forms], using with text
- text [Windows Forms], smoothing
- text [Windows Forms], antialiasing
- strings [Windows Forms], antialiasing when drawing
ms.assetid: 48fc34f3-f236-4b01-a0cb-f0752e6d22ae
ms.openlocfilehash: 632ed329173d134495a424b34ca7c71e402607bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182480"
---
# <a name="how-to-use-antialiasing-with-text"></a><span data-ttu-id="e377c-102">Nasıl yapılır: Metinle Düzgünleştirme Kullanma</span><span class="sxs-lookup"><span data-stu-id="e377c-102">How to: Use Antialiasing with Text</span></span>
<span data-ttu-id="e377c-103">*Antialiasing,* görünümlerini veya okunabilirliklerini geliştirmek için çizilen grafiklerin ve metnin pürüzlü kenarlarının düzgünlemesi anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e377c-103">*Antialiasing* refers to the smoothing of jagged edges of drawn graphics and text to improve their appearance or readability.</span></span> <span data-ttu-id="e377c-104">Yönetilen GDI+ sınıfları ile yüksek kaliteli antialiased metin ve daha düşük kaliteli metin işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e377c-104">With the managed GDI+ classes, you can render high quality antialiased text, as well as lower quality text.</span></span> <span data-ttu-id="e377c-105">Genellikle, daha yüksek kaliteli işleme, daha düşük kaliteli işleme daha fazla işlem süresi alır.</span><span class="sxs-lookup"><span data-stu-id="e377c-105">Typically, higher quality rendering takes more processing time than lower quality rendering.</span></span> <span data-ttu-id="e377c-106">Metin kalite düzeyini ayarlamak için, a'nın <xref:System.Drawing.Graphics.TextRenderingHint%2A> <xref:System.Drawing.Graphics> özelliğini numaralandırmanın öğelerinden <xref:System.Drawing.Text.TextRenderingHint> birine ayarlayın</span><span class="sxs-lookup"><span data-stu-id="e377c-106">To set the text quality level, set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property of a <xref:System.Drawing.Graphics> to one of the elements of the <xref:System.Drawing.Text.TextRenderingHint> enumeration</span></span>  
  
## <a name="example"></a><span data-ttu-id="e377c-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="e377c-107">Example</span></span>  
 <span data-ttu-id="e377c-108">Aşağıdaki kod örneği, iki farklı kalite ayarı içeren metin çizer.</span><span class="sxs-lookup"><span data-stu-id="e377c-108">The following code example draws text with two different quality settings.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  

 <span data-ttu-id="e377c-109">Aşağıdaki resimde örnek kodun çıktısı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="e377c-109">The following illustration shows the output of the example code:</span></span>  
  
 ![İki farklı kalite ayarı olan metni gösteren ekran görüntüsü.](./media/how-to-use-antialiasing-with-text/antialiasing-text-quality-settings.png)  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e377c-111">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e377c-111">Compiling the Code</span></span>  
 <span data-ttu-id="e377c-112">Önceki kod örneği Windows Formlar ile kullanılmak üzere <xref:System.Windows.Forms.PaintEventArgs> `e`tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventHandler>, hangi bir parametre .</span><span class="sxs-lookup"><span data-stu-id="e377c-112">The preceding code example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e377c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e377c-113">See also</span></span>

- [<span data-ttu-id="e377c-114">Yazı Tipleri ve Metin Kullanma</span><span class="sxs-lookup"><span data-stu-id="e377c-114">Using Fonts and Text</span></span>](using-fonts-and-text.md)
