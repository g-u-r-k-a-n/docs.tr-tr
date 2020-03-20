---
title: "Nasıl yapılır: Bir ContextMenuStrip'ne Menü Öğeleri Ekleme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrips [Windows Forms], adding menu items
- shortcut menus [Windows Forms], adding items
- context menus [Windows Forms], adding menu items
ms.assetid: 1ec14776-3ea2-4752-bd22-4fae0fd19e1a
ms.openlocfilehash: 7e3480c5a56170ce94d5b5bde0208542c82e7702
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182308"
---
# <a name="how-to-add-menu-items-to-a-contextmenustrip"></a><span data-ttu-id="77ae6-102">Nasıl yapılır: Bir ContextMenuStrip'ne Menü Öğeleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="77ae6-102">How to: Add Menu Items to a ContextMenuStrip</span></span>
<span data-ttu-id="77ae6-103">Bir öğeye aynı anda yalnızca bir <xref:System.Windows.Forms.ContextMenuStrip>menü öğesi veya birkaç öğe ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77ae6-103">You can add just one menu item or several items at a time to a <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
### <a name="to-add-a-single-menu-item-to-a-contextmenustrip"></a><span data-ttu-id="77ae6-104">ContextMenuStrip'e tek bir menü öğesi eklemek için</span><span class="sxs-lookup"><span data-stu-id="77ae6-104">To add a single menu item to a ContextMenuStrip</span></span>  
  
- <span data-ttu-id="77ae6-105">Bir <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> menü öğesine bir menü <xref:System.Windows.Forms.ContextMenuStrip>öğesi eklemek için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="77ae6-105">Use the <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> method to add one menu item to a <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
    ```vb  
    Me.contextMenuStrip1.Items.Add(Me.toolStripMenuItem1)  
    ```  
  
    ```csharp  
    this.contextMenuStrip1.Items.Add(toolStripMenuItem1);  
    ```  
  
### <a name="to-add-several-menu-items-to-a-contextmenustrip"></a><span data-ttu-id="77ae6-106">ContextMenuStrip'e birkaç menü öğesi eklemek için</span><span class="sxs-lookup"><span data-stu-id="77ae6-106">To add several menu items to a ContextMenuStrip</span></span>  
  
- <span data-ttu-id="77ae6-107">Bir <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> <xref:System.Windows.Forms.ContextMenuStrip>' ye birkaç menü öğesi eklemek için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="77ae6-107">Use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> method to add several menu items to a <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
    ```vb  
    Me.contextMenuStrip1.Items.AddRange(New _  
       System.Windows.Forms.ToolStripItem() {Me.toolStripMenuItem1, _  
          Me.toolStripMenuItem2})  
    ```  
  
    ```csharp  
    this.contextMenuStrip1.Items.AddRange(new
       System.Windows.Forms.ToolStripItem[] {  
          this.toolStripMenuItem1, this.toolStripMenuItem2});  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="77ae6-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77ae6-108">See also</span></span>

- [<span data-ttu-id="77ae6-109">ContextMenuStrip Denetimi</span><span class="sxs-lookup"><span data-stu-id="77ae6-109">ContextMenuStrip Control</span></span>](contextmenustrip-control.md)
