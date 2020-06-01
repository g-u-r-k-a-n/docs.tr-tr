---
title: Her seferinde bir metin dosyasını okuma-C# programlama kılavuzunda bir satır
ms.date: 07/20/2015
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
ms.openlocfilehash: b54d072ce9837f9b15694f2d7100817de62e9762
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241779"
---
# <a name="how-to-read-a-text-file-one-line-at-a-time-c-programming-guide"></a><span data-ttu-id="c2c57-102">Bir metin dosyasını tek seferde bir satır okuma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c2c57-102">How to read a text file one line at a time (C# Programming Guide)</span></span>
<span data-ttu-id="c2c57-103">Bu örnek, bir metin dosyasının içeriğini, tek seferde bir satırı, sınıfının yöntemini kullanarak bir dizeye okur `ReadLine` `StreamReader` .</span><span class="sxs-lookup"><span data-stu-id="c2c57-103">This example reads the contents of a text file, one line at a time, into a string using the `ReadLine` method of the `StreamReader` class.</span></span> <span data-ttu-id="c2c57-104">Her metin satırı, dizede depolanır `line` ve ekranda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c2c57-104">Each text line is stored into the string `line` and displayed on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2c57-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="c2c57-105">Example</span></span>  
  
```csharp
int counter = 0;  
string line;  
  
// Read the file and display it line by line.  
System.IO.StreamReader file =
    new System.IO.StreamReader(@"c:\test.txt");  
while((line = file.ReadLine()) != null)  
{  
    System.Console.WriteLine(line);  
    counter++;  
}  
  
file.Close();  
System.Console.WriteLine("There were {0} lines.", counter);  
// Suspend the screen.  
System.Console.ReadLine();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c2c57-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="c2c57-106">Compiling the Code</span></span>  
 <span data-ttu-id="c2c57-107">Kodu kopyalayın ve `Main` konsol uygulamasının yöntemine yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="c2c57-107">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
 <span data-ttu-id="c2c57-108">`"c:\test.txt"`Gerçek dosya adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c2c57-108">Replace `"c:\test.txt"` with the actual file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c2c57-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="c2c57-109">Robust Programming</span></span>  
 <span data-ttu-id="c2c57-110">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="c2c57-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="c2c57-111">Dosya mevcut olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="c2c57-111">The file may not exist.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="c2c57-112">.NET güvenliği</span><span class="sxs-lookup"><span data-stu-id="c2c57-112">.NET Security</span></span>  
 <span data-ttu-id="c2c57-113">Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin.</span><span class="sxs-lookup"><span data-stu-id="c2c57-113">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="c2c57-114">Örneğin, dosya `myFile.cs` bir C# kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="c2c57-114">For example, the file `myFile.cs` may not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2c57-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2c57-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="c2c57-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c2c57-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c2c57-117">Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c2c57-117">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
