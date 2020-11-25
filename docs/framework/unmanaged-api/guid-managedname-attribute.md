---
title: GUID_ManagedName Özniteliği
ms.date: 03/30/2017
api_name:
- GUID_ManagedName
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GUID_ManagedName
helpviewer_keywords:
- GUID_ManagedName attribute
ms.assetid: 11e18095-e444-47bc-aff6-b887ac5dc01e
topic_type:
- apiref
ms.openlocfilehash: 0127b6894f1095521f1b24fc8c0424dc7db824b3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721055"
---
# <a name="guid_managedname-attribute"></a>GUID_ManagedName Özniteliği

Bir bileşen nesne modeli (COM) kitaplığı için yönetilen ad alanı adını belirten bir özel arabirim özniteliği tanımlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```idl
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
## <a name="parameters"></a>Parametreler  

 `value`  
 Kitaplık için yönetilen ad alanı adı.  
  
## <a name="definition"></a>Tanım  

 `GUID_ManagedName` , Cor. h içinde aşağıdaki gibi tanımlanır:  
  
```cpp
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a>Açıklamalar  

 Özel bir arabirim özniteliği tür kitaplığındaki bir nesne için meta verileri tanımlar.  
  
 <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> Özniteliğinden yönetilen adı almak için veya kullanın.  
  
 Daha fazla bilgi için Visual C++ başvuru belgelerindeki [arabirim öznitelikleri](/cpp/windows/attributes/interface-attributes) ' ne bakın.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, özniteliğini kullanan bir kitaplık tanımını gösterir `GUID_ManagedName` .  
  
```idl
[  
   ...  
   custom(GUID_ManagedName, Microsoft.VisualStudio.CommandBars.dll")  
]  
library Microsoft_VisualStudio_CommandBars  
{  
   ...  
}  
```  
  
## <a name="requirements"></a>Gereksinimler  

 **Üst bilgi:** Cor. h
