---
title: Bağlantı sınıfı (System.Net)
ms.date: 05/01/2017
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Connection
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 6f0b8902-f31c-4ab9-a8c9-de43228995ec
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b3045e9f6a4b3d86580ec3bc5719520fed7d3a35
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429353"
---
# <a name="connection-class"></a><span data-ttu-id="a140f-102">Connection Sınıfı</span><span class="sxs-lookup"><span data-stu-id="a140f-102">Connection Class</span></span>

<span data-ttu-id="a140f-103">`Connection` sınıfı sunucu yanıtlarını, kuyruk isteklerini ve işlem hattı isteklerini ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="a140f-103">The `Connection` class parses server responses, queue requests, and pipeline requests.</span></span>

## <a name="syntax"></a><span data-ttu-id="a140f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a140f-104">Syntax</span></span>
  
```csharp  
internal class Connection : PooledStream
```

> [!WARNING]
> <span data-ttu-id="a140f-105">`Connection` sınıfı dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a140f-105">The `Connection` class is internal and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="a140f-106">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="a140f-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="a140f-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a140f-107">Requirements</span></span>

<span data-ttu-id="a140f-108">**Ad alanı:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="a140f-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="a140f-109">**Bütünleştirilmiş kod:** Sistem (System. dll içinde)</span><span class="sxs-lookup"><span data-stu-id="a140f-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="a140f-110">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a140f-110">**.NET Framework versions:** Available since 2.0.</span></span>
