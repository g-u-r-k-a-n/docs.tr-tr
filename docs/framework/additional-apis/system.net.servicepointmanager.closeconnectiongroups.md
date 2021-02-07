---
description: 'Şu konuda daha fazla bilgi edinin: ServicePointManager. CloseConnectionGroups yöntemi'
title: ServicePointManager. CloseConnectionGroups yöntemi (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.CloseConnectionGroups
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 8cd1a1f0f4dbdaeaee117e6a7ae4219680363a6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99699564"
---
# <a name="servicepointmanagercloseconnectiongroups-method"></a><span data-ttu-id="a58e1-103">ServicePointManager. CloseConnectionGroups yöntemi</span><span class="sxs-lookup"><span data-stu-id="a58e1-103">ServicePointManager.CloseConnectionGroups method</span></span>

<span data-ttu-id="a58e1-104">Tüm hizmet noktalarında dolaşır ve belirtilen ada sahip bağlantı gruplarını kapatır.</span><span class="sxs-lookup"><span data-stu-id="a58e1-104">Iterates through all service points and closes connection groups that have the specified name.</span></span>

```csharp
internal static void CloseConnectionGroups(string connectionGroupName)
```

> [!WARNING]
> <span data-ttu-id="a58e1-105">Bu yöntem dahili ve doğrudan kodunuzda kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a58e1-105">This method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="a58e1-106">Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="a58e1-106">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="a58e1-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a58e1-107">Parameters</span></span>

<span data-ttu-id="a58e1-108">`connectionGroupName` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a58e1-108">`connectionGroupName` <xref:System.String></span></span>

<span data-ttu-id="a58e1-109">Kapatılacak bağlantı grubunun adı.</span><span class="sxs-lookup"><span data-stu-id="a58e1-109">The name of the connection group to close.</span></span>

## <a name="requirements"></a><span data-ttu-id="a58e1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a58e1-110">Requirements</span></span>

<span data-ttu-id="a58e1-111">**Ad alanı:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="a58e1-111">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="a58e1-112">**Bütünleştirilmiş kod:** Sistem (System.dll)</span><span class="sxs-lookup"><span data-stu-id="a58e1-112">**Assembly:** System (in System.dll)</span></span>
