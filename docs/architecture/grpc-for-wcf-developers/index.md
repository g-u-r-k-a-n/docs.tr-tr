---
title: WCF geliştiricileri için ASP.NET Core gRPC-WCF geliştiricileri için gRPC
description: WCF geliştiricileri için ASP.NET Core 5,0 ' de gRPC hizmetleri oluşturmaya giriş
ms.date: 01/06/2021
ms.openlocfilehash: 26cce6bb784c08a5b59623ff5882fcf2fbb9e9ac
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970199"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a>WCF Geliştiricileri için ASP.NET Core gRPC

![kapak resmi](./media/cover.png)

SÜRÜM v 1.0.1-ASP.NET Core 5,0 ' ye güncelleştirildi

Kitap güncelleştirmeleri ve topluluk katkılarına yönelik [changelog](https://aka.ms/grpc-ebook-changelog) 'u inceleyin.

YAYIMLAYAN

Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri

Microsoft Corporation 'ın bir bölümü

One Microsoft Way

Redmond, Washington 98052-6399

Telif hakkı © 2021 Microsoft Corporation

All rights reserved. Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.

Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder. Bu kitapta ifade edilen görünümler, eklentiler ve bilgiler, URL ve diğer Internet Web sitesi başvuruları da dahil olmak üzere bildirimde bulunmaksızın değiştirilebilir.

Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır. Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.

Microsoft ve <https://www.microsoft.com> "ticari markalar" Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.

Docker balina logosu,, izin tarafından kullanılan Docker, Inc. ' in tescilli ticari markasıdır.

Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.

Düzenliyor

> Yeniden **işaretle** -BT Teknik Müdürü- [görsel recode](https://visualrecode.com)
>
> **MDA bu,** teknik yazar

Düzenleyen

> **Maira Wenzel** -SR. Content Developer-Microsoft

## <a name="introduction"></a>Giriş

gRPC, ağa bağlı hizmetler ve dağıtılmış uygulamalar oluşturmaya yönelik modern bir çerçevedir. SOAP 'ın platformlar arası birlikte çalışabilirliğiyle birlikte Windows Communication Foundation (WCF) NetTCP bağlamalarının performansını düşünün. , uygulamalar ve hizmetler arasında yüksek performans, düşük bant genişliğine sahip bir iletişim sağlamak için HTTP/2 ve prototip ileti kodlama protokolü üzerinde gRPC derlemeleri. .NET, Java, Python, Node.js, Go ve C++ gibi popüler programlama dilleri ve platformları genelinde sunucu ve istemci kodu üretimini destekler. ASP.NET Core 5,0 ' de gRPC için birinci sınıf destek sayesinde, .NET Framework 4. x için mevcut gRPC araçları ve kitaplıklarının yanı sıra, kuruluşlarda .NET benimsemek isteyen geliştirme ekiplerine yönelik WCF için çok iyi bir alternatiftir.

## <a name="who-should-use-this-guide"></a>Bu kılavuzu kimler kullanmalıdır?

Bu kılavuz, daha önce WCF kullanan .NET Framework veya .NET üzerinde çalışan geliştiriciler için yazılmıştır ve uygulamalarını .NET Core 3,0 ve sonraki sürümleri için modern bir RPC ortamına geçirmeye yöneliktir. Daha genel olarak, yükseltme yapıyorsanız, .NET 5 ' e yükseltme yapıyorsanız ve yerleşik gRPC araçlarını kullanmak istiyorsanız, bu kılavuz de yararlı olur.

## <a name="how-you-can-use-this-guide"></a>Bu Kılavuzu nasıl kullanabileceğiniz

Bu, ASP.NET Core 5,0 ' de gRPC hizmetlerini, benzer bir platform olarak WCF 'ye belirli bir şekilde oluşturmaya yönelik kısa bir giriş niteliğindedir. GRPC 'nin ilkelerini açıklar, her bir kavramı WCF 'nin eşdeğer özellikleriyle birbirleriyle ilgili olarak, mevcut bir WCF uygulamasının gRPC 'ye geçirilmesi için rehberlik sunar. Ayrıca, WCF ile karşılaşan ve yeni hizmetler oluşturmak üzere gRPC 'yi öğrenmek isteyen geliştiriciler için de yararlıdır. Örnek uygulamaları kendi projeleriniz için bir şablon veya başvuru olarak kullanabilir ve kodu kitap veya örneklerinden kopyalayabilir ve yeniden kullanabilirsiniz.

Bu noktaların ve fırsatların yaygın olarak anlaşılmasına yardımcı olmak için bu kılavuzu ekibinize iletmekten çekinmeyin. Her birinin ortak bir terim kümesinden ve temel ilkelerin üzerinde çalışmasını sağlamak, mimari desenlerinin ve uygulamaların tutarlı olmasını sağlamaya yardımcı olur.

## <a name="references"></a>Başvurular

- **gRPC Web sitesi**
  <https://grpc.io>
- **Sunucu uygulamaları için .NET 5 ve .NET Framework arasında seçim yapma**
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[Sonraki](introduction.md)
