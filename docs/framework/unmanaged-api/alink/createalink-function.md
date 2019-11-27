---
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
ms.openlocfilehash: 9165a4db7e65fb0f409a902b06d32e9c2988aa69
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446546"
---
# <a name="createalink-function"></a><span data-ttu-id="9df74-102">CreateALink İşlevi</span><span class="sxs-lookup"><span data-stu-id="9df74-102">CreateALink Function</span></span>
<span data-ttu-id="9df74-103">Derleme bağlayıcının bir örneğini oluşturur ve belirtilen arabirime bir işaretçi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9df74-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9df74-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9df74-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9df74-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9df74-105">Parameters</span></span>  
  
|<span data-ttu-id="9df74-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="9df74-106">Parameter</span></span>|<span data-ttu-id="9df74-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9df74-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="9df74-108">Bütünleştirilmiş kod bağlayıcı arabirimlerinden birinin fiziksel adı.</span><span class="sxs-lookup"><span data-stu-id="9df74-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="9df74-109">Başarılı tamamlamada yer alan konum `riid` arabirimine yönelik bir işaretçi içerir.</span><span class="sxs-lookup"><span data-stu-id="9df74-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9df74-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9df74-110">Requirements</span></span>  
 <span data-ttu-id="9df74-111">**Kitaplık**: ALink. dll</span><span class="sxs-lookup"><span data-stu-id="9df74-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9df74-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9df74-112">See also</span></span>

- [<span data-ttu-id="9df74-113">Al.exe (Bütünleştirilmiş Kod Bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="9df74-113">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
