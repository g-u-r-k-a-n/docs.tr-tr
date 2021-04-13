---
title: C#-.NET kullanarak JSON serisini serileştirme ve serisini kaldırma
description: Bu genel bakışta, System.Text.Json .net 'TEKI JSON 'a serileştirmek ve seri durumdan çıkarmak için ad alanı işlevselliği açıklanmaktadır.
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 9a57319dc1d744bfc06cc7360ffcb59b24fe3646
ms.sourcegitcommit: fdfa01f6cd3aa4c36b6e8a1830693ff22d35aeea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107292268"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a><span data-ttu-id="57ef7-103">.NET 'te JSON serileştirme ve seri durumundan çıkarma (sıralama ve kaldırma)-genel bakış</span><span class="sxs-lookup"><span data-stu-id="57ef7-103">JSON serialization and deserialization (marshalling and unmarshalling) in .NET - overview</span></span>

<span data-ttu-id="57ef7-104">`System.Text.Json`Ad alanı, JavaScript nesne gösterimi (JSON) öğesinden serileştirmek ve seri durumdan çıkarmak için işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="57ef7-104">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="57ef7-105">Kitaplık tasarımı, kapsamlı bir özellik kümesi üzerinden yüksek performans ve düşük bellek ayırmayı vurgular.</span><span class="sxs-lookup"><span data-stu-id="57ef7-105">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="57ef7-106">Yerleşik UTF-8 desteği, UTF-8 olarak kodlanmış JSON metnini okuma ve yazma sürecini en iyi duruma getirir. Bu, Web ve disk üzerindeki dosyalardaki veriler için en yaygın kodlama olur.</span><span class="sxs-lookup"><span data-stu-id="57ef7-106">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="57ef7-107">Kitaplık Ayrıca, bellek içi belge nesne modeli (DOM) ile çalışmak için sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="57ef7-107">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="57ef7-108">Bu özellik bir JSON dosyası veya dizesindeki öğelerin rastgele salt okunurdur erişimine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="57ef7-108">This feature enables random read-only access of the elements in a JSON file or string.</span></span>

<span data-ttu-id="57ef7-109">Kitaplığın Visual Basic koddan kullanabileceğiniz bölümlerine ilişkin bazı sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="57ef7-109">There are some limitations on what parts of the library that you can use from Visual Basic code.</span></span> <span data-ttu-id="57ef7-110">Daha fazla bilgi için bkz. [Visual Basic desteği](system-text-json-how-to.md#visual-basic-support).</span><span class="sxs-lookup"><span data-stu-id="57ef7-110">For more information, see [Visual Basic support](system-text-json-how-to.md#visual-basic-support).</span></span>

## <a name="how-to-get-the-library"></a><span data-ttu-id="57ef7-111">Kitaplığı alma</span><span class="sxs-lookup"><span data-stu-id="57ef7-111">How to get the library</span></span>

* <span data-ttu-id="57ef7-112">Kitaplık, .NET Core 3,0 ve üzeri sürümler için paylaşılan Framework 'ün bir parçası olarak yerleşik olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="57ef7-112">The library is built-in as part of the shared framework for .NET Core 3.0 and later versions.</span></span>
* <span data-ttu-id="57ef7-113">Önceki Framework sürümleri için [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet paketini yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="57ef7-113">For earlier framework versions, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="57ef7-114">Paket şunları destekler:</span><span class="sxs-lookup"><span data-stu-id="57ef7-114">The package supports:</span></span>

  * <span data-ttu-id="57ef7-115">.NET Standard 2,0 ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="57ef7-115">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="57ef7-116">.NET Framework 4.7.2 ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="57ef7-116">.NET Framework 4.7.2 and later versions</span></span>
  * <span data-ttu-id="57ef7-117">.NET Core 2,0, 2,1 ve 2,2</span><span class="sxs-lookup"><span data-stu-id="57ef7-117">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="security-information"></a><span data-ttu-id="57ef7-118">Güvenlik bilgileri</span><span class="sxs-lookup"><span data-stu-id="57ef7-118">Security information</span></span>

<span data-ttu-id="57ef7-119">Tasarlarken kabul edilen güvenlik tehditleri <xref:System.Text.Json.JsonSerializer> ve nasıl hafiflebilecekleri hakkında bilgi için bkz. [ `System.Text.Json` Threat model](https://github.com/dotnet/runtime/blob/main/src/libraries/System.Text.Json/docs/ThreatModel.md).</span><span class="sxs-lookup"><span data-stu-id="57ef7-119">For information about security threats that were considered when designing <xref:System.Text.Json.JsonSerializer>, and how they can be mitigated, see [`System.Text.Json` Threat Model](https://github.com/dotnet/runtime/blob/main/src/libraries/System.Text.Json/docs/ThreatModel.md).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="57ef7-120">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="57ef7-120">Additional resources</span></span>

* [<span data-ttu-id="57ef7-121">Kitaplığı kullanma</span><span class="sxs-lookup"><span data-stu-id="57ef7-121">How to use the library</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="57ef7-122">JsonSerializerOptions örneklerinin örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="57ef7-122">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="57ef7-123">Büyük/küçük harf duyarlı eşlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="57ef7-123">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="57ef7-124">Özellik adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="57ef7-124">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="57ef7-125">Özellikleri yoksayma</span><span class="sxs-lookup"><span data-stu-id="57ef7-125">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="57ef7-126">Geçersiz JSON’a izin verme</span><span class="sxs-lookup"><span data-stu-id="57ef7-126">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="57ef7-127">Sap taşması JSON’ı</span><span class="sxs-lookup"><span data-stu-id="57ef7-127">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="57ef7-128">Başvuruları koruma</span><span class="sxs-lookup"><span data-stu-id="57ef7-128">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="57ef7-129">Sabit türler ve genel olmayan erişimciler</span><span class="sxs-lookup"><span data-stu-id="57ef7-129">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="57ef7-130">Polimorfik serileştirme</span><span class="sxs-lookup"><span data-stu-id="57ef7-130">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="57ef7-131">' Den ' a geçiş Newtonsoft.JsonSystem.Text.Json</span><span class="sxs-lookup"><span data-stu-id="57ef7-131">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="57ef7-132">Karakter kodlamasını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="57ef7-132">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="57ef7-133">Özel serileştiriciler ve seri hale getiriciler yazma</span><span class="sxs-lookup"><span data-stu-id="57ef7-133">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="57ef7-134">JSON serileştirme için özel dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="57ef7-134">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="57ef7-135">DateTime ve DateTimeOffset desteği</span><span class="sxs-lookup"><span data-stu-id="57ef7-135">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* [<span data-ttu-id="57ef7-136">İçinde desteklenen koleksiyon türleri System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="57ef7-136">Supported collection types in System.Text.Json</span></span>](system-text-json-supported-collection-types.md)
* <span data-ttu-id="57ef7-137">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="57ef7-137">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="57ef7-138">[System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="57ef7-138">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
