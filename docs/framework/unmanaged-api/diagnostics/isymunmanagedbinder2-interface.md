---
title: ISymUnmanagedBinder2 Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2 Interface
helpviewer_keywords:
- ISymUnmanagedBinder2 interface [.NET Framework debugging]
ms.assetid: 7a59f405-73e8-4434-8bcc-a9dc45ea08e6
topic_type:
- apiref
ms.openlocfilehash: c5a43f6c277f582f9f14cefe5bfba6f5300c09d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727360"
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="cff12-102">ISymUnmanagedBinder2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cff12-102">ISymUnmanagedBinder2 Interface</span></span>

<span data-ttu-id="cff12-103">Yönetilmeyen kod için bir sembol cildi temsil eder ve [ıstreamunmanagedciltçi](isymunmanagedbinder-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="cff12-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cff12-104">Güvenilmeyen bir kaynaktan program veritabanı (PDB) dosyasını açmak için bir güvenlik riskidir.</span><span class="sxs-lookup"><span data-stu-id="cff12-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cff12-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cff12-105">Methods</span></span>  
  
|<span data-ttu-id="cff12-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cff12-106">Method</span></span>|<span data-ttu-id="cff12-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cff12-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cff12-108">GetReaderForFile2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cff12-108">GetReaderForFile2 Method</span></span>](isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="cff12-109">Meta veri arabirimi ve dosya adı verildiğinde, modülle ilişkili hata ayıklama sembollerini okuyacak doğru [ıdimunmanagedreader](isymunmanagedreader-interface.md) arabirimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="cff12-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="cff12-110">[Istreamunmanagedciltçi:: GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) yönteminden daha kapsamlı bir arama sağlar.</span><span class="sxs-lookup"><span data-stu-id="cff12-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cff12-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cff12-111">Requirements</span></span>  

 <span data-ttu-id="cff12-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="cff12-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cff12-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cff12-113">See also</span></span>

- [<span data-ttu-id="cff12-114">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cff12-114">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="cff12-115">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cff12-115">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="cff12-116">ISymUnmanagedBinder3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cff12-116">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
