---
title: Tasarımcıyı kullanarak TreeView denetimi ile düğüm ekleme ve kaldırma
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: 7edf09539719ec76fa3f650254c5c84ff0bc3af7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732244"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları TreeView Denetimi ile Düğüm Ekleme ve Kaldırma

Windows Forms <xref:System.Windows.Forms.TreeView> denetimi düğümleri hiyerarşik bir şekilde görüntülediğinden, bir düğüm eklenirken, üst düğümünün ne olduğuna dikkat etmeniz gerekir.

Aşağıdaki yordam, bir <xref:System.Windows.Forms.TreeView> denetimi içeren bir form ile **Windows uygulama** projesi gerektirir. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma Windows Forms uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md).

### <a name="to-add-or-remove-nodes-in-the-designer"></a>Tasarımcıya düğüm eklemek veya kaldırmak için

1. <xref:System.Windows.Forms.TreeView> denetimini seçin.

2. **Özellikler** penceresinde, <xref:System.Windows.Forms.TreeView.Nodes%2A> özelliğinin yanındaki Visual Studio 'nun Özellikler penceresi](./media/visual-studio-ellipsis-button.png)) düğmesine **üç nokta**![(...) düğmesini tıklatın.

     **TreeNode Düzenleyicisi** görünür.

3. Düğüm eklemek için bir kök düğümün mevcut olması gerekir; birisi yoksa, önce **kök Ekle** düğmesine tıklayarak bir kök eklemeniz gerekir. Ardından, kökü veya diğer düğümleri seçerek ve **alt Ekle** düğmesine tıklayarak alt düğümler ekleyebilirsiniz.

4. Düğümleri silmek için, silinecek düğümü seçin ve **Sil** düğmesine tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [TreeView Denetimi](treeview-control-windows-forms.md)
- [TreeView Denetimine Genel Bakış](treeview-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms TreeView Denetimi için Simgeler Ayarlama](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [Nasıl yapılır: Bir Windows Forms TreeView Denetiminin Tüm Düğümlerinde Yineleme](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Nasıl yapılır: Hangi TreeView Düğümüne Tıklandığını Belirleme](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
