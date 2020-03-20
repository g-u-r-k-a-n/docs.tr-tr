---
title: Kullanıcı Çizimli Denetimler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user-drawn
- OnPaint method [Windows Forms]
- user-drawn controls [Windows Forms]
ms.assetid: 034af4b5-457f-4160-a937-22891817faa8
ms.openlocfilehash: c68c8c88376cfe7295962264c466030115f2f3db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182017"
---
# <a name="user-drawn-controls"></a><span data-ttu-id="01669-102">Kullanıcı Çizimli Denetimler</span><span class="sxs-lookup"><span data-stu-id="01669-102">User-Drawn Controls</span></span>
<span data-ttu-id="01669-103">.NET Framework size kendi denetimlerinizi kolayca geliştirme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="01669-103">The .NET Framework provides you with the ability to easily develop your own controls.</span></span> <span data-ttu-id="01669-104">Kodla birbirine bağlı standart denetimler kümesi olan bir kullanıcı denetimi oluşturabilir veya kendi denetiminizi sıfırdan tasarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01669-104">You can create a user control, which is a set of standard controls bound together by code, or you can design your own control from the ground up.</span></span> <span data-ttu-id="01669-105">Hatta varolan bir denetimden devralan bir denetim oluşturmak ve doğal işlevselliğini eklemek için devralma kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01669-105">You can even use inheritance to create a control that inherits from an existing control and add to its inherent functionality.</span></span> <span data-ttu-id="01669-106">Hangi yaklaşımı kullanırsanız kullanın, .NET Framework oluşturduğunuz herhangi bir denetim için özel bir grafik arabirimi çizmek için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="01669-106">Whatever approach you use, the .NET Framework provides the functionality to draw a custom graphical interface for any control you create.</span></span>  
  
 <span data-ttu-id="01669-107">Denetimin boyanmasi, denetim <xref:System.Windows.Forms.Control.OnPaint%2A> yönteminde kodun yürütülmesi yle gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="01669-107">Painting of a control is accomplished by the execution of code in the control's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="01669-108"><xref:System.Windows.Forms.Control.OnPaint%2A> Yöntemin tek bağımsız değişkeni, denetiminizi işlemek için gereken tüm bilgileri ve işlevselliği sağlayan bir <xref:System.Windows.Forms.PaintEventArgs> nesnedir.</span><span class="sxs-lookup"><span data-stu-id="01669-108">The single argument of the <xref:System.Windows.Forms.Control.OnPaint%2A> method is a <xref:System.Windows.Forms.PaintEventArgs> object that provides all of the information and functionality required to render your control.</span></span> <span data-ttu-id="01669-109">Özellikleri <xref:System.Windows.Forms.PaintEventArgs> olarak denetim oluşturma kullanılacak iki temel nesneleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="01669-109">The <xref:System.Windows.Forms.PaintEventArgs> provides as properties two principal objects that will be used in the rendering of your control:</span></span>  
  
- <span data-ttu-id="01669-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>nesne - çizilecek denetimin bölümünü temsil eden dikdörtgen.</span><span class="sxs-lookup"><span data-stu-id="01669-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object - the rectangle that represents the part of the control that will be drawn.</span></span> <span data-ttu-id="01669-111">Bu, denetimin nasıl çizildiğine bağlı olarak tüm denetim veya denetimin bir parçası olabilir.</span><span class="sxs-lookup"><span data-stu-id="01669-111">This can be the entire control, or part of the control depending on how the control is drawn.</span></span>  
  
- <span data-ttu-id="01669-112"><xref:System.Drawing.Graphics>nesne - denetiminizi çizmek için gerekli işlevselliği sağlayan birkaç grafik yönelimli nesne ve yöntem kapsüller.</span><span class="sxs-lookup"><span data-stu-id="01669-112"><xref:System.Drawing.Graphics> object - encapsulates several graphics-oriented objects and methods that provide the functionality necessary to draw your control.</span></span>  
  
 <span data-ttu-id="01669-113"><xref:System.Drawing.Graphics> Nesne ve nasıl kullanılacağı hakkında daha fazla bilgi için [bkz.](../advanced/how-to-create-graphics-objects-for-drawing.md)</span><span class="sxs-lookup"><span data-stu-id="01669-113">For more information on the <xref:System.Drawing.Graphics> object and how to use it, see [How to: Create Graphics Objects for Drawing](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
 <span data-ttu-id="01669-114">Olay, <xref:System.Windows.Forms.Control.OnPaint%2A> denetim ekranda çizildiğinde veya yenilendiğinde ateşlenir ve <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> nesne boyamanın gerçekleşeceği dikdörtgeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="01669-114">The <xref:System.Windows.Forms.Control.OnPaint%2A> event is fired whenever the control is drawn or refreshed on the screen, and the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object represents the rectangle in which painting will take place.</span></span> <span data-ttu-id="01669-115">Tüm denetimin yenilenmesi gerekiyorsa, tüm <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> denetimin boyutunu temsil edecektir.</span><span class="sxs-lookup"><span data-stu-id="01669-115">If the entire control needs to be refreshed, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> will represent the size of the entire control.</span></span> <span data-ttu-id="01669-116">Ancak denetimin yalnızca bir kısmının yenilenmesi gerekiyorsa, <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> nesne yalnızca yeniden çizilmesi gereken bölgeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="01669-116">If only part of the control needs to be refreshed, however, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object will represent only the region that needs to be redrawn.</span></span> <span data-ttu-id="01669-117">Böyle bir duruma örnek olarak, bir denetimin kullanıcı arabirimindeki başka bir denetim veya form tarafından kısmen gizlenmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="01669-117">An example of such a case would be when a control was partially obscured by another control or form in the user interface.</span></span>  
  
 <span data-ttu-id="01669-118"><xref:System.Windows.Forms.Control> Sınıftan devralma yaparken, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi geçersiz kılmanız ve içinde grafik oluşturma kodu sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="01669-118">When inheriting from the <xref:System.Windows.Forms.Control> class, you must override the <xref:System.Windows.Forms.Control.OnPaint%2A> method and provide graphics-rendering code within.</span></span> <span data-ttu-id="01669-119">Kullanıcı denetimine veya devralınan denetime özel bir grafik arabirimi sağlamak istiyorsanız, <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemi geçersiz kılarak da yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01669-119">If you want to provide a custom graphical interface to a user control or an inherited control, you can also do so by overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="01669-120">Aşağıda bir örnek gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="01669-120">An example is shown below:</span></span>  
  
```vb  
Protected Overrides Sub OnPaint(ByVal e As PaintEventArgs)  
   ' Call the OnPaint method of the base class.  
   MyBase.OnPaint(e)  
  
   ' Declare and instantiate a drawing pen.  
   Using myPen As System.Drawing.Pen = New System.Drawing.Pen(Color.Aqua)  
      ' Draw an aqua rectangle in the rectangle represented by the control.  
      e.Graphics.DrawRectangle(myPen, New Rectangle(Me.Location, Me.Size))  
   End Using
End Sub  
```  
  
```csharp  
protected override void OnPaint(PaintEventArgs e)  
{  
   // Call the OnPaint method of the base class.  
   base.OnPaint(e);  
  
   // Declare and instantiate a new pen.  
   using (System.Drawing.Pen myPen = new System.Drawing.Pen(Color.Aqua))  
   {
      // Draw an aqua rectangle in the rectangle represented by the control.  
      e.Graphics.DrawRectangle(myPen, new Rectangle(this.Location,
         this.Size));  
   }
}  
```  
  
 <span data-ttu-id="01669-121">Önceki örnek, çok basit bir grafik gösterimi ile bir denetim nasıl işlenir gösterir.</span><span class="sxs-lookup"><span data-stu-id="01669-121">The preceding example demonstrates how to render a control with a very simple graphical representation.</span></span> <span data-ttu-id="01669-122">Taban sınıfın <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini çağırır, çizeceği <xref:System.Drawing.Pen> bir nesne oluşturur ve son olarak denetim tarafından <xref:System.Windows.Forms.Control.Location%2A> <xref:System.Windows.Forms.Control.Size%2A> belirlenen dikdörtgende bir elips çizer.</span><span class="sxs-lookup"><span data-stu-id="01669-122">It calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class, it creates a <xref:System.Drawing.Pen> object with which to draw, and finally draws an ellipse in the rectangle determined by the <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Size%2A> of the control.</span></span> <span data-ttu-id="01669-123">Çoğu işleme kodu bundan önemli ölçüde daha karmaşık olsa da, <xref:System.Drawing.Graphics> bu örnek <xref:System.Windows.Forms.PaintEventArgs> nesnenin içinde bulunan nesnenin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="01669-123">Although most rendering code will be significantly more complicated than this, this example demonstrates the use of the <xref:System.Drawing.Graphics> object contained within the <xref:System.Windows.Forms.PaintEventArgs> object.</span></span> <span data-ttu-id="01669-124">Zaten grafik gösterimi olan bir sınıftan devralma kalıyorsanız, <xref:System.Windows.Forms.UserControl> <xref:System.Windows.Forms.Button>örneğin veya , bu temsili işlemenize dahil etmek istemiyorsanız, taban sınıfınızın <xref:System.Windows.Forms.Control.OnPaint%2A> yöntemini aramamalısınız.</span><span class="sxs-lookup"><span data-stu-id="01669-124">Note that if you are inheriting from a class that already has a graphical representation, such as <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Button>, and you do not wish to incorporate that representation into your rendering, you should not call your base class's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
 <span data-ttu-id="01669-125">Denetim yönteminizdeki <xref:System.Windows.Forms.Control.OnPaint%2A> kod, denetim ilk çizildiğinde ve yenilendiğinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="01669-125">The code in the <xref:System.Windows.Forms.Control.OnPaint%2A> method of your control will execute when the control is first drawn, and whenever it is refreshed.</span></span> <span data-ttu-id="01669-126">Denetiminizin her yeniden boyutlandırılışında yeniden çizildiğinden emin olmak için denetiminizin oluşturucuya aşağıdaki satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="01669-126">To ensure that your control is redrawn every time it is resized, add the following line to the constructor of your control:</span></span>  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
> <span data-ttu-id="01669-127">Dikdörtgen <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> olmayan bir denetim uygulamak için özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="01669-127">Use the <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> property to implement a non-rectangular control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01669-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01669-128">See also</span></span>

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [<span data-ttu-id="01669-129">Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="01669-129">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="01669-130">Bağlı Denetimler</span><span class="sxs-lookup"><span data-stu-id="01669-130">Constituent Controls</span></span>](constituent-controls.md)
- [<span data-ttu-id="01669-131">Özel Denetim Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="01669-131">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
