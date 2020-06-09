---
title: 'Nasıl yapılır: Meta Verileri Derlenmiş Hizmet Kodundan Dışarı Aktarmak için Svcutil.exe Kullanma'
ms.date: 03/30/2017
ms.assetid: 95d0aed3-16a2-4398-89bb-39418eeb7355
ms.openlocfilehash: 9acefdec63a6f518ead6cdbcb19ebc8c75609dd6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595368"
---
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a>Nasıl yapılır: Meta Verileri Derlenmiş Hizmet Kodundan Dışarı Aktarmak için Svcutil.exe Kullanma
Svcutil. exe, derlenmiş derlemelerde hizmetler, sözleşmeler ve veri türleri için meta verileri aşağıdaki gibi dışarı aktarabilir:  
  
- Svcutil. exe ' yi kullanarak bir derleme kümesine yönelik tüm derlenmiş hizmet sözleşmeleri için meta verileri dışarı aktarmak için, derlemeleri giriş parametreleri olarak belirtin. Bu, varsayılan davranıştır.  
  
- Svcutil. exe ' yi kullanarak derlenmiş bir hizmetin meta verilerini dışa aktarmak için, hizmet derlemesini veya derlemeleri giriş parametreleri olarak belirtin. `/serviceName`Dışarı aktarmak istediğiniz hizmetin yapılandırma adını belirtmek için seçeneğini kullanmanız gerekir. Svcutil. exe, belirtilen yürütülebilir derleme için yapılandırma dosyasını otomatik olarak yükler.  
  
- Bir derleme kümesi içindeki tüm veri anlaşması türlerini dışarı aktarmak için `/dataContractOnly` seçeneğini kullanın.  
  
> [!NOTE]
> `/reference`Herhangi bir bağımlı derlemeye dosya yollarını belirtmek için seçeneğini kullanın.  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a>Derlenmiş hizmet sözleşmeleri için meta verileri dışarı aktarmak için  
  
1. Hizmet sözleşmesi uygulamalarınızı bir veya daha fazla sınıf kitaplığı halinde derleyin. 1  
  
2. Derlenen derlemelerde Svcutil. exe ' yi çalıştırın.  
  
    > [!NOTE]
    > `/reference`Herhangi bir bağımlı derlemeye dosya yolunu belirtmek için anahtarını kullanmanız gerekebilir.  
  
    ```console
    svcutil.exe Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-a-compiled-service"></a>Derlenmiş bir hizmetin meta verilerini dışarı aktarmak için  
  
1. Hizmet uygulamanızı yürütülebilir bir derlemede derleyin.  
  
2. Hizmet yürütülebilir dosyanız için bir yapılandırma dosyası oluşturun ve bir hizmet yapılandırması ekleyin.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="MyService" >  
            <endpoint address="finder" contract="IPeopleFinder" binding="wsHttpBinding" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
3. `/serviceName`Hizmetin yapılandırma adını belirtmek için anahtarı kullanarak derlenmiş hizmet yürütülebilir dosyası üzerinde Svcutil. exe ' yi çalıştırın.  
  
    > [!NOTE]
    > `/reference`Herhangi bir bağımlı derlemeye dosya yolunu belirtmek için anahtarını kullanmanız gerekebilir.  
  
    ```console  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a>Derlenen veri sözleşmeleri için meta verileri dışarı aktarmak için  
  
1. Veri sözleşmesi uygulamalarınızı bir veya daha fazla sınıf kitaplığı halinde derleyin.  
  
2. `/dataContract`Veri sözleşmelerinin yalnızca meta verilerinin oluşturulması gerektiğini belirtmek için anahtarını kullanarak derlenmiş derlemelerde Svcutil. exe ' yi çalıştırın.  
  
    > [!NOTE]
    > `/reference`Herhangi bir bağımlı derlemeye dosya yolunu belirtmek için anahtarını kullanmanız gerekebilir.  
  
    ```console  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir basit hizmet uygulama ve yapılandırması için meta verilerin nasıl oluşturulacağını göstermektedir.  
  
 Hizmet sözleşmesinin meta verilerini dışarı aktarmak için.  
  
```console  
svcutil.exe Contracts.dll  
```  
  
 Veri sözleşmelerinin meta verilerini dışarı aktarmak için.  
  
```console  
svcutil.exe /dataContractOnly Contracts.dll  
```  
  
 Hizmet uygulamasının meta verilerini dışarı aktarmak için.  
  
```console  
svcutil.exe /serviceName:MyService Service.exe /reference:<path>/Contracts.dll  
```  
  
 , `<path>` Sözleşmelerin. dll yoludur.  
  
```csharp
// The following service contract and data contracts are compiled into
// Contracts.dll.  
[ServiceContract(ConfigurationName="IPeopleFinder")]  
public interface IPersonFinder  
{  
    [OperationContract]  
    Address GetAddress(Person s);  
}  
  
[DataContract]  
public class Person  
{  
    [DataMember]  
    public string firstName;  
    [DataMember]  
    public string lastName;  
    [DataMember]  
    public int age;  
}  
  
[DataContract]  
public class Address  
{  
    [DataMember]  
    public string city;  
    [DataMember]  
    public string state;  
    [DataMember]  
    public string street;  
    [DataMember]  
    public int zipCode;  
    [DataMember]  
    public Person person;  
}  
```

```csharp
// The following service implementation is compiled into Service.exe.
// This service uses the contracts specified in Contracts.dll.  
[ServiceBehavior(ConfigurationName = "MyService")]  
public class MyService : IPersonFinder  
{  
    public Address GetAddress(Person person)  
    {  
        Address address = new Address();  
        address.person = person;  
        return address;  
    }  
}  
```

```xml  
<!-- The following is the configuration file for Service.exe. -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="MyService">  
         <endpoint  address="finder"  
                    binding="basicHttpBinding"  
                    contract="IPeopleFinder"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Meta Verileri Dışarı ve İçeri Aktarma](exporting-and-importing-metadata.md)
