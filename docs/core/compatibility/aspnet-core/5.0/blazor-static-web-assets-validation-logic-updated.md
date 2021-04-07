---
title: 'Son değişiklik: Blazor: statik Web varlıkları için doğrulama mantığı güncelleştirildi'
description: "Blazor başlıklı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: statik Web varlıkları için güncelleştirilmiş doğrulama mantığı"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: b6fb8e9a10157a97119fa07a95fb3dbb8b207214
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498158"
---
# <a name="blazor-updated-validation-logic-for-static-web-assets"></a><span data-ttu-id="bc79b-103">Blazor: Statik web varlıkları için doğrulama mantığı güncelleştirildi</span><span class="sxs-lookup"><span data-stu-id="bc79b-103">Blazor: Updated validation logic for static web assets</span></span>

<span data-ttu-id="bc79b-104">ASP.NET Core 3,1 ve Blazor WebAssembly 3,2 ' de statik Web varlıkları için çakışma doğrulamasında bir sorun oluştu.</span><span class="sxs-lookup"><span data-stu-id="bc79b-104">There was an issue in conflict validation for static web assets in ASP.NET Core 3.1 and Blazor WebAssembly 3.2.</span></span> <span data-ttu-id="bc79b-105">Sorun:</span><span class="sxs-lookup"><span data-stu-id="bc79b-105">The issue:</span></span>

* <span data-ttu-id="bc79b-106">Razor sınıf kitaplıkları (RCLs) ve Blazor WebAssembly uygulamalarından gelen konak varlıkları ve varlıklar arasında doğru çakışma algılamayı engelledi.</span><span class="sxs-lookup"><span data-stu-id="bc79b-106">Prevented proper conflict detection between the host assets and assets from Razor Class Libraries (RCLs) and Blazor WebAssembly apps.</span></span>
* <span data-ttu-id="bc79b-107">, Varsayılan olarak, RCLs içindeki statik web varlıklarının ön ek kapsamında sunulduğundan, genellikle Blazor WebAssembly uygulamalarını etkiler `_content/$(PackageId)` .</span><span class="sxs-lookup"><span data-stu-id="bc79b-107">Mostly affects Blazor WebAssembly apps, since by default, static web assets in RCLs are served under the `_content/$(PackageId)` prefix.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="bc79b-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="bc79b-108">Version introduced</span></span>

<span data-ttu-id="bc79b-109">5.0</span><span class="sxs-lookup"><span data-stu-id="bc79b-109">5.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="bc79b-110">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="bc79b-110">Old behavior</span></span>

<span data-ttu-id="bc79b-111">Geliştirme sırasında, bir RCL 'nin statik web varlıklarının aynı konak yolu ana bilgisayar proje varlıkları ile sessizce geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="bc79b-111">During development, an RCL's static web assets could be silently overridden with host project assets on the same host path.</span></span> <span data-ttu-id="bc79b-112">*/Folder/file.txt* adresinden sunulacak statik bir web varlığı tanımlamış bir RCL düşünün.</span><span class="sxs-lookup"><span data-stu-id="bc79b-112">Consider an RCL that has defined a static web asset to be served at */folder/file.txt*.</span></span> <span data-ttu-id="bc79b-113">Ana bilgisayar *Wwwroot/klasör/file.txt*' a bir dosya yerleştirirse, sunucudaki dosya, RCL veya Blazor WebAssembly uygulamasındaki dosyayı sessizce yok kılar.</span><span class="sxs-lookup"><span data-stu-id="bc79b-113">If the host placed a file at *wwwroot/folder/file.txt*, the file on the server silently overrode the file on the RCL or Blazor WebAssembly app.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="bc79b-114">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="bc79b-114">New behavior</span></span>

<span data-ttu-id="bc79b-115">ASP.NET Core, bu sorunun ne zaman gerçekleştiğini doğru şekilde algılar.</span><span class="sxs-lookup"><span data-stu-id="bc79b-115">ASP.NET Core correctly detects when this issue happens.</span></span> <span data-ttu-id="bc79b-116">İlgili eylemi gerçekleştirebileceğiniz için, çakışmayı kullanıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="bc79b-116">It informs you, the user, of the conflict so that you can take the appropriate action.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="bc79b-117">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="bc79b-117">Reason for change</span></span>

<span data-ttu-id="bc79b-118">Statik web varlıklarının, projenin *Wwwroot* ana bilgisayarındaki dosyalar tarafından geçersiz kılınabilir olması amaçlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="bc79b-118">Static web assets weren't intended to be overridable by files on the *wwwroot* host of the project.</span></span> <span data-ttu-id="bc79b-119">Bu dosyaların geçersiz kılınmasına izin verilmesi, tanılanması zor hatalara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="bc79b-119">Allowing for the overriding of those files could lead to errors that are difficult to diagnose.</span></span> <span data-ttu-id="bc79b-120">Sonuç, yayımlanan uygulamalarda tanımsız davranış değişiklikleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="bc79b-120">The result could be undefined behavior changes in published apps.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="bc79b-121">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="bc79b-121">Recommended action</span></span>

<span data-ttu-id="bc79b-122">Varsayılan olarak, bir RCL dosyasının konaktaki bir dosyayla çakışmasının nedeni yoktur.</span><span class="sxs-lookup"><span data-stu-id="bc79b-122">By default, there's no reason for an RCL file to conflict with a file on the host.</span></span> <span data-ttu-id="bc79b-123">RCL dosyaları ön ekine sahiptir `_content/${PackageId}` .</span><span class="sxs-lookup"><span data-stu-id="bc79b-123">RCL files are prefixed with `_content/${PackageId}`.</span></span> <span data-ttu-id="bc79b-124">Blazor WebAssembly dosyaları, çakışma daha kolay hale getiren ana bilgisayar URL 'SI alanının köküne yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="bc79b-124">Blazor WebAssembly files are placed at the root of the host URL space, which makes conflicts easier.</span></span> <span data-ttu-id="bc79b-125">Örneğin, Blazor WebAssembly Apps, konağın *Wwwroot* klasörüne de dahil olabileceği bir *tercih edilen Icon. ico* dosyası içerir.</span><span class="sxs-lookup"><span data-stu-id="bc79b-125">For example, Blazor WebAssembly apps contain a *favicon.ico* file that the host might also include in its *wwwroot* folder.</span></span>

<span data-ttu-id="bc79b-126">Çakışmanın kaynağı bir RCL dosyası ise, genellikle kodun varlıkları kitaplıktan projenin *Wwwroot* klasörüne kopyalandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bc79b-126">If the conflict's source is an RCL file, it often means code is copying assets from the library into the project's *wwwroot* folder.</span></span> <span data-ttu-id="bc79b-127">Dosyaları kopyalamak için kod yazma, statik web varlıklarının birincil hedefini erteler.</span><span class="sxs-lookup"><span data-stu-id="bc79b-127">Writing code to copy files defeats a primary goal of static web assets.</span></span> <span data-ttu-id="bc79b-128">Bu hedef, içerik yeni bir derleme tetiklemeye gerek kalmadan güncelleştirildiğinde tarayıcıda güncelleştirmeleri almak için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="bc79b-128">This goal is fundamental to get updates on the browser when the contents are updated without having to trigger a new compilation.</span></span>

<span data-ttu-id="bc79b-129">Bu davranışı korumayı ve dosyayı konakta korumayı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc79b-129">You may choose to preserve this behavior and maintain the file on the host.</span></span> <span data-ttu-id="bc79b-130">Bunu yapmak için, dosyayı özel bir MSBuild hedefi olan statik Web varlıkları listesinden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="bc79b-130">To do so, remove the file from the list of static web assets with a custom MSBuild target.</span></span>

<span data-ttu-id="bc79b-131">Ana bilgisayar projesinin dosyası yerine RCL 'nin dosyasını veya Blazor WebAssembly uygulamasının dosyasını kullanmak için, dosyayı konak projesinden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="bc79b-131">To use the RCL's file or the Blazor WebAssembly app's file instead of the host project's file, remove the file from the host project.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="bc79b-132">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="bc79b-132">Affected APIs</span></span>

<span data-ttu-id="bc79b-133">Yok</span><span class="sxs-lookup"><span data-stu-id="bc79b-133">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
