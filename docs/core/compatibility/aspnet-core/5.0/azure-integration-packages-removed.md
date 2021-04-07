---
title: 'Son değişiklik: Azure: Microsoft-önekli Azure tümleştirme paketleri kaldırıldı'
description: "ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: Microsoft-önekli Azure tümleştirme paketleri kaldırıldı"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: be7b2eeb6b12d033517c15ecb29e0d5364d64817
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498236"
---
# <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a><span data-ttu-id="b3332-103">Azure: Microsoft 'un ön eki olan Azure tümleştirme paketleri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="b3332-103">Azure: Microsoft-prefixed Azure integration packages removed</span></span>

<span data-ttu-id="b3332-104">`Microsoft.*`ASP.NET Core ve Azure SDK 'ları arasında tümleştirme sağlayan aşağıdaki paketler, ASP.NET Core 5,0 ' ye dahil değildir:</span><span class="sxs-lookup"><span data-stu-id="b3332-104">The following `Microsoft.*` packages that provide integration between ASP.NET Core and Azure SDKs aren't included in ASP.NET Core 5.0:</span></span>

* <span data-ttu-id="b3332-105">[Microsoft.Extensions.Configurlama. ](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/) [Yapılandırma sistemine](/aspnet/core/fundamentals/configuration/) [Azure Key Vault](/azure/key-vault/) tümleştiren AzureKeyVault.</span><span class="sxs-lookup"><span data-stu-id="b3332-105">[Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), which integrates [Azure Key Vault](/azure/key-vault/) into the [Configuration system](/aspnet/core/fundamentals/configuration/).</span></span>
* <span data-ttu-id="b3332-106">Azure Key Vault [ASP.NET Core veri koruma sistemine](/aspnet/core/security/data-protection/introduction)tümleştiren [Microsoft. Aspnetcore. DataProtection. AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/).</span><span class="sxs-lookup"><span data-stu-id="b3332-106">[Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), which integrates Azure Key Vault into the [ASP.NET Core Data Protection system](/aspnet/core/security/data-protection/introduction).</span></span>
* <span data-ttu-id="b3332-107">[Azure Blob depolamayı](/azure/storage/blobs/) ASP.NET Core veri koruma sistemine tümleştiren [Microsoft. Aspnetcore. DataProtection. azurestorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/).</span><span class="sxs-lookup"><span data-stu-id="b3332-107">[Microsoft.AspNetCore.DataProtection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), which integrates [Azure Blob Storage](/azure/storage/blobs/) into the ASP.NET Core Data Protection system.</span></span>

<span data-ttu-id="b3332-108">Bu sorunla ilgili tartışmak için bkz. [DotNet/aspnetcore # 19570](https://github.com/dotnet/aspnetcore/issues/19570).</span><span class="sxs-lookup"><span data-stu-id="b3332-108">For discussion on this issue, see [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="b3332-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="b3332-109">Version introduced</span></span>

<span data-ttu-id="b3332-110">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="b3332-110">5.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="b3332-111">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="b3332-111">Old behavior</span></span>

<span data-ttu-id="b3332-112">, `Microsoft.*` Yapılandırma ve veri koruma API 'leri ile tümleştirilmiş Azure hizmetlerini paketler.</span><span class="sxs-lookup"><span data-stu-id="b3332-112">The `Microsoft.*` packages integrated Azure services with the Configuration and Data Protection APIs.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="b3332-113">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="b3332-113">New behavior</span></span>

<span data-ttu-id="b3332-114">Yeni `Azure.*` paketler, Azure hizmetlerini yapılandırma ve veri koruma API 'leriyle tümleştirir.</span><span class="sxs-lookup"><span data-stu-id="b3332-114">New `Azure.*` packages integrate Azure services with the Configuration and Data Protection APIs.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="b3332-115">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="b3332-115">Reason for change</span></span>

<span data-ttu-id="b3332-116">Bu değişiklik, paketler şu şekilde yapılmıştır `Microsoft.*` :</span><span class="sxs-lookup"><span data-stu-id="b3332-116">The change was made because the `Microsoft.*` packages were:</span></span>

* <span data-ttu-id="b3332-117">Azure SDK 'sının güncel olmayan sürümlerini kullanma.</span><span class="sxs-lookup"><span data-stu-id="b3332-117">Using outdated versions of the Azure SDK.</span></span> <span data-ttu-id="b3332-118">Azure SDK 'sının yeni sürümleri büyük değişiklikler yaptığından basit güncelleştirmeler yapılamıyor.</span><span class="sxs-lookup"><span data-stu-id="b3332-118">Simple updates weren't possible because the new versions of the Azure SDK included breaking changes.</span></span>
* <span data-ttu-id="b3332-119">.NET Core sürüm çizelgesine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b3332-119">Tied to the .NET Core release schedule.</span></span> <span data-ttu-id="b3332-120">Paketlerin sahipliğini Azure SDK ekibine aktarmak, Azure SDK güncelleştirildiğinde paket güncelleştirmelerinin yapılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3332-120">Transferring ownership of the packages to the Azure SDK team enables package updates as the Azure SDK is updated.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="b3332-121">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="b3332-121">Recommended action</span></span>

<span data-ttu-id="b3332-122">ASP.NET Core 2,1 veya üzeri projelerde eskisini `Microsoft.*` Yeni `Azure.*` paketlerle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b3332-122">In ASP.NET Core 2.1 or later projects, replace the old `Microsoft.*` with the new `Azure.*` packages.</span></span>

| <span data-ttu-id="b3332-123">Eskisi</span><span class="sxs-lookup"><span data-stu-id="b3332-123">Old</span></span> | <span data-ttu-id="b3332-124">Yeni</span><span class="sxs-lookup"><span data-stu-id="b3332-124">New</span></span> |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [<span data-ttu-id="b3332-125">Azure. Extensions. AspNetCore. DataProtection. Keys</span><span class="sxs-lookup"><span data-stu-id="b3332-125">Azure.Extensions.AspNetCore.DataProtection.Keys</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [<span data-ttu-id="b3332-126">Azure. Extensions. AspNetCore. DataProtection. blob 'Lar</span><span class="sxs-lookup"><span data-stu-id="b3332-126">Azure.Extensions.AspNetCore.DataProtection.Blobs</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [<span data-ttu-id="b3332-127">Azure.Extensions.AspNetCore.Configurlama. Kaynaklanır</span><span class="sxs-lookup"><span data-stu-id="b3332-127">Azure.Extensions.AspNetCore.Configuration.Secrets</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.Configuration.Secrets) |

<span data-ttu-id="b3332-128">Yeni paketler Azure SDK 'sının son değişiklikleri içeren yeni bir sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="b3332-128">The new packages use a new version of the Azure SDK that includes breaking changes.</span></span> <span data-ttu-id="b3332-129">Genel kullanım desenleri değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="b3332-129">The general usage patterns are unchanged.</span></span> <span data-ttu-id="b3332-130">Bazı aşırı yüklemeler ve seçenekler, temel alınan Azure SDK API 'Lerinde değişikliklere uyum sağlamak için farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="b3332-130">Some overloads and options may differ to adapt to changes in the underlying Azure SDK APIs.</span></span>

<span data-ttu-id="b3332-131">Eski paketler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b3332-131">The old packages will:</span></span>

* <span data-ttu-id="b3332-132">.NET Core 2,1 ve 3,1 ' nin kullanım ömrü boyunca ASP.NET Core ekibi tarafından desteklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="b3332-132">Be supported by the ASP.NET Core team for the lifetime of .NET Core 2.1 and 3.1.</span></span>
* <span data-ttu-id="b3332-133">.NET 5 ' te bulunmaz.</span><span class="sxs-lookup"><span data-stu-id="b3332-133">Not be included in .NET 5.</span></span>

<span data-ttu-id="b3332-134">Projenizi .NET 5 ' e yükseltirken, `Azure.*` destek sağlamak için paketlere geçiş yapın.</span><span class="sxs-lookup"><span data-stu-id="b3332-134">When upgrading your project to .NET 5, transition to the `Azure.*` packages to maintain support.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="b3332-135">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b3332-135">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage`

-->
