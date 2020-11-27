---
title: Akış
ms.date: 03/30/2017
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
ms.openlocfilehash: 04bc5db4172d9052b45f63a2f7ed0fb997dc4c6c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257204"
---
# <a name="stream"></a>Akış

Akış örneği, akış aktarım modu iletişiminin kullanımını gösterir. Hizmet, akışları gönderen ve alan birkaç işlem sunar. Bu örnek kendi kendine barındırılır. Hem istemci hem de hizmet konsol programlarıdır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Windows Communication Foundation (WCF), iki Aktarım modunda (ara belleğe alınmış veya akış) iletişim kurabilir. Varsayılan arabellekli Aktarım modunda, bir alıcının okuyabilmesi için bir iletinin tamamen teslim edilmesi gerekir. Akış Aktarım modunda, alıcı tamamen teslim edilmeden önce iletiyi işlemeye başlayabilir. Aktarım modu, iletilen bilgiler uzun olduğunda ve hizmet dışı olarak işlenebilmesi durumunda faydalıdır. İleti tamamen arabelleğe alınamayacak kadar büyük olduğunda akış modu da yararlıdır.  
  
## <a name="streaming-and-service-contracts"></a>Akış ve hizmet sözleşmeleri  

 Akış, bir hizmet sözleşmesi tasarlarken göz önünde bulundurulmalıdır. Bir işlem büyük miktarlarda veri alırsa veya döndürürse, giriş veya çıkış iletilerinin arabelleğe alınması nedeniyle yüksek bellek kullanımının oluşmaması için bu verileri akışını göz önünde bulundurmanız gerekir. Veri akışı için, bu verileri tutan parametre iletideki tek parametre olmalıdır. Örneğin, giriş iletisi akışla bir giriş ise, işlemin tam olarak bir giriş parametresi olmalıdır. Benzer şekilde, çıkış iletisi akışı ise, işlemin tam olarak bir çıkış parametresi veya dönüş değeri olması gerekir. Her iki durumda da parametre veya dönüş değeri türü, ya da olmalıdır `Stream` `Message` `IXmlSerializable` . Bu akış örneğinde kullanılan hizmet sözleşmesi aşağıda verilmiştir.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IStreamingSample  
{  
    [OperationContract]  
    Stream GetStream(string data);  
    [OperationContract]  
    bool UploadStream(Stream stream);  
    [OperationContract]  
    Stream EchoStream(Stream stream);  
    [OperationContract]  
    Stream GetReversedStream();  
  
}  
```  
  
 `GetStream`İşlem, arabelleğe alınmış bir dize olarak bazı giriş verileri alır ve akış olan bir döndürür `Stream` . Buna karşılık, `UploadStream` `Stream` (akış) alır ve `bool` (ara belleğe alınmış) döndürür. `EchoStream` , `Stream` giriş ve çıkış iletilerinin her ikisi de akışındaki bir işlemin örneğini alır ve döndürür. Son olarak, `GetReversedStream` giriş yapılmaz ve `Stream` (akış) döndürür.  
  
## <a name="enabling-streamed-transfers"></a>Akışlı aktarımları etkinleştirme  

 Daha önce açıklandığı gibi, işlem sözleşmelerini tanımlama, programlama modeli düzeyinde akış sağlar. Bunu durdurursanız, aktarım, tüm ileti içeriğini arabelleğe almaya devam eder. Aktarım akışını etkinleştirmek için, taşımanın bağlama öğesinde bir aktarım modu seçin. Binding öğesi,,, `TransferMode` veya olarak ayarlanabilir bir özelliğine sahiptir `Buffered` `Streamed` `StreamedRequest` `StreamedResponse` . Aktarım modunun, `Streamed` her iki yönde de akış iletişimini sağlamak üzere ayarlanması. Aktarım modunun, `StreamedRequest` `StreamedResponse` sırasıyla yalnızca istekte veya yanıtta akış iletişimini ayarlama veya sağlama.  
  
 , `basicHttpBinding` `TransferMode` Bağlama üzerinde özelliğini, ve gibi kullanıma sunar `NetTcpBinding` `NetNamedPipeBinding` . Diğer aktarımlar için, aktarım modunu ayarlamak üzere özel bir bağlama oluşturmanız gerekir.  
  
 Örnekteki aşağıdaki yapılandırma kodu, `TransferMode` özelliği, `basicHttpBinding` ve özel bir http bağlamasındaki akış olarak ayarlamayı gösterir:  
  
```xml  
<!-- An example basicHttpBinding using streaming. -->  
<basicHttpBinding>  
  <binding name="HttpStreaming" maxReceivedMessageSize="67108864"  
           transferMode="Streamed"/>  
</basicHttpBinding>  
<!-- An example customBinding using HTTP and streaming.-->  
<customBinding>  
  <binding name="Soap12">  
    <textMessageEncoding messageVersion="Soap12WSAddressing10" />  
    <httpTransport transferMode="Streamed"  
                   maxReceivedMessageSize="67108864"/>  
  </binding>  
</customBinding>  
```  
  
 ' I ' a ayarlamaya ek olarak, `transferMode` `Streamed` önceki yapılandırma kodu, `maxReceivedMessageSize` 64 MB olarak ayarlanır. Bir savunma mekanizması olarak, `maxReceivedMessageSize` alma sırasında izin verilen en fazla ileti boyutuna bir üst sınır koyar. Varsayılan değer, `maxReceivedMessageSize` genellikle akış senaryolarında çok düşük olan 64 KB 'tır.  
  
## <a name="processing-data-as-it-is-streamed"></a>Akış sırasında verileri işleme  

 İşlemler `GetStream` `UploadStream` ve `EchoStream` tümü doğrudan bir dosyadan veri göndermeye veya alınan verileri doğrudan bir dosyaya kaydetmeye yöneliktir. Ancak bazı durumlarda, büyük miktarlarda veri gönderilmesi veya alınması ve verilerin gönderildiği veya alındığı şekilde öbeklerinde bazı işlemler gerçekleştirme gereksinimi vardır. Bu tür senaryoları ele almanın bir yolu, <xref:System.IO.Stream> verileri okunan veya yazıldığı gibi işleyen özel bir akış (öğesinden türetilen bir sınıf) yazmak. `GetReversedStream`İşlem ve `ReverseStream` sınıf buna bir örnektir.  
  
 `GetReversedStream` Yeni bir örneğini oluşturur ve döndürür `ReverseStream` . Bu nesneden sistem okuduğu için gerçek işlem gerçekleşir `ReverseStream` . `ReverseStream.Read`Uygulama, temel alınan dosyadaki bir bayt öbeğini okur, bunları tersine çevirir ve ters bayt döndürür. Bu, tüm dosya içeriğini tersine döndürmez; tek seferde bir bayt öbeğini tersine çevirir. Bu, içerik okunmakta veya akışa yazılırken akış işlemeyi nasıl gerçekleştirebileceğini gösteren bir örnektir.  
  
```csharp
class ReverseStream : Stream  
{  
  
    FileStream inStream;  
    internal ReverseStream(string filePath)  
    {  
        //Opens the file and places a StreamReader around it.  
        inStream = File.OpenRead(filePath);  
    }  
  
    // Other methods removed for brevity.  
  
    public override int Read(byte[] buffer, int offset, int count)  
    {  
        int countRead=inStream.Read(buffer, offset,count);  
        ReverseBuffer(buffer, offset, countRead);  
        return countRead;  
    }  
  
    public override void Close()  
    {  
        inStream.Close();  
        base.Close();  
    }  
    protected override void Dispose(bool disposing)  
    {  
        inStream.Dispose();  
        base.Dispose(disposing);  
    }  
    void ReverseBuffer(byte[] buffer, int offset, int count)  
    {  
        int i, j;  
        for (i = offset, j = offset + count - 1; i < j; i++, j--)  
        {  
            byte currenti = buffer[i];  
            buffer[i] = buffer[j];  
            buffer[j] = currenti;  
        }  
  
    }  
}  
```  
  
## <a name="running-the-sample"></a>Örnek çalıştırma  

 Örneği çalıştırmak için, önce bu belgenin sonundaki yönergeleri izleyerek hem hizmeti hem de istemciyi derleyin. Ardından hizmeti ve istemciyi iki farklı konsol penceresinde başlatın. İstemci başladığında, hizmet hazırlanıyor, ENTER tuşuna basmanız bekler. İstemci daha sonra yöntemleri `GetStream()` `UploadStream()` ve `GetReversedStream()` ilk olarak http üzerinden ve daha sonra TCP üzerinden çağırır. Aşağıda, istemciden gelen örnek çıktıyı izleyen bir örnek çıktı verilmiştir:  
  
 Hizmet çıkışı:  
  
```console  
The streaming service is ready.  
Press <ENTER> to terminate service.  
  
Saving to file D:\...\uploadedfile  
......................  
File D:\...\uploadedfile saved  
Saving to file D:\...\uploadedfile  
...............  
File D:\...\uploadedfile saved  
```  
  
 İstemci çıkışı:  
  
```console  
Press <ENTER> when service is ready  
------ Using HTTP ------
Calling GetStream()  
Saving to file D:\...\clientfile  
......................  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
Calling UploadStream()  
Calling GetReversedStream()  
Saving to file D:\...\clientfile  
......................  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
------ Using Custom HTTP ------  
Calling GetStream()  
Saving to file D:\...\clientfile  
...............  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
Calling UploadStream()  
Calling GetReversedStream()  
Saving to file D:\...\clientfile  
...............  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!NOTE]
> Bu örneğe yönelik yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanıyorsanız, istemci yapılandırmasındaki uç nokta adını istemci koduyla eşleşecek şekilde değiştirdiğinizden emin olun.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
