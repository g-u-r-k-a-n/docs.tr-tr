---
title: Başlangıç formu belirtilmedi
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: 058deb1378ed9218274ae20c8340178f7c8fa58c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409913"
---
# <a name="a-startup-form-has-not-been-specified"></a><span data-ttu-id="11b06-102">Başlangıç formu belirtilmedi</span><span class="sxs-lookup"><span data-stu-id="11b06-102">A startup form has not been specified</span></span>

<span data-ttu-id="11b06-103">Uygulama sınıfı kullanır, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> ancak başlangıç formunu belirtmez.</span><span class="sxs-lookup"><span data-stu-id="11b06-103">The application uses the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class but does not specify the startup form.</span></span>  
  
 <span data-ttu-id="11b06-104">Bu durum proje tasarımcısında **uygulama çerçevesini etkinleştir** onay kutusu işaretliyse, ancak **başlangıç formu** belirtilmediğinde ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="11b06-104">This can occur if the **Enable application framework** check box is selected in the project designer but the **Startup form** is not specified.</span></span> <span data-ttu-id="11b06-105">Daha fazla bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="11b06-105">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="11b06-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="11b06-106">To correct this error</span></span>  
  
1. <span data-ttu-id="11b06-107">Uygulama için bir başlangıç nesnesi belirtin.</span><span class="sxs-lookup"><span data-stu-id="11b06-107">Specify a startup object for the application.</span></span>  
  
     <span data-ttu-id="11b06-108">Daha fazla bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="11b06-108">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
2. <span data-ttu-id="11b06-109"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>Özelliği başlangıç formu olarak ayarlamak için yöntemini geçersiz kılın <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> .</span><span class="sxs-lookup"><span data-stu-id="11b06-109">Override the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> method to set the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> property to the startup form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11b06-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11b06-110">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [<span data-ttu-id="11b06-111">Visual Basic Uygulama Modeline Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="11b06-111">Overview of the Visual Basic Application Model</span></span>](../../developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
