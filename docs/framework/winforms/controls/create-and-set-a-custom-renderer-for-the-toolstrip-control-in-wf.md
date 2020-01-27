---
title: 'Nasıl yapılır: ToolStrip denetimi için özel Oluşturucu oluşturma ve ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], custom rendering
- toolbars [Windows Forms], rendering
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], rendering
ms.assetid: 88a804ba-679f-4ba3-938a-0dc396199c5b
ms.openlocfilehash: ad5ced42754fba6a714452220dd824c4f54fb5e5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743414"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a><span data-ttu-id="722d5-102">Nasıl yapılır: Windows Forms'ta ToolStrip Denetimi için Özel Oluşturucu Oluşturma ve Ayarlama</span><span class="sxs-lookup"><span data-stu-id="722d5-102">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>
<span data-ttu-id="722d5-103"><xref:System.Windows.Forms.ToolStrip> denetimleri, temalara ve stillere kolay destek verir.</span><span class="sxs-lookup"><span data-stu-id="722d5-103"><xref:System.Windows.Forms.ToolStrip> controls give easy support to themes and styles.</span></span> <span data-ttu-id="722d5-104"><xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> özelliğini ya da <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> özelliğini özel bir işleyiciye ayarlayarak tamamen özel görünüm ve davranış (göz atın) elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="722d5-104">You can achieve completely custom appearance and behavior (look and feel) by setting either the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property or the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to a custom renderer.</span></span>  
  
 <span data-ttu-id="722d5-105">Her bireysel <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>veya <xref:System.Windows.Forms.StatusStrip> denetimine işlem atayabilir veya <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> özelliğini <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> olarak ayarlayarak tüm nesneleri etkilemek için <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="722d5-105">You can assign renderers to each individual <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, or <xref:System.Windows.Forms.StatusStrip> control, or you can use the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> property to affect all objects by setting the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="722d5-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A>, yalnızca <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> değeri `null`değilse <xref:System.Windows.Forms.ToolStripRenderMode.Custom> döndürür.</span><span class="sxs-lookup"><span data-stu-id="722d5-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> returns <xref:System.Windows.Forms.ToolStripRenderMode.Custom> only if the value of <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> is not `null`.</span></span>  
  
### <a name="to-create-a-custom-renderer"></a><span data-ttu-id="722d5-107">Özel bir işleyici oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="722d5-107">To create a custom renderer</span></span>  
  
1. <span data-ttu-id="722d5-108"><xref:System.Windows.Forms.ToolStripRenderer> sınıfını genişletin.</span><span class="sxs-lookup"><span data-stu-id="722d5-108">Extend the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span>  
  
2. <span data-ttu-id="722d5-109">Uygun üzerine yazarak istenen özel işlemeyi uygulayın *...*</span><span class="sxs-lookup"><span data-stu-id="722d5-109">Implement desired custom rendering by overriding appropriate *On…*</span></span> <span data-ttu-id="722d5-110">üyeler</span><span class="sxs-lookup"><span data-stu-id="722d5-110">members</span></span>  
  
    ```vb  
    Public Class RedTextRenderer  
        Inherits System.Windows.Forms.ToolStripRenderer  
        Protected Overrides Sub OnRenderItemText(ByVal e As _  
            ToolStripItemTextRenderEventArgs)   
            e.TextColor = Color.Red  
            e.TextFont = New Font("Helvetica", 7, FontStyle.Bold)  
            MyBase.OnRenderItemText(e)  
        End Sub  
    End Class  
    ```  
  
    ```csharp  
    public class RedTextRenderer : _  
        System.Windows.Forms.ToolStripRenderer  
    {  
        protected override void _  
            OnRenderItemText(ToolStripItemTextRenderEventArgs e)  
        {  
            e.TextColor = Color.Red;  
            e.TextFont = new Font("Helvetica", 7, FontStyle.Bold);  
           base.OnRenderItemText(e);  
        }  
    }  
    ```  
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a><span data-ttu-id="722d5-111">Özel oluşturucuyu geçerli işleyici olacak şekilde ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="722d5-111">To set the custom renderer to be the current renderer</span></span>  
  
1. <span data-ttu-id="722d5-112">Bir <xref:System.Windows.Forms.ToolStrip>için özel oluşturucuyu ayarlamak için, <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> özelliğini özel Oluşturucu olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="722d5-112">To set the custom renderer for one <xref:System.Windows.Forms.ToolStrip>, set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to the custom renderer.</span></span>  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. <span data-ttu-id="722d5-113">Veya uygulamanızda bulunan tüm <xref:System.Windows.Forms.ToolStrip> sınıfları için özel oluşturucuyu ayarlamak için: <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> özelliğini özel Oluşturucu olarak ayarlayın ve <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> özelliğini <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="722d5-113">Or to set the custom renderer for all <xref:System.Windows.Forms.ToolStrip> classes contained in your application: Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to the custom renderer and set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="722d5-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="722d5-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [<span data-ttu-id="722d5-115">ToolStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="722d5-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="722d5-116">ToolStrip Denetim, Mimarisi</span><span class="sxs-lookup"><span data-stu-id="722d5-116">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="722d5-117">ToolStrip Teknoloji Özeti</span><span class="sxs-lookup"><span data-stu-id="722d5-117">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
