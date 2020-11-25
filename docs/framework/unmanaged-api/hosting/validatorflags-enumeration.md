---
title: ValidatorFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- ValidatorFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ValidatorFlags
helpviewer_keywords:
- ValidatorFlags enumeration [.NET Framework hosting]
ms.assetid: a3f5c266-3fcc-4ad1-aaf5-4cdbe26304ad
topic_type:
- apiref
ms.openlocfilehash: 92c430cdb8b46cf75dde9a8395ce713116dc05a5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732875"
---
# <a name="validatorflags-enumeration"></a><span data-ttu-id="7ecc6-102">ValidatorFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7ecc6-102">ValidatorFlags Enumeration</span></span>

<span data-ttu-id="7ecc6-103">[ICLRValidator:: Validate](iclrvalidator-validate-method.md) metoduna yapılan bir çağrıda gerçekleştirilmesi gereken doğrulamanın türünü belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-103">Contains values that indicate the type of validation that should be performed in a call to the [ICLRValidator::Validate](iclrvalidator-validate-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ecc6-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="7ecc6-104">Syntax</span></span>  
  
```cpp  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a><span data-ttu-id="7ecc6-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7ecc6-105">Members</span></span>  
  
|<span data-ttu-id="7ecc6-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7ecc6-106">Member</span></span>|<span data-ttu-id="7ecc6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ecc6-107">Description</span></span>|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|<span data-ttu-id="7ecc6-108">Yürütülebilir dosyadaki yalnızca Microsoft ara dili 'nin (MSIL) doğrulanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-108">Specifies that only the Microsoft intermediate language (MSIL) in the executable file should be validated.</span></span>|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|<span data-ttu-id="7ecc6-109">Yalnızca yürütülebilir dosyanın biçiminin doğrulanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-109">Specifies that only the format of the executable file should be validated.</span></span>|  
|`VALIDATOR_EXTRA_VERBOSE`|<span data-ttu-id="7ecc6-110">Tüm doğrulama türlerinin üzerinde gerçekleştirilmesi ve bildirilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-110">Specifies that all types of validation should be performed and reported on.</span></span>|  
|`VALIDATOR_NOCHECK_PEFORMAT`|<span data-ttu-id="7ecc6-111">Yürütülebilir dosyanın biçiminin doğrulanmamış olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-111">Specifies that the format of the executable file should not be validated.</span></span>|  
|`VALIDATOR_SHOW_SOURCE_LINES`|<span data-ttu-id="7ecc6-112">Doğrulama hatası iletilerinin, doğrulama hatalarını oluşturan kaynak kodu satırlarını içermesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-112">Specifies that validation error messages should include the lines of source code that raise validation errors.</span></span> <span data-ttu-id="7ecc6-113">Bu alan değeri 2,0 .NET Framework sürümünde geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-113">This field value is not valid in the .NET Framework version 2.0.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7ecc6-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ecc6-114">Requirements</span></span>  

 <span data-ttu-id="7ecc6-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ecc6-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ecc6-116">**Üst bilgi:** IValidator. IDL, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="7ecc6-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="7ecc6-117">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7ecc6-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7ecc6-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ecc6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ecc6-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ecc6-119">See also</span></span>

- [<span data-ttu-id="7ecc6-120">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ecc6-120">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="7ecc6-121">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="7ecc6-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
