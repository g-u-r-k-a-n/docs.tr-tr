---
title: Şifreleme son değişiklikleri
description: .NET Core ile ilgili şifrelemeye ilişkin önemli değişiklikleri listeler.
ms.date: 04/22/2020
ms.openlocfilehash: f7d580938fb7620728b8ff7f67412c9f5bbbb6c3
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558015"
---
# <a name="cryptography-breaking-changes"></a>Şifreleme son değişiklikleri

Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:

| Son değişiklik | Sunulan sürüm |
| - | :-: |
| [System. Security. Cryptography. OID yalnızca işlev olarak init](#systemsecuritycryptographyoid-is-functionally-init-only) | 5.0 |
| [Linux 'ta artık desteklenmeyen GÜVENILEN SERTIFIKA sözdizimini Başlat](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | 3,0 |
| [EnvelopedCms varsayılan değer AES-256 şifrelemesi](#envelopedcms-defaults-to-aes-256-encryption) | 3,0 |
| [RSAOpenSsl anahtar üretimi için en düşük boyut arttı](#minimum-size-for-rsaopenssl-key-generation-has-increased) | 3,0 |
| [.NET Core 3,0 OpenSSL 1.1. x ile OpenSSL 1.0. x tercih eder](#net-core-30-prefers-openssl-11x-to-openssl-10x) | 3,0 |
| [SignedCms. ComputeSignature Boolean parametresi dikkate alındı](#boolean-parameter-of-signedcmscomputesignature-is-respected) | 2.1 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [cryptography-oid-init-only](../../../includes/core-changes/cryptography/5.0/cryptography-oid-init-only.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE [begin-trusted-cert-linux](~/includes/core-changes/cryptography/3.0/begin-trusted-cert-linux.md)]

***

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***
