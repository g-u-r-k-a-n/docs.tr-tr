---
ms.openlocfilehash: b90991affe158286f535f3cc17232efd0b730fec
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275234"
---
### <a name="envelopedcms-defaults-to-aes-256-encryption"></a><span data-ttu-id="7e2d2-101">EnvelopedCms varsayılan olarak AES-256 şifrelemesi için</span><span class="sxs-lookup"><span data-stu-id="7e2d2-101">EnvelopedCms defaults to AES-256 encryption</span></span>

<span data-ttu-id="7e2d2-102">Kullanılan `EnvelopedCms` varsayılan simetrik şifreleme algoritması TripleDES'ten AES-256'ya değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="7e2d2-102">The default symmetric encryption algorithm used by `EnvelopedCms` has changed from TripleDES to AES-256.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7e2d2-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="7e2d2-103">Change description</span></span>

<span data-ttu-id="7e2d2-104">.NET Core Preview 7 ve <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> önceki sürümlerinde, bir yapıcı aşırı yük yoluyla simetrik şifreleme algoritması belirtmeden verileri şifrelemek için kullanıldığında, veriler TripleDES/3DES/3DEA/DES3-EDE algoritması ile şifrelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="7e2d2-104">In .NET Core Preview 7 and earlier versions, when <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> is used to encrypt data without specifying a symmetric encryption algorithm via a constructor overload, the data was encrypted with the TripleDES/3DES/3DEA/DES3-EDE algorithm.</span></span>

<span data-ttu-id="7e2d2-105">.NET Core 3.0 Preview 8 ile başlayarak [(System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet paketinin 4.6.0 sürümü üzerinden) varsayılan algoritma algoritma modernizasyonu ve varsayılan seçeneklerin güvenliğini artırmak için AES-256 olarak değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="7e2d2-105">Starting with .NET Core 3.0 Preview 8 (via version 4.6.0 of the [System.Security.Cryptography.Pkcs](https://www.nuget.org/packages/System.Security.Cryptography.Pkcs/) NuGet package), the default algorithm has been changed to AES-256 for algorithm modernization and to improve the security of default options.</span></span> <span data-ttu-id="7e2d2-106">İleti alıcısı sertifikasında (EC olmayan) diffie-Hellman ortak anahtarı varsa, <xref:System.Security.Cryptography.CryptographicException> şifreleme işlemi temel platformdaki sınırlamalar nedeniyle başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="7e2d2-106">If a message recipient certificate has a (non-EC) Diffie-Hellman public key, the encryption operation may fail with a <xref:System.Security.Cryptography.CryptographicException> due to limitations in the underlying platform.</span></span>

<span data-ttu-id="7e2d2-107">Aşağıdaki örnek kodda, .NET Core 3.0 Preview 7 veya daha önce çalışıyorsa veriler TripleDES ile şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="7e2d2-107">In the following sample code, the data is encrypted with TripleDES if running on .NET Core 3.0 Preview 7 or earlier.</span></span> <span data-ttu-id="7e2d2-108">.NET Core 3.0 Preview 8 veya sonraki saatlerde çalışıyorsa, AES-256 ile şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="7e2d2-108">If running on .NET Core 3.0 Preview 8 or later, it is encrypted with AES-256.</span></span>

```csharp
EnvelopedCms cms = new EnvelopedCms(content);
cms.Encrypt(recipient);
return cms.Encode();
```

#### <a name="version-introduced"></a><span data-ttu-id="7e2d2-109">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="7e2d2-109">Version introduced</span></span>

<span data-ttu-id="7e2d2-110">3.0 Önizleme 8</span><span class="sxs-lookup"><span data-stu-id="7e2d2-110">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7e2d2-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="7e2d2-111">Recommended action</span></span>

<span data-ttu-id="7e2d2-112">Değişiklikten olumsuz etkilenirseniz, aşağıdakigibi bir tür <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>parametresi içeren bir oluşturucudaki şifreleme algoritma tanımlayıcısını açıkça belirterek TripleDES şifrelemesini geri yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7e2d2-112">If you are negatively impacted by the change, you can restore TripleDES encryption by explicitly specifying the encryption algorithm identifier in an <xref:System.Security.Cryptography.Pkcs.EnvelopedCms> constructor that includes a parameter of type <xref:System.Security.Cryptography.Pkcs.AlgorithmIdentifier>, such as:</span></span>

```csharp
Oid tripleDesOid = new Oid("1.2.840.113549.3.7", null);
AlgorithmIdentifier tripleDesIdentifier = new AlgorithmIdentifier(tripleDesOid);
EnvelopedCms cms = new EnvelopedCms(content, tripleDesIdentifier);

cms.Encrypt(recipient);
return cms.Encode()l
```

#### <a name="category"></a><span data-ttu-id="7e2d2-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="7e2d2-113">Category</span></span>

<span data-ttu-id="7e2d2-114">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="7e2d2-114">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7e2d2-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="7e2d2-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.ContentInfo)>
- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.#ctor(System.Security.Cryptography.Pkcs.ContentInfo)`
- `M:System.Security.Cryptography.Pkcs.EnvelopedCms.%23ctor(System.Security.Cryptography.Pkcs.SubjectIdentifierType,System.Security.Cryptography.Pkcs.ContentInfo)`

-->
