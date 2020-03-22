---
title: Metin dosyalarını TextFieldParser nesnesiyle ayrıştırma
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, using
- I/O [Visual Basic], parsing files
- files [Visual Basic], parsing
ms.assetid: fc31d6e6-af0c-403f-8a00-d556b2c57567
ms.openlocfilehash: f3239184beb58312a8e3598545fc37423ff85287
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74333853"
---
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a><span data-ttu-id="c7cd2-102">Metin dosyalarını TextFieldParser nesnesi ile ayrıştırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7cd2-102">Parsing text files with the TextFieldParser object (Visual Basic)</span></span>

<span data-ttu-id="c7cd2-103">Nesne, `TextFieldParser` günlük dosyaları veya eski veritabanı bilgileri gibi sınırlı genişlikte metin sütunları olarak yapılandırılan çok büyük dosyayı ayrıştırmanızı ve işlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7cd2-103">The `TextFieldParser` object allows you to parse and process very large file that are structured as delimited-width columns of text, such as log files or legacy database information.</span></span> <span data-ttu-id="c7cd2-104">Metin dosyasını ayrıştırmak `TextFieldParser` metin dosyası üzerinde yineleme yle benzerken, metin alanlarını ayıklamak için ayrıştırma yöntemi, sınırlandırılmış dizeleri belirtebilmek için kullanılan dize işleme yöntemlerine benzer.</span><span class="sxs-lookup"><span data-stu-id="c7cd2-104">Parsing a text file with `TextFieldParser` is similar to iterating over a text file, while the parse method to extract fields of text is similar to string manipulation methods used to tokenize delimited strings.</span></span>  
  
## <a name="parsing-different-types-of-text-files"></a><span data-ttu-id="c7cd2-105">Farklı metin dosyalarını ayrıştma</span><span class="sxs-lookup"><span data-stu-id="c7cd2-105">Parsing different types of text files</span></span>  

 <span data-ttu-id="c7cd2-106">Metin dosyaları, virgül veya sekme alanı gibi bir karakterle sınırlandırılmış çeşitli genişlikteki alanlara sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7cd2-106">Text files may have fields of various width, delimited by a character such as a comma or a tab space.</span></span> <span data-ttu-id="c7cd2-107">Aşağıdaki `TextFieldType` örnekte olduğu gibi, sekme sınırlandırılmış `SetDelimiters` bir metin dosyasını tanımlamak için yöntemi kullanan sınırlayıcıyı tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="c7cd2-107">Define `TextFieldType` and the delimiter, as in the following example, which uses the `SetDelimiters` method to define a tab-delimited text file:</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#21)]  
  
 <span data-ttu-id="c7cd2-108">Diğer metin dosyaları sabit alan genişlikleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7cd2-108">Other text files may have field widths that are fixed.</span></span> <span data-ttu-id="c7cd2-109">Bu gibi durumlarda, aşağıdaki `TextFieldType` örnekte olduğu gibi, her alanın genişlikleri olarak `FixedWidth` tanımlamak ve tanımlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7cd2-109">In such cases, you need to define the `TextFieldType` as `FixedWidth` and define the widths of each field, as in the following example.</span></span> <span data-ttu-id="c7cd2-110">Bu örnek, `SetFieldWidths` metin sütunlarını tanımlamak için yöntemi kullanır: ilk sütun 5 karakter genişliğinde, ikinci 10, üçüncü 11 ve dördüncü değişken genişliği.</span><span class="sxs-lookup"><span data-stu-id="c7cd2-110">This example uses the `SetFieldWidths` method to define the columns of text: the first column is 5 characters wide, the second is 10, the third is 11, and the fourth is of variable width.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#22)]  
  
 <span data-ttu-id="c7cd2-111">Biçim tanımlandıktan sonra, her satırı sırayla `ReadFields` işlemek için yöntemi kullanarak dosya yı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7cd2-111">Once the format is defined, you can loop through the file, using the `ReadFields` method to process each line in turn.</span></span>  
  
 <span data-ttu-id="c7cd2-112">Bir alan belirtilen biçimle eşleşmiyorsa, bir <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="c7cd2-112">If a field does not match the specified format, a <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> exception is thrown.</span></span> <span data-ttu-id="c7cd2-113">Bu tür özel durumlar `ErrorLine` atıldığında, özel durum ve bu metnin satır numarasıneden metin ve `ErrorLineNumber` özellikleri tutun.</span><span class="sxs-lookup"><span data-stu-id="c7cd2-113">When such exceptions are thrown, the `ErrorLine` and `ErrorLineNumber` properties hold the text causing the exception and the line number of that text.</span></span>  
  
## <a name="parsing-files-with-multiple-formats"></a><span data-ttu-id="c7cd2-114">Dosyaları birden çok biçimle ayrışdırma</span><span class="sxs-lookup"><span data-stu-id="c7cd2-114">Parsing files with multiple formats</span></span>  

 <span data-ttu-id="c7cd2-115">`TextFieldParser` Nesnenin `PeekChars` yöntemi, okumadan önce her alanı denetlemek için kullanılabilir, böylece alanlar için birden çok biçim tanımlamak ve buna göre tepki vermek.</span><span class="sxs-lookup"><span data-stu-id="c7cd2-115">The `PeekChars` method of the `TextFieldParser` object can be used to check each field before reading it, allowing you to define multiple formats for the fields and react accordingly.</span></span> <span data-ttu-id="c7cd2-116">Daha fazla bilgi [için bkz: Birden Çok Biçimli Metin Dosyalarından Okuma](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).</span><span class="sxs-lookup"><span data-stu-id="c7cd2-116">For more information, see [How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7cd2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7cd2-117">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFieldParser%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ReadFields%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLineNumber%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.FieldWidths%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.HasFieldsEnclosedInQuotes%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.LineNumber%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TrimWhiteSpace%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetFieldWidths%2A>
