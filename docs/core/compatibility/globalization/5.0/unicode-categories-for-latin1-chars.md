---
title: 'Son değişiklik: bazı Latin-1 karakterleri için Unicode kategorisi değişti'
description: .NET 5 ' teki Genelleştirme bölünmesi değişikliği hakkında bilgi edinmek için Char yöntemlerinin artık Latin-1 aralığındaki karakterler için doğru Unicode kategorisini döndürdüğü yerde.
ms.date: 04/07/2020
ms.openlocfilehash: 03355c488d2bdae78f989e647c9b5b7913d73649
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256679"
---
# <a name="unicode-category-changed-for-some-latin-1-characters"></a><span data-ttu-id="19010-103">Bazı Latin-1 karakterleri için Unicode kategorisi değişti</span><span class="sxs-lookup"><span data-stu-id="19010-103">Unicode category changed for some Latin-1 characters</span></span>

<span data-ttu-id="19010-104"><xref:System.Char> Yöntemler şimdi Latin-1 aralığındaki karakterler için doğru Unicode kategorisini döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="19010-104"><xref:System.Char> methods now return the correct Unicode category for characters in the Latin-1 range.</span></span> <span data-ttu-id="19010-105">Kategori Unicode standardına göre eşleşir.</span><span class="sxs-lookup"><span data-stu-id="19010-105">The category matches that of the Unicode standard.</span></span>

## <a name="change-description"></a><span data-ttu-id="19010-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="19010-106">Change description</span></span>

<span data-ttu-id="19010-107">Önceki .NET sürümlerinde, <xref:System.Char> Yöntemler Latin-1 aralığındaki karakterler için sabit bir Unicode kategori listesi kullandı.</span><span class="sxs-lookup"><span data-stu-id="19010-107">In previous .NET versions, <xref:System.Char> methods used a fixed list of Unicode categories for characters in the Latin-1 range.</span></span> <span data-ttu-id="19010-108">Ancak, Unicode standardı Bu API 'lerin uygulandığından bu karakterlerin bazı kategorilerini değiştirmiştir, bu da bir tutarsızlık oluşturuyor.</span><span class="sxs-lookup"><span data-stu-id="19010-108">However, the Unicode standard has changed the categories of some of these characters since those APIs were implemented, creating a discrepancy.</span></span> <span data-ttu-id="19010-109">Ayrıca, ve API 'ler arasında bir tutarsızlık vardı <xref:System.Char> <xref:System.Globalization.CharUnicodeInfo> , bu da Unicode standardını izler.</span><span class="sxs-lookup"><span data-stu-id="19010-109">In addition, there was also a discrepancy between <xref:System.Char> and <xref:System.Globalization.CharUnicodeInfo> APIs, which follow the Unicode standard.</span></span> <span data-ttu-id="19010-110">.NET 5 ve sonraki sürümlerde Yöntemler, <xref:System.Char> tüm karakterler Için Unicode standardı ile eşleşen Unicode kategorisini kullanır ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="19010-110">In .NET 5 and later versions, <xref:System.Char> methods use and return the Unicode category that matches the Unicode standard for all characters.</span></span>

<span data-ttu-id="19010-111">Aşağıdaki tabloda, .NET 5,0 ' de Unicode kategorileri değişmiş olan karakterler gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="19010-111">The following table shows the characters whose Unicode categories have changed in .NET 5.0:</span></span>

| <span data-ttu-id="19010-112">Karakter</span><span class="sxs-lookup"><span data-stu-id="19010-112">Character</span></span>    | <span data-ttu-id="19010-113">Unicode kategorisi</span><span class="sxs-lookup"><span data-stu-id="19010-113">Unicode category</span></span><br><span data-ttu-id="19010-114">önceki .NET sürümlerinde</span><span class="sxs-lookup"><span data-stu-id="19010-114">in previous .NET versions</span></span> | <span data-ttu-id="19010-115">Unicode kategorisi</span><span class="sxs-lookup"><span data-stu-id="19010-115">Unicode category</span></span><br><span data-ttu-id="19010-116">.NET 5 ve sonraki sürümlerde</span><span class="sxs-lookup"><span data-stu-id="19010-116">in .NET 5 and later versions</span></span> |
|:------------:|:---------------------------------------------:|:--------------------------------------------------:|
| <span data-ttu-id="19010-117">§ (\u00a7)</span><span class="sxs-lookup"><span data-stu-id="19010-117">§ (\u00a7)</span></span>   | `OtherSymbol`                                 | `OtherPunctuation`                                 |
| <span data-ttu-id="19010-118">ª (\u00aa)</span><span class="sxs-lookup"><span data-stu-id="19010-118">ª (\u00aa)</span></span>   | `LowercaseLetter`                             | `OtherLetter`                                      |
| <span data-ttu-id="19010-119">KıY (\u00ad)</span><span class="sxs-lookup"><span data-stu-id="19010-119">SHY (\u00ad)</span></span> | `DashPunctuation`                             | `Format`                                           |
| <span data-ttu-id="19010-120">¶ (\u00b6)</span><span class="sxs-lookup"><span data-stu-id="19010-120">¶ (\u00b6)</span></span>   | `OtherSymbol`                                 | `OtherPunctuation`                                 |
| <span data-ttu-id="19010-121">† (\u00ba)</span><span class="sxs-lookup"><span data-stu-id="19010-121">º (\u00ba)</span></span>   | `LowercaseLetter`                             | `OtherLetter`                                      |

## <a name="version-introduced"></a><span data-ttu-id="19010-122">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="19010-122">Version introduced</span></span>

<span data-ttu-id="19010-123">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="19010-123">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="19010-124">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="19010-124">Recommended action</span></span>

<span data-ttu-id="19010-125">Sınıfını kullanarak Unicode karakter kategorisini alan herhangi bir kodunuz varsa <xref:System.Char> ve kategorinin hiçbir şekilde değişmediğini kabul eterdiğinizi, güncelleştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="19010-125">If you have any code that gets the Unicode character category by using the <xref:System.Char> class and assumes the category will never change, you may need to update it.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="19010-126">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="19010-126">Reason for change</span></span>

<span data-ttu-id="19010-127">Bu değişiklik, türü tarafından döndürülen kategorilerin <xref:System.Char> hem Unicode standardı hem de türü ile tutarlı olması için yapılmıştır <xref:System.Globalization.CharUnicodeInfo> .</span><span class="sxs-lookup"><span data-stu-id="19010-127">This change was made so that the categories returned by the <xref:System.Char> type are consistent with both the Unicode standard and the <xref:System.Globalization.CharUnicodeInfo> type.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="19010-128">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="19010-128">Affected APIs</span></span>

- <xref:System.Char.GetUnicodeCategory%2A?displayProperty=fullName>
- <xref:System.Char.IsLetter%2A?displayProperty=fullName>
- <xref:System.Char.IsPunctuation%2A?displayProperty=fullName>
- <xref:System.Char.IsSymbol%2A?displayProperty=fullName>
- <xref:System.Char.IsLower%2A?displayProperty=fullName>

<span data-ttu-id="19010-129">Ayrıca, <xref:System.Char> Unicode karakter kategorisini elde etmek için bağlı olan herhangi bir sınıf, örneğin, <xref:System.Text.RegularExpressions.Regex> Bu değişiklikten etkilenir.</span><span class="sxs-lookup"><span data-stu-id="19010-129">Additionally, any class that depends on <xref:System.Char> to obtain the Unicode character category, for example, <xref:System.Text.RegularExpressions.Regex>, is affected by this change.</span></span>

<!--

### Affected APIs

- `Overload:System.Char.GetUnicodeCategory`
- `Overload:System.Char.IsLetter`
- `Overload:System.Char.IsPunctuation`
- `Overload:System.Char.IsSymbol`
- `Overload:System.Char.IsLower`

### Category

- Core .NET libraries
- Globalization
-
-->
