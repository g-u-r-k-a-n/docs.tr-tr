---
title: Activate Işlevi-WPF yönetilmeyen API başvurusu
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- Activate
api_location:
- PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
ms.openlocfilehash: 9c0a235e8b94294ab82da88e43f7446c29739c12
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734505"
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="ed93c-102">Activate Işlevi (WPF yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ed93c-102">Activate Function (WPF Unmanaged API Reference)</span></span>

<span data-ttu-id="ed93c-103">Bu API Windows Presentation Foundation (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="ed93c-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>

<span data-ttu-id="ed93c-104">Windows yönetimi için Windows Presentation Foundation (WPF) altyapısı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ed93c-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>

## <a name="syntax"></a><span data-ttu-id="ed93c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ed93c-105">Syntax</span></span>

```cpp
void Activate(
    const ActivateParameters* pParameters,
    __deref_out_ecount(1) LPUNKNOWN* ppInner,
    );
```

## <a name="parameters"></a><span data-ttu-id="ed93c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ed93c-106">Parameters</span></span>

`pParameters`\
<span data-ttu-id="ed93c-107">Pencerenin etkinleştirme parametrelerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ed93c-107">A pointer to the window's activation parameters.</span></span>

`ppInner`\
<span data-ttu-id="ed93c-108"><xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> nesnesine yönelik bir işaretçi içeren tek öğeli arabelleğin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ed93c-108">A pointer to the address of a single-element buffer that contains a pointer to an <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> object.</span></span>

## <a name="requirements"></a><span data-ttu-id="ed93c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ed93c-109">Requirements</span></span>

<span data-ttu-id="ed93c-110">**Platformlar:** Bkz. [.NET Framework sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed93c-110">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="ed93c-111">**DOSYASıNı**</span><span class="sxs-lookup"><span data-stu-id="ed93c-111">**DLL:**</span></span>

<span data-ttu-id="ed93c-112">.NET Framework 3,0 ve 3,5: PresentationHostDLL. dll</span><span class="sxs-lookup"><span data-stu-id="ed93c-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>

<span data-ttu-id="ed93c-113">.NET Framework 4 ve üzeri: PresentationHost_v0400. dll</span><span class="sxs-lookup"><span data-stu-id="ed93c-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>

<span data-ttu-id="ed93c-114">**.NET Framework sürümü:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed93c-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ed93c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed93c-115">See also</span></span>

- [<span data-ttu-id="ed93c-116">WPF Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="ed93c-116">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
