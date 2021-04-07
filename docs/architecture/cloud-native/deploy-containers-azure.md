---
title: Azure’da kapsayıcıları dağıtma
description: Azure Container Registry, Azure Kubernetes hizmeti ve Azure Dev Spaces Azure 'da kapsayıcı dağıtma.
ms.date: 04/13/2020
ms.openlocfilehash: f8b029f31ba493b3a777e12ca72854145ef312c4
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497417"
---
# <a name="deploying-containers-in-azure"></a>Azure’da kapsayıcıları dağıtma

Bu bölümde ve Bölüm 1 ' de kapsayıcılar tartışıyoruz. Kapsayıcıların taşınabilirlik dahil olmak üzere bulutta yerel uygulamalara birçok avantaj sunduğumuz görüldü. Azure bulutunda, aynı Kapsayıcılı Hizmetleri hazırlama ve üretim ortamları arasında dağıtabilirsiniz. Azure, bu Kapsayıcılı iş yüklerini barındırmak için çeşitli seçenekler sunar:

- Azure Kubernetes Services (AKS)
- Azure Container Instance (ACI)
- Kapsayıcılar için Azure Web Apps

## <a name="azure-container-registry"></a>Azure Container Registry

Bir mikro hizmeti kapsayıcıında, önce bir kapsayıcı "görüntüsü" oluşturursunuz. Görüntü, hizmet kodu, bağımlılıklar ve çalışma zamanının ikili bir gösterimidir. Docker API 'sindeki komutunu kullanarak el ile bir görüntü oluşturmanıza karşın `Docker Build` , otomatik derleme sürecinin bir parçası olarak daha iyi bir yaklaşım oluşturmanız daha iyidir.

Oluşturulduktan sonra kapsayıcı görüntüleri kapsayıcı kayıt defterlerine depolanır. Kapsayıcı görüntülerini oluşturmanıza, depolamanıza ve yönetmenize olanak sağlar. Hem ortak hem de özel çok sayıda kayıt defterleri mevcuttur. Azure Container Registry (ACR), Azure bulutundaki tam olarak yönetilen bir kapsayıcı kayıt defteri hizmetidir. Azure ağ içindeki görüntülerinizi devam ettirir ve bunları Azure Container konaklarına dağıtma süresini azaltır. Ayrıca, diğer Azure kaynakları için kullandığınız güvenlik ve kimlik yordamlarını kullanarak bunları da güvenli hale getirebilirsiniz.

[Azure Portal](/azure/container-registry/container-registry-get-started-portal), [Azure CLI](/azure/container-registry/container-registry-get-started-azure-cli)veya [PowerShell araçlarını](/azure/container-registry/container-registry-get-started-powershell)kullanarak bir Azure Container Registry oluşturursunuz. Azure 'da bir kayıt defteri oluşturmak basittir. Azure aboneliği, kaynak grubu ve benzersiz bir ad gerektirir. Şekil 3-11, üzerinde barındırılacak bir kayıt defteri oluşturmak için temel seçenekleri gösterir `registryname.azurecr.io` .

![Kapsayıcı kayıt defteri oluşturma](./media/create-container-registry.png)

**Şekil 3-11**. Kapsayıcı kayıt defteri oluşturma

Kayıt defterini oluşturduktan sonra, kullanabilmeniz için kimlik doğrulaması yapmanız gerekir. Genellikle, Azure CLı komutunu kullanarak kayıt defterinde oturum açmanız gerekir:

```azurecli
az acr login --name *registryname*
```

Kimliği doğrulandıktan sonra Docker komutlarını kullanarak kapsayıcı görüntülerini buna gönderebilirsiniz. Ancak bunu yapabilmeniz için önce, görüntünüzü ACR oturum açma sunucunuzun tam adı (URL) ile etiketlemelisiniz. *Registryname*. azurecr.io biçiminde olacaktır.

```console
docker tag mycontainer myregistry.azurecr.io/mycontainer:v1
```

Görüntüyü etiketledikten sonra, `docker push` görüntüyü ACR örneğinize göndermek için komutunu kullanın.

```console
docker push myregistry.azurecr.io/mycontainer:v1
```

Bir görüntüyü kayıt defterine gönderdikten sonra, bu komutu kullanarak görüntüyü yerel Docker ortamınızdan kaldırmak iyi bir fikirdir:

```console
docker rmi myregistry.azurecr.io/mycontainer:v1
```

En iyi uygulama olarak, geliştiricilerin resimleri bir kapsayıcı kayıt defterine el ile göndermemesi gerekir. Bunun yerine, bu işlemden GitHub veya Azure DevOps gibi bir araçta tanımlanan derleme işlem hattı sorumludur. [Cloud-Native DevOps](devops.md)bölümünde daha fazla bilgi edinin.

## <a name="acr-tasks"></a>ACR Görevleri

[ACR görevleri](/azure/container-registry/container-registry-tasks-overview) , Azure Container Registry kullanılabilen bir özellikler kümesidir. Azure bulutunda kapsayıcı görüntüleri oluşturup yöneterek [iç döngü geliştirme döngünüzü](../containerized-lifecycle/design-develop-containerized-apps/docker-apps-inner-loop-workflow.md) genişletir. `docker build` `docker push` Geliştirme makinenizde bir ve yerel olarak çağırmak yerine, bulutta ACR görevleri tarafından otomatik olarak işlenir.

Aşağıdaki AZ CLı komutu her ikisi de bir kapsayıcı görüntüsü oluşturur ve ACR 'ye gönderir:

```azurecli
# create a container registry
az acr create --resource-group myResourceGroup --name myContainerRegistry008 --sku Basic

# build container image in ACR and push it into your container regsitry
az acr build --image sample/hello-world:v1  --registry myContainerRegistry008 --file Dockerfile .
```

Önceki komut bloğundan görebileceğiniz gibi, geliştirme makinenize Docker Desktop yüklemeniz gerekmez. Ayrıca, her iki kaynak kodunda ve temel görüntü güncelleştirmelerinde, kapsayıcılar görüntülerini yeniden oluşturmak için ACR görev tetikleyicilerini yapılandırabilirsiniz.

## <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Bu bölümde Azure Kubernetes hizmeti (AKS) ile tartışıyoruz. Kapsayıcının yerleşik bulut Yerel uygulamalarını yöneten kapsayıcı Orchestrator 'ın de olduğunu gördük.

Bir görüntüyü bir kayıt defterine dağıttıktan sonra ACR gibi, AKS 'leri otomatik olarak çekmek ve dağıtmak için yapılandırabilirsiniz. Bir CI/CD işlem hattı varken, güncelleştirmeleri hızlı bir şekilde dağıtmaya yönelik riskleri en aza indirmek için bir  [kanarya yayın](https://martinfowler.com/bliki/CanaryRelease.html) stratejisi yapılandırabilirsiniz. Uygulamanın yeni sürümü başlangıçta hiçbir trafik yönlendirilmeden üretimde yapılandırılır. Daha sonra, sistem yeni dağıtılan sürüme küçük bir Kullanıcı yüzdesi yönlendirir. Ekip yeni sürümde güvenli bir şekilde güvendiğinden, daha fazla örnek alabilir ve eskisini devre dışı bırakabilirsiniz. AKS bu dağıtım stilini kolayca destekler.

Azure 'daki kaynakların çoğunda olduğu gibi portal, komut satırı veya Helm ya da Terkform gibi Otomasyon araçlarını kullanarak bir Azure Kubernetes hizmet kümesi oluşturabilirsiniz. Yeni bir kümeye başlamak için aşağıdaki bilgileri sağlamanız gerekir:

- Azure aboneliği
- Kaynak grubu
- Kubernetes küme adı
- Bölge
- Kubernetes sürümü
- DNS adı ön eki
- Düğüm boyutu
- Düğüm sayısı

Bu bilgiler başlamak için yeterlidir. Azure portal oluşturma sürecinin bir parçası olarak, kümenizin aşağıdaki özellikleri için seçenekleri de yapılandırabilirsiniz:

- Ölçek
- Kimlik Doğrulaması
- Ağ
- İzleme
- Etiketler

Bu [hızlı başlangıçta Azure Portal kullanarak bir AKS kümesi dağıtma işlemi adım adım](/azure/aks/kubernetes-walkthrough-portal)açıklanmaktadır.

## <a name="azure-dev-spaces"></a>Azure Dev Spaces

Bulutta yerel uygulamalar hızlı bir şekilde büyük ve karmaşık bir şekilde büyüyerek önemli işlem kaynaklarının çalıştırılmasını gerektirir. Bu senaryolarda, tüm uygulama bir geliştirme makinesinde (özellikle bir dizüstü bilgisayar) barındırılamaz. Azure Dev Spaces, AKS kullanarak bu sorunu gidermek için tasarlanmıştır. Geliştiricilerin, bir AKS geliştirme kümesinde uygulamanın geri kalanını barındırırken hizmetlerinin yerel bir sürümüyle çalışmasını sağlar.

Geliştiriciler, Kapsayıcılı uygulamanın tamamını içeren bir AKS kümesinde çalışan (geliştirme) örneği paylaşır. Ancak, hizmetlerini yerel olarak geliştirmek üzere makinesinde ayarlanan kişisel alanları kullanırlar. Hazırlık yapıldığında, bağımlılıklar çoğaltılmaksızın AKS kümesindeki uçtan uca test ederler. Azure Dev Spaces, yerel makineden AKS Hizmetleri ile kod birleştirir. Geliştiriciler Visual Studio veya Visual Studio Code kullanarak doğrudan Kubernetes 'te kodu hızla yineleyebilir ve hata ayıklamanıza olanak sağlar.

Azure Dev Spaces değerini anlamak için, bu teklifi Gato Monroy 'tan paylaşalım, Microsoft Azure kapsayıcıların zaman adayı:

> "Her biri kendi yapılandırma ve Destek Hizmetleri olan onlarca bileşenden oluşan karmaşık mikro hizmetler uygulamasındaki bir hatayı gidermeye çalışan yeni bir çalışan olduğunuzu düşünün. Başlamak için, yerel geliştirme ortamınızı, IDE 'nizi ayarlama, araç zinciri oluşturma, Kapsayıcılı hizmet bağımlılıkları, yerel bir Kubernetes ortamı, hizmet yedekleme için molar ve daha fazlasını içeren üretime benzetebilmek üzere yapılandırmanız gerekir. Geliştirme ortamınızı ayarlamaya yönelik tüm zamanlı olarak, ilk hatanın bu kadar gün sürebiliyor.
> Ya da dev Spaces ve AKS kullanabilirsiniz. "

Azure Dev Spaces ile çalışma işlemi aşağıdaki adımları içerir:

1. Geliştirme alanını oluşturun.
2. Kök dev alanını yapılandırın.
3. Bir alt dev alanı yapılandırın (sisteminizin kendi sürümünüz için).
4. Geliştirme alanına bağlanın.

Bu adımların tümü, Azure CLı ve yeni  `azds` komut satırı araçları kullanılarak gerçekleştirilebilir. Örneğin, belirli bir Kubernetes kümesi için yeni bir Azure dev alanı oluşturmak için, şöyle bir komut kullanacaksınız:

```azurecli
az aks use-dev-spaces -g my-aks-resource-group -n MyAKSCluster
```

Ardından, `azds prep` uygulamayı çalıştırmak için gerekli Docker ve hele grafik varlıklarını oluşturmak için komutunu kullanabilirsiniz. Ardından, kodunuzu kullanarak AKS 'de çalıştırırsınız `azds up` . Bu komutu ilk kez çalıştırdığınızda HELI grafiği yüklenecektir. Kapsayıcılar, yönergelerinizi temel alarak oluşturulup dağıtılacak. Bu görev ilk kez çalıştırıldığında birkaç dakika sürebilir. Bununla birlikte, değişiklikleri yaptıktan sonra kendi alt geliştirme alanınıza bağlanarak bunları `azds space select` yalıtılmış alt geliştirme alanınızda dağıtıp hata ayıklaması yapabilirsiniz. Geliştirme alanınızı çalışır durumda yaptıktan sonra, komutu yeniden yayımlayarak bu güncelleştirme gönderebilirsiniz `azds up` veya Visual Studio veya Visual Studio Code yerleşik araçları kullanabilirsiniz. VS Code, geliştirme alanınıza bağlanmak için komut paletini kullanın. Şekil 3-12, Visual Studio 'da Azure Dev Spaces kullanarak Web uygulamanızı nasıl başlatacağınızı gösterir.

![Visual Studio ](./media/azure-dev-spaces-visual-studio-launchsettings.png)
 **Şekil 3-12**' de Azure dev Spaces bağlanın. Visual Studio 'da Azure Dev Spaces bağlanma

>[!div class="step-by-step"]
>[Önceki](combine-containers-serverless-approaches.md) 
> [Sonraki](scale-containers-serverless.md)
