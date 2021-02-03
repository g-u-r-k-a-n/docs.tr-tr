---
title: Merkezi yapılandırma
description: Azure Uygulama yapılandırması ve AzureKey kasasını kullanarak bulutta yerel uygulamalar için yapılandırmayı merkezileştirme.
ms.date: 01/19/2021
ms.openlocfilehash: 770c0c19a6de01250c59a586badb6a4afa2e9ae5
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99505719"
---
# <a name="centralized-configuration"></a>Merkezi yapılandırma

Her şeyin tek bir örnek içinde çalıştığı tek parçalı bir uygulamanın aksine, bulutta yerel bir uygulama, sanal makineler, kapsayıcılar ve coğrafi bölgeler arasında dağıtılan bağımsız hizmetlerden oluşur. Onlarca birbirine bağlı hizmetlerin yapılandırma ayarlarını yönetmek zor olabilir. Farklı konumlarda yapılandırma ayarlarının yinelenen kopyaları, yönetim açısından hataya açık ve zor bir hatadır. Merkezi yapılandırma, dağıtılmış bulutta yerel uygulamalar için kritik bir gereksinimdir.

[Bölüm 1](introduction.md)' de anlatıldığı gibi Twelve-Factor uygulama önerileri, kod ve yapılandırma arasında katı ayrım gerektirir. Yapılandırma, uygulamadan dışarıdan depolanmalıdır ve gerektiğinde okunabilir olmalıdır. Yapılandırma değerlerini sabitler veya kodda değişmez değer olarak depolamak bir ihladir. Aynı yapılandırma değerleri genellikle aynı uygulamadaki birçok hizmet tarafından kullanılır. Ayrıca, geliştirme, test ve üretim gibi birden çok ortamda aynı değerleri desteklememiz gerekir. En iyi uygulama, bunları merkezi bir yapılandırma deposunda saklar.

Azure bulutu birçok harika seçenek sunar.

## <a name="azure-app-configuration"></a>Azure Uygulama Yapılandırması

[Azure Uygulama yapılandırması](/azure/azure-app-configuration/overview) , gizli olmayan yapılandırma ayarlarını güvenli, merkezi bir konumda depolayan, tam olarak yönetilen bir Azure hizmetidir. Depolanan değerler, birden fazla hizmet ve uygulama arasında paylaşılabilir.

Hizmetin kullanımı basittir ve çeşitli avantajlar sunar:

- Esnek anahtar/değer gösterimleri ve eşlemeler
- Azure etiketleriyle etiketleme
- Yönetim için adanmış Kullanıcı arabirimi
- Hassas bilgilerin şifrelenmesi
- Sorgulama ve toplu alma

Azure Uygulama yapılandırması, yedi gün için anahtar-değer ayarlarında yapılan değişiklikleri tutar. Noktadan noktaya anlık görüntü özelliği, bir ayarın geçmişini yeniden yapılandırmanızı ve hatta başarısız bir dağıtım için geri dönmenizi sağlar.

Yapılandırma deposuna aşırı çağrı yapmaktan kaçınmak için uygulama yapılandırması her ayarı otomatik olarak önbelleğe alır. Yenileme işlemi, yapılandırma deposundaki değeri değiştiğinde bile bu ayarı güncelleştirmek için bir ayarın önbelleğe alınmış değerinin süresinin dolacağını bekler. Varsayılan önbellek süre sonu zamanı 30 saniyedir. Süre sonu süresini geçersiz kılabilirsiniz.

Uygulama yapılandırması, yoldaki ve bekleyen tüm yapılandırma değerlerini şifreler. Anahtar adları ve Etiketler, yapılandırma verilerini almak için dizinler olarak kullanılır ve şifrelenmez.

Uygulama yapılandırması sıkı güvenlik sağlar, ancak Azure Key Vault uygulama gizli dizileri depolamak için de en iyi yerdir. Key Vault, donanım düzeyinde şifreleme, ayrıntılı erişim ilkeleri ve sertifika döndürme gibi yönetim işlemleri sağlar. Key Vault depolanan gizli dizileri referans eden uygulama yapılandırma değerleri oluşturabilirsiniz.

## <a name="azure-key-vault"></a>Azure Key Vault

Key Vault, gizli dizileri güvenli bir şekilde depolamak ve bunlara erişmek için yönetilen bir hizmettir. Gizli dizi; API anahtarları, parolalar veya sertifikalar gibi erişimi sıkı bir şekilde denetlemek istediğiniz tüm öğelerdir. Kasa, mantıksal bir gizli dizi grubudur.

Key Vault, gizli dizilerin yanlışlıkla sızdırılma olasılığını büyük oranda azaltır. Key Vault kullanırken, uygulama geliştiricilerinin güvenlik bilgilerini uygulamalarında depolaması artık gerekli değildir. Bu uygulama, bu bilgileri kodunuzun içinde depolama gereksinimini ortadan kaldırır. Örneğin, bir uygulamanın bir veritabanına bağlanması gerekebilir. Bağlantı dizesini uygulamanın kodunda depolamak yerine, Key Vault ' de güvenli bir şekilde depolayabilirsiniz.

Uygulamalarınız, URI 'Leri kullanarak ihtiyaç duydukları bilgilere güvenli bir şekilde erişebilir. Bu URI 'Ler, uygulamaların belirli bir gizli sürümü almasına izin verir. Key Vault depolanan gizli bilgilerin hiçbirini korumak için özel kod yazmanıza gerek yoktur.

Key Vault erişim, uygun arayan kimlik doğrulaması ve yetkilendirme gerektirir. Genellikle, her bir bulutta yerel mikro hizmet bir ClientID/ClientSecret birleşimini kullanır. Bu kimlik bilgilerinin kaynak denetimi dışında tutulması önemlidir. En iyi uygulama, bunları uygulamanın ortamında ayarlamanıza olanak sağlar. AKS 'ten Key Vault doğrudan erişim, [Key Vault FlexVolume](https://github.com/Azure/kubernetes-keyvault-flexvol)kullanılarak elde edilebilir.

## <a name="configuration-in-eshop"></a>EShop 'de yapılandırma

EShopOnContainers uygulaması, her mikro hizmetle yerel uygulama ayarları dosyalarını içerir. Bu dosyalar kaynak denetimine iade edilir, ancak bağlantı dizeleri veya API anahtarları gibi üretim sırları dahil değildir. Üretimde, hizmet başına ortam değişkenleriyle bireysel ayarların üzerine yazılabilir. Ortam değişkenlerinde ekleme gizli dizileri barındırılan uygulamalar için yaygın bir uygulamadır, ancak merkezi bir yapılandırma deposu sağlamaz. Yapılandırma ayarlarının merkezi yönetimini desteklemek için her mikro hizmet, yerel ayarları veya Azure Key Vault ayarları kullanımı arasında geçiş yapmak için bir ayar içerir.

## <a name="references"></a>Başvurular

- [EShopOnContainers mimarisi](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Architecture)
- [Yüksek ölçeklenebilirlik ve kullanılabilirlik için mikro hizmetleri ve çok kapsayıcılı uygulamaları yönetme](../microservices/architect-microservice-container-applications/scalable-available-multi-container-microservice-applications.md)
- [Azure API Management](/azure/api-management/api-management-key-concepts)
- [Azure SQL veritabanına genel bakış](/azure/sql-database/sql-database-technical-overview)
- [Redis için Azure Önbelleği](https://azure.microsoft.com/services/cache/)
- [MongoDB için Azure Cosmos DB API’si](/azure/cosmos-db/mongodb-introduction)
- [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview)
- [Azure İzleyici'ye genel bakış](/azure/azure-monitor/overview)
- [eShopOnContainers: AKS 'te Kubernetes kümesi oluşturma](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Deploy-to-Azure-Kubernetes-Service-(AKS)#create-kubernetes-cluster-in-aks)
- [eShopOnContainers: Azure Dev Spaces](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Azure-Dev-Spaces)
- [Azure Dev Spaces](/azure/dev-spaces/about)

>[!div class="step-by-step"]
>[Önceki](deploy-eshoponcontainers-azure.md) 
> [Sonraki](scale-applications.md)
