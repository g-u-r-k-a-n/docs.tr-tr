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
ms.openlocfilehash: b4432e7a137720216e7c0941b3384ce7ad7049e9
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970921"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a>.NET 'te JSON serileştirme ve seri durumundan çıkarma (sıralama ve kaldırma)-genel bakış

`System.Text.Json`Ad alanı, JavaScript nesne gösterimi (JSON) öğesinden serileştirmek ve seri durumdan çıkarmak için işlevsellik sağlar.

Kitaplık tasarımı, kapsamlı bir özellik kümesi üzerinden yüksek performans ve düşük bellek ayırmayı vurgular. Yerleşik UTF-8 desteği, UTF-8 olarak kodlanmış JSON metnini okuma ve yazma sürecini en iyi duruma getirir. Bu, Web ve disk üzerindeki dosyalardaki veriler için en yaygın kodlama olur.

Kitaplık Ayrıca, bellek içi belge nesne modeli (DOM) ile çalışmak için sınıflar sağlar. Bu özellik bir JSON dosyası veya dizesindeki öğelerin rastgele salt okunurdur erişimine izin vermez.

## <a name="how-to-get-the-library"></a>Kitaplığı alma

* Kitaplık, .NET Core 3,0 ve üzeri sürümler için paylaşılan Framework 'ün bir parçası olarak yerleşik olarak bulunur.
* Önceki Framework sürümleri için [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet paketini yüklersiniz. Paket şunları destekler:

  * .NET Standard 2,0 ve sonraki sürümler
  * .NET Framework 4.7.2 ve sonraki sürümler
  * .NET Core 2,0, 2,1 ve 2,2

## <a name="additional-resources"></a>Ek kaynaklar

* [Kitaplığı kullanma](system-text-json-how-to.md)
* [JsonSerializerOptions örneklerinin örneğini oluşturma](system-text-json-configure-options.md)
* [Büyük/küçük harf duyarlı eşlemeyi etkinleştirme](system-text-json-character-casing.md)
* [Özellik adlarını ve değerlerini özelleştirme](system-text-json-customize-properties.md)
* [Özellikleri yoksayma](system-text-json-ignore-properties.md)
* [Geçersiz JSON’a izin verme](system-text-json-invalid-json.md)
* [Sap taşması JSON’ı](system-text-json-handle-overflow.md)
* [Başvuruları koruma](system-text-json-preserve-references.md)
* [Sabit türler ve genel olmayan erişimciler](system-text-json-immutability.md)
* [Polimorfik serileştirme](system-text-json-polymorphism.md)
* [' Den ' a geçiş Newtonsoft.JsonSystem.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [Karakter kodlamasını özelleştirme](system-text-json-character-encoding.md)
* [Özel serileştiriciler ve seri hale getiriciler yazma](write-custom-serializer-deserializer.md)
* [JSON serileştirme için özel dönüştürücüler yazma](system-text-json-converters-how-to.md)
* [DateTime ve DateTimeOffset desteği](../datetime/system-text-json-support.md)
* [İçinde desteklenen koleksiyon türleri System.Text.Json](system-text-json-supported-collection-types.md)
* [System.Text.Json API başvurusu](xref:System.Text.Json)
* [System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)
