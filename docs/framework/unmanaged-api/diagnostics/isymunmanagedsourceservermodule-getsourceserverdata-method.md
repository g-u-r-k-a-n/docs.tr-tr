---
title: ISymUnmanagedSourceServerModule::GetSourceServerData Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSourceServerModule.GetSourceServerData
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData
helpviewer_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData method [.NET Framework debugging]
- GetSourceServerData method [.NET Framework debugging]
ms.assetid: 20bdf8ff-2d15-4c64-8950-6888f642d6c0
topic_type:
- apiref
ms.openlocfilehash: 9a3a6c07a9cace0ac9834cdb05925a301285204c
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615325"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="4d907-102">ISymUnmanagedSourceServerModule::GetSourceServerData Metodu</span><span class="sxs-lookup"><span data-stu-id="4d907-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="4d907-103">Modülün kaynak sunucu verilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="4d907-103">Returns the source server data for the module.</span></span> <span data-ttu-id="4d907-104">Çağıran, kullanarak kaynakları serbest vermelidir `CoTaskMemFree` .</span><span class="sxs-lookup"><span data-stu-id="4d907-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d907-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="4d907-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d907-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4d907-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="4d907-107">dışı `ULONG32`Kaynak sunucu verilerinin bayt cinsinden boyutunu alan bir bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="4d907-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="4d907-108">dışı Döndürülen değere yönelik bir işaretçi `pDataByteCount` .</span><span class="sxs-lookup"><span data-stu-id="4d907-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d907-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4d907-109">Return Value</span></span>  
 <span data-ttu-id="4d907-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="4d907-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d907-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4d907-111">Requirements</span></span>  
 <span data-ttu-id="4d907-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4d907-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d907-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d907-113">See also</span></span>

- [<span data-ttu-id="4d907-114">ISymUnmanagedSourceServerModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d907-114">ISymUnmanagedSourceServerModule Interface</span></span>](isymunmanagedsourceservermodule-interface.md)
