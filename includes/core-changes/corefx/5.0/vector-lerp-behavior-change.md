---
ms.openlocfilehash: 4bc060f991501b81db0cb7c521e55996a2b5e91e
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281321"
---
### <a name="behavior-change-for-vector2lerp-and-vector4lerp"></a><span data-ttu-id="2ef12-101">Vector2. Lerp ve Vector4. Lerp için davranış değişikliği</span><span class="sxs-lookup"><span data-stu-id="2ef12-101">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>

<span data-ttu-id="2ef12-102"><xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> Bir kayan nokta yuvarlama hatası için uygulamasının uygulanması ve doğru hesaba değiştirilmesi.</span><span class="sxs-lookup"><span data-stu-id="2ef12-102">The implementation of <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> and <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> changed to correctly account for a floating-point rounding error.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2ef12-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="2ef12-103">Change description</span></span>

<span data-ttu-id="2ef12-104">Daha önce <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> ve <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> olarak uygulandı `value1 + (value2 - value1) * amount` .</span><span class="sxs-lookup"><span data-stu-id="2ef12-104">Previously, <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> and <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> were implemented as `value1 + (value2 - value1) * amount`.</span></span> <span data-ttu-id="2ef12-105">Ancak, bir kayan nokta yuvarlama hatası nedeniyle, bu algoritma olduğunda her zaman döndürmez `value2` `amount` `1.0f` .</span><span class="sxs-lookup"><span data-stu-id="2ef12-105">However, due to a floating-point rounding error, this algorithm doesn't always return `value2` when `amount` is `1.0f`.</span></span>

<span data-ttu-id="2ef12-106">.NET 5,0 ve üzeri sürümlerde, uygulama ile aynı algoritmayı kullanır <xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType> `(value1 * (1.0f - amount)) + (value2 * amount)` .</span><span class="sxs-lookup"><span data-stu-id="2ef12-106">In .NET 5.0 and later, the implementation uses the same algorithm as <xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType>, which is `(value1 * (1.0f - amount)) + (value2 * amount)`.</span></span> <span data-ttu-id="2ef12-107">Bu algoritma, yuvarlama hatası için doğru şekilde hesaplar.</span><span class="sxs-lookup"><span data-stu-id="2ef12-107">This algorithm correctly accounts for the rounding error.</span></span> <span data-ttu-id="2ef12-108">Şimdi, ne zaman, `amount` `1.0f` sonuç kesin olarak olur `value2` .</span><span class="sxs-lookup"><span data-stu-id="2ef12-108">Now, when `amount` is `1.0f`, the result is precisely `value2`.</span></span> <span data-ttu-id="2ef12-109">Güncelleştirilmiş algoritma Ayrıca algoritmaların kullanılabilir olduğunda, kullanımı uygun şekilde iyileştirilme olanağı sağlar <xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2ef12-109">The updated algorithm also allows the algorithm to be freely optimized using <xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> when it's available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2ef12-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="2ef12-110">Version introduced</span></span>

<span data-ttu-id="2ef12-111">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="2ef12-111">5.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2ef12-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="2ef12-112">Recommended action</span></span>

<span data-ttu-id="2ef12-113">Herhangi bir işlem gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="2ef12-113">No action is necessary.</span></span> <span data-ttu-id="2ef12-114">Ancak, eski davranışı sürdürmek istiyorsanız, `Lerp` önceki algoritmasını kullanan kendi işlevinizi uygulayabilirsiniz `value1 + (value2 - value1) * amount` .</span><span class="sxs-lookup"><span data-stu-id="2ef12-114">However, if you want to maintain the old behavior, you can implement your own `Lerp` function that uses the previous algorithm of `value1 + (value2 - value1) * amount`.</span></span>

#### <a name="category"></a><span data-ttu-id="2ef12-115">Category</span><span class="sxs-lookup"><span data-stu-id="2ef12-115">Category</span></span>

<span data-ttu-id="2ef12-116">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="2ef12-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2ef12-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="2ef12-117">Affected APIs</span></span>

- <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=fullName>
- <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)`
- `M:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)`

-->
