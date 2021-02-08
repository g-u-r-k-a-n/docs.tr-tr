---
description: 'Hakkında daha fazla bilgi edinin: TextFieldParser nesnesiyle metin dosyaları ayrıştırma (Visual Basic)'
title: TextFieldParser nesnesiyle metin dosyalarını ayrıştırma
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, using
- I/O [Visual Basic], parsing files
- files [Visual Basic], parsing
ms.assetid: fc31d6e6-af0c-403f-8a00-d556b2c57567
ms.openlocfilehash: 7ba3e9f98e4fea882260e8f194d59fda8eda9f69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797386"
---
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a><span data-ttu-id="6f58e-103">TextFieldParser nesnesiyle metin dosyalarını ayrıştırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f58e-103">Parsing text files with the TextFieldParser object (Visual Basic)</span></span>

<span data-ttu-id="6f58e-104">`TextFieldParser`Nesnesi, günlük dosyaları veya eski veritabanı bilgileri gibi, metnin ayrılmış genişlik sütunları olarak yapılandırılmış çok büyük bir dosyayı ayrıştırmanıza ve işleetmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6f58e-104">The `TextFieldParser` object allows you to parse and process very large file that are structured as delimited-width columns of text, such as log files or legacy database information.</span></span> <span data-ttu-id="6f58e-105">Bir metin dosyasının `TextFieldParser` ayrıştırılmasında metin dosyası üzerinde yineleme yapmak benzer, ancak metin alanlarını ayıklamak için ayrıştırma yöntemi, sınırlandırılmış dizeleri simgeleştirmek için kullanılan dize işleme yöntemlerine benzerdir.</span><span class="sxs-lookup"><span data-stu-id="6f58e-105">Parsing a text file with `TextFieldParser` is similar to iterating over a text file, while the parse method to extract fields of text is similar to string manipulation methods used to tokenize delimited strings.</span></span>  
  
## <a name="parsing-different-types-of-text-files"></a><span data-ttu-id="6f58e-106">Farklı metin dosyası türlerini ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="6f58e-106">Parsing different types of text files</span></span>  

 <span data-ttu-id="6f58e-107">Metin dosyalarında, virgül veya sekme alanı gibi bir karakterle ayrılmış çeşitli genişlik alanları olabilir.</span><span class="sxs-lookup"><span data-stu-id="6f58e-107">Text files may have fields of various width, delimited by a character such as a comma or a tab space.</span></span> <span data-ttu-id="6f58e-108">`TextFieldType`Aşağıdaki örnekte olduğu gibi, `SetDelimiters` sekmeyle ayrılmış bir metin dosyası tanımlamak için yöntemini kullanan sınırlayıcısı tanımlayın:</span><span class="sxs-lookup"><span data-stu-id="6f58e-108">Define `TextFieldType` and the delimiter, as in the following example, which uses the `SetDelimiters` method to define a tab-delimited text file:</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#21)]  
  
 <span data-ttu-id="6f58e-109">Diğer metin dosyaları, sabit olan alan genişliklerine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="6f58e-109">Other text files may have field widths that are fixed.</span></span> <span data-ttu-id="6f58e-110">Bu gibi durumlarda, `TextFieldType` `FixedWidth` Aşağıdaki örnekte olduğu gibi, her bir alanın genişliğini tanımlamanız ve tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6f58e-110">In such cases, you need to define the `TextFieldType` as `FixedWidth` and define the widths of each field, as in the following example.</span></span> <span data-ttu-id="6f58e-111">Bu örnek, `SetFieldWidths` metin sütunlarını tanımlamak için yöntemini kullanır: ilk sütun 5 karakter genişliğinde, ikincisi 10, üçüncüsü 11 ve dördüncü değişken genişliktir.</span><span class="sxs-lookup"><span data-stu-id="6f58e-111">This example uses the `SetFieldWidths` method to define the columns of text: the first column is 5 characters wide, the second is 10, the third is 11, and the fourth is of variable width.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#22)]  
  
 <span data-ttu-id="6f58e-112">Biçim tanımlandıktan sonra, `ReadFields` her satırı sırayla işlemek için yöntemini kullanarak dosyasında döngü yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f58e-112">Once the format is defined, you can loop through the file, using the `ReadFields` method to process each line in turn.</span></span>  
  
 <span data-ttu-id="6f58e-113">Bir alan belirtilen biçimle eşleşmezse, bir <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6f58e-113">If a field does not match the specified format, a <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> exception is thrown.</span></span> <span data-ttu-id="6f58e-114">Bu tür özel durumlar oluştuğunda `ErrorLine` ve özellikleri, `ErrorLineNumber` özel duruma ve bu metnin satır numarasına neden olan metni tutar.</span><span class="sxs-lookup"><span data-stu-id="6f58e-114">When such exceptions are thrown, the `ErrorLine` and `ErrorLineNumber` properties hold the text causing the exception and the line number of that text.</span></span>  
  
## <a name="parsing-files-with-multiple-formats"></a><span data-ttu-id="6f58e-115">Birden çok biçimdeki dosyaları ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="6f58e-115">Parsing files with multiple formats</span></span>  

 <span data-ttu-id="6f58e-116">`PeekChars`Nesne yöntemi, `TextFieldParser` okumadan önce her bir alanı denetlemek için kullanılabilir ve alanlar için birden çok biçim tanımlamanızı ve buna uygun şekilde tepki vermesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f58e-116">The `PeekChars` method of the `TextFieldParser` object can be used to check each field before reading it, allowing you to define multiple formats for the fields and react accordingly.</span></span> <span data-ttu-id="6f58e-117">Daha fazla bilgi için bkz. [nasıl yapılır: birden çok biçimdeki metin dosyalarından okuma](how-to-read-from-text-files-with-multiple-formats.md).</span><span class="sxs-lookup"><span data-stu-id="6f58e-117">For more information, see [How to: Read From Text Files with Multiple Formats](how-to-read-from-text-files-with-multiple-formats.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f58e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f58e-118">See also</span></span>

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
