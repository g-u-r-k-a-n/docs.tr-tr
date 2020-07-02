---
ms.openlocfilehash: 0f87f9e9b87860da97ce96e18104b44ec4327c91
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621388"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="b6d8f-101">WCF PipeConnection. GetHashAlgorithm artık SHA256 kullanıyor</span><span class="sxs-lookup"><span data-stu-id="b6d8f-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="b6d8f-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b6d8f-102">Details</span></span>

<span data-ttu-id="b6d8f-103">Windows Communication Foundation .NET Framework başlayarak, adlandırılmış kanallar için rastgele adlar oluşturmak üzere bir SHA256 karması kullanır.</span><span class="sxs-lookup"><span data-stu-id="b6d8f-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="b6d8f-104">.NET Framework 4,7 ve önceki sürümlerde, bir SHA1 karması kullandı.</span><span class="sxs-lookup"><span data-stu-id="b6d8f-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b6d8f-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="b6d8f-105">Suggestion</span></span>

<span data-ttu-id="b6d8f-106">Bu değişiklik ile .NET Framework 4.7.1 veya sonraki bir sürümde uyumluluk sorunuyla karşılaşırsanız, app.config dosyanızın bölümüne aşağıdaki satırı ekleyerek geri alabilirsiniz <code>&lt;runtime&gt;</code> :</span><span class="sxs-lookup"><span data-stu-id="b6d8f-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the <code>&lt;runtime&gt;</code> section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="b6d8f-107">Name</span><span class="sxs-lookup"><span data-stu-id="b6d8f-107">Name</span></span>    | <span data-ttu-id="b6d8f-108">Değer</span><span class="sxs-lookup"><span data-stu-id="b6d8f-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b6d8f-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="b6d8f-109">Scope</span></span>   |<span data-ttu-id="b6d8f-110">İkincil</span><span class="sxs-lookup"><span data-stu-id="b6d8f-110">Minor</span></span>|
|<span data-ttu-id="b6d8f-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="b6d8f-111">Version</span></span>|<span data-ttu-id="b6d8f-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="b6d8f-112">4.7.1</span></span>|
|<span data-ttu-id="b6d8f-113">Tür</span><span class="sxs-lookup"><span data-stu-id="b6d8f-113">Type</span></span>|<span data-ttu-id="b6d8f-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="b6d8f-114">Runtime</span></span>|
