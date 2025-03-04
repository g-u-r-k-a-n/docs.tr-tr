---
title: Microsoft araçları ile Docker uygulaması DevOps iş akışı
description: Microsoft araçları ile Microsoft platformu ve araçları DevOps iş akışı ile Kapsayıcılı Docker uygulaması yaşam döngüsü
ms.date: 01/06/2021
ms.openlocfilehash: 7f2d380dec046804772ea7d13e764ab6f3224c12
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970160"
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a>Microsoft araçları ile Docker uygulaması DevOps iş akışı

*Microsoft Visual Studio, Azure DevOps Services, Team Foundation Server ve Azure Izleyici, ekibinize projeleri yönetmek ve Kapsayıcılı uygulamaları hızla oluşturmak, test etmek ve dağıtmak için gereken geliştirme ve BT işlemlerine yönelik kapsamlı bir ekosistem sağlar.*

Visual Studio ve Bulutta Azure DevOps Services, şirket içi Team Foundation Server birlikte, geliştirme ekipleri Windows veya Linux 'u hedefleyen Kapsayıcılı uygulamaları verimli bir şekilde oluşturabilir, test edebilir ve serbest bırakabilir.

Microsoft araçları, Azure Izleyici aracılığıyla genel derlemeler ve sürekli tümleştirme (CI) ve Azure DevOps Services ya da Team Foundation Server, sürekli dağıtım (CD) ve hizmet hakkındaki analiz bilgilerini Azure Izleyici aracılığıyla bir araya getirmek için (geliştirme, hazırlama, üretim), Kapsayıcılı uygulamaların belirli uygulamaları (Docker, .NET veya diğer platformlarla herhangi bir bileşim) için ardışık düzeni otomatikleştirebilir. Her kod yürütmesi bir yapı (CI) başlatabilir ve hizmetleri otomatik olarak belirli Kapsayıcılı ortamlara (CD) dağıtır.

Geliştiriciler ve test ediciler, Microsoft Azure şablonlar kullanarak, Docker tabanlı üretim geliştirme ve test ortamlarını kolayca ve hızlı bir şekilde sağlayabilir.

Kapsayıcılı uygulama geliştirmenin karmaşıklığı, iş karmaşıklığı ve ölçeklenebilirlik gereksinimlerine bağlı olarak artmasıyla artar. Bu karmaşıklığa yönelik iyi bir örnek, mikro hizmet mimarilerine dayalı uygulamalardır. Bu tür bir ortamda başarılı olmak için, projeniz yalnızca derleme ve dağıtım değil tüm yaşam döngüsünü otomatikleştirmelidir, ancak aynı zamanda sürümleri telemetri koleksiyonuyla birlikte yönetmelidir. Azure DevOps Services ve Azure aşağıdaki özellikleri sunar:

- Azure DevOps Services/Team Foundation Server kaynak kodu yönetimi (git veya Team Foundation Sürüm Denetimi tabanlı), çevik planlama (çevik, Scrum ve CMMı desteklenir), CI, Release Management ve Çevik takımlar için diğer araçlar.

- Azure DevOps Services ve Team Foundation Server, mikro hizmetler için bir CI, derleme, test, teslim ve sürüm yönetimi işlem hattı oluşturabileceğiniz ve üçüncü taraf genişletmenin güçlü ve büyüyen bir ekosistemini içerir.

- Azure DevOps Services içinde derleme işlem hattınızı bir parçası olarak otomatikleştirilmiş testler çalıştırın.

- Azure DevOps Services DevOps yaşam döngüsünü yalnızca üretim ortamları için değil, aynı zamanda bir/B deneme, [kanarya](https://martinfowler.com/bliki/CanaryRelease.html)ve benzeri gibi test için değil, birden çok ortama gönderim ile açabilir.

- Kuruluşlar, Azure Container Registry ' de depolanan özel görüntülerden (veri, PaaS, vb.), zaten rahat olan araçlarla Azure Resource Manager şablonları kullanarak Azure bileşenleri (Data, PaaS vb.) ile birlikte her türlü bağımlılıktan Docker Kapsayıcıları sağlayabilir.

>[!div class="step-by-step"]
>[Önceki](../design-develop-containerized-apps/build-aspnet-core-applications-linux-containers-aks-kubernetes.md) 
> [Sonraki](docker-application-outer-loop-devops-workflow.md)
