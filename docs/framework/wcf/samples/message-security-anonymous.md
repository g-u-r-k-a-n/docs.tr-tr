---
title: İleti Güvenliği Anonim
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c321cbf9-8c05-4cce-b5a5-4bf7b230ee03
ms.openlocfilehash: 7ba64f28d621dad51957438025de22827405dd87
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558673"
---
# <a name="message-security-anonymous"></a>İleti Güvenliği Anonim
Ileti güvenliği anonim örneği, istemci kimlik doğrulaması olmadan ileti düzeyinde güvenlik kullanan ancak sunucunun X. 509.440 sertifikasını kullanarak sunucu kimlik doğrulaması gerektiren bir Windows Communication Foundation (WCF) uygulamasının nasıl uygulanacağını gösterir. İstemci ve sunucu arasındaki tüm uygulama iletileri imzalanır ve şifrelenir. Bu örnek, [WSHttpBinding](wshttpbinding.md) örneğine dayalıdır. Bu örnek, Internet Information Services (IIS) tarafından barındırılan bir istemci konsol programından (. exe) ve hizmet kitaplığından (. dll) oluşur. Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

 Bu örnek, `True` istemci kimlik doğrulamasından geçirilmediğinden döndüren Hesaplayıcı arabirimine yeni bir işlem ekler.

```csharp
public class CalculatorService : ICalculator
{
    public bool IsCallerAnonymous()
    {
        // ServiceSecurityContext.IsAnonymous returns true if the caller is not authenticated.
        return ServiceSecurityContext.Current.IsAnonymous;
    }
    ...
}
```

 Hizmet, bir yapılandırma dosyası (Web.config) kullanılarak tanımlanan hizmetle iletişim kurmak için tek bir uç nokta sunar. Uç nokta bir adres, bağlama ve bir anlaşmada oluşur. Bağlama bir bağlama ile yapılandırılır `wsHttpBinding` . Bağlama için varsayılan güvenlik modu `wsHttpBinding` `Message` . `clientCredentialType`Özniteliği olarak ayarlanır `None` .

```xml
<system.serviceModel>

  <protocolMapping>
    <add scheme="http" binding="wsHttpBinding" />
  </protocolMapping>

  <bindings>
    <wsHttpBinding>
     <!-- This configuration defines the security mode as Message and -->
     <!-- the clientCredentialType as None. This mode provides -->
     <!-- server authentication only using the service certificate. -->

     <binding>
       <security mode="Message">
         <message clientCredentialType="None" />
       </security>
     </binding>
    </wsHttpBinding>
  </bindings>
  ...
</system.serviceModel>
```

 Hizmet kimlik doğrulaması için kullanılacak kimlik bilgileri içinde belirtilir [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) . Sunucu sertifikası, `SubjectName` `findValue` Aşağıdaki örnek kodda gösterildiği gibi, özniteliği için belirtilen değer olarak aynı değeri içermelidir.

```xml
<behaviors>
  <serviceBehaviors>
    <behavior>
      <!--
    The serviceCredentials behavior allows you to define a service certificate.
    A service certificate is used by a client to authenticate the service and provide message protection.
    This configuration references the "localhost" certificate installed during the setup instructions.
    -->
      <serviceCredentials>
        <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
      </serviceCredentials>
      <serviceMetadata httpGetEnabled="True"/>
      <serviceDebug includeExceptionDetailInFaults="False" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```

 İstemci uç noktası yapılandırması, hizmet uç noktası, bağlama ve sözleşme için mutlak bir adresten oluşur. Bağlama için istemci güvenlik modu `wsHttpBinding` `Message` . `clientCredentialType`Özniteliği olarak ayarlanır `None` .

```xml
<system.serviceModel>
  <client>
    <endpoint name=""
             address="http://localhost/servicemodelsamples/service.svc"
             binding="wsHttpBinding"
             behaviorConfiguration="ClientCredentialsBehavior"
             bindingConfiguration="Binding1"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </client>

  <bindings>
    <wsHttpBinding>
      <!--This configuration defines the security mode as -->
      <!--Message and the clientCredentialType as None. -->
      <binding name="Binding1">
        <security mode = "Message">
          <message clientCredentialType="None"/>
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>
  ...
</system.serviceModel>
```

 Örnek, <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> hizmet sertifikasının kimliğini doğrulamak için öğesini olarak ayarlar. Bu, bölümünde istemcinin App.config dosyasında yapılır `behaviors` . Bu, sertifika kullanıcının güvenilir kişiler depoluiyorsa, sertifikanın veren zincirinin doğrulanması yapılmadan güvenilir hale gelir. Bu ayar, örneğin bir sertifika yetkilisi (CA) tarafından verilen sertifikalara gerek kalmadan çalıştırılabilmesi için kolaylık sağlamak amacıyla burada kullanılır. Bu ayar varsayılan, ChainTrust değerinden daha az güvenlidir. Bu ayarın güvenlik etkileri, üretim kodunda kullanılmadan önce dikkatle düşünülmelidir `PeerOrChainTrust` .

 İstemci uygulama yöntemine bir çağrı ekler ve bu `IsCallerAnonymous` nedenle [WSHttpBinding](wshttpbinding.md) örneğinden farklı değildir.

```csharp
// Create a client with a client endpoint configuration.
CalculatorClient client = new CalculatorClient();

// Call the GetCallerIdentity operation.
Console.WriteLine("IsCallerAnonymous returned: {0}", client.IsCallerAnonymous());

// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = client.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

...

//Closing the client gracefully closes the connection and cleans up resources.
client.Close();

Console.WriteLine();
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.

```console
IsCallerAnonymous returned: True
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 Ileti güvenliği anonim örneğine eklenen Setup.bat toplu iş dosyası, sertifika tabanlı güvenlik gerektiren barındırılan bir uygulamayı çalıştırmak için sunucuyu ilgili sertifikayla yapılandırmanızı sağlar. Toplu iş dosyası iki modda çalıştırılabilir. Toplu iş dosyasını tek bilgisayar modunda çalıştırmak için `setup.bat` komut satırına yazın. Hizmet modunda çalıştırmak için yazın `setup.bat service` . Örneği bilgisayarlar arasında çalıştırırken bu modu kullanın. Ayrıntılar için bu konunun sonundaki Kurulum yordamına bakın.

 Aşağıdakiler, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlar:

- Sunucu sertifikası oluşturuluyor.

     Setup.bat Batch dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur.

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     % SERVER_NAME% değişkeni sunucu adını belirtiyor. Sertifika, LocalMachine deposunda depolanır. Kurulum Batch dosyası bir hizmet bağımsız değişkeniyle (örneğin `setup.bat service` ,) çalışıyorsa% SERVER_NAME% bilgisayarın tam etki alanı adını içerir. Aksi takdirde, varsayılan olarak localhost olur.

- Sunucu sertifikasını istemcinin güvenilen sertifika deposuna yükleme.

     Aşağıdaki satır, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar. Makecert.exe tarafından oluşturulan sertifikalara istemci sistemi tarafından örtük olarak güvenilmediğinden Bu adım gereklidir. İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- Sertifikanın özel anahtarına izin veriliyor.

     Setup.bat Batch dosyasındaki aşağıdaki satırlar, LocalMachine deposunda depolanan sunucu sertifikasını ASP.NET çalışan işlem hesabına erişilebilir hale getirir.

    ```bat
    echo ************
    echo setting privileges on server certificates
    echo ************
    for /F "delims=" %%i in ('"%MSSDK%\bin\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
    (ver | findstr "5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
    iisreset
    ```

> [!NOTE]
> U-U olmayan bir. S kullanıyorsanız. Windows 'un İngilizce sürümü Setup.bat dosyasını düzenlemeniz ve `NT AUTHORITY\NETWORK SERVICE` hesap adını bölgesel eşdeğerle değiştirmeniz gerekir.

### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.

### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için

1. Yolun Makecert.exe ve FindPrivateKey.exe bulunduğu klasörü içerdiğinden emin olun.

2. Visual Studio için Geliştirici Komut İstemi örnek install klasöründen yönetici ayrıcalıklarıyla Çalıştır ' a Setup.bat çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.

    > [!NOTE]
    > Kurulum toplu iş dosyası, Visual Studio için bir Geliştirici Komut İstemi çalıştırılmak üzere tasarlanmıştır. PATH ortam değişkeninin, SDK 'nın yüklü olduğu dizine işaret olmasını gerektirir. Bu ortam değişkeni, Visual Studio için bir Geliştirici Komut İstemi içinde otomatik olarak ayarlanır.  
  
3. Adresi girerek bir tarayıcı kullanarak hizmete erişimi doğrulayın `http://localhost/servicemodelsamples/service.svc` .  
  
4. \Client\bin. 'den başlatma Client.exe İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
5. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Örneği bilgisayarlar arasında çalıştırmak için  
  
1. Hizmet bilgisayarında bir dizin oluşturun. Internet Information Services (IIS) yönetim aracını kullanarak bu dizin için servicemodelsamples adlı bir sanal uygulama oluşturun.  
  
2. Hizmet programı dosyalarını \inetpub\wwwroot\servicemodelsamples adresinden hizmet bilgisayarındaki sanal dizine kopyalayın. Dosyaları \bin alt dizininde kopyalamadiğinizden emin olun. Ayrıca, Setup.bat ve Cleanup.bat dosyalarını hizmet bilgisayarına kopyalayın.  
  
3. İstemci bilgisayarda istemci ikilileri için bir dizin oluşturun.  
  
4. İstemci programı dosyalarını istemci bilgisayardaki istemci dizinine kopyalayın. Ayrıca Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını istemciye kopyalayın.  
  
5. Sunucusunda, `setup.bat service` yönetici ayrıcalıklarıyla açılan bir Visual Studio için geliştirici komut istemi çalıştırın. `setup.bat`Bağımsız değişkeniyle birlikte çalıştırmak, `service` bilgisayarın tam etki alanı adına sahip bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service. cer adlı bir dosyaya aktarır.  
  
6. Web.config, `findValue` [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) bilgisayarın tam etki alanı adıyla aynı olan yeni sertifika adını (içindeki özniteliğinde) yansıtacak şekilde düzenleyin.  
  
7. Service. cer dosyasını hizmet dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.  
  
8. İstemci bilgisayardaki Client.exe.config dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.  
  
9. İstemcisinde ImportServiceCert.bat, yönetici ayrıcalıklarıyla açılmış bir Visual Studio Geliştirici Komut İstemi çalıştırın. Bu, hizmet sertifikasını Service. cer dosyasından CurrentUser-Trustedkişiler deposuna aktarır.  
  
10. İstemci bilgisayarda, bir komut isteminden Client.exe başlatın. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
- Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup.bat çalıştırın.  
  
> [!NOTE]
> Bu betik, bilgisayarlar arasında bu örneği çalıştırırken bir istemcideki hizmet sertifikalarını kaldırmaz. Bilgisayarlar arasında sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırırsanız, CurrentUser-Trustedkişiler deposuna yüklenmiş olan hizmet sertifikalarını temizlediğinizden emin olun. Bunu yapmak için şu komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`
