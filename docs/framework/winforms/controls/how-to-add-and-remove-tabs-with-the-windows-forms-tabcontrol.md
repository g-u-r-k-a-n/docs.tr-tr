---
title: TabControl ile sekme ekleme ve kaldırma
description: İki TabPage denetimi içeren Windows Forms TabControl denetimiyle sekme ekleme ve kaldırma hakkında bilgi edinin. Bu sekmelere TabPages özelliği aracılığıyla erişin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tabs [Windows Forms], removing from pages
- TabPage control
- TabControl control [Windows Forms], adding and removing tabs
- tabs [Windows Forms], adding to pages
- tab pages
ms.assetid: 66d4dfca-41e8-44e3-9c80-fb7ac4cb1619
ms.openlocfilehash: 7e67d0bbc13bd7d9c8835dc6fb9b9c5c9333b8bf
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618083"
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol"></a><span data-ttu-id="337a0-104">Nasıl yapılır: Windows Forms TabControl' ile Sekme Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="337a0-104">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>
<span data-ttu-id="337a0-105">Varsayılan olarak, bir <xref:System.Windows.Forms.TabControl> Denetim iki <xref:System.Windows.Forms.TabPage> denetim içerir.</span><span class="sxs-lookup"><span data-stu-id="337a0-105">By default, a <xref:System.Windows.Forms.TabControl> control contains two <xref:System.Windows.Forms.TabPage> controls.</span></span> <span data-ttu-id="337a0-106">Bu sekmelere özelliği aracılığıyla erişebilirsiniz <xref:System.Windows.Forms.TabControl.TabPages%2A> .</span><span class="sxs-lookup"><span data-stu-id="337a0-106">You can access these tabs through the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
### <a name="to-add-a-tab-programmatically"></a><span data-ttu-id="337a0-107">Program aracılığıyla sekme eklemek için</span><span class="sxs-lookup"><span data-stu-id="337a0-107">To add a tab programmatically</span></span>  
  
- <span data-ttu-id="337a0-108"><xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A>Özelliğin yöntemini kullanın <xref:System.Windows.Forms.TabControl.TabPages%2A> .</span><span class="sxs-lookup"><span data-stu-id="337a0-108">Use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
    ```vb  
    Dim myTabPage As New TabPage()  
    myTabPage.Text = "TabPage" & (TabControl1.TabPages.Count + 1)  
    TabControl1.TabPages.Add(myTabPage)  
    ```  
  
    ```csharp  
    string title = "TabPage " + (tabControl1.TabCount + 1).ToString();  
    TabPage myTabPage = new TabPage(title);  
    tabControl1.TabPages.Add(myTabPage);  
    ```  
  
    ```cpp  
    String^ title = String::Concat("TabPage ",  
       (tabControl1->TabCount + 1).ToString());  
    TabPage^ myTabPage = gcnew TabPage(title);  
    tabControl1->TabPages->Add(myTabPage);  
    ```  
  
### <a name="to-remove-a-tab-programmatically"></a><span data-ttu-id="337a0-109">Bir sekmeyi programlı bir şekilde kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="337a0-109">To remove a tab programmatically</span></span>  
  
- <span data-ttu-id="337a0-110">Seçili sekmeleri kaldırmak için, <xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A> özelliğinin yöntemini kullanın <xref:System.Windows.Forms.TabControl.TabPages%2A> .</span><span class="sxs-lookup"><span data-stu-id="337a0-110">To remove selected tabs, use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
     <span data-ttu-id="337a0-111">-veya-</span><span class="sxs-lookup"><span data-stu-id="337a0-111">-or-</span></span>  
  
- <span data-ttu-id="337a0-112">Tüm sekmeleri kaldırmak için, <xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A> özelliğinin yöntemini kullanın <xref:System.Windows.Forms.TabControl.TabPages%2A> .</span><span class="sxs-lookup"><span data-stu-id="337a0-112">To remove all tabs, use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
    ```vb  
    ' Removes the selected tab:  
    TabControl1.TabPages.Remove(TabControl1.SelectedTab)  
    ' Removes all the tabs:  
    TabControl1.TabPages.Clear()  
    ```  
  
    ```csharp  
    // Removes the selected tab:  
    tabControl1.TabPages.Remove(tabControl1.SelectedTab);  
    // Removes all the tabs:  
    tabControl1.TabPages.Clear();  
    ```  
  
    ```cpp  
    // Removes the selected tab:  
    tabControl1->TabPages->Remove(tabControl1->SelectedTab);  
    // Removes all the tabs:  
    tabControl1->TabPages->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="337a0-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="337a0-113">See also</span></span>

- [<span data-ttu-id="337a0-114">TabControl Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="337a0-114">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="337a0-115">Nasıl yapılır: Sekme Sayfasına Denetim Ekleme</span><span class="sxs-lookup"><span data-stu-id="337a0-115">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="337a0-116">Nasıl yapılır: Sekme Sayfalarını Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="337a0-116">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="337a0-117">Nasıl yapılır: Windows Forms TabControl’un Görünüşünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="337a0-117">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
