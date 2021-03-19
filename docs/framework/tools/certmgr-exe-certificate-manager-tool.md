---
title: Certmgr.exe (Sertifika Yönetim Aracı)
description: Sertifika Yöneticisi aracını Certmgr.exe keşfedelim. Bu araç sertifikaları, sertifika güven listelerini (CTL) ve sertifika iptal listelerini (CRL 'Ler) yönetir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates, managing
- CRLs
- certificate trust lists
- Certmgr.exe
- Certificate Manager tool
- CTLs
- certificate revocation lists
ms.assetid: 7e953b43-1374-4bbc-814f-53ca1b6b52bb
ms.openlocfilehash: eba8253a52f9dc533848fc7cbb76566c726495a2
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104654199"
---
# <a name="certmgrexe-certificate-manager-tool"></a>Certmgr.exe (Sertifika Yönetim Aracı)

Sertifika Yöneticisi aracı (Certmgr.exe) sertifikaları, sertifika güven listelerini (CTL) ve sertifika iptal listelerini (CRL) yönetir.  
  
 Sertifika Yöneticisi Visual Studio ile birlikte otomatik olarak yüklenir. Aracı başlatmak için [Visual studio Geliştirici komut istemi veya Visual Studio Geliştirici PowerShell](/visualstudio/ide/reference/command-prompt-powershell)kullanın.  
  
> [!NOTE]
> Sertifika Yöneticisi aracı (Certmgr.exe) bir komut satırı aracıyken, Sertifikalar (Certmgr.msc) bir Microsoft Yönetim Konsolu (MMC) ek bileşenidir. Certmgr. msc genellikle Windows sistem dizininde bulunduğu için, komut satırına girildiğinde, `certmgr` Visual Studio için geliştirici komut istemi açmış olsanız bile SERTIFIKALAR MMC ek bileşenini yükleyebilirsiniz. Bu, PATH ortam değişkeninde ek bileşene olan yol Sertifika Yöneticisi aracına olan yoldan önce geldiği için gerçekleşir. Eğer bu sorunla karşılaşırsanız, çalıştırılabilir öğenin yolunu belirterek Certmgr.exe komutlarını yürütebilirsiniz.
  
 X. 509.440 sertifikalarına genel bakış için bkz. [sertifikalarla çalışma](../wcf/feature-details/working-with-certificates.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Bağımsız Değişken|Description|  
|--------------|-----------------|  
|*sourceStorename*|Eklenecek, silinecek, kaydedilecek veya görüntülenecek varolan sertifikaları, CTL'leri veya CRL'leri içeren sertifika deposu. Bu bir depo dosyası veya sistem deposu olabilir.|  
|*destinationStorename*|Çıktı sertifika deposu veya dosyası.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/Add**|Bir sertifika deposuna sertifikalar, CTL'ler ve CRL'ler ekler.|  
|**/All**|**/Add** ile kullanıldığında tüm girdileri ekler. **/Del&lt** ile kullanıldığında tüm girdileri siler. **/Add** veya **/del&lt** seçenekleri olmadan kullanıldığında tüm girişleri görüntüler. **/All** seçeneği **/PUT** ile kullanılamaz.|  
|**/c**|**/Add** ile kullanıldığında sertifikaları ekler. **/Del&lt** ile kullanıldığında sertifikaları siler. , **/PUT** ile kullanıldığında sertifikaları kaydeder. **/Add**, **/del&lt** veya **/PUT** seçeneği olmadan kullanıldığında sertifikaları görüntüler.|  
|**/CRL**|**/Add** Ile kullanıldığında CRL 'leri ekler. **/Del&lt** Ile kullanıldığında CRL 'leri siler. , **/PUT** Ile kullanıldığında CRL 'leri kaydeder. **/Add**, **/del&lt** veya **/PUT** seçeneği olmadan kullanıldığında CRL 'leri görüntüler.|  
|**/CTL**|**/Add** Ile kullanıldığında CTL ekler. **/Del&lt** Ile kullanıldığında CTL 'leri siler. **/PUT** Ile kullanıldığında CTL 'leri kaydeder. **/Add**, **/del&lt** veya **/PUT** seçeneği olmadan kullanıldığında CTL 'leri görüntüler.|  
|**/del&lt**|Bir sertifika deposundan sertifikaları, CTL'leri ve CRL'leri siler.|  
|**/E** *EncodingType*|Sertifika kodlama türünü belirtir. Varsayılan değer: `X509_ASN_ENCODING`.|  
|**/F** *dwFlags*|Depo açık bayrağını belirtir. Bu, **CertOpenStore**'A geçirilen *dwFlags* parametresidir. Varsayılan değer CERT_SYSTEM_STORE_CURRENT_USER değeridir. Bu seçenek yalnızca **/y** seçeneği kullanılırsa değerlendirilir.|  
|**/h**[**ELP**]|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/n** *Nam*|Eklenecek, silinecek veya kaydedilecek sertifika için ortak adı belirtir. Bu seçenek yalnızca sertifikalarla kullanılabilir; CTL'ler veya CRL'ler ile kullanılamaz.|  
|**/Put**|Bir sertifika deposundan bir X.509 sertifikasını, CTL'yi veya CRL'yi dosyaya kaydeder. Dosya X.509 biçiminde kaydedilir. Dosyayı PKCS #7 biçiminde kaydetmek için **/PUT** seçeneğiyle birlikte **/7** seçeneğini kullanabilirsiniz. **/PUT** seçeneğinin arkasından **/c**, **/CTL** veya **/CRL** gelmelidir. **/All** seçeneği **/PUT** ile kullanılamaz.|  
|**/r** *konumu*|Sistem deposu için kayıt defteri konumunu tanımlar. Bu seçenek yalnızca **/s** seçeneğini belirtirseniz değerlendirilir. *konum* aşağıdakilerden biri olmalıdır:<br /><br /> -   `currentUser` sertifika deposunun HKEY_CURRENT_USER anahtarı altında olduğunu gösterir. Bu varsayılan seçenektir.<br />-   `localMachine` sertifika deposunun HKEY_LOCAL_MACHINE anahtarı altında olduğunu gösterir.|  
|**sn**|Sertifika deposunun bir sistem deposu olduğunu gösterir. Bu seçeneği belirtmezseniz, mağaza bir **StoreFile** olarak kabul edilir.|  
|**/SHA1** *sha1Hash*|Eklenecek, silinecek veya kaydedilecek sertifikanın, CTL'nin veya CRL'nin SHA1 karmasını belirtir.|  
|**çıktıda**|Ayrıntılı modu belirtir; sertifikalar, CTL'ler ve CRL'ler hakkında ayrıntılı bilgi görüntüler. Bu seçenek **/Add**, **/del&lt** veya **/PUT** seçenekleriyle birlikte kullanılamaz.|  
|**/y** *sağlayıcısı*|Depo sağlayıcısı adını sağlar.|  
|**/7**|Hedef depoyu bir PKCS #7 nesnesi olarak kaydeder.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  

 Certmgr.exe aşağıdaki temel işlevleri gerçekleştirir:  
  
- Sertifikaları, CTL'leri ve CRL'leri konsolda görüntüler.  
  
- Bir sertifika deposuna sertifikalar, CTL'ler ve CRL'ler ekler.  
  
- Bir sertifika deposundan sertifikaları, CTL'leri ve CRL'leri siler.  
  
- Bir sertifika deposundan bir X.509 sertifikasını, CTL'yi veya CRL'yi dosyaya kaydeder.  
  
 Certmgr.exe, iki tür sertifika deposu ile birlikte kullanılabilir: **StoreFile** ve System Store. Sertifika deposu türünü belirtmek gerekli değildir: Certmgr.exe depo türünü tanımlayarak uygun işlemleri gerçekleştirebilir.  
  
 Certmgr.exe'yi hiçbir seçenek olmadan belirtmek, komut satırından kullanılabilen sertifika yönetim görevlerine yardımcı olan bir GUI'ye sahip certmgr.msc ek bileşenini yönetir. GUI; sertifikaları, CTL'leri ve CRL'leri diskinizden bir sertifika deposuna kopyalayan bir içeri aktarma sihirbazı sağlar.  
  
 `sourceStorename`Aşağıdaki kodu derleyerek ve çalıştırarak, ve parametreleri Için X509Certificate mağazaların adlarını bulabilirsiniz `destinationStorename` .  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 Sertifikalar hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](../wcf/feature-details/working-with-certificates.md).  
  
## <a name="examples"></a>Örnekler  

 Aşağıdaki komut, ayrıntılı çıktıyla çağrılan bir varsayılan sistem deposunu görüntüler `my` .  
  
```console  
certmgr /v /s my  
```  
  
 Aşağıdaki komut adlı bir dosyadaki tüm sertifikaları `myFile.ext` adlı yeni bir dosyaya ekler `newFile.ext` .  
  
```console  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 Aşağıdaki komut, sertifikayı sistem deposuna adlı bir dosyaya ekler `testcert.cer` `my` .  
  
```console  
certmgr /add /c testcert.cer /s my  
```  
  
 Aşağıdaki komut, sertifikayı Kök sertifika deposuna adlı bir dosyaya ekler `TrustedCert.cer` .  
  
```console  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 Aşağıdaki komut, sistem deposunda ortak ada sahip bir sertifikayı `myCert` `my` adlı bir dosyaya kaydeder `newCert.cer` .  
  
```console  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 Aşağıdaki komut, sistem deposundaki tüm CTL 'leri siler `my` ve elde edilen depoyu adlı bir dosyaya kaydeder `newStore.str` .  
  
```console  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 Aşağıdaki komut, bir sertifikayı `my` dosyadaki sistem deposuna kaydeder `newFile` . İçine koymak için sertifika numarasını girmeniz istenir `my` `newFile` .  
  
```console  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Makecert.exe (sertifika oluşturma aracı)](/windows/desktop/SecCrypto/makecert)
- [Geliştirici komut satırı kabukları](/visualstudio/ide/reference/command-prompt-powershell)
