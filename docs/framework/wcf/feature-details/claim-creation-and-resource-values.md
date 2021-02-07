---
description: 'Daha fazla bilgi edinin: talep oluşturma ve kaynak değerleri'
title: Beyan Oluşturma ve Kaynak Değerleri
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], creation and resource values
ms.assetid: 30431f76-cbe7-4bad-bad7-8e43e23a82d4
ms.openlocfilehash: 20763c683c5bf5734a21a4315576a8f9f354ff35
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734990"
---
# <a name="claim-creation-and-resource-values"></a><span data-ttu-id="39dea-103">Beyan Oluşturma ve Kaynak Değerleri</span><span class="sxs-lookup"><span data-stu-id="39dea-103">Claim Creation and Resource Values</span></span>

<span data-ttu-id="39dea-104"><xref:System.IdentityModel.Claims.Claim>Sınıfı, yerleşik talep türlerinin örneklerini oluşturmak için çeşitli yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="39dea-104">The <xref:System.IdentityModel.Claims.Claim> class provides several methods for creating instances of built-in claims types.</span></span> <span data-ttu-id="39dea-105">Bu yöntemlerin her biri, sağlanan kaynakta hiçbir anlam veya biçimlendirme denetimi gerçekleştirmez:</span><span class="sxs-lookup"><span data-stu-id="39dea-105">Of these methods, the following perform no semantic or format checking on the supplied resource:</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateDnsClaim%2A>  
  
- <span data-ttu-id="39dea-106"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (bayt dizisinin uzunluğunu veya içeriğini denetlemez)</span><span class="sxs-lookup"><span data-stu-id="39dea-106"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateNameClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateSpnClaim%2A>  
  
- <span data-ttu-id="39dea-107"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (bayt dizisinin uzunluğunu veya içeriğini denetlemez)</span><span class="sxs-lookup"><span data-stu-id="39dea-107"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateUpnClaim%2A>  
  
 <span data-ttu-id="39dea-108">Geçirilen kaynak değerlerinin doğru biçimde veya doğru türde bilgileri (veya her ikisi de) içerdiğinden emin olmak için yukarıdaki Yöntemler çağrılırken dikkatli olunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="39dea-108">Care should be taken when calling the above methods to ensure that the resource values passed in are of the correct format or contain the correct kind of information (or both).</span></span>  
  
 <span data-ttu-id="39dea-109">Aşağıdaki yöntemler belirli türleri alır:</span><span class="sxs-lookup"><span data-stu-id="39dea-109">The following methods take specific types:</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateDenyOnlyWindowsSidClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateMailAddressClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateRsaClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateUriClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateWindowsSidClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateX500DistinguishedNameClaim%2A>  
  
## <a name="see-also"></a><span data-ttu-id="39dea-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39dea-110">See also</span></span>

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [<span data-ttu-id="39dea-111">Kimlik Modeliyle Beyanlar ve Yetkilendirmeyi Yönetme</span><span class="sxs-lookup"><span data-stu-id="39dea-111">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)
