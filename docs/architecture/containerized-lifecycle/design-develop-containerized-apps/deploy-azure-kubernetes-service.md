---
title: Yüksek ölçeklenebilirlik ve kullanılabilirlik için mikro hizmetleri ve çok kapsayıcılı uygulamaları yönetme
description: Azure Kubernetes hizmetini kullanarak bir uygulamayı dağıtmayı öğrenin.
ms.date: 02/15/2019
ms.openlocfilehash: 0aa2f83fbf8f9a8815d65730002943cca748643d
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182364"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a>Azure Kubernetes Service’e (AKS) Dağıtma

Tercih ettiğiniz istemci işletim sistemini kullanarak AKS ile etkileşim kurabilirsiniz. burada, Windows 'da Bash komutlarını kullanarak Microsoft Windows ve Ubuntu Linux Embedded sürümü ile nasıl yapılacağını göstereceğiz.

AKS kullanılmadan önce sahip olmanın önkoşulları şunlardır:

- Linux veya Mac geliştirme makinesi
- Windows geliştirme makinesi
  - Windows üzerinde geliştirici modu etkin
  - Linux için Windows alt sistemi
- [Windows, Mac veya Linux](https://docs.microsoft.com/cli/azure/install-azure-cli) 'ta yüklü Azure-CLI

> [!NOTE]
> Hakkında ayrıntılı bilgi edinmek için:
>
> Azure-CLı: <https://docs.microsoft.com/cli/azure/index>
>
> Linux için Windows alt sistemi: <https://docs.microsoft.com/windows/wsl/about>

## <a name="create-the-aks-environment-in-azure"></a>Azure 'da AKS ortamını oluşturma

AKS ortamını oluşturmanın birkaç yolu vardır. Bu, Azure-CLı komutları kullanılarak veya Azure portal kullanılarak yapılabilir.

Burada, kümeyi oluşturmak için Azure-CLı kullanarak bazı örnekleri keşfedebilirsiniz ve sonuçları gözden geçirmek için Azure portal. Geliştirme makinenizde Kubectl ve Docker de sahip olmanız gerekir.  

## <a name="create-the-aks-cluster"></a>AKS kümesini oluşturma

Şu komutu kullanarak AKS kümesini oluşturun:

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

Oluşturma işi bittikten sonra, Azure portal oluşturulan AKS 'leri görebilirsiniz:

Kaynak grubu:

![Azure AKS kaynak grubunun tarayıcı görünümü.](media/aks-resource-group-view.png)

**Şekil 4-17**. Azure 'dan AKS kaynak grubu görünümü.

AKS kümesi:

![AKS kaynak grubunun tarayıcı görünümü.](media/aks-cluster-view.png)

**Şekil 4-18**. Azure 'dan AKS görünümü.

Ayrıca, `Azure-CLI` ve `Kubectl`kullanarak oluşturulan düğümü görüntüleyebilirsiniz.

İlk olarak, kimlik bilgileri alınıyor:

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![Yukarıdaki komuttan konsol çıkışı: "MsSampleK8Cluster,/root/. Kube/configiçinde geçerli bağlam olarak birleştirildi.](media/get-credentials-command-result.png)

**Şekil 4-19**. `aks get-credentials` komut sonucu.

Ardından, Kubectl 'den düğüm alma:

```console
kubectl get nodes
```

![Yukarıdaki komutun konsol çıkışı: durum, Yaş (çalıştırma süresi) ve sürüm ile düğümlerin listesi](media/kubectl-get-nodes-command-result.png)

**Şekil 4-20**. `kubectl get nodes` komut sonucu.

>[!div class="step-by-step"]
>[Önceki](orchestrate-high-scalability-availability.md)
>[İleri](docker-apps-development-environment.md)
