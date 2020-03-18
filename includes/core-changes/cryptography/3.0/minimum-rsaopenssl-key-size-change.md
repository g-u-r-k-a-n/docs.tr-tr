---
ms.openlocfilehash: 2fb980c8b75e25ba347c56ccc1c90f2959e83e21
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567954"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a><span data-ttu-id="f5c09-101">RSAOpenSsl anahtar üretimi için minimum boyut arttı</span><span class="sxs-lookup"><span data-stu-id="f5c09-101">Minimum size for RSAOpenSsl key generation has increased</span></span>

<span data-ttu-id="f5c09-102">Linux'ta yeni RSA anahtarları üretmek için minimum boyut 384 bit'ten 512 bit'e yükselmiştir.</span><span class="sxs-lookup"><span data-stu-id="f5c09-102">The minimum size for generating new RSA keys on Linux has increased from 384-bit to 512-bit.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f5c09-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="f5c09-103">Change description</span></span>

<span data-ttu-id="f5c09-104">.NET Core 3.0 ile başlayarak, RSA `LegalKeySizes` örneklerinde mülk tarafından <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>bildirilen <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType> minimum yasal anahtar boyutu , ve Linux'ta 384'ten 512'ye yükselmiştir.</span><span class="sxs-lookup"><span data-stu-id="f5c09-104">Starting with .NET Core 3.0, the minimum legal key size reported by the `LegalKeySizes` property on RSA instances from <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>, <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>, and <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType> on Linux has increased from 384 to 512.</span></span>

<span data-ttu-id="f5c09-105">Sonuç olarak, .NET Core 2.2 ve önceki sürümlerde, başarılı gibi `RSA.Create(384)` bir yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="f5c09-105">As a result, in .NET Core 2.2 and earlier versions, a method call such as `RSA.Create(384)` succeeds.</span></span> <span data-ttu-id="f5c09-106">.NET Core 3.0 ve sonraki sürümlerinde, yöntem çağrısı `RSA.Create(384)` boyutu çok küçük olduğunu belirten bir özel durum atar.</span><span class="sxs-lookup"><span data-stu-id="f5c09-106">In .NET Core 3.0 and later versions, the method call `RSA.Create(384)` throws an exception indicating the size is too small.</span></span>

<span data-ttu-id="f5c09-107">Bu değişiklik, Linux'taki şifreleme işlemlerini gerçekleştiren OpenSSL'nin 1.0.2 ve 1.1.0 sürümleri arasındaki minimum limitini yükseltmesi nedeniyle yapıldı.</span><span class="sxs-lookup"><span data-stu-id="f5c09-107">This change was made because OpenSSL, which performs the cryptographic operations on Linux, raised its minimum between versions 1.0.2 and 1.1.0.</span></span> <span data-ttu-id="f5c09-108">.NET Core 3.0 OpenSSL 1.1.x ile 1.0.x arasında tercih eder ve bildirilen minimum sürüm bu yeni yüksek bağımlılık sınırlamasını yansıtacak şekilde yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="f5c09-108">.NET Core 3.0 prefers OpenSSL 1.1.x to 1.0.x, and the minimum reported version was raised to reflect this new higher dependency limitation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f5c09-109">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="f5c09-109">Version introduced</span></span>

<span data-ttu-id="f5c09-110">3,0</span><span class="sxs-lookup"><span data-stu-id="f5c09-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f5c09-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="f5c09-111">Recommended action</span></span>

<span data-ttu-id="f5c09-112">Etkilenen API'lerden herhangi birini ararsanız, oluşturulan anahtarların boyutunun sağlayıcı minimumundan az olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="f5c09-112">If you call any of the affected APIs, ensure that the size of any generated keys is not less than the provider minimum.</span></span>

> [!NOTE]
> <span data-ttu-id="f5c09-113">384-bit RSA zaten güvensiz olarak kabul edilir (512-bit RSA olduğu gibi).</span><span class="sxs-lookup"><span data-stu-id="f5c09-113">384-bit RSA is already considered insecure (as is 512-bit RSA).</span></span> <span data-ttu-id="f5c09-114">[NIST Özel Yayın 800-57 Bölüm 1 Revizyon 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf)gibi modern öneriler, yeni oluşturulan anahtarlar için minimum boyut olarak 2048-bit öneririz.</span><span class="sxs-lookup"><span data-stu-id="f5c09-114">Modern recommendations, such as [NIST Special Publication 800-57 Part 1 Revision 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), suggest 2048-bit as the minimum size for newly generated keys.</span></span>

#### <a name="category"></a><span data-ttu-id="f5c09-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="f5c09-115">Category</span></span>

<span data-ttu-id="f5c09-116">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="f5c09-116">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f5c09-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f5c09-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType>

<!--
### Affected APIs

- `P:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes`
- `Overload:System.Security.Cryptography.RSA.Create`
- `Overload:System.Security.Cryptography.RSAOpenSsl.#ctor`
- `Overload:System.Security.Cryptography.RSACryptoServiceProvider.#ctor`

-->
