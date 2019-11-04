---
title: 'Nasıl yapılır: Görüntülerdeki Alfa Değerleri Ayarlamak için Renk Matrisi Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using color matrices for semi-transparent
- transparency [Windows Forms], color matrices
- matrices [Windows Forms], alpha values
- bitmaps [Windows Forms], using color matrices for semi-transparent
ms.assetid: a27121e6-f7e9-4c09-84e2-f05aa9d2a1bb
ms.openlocfilehash: 73e820845d040856a0ae367da8b9371ad6afa142
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423730"
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a><span data-ttu-id="556a0-102">Nasıl yapılır: Görüntülerdeki Alfa Değerleri Ayarlamak için Renk Matrisi Kullanma</span><span class="sxs-lookup"><span data-stu-id="556a0-102">How to: Use a Color Matrix to Set Alpha Values in Images</span></span>
<span data-ttu-id="556a0-103"><xref:System.Drawing.Bitmap> sınıfı (<xref:System.Drawing.Image> sınıfından devralan) ve <xref:System.Drawing.Imaging.ImageAttributes> sınıfı, piksel değerlerini almak ve ayarlamak için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="556a0-103">The <xref:System.Drawing.Bitmap> class (which inherits from the <xref:System.Drawing.Image> class) and the <xref:System.Drawing.Imaging.ImageAttributes> class provide functionality for getting and setting pixel values.</span></span> <span data-ttu-id="556a0-104">Tüm görüntünün Alfa değerlerini değiştirmek için <xref:System.Drawing.Imaging.ImageAttributes> sınıfını kullanabilir veya tek tek piksel değerlerini değiştirmek için <xref:System.Drawing.Bitmap> sınıfının <xref:System.Drawing.Bitmap.SetPixel%2A> yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="556a0-104">You can use the <xref:System.Drawing.Imaging.ImageAttributes> class to modify the alpha values for an entire image, or you can call the <xref:System.Drawing.Bitmap.SetPixel%2A> method of the <xref:System.Drawing.Bitmap> class to modify individual pixel values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="556a0-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="556a0-105">Example</span></span>  
 <span data-ttu-id="556a0-106"><xref:System.Drawing.Imaging.ImageAttributes> sınıfı, işleme sırasında görüntüleri değiştirmek için kullanabileceğiniz birçok özelliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="556a0-106">The <xref:System.Drawing.Imaging.ImageAttributes> class has many properties that you can use to modify images during rendering.</span></span> <span data-ttu-id="556a0-107">Aşağıdaki örnekte, bir <xref:System.Drawing.Imaging.ImageAttributes> nesnesi, tüm Alfa değerlerini ne gibi bir yüzde 80 ' e ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="556a0-107">In the following example, an <xref:System.Drawing.Imaging.ImageAttributes> object is used to set all the alpha values to 80 percent of what they were.</span></span> <span data-ttu-id="556a0-108">Bu, bir renk matrisi başlatarak ve Matristeki Alfa ölçekleme değeri 0,8 olarak ayarlanarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="556a0-108">This is done by initializing a color matrix and setting the alpha scaling value in the matrix to 0.8.</span></span> <span data-ttu-id="556a0-109">Renk matrisinin adresi <xref:System.Drawing.Imaging.ImageAttributes> nesnesinin <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> yöntemine geçirilir ve <xref:System.Drawing.Imaging.ImageAttributes> nesnesi <xref:System.Drawing.Graphics> nesnesinin <xref:System.Drawing.Graphics.DrawString%2A> yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="556a0-109">The address of the color matrix is passed to the <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> method of the <xref:System.Drawing.Imaging.ImageAttributes> object, and the <xref:System.Drawing.Imaging.ImageAttributes> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="556a0-110">Oluşturma sırasında, bit eşlemdeki alfa değerleri, ne olduğu konusunda yüzde 80 ' e dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="556a0-110">During rendering, the alpha values in the bitmap are converted to 80 percent of what they were.</span></span> <span data-ttu-id="556a0-111">Bu, arka planla karışan bir görüntüyle sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="556a0-111">This results in an image that is blended with the background.</span></span> <span data-ttu-id="556a0-112">Aşağıdaki çizimde gösterildiği gibi, bit eşlem görüntüsü saydam görünüyor; düz siyah çizgiyi onunla görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="556a0-112">As the following illustration shows, the bitmap image looks transparent; you can see the solid black line through it.</span></span>  
  
 <span data-ttu-id="556a0-113">![Matris kullanan Alfa karıştırma ekran görüntüsü.](./media/how-to-use-a-color-matrix-to-set-alpha-values-in-images/alpha-blending-matrix.png "image2")</span><span class="sxs-lookup"><span data-stu-id="556a0-113">![Screenshot of alpha blending using a matrix.](./media/how-to-use-a-color-matrix-to-set-alpha-values-in-images/alpha-blending-matrix.png "image2")</span></span>  
  
 <span data-ttu-id="556a0-114">Görüntünün arka planın beyaz kısmının üzerinde olduğu yerlerde görüntü beyaz renkle karışmıştır.</span><span class="sxs-lookup"><span data-stu-id="556a0-114">Where the image is over the white portion of the background, the image has been blended with the color white.</span></span> <span data-ttu-id="556a0-115">Görüntüde siyah çizgi kesiştiği yerde görüntü siyah renkle karıştırıyor.</span><span class="sxs-lookup"><span data-stu-id="556a0-115">Where the image crosses the black line, the image is blended with the color black.</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="556a0-116">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="556a0-116">Compiling the Code</span></span>  
 <span data-ttu-id="556a0-117">Yukarıdaki örnek, Windows Forms kullanımı için tasarlanmıştır ve <xref:System.Windows.Forms.PaintEventHandler>parametresi olan <xref:System.Windows.Forms.PaintEventArgs> `e`gerektirir.</span><span class="sxs-lookup"><span data-stu-id="556a0-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="556a0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="556a0-118">See also</span></span>

- [<span data-ttu-id="556a0-119">Windows Forms’da Grafikler ve Çizim</span><span class="sxs-lookup"><span data-stu-id="556a0-119">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="556a0-120">Çizgi ve Dolgularda Alfa Karışım Kullanma</span><span class="sxs-lookup"><span data-stu-id="556a0-120">Alpha Blending Lines and Fills</span></span>](alpha-blending-lines-and-fills.md)
