---
title: Genel Derleme Önbelleği ile Hizmet Verilen Bileşenleri Kullanma
description: .NET 'teki genel derleme önbelleği ile hizmet verilen bileşenleri (yönetilen kod COM+ bileşenleri) kullanın. CLR ve COM+ hizmetlerinin GAC olmayan bileşenleri işleyebileceğini görün.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
ms.openlocfilehash: 314f804dfcaee64ef364cc881ae76651961294d7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254590"
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a>Genel Derleme Önbelleği ile Hizmet Verilen Bileşenleri Kullanma

Hizmet verilen bileşenler (yönetilen kod COM+ bileşenleri), genel derleme önbelleğine yerleştirilmelidir. Bazı senaryolarda, ortak dil çalışma zamanı ve COM+ Hizmetleri, genel derleme önbelleğinde olmayan hizmet verilen bileşenleri işleyebilir; diğer senaryolarda, bunları kullanamaz. Aşağıdaki senaryolarda şunlar gösterilmektedir:  
  
- Bir COM+ sunucu uygulamasındaki hizmet verilen bileşenler için, bileşenleri içeren derlemenin genel derleme önbelleğinde olması gerekir, çünkü Dllhost.exe, hizmet verilen bileşenleri içeren dizin ile aynı dizinde çalışmaz.  
  
- Bir COM+ kitaplığı uygulamasındaki hizmet verilen bileşenler için, çalışma zamanı ve COM+ Hizmetleri, geçerli dizinde arama yaparak bileşenleri içeren derleme başvurusunu çözümleyebilir. Bu durumda, derlemenin genel derleme önbelleğinde olması gerekmez.  
  
- Bir ASP.NET uygulamasındaki hizmet verilen bileşenler için, durum farklıdır. Hizmet verilen bileşenleri içeren derlemeyi uygulama tabanının bin dizinine yerleştirirseniz ve isteğe bağlı kaydı kullanıyorsanız, ASP.NET, çalışma zamanının gölge özelliklerini kullandığından, derleme indirme önbelleğine gölge olarak kopyalanacaktır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Derlemeler ve Genel Derleme Önbelleği ile Çalışma](working-with-assemblies-and-the-gac.md)
- [Gacutil.exe (Genel Bütünleştirilmiş Kod Önbelleği Aracı)](../tools/gacutil-exe-gac-tool.md)
