---
title: MonthCalendar denetiminin görünümünü değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
ms.openlocfilehash: ded9059ede4ad03f637c0e697b880c41a9a8ba32
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746645"
---
# <a name="how-to-change-the-windows-forms-monthcalendar-controls-appearance"></a>Nasıl yapılır: Windows Forms MonthCalendar Denetiminin Görünüşünü Değiştirme
Windows Forms <xref:System.Windows.Forms.MonthCalendar> denetimi takvimin görünümünü birçok şekilde özelleştirmenize olanak tanır. Örneğin, renk şemasını ayarlayabilir ve hafta numaralarını ve geçerli tarihi görüntülemeyi veya gizlemeyi seçebilirsiniz.  
  
### <a name="to-change-the-month-calendars-color-scheme"></a>Aylık takvimin renk düzenini değiştirmek için  
  
- <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> ve <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>gibi özellikleri ayarlayın. <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> özelliği, haftanın günleri için yazı tipi rengini de belirler. <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> özelliği, görüntülenen aya veya aya önce gelen tarihlerin rengini belirler.  
  
    ```vb  
    MonthCalendar1.TitleBackColor = System.Drawing.Color.Blue  
    MonthCalendar1.TrailingForeColor = System.Drawing.Color.Red  
    MonthCalendar1.TitleForeColor = System.Drawing.Color.Yellow  
    ```  
  
    ```csharp  
    monthCalendar1.TitleBackColor = System.Drawing.Color.Blue;  
    monthCalendar1.TrailingForeColor = System.Drawing.Color.Red;  
    monthCalendar1.TitleForeColor = System.Drawing.Color.Yellow;  
    ```  
  
    ```cpp  
    monthCalendar1->TitleBackColor = System::Drawing::Color::Blue;  
    monthCalendar1->TrailingForeColor = System::Drawing::Color::Red;  
    monthCalendar1->TitleForeColor = System::Drawing::Color::Yellow;  
    ```  
  
    > [!NOTE]
    > Windows Vista ile başlayıp temaya bağlı olarak, bazı özelliklerin ayarlanması takvimin görünümünü değiştiremeyebilir. Örneğin, Windows, Aero temasını kullanmak üzere ayarlandıysa <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>veya <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> özelliklerinin ayarlanması etkisizdir. Bunun nedeni, takvimin güncelleştirilmiş bir sürümünün geçerli işletim sistemi temasından çalışma zamanında elde edilen bir görünümle işlenmesinden kaynaklanır. Bu özellikleri kullanmak ve takvimin önceki sürümünü etkinleştirmek istiyorsanız, uygulamanız için görsel stilleri devre dışı bırakabilirsiniz. Görsel stilleri devre dışı bırakmak, uygulamanızdaki diğer denetimlerin görünümünü ve davranışını etkileyebilir. Visual Basic 'de görsel stilleri devre dışı bırakmak için proje tasarımcısını açın ve **XP görsel stillerini etkinleştir** onay kutusunun işaretini kaldırın. İçinde C#görsel stilleri devre dışı bırakmak için, program.cs açın ve dışarı açıklama `Application.EnableVisualStyles();`. Görsel stiller hakkında daha fazla bilgi için bkz. [görsel stilleri etkinleştirme](/windows/desktop/controls/cookbook-overview).  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a>Denetimin en altındaki geçerli tarihi görüntüleme  
  
- Ayarlama <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> özelliğini `true`. Aşağıdaki örnek, form çift tıklandığında bugünün tarihini görüntüleme ve atlama arasında geçiş yapar.  
  
    ```vb  
    Private Sub Form1_DoubleClick(ByVal sender As Object, _  
    ByVal e As System.EventArgs) Handles MyBase.DoubleClick  
       ' Toggle between True and False.  
       MonthCalendar1.ShowToday = Not MonthCalendar1.ShowToday  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_DoubleClick(object sender, System.EventArgs e)  
    {  
       // Toggle between True and False.  
       monthCalendar1.ShowToday = !monthCalendar1.ShowToday;  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void Form1_DoubleClick(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          // Toggle between True and False.  
          monthCalendar1->ShowToday = !monthCalendar1->ShowToday;  
       }  
    ```  
  
     (Görsel C#, görsel C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a>Hafta numaralarını görüntüleme  
  
- Ayarlama <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> özelliğini `true`. Bu özelliği kodda ya da Özellikler penceresi olarak ayarlayabilirsiniz.  
  
     Hafta numaraları, haftanın ilk gününün solunda ayrı bir sütunda görüntülenir.  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [MonthCalendar Denetimi](monthcalendar-control-windows-forms.md)
- [Nasıl yapılır: Windows Forms MonthCalendar Denetiminde Tarih Aralığı Seçme](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [Nasıl yapılır: Windows Forms MonthCalendar Denetimi ile Belirli Günleri Kalın Olarak Görüntüleme](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [Nasıl yapılır: Windows Forms MonthCalendar Denetiminde Birden Fazla Ay Görüntüleme](display-more-than-one-month-wf-monthcalendar-control.md)
