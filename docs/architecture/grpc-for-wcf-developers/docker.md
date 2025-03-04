---
title: WCF geliştiricileri için Docker-gRPC
description: ASP.NET Core gRPC uygulamaları için Docker görüntüleri oluşturma
ms.date: 01/06/2021
ms.openlocfilehash: f59518a28b0a1dee75c792ba03bd4af826638502
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970095"
---
# <a name="create-docker-images"></a>Docker görüntüleri oluşturma

Bu bölümde, ASP.NET Core gRPC uygulamalarına yönelik Docker görüntülerinin oluşturulması, Docker, Kubernetes veya diğer kapsayıcı ortamlarında çalıştırılmaya hazır olarak ele alınmaktadır. ASP.NET Core MVC web uygulamasıyla kullanılan örnek uygulama ve gRPC hizmeti, GitHub 'daki [DotNet-Architecture/GRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) deposunda bulunur.

## <a name="microsoft-base-images-for-aspnet-core-applications"></a>ASP.NET Core uygulamalar için Microsoft temel görüntüleri

Microsoft, .NET uygulamaları oluşturmaya ve çalıştırmaya yönelik bir dizi temel görüntü sağlar. ASP.NET Core 5,0 görüntüsü oluşturmak için iki temel görüntü kullanırsınız:

- Uygulamayı derlemek ve yayımlamak için bir SDK görüntüsü.
- Dağıtım için bir çalışma zamanı görüntüsü.

| Görüntü | Açıklama |
| ----- | ----------- |
| [mcr.microsoft.com/dotnet/sdk](https://hub.docker.com/_/microsoft-dotnet-sdk/) | İle uygulama oluşturmak için `docker build` . Üretimde kullanılmamalıdır. |
| [mcr.microsoft.com/dotnet/aspnet](https://hub.docker.com/_/microsoft-dotnet-aspnet/) | Çalışma zamanı ve ASP.NET Core bağımlılıklarını içerir. Üretim için. |

Her görüntü için, etiketlere göre ayırt edilen farklı Linux dağıtımlarını temel alan dört çeşit vardır.

| Resim etiketi (ler) | Linux | Notlar |
| --------- | ----- | ----- |
| 5,0-Buster-Slim, 5,0 | Debian 10 | Bir işletim sistemi değişkeni belirtilmemişse varsayılan görüntü. |
| 5,0-alçam | Alçam 3,12 | Alp taban görüntüleri, Deleyden veya Ubuntu 'dan çok daha küçüktür. |
| 5,0-odak| Ubuntu 20.04 | |

Alp temel görüntüsü 100 MB boyutunda, de, ve Ubuntu görüntüleri için 200 MB ile karşılaştırılır. Bazı yazılım paketleri veya kitaplıkları alp 'nin paket yönetiminde bulunmayabilir. Hangi görüntünün kullanılacağı konusunda emin değilseniz, muhtemelen varsayılan deni seçmeniz gerekir.

> [!IMPORTANT]
> Derleme ve çalışma zamanı için aynı Linux türevini kullandığınızdan emin olun. Bir çeşit üzerinde oluşturulan ve yayımlanan uygulamalar, başka bir değişkenle çalışmayabilir.

## <a name="create-a-docker-image"></a>Docker görüntüsü oluşturma

Docker görüntüsü bir *Dockerfile* tarafından tanımlanır. Bu *Dockerfile* , uygulamayı oluşturmak için gereken tüm komutları içeren bir metin dosyasıdır ve uygulamayı oluşturmak ya da çalıştırmak için gerekli olan tüm bağımlılıkları yükler. Aşağıdaki örnekte, bir ASP.NET Core 5,0 uygulaması için en basit Dockerfile gösterilmektedir:

```dockerfile
FROM mcr.microsoft.com/dotnet/sdk:5.0 as build

WORKDIR /src

COPY ./StockKube.sln .
COPY ./src/StockData/StockData.csproj ./src/StockData/
COPY ./src/StockWeb/StockWeb.csproj ./src/StockWeb/

RUN dotnet restore

COPY . .

RUN dotnet publish --no-restore -c Release -o /published src/StockData/StockData.csproj

FROM mcr.microsoft.com/dotnet/aspnet:5.0 as runtime

# Uncomment the line below if running with HTTPS
# ENV ASPNETCORE_URLS=https://+:443

WORKDIR /app

COPY --from=build /published .

ENTRYPOINT [ "dotnet", "StockData.dll" ]
```

Dockerfile iki bölümden oluşur: ilki `sdk` uygulamayı derlemek ve yayımlamak için temel görüntüyü kullanır; ikincisi ise temelden bir çalışma zamanı görüntüsü oluşturur `aspnet` . Bunun nedeni, `sdk` görüntünün 900 MB 'ın etrafında, çalışma zamanı görüntüsü için 200 MB 'nin etrafında, ve içeriğinin çoğunun çalışma zamanında gereksiz olmasından kaynaklanır.

### <a name="the-build-steps"></a>Derleme adımları

| Adım | Açıklama |
| ---- | ----------- |
| `FROM ...` | Temel görüntüyü bildirir ve `builder` diğer adı atar. |
| `WORKDIR /src` | Dizini oluşturur `/src` ve geçerli çalışma dizini olarak ayarlar. |
| `COPY . .` | Konaktaki geçerli dizinin altındaki her şeyi görüntüdeki geçerli dizine kopyalar. |
| `RUN dotnet restore` | Tüm harici paketleri (ASP.NET Core 3,0 Framework SDK ile önceden yüklenmiş) geri yükler. |
| `RUN dotnet publish ...` | Bir yayın derlemesi oluşturur ve yayımlar. `--runtime`Bayrağın gerekli olmadığını unutmayın. |

### <a name="the-runtime-image-steps"></a>Çalışma zamanı görüntüsü adımları

| Adım | Açıklama |
| ---- | ----------- |
| `FROM ...` | Yeni bir temel görüntü bildirir. |
| `WORKDIR /app` | Dizini oluşturur `/app` ve geçerli çalışma dizini olarak ayarlar. |
| `COPY --from=builder ...` | `builder`İlk satırdaki diğer adı kullanarak yayımlanmış uygulamayı önceki görüntüden kopyalar `FROM` . |
| `ENTRYPOINT [ ... ]` | Kapsayıcı başladığında çalıştırılacak komutu ayarlar. `dotnet`Çalışma zamanı görüntüsündeki komutu yalnızca dll dosyalarını çalıştırabilir. |

### <a name="https-in-docker"></a>Docker 'da HTTPS

Docker için Microsoft temel görüntüleri, `ASPNETCORE_URLS` ortam değişkenini, `http://+:80` Kestrel Bu bağlantı noktasında HTTPS olmadan çalıştığı anlamına gelen olarak ayarlar. HTTPS 'yi özel bir sertifikayla kullanıyorsanız ( [Şirket içinde barındırılan gRPC uygulamalarında](self-hosted.md)açıklandığı gibi), bu yapılandırmayı geçersiz kılmanız gerekir. Dockerfile 'ın çalışma zamanı görüntüsü oluşturma bölümünde ortam değişkenini ayarlayın.

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/aspnet:5.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a>. Dockerıgnore dosyası

`.gitignore`Kaynak denetiminden belirli dosyaları ve dizinleri hariç tutmakta olan dosyalar, `.dockerignore` dosya ve dizinlerin derleme sırasında görüntüye kopyalanmasını hariç tutmak için kullanılabilir. Bu dosya, yalnızca kopyalama zamandan tasarruf etmez, ancak `obj` bilgisayarınızdaki bir dizinin görüntüye kopyalanmasını gerektiren bazı hatalardan da kaçınabilirsiniz. En azından, dosyanıza ve için girdi eklemeniz gerekir `bin` `obj` `.dockerignore` .

```console
bin/
obj/
```

## <a name="build-the-image"></a>Görüntü oluşturma

`StockKube.sln`İki farklı uygulama içeren bir çözüm için `StockData` `StockWeb` , dockerfile 'ın her biri için temel dizine yerleştirilmeleri en iyisidir. Bu durumda, görüntüyü derlemek için `docker build` dosyanın bulunduğu dizinden aşağıdaki komutu kullanın `.sln` .

```console
docker build -t stockdata:1.0.0 -f ./src/StockData/Dockerfile .
```

`--tag`Tam adlandırılmış bayrak (kısaltıldı `-t` ), belirtilmişse gerçek etiket dahil olmak üzere görüntünün tam adını belirtir. `.`Sonda, yapı çalıştırılacağı bağlamı ve `COPY` Dockerfile içindeki komutlar için geçerli çalışma dizinini belirtir.

Tek bir çözümde birden çok uygulamanız varsa, dosyanın yanında her bir uygulama için Dockerfile dosyasını kendi klasöründe tutabilirsiniz `.csproj` . `docker build`Çözümün ve tüm projelerin görüntüye kopyalandığından emin olmak için komutu yine de temel dizinden çalıştırmalısınız. `--file`(Veya) bayrağını kullanarak geçerli dizinin altına bir Dockerfile belirtebilirsiniz `-f` .

```console
docker build -t stockdata:1.0.0 -f ./src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a>Görüntüyü makinenizdeki bir kapsayıcıda çalıştırın

Görüntüyü yerel Docker örneğiniz içinde çalıştırmak için `docker run` komutunu kullanın.

```console
docker run -ti -p 5000:80 stockdata:1.0.0
```

`-ti`Bayrak geçerli terminalinizi kapsayıcının terminaline bağlar ve etkileşimli modda çalışır. `-p 5000:80`Kapsayıcıda, localhost ağ arabirimindeki bağlantı noktası 5000 ' e bağlantı noktası 80 ' ü yayınlar.

## <a name="push-the-image-to-a-registry"></a>Görüntüyü bir kayıt defterine gönderme

Görüntünün çalıştığını doğruladıktan sonra, diğer sistemlerde kullanılabilir hale getirmek için bir Docker kayıt defterine gönderin. İç ağların bir Docker kayıt defteri sağlaması gerekir. Bu etkinlik, [Docker 'ın kendi `registry` görüntüsünü](https://docs.docker.com/registry/deploying/) (Docker kayıt defteri bir Docker kapsayıcısında çalıştırılır) çalıştırmak kadar basit olabilir, ancak daha kapsamlı çeşitli çözümler mevcuttur. Dış paylaşım ve bulut kullanımı için [Azure Container Registry](/azure/container-registry/) veya [Docker Hub](https://docs.docker.com/docker-hub/repos/)gibi çeşitli yönetilen kayıt defterleri mevcuttur.

Docker Hub 'ına göndermek için, görüntü adını Kullanıcı veya kuruluş adınızla ön eke koyun.

```console
docker tag stockdata:1.0.0 <myorg>/stockdata:1.0.0
docker push <myorg>/stockdata:1.0.0
```

Özel bir kayıt defterine göndermek için, görüntü adını kayıt defteri ana bilgisayar adı ve kuruluş adı ile önek olarak ekleyin.

```console
docker tag stockdata <internal-registry:5000>/<myorg>/stockdata:1.0.0
docker push <internal-registry:5000>/<myorg>/stockdata:1.0.0
```

Görüntü bir kayıt defterinden olduktan sonra, tek tek Docker konaklarına veya Kubernetes gibi bir kapsayıcı düzenleme altyapısına dağıtabilirsiniz.

>[!div class="step-by-step"]
>[Önceki](self-hosted.md) 
> [Sonraki](kubernetes.md)
