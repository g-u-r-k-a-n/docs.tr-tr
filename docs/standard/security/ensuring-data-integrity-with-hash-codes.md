---
title: Karma Kodlarla Veri Bütünlüğünü Sağlama
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generating hash
- verifying hash codes
- cryptography [.NET Framework], hash
- data integrity
- checking hash codes
- encryption [.NET Framework], hash
- hash
ms.assetid: 33660f33-b70f-4dca-8c87-ab35cfc2961a
ms.openlocfilehash: 98bdce59ccbbb3b1d00ea5521169214c2bd7a10b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706207"
---
# <a name="ensuring-data-integrity-with-hash-codes"></a><span data-ttu-id="3cee6-102">Karma Kodlarla Veri Bütünlüğünü Sağlama</span><span class="sxs-lookup"><span data-stu-id="3cee6-102">Ensuring Data Integrity with Hash Codes</span></span>
<span data-ttu-id="3cee6-103">Karma değeri, verileri benzersiz bir şekilde tanımlayan sabit uzunlukta sayısal bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="3cee6-103">A hash value is a numeric value of a fixed length that uniquely identifies data.</span></span> <span data-ttu-id="3cee6-104">Karma değerler, büyük miktarlarda veriyi çok daha küçük sayısal değerler halinde temsil eder, bu nedenle dijital imzalarla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3cee6-104">Hash values represent large amounts of data as much smaller numeric values, so they are used with digital signatures.</span></span> <span data-ttu-id="3cee6-105">Karma değeri, daha büyük değeri imzalamadan daha verimli bir şekilde imzalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cee6-105">You can sign a hash value more efficiently than signing the larger value.</span></span> <span data-ttu-id="3cee6-106">Karma değerleri, güvenli olmayan kanallar aracılığıyla gönderilen verilerin bütünlüğünü doğrulamak için de kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="3cee6-106">Hash values are also useful for verifying the integrity of data sent through insecure channels.</span></span> <span data-ttu-id="3cee6-107">Alınan verilerin karma değeri, verilerin değiştirilip değiştirilmediğini tespit etmek için gönderilen verilerin karma değeriyle karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="3cee6-107">The hash value of received data can be compared to the hash value of data as it was sent to determine whether the data was altered.</span></span>  
  
 <span data-ttu-id="3cee6-108">Bu konu, <xref:System.Security.Cryptography?displayProperty=nameWithType> ad alanındaki sınıfları kullanarak karma kodların nasıl oluşturulacağını ve doğrulanacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="3cee6-108">This topic describes how to generate and verify hash codes by using the classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="generating-a-hash"></a><span data-ttu-id="3cee6-109">Karma oluşturma</span><span class="sxs-lookup"><span data-stu-id="3cee6-109">Generating a Hash</span></span>  
 <span data-ttu-id="3cee6-110">Yönetilen karma sınıflar bir bayt dizisini veya yönetilen bir akış nesnesini karma hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cee6-110">The managed hash classes can hash either an array of bytes or a managed stream object.</span></span> <span data-ttu-id="3cee6-111">Aşağıdaki örnek, bir dize için bir karma değer oluşturmak üzere SHA1 karma algoritmasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="3cee6-111">The following example uses the SHA1 hash algorithm to create a hash value for a string.</span></span> <span data-ttu-id="3cee6-112">Örnek, <xref:System.Security.Cryptography.SHA1Managed> sınıfını kullanarak dizeyi karma bir bayt dizisine dönüştürmek için <xref:System.Text.UnicodeEncoding> sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="3cee6-112">The example uses the <xref:System.Text.UnicodeEncoding> class to convert the string into an array of bytes that are hashed by using the <xref:System.Security.Cryptography.SHA1Managed> class.</span></span> <span data-ttu-id="3cee6-113">Karma değeri daha sonra konsola görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="3cee6-113">The hash value is then displayed to the console.</span></span>  

 <span data-ttu-id="3cee6-114">Microsoft, SHA1 ile ilgili çakışma sorunları nedeniyle SHA256 veya daha iyi bir performans öneriyor.</span><span class="sxs-lookup"><span data-stu-id="3cee6-114">Due to collision problems with SHA1, Microsoft recommends SHA256 or better.</span></span>
  
 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="3cee6-115">Bu kod konsola aşağıdaki dizeyi gösterir:</span><span class="sxs-lookup"><span data-stu-id="3cee6-115">This code will display the following string to the console:</span></span>  
  
 `59 4 248 102 77 97 142 201 210 12 224 93 25 41 100 197 213 134 130 135`  
  
## <a name="verifying-a-hash"></a><span data-ttu-id="3cee6-116">Karma doğrulama</span><span class="sxs-lookup"><span data-stu-id="3cee6-116">Verifying a Hash</span></span>  
 <span data-ttu-id="3cee6-117">Verileri, bütünlüğünü tespit etmek için bir karma değerle karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="3cee6-117">Data can be compared to a hash value to determine its integrity.</span></span> <span data-ttu-id="3cee6-118">Genellikle, veriler belirli bir zamanda karma hale getirilir ve karma değeri bir şekilde korunur.</span><span class="sxs-lookup"><span data-stu-id="3cee6-118">Usually, data is hashed at a certain time and the hash value is protected in some way.</span></span> <span data-ttu-id="3cee6-119">Daha sonra veriler karma hale getirilir ve korunan değerle karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="3cee6-119">At a later time, the data can be hashed again and compared to the protected value.</span></span> <span data-ttu-id="3cee6-120">Karma değerleri eşleşiyorsa, veriler değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="3cee6-120">If the hash values match, the data has not been altered.</span></span> <span data-ttu-id="3cee6-121">Değerler eşleşmiyorsa, veriler bozulmuş demektir.</span><span class="sxs-lookup"><span data-stu-id="3cee6-121">If the values do not match, the data has been corrupted.</span></span> <span data-ttu-id="3cee6-122">Bu sistemin çalışması için korunan karmaların güvenilmeyen tüm taraflardan şifrelenmesi veya gizli tutulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3cee6-122">For this system to work, the protected hash must be encrypted or kept secret from all untrusted parties.</span></span>  
  
 <span data-ttu-id="3cee6-123">Aşağıdaki örnek bir dizenin önceki karma değerini yeni bir karma değerle karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="3cee6-123">The following example compares the previous hash value of a string to a new hash value.</span></span> <span data-ttu-id="3cee6-124">Bu örnek, karma değerlerin her baytında döngü yapar ve bir karşılaştırma yapar.</span><span class="sxs-lookup"><span data-stu-id="3cee6-124">This example loops through each byte of the hash values and makes a comparison.</span></span>  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="3cee6-125">İki karma değer eşleşiyorsa, bu kod konsola aşağıdakileri gösterir:</span><span class="sxs-lookup"><span data-stu-id="3cee6-125">If the two hash values match, this code displays the following to the console:</span></span>  
  
```console  
The hash codes match.  
```  
  
 <span data-ttu-id="3cee6-126">Bunlar eşleşmiyorsa, kod aşağıdakileri görüntüler:</span><span class="sxs-lookup"><span data-stu-id="3cee6-126">If they do not match, the code displays the following:</span></span>  
  
```console  
The hash codes do not match.  
```  
  
## <a name="see-also"></a><span data-ttu-id="3cee6-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3cee6-127">See also</span></span>

- [<span data-ttu-id="3cee6-128">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="3cee6-128">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
