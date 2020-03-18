---
title: .NET'te Dizeleri Kırpma ve Çıkarma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strings [.NET Framework], removing characters
- Remove method
- TrimEnd method
- Trim method
- trimming characters
- TrimStart method
- removing characters
ms.assetid: ab248dab-70d4-4413-81c6-542d153fd195
ms.openlocfilehash: bdbe267bb178e90c0008422e6543a23178c2c4d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159994"
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a><span data-ttu-id="bd6cd-102">.NET'te Dizeleri Kırpma ve Çıkarma</span><span class="sxs-lookup"><span data-stu-id="bd6cd-102">Trimming and Removing Characters from Strings in .NET</span></span>
<span data-ttu-id="bd6cd-103">Bir cümleyi tek tek sözcüklere ayrıştırıyorsanız, sözcüğün her iki ucunda boş alanlar (beyaz boşluklar olarak da adlandırılır) sözcüklerle sona erebilir.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-103">If you are parsing a sentence into individual words, you might end up with words that have blank spaces (also called white spaces) on either end of the word.</span></span> <span data-ttu-id="bd6cd-104">Bu durumda, string'deki belirli bir konumdan herhangi bir sayıda boşluk veya diğer karakteri kaldırmak için **System.String** sınıfındaki kırpma yöntemlerinden birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-104">In this situation, you can use one of the trim methods in the **System.String** class to remove any number of spaces or other characters from a specified position in the string.</span></span> <span data-ttu-id="bd6cd-105">Aşağıdaki tabloda kullanılabilir kırpma yöntemleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-105">The following table describes the available trim methods.</span></span>  
  
|<span data-ttu-id="bd6cd-106">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="bd6cd-106">Method name</span></span>|<span data-ttu-id="bd6cd-107">Kullanım</span><span class="sxs-lookup"><span data-stu-id="bd6cd-107">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|<span data-ttu-id="bd6cd-108">Dize başından ve sonundan bir karakter dizisinde belirtilen beyaz boşlukları veya karakterleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-108">Removes white spaces or characters specified in an array of characters from the beginning and end of a string.</span></span>|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|<span data-ttu-id="bd6cd-109">Dize sonundan bir karakter dizisinde belirtilen karakterleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-109">Removes characters specified in an array of characters from the end of a string.</span></span>|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|<span data-ttu-id="bd6cd-110">Dize başlangıcından bir karakter dizisinde belirtilen karakterleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-110">Removes characters specified in an array of characters from the beginning of a string.</span></span>|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="bd6cd-111">Bir dizedeki belirli bir dizin konumundan belirli sayıda karakter kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-111">Removes a specified number of characters from a specified index position in a string.</span></span>|  
  
## <a name="trim"></a><span data-ttu-id="bd6cd-112">Trim</span><span class="sxs-lookup"><span data-stu-id="bd6cd-112">Trim</span></span>

 <span data-ttu-id="bd6cd-113">Aşağıdaki örnekte gösterildiği gibi <xref:System.String.Trim%2A?displayProperty=nameWithType> yöntemi kullanarak dizenin her iki ucundan beyaz boşlukları kolayca kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-113">You can easily remove white spaces from both ends of a string by using the <xref:System.String.Trim%2A?displayProperty=nameWithType> method, as shown in the following example.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 <span data-ttu-id="bd6cd-114">Ayrıca, bir karakter dizisinde belirttiğiniz karakterleri bir dizebaşından ve sonundan da kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-114">You can also remove characters that you specify in a character array from the beginning and end of a string.</span></span> <span data-ttu-id="bd6cd-115">Aşağıdaki örnek, boşluk karakterlerini, dönemleri ve yıldız yıldızlarını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-115">The following example removes white-space characters, periods, and asterisks.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a><span data-ttu-id="bd6cd-116">TrimEnd</span><span class="sxs-lookup"><span data-stu-id="bd6cd-116">TrimEnd</span></span>

 <span data-ttu-id="bd6cd-117">**String.TrimEnd** yöntemi karakterleri bir dize sonundan kaldırarak yeni bir dize nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-117">The **String.TrimEnd** method removes characters from the end of a string, creating a new string object.</span></span> <span data-ttu-id="bd6cd-118">Kaldırılacak karakterleri belirtmek için bu yönteme bir dizi karakter aktarılır.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-118">An array of characters is passed to this method to specify the characters to be removed.</span></span> <span data-ttu-id="bd6cd-119">Karakter dizisindeki öğelerin sırası kırpma işlemini etkilemez.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-119">The order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="bd6cd-120">Dizide belirtilmeyen bir karakter bulunduğunda kırpma durur.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-120">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="bd6cd-121">Aşağıdaki örnek, **TrimEnd** yöntemini kullanarak bir dize son harflerini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-121">The following example removes the last letters of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="bd6cd-122">Bu örnekte, `'r'` dizideki karakterlerin `'W'` sırasının önemli olmadığını göstermek için karakterin ve karakterin konumu tersine çevrilir.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-122">In this example, the position of the `'r'` character and the `'W'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span> <span data-ttu-id="bd6cd-123">Bu kodun ilkinin son `MyString` sözcüğünün artı bir kısmını kaldırdığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-123">Notice that this code removes the last word of `MyString` plus part of the first.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 <span data-ttu-id="bd6cd-124">Bu kod `He` konsola görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-124">This code displays `He` to the console.</span></span>  
  
 <span data-ttu-id="bd6cd-125">Aşağıdaki örnek, **TrimEnd** yöntemini kullanarak bir dize son sözcük kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-125">The following example removes the last word of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="bd6cd-126">Bu kodda virgül sözcüğü `Hello` izler ve virgül kırpılacak karakter dizisinde belirtilmediksin, kırpma virgülle sona erer.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-126">In this code, a comma follows the word `Hello` and, because the comma is not specified in the array of characters to trim, the trim ends at the comma.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 <span data-ttu-id="bd6cd-127">Bu kod `Hello,` konsola görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-127">This code displays `Hello,` to the console.</span></span>  
  
## <a name="trimstart"></a><span data-ttu-id="bd6cd-128">TrimStart</span><span class="sxs-lookup"><span data-stu-id="bd6cd-128">TrimStart</span></span>

 <span data-ttu-id="bd6cd-129">**String.TrimStart** yöntemi, varolan bir dize nesnesinin başlangıcından karakterleri kaldırarak yeni bir dize oluşturması dışında **String.TrimEnd** yöntemine benzer.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-129">The **String.TrimStart** method is similar to the **String.TrimEnd** method except that it creates a new string by removing characters from the beginning of an existing string object.</span></span> <span data-ttu-id="bd6cd-130">Kaldırılacak karakterleri belirtmek için **TrimStart** yöntemine bir dizi karakter aktarılır.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-130">An array of characters is passed to the **TrimStart** method to specify the characters to be removed.</span></span> <span data-ttu-id="bd6cd-131">**TrimEnd** yönteminde olduğu gibi, karakter dizisindeki öğelerin sırası kırpma işlemini etkilemez.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-131">As with the **TrimEnd** method, the order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="bd6cd-132">Dizide belirtilmeyen bir karakter bulunduğunda kırpma durur.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-132">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="bd6cd-133">Aşağıdaki örnek, bir dize ilk sözcük kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-133">The following example removes the first word of a string.</span></span> <span data-ttu-id="bd6cd-134">Bu örnekte, `'l'` dizideki karakterlerin `'H'` sırasının önemli olmadığını göstermek için karakterin ve karakterin konumu tersine çevrilir.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-134">In this example, the position of the `'l'` character and the `'H'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 <span data-ttu-id="bd6cd-135">Bu kod `World!` konsola görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-135">This code displays `World!` to the console.</span></span>  
  
## <a name="remove"></a><span data-ttu-id="bd6cd-136">Kaldır</span><span class="sxs-lookup"><span data-stu-id="bd6cd-136">Remove</span></span>

 <span data-ttu-id="bd6cd-137">Yöntem, <xref:System.String.Remove%2A?displayProperty=nameWithType> varolan bir dizede belirli bir konumda başlayan belirli sayıda karakter kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-137">The <xref:System.String.Remove%2A?displayProperty=nameWithType> method removes a specified number of characters that begin at a specified position in an existing string.</span></span> <span data-ttu-id="bd6cd-138">Bu yöntem, sıfır tabanlı bir dizin varsayar.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-138">This method assumes a zero-based index.</span></span>  
  
 <span data-ttu-id="bd6cd-139">Aşağıdaki örnek, dize sıfır tabanlı dizinin beşinci konumundan başlayarak bir dizeden on karakter kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-139">The following example removes ten characters from a string beginning at position five of a zero-based index of the string.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
## <a name="replace"></a><span data-ttu-id="bd6cd-140">Değiştir</span><span class="sxs-lookup"><span data-stu-id="bd6cd-140">Replace</span></span>

 <span data-ttu-id="bd6cd-141"><xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> Ayrıca, yöntemi çağırarak ve yerine boş bir dize (<xref:System.String.Empty?displayProperty=nameWithType>) belirterek, belirli bir karakteri veya alt dizeyi dizeden kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-141">You can also remove a specified character or substring from a string by calling the <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> method and specifying an empty string (<xref:System.String.Empty?displayProperty=nameWithType>) as the replacement.</span></span> <span data-ttu-id="bd6cd-142">Aşağıdaki örnek, bir dizedeki tüm virgülleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-142">The following example removes all commas from a string.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="bd6cd-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd6cd-143">See also</span></span>

- [<span data-ttu-id="bd6cd-144">Temel Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="bd6cd-144">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
