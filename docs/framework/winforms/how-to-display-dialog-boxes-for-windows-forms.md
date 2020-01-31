---
title: 'Nasıl yapılır: Iletişim kutularını görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, displaying
- Windows Forms dialog boxes [Windows Forms], displaying
- Windows Forms, calling one form from another
- dialog boxes [Windows Forms], displaying for Windows Forms
ms.assetid: aaac1b38-c651-495a-8d3d-5a9bfb32fee3
ms.openlocfilehash: dd04a06eaa0dd7583ef2f72edb4cffa99aaaa60c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739468"
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a><span data-ttu-id="b0290-102">Nasıl yapılır: Windows Forms için İletişim Kutularını Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="b0290-102">How to: Display Dialog Boxes for Windows Forms</span></span>
<span data-ttu-id="b0290-103">Bir iletişim kutusunu, bir uygulamadaki diğer formları görüntülerken kullandığınız şekilde görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0290-103">You display a dialog box in the same way you display any other form in an application.</span></span> <span data-ttu-id="b0290-104">Başlangıç formu, uygulama çalıştırıldığında otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="b0290-104">The startup form loads automatically when the application is run.</span></span> <span data-ttu-id="b0290-105">Uygulamada ikinci bir form veya iletişim kutusu görüntülenmesini sağlamak için kodu yazın ve görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="b0290-105">To make a second form or dialog box appear in the application, write code to load and display it.</span></span> <span data-ttu-id="b0290-106">Benzer şekilde, form veya iletişim kutusunun kaybolması için, kaldırmak veya gizlemek için kod yazın.</span><span class="sxs-lookup"><span data-stu-id="b0290-106">Similarly, to make the form or dialog box disappear, write code to unload or hide it.</span></span>  
  
### <a name="to-display-a-dialog-box"></a><span data-ttu-id="b0290-107">Bir iletişim kutusunu göstermek için</span><span class="sxs-lookup"><span data-stu-id="b0290-107">To display a dialog box</span></span>  
  
1. <span data-ttu-id="b0290-108">İletişim kutusunu açmak istediğiniz olay işleyicisine gidin.</span><span class="sxs-lookup"><span data-stu-id="b0290-108">Navigate to the event handler with which you want to open the dialog box.</span></span> <span data-ttu-id="b0290-109">Bu, bir menü komutu seçildiğinde, bir düğmeye tıklandığında veya başka herhangi bir olay gerçekleştiğinde meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="b0290-109">This can happen when a menu command is selected, when a button is clicked, or when any other event occurs.</span></span>  
  
2. <span data-ttu-id="b0290-110">Olay işleyicisinde, iletişim kutusunu açmak için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b0290-110">In the event handler, add code to open the dialog box.</span></span> <span data-ttu-id="b0290-111">Bu örnekte, iletişim kutusunu göstermek için bir düğme tıklama olayı kullanılır:</span><span class="sxs-lookup"><span data-stu-id="b0290-111">In this example, a button-click event is used to show the dialog box:</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim dlg1 as new Form()  
       dlg1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
       Form dlg1 = new Form();  
       dlg1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:   
      void button1_Click(System::Object ^ sender,  
        System::EventArgs ^ e)  
      {  
        Form ^ dlg1 = gcnew Form();  
        dlg1->ShowDialog();  
      }  
    ```
