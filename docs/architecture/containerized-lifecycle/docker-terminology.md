---
title: Docker terimleri
description: Docker ile çalışırken gündelik olarak kullanılan bazı temel terminolojiyi öğrenin.
ms.date: 01/06/2021
ms.openlocfilehash: 640c3481e271b8fe2b7d7eeb7d5eaeb02af1cc21
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970108"
---
# <a name="docker-terminology"></a>Docker terimleri

Bu bölümde, Docker 'a daha ayrıntılı bir şekilde yararlanmak için bilmeniz gereken hüküm ve tanımlar listelenmektedir. Daha fazla tanım için bkz. Docker tarafından sağlanan kapsamlı [Sözlük](https://docs.docker.com/glossary/) .

**Kapsayıcı görüntüsü**: bir kapsayıcı oluşturmak için gereken tüm bağımlılıkları ve bilgileri içeren bir paket. Bir görüntü, bir kapsayıcı çalışma zamanı tarafından kullanılacak tüm bağımlılıkları (örneğin, çerçeveler) ve dağıtım ve yürütme yapılandırmasını içerir. Genellikle, bir görüntü kapsayıcının dosya sistemini biçimlendirmek için her bir katmanın üzerine yığılan birden çok temel görüntüden türetilir. Bir görüntü oluşturulduktan sonra sabittir.

**Dockerfile**: Docker görüntüsü oluşturmaya yönelik yönergeleri içeren bir metin dosyası. Bir toplu iş betiğine benzer şekilde, ilk satırda temel görüntünün başlaması ve ardından gerekli programları yüklemek, dosyaları kopyalamak ve daha fazlasını yapmak için gereken çalışma ortamına ulaşana kadar yönergeleri izlemeniz gerekir.

**Yapı**: Dockerfile tarafından belirtilen bilgileri ve bağlamı temel alan bir kapsayıcı görüntüsü oluşturma eylemi ve görüntünün oluşturulduğu klasördeki ek dosyalar. Aşağıdaki Docker komutuyla resim oluşturabilirsiniz:

```bash
docker build
```

**Kapsayıcı**: Docker görüntüsünün bir örneği. Kapsayıcı, tek bir uygulama, işlem veya hizmetin yürütülmesini temsil eder. Docker görüntüsü, yürütme ortamı ve standart bir yönerge kümesi içeriğinden oluşur. Bir hizmeti ölçeklendirirken, aynı görüntüden bir kapsayıcının birden çok örneğini oluşturursunuz. Ya da bir toplu iş, her örneğe farklı parametreler geçirerek aynı görüntüden birden fazla kapsayıcı oluşturabilir.

**Birimler**: kapsayıcının kullanabileceği yazılabilir bir dosya sistemi sunun. Görüntüler salt okunurdur, ancak çoğu programın dosya sistemine yazması gerektiğinden, birimler kapsayıcı görüntüsünün üzerine yazılabilir bir katman ekleyerek programların yazılabilir bir dosya sistemine erişimi vardır. Program, katmanlı bir dosya sistemine eriştiğini bilmez, her zamanki gibi yalnızca dosya sistemi. Konak sisteminde bulunan ve Docker tarafından yönetilen birimler.

**Etiket**: görüntüler için uygulayabileceğiniz bir işaret veya etiket, aynı görüntünün farklı görüntülerinin veya sürümlerinin (sürüm numarasına veya hedef ortama göre) tanımlanabilmesi için kullanabilirsiniz.

**Çok aşamalı derleme**: docker 17,05 veya üzeri olduğundan, son görüntülerin boyutunu azaltmaya yardımcı olan bir özelliktir. Örneğin, SDK içeren büyük bir temel görüntü, derleme ve yayımlama için kullanılabilir ve sonra yalnızca küçük bir çalışma zamanı temel görüntüsü uygulamayı barındırmak için kullanılabilir.

**Depo (depo)**: görüntü sürümünü gösteren bir etiketle etiketlenmiş Ilgili Docker görüntülerinin koleksiyonu. Bazı depolarda, SDK (daha ağır) içeren bir görüntü, yalnızca çalışma zamanları içeren bir görüntü (daha açık) vb. gibi belirli bir görüntünün birden fazla çeşitlemesi bulunur. Bu çeşitler etiketlerle işaretlenebilir. Tek bir depo, Linux görüntüsü ve Windows görüntüsü gibi platform türevlerini içerebilir.

**Kayıt defteri**: depolara erişim sağlayan bir hizmet. Çoğu ortak görüntü için varsayılan kayıt defteri, [Docker Hub](https://hub.docker.com/) ' dır (kuruluş olarak Docker tarafından sahiplenilir). Kayıt defteri genellikle birden çok ekipten depoları içerir. Şirketler genellikle oluşturdukları görüntüleri depolamak ve yönetmek için özel kayıt defterlerine sahiptir. Azure Container Registry başka bir örnektir.

**Çok katmanlı görüntü**: çok mimaride, Docker 'ın çalıştırıldığı platforma göre uygun görüntünün seçimini kolaylaştıran bir özelliktir. Örneğin, bir Dockerfile, kayıt defterinden **MCR.Microsoft.com/DotNet/SDK:5.0 öğesinden** bir temel görüntü Istediğinde, Docker 'ın çalıştırıldığı işletim sistemine ve sürüme bağlı olarak **5,0-Nanoserver-20h2**, **5,0-nanoserver-2004** veya **5,0-Buster-ince** değerini alır.

**Docker Hub**: görüntüleri karşıya yüklemek ve bunlarla çalışmak için ortak bir kayıt defteri. Docker Hub, Docker görüntüsü barındırma, genel veya özel kayıt defterleri, derleme Tetikleyicileri ve Web kancaları, GitHub ve BitBucket ile tümleştirme sağlar.

**Azure Container Registry**: Docker görüntüleriyle ve Azure 'daki bileşenleriyle çalışmak için ortak bir kaynak. Bu, Azure 'daki dağıtımlarınıza yakın bir kayıt defteri sağlar ve erişim üzerinde denetim sağlayarak Azure Active Directory gruplarınızı ve izinlerinizi kullanmayı mümkün kılar.

**Docker güvenilir kayıt defteri (DTR)**: kuruluşun veri merkezinde ve ağında yer alması için şirket içinde yüklenebilen bir Docker kayıt defteri hizmeti (Docker 'dan). Kuruluş dahilinde yönetilmesi gereken özel görüntüler için kolaylık vardır. Docker güvenilen kayıt defteri, Docker Datacenter ürününün bir parçası olarak dahil edilmiştir. Daha fazla bilgi için bkz. [Docker güvenilir kayıt defteri (DTR)](https://www.docker.com/sites/default/files/Docker%20Trusted%20Registry.pdf).

**Docker Community Edition (CE)**: yerel olarak kapsayıcı oluşturma, çalıştırma ve test etme için Windows ve MacOS için geliştirme araçları. Docker CE for Windows hem Linux hem de Windows kapsayıcıları için geliştirme ortamları sağlar. Windows üzerindeki Linux Docker ana bilgisayarı bir [Hyper-V](https://www.microsoft.com/cloud-platform/server-virtualization) sanal makinesini temel alır. Windows kapsayıcıları için ana bilgisayar, doğrudan Windows 'a dayalıdır. Mac için Docker CE, Apple hiper yönetici çerçevesini ve Mac OS X bir Linux Docker konak sanal makinesi sağlayan [xhyve hiper yönetici](https://github.com/mist64/xhyve)'yi temel alır. Docker CE for Windows ve Mac Için, Oracle VirtualBox tabanlı olan Docker araç kutusu bulunur.

**Docker Enterprise Edition (ee)**: Linux ve Windows geliştirme Için Docker araçlarının kurumsal ölçekli bir sürümüdür.

**Oluştur**: çok Kapsayıcılı uygulamalar tanımlamak ve çalıştırmak için meta veriler içeren bir komut satırı aracı ve YAML dosya biçimi. Ortama bağlı olarak değerleri geçersiz kılabileceğiniz bir veya daha fazla............... Tanımları oluşturduktan sonra, Docker konağında görüntü başına kapsayıcı oluşturan tek bir komutla (Docker-Compose) tüm çok Kapsayıcılı uygulamayı dağıtabilirsiniz.

**Küme**: tek bir sanal Docker ana bilgisayarı gibi kullanıma sunulan Docker konaklarının bir koleksiyonu, uygulamanın birden fazla hizmetin kümedeki birden fazla örneğine yayılabilmesini sağlamak için, bu, uygulamanın birden çok hizmet örneğine ölçeklenebilmesini sağlar. Docker kümeleri, Kubernetes, Azure Service Fabric, Docker Sısınma ve Mesosphere DC/OS ile oluşturulabilir.

**Orchestrator**: kümelerin ve Docker ana bilgisayarlarının yönetimini kolaylaştıran bir araç. Düzenleyiciler, bir komut satırı arabirimi (CLı) veya grafik kullanıcı arabirimi aracılığıyla görüntülerini, kapsayıcıları ve konaklarını yönetmenizi sağlar. Kapsayıcı ağ, yapılandırma, Yük Dengeleme, hizmet bulma, yüksek kullanılabilirlik, Docker ana bilgisayar yapılandırması ve daha fazlasını yönetebilirsiniz. Bir Orchestrator, bir düğüm koleksiyonunda çalıştırma, dağıtma, ölçekleme ve düzeltme yüklerini çalıştırmaktan sorumludur. Genellikle, Orchestrator ürünleri, piyasadaki diğer tekliflerin yanı sıra Kubernetes ve Azure Service Fabric gibi küme altyapısı sağlayan ürünlerdir.

>[!div class="step-by-step"]
>[Önceki](what-is-docker.md) 
> [Sonraki](docker-containers-images-and-registries.md)
