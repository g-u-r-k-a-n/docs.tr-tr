---
title: 'Normal İfade Örneği: Tarih Biçimlerini Değiştirme'
ms.date: 06/30/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET regular expressions, examples
- regular expressions [.NET], examples
- pattern-matching with regular expressions, examples
ms.assetid: 5fcc75a5-09d7-45ae-a4c0-9ad6085ac83d
ms.openlocfilehash: 9e23a11bd6eac0a77ef04d95cfab8db5d5e26807
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733574"
---
# <a name="regular-expression-example-changing-date-formats"></a><span data-ttu-id="f4891-102">Normal İfade Örneği: Tarih Biçimlerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="f4891-102">Regular Expression Example: Changing Date Formats</span></span>

<span data-ttu-id="f4891-103">Aşağıdaki kod örneği, <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> *AA* / *gg* / *yy* biçimindeki tarihleri *gg* - *AA* - *yy* olan tarihlerle değiştirmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f4891-103">The following code example uses the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to replace dates that have the form *mm*/*dd*/*yy* with dates that have the form *dd*-*mm*-*yy*.</span></span>  

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a><span data-ttu-id="f4891-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f4891-104">Example</span></span>  

 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 <span data-ttu-id="f4891-105">Aşağıdaki kod, `MDYToDMY` yönteminin bir uygulamada nasıl çağrılabilecek olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4891-105">The following code shows how the `MDYToDMY` method can be called in an application.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a><span data-ttu-id="f4891-106">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="f4891-106">Comments</span></span>  

 <span data-ttu-id="f4891-107">Normal ifade deseninin  `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` Aşağıdaki tabloda gösterildiği gibi yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="f4891-107">The regular expression pattern  `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="f4891-108">Desen</span><span class="sxs-lookup"><span data-stu-id="f4891-108">Pattern</span></span>|<span data-ttu-id="f4891-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4891-109">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="f4891-110">Bir sözcük sınırında eşleşmeye başla.</span><span class="sxs-lookup"><span data-stu-id="f4891-110">Begin the match at a word boundary.</span></span>|  
|`(?<month>\d{1,2})`|<span data-ttu-id="f4891-111">Bir veya iki ondalık basamağı eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="f4891-111">Match one or two decimal digits.</span></span> <span data-ttu-id="f4891-112">Bu, `month` yakalanan gruptur.</span><span class="sxs-lookup"><span data-stu-id="f4891-112">This is the `month` captured group.</span></span>|  
|`/`|<span data-ttu-id="f4891-113">Eğik çizgi işaretiyle eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="f4891-113">Match the slash mark.</span></span>|  
|`(?<day>\d{1,2})`|<span data-ttu-id="f4891-114">Bir veya iki ondalık basamağı eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="f4891-114">Match one or two decimal digits.</span></span> <span data-ttu-id="f4891-115">Bu, `day` yakalanan gruptur.</span><span class="sxs-lookup"><span data-stu-id="f4891-115">This is the `day` captured group.</span></span>|  
|`/`|<span data-ttu-id="f4891-116">Eğik çizgi işaretiyle eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="f4891-116">Match the slash mark.</span></span>|  
|`(?<year>\d{2,4})`|<span data-ttu-id="f4891-117">İki ile dört ondalık basamağa eşleştirin.</span><span class="sxs-lookup"><span data-stu-id="f4891-117">Match from two to four decimal digits.</span></span> <span data-ttu-id="f4891-118">Bu, `year` yakalanan gruptur.</span><span class="sxs-lookup"><span data-stu-id="f4891-118">This is the `year` captured group.</span></span>|  
|`\b`|<span data-ttu-id="f4891-119">Eşlemeyi bir sözcük sınırında sonlandır.</span><span class="sxs-lookup"><span data-stu-id="f4891-119">End the match at a word boundary.</span></span>|  
  
 <span data-ttu-id="f4891-120">Bu model, `${day}-${month}-${year}` Aşağıdaki tabloda gösterildiği gibi değiştirme dizesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f4891-120">The pattern `${day}-${month}-${year}` defines the replacement string as shown in the following table.</span></span>  
  
|<span data-ttu-id="f4891-121">Desen</span><span class="sxs-lookup"><span data-stu-id="f4891-121">Pattern</span></span>|<span data-ttu-id="f4891-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4891-122">Description</span></span>|  
|-------------|-----------------|  
|`$(day)`|<span data-ttu-id="f4891-123">Yakalama grubu tarafından yakalanan dizeyi ekleyin `day` .</span><span class="sxs-lookup"><span data-stu-id="f4891-123">Add the string captured by the `day` capturing group.</span></span>|  
|`-`|<span data-ttu-id="f4891-124">Kısa çizgi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f4891-124">Add a hyphen.</span></span>|  
|`$(month)`|<span data-ttu-id="f4891-125">Yakalama grubu tarafından yakalanan dizeyi ekleyin `month` .</span><span class="sxs-lookup"><span data-stu-id="f4891-125">Add the string captured by the `month` capturing group.</span></span>|  
|`-`|<span data-ttu-id="f4891-126">Kısa çizgi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f4891-126">Add a hyphen.</span></span>|  
|`$(year)`|<span data-ttu-id="f4891-127">Yakalama grubu tarafından yakalanan dizeyi ekleyin `year` .</span><span class="sxs-lookup"><span data-stu-id="f4891-127">Add the string captured by the `year` capturing group.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f4891-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4891-128">See also</span></span>

- [<span data-ttu-id="f4891-129">.NET normal Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="f4891-129">.NET Regular Expressions</span></span>](regular-expressions.md)
