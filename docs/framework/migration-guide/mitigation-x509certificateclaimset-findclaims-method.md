---
title: 'Risk azaltma: X509CertificateClaimSet. Findclaim yöntemi'
description: X509CertificateClaimSet. Findclaim yönteminin, .NET Framework 4.6.1 ' i hedefleyen uygulamalar için nasıl değiştiğini öğrenin.
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: ed9e345f9e48156f37f493caa78e6b3901cecf23
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253576"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="075c6-103">Risk azaltma: X509CertificateClaimSet. Findclaim yöntemi</span><span class="sxs-lookup"><span data-stu-id="075c6-103">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>

<span data-ttu-id="075c6-104">.NET Framework 4.6.1 ' i hedefleyen uygulamalarla başlayarak, <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> yöntemi, `claimType` San ALANıNDAKI tüm DNS girişleriyle bağımsız değişkeni ile eşleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="075c6-104">Starting with apps that target .NET Framework 4.6.1, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="075c6-105">Etki</span><span class="sxs-lookup"><span data-stu-id="075c6-105">Impact</span></span>  

 <span data-ttu-id="075c6-106">Bu değişiklik yalnızca .NET Framework 4.6.1 başlayarak .NET Framework sürümlerini hedefleyen uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="075c6-106">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="075c6-107">.NET Framework önceki sürümlerini hedefleyen uygulamalar için, <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> yöntemi `claimType` yalnızca son DNS girdisiyle bağımsız değişkenle eşleştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="075c6-107">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="075c6-108">Risk azaltma</span><span class="sxs-lookup"><span data-stu-id="075c6-108">Mitigation</span></span>  

 <span data-ttu-id="075c6-109">Bu değişiklik istenmeyen ise, .NET Framework 4.6.1 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar, [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) uygulamanın yapılandırma dosyasının bölümüne aşağıdaki yapılandırma ayarını ekleyerek devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="075c6-109">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />
</runtime>  
```  
  
 <span data-ttu-id="075c6-110">Ayrıca, .NET Framework önceki sürümlerini hedefleyen, ancak .NET Framework 4.6.1 altında çalışan uygulamalar ve sonraki sürümler, [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) uygulamanın yapılandırma dosyasının bölümüne aşağıdaki yapılandırma ayarını ekleyerek bu davranışı kabul edebilir:</span><span class="sxs-lookup"><span data-stu-id="075c6-110">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="075c6-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="075c6-111">See also</span></span>

- [<span data-ttu-id="075c6-112">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="075c6-112">Application compatibility</span></span>](application-compatibility.md)
