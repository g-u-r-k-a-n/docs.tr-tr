---
title: .NET 'teki araçlar ve Tanılamalar
author: IEvangelist
description: .NET geliştiricileri için kullanılabilen geliştirme ve tanılama araçları hakkında bilgi edinin.
ms.author: dapine
ms.date: 10/21/2020
ms.topic: overview
ms.openlocfilehash: 85d64c0d5857d8603316175d18f8c2f7eab3cc93
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498535"
---
# <a name="tools-and-diagnostics-in-net"></a>.NET 'teki araçlar ve Tanılamalar

Bu makalede, .NET geliştiricileri için kullanılabilen çeşitli araçlar hakkında bilgi edineceksiniz. .NET ile, bir komut satırı arabirimi (CLı) içeren sağlam bir yazılım geliştirme seti (SDK) vardır. .NET CLı, içindeki birçok özelliği sunar. NET Ready tümleşik geliştirme ortamları (IDEs). Bu makalede ayrıca, performans sorunlarını, bellek sızıntılarını, yüksek CPU, kilitlenmeleri ve kod analizi için araç desteğini tanılamaya yönelik .NET CLı araçları gibi üretkenlik özelliklerine yönelik kaynaklar da sağlanmaktadır.

## <a name="net-sdk"></a>.NET SDK

.NET SDK, hem .NET çalışma zamanını hem de .NET CLı 'yi içerir. Windows, Linux, macOS veya Docker için [.NET SDK 'sını](https://dotnet.microsoft.com/download) indirebilirsiniz. Daha fazla bilgi için bkz. [.NET SDK 'ya genel bakış](../core/sdk.md).

## <a name="net-cli"></a>.NET CLı

.NET CLı, .NET uygulamaları geliştirmeye, oluşturmaya, çalıştırmaya ve yayımlamaya yönelik platformlar arası bir araç zinciridir. .Net CLı, .NET SDK 'ya dahildir. Daha fazla bilgi için bkz. [.net CLI 'ya genel bakış](../core/tools/index.md).

## <a name="ides"></a>IDE

.NET uygulamalarını [Visual Studio Code](https://code.visualstudio.com/docs), [Visual Studio](/visualstudio/windows)veya [Mac için Visual Studio](/visualstudio/mac)yazabilirsiniz.

## <a name="additional-tools"></a>Ek araçlar

.NET, daha yaygın araçların yanı sıra belirli senaryolar için de araçlar sağlar. Bazı kullanım örnekleri, .NET SDK veya .NET çalışma zamanı kaldırma, Windows Communication Foundation (WCF) meta verilerini alma, proxy kaynak kodu oluşturma ve XML serileştirilmesi içerir. Daha fazla bilgi için bkz. [.net ek araçlara genel bakış](../core/additional-tools/index.md).

## <a name="diagnostics-and-instrumentation"></a>Tanılama ve izleme

.NET geliştiricisi olarak, uygulama performansını izlemek, izleme ile uygulama profili oluşturmak, performans ölçümlerini toplamak ve döküm dosyalarını çözümlemek için ortak performans tanılama araçlarından yararlanabilirsiniz. Performans ölçümlerini olay sayaçlarıyla toplayıp, uygulamaların nasıl gerçekleştirdiği hakkında öngörüler elde etmek için profil oluşturma araçlarını kullanabilirsiniz. Daha fazla bilgi için bkz. [.net tanılama araçları](../core/diagnostics/index.md).

## <a name="code-analysis"></a>Kod analizi

.NET derleyici platformu (Roslyn) Çözümleyicileri, kod kalitesi ve kod stili sorunları için C# veya Visual Basic kodunuzu inceleyin. Daha fazla bilgi için bkz. [.net kaynak kodu analizine genel bakış](code-analysis/overview.md).
