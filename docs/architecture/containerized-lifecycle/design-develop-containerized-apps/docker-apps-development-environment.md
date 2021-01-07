---
title: Docker uygulamaları için geliştirme ortamı
description: Docker geliştirme yaşam döngüsünü destekleyen en önemli geliştirme aracı seçeneklerini öğrenin.
ms.date: 01/06/2021
ms.openlocfilehash: c6c4a1fda41131c00ba87808ed408f1d3250cabf
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970531"
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="d7490-103">Docker uygulamaları için geliştirme ortamı</span><span class="sxs-lookup"><span data-stu-id="d7490-103">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="d7490-104">Geliştirme araçları seçimleri: IDE veya düzenleyici</span><span class="sxs-lookup"><span data-stu-id="d7490-104">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="d7490-105">Tam ve güçlü bir IDE ya da hafif ve çevik bir düzenleyiciyi tercih ediyorsanız, Microsoft, Docker uygulamaları geliştirmeye ne zaman bahsedildiğinizi de kapsamıştır.</span><span class="sxs-lookup"><span data-stu-id="d7490-105">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="d7490-106">Visual Studio Code ve Docker CLı (Mac, Linux ve Windows için platformlar arası araçlar)</span><span class="sxs-lookup"><span data-stu-id="d7490-106">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="d7490-107">Herhangi bir geliştirme dilini destekleyen basit, platformlar arası bir düzenleyiciyi tercih ediyorsanız, Visual Studio Code ve Docker CLı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7490-107">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="d7490-108">Bu ürünler, geliştirici iş akışını hızlandırma açısından kritik olan basit ancak sağlam bir deneyim sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7490-108">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="d7490-109">Docker geliştiricileri, "Docker for Mac" veya "Docker for Windows" (geliştirme ortamı) yükleyerek, tek bir Docker CLı kullanarak hem Windows hem de Linux (çalışma zamanı ortamı) için uygulama oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="d7490-109">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="d7490-110">Ayrıca, Visual Studio Code Dockerfiles için IntelliSense ile Docker uzantılarını ve düzenleyiciden Docker komutlarını çalıştırmak için kısayol görevlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="d7490-110">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
> <span data-ttu-id="d7490-111">Visual Studio Code indirmek için bölümüne gidin <https://code.visualstudio.com/download> .</span><span class="sxs-lookup"><span data-stu-id="d7490-111">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>
>
> <span data-ttu-id="d7490-112">Mac ve Windows için Docker indirmek için adresine gidin <https://www.docker.com/products/docker> .</span><span class="sxs-lookup"><span data-stu-id="d7490-112">To download Docker for Mac and Windows, go to <https://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a><span data-ttu-id="d7490-113">Visual Studio ile Docker Araçları (Windows geliştirme makinesi)</span><span class="sxs-lookup"><span data-stu-id="d7490-113">Visual Studio with Docker Tools (Windows development machine)</span></span>

<span data-ttu-id="d7490-114">Yerleşik Docker Araçları 'nın etkin olduğu Visual Studio 2019 ' i kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="d7490-114">It's recommend that you use Visual Studio 2019 with the built-in Docker Tools enabled.</span></span> <span data-ttu-id="d7490-115">Visual Studio ile uygulamalarınızı doğrudan seçilen Docker ortamında geliştirebilir, çalıştırabilir ve doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7490-115">With Visual Studio, you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="d7490-116">Uygulamanızda (tek kapsayıcı veya birden çok kapsayıcı) doğrudan bir Docker konağında hata ayıklamak için F5 tuşuna basın veya kapsayıcıyı yeniden oluşturmak zorunda kalmadan uygulamanızı düzenlemek ve yenilemek için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="d7490-116">Press F5 to debug your application (single container or multiple containers) directly in a Docker host, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="d7490-117">Windows geliştiricilerinin Linux veya Windows için Docker Kapsayıcıları oluşturması için kullanabileceğiniz en basit ve en güçlü seçenektir.</span><span class="sxs-lookup"><span data-stu-id="d7490-117">It's the simplest and most powerful choice for Windows developers to create Docker containers for Linux or Windows.</span></span>

### <a name="visual-studio-for-mac-mac-development-machine"></a><span data-ttu-id="d7490-118">Mac için Visual Studio (Mac geliştirme makinesi)</span><span class="sxs-lookup"><span data-stu-id="d7490-118">Visual Studio for Mac (Mac development machine)</span></span>

<span data-ttu-id="d7490-119">Docker tabanlı uygulamalar geliştirirken [Mac için Visual Studio](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7490-119">You can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) when developing Docker-based applications.</span></span> <span data-ttu-id="d7490-120">Mac için Visual Studio, Mac için Visual Studio Code karşılaştırıldığında daha zengin bir IDE sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7490-120">Visual Studio for Mac offers a richer IDE when compared to Visual Studio Code for Mac.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="d7490-121">Dil ve çerçeve seçimleri</span><span class="sxs-lookup"><span data-stu-id="d7490-121">Language and framework choices</span></span>

<span data-ttu-id="d7490-122">En modern dillerle Microsoft araçları 'nı kullanarak Docker uygulamaları geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7490-122">You can develop Docker applications using Microsoft tools with most modern languages.</span></span> <span data-ttu-id="d7490-123">Aşağıda bir başlangıç listesi verilmiştir ancak bunlarla sınırlı değilsiniz:</span><span class="sxs-lookup"><span data-stu-id="d7490-123">The following is an initial list, but you're not limited to it:</span></span>

- <span data-ttu-id="d7490-124">.NET ve ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d7490-124">.NET and ASP.NET Core</span></span>
- <span data-ttu-id="d7490-125">Node.js</span><span class="sxs-lookup"><span data-stu-id="d7490-125">Node.js</span></span>
- <span data-ttu-id="d7490-126">Başlayın</span><span class="sxs-lookup"><span data-stu-id="d7490-126">Go</span></span>
- <span data-ttu-id="d7490-127">Java</span><span class="sxs-lookup"><span data-stu-id="d7490-127">Java</span></span>
- <span data-ttu-id="d7490-128">Ruby</span><span class="sxs-lookup"><span data-stu-id="d7490-128">Ruby</span></span>
- <span data-ttu-id="d7490-129">Python</span><span class="sxs-lookup"><span data-stu-id="d7490-129">Python</span></span>

<span data-ttu-id="d7490-130">Temel olarak, Linux veya Windows 'da Docker tarafından desteklenen tüm modern dilleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7490-130">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d7490-131">[Önceki](deploy-azure-kubernetes-service.md) 
> [Sonraki](docker-apps-inner-loop-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="d7490-131">[Previous](deploy-azure-kubernetes-service.md)
[Next](docker-apps-inner-loop-workflow.md)</span></span>
