---
title: Genelleştirme yapılandırma ayarları
description: .NET Core uygulamasının Genelleştirme yönlerini yapılandıran çalışma zamanı ayarları hakkında bilgi edinin. Örneğin, Japonca tarihleri nasıl ayrıştırır.
ms.date: 05/18/2020
ms.topic: reference
ms.openlocfilehash: e8179a7e1421a3ff0ceacf07a2843c1b77af6143
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873555"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="0efbb-103">Genelleştirme için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="0efbb-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="0efbb-104">Sabit mod</span><span class="sxs-lookup"><span data-stu-id="0efbb-104">Invariant mode</span></span>

- <span data-ttu-id="0efbb-105">.NET Core uygulamasının kültüre özgü verilere ve davranışa erişim olmadan Genelleştirme sabit modunda çalışıp çalışmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="0efbb-105">Determines whether a .NET Core app runs in globalization-invariant mode without access to culture-specific data and behavior.</span></span>
- <span data-ttu-id="0efbb-106">Bu ayarı atlarsanız, uygulama kültürel verilerine erişimle çalışır.</span><span class="sxs-lookup"><span data-stu-id="0efbb-106">If you omit this setting, the app runs with access to cultural data.</span></span> <span data-ttu-id="0efbb-107">Bu değeri değerine ayarlamaya eşdeğerdir `false` .</span><span class="sxs-lookup"><span data-stu-id="0efbb-107">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="0efbb-108">Daha fazla bilgi için bkz. [.NET Core Genelleştirme sabit modu](https://github.com/dotnet/runtime/blob/main/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="0efbb-108">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/main/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="0efbb-109">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="0efbb-109">Setting name</span></span> | <span data-ttu-id="0efbb-110">Değerler</span><span class="sxs-lookup"><span data-stu-id="0efbb-110">Values</span></span> |
| - | - | - |
| <span data-ttu-id="0efbb-111">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="0efbb-111">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="0efbb-112">`false` -kültürel verilerine erişim</span><span class="sxs-lookup"><span data-stu-id="0efbb-112">`false` - access to cultural data</span></span><br/><span data-ttu-id="0efbb-113">`true` -Sabit modda çalıştır</span><span class="sxs-lookup"><span data-stu-id="0efbb-113">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="0efbb-114">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="0efbb-114">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="0efbb-115">`false` -kültürel verilerine erişim</span><span class="sxs-lookup"><span data-stu-id="0efbb-115">`false` - access to cultural data</span></span><br/><span data-ttu-id="0efbb-116">`true` -Sabit modda çalıştır</span><span class="sxs-lookup"><span data-stu-id="0efbb-116">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="0efbb-117">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="0efbb-117">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="0efbb-118">`0` -kültürel verilerine erişim</span><span class="sxs-lookup"><span data-stu-id="0efbb-118">`0` - access to cultural data</span></span><br/><span data-ttu-id="0efbb-119">`1` -Sabit modda çalıştır</span><span class="sxs-lookup"><span data-stu-id="0efbb-119">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="0efbb-120">Örnekler</span><span class="sxs-lookup"><span data-stu-id="0efbb-120">Examples</span></span>

<span data-ttu-id="0efbb-121">*runtimeconfig.js* dosya:</span><span class="sxs-lookup"><span data-stu-id="0efbb-121">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="0efbb-122">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="0efbb-122">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="0efbb-123">Dönem yıl aralıkları</span><span class="sxs-lookup"><span data-stu-id="0efbb-123">Era year ranges</span></span>

- <span data-ttu-id="0efbb-124">Birden çok dönemi destekleyen takvimler için Aralık denetimlerinin gevşek olduğunu veya bir dönem tarih aralığını taşan tarihlerin bir oluşturma yapıp olmadığını belirler <xref:System.ArgumentOutOfRangeException> .</span><span class="sxs-lookup"><span data-stu-id="0efbb-124">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="0efbb-125">Bu ayarı atlarsanız, Aralık denetimleri gevşek bir şekilde yapılır.</span><span class="sxs-lookup"><span data-stu-id="0efbb-125">If you omit this setting, range checks are relaxed.</span></span> <span data-ttu-id="0efbb-126">Bu değeri değerine ayarlamaya eşdeğerdir `false` .</span><span class="sxs-lookup"><span data-stu-id="0efbb-126">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="0efbb-127">Daha fazla bilgi için bkz. [takvimler, eras ve tarih aralıkları: gevşek Aralık denetimleri](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="0efbb-127">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="0efbb-128">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="0efbb-128">Setting name</span></span> | <span data-ttu-id="0efbb-129">Değerler</span><span class="sxs-lookup"><span data-stu-id="0efbb-129">Values</span></span> |
| - | - | - |
| <span data-ttu-id="0efbb-130">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="0efbb-130">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="0efbb-131">`false` -gevşek Aralık denetimleri</span><span class="sxs-lookup"><span data-stu-id="0efbb-131">`false` - relaxed range checks</span></span><br/><span data-ttu-id="0efbb-132">`true` -bir özel duruma neden olan taşmalar</span><span class="sxs-lookup"><span data-stu-id="0efbb-132">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="0efbb-133">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="0efbb-133">**Environment variable**</span></span> | <span data-ttu-id="0efbb-134">Yok</span><span class="sxs-lookup"><span data-stu-id="0efbb-134">N/A</span></span> | <span data-ttu-id="0efbb-135">Yok</span><span class="sxs-lookup"><span data-stu-id="0efbb-135">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="0efbb-136">Japonca Tarih ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="0efbb-136">Japanese date parsing</span></span>

- <span data-ttu-id="0efbb-137">Yıl olarak "1" veya "gannen" içeren bir dizenin başarıyla ayrıştıranıp desteklenmediğini veya yalnızca "1" desteklenip desteklenmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="0efbb-137">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="0efbb-138">Bu ayarı atlarsanız, yıl için "1" veya "gannen" içeren dizeler başarıyla ayrıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="0efbb-138">If you omit this setting, strings that contain either "1" or "Gannen" as the year parse successfully.</span></span> <span data-ttu-id="0efbb-139">Bu değeri değerine ayarlamaya eşdeğerdir `false` .</span><span class="sxs-lookup"><span data-stu-id="0efbb-139">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="0efbb-140">Daha fazla bilgi için bkz. [birden çok dönemi ile takvimlerdeki tarihleri temsil](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)etme.</span><span class="sxs-lookup"><span data-stu-id="0efbb-140">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="0efbb-141">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="0efbb-141">Setting name</span></span> | <span data-ttu-id="0efbb-142">Değerler</span><span class="sxs-lookup"><span data-stu-id="0efbb-142">Values</span></span> |
| - | - | - |
| <span data-ttu-id="0efbb-143">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="0efbb-143">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="0efbb-144">`false` -"Gannen" veya "1" destekleniyor</span><span class="sxs-lookup"><span data-stu-id="0efbb-144">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="0efbb-145">`true` -yalnızca "1" destekleniyor</span><span class="sxs-lookup"><span data-stu-id="0efbb-145">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="0efbb-146">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="0efbb-146">**Environment variable**</span></span> | <span data-ttu-id="0efbb-147">Yok</span><span class="sxs-lookup"><span data-stu-id="0efbb-147">N/A</span></span> | <span data-ttu-id="0efbb-148">Yok</span><span class="sxs-lookup"><span data-stu-id="0efbb-148">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="0efbb-149">Japon yıl biçimi</span><span class="sxs-lookup"><span data-stu-id="0efbb-149">Japanese year format</span></span>

- <span data-ttu-id="0efbb-150">Japonca takvim çağının ilk yılının "gannen" olarak mı yoksa sayı olarak mı biçimlendirildiğini belirler.</span><span class="sxs-lookup"><span data-stu-id="0efbb-150">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="0efbb-151">Bu ayarı atlarsanız, ilk yıl "gannen" olarak biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="0efbb-151">If you omit this setting, the first year is formatted as "Gannen".</span></span> <span data-ttu-id="0efbb-152">Bu değeri değerine ayarlamaya eşdeğerdir `false` .</span><span class="sxs-lookup"><span data-stu-id="0efbb-152">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="0efbb-153">Daha fazla bilgi için bkz. [birden çok dönemi ile takvimlerdeki tarihleri temsil](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)etme.</span><span class="sxs-lookup"><span data-stu-id="0efbb-153">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="0efbb-154">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="0efbb-154">Setting name</span></span> | <span data-ttu-id="0efbb-155">Değerler</span><span class="sxs-lookup"><span data-stu-id="0efbb-155">Values</span></span> |
| - | - | - |
| <span data-ttu-id="0efbb-156">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="0efbb-156">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="0efbb-157">`false` "gannen" olarak biçimlendirin</span><span class="sxs-lookup"><span data-stu-id="0efbb-157">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="0efbb-158">`true` -sayı olarak Biçimlendir</span><span class="sxs-lookup"><span data-stu-id="0efbb-158">`true` - format as number</span></span> |
| <span data-ttu-id="0efbb-159">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="0efbb-159">**Environment variable**</span></span> | <span data-ttu-id="0efbb-160">Yok</span><span class="sxs-lookup"><span data-stu-id="0efbb-160">N/A</span></span> | <span data-ttu-id="0efbb-161">Yok</span><span class="sxs-lookup"><span data-stu-id="0efbb-161">N/A</span></span> |

## <a name="nls"></a><span data-ttu-id="0efbb-162">NLS</span><span class="sxs-lookup"><span data-stu-id="0efbb-162">NLS</span></span>

- <span data-ttu-id="0efbb-163">.NET 'in, Windows uygulamaları için, Unicode (ıCU) genelleştirme API 'Leri için ulusal dil desteği (NLS) veya uluslararası bileşenleri kullanıp kullanmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="0efbb-163">Determines whether .NET uses National Language Support (NLS) or International Components for Unicode (ICU) globalization APIs for Windows apps.</span></span> <span data-ttu-id="0efbb-164">.NET 5,0 ve sonraki sürümleri, Windows 10 Mayıs 2019 güncelleştirme ve sonraki sürümlerinde ıCU genelleştirme API 'Lerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0efbb-164">.NET 5.0 and later versions use ICU globalization APIs by default on Windows 10 May 2019 Update and later versions.</span></span>
- <span data-ttu-id="0efbb-165">Bu ayarı atlarsanız, .NET varsayılan olarak ıCU genelleştirme API 'Lerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0efbb-165">If you omit this setting, .NET uses ICU globalization APIs by default.</span></span> <span data-ttu-id="0efbb-166">Bu değeri değerine ayarlamaya eşdeğerdir `false` .</span><span class="sxs-lookup"><span data-stu-id="0efbb-166">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="0efbb-167">Daha fazla bilgi için bkz. [genelleştirme API 'Leri Windows üzerinde IU kitaplıklarını kullanma](../compatibility/globalization/5.0/icu-globalization-api.md).</span><span class="sxs-lookup"><span data-stu-id="0efbb-167">For more information, see [Globalization APIs use ICU libraries on Windows](../compatibility/globalization/5.0/icu-globalization-api.md).</span></span>

| | <span data-ttu-id="0efbb-168">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="0efbb-168">Setting name</span></span> | <span data-ttu-id="0efbb-169">Değerler</span><span class="sxs-lookup"><span data-stu-id="0efbb-169">Values</span></span> | <span data-ttu-id="0efbb-170">Sunulan özellikler</span><span class="sxs-lookup"><span data-stu-id="0efbb-170">Introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="0efbb-171">**Üzerinderuntimeconfig.js**</span><span class="sxs-lookup"><span data-stu-id="0efbb-171">**runtimeconfig.json**</span></span> | `System.Globalization.UseNls` | <span data-ttu-id="0efbb-172">`false` -ICU genelleştirme API 'Lerini kullanma</span><span class="sxs-lookup"><span data-stu-id="0efbb-172">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="0efbb-173">`true` -NLS genelleştirme API 'Lerini kullanma</span><span class="sxs-lookup"><span data-stu-id="0efbb-173">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="0efbb-174">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="0efbb-174">.NET 5.0</span></span> |
| <span data-ttu-id="0efbb-175">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="0efbb-175">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_USENLS` | <span data-ttu-id="0efbb-176">`false` -ICU genelleştirme API 'Lerini kullanma</span><span class="sxs-lookup"><span data-stu-id="0efbb-176">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="0efbb-177">`true` -NLS genelleştirme API 'Lerini kullanma</span><span class="sxs-lookup"><span data-stu-id="0efbb-177">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="0efbb-178">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="0efbb-178">.NET 5.0</span></span> |
