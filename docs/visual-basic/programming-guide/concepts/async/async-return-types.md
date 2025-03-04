---
description: 'Daha fazla bilgi edinin: zaman uyumsuz dönüş türleri (Visual Basic)'
title: Zaman Uyumsuz Dönüş Türleri
ms.date: 07/20/2015
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
ms.openlocfilehash: 12a7f577a89ff8f8037de879f9e37d6fdb917aa8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100438924"
---
# <a name="async-return-types-visual-basic"></a>Zaman uyumsuz dönüş türleri (Visual Basic)

Zaman uyumsuz metotlarda üç olası dönüş türü vardır: <xref:System.Threading.Tasks.Task%601> , <xref:System.Threading.Tasks.Task> ve void. Visual Basic, void dönüş türü bir [alt](../../language-features/procedures/sub-procedures.md) yordam olarak yazılır. Zaman uyumsuz yöntemler hakkında daha fazla bilgi için bkz. [Async ve await Ile zaman uyumsuz programlama (Visual Basic)](index.md).

Her dönüş türü aşağıdaki bölümlerden birinde incelenir ve konunun sonunda her üç türü kullanan tam bir örnek bulabilirsiniz.

> [!NOTE]
> Örneği çalıştırmak için, bilgisayarınızda Visual Studio 2012 veya daha yeni bir sürümü ve .NET Framework 4,5 ya da daha yeni bir sürümü yüklü olmalıdır.

## <a name="taskt-return-type"></a><a name="BKMK_TaskTReturnType"></a> Görev (T) dönüş türü

<xref:System.Threading.Tasks.Task%601>Dönüş türü, işlenenin türü olan bir [Return](../../../language-reference/statements/return-statement.md) ifadesini içeren zaman uyumsuz bir yöntem için kullanılır `TResult` .

Aşağıdaki örnekte, `TaskOfT_MethodAsync` Async yöntemi bir tamsayı döndüren return ifadesini içerir. Bu nedenle, metot bildiriminin bir dönüş türü belirtmesi gerekir `Task(Of Integer)` .

```vb
' TASK(OF T) EXAMPLE
Async Function TaskOfT_MethodAsync() As Task(Of Integer)

    ' The body of an async method is expected to contain an awaited
    ' asynchronous call.
    ' Task.FromResult is a placeholder for actual work that returns a string.
    Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())

    ' The method then can process the result in some way.
    Dim leisureHours As Integer
    If today.First() = "S" Then
        leisureHours = 16
    Else
        leisureHours = 5
    End If

    ' Because the return statement specifies an operand of type Integer, the
    ' method must have a return type of Task(Of Integer).
    Return leisureHours
End Function
```

`TaskOfT_MethodAsync`Await ifadesi içinden çağrıldığında, await ifadesi `leisureHours` tarafından döndürülen görevde depolanan tamsayı değerini (değeri) alır `TaskOfT_MethodAsync` . Await ifadeleri hakkında daha fazla bilgi için bkz. [Await işleci](../../../language-reference/operators/await-operator.md).

Aşağıdaki kod çağrıları ve Await yöntemi `TaskOfT_MethodAsync` . Sonuç `result1` değişkenine atanır.

```vb
' Call and await the Task(Of T)-returning async method in the same statement.
Dim result1 As Integer = Await TaskOfT_MethodAsync()
```

`TaskOfT_MethodAsync` `Await` Aşağıdaki kodda gösterildiği gibi, çağrısını uygulamasından ayırarak bunun nasıl gerçekleştiğini daha iyi anlayabilirsiniz. `TaskOfT_MethodAsync`Yönteminin bildiriminden bekleyebileceğiniz için hemen beklenen bir yönteme çağrı bir döndürür `Task(Of Integer)` . Görev `integerTask` örnekteki değişkenine atanır. `integerTask`Bir olduğundan <xref:System.Threading.Tasks.Task%601> , türünde bir özelliği içerir <xref:System.Threading.Tasks.Task%601.Result> `TResult` . Bu durumda, TResult bir tamsayı türünü temsil eder. `Await`Öğesine uygulandığında `integerTask` , await ifadesi <xref:System.Threading.Tasks.Task%601.Result%2A> öğesinin özelliğinin içeriğini değerlendirir `integerTask` . Değer `result2` değişkenine atanır.

> [!WARNING]
> <xref:System.Threading.Tasks.Task%601.Result%2A>Özelliği engelleyici bir özelliktir. Görevi tamamlanmadan önce ona erişmeye çalışırsanız, etkin olan iş parçacığı, görev tamamlanana ve değer kullanılabilir olana kadar engellenir. Çoğu durumda, `Await` özelliğine doğrudan erişmek yerine kullanarak değere erişmeniz gerekir.

```vb
' Call and await in separate statements.
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()

' You can do other work that does not rely on resultTask before awaiting.
textBox1.Text &= "Application can continue working while the Task(Of T) runs. . . . " & vbCrLf

Dim result2 As Integer = Await integerTask
```

Aşağıdaki koddaki Display deyimleri, `result1` değişkenin değerlerinin, `result2` değişkenin ve `Result` özelliğinin aynı olduğunu doğrular. `Result`Özelliğin engelleme özelliği olduğunu ve görevi beklenmeden önce erişilmemesi gerektiğini unutmayın.

```vb
' Display the values of the result1 variable, the result2 variable, and
' the resultTask.Result property.
textBox1.Text &= vbCrLf & $"Value of result1 variable:   {result1}" & vbCrLf
textBox1.Text &= $"Value of result2 variable:   {result2}" & vbCrLf
textBox1.Text &= $"Value of resultTask.Result:  {integerTask.Result}" & vbCrLf
```

## <a name="task-return-type"></a><a name="BKMK_TaskReturnType"></a> Görev dönüş türü

Dönüş açıklaması içermeyen veya bir işleneni döndürmeyen bir return ifadesini içeren zaman uyumsuz yöntemler genellikle dönüş türüne sahiptir <xref:System.Threading.Tasks.Task> . Bu tür yöntemler, zaman uyumlu olarak çalışmak üzere yazılmışsa [alt](../../language-features/procedures/sub-procedures.md) yordamlar olur. `Task`Zaman uyumsuz bir yöntem için dönüş türü kullanırsanız, çağıran `Await` zaman uyumsuz yöntem bitene kadar çağıranın tamamlanmasını askıya almak için bir operatör kullanabilirsiniz.

Aşağıdaki örnekte, Async yöntemi `Task_MethodAsync` return ifadesini içermez. Bu nedenle, `Task` beklenmeye olanak tanıyan yöntemi için dönüş türü belirtirsiniz `Task_MethodAsync` . `Task`Türün tanımı `Result` bir dönüş değeri depolamak için bir özellik içermez.

```vb
' TASK EXAMPLE
Async Function Task_MethodAsync() As Task

    ' The body of an async method is expected to contain an awaited
    ' asynchronous call.
    ' Task.Delay is a placeholder for actual work.
    Await Task.Delay(2000)
    textBox1.Text &= vbCrLf & "Sorry for the delay. . . ." & vbCrLf

    ' This method has no return statement, so its return type is Task.
End Function
```

`Task_MethodAsync` , zaman uyumlu veya void döndüren bir yöntem için çağırma deyimine benzer bir await ifadesi yerine await deyimi kullanılarak çağrılır ve bekletildi `Sub` . `Await`Bu durumda bir işlecin uygulaması bir değer üretmez.

Aşağıdaki kod çağrıları ve Await yöntemi `Task_MethodAsync` .

```vb
' Call and await the Task-returning async method in the same statement.
Await Task_MethodAsync()
```

Önceki örnekte olduğu gibi <xref:System.Threading.Tasks.Task%601> , `Task_MethodAsync` `Await` aşağıdaki kodda gösterildiği gibi, çağrısını bir işlecin uygulamasından ayırabilirsiniz. Ancak, bir `Task` özelliğine sahip olmadığını `Result` ve bir Await işleci uygulandığında hiçbir değer üretilmediğini unutmayın `Task` .

Aşağıdaki kod, çağırma `Task_MethodAsync` görevinin döndürdüğü görevi bekleten ayırır `Task_MethodAsync` .

```vb
' Call and await in separate statements.
Dim simpleTask As Task = Task_MethodAsync()

' You can do other work that does not rely on simpleTask before awaiting.
textBox1.Text &= vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf

Await simpleTask
```

## <a name="void-return-type"></a><a name="BKMK_VoidReturnType"></a> Void dönüş türü

Yordamların birincil kullanımı, `Sub` dönüş türü olmayan (diğer dillerde void dönüş türü olarak ifade edilen) olay işleyicileridir. Void Return Ayrıca, void döndüren yöntemleri geçersiz kılmak için veya "Fire ve unut" olarak kategorilere ayrılmamış etkinlikler gerçekleştiren yöntemler için de kullanılabilir. Ancak, `Task` void döndüren zaman uyumsuz bir yöntem beklenmediğinden, mümkün olan her yerde dönebilmelisiniz. Bu tür bir yöntemi çağıran, çağrılan zaman uyumsuz yöntemin tamamlanmasını beklemeden tamamlamaya devam edebilmelidir ve çağıranın, zaman uyumsuz yöntemin ürettiği herhangi bir değerden veya özel durumlardan bağımsız olması gerekir.

Void döndüren zaman uyumsuz bir yöntemi çağıran, yöntemden oluşturulan özel durumları yakalayabilir ve bu tür işlenmemiş özel durumlar uygulamanızın başarısız olmasına neden olabilir. Bir veya döndüren zaman uyumsuz bir yöntemde özel durum oluşursa <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> , özel durum döndürülen görevde depolanır ve görev beklendiğinde yeniden oluşturulur. Bu nedenle, bir özel durum üretemeyen herhangi bir zaman uyumsuz metodun, veya dönüş türüne sahip olduğundan ve metoda yapılan çağrıların beklenmediğinden emin olun <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> .

Zaman uyumsuz yöntemlerde özel durumları yakalama hakkında daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](../../../language-reference/statements/try-catch-finally-statement.md).

Aşağıdaki kod zaman uyumsuz bir olay işleyicisini tanımlar.

```vb
' SUB EXAMPLE
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click

    textBox1.Clear()

    ' Start the process and await its completion. DriverAsync is a
    ' Task-returning async method.
    Await DriverAsync()

    ' Say goodbye.
    textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."
End Sub
```

## <a name="complete-example"></a><a name="BKMK_Example"></a> Örnek Tamam

Aşağıdaki Windows Presentation Foundation (WPF) projesi bu konudan kod örneklerini içerir.

 Projeyi çalıştırmak için aşağıdaki adımları gerçekleştirin:

1. Visual Studio’yu çalıştırın.

2. Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.

     **Yeni proje** iletişim kutusu açılır.

3. **Yüklü**, **Şablonlar** kategorisinde **Visual Basic** ve ardından **Windows**' u seçin. Proje türleri listesinden **WPF uygulaması** ' nı seçin.

4. `AsyncReturnTypes`Projenin adı olarak girin ve **Tamam** düğmesini seçin.

     Yeni proje **Çözüm Gezgini** görüntülenir.

5. Visual Studio Code düzenleyicisinde **MainWindow. xaml** sekmesini seçin.

     Sekme görünür değilse, **Çözüm Gezgini**' de MainWindow. xaml için kısayol menüsünü açın ve **Aç**' ı seçin.

6. MainWindow. xaml ' nin **xaml** penceresinde, kodu aşağıdaki kodla değiştirin.

    ```vb
    <Window x:Class="MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            Title="MainWindow" Height="350" Width="525">
        <Grid>
            <Button x:Name="button1" Content="Start" HorizontalAlignment="Left" Margin="214,28,0,0" VerticalAlignment="Top" Width="75" HorizontalContentAlignment="Center" FontWeight="Bold" FontFamily="Aharoni" Click="button1_Click"/>
            <TextBox x:Name="textBox1" Margin="0,80,0,0" TextWrapping="Wrap" FontFamily="Lucida Console"/>

        </Grid>
    </Window>
    ```

     Bir metin kutusu ve bir düğme içeren basit bir pencere, MainWindow. xaml **Tasarım** penceresinde görünür.

7. **Çözüm Gezgini**, MainWindow. xaml. vb için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

8. MainWindow. xaml. vb içindeki kodu aşağıdaki kodla değiştirin.

    ```vb
    Class MainWindow

        ' SUB EXAMPLE
        Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click

            textBox1.Clear()

            ' Start the process and await its completion. DriverAsync is a
            ' Task-returning async method.
            Await DriverAsync()

            ' Say goodbye.
            textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."
        End Sub

        Async Function DriverAsync() As Task

            ' Task(Of T)
            ' Call and await the Task(Of T)-returning async method in the same statement.
            Dim result1 As Integer = Await TaskOfT_MethodAsync()

            ' Call and await in separate statements.
            Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()

            ' You can do other work that does not rely on resultTask before awaiting.
            textBox1.Text &= "Application can continue working while the Task(Of T) runs. . . . " & vbCrLf

            Dim result2 As Integer = Await integerTask

            ' Display the values of the result1 variable, the result2 variable, and
            ' the resultTask.Result property.
            textBox1.Text &= vbCrLf & $"Value of result1 variable:   {result1}" & vbCrLf
            textBox1.Text &= $"Value of result2 variable:   {result2}" & vbCrLf
            textBox1.Text &= $"Value of resultTask.Result:  {integerTask.Result}" & vbCrLf

            ' Task
            ' Call and await the Task-returning async method in the same statement.
            Await Task_MethodAsync()

            ' Call and await in separate statements.
            Dim simpleTask As Task = Task_MethodAsync()

            ' You can do other work that does not rely on simpleTask before awaiting.
            textBox1.Text &= vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf

            Await simpleTask
        End Function

        ' TASK(OF T) EXAMPLE
        Async Function TaskOfT_MethodAsync() As Task(Of Integer)

            ' The body of an async method is expected to contain an awaited
            ' asynchronous call.
            ' Task.FromResult is a placeholder for actual work that returns a string.
            Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())

            ' The method then can process the result in some way.
            Dim leisureHours As Integer
            If today.First() = "S" Then
                leisureHours = 16
            Else
                leisureHours = 5
            End If

            ' Because the return statement specifies an operand of type Integer, the
            ' method must have a return type of Task(Of Integer).
            Return leisureHours
        End Function

        ' TASK EXAMPLE
        Async Function Task_MethodAsync() As Task

            ' The body of an async method is expected to contain an awaited
            ' asynchronous call.
            ' Task.Delay is a placeholder for actual work.
            Await Task.Delay(2000)
            textBox1.Text &= vbCrLf & "Sorry for the delay. . . ." & vbCrLf

            ' This method has no return statement, so its return type is Task.
        End Function

    End Class
    ```

9. Programı çalıştırmak için F5 tuşunu seçin ve sonra **Başlat** düğmesini seçin.

     Aşağıdaki çıkışın görünmesi gerekir:

    ```console
    Application can continue working while the Task<T> runs. . . .

    Value of result1 variable:   5
    Value of result2 variable:   5
    Value of integerTask.Result: 5

    Sorry for the delay. . . .

    Application can continue working while the Task runs. . . .

    Sorry for the delay. . . .

    All done, exiting button-click event handler.
    ```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [İzlenecek yol: Async ve await kullanarak Web 'e erişme (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Zaman uyumsuz programlarda denetim akışı (Visual Basic)](control-flow-in-async-programs.md)
- [Eş](../../../language-reference/modifiers/async.md)
- [Await Işleci](../../../language-reference/operators/await-operator.md)
