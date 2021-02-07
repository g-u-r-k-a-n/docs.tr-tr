---
description: 'Daha fazla bilgi edinin: özel bağlama güvenliği'
title: Özel Bağlama Güvenliği
ms.date: 03/30/2017
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
ms.openlocfilehash: f0ed4b40fe4e0869f34a4f6016123dc9f0a57f45
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732637"
---
# <a name="custom-binding-security"></a>Özel Bağlama Güvenliği

Bu örnek, bir özel bağlama kullanılarak güvenliğin nasıl yapılandırılacağını gösterir. Güvenli bir aktarımla ileti düzeyi güvenliği etkinleştirmek için özel bağlamayı nasıl kullanacağınızı gösterir. Bu, iletileri istemci ve hizmet arasında iletmek için güvenli bir aktarım gerektiğinde ve iletilerin ileti düzeyinde güvenli olması gerektiği durumlarda yararlıdır. Bu yapılandırma sistem tarafından belirtilen bağlamalar tarafından desteklenmiyor.

Bu örnek, bir istemci konsol programından (EXE) ve bir hizmet konsolu programından (EXE) oluşur. Hizmet bir çift yönlü sözleşme uygular. Sözleşme, `ICalculatorDuplex` matematik işlemlerini (ekleme, çıkarma, çarpma ve bölme) sunan arabirim tarafından tanımlanır. `ICalculatorDuplex`Arabirim, istemcinin bir oturum üzerinde çalışan bir sonucu hesaplamak için matematik işlemleri gerçekleştirmesini sağlar. Bağımsız olarak, hizmet sonuçları `ICalculatorDuplexCallback` arabirime döndürebilir. Bir çift yönlü sözleşme, istemci ve hizmet arasında gönderilen ileti kümesiyle ilişkilendirilmesi için bir bağlam kurulması gerektiğinden oturum gerektirir. Çift yönlü iletişimi destekleyen ve güvenli hale gelen özel bir bağlama tanımlanmıştır.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

Hizmet yapılandırması aşağıdakileri destekleyen özel bir bağlama tanımlar:

- TLS/SSL protokolü kullanılarak korunan TCP iletişimi.

- Windows ileti güvenliği.

Özel bağlama yapılandırması, ileti düzeyi güvenliği aynı anda etkinleştirerek güvenli aktarımı etkinleştirir. Bağlama öğelerinin sıralaması, her biri kanal yığınındaki bir katmanı temsil ettiğinden (bkz. [Özel Bağlamalar](../extending/custom-bindings.md)) özel bir bağlama tanımlamak açısından önemlidir. Özel bağlama, aşağıdaki örnek yapılandırmada gösterildiği gibi hizmette ve istemci yapılandırma dosyalarında tanımlanmıştır.

```xml
<bindings>
  <!-- Configure a custom binding. -->
  <customBinding>
    <binding name="Binding1">
      <security authenticationMode="SecureConversation"
                 requireSecurityContextCancellation="true">
      </security>
      <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>
      <sslStreamSecurity requireClientCertificate="false"/>
      <tcpTransport/>
    </binding>
  </customBinding>
</bindings>
```

Özel bağlama, Aktarım düzeyinde hizmetin kimliğini doğrulamak ve istemci ile hizmet arasında iletim sırasında iletileri korumak için bir hizmet sertifikası kullanır. Bu, `sslStreamSecurity` Binding öğesi tarafından gerçekleştirilir. Hizmetin sertifikası, aşağıdaki örnek yapılandırmada gösterildiği gibi bir hizmet davranışı kullanılarak yapılandırılır.

```xml
<behaviors>
    <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
        <serviceMetadata />
        <serviceDebug includeExceptionDetailInFaults="False" />
        <serviceCredentials>
        <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName"/>
        </serviceCredentials>
    </behavior>
    </serviceBehaviors>
</behaviors>
```

Ayrıca, özel bağlama Windows kimlik bilgisi türü ile ileti güvenliği kullanır-bu, varsayılan kimlik bilgisi türüdür. Bu, `security` Binding öğesi tarafından gerçekleştirilir. Kerberos kimlik doğrulama mekanizması kullanılabiliyorsa, istemci ve hizmetin her ikisi de ileti düzeyi güvenlik kullanılarak doğrulanır. Bu, örnek Active Directory ortamda çalıştırıldığında oluşur. Kerberos kimlik doğrulama mekanizması kullanılamıyorsa, NTLM kimlik doğrulaması kullanılır. NTLM, istemcinin hizmet kimliğini doğrular, ancak hizmette hizmetin kimliğini doğrulamaz. `security`Bağlama öğesi kullanmak üzere yapılandırılmıştır `SecureConversation` `authenticationType` , bu da hem istemcide hem de hizmette bir güvenlik oturumu oluşturulmasına neden olur. Bu, hizmetin çift yönlü sözleşmesinin çalışmasını sağlamak için gereklidir.

Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemcinin konsol penceresinde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.

```console
Press <ENTER> to terminate client.
Result(100)
Result(50)
Result(882.5)
Result(441.25)
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)
```

Örneği çalıştırdığınızda, hizmetten gönderilen geri çağırma arabirimindeki istemciye döndürülen iletileri görürsünüz. Her ara sonuç görüntülenir ve tüm işlemler tamamlandıktan sonra denklemin tamamı gelir. İstemcisini kapatmak için ENTER tuşuna basın.

Eklenen Setup.bat dosyası, sertifika tabanlı güvenlik gerektiren bir barındırılan uygulamayı çalıştırmak için istemciyi ve sunucuyu ilgili hizmet sertifikasıyla yapılandırmanıza olanak sağlar. Bu toplu iş dosyasının bilgisayarlarda çalışmak veya barındırılmayan bir durumda çalışması için değiştirilmesi gerekir.

Aşağıda, uygun yapılandırmada çalışacak şekilde değiştirilebilecek şekilde, bu örneğe uygulanan toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış verilmiştir:

- Sunucu sertifikası oluşturuluyor.

  Setup.bat dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur. `%SERVER_NAME%`Değişken, sunucu adını belirtir. Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin. Bu toplu iş dosyası, sunucu adını localhost olarak varsayılan olarak belirler.

  Sertifika, Web 'de barındırılan hizmetler için CurrentUser deposunda depolanır.

  ```bat
  echo ************
  echo Server cert setup starting
  echo %SERVER_NAME%
  echo ************
  echo making server cert
  echo ************
  makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
  ```

- Sunucu sertifikasını istemcinin güvenilen sertifika deposuna yükleme.

  Setup.bat dosyasındaki aşağıdaki satırlar, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar. Makecert.exe tarafından oluşturulan sertifikalara istemci sistemi tarafından örtük olarak güvenilmediğinden Bu adım gereklidir. İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.

  ```console
  certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
  ```

  > [!NOTE]
  > Setup.bat Batch dosyası bir Visual Studio 2010 komut Isteminden çalıştırılmak üzere tasarlanmıştır. MSSDK ortam değişkeninin, SDK 'nın yüklü olduğu dizine işaret olmasını gerektirir. Bu ortam değişkeni, Visual Studio 2010 komut Istemi içinde otomatik olarak ayarlanır.

### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.

3. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.

### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için

1. Yönetici ayrıcalıklarıyla Visual Studio için bir Geliştirici Komut İstemi açın ve örnek yüklemesi klasöründen Setup.bat çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.

    > [!NOTE]
    > Setup.bat Batch dosyası bir Visual Studio 2012 komut Isteminden çalıştırılmak üzere tasarlanmıştır. Visual Studio 2012 komut Isteminde ayarlanan PATH ortam değişkeni, Setup.bat betiği için gereken yürütülebilir dosyaları içeren dizine işaret eder.

2. \Service\bin. 'den başlatma Service.exe

3. \Client\bin. 'den başlatma Client.exe İstemci etkinliği istemci konsol uygulamasında görüntülenir.

4. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).

### <a name="to-run-the-sample-across-computers"></a>Örneği bilgisayarlar arasında çalıştırmak için

1. Hizmet bilgisayarında:

    1. Hizmet bilgisayarında servicemodelsamples adlı bir sanal dizin oluşturun.

    2. Hizmet programı dosyalarını \inetpub\wwwroot\servicemodelsamples adresinden hizmet bilgisayarındaki sanal dizine kopyalayın. Dosyaları \bin alt dizininde kopyalamadiğinizden emin olun.

    3. Setup.bat ve Cleanup.bat dosyalarını hizmet bilgisayarına kopyalayın.

    4. Yönetici ayrıcalıklarıyla açılmış bir Visual Studio Geliştirici Komut İstemi için aşağıdaki komutu çalıştırın: `Setup.bat service` . Bu işlem, toplu iş dosyasının çalıştırıldığı bilgisayarın adıyla eşleşen konu adına sahip hizmet sertifikasını oluşturur.

        > [!NOTE]
        > Setup.bat Batch dosyası bir Visual Studio 2010 komut Isteminden çalıştırılmak üzere tasarlanmıştır. PATH ortam değişkeninin, SDK 'nın yüklü olduğu dizine işaret olmasını gerektirir. Bu ortam değişkeni, Visual Studio 2010 komut Istemi içinde otomatik olarak ayarlanır.

    5. [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)Service.exe.config dosyanın içinde, önceki adımda oluşturulan sertifikanın konu adını yansıtacak şekilde değiştirin.

    6. Komut isteminden Service.exe çalıştırın.

2. İstemci bilgisayarda:

    1. İstemci program dosyalarını \client\bin\ klasöründen istemci bilgisayara kopyalayın. Cleanup.bat dosyasını da kopyalayın.

    2. Önceki örneklerden gelen eski sertifikaları kaldırmak için Cleanup.bat çalıştırın.

    3. Yönetim ayrıcalıklarına sahip bir Visual Studio Geliştirici Komut İstemi açarak ve hizmet bilgisayarında aşağıdaki komutu çalıştırarak hizmetin sertifikasını dışarı aktarın ( `%SERVER_NAME%` hizmetin çalıştığı bilgisayarın tam adıyla değiştirin):

        ```console
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer
        ```

    4. % SERVER_NAME%. cer öğesini istemci bilgisayara kopyalayın (% SERVER_NAME% değerini hizmetin çalıştığı bilgisayarın tam adı ile değiştirin).

    5. Yönetim ayrıcalıklarına sahip bir Visual Studio Geliştirici Komut İstemi açarak hizmetin sertifikasını içeri aktarın ve istemci bilgisayarda aşağıdaki komutu çalıştırın (% SERVER_NAME% değerini hizmetin çalıştığı bilgisayarın tam adı ile değiştirin):

        ```console
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople
        ```

        Sertifika güvenilen bir veren tarafından verildiyse, c, d ve e adımları gerekli değildir.

    6. İstemcinin App.config dosyasını aşağıdaki gibi değiştirin:

        ```xml
        <client>
            <endpoint name="default"
                address="net.tcp://ReplaceThisWithServiceMachineName:8000/ServiceModelSamples/Service"
                binding="customBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex"
                behaviorConfiguration="CalculatorClientBehavior" />
        </client>
        ```

    7. Hizmet, bir etki alanı ortamında NetworkService veya LocalSystem hesabı dışında bir hesap altında çalışıyorsa, hizmeti çalıştırmak için kullanılan hesaba göre uygun UPN veya SPN 'yi ayarlamak için istemci App.config dosyası içindeki hizmet uç noktası kimliğini değiştirmeniz gerekebilir. Uç nokta kimliği hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulama](../feature-details/service-identity-and-authentication.md) konusu.

    8. Komut isteminden Client.exe çalıştırın.

### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için

- Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup.bat çalıştırın.
