---
title: Yan Yana Yürütme için Bileşen Oluşturma Yönergeleri
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, multiple application versions
- side-by-side execution, multiple component versions
ms.assetid: 5c540161-6e40-42e9-be92-6175aee2c46a
ms.openlocfilehash: 42d0e2d85517d4a8fb443db9b63e6b893267caca
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121582"
---
# <a name="guidelines-for-creating-components-for-side-by-side-execution"></a>Yan Yana Yürütme için Bileşen Oluşturma Yönergeleri
Yan yana yürütme için tasarlanan yönetilen uygulamaları veya bileşenleri oluşturmak için aşağıdaki genel yönergeleri izleyin:  
  
- Tür kimliğini bir dosyanın belirli bir sürümüne bağlayın.  
  
     Ortak dil çalışma zamanı, tanımlayıcı adlı derlemeler kullanarak tür kimliğini belirli bir dosya sürümüne bağlar. Yan yana yürütmeye yönelik bir uygulama veya bileşen oluşturmak için, tüm derlemelere tanımlayıcı bir ad vermeniz gerekir. Bu kesin tür kimliği oluşturur ve herhangi bir tür çözümlemenin doğru dosyaya yönlendirilmesini sağlar. Tanımlayıcı adlı bir derleme, çalışma zamanının bir bağlama isteğini yerine getiren doğru dosyayı bulmak için kullandığı sürüm, kültür ve Yayımcı bilgilerini içerir.  
  
- Sürüm duyarlı depolama kullanın.  
  
     Çalışma zamanı, sürüm algılayan depolama sağlamak için genel derleme önbelleğini kullanır. Genel bütünleştirilmiş kod önbelleği, .NET Framework kullanan her bilgisayarda yüklü sürümü algılayan bir dizin yapısıdır. Bu derlemenin yeni bir sürümü yüklendiğinde, genel derleme önbelleğinde yüklü olan derlemelerin üzerine yazılmaz.  
  
- Yalıtılmış olarak çalışan bir uygulama veya bileşen oluşturun.  
  
     Yalıtım aşamasında çalışan bir uygulama veya bileşen, uygulamanın veya bileşenin iki örneği aynı anda çalıştığında çakışmaları önlemek için kaynakları yönetmelidir. Uygulama veya bileşen ayrıca sürüme özgü bir dosya yapısı kullanmalıdır.  
  
## <a name="application-and-component-isolation"></a>Uygulama ve bileşen yalıtımı  
 Yan yana yürütme için bir uygulamanın veya bileşenin başarıyla tasarlanmasına yönelik bir anahtar, yalıtımdır. Uygulamanın veya bileşenin tüm kaynakları, özellikle de dosya g/ç 'yi yalıtılmış bir şekilde yönetmesi gerekir. Uygulamanızın veya bileşenin yalıtımta çalıştığından emin olmak için bu yönergeleri izleyin:  
  
- Kayıt defterine sürüme özgü bir şekilde yazın. Değerleri, sürümü gösteren yığınlar veya anahtarlar halinde depolayın ve bir bileşenin sürümleri arasında bilgi veya durum paylaşmayın. Bu, aynı anda çalışan iki uygulamanın veya bileşenin, bilgilerin üzerine yazılmasına engel olur.  
  
- Bir yarış durumu gerçekleşmemesi için adlandırılmış çekirdek nesneleri sürümüne özel yapın. Örneğin, bir yarış durumu aynı uygulamanın iki sürümünden iki semafor aynı olduğunda meydana gelir.  
  
- Dosya ve dizin adlarını sürümü algılayan hale getirin. Bu, dosya yapılarının sürüm bilgilerine dayanması gerektiği anlamına gelir.  
  
- Kullanıcı hesaplarını ve grupları sürüme özgü bir şekilde oluşturun. Bir uygulama tarafından oluşturulan kullanıcı hesapları ve gruplar, sürümle tanımlanmalıdır. Kullanıcı hesaplarını ve grupları bir uygulamanın sürümleri arasında paylaşmayın.  
  
## <a name="installing-and-uninstalling-versions"></a>Sürümleri yükleme ve kaldırma  
 Yan yana yürütme için bir uygulama tasarlarken, sürümleri yükleme ve kaldırma ile ilgili aşağıdaki yönergeleri izleyin:  
  
- .NET Framework farklı bir sürümünde çalışan diğer uygulamalar tarafından gerekebilecek bilgileri kayıt defterinden silmeyin.  
  
- Kayıt defterindeki, .NET Framework farklı bir sürümünde çalışan diğer uygulamalar tarafından gerekebilecek bilgileri değiştirme.  
  
- .NET Framework farklı bir sürümünde çalışan diğer uygulamalar tarafından gerekebilecek COM bileşenlerinin kaydını kaldırmayın.  
  
- Zaten kayıtlı olan bir COM sunucusu için **ınprocserver32** veya diğer kayıt defteri girdilerini değiştirmeyin.  
  
- .NET Framework farklı bir sürümünde çalışan diğer uygulamalar tarafından gerekebilecek Kullanıcı hesaplarını veya grupları silmeyin.  
  
- Sürüm bilgisi olmayan bir yol içeren kayıt defterine hiçbir şey eklemeyin.  
  
## <a name="file-version-number-and-assembly-version-number"></a>Dosya sürüm numarası ve derleme sürüm numarası  
 Dosya sürümü, çalışma zamanı tarafından kullanılmayan bir Win32 sürümü kaynağıdır. Genel olarak, dosya sürümünü yerinde güncelleştirme için de güncelleştirebilirsiniz. İki özdeş dosya farklı dosya sürümü bilgilerine sahip olabilir ve iki farklı dosya aynı dosya sürümü bilgisine sahip olabilir.  
  
 Derleme sürümü derleme bağlaması için çalışma zamanı tarafından kullanılır. Farklı sürüm numaralarına sahip iki özdeş derleme çalışma zamanı tarafından iki farklı derleme olarak değerlendirilir.  
  
 [Genel derleme önbelleği aracı (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) yalnızca dosya sürüm numarası yeniyse bir derlemeyi değiştirmenize izin verir. Derleme sürüm numarası daha büyük değilse, yükleyici genellikle derleme üzerine yüklemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yan Yana Yürütme](side-by-side-execution.md)
- [Nasıl yapılır: Otomatik Bağlama Yönlendirmesini Etkinleştirme veya Devre Dışı Bırakma](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
