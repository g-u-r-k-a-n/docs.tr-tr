---
title: Şifreleme bölünmesi, sürüm 2,2, 3,0-.NET Core
description: Sürüm 2,2 ' den, .NET Core, ASP.NET Core ve EF Core sürüm 3,0 ' den son değişiklikleri listeler.
ms.date: 09/10/2019
ms.openlocfilehash: ba330bdef4be8cfe0e74f5645adaf66b2e0051ac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73089578"
---
# <a name="breaking-changes-for-migration-from-version-22-to-30"></a><span data-ttu-id="524b0-103">2,2 sürümünden 3,0 sürümüne geçiş için son değişiklikler</span><span class="sxs-lookup"><span data-stu-id="524b0-103">Breaking changes for migration from Version 2.2 to 3.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="524b0-104">Bu makale yapım aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="524b0-104">This article is under construction.</span></span> <span data-ttu-id="524b0-105">Bu, .NET Core önemli değişikliklerinin tamamen bir listesi değildir.</span><span class="sxs-lookup"><span data-stu-id="524b0-105">This is not a complete list of .NET Core breaking changes.</span></span> <span data-ttu-id="524b0-106">.NET Core ile ilgili değişiklikler hakkında daha fazla bilgi için GitHub 'daki DotNet/docs deposundaki tek tek [değişiklikler sorunlarını](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="524b0-106">For more information on .NET Core breaking changes, you can examine individual [breaking changes issues](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) in the dotnet/docs repository on GitHub.</span></span> 

<span data-ttu-id="524b0-107">Sürüm 2,2 ' den .NET Core, ASP.NET Core veya EF Core 3,0 sürümüne geçiş yapıyorsanız, uygulamanızı etkileyebilecek değişiklikler için aşağıdaki konuları gözden geçirin:</span><span class="sxs-lookup"><span data-stu-id="524b0-107">If you are migrating from version 2.2 to version 3.0 of .NET Core, ASP.NET Core, or EF Core, review the following topics for breaking changes that may affect your app:</span></span>

## <a name="corefx"></a><span data-ttu-id="524b0-108">CoreFx</span><span class="sxs-lookup"><span data-stu-id="524b0-108">CoreFx</span></span>

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/floating-point-changes.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/ziparchiveentry-and-inconsistent-entry-sizes.md)]

## <a name="cryptography"></a><span data-ttu-id="524b0-109">To</span><span class="sxs-lookup"><span data-stu-id="524b0-109">Cryptography</span></span>

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/net-core-3-0-prefers-openssl-1-1-x.md)]

## <a name="globalization"></a><span data-ttu-id="524b0-110">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="524b0-110">Globalization</span></span>

[!INCLUDE["C" locale maps to the invariant locale](~/includes/core-changes/globalization/c-locale-maps-to-invariant-locale.md)]

## <a name="visual-basic"></a><span data-ttu-id="524b0-111">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="524b0-111">Visual Basic</span></span>

[!INCLUDE[vbNewLine is obsolete](~/includes/core-changes/visualbasic/vbnewline-is-obsolete.md)]

## <a name="entity-framework-core"></a><span data-ttu-id="524b0-112">Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="524b0-112">Entity Framework Core</span></span>

[<span data-ttu-id="524b0-113">Entity Framework Core son değişiklikler</span><span class="sxs-lookup"><span data-stu-id="524b0-113">Entity Framework Core breaking changes</span></span>](/ef/core/what-is-new/ef-core-3.0/breaking-changes)
