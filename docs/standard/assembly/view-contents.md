---
title: 'Nasıl yapılır: derleme içeriğini görüntüleme'
description: Bir derlemenin özniteliklerini ve diğer modüller ve derlemelere yönelik başvuruları görüntülemek için Il ayrıştırma ' i kullanabilirsiniz.
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: c881abc3e88df4c1855a0faa29936621a4488078
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103060"
---
# <a name="how-to-view-assembly-contents"></a>Nasıl yapılır: derleme içeriğini görüntüleme

Microsoft ara dili (MSIL) bilgilerini bir dosyada görüntülemek için [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) kullanabilirsiniz. İncelenen dosya bir derlemedir, bu bilgiler derlemenin özniteliklerini ve diğer modüller ve derlemelere yönelik başvuruları içerebilir. Bu bilgiler, bir dosyanın derleme veya bir derlemenin parçası olup olmadığını ve dosyanın diğer modüllere veya derlemelere başvurular içerip içermediğini belirlemede yardımcı olabilir.

*Ildasm.exe* kullanarak bir derlemenin içeriğini göstermek için, komut istemine **ıldadsm \<assembly name>** girin. Örneğin, aşağıdaki komut *Hello.exe* derlemesini ayrıştırır.

```cmd
ildasm Hello.exe
```

Derleme bildirimi bilgilerini görüntülemek için MSIL ayrıştırma penceresindeki **bildirim** simgesine çift tıklayın.

## <a name="example"></a>Örnek

Aşağıdaki örnek, temel bir "Merhaba Dünya" programıyla başlar. Programı derledikten sonra, *Hello.exe* derlemesini ve derleme bildirimini görüntülemek için *Ildasm.exe* kullanın.

```cpp
using namespace System;

class MainApp
{
public:
    static void Main()
    {
        Console::WriteLine("Hello World using C++/CLI!");
    }
};

int main()
{
    MainApp::Main();
}
```

```csharp
using System;

class MainApp
{
    public static void Main()
    {
        Console.WriteLine("Hello World using C#!");
    }
}
```

```vb
Class MainApp
    Public Shared Sub Main()
        Console.WriteLine("Hello World using Visual Basic!")
    End Sub
End Class
```

*Hello.exe* derlemesinde komut *ildasm.exe* çalıştırmak ve MSIL ayrıştırma penceresindeki **bildirim** simgesine çift tıklamak aşağıdaki çıktıyı üretir:

```output
// Metadata version: v4.0.30319
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 4:0:0:0
}
.assembly Hello
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .custom instance void [mscorlib]System.Runtime.CompilerServices.RuntimeCompatibilityAttribute::.ctor() = ( 01 00 01 00 54 02 16 57 72 61 70 4E 6F 6E 45 78   // ....T..WrapNonEx
                                                                                                             63 65 70 74 69 6F 6E 54 68 72 6F 77 73 01 )       // ceptionThrows.
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module Hello.exe
// MVID: {7C2770DB-1594-438D-BAE5-98764C39CCCA}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x00600000
```

Aşağıdaki tabloda, örnekte kullanılan *Hello.exe* derlemesinin derleme bildirimindeki her yönerge açıklanmaktadır:

|Deki|Açıklama|
|---------------|-----------------|
|**. Assembly extern \<assembly name>**|Geçerli modülün başvurduğu öğeleri içeren başka bir derlemeyi belirtir (Bu örnekte, `mscorlib` ).|
|**. PublicKeyToken \<token>**|Başvurulan derlemenin gerçek anahtarının belirtecini belirtir.|
|**. ver \<version number>**|Başvurulan derlemenin sürüm numarasını belirtir.|
|**. Assembly \<assembly name>**|Derleme adını belirtir.|
|**. Hash algoritması \<int32 value>**|Kullanılan karma algoritmasını belirtir.|
|**. ver \<version number>**|Derlemenin sürüm numarasını belirtir.|
|**. Module \<file name>**|Derlemeyi oluşturan modüllerin adını belirtir. Bu örnekte, derleme yalnızca bir dosyadan oluşur.|
|**. Subsystem \<value>**|Program için gereken uygulama ortamını belirtir. Bu örnekte, 3 değeri bu yürütülebilir dosyanın bir konsolundan çalıştırıldığını gösterir.|
|**. CorFlags**|Şu anda meta verilerde ayrılmış bir alan.|

Bütünleştirilmiş kod bildirimi, derlemenin içeriğine bağlı olarak bir dizi farklı yönergeler içerebilir. Derleme bildirimindeki yönergelerin kapsamlı bir listesi için, bkz. ECMA belgeleri, özellikle "Bölüm II: meta veri tanımı ve semantiği" ve "Bölüm III: CıL yönerge kümesi":

- [ECMA C# ve ortak dil altyapısı standartları](../components.md#applicable-standards)
- [Standart ECMA-335-ortak dil altyapısı (CLı)](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/)

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Etki Alanları ve derlemeler](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [Uygulama etki alanları ve derlemeler ile ilgili nasıl yapılır konuları](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [Ildasm.exe (Il ayırıcı)](../../framework/tools/ildasm-exe-il-disassembler.md)
