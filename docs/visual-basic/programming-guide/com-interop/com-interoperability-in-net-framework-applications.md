---
title: .NET Framework Uygulamalarında COM Birlikte Çalışabilirliği
ms.date: 07/20/2015
helpviewer_keywords:
- interoperability, COM and .NET Framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
ms.openlocfilehash: c3567464616d3b0b3f91ff57e8a169aca046c866
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452298"
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a>.NET Framework Uygulamalarında COM Birlikte Çalışabilirliği (Visual Basic)

Aynı uygulamadaki COM nesnelerini ve .NET Framework nesneleri kullanmak istediğinizde, nesnelerin bellekte nasıl mevcut olduğu farklılıkları ele almanız gerekir. .NET Framework nesne yönetilen bellekte bulunur — ortak dil çalışma zamanı tarafından denetlenen bellek — ve gerektiğinde çalışma zamanı tarafından taşınabilir. Bir COM nesnesi, yönetilmeyen bellekte bulunur ve başka bir bellek konumuna taşınması beklenmez. Visual Studio ve .NET Framework, bu yönetilen ve yönetilmeyen bileşenlerin etkileşimini denetlemek için araçlar sağlar. Yönetilen kod hakkında daha fazla bilgi için bkz. [ortak dil çalışma zamanı](../../../standard/clr.md).

.NET uygulamalarında COM nesneleri kullanmanın yanı sıra, COM aracılığıyla yönetilmeyen koddan erişilebilen nesneleri geliştirmek için Visual Basic kullanmak da isteyebilirsiniz.

Bu sayfadaki bağlantılar, COM ve .NET Framework nesneleri arasındaki etkileşimler hakkında ayrıntılı bilgi sağlar.

## <a name="related-sections"></a>İlgili bölümler

| | |
|---------|---------|
| [COM Birlikte Çalışma](../../../visual-basic/programming-guide/com-interop/index.md) | Com nesneleri, ActiveX denetimleri, Win32 DLL 'Leri, yönetilen nesneler ve COM nesnelerinin devralınması gibi Visual Basic COM birlikte çalışabilirliğini kapsayan konuların bağlantılarını sağlar. |
| [Yönetilmeyen Kod ile Birlikte Çalışma](../../../framework/interop/index.md) | Yönetilen ve yönetilmeyen kod arasındaki etkileşim sorunlarından bazılarını kısaca açıklar ve daha fazla çalışma için bağlantılar sağlar. |
| [COM Sarmalayıcıları](../../../standard/native-interop/com-wrappers.md) | Yönetilen kodun COM yöntemlerine çağrı yapmasına izin veren ve com 'un .NET nesne yöntemlerini çağırabileceği com çağrılabilir sarmalayıcıları sağlayan, çalışma zamanında çağrılabilir sarmalayıcıları açıklar. |
| [Gelişmiş COM birlikte çalışabilirlik](../../../framework/interop/index.md) | Sarmalayıcılar, özel durumlar, devralma, iş parçacığı, olaylar, dönüştürmeler ve sıralama açısından COM birlikte çalışabilirliğini kapsayan konuların bağlantılarını sağlar. |
| [Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)](../../../framework/tools/tlbimp-exe-type-library-importer.md) | Bir COM tür kitaplığı içinde bulunan tür tanımlarını ortak dil çalışma zamanı derlemesinde eşdeğer tanımlara dönüştürmek için kullanabileceğiniz aracı açıklar. |
