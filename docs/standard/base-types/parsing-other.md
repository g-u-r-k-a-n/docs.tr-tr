---
title: .NET 'teki diğer dizeleri ayrıştırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Char data type, parsing strings
- enumerations [.NET], parsing strings
- base types, parsing strings
- parsing strings, other strings
- Boolean data type, parsing strings
ms.assetid: d139bc00-3c4e-4d78-ac9a-5c951b258d28
ms.openlocfilehash: 352bd426c889996daa5f420ccc384947896dc118
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683751"
---
# <a name="parsing-other-strings-in-net"></a><span data-ttu-id="1e220-102">.NET 'teki diğer dizeleri ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="1e220-102">Parsing Other Strings in .NET</span></span>

<span data-ttu-id="1e220-103">Sayısal ve dizelere ek olarak,, <xref:System.DateTime> ve türlerini temsil eden dizeleri de ayrıştırabilirsiniz <xref:System.Char> <xref:System.Boolean> <xref:System.Enum> .</span><span class="sxs-lookup"><span data-stu-id="1e220-103">In addition to numeric and <xref:System.DateTime> strings, you can also parse strings that represent the types <xref:System.Char>, <xref:System.Boolean>, and <xref:System.Enum> into data types.</span></span>  
  
## <a name="char"></a><span data-ttu-id="1e220-104">Char</span><span class="sxs-lookup"><span data-stu-id="1e220-104">Char</span></span>  

 <span data-ttu-id="1e220-105">**Char** veri türüyle ilişkili statik Parse yöntemi, tek bir karakter içeren bir dizeyi Unicode değerine dönüştürmek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="1e220-105">The static parse method associated with the **Char** data type is useful for converting a string that contains a single character into its Unicode value.</span></span> <span data-ttu-id="1e220-106">Aşağıdaki kod örneği bir dizeyi Unicode karakter olarak ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="1e220-106">The following code example parses a string into a Unicode character.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a><span data-ttu-id="1e220-107">Boole</span><span class="sxs-lookup"><span data-stu-id="1e220-107">Boolean</span></span>  

 <span data-ttu-id="1e220-108">**Boolean** veri türü, bir Boolean değeri temsil eden bir dizeyi gerçek bir **Boolean** türüne dönüştürmek için kullanabileceğiniz bir **Parse** yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="1e220-108">The **Boolean** data type contains a **Parse** method that you can use to convert a string that represents a Boolean value into an actual **Boolean** type.</span></span> <span data-ttu-id="1e220-109">Bu yöntem, büyük/küçük harfe duyarlı değildir ve "true" veya "false" içeren bir dizeyi başarıyla ayrıştırabilirler.</span><span class="sxs-lookup"><span data-stu-id="1e220-109">This method is not case-sensitive and can successfully parse a string containing "True" or "False."</span></span> <span data-ttu-id="1e220-110">**Boolean** türüyle ilişkili **Parse** yöntemi, boşluk ile çevrelenen dizeleri de ayrıştırabilirler.</span><span class="sxs-lookup"><span data-stu-id="1e220-110">The **Parse** method associated with the **Boolean** type can also parse strings that are surrounded by white spaces.</span></span> <span data-ttu-id="1e220-111">Başka bir dize geçirilirse, bir <xref:System.FormatException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1e220-111">If any other string is passed, a <xref:System.FormatException> is thrown.</span></span>  
  
 <span data-ttu-id="1e220-112">Aşağıdaki kod örneği bir dizeyi Boole değerine dönüştürmek için **Parse** metodunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="1e220-112">The following code example uses the **Parse** method to convert a string into a Boolean value.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a><span data-ttu-id="1e220-113">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="1e220-113">Enumeration</span></span>  

 <span data-ttu-id="1e220-114">Statik **Parse** yöntemini bir dize değerine bir sabit listesi türü başlatmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e220-114">You can use the static **Parse** method to initialize an enumeration type to the value of a string.</span></span> <span data-ttu-id="1e220-115">Bu yöntem, ayrıştırma yaptığınız numaralandırma türünü, ayrıştırılacak dizeyi ve ayrıştırmanın büyük/küçük harfe duyarlı olup olmadığını belirten isteğe bağlı bir Boolean bayrağını kabul eder.</span><span class="sxs-lookup"><span data-stu-id="1e220-115">This method accepts the enumeration type you are parsing, the string to parse, and an optional Boolean flag indicating whether or not the parse is case-sensitive.</span></span> <span data-ttu-id="1e220-116">Ayrıştırıldıkları dize, bir veya daha fazla boş boşluk (boşluk da denir) tarafından öncesinde veya sonra gelen virgüllerle ayrılmış birkaç değer içerebilir.</span><span class="sxs-lookup"><span data-stu-id="1e220-116">The string you are parsing can contain several values separated by commas, which can be preceded or followed by one or more empty spaces (also called white spaces).</span></span> <span data-ttu-id="1e220-117">Dize birden çok değer içerdiğinde, döndürülen nesnenin değeri, bir bit düzeyinde veya işlemle birlikte belirtilen tüm değerlerin değeridir.</span><span class="sxs-lookup"><span data-stu-id="1e220-117">When the string contains multiple values, the value of the returned object is the value of all specified values combined with a bitwise OR operation.</span></span>  
  
 <span data-ttu-id="1e220-118">Aşağıdaki örnek, bir dize gösterimini bir numaralandırma değerine dönüştürmek için **Parse** metodunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="1e220-118">The following example uses the **Parse** method to convert a string representation into an enumeration value.</span></span> <span data-ttu-id="1e220-119"><xref:System.DayOfWeek>Sabit listesi bir dizeden **Perşembe** olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="1e220-119">The <xref:System.DayOfWeek> enumeration is initialized to **Thursday** from a string.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="1e220-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e220-120">See also</span></span>

- [<span data-ttu-id="1e220-121">Dizeleri Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="1e220-121">Parsing Strings</span></span>](parsing-strings.md)
- [<span data-ttu-id="1e220-122">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="1e220-122">Formatting Types</span></span>](formatting-types.md)
- [<span data-ttu-id="1e220-123">.NET 'te tür dönüştürme</span><span class="sxs-lookup"><span data-stu-id="1e220-123">Type Conversion in the .NET</span></span>](type-conversion.md)
