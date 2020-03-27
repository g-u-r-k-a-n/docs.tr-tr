---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Çifte Animasyon Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Doubles [WPF], animating with key frames
- animation [WPF], Doubles with key frames
- key frames [WPF], animating Doubles with
ms.assetid: 3a1a7dba-7694-4907-8a2f-3408baebfa82
ms.openlocfilehash: 9eab794cc8411230226cddc97beaa13c1bdd9405
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344923"
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a><span data-ttu-id="cd5cb-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Çifte Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="cd5cb-102">How to: Animate a Double by Using Key Frames</span></span>
<span data-ttu-id="cd5cb-103">Bu örnek, anahtar çerçeveleri kullanarak bir <xref:System.Double> gereken bir özelliğin değerini nasıl canlandırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="cd5cb-103">This example shows how to animate the value of a property that takes a <xref:System.Double> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd5cb-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="cd5cb-104">Example</span></span>  
 <span data-ttu-id="cd5cb-105">Aşağıdaki örnek, bir dikdörtgeni ekran üzerinde taşır.</span><span class="sxs-lookup"><span data-stu-id="cd5cb-105">The following example moves a rectangle across a screen.</span></span> <span data-ttu-id="cd5cb-106">Örnek, uygulanan bir <xref:System.Windows.Media.TranslateTransform> <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> <xref:System.Windows.Media.TranslateTransform.X%2A></span><span class="sxs-lookup"><span data-stu-id="cd5cb-106">The example uses the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.TranslateTransform.X%2A> property of a <xref:System.Windows.Media.TranslateTransform> applied to a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="cd5cb-107">Süresiz olarak yineleyen bu animasyon, aşağıdaki şekilde üç anahtar kare kullanır:</span><span class="sxs-lookup"><span data-stu-id="cd5cb-107">This animation, which repeats indefinitely, uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="cd5cb-108">İlk üç saniye boyunca, dikdörtgeni <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> başlangıç konumundan 500 konumuna sabit bir hızda bir yol boyunca taşımak için sınıfın bir örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="cd5cb-108">During the first three seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> class to move the rectangle along a path at a steady rate from its starting position to the 500 position.</span></span> <span data-ttu-id="cd5cb-109">Değerler arasında düzgün <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> doğrusal geçiş oluşturma gibi doğrusal anahtar çerçeveler.</span><span class="sxs-lookup"><span data-stu-id="cd5cb-109">Linear key frames like <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="cd5cb-110">Dördüncü saniyenin sonunda, dikdörtgeni <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> aniden bir sonraki konuma taşımak için sınıfın bir örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="cd5cb-110">At the end of the fourth second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> class to suddenly move the rectangle to the next position.</span></span> <span data-ttu-id="cd5cb-111">Değerler arasında ani <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> sıçramalar oluşturmak gibi ayrık anahtar kareler.</span><span class="sxs-lookup"><span data-stu-id="cd5cb-111">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> create sudden jumps between values.</span></span> <span data-ttu-id="cd5cb-112">Bu örnekte, dikdörtgen başlangıç konumundadır ve sonra aniden 500 konumunda görünür.</span><span class="sxs-lookup"><span data-stu-id="cd5cb-112">In this example, the rectangle is at the starting position and then suddenly appears at the 500 position.</span></span>  
  
3. <span data-ttu-id="cd5cb-113">Son iki saniye içinde, dikdörtgeni <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> başlangıç konumuna geri taşımak için sınıfın bir örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="cd5cb-113">In the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> class to move the rectangle back to its starting position.</span></span> <span data-ttu-id="cd5cb-114">Özellik değerine <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> göre <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> değerler arasında değişken bir geçiş oluşturmak gibi spline anahtar çerçeveleri.</span><span class="sxs-lookup"><span data-stu-id="cd5cb-114">Spline key frames like <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> create a variable transition between values according to the value of the <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="cd5cb-115">Bu örnekte, dikdörtgen yavaş hareket ederek başlar ve sonra zaman diliminin sonuna doğru katlanarak hızlanır.</span><span class="sxs-lookup"><span data-stu-id="cd5cb-115">In this example, the rectangle begins by moving slowly and then speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="cd5cb-116">Tam örnek için [Anahtar Çerçeve Animasyon Örneği'ne](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)bakın.</span><span class="sxs-lookup"><span data-stu-id="cd5cb-116">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
 <span data-ttu-id="cd5cb-117">Diğer animasyon örnekleri ile tutarlılık için, bu örneğin <xref:System.Windows.Media.Animation.Storyboard> kod sürümleri <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>bir nesne uygulamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="cd5cb-117">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span></span> <span data-ttu-id="cd5cb-118">Alternatif olarak, kod da tek bir animasyon uygularken, <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> bir <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="cd5cb-118">Alternatively, when applying a single animation in code, it is simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="cd5cb-119">Örneğin, Bir [Storyboard kullanmadan bir Özellik Animasyon](how-to-animate-a-property-without-using-a-storyboard.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="cd5cb-119">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd5cb-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd5cb-120">See also</span></span>

- <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>
- <xref:System.Windows.Shapes.Rectangle>
- <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>
- [<span data-ttu-id="cd5cb-121">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cd5cb-121">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="cd5cb-122">Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="cd5cb-122">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
