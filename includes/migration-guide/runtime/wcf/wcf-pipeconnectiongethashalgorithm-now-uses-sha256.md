---
ms.openlocfilehash: 3cf1740565343558a85fdfa68957773468c28231
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770957"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="73311-101">WCF PipeConnection. GetHashAlgorithm artık SHA256 kullanıyor</span><span class="sxs-lookup"><span data-stu-id="73311-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="73311-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="73311-102">Details</span></span>

<span data-ttu-id="73311-103">Windows Communication Foundation .NET Framework başlayarak, adlandırılmış kanallar için rastgele adlar oluşturmak üzere bir SHA256 karması kullanır.</span><span class="sxs-lookup"><span data-stu-id="73311-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="73311-104">.NET Framework 4,7 ve önceki sürümlerde, bir SHA1 karması kullandı.</span><span class="sxs-lookup"><span data-stu-id="73311-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="73311-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="73311-105">Suggestion</span></span>

<span data-ttu-id="73311-106">Bu değişiklik ile .NET Framework 4.7.1 veya sonraki bir sürümde uyumluluk sorunuyla karşılaşırsanız, app.config dosyanızın bölümüne aşağıdaki satırı ekleyerek geri alabilirsiniz `<runtime>` :</span><span class="sxs-lookup"><span data-stu-id="73311-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the `<runtime>` section of your app.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true" />
  </runtime>
</configuration>

| Name    | Value   |
|:--------|:--------|
| Scope   | Minor   |
| Version | 4.7.1   |
| Type    | Runtime |

#### Affected APIs

Not detectable via API analysis.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
