---
title: docker-compose.yml ile çok kapsayıcılı uygulamanızı tanımlama
description: Docker-Compose. yıml ile çok kapsayıcılı bir uygulama için mikro hizmet birleşimini belirtme.
ms.date: 01/30/2020
ms.openlocfilehash: 81303be621da54b7336228585e86d1120a6b7598
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739795"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="7e15f-103">docker-compose.yml ile çok kapsayıcılı uygulamanızı tanımlama</span><span class="sxs-lookup"><span data-stu-id="7e15f-103">Defining your multi-container application with docker-compose.yml</span></span>

<span data-ttu-id="7e15f-104">Bu kılavuzda, 4. adım bölümünde [Docker-Compose. yıml](https://docs.docker.com/compose/compose-file/) dosyası eklenmiştir [. Çok kapsayıcılı bir Docker uygulaması oluştururken hizmetlerinizi Docker-Compose. yıml içinde tanımlayın](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application).</span><span class="sxs-lookup"><span data-stu-id="7e15f-104">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application).</span></span> <span data-ttu-id="7e15f-105">Ancak, daha ayrıntılı bir şekilde Araştırılması gereken Docker-Compose dosyalarını kullanmak için ek yollar vardır.</span><span class="sxs-lookup"><span data-stu-id="7e15f-105">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="7e15f-106">Örneğin, Docker-Compose. yıml dosyasında çok Kapsayıcılı uygulamanızı nasıl dağıtmak istediğinizi açıkça tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e15f-106">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="7e15f-107">İsteğe bağlı olarak, özel Docker görüntülerinizi nasıl oluşturacağınız de tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e15f-107">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="7e15f-108">(Özel Docker görüntüleri de Docker CLı ile oluşturulabilir.)</span><span class="sxs-lookup"><span data-stu-id="7e15f-108">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="7e15f-109">Temel olarak, dağıtmak istediğiniz kapsayıcıların her birini ve her bir kapsayıcı dağıtımı için belirli özellikleri tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="7e15f-109">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="7e15f-110">Çok kapsayıcılı bir dağıtım açıklama dosyanız olduktan sonra, tüm çözümü [Docker-Compose](https://docs.docker.com/compose/overview/) CLI komutuyla düzenlenmiş tek bir eylemde dağıtabilir veya Visual Studio 'dan saydam olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e15f-110">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="7e15f-111">Aksi takdirde, komut satırından komutunu kullanarak kapsayıcıyı birden çok adımda dağıtmak için Docker CLı 'yi kullanmanız gerekir `docker run` .</span><span class="sxs-lookup"><span data-stu-id="7e15f-111">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the `docker run` command from the command line.</span></span> <span data-ttu-id="7e15f-112">Bu nedenle, Docker-Compose. yıml içinde tanımlanan her bir hizmetin tam olarak bir görüntü veya yapı belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-112">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="7e15f-113">Diğer anahtarlar isteğe bağlıdır ve `docker run` komut satırı karşılıklarına benzer.</span><span class="sxs-lookup"><span data-stu-id="7e15f-113">Other keys are optional, and are analogous to their `docker run` command-line counterparts.</span></span>

<span data-ttu-id="7e15f-114">Aşağıdaki YAML kodu, eShopOnContainers örneği için olası genel ancak tek bir Docker-Compose. yıml dosyasının tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="7e15f-114">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="7e15f-115">Bu, eShopOnContainers 'dan gerçek Docker-Compose dosyası değildir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-115">This is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="7e15f-116">Bunun yerine, daha sonra açıklanacak şekilde Docker-Compose dosyaları ile çalışmanın en iyi yolu olmayan tek bir dosyadaki Basitleştirilmiş ve birleştirilmiş bir sürümdür.</span><span class="sxs-lookup"><span data-stu-id="7e15f-116">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

```yml
version: '3.4'

services:
  webmvc:
    image: eshop/webmvc
    environment:
      - CatalogUrl=http://catalog-api
      - OrderingUrl=http://ordering-api
      - BasketUrl=http://basket-api
    ports:
      - "5100:80"
    depends_on:
      - catalog-api
      - ordering-api
      - basket-api

  catalog-api:
    image: eshop/catalog-api
    environment:
      - ConnectionString=Server=sqldata;Initial Catalog=CatalogData;User Id=sa;Password=[PLACEHOLDER]
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sqldata

  ordering-api:
    image: eshop/ordering-api
    environment:
      - ConnectionString=Server=sqldata;Database=Services.OrderingDb;User Id=sa;Password=[PLACEHOLDER]
    ports:
      - "5102:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sqldata

  basket-api:
    image: eshop/basket-api
    environment:
      - ConnectionString=sqldata
    ports:
      - "5103:80"
    depends_on:
      - sqldata

  sqldata:
    environment:
      - SA_PASSWORD=[PLACEHOLDER]
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"

  basketdata:
    image: redis
```

<span data-ttu-id="7e15f-117">Bu dosyadaki kök anahtar hizmetdir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-117">The root key in this file is services.</span></span> <span data-ttu-id="7e15f-118">Bu anahtar altında, `docker-compose up` komutunu çalıştırdığınızda veya bu Docker-Compose. yıml dosyasını kullanarak Visual Studio 'dan dağıtırken dağıtmak ve çalıştırmak istediğiniz hizmetleri tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="7e15f-118">Under that key, you define the services you want to deploy and run when you execute the `docker-compose up` command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="7e15f-119">Bu durumda, aşağıdaki tabloda açıklandığı gibi, Docker-Compose. yıml dosyasında birden çok hizmet tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7e15f-119">In this case, the docker-compose.yml file has multiple services defined, as described in the following table.</span></span>

| <span data-ttu-id="7e15f-120">Hizmet adı</span><span class="sxs-lookup"><span data-stu-id="7e15f-120">Service name</span></span> | <span data-ttu-id="7e15f-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e15f-121">Description</span></span> |
|--------------|-------------|
| <span data-ttu-id="7e15f-122">webmvc</span><span class="sxs-lookup"><span data-stu-id="7e15f-122">webmvc</span></span>       | <span data-ttu-id="7e15f-123">Sunucu tarafı C 'den mikro hizmetleri kullanan ASP.NET Core MVC uygulamasını içeren kapsayıcı\#</span><span class="sxs-lookup"><span data-stu-id="7e15f-123">Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>|
| <span data-ttu-id="7e15f-124">Katalog-API</span><span class="sxs-lookup"><span data-stu-id="7e15f-124">catalog-api</span></span>  | <span data-ttu-id="7e15f-125">Katalog ASP.NET Core Web API mikro hizmeti de dahil olmak üzere kapsayıcı</span><span class="sxs-lookup"><span data-stu-id="7e15f-125">Container including the Catalog ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="7e15f-126">sıralama-API</span><span class="sxs-lookup"><span data-stu-id="7e15f-126">ordering-api</span></span> | <span data-ttu-id="7e15f-127">Web API mikro hizmeti ASP.NET Core sıralamasını içeren kapsayıcı</span><span class="sxs-lookup"><span data-stu-id="7e15f-127">Container including the Ordering ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="7e15f-128">SQLdata</span><span class="sxs-lookup"><span data-stu-id="7e15f-128">sqldata</span></span>     | <span data-ttu-id="7e15f-129">Mikro hizmet veritabanlarını tutan Linux için SQL Server çalıştıran kapsayıcı</span><span class="sxs-lookup"><span data-stu-id="7e15f-129">Container running SQL Server for Linux, holding the microservices databases</span></span> |
| <span data-ttu-id="7e15f-130">sepet-API</span><span class="sxs-lookup"><span data-stu-id="7e15f-130">basket-api</span></span>   | <span data-ttu-id="7e15f-131">Sepet ASP.NET Core Web API mikro hizmeti olan kapsayıcı</span><span class="sxs-lookup"><span data-stu-id="7e15f-131">Container with the Basket ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="7e15f-132">basketdata</span><span class="sxs-lookup"><span data-stu-id="7e15f-132">basketdata</span></span>  | <span data-ttu-id="7e15f-133">Redsıs Cache hizmetini çalıştıran kapsayıcı, sepet veritabanı REDSıS Cache olarak</span><span class="sxs-lookup"><span data-stu-id="7e15f-133">Container running the REDIS cache service, with the basket database as a REDIS cache</span></span> |

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="7e15f-134">Basit bir Web hizmeti API kapsayıcısı</span><span class="sxs-lookup"><span data-stu-id="7e15f-134">A simple Web Service API container</span></span>

<span data-ttu-id="7e15f-135">Tek bir kapsayıcıya odaklanarak katalog-API kapsayıcısı-mikro hizmetin basit bir tanımı vardır:</span><span class="sxs-lookup"><span data-stu-id="7e15f-135">Focusing on a single container, the catalog-api container-microservice has a straightforward definition:</span></span>

```yml
  catalog-api:
    image: eshop/catalog-api
    environment:
      - ConnectionString=Server=sqldata;Initial Catalog=CatalogData;User Id=sa;Password=[PLACEHOLDER]
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sqldata
```

<span data-ttu-id="7e15f-136">Bu Kapsayıcılı hizmet aşağıdaki temel yapılandırmaya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="7e15f-136">This containerized service has the following basic configuration:</span></span>

- <span data-ttu-id="7e15f-137">Özel **eShop/Catalog-API** görüntüsünü temel alır.</span><span class="sxs-lookup"><span data-stu-id="7e15f-137">It is based on the custom **eshop/catalog-api** image.</span></span> <span data-ttu-id="7e15f-138">Basitlik 'in sake için, dosyada derleme: anahtar ayarı yoktur.</span><span class="sxs-lookup"><span data-stu-id="7e15f-138">For simplicity's sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="7e15f-139">Bu, görüntünün daha önce oluşturulmuş olması (Docker derlemesi ile) veya herhangi bir Docker kayıt defterinden indirilen (docker pull komutuyla) olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-139">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

- <span data-ttu-id="7e15f-140">Katalog veri modelini içeren SQL Server örneğine erişmek üzere Entity Framework tarafından kullanılacak bağlantı dizesiyle ConnectionString adlı bir ortam değişkenini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7e15f-140">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="7e15f-141">Bu durumda, aynı SQL Server kapsayıcısı birden çok veritabanını tutuyor.</span><span class="sxs-lookup"><span data-stu-id="7e15f-141">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="7e15f-142">Bu nedenle, Docker için geliştirme makinenizde daha az bellek gerekir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-142">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="7e15f-143">Ancak, her mikro hizmet veritabanı için bir SQL Server kapsayıcısı da dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e15f-143">However, you could also deploy one SQL Server container for each microservice database.</span></span>

- <span data-ttu-id="7e15f-144">SQL Server adı, Linux için SQL Server örneğini çalıştıran kapsayıcı için kullanılan ad **SQLdata**' dır.</span><span class="sxs-lookup"><span data-stu-id="7e15f-144">The SQL Server name is **sqldata**, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="7e15f-145">Bu kullanışlıdır; Bu ad çözümlemesini kullanabilmeniz (Docker ana bilgisayarına iç) ağ adresini çözümleyecek ve bu sayede diğer kapsayıcılardan eriştiğiniz kapsayıcıların iç IP 'sini bilmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="7e15f-145">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don't need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="7e15f-146">Bağlantı dizesi bir ortam değişkeni tarafından tanımlandığından, bu değişkeni farklı bir mekanizmaya ve farklı bir zamanda ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e15f-146">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="7e15f-147">Örneğin, son Konaklarda üretime dağıtım yaparken veya Azure DevOps Services ya da tercih ettiğiniz DevOps sisteminizin CI/CD işlem hatlarından yararlanarak farklı bir bağlantı dizesi ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e15f-147">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in Azure DevOps Services or your preferred DevOps system.</span></span>

- <span data-ttu-id="7e15f-148">Docker Konağı içindeki **Catalog-API** hizmetine iç erişim için 80 bağlantı noktasını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="7e15f-148">It exposes port 80 for internal access to the **catalog-api** service within the Docker host.</span></span> <span data-ttu-id="7e15f-149">Konak, Linux için bir Docker görüntüsünü temel aldığı için şu anda bir Linux sanal makinesi. ancak kapsayıcıyı bir Windows görüntüsünde çalışacak şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e15f-149">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

- <span data-ttu-id="7e15f-150">Kapsayıcı üzerinde 80 numaralı bağlantı noktasını Docker ana makinesi (Linux VM) üzerinde bağlantı noktası 5101 ' e iletir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-150">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

- <span data-ttu-id="7e15f-151">Web hizmetini **SQLdata** Service 'e bağlar (bir kapsayıcıda çalışan Linux veritabanı için SQL Server örneği).</span><span class="sxs-lookup"><span data-stu-id="7e15f-151">It links the web service to the **sqldata** service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="7e15f-152">Bu bağımlılığı belirttiğinizde, SQLveri kapsayıcısı zaten başlatılana kadar Catalog-API kapsayıcısı başlatılmaz; Bu önemlidir çünkü Catalog-API SQL Server veritabanının önce çalışır ve çalışıyor olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-152">When you specify this dependency, the catalog-api container will not start until the sqldata container has already started; this is important because catalog-api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="7e15f-153">Ancak, bu tür bir kapsayıcı bağımlılığı birçok durumda yeterli değildir çünkü Docker yalnızca kapsayıcı düzeyinde kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="7e15f-153">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="7e15f-154">Bazen hizmet (Bu durumda SQL Server) hala hazırlanmayabilir, bu nedenle, istemci mikro hizmetinizdeki üstel geri alma ile yeniden deneme mantığını uygulamanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-154">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="7e15f-155">Bu şekilde, bir bağımlılık kapsayıcısı kısa bir süre için hazırsanız, uygulama yine de dayanıklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="7e15f-155">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

- <span data-ttu-id="7e15f-156">Bu, dış sunuculara erişime izin verecek şekilde yapılandırıldı: ek \_ konaklar ayarı, dış sunuculara veya makinelere, GELIŞTIRME PC 'nizdeki yerel bir SQL Server örneği gibi Docker Konağı dışındaki (bir geliştirme Docker ana bilgisayarı olan varsayılan LINUX VM 'nin dışında) erişmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7e15f-156">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM, which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="7e15f-157">Ayrıca, `docker-compose.yml` Aşağıdaki bölümlerde ele alacağız başka gelişmiş ayarlar da vardır.</span><span class="sxs-lookup"><span data-stu-id="7e15f-157">There are also other, more advanced `docker-compose.yml` settings that we'll discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="7e15f-158">Çoklu ortamları hedeflemek için Docker-Compose dosyalarını kullanma</span><span class="sxs-lookup"><span data-stu-id="7e15f-158">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="7e15f-159">`docker-compose.*.yml`Dosyalar tanım dosyalarıdır ve bu biçimi anlayan birden çok altyapı tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-159">The `docker-compose.*.yml` files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="7e15f-160">En kolay araç Docker-Compose komutındır.</span><span class="sxs-lookup"><span data-stu-id="7e15f-160">The most straightforward tool is the docker-compose command.</span></span>

<span data-ttu-id="7e15f-161">Bu nedenle, Docker-Compose komutunu kullanarak aşağıdaki ana senaryoları hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e15f-161">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="7e15f-162">Geliştirme ortamları</span><span class="sxs-lookup"><span data-stu-id="7e15f-162">Development environments</span></span>

<span data-ttu-id="7e15f-163">Uygulama geliştirirken, bir uygulamayı yalıtılmış bir geliştirme ortamında çalıştırabilmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-163">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="7e15f-164">Bu ortamı veya bu ortamı oluşturmak için Docker-Compose CLı komutunu, kapabileşenler altında Docker-Compose kullanan Visual Studio 'Yu oluşturmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e15f-164">You can use the docker-compose CLI command to create that environment or Visual Studio, which uses docker-compose under the covers.</span></span>

<span data-ttu-id="7e15f-165">Docker-Compose. yıml dosyası, tüm uygulamanızın hizmet bağımlılıklarını (diğer hizmetler, önbellek, veritabanları, kuyruklar vb.) yapılandırmanıza ve belgeetmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7e15f-165">The docker-compose.yml file allows you to configure and document all your application's service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="7e15f-166">Docker-Compose CLı komutunu kullanarak her bağımlılık için bir veya daha fazla kapsayıcıyı tek bir komutla oluşturup başlatabilirsiniz (Docker-Compose).</span><span class="sxs-lookup"><span data-stu-id="7e15f-166">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="7e15f-167">Docker-Compose. yıml dosyaları Docker altyapısı tarafından yorumlanan yapılandırma dosyalarıdır, ancak aynı zamanda çok Kapsayıcılı uygulamanızın kompozisyonu hakkında uygun belge dosyaları da sunar.</span><span class="sxs-lookup"><span data-stu-id="7e15f-167">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="7e15f-168">Ortamları test etme</span><span class="sxs-lookup"><span data-stu-id="7e15f-168">Testing environments</span></span>

<span data-ttu-id="7e15f-169">Herhangi bir sürekli dağıtım (CD) veya sürekli tümleştirme (CI) işleminin önemli bir bölümü, birim testleri ve tümleştirme sınamalardır.</span><span class="sxs-lookup"><span data-stu-id="7e15f-169">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="7e15f-170">Bu otomatikleştirilmiş testler, kullanıcılardan etkilenmemesi için yalıtılmış bir ortam gerektirir ve uygulamanın verilerinde başka bir değişiklik olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-170">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application's data.</span></span>

<span data-ttu-id="7e15f-171">Docker Compose, aşağıdaki komutlar gibi komut isteminizden veya betiklerinizde bulunan birkaç komut için yalıtılmış ortamı kolayca oluşturabilir ve yok edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7e15f-171">With Docker Compose, you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```console
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml up -d
./run_unit_tests
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml down
```

#### <a name="production-deployments"></a><span data-ttu-id="7e15f-172">Üretim dağıtımları</span><span class="sxs-lookup"><span data-stu-id="7e15f-172">Production deployments</span></span>

<span data-ttu-id="7e15f-173">Ayrıca, bir uzak Docker altyapısına dağıtmak için Oluştur ' da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e15f-173">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="7e15f-174">Tipik bir durum, tek bir Docker ana bilgisayar örneğine (bir üretim VM 'si veya [Docker makinesi](https://docs.docker.com/machine/overview/)ile sağlanan sunucu gibi) dağıtılmaktır.</span><span class="sxs-lookup"><span data-stu-id="7e15f-174">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span>

<span data-ttu-id="7e15f-175">Başka bir Orchestrator (Azure Service Fabric, Kubernetes vb.) kullanıyorsanız, Docker-Compose. yml ' de olduğu gibi, diğer Orchestrator için gereken biçimde kurulum ve meta veri yapılandırma ayarları eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-175">If you are using any other orchestrator (Azure Service Fabric, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="7e15f-176">Her durumda, Docker-Compose geliştirme, test ve üretim iş akışları için uygun bir araç ve meta veri biçimidir, ancak üretim iş akışı kullandığınız Orchestrator üzerinde farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-176">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="7e15f-177">Çeşitli ortamları işlemek için birden çok Docker-Compose dosyası kullanma</span><span class="sxs-lookup"><span data-stu-id="7e15f-177">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="7e15f-178">Farklı ortamları hedeflerken, birden çok oluşturma dosyası kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-178">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="7e15f-179">Bu, ortama bağlı olarak birden çok yapılandırma çeşitlemesi oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="7e15f-179">This lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="7e15f-180">Temel Docker-Compose dosyasını geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="7e15f-180">Overriding the base docker-compose file</span></span>

<span data-ttu-id="7e15f-181">Önceki bölümlerde gösterilen Basitleştirilmiş örneklerde olduğu gibi tek bir Docker-Compose. yıml dosyası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e15f-181">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="7e15f-182">Ancak, çoğu uygulama için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="7e15f-182">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="7e15f-183">Varsayılan olarak, Compose iki dosyayı okur, bir Docker-Compose. yıml ve isteğe bağlı bir Docker-Compose. override. yıml dosyası.</span><span class="sxs-lookup"><span data-stu-id="7e15f-183">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="7e15f-184">Şekil 6-11 ' de gösterildiği gibi, Visual Studio 'Yu kullanırken ve Docker desteğini etkinleştirirken, Visual Studio uygulamada hata ayıklamak için ek bir Docker-Compose. vs. Debug. g. yıml dosyası da oluşturur. bu dosyaya, \\ ana çözüm klasöründeki obj Docker klasöründe bakabilirsiniz \\ .</span><span class="sxs-lookup"><span data-stu-id="7e15f-184">As shown in Figure 6-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates an additional docker-compose.vs.debug.g.yml file for debugging the application, you can take a look at this file in folder obj\\Docker\\ in the main solution folder.</span></span>

![Docker Compose projesindeki dosyalar.](./media/multi-container-applications-docker-compose/docker-compose-file-visual-studio.png)

<span data-ttu-id="7e15f-186">**Şekil 6-11**.</span><span class="sxs-lookup"><span data-stu-id="7e15f-186">**Figure 6-11**.</span></span> <span data-ttu-id="7e15f-187">Visual Studio 'da Docker-dosyaları oluşturma 2019</span><span class="sxs-lookup"><span data-stu-id="7e15f-187">docker-compose files in Visual Studio 2019</span></span>

<span data-ttu-id="7e15f-188">**Docker-** proje dosyası yapısını oluşturma:</span><span class="sxs-lookup"><span data-stu-id="7e15f-188">**docker-compose** project file structure:</span></span>

- <span data-ttu-id="7e15f-189">*. dockerıgnore* -dosyaları yoksaymak için kullanılır</span><span class="sxs-lookup"><span data-stu-id="7e15f-189">*.dockerignore* - used to ignore files</span></span>
- <span data-ttu-id="7e15f-190">*Docker-Compose. yıml* -mikro hizmetleri oluşturmak için kullanılır</span><span class="sxs-lookup"><span data-stu-id="7e15f-190">*docker-compose.yml* - used to compose microservices</span></span>
- <span data-ttu-id="7e15f-191">*Docker-Compose. override. yıml* -mikro hizmetler ortamını yapılandırmak için kullanılır</span><span class="sxs-lookup"><span data-stu-id="7e15f-191">*docker-compose.override.yml* - used to configure microservices environment</span></span>

<span data-ttu-id="7e15f-192">Docker-Compose dosyalarını, Visual Studio Code veya alt lime gibi herhangi bir düzenleyici ile düzenleyebilir ve uygulamayı Docker-Compose up komutuyla çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e15f-192">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="7e15f-193">Kural gereği, Docker-Compose. yıml dosyası temel yapılandırmanızı ve diğer statik ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-193">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="7e15f-194">Bu, hizmet yapılandırmasının hedeflediğiniz dağıtım ortamına bağlı olarak değişmeyeceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-194">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="7e15f-195">Docker-Compose. override. yıml dosyası, adının önereceği gibi, temel yapılandırmayı geçersiz kılan yapılandırma ayarlarını (dağıtım ortamına bağlı yapılandırma gibi) içerir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-195">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="7e15f-196">Aynı zamanda farklı adlara sahip birden fazla geçersiz kılma dosyasına sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e15f-196">You can have multiple override files with different names also.</span></span> <span data-ttu-id="7e15f-197">Geçersiz kılma dosyaları genellikle uygulama için gerekli olan, ancak bir ortama veya dağıtıma özgü ek bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-197">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="7e15f-198">Birden çok ortamı hedefleme</span><span class="sxs-lookup"><span data-stu-id="7e15f-198">Targeting multiple environments</span></span>

<span data-ttu-id="7e15f-199">Tipik kullanım örneği, birden çok ortamı, hazırlama, CI veya geliştirme gibi birden çok ortamı hedefleyebilir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-199">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="7e15f-200">Bu farklılıkları desteklemek için, Şekil 6-12 ' de gösterildiği gibi, oluşturma yapılandırmanızı birden çok dosyaya bölebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e15f-200">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 6-12.</span></span>

![Temel dosyayı geçersiz kılmak için ayarlanan üç Docker-Compose dosyası diyagramı.](./media/multi-container-applications-docker-compose/multiple-docker-compose-files-override-base.png)

<span data-ttu-id="7e15f-202">**Şekil 6-12**.</span><span class="sxs-lookup"><span data-stu-id="7e15f-202">**Figure 6-12**.</span></span> <span data-ttu-id="7e15f-203">Temel Docker-Compose. yıml dosyasındaki değerleri geçersiz kılan birden çok Docker-dosya oluşturma</span><span class="sxs-lookup"><span data-stu-id="7e15f-203">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="7e15f-204">Farklı ortamları işlemek için birden çok Docker-Compose\*. yıml dosyasını birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e15f-204">You can combine multiple docker-compose\*.yml files to handle different environments.</span></span> <span data-ttu-id="7e15f-205">Temel Docker-Compose. yıml dosyası ile başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e15f-205">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="7e15f-206">Bu temel dosya, ortama bağlı olarak değişmeyen temel veya statik yapılandırma ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-206">This base file contains the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="7e15f-207">Örneğin, eShopOnContainers uygulaması, temel dosya olarak aşağıdaki Docker-Compose. yıml dosyasına (daha az hizmet ile Basitleştirilmiş) sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-207">For example, the eShopOnContainers app has the following docker-compose.yml file (simplified with fewer services) as the base file.</span></span>

```yml
#docker-compose.yml (Base)
version: '3.4'
services:
  basket-api:
    image: eshop/basket-api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Basket/Basket.API/Dockerfile
    depends_on:
      - basketdata
      - identity-api
      - rabbitmq

  catalog-api:
    image: eshop/catalog-api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Catalog/Catalog.API/Dockerfile
    depends_on:
      - sqldata
      - rabbitmq

  marketing-api:
    image: eshop/marketing-api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Marketing/Marketing.API/Dockerfile
    depends_on:
      - sqldata
      - nosqldata
      - identity-api
      - rabbitmq

  webmvc:
    image: eshop/webmvc:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Web/WebMVC/Dockerfile
    depends_on:
      - catalog-api
      - ordering-api
      - identity-api
      - basket-api
      - marketing-api

  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest

  nosqldata:
    image: mongo

  basketdata:
    image: redis

  rabbitmq:
    image: rabbitmq:3-management

```

<span data-ttu-id="7e15f-208">Temel Docker-Compose. yıml dosyasındaki değerler farklı hedef dağıtım ortamları nedeniyle değişmemelidir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-208">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="7e15f-209">Örneğin, webmvc hizmeti tanımına odaklandıysanız, bu bilgilerin ne kadar hedeflendiğine bakılmaksızın bu bilgilerin nasıl fazla olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e15f-209">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="7e15f-210">Aşağıdaki bilgilere sahipsiniz:</span><span class="sxs-lookup"><span data-stu-id="7e15f-210">You have the following information:</span></span>

- <span data-ttu-id="7e15f-211">Hizmet adı: webmvc.</span><span class="sxs-lookup"><span data-stu-id="7e15f-211">The service name: webmvc.</span></span>

- <span data-ttu-id="7e15f-212">Kapsayıcının özel görüntüsü: eshop/webmvc.</span><span class="sxs-lookup"><span data-stu-id="7e15f-212">The container's custom image: eshop/webmvc.</span></span>

- <span data-ttu-id="7e15f-213">Özel Docker görüntüsünü oluşturma komutu, hangi Dockerfile 'ın kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-213">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

- <span data-ttu-id="7e15f-214">Diğer hizmetlerde bağımlılıklar, bu nedenle diğer bağımlılık kapsayıcıları başlatılana kadar bu kapsayıcı başlatılmaz.</span><span class="sxs-lookup"><span data-stu-id="7e15f-214">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="7e15f-215">Ek yapılandırmaya sahip olabilirsiniz ancak önemli nokta, temel Docker-Compose. yıml dosyasında yalnızca ortamlar genelinde ortak olan bilgileri ayarlamak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="7e15f-215">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="7e15f-216">Ardından Docker-Compose. override. yıml veya üretim ya da hazırlama için benzer dosyalarda, her ortam için özel yapılandırmayı yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-216">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="7e15f-217">Genellikle, eShopOnContainers 'dan aşağıdaki örnekte olduğu gibi, Docker-Compose. override. yml, geliştirme ortamınız için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="7e15f-217">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '3.4'

services:
# Simplified number of services here:

  basket-api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_REDIS_BASKET_DB:-basketdata}
      - identityUrl=http://identity-api
      - IdentityUrlExternal=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5105
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}
      - AzureServiceBusEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}

    ports:
      - "5103:80"

  catalog-api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_CATALOG_DB:-Server=sqldata;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=[PLACEHOLDER]}
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_CATALOG_URL:-http://localhost:5202/api/v1/catalog/items/[0]/pic/}
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}
      - AzureStorageAccountName=${ESHOP_AZURE_STORAGE_CATALOG_NAME}
      - AzureStorageAccountKey=${ESHOP_AZURE_STORAGE_CATALOG_KEY}
      - UseCustomizationData=True
      - AzureServiceBusEnabled=False
      - AzureStorageEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
    ports:
      - "5101:80"

  marketing-api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_MARKETING_DB:-Server=sqldata;Database=Microsoft.eShopOnContainers.Services.MarketingDb;User Id=sa;Password=[PLACEHOLDER]}
      - MongoConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosqldata}
      - MongoDatabase=MarketingDb
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}
      - identityUrl=http://identity-api
      - IdentityUrlExternal=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5105
      - CampaignDetailFunctionUri=${ESHOP_AZUREFUNC_CAMPAIGN_DETAILS_URI}
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_MARKETING_URL:-http://localhost:5110/api/v1/campaigns/[0]/pic/}
      - AzureStorageAccountName=${ESHOP_AZURE_STORAGE_MARKETING_NAME}
      - AzureStorageAccountKey=${ESHOP_AZURE_STORAGE_MARKETING_KEY}
      - AzureServiceBusEnabled=False
      - AzureStorageEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5110:80"

  webmvc:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - PurchaseUrl=http://webshoppingapigw
      - IdentityUrl=http://10.0.75.1:5105
      - MarketingUrl=http://webmarketingapigw
      - CatalogUrlHC=http://catalog-api/hc
      - OrderingUrlHC=http://ordering-api/hc
      - IdentityUrlHC=http://identity-api/hc
      - BasketUrlHC=http://basket-api/hc
      - MarketingUrlHC=http://marketing-api/hc
      - PaymentUrlHC=http://payment-api/hc
      - SignalrHubUrl=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5202
      - UseCustomizationData=True
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5100:80"
  sqldata:
    environment:
      - SA_PASSWORD=[PLACEHOLDER]
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosqldata:
    ports:
      - "27017:27017"
  basketdata:
    ports:
      - "6379:6379"
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672"

```

<span data-ttu-id="7e15f-218">Bu örnekte, geliştirme geçersiz kılma yapılandırması konağa bazı bağlantı noktaları gösterir, yönlendirme URL 'Leri ile ortam değişkenlerini tanımlar ve geliştirme ortamı için bağlantı dizelerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-218">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="7e15f-219">Bu ayarlar yalnızca geliştirme ortamına yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-219">These settings are all just for the development environment.</span></span>

<span data-ttu-id="7e15f-220">Çalıştırdığınızda `docker-compose up` (veya Visual Studio 'dan başlattığınızda), komut geçersiz kılmaları her iki dosyayı birleştiriyor gibi otomatik olarak okur.</span><span class="sxs-lookup"><span data-stu-id="7e15f-220">When you run `docker-compose up` (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="7e15f-221">Üretim ortamı için farklı yapılandırma değerleriyle, bağlantı noktalarıyla veya bağlantı dizelerine sahip başka bir oluşturma dosyası istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="7e15f-221">Suppose that you want another Compose file for the production environment, with different configuration values, ports, or connection strings.</span></span> <span data-ttu-id="7e15f-222">Farklı ayarlar ve ortam değişkenleriyle adlı dosya gibi başka bir geçersiz kılma dosyası oluşturabilirsiniz `docker-compose.prod.yml` .</span><span class="sxs-lookup"><span data-stu-id="7e15f-222">You can create another override file, like file named `docker-compose.prod.yml` with different settings and environment variables.</span></span> <span data-ttu-id="7e15f-223">Bu dosya farklı bir git deposunda depolanabilir veya yönetilen ve farklı bir ekip tarafından güvenli hale getirilmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-223">That file might be stored in a different Git repo or managed and secured by a different team.</span></span>

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="7e15f-224">Belirli bir geçersiz kılma dosyası ile dağıtım</span><span class="sxs-lookup"><span data-stu-id="7e15f-224">How to deploy with a specific override file</span></span>

<span data-ttu-id="7e15f-225">Birden çok geçersiz kılma dosyası ya da farklı bir ada sahip bir geçersiz kılma dosyası kullanmak için, Docker-Compose komutuyla-f seçeneğini kullanabilir ve dosyaları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e15f-225">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="7e15f-226">Birleştirme dosyalarını komut satırında belirtildikleri sırada oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7e15f-226">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="7e15f-227">Aşağıdaki örnek, geçersiz kılma dosyalarıyla nasıl dağıtılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-227">The following example shows how to deploy with override files.</span></span>

```console
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="7e15f-228">Docker-Compose dosyalarında ortam değişkenlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="7e15f-228">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="7e15f-229">Önceki örneklerde gösterildiği gibi, özellikle üretim ortamlarında, ortam değişkenlerinden yapılandırma bilgilerini alabilmesi için kullanışlı bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-229">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="7e15f-230">$ {MY var} sözdizimini kullanarak Docker-Compose dosyalarınızda bir ortam değişkenine başvurabilirsiniz \_ .</span><span class="sxs-lookup"><span data-stu-id="7e15f-230">You can reference an environment variable in your docker-compose files using the syntax ${MY\_VAR}.</span></span> <span data-ttu-id="7e15f-231">Bir Docker-Compose. prod. yıml dosyasından aşağıdaki satır, bir ortam değişkeninin değerine nasıl başvurulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-231">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="7e15f-232">Ortam değişkenleri, ana bilgisayar ortamınıza (Linux, Windows, bulut kümesi, vb.) bağlı olarak farklı yollarla oluşturulur ve başlatılır.</span><span class="sxs-lookup"><span data-stu-id="7e15f-232">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="7e15f-233">Ancak, uygun bir yaklaşım. env dosyası kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="7e15f-233">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="7e15f-234">Docker-Compose dosyaları,. env dosyasında varsayılan ortam değişkenlerini bildirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="7e15f-234">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="7e15f-235">Ortam değişkenlerine yönelik bu değerler varsayılan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-235">These values for the environment variables are the default values.</span></span> <span data-ttu-id="7e15f-236">Ancak, ortamınızda (konak işletim sistemi veya ortam değişkenleri kümenizdeki) tanımlamış olabileceğiniz değerler tarafından geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-236">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="7e15f-237">Bu. env dosyasını Docker-Compose komutunun yürütüldüğü klasöre yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e15f-237">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="7e15f-238">Aşağıdaki örnek, eShopOnContainers uygulaması için [. env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) dosyası gibi bir. env dosyasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-238">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) file for the eShopOnContainers application.</span></span>

```sh
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="7e15f-239">Docker-Compose,. env dosyasındaki her satırın biçimde olmasını bekler \<variable\> = \<value\> .</span><span class="sxs-lookup"><span data-stu-id="7e15f-239">Docker-compose expects each line in an .env file to be in the format \<variable\>=\<value\>.</span></span>

<span data-ttu-id="7e15f-240">Çalışma zamanı ortamında ayarlanan değerler her zaman. env dosyası içinde tanımlanan değerleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="7e15f-240">The values set in the run-time environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="7e15f-241">Benzer şekilde, komut satırı bağımsız değişkenleri ile geçirilen değerler aynı zamanda. env dosyasında ayarlanan varsayılan değerleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="7e15f-241">In a similar way, values passed via command-line arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="7e15f-242">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="7e15f-242">Additional resources</span></span>

- <span data-ttu-id="7e15f-243">**Docker Compose genel bakış** </span><span class="sxs-lookup"><span data-stu-id="7e15f-243">**Overview of Docker Compose** </span></span>\
    <https://docs.docker.com/compose/overview/>

- <span data-ttu-id="7e15f-244">**Birden çok oluşturma dosyası** </span><span class="sxs-lookup"><span data-stu-id="7e15f-244">**Multiple Compose files** </span></span>\
    [https://docs.docker.com/compose/extends/\#multiple-compose-files](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="7e15f-245">İyileştirilmiş ASP.NET Core Docker görüntüleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="7e15f-245">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="7e15f-246">Internet 'teki kaynaklarda Docker ve .NET Core 'u araştırıyorsanız, kaynağınızı bir kapsayıcıya kopyalayarak bir Docker görüntüsü oluşturmanın basitliğini gösteren Dockerfiles 'ı bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e15f-246">If you are exploring Docker and .NET Core on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="7e15f-247">Bu örnekler, basit bir yapılandırma kullanarak, uygulamanızla birlikte paketlenmiş bir Docker görüntüsüne sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e15f-247">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="7e15f-248">Aşağıdaki örnekte, bu Vein içindeki basit bir Dockerfile gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-248">The following example shows a simple Dockerfile in this vein.</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/sdk:3.1
WORKDIR /app
ENV ASPNETCORE_URLS http://+:80
EXPOSE 80
COPY . .
RUN dotnet restore
ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="7e15f-249">Bunun gibi bir Dockerfile çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="7e15f-249">A Dockerfile like this will work.</span></span> <span data-ttu-id="7e15f-250">Ancak, görüntülerinizi önemli ölçüde iyileştirebilirsiniz, özellikle de üretim görüntüleriniz.</span><span class="sxs-lookup"><span data-stu-id="7e15f-250">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="7e15f-251">Kapsayıcı ve mikro hizmetler modelinde, kapsayıcılardan sürekli olarak başlangıç yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e15f-251">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="7e15f-252">Kapsayıcıları kullanmanın tipik yolu, kapsayıcı atılabilir olduğundan, uyuma bir kapsayıcıyı yeniden başlatmaz.</span><span class="sxs-lookup"><span data-stu-id="7e15f-252">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="7e15f-253">Düzenleyiciler (Kubernetes ve Azure Service Fabric gibi) yalnızca yeni görüntü örnekleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7e15f-253">Orchestrators (like Kubernetes and Azure Service Fabric) simply create new instances of images.</span></span> <span data-ttu-id="7e15f-254">Bunun anlamı, örnek oluşturma işleminin daha hızlı olması için uygulamayı derleme sırasında önceden derleyerek iyileştirmeniz gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-254">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="7e15f-255">Kapsayıcı başlatıldığında, çalıştırılmaya hazırlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7e15f-255">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="7e15f-256">`dotnet restore` `dotnet build` .NET Core ve Docker hakkındaki blog gönderilerinde görebileceğiniz gibi, ve CLI komutlarını kullanarak çalışma zamanında geri yükleme ve derleme yapmayın.</span><span class="sxs-lookup"><span data-stu-id="7e15f-256">Don't restore and compile at run time using the `dotnet restore` and `dotnet build` CLI commands as you may see in blog posts about .NET Core and Docker.</span></span>

<span data-ttu-id="7e15f-257">.NET ekibi, .NET Core ve kapsayıcı için iyileştirilmiş bir çerçeve ASP.NET Core için önemli bir iş yapıyor.</span><span class="sxs-lookup"><span data-stu-id="7e15f-257">The .NET team has been doing important work to make .NET Core and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="7e15f-258">.NET Core, küçük bellek ayak izine sahip hafif bir çerçeve; ekip, üç ana senaryo için iyileştirilmiş Docker görüntülerine odaklanmıştır ve 2,1 sürümünden itibaren *DotNet/Core*'Da Docker Hub kayıt defterinde yayımlanır:</span><span class="sxs-lookup"><span data-stu-id="7e15f-258">Not only is .NET Core a lightweight framework with a small memory footprint; the team has focused on optimized Docker images for three main scenarios and published them in the Docker Hub registry at *dotnet/core*, beginning with version 2.1:</span></span>

1. <span data-ttu-id="7e15f-259">**Geliştirme**: öncelik, değişiklikleri hızlı bir şekilde yinelemek ve hata ayıklamanın yanı sıra boyutun ikincil olduğu yerdir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-259">**Development**: The priority is the ability to quickly iterate and debug changes, and where size is secondary.</span></span>

2. <span data-ttu-id="7e15f-260">**Yapı**: öncelik uygulamayı derler ve görüntü ikililerini iyileştirmek için ikili dosyaları ve diğer bağımlılıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="7e15f-260">**Build**: The priority is compiling the application, and the image includes binaries and other dependencies to optimize binaries.</span></span>

3. <span data-ttu-id="7e15f-261">**Üretim**: odak, kapsayıcıların hızlı bir şekilde dağıtılmasını ve başlamasını sağlar. bu sayede, bu görüntüler uygulamayı çalıştırmak için gereken ikili ve içerikle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="7e15f-261">**Production**: The focus is fast deploying and starting of containers, so these images are limited to the binaries and content needed to run the application.</span></span>

<span data-ttu-id="7e15f-262">.NET ekibi, [DotNet/Core](https://hub.docker.com/_/microsoft-dotnet/) 'da dört temel çeşit sağlar (Docker Hub 'da):</span><span class="sxs-lookup"><span data-stu-id="7e15f-262">The .NET team provides four basic variants in [dotnet/core](https://hub.docker.com/_/microsoft-dotnet/) (at Docker Hub):</span></span>

1. <span data-ttu-id="7e15f-263">**SDK**: geliştirme ve derleme senaryoları için</span><span class="sxs-lookup"><span data-stu-id="7e15f-263">**sdk**: for development and build scenarios</span></span>
1. <span data-ttu-id="7e15f-264">**ASPNET**: ASP.NET üretim senaryoları için</span><span class="sxs-lookup"><span data-stu-id="7e15f-264">**aspnet**: for ASP.NET production scenarios</span></span>
1. <span data-ttu-id="7e15f-265">**çalışma zamanı**: .NET üretim senaryoları için</span><span class="sxs-lookup"><span data-stu-id="7e15f-265">**runtime**: for .NET production scenarios</span></span>
1. <span data-ttu-id="7e15f-266">**Runtime-Deps**: [kendi içindeki uygulamaların](../../../core/deploying/index.md#publish-self-contained) üretim senaryoları için</span><span class="sxs-lookup"><span data-stu-id="7e15f-266">**runtime-deps**: for production scenarios of [self-contained applications](../../../core/deploying/index.md#publish-self-contained)</span></span>

<span data-ttu-id="7e15f-267">Daha hızlı başlangıç için, çalışma zamanı görüntüleri Ayrıca aspnetcore \_ URL 'lerini otomatik olarak 80 numaralı bağlantı noktasına ayarlar ve derlemelerin yerel görüntü önbelleğini oluşturmak Için Ngen 'i kullanır.</span><span class="sxs-lookup"><span data-stu-id="7e15f-267">For faster startup, runtime images also automatically set aspnetcore\_urls to port 80 and use Ngen to create a native image cache of assemblies.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="7e15f-268">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="7e15f-268">Additional resources</span></span>

- <span data-ttu-id="7e15f-269">**ASP.NET Core ile Iyileştirilmiş Docker görüntüleri oluşturma**
  <https://docs.microsoft.com/archive/blogs/stevelasker/building-optimized-docker-images-with-asp-net-core></span><span class="sxs-lookup"><span data-stu-id="7e15f-269">**Building Optimized Docker Images with ASP.NET Core**
<https://docs.microsoft.com/archive/blogs/stevelasker/building-optimized-docker-images-with-asp-net-core></span></span>

- <span data-ttu-id="7e15f-270">**.NET Core uygulamaları için Docker görüntüleri oluşturma**
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)</span><span class="sxs-lookup"><span data-stu-id="7e15f-270">**Building Docker Images for .NET Core Applications**
[https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="7e15f-271">[Önceki](data-driven-crud-microservice.md) 
>  [Sonraki](database-server-container.md)</span><span class="sxs-lookup"><span data-stu-id="7e15f-271">[Previous](data-driven-crud-microservice.md)
[Next](database-server-container.md)</span></span>
