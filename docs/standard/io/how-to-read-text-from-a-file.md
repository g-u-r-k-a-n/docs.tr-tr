---
title: 'Nasıl yapılır: dosyadan metin okuma'
description: Bu makalede, masaüstü uygulamaları için .NET 'teki StreamReader sınıfını kullanarak metin dosyasındaki metni zaman uyumlu veya zaman uyumsuz olarak okuma örneklerine bakın.
ms.date: 01/03/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, reading text from files
- reading text files
- reading data, text files
- data streams, reading text from files
- I/O [.NET], reading text from files
ms.assetid: ed180baa-dfc6-4c69-a725-46e87edafb27
ms.openlocfilehash: 7c772ec1de41d0ba2b4ef0d924a252326ee6909e
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823374"
---
# <a name="how-to-read-text-from-a-file"></a>Nasıl yapılır: dosyadan metin okuma

Aşağıdaki örnek, masaüstü uygulamaları için .NET kullanılarak bir metin dosyasındaki metnin nasıl zaman uyumlu ve zaman uyumsuz olarak okunacağını gösterir. Her iki örnekte, sınıfının örneğini oluşturduğunuzda <xref:System.IO.StreamReader> , dosyanın göreli veya mutlak yolunu sağlarsınız.
  
> [!NOTE]
> Bu kod örnekleri, Evrensel Windows (UWP) uygulamalarına uygulanmaz çünkü Windows Çalışma Zamanı dosyalara okuma ve yazma için farklı akış türleri sağlar. UWP uygulamasında bir dosyadaki metnin nasıl okunacağını gösteren bir örnek için bkz. [hızlı başlangıç: dosya okuma ve yazma](/previous-versions/windows/apps/hh758325(v=win.10)). .NET Framework akışlar ve Windows Çalışma Zamanı akışları arasında nasıl dönüştürme yapılacağını gösteren örnekler için bkz. [nasıl yapılır: .NET Framework akışlar ve Windows çalışma zamanı akışları arasında dönüştürme](how-to-convert-between-dotnet-streams-and-winrt-streams.md).  
  
## <a name="example-synchronous-read-in-a-console-app"></a>Örnek: konsol uygulamasında zaman uyumlu okuma  
Aşağıdaki örnek, bir konsol uygulaması içinde zaman uyumlu okuma işlemini gösterir. Bu örnek, bir akış okuyucusu kullanarak metin dosyasını açar, içeriği bir dizeye kopyalar ve dizeyi konsola verir.  
  
> [!IMPORTANT]
> Örnek, *TestFile.txt* adlı bir dosyanın uygulamayla aynı klasörde zaten bulunduğunu varsayar.  

:::code language="csharp" source="snippets/how-to-read-text-from-a-file/csharp/sync-console/Program.cs":::
:::code language="vb" source="snippets/how-to-read-text-from-a-file/vb/sync-console/Program.vb":::
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a>Örnek: WPF uygulamasında zaman uyumsuz okuma
 Aşağıdaki örnek, bir Windows Presentation Foundation (WPF) uygulamasında zaman uyumsuz okuma işlemini gösterir.  
  
> [!IMPORTANT]
> Örnek, *TestFile.txt* adlı bir dosyanın uygulamayla aynı klasörde zaten bulunduğunu varsayar.  

:::code language="csharp" source="snippets/how-to-read-text-from-a-file/csharp/async-wpf/MainWindow.xaml.cs":::
:::code language="vb" source="snippets/how-to-read-text-from-a-file/vb/async-wpf/MainWindow.xaml.vb":::
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [Zaman uyumsuz dosya G/Ç](asynchronous-file-i-o.md)  
- [Nasıl yapılır: Dizin listesi oluşturma](/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))  
- [Hızlı başlangıç: dosyaları okuma ve yazma](/previous-versions/windows/apps/hh758325(v=win.10))  
- [Nasıl yapılır: .NET Framework akışlar ve Windows Çalışma Zamanı akışları arasında dönüştürme](how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [Nasıl yapılır: yeni oluşturulan bir veri dosyasını okuma ve yazma](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Nasıl yapılır: günlük dosyasını açma ve ekleme](how-to-open-and-append-to-a-log-file.md)  
- [Nasıl yapılır: bir dosyaya metin yazma](how-to-write-text-to-a-file.md)  
- [Nasıl yapılır: dizeden karakterleri okuma](how-to-read-characters-from-a-string.md)  
- [Nasıl yapılır: bir dizeye karakter yazma](how-to-write-characters-to-a-string.md)  
- [Dosya ve akış G/Ç](index.md)
