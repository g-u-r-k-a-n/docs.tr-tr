---
title: 'Nasıl yazılır: Karakterleri bir dize yazma'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET Framework], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
ms.openlocfilehash: ecbfa2de2c21ff79df269f74eeddfa0738e7e25c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160293"
---
# <a name="how-to-write-characters-to-a-string"></a><span data-ttu-id="0ff6a-102">Nasıl yazılır: Karakterleri bir dize yazma</span><span class="sxs-lookup"><span data-stu-id="0ff6a-102">How to: Write characters to a string</span></span>
<span data-ttu-id="0ff6a-103">Aşağıdaki kod örnekleri, karakterleri eşzamanlı olarak veya bir karakter dizisinden bir dize eşit olarak yazar.</span><span class="sxs-lookup"><span data-stu-id="0ff6a-103">The following code examples write characters synchronously or asynchronously from a character array into a string.</span></span>  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a><span data-ttu-id="0ff6a-104">Örnek: Konsol uygulamasına eşzamanlı karakter yazma</span><span class="sxs-lookup"><span data-stu-id="0ff6a-104">Example: Write characters synchronously in a console app</span></span>  
 <span data-ttu-id="0ff6a-105">Aşağıdaki örnek, <xref:System.IO.StringWriter> bir <xref:System.Text.StringBuilder> nesneye eşzamanlı olarak beş karakter yazmak için a kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ff6a-105">The following example uses a <xref:System.IO.StringWriter> to write five characters synchronously to a <xref:System.Text.StringBuilder> object.</span></span>
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a><span data-ttu-id="0ff6a-106">Örnek: Karakterleri bir WPF uygulamasına eşzamanlı olarak yazma</span><span class="sxs-lookup"><span data-stu-id="0ff6a-106">Example: Write characters asynchronously in a WPF app</span></span>
 <span data-ttu-id="0ff6a-107">Sonraki örnek, bir WPF uygulamasının arkasındaki koddur.</span><span class="sxs-lookup"><span data-stu-id="0ff6a-107">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="0ff6a-108">Pencere yükünde, örnek tüm karakterleri denetimden <xref:System.Windows.Controls.TextBox> eşit bir şekilde okur ve bir dizide saklar.</span><span class="sxs-lookup"><span data-stu-id="0ff6a-108">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="0ff6a-109">Daha sonra eşzamanlı bir denetim ayrı bir satıra <xref:System.Windows.Controls.TextBlock> her harf veya beyaz boşluk karakter yazar.</span><span class="sxs-lookup"><span data-stu-id="0ff6a-109">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0ff6a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ff6a-110">See also</span></span>

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [<span data-ttu-id="0ff6a-111">Dosya ve akış G/Ç</span><span class="sxs-lookup"><span data-stu-id="0ff6a-111">File and stream I/O</span></span>](../../../docs/standard/io/index.md)  
- [<span data-ttu-id="0ff6a-112">Asynchronous dosya I/O</span><span class="sxs-lookup"><span data-stu-id="0ff6a-112">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [<span data-ttu-id="0ff6a-113">Nasıl yapılır: Dizinleri ve dosyaları sayısal</span><span class="sxs-lookup"><span data-stu-id="0ff6a-113">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="0ff6a-114">Nasıl kullanılır: Yeni oluşturulan bir veri dosyasını okuma ve yazma</span><span class="sxs-lookup"><span data-stu-id="0ff6a-114">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="0ff6a-115">Nasıl yapılı: Günlük dosyasını açma ve ekle</span><span class="sxs-lookup"><span data-stu-id="0ff6a-115">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="0ff6a-116">Nasıl yapilir: Dosyadaki metni okuma</span><span class="sxs-lookup"><span data-stu-id="0ff6a-116">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="0ff6a-117">Nasıl yazılır: Dosyaya metin yazma</span><span class="sxs-lookup"><span data-stu-id="0ff6a-117">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="0ff6a-118">Nasıl yapilir: Bir dizedeki karakterleri okuma</span><span class="sxs-lookup"><span data-stu-id="0ff6a-118">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
