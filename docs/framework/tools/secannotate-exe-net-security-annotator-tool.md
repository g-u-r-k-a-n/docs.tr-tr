---
title: SecAnnotate.exe (.NET Güvenlik Not Ekleyici Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- SecAnnotate.exe
- Security Annotator tool
ms.assetid: 8104d208-7813-4a1d-8a75-58f9a7bcb8c9
ms.openlocfilehash: 7c9fad9b420044cce2c9d75cca66ecdb5b0558cd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104677"
---
# <a name="secannotateexe-net-security-annotator-tool"></a>SecAnnotate.exe (.NET Güvenlik Not Ekleyici Aracı)
.NET Security açıklaması Ekleyici Tool (SecAnnotate. exe), bir veya daha fazla derlemenin `SecurityCritical` ve `SecuritySafeCritical` bölümlerini tanımlayan bir komut satırı uygulamasıdır.  
  
 Bir Visual Studio uzantısı olan [Security açıklaması Ekleyici](https://go.microsoft.com/fwlink/?LinkId=198007), SecAnnotate. exe için grafiksel bir kullanıcı arabirimi sağlar ve aracı Visual Studio 'dan çalıştırmanızı sağlar.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).  
  
 Komut isteminde, aşağıdaki bölümde açıklanan *parametreleri* ve *derlemeler* boşluklarla ayrılmış bir veya daha fazla derleme adından oluşur:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
SecAnnotate.exe [parameters] [assemblies]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`/a`<br /><br /> veya<br /><br /> `/showstatistics`|Analiz edilmekte olan derlemelerde saydamlık kullanımıyla ilgili istatistikleri gösterir.|  
|`/d:` *dizini*<br /><br /> veya<br /><br /> `/referencedir:` *dizini*|Ek açıklama sırasında bağımlı derlemelerin aranacağı bir dizin belirtir.|  
|`/i`<br /><br /> veya<br /><br /> `/includesignatures`|Ek açıklama raporu dosyasına genişletilmiş imza bilgileri ekler.|  
|`/n`<br /><br /> veya<br /><br /> `/nogac`|Genel derleme belleğinde başvurulan derlemelerin aranmasını bastırır.|  
|*output. xml* `/o:`<br /><br /> veya<br /><br /> *output. xml* `/out:`|Çıktı ek açıklama dosyasını belirtir.|  
|`/p:` *maxpass*<br /><br /> veya<br /><br /> `/maximumpasses:` *maxpass*|Yeni ek açıklamaların üretilmesini durdurmadan önce derlemelere yapılacak en fazla ek açıklama sayısını belirtir.|  
|`/q`<br /><br /> veya<br /><br /> `/quiet`|Açıklama ekleyicinin durum iletileri vermediği sessiz modu belirtir; yalnızca hata bilgilerini verir.|  
|`/r:` *derlemesi*<br /><br /> veya<br /><br /> `/referenceassembly:` *derlemesi*|Açıklama ekleme sırasında bağımlı derlemeleri çözerken, belirtilen derlemeyi ekler. Başvuru derlemelerine, başvuru yolunda bulunan derlemelere göre öncelik verilir.|  
|`/s:` *RuleName*<br /><br /> veya<br /><br /> `/suppressrule:` *RuleName*|Belirtilen saydamlık kuralını giriş derlemeleri üzerinde çalıştırmayı bastırır.|  
|`/t`<br /><br /> veya<br /><br /> `/forcetransparent`|Açıklama Ekleyici aracını, herhangi bir saydamlık ek açıklaması olmayan tüm derlemelere tümüyle saydamlarmış gibi davranmaya zorlar.|  
|`/t`:*derleme*<br /><br /> veya<br /><br /> `/forcetransparent`:*derleme*|Derleme düzeyindeki geçerli ek açıklamalarına bakılmaksızın, verilen derlemeyi saydam olmaya zorlar.|  
|||  
|`/v`<br /><br /> veya<br /><br /> `/verify`|Yalnızca bir derlemenin ek açıklamalarının doğru olduğunu doğrular; derleme doğrulamazsa, gerekli tüm ek açıklamaları bulmak için birden çok geçiş yapmayı denemez.|  
|`/x`<br /><br /> veya<br /><br /> `/verbose`|Ek açıklama eklerken ayrıntılı çıktı belirtir.|  
|`/y:` *dizini*<br /><br /> veya<br /><br /> `/symbolpath:` *dizini*|Açıklama ekleme sırasında simge dosyalarını ararken, belirtilen dizini ekler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Komut satırında belirtilen ve önüne bir at işareti (@) eklenen bir yanıt dosyasında parametreler ve derlemeler de sağlanabilir. Yanıt dosyasındaki her bir satır tek bir parametre veya derleme adı içermelidir.  
  
 .NET Security açıklaması Ekleyici hakkında daha fazla bilgi için bkz. [SecAnnotate kullanarak, derlemelerinizi .NET güvenlik blogundan saydamlık ihlalleri Için analiz etme](https://go.microsoft.com/fwlink/?LinkId=187648) .  
  
## <a name="examples"></a>Örnekler
