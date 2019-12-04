---
title: Await İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
ms.openlocfilehash: e0c617ce32f80bdde1bcfda31da40ae610e07452
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74712358"
---
# <a name="await-operator-visual-basic"></a>Await İşleci (Visual Basic)

`Await` operatörünü awaited görevi tamamlanıncaya kadar, metodun yürütülmesini askıya almak için bir zaman uyumsuz metod veya lambda ifadesinde bir işlenene uygularsınız. Görev, devam eden işi temsil eder.

`Await` kullanıldığı yöntemin [zaman uyumsuz](../../../visual-basic/language-reference/modifiers/async.md) değiştiricisi olmalıdır. `Async` değiştirici kullanılarak tanımlanan ve genellikle bir veya daha fazla `Await` ifadesi içeren böyle bir yöntem, *zaman uyumsuz bir yöntem*olarak adlandırılır.

> [!NOTE]
> `Async` ve `Await` anahtar sözcükleri Visual Studio 2012 ' de tanıtılmıştı. Zaman uyumsuz programlamaya giriş için bkz. [Async ve await Ile zaman uyumsuz programlama](../../../visual-basic/programming-guide/concepts/async/index.md).

Genellikle, `Await` işlecini uyguladığınız görev, [görev tabanlı zaman uyumsuz model](https://www.microsoft.com/download/details.aspx?id=19957), yani bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>uygulayan bir yönteme yapılan çağrıdan dönüş değeridir.

Aşağıdaki kodda, <xref:System.Net.Http.HttpClient> yöntemi <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>, `getContentsTask`, bir `Task(Of Byte())` döndürür. Görev, işlem tamamlandığında gerçek bayt dizisini üretmek için bir vaattir. `Await` işleci, `getContentsTask` tamamlanana kadar `SumPageSizesAsync` yürütmeyi askıya almak için `getContentsTask` uygulanır. Bu sırada denetim, `SumPageSizesAsync`çağıranına döndürülür. `getContentsTask` tamamlandığında, `Await` ifadesi bir bayt dizisi olarak değerlendirilir.

```vb
Private Async Function SumPageSizesAsync() As Task

    ' To use the HttpClient type in desktop apps, you must include a using directive and add a
    ' reference for the System.Net.Http namespace.
    Dim client As HttpClient = New HttpClient()
    ' . . .
    Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
    Dim urlContents As Byte() = Await getContentsTask

    ' Equivalently, now that you see how it works, you can write the same thing in a single line.
    'Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
    ' . . .
End Function
```

> [!IMPORTANT]
> Tüm örnek için bkz. [Izlenecek yol: Async ve await kullanarak Web 'e erişme](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Örneği, Microsoft Web sitesindeki [Geliştirici kodu örneklerinden](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) indirebilirsiniz. Örnek, AsyncWalkthrough_HttpClient projem.

`Await` getiren bir metot çağrısının sonucuna `Task(Of TResult)` uygulanırsa, `Await` ifadesinin türü TResult olur. `Await`, bir `Task` getiren bir metot çağrısının sonucuna uygulanırsa, `Await` ifadesi bir değer getirmez. Aşağıdaki örnek, farkı göstermektedir.

```vb
' Await used with a method that returns a Task(Of TResult).
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()

' Await used with a method that returns a Task.
Await AsyncMethodThatReturnsTask()
```

Bir `Await` ifadesi veya açıklaması, üzerinde yürütme yaptığı iş parçacığını engellemez. Bunun yerine, `Await` ifadesinden sonra, bekleyen görevlerin bir devamı olarak, derleyicinin zaman uyumsuz yöntemin geri kalanını imzalamasına yol açar. Sonra Denetim zaman uyumsuz yöntemi çağırana döner. Görev tamamlandığında, devamlılığını çağırır ve zaman uyumsuz yöntemin yürütülmesi kaldığınız yerden devam eder.

Bir `Await` ifadesi yalnızca bir `Async` değiştiricisiyle işaretlenmiş bir anında kapatma metodunun veya lambda ifadesinin gövdesinde gerçekleşebilir. *Await* terimi yalnızca söz konusu bağlamda anahtar sözcük olarak işlev görür. Başka bir yerde, tanımlayıcı olarak yorumlanır. Zaman uyumsuz yöntem veya lambda ifadesi içinde, bir `Await` ifadesi bir sorgu ifadesinde, bir TRY öğesinin `catch` veya `finally` bloğunda gerçekleşemez [... Yakala... Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) deyimi, bir `For` veya `For Each` döngüsünün döngü denetim değişkeni ifadesinde veya bir [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) deyiminin gövdesinde.

## <a name="exceptions"></a>Özel Durumlar

En zaman uyumsuz yöntemler bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>döndürür. Döndürülen görevin özellikleri, görevin tamamlanıp tamamlanmayacağı, zaman uyumsuz yöntemin bir özel durum mi olduğunu, yoksa iptal edildiğini mi olduğunu ve nihai sonucun ne olduğunu belirtir gibi durum ve geçmişi hakkındaki bilgileri taşır. `Await` işleci bu özelliklere erişir.

Bir özel duruma neden olan bir görev döndüren zaman uyumsuz yöntemi beklelerseniz `Await` işleci özel durumu yeniden oluşturur.

İptal edilen bir görev döndüren zaman uyumsuz yöntemi beklerseniz, `Await` operatörü yeniden bir <xref:System.OperationCanceledException> oluşturur.

Hatalı durumda olan tek bir görev birden çok özel durumu yansıtabilir.  Örneğin, görev bir <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>çağrısının sonucu olabilir. Böyle bir görevi beklelerseniz, await işlemi özel durumların yalnızca birini yeniden oluşturur. Ancak, özel durumların hangisinin yeniden oluşturulduğu tahmin edebilirsiniz.

Zaman uyumsuz yöntemlerde hata işleme örnekleri için bkz [. TRY... Yakala... Finally ekstresi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).

## <a name="example"></a>Örnek

Aşağıdaki Windows Forms örnek, `WaitAsynchronouslyAsync`zaman uyumsuz yöntemde `Await` kullanımını gösterir. `WaitSynchronously`davranış ile bu yöntemin davranışını tersine kontrast. Bir `Await` operatörü olmadan, `WaitSynchronously` zaman uyumlu olarak çalışır, tanımında `Async` değiştiricisinin ve gövdesinde bir <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> çağrısı kullanılmasına rağmen.

```vb
Private Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
    ' Call the method that runs asynchronously.
    Dim result As String = Await WaitAsynchronouslyAsync()

    ' Call the method that runs synchronously.
    'Dim result As String = Await WaitSynchronously()

    ' Display the result.
    TextBox1.Text &= result
End Sub

' The following method runs asynchronously. The UI thread is not
' blocked during the delay. You can move or resize the Form1 window
' while Task.Delay is running.
Public Async Function WaitAsynchronouslyAsync() As Task(Of String)
    Await Task.Delay(10000)
    Return "Finished"
End Function

' The following method runs synchronously, despite the use of Async.
' You cannot move or resize the Form1 window while Thread.Sleep
' is running because the UI thread is blocked.
Public Async Function WaitSynchronously() As Task(Of String)
    ' Import System.Threading for the Sleep method.
    Thread.Sleep(10000)
    Return "Finished"
End Function
```

## <a name="see-also"></a>Ayrıca bkz.

- [Async ve Await ile Zaman Uyumsuz Programlama](../../../visual-basic/programming-guide/concepts/async/index.md)
- [İzlenecek yol: Async ve Await Kullanarak Web'e Erişme](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Async](../../../visual-basic/language-reference/modifiers/async.md)
