---
description: 'Hakkında daha fazla bilgi edinin: WSStreamedHttpBinding'
title: WSStreamedHttpBinding
ms.date: 03/30/2017
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
ms.openlocfilehash: ef5b3bf3501f64389005ea1542874ff32a42ad82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668285"
---
# <a name="wsstreamedhttpbinding"></a>WSStreamedHttpBinding

Örnek, HTTP taşıması kullanıldığında akış senaryolarını destekleyecek şekilde tasarlanan bir bağlamanın nasıl oluşturulacağını gösterir.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`

 Yeni bir standart bağlama oluşturma ve yapılandırma adımları aşağıdaki gibidir.

1. Yeni bir standart bağlama oluştur

    BasicHttpBinding ve netTcpBinding gibi Windows Communication Foundation (WCF) içindeki standart bağlamalar, belirli gereksinimler için temel taşımaları ve kanal yığınını yapılandırır. Bu örnekte, `WSStreamedHttpBinding` Kanal yığınını akışı destekleyecek şekilde yapılandırır. Varsayılan olarak, WS-Security ve güvenilir mesajlaşma, her iki özellik de akış tarafından desteklenmediğinden kanal yığınına eklenmez. Yeni bağlama, `WSStreamedHttpBinding` öğesinden türetilen sınıfta uygulanır <xref:System.ServiceModel.Channels.Binding> . , `WSStreamedHttpBinding` Aşağıdaki bağlama öğelerini içerir: <xref:System.ServiceModel.Channels.HttpTransportBindingElement> , <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> , <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> ve <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> . Sınıfı, `CreateBindingElements()` Aşağıdaki örnek kodda gösterildiği gibi, elde edilen bağlama yığınını yapılandırmak için bir yöntem sağlar.

    ```csharp
    public override BindingElementCollection CreateBindingElements()
    {
        // return collection of BindingElements
        BindingElementCollection bindingElements = new BindingElementCollection();

        // the order of binding elements within the collection is important: layered channels are applied in the order included, followed by
        // the message encoder, and finally the transport at the end
        if (flowTransactions)
        {
            bindingElements.Add(transactionFlow);
        }
        bindingElements.Add(textEncoding);

        // add transport (http or https)
        bindingElements.Add(transport);
        return bindingElements.Clone();
    }
    ```

2. Yapılandırma desteği ekle

    Aktarımı yapılandırma yoluyla göstermek için örnek iki sınıf daha uygular — `WSStreamedHttpBindingConfigurationElement` ve `WSStreamedHttpBindingSection` . Sınıfı, `WSStreamedHttpBindingSection` <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> `WSStreamedHttpBinding` WCF yapılandırma sistemine yönelik bir ' dir. Uygulamanın toplu işlemi, `WSStreamedHttpBindingConfigurationElement` ' den türetilen için Temsilcili <xref:System.ServiceModel.Configuration.StandardBindingElement> . Sınıfı `WSStreamedHttpBindingConfigurationElement` , özelliklerine karşılık gelen özelliklere `WSStreamedHttpBinding` ve her yapılandırma öğesini bir bağlamaya eşlemek için işlevlere sahiptir.

    Hizmetin yapılandırma dosyasına aşağıdaki bölümü ekleyerek işleyiciyi yapılandırma sistemine kaydedin.

    ```xml
    <configuration>
      <system.serviceModel>
        <extensions>
          <bindingExtensions>
            <add name="wsStreamedHttpBinding" type="Microsoft.ServiceModel.Samples.WSStreamedHttpBindingCollectionElement, WSStreamedHttpBinding, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />
          </bindingExtensions>
        </extensions>
      </system.serviceModel>
    </configuration>
    ```

    İşleyiciye daha sonra serviceModel yapılandırma bölümünden başvurulabilir.

    ```xml
    <configuration>
      <system.serviceModel>
        <client>
          <endpoint
                    address="https://localhost/servicemodelsamples/service.svc"
                    bindingConfiguration="Binding"
                    binding="wsStreamedHttpBinding"
                    contract="Microsoft.ServiceModel.Samples.IStreamedEchoService"/>
        </client>
      </system.serviceModel>
    </configuration>
    ```

### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. [Windows Communication Foundation Örnekleri Için tek seferlik kurulum yordamında](one-time-setup-procedure-for-the-wcf-samples.md)listelenen adımları gerçekleştirdiğinizden emin olun.

3. [Internet Information Services (IIS) sunucu sertifikası yükleme yönergelerini](iis-server-certificate-installation-instructions.md)gerçekleştirdiğinizden emin olun.

4. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.

5. Örneği bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.

6. İstemci penceresi görüntülendiğinde "Sample.txt" yazın. Dizininizde bir "Sample.txt kopyası" bulmanız gerekir.

## <a name="the-wsstreamedhttpbinding-sample-service"></a>WSStreamedHttpBinding örnek hizmeti

Tarafından kullanılan örnek hizmet, `WSStreamedHttpBinding` hizmet alt dizininde bulunur. Uygulamasının uygulamasını `OperationContract` `MemoryStream` döndürmeden önce gelen akıştan tüm verileri almak için bir kullanır `MemoryStream` . Örnek hizmet Internet Information Services (IIS) tarafından barındırılır.

```csharp
[ServiceContract]
public interface IStreamedEchoService
{
    [OperationContract]
    Stream Echo(Stream data);
}

public class StreamedEchoService : IStreamedEchoService
{
    public Stream Echo(Stream data)
    {
        MemoryStream dataStorage = new MemoryStream();
        byte[] byteArray = new byte[8192];
        int bytesRead = data.Read(byteArray, 0, 8192);
        while (bytesRead > 0)
        {
            dataStorage.Write(byteArray, 0, bytesRead);
            bytesRead = data.Read(byteArray, 0, 8192);
        }
        data.Close();
        dataStorage.Seek(0, SeekOrigin.Begin);

        return dataStorage;
    }
}
```

## <a name="the-wsstreamedhttpbinding-sample-client"></a>WSStreamedHttpBinding örnek Istemcisi

Kullanılarak hizmetle etkileşim kurmak için kullanılan istemci, `WSStreamedHttpBinding` istemci alt dizininde bulunur. Bu örnekte kullanılan sertifika Makecert.exe ile oluşturulmuş bir test sertifikası olduğundan, tarayıcınızda bir HTTPS adresine erişmeye çalıştığınızda bir güvenlik uyarısı görüntülenir `https://localhost/servicemodelsamples/service.svc` . WCF istemcisinin yerinde bir test sertifikasıyla çalışmasına izin vermek için, güvenlik uyarısını bastırmak üzere istemciye bazı ek kodlar eklenmiştir. Üretim sertifikaları kullanılırken kod ve eşlik eden sınıf gerekli değildir.

```csharp
// WARNING: This code is only required for test certificates such as those created by makecert. It is
// not recommended for production code.
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");
```
