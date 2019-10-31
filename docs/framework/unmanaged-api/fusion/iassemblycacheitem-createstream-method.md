---
title: IAssemblyCacheItem::CreateStream Yöntemi
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.CreateStream
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::CreateStream
helpviewer_keywords:
- CreateStream method [.NET Framework fusion]
- IAssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
ms.openlocfilehash: 0660621f465f2ba3610e06bd1df38baa1bc5c907
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134478"
---
# <a name="iassemblycacheitemcreatestream-method"></a><span data-ttu-id="af3a0-102">IAssemblyCacheItem::CreateStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="af3a0-102">IAssemblyCacheItem::CreateStream Method</span></span>

<span data-ttu-id="af3a0-103">Belirtilen ad ve biçimle bir akış oluşturur.</span><span class="sxs-lookup"><span data-stu-id="af3a0-103">Creates a stream with the specified name and format.</span></span>

## <a name="syntax"></a><span data-ttu-id="af3a0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af3a0-104">Syntax</span></span>

```cpp
HRESULT CreateStream (
    [in]  DWORD dwFlags,
    [in]  LPCWSTR pszStreamName,
    [in]  DWORD dwFormat,
    [in]  DWORD dwFormatFlags,
    [out] IStream **ppIStream,
    [in, optional] ULARGE_INTEGER *puliMaxSize
);
```

## <a name="parameters"></a><span data-ttu-id="af3a0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="af3a0-105">Parameters</span></span>

`dwFlags`\
<span data-ttu-id="af3a0-106">'ndaki Fusion. IDL içinde tanımlanan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="af3a0-106">[in] Flags defined in Fusion.idl.</span></span>

`pszStreamName`\
<span data-ttu-id="af3a0-107">'ndaki Oluşturulacak akışın adı.</span><span class="sxs-lookup"><span data-stu-id="af3a0-107">[in] The name of the stream to be created.</span></span>

`dwFormat`\
<span data-ttu-id="af3a0-108">'ndaki Akışa eklenecek dosyanın biçimi.</span><span class="sxs-lookup"><span data-stu-id="af3a0-108">[in] The format of the file to be streamed.</span></span>

`dwFormatFlags`\
<span data-ttu-id="af3a0-109">'ndaki Fusion. IDL içinde tanımlı formata özgü bayraklar.</span><span class="sxs-lookup"><span data-stu-id="af3a0-109">[in] Format-specific flags defined in Fusion.idl.</span></span>

`ppIStream`\
<span data-ttu-id="af3a0-110">dışı Döndürülen [IStream](/windows/desktop/api/objidl/nn-objidl-istream) örneğinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="af3a0-110">[out] A pointer to the address of the returned [IStream](/windows/desktop/api/objidl/nn-objidl-istream) instance.</span></span>

`puliMaxSize`\
<span data-ttu-id="af3a0-111">[ın, isteğe bağlı] `ppIStream`başvurduğu akışın en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="af3a0-111">[in, optional] The maximum size of the stream referenced by `ppIStream`.</span></span>

## <a name="requirements"></a><span data-ttu-id="af3a0-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="af3a0-112">Requirements</span></span>

<span data-ttu-id="af3a0-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af3a0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="af3a0-114">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="af3a0-114">**Header:** Fusion.h</span></span>

<span data-ttu-id="af3a0-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af3a0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="af3a0-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af3a0-116">See also</span></span>

- [<span data-ttu-id="af3a0-117">IAssemblyCacheItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="af3a0-117">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
