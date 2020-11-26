---
title: 'Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme'
description: .NET 'teki uygulama koduna izleme deyimleri eklemeyi öğrenin. İzleme için en sık kullanılan yöntemler, dinleyicilerine çıkış yazma yöntemleridir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tracing [.NET Framework], conditional writes based on switches
- trace statements
- WriteLineIf method
- tracing [.NET Framework], adding trace statements
- Assert method, tracing code
- trace switches, conditional writes based on switches
- WriteIf method
ms.assetid: f3a93fa7-1717-467d-aaff-393e5c9828b4
ms.openlocfilehash: 6beecf39d4372a194a9110ed8942b998443934d4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244216"
---
# <a name="how-to-add-trace-statements-to-application-code"></a>Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme

İzleme için en sık kullanılan yöntemler, dinleyicilerine çıkış yazma yöntemleridir: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **onaylama** ve **başarısız**. Bu yöntemler iki kategoriye ayrılabilir: **Write**, **WriteLine** ve **Fail** for All, on Unon, **WriteLineIf** ve **WriteIf** **onaylama** testi, Boolean koşulunu ve onay testini, koşulun değerine göre yazma veya yazma. Koşul ise, **WriteIf** ve **WriteLineIf** bir çıkış yayıyorsa `true` , **Assert** Eğer koşul ise çıkış yayar `false` .  
  
 İzleme ve hata ayıklama stratejinizi tasarlarken çıkışın nasıl görünmesini istediğinizi ele almanız gerekir. İlişkisiz bilgilerle doldurulmuş birden fazla **yazma** deyimi, okunması zor olan bir günlük oluşturur. Diğer taraftan, ilişkili deyimleri ayrı satırlara koymak için **WriteLine** kullanmak, hangi bilgilerin birlikte olduğunu ayırt etmenizi zorlaştırır. Genel olarak, tek bir bilgilendirici ileti oluşturmak için birden fazla kaynaktaki bilgileri birleştirmek istediğinizde birden çok **yazma** ifadesi kullanın ve tek bir ileti oluşturmak istediğinizde **WriteLine** deyimini kullanın.  
  
### <a name="to-write-a-complete-line"></a>Tüm satırları yazmak için  
  
1. Arama <xref:System.Diagnostics.Trace.WriteLine%2A> veya <xref:System.Diagnostics.Trace.WriteLineIf%2A> yöntemi.  
  
     Bu yöntemin döndürdüğü iletinin sonuna bir satır başı eklenir, böylece **Write**, **WriteIf**, **WriteLine** veya **writelinetarafından** döndürülen sonraki ileti aşağıdaki satırda başlayacaktır:  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteLine("Error in AppendData procedure.")  
    Trace.WriteLineIf(errorFlag, "Error in AppendData procedure.")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteLine ("Error in AppendData procedure.");  
    System.Diagnostics.Trace.WriteLineIf(errorFlag,
       "Error in AppendData procedure.");  
    ```  
  
### <a name="to-write-a-partial-line"></a>Kısmi satır yazmak için  
  
1. Arama <xref:System.Diagnostics.Trace.Write%2A> veya <xref:System.Diagnostics.Trace.WriteIf%2A> yöntemi.  
  
     Sonraki ileti bir **Write**, **WriteIf**, **WriteLine** veya **WriteLineIf** tarafından dışarı yazılır ve bu, **Write** veya **WriteIf** ifadesiyle ileti yerleştirerek aynı satırda başlayacaktır:  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteIf(errorFlag, "Error in AppendData procedure.")  
    Debug.WriteIf(errorFlag, "Transaction abandoned.")  
    Trace.Write("Invalid value for data request")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteIf(errorFlag,
       "Error in AppendData procedure.");  
    System.Diagnostics.Debug.WriteIf(errorFlag, "Transaction abandoned.");  
    Trace.Write("Invalid value for data request");  
    ```  
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a>Belirli koşulların, bir yöntemi yürütmeden önce veya sonra var olduğunu doğrulamak için  
  
1. Yöntemini çağırın <xref:System.Diagnostics.Trace.Assert%2A> .  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    > Hem izleme hem de hata ayıklama ile **onaylama** kullanabilirsiniz. Bu **örnek, çağrı yığınını dinleyici koleksiyonundaki herhangi** bir dinleyiciye verir. Daha fazla bilgi için bkz. [Yönetilen koddaki Onaylamalar](/visualstudio/debugger/assertions-in-managed-code) ve <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>
- [Uygulamaları izleme ve İşaretleme](tracing-and-instrumenting-applications.md)
- [Nasıl yapılır: İzleme Anahtarları Oluşturma ve Başlatma](how-to-create-initialize-and-configure-trace-switches.md)
- [İzleme Anahtarları](trace-switches.md)
- [İz Dinleyicileri](trace-listeners.md)
