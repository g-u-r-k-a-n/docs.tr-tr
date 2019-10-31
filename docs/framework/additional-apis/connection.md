---
title: Connection Sınıfı
ms.date: 05/01/2017
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
ms.openlocfilehash: a305b28a34a70112cc80c33b11f30ab02213f0c6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120062"
---
# <a name="connection-class"></a><span data-ttu-id="abb9c-102">Connection Sınıfı</span><span class="sxs-lookup"><span data-stu-id="abb9c-102">Connection Class</span></span>

<span data-ttu-id="abb9c-103">`Connection` sınıfı sunucu yanıtlarını, kuyruk isteklerini ve işlem hattı isteklerini ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="abb9c-103">The `Connection` class parses server responses, queue requests, and pipeline requests.</span></span>

## <a name="syntax"></a><span data-ttu-id="abb9c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="abb9c-104">Syntax</span></span>
  
```csharp  
internal class Connection : PooledStream
```

> [!WARNING]
> <span data-ttu-id="abb9c-105">`Connection` sınıfı dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="abb9c-105">The `Connection` class is internal and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="abb9c-106">Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="abb9c-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="abb9c-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="abb9c-107">Requirements</span></span>

<span data-ttu-id="abb9c-108">**Ad alanı:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="abb9c-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="abb9c-109">**Bütünleştirilmiş kod:** Sistem (System. dll içinde)</span><span class="sxs-lookup"><span data-stu-id="abb9c-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="abb9c-110">**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="abb9c-110">**.NET Framework versions:** Available since 2.0.</span></span>
