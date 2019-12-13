---
ms.openlocfilehash: db1d09c8c9e606b5327a42977a74a74703282d84
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568230"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a><span data-ttu-id="d2081-101">.NET Core 3,0 hatalı biçimlendirilmiş UTF-8 bayt dizilerini değiştirirken Unicode en iyi yöntemlerini izler</span><span class="sxs-lookup"><span data-stu-id="d2081-101">.NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>

<span data-ttu-id="d2081-102"><xref:System.Text.UTF8Encoding> sınıfı, bir bayt karakter dönüştürme işlemi sırasında hatalı biçimlendirilmiş bir UTF-8 bayt dizisiyle karşılaştığında, bu diziyi çıkış dizesindeki bir ' ' (U + FFFD DEĞIŞTIRME KARAKTERI) karakteriyle değiştirecek.</span><span class="sxs-lookup"><span data-stu-id="d2081-102">When the <xref:System.Text.UTF8Encoding> class encounters an ill-formed UTF-8 byte sequence during a byte-to-character transcoding operation, it will replace that sequence with a '�' (U+FFFD REPLACEMENT CHARACTER) character in the output string.</span></span> <span data-ttu-id="d2081-103">.NET Core 3,0, .NET Core 'un önceki sürümlerinden ve .NET Framework dönüştürme işlemi sırasında bu değişikliği gerçekleştirmek için en iyi Unicode yöntemi izleyerek farklıdır.</span><span class="sxs-lookup"><span data-stu-id="d2081-103">.NET Core 3.0 differs from previous versions of .NET Core and the .NET Framework by following the Unicode best practice for performing this replacement during the transcoding operation.</span></span>

<span data-ttu-id="d2081-104">Bu, yeni <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> ve <xref:System.Text.Rune?displayProperty=nameWithType> türleri dahil olmak üzere .NET genelinde UTF-8 işlemesini geliştirmenin daha büyük bir çaba parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="d2081-104">This is part of a larger effort to improve UTF-8 handling throughout .NET, including by the new <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> and <xref:System.Text.Rune?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="d2081-105"><xref:System.Text.UTF8Encoding> türüne, Yeni tanıtılan türlerle tutarlı bir çıkış üretmesi için, bir hata işleme mekanizması sağlanmadı.</span><span class="sxs-lookup"><span data-stu-id="d2081-105">The <xref:System.Text.UTF8Encoding> type was given improved error handling mechanics so that it produces output consistent with the newly introduced types.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d2081-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="d2081-106">Change description</span></span>

<span data-ttu-id="d2081-107">.NET Core 3,0 ile başlayarak, baytları karakterlere dönüştürme sırasında <xref:System.Text.UTF8Encoding> sınıfı, Unicode en iyi uygulamalarına göre karakter değiştirme işlemini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="d2081-107">Starting with .NET Core 3.0, when transcoding bytes to characters, the <xref:System.Text.UTF8Encoding> class performs character substitution based on Unicode best practices.</span></span> <span data-ttu-id="d2081-108">Kullanılan değiştirme mekanizması, _U + FFFD Substitution alt bölümlerinin_başlığı altında bulunan başlık Içindeki [Unicode standart, sürüm 12,0, sec. 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) ile açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d2081-108">The substitution mechanism used is described by [The Unicode Standard, Version 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) in the heading titled _U+FFFD Substitution of Maximal Subparts_.</span></span>

<span data-ttu-id="d2081-109">Bu davranış _yalnızca_ , giriş bayt dizisi hatalı biçimlendirilmiş UTF-8 verileri içerdiğinde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d2081-109">This behavior _only_ applies when the input byte sequence contains ill-formed UTF-8 data.</span></span> <span data-ttu-id="d2081-110">Ek olarak, <xref:System.Text.UTF8Encoding> örneği `throwOnInvalidBytes: true` ile oluşturulmuşsa (bkz. [UTF8Encoding Oluşturucu belgeleri] (<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, `UTF8Encoding` örneği U + FFFD değişimi gerçekleştirmek yerine geçersiz giriş üzerinde throw 'e devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="d2081-110">Additionally, if the <xref:System.Text.UTF8Encoding> instance has been constructed with `throwOnInvalidBytes: true` (see the [UTF8Encoding constructor documentation](<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, the `UTF8Encoding` instance will continue to throw on invalid input rather than perform U+FFFD replacement.</span></span>

<span data-ttu-id="d2081-111">Aşağıda, bu değişikliğin geçerli bir 3 baytlık giriş ile etkisi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="d2081-111">The following illustrates the impact of this change with an invalid 3-byte input:</span></span>

|<span data-ttu-id="d2081-112">Hatalı biçimlendirilmiş 3 baytlık giriş</span><span class="sxs-lookup"><span data-stu-id="d2081-112">Ill-formed 3-byte input</span></span>|<span data-ttu-id="d2081-113">.NET Core 3,0 öncesi çıkış</span><span class="sxs-lookup"><span data-stu-id="d2081-113">Output before .NET Core 3.0</span></span>|<span data-ttu-id="d2081-114">.NET Core 3,0 ile başlayan çıkış</span><span class="sxs-lookup"><span data-stu-id="d2081-114">Output starting with .NET Core 3.0</span></span>|
|---|---|---|
| `[ ED A0 90 ]` | <span data-ttu-id="d2081-115">`[ FFFD FFFD ]` (2 karakterlik çıkış)</span><span class="sxs-lookup"><span data-stu-id="d2081-115">`[ FFFD FFFD ]` (2-character output)</span></span>| <span data-ttu-id="d2081-116">`[ FFFD FFFD FFFD ]` (3 karakterlik çıkış)</span><span class="sxs-lookup"><span data-stu-id="d2081-116">`[ FFFD FFFD FFFD ]` (3-character output)</span></span>|

<span data-ttu-id="d2081-117">Bu 3-char çıktısı, daha önce bağlantılı Unicode standart PDF 'nin _3-9 tablosuna_ göre tercih edilen çıktıdır.</span><span class="sxs-lookup"><span data-stu-id="d2081-117">This 3-char output is the preferred output, according to _Table 3-9_ of the previously linked Unicode Standard PDF.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d2081-118">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="d2081-118">Version introduced</span></span>

<span data-ttu-id="d2081-119">3,0</span><span class="sxs-lookup"><span data-stu-id="d2081-119">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d2081-120">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="d2081-120">Recommended action</span></span>

<span data-ttu-id="d2081-121">Geliştiricinin bölümünde herhangi bir eylem gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d2081-121">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="d2081-122">Category</span><span class="sxs-lookup"><span data-stu-id="d2081-122">Category</span></span>

<span data-ttu-id="d2081-123">CoreFx</span><span class="sxs-lookup"><span data-stu-id="d2081-123">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d2081-124">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="d2081-124">Affected APIs</span></span>

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->
