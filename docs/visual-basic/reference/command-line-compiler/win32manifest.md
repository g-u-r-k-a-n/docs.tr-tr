---
description: Hakkında daha fazla bilgi edinin:-win32manifest (Visual Basic)
title: -win32manifest
ms.date: 03/13/2018
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
ms.openlocfilehash: d8b674d3eb101fdaa05cca7fa67ba0a43999ca37
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433516"
---
# <a name="-win32manifest-visual-basic"></a>-win32manifest (Visual Basic)

Bir projenin taşınabilir yürütülebilir (PE) dosyasına gömülecek Kullanıcı tanımlı bir Win32 uygulama bildirim dosyası tanımlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
  
|Terim|Tanım|  
|---|---|  
|`fileName`|Özel bildirim dosyasının yolu.|  
  
## <a name="remarks"></a>Açıklamalar  

 Varsayılan olarak Visual Basic derleyici, istenen bir yürütme düzeyi olan asInvoker belirten bir uygulama bildirimi katıştırır. Bu, bildirim, yürütülebilir dosyanın oluşturulduğu klasörde, genellikle Visual Studio kullandığınızda bin\Debug veya bin\Release klasöründe oluşturulur. Özel bir bildirim sağlamak istiyorsanız, örneğin, bir highestAvailable veya requireAdministrator istenen yürütme düzeyini belirtmek için bu seçeneği, dosyanın adını belirtmek için kullanın.  
  
> [!NOTE]
> Bu seçenek ve [-Win32Resource](win32resource.md) seçeneği birbirini dışlıyor. Her iki seçeneği de aynı komut satırında kullanmayı denerseniz, bir derleme hatası alırsınız.  
  
 İstenen bir yürütme düzeyini belirten uygulama bildirimi olmayan bir uygulama, Windows Vista 'daki Kullanıcı hesabı denetimi özelliği altında dosya/kayıt defteri sanallaştırmaya tabidir. Sanallaştırma hakkında daha fazla bilgi için bkz. [Windows Vista 'Da ClickOnce dağıtımı](/visualstudio/deployment/clickonce-deployment-on-windows-vista).  
  
 Aşağıdaki koşullardan biri doğru ise uygulamanız sanallaştırmaya tabi olacaktır:  
  
1. Seçeneğini kullanarak, seçeneğini `-nowin32manifest` kullanarak sonraki bir derleme adımında veya bir Windows kaynak (. res) dosyasının parçası olarak bir bildirim sağlamaz `-win32resource` .  
  
2. İstenen yürütme düzeyini belirtmeyen özel bir bildirim sağlarsınız.  
  
 Visual Studio varsayılan bir. manifest dosyası oluşturur ve yürütülebilir dosyanın yanı sıra hata ayıklama ve sürüm dizinlerinde depolar. Varsayılan App. manifest dosyasını, proje Tasarımcısı 'ndaki **uygulama** sekmesinde **UAC ayarlarını görüntüle** ' ye tıklayarak görüntüleyebilir veya düzenleyebilirsiniz. Daha fazla bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
 Uygulama bildirimini özel derleme sonrası bir adım olarak veya seçeneğini kullanarak bir Win32 kaynak dosyasının parçası olarak sağlayabilirsiniz `-nowin32manifest` . Uygulamanızın Windows Vista 'da dosya veya kayıt defteri sanallaştırmaya tabi olmasını istiyorsanız bu seçeneği kullanın. Bu, derleyicinin PE dosyasında varsayılan bir bildirim oluşturmasını ve katıştırmasını engeller.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, Visual Basic derleyicisinin bir PE 'ye eklediği varsayılan bildirimi gösterir.  
  
> [!NOTE]
> Derleyici, bildirim XML dosyasına bir standart uygulama adı MyApplication. uygulaması ekler. Bu, uygulamaların Windows Server 2003 Service Pack 3 üzerinde çalışmasını sağlamak için geçici bir çözümdür.  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>  
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">  
    <security>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <requestedExecutionLevel level="asInvoker"/>  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
</assembly>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Command-Line derleyicisi](index.md)
- [-nowin32manifest (Visual Basic)](nowin32manifest.md)
