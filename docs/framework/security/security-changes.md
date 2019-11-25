---
title: .NET Framework'te Güvenlik Değişiklikleri
ms.date: 03/30/2017
helpviewer_keywords:
- Allow Partially Trusted Callers attribute
- .NET Framework 4, security changes
- .NET Framework security
- security-transparent code
- security-critical code
- code access security, changes
ms.assetid: 5e87881c-9c13-4b52-8ad1-e34bb46e8aaa
author: mairaw
ms.author: mairaw
ms.openlocfilehash: af2869e5ca3b41778c094b7a78a9493e74868811
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204500"
---
# <a name="security-changes-in-the-net-framework"></a><span data-ttu-id="afdc5-102">.NET Framework'te Güvenlik Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="afdc5-102">Security Changes in the .NET Framework</span></span>

<span data-ttu-id="afdc5-103">The most important change to security in the .NET Framework 4.5 is in strong naming.</span><span class="sxs-lookup"><span data-stu-id="afdc5-103">The most important change to security in the .NET Framework 4.5 is in strong naming.</span></span> <span data-ttu-id="afdc5-104">See [Enhanced Strong Naming](../../standard/assembly/enhanced-strong-naming.md) for a description of those changes.</span><span class="sxs-lookup"><span data-stu-id="afdc5-104">See [Enhanced Strong Naming](../../standard/assembly/enhanced-strong-naming.md) for a description of those changes.</span></span>  
  
<span data-ttu-id="afdc5-105">The .NET Framework provides a two-tier security model for managed applications.</span><span class="sxs-lookup"><span data-stu-id="afdc5-105">The .NET Framework provides a two-tier security model for managed applications.</span></span> <span data-ttu-id="afdc5-106">Windows 8.x Store apps run in a Windows security container that limits access to resources.</span><span class="sxs-lookup"><span data-stu-id="afdc5-106">Windows 8.x Store apps run in a Windows security container that limits access to resources.</span></span> <span data-ttu-id="afdc5-107">Within that container, managed applications run fully trusted.</span><span class="sxs-lookup"><span data-stu-id="afdc5-107">Within that container, managed applications run fully trusted.</span></span> <span data-ttu-id="afdc5-108">From a code access security (CAS) perspective, there is nothing a developer can do to elevate privileges.</span><span class="sxs-lookup"><span data-stu-id="afdc5-108">From a code access security (CAS) perspective, there is nothing a developer can do to elevate privileges.</span></span> <span data-ttu-id="afdc5-109">For information about the privileges granted by Windows, see [App capability declarations (Windows Store apps)](https://go.microsoft.com/fwlink/?LinkId=230436) in the Windows Dev Center.</span><span class="sxs-lookup"><span data-stu-id="afdc5-109">For information about the privileges granted by Windows, see [App capability declarations (Windows Store apps)](https://go.microsoft.com/fwlink/?LinkId=230436) in the Windows Dev Center.</span></span> <span data-ttu-id="afdc5-110">For information about creating a Windows 8.x Store app, see [Create your first Windows Store app using C# or Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).</span><span class="sxs-lookup"><span data-stu-id="afdc5-110">For information about creating a Windows 8.x Store app, see [Create your first Windows Store app using C# or Visual Basic](https://go.microsoft.com/fwlink/?LinkId=230461).</span></span>
