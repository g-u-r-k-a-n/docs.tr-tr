---
title: Desteklenmeyen Senaryolar
ms.date: 03/30/2017
ms.assetid: 72027d0f-146d-40c5-9d72-e94392c8bb40
ms.openlocfilehash: 2d779b49a8201b3ad53507af7710f7aef5e9321c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289652"
---
# <a name="unsupported-scenarios"></a>Desteklenmeyen senaryolar

Çeşitli nedenlerle Windows Communication Foundation (WCF) bazı belirli güvenlik senaryolarını desteklemez. Örneğin, Windows XP Home Edition SSPI veya Kerberos kimlik doğrulama protokollerini uygulamaz ve bu nedenle WCF, bu platformda Windows kimlik doğrulamasına sahip bir hizmetin çalıştırılmasını desteklemez. Windows XP Home Edition altında WCF çalıştırılırken Kullanıcı adı/parola ve HTTP/HTTPS tümleşik kimlik doğrulaması gibi diğer kimlik doğrulama mekanizmaları desteklenir.

## <a name="impersonation-scenarios"></a>Kimliğe bürünme senaryoları

### <a name="impersonated-identity-might-not-flow-when-clients-make-asynchronous-calls"></a>İstemciler zaman uyumsuz çağrılar yaparken kimliğe bürünme kimliği akamayabilir

 Bir WCF istemcisi, kimliğe bürünme altında Windows kimlik doğrulaması kullanarak bir WCF hizmetine zaman uyumsuz çağrılar yaptığında kimlik doğrulaması, kimliğe bürünülmüş kimlik yerine istemci işleminin kimliğiyle meydana gelebilir.

### <a name="windows-xp-and-secure-context-token-cookie-enabled"></a>Windows XP ve güvenli bağlam belirteci tanımlama bilgisi etkin

WCF, kimliğe bürünme özelliğini desteklemez ve <xref:System.InvalidOperationException> aşağıdaki koşullar mevcut olduğunda oluşturulur:

- İşletim sistemi Windows XP 'dir.

- Kimlik doğrulama modu bir Windows kimliği ile sonuçlanır.

- <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>Öğesinin özelliği <xref:System.ServiceModel.OperationBehaviorAttribute> olarak ayarlanır <xref:System.ServiceModel.ImpersonationOption.Required> .

- Durum tabanlı bir güvenlik bağlamı belirteci (SCT) oluşturulur (varsayılan olarak, oluşturma devre dışıdır).

 Durum tabanlı SCT yalnızca özel bir bağlama kullanılarak oluşturulabilir. Daha fazla bilgi için bkz. [nasıl yapılır: güvenli bir oturum Için güvenlik bağlamı belirteci oluşturma](how-to-create-a-security-context-token-for-a-secure-session.md).) Kodda, belirteç, veya yöntemini kullanarak bir güvenlik bağlama öğesi (ya da <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ) oluşturarak <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%28System.Boolean%29?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%28System.ServiceModel.Channels.SecurityBindingElement%2CSystem.Boolean%29?displayProperty=nameWithType> ve `requireCancellation` parametresi olarak ayarlanarak etkinleştirilir `false` . Parametresi, SCT 'nin önbelleğe alınmasını ifade eder. Değeri, `false` durum tabanlı SCT özelliğini sağlar.

 Alternatif olarak, yapılandırmada, belirteç bir <`customBinding`> oluşturarak ve sonra bir <`security`> öğesi eklenerek ve `authenticationMode` özniteliği SecureConversation ve özniteliği olarak ayarlanarak etkinleştirilir `requireSecurityContextCancellation` `true` .

> [!NOTE]
> Önceki gereksinimler özeldir. Örneğin, <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> bir Windows kimliği ile sonuçlanan, ancak BIR SCT oluşturmayan bir bağlama öğesi oluşturur. Bu nedenle, `Required` WINDOWS XP 'yi seçeneğiyle kullanabilirsiniz.

### <a name="possible-aspnet-conflict"></a>Olası ASP.NET çakışması

WCF ve ASP.NET, kimliğe bürünme özelliğini etkinleştirebilir veya devre dışı bırakabilir. ASP.NET bir WCF uygulaması barındırıyorsa, WCF ve ASP.NET yapılandırma ayarları arasında bir çakışma var olabilir. Çakışma durumunda, <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> <xref:System.ServiceModel.ImpersonationOption.NotAllowed> bu, ASP.NET Kimliğe bürünme ayarı öncelikli olarak AYARLANMADıĞı takdirde WCF ayarı önceliklidir.

### <a name="assembly-loads-may-fail-under-impersonation"></a>Derleme yüklemeleri, kimliğe bürünme altında başarısız olabilir

Kimliğe bürünülmüş bağlamın bir derlemeyi yüklemek için erişim hakları yoksa ve ilk kez ortak dil çalışma zamanı (CLR) bu AppDomain için derlemeyi yüklemeye çalışıyorsa, <xref:System.AppDomain> hatayı önbelleğe alır. Daha sonra bu derlemeyi (veya derlemeleri) yükleme girişimleri, kimliğe bürünme geri alındıktan sonra bile başarısız olur ve geri döndürülmüş bağlam derlemeyi yüklemek için erişim haklarına sahip olsa bile. Bunun nedeni, CLR 'nin Kullanıcı bağlamı değiştirildikten sonra yükü yeniden oluşturmaz. Hatadan kurtarmak için uygulama etki alanını yeniden başlatmanız gerekir.

> [!NOTE]
> Sınıfının özelliği için varsayılan değer <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> <xref:System.ServiceModel.Security.WindowsClientCredential> <xref:System.Security.Principal.TokenImpersonationLevel.Identification> . Çoğu durumda, kimlik düzeyi kimliğe bürünme bağlamının herhangi bir ek derlemeyi yükleme izni yoktur. Bu varsayılan değerdir, bu nedenle farkında olmak üzere çok yaygın bir durumdur. Kimliğe bürünme işlemi ayrıcalığına sahip olmadığında, kimlik düzeyi kimliğe bürünme da oluşur `SeImpersonate` . Daha fazla bilgi için bkz. [temsil ve kimliğe bürünme](delegation-and-impersonation-with-wcf.md).

### <a name="delegation-requires-credential-negotiation"></a>Temsili kimlik bilgisi anlaşması gerektirir

Kerberos kimlik doğrulama protokolünü temsilcisiyle birlikte kullanmak için, Kerberos protokolünü kimlik bilgisi anlaşmasına (bazen çok aşamalı veya çok adımlı Kerberos olarak adlandırılır) uygulamanız gerekir. Kimlik bilgisi anlaşması olmadan Kerberos kimlik doğrulaması uygularsanız (bazen tek veya tek seferlik Kerberos olarak adlandırılır), bir özel durum oluşturulur. Kimlik bilgisi anlaşmasını uygulama hakkında daha fazla bilgi için bkz. [Windows kimlik doğrulama hatalarını ayıklama](debugging-windows-authentication-errors.md).

## <a name="cryptography"></a>Şifreleme

### <a name="sha-256-supported-only-for-symmetric-key-usages"></a>SHA-256 yalnızca simetrik anahtar kullanımları için desteklenir

WCF, sistem tarafından belirtilen bağlamalarda algoritma paketini kullanarak belirtebileceğiniz çeşitli şifreleme ve imza özeti oluşturma algoritmalarını destekler. WCF, daha iyi güvenlik için imza Özet karmaları oluşturmak amacıyla güvenli karma algoritması (SHA) 2 algoritmalarını, özellikle SHA-256 ' i destekler. Bu sürüm, yalnızca Kerberos anahtarları gibi simetrik anahtar kullanımları için SHA-256 ' ı destekler ve iletiyi imzalamak için bir X. 509.440 sertifikası kullanılmaz. WCF, WinFX 'de RSA-SHA256 için desteklenmeyen destek olmaması nedeniyle, SHA-256 karması kullanılarak RSA imzalarını (X. 509.440 sertifikalarında kullanılır) desteklemez.

### <a name="fips-compliant-sha-256-hashes-not-supported"></a>FIPS uyumlu SHA-256 karmaları desteklenmez

WCF, SHA-256 FIPS uyumlu karmaları desteklemez, bu nedenle SHA-256 kullanan algoritma paketleri, FIPS uyumlu algoritmaların kullanılması gereken sistemlerde WCF tarafından desteklenmez.

### <a name="fips-compliant-algorithms-may-fail-if-registry-is-edited"></a>Kayıt defteri düzenlendiğinde FIPS uyumlu algoritmalar başarısız olabilir

Yerel güvenlik ayarları Microsoft Yönetim Konsolu (MMC) ek bileşenini kullanarak Federal bilgi Işleme standartları (FIPS) ile uyumlu algoritmaları etkinleştirebilir ve devre dışı bırakabilirsiniz. Ayrıca, kayıt defterindeki ayarına erişebilirsiniz. Ancak, WCF 'nin ayarı sıfırlamak için kayıt defterini kullanmayı desteklemediğini unutmayın. Değer 1 veya 0 ' dan farklı bir değere ayarlandıysa, CLR ve işletim sistemi arasında tutarsız sonuçlar meydana gelebilir.

### <a name="fips-compliant-aes-encryption-limitation"></a>FIPS uyumlu AES şifreleme sınırlaması

FIPS uyumlu AES şifrelemesi, kimlik düzeyi kimliğe bürünme altında çift yönlü geri çağırmalar içinde çalışmaz.

### <a name="cngksp-certificates"></a>CNG/KSP sertifikaları

*Şifreleme API 'si: yeni nesil (CNG)* , CryptoAPI 'nin uzun süreli yerini alır. Bu API, Windows Vista, Windows Server 2008 ve sonraki Windows sürümlerinde yönetilmeyen kodda kullanılabilir.

 .NET Framework 4.6.1 ve önceki sürümler, CNG/KSP sertifikalarını işlemek için eski CryptoAPI 'yi kullandıkları için bu sertifikaları desteklemez. Bu sertifikaların .NET Framework 4.6.1 ve önceki sürümleriyle kullanımı bir özel duruma neden olur.

 Bir sertifikanın KSP kullanıp kullanmadığını söylemek için iki olası yol vardır:

- `p/invoke` `CertGetCertificateContextProperty` ' İ yapın ve döndürülen ' ı inceleyin `dwProvType` `CertGetCertificateContextProperty` .

- `certutil`Sertifikaları sorgulamak için komut satırından komutunu kullanın. Daha fazla bilgi için bkz. [sertifika sorunlarını giderme Için Certutil görevleri](/previous-versions/orphan-topics/ws.10/cc772619(v=ws.10)).

## <a name="message-security-fails-if-using-aspnet-impersonation-and-aspnet-compatibility-is-required"></a>ASP.NET Kimliğe bürünme ve ASP.NET uyumluluğu kullanılması gerekiyorsa ileti güvenliği başarısız olur

WCF, istemci kimlik doğrulamasının oluşmasını engelleyebileceğinden aşağıdaki ayar birleşimini desteklemez:

- ASP.NET Kimliğe bürünme etkindir. Bu, `impersonate` <> öğesinin özniteliğini olarak ayarlayarak Web.config dosyasında yapılır `identity` `true` .

- Öğesinin özniteliği olarak ayarlanarak ASP.NET uyumluluk modu etkinleştirilir `aspNetCompatibilityEnabled` [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md) `true` .

- İleti modu güvenliği kullanılır.

Geçici çözüm, ASP.NET uyumluluk modunu Kapatbir şekilde çalışır. Ya da ASP.NET uyumluluk modu gerekliyse, ASP.NET Kimliğe bürünme özelliğini devre dışı bırakın ve bunun yerine WCF tarafından belirtilen kimliğe bürünme özelliğini kullanın. Daha fazla bilgi için bkz. [temsil ve kimliğe bürünme](delegation-and-impersonation-with-wcf.md).

## <a name="ipv6-literal-address-failure"></a>IPv6 değişmez değer adresi hatası

İstemci ve hizmet aynı makineden olduğunda güvenlik istekleri başarısız olur ve hizmet için IPv6 değişmez adresler kullanılır.

 Hizmet ve istemci farklı makinelerinizde, sabit IPv6 adresleri çalışır.

## <a name="wsdl-retrieval-failures-with-federated-trust"></a>Federasyon güveniyle WSDL alma sorunları

WCF, Federasyon güven zincirindeki her düğüm için tam olarak bir WSDL belgesi gerektirir. Uç noktaları belirtirken bir döngü ayarlanmamaya dikkat edin. Döngülerin ortaya çıkarılabileceği bir yol, aynı WSDL belgesinde iki veya daha fazla bağlantıyla federasyon güven zincirlerinin WSDL indirmesi kullanmaktır. Bu sorunu oluşturabilecek yaygın bir senaryo, güvenlik belirteci sunucusunun ve hizmetin aynı ServiceHost içinde bulunduğu bir Federasyon hizmetidir.

 Bu durumun bir örneği, aşağıdaki üç uç nokta adresini içeren bir hizmettir:

- `http://localhost/CalculatorService/service` (hizmet)

- `http://localhost/CalculatorService/issue_ticket` (STS)

- `http://localhost/CalculatorService/mex` (meta veri uç noktası)

 Bu bir özel durum oluşturur.

 `issue_ticket`Uç noktayı başka bir yere yerleştirerek bu senaryonun çalışmasını sağlayabilirsiniz.

## <a name="wsdl-import-attributes-can-be-lost"></a>WSDL içeri aktarma öznitelikleri kaybolabilir

`<wst:Claims>` `RST` Bir wsdl içeri aktarma IŞLEMI yaparken WCF, bir şablondaki öğe üzerindeki öznitelikleri izlemeyi kaybeder. Bu durum doğrudan `<Claims>` `WSFederationHttpBinding.Security.Message.TokenRequestParameters` `IssuedSecurityTokenRequestParameters.AdditionalRequestParameters` talep türü koleksiyonları kullanmak yerine veya ' de belirttiğinizde bir wsdl içeri aktarma işlemi sırasında gerçekleşir.  İçeri aktarma öznitelikleri kaybederse, bağlama WSDL aracılığıyla doğru şekilde geri dönmez ve bu nedenle istemci tarafında yanlış.

 Bu, içeri aktarma işlemi yapıldıktan sonra bağlamayı doğrudan istemci üzerinde değiştirmektir.

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik konuları](security-considerations-in-wcf.md)
- [Bilgilerin Açığa Çıkması](information-disclosure.md)
- [Ayrıcalık Yükseltme](elevation-of-privilege.md)
- [Hizmet Reddi](denial-of-service.md)
- [Kurcalama](tampering.md)
- [Yeniden Yürütme Saldırıları](replay-attacks.md)
