---
title: Parallel. ForEach kullanarak basit bir paralel program yazın
ms.date: 02/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
ms.openlocfilehash: c2f2484f37c0e99f45b3f10951540c2bb3a4cb8d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134171"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a>Nasıl yapılır: basit bir Parallel. ForEach Döngüsü Yazma

Bu örnek, <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> veri kaynağı üzerinde veri paralelliğini etkinleştirmek için <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> döngüsünün nasıl kullanılacağını gösterir.

> [!NOTE]
> Bu belgede, PLıNQ içinde temsilciler tanımlamak için lambda ifadeleri kullanılmaktadır. Veya Visual Basic içindeki C# lambda ifadeleriyle ilgili bilgi sahibi değilseniz bkz. [PLıNQ ve TPL içindeki lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

## <a name="example"></a>Örnek

Bu örnek, *C:\users\public\resim\sample resimler* klasöründe birkaç. jpg dosyası olduğunu varsayar ve *değiştirilmiş*adlı yeni bir alt klasör oluşturur. Örneği çalıştırdığınızda, *örnek resimlerde* her. jpg görüntüsünü döndürür ve *Değiştirilecek*şekilde kaydeder. Gerektiğinde iki yolu değiştirebilirsiniz.

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

Bir <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> döngüsü <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> döngüsü gibi çalışmaktadır. Döngü, kaynak koleksiyonu bölümler ve sistem ortamına göre birden çok iş parçacığında çalışmayı zamanlar. Sistemde daha fazla işlemci varsa, paralel yöntem daha hızlı çalışır. Bazı kaynak koleksiyonlarında, kaynağın boyutuna ve döngünün gerçekleştirdiği iş türüne bağlı olarak sıralı bir döngü daha hızlı olabilir. Performans hakkında daha fazla bilgi için bkz. [veri ve görev paralelliği Içindeki olası](potential-pitfalls-in-data-and-task-parallelism.md)bilgiler.

Paralel döngüler hakkında daha fazla bilgi için bkz. [nasıl yapılır: basit bir Parallel. for döngüsü yazma](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).

Genel olmayan bir koleksiyonla <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> kullanmak için, aşağıdaki örnekte gösterildiği gibi, koleksiyonu genel bir koleksiyona dönüştürmek için <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> uzantısı yöntemini kullanabilirsiniz:

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

Paralel LINQ (PLıNQ) kullanarak <xref:System.Collections.Generic.IEnumerable%601> veri kaynaklarını işlemeyi paralel hale getirmek de kullanabilirsiniz. PLıNQ, döngü davranışını ifade etmek için bildirime dayalı sorgu söz dizimi kullanmanıza olanak sağlar. Daha fazla bilgi için bkz. [Parallel LINQ (PLıNQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).

## <a name="compile-and-run-the-code"></a>Kodu derleyin ve çalıştırın

Kodu, .NET Framework için bir konsol uygulaması olarak veya .NET Core için bir konsol uygulaması olarak derleyebilirsiniz.

Visual Studio 'da, Windows Masaüstü ve .NET C# Core için Visual Basic ve konsol uygulaması şablonları vardır.

Komut satırından, .NET Core ve CLı araçlarından birini (örneğin, `dotnet new console` veya `dotnet new console -lang vb`) kullanabilir veya dosyayı oluşturabilir ve bir .NET Framework uygulaması için komut satırı derleyicisini kullanabilirsiniz.

Bir .NET Core projesi için **System. Drawing. Common** NuGet paketine başvurmanız gerekir. Visual Studio 'da, paketi yüklemek için NuGet Paket Yöneticisi ' ni kullanın. Alternatif olarak, \*. csproj veya \*. vbproj dosyanızdaki pakete bir başvuru ekleyebilirsiniz:
 
```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

Bir .NET Core konsol uygulamasını komut satırından çalıştırmak için, uygulamanızı içeren klasörden `dotnet run` kullanın.

Konsol uygulamanızı Visual Studio 'dan çalıştırmak için **F5**'e basın.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Paralel programlama](../../../docs/standard/parallel-programming/index.md)
- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
