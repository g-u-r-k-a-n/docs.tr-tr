---
title: Nesne Başvuruları
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: bc9c318fc0e05f384a00df7cd1436a138315d880
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714675"
---
# <a name="object-references"></a>Nesne Başvuruları
Bu örnek, nesneleri sunucu ve istemci arasında başvuruya göre nasıl geçileceğini gösterir. Örnek, sanal *sosyal ağları*kullanır. Sosyal ağ, her arkadaşın kendi arkadaş listesi ile `Person` sınıfının bir örneği olduğu arkadaş listesini içeren `Person` sınıfından oluşur. Bu, nesnelerin bir grafiğini oluşturur. Hizmet, bu sosyal ağlarda işlemleri kullanıma sunar.  
  
 Bu örnekte, hizmet Internet Information Services (IIS) tarafından barındırılır ve istemci bir konsol uygulaması (. exe).  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
## <a name="service"></a>Hizmet  
 `Person` sınıfında, <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> alanı bir başvuru türü olarak bildirmek için `true` olarak ayarlanmış <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği uygulanır. Tüm özelliklerde <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği uygulandı.  
  
```csharp
[DataContract(IsReference=true)]  
public class Person  
{  
    string name;  
    string location;  
    string gender;  
    int age;  
    List<Person> friends;  
    [DataMember()]  
    public string Name  
    {  
        get { return name; }  
        set { name = value; }  
    }  
    [DataMember()]  
    public string Location  
    {  
        get { return location; }  
        set { location = value; }  
    }  
    [DataMember()]  
    public string Gender  
    {  
        get { return gender; }  
        set { gender = value; }  
    }  
…  
}  
```  
  
 `GetPeopleInNetwork` işlemi, `Person` türünde bir parametre alır ve ağdaki tüm kişileri döndürür; diğer bir deyişle, `friends` listesindeki tüm kişiler, arkadaşınızın arkadaşları, vb., yinelemeler olmadan.  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 `GetMutualFriends` işlem, `Person` türünde bir parametre alır ve bu kişinin `friends` listesinde de bulunan tüm arkadaşlarınızı geri döndürür.  
  
```csharp
public List<Person> GetMutualFriends(Person p)  
{  
    List<Person> mutual = new List<Person>();  
    foreach (Person friend in p.Friends)  
    {  
        if (friend.Friends.Contains(p))  
            mutual.Add(friend);  
    }  
    return mutual;  
}  
```  
  
 `GetCommonFriends` işlem `Person`türünün bir listesini alır. Listenin içinde iki `Person` nesne olması beklenir. İşlem, giriş listesindeki `Person` nesnelerinin `friends` listelerinde bulunan `Person` nesnelerinin bir listesini döndürür.  
  
```csharp
public List<Person> GetCommonFriends(List<Person> people)  
{  
    List<Person> common = new List<Person>();  
    foreach (Person friend in people[0].Friends)  
        if (people[1].Friends.Contains(friend))  
            common.Add(friend);  
    return common;  
}  
```  
  
## <a name="client"></a>İstemci  
 İstemci proxy 'si, Visual Studio 'nun **hizmet başvurusu Ekle** özelliği kullanılarak oluşturulur.  
  
 Beş `Person` nesnesinden oluşan bir sosyal ağ oluşturulur. İstemci, hizmette üç yöntemin her birini çağırır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [Birlikte Çalışabilir Nesne Başvuruları](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
