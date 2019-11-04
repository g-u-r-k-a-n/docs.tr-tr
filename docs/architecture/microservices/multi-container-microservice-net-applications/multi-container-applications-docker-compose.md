---
title: docker-compose.yml ile çok kapsayıcılı uygulamanızı tanımlama
description: Docker-Compose. yıml ile çok kapsayıcılı bir uygulama için mikro hizmet birleşimini belirtme.
ms.date: 10/02/2018
ms.openlocfilehash: 938a9aa192f82628051bd7dc065f661f510ba544
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73416699"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="80b0b-103">docker-compose.yml ile çok kapsayıcılı uygulamanızı tanımlama</span><span class="sxs-lookup"><span data-stu-id="80b0b-103">Defining your multi-container application with docker-compose.yml</span></span>

<span data-ttu-id="80b0b-104">Bu kılavuzda, 4. adım bölümünde [Docker-Compose. yıml](https://docs.docker.com/compose/compose-file/) dosyası eklenmiştir [. Çok kapsayıcılı bir Docker uygulaması oluştururken hizmetlerinizi Docker-Compose. yıml içinde tanımlayın](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application).</span><span class="sxs-lookup"><span data-stu-id="80b0b-104">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application).</span></span> <span data-ttu-id="80b0b-105">Ancak, daha ayrıntılı bir şekilde Araştırılması gereken Docker-Compose dosyalarını kullanmak için ek yollar vardır.</span><span class="sxs-lookup"><span data-stu-id="80b0b-105">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="80b0b-106">Örneğin, Docker-Compose. yıml dosyasında çok Kapsayıcılı uygulamanızı nasıl dağıtmak istediğinizi açıkça tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b0b-106">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="80b0b-107">İsteğe bağlı olarak, özel Docker görüntülerinizi nasıl oluşturacağınız de tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b0b-107">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="80b0b-108">(Özel Docker görüntüleri de Docker CLı ile oluşturulabilir.)</span><span class="sxs-lookup"><span data-stu-id="80b0b-108">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="80b0b-109">Temel olarak, dağıtmak istediğiniz kapsayıcıların her birini ve her bir kapsayıcı dağıtımı için belirli özellikleri tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="80b0b-109">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="80b0b-110">Çok kapsayıcılı bir dağıtım açıklama dosyanız olduktan sonra, tüm çözümü [Docker-Compose](https://docs.docker.com/compose/overview/) CLI komutuyla düzenlenmiş tek bir eylemde dağıtabilir veya Visual Studio 'dan saydam olarak dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b0b-110">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="80b0b-111">Aksi takdirde, komut satırından `docker run` komutunu kullanarak kapsayıcıyı kapsayıcı ile birden çok adımda dağıtmak için Docker CLı 'yi kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-111">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the `docker run` command from the command line.</span></span> <span data-ttu-id="80b0b-112">Bu nedenle, Docker-Compose. yıml içinde tanımlanan her bir hizmetin tam olarak bir görüntü veya yapı belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-112">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="80b0b-113">Diğer anahtarlar isteğe bağlıdır ve `docker run` komut satırı karşılıklarına benzer.</span><span class="sxs-lookup"><span data-stu-id="80b0b-113">Other keys are optional, and are analogous to their `docker run` command-line counterparts.</span></span>

<span data-ttu-id="80b0b-114">Aşağıdaki YAML kodu, eShopOnContainers örneği için olası genel ancak tek bir Docker-Compose. yıml dosyasının tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="80b0b-114">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="80b0b-115">Bu, eShopOnContainers 'dan gerçek Docker-Compose dosyası değildir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-115">This is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="80b0b-116">Bunun yerine, daha sonra açıklanacak şekilde Docker-Compose dosyaları ile çalışmanın en iyi yolu olmayan tek bir dosyadaki Basitleştirilmiş ve birleştirilmiş bir sürümdür.</span><span class="sxs-lookup"><span data-stu-id="80b0b-116">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

```yml
version: '3.4'

services:
  webmvc:
    image: eshop/webmvc
    environment:
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
      - BasketUrl=http://basket.api
    ports:
      - "5100:80"
    depends_on:
      - catalog.api
      - ordering.api
      - basket.api

  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=sql.data;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    environment:
      - ConnectionString=Server=sql.data;Database=Services.OrderingDb;User Id=sa;Password=your@password
    ports:
      - "5102:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data

  basket.api:
    image: eshop/basket.api
    environment:
      - ConnectionString=sql.data
    ports:
      - "5103:80"
    depends_on:
      - sql.data

  sql.data:
    environment:
      - SA_PASSWORD=your@password
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"

  basket.data:
    image: redis
```

<span data-ttu-id="80b0b-117">Bu dosyadaki kök anahtar hizmetdir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-117">The root key in this file is services.</span></span> <span data-ttu-id="80b0b-118">Bu anahtar altında, `docker-compose up` komutunu yürüttüğünüzde veya bu Docker-Compose. yıml dosyasını kullanarak Visual Studio 'dan dağıtırken, dağıtmak ve çalıştırmak istediğiniz hizmetleri tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="80b0b-118">Under that key you define the services you want to deploy and run when you execute the `docker-compose up` command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="80b0b-119">Bu durumda, aşağıdaki tabloda açıklandığı gibi, Docker-Compose. yıml dosyasında birden çok hizmet tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="80b0b-119">In this case, the docker-compose.yml file has multiple services defined, as described in the following table.</span></span>

| <span data-ttu-id="80b0b-120">Hizmet adı</span><span class="sxs-lookup"><span data-stu-id="80b0b-120">Service name</span></span> | <span data-ttu-id="80b0b-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80b0b-121">Description</span></span> |
|--------------|-------------|
| <span data-ttu-id="80b0b-122">webmvc</span><span class="sxs-lookup"><span data-stu-id="80b0b-122">webmvc</span></span>       | <span data-ttu-id="80b0b-123">Sunucu tarafı C 'den mikro hizmetleri kullanan ASP.NET Core MVC uygulamasını içeren kapsayıcı\#</span><span class="sxs-lookup"><span data-stu-id="80b0b-123">Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>|
| <span data-ttu-id="80b0b-124">Catalog. API</span><span class="sxs-lookup"><span data-stu-id="80b0b-124">catalog.api</span></span>  | <span data-ttu-id="80b0b-125">Katalog ASP.NET Core Web API mikro hizmeti de dahil olmak üzere kapsayıcı</span><span class="sxs-lookup"><span data-stu-id="80b0b-125">Container including the Catalog ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="80b0b-126">sıralama. API</span><span class="sxs-lookup"><span data-stu-id="80b0b-126">ordering.api</span></span> | <span data-ttu-id="80b0b-127">Web API mikro hizmeti ASP.NET Core sıralamasını içeren kapsayıcı</span><span class="sxs-lookup"><span data-stu-id="80b0b-127">Container including the Ordering ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="80b0b-128">SQL. Data</span><span class="sxs-lookup"><span data-stu-id="80b0b-128">sql.data</span></span>     | <span data-ttu-id="80b0b-129">Mikro hizmet veritabanlarını tutan Linux için SQL Server çalıştıran kapsayıcı</span><span class="sxs-lookup"><span data-stu-id="80b0b-129">Container running SQL Server for Linux, holding the microservices databases</span></span> |
| <span data-ttu-id="80b0b-130">sepet. API</span><span class="sxs-lookup"><span data-stu-id="80b0b-130">basket.api</span></span>   | <span data-ttu-id="80b0b-131">Sepet ASP.NET Core Web API mikro hizmeti olan kapsayıcı</span><span class="sxs-lookup"><span data-stu-id="80b0b-131">Container with the Basket ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="80b0b-132">sepet. Data</span><span class="sxs-lookup"><span data-stu-id="80b0b-132">basket.data</span></span>  | <span data-ttu-id="80b0b-133">Redsıs Cache hizmetini çalıştıran kapsayıcı, sepet veritabanı REDSıS Cache olarak</span><span class="sxs-lookup"><span data-stu-id="80b0b-133">Container running the REDIS cache service, with the basket database as a REDIS cache</span></span> |

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="80b0b-134">Basit bir Web hizmeti API kapsayıcısı</span><span class="sxs-lookup"><span data-stu-id="80b0b-134">A simple Web Service API container</span></span>

<span data-ttu-id="80b0b-135">Tek bir kapsayıcıya odaklanarak Catalog. API Container-mikro hizmeti basit bir tanıma sahiptir:</span><span class="sxs-lookup"><span data-stu-id="80b0b-135">Focusing on a single container, the catalog.api container-microservice has a straightforward definition:</span></span>

```yml
  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=sql.data;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data
```

<span data-ttu-id="80b0b-136">Bu Kapsayıcılı hizmet aşağıdaki temel yapılandırmaya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="80b0b-136">This containerized service has the following basic configuration:</span></span>

- <span data-ttu-id="80b0b-137">Özel eShop/Catalog. API görüntüsünü temel alır.</span><span class="sxs-lookup"><span data-stu-id="80b0b-137">It is based on the custom eshop/catalog.api image.</span></span> <span data-ttu-id="80b0b-138">Basitlik 'in sake için, dosyada derleme: anahtar ayarı yoktur.</span><span class="sxs-lookup"><span data-stu-id="80b0b-138">For simplicity’s sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="80b0b-139">Bu, görüntünün daha önce oluşturulmuş olması (Docker derlemesi ile) veya herhangi bir Docker kayıt defterinden indirilen (docker pull komutuyla) olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-139">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

- <span data-ttu-id="80b0b-140">Katalog veri modelini içeren SQL Server örneğine erişmek üzere Entity Framework tarafından kullanılacak bağlantı dizesiyle ConnectionString adlı bir ortam değişkenini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="80b0b-140">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="80b0b-141">Bu durumda, aynı SQL Server kapsayıcısı birden çok veritabanını tutuyor.</span><span class="sxs-lookup"><span data-stu-id="80b0b-141">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="80b0b-142">Bu nedenle, Docker için geliştirme makinenizde daha az bellek gerekir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-142">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="80b0b-143">Ancak, her mikro hizmet veritabanı için bir SQL Server kapsayıcısı da dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b0b-143">However, you could also deploy one SQL Server container for each microservice database.</span></span>

- <span data-ttu-id="80b0b-144">SQL Server adı, Linux için SQL Server örneğini çalıştıran kapsayıcı için kullanılan ad olan SQL. Data ' dır.</span><span class="sxs-lookup"><span data-stu-id="80b0b-144">The SQL Server name is sql.data, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="80b0b-145">Bu kullanışlıdır; Bu ad çözümlemesini kullanabilmeniz (Docker ana bilgisayarına iç) ağ adresini çözümleyecek ve bu sayede diğer kapsayıcılardan eriştiğiniz kapsayıcıların iç IP 'sini bilmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="80b0b-145">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don’t need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="80b0b-146">Bağlantı dizesi bir ortam değişkeni tarafından tanımlandığından, bu değişkeni farklı bir mekanizmaya ve farklı bir zamanda ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b0b-146">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="80b0b-147">Örneğin, son Konaklarda üretime dağıtım yaparken veya Azure DevOps Services ya da tercih ettiğiniz DevOps sisteminizin CI/CD işlem hatlarından yararlanarak farklı bir bağlantı dizesi ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b0b-147">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in Azure DevOps Services or your preferred DevOps system.</span></span>

- <span data-ttu-id="80b0b-148">Docker Konağı içindeki Catalog. API hizmetine iç erişim için 80 bağlantı noktasını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="80b0b-148">It exposes port 80 for internal access to the catalog.api service within the Docker host.</span></span> <span data-ttu-id="80b0b-149">Konak, Linux için bir Docker görüntüsünü temel aldığı için şu anda bir Linux sanal makinesi. ancak kapsayıcıyı bir Windows görüntüsünde çalışacak şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b0b-149">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

- <span data-ttu-id="80b0b-150">Kapsayıcı üzerinde 80 numaralı bağlantı noktasını Docker ana makinesi (Linux VM) üzerinde bağlantı noktası 5101 ' e iletir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-150">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

- <span data-ttu-id="80b0b-151">Web hizmetini SQL. Data hizmetine bağlar (bir kapsayıcıda çalışan Linux veritabanı için SQL Server örneği).</span><span class="sxs-lookup"><span data-stu-id="80b0b-151">It links the web service to the sql.data service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="80b0b-152">Bu bağımlılığı belirttiğinizde, SQL. Data kapsayıcısı zaten başlatılana kadar Catalog. API kapsayıcısı başlatılmaz; Bu önemlidir çünkü Catalog. API SQL Server veritabanının önce çalışır ve çalışıyor olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-152">When you specify this dependency, the catalog.api container will not start until the sql.data container has already started; this is important because catalog.api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="80b0b-153">Ancak, bu tür bir kapsayıcı bağımlılığı birçok durumda yeterli değildir çünkü Docker yalnızca kapsayıcı düzeyinde kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="80b0b-153">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="80b0b-154">Bazen hizmet (Bu durumda SQL Server) hala hazırlanmayabilir, bu nedenle, istemci mikro hizmetinizdeki üstel geri alma ile yeniden deneme mantığını uygulamanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-154">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="80b0b-155">Bu şekilde, bir bağımlılık kapsayıcısı kısa bir süre için hazırsanız, uygulama yine de dayanıklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="80b0b-155">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

- <span data-ttu-id="80b0b-156">Dış sunuculara erişime izin verecek şekilde yapılandırıldı: ek\_konaklar ayarı, dış sunuculara veya makinelere, yerel bir SQL Server gibi, Docker ana bilgisayarı dışındaki (bir geliştirme Docker ana bilgisayarı olan varsayılan Linux VM 'nin dışında) erişmenizi sağlar geliştirme PC 'nizdeki örnek.</span><span class="sxs-lookup"><span data-stu-id="80b0b-156">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="80b0b-157">Ayrıca, aşağıdaki bölümlerde tartışacak başka, daha gelişmiş Docker-Compose. yıml ayarları da vardır.</span><span class="sxs-lookup"><span data-stu-id="80b0b-157">There are also other, more advanced docker-compose.yml settings that we will discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="80b0b-158">Çoklu ortamları hedeflemek için Docker-Compose dosyalarını kullanma</span><span class="sxs-lookup"><span data-stu-id="80b0b-158">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="80b0b-159">Docker-Compose. yıml dosyaları tanım dosyalarıdır ve bu biçimi anlayan birden çok altyapı tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-159">The docker-compose.yml files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="80b0b-160">En kolay araç Docker-Compose komutındır.</span><span class="sxs-lookup"><span data-stu-id="80b0b-160">The most straightforward tool is the docker-compose command.</span></span>

<span data-ttu-id="80b0b-161">Bu nedenle, Docker-Compose komutunu kullanarak aşağıdaki ana senaryoları hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b0b-161">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="80b0b-162">Geliştirme ortamları</span><span class="sxs-lookup"><span data-stu-id="80b0b-162">Development environments</span></span>

<span data-ttu-id="80b0b-163">Uygulama geliştirirken, bir uygulamayı yalıtılmış bir geliştirme ortamında çalıştırabilmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-163">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="80b0b-164">Bu ortamı oluşturmak için Docker-Compose CLı komutunu veya kapabileşenler altında Docker-Compose kullanan Visual Studio 'Yu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b0b-164">You can use the docker-compose CLI command to create that environment or use Visual Studio which uses docker-compose under the covers.</span></span>

<span data-ttu-id="80b0b-165">Docker-Compose. yıml dosyası, tüm uygulamanızın hizmet bağımlılıklarını (diğer hizmetler, önbellek, veritabanları, kuyruklar vb.) yapılandırmanıza ve belgeetmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="80b0b-165">The docker-compose.yml file allows you to configure and document all your application’s service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="80b0b-166">Docker-Compose CLı komutunu kullanarak her bağımlılık için bir veya daha fazla kapsayıcıyı tek bir komutla oluşturup başlatabilirsiniz (Docker-Compose).</span><span class="sxs-lookup"><span data-stu-id="80b0b-166">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="80b0b-167">Docker-Compose. yıml dosyaları Docker altyapısı tarafından yorumlanan yapılandırma dosyalarıdır, ancak aynı zamanda çok Kapsayıcılı uygulamanızın kompozisyonu hakkında uygun belge dosyaları da sunar.</span><span class="sxs-lookup"><span data-stu-id="80b0b-167">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="80b0b-168">Ortamları test etme</span><span class="sxs-lookup"><span data-stu-id="80b0b-168">Testing environments</span></span>

<span data-ttu-id="80b0b-169">Herhangi bir sürekli dağıtım (CD) veya sürekli tümleştirme (CI) işleminin önemli bir bölümü, birim testleri ve tümleştirme sınamalardır.</span><span class="sxs-lookup"><span data-stu-id="80b0b-169">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="80b0b-170">Bu otomatikleştirilmiş testler, kullanıcılardan etkilenmemesi için yalıtılmış bir ortam gerektirir ve uygulamanın verilerinde başka bir değişiklik olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-170">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application’s data.</span></span>

<span data-ttu-id="80b0b-171">Docker Compose, aşağıdaki komutlar gibi komut isteminizden veya betiklerinizde bulunan birkaç komut için yalıtılmış ortamı kolayca oluşturabilir ve yok edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="80b0b-171">With Docker Compose you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```console
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml up -d
./run_unit_tests
docker-compose -f docker-compose.yml -f docker-compose.test.override.yml down
```

#### <a name="production-deployments"></a><span data-ttu-id="80b0b-172">Üretim dağıtımları</span><span class="sxs-lookup"><span data-stu-id="80b0b-172">Production deployments</span></span>

<span data-ttu-id="80b0b-173">Ayrıca, bir uzak Docker altyapısına dağıtmak için Oluştur ' da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b0b-173">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="80b0b-174">Tipik bir durum, tek bir Docker ana bilgisayar örneğine (bir üretim VM 'si veya [Docker makinesi](https://docs.docker.com/machine/overview/)ile sağlanan sunucu gibi) dağıtılmaktır.</span><span class="sxs-lookup"><span data-stu-id="80b0b-174">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span>

<span data-ttu-id="80b0b-175">Başka bir Orchestrator (Azure Service Fabric, Kubernetes vb.) kullanıyorsanız, Docker-Compose. yml ' de olduğu gibi, diğer Orchestrator için gereken biçimde kurulum ve meta veri yapılandırma ayarları eklemeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-175">If you are using any other orchestrator (Azure Service Fabric, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="80b0b-176">Her durumda, Docker-Compose geliştirme, test ve üretim iş akışları için uygun bir araç ve meta veri biçimidir, ancak üretim iş akışı kullandığınız Orchestrator üzerinde farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-176">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="80b0b-177">Çeşitli ortamları işlemek için birden çok Docker-Compose dosyası kullanma</span><span class="sxs-lookup"><span data-stu-id="80b0b-177">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="80b0b-178">Farklı ortamları hedeflerken, birden çok oluşturma dosyası kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-178">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="80b0b-179">Bu, ortama bağlı olarak birden çok yapılandırma çeşitlemesi oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="80b0b-179">This lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="80b0b-180">Temel Docker-Compose dosyasını geçersiz kılma</span><span class="sxs-lookup"><span data-stu-id="80b0b-180">Overriding the base docker-compose file</span></span>

<span data-ttu-id="80b0b-181">Önceki bölümlerde gösterilen Basitleştirilmiş örneklerde olduğu gibi tek bir Docker-Compose. yıml dosyası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b0b-181">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="80b0b-182">Ancak, çoğu uygulama için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="80b0b-182">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="80b0b-183">Varsayılan olarak, Compose iki dosyayı okur, bir Docker-Compose. yıml ve isteğe bağlı bir Docker-Compose. override. yıml dosyası.</span><span class="sxs-lookup"><span data-stu-id="80b0b-183">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="80b0b-184">Şekil 6-11 ' de gösterildiği gibi, Visual Studio 'Yu kullanırken ve Docker desteğini etkinleştirirken, Visual Studio uygulamada hata ayıklamak için ek bir Docker-Compose. vs. Debug. g. i ml dosyası da oluşturur.\\Docker klasöründe bu dosyaya göz atabilirsiniz @no__t_ Ana çözüm klasöründe 1_.</span><span class="sxs-lookup"><span data-stu-id="80b0b-184">As shown in Figure 6-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates an additional docker-compose.vs.debug.g.yml file for debugging the application, you can take a look at this file in folder obj\\Docker\\ in the main solution folder.</span></span>

![Docker-Compose proje dosyası yapısı:. dockerıgnore, dosyaları yoksaymak için; Docker-Compose. yıml, mikro hizmetler oluşturmak için; Mikro hizmetler ortamını yapılandırmak için Docker-Compose. override. yıml.](./media/image12.png)

<span data-ttu-id="80b0b-186">**Şekil 6-11**.</span><span class="sxs-lookup"><span data-stu-id="80b0b-186">**Figure 6-11**.</span></span> <span data-ttu-id="80b0b-187">Visual Studio 'da Docker-dosyaları oluşturma 2017</span><span class="sxs-lookup"><span data-stu-id="80b0b-187">docker-compose files in Visual Studio 2017</span></span>

<span data-ttu-id="80b0b-188">Docker-Compose dosyalarını, Visual Studio Code veya alt lime gibi herhangi bir düzenleyici ile düzenleyebilir ve uygulamayı Docker-Compose up komutuyla çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b0b-188">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="80b0b-189">Kural gereği, Docker-Compose. yıml dosyası temel yapılandırmanızı ve diğer statik ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-189">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="80b0b-190">Bu, hizmet yapılandırmasının hedeflediğiniz dağıtım ortamına bağlı olarak değişmeyeceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-190">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="80b0b-191">Docker-Compose. override. yıml dosyası, adının önereceği gibi, temel yapılandırmayı geçersiz kılan yapılandırma ayarlarını (dağıtım ortamına bağlı yapılandırma gibi) içerir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-191">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="80b0b-192">Aynı zamanda farklı adlara sahip birden fazla geçersiz kılma dosyasına sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b0b-192">You can have multiple override files with different names also.</span></span> <span data-ttu-id="80b0b-193">Geçersiz kılma dosyaları genellikle uygulama için gerekli olan, ancak bir ortama veya dağıtıma özgü ek bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-193">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="80b0b-194">Birden çok ortamı hedefleme</span><span class="sxs-lookup"><span data-stu-id="80b0b-194">Targeting multiple environments</span></span>

<span data-ttu-id="80b0b-195">Tipik kullanım örneği, birden çok ortamı, hazırlama, CI veya geliştirme gibi birden çok ortamı hedefleyebilir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-195">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="80b0b-196">Bu farklılıkları desteklemek için, Şekil 6-12 ' de gösterildiği gibi, oluşturma yapılandırmanızı birden çok dosyaya bölebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b0b-196">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 6-12.</span></span>

![Farklı ortamları işlemek için birden çok Docker-Compose\*. FML dosyasını birleştirebilirsiniz.](./media/image13.png)

<span data-ttu-id="80b0b-198">**Şekil 6-12**.</span><span class="sxs-lookup"><span data-stu-id="80b0b-198">**Figure 6-12**.</span></span> <span data-ttu-id="80b0b-199">Temel Docker-Compose. yıml dosyasındaki değerleri geçersiz kılan birden çok Docker-dosya oluşturma</span><span class="sxs-lookup"><span data-stu-id="80b0b-199">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="80b0b-200">Temel Docker-Compose. yıml dosyası ile başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b0b-200">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="80b0b-201">Bu temel dosya, ortama bağlı olarak değişmeyen temel veya statik yapılandırma ayarlarını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-201">This base file has to contain the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="80b0b-202">Örneğin eShopOnContainers, temel dosya olarak aşağıdaki Docker-Compose. yıml dosyasına (daha az hizmetlerle Basitleştirilmiş) sahiptir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-202">For example, the eShopOnContainers has the following docker-compose.yml file (simplified with less services) as the base file.</span></span>

```yml
#docker-compose.yml (Base)
version: '3.4'
services:
  basket.api:
    image: eshop/basket.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Basket/Basket.API/Dockerfile
    depends_on:
      - basket.data
      - identity.api
      - rabbitmq

  catalog.api:
    image: eshop/catalog.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Catalog/Catalog.API/Dockerfile
    depends_on:
      - sql.data
      - rabbitmq

  marketing.api:
    image: eshop/marketing.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Marketing/Marketing.API/Dockerfile
    depends_on:
      - sql.data
      - nosql.data
      - identity.api
      - rabbitmq

  webmvc:
    image: eshop/webmvc:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Web/WebMVC/Dockerfile
    depends_on:
      - catalog.api
      - ordering.api
      - identity.api
      - basket.api
      - marketing.api

  sql.data:
    image: microsoft/mssql-server-linux:2017-latest

  nosql.data:
    image: mongo

  basket.data:
    image: redis

  rabbitmq:
    image: rabbitmq:3-management

```

<span data-ttu-id="80b0b-203">Temel Docker-Compose. yıml dosyasındaki değerler farklı hedef dağıtım ortamları nedeniyle değişmemelidir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-203">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="80b0b-204">Örneğin, webmvc hizmeti tanımına odaklandıysanız, bu bilgilerin ne kadar hedeflendiğine bakılmaksızın bu bilgilerin nasıl fazla olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b0b-204">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="80b0b-205">Aşağıdaki bilgilere sahipsiniz:</span><span class="sxs-lookup"><span data-stu-id="80b0b-205">You have the following information:</span></span>

- <span data-ttu-id="80b0b-206">Hizmet adı: webmvc.</span><span class="sxs-lookup"><span data-stu-id="80b0b-206">The service name: webmvc.</span></span>

- <span data-ttu-id="80b0b-207">Kapsayıcının özel görüntüsü: eshop/webmvc.</span><span class="sxs-lookup"><span data-stu-id="80b0b-207">The container’s custom image: eshop/webmvc.</span></span>

- <span data-ttu-id="80b0b-208">Özel Docker görüntüsünü oluşturma komutu, hangi Dockerfile 'ın kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-208">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

- <span data-ttu-id="80b0b-209">Diğer hizmetlerde bağımlılıklar, bu nedenle diğer bağımlılık kapsayıcıları başlatılana kadar bu kapsayıcı başlatılmaz.</span><span class="sxs-lookup"><span data-stu-id="80b0b-209">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="80b0b-210">Ek yapılandırmaya sahip olabilirsiniz ancak önemli nokta, temel Docker-Compose. yıml dosyasında yalnızca ortamlar genelinde ortak olan bilgileri ayarlamak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="80b0b-210">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="80b0b-211">Ardından Docker-Compose. override. yıml veya üretim ya da hazırlama için benzer dosyalarda, her ortam için özel yapılandırmayı yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-211">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="80b0b-212">Genellikle, eShopOnContainers 'dan aşağıdaki örnekte olduğu gibi, Docker-Compose. override. yml, geliştirme ortamınız için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="80b0b-212">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '3.4'

services:
# Simplified number of services here:

  basket.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_REDIS_BASKET_DB:-basket.data}
      - identityUrl=http://identity.api
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

  catalog.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_CATALOG_DB:-Server=sql.data;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word}
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

  marketing.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_MARKETING_DB:-Server=sql.data;Database=Microsoft.eShopOnContainers.Services.MarketingDb;User Id=sa;Password=Pass@word}
      - MongoConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosql.data}
      - MongoDatabase=MarketingDb
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}
      - identityUrl=http://identity.api
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
      - CatalogUrlHC=http://catalog.api/hc
      - OrderingUrlHC=http://ordering.api/hc
      - IdentityUrlHC=http://identity.api/hc
      - BasketUrlHC=http://basket.api/hc
      - MarketingUrlHC=http://marketing.api/hc
      - PaymentUrlHC=http://payment.api/hc
      - SignalrHubUrl=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5202
      - UseCustomizationData=True
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5100:80"
  sql.data:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosql.data:
    ports:
      - "27017:27017"
  basket.data:
    ports:
      - "6379:6379"
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672"

```

<span data-ttu-id="80b0b-213">Bu örnekte, geliştirme geçersiz kılma yapılandırması konağa bazı bağlantı noktaları gösterir, yönlendirme URL 'Leri ile ortam değişkenlerini tanımlar ve geliştirme ortamı için bağlantı dizelerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-213">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="80b0b-214">Bu ayarlar yalnızca geliştirme ortamına yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-214">These settings are all just for the development environment.</span></span>

<span data-ttu-id="80b0b-215">`docker-compose up` çalıştırdığınızda (veya Visual Studio 'dan başlattığınızda), komut geçersiz kılmaları her iki dosyayı birleştiriyor gibi otomatik olarak okur.</span><span class="sxs-lookup"><span data-stu-id="80b0b-215">When you run `docker-compose up` (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="80b0b-216">Üretim ortamı için farklı yapılandırma değerleriyle, bağlantı noktalarıyla veya bağlantı dizelerine sahip başka bir oluşturma dosyası istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="80b0b-216">Suppose that you want another Compose file for the production environment, with different configuration values, ports or connection strings.</span></span> <span data-ttu-id="80b0b-217">Farklı ayarlar ve ortam değişkenleriyle `docker-compose.prod.yml` adlı dosya gibi başka bir geçersiz kılma dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b0b-217">You can create another override file, like file named `docker-compose.prod.yml` with different settings and environment variables.</span></span> <span data-ttu-id="80b0b-218">Bu dosya farklı bir git deposunda depolanabilir veya yönetilen ve farklı bir ekip tarafından güvenli hale getirilmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-218">That file might be stored in a different Git repo or managed and secured by a different team.</span></span>

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="80b0b-219">Belirli bir geçersiz kılma dosyası ile dağıtım</span><span class="sxs-lookup"><span data-stu-id="80b0b-219">How to deploy with a specific override file</span></span>

<span data-ttu-id="80b0b-220">Birden çok geçersiz kılma dosyası ya da farklı bir ada sahip bir geçersiz kılma dosyası kullanmak için, Docker-Compose komutuyla-f seçeneğini kullanabilir ve dosyaları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b0b-220">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="80b0b-221">Birleştirme dosyalarını komut satırında belirtildikleri sırada oluşturun.</span><span class="sxs-lookup"><span data-stu-id="80b0b-221">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="80b0b-222">Aşağıdaki örnek, geçersiz kılma dosyalarıyla nasıl dağıtılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-222">The following example shows how to deploy with override files.</span></span>

```console
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="80b0b-223">Docker-Compose dosyalarında ortam değişkenlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="80b0b-223">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="80b0b-224">Önceki örneklerde gösterildiği gibi, özellikle üretim ortamlarında, ortam değişkenlerinden yapılandırma bilgilerini alabilmesi için kullanışlı bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-224">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="80b0b-225">$ {MY\_VAR} sözdizimini kullanarak Docker-Compose dosyalarınızda bir ortam değişkenine başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b0b-225">You can reference an environment variable in your docker-compose files using the syntax ${MY\_VAR}.</span></span> <span data-ttu-id="80b0b-226">Bir Docker-Compose. prod. yıml dosyasından aşağıdaki satır, bir ortam değişkeninin değerine nasıl başvurulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-226">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="80b0b-227">Ortam değişkenleri, ana bilgisayar ortamınıza (Linux, Windows, bulut kümesi, vb.) bağlı olarak farklı yollarla oluşturulur ve başlatılır.</span><span class="sxs-lookup"><span data-stu-id="80b0b-227">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="80b0b-228">Ancak, uygun bir yaklaşım. env dosyası kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="80b0b-228">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="80b0b-229">Docker-Compose dosyaları,. env dosyasında varsayılan ortam değişkenlerini bildirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="80b0b-229">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="80b0b-230">Ortam değişkenlerine yönelik bu değerler varsayılan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-230">These values for the environment variables are the default values.</span></span> <span data-ttu-id="80b0b-231">Ancak, ortamınızda (konak işletim sistemi veya ortam değişkenleri kümenizdeki) tanımlamış olabileceğiniz değerler tarafından geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-231">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="80b0b-232">Bu. env dosyasını Docker-Compose komutunun yürütüldüğü klasöre yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b0b-232">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="80b0b-233">Aşağıdaki örnek, eShopOnContainers uygulaması için [. env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) dosyası gibi bir. env dosyasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-233">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) file for the eShopOnContainers application.</span></span>

```env
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="80b0b-234">Docker-Compose, bir. env dosyasındaki her satırın \<değişken\>=\<değer\>biçiminde olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="80b0b-234">Docker-compose expects each line in an .env file to be in the format \<variable\>=\<value\>.</span></span>

<span data-ttu-id="80b0b-235">Çalışma zamanı ortamında ayarlanan değerlerin her zaman. env dosyası içinde tanımlanan değerleri geçersiz kıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="80b0b-235">Note that the values set in the runtime environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="80b0b-236">Benzer şekilde, komut satırı komut bağımsız değişkenleri ile geçirilen değerler aynı zamanda. env dosyasında ayarlanan varsayılan değerleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="80b0b-236">In a similar way, values passed via command-line command arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="80b0b-237">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="80b0b-237">Additional resources</span></span>

- <span data-ttu-id="80b0b-238">**Docker Compose \ genel bakış**</span><span class="sxs-lookup"><span data-stu-id="80b0b-238">**Overview of Docker Compose** \</span></span>
    <https://docs.docker.com/compose/overview/>

- <span data-ttu-id="80b0b-239">**Birden çok oluşturma dosyası** </span><span class="sxs-lookup"><span data-stu-id="80b0b-239">**Multiple Compose files** </span></span>\
    [https://docs.docker.com/compose/extends/\#multiple-compose-files](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="80b0b-240">İyileştirilmiş ASP.NET Core Docker görüntüleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="80b0b-240">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="80b0b-241">Internet 'teki kaynaklarda Docker ve .NET Core 'u araştırıyorsanız, kaynağınızı bir kapsayıcıya kopyalayarak bir Docker görüntüsü oluşturmanın basitliğini gösteren Dockerfiles 'ı bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b0b-241">If you are exploring Docker and .NET Core on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="80b0b-242">Bu örnekler, basit bir yapılandırma kullanarak, uygulamanızla birlikte paketlenmiş bir Docker görüntüsüne sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b0b-242">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="80b0b-243">Aşağıdaki örnekte, bu Vein içindeki basit bir Dockerfile gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-243">The following example shows a simple Dockerfile in this vein.</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/sdk:2.2
WORKDIR /app
ENV ASPNETCORE_URLS http://+:80
EXPOSE 80
COPY . .
RUN dotnet restore
ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="80b0b-244">Bunun gibi bir Dockerfile çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="80b0b-244">A Dockerfile like this will work.</span></span> <span data-ttu-id="80b0b-245">Ancak, görüntülerinizi önemli ölçüde iyileştirebilirsiniz, özellikle de üretim görüntüleriniz.</span><span class="sxs-lookup"><span data-stu-id="80b0b-245">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="80b0b-246">Kapsayıcı ve mikro hizmetler modelinde, kapsayıcılardan sürekli olarak başlangıç yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b0b-246">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="80b0b-247">Kapsayıcıları kullanmanın tipik yolu, kapsayıcı atılabilir olduğundan, uyuma bir kapsayıcıyı yeniden başlatmaz.</span><span class="sxs-lookup"><span data-stu-id="80b0b-247">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="80b0b-248">Düzenleyiciler (Kubernetes ve Azure Service Fabric gibi) yalnızca yeni görüntü örnekleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="80b0b-248">Orchestrators (like Kubernetes and Azure Service Fabric) simply create new instances of images.</span></span> <span data-ttu-id="80b0b-249">Bunun anlamı, örnek oluşturma işleminin daha hızlı olması için uygulamayı derleme sırasında önceden derleyerek iyileştirmeniz gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-249">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="80b0b-250">Kapsayıcı başlatıldığında, çalıştırılmaya hazırlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="80b0b-250">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="80b0b-251">.NET Core ve Docker hakkında birçok blog gönderisine gördüğünüz gibi, DotNet CLı 'dan `dotnet restore` ve `dotnet build` komutlarını kullanarak çalışma zamanında geri yükleme ve derleme yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="80b0b-251">You should not restore and compile at run time, using `dotnet restore` and `dotnet build` commands from the dotnet CLI that, as you see in many blog posts about .NET Core and Docker.</span></span>

<span data-ttu-id="80b0b-252">.NET ekibi, .NET Core ve kapsayıcı için iyileştirilmiş bir çerçeve ASP.NET Core için önemli bir iş yapıyor.</span><span class="sxs-lookup"><span data-stu-id="80b0b-252">The .NET team has been doing important work to make .NET Core and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="80b0b-253">.NET Core, küçük bellek ayak izine sahip hafif bir çerçeve; ekip, üç ana senaryo için iyileştirilmiş Docker görüntülerine odaklanmıştır ve 2,1 sürümünden itibaren *DotNet/Core*'Da Docker Hub kayıt defterinde yayımlanır:</span><span class="sxs-lookup"><span data-stu-id="80b0b-253">Not only is .NET Core a lightweight framework with a small memory footprint; the team has focused on optimized Docker images for three main scenarios and published them in the Docker Hub registry at *dotnet/core*, beginning with version 2.1:</span></span>

1. <span data-ttu-id="80b0b-254">**Geliştirme**: önceliğin, değişiklikleri hızla yineleme ve hata ayıklama özelliği olduğu ve boyutun ikincil olduğu durumlar burada.</span><span class="sxs-lookup"><span data-stu-id="80b0b-254">**Development**: Where the priority is the ability to quickly iterate and debug changes, and where size is secondary.</span></span>

2. <span data-ttu-id="80b0b-255">**Yapı**: öncelik, uygulamayı derler ve ikili dosyaları ve diğer bağımlılıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-255">**Build**: The priority is compiling the application and includes binaries and other dependencies to optimize binaries.</span></span>

3. <span data-ttu-id="80b0b-256">**Üretim**: odağın, kapsayıcının hızlı bir şekilde dağıtıldığı ve başladığı yerde, bu görüntülerin ikili dosyalarla ve uygulamayı çalıştırmak için gereken içerikle sınırlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="80b0b-256">**Production**: Where the focus is fast deploying and starting of containers, so these images are limited to the binaries and the content needed to run the application.</span></span>

<span data-ttu-id="80b0b-257">Bu işlemi gerçekleştirmek için, .NET ekibi [DotNet/Core](https://hub.docker.com/_/microsoft-dotnet-core/) 'da dört temel çeşit sağlar (Docker Hub 'da):</span><span class="sxs-lookup"><span data-stu-id="80b0b-257">To achieve this, the .NET team is providing four basic variants in [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) (at Docker Hub):</span></span>

1. <span data-ttu-id="80b0b-258">**SDK**: geliştirme ve derleme senaryoları için</span><span class="sxs-lookup"><span data-stu-id="80b0b-258">**sdk**: for development and build scenarios</span></span>
1. <span data-ttu-id="80b0b-259">**ASPNET**: ASP.NET üretim senaryoları için</span><span class="sxs-lookup"><span data-stu-id="80b0b-259">**aspnet**: for ASP.NET production scenarios</span></span>
1. <span data-ttu-id="80b0b-260">**çalışma zamanı**: .NET üretim senaryoları için</span><span class="sxs-lookup"><span data-stu-id="80b0b-260">**runtime**: for .NET production scenarios</span></span>
1. <span data-ttu-id="80b0b-261">**Runtime-Deps**: [kendi içindeki uygulamaların](../../../core/deploying/index.md#self-contained-deployments-scd)üretim senaryoları için.</span><span class="sxs-lookup"><span data-stu-id="80b0b-261">**runtime-deps**: for production scenarios of [self-contained applications](../../../core/deploying/index.md#self-contained-deployments-scd).</span></span>

<span data-ttu-id="80b0b-262">Daha hızlı başlangıç için, çalışma zamanı görüntüleri Ayrıca aspnetcore\_URL 'lerini otomatik olarak 80 numaralı bağlantı noktasına ayarlar ve derlemelerin yerel görüntü önbelleğini oluşturmak için Ngen 'i kullanır.</span><span class="sxs-lookup"><span data-stu-id="80b0b-262">For faster startup, runtime images also automatically set aspnetcore\_urls to port 80 and use Ngen to create a native image cache of assemblies.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="80b0b-263">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="80b0b-263">Additional resources</span></span>

- <span data-ttu-id="80b0b-264">**ASP.NET Core ile Iyileştirilmiş Docker görüntüleri oluşturma**</span><span class="sxs-lookup"><span data-stu-id="80b0b-264">**Building Optimized Docker Images with ASP.NET Core**</span></span>  
  <https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/>

- <span data-ttu-id="80b0b-265">**.NET Core Uygulamaları için Docker Görüntülerinizi Derleme**</span><span class="sxs-lookup"><span data-stu-id="80b0b-265">**Building Docker Images for .NET Core Applications**</span></span>  
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

> [!div class="step-by-step"]
> <span data-ttu-id="80b0b-266">[Önceki](data-driven-crud-microservice.md)
> [İleri](database-server-container.md)</span><span class="sxs-lookup"><span data-stu-id="80b0b-266">[Previous](data-driven-crud-microservice.md)
[Next](database-server-container.md)</span></span>
