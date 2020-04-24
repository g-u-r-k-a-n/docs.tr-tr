---
title: Temel sınıf kitaplığı bölünmesi değişiklikleri
description: Çekirdek .NET kitaplıklarında son değişiklikleri listeler.
ms.date: 09/20/2019
ms.openlocfilehash: 841003fdb114042466cc15b4846e133cf37de85c
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135652"
---
# <a name="core-net-libraries-breaking-changes"></a>Çekirdek .NET kitaplıklarının parçalara bölünmesi

Çekirdek .NET kitaplıkları, .NET Core tarafından kullanılan temel ve diğer genel türleri sağlar.

Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:

| Son değişiklik | Sunulan sürüm |
| - | :-: |
| [Sürümü şimdi rapor eden API 'Ler rapor ürünü ve dosya sürümü değil](#apis-that-report-version-now-report-product-and-not-file-version) | 3,0 |
| [Özel EncoderFallbackBuffer örnekleri özyinelemeli olarak geri dönemez](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | 3,0 |
| [Kayan nokta biçimlendirme ve ayrıştırma davranışı değişiklikleri](#floating-point-formatting-and-parsing-behavior-changed) | 3,0 |
| [Kayan nokta ayrıştırma işlemleri artık başarısız olmaz veya bir OverflowException oluşturmaz](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | 3,0 |
| [InvalidAsynchronousStateException başka bir derlemeye taşındı](#invalidasynchronousstateexception-moved-to-another-assembly) | 3,0 |
| [NET Core 3,0 hatalı biçimlendirilmiş UTF-8 bayt dizilerini değiştirirken Unicode en iyi yöntemlerini izler](#net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences) | 3,0 |
| [TypeDescriptionProviderAttribute başka bir derlemeye taşındı](#typedescriptionproviderattribute-moved-to-another-assembly) | 3,0 |
| [ZipArchiveEntry artık tutarsız giriş boyutlarına sahip arşivleri işliyor](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | 3,0 |
| [JsonException iken NotSupportedException olarak değiştirilen JSON seri hale getirici özel durum türü](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | 3,0 |
| [Utf8JsonWriter içinde (String) null semantiğinin değiştirilmesi](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | 3,0 |
| [JsonEncodedText. Encode yöntemlerinde ek bir JavaScriptEncoder bağımsız değişkeni vardır](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | 3,0 |
| [JsonFactoryConverter. CreateConverter imzası değişti](#jsonfactoryconvertercreateconverter-signature-changed) | 3,0 |
| [JsonElement API değişiklikleri](#jsonelement-api-changes) | 3,0 |
| [FieldInfo. SetValue statik, yalnızca init alanları için özel durum oluşturur](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | 3,0 |
| [Yerleşik yapı türlerine eklenen özel alanlar](#private-fields-added-to-built-in-struct-types) | 2.1 |
| [UseShellExecute varsayılan değerindeki değişiklik](#change-in-default-value-of-useshellexecute) | 2.1 |
| [MacOS üzerinde OpenSSL sürümleri](#openssl-versions-on-macos) | 2.1 |
| [Fılesystemınfo. Attributes tarafından oluşturulan UnauthorizedAccessException](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | 1.0 |
| [Bozuk işlem durumu özel durumlarını işleme desteklenmiyor](#handling-corrupted-state-exceptions-is-not-supported) | 1.0 |

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

***

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

***

[!INCLUDE[JSON serializer exception type changed from JsonException to NotSupportedException](~/includes/core-changes/corefx/3.0/serializer-throws-notsupportedexception.md)]

***

[!INCLUDE[Change in semantics of (string)null in Utf8JsonWriter](~/includes/core-changes/corefx/3.0/change-in-null-in-utf8jsonwriter.md)]

***

[!INCLUDE[JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument](~/includes/core-changes/corefx/3.0/jsonencodedtext-encode-has-additional-argument.md)]

***

[!INCLUDE[JsonFactoryConverter.CreateConverter signature changed](~/includes/core-changes/corefx/3.0/jsonfactoryconverter-createconverter.md)]

***

[!INCLUDE[JsonElement API changes](~/includes/core-changes/corefx/3.0/jsonelement-api-changes.md)]

***

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

***

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a>.NET Core 1,0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***
