---
title: 'Nasıl yapılır: MDI Üst Formları Oluşturma'
description: Programlama yoluyla ve Windows Form Tasarımcısı kullanarak bir MDI üst formu oluşturmayı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms
- MDI [Windows Forms], creating forms
ms.assetid: 12c71221-2377-4bb6-b10b-7b4b300fd462
ms.openlocfilehash: d387837a565ca247f62828c19f353990b35117c7
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174711"
---
# <a name="how-to-create-mdi-parent-forms"></a><span data-ttu-id="b4b79-103">Nasıl yapılır: MDI Üst Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b4b79-103">How to: Create MDI Parent Forms</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b4b79-104">Bu konu, <xref:System.Windows.Forms.MainMenu> Denetim tarafından değiştirilmiş olan denetimini kullanır <xref:System.Windows.Forms.MenuStrip> .</span><span class="sxs-lookup"><span data-stu-id="b4b79-104">This topic uses the <xref:System.Windows.Forms.MainMenu> control, which has been replaced by the <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="b4b79-105"><xref:System.Windows.Forms.MainMenu>' Yi seçerseniz, Denetim hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur.</span><span class="sxs-lookup"><span data-stu-id="b4b79-105">The <xref:System.Windows.Forms.MainMenu> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="b4b79-106">Kullanarak bir MDI parent formu oluşturma hakkında daha fazla bilgi için <xref:System.Windows.Forms.MenuStrip> bkz. [nasıl yapılır: MENUSTRIP Ile MDI pencere listesi oluşturma](../controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="b4b79-106">For information about creating a MDI parent Form by using a <xref:System.Windows.Forms.MenuStrip>, see [How to: Create an MDI Window List with MenuStrip](../controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).</span></span>

<span data-ttu-id="b4b79-107">Çoklu belge arabirimi (MDI) uygulamasının temeli MDI parent formundadır.</span><span class="sxs-lookup"><span data-stu-id="b4b79-107">The foundation of a Multiple-Document Interface (MDI) application is the MDI parent form.</span></span> <span data-ttu-id="b4b79-108">Bu, kullanıcının MDI uygulamasıyla etkileşime girdiği alt pencereler olan MDI alt pencerelerini içeren formdur.</span><span class="sxs-lookup"><span data-stu-id="b4b79-108">This is the form that contains the MDI child windows, which are the sub-windows wherein the user interacts with the MDI application.</span></span> <span data-ttu-id="b4b79-109">MDI parent form oluşturmak kolaydır, hem Windows Form Tasarımcısı hem de programlı olarak.</span><span class="sxs-lookup"><span data-stu-id="b4b79-109">Creating an MDI parent form is easy, both in the Windows Forms Designer and programmatically.</span></span>

## <a name="create-an-mdi-parent-form-at-design-time"></a><span data-ttu-id="b4b79-110">Tasarım zamanında bir MDI parent formu oluşturma</span><span class="sxs-lookup"><span data-stu-id="b4b79-110">Create an MDI parent form at design time</span></span>

1. <span data-ttu-id="b4b79-111">Visual Studio 'da bir Windows uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b4b79-111">Create a Windows Application project in Visual Studio.</span></span>

2. <span data-ttu-id="b4b79-112">**Özellikler** penceresinde, <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliği **true**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b4b79-112">In the **Properties** window, set the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to **true**.</span></span>

     <span data-ttu-id="b4b79-113">Bu, formu alt Windows için bir MDI kapsayıcısı olarak belirler.</span><span class="sxs-lookup"><span data-stu-id="b4b79-113">This designates the form as an MDI container for child windows.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b4b79-114">**Özellikler penceresinde özellikleri** ayarlarken, `WindowState` üst form ekranı KAPLADıKTAN sonra MDI alt pencerelerini işlemek en kolay olduğu Için özelliği de **ekranı kaplamış**olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4b79-114">While setting properties in the **Properties** window, you can also set the `WindowState` property to **Maximized**, if you like, as it is easiest to manipulate MDI child windows when the parent form is maximized.</span></span> <span data-ttu-id="b4b79-115">Ayrıca, MDI parent form ucunun, özelliği kullanarak ayarladığınız arka rengi yerine sistem rengini (Windows Sistem Denetim Masası 'nda ayarlanır) aldığını unutmayın <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b4b79-115">Additionally, be aware that the edge of the MDI parent form will pick up the system color (set in the Windows System Control Panel), rather than the back color you set using the <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> property.</span></span>

3. <span data-ttu-id="b4b79-116">**Araç kutusundan**bir **MenuStrip** denetimini forma sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="b4b79-116">From the **Toolbox**, drag a **MenuStrip** control to the form.</span></span> <span data-ttu-id="b4b79-117">**Metin** özelliği, **yeni&** ve **&kapat**olarak adlandırılan alt menü öğeleriyle **&dosya** olarak ayarlanmış bir üst düzey menü öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b4b79-117">Create a top-level menu item with the **Text** property set to **&File** with submenu items called **&New** and **&Close**.</span></span> <span data-ttu-id="b4b79-118">Ayrıca **&pencere**adlı bir üst düzey menü öğesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b4b79-118">Also create a top-level menu item called **&Window**.</span></span>

     <span data-ttu-id="b4b79-119">İlk menü çalışma zamanında menü öğelerini oluşturup gizler ve ikinci menü açık MDI alt pencerelerini takip eder.</span><span class="sxs-lookup"><span data-stu-id="b4b79-119">The first menu will create and hide menu items at run time, and the second menu will keep track of the open MDI child windows.</span></span> <span data-ttu-id="b4b79-120">Bu noktada, bir MDI üst penceresi oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="b4b79-120">At this point, you have created an MDI parent window.</span></span>

4. <span data-ttu-id="b4b79-121">Uygulamayı çalıştırmak için **F5**'e basın.</span><span class="sxs-lookup"><span data-stu-id="b4b79-121">Press **F5** to run the application.</span></span> <span data-ttu-id="b4b79-122">MDI parent form içinde çalışan MDI alt pencereleri oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: MDI alt formları oluşturma](how-to-create-mdi-child-forms.md).</span><span class="sxs-lookup"><span data-stu-id="b4b79-122">For information about creating MDI child windows that operate within the MDI parent form, see [How to: Create MDI Child Forms](how-to-create-mdi-child-forms.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b4b79-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4b79-123">See also</span></span>

- [<span data-ttu-id="b4b79-124">Çoklu Belge Arabirimi (MDI) Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="b4b79-124">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="b4b79-125">Nasıl yapılır: MDI Alt Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b4b79-125">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="b4b79-126">Nasıl yapılır: Etkin MDI Alt Öğesini Belirleme</span><span class="sxs-lookup"><span data-stu-id="b4b79-126">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="b4b79-127">Nasıl yapılır: Etkin MDI Alt Öğesine Veri Gönderme</span><span class="sxs-lookup"><span data-stu-id="b4b79-127">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="b4b79-128">Nasıl yapılır: MDI Alt Formlarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="b4b79-128">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
