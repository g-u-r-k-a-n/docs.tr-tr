---
title: INotifySink2::OnSyncCallExit Yöntemi
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallExit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallExit
helpviewer_keywords:
- INotifySink2::OnSyncCallExit method [.NET Framework debugging]
- OnSyncCallExit method [.NET Framework debugging]
ms.assetid: d9d7600e-a8f5-443a-96de-67d26e130f2d
topic_type:
- apiref
ms.openlocfilehash: 03b8afc1276dae6244bcf12bd0bc78c2fa5380bb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448689"
---
# <a name="inotifysink2onsynccallexit-method"></a>INotifySink2::OnSyncCallExit Yöntemi
Gets invoked when exiting a call.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT OnSyncCallExit  
(  
    [in]  CALL_ID   in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*    out_pBufferSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `in_CallID`  
 [in] ID of the call being exited. See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).  
  
 `out_ppBuffer`  
 [out] Call buffer.  
  
 `out_pBufferSize`  
 [out] Size of the call buffer, in bytes.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK if the method succeeds.  
  
## <a name="requirements"></a>Gereksinimler  
 **Header:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>Ayrıca bkz.

- [INotifySink2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [INotifySource2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [INotifyConnection2 Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
