---
description: 'Daha fazla bilgi edinin: ISymUnmanagedBinder2 Interface'
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
ms.openlocfilehash: 73847cdc9366ec18974fac261cbbad4d7dc6ccc6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689891"
---
# <a name="isymunmanagedbinder2-interface"></a>ISymUnmanagedBinder2 Arabirimi

Yönetilmeyen kod için bir sembol cildi temsil eder ve [ıstreamunmanagedciltçi](isymunmanagedbinder-interface.md) arabirimini genişletir.  
  
> [!IMPORTANT]
> Güvenilmeyen bir kaynaktan program veritabanı (PDB) dosyasını açmak için bir güvenlik riskidir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetReaderForFile2 Yöntemi](isymunmanagedbinder2-getreaderforfile2-method.md)|Meta veri arabirimi ve dosya adı verildiğinde, modülle ilişkili hata ayıklama sembollerini okuyacak doğru [ıdimunmanagedreader](isymunmanagedreader-interface.md) arabirimini döndürür. [Istreamunmanagedciltçi:: GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) yönteminden daha kapsamlı bir arama sağlar.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** CorSym. IDL, CorSym. h  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tanılama Sembol Deposu Arabirimleri](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedBinder Arabirimi](isymunmanagedbinder-interface.md)
- [ISymUnmanagedBinder3 Arabirimi](isymunmanagedbinder3-interface.md)
