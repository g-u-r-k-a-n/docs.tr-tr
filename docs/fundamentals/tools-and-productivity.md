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
# <a name="tools-and-diagnostics-in-net"></a><span data-ttu-id="f03d0-103">.NET 'teki araçlar ve Tanılamalar</span><span class="sxs-lookup"><span data-stu-id="f03d0-103">Tools and diagnostics in .NET</span></span>

<span data-ttu-id="f03d0-104">Bu makalede, .NET geliştiricileri için kullanılabilen çeşitli araçlar hakkında bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f03d0-104">In this article, you'll learn about the various tools available to .NET developers.</span></span> <span data-ttu-id="f03d0-105">.NET ile, bir komut satırı arabirimi (CLı) içeren sağlam bir yazılım geliştirme seti (SDK) vardır.</span><span class="sxs-lookup"><span data-stu-id="f03d0-105">With .NET, you have a robust software development kit (SDK) that includes a command-line interface (CLI).</span></span> <span data-ttu-id="f03d0-106">.NET CLı, içindeki birçok özelliği sunar. NET Ready tümleşik geliştirme ortamları (IDEs).</span><span class="sxs-lookup"><span data-stu-id="f03d0-106">The .NET CLI enables many of the features throughout the .NET-ready integrated development environments (IDEs).</span></span> <span data-ttu-id="f03d0-107">Bu makalede ayrıca, performans sorunlarını, bellek sızıntılarını, yüksek CPU, kilitlenmeleri ve kod analizi için araç desteğini tanılamaya yönelik .NET CLı araçları gibi üretkenlik özelliklerine yönelik kaynaklar da sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f03d0-107">This article also provides resources to productivity capabilities, such as .NET CLI tools for diagnosing performance issues, memory leaks, high CPU, deadlocks, and tooling support for code analysis.</span></span>

## <a name="net-sdk"></a><span data-ttu-id="f03d0-108">.NET SDK</span><span class="sxs-lookup"><span data-stu-id="f03d0-108">.NET SDK</span></span>

<span data-ttu-id="f03d0-109">.NET SDK, hem .NET çalışma zamanını hem de .NET CLı 'yi içerir.</span><span class="sxs-lookup"><span data-stu-id="f03d0-109">The .NET SDK includes both the .NET Runtime and the .NET CLI.</span></span> <span data-ttu-id="f03d0-110">Windows, Linux, macOS veya Docker için [.NET SDK 'sını](https://dotnet.microsoft.com/download) indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f03d0-110">You can download the [.NET SDK](https://dotnet.microsoft.com/download) for Windows, Linux, macOS, or Docker.</span></span> <span data-ttu-id="f03d0-111">Daha fazla bilgi için bkz. [.NET SDK 'ya genel bakış](../core/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="f03d0-111">For more information, see [.NET SDK overview](../core/sdk.md).</span></span>

## <a name="net-cli"></a><span data-ttu-id="f03d0-112">.NET CLı</span><span class="sxs-lookup"><span data-stu-id="f03d0-112">.NET CLI</span></span>

<span data-ttu-id="f03d0-113">.NET CLı, .NET uygulamaları geliştirmeye, oluşturmaya, çalıştırmaya ve yayımlamaya yönelik platformlar arası bir araç zinciridir.</span><span class="sxs-lookup"><span data-stu-id="f03d0-113">The .NET CLI is a cross-platform toolchain for developing, building, running, and publishing .NET applications.</span></span> <span data-ttu-id="f03d0-114">.Net CLı, .NET SDK 'ya dahildir.</span><span class="sxs-lookup"><span data-stu-id="f03d0-114">The .NET CLI is included with the .NET SDK.</span></span> <span data-ttu-id="f03d0-115">Daha fazla bilgi için bkz. [.net CLI 'ya genel bakış](../core/tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="f03d0-115">For more information, see [.NET CLI overview](../core/tools/index.md).</span></span>

## <a name="ides"></a><span data-ttu-id="f03d0-116">IDE</span><span class="sxs-lookup"><span data-stu-id="f03d0-116">IDEs</span></span>

<span data-ttu-id="f03d0-117">.NET uygulamalarını [Visual Studio Code](https://code.visualstudio.com/docs), [Visual Studio](/visualstudio/windows)veya [Mac için Visual Studio](/visualstudio/mac)yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f03d0-117">You can write .NET applications in [Visual Studio Code](https://code.visualstudio.com/docs), [Visual Studio](/visualstudio/windows), or [Visual Studio for Mac](/visualstudio/mac).</span></span>

## <a name="additional-tools"></a><span data-ttu-id="f03d0-118">Ek araçlar</span><span class="sxs-lookup"><span data-stu-id="f03d0-118">Additional tools</span></span>

<span data-ttu-id="f03d0-119">.NET, daha yaygın araçların yanı sıra belirli senaryolar için de araçlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="f03d0-119">In addition to the more common tools, .NET also provides tools for specific scenarios.</span></span> <span data-ttu-id="f03d0-120">Bazı kullanım örnekleri, .NET SDK veya .NET çalışma zamanı kaldırma, Windows Communication Foundation (WCF) meta verilerini alma, proxy kaynak kodu oluşturma ve XML serileştirilmesi içerir.</span><span class="sxs-lookup"><span data-stu-id="f03d0-120">Some of the use cases include uninstalling the .NET SDK or the .NET Runtime, retrieving Windows Communication Foundation (WCF) metadata, generating proxy source code, and serializing XML.</span></span> <span data-ttu-id="f03d0-121">Daha fazla bilgi için bkz. [.net ek araçlara genel bakış](../core/additional-tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="f03d0-121">For more information, see [.NET additional tools overview](../core/additional-tools/index.md).</span></span>

## <a name="diagnostics-and-instrumentation"></a><span data-ttu-id="f03d0-122">Tanılama ve izleme</span><span class="sxs-lookup"><span data-stu-id="f03d0-122">Diagnostics and instrumentation</span></span>

<span data-ttu-id="f03d0-123">.NET geliştiricisi olarak, uygulama performansını izlemek, izleme ile uygulama profili oluşturmak, performans ölçümlerini toplamak ve döküm dosyalarını çözümlemek için ortak performans tanılama araçlarından yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f03d0-123">As a .NET developer, you can make use of common performance diagnostic tools to monitor app performance, profile apps with tracing, collect performance metrics, and analyze dump files.</span></span> <span data-ttu-id="f03d0-124">Performans ölçümlerini olay sayaçlarıyla toplayıp, uygulamaların nasıl gerçekleştirdiği hakkında öngörüler elde etmek için profil oluşturma araçlarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f03d0-124">You collect performance metrics with event counters, and use profiling tools to gain insights into how apps perform.</span></span> <span data-ttu-id="f03d0-125">Daha fazla bilgi için bkz. [.net tanılama araçları](../core/diagnostics/index.md).</span><span class="sxs-lookup"><span data-stu-id="f03d0-125">For more information, see [.NET diagnostics tools](../core/diagnostics/index.md).</span></span>

## <a name="code-analysis"></a><span data-ttu-id="f03d0-126">Kod analizi</span><span class="sxs-lookup"><span data-stu-id="f03d0-126">Code analysis</span></span>

<span data-ttu-id="f03d0-127">.NET derleyici platformu (Roslyn) Çözümleyicileri, kod kalitesi ve kod stili sorunları için C# veya Visual Basic kodunuzu inceleyin.</span><span class="sxs-lookup"><span data-stu-id="f03d0-127">The .NET compiler platform (Roslyn) analyzers inspect your C# or Visual Basic code for code quality and code style issues.</span></span> <span data-ttu-id="f03d0-128">Daha fazla bilgi için bkz. [.net kaynak kodu analizine genel bakış](code-analysis/overview.md).</span><span class="sxs-lookup"><span data-stu-id="f03d0-128">For more information, see [.NET source code analysis overview](code-analysis/overview.md).</span></span>
