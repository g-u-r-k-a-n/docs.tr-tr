---
title: Şifreleme bölünmesi değişiklikleri-.NET Core
description: .NET Core 'da şifreleme ile ilgili son değişiklikleri listeler.
ms.date: 09/20/2019
ms.openlocfilehash: ce6739c57df801ef6ae3ab35e31bba6ad4055caa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73093088"
---
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="bcdef-103">Şifreleme son değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="bcdef-103">Cryptography breaking changes</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bcdef-104">Bu makale yapım aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="bcdef-104">This article is under construction.</span></span> <span data-ttu-id="bcdef-105">Bu, .NET Core önemli değişikliklerinin tamamen bir listesi değildir.</span><span class="sxs-lookup"><span data-stu-id="bcdef-105">This is not a complete list of .NET Core breaking changes.</span></span> <span data-ttu-id="bcdef-106">.NET Core ile ilgili değişiklikler hakkında daha fazla bilgi için GitHub 'daki DotNet/docs deposundaki tek tek [değişiklikler sorunlarını](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bcdef-106">For more information on .NET Core breaking changes, you can examine individual [breaking changes issues](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) in the dotnet/docs repository on GitHub.</span></span> 

<span data-ttu-id="bcdef-107">Aşağıda, .NET Core sürümüne göre şifrelemeye ilişkin önemli değişiklikler listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="bcdef-107">The following is a list of cryptography-related breaking changes by .NET Core version.</span></span>

## <a name="net-core-30-preview-9"></a><span data-ttu-id="bcdef-108">.NET Core 3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="bcdef-108">.NET Core 3.0 Preview 9</span></span>

[!INCLUDE[Better argument validation in the Pkcs8PrivateKeyInfo constructor](~/includes/core-changes/cryptography/better-argument-validation-in-pkcs8privatekeyinfo-ctor.md)]

## <a name="net-core-30"></a><span data-ttu-id="bcdef-109">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="bcdef-109">.NET Core 3.0</span></span>

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/net-core-3-0-prefers-openssl-1-1-x.md)]
