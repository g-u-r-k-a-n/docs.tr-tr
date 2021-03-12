---
title: Main () dönüş değerleri-C# Programlama Kılavuzu
description: Main () dönüş değerleri hakkında bilgi edinin. Bkz. kod örnekleri, derleyici tarafından oluşturulan kod ve kullanılabilir ek kaynakları görüntüleme.
ms.date: 03/11/2021
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 6f4001ecd490d5627d3a1ec74ecf7d593451e104
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190365"
---
# <a name="main-return-values-c-programming-guide"></a>Main () dönüş değerleri (C# Programlama Kılavuzu)

Yöntemini `int` `Main` aşağıdaki yöntemlerden biriyle tanımlayarak yönteminden dönüştürebilirsiniz:

| `Main` Yöntem kodu             | `Main` imza                             |
|--------------------------------|----------------------------------------------|
| `args`Veya kullanımı`await`    | `static int Main()`                          |
| `args`, Kullanımları`await` | `static int Main(string[] args)`             |
| Kullanım yok `args` , kullanımları `await` | `static async Task<int> Main()`              |
| `args`Ve kullanır`await`        | `static async Task<int> Main(string[] args)` |

Dönüş değeri `Main` kullanılmazsa, `void` `Task` biraz daha basit bir kod döndürülmesi veya bu kodun kullanılmasına izin verir.

| `Main` Yöntem kodu             | `Main` imza                        |
|--------------------------------|-----------------------------------------|
| `args`Veya kullanımı`await`    | `static void Main()`                    |
| `args`, Kullanımları`await` | `static void Main(string[] args)`       |
| Kullanım yok `args` , kullanımları `await` | `static async Task Main()`              |
| `args`Ve kullanır`await`        | `static async Task Main(string[] args)` |

Ancak, `int` `Task<int>` programın durum bilgilerini yürütülebilir dosyayı çağıran diğer programlarla veya betiklerine iletmesine olanak sağlar.

Aşağıdaki örnek, işlem için çıkış kodunun nasıl erişilebilir olduğunu gösterir.

## <a name="example"></a>Örnek

Bu örnek [.NET Core](../../../core/introduction.md) komut satırı araçlarını kullanır. .NET Core komut satırı araçları hakkında bilginiz yoksa, bu [Get-Started makalesinde](../../../core/tutorials/with-visual-studio-code.md)hakkında bilgi edinebilirsiniz.

`Main` *Program.cs* içindeki yöntemi aşağıdaki gibi değiştirin:

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

Bir program Windows 'da yürütüldüğünde, işlevden döndürülen herhangi bir değer `Main` bir ortam değişkeninde depolanır. Bu ortam değişkeni `ERRORLEVEL` , bir toplu iş dosyasından veya PowerShell 'den kullanılarak alınabilir `$LastExitCode` .

[DotNet CLI](../../../core/tools/dotnet.md) komutunu kullanarak uygulamayı oluşturabilirsiniz `dotnet build` .

Sonra, uygulamayı çalıştırmak için bir PowerShell betiği oluşturun ve sonucu görüntüleyin. Aşağıdaki kodu bir metin dosyasına yapıştırın ve `test.ps1` projeyi içeren klasöre kaydedin. PowerShell komut istemine yazarak PowerShell betiğini çalıştırın `test.ps1` .

Kod sıfır döndürdüğünden, toplu iş dosyası başarıyı bildirir. Ancak, MainReturnValTest.cs değerini sıfır olmayan bir değer döndürecek şekilde değiştirirseniz ve sonra programı yeniden derleytiğinizde, PowerShell betiğinin sonraki yürütülmesi hata bildirir.

```dotnetcli
dotnet run
```

```powershell
if ($LastExitCode -eq 0) {
    Write-Host "Execution succeeded"
} else
{
    Write-Host "Execution Failed"
}
Write-Host "Return value = " $LastExitCode
```

## <a name="sample-output"></a>Örnek çıktı

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a>Zaman uyumsuz ana dönüş değerleri

Zaman uyumsuz ana dönüş değerleri, içinde zaman uyumsuz yöntemleri çağırmak için gereken ortak kodu `Main` derleyici tarafından oluşturulan koda taşır. Daha önce, zaman uyumsuz kodu çağırmak ve programınızın zaman uyumsuz işlem tamamlanana kadar çalıştığından emin olmak için bu yapıyı yazmanız gerekir:

```csharp
public static void Main()
{
    AsyncConsoleWork().GetAwaiter().GetResult();
}

private static async Task<int> AsyncConsoleWork()
{
    // Main body here
    return 0;
}
```

Şimdi bu, şu şekilde değiştirilebilir:

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

Yeni sözdiziminin avantajı, derleyicinin her zaman doğru kodu üretmesinin avantajına sahiptir.

## <a name="compiler-generated-code"></a>Derleyici tarafından üretilen kod

Uygulama giriş noktası bir `Task` veya döndürdüğünde `Task<int>` , derleyici uygulama kodunda belirtilen giriş noktası yöntemini çağıran yeni bir giriş noktası oluşturur. Bu giriş noktasının çağrıldığı kabul edildiğinde `$GeneratedMain` , derleyici bu giriş noktaları için aşağıdaki kodu üretir:

- `static Task Main()` Derleyicinin ' ın eşdeğerini yaymasına ilişkin sonuçlar `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task Main(string[])` Derleyicinin ' ın eşdeğerini yaymasına ilişkin sonuçlar `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`
- `static Task<int> Main()` Derleyicinin ' ın eşdeğerini yaymasına ilişkin sonuçlar `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`
- `static Task<int> Main(string[])` Derleyicinin ' ın eşdeğerini yaymasına ilişkin sonuçlar `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`

> [!NOTE]
>Örnekler `async` yöntemde değiştirici kullandıysanız `Main` , derleyici aynı kodu oluşturur.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [C# başvurusu](../../language-reference/index.md)
- [Main () ve Command-Line bağımsız değişkenleri](index.md)
- [Komut satırı bağımsız değişkenlerini görüntüleme](./how-to-display-command-line-arguments.md)
