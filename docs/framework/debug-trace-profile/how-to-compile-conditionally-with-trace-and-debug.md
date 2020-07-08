---
title: 'Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme'
description: Bir .NET uygulamasını derlerken, Izleme ve hata ayıklama koşullu özniteliklerini koşullu olarak derlemeyi öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- trace compiler options
- trace statements
- compiling source code, trace statements
- tracing [.NET Framework], enabling or disabling
- tracing [.NET Framework], compiling conditionally
- TRACE directive
- conditional compilation, tracing code
ms.assetid: 56d051c3-012c-42c1-9a58-7270edc624aa
ms.openlocfilehash: 8758b793866ec0317f91d636476d33bd001ddd78
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051226"
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a>Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme
Geliştirme sırasında bir uygulamada hata ayıklarken, hem izleme hem de hata ayıklama çıkışı Visual Studio 'daki çıkış penceresine gider. Ancak, dağıtılmış bir uygulamada izleme özelliklerini dahil etmek için, izlenen uygulamalarınızı **Trace** derleyici yönergesi etkinken derlemeniz gerekir. Bu, izleme kodunun uygulamanızın yayın sürümüne derlenmesini sağlar. **İzleme** yönergesini etkinleştirmezseniz, derleme sırasında tüm izleme kodu yok sayılır ve dağıtacağınız yürütülebilir koda dahil edilmez.  
  
 Hem izleme hem de hata ayıklama yöntemlerinin ilişkili koşullu öznitelikleri vardır. Örneğin, izlemenin koşullu özniteliği **true**ise, tüm Trace deyimleri bir derlemeye (derlenmiş bir. exe dosyası veya. dll) dahil edilir; **Trace** Conditional özniteliği **false**ise, Trace deyimleri dahil edilmez.  
  
 Bir derleme veya her ikisi için de **Trace** veya **Debug** koşullu özniteliği açık olabilir ya da hiçbiri. Bu nedenle, dört tür derleme vardır: **hata ayıklama**, **izleme**, her ikisi de veya hiçbiri. Üretim dağıtımı için bazı yayın yapıları ne içermez; Çoğu hata ayıklama derlemesi her ikisini de içerir.  
  
 Uygulamanız için derleyici ayarlarını birkaç şekilde belirtebilirsiniz:  
  
- Özellik sayfaları  
  
- Komut satırı  
  
- **#CONST** (Visual Basic için) ve **#define** (C# için)  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a>Özellik sayfaları iletişim kutusundan derleme ayarlarını değiştirmek için  
  
1. **Çözüm Gezgini**' de proje düğümüne sağ tıklayın.  
  
2. Kısayol menüsünden **Özellikler** ' i seçin.  
  
    - Visual Basic, özellik sayfasının sol bölmesindeki **Derle** sekmesine tıklayın, ardından Gelişmiş **derleyici ayarları** Iletişim kutusunu göstermek için **Gelişmiş derleme seçenekleri** düğmesine tıklayın. Etkinleştirmek istediğiniz derleyici ayarlarının onay kutularını seçin. Devre dışı bırakmak istediğiniz ayarların onay kutularını temizleyin.  
  
    - C# ' de, özellik sayfasının sol bölmesindeki **derleme** sekmesine tıklayın ve ardından etkinleştirmek istediğiniz derleyici ayarlarının onay kutularını seçin. Devre dışı bırakmak istediğiniz ayarların onay kutularını temizleyin.  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a>Komut satırını kullanarak belgelenmiş kodu derlemek için  
  
1. Komut satırında koşullu bir derleyici anahtarı ayarlayın. Derleyici, yürütülebilir dosyaya izleme veya hata ayıklama kodu içerecektir.  
  
     Örneğin, komut satırına girilen aşağıdaki derleyici yönergesi, derleme kodunuzu derlenmiş bir yürütülebilir dosyaya dahil eder:  
  
     Visual Basic için: **vbc -r:System.dll-d:TRACE = true-d:DEBUG = false MyApplication. vb**  
  
     C# için: **csc -r:System.dll-d:TRACE-d:DEBUG = FALSE MyApplication.cs**  
  
    > [!TIP]
    > Birden fazla uygulama dosyası derlemek için dosya adları arasında boş bir boşluk bırakın; Örneğin, **MyApplication1. vb MyApplication2. vb MyApplication3. vb** veya **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.  
  
     Yukarıdaki örneklerde kullanılan koşullu derleme yönergelerinin anlamı aşağıdaki gibidir:  
  
    |Deki|Anlamı|  
    |---------------|-------------|  
    |`vbc`|Visual Basic derleyici|  
    |`csc`|C# derleyicisi|  
    |`-r:`|Bir dış derlemeye (EXE veya DLL) başvurur|  
    |`-d:`|Koşullu derleme sembolünü tanımlar|  
  
    > [!NOTE]
    > Büyük harflerle TRACE veya DEBUG yazmanız gerekir. Koşullu derleme komutları hakkında daha fazla bilgi için, `vbc /?` komut istemine (Visual Basic için) veya `csc /?` (C# için) girin. Daha fazla bilgi için, bkz. [komut satırından oluşturma](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) veya [komut satırı derleyicisini çağırma](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a>#CONST veya #define kullanarak koşullu derleme gerçekleştirmek için  
  
1. Kaynak kodu dosyasının en üstünde programlama diliniz için uygun olan ifadeyi yazın.  
  
    |Dil|Deyim|Sonuç|  
    |--------------|---------------|------------|  
    |**Visual Basic**|**#CONST TRACE = true**|İzlemeyi etkinleştirilir|  
    ||**#CONST TRACE = false**|İzlemeyi devre dışı bırakır|  
    ||**#CONST DEBUG = true**|Hata ayıklamayı sağlar|  
    ||**#CONST DEBUG = false**|Hata ayıklamayı devre dışı bırakır|  
    |**C#**|**#define Izleme**|İzlemeyi etkinleştirilir|  
    ||**#undef Izleme**|İzlemeyi devre dışı bırakır|  
    ||**hata ayıklama #define**|Hata ayıklamayı sağlar|  
    ||**hata ayıklama #undef**|Hata ayıklamayı devre dışı bırakır|  
  
### <a name="to-disable-tracing-or-debugging"></a>İzlemeyi veya hata ayıklamayı devre dışı bırakmak için  
  
Derleyici yönergesini kaynak kodınızdan silin.  
  
\-veya  
  
Derleyici yönergesini açıklama.  
  
> [!NOTE]
> **Derlemeye hazırsanız derleme menüsünden** **Oluştur** ' u seçebilir veya koşullu derleme sembolleri tanımlamak için **d:** yazmadan komut satırı yöntemini kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme ve İşaretleme Uygulamaları](tracing-and-instrumenting-applications.md)
- [Nasıl yapılır: İzleme Anahtarları Oluşturma ve Başlatma](how-to-create-initialize-and-configure-trace-switches.md)
- [İzleme Anahtarları](trace-switches.md)
- [İz Dinleyicileri](trace-listeners.md)
- [Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme](how-to-add-trace-statements-to-application-code.md)
- [Visual Studio Komut Satırı için ortam değişkenlerini ayarlama](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [Nasıl yapılır: Komut Satırı Derleyicisini Çağırma](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
