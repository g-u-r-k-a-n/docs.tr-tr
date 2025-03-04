---
ms.openlocfilehash: ed269683f5c4569c21ae53e9a3c1ec65eb5ebd43
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506874"
---

### <a name="install-the-sdk"></a>SDK Yükleme

.NET SDK, .NET ile uygulama geliştirmenize olanak tanır. .NET SDK 'yı yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez. .NET SDK 'yı yüklemek için aşağıdaki komutları çalıştırın:

```bash
sudo zypper install dotnet-sdk-5.0
```

### <a name="install-the-runtime"></a>Çalışma zamanını yükler

ASP.NET Core çalışma zamanı, .NET ile yapılan ve çalışma zamanı sağlamayan uygulamaları çalıştırmanızı sağlar. Aşağıdaki komutlar, .NET için en uyumlu çalışma zamanı olan ASP.NET Core çalışma zamanını yükler. Terminalinizde aşağıdaki komutları çalıştırın:

```bash
sudo zypper install aspnetcore-runtime-5.0
```

ASP.NET Core çalışma zamanına alternatif olarak, ASP.NET Core desteği içermeyen .NET çalışma zamanını yükleyebilirsiniz: `aspnetcore-runtime-5.0` önceki komutta ile değiştirin `dotnet-runtime-5.0` :

```bash
sudo zypper install dotnet-runtime-5.0
```
