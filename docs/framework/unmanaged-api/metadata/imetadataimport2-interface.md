---
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
ms.openlocfilehash: 0fd7915ef46899bdce8312bc6e8a466167e26382
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429213"
---
# <a name="imetadataimport2-interface"></a><span data-ttu-id="e1b21-102">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1b21-102">IMetaDataImport2 Interface</span></span>
<span data-ttu-id="e1b21-103">Extends the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface to provide the capability of working with generic types.</span><span class="sxs-lookup"><span data-stu-id="e1b21-103">Extends the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface to provide the capability of working with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e1b21-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e1b21-104">Methods</span></span>  
  
|<span data-ttu-id="e1b21-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e1b21-105">Method</span></span>|<span data-ttu-id="e1b21-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1b21-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e1b21-107">EnumGenericParamConstraints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1b21-107">EnumGenericParamConstraints Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|<span data-ttu-id="e1b21-108">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span><span class="sxs-lookup"><span data-stu-id="e1b21-108">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="e1b21-109">EnumGenericParams Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1b21-109">EnumGenericParams Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|<span data-ttu-id="e1b21-110">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span><span class="sxs-lookup"><span data-stu-id="e1b21-110">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>|  
|[<span data-ttu-id="e1b21-111">EnumMethodSpecs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1b21-111">EnumMethodSpecs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|<span data-ttu-id="e1b21-112">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span><span class="sxs-lookup"><span data-stu-id="e1b21-112">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>|  
|[<span data-ttu-id="e1b21-113">GetGenericParamConstraintProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1b21-113">GetGenericParamConstraintProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|<span data-ttu-id="e1b21-114">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span><span class="sxs-lookup"><span data-stu-id="e1b21-114">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>|  
|[<span data-ttu-id="e1b21-115">GetGenericParamProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1b21-115">GetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|<span data-ttu-id="e1b21-116">Gets the metadata associated with the generic parameter represented by the specified token.</span><span class="sxs-lookup"><span data-stu-id="e1b21-116">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="e1b21-117">GetMethodSpecProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1b21-117">GetMethodSpecProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|<span data-ttu-id="e1b21-118">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span><span class="sxs-lookup"><span data-stu-id="e1b21-118">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>|  
|[<span data-ttu-id="e1b21-119">GetPEKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1b21-119">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|<span data-ttu-id="e1b21-120">Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope</span><span class="sxs-lookup"><span data-stu-id="e1b21-120">Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope</span></span>|  
|[<span data-ttu-id="e1b21-121">GetVersionString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1b21-121">GetVersionString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|<span data-ttu-id="e1b21-122">Gets the version number of the runtime that was used to build the assembly.</span><span class="sxs-lookup"><span data-stu-id="e1b21-122">Gets the version number of the runtime that was used to build the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e1b21-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e1b21-123">Requirements</span></span>  
 <span data-ttu-id="e1b21-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1b21-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1b21-125">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e1b21-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e1b21-126">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e1b21-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e1b21-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1b21-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1b21-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1b21-128">See also</span></span>

- <xref:System.Reflection.PortableExecutableKinds>
- [<span data-ttu-id="e1b21-129">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e1b21-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="e1b21-130">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1b21-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
