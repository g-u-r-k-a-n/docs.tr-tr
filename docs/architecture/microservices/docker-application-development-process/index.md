---
title: Docker tabanlı uygulamalar için geliştirme süreci
description: Docker tabanlı uygulamalar geliştirmeye yönelik seçeneklere yönelik üst düzey bir genel bakış alın. Çoklu platform desteği (Windows, macOS ve Linux) için Windows, Mac için Visual Studio veya Visual Studio Code için istediğiniz Visual Studio 'Yu kullanma.
ms.date: 01/13/2021
ms.openlocfilehash: 3a4f4078e745c52e8eca46473668e3319917bfd2
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188302"
---
# <a name="development-process-for-docker-based-applications"></a>Docker tabanlı uygulamalar için geliştirme süreci

*Visual Studio ile odaklanan tümleşik geliştirme ortamı (IDE) ve Docker için Visual Studio Araçları veya Docker CLı ve Visual Studio Code ile odaklanan CLı/düzenleyici için tümleşik geliştirme ortamı (IDE) gibi Kapsayıcılı .NET uygulamaları geliştirin.*

## <a name="development-environment-for-docker-apps"></a>Docker uygulamaları için geliştirme ortamı

### <a name="development-tool-choices-ide-or-editor"></a>Geliştirme aracı seçimleri: IDE veya düzenleyici

Tam ve güçlü bir IDE veya hafif ve çevik bir düzenleyiciyi tercih etmeksizin, Microsoft, Docker uygulamaları geliştirmek için kullanabileceğiniz araçlara sahiptir.

**Visual Studio (Windows için).** Visual Studio ile Docker tabanlı .NET 5 uygulama geliştirme, Visual Studio 2019 sürüm 16,4 veya üstünü gerektirir. Visual Studio 2019, zaten yerleşik olarak bulunan Docker Araçları ile birlikte gelir. Docker Araçları, uygulamalarınızı doğrudan hedef Docker ortamında geliştirmenize, çalıştırmanıza ve doğrulamanıza olanak sağlar. F5 tuşuna basarak uygulamanızı (tek bir kapsayıcı veya birden çok kapsayıcı) doğrudan bir Docker konağına kaydedebilir ve hata ayıklamanızı sağlar veya kapsayıcıyı yeniden oluşturmak zorunda kalmadan uygulamanızı düzenlemek ve yenilemek için CTRL + F5 ' e basabilirsiniz. Bu IDE, Docker tabanlı uygulamalar için en güçlü geliştirme seçimdir.

**Mac için Visual Studio.** MacOS 'ta çalışan Xamarin Studio bir IDE, evmidir. .NET 5 geliştirme için sürüm 8,4 veya üzerini gerektirir. Bu araç, güçlü bir IDE kullanmak isteyen macOS makinelerinde çalışan geliştiriciler için tercih edilen seçim olmalıdır.

**Visual Studio Code ve Docker CLI**. Herhangi bir geliştirme dilini destekleyen basit ve platformlar arası bir düzenleyiciyi tercih ediyorsanız, Visual Studio Code ve Docker CLı kullanabilirsiniz. Bu IDE, macOS, Linux ve Windows için platformlar arası bir geliştirme yaklaşımıdır. Ayrıca, Visual Studio Code Dockerfiles için IntelliSense ve düzenleyiciden Docker komutlarını çalıştırmak için kısayol görevleri gibi Docker için uzantıları destekler.

[Docker Desktop Community Edition 'ı (CE)](https://hub.docker.com/search/?type=edition&offering=community)yükleyerek, tek bir DOCKER CLI kullanarak hem Windows hem de Linux için uygulama oluşturabilirsiniz.

### <a name="additional-resources"></a>Ek kaynaklar

- **Visual Studio**. Resmi site. \
  [https://visualstudio.microsoft.com/vs/](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

- **Visual Studio Code**. Resmi site. \
  <https://code.visualstudio.com/download>

- **Windows Community Edition için Docker Desktop (CE)** \
  [https://hub.docker.com/editions/community/docker-ce-desktop-windows](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

- **Mac Community Edition için Docker Desktop (CE)** \
  [https://hub.docker.com/editions/community/docker-ce-desktop-mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>Docker kapsayıcıları için .NET dilleri ve çerçeveleri

Bu kılavuzun önceki bölümlerinde belirtildiği gibi, Docker Kapsayıcılı .NET uygulamaları geliştirirken .NET Framework, .NET 5 veya açık kaynaklı mono projesi kullanabilirsiniz. \# \# Hangi .NET Framework 'ün kullanımda olduğuna bağlı olarak, Linux veya Windows kapsayıcılarını hedeflemek için C, F veya Visual Basic ile geliştirebilirsiniz. Daha ayrıntılı about.NET dil için bkz. [.NET dil stratejisi](https://devblogs.microsoft.com/dotnet/the-net-language-strategy/)blog gönderisi.

>[!div class="step-by-step"]
>[Önceki](../architect-microservice-container-applications/scalable-available-multi-container-microservice-applications.md) 
> [Sonraki](docker-app-development-workflow.md)
