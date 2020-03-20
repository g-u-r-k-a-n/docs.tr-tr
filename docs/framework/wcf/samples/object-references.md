---
title: Nesne Başvuruları
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: 5eb842e1bff9ba60074379fde5ef3d0597f2184e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183455"
---
# <a name="object-references"></a><span data-ttu-id="5e344-102">Nesne Başvuruları</span><span class="sxs-lookup"><span data-stu-id="5e344-102">Object References</span></span>
<span data-ttu-id="5e344-103">Bu örnek, sunucu ve istemci arasında başvurular tarafından nesnelerin nasıl geçirilmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5e344-103">This sample demonstrates how to pass objects by references between server and client.</span></span> <span data-ttu-id="5e344-104">Örnek simüle *sosyal ağlar*kullanır.</span><span class="sxs-lookup"><span data-stu-id="5e344-104">The sample uses simulated *social networks*.</span></span> <span data-ttu-id="5e344-105">Bir sosyal ağ, `Person` her arkadaşınızın kendi arkadaş listesiyle `Person` sınıfın bir örneği olduğu bir arkadaş listesi içeren bir sınıftan oluşur.</span><span class="sxs-lookup"><span data-stu-id="5e344-105">A social network consists of a `Person` class that contains a list of friends in which each friend is an instance of the `Person` class, with its own list of friends.</span></span> <span data-ttu-id="5e344-106">Bu nesnelerin bir grafik oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5e344-106">This creates a graph of objects.</span></span> <span data-ttu-id="5e344-107">Hizmet, bu sosyal ağlardaki işlemleri ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="5e344-107">The service exposes operations on these social networks.</span></span>  
  
 <span data-ttu-id="5e344-108">Bu örnekte, hizmet Internet Information Services (IIS) tarafından barındırılır ve istemci bir konsol uygulamasıdır (.exe).</span><span class="sxs-lookup"><span data-stu-id="5e344-108">In this sample, the service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5e344-109">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="5e344-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="5e344-110">Hizmet</span><span class="sxs-lookup"><span data-stu-id="5e344-110">Service</span></span>  
 <span data-ttu-id="5e344-111">Sınıf, `Person` <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> alan bir başvuru türü olarak `true` bildirmek için ayarlanmış olan öznitelik uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5e344-111">The `Person` class has the <xref:System.Runtime.Serialization.DataContractAttribute> attribute applied, with the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> field set to `true` to declare it as a reference type.</span></span> <span data-ttu-id="5e344-112">Tüm özellikler <xref:System.Runtime.Serialization.DataMemberAttribute> uygulanan öznitelik vardır.</span><span class="sxs-lookup"><span data-stu-id="5e344-112">All properties have the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute applied.</span></span>  
  
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
  
 <span data-ttu-id="5e344-113">İşlem `GetPeopleInNetwork` bir tür `Person` parametresi alır ve ağdaki tüm kişileri döndürür; yani, listedeki `friends` tüm insanlar, arkadaşının arkadaşları, ve saire, kopyaları olmadan.</span><span class="sxs-lookup"><span data-stu-id="5e344-113">The `GetPeopleInNetwork` operation takes a parameter of type `Person` and returns all the people in the network; that is, all the people in the `friends` list, the friend's friends, and so on, without duplicates.</span></span>  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 <span data-ttu-id="5e344-114">İşlem, `GetMutualFriends` bir tür `Person` parametresi alır ve listedeki bu kişiyi `friends` de listesinde bulunan tüm arkadaşları döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e344-114">The `GetMutualFriends` operation takes a parameter of type `Person` and returns all the friends in the list who also have this person in their `friends` list.</span></span>  
  
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
  
 <span data-ttu-id="5e344-115">İşlem `GetCommonFriends` türü `Person`bir liste alır.</span><span class="sxs-lookup"><span data-stu-id="5e344-115">The `GetCommonFriends` operation takes a list of type `Person`.</span></span> <span data-ttu-id="5e344-116">Listede iki `Person` nesne olması bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="5e344-116">The list is expected to have two `Person` objects in it.</span></span> <span data-ttu-id="5e344-117">İşlem, giriş listesindeki her iki `Person` `friends` `Person` nesnenin listesinde yer alan nesnelerin listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e344-117">The operation returns a list of `Person` objects that are in the `friends` lists of both `Person` objects in the input list.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="5e344-118">İstemci</span><span class="sxs-lookup"><span data-stu-id="5e344-118">Client</span></span>  
 <span data-ttu-id="5e344-119">İstemci proxy Visual Studio **Hizmet Başvurusu Ekle** özelliği kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5e344-119">The client proxy is created using the **Add Service Reference** feature of Visual Studio.</span></span>  
  
 <span data-ttu-id="5e344-120">Beş `Person` nesneden oluşan bir sosyal ağ oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5e344-120">A social network that consists of five `Person` objects is created.</span></span> <span data-ttu-id="5e344-121">İstemci, hizmetteki üç yöntemin her birini çağırır.</span><span class="sxs-lookup"><span data-stu-id="5e344-121">The client calls each of the three methods in the service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5e344-122">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="5e344-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5e344-123">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="5e344-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5e344-124">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="5e344-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5e344-125">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="5e344-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5e344-126">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="5e344-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5e344-127">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5e344-127">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5e344-128">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="5e344-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5e344-129">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="5e344-129">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a><span data-ttu-id="5e344-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e344-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [<span data-ttu-id="5e344-131">Birlikte Çalışabilir Nesne Başvuruları</span><span class="sxs-lookup"><span data-stu-id="5e344-131">Interoperable Object References</span></span>](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
