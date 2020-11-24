---
title: IDefinitionAppId Arabirimi
ms.date: 03/30/2017
api_name:
- IDefinitionAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionAppId
helpviewer_keywords:
- IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type:
- apiref
ms.openlocfilehash: 1e6c42d8e74d2d3e7925c657c67832f662416e64
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673879"
---
# <a name="idefinitionappid-interface"></a><span data-ttu-id="4d899-102">IDefinitionAppId Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d899-102">IDefinitionAppId Interface</span></span>

<span data-ttu-id="4d899-103">Geçerli kapsamda uygulamayı tanımlayan kod için benzersiz tanımlayıcıyı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4d899-103">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4d899-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4d899-104">Methods</span></span>  
  
|<span data-ttu-id="4d899-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4d899-105">Method</span></span>|<span data-ttu-id="4d899-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d899-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|<span data-ttu-id="4d899-107">Bu nesnedeki kodu temsil eden biçimli bir dize alır `IDefinitionAppId` .</span><span class="sxs-lookup"><span data-stu-id="4d899-107">Gets a formatted string that represents the code in this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_Codebase`|<span data-ttu-id="4d899-108">Bu `IDefinitionAppId` nesnenin kodunu belirtilen biçimli dize değerine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4d899-108">Sets the code of this `IDefinitionAppId` object to the specified formatted string value.</span></span>|  
|`IDefinitionAppId::EnumAppPath`|<span data-ttu-id="4d899-109">Geçerli uygulama yolundaki derlemeleri içeren bir [IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md) nesnesine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="4d899-109">Gets an interface pointer to an [IEnumDefinitionIdentity](ienumdefinitionidentity-interface.md) object that contains the assemblies in the current application path.</span></span>|  
|`IDefinitionAppId::SetAppPath`|<span data-ttu-id="4d899-110">Geçerli kapsamdaki derleme için uygulama yolunu, belirtilen [IDefinitionIdentity](idefinitionidentity-interface.md) nesnesinin başvurduğu değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4d899-110">Sets the application path for the assembly in the current scope to the value referenced by the specified [IDefinitionIdentity](idefinitionidentity-interface.md) object.</span></span>|  
|`IDefinitionAppId::get_SubscriptionId`|<span data-ttu-id="4d899-111">Bu nesne için bir abonelik için belirteç tanımlayıcısının dize gösterimine yönelik bir işaretçi alır `IDefinitionAppId` .</span><span class="sxs-lookup"><span data-stu-id="4d899-111">Gets a pointer to a string representation of the token identifier for a subscription to this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_SubscriptionId`|<span data-ttu-id="4d899-112">Bu nesne için bir aboneliğin Belirteç tanımlayıcısını `IDefinitionAppId` belirtilen dize değerine ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4d899-112">Sets the token identifier for a subscription to this `IDefinitionAppId` object to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4d899-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4d899-113">Requirements</span></span>  

 <span data-ttu-id="4d899-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d899-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d899-115">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="4d899-115">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="4d899-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d899-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d899-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d899-117">See also</span></span>

- [<span data-ttu-id="4d899-118">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4d899-118">Fusion Interfaces</span></span>](fusion-interfaces.md)
