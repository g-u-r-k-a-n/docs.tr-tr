---
description: 'Daha fazla bilgi edinin: CreateALink Işlevi'
title: CreateALink İşlevi
ms.date: 03/30/2017
api_name:
- CreateALink
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type:
- apiref
ms.openlocfilehash: cf34ae8d38a8339f539c770df8f5dd14e4a3e4b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638372"
---
# <a name="createalink-function"></a><span data-ttu-id="e4de4-103">CreateALink İşlevi</span><span class="sxs-lookup"><span data-stu-id="e4de4-103">CreateALink Function</span></span>

<span data-ttu-id="e4de4-104">Derleme bağlayıcının bir örneğini oluşturur ve belirtilen arabirime bir işaretçi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e4de4-104">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4de4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4de4-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4de4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e4de4-106">Parameters</span></span>  
  
|<span data-ttu-id="e4de4-107">Parametre</span><span class="sxs-lookup"><span data-stu-id="e4de4-107">Parameter</span></span>|<span data-ttu-id="e4de4-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4de4-108">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="e4de4-109">Bütünleştirilmiş kod bağlayıcı arabirimlerinden birinin fiziksel adı.</span><span class="sxs-lookup"><span data-stu-id="e4de4-109">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="e4de4-110">Başarılı tamamlamadaki konum, arabirime yönelik bir işaretçi içerir `riid` .</span><span class="sxs-lookup"><span data-stu-id="e4de4-110">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e4de4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e4de4-111">Requirements</span></span>  

 <span data-ttu-id="e4de4-112">**Kitaplık**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="e4de4-112">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4de4-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4de4-113">See also</span></span>

- [<span data-ttu-id="e4de4-114">Al.exe (bütünleştirilmiş kod bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="e4de4-114">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
