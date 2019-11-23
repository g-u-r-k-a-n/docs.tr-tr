---
title: AKS/Kubernetes kümelerine Linux kapsayıcıları olarak dağıtılan derleme ASP.NET Core 2,2 uygulamaları
description: Microsoft Platformu ve Araçları ile Kapsayıcı Docker Uygulaması Yaşam Döngüsü
ms.date: 02/25/2019
ms.openlocfilehash: ab64a0423ceceb8285c159af276d6d97e12379d8
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848747"
---
# <a name="build-aspnet-core-22-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a>AKS/Kubernetes Orchestrator 'a Linux kapsayıcıları olarak dağıtılan derleme ASP.NET Core 2,2 uygulamaları

Azure Kubernetes Hizmetleri (AKS), Azure 'un kapsayıcı dağıtımı ve yönetimini kolaylaştıran yönetilen Kubernetes yönetimi hizmetidir.

AKS ana özellikleri şunlardır:

- Azure 'da barındırılan denetim düzlemi
- Otomatik yükseltmeler
- Kendi kendini onaran
- Kullanıcı tarafından yapılandırılabilir ölçeklendirme
- Hem geliştiriciler hem de küme işleçleri için daha basit bir kullanıcı deneyimi.

Aşağıdaki örneklerde, Linux üzerinde çalışan ve Azure 'daki bir AKS kümesine dağıtan ASP.NET Core 2,2 uygulamasının oluşturulması araştırırken Visual Studio 2017 kullanılarak geliştirme yapılır.

## <a name="creating-the-aspnet-core-22-project-using-visual-studio-2017"></a>Visual Studio 2017 kullanarak ASP.NET Core 2,2 projesi oluşturma

ASP.NET Core, GitHub 'da Microsoft ve .NET Community tarafından tutulan genel amaçlı bir geliştirme platformudur. Windows, macOS ve Linux 'un desteklenme ve cihaz, bulut ve katıştırılmış/IoT senaryolarında kullanılabilen platformlar arası bir platformdur.

Bu örnek, Visual Studio Web API şablonunu temel alan basit bir proje kullanır, bu nedenle örneği oluşturmak için ek bilgiye ihtiyacınız yoktur. Projeyi, ASP.NET Core 2,2 teknolojisini kullanarak, REST API küçük bir projeyi çalıştırmak için tüm öğeleri içeren standart bir şablon kullanarak oluşturmanız yeterlidir.

![Visual Studio 'da ASP.NET Core Web uygulaması ' nı seçerek yeni proje penceresi ekleyin.](media/create-aspnet-core-application.png)

**Şekil 4-36**. ASP.NET Core uygulaması oluşturuluyor

Visual Studio 'da örnek proje oluşturmak için **dosya** > **Yeni** > **Proje**' yi seçin, sol bölmedeki **Web** projesi türlerini seçin ve ardından **ASP.NET Core Web uygulaması**' nı seçin.

Visual Studio, Web projeleri için şablonlar listeler. Örneğimiz için **API** 'yi seçerek bir ASP.NET Web API uygulaması oluşturun.

Framework olarak ASP.NET Core 2,2 ' i seçtiğinizi doğrulayın. .NET Core 2,2, Visual Studio 2017 ' nin son sürümüne dahildir ve Visual Studio 2017 ' i yüklediğinizde sizin için otomatik olarak yüklenir ve yapılandırılır.

![API seçeneği seçili ASP.NET Core Web uygulaması türünü seçmek için Visual Studio iletişim kutusu.](media/create-web-api-application.png)

**Şekil 4-37**. ASP.NET CORE 2,2 ve Web API proje türünü seçme

.NET Core 'un önceki bir sürümüne sahipseniz <https://dotnet.microsoft.com/download>2,2 sürümünü indirip yükleyebilirsiniz.

Projeyi oluştururken Docker desteği ekleyebilirsiniz, böylece projenizi istediğiniz zaman "Dockerize" edebilirsiniz. Proje oluşturulduktan sonra Docker desteği eklemek için, Çözüm Gezgini içindeki proje düğümüne sağ tıklayın ve bağlam menüsünde > **Docker desteği** **Ekle** ' yi seçin.

![Mevcut bir projeye Docker desteği eklemek için bağlam menüsü seçeneği: > > Docker desteği eklemek için (projede) öğesine sağ tıklayın.](media/add-docker-support-to-project.png)

**Şekil 4-38**. Mevcut projeye Docker desteği ekleniyor

Docker desteği ekleme işleminin tamamlanabilmesi için Windows veya Linux ' u seçebilirsiniz. Bu durumda, AKS Windows kapsayıcılarını desteklemediğinden (geç 2018 itibariyle) **Linux**' u seçin.

![Dockerfile için hedef işletim sistemini seçmek üzere seçenek iletişim kutusu.](media/select-linux-docker-support.png)

**Şekil 4-39**. Linux kapsayıcıları seçiliyor.

Bu basit adımlarla bir Linux kapsayıcısında çalışan ASP.NET Core 2,2 uygulamanız vardır.

Gördüğünüz gibi, Visual Studio 2017 ile Docker arasındaki tümleştirme, geliştiricinin verimliliğine tamamen dayalıdır.

Artık uygulamanızı **F5** tuşuyla veya **Play** düğmesini kullanarak çalıştırabilirsiniz.

Projeyi çalıştırdıktan sonra, `docker images` komutunu kullanarak görüntüleri listeleyebilirsiniz. Visual Studio 2017 ile projemizin otomatik dağıtımı tarafından oluşturulan `mssampleapplication` görüntüsünü görmeniz gerekir.

```console
docker images
```

![Docker görüntüleri komutundan konsol çıktısı: depo, etiket, görüntü KIMLIĞI, oluşturulan (Tarih) ve boyut içeren bir liste gösterir.](media/docker-images-command.png)

**Şekil 4-40**. Docker görüntülerinin görünümü

## <a name="register-the-solution-in-the-azure-container-registry"></a>Çözümü Azure Container Registry kaydetme

Görüntüyü, [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) veya Docker Hub gibi herhangi bir Docker kayıt defterine yükleyin, bu nedenle görüntüler bu kayıt defterinden aks kümesine dağıtılabilir. Bu durumda, görüntüyü Azure Container Registry karşıya yüklüyoruz.

### <a name="create-the-image-in-release-mode"></a>Görüntüyü yayın modunda oluşturma

Şimdi, Şekil 4-41 ' de gösterildiği gibi, **yayın**moduna geçiş yaparak ve uygulamayı daha önce yaptığımız gibi çalıştırırken **yayın** modunda (üretim için hazır) görüntü oluşturacağız.

![Yayın modunda derleme ' deki araç çubuğu seçeneği.](media/select-release-mode.png)

**Şekil 4-41**. Yayın modunu seçme

`docker image` komutunu çalıştırırsanız, biri `debug` ve diğeri `release` modu için oluşturulan her iki görüntüyü da görürsünüz.

### <a name="create-a-new-tag-for-the-image"></a>Görüntü için yeni bir etiket oluşturun

Her kapsayıcı görüntüsünün, kayıt defterinin `loginServer` adı ile etiketlenmesi gerekir. Bu etiket, kapsayıcı görüntüleri bir görüntü kayıt defterine gönderilirken yönlendirme için kullanılır.

Azure Container Registry bilgileri alarak Azure portal `loginServer` adı görüntüleyebilirsiniz

![Azure Container kayıt defteri adının sağ üst tarafındaki tarayıcı görünümü.](media/loginServer-name.png)

**Şekil 4-42**. Kayıt defterinin adının görünümü

Ya da aşağıdaki komutu çalıştırarak:

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Yukarıdaki komuttan konsol çıktısı.](media/az-cli-loginServer-name.png)

**Şekil 4-43**. PowerShell kullanarak kayıt defterinin adını alın

Her iki durumda da adı elde edersiniz. Örneğimizde, `mssampleacr.azurecr.io`.

Artık, şu komutla birlikte en son görüntüyü (yayın görüntüsü) alarak resmi etiketleyebilir:

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

`docker tag` komutunu çalıştırdıktan sonra, `docker images` komutuyla görüntüleri listeleyin ve yeni etiketiyle birlikte resmi görmeniz gerekir.

![Docker görüntüleri komutundan konsol çıktısı.](media/tagged-docker-images-list.png)

**Şekil 4-44**. Etiketli görüntülerin görünümü

### <a name="push-the-image-into-the-azure-acr"></a>Görüntüyü Azure ACR 'ye gönderme

Azure Container Registry oturum açın

```console
az acr login --name mssampleacr
```

Aşağıdaki komutu kullanarak görüntüyü Azure ACR 'ye gönderin:

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

Bu komut, görüntüleri karşıya yüklerken bir işlem gerçekleştirir, ancak işlemde geri bildirim sağlar.

![Docker Push komutundan konsol çıkışı: her katman için bir karakter tabanlı ilerleme çubuğu gösterir.](media/uploading-image-to-acr.png)

**Şekil 4-45**. Görüntüyü ACR 'ye yükleme

İşlem tamamlandığında almanız gereken sonucun altına bakabilirsiniz:

![Docker Push komutundan konsol çıktısı, tüm katmanları veya düğümleri gösterir.](media/uploading-docker-images-complete.png)

**Şekil 4-46**. Düğümlerin görünümü

Bir sonraki adım, kapsayıcınızı AKS Kubernetes kümenize dağıtmaktır. Bunun için, aşağıdakileri içeren bir dosya ( **. yml dağıtım dosyası**) gerekir:

```yml
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: mssamplesbook
spec:
  replicas: 1
  template:
    metadata:
      labels:
        app: mssample-kub-app
    spec:
      containers:
        - name: mssample-services-app
          image: mssampleacr.azurecr.io/mssampleaksapplication:v1
          ports:
            - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
    name: mssample-kub-app
spec:
  ports:
    - name: http-port
      port: 80
      targetPort: 80
  selector:
    app: mssample-kub-app
  type: LoadBalancer
```

> [!NOTE]
> Kubernetes ile dağıtım hakkında daha fazla bilgi için bkz. <https://kubernetes.io/docs/reference/kubectl/cheatsheet/>

Artık, **Kubectl**kullanarak dağıtıma hazırsınız, ancak önce bu komutla aks kümesi için kimlik bilgilerini almalısınız:

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Yukarıdaki komuttan konsol çıkışı: "MSSampleK8Cluster,/root/.exe içinde geçerli bağlam olarak birleştirildi. Kube/config](media/getting-aks-credentials.png)

**Şekil 4-47**. kimlik bilgileri alınıyor

Ardından, dağıtımı başlatmak için `kubectl create` komutunu kullanın.

```console
kubectl create -f mssample-deploy.yml
```

![Yukarıdaki komuttan konsol çıkışı: dağıtım "mssamplesbook" oluşturuldu. "mssample-Kub-App" hizmeti oluşturuldu.](media/kubectl-create-command.png)

**Şekil 4-48**. Kubernetes 'e dağıtma

Dağıtım tamamlandığında, bu komutla zamana bağlı erişebileceğiniz bir yerel ara sunucu ile Kubernetes konsoluna erişebilirsiniz:

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

Ve `http://127.0.0.1:8001`URL 'sine erişme.

![Dağıtım, dizin, çoğaltma kümesi ve hizmet gösteren Kubernetes panosunun tarayıcı görünümü.](media/kubernetes-cluster-information.png)

**Şekil 4-49**. Kubernetes kümesi bilgilerini görüntüle

Artık uygulamanız Azure 'da, bir Linux kapsayıcısı ve bir AKS Kubernetes kümesi kullanılarak dağıtılır. Uygulamanızın, hizmetinizin genel IP 'ye gözatmasına erişerek Azure portal edinebilirsiniz.

> [!NOTE]
> Bu kılavuzda [**Azure Kubernetes Service 'e (aks) dağıtım**](deploy-azure-kubernetes-service.md) bölümünde bu örnek için aks kümesini nasıl oluşturacağınız hakkında bilgi alabilirsiniz.

>[!div class="step-by-step"]
>[Önceki](set-up-windows-containers-with-powershell.md)
>[İleri](../docker-devops-workflow/index.md)
