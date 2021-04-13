---
author: IEvangelist
ms.topic: include
ms.date: 04/07/2021
ms.author: dapine
ms.custom: include
ms.openlocfilehash: 82802e0aef69a3c3e902edaefad621b4062de09e
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2021
ms.locfileid: "107260520"
---
> [!TIP]
> <span data-ttu-id="3508a-101">Bağımlılık ekleme ile ilgili olarak, Hizmetleri bir içinde kaydettirirken <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> [hizmet ömrü](/dotnet/core/extensions/dependency-injection.md#service-lifetimes) sizin adınıza örtülü olarak yönetilir.</span><span class="sxs-lookup"><span data-stu-id="3508a-101">With regard to dependency injection, when registering services in an <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>, the [service lifetime](/dotnet/core/extensions/dependency-injection.md#service-lifetimes) is managed implicitly on your behalf.</span></span> <span data-ttu-id="3508a-102"><xref:System.IServiceProvider>Ve buna karşılık gelen <xref:Microsoft.Extensions.Hosting.IHost> kaynak temizliği.</span><span class="sxs-lookup"><span data-stu-id="3508a-102">The <xref:System.IServiceProvider> and corresponding <xref:Microsoft.Extensions.Hosting.IHost> orchestrate resource cleanup.</span></span> <span data-ttu-id="3508a-103">Özellikle, ve uygulamaları <xref:System.IDisposable> , <xref:System.IAsyncDisposable> belirtilen yaşam sürelerinin sonuna doğru şekilde atıldı.</span><span class="sxs-lookup"><span data-stu-id="3508a-103">Specifically, implementations of <xref:System.IDisposable> and <xref:System.IAsyncDisposable> are properly disposed at the end of their specified lifetime.</span></span>
>
> <span data-ttu-id="3508a-104">Daha fazla bilgi için bkz. [.net 'e bağımlılık ekleme](/dotnet/core/extensions/dependency-injection.md).</span><span class="sxs-lookup"><span data-stu-id="3508a-104">For more information, see [Dependency injection in .NET](/dotnet/core/extensions/dependency-injection.md).</span></span>
