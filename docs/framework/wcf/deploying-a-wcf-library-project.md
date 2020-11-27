---
title: Bir WCF Kitaplık Projesini Dağıtma
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: e3a90f03639a888b4528a1962a24b7adc5d43c58
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96260896"
---
# <a name="deploying-a-wcf-library-project"></a>Bir WCF Kitaplık Projesini Dağıtma

Bu konu, bir Windows Communication Foundation (WCF) hizmet kitaplığı projesini nasıl dağıtabileceğinizi açıklamaktadır.  
  
## <a name="deploying-a-wcf-service-library"></a>WCF hizmet kitaplığı dağıtma  

 Bir WCF hizmet kitaplığı, dinamik bağlantı kitaplığı (DLL). Bu nedenle, kendi üzerinde yürütülemez. Barındırma ortamına dağıtılması gerekir. Bu işlem hakkında daha fazla bilgi için bkz. [WCF hizmetleri barındırma ve](/previous-versions/dotnet/articles/bb332338(v=msdn.10))kullanma.  
  
 Bir WCF hizmet kitaplığı, diğer herhangi bir WCF hizmeti gibi dağıtılabilir. Ancak, .NET Framework dll yapılandırmalarını desteklemediğini unutmayın. <xref:System.Configuration> her uygulama etki alanı için bir yapılandırma dosyasını destekler. WCF hizmet kitaplığı projesi, geliştirme sırasında kitaplık için bir App.config dosyası sağlayarak bu sınırlamayı konuma almayı azaltır. Ancak, App.config dosyası dağıtımdan sonra tanınmaz.  
  
 Yapılandırma kodunuzu Barındırma ortamınız tarafından tanınan yapılandırma dosyasına taşımanız gerekir. Kendi kendine barındırma için, App.config dosyanın içeriğini barındıran yürütülebilir dosyanın App.config dosyasına kopyalamanız gerekir. Hizmetinizi barındırmak için IIS kullanıyorsanız, App.config dosyanın içeriğini sanal dizinin Web.config dosyasına kopyalamanız gerekir.
