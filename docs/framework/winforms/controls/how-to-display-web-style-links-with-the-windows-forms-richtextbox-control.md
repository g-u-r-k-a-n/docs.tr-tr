---
title: RichTextBox denetimiyle Web stili bağlantıları görüntüleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], displaying Web links
- examples [Windows Forms], text boxes
- RichTextBox control [Windows Forms], linking to Web pages
ms.assetid: 95089a37-a202-4f7a-94ee-6ee312908851
ms.openlocfilehash: 06ed304e566bb437a2353dd330d7de5328f2a729
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144831"
---
# <a name="how-to-display-web-style-links-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="7758c-102">Nasıl yapılır: Windows Forms RichTextBox Denetimi ile Web Stili Bağlantılar Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="7758c-102">How to: Display Web-Style Links with the Windows Forms RichTextBox Control</span></span>

<span data-ttu-id="7758c-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> Denetim, web bağlantılarını renkli ve altı çizili olarak gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="7758c-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display Web links as colored and underlined.</span></span> <span data-ttu-id="7758c-104">Bağlantı tıklandığında bağlantı metninde belirtilen Web sitesini gösteren tarayıcı penceresi açan bir kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7758c-104">You can write code that opens a browser window showing the Web site specified in the link text when the link is clicked.</span></span>

### <a name="to-link-to-a-web-page-with-the-richtextbox-control"></a><span data-ttu-id="7758c-105">RichTextBox denetimiyle bir Web sayfasına bağlantı sağlamak için</span><span class="sxs-lookup"><span data-stu-id="7758c-105">To link to a Web page with the RichTextBox control</span></span>

1. <span data-ttu-id="7758c-106"><xref:System.Windows.Forms.RichTextBox.Text%2A>Özelliğini geçerli BIR URL (örneğin, "") içeren bir dizeye ayarlayın https://www.microsoft.com/ .</span><span class="sxs-lookup"><span data-stu-id="7758c-106">Set the <xref:System.Windows.Forms.RichTextBox.Text%2A> property to a string that includes a valid URL (for example, "https://www.microsoft.com/").</span></span>

2. <span data-ttu-id="7758c-107"><xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>Özelliğin (varsayılan) olarak ayarlandığından emin olun `true` .</span><span class="sxs-lookup"><span data-stu-id="7758c-107">Make sure the <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> property is set to `true` (the default).</span></span>

3. <span data-ttu-id="7758c-108">Nesnenin yeni bir genel örneğini oluşturun <xref:System.Diagnostics.Process> .</span><span class="sxs-lookup"><span data-stu-id="7758c-108">Create a new global instance of the <xref:System.Diagnostics.Process> object.</span></span>

4. <span data-ttu-id="7758c-109"><xref:System.Windows.Forms.RichTextBox.LinkClicked>Tarayıcıya istenen metni gönderen olay için bir olay işleyicisi yazın.</span><span class="sxs-lookup"><span data-stu-id="7758c-109">Write an event handler for the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event that sends the browser the desired text.</span></span>

    <span data-ttu-id="7758c-110">Aşağıdaki örnekte, <xref:System.Windows.Forms.RichTextBox.LinkClicked> olay, bir Internet Explorer örneğini denetimin özelliğinde BELIRTILEN URL 'ye açar <xref:System.Windows.Forms.RichTextBox.Text%2A> <xref:System.Windows.Forms.RichTextBox> .</span><span class="sxs-lookup"><span data-stu-id="7758c-110">In the example below, the <xref:System.Windows.Forms.RichTextBox.LinkClicked> event opens an instance of Internet Explorer to the URL specified in the <xref:System.Windows.Forms.RichTextBox.Text%2A> property of the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="7758c-111">Bu örnekte, bir denetimi olan bir form varsayılır <xref:System.Windows.Forms.RichTextBox> .</span><span class="sxs-lookup"><span data-stu-id="7758c-111">This example assumes a form with a <xref:System.Windows.Forms.RichTextBox> control.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="7758c-112"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>Yöntemi çağırırken, <xref:System.Security.SecurityException> yetersiz ayrıcalıklar nedeniyle kodu kısmi güven bağlamında çalıştırıyorsanız bir özel durumla karşılaşacaksınız.</span><span class="sxs-lookup"><span data-stu-id="7758c-112">In calling the <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> method, you will encounter a <xref:System.Security.SecurityException> exception if you are running the code in a partial-trust context because of insufficient privileges.</span></span> <span data-ttu-id="7758c-113">Daha fazla bilgi için bkz. [kod erişimi güvenlik temelleri](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="7758c-113">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

    ```vb
    Public p As New System.Diagnostics.Process
    Private Sub RichTextBox1_LinkClicked _
       (ByVal sender As Object, ByVal e As _
       System.Windows.Forms.LinkClickedEventArgs) _
       Handles RichTextBox1.LinkClicked
          ' Call Process.Start method to open a browser
          ' with link text as URL.
          p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText)
    End Sub
    ```

    ```csharp
    public System.Diagnostics.Process p = new System.Diagnostics.Process();

    private void richTextBox1_LinkClicked(object sender,
    System.Windows.Forms.LinkClickedEventArgs e)
    {
       // Call Process.Start method to open a browser
       // with link text as URL.
       p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText);
    }
    ```

    ```cpp
    public:
       System::Diagnostics::Process ^ p;

    private:
       void richTextBox1_LinkClicked(System::Object ^  sender,
          System::Windows::Forms::LinkClickedEventArgs ^  e)
       {
          // Call Process.Start method to open a browser
          // with link text as URL.
          p = System::Diagnostics::Process::Start("IExplore.exe",
             e->LinkText);
       }
    ```

    <span data-ttu-id="7758c-114">(Visual C++) `p`Aşağıdaki deyiminizi formunuzun yapıcısına ekleyerek yapabileceğiniz işlemi başlatmalısınız:</span><span class="sxs-lookup"><span data-stu-id="7758c-114">(Visual C++) You must initialize process `p`, which you can do by including the following statement in the constructor of your form:</span></span>

    ```cpp
    p = gcnew System::Diagnostics::Process();
    ```

    <span data-ttu-id="7758c-115">(Visual C#, Visual C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="7758c-115">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>

    ```csharp
    this.richTextBox1.LinkClicked += new
       System.Windows.Forms.LinkClickedEventHandler
       (this.richTextBox1_LinkClicked);
    ```

    ```cpp
    this->richTextBox1->LinkClicked += gcnew
       System::Windows::Forms::LinkClickedEventHandler
       (this, &Form1::richTextBox1_LinkClicked);
    ```

    <span data-ttu-id="7758c-116">Üzerinde çalışmayı bitirdikten sonra oluşturduğunuz işlemi hemen durdurmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="7758c-116">It is important to immediately stop the process you have created once you have finished working with it.</span></span> <span data-ttu-id="7758c-117">Yukarıda sunulan koda başvurarak, işlemi durdurmak için kodunuz şuna benzeyebilir:</span><span class="sxs-lookup"><span data-stu-id="7758c-117">Referring to the code presented above, your code to stop the process might look like this:</span></span>

    ```vb
    Public Sub StopWebProcess()
       p.Kill()
    End Sub
    ```

    ```csharp
    public void StopWebProcess()
    {
       p.Kill();
    }
    ```

    ```cpp
    public: void StopWebProcess()
    {
       p->Kill();
    }
    ```

## <a name="see-also"></a><span data-ttu-id="7758c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7758c-118">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>
- <xref:System.Windows.Forms.RichTextBox.LinkClicked>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="7758c-119">RichTextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="7758c-119">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="7758c-120">Windows Forms'ta Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="7758c-120">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
