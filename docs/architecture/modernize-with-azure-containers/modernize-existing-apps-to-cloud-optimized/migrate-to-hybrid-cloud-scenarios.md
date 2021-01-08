---
title: Karma bulut senaryolarına geçiş
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | Karma bulut senaryolarına geçiş
ms.date: 12/21/2020
ms.openlocfilehash: d5bf7f08381f3718061742b37c73604d8e57f1e2
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025231"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a>Karma bulut senaryolarına geçiş

Bazı kuruluşlar ve kuruluşlar, bazı uygulamalarını, düzenlemeler veya kendi ilkeleri nedeniyle Microsoft Azure veya başka bir genel bulut gibi genel bulutlara geçiremez. Ancak, herhangi bir kuruluşun bazı uygulamalarını genel bulutta ve şirket içi diğer uygulamalarda sahip olma olasılığı yüksektir. Ancak, karma bir ortam, genel bulutlarda kullanılan farklı platformlar ve teknolojiler ve şirket içi ortamlardan dolayı ortamlarda aşırı karmaşıklığa yol açabilir.

Microsoft, bir Azure hibrit bulutu 'nda tutarlılığın sağladığından, mevcut varlıklarınızı şirket içinde ve genel bulutta iyileştirilebilmenizi sağlayan en iyi karma bulut çözümünü sağlar. Var olan becerileri en üst düzeye çıkarabilir ve bulutta veya şirket içinde çalışabilen uygulamalar oluşturmaya yönelik esnek ve birleştirilmiş bir yaklaşım edinebilirsiniz (Şirket içi) ve Azure (genel bulut) Azure Stack sayesinde.

Güvenlik 'e geldiğinde, karma bulutunuz genelinde yönetim ve güvenliği merkezileştirme sağlayabilirsiniz. Şirket içi ve bulut uygulamaları için çoklu oturum açma olanağı sunarak, veri merkezinizden buluta kadar tüm varlıklar üzerinde denetim edinebilirsiniz. Active Directory karma buluta genişleterek ve kimlik yönetimi 'ni kullanarak bu işlevselliği gerçekleştirirsiniz.

Son olarak, verileri sorunsuzca dağıtabilir ve analiz edebilir, bulut ve şirket içi varlıklar için aynı sorgu dillerini kullanabilir ve Azure 'da, kaynağına bakılmaksızın verilerinizi zenginleştirmek için analiz ve derin öğrenme uygulayabilirsiniz.

## <a name="azure-stack"></a>Azure Stack

Azure Stack, kuruluşunuzun veri merkezinden Azure hizmetleri sunmanıza olanak tanıyan bir karma bulut platformudur. Azure Stack, kenar ve bağlı olmayan ortamlar gibi önemli senaryolarda modern uygulamalarınızın yeni seçeneklerini destekleyecek şekilde tasarlanmıştır veya belirli güvenlik ve uyumluluk gereksinimlerini karşılayarak.

Şekil 4-13, Microsoft 'un sunduğu gerçek hibrit bulut platformunun bir genel görünümünü gösterir.

![Azure Stack ve Azure ile Microsoft hibrit bulut platformu diyagramı.](./media/migrate-to-hybrid-cloud-scenarios/microsoft-hybrid-cloud-platform.png)

**Şekil 4-13.** Azure Stack ve Azure ile Microsoft hibrit bulut platformu

Azure Stack, gereksinimlerinizi karşılamak için iki dağıtım seçeneği sunulur:

- Azure Stack tümleşik sistemler

- Azure Stack Geliştirme Seti

### <a name="azure-stack-integrated-systems"></a>Azure Stack tümleşik sistemler

Azure Stack tümleşik sistemler, Microsoft ve donanım iş ortaklarının bir ortaklığı aracılığıyla sunulur. İş ortaklığı, yönetimin basitliği ile dengeli bulut adımlı yenilik sunan bir çözüm oluşturur. Azure Stack, donanım ve yazılım tümleştirilmiş bir sistem olarak sunulduğundan, doğru esneklik ve denetim elde edersiniz, ancak yine de buluttan yeniliği benimsemiş olursunuz. 4 ile 12 düğümden oluşan tümleşik sistemleri Azure Stack ve donanım ortağı ve Microsoft tarafından ortaklaşa desteklenir. Üretim iş yükleriniz için yeni senaryolar uygulamak üzere Azure Stack tümleşik sistemleri kullanın.

### <a name="azure-stack-development-kit"></a>Azure Stack Geliştirme Seti

Microsoft Azure Stack Development Kit, Azure Stack hakkında değerlendirmek ve bilgi edinmek için kullanabileceğiniz Azure Stack tek düğümlü bir dağıtımdır. Azure ile tutarlı olan API 'Leri ve araçları kullanarak geliştirebileceğiniz bir geliştirici ortamı olarak Azure Stack Geliştirme Seti de kullanabilirsiniz. Azure Stack Geliştirme Seti, üretim ortamı olarak kullanılmak üzere tasarlanmamıştır.

### <a name="additional-resources"></a>Ek kaynaklar

- **Azure hibrit bulutu**

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- **Azure Stack**

    <https://azure.microsoft.com/overview/azure-stack/>

- **Windows kapsayıcıları için hizmet hesaplarını Active Directory**

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- **Active Directory desteğiyle kapsayıcı oluşturma**

    <https://docs.microsoft.com/archive/blogs/containerstuff/create-a-container-with-active-directory-support>

- **Azure Hibrit Avantajı lisanslama**

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
>[Önceki](life-cycle-ci-cd-pipelines-devops-tools.md) 
> [Sonraki](../walkthroughs-technical-get-started-overview.md)
