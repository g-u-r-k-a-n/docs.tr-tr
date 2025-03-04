---
description: 'Hakkında daha fazla bilgi edinin: hata Işleme ve raporlama üzerinde genişletme denetimi'
title: Hata İşleme ve Bildirme Denetimini Genişletme
ms.date: 03/30/2017
ms.assetid: 45f996a7-fa00-45cb-9d6f-b368f5778aaa
ms.openlocfilehash: 9b9dd7761757235b2381fce575021aca2be404f2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752385"
---
# <a name="extending-control-over-error-handling-and-reporting"></a>Hata İşleme ve Bildirme Denetimini Genişletme

Bu örnek, arabirimi kullanarak bir Windows Communication Foundation (WCF) hizmetinde hata işleme ve hata raporlama üzerinde denetimin nasıl genişletileceğini gösterir <xref:System.ServiceModel.Dispatcher.IErrorHandler> . Örnek, hataları işlemek için hizmete eklenen bazı ek kod ile [çalışmaya](getting-started-sample.md) başlama konusunda temel alır. İstemci birkaç hata koşulu zorlar. Hizmet hataları karşılar ve bunları bir dosyada günlüğe kaydeder.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Hizmetler hataları ele geçirebilir, işleme gerçekleştirebilir ve arabirim kullanarak hataların nasıl raporlanacağı etkisini etkileyebilir <xref:System.ServiceModel.Dispatcher.IErrorHandler> . Arabirimin uygulanıuygulanabilen iki yöntemi vardır: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> ve <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> . <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29>Yöntemi, bir özel duruma yanıt olarak oluşturulan bir hata iletisini eklemenize, değiştirmenize veya gizlemesine olanak sağlar. <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>Yöntemi hata işlemenin hata durumunda gerçekleşmesini sağlar ve ek hata işlemenin çalıştırılıp çalıştırılmadığını denetler.  
  
 Bu örnekte, `CalculatorErrorHandler` türü <xref:System.ServiceModel.Dispatcher.IErrorHandler> arabirimini uygular. İçinde  
  
 <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> yöntemi, `CalculatorErrorHandler` hata günlüğünü c:\logs. içindeki bir Error.txt metin dosyasına yazar. Örneğin hatayı günlüğe kaydettiğine ve bunu göstermez ve istemciye geri raporlanmasını sağlar.  
  
```csharp
public class CalculatorErrorHandler : IErrorHandler
{
    // Provide a fault. The Message fault parameter can be replaced, or set to
    // null to suppress reporting a fault.

    public void ProvideFault(Exception error, MessageVersion version, ref Message fault)
    {
    }

    // HandleError. Log an error, then allow the error to be handled as usual.
    // Return true if the error is considered as already handled

    public bool HandleError(Exception error)
    {
        using (TextWriter tw = File.AppendText(@"c:\logs\error.txt"))
        {
            if (error != null)
            {
                tw.WriteLine("Exception: " + error.GetType().Name + " - " + error.Message);
            }
            tw.Close();
        }
        return true;
    }
}  
```  
  
 `ErrorBehaviorAttribute`Bir hizmet ile bir hata işleyicisini kaydetme mekanizması olarak mevcuttur. Bu öznitelik tek bir tür parametresi alır. Bu tür <xref:System.ServiceModel.Dispatcher.IErrorHandler> arabirimini uygulamalıdır ve genel, boş bir oluşturucuya sahip olmalıdır. Özniteliği daha sonra bu hata işleyicisi türünün bir örneğini başlatır ve hizmete kurar. Bunu, <xref:System.ServiceModel.Description.IServiceBehavior> arabirimini uygulayarak ve sonra <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> Hata işleyicisinin örneklerine eklemek için yöntemini kullanarak yapar.  
  
```csharp
// This attribute can be used to install a custom error handler for a service.  
public class ErrorBehaviorAttribute : Attribute, IServiceBehavior  
{  
    Type errorHandlerType;  
  
    public ErrorBehaviorAttribute(Type errorHandlerType)  
    {  
        this.errorHandlerType = errorHandlerType;  
    }  
  
    void IServiceBehavior.Validate(ServiceDescription description, ServiceHostBase serviceHostBase)  
    {  
    }  
  
    void IServiceBehavior.AddBindingParameters(ServiceDescription description, ServiceHostBase serviceHostBase, System.Collections.ObjectModel.Collection<ServiceEndpoint> endpoints, BindingParameterCollection parameters)  
    {  
    }  
  
    void IServiceBehavior.ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
    {  
        IErrorHandler errorHandler;  
  
        try  
        {  
            errorHandler = (IErrorHandler)Activator.CreateInstance(errorHandlerType);  
        }  
        catch (MissingMethodException e)  
        {  
            throw new ArgumentException("The errorHandlerType specified in the ErrorBehaviorAttribute constructor must have a public empty constructor.", e);  
        }  
        catch (InvalidCastException e)  
        {  
            throw new ArgumentException("The errorHandlerType specified in the ErrorBehaviorAttribute constructor must implement System.ServiceModel.Dispatcher.IErrorHandler.", e);  
        }  
  
        foreach (ChannelDispatcherBase channelDispatcherBase in serviceHostBase.ChannelDispatchers)  
        {  
            ChannelDispatcher channelDispatcher = channelDispatcherBase as ChannelDispatcher;  
            channelDispatcher.ErrorHandlers.Add(errorHandler);  
        }
    }  
}  
```  
  
 Örnek, bir Hesaplayıcı hizmeti uygular. İstemci, geçersiz değerlere sahip parametreler sağlayarak hizmette iki hatanın oluşmasına neden olur. , `CalculatorErrorHandler` <xref:System.ServiceModel.Dispatcher.IErrorHandler> Hataları yerel bir dosyaya kaydetmek için arabirimini kullanır ve ardından istemciye geri bildirilmelerini sağlar. İstemci, sıfıra bölme ve bağımsız değişken olmayan bir koşula zorlar.  
  
```csharp
try
{  
    Console.WriteLine("Forcing an error in Divide");  
    // Call the Divide service operation - trigger a divide by 0 error.  
    value1 = 22;  
    value2 = 0;  
    result = proxy.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
}  
catch (FaultException e)  
{  
    Console.WriteLine("FaultException: " + e.GetType().Name + " - " + e.Message);  
}  
catch (Exception e)  
{  
    Console.WriteLine("Exception: " + e.GetType().Name + " - " + e.Message);  
}  
```  
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. Sıfıra göre bölme ve bağımsız değişken dışı koşulların hata olarak raporlanmakta olduğunu görürsünüz. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
Forcing an error in Divide  
FaultException: FaultException - Invalid Argument: The second argument must not be zero.  
Forcing an error in Factorial  
FaultException: FaultException - Invalid Argument: The argument must be greater than zero.  
  
Press <ENTER> to terminate client.  
```  
  
 Dosya c:\logs\errors.txt, hizmetle ilgili hatalar hakkında günlüğe kaydedilen bilgileri içerir. Hizmetin dizine yazması için hizmetin çalıştığı işlemin (genellikle ASP.NET veya ağ hizmeti) dizine yazma iznine sahip olduğundan emin olun.  
  
```txt
Fault: Reason = Invalid Argument: The second argument must not be zero.  
Fault: Reason = Invalid Argument: The argument must be greater than zero.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.  
  
3. error.txt dosyası için c:\logs. dizinini oluşturduğunuzdan emin olun. Veya ' de kullanılan dosya adını değiştirebilirsiniz `CalculatorErrorHandler.HandleError` .  
  
4. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\ErrorHandling`  
