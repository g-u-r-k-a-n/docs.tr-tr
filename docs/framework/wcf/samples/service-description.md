---
title: Hizmet Açıklaması
ms.date: 03/30/2017
ms.assetid: 7034b5d6-d608-45f3-b57d-ec135f83ff24
ms.openlocfilehash: a087b595a426e1485e9990a5fa38e49ae940ffcb
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716288"
---
# <a name="service-description"></a>Hizmet Açıklaması
Hizmet açıklaması örneği, bir hizmetin çalışma zamanında hizmet açıklaması bilgilerini nasıl alabileceğinizi gösterir. Örnek, hizmet hakkında açıklayıcı bilgiler döndürmek için tanımlanmış ek bir hizmet işlemi ile [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır. Döndürülen bilgiler, hizmetin temel adreslerini ve uç noktalarını listeler. Hizmet, bu bilgileri <xref:System.ServiceModel.OperationContext>, <xref:System.ServiceModel.ServiceHost>ve <xref:System.ServiceModel.Description.ServiceDescription> sınıflarını kullanarak sağlar.  
  
 Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Bu örnek, `IServiceDescriptionCalculator`adlı Hesaplayıcı sözleşmesinin değiştirilmiş bir sürümüne sahiptir. Sözleşme, istemciye yönelik temel adresi veya adresleri, hizmet uç noktasını veya bitiş noktalarını tanımlayan, istemciye çok satırlı bir dize döndüren `GetServiceDescriptionInfo` adlı ek bir hizmet işlemi tanımlar.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IServiceDescriptionCalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    int Divide(int n1, int n2);  
    [OperationContract]  
    string GetServiceDescriptionInfo();  
}  
```  
  
 `GetServiceDescriptionInfo` için uygulama kodu, hizmet uç noktalarını listelemek için <xref:System.ServiceModel.Description.ServiceDescription> kullanır. Hizmet uç noktalarında göreli adresler olabileceğinden, önce hizmetin temel adreslerini listeler. Bu bilgilerin tümünü almak için, kod <xref:System.ServiceModel.OperationContext.Current%2A>kullanarak işlem bağlamını edinir. <xref:System.ServiceModel.ServiceHost> ve <xref:System.ServiceModel.Description.ServiceDescription> nesnesi işlem bağlamından alınır. Hizmetin temel uç noktalarını listelemek için, kod hizmet ana bilgisayarının <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> koleksiyonu üzerinden yinelenir. Hizmetin hizmet uç noktalarını listelemek için, kod hizmet açıklamasının uç noktalar koleksiyonu üzerinden yinelenir.  
  
```csharp
public string GetServiceDescriptionInfo()  
{  
    string info = "";  
    OperationContext operationContext = OperationContext.Current;  
    ServiceHost host = (ServiceHost)operationContext.Host;  
    ServiceDescription desc = host.Description;  
    // Enumerate the base addresses in the service host.  
    info += "Base addresses:\n";  
    foreach (Uri uri in host.BaseAddresses)  
    {  
        info += "    " + uri + "\n";  
    }  
    // Enumerate the service endpoints in the service description.  
    info += "Service endpoints:\n";  
    foreach (ServiceEndpoint endpoint in desc.Endpoints)  
    {  
        info += "    Address:  " + endpoint.Address + "\n";  
        info += "    Binding:  " + endpoint.Binding.Name + "\n";  
        info += "    Contract: " + endpoint.Contract.Name + "\n";  
    }  
     return info;  
}  
```  
  
 Örneği çalıştırdığınızda, hesaplayıcı işlemlerini ve sonra `GetServiceDescriptionInfo` işlemi tarafından döndürülen hizmet bilgilerini görürsünüz. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
Divide(22,7) = 3  
GetServiceDescriptionInfo  
Base addresses:  
    http://<machine-name>/ServiceModelSamples/service.svc  
    https://<machine-name>/ServiceModelSamples/service.svc  
Service endpoints:  
    Address:  http://<machine-name>/ServiceModelSamples/service.svc  
    Binding:  WSHttpBinding  
    Contract: IServiceDescriptionCalculator  
    Address:  http://<machine-name>/ServiceModelSamples/service.svc/mex  
    Binding:  MetadataExchangeHttpBinding  
    Contract: IMetadataExchange  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ServiceDescription`  
