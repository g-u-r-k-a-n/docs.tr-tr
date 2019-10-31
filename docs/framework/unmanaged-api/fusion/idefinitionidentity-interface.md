---
title: IDefinitionIdentity Arabirimi
ms.date: 03/30/2017
api_name:
- IDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionIdentity
helpviewer_keywords:
- IDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: ce5ba888-5fbe-4efd-91cf-f0ff94d8428b
topic_type:
- apiref
ms.openlocfilehash: 59578e1d3a66809c86f7daad1b208df2ae09568d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108036"
---
# <a name="idefinitionidentity-interface"></a><span data-ttu-id="ec1ae-102">IDefinitionIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec1ae-102">IDefinitionIdentity Interface</span></span>
<span data-ttu-id="ec1ae-103">Geçerli kapsamdaki uygulamayı tanımlayan kodun benzersiz imzasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ec1ae-103">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ec1ae-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ec1ae-104">Methods</span></span>  
  
|<span data-ttu-id="ec1ae-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ec1ae-105">Method</span></span>|<span data-ttu-id="ec1ae-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec1ae-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|<span data-ttu-id="ec1ae-107">Belirtilen öznitelik değişiklikleri dışında, bu `IDefinitionIdentity`özdeş olan yeni bir `IDefinitionIdentity` nesnesine bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="ec1ae-107">Gets an interface pointer to a new `IDefinitionIdentity` object that is identical to this `IDefinitionIdentity`, except for the specified attribute changes.</span></span>|  
|`IDefinitionIdentity::EnumAttributes`|<span data-ttu-id="ec1ae-108">Bu `IDefinitionIdentity`ilişkili öznitelikleri içeren bir [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) nesnesine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="ec1ae-108">Gets an interface pointer to an [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) object that contains the attributes associated with this `IDefinitionIdentity`.</span></span>|  
|`IDefinitionIdentity::GetAttribute`|<span data-ttu-id="ec1ae-109">Belirtilen ad alanında belirtilen ada sahip özniteliğin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="ec1ae-109">Gets the value of the attribute with the specified name in the specified namespace.</span></span>|  
|`IDefinitionIdentity::SetAttribute`|<span data-ttu-id="ec1ae-110">Belirtilen ad alanında belirtilen ada sahip özniteliği belirtilen değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ec1ae-110">Sets the attribute that has the specified name in the specified namespace to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ec1ae-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec1ae-111">Requirements</span></span>  
 <span data-ttu-id="ec1ae-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec1ae-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec1ae-113">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="ec1ae-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="ec1ae-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec1ae-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec1ae-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec1ae-115">See also</span></span>

- [<span data-ttu-id="ec1ae-116">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ec1ae-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
