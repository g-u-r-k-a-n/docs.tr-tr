---
title: "Son değişiklik: MVC: ObjectModelValidator, ValidationVisitor 'un yeni bir aşırı yüklemesini çağırır. doğrulama"
description: "ASP.NET Core 5,0 ' deki Son değişiklik hakkında MVC hakkında bilgi edinin: ObjectModelValidator, ValidationVisitor 'un yeni bir aşırı yüklemesini çağırır. doğrula"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 7bf07360f5d5e93641b7fbc6634fda2e9f3e649f
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497599"
---
# <a name="mvc-objectmodelvalidator-calls-a-new-overload-of-validationvisitorvalidate"></a><span data-ttu-id="31737-103">MVC: ObjectModelValidator, ValidationVisitor 'un yeni bir aşırı yüklemesini çağırır. doğrulama</span><span class="sxs-lookup"><span data-stu-id="31737-103">MVC: ObjectModelValidator calls a new overload of ValidationVisitor.Validate</span></span>

<span data-ttu-id="31737-104">ASP.NET Core 5,0 ' de, öğesinin aşırı yüklemesi <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType> eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="31737-104">In ASP.NET Core 5.0, an overload of the <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType> was added.</span></span> <span data-ttu-id="31737-105">Yeni aşırı yükleme, özellikleri içeren en üst düzey model örneğini kabul eder:</span><span class="sxs-lookup"><span data-stu-id="31737-105">The new overload accepts the top-level model instance that contains properties:</span></span>

```diff
  bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel);
+ bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container);
```

<span data-ttu-id="31737-106"><xref:Microsoft.AspNetCore.Mvc.ModelBinding.ObjectModelValidator> doğrulamayı gerçekleştirmek için bu yeni aşırı yüklemesini çağırır `ValidationVisitor` .</span><span class="sxs-lookup"><span data-stu-id="31737-106"><xref:Microsoft.AspNetCore.Mvc.ModelBinding.ObjectModelValidator> invokes this new overload of `ValidationVisitor` to perform validation.</span></span> <span data-ttu-id="31737-107">Doğrulama kitaplığınız ASP.NET Core MVC 'nin model doğrulama sistemiyle tümleştirirse, bu yeni aşırı yükleme ilgili olur.</span><span class="sxs-lookup"><span data-stu-id="31737-107">This new overload is pertinent if your validation library integrates with ASP.NET Core MVC's model validation system.</span></span>

<span data-ttu-id="31737-108">Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 26020](https://github.com/dotnet/aspnetcore/issues/26020).</span><span class="sxs-lookup"><span data-stu-id="31737-108">For discussion, see GitHub issue [dotnet/aspnetcore#26020](https://github.com/dotnet/aspnetcore/issues/26020).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="31737-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="31737-109">Version introduced</span></span>

<span data-ttu-id="31737-110">5.0</span><span class="sxs-lookup"><span data-stu-id="31737-110">5.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="31737-111">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="31737-111">Old behavior</span></span>

<span data-ttu-id="31737-112">`ObjectModelValidator` Model doğrulaması sırasında aşağıdaki aşırı yüklemeyi çağırır:</span><span class="sxs-lookup"><span data-stu-id="31737-112">`ObjectModelValidator` invokes the following overload during model validation:</span></span>

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel)
```

## <a name="new-behavior"></a><span data-ttu-id="31737-113">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="31737-113">New behavior</span></span>

<span data-ttu-id="31737-114">`ObjectModelValidator` Model doğrulaması sırasında aşağıdaki aşırı yüklemeyi çağırır:</span><span class="sxs-lookup"><span data-stu-id="31737-114">`ObjectModelValidator` invokes the following overload during model validation:</span></span>

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
```

## <a name="reason-for-change"></a><span data-ttu-id="31737-115">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="31737-115">Reason for change</span></span>

<span data-ttu-id="31737-116">Bu değişiklik, diğer özelliklerin denetimine bağlı olan gibi Doğrulayıcıları desteklemek için sunulmuştur <xref:System.ComponentModel.DataAnnotations.CompareAttribute> .</span><span class="sxs-lookup"><span data-stu-id="31737-116">This change was introduced to support validators, such as <xref:System.ComponentModel.DataAnnotations.CompareAttribute>, that rely on inspection of other properties.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="31737-117">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="31737-117">Recommended action</span></span>

<span data-ttu-id="31737-118">`ObjectModelValidator`Var olan aşırı yüklemesini çağırmak için kullanan doğrulama çerçeveleri, `ValidationVisitor` .NET 5,0 veya üstünü hedeflerken yeni yöntemi geçersiz kılmalıdır:</span><span class="sxs-lookup"><span data-stu-id="31737-118">Validation frameworks that rely on `ObjectModelValidator` to invoke the existing overload of `ValidationVisitor` must override the new method when targeting .NET 5.0 or later:</span></span>

```csharp
public class MyCustomValidationVisitor : ValidationVisitor
{
+  public override bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
+  {
+    ...
}
```

## <a name="affected-apis"></a><span data-ttu-id="31737-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="31737-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`Overload:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate`

-->
