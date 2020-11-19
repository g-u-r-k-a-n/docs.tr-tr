---
title: Visual Studio Code kullanarak bir .NET konsol uygulaması oluşturma
description: Visual Studio Code ve .NET CLı kullanarak bir .NET konsol uygulaması oluşturmayı öğrenin.
ms.date: 11/17/2020
ms.openlocfilehash: dbbdf88b0c84089249eb7e446c25eddc11543c1a
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94915875"
---
# <a name="tutorial-create-a-net-console-application-using-visual-studio-code"></a>Öğretici: Visual Studio Code kullanarak bir .NET konsol uygulaması oluşturma

Bu öğreticide, Visual Studio Code ve .NET CLı kullanarak bir .NET konsol uygulamasının nasıl oluşturulacağı ve çalıştırılacağı gösterilmektedir. Proje oluşturma, derleme ve çalıştırma gibi proje görevleri .NET CLı kullanılarak yapılır. Bu öğreticiyi, farklı bir kod Düzenleyicisi ile izleyebilir ve tercih ediyorsanız komutları terminalde çalıştırabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

1. [C# uzantısı](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) yüklü [Visual Studio Code](https://code.visualstudio.com/) . Visual Studio Code uzantıları nasıl yükleyeceğiniz hakkında daha fazla bilgi için bkz. [vs Code uzantısı marketi](https://code.visualstudio.com/docs/editor/extension-gallery).
2. [.Net 5,0 SDK veya üzeri](https://dotnet.microsoft.com/download)

## <a name="create-the-app"></a>Uygulama oluşturma

"HelloWorld" adlı bir .NET konsol uygulaması projesi oluşturun.

1. Visual Studio Code’u başlatın.

1. Ana menüden **Dosya**  >  **açma klasörünü** (**File**  >  MacOS üzerinde dosya **Aç...** ) seçin.

1. **Klasörü aç** iletişim kutusunda bir *HelloWorld* klasörü oluşturun ve **Klasör Seç** ' e tıklayın (MacOS üzerinde **açın** ).

   Klasör adı, varsayılan olarak proje adı ve ad alanı adı olur. Daha sonra, proje ad alanının olduğunu varsayan öğreticide kod ekleyeceksiniz `HelloWorld` .

1. Ana menüden **Terminal görünümü ' nu** seçerek **View** Visual Studio Code açın  >  **Terminal** .

   **Terminal** , *HelloWorld* klasöründe komut istemiyle açılır.

1. **Terminalde** aşağıdaki komutu girin:

   ```dotnetcli
   dotnet new console
   ```

Şablon basit bir "Merhaba Dünya" uygulaması oluşturur. <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>Konsol penceresinde "" görüntülenmesini sağlamak için yöntemini çağırır :::no-loc text="Hello World!"::: .

Şablon kodu, `Program` `Main` bağımsız değişken olarak bir diziyi alan tek bir yöntemi olan sınıfını tanımlar <xref:System.String> :

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

`Main` uygulama giriş noktası, uygulamayı başlattığında çalışma zamanı tarafından otomatik olarak çağrılan yöntemdir. Uygulama başlatıldığında sağlanan herhangi bir komut satırı bağımsız değişkeni, *args* dizisinde kullanılabilir.

## <a name="run-the-app"></a>Uygulamayı çalıştırma

**Terminalde** aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet run
```

Program "Merhaba Dünya!" görüntülüyor ve bitiyor.

![DotNet Run komutu](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="enhance-the-app"></a>Uygulamayı geliştirin

Kullanıcıya adını istemek ve Tarih ve saat ile birlikte göstermek için uygulamayı geliştirin.

1. *Program.cs* dosyasını tıklayarak açın.

   Visual Studio Code bir C# dosyasını ilk açışınızda, [Omnisharp](https://www.omnisharp.net/) düzenleyicide yüklenir.

   ![Program.cs dosyasını açın](media/with-visual-studio-code/open-program-cs.png)

1. Visual Studio Code, uygulamanızda derlemek ve hata ayıklamak için eksik varlıkları eklemenizi istediğinizde **Evet** ' i seçin.

   ![Eksik varlıklar için istem](media/with-visual-studio-code/missing-assets.png)

1. `Main`Aşağıdaki kodla, çağıran satır olan *program.cs* içindeki yönteminin içeriğini değiştirin `Console.WriteLine` :

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::

   Bu kod, konsol penceresinde bir istem görüntüler ve ardından <kbd>ENTER</kbd> tuşuna basarak Kullanıcı bir dize girene kadar bekler. Bu dizeyi adlı bir değişkende depolar `name` . Ayrıca <xref:System.DateTime.Now?displayProperty=nameWithType> , geçerli yerel saati içeren özelliğinin değerini alır ve bunu adlı bir değişkene atar `date` . Bu değerleri konsol penceresinde görüntüler. Son olarak, konsol penceresinde bir istem görüntüler ve <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> Kullanıcı girişini beklemek için yöntemini çağırır.

   `\n`Bir yeni satır karakterini temsil eder.

   `$`Bir dizenin önünde dolar işareti (), değişken adları gibi ifadeleri dizedeki küme ayraçları içine koymanıza imkan tanır. İfade değeri, ifadenin yerine dizeye eklenir. Bu söz dizimi, [enterpolasyonlu dizeler](../../csharp/language-reference/tokens/interpolated.md)olarak adlandırılır.

1. Yaptığınız değişiklikleri kaydedin.

   > [!IMPORTANT]
   > Visual Studio Code, değişiklikleri açıkça kaydetmeniz gerekir. Visual Studio 'dan farklı olarak, bir uygulamayı derleyip çalıştırdığınızda dosya değişiklikleri otomatik olarak kaydedilmez.

1. Programı yeniden çalıştırın:

   ```dotnetcli
   dotnet run
   ```

1. Bir ad girip <kbd>ENTER</kbd> tuşuna basarak istemi yanıtlayın.

   :::image type="content" source="media/debugging-with-visual-studio-code/run-modified-program.png" alt-text="Değiştirilmiş program çıkışını içeren Terminal penceresi":::

1. Programdan çıkmak için herhangi bir tuşa basın.

## <a name="additional-resources"></a>Ek kaynaklar

- [Visual Studio Code ayarlama](https://code.visualstudio.com/docs/setup/setup-overview)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, bir .NET konsol uygulaması oluşturdunuz. Sonraki öğreticide, uygulamada hata ayıklaması yapabilirsiniz.

> [!div class="nextstepaction"]
> [Visual Studio Code kullanarak bir .NET konsol uygulamasında hata ayıklama](debugging-with-visual-studio-code.md)
