---
description: 'Daha fazla bilgi edinin: IMetaDataImport2 Interface'
title: IMetaDataImport2 Arabirimi
ms.date: 03/30/2017
api_name:
- IMetaDataImport2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2
helpviewer_keywords:
- IMetaDataImport2 interface [.NET Framework metadata]
ms.assetid: d39b2b87-ba53-4771-ae53-952a68452511
topic_type:
- apiref
ms.openlocfilehash: de1b190ae174c6028e4f116d7f6fc0b9af0aac6d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688552"
---
# <a name="imetadataimport2-interface"></a>IMetaDataImport2 Arabirimi

, Genel türlerle çalışma yeteneği sağlamak için [IMetaDataImport](imetadataimport-interface.md) arabirimini genişletir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumGenericParamConstraints Yöntemi](imetadataimport2-enumgenericparamconstraints-method.md)|Belirtilen belirteçle temsil edilen genel parametreyle ilişkili genel parametre kısıtlamaları dizisi için bir Numaralandırıcı alır.|  
|[EnumGenericParams Yöntemi](imetadataimport2-enumgenericparams-method.md)|Belirtilen TypeDef veya MethodDef belirteciyle ilişkili bir genel parametre belirteçleri dizisi için bir Numaralandırıcı alır.|  
|[EnumMethodSpecs Yöntemi](imetadataimport2-enummethodspecs-method.md)|Belirtilen MethodDef veya MemberRef belirteciyle ilişkili bir MethodSpec belirteçleri dizisi için bir Numaralandırıcı alır.|  
|[GetGenericParamConstraintProps Yöntemi](imetadataimport2-getgenericparamconstraintprops-method.md)|Belirtilen kısıtlama belirteci tarafından temsil edilen genel parametre kısıtlamasıyla ilişkili meta verileri alır.|  
|[GetGenericParamProps Yöntemi](imetadataimport2-getgenericparamprops-method.md)|Belirtilen belirteç tarafından temsil edilen genel parametreyle ilişkili meta verileri alır.|  
|[GetMethodSpecProps Yöntemi](imetadataimport2-getmethodspecprops-method.md)|Belirtilen MethodSpec belirteci tarafından başvurulan metodun meta veri imzasını alır.|  
|[GetPEKind Yöntemi](imetadataimport2-getpekind-method.md)|Geçerli meta veri kapsamında tanımlanan, genellikle bir DLL veya EXE dosyası olan Taşınabilir çalıştırılabilir (PE) dosyasındaki kodun yapısını tanımlayan bir değer alır|  
|[GetVersionString Yöntemi](imetadataimport2-getversionstring-method.md)|Derlemeyi oluşturmak için kullanılan çalışma zamanının sürüm numarasını alır.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.PortableExecutableKinds>
- [Meta Veri Arabirimleri](metadata-interfaces.md)
- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
