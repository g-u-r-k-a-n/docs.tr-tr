---
title: Install .NET Core on Fedora 30 - package manager - .NET Core
description: Use a package manager to install .NET Core SDK and runtime on Fedora 30.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.openlocfilehash: 2cba627f876efecd3c7e28ef97ddff68456fb019
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450998"
---
# <a name="fedora-30-package-manager---install-net-core"></a><span data-ttu-id="9d309-103">Fedora 30 Package Manager - Install .NET Core</span><span class="sxs-lookup"><span data-stu-id="9d309-103">Fedora 30 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="9d309-104">This article describes how to use a package manager to install .NET Core on Fedora 30.</span><span class="sxs-lookup"><span data-stu-id="9d309-104">This article describes how to use a package manager to install .NET Core on Fedora 30.</span></span> <span data-ttu-id="9d309-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span><span class="sxs-lookup"><span data-stu-id="9d309-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="9d309-106">Register Microsoft key and feed</span><span class="sxs-lookup"><span data-stu-id="9d309-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="9d309-107">Before installing .NET, you'll need to:</span><span class="sxs-lookup"><span data-stu-id="9d309-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="9d309-108">Register the Microsoft key</span><span class="sxs-lookup"><span data-stu-id="9d309-108">Register the Microsoft key</span></span>
- <span data-ttu-id="9d309-109">register the product repository</span><span class="sxs-lookup"><span data-stu-id="9d309-109">register the product repository</span></span>
- <span data-ttu-id="9d309-110">Install required dependencies</span><span class="sxs-lookup"><span data-stu-id="9d309-110">Install required dependencies</span></span>

<span data-ttu-id="9d309-111">This only needs to be done once per machine.</span><span class="sxs-lookup"><span data-stu-id="9d309-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="9d309-112">Open a terminal and run the following commands.</span><span class="sxs-lookup"><span data-stu-id="9d309-112">Open a terminal and run the following commands.</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -q -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/30/prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="9d309-113">Install the .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="9d309-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="9d309-114">Update the products available for installation, then install the .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="9d309-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="9d309-115">In your terminal, run the following command.</span><span class="sxs-lookup"><span data-stu-id="9d309-115">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.0
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="9d309-116">Install the ASP.NET Core runtime</span><span class="sxs-lookup"><span data-stu-id="9d309-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="9d309-117">Update the products available for installation, then install the ASP.NET runtime.</span><span class="sxs-lookup"><span data-stu-id="9d309-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="9d309-118">In your terminal, run the following command.</span><span class="sxs-lookup"><span data-stu-id="9d309-118">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.0
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="9d309-119">Install the .NET Core runtime</span><span class="sxs-lookup"><span data-stu-id="9d309-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="9d309-120">Update the products available for installation, then install the .NET Core runtime.</span><span class="sxs-lookup"><span data-stu-id="9d309-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="9d309-121">In your terminal, run the following command.</span><span class="sxs-lookup"><span data-stu-id="9d309-121">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.0
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="9d309-122">How to install other versions</span><span class="sxs-lookup"><span data-stu-id="9d309-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
