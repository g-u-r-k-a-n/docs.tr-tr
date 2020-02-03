---
title: Açık kaynaklı .NET kitaplığı Kılavuzu
description: Geliştiricilerin yüksek kaliteli .NET kitaplıkları oluşturmalarına yönelik en iyi yöntem önerileri.
ms.date: 10/17/2018
ms.openlocfilehash: 4c76dfae6ffc39df7f15381be64e33657067d79d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731429"
---
# <a name="open-source-library-guidance"></a><span data-ttu-id="ffa5b-103">Açık kaynak kitaplık kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ffa5b-103">Open-source library guidance</span></span>

<span data-ttu-id="ffa5b-104">Bu kılavuz, geliştiricilerin yüksek kaliteli .NET kitaplıkları oluşturmalarına yönelik öneriler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-104">This guidance provides recommendations for developers to create high-quality .NET libraries.</span></span> <span data-ttu-id="ffa5b-105">Bu belgeler, *nasıl*bir .NET kitaplığı oluşturamadığına göre değil, *neden* ve ne *olduğuna* odaklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-105">This documentation focuses on the *what* and the *why* when building a .NET library, not the *how*.</span></span>

<span data-ttu-id="ffa5b-106">Yüksek kaliteli açık kaynaklı .NET kitaplıklarının yönleri:</span><span class="sxs-lookup"><span data-stu-id="ffa5b-106">Aspects of high-quality open-source .NET libraries:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="ffa5b-107">**Kapsamlı** .NET kitaplıkları birçok platformu, programlama dilini ve uygulamayı desteklemek için çaba harcar.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-107">**Inclusive** - Good .NET libraries strive to support many platforms, programming languages, and applications.</span></span>
> * <span data-ttu-id="ffa5b-108">**Kararlı** -iyi .NET kitaplıkları, çok sayıda kitaplıklarla oluşturulmuş uygulamalarda çalışan .net ekosisteminde birlikte yer vardır.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-108">**Stable** - Good .NET libraries coexist in the .NET ecosystem, running in applications built with many libraries.</span></span>
> * <span data-ttu-id="ffa5b-109">**Geliştirecek şekilde tasarlanan** .NET kitaplıkları, mevcut kullanıcıları desteklerken zaman içinde iyileştirmeli ve gelişmelidir.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-109">**Designed to evolve** - .NET libraries should improve and evolve over time, while supporting existing users.</span></span>
> * <span data-ttu-id="ffa5b-110">**Hata ayıklanabilir** -.NET kitaplıkları, kullanıcılar için harika bir hata ayıklama deneyimi oluşturmak üzere en son araçları kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-110">**Debuggable** - .NET libraries should use the latest tools to create a great debugging experience for users.</span></span>
> * <span data-ttu-id="ffa5b-111">**Güvenilen** -.net kitaplıklarında, en iyi güvenlik uygulamalarını kullanarak NuGet 'e yayımlayarak geliştiricilerin güveni vardır.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-111">**Trusted** - .NET libraries have developers' trust by publishing to NuGet using security best practices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ffa5b-112">Başlarken</span><span class="sxs-lookup"><span data-stu-id="ffa5b-112">Get Started</span></span>](./get-started.md)

## <a name="types-of-recommendations"></a><span data-ttu-id="ffa5b-113">Öneri türleri</span><span class="sxs-lookup"><span data-stu-id="ffa5b-113">Types of recommendations</span></span>

<span data-ttu-id="ffa5b-114">Her makalede dört tür öneri sunulmaktadır: **Do**, **düþünün**, **önleyin**ve **Not**.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-114">Each article presents four types of recommendations: **Do**, **Consider**, **Avoid**, and **Do not**.</span></span> <span data-ttu-id="ffa5b-115">Öneri türü, ne kadar önemli olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-115">The type of recommendation indicates how strongly it should be followed.</span></span>

<span data-ttu-id="ffa5b-116">Neredeyse her zaman bir **Do** önerisi izlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-116">You should almost always follow a **Do** recommendation.</span></span> <span data-ttu-id="ffa5b-117">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ffa5b-117">For example:</span></span>

<span data-ttu-id="ffa5b-118">✔️, bir NuGet paketi kullanarak kitaplığınızı dağıtır.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-118">✔️ DO distribute your library using a NuGet package.</span></span>

<span data-ttu-id="ffa5b-119">Diğer yandan, önerilerin genellikle izlenmesi gerektiğine **dikkat** edin, ancak kuralın meşru özel durumları vardır ve bu kılavuzdan sonra da kötü bir sorun olmaz:</span><span class="sxs-lookup"><span data-stu-id="ffa5b-119">On the other hand, **Consider** recommendations should generally be followed, but there are legitimate exceptions to the rule and you shouldn't feel bad about not following the guidance:</span></span>

<span data-ttu-id="ffa5b-120">✔️ NuGet paketinizi sürüm için [Semver 2.0.0](https://semver.org/) kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-120">✔️ CONSIDER using [SemVer 2.0.0](https://semver.org/) to version your NuGet package.</span></span>

<span data-ttu-id="ffa5b-121">Genellikle iyi bir fikir olmayan ancak kuralın bölünmesi bazen anlamlı hale getirmeyen önerilerden **kaçının** :</span><span class="sxs-lookup"><span data-stu-id="ffa5b-121">**Avoid** recommendations mention things that are generally not a good idea, but breaking the rule sometimes makes sense:</span></span>

<span data-ttu-id="ffa5b-122">❌, tam bir sürümü talep eden NuGet paket başvurularını ÖNLEYIN.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-122">❌ AVOID NuGet package references that demand an exact version.</span></span>

<span data-ttu-id="ffa5b-123">Son **olarak, önermeyin,** neredeyse asla yapmanız gereken bir şeyi gösterir:</span><span class="sxs-lookup"><span data-stu-id="ffa5b-123">And finally, **Do not** recommendations indicate something you should almost never do:</span></span>

<span data-ttu-id="ffa5b-124">❌, kitaplığınızın güçlü adlandırılmış ve tanımlayıcı olmayan sürümlerini yayımlamaz.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-124">❌ DO NOT publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="ffa5b-125">Örneğin, `Contoso.Api` ve `Contoso.Api.StrongNamed`.</span><span class="sxs-lookup"><span data-stu-id="ffa5b-125">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="ffa5b-126">Next</span><span class="sxs-lookup"><span data-stu-id="ffa5b-126">Next</span></span>](get-started.md)
