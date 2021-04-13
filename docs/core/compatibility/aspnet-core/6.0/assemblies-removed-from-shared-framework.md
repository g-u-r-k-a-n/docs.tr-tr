---
title: "Son değişiklik: Microsoft.AspNetCore.App Shared Framework 'ten kaldırılan derlemeler"
description: Microsoft.AspNetCore.App paylaşılan çerçevesinden kaldırılan bazı derlemelerin ASP.NET Core 6,0 ' deki Son değişiklik hakkında bilgi edinin.
ms.date: 04/02/2021
ms.openlocfilehash: e6a0aa97dd97eae2cdc5aa8ae64e277840d6a083
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255265"
---
# <a name="assemblies-removed-from-microsoftaspnetcoreapp-shared-framework"></a><span data-ttu-id="9625a-103">Microsoft.AspNetCore.App paylaşılan çerçevesinden kaldırılan derlemeler</span><span class="sxs-lookup"><span data-stu-id="9625a-103">Assemblies removed from Microsoft.AspNetCore.App shared framework</span></span>

<span data-ttu-id="9625a-104">Aşağıdaki iki derleme ASP.NET Core hedefleme paketinden kaldırılmıştır:</span><span class="sxs-lookup"><span data-stu-id="9625a-104">The following two assemblies were removed from the ASP.NET Core targeting pack:</span></span>

- <span data-ttu-id="9625a-105">System. Security. Permissions</span><span class="sxs-lookup"><span data-stu-id="9625a-105">System.Security.Permissions</span></span>
- <span data-ttu-id="9625a-106">System. Windows. Extensions</span><span class="sxs-lookup"><span data-stu-id="9625a-106">System.Windows.Extensions</span></span>

<span data-ttu-id="9625a-107">Ayrıca, aşağıdaki derlemeler ASP.NET Core çalışma zamanı paketinden kaldırılmıştır:</span><span class="sxs-lookup"><span data-stu-id="9625a-107">In addition, the following assemblies were removed from the ASP.NET Core runtime pack:</span></span>

- <span data-ttu-id="9625a-108">Microsoft.Win32.SystemEvents</span><span class="sxs-lookup"><span data-stu-id="9625a-108">Microsoft.Win32.SystemEvents</span></span>
- <span data-ttu-id="9625a-109">System. Drawing. Common</span><span class="sxs-lookup"><span data-stu-id="9625a-109">System.Drawing.Common</span></span>
- <span data-ttu-id="9625a-110">System. Security. Permissions</span><span class="sxs-lookup"><span data-stu-id="9625a-110">System.Security.Permissions</span></span>
- <span data-ttu-id="9625a-111">System. Windows. Extensions</span><span class="sxs-lookup"><span data-stu-id="9625a-111">System.Windows.Extensions</span></span>

## <a name="version-introduced"></a><span data-ttu-id="9625a-112">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="9625a-112">Version introduced</span></span>

<span data-ttu-id="9625a-113">ASP.NET Core 6,0</span><span class="sxs-lookup"><span data-stu-id="9625a-113">ASP.NET Core 6.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="9625a-114">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="9625a-114">Old behavior</span></span>

<span data-ttu-id="9625a-115">Uygulamalar, [Microsoft.AspNetCore.app](/aspnet/core/fundamentals/metapackage-app) paylaşılan çerçevesine başvurarak bu kitaplıklar tarafından sunulan API 'leri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="9625a-115">Applications could use APIs provided by these libraries by referencing the [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) shared framework.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="9625a-116">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="9625a-116">New behavior</span></span>

<span data-ttu-id="9625a-117">Etkilenen derlemelerden API 'Leri, proje dosyanızda [Packagereference](../../../project-sdk/msbuild-props.md#packagereference) olmadan kullanırsanız, çalışma zamanı hataları görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9625a-117">If you use APIs from the affected assemblies without having a [PackageReference](../../../project-sdk/msbuild-props.md#packagereference) in your project file, you might see run-time errors.</span></span> <span data-ttu-id="9625a-118">Örneğin, pakete açık bir başvuru eklemeden bu derlemelerden birindeki API 'Lere erişmek için yansıma kullanan bir uygulama, çalışma zamanı hatalarına sahip olur.</span><span class="sxs-lookup"><span data-stu-id="9625a-118">For example, an application that uses reflection to access APIs from one of these assemblies without adding an explicit reference to the package will have run-time errors.</span></span> <span data-ttu-id="9625a-119">, `PackageReference` Derlemelerin uygulama çıktısının bir parçası olarak mevcut olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9625a-119">The `PackageReference` ensures that the assemblies are present as part of the application output.</span></span>

<span data-ttu-id="9625a-120">Tartışma için bkz <https://github.com/dotnet/aspnetcore/issues/31007> ..</span><span class="sxs-lookup"><span data-stu-id="9625a-120">For discussion, see <https://github.com/dotnet/aspnetcore/issues/31007>.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="9625a-121">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="9625a-121">Reason for change</span></span>

<span data-ttu-id="9625a-122">Bu değişiklik, ASP.NET Core paylaşılan çerçevesinin boyutunu azaltmak için sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="9625a-122">This change was introduced to reduce the size of the ASP.NET Core shared framework.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="9625a-123">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="9625a-123">Recommended action</span></span>

<span data-ttu-id="9625a-124">Bu API 'Leri projenizde kullanmaya devam etmek için bir [Packagereference](../../../project-sdk/msbuild-props.md#packagereference)ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9625a-124">To continue using these APIs in your project, add a [PackageReference](../../../project-sdk/msbuild-props.md#packagereference).</span></span> <span data-ttu-id="9625a-125">Örnek:</span><span class="sxs-lookup"><span data-stu-id="9625a-125">For example:</span></span>

```xml
<PackageReference Include="System.Security.Permissions" Version="6.0.0" />
```

## <a name="affected-apis"></a><span data-ttu-id="9625a-126">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="9625a-126">Affected APIs</span></span>

- <xref:System.Security.Permissions?displayProperty=fullName>
- <xref:System.Media?displayProperty=fullName>
- <xref:System.Security.Cryptography.X509Certificates.X509Certificate2UI?displayProperty=fullName>
- <xref:System.Xaml.Permissions.XamlAccessLevel?displayProperty=fullName>

<!--

## Category

ASP.NET Core

## Affected APIs

- `N:System.Security.Permissions`
- `N:System.Media`
- `N:System.Security.Cryptography.X509Certificates.X509Certificate2UI`
- `N:System.Xaml.Permissions.XamlAccessLevel`

-->
