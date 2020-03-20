---
title: Zamanlayıcı Bileşeni ile Ayarlı Aralıklarda Yordamları Çalıştır
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], timers
- timers [Windows Forms], event intervals
- initialization [Windows Forms], Timer components
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], initializing
- procedures [Windows Forms], specific time intervals
ms.assetid: 8025247a-2de4-4d86-b8ab-a8cb8aeab2ea
ms.openlocfilehash: 52d68a8136551384f67ff6232799600af09f8b66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182053"
---
# <a name="how-to-run-procedures-at-set-intervals-with-the-windows-forms-timer-component"></a>Nasıl yapılır: Windows Forms Süreölçer Bileşeni ile Belirlenen Aralıklarda Yordamları Çalıştırma
Bazen bir döngü bitene veya belirli bir zaman aralığı dolduğunda çalışana kadar belirli zaman aralıklarında çalışan bir yordam oluşturmak isteyebilirsiniz. Bileşen <xref:System.Windows.Forms.Timer> böyle bir yordamı mümkün kılar.  
  
 Bu bileşen, Windows Forms ortamı için tasarlanmıştır. Sunucu ortamı için uygun bir zamanlayıcıya ihtiyacınız varsa, [bkz.](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90))  
  
> [!NOTE]
> <xref:System.Windows.Forms.Timer> Bileşeni kullanırken bazı sınırlamalar vardır. Daha fazla bilgi için Bkz. [Windows Formlar Zamanlayıcı Bileşeninin Interval Özelliğinin Sınırlamaları.](limitations-of-the-timer-component-interval-property.md)  
  
## <a name="to-run-a-procedure-at-set-intervals-with-the-timer-component"></a>Zamanlayıcı bileşeni ile belirli aralıklarla bir yordam çalıştırmak için  
  
1. Formunuza <xref:System.Windows.Forms.Timer> bir ekleyin. Bunu programlı olarak nasıl yapacağınız ile ilgili bir resim için aşağıdaki Örnek bölümüne bakın. Visual Studio da bir forma bileşenleri eklemek için destek vardır. Ayrıca [bkz.](how-to-add-controls-without-a-user-interface-to-windows-forms.md)  
  
2. Zamanlayıcının özelliğini <xref:System.Windows.Forms.Timer.Interval%2A> (milisaniye cinsinden) ayarlayın. Bu özellik, yordam yeniden çalıştırılmadan önce ne kadar zaman geçeceğini belirler.  
  
    > [!NOTE]
    > Zamanlayıcı olayı ne kadar sık gerçekleşirse, olaya yanıt vermede o kadar çok işlemci süresi kullanılır. Bu, genel performansı yavaşlatabilir. İhtiyacınız olandan daha küçük bir aralık ayarlamayın.  
  
3. Olay işleyicisi <xref:System.Windows.Forms.Timer.Tick> uygun kod yazın. Bu olayda yazdığınız <xref:System.Windows.Forms.Timer.Interval%2A> kod, özellikte belirtilen aralıkta çalışır.  
  
4. Özelliği <xref:System.Windows.Forms.Timer.Enabled%2A> zamanlayıcıyı başlatmak için `true` ayarlayın. Yordamınızı <xref:System.Windows.Forms.Timer.Tick> ayarlanan aralıkta çalıştırarak olay oluşmaya başlar.  
  
5. Uygun zamanda, yordamın <xref:System.Windows.Forms.Timer.Enabled%2A> yeniden `false` çalışmasını durdurmak için özelliği ayarlayın. Aralığı ayarlamak `0` zamanlayıcının durmasına neden olmaz.  
  
## <a name="example"></a>Örnek  
 Bu ilk kod örneği, bir saniyelik artışlarla günün saatini izler. Bir form <xref:System.Windows.Forms.Button>üzerinde <xref:System.Windows.Forms.Label>bir <xref:System.Windows.Forms.Timer> , a ve bileşen kullanır. Özellik <xref:System.Windows.Forms.Timer.Interval%2A> 1000 olarak ayarlanır (bir saniyeye eşittir). <xref:System.Windows.Forms.Timer.Tick> Olayda, etiketin resim yazısı geçerli saate ayarlanır. Düğme tıklatıldığında, <xref:System.Windows.Forms.Timer.Enabled%2A> özellik `false`zamanlayıcının etiketin alt yazısını güncelleştirmesini durduracak şekilde ayarlanır. <xref:System.Windows.Forms.Button> Aşağıdaki kod örneği, adlı `Button1` <xref:System.Windows.Forms.Timer> `Timer1`bir denetim , bir denetim ve <xref:System.Windows.Forms.Label> adlı `Label1`bir denetim ile bir form gerektirir .  
  
```vb  
Private Sub InitializeTimer()  
   ' Run this procedure in an appropriate event.  
   ' Set to 1 second.  
   Timer1.Interval = 1000  
   ' Enable timer.  
   Timer1.Enabled = True  
   Button1.Text = "Enabled"  
End Sub  
x  
Private Sub Timer1_Tick(ByVal Sender As Object, ByVal e As EventArgs) Handles Timer1.Tick  
' Set the caption to the current time.  
   Label1.Text = DateTime.Now  
End Sub  
  
Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
      If Button1.Text = "Stop" Then  
         Button1.Text = "Start"  
         Timer1.Enabled = False  
      Else  
         Button1.Text = "Stop"  
         Timer1.Enabled = True  
      End If  
End Sub  
```  
  
```csharp  
private void InitializeTimer()  
{  
    // Call this procedure when the application starts.  
    // Set to 1 second.  
    Timer1.Interval = 1000;  
    Timer1.Tick += new EventHandler(Timer1_Tick);  
  
    // Enable timer.  
    Timer1.Enabled = true;  
  
    Button1.Text = "Stop";  
    Button1.Click += new EventHandler(Button1_Click);  
}  
  
private void Timer1_Tick(object Sender, EventArgs e)
{  
   // Set the caption to the current time.  
   Label1.Text = DateTime.Now.ToString();  
}  
  
private void Button1_Click(object sender, EventArgs e)  
{  
  if ( Button1.Text == "Stop" )  
  {  
    Button1.Text = "Start";  
    Timer1.Enabled = false;  
  }  
  else  
  {  
    Button1.Text = "Stop";  
    Timer1.Enabled = true;  
  }  
}  
```  
  
```cpp  
private:  
   void InitializeTimer()  
   {  
      // Run this procedure in an appropriate event.  
      // Set to 1 second.  
      timer1->Interval = 1000;  
      // Enable timer.  
      timer1->Enabled = true;  
      this->timer1->Tick += gcnew System::EventHandler(this,
                               &Form1::timer1_Tick);  
  
      button1->Text = S"Stop";  
      this->button1->Click += gcnew System::EventHandler(this,
                               &Form1::button1_Click);  
   }  
  
   void timer1_Tick(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      // Set the caption to the current time.  
      label1->Text = DateTime::Now.ToString();  
   }  
  
   void button1_Click(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      if ( button1->Text == "Stop" )  
      {  
         button1->Text = "Start";  
         timer1->Enabled = false;  
      }  
      else  
      {  
         button1->Text = "Stop";  
         timer1->Enabled = true;  
      }  
   }  
```  
  
## <a name="example"></a>Örnek  
 Bu ikinci kod örneği, bir döngü bitene kadar her 600 milisaniyede bir yordam çalıştırın. <xref:System.Windows.Forms.Button> Aşağıdaki kod örneği, adlı `Button1` <xref:System.Windows.Forms.Timer> `Timer1`bir denetim , bir denetim ve <xref:System.Windows.Forms.Label> adlı `Label1`bir denetim ile bir form gerektirir .  
  
```vb  
' This variable will be the loop counter.  
Private counter As Integer  
  
Private Sub InitializeTimer()  
   ' Run this procedure in an appropriate event.  
   counter = 0  
   Timer1.Interval = 600  
   Timer1.Enabled = True  
End Sub  
  
Private Sub Timer1_Tick(ByVal sender As Object, ByVal e As System.EventArgs) Handles Timer1.Tick  
   If counter => 10 Then  
      ' Exit loop code.  
      Timer1.Enabled = False  
      counter = 0  
   Else  
      ' Run your procedure here.  
      ' Increment counter.  
      counter = counter + 1  
      Label1.Text = "Procedures Run: " & counter.ToString  
   End If  
End Sub  
```  
  
```csharp  
// This variable will be the loop counter.  
private int counter;  
  
private void InitializeTimer()  
{  
   // Run this procedure in an appropriate event.  
   counter = 0;  
   timer1.Interval = 600;  
   timer1.Enabled = true;  
   // Hook up timer's tick event handler.  
   this.timer1.Tick += new System.EventHandler(this.timer1_Tick);  
}  
  
private void timer1_Tick(object sender, System.EventArgs e)
{  
   if (counter >= 10)
   {  
      // Exit loop code.  
      timer1.Enabled = false;  
      counter = 0;  
   }  
   else  
   {  
      // Run your procedure here.  
      // Increment counter.  
      counter = counter + 1;  
      label1.Text = "Procedures Run: " + counter.ToString();  
      }  
}  
```  
  
```cpp  
private:  
   int counter;  
  
   void InitializeTimer()  
   {  
      // Run this procedure in an appropriate event.  
      counter = 0;  
      timer1->Interval = 600;  
      timer1->Enabled = true;  
      // Hook up timer's tick event handler.  
      this->timer1->Tick += gcnew System::EventHandler(this, &Form1::timer1_Tick);  
   }  
  
   void timer1_Tick(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      if (counter >= 10)
      {  
         // Exit loop code.  
         timer1->Enabled = false;  
         counter = 0;  
      }  
      else  
      {  
         // Run your procedure here.  
         // Increment counter.  
         counter = counter + 1;  
         label1->Text = String::Concat("Procedures Run: ",  
            counter.ToString());  
      }  
   }  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Timer>
- [Süreölçer Bileşeni](timer-component-windows-forms.md)
- [Süreölçer Bileşenine Genel Bakış](timer-component-overview-windows-forms.md)
