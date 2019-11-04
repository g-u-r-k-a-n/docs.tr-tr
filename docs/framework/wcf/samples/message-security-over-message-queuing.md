---
title: İleti Kuyruğa Alma ile İleti Güvenliği
ms.date: 03/30/2017
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
ms.openlocfilehash: d27ee01636e37ac8f09c4f7dc497f14bfac1b0f1
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424120"
---
# <a name="message-security-over-message-queuing"></a>İleti Kuyruğa Alma ile İleti Güvenliği
Bu örnek, istemci için X. 509v3 sertifika kimlik doğrulamasıyla WS-Security kullanan bir uygulamanın nasıl uygulanacağını gösterir ve sunucunun X. 509v3 sertifikasını MSMQ üzerinden kullanarak sunucu kimlik doğrulaması gerektirir. İleti güvenliği bazen MSMQ deposundaki iletilerin şifrelenmesinin ve uygulamanın kendi ileti kimlik doğrulamasını gerçekleştirebileceği durumlarda daha da tercih edilir.

 Bu örnek, [IŞLENEN MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örneğine dayalıdır. İletiler şifrelenir ve imzalanır.

### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Önce hizmet çalıştırıldığında, sıranın mevcut olduğundan emin olmak için kontrol edilir. Sıra yoksa, hizmet bir tane oluşturur. Kuyruğu oluşturmak için önce hizmeti çalıştırabilir veya MSMQ kuyruğu Yöneticisi aracılığıyla bir tane oluşturabilirsiniz. Windows 2008 ' de bir sıra oluşturmak için aşağıdaki adımları izleyin.

    1. Visual Studio 2012 ' de Sunucu Yöneticisi açın.

    2. **Özellikler** sekmesini genişletin.

    3. **Özel Ileti kuyrukları**' ne sağ tıklayıp **Yeni**, **özel kuyruk**' u seçin.

    4. **İşlem** kutusunu işaretleyin.

    5. Yeni kuyruğun adı olarak `ServiceModelSamplesTransacted` girin.

3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.

### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için

1. Yolun MakeCert. exe ve FindPrivateKey. exe içeren klasörü içerdiğinden emin olun.

2. Örnek yükleme klasöründen Setup. bat dosyasını çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.

    > [!NOTE]
    > Örnek ile işiniz bittiğinde Cleanup. bat dosyasını çalıştırarak sertifikaları kaldırtığınızdan emin olun. Diğer güvenlik örnekleri aynı sertifikaları kullanır.  
  
3. \Service\bin. adresinden Service. exe ' yi Başlat  
  
4. \Client\bin. adresinden Client. exe ' yi Başlat İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
5. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Örneği bilgisayarlar arasında çalıştırmak için  
  
1. Setup. bat, Cleanup. bat ve ImportClientCert. bat dosyalarını hizmet bilgisayarına kopyalayın.  
  
2. İstemci bilgisayarda istemci ikilileri için bir dizin oluşturun.  
  
3. İstemci programı dosyalarını istemci bilgisayardaki istemci dizinine kopyalayın. Ayrıca Setup. bat, Cleanup. bat ve ImportServiceCert. bat dosyalarını istemciye kopyalayın.  
  
4. Sunucusunda `setup.bat service`çalıştırın. `setup.bat` `service` bağımsız değişkeniyle çalıştırmak, bilgisayarın tam etki alanı adına sahip bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service. cer adlı bir dosyaya aktarır.  
  
5. Hizmetin Service. exe. config dosyasını, bilgisayarın tam etki alanı adıyla aynı olan yeni sertifika adını `findValue` ( [\<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) göstermek için düzenleyin.  
  
6. Service. cer dosyasını hizmet dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.  
  
7. İstemcisinde `setup.bat client`' yi çalıştırın. `setup.bat` `client` bağımsız değişkeniyle çalıştırmak, client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client. cer adlı bir dosyaya aktarır.  
  
8. İstemci bilgisayardaki Client. exe. config dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin. Localhost 'u sunucunun tam etki alanı adıyla değiştirerek bunu yapın.  Ayrıca hizmetin sertifika adını, hizmet bilgisayarının tam etki alanı adıyla aynı olacak şekilde değiştirmeniz gerekir (`clientCredentials`altında `serviceCertificate` `defaultCertificate` öğesindeki `findValue` özniteliğinde).  
  
9. Client. cer dosyasını istemci dizininden sunucusundaki hizmet dizinine kopyalayın.  
  
10. İstemcisinde `ImportServiceCert.bat`' yi çalıştırın. Bu, hizmet sertifikasını Service. cer dosyasından CurrentUser-Trustedkişiler deposuna aktarır.  
  
11. Sunucusunda `ImportClientCert.bat`çalıştırın, bu, istemci sertifikasını Client. cer dosyasından LocalMachine-Trustedkişiler deposuna aktarır.  
  
12. Hizmet bilgisayarında, komut isteminden Service. exe ' yi başlatın.  
  
13. İstemci bilgisayarda, komut isteminden Client. exe ' yi başlatın. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
- Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup. bat dosyasını çalıştırın.  
  
    > [!NOTE]
    > Bu betik, bilgisayarlar arasında bu örneği çalıştırırken bir istemcideki hizmet sertifikalarını kaldırmaz. Bilgisayarlar arasında sertifika kullanan Windows Communication Foundation (WCF) örneklerini çalıştırırsanız, CurrentUser-Trustedkişiler deposuna yüklenmiş olan hizmet sertifikalarını temizlediğinizden emin olun. Bunu yapmak için şu komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.

## <a name="requirements"></a>Gereksinimler
 Bu örnek, MSMQ 'nun yüklü ve çalışıyor olmasını gerektirir.

## <a name="demonstrates"></a>Gösteriler
 İstemci, hizmetin ortak anahtarını kullanarak iletiyi şifreler ve kendi sertifikasını kullanarak iletiyi imzalar. Sıradan iletiyi okuyan hizmet, güvenilen kişiler deposundaki sertifikayla istemci sertifikasının kimliğini doğrular. Daha sonra iletinin şifresini çözer ve iletiyi hizmet işlemine gönderir.

 Windows Communication Foundation (WCF) iletisi MSMQ iletisinin gövdesinde bir yük olarak yapıldığından, gövde MSMQ deposunda şifreli olarak kalır. Bu, iletinin istenmeyen açıklanmasını sağlar. MSMQ 'nun, taşıma işlemi yaptığı İletinin şifrelenip şifrelenmediğini unutmayın.

 Örnek, ileti düzeyindeki karşılıklı kimlik doğrulamanın MSMQ ile nasıl kullanılabileceğini gösterir. Sertifikalar bant dışı olarak değiştirilir. Hizmet ve istemcinin aynı anda çalışmaya ve çalışır durumda olmaması gerektiğinden, bu her zaman kuyruğa alınmış uygulama ile aynıdır.

## <a name="description"></a>Açıklama
 Örnek istemci ve hizmet kodu, [IŞLENEN MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örneğiyle tek bir farklılık ile aynıdır. İşlem sözleşmesine, iletinin imzalanması ve şifrelenmesi gerektiğini öneren koruma düzeyiyle açıklama eklenir.

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Hizmeti ve istemciyi tanımlamak için gereken belirteç kullanılarak iletinin güvenli olduğundan emin olmak için, App. config kimlik bilgisi bilgilerini içerir.

 İstemci yapılandırması, hizmetin kimliğini doğrulamak için hizmet sertifikasını belirtir. Hizmetin geçerliliğini sağlamak için, güvenli depo olarak kendi LocalMachine mağazasını kullanır. Ayrıca, istemcinin hizmet kimlik doğrulaması için iletiyle ilişkili istemci sertifikasını da belirtir.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>

  <system.serviceModel>

    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"
                binding="netMsmqBinding"
                bindingConfiguration="messageSecurityBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor"
                behaviorConfiguration="ClientCertificateBehavior" />
    </client>

    <bindings>
        <netMsmqBinding>
            <binding name="messageSecurityBinding">
                <security mode="Message">
                    <message clientCredentialType="Certificate"/>
                </security>
            </binding>
        </netMsmqBinding>
    </bindings>

    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <!--
        The clientCredentials behavior allows one to define a certificate to present to a service.
        A certificate is used by a client to authenticate itself to the service and provide message integrity.
        This configuration references the "client.com" certificate installed during the setup instructions.
        -->
          <clientCredentials>
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />
            <serviceCertificate>
                <defaultCertificate findValue="localhost" storeLocation="CurrentUser" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it is trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </serviceCertificate>
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>

  </system.serviceModel>
</configuration>
```

 Güvenlik modunun Ileti olarak ayarlandığını ve ClientCredentialType 'un sertifika olarak ayarlandığını unutmayın.

 Hizmet yapılandırması, istemci hizmetin kimliğini doğruladığında kullanılan hizmetin kimlik bilgilerini belirten bir hizmet davranışı içerir. Sunucu sertifikası konu adı, [\<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)`findValue` özniteliğinde belirtilir.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>

  <appSettings>
    <!-- Use appSetting to configure MSMQ queue name. -->
    <add key="queueName" value=".\private$\ServiceModelSamplesMessageSecurity" />
  </appSettings>

  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.OrderProcessorService"
          behaviorConfiguration="PurchaseOrderServiceBehavior">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
          </baseAddresses>
        </host>
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"
                  binding="netMsmqBinding"
                  bindingConfiguration="messageSecurityBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
        <!-- The mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex. -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>

    <bindings>
        <netMsmqBinding>
            <binding name="messageSecurityBinding">
                <security mode="Message">
                    <message clientCredentialType="Certificate" />
                </security>
            </binding>
        </netMsmqBinding>
    </bindings>

    <behaviors>
      <serviceBehaviors>
        <behavior name="PurchaseOrderServiceBehavior">
          <serviceMetadata httpGetEnabled="True"/>
          <!--
               The serviceCredentials behavior allows one to define a service certificate.
               A service certificate is used by the service to authenticate itself to its clients and to provide message protection.
               This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
            <clientCertificate>
                <certificate findValue="client.com" storeLocation="LocalMachine" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it is trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </clientCertificate>
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>

</configuration>
```

 Örnek, yapılandırma kullanarak kimlik doğrulamanın denetlenmesini ve aşağıdaki örnek kodda gösterildiği gibi çağıranın kimliğini güvenlik bağlamında nasıl elde leyeceğinizi gösterir:

```csharp
// Service class which implements the service contract.
// Added code to write output to the console window.
public class OrderProcessorService : IOrderProcessor
{
    private string GetCallerIdentity()
    {
        // The client certificate is not mapped to a Windows identity by default.
        // ServiceSecurityContext.PrimaryIdentity is populated based on the information
        // in the certificate that the client used to authenticate itself to the service.
        return ServiceSecurityContext.Current.PrimaryIdentity.Name;
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Console.WriteLine("Client's Identity {0} ", GetCallerIdentity());
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
    }
  //…
}
```

 Çalıştırıldığında, hizmet kodu istemci kimliğini görüntüler. Aşağıda, hizmet kodundan alınan bir örnek çıktı verilmiştir:

```console
The service is ready.
Press <ENTER> to terminate service.

Client's Identity CN=client.com; ECA6629A3C695D01832D77EEE836E04891DE9D3C
Processing Purchase Order: 6536e097-da96-4773-9da3-77bab4345b5d
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

## <a name="comments"></a>Açıklamalar

- İstemci sertifikası oluşturuluyor.

     Toplu iş dosyasındaki aşağıdaki satır, istemci sertifikasını oluşturur. Belirtilen istemci adı, oluşturulan sertifikanın konu adı ' nda kullanılır. Sertifika, `CurrentUser` depolama konumunda `My` deposunda depolanır.

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- İstemci sertifikası sunucunun Güvenilen sertifika deposuna yükleniyor.

     Toplu iş dosyasında aşağıdaki satır, sunucunun ilgili güveni veya güven dışı kararlar verebilmeleri için istemci sertifikasını sunucunun Trustedkişiler deposuna kopyalar. Trustedkişiler deposuna bir Windows Communication Foundation (WCF) hizmeti tarafından Güvenilmeye yönelik bir sertifika için, istemci sertifikası doğrulama modunun `PeerOrChainTrust` veya `PeerTrust` değeri olarak ayarlanması gerekir. Bunun bir yapılandırma dosyası kullanılarak nasıl yapılabileceğinizi öğrenmek için önceki hizmet yapılandırma örneğine bakın.

    ```bat
    echo ************
    echo copying client cert to server's LocalMachine store
    echo ************
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

- Sunucu sertifikası oluşturuluyor.

     Setup. bat toplu iş dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturun:

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     % SERVER_NAME% değişkeni sunucu adını belirtiyor. Sertifika, LocalMachine deposunda depolanır. Kurulum Batch dosyası bir hizmet bağımsız değişkeniyle (örneğin, `setup.bat service`) çalışıyorsa% SUNUCU_ADı% bilgisayarın tam etki alanı adını içerir. Aksi takdirde, varsayılan olarak localhost olur

- Sunucu sertifikası istemcinin güvenilen sertifika deposuna yükleniyor.

     Aşağıdaki satır, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar. Bu adım, MakeCert. exe tarafından oluşturulan sertifikaların istemci sistemi tarafından örtük olarak güvenilir olmadığından gereklidir. İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > Microsoft Windows 'un U. S. Ingilizce sürümünü kullanıyorsanız, Setup. bat dosyasını düzenlemeniz ve "NT AUTHORITY\NETWORK SERVICE" hesap adını bölgesel eşdeğerle değiştirmeniz gerekir.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
