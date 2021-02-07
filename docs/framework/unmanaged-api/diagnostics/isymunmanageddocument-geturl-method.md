---
description: 'Şu konuda daha fazla bilgi edinin: ıvmunmanageddocument:: GetURL Yöntemi'
title: ISymUnmanagedDocument::GetURL Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetURL
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetURL
helpviewer_keywords:
- GetURL method [.NET Framework debugging]
- ISymUnmanagedDocument::GetURL method [.NET Framework debugging]
ms.assetid: 60600178-c2b5-4cab-b3a5-f0f61acebaf1
topic_type:
- apiref
ms.openlocfilehash: b39b36054d80f9ad2f9dd076e2055ccbc6526973
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710198"
---
# <a name="isymunmanageddocumentgeturl-method"></a><span data-ttu-id="fa1d9-103">ISymUnmanagedDocument::GetURL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa1d9-103">ISymUnmanagedDocument::GetURL Method</span></span>

<span data-ttu-id="fa1d9-104">Bu belge için Tekdüzen Kaynak Konumlandırıcı 'sını (URL) döndürür.</span><span class="sxs-lookup"><span data-stu-id="fa1d9-104">Returns the uniform resource locator (URL) for this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa1d9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa1d9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa1d9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fa1d9-106">Parameters</span></span>  

 `cchUrl`  
 <span data-ttu-id="fa1d9-107">'ndaki Arabelleğin karakter cinsinden boyutu `szURL` .</span><span class="sxs-lookup"><span data-stu-id="fa1d9-107">[in] The size, in characters, of the `szURL` buffer.</span></span>  
  
 `pcchUrl`  
 <span data-ttu-id="fa1d9-108">dışı Null sonlandırma dahil olmak üzere URL boyutunu alan bir değişkene yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fa1d9-108">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span></span>  
  
 `szUrl`  
 <span data-ttu-id="fa1d9-109">dışı URL 'YI içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="fa1d9-109">[out] The buffer containing the URL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa1d9-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fa1d9-110">Return Value</span></span>  

 <span data-ttu-id="fa1d9-111">Yöntem başarılı olursa S_OK; Aksi takdirde, bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="fa1d9-111">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa1d9-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa1d9-112">See also</span></span>

- [<span data-ttu-id="fa1d9-113">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa1d9-113">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
