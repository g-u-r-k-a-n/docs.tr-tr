---
description: 'Hakkında daha fazla bilgi edinin: veri sözleşme Çözümleyicisi kullanma'
title: Veri Sözleşmesi Çözücü Kullanma
ms.date: 03/30/2017
ms.assetid: 2e68a16c-36f0-4df4-b763-32021bff2b89
ms.openlocfilehash: 89571c63b9135f164e0b687251798e3b67153b8e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632301"
---
# <a name="using-a-data-contract-resolver"></a><span data-ttu-id="969dd-103">Veri Sözleşmesi Çözücü Kullanma</span><span class="sxs-lookup"><span data-stu-id="969dd-103">Using a Data Contract Resolver</span></span>

<span data-ttu-id="969dd-104">Bir veri anlaşması Çözümleyicisi, bilinen türleri dinamik olarak yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="969dd-104">A data contract resolver allows you to configure known types dynamically.</span></span> <span data-ttu-id="969dd-105">Bir veri sözleşmesinin beklenmediği bir tür serileştirildiğinde veya seri durumdan çıkarılırken bilinen türler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="969dd-105">Known types are required when serializing or deserializing a type not expected by a data contract.</span></span> <span data-ttu-id="969dd-106">Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="969dd-106">For more information about known types, see [Data Contract Known Types](data-contract-known-types.md).</span></span> <span data-ttu-id="969dd-107">Bilinen türler normalde statik olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="969dd-107">Known types are normally specified statically.</span></span> <span data-ttu-id="969dd-108">Bu durum, işlem uygulanırken bir işlemin alabileceği tüm olası türleri bilmeniz gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="969dd-108">This means you would have to know all the possible types an operation may receive while implementing the operation.</span></span> <span data-ttu-id="969dd-109">Bu, doğru olmayan ve bilinen türleri dinamik olarak belirleyebilen senaryolar vardır.</span><span class="sxs-lookup"><span data-stu-id="969dd-109">There are scenarios in which this is not true and being able to specify known types dynamically is important.</span></span>  
  
## <a name="creating-a-data-contract-resolver"></a><span data-ttu-id="969dd-110">Veri anlaşması Çözümleyicisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="969dd-110">Creating a Data Contract Resolver</span></span>  

 <span data-ttu-id="969dd-111">Bir veri anlaşması Çözümleyicisi oluşturmak, iki yöntem ve uygulamayı <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> içerir <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> .</span><span class="sxs-lookup"><span data-stu-id="969dd-111">Creating a data contract resolver involves implementing two methods, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> and <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>.</span></span> <span data-ttu-id="969dd-112">Bu iki yöntem sırasıyla serileştirme ve seri durumundan çıkarma sırasında kullanılan geri çağırmaları uygular.</span><span class="sxs-lookup"><span data-stu-id="969dd-112">These two methods implement callbacks that are used during serialization and deserialization, respectively.</span></span> <span data-ttu-id="969dd-113"><xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A>Yöntem serileştirme sırasında çağrılır ve bir veri anlaşması türü alır ve bunu bir `xsi:type` ad ve ad alanına eşler.</span><span class="sxs-lookup"><span data-stu-id="969dd-113">The <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> method is invoked during serialization and takes a data contract type and maps it to an `xsi:type` name and namespace.</span></span> <span data-ttu-id="969dd-114"><xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>Yöntemi seri durumundan çıkarma sırasında çağrılır ve bir `xsi:type` ad ve ad alanı alır ve bunu bir veri anlaşması türü olarak çözer.</span><span class="sxs-lookup"><span data-stu-id="969dd-114">The <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> method is invoked during deserialization and takes an `xsi:type` name and namespace and resolves it to a data contract type.</span></span> <span data-ttu-id="969dd-115">Bu yöntemlerin her ikisinde de, `knownTypeResolver` uygulamanızda varsayılan olarak bilinen tür çözümleyici 'yi kullanmak için kullanılabilecek bir parametre vardır.</span><span class="sxs-lookup"><span data-stu-id="969dd-115">Both of these methods have a `knownTypeResolver` parameter that can be used to use the default known type resolver in your implementation.</span></span>  
  
 <span data-ttu-id="969dd-116">Aşağıdaki örnek, bir <xref:System.Runtime.Serialization.DataContractResolver> `Customer` veri anlaşması türünden türetilmiş adlı bir veri sözleşmesi türüne ve bir eşlemenin nasıl uygulanacağını gösterir `Person` .</span><span class="sxs-lookup"><span data-stu-id="969dd-116">The following example shows how to implement a <xref:System.Runtime.Serialization.DataContractResolver> to map to and from a data contract type named `Customer` derived from a data contract type `Person`.</span></span>  
  
```csharp  
public class MyCustomerResolver : DataContractResolver  
{  
    public override bool TryResolveType(Type dataContractType, Type declaredType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)  
    {  
        if (dataContractType == typeof(Customer))  
        {  
            XmlDictionary dictionary = new XmlDictionary();  
            typeName = dictionary.Add("SomeCustomer");  
            typeNamespace = dictionary.Add("http://tempuri.com");  
            return true;  
        }  
        else  
        {  
            return knownTypeResolver.TryResolveType(dataContractType, declaredType, null, out typeName, out typeNamespace);  
        }  
    }  
  
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)  
    {  
        if (typeName == "SomeCustomer" && typeNamespace == "http://tempuri.com")  
        {  
            return typeof(Customer);  
        }  
        else  
        {  
            return knownTypeResolver.ResolveName(typeName, typeNamespace, null);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="969dd-117">Bir tanımladıktan sonra, <xref:System.Runtime.Serialization.DataContractResolver> <xref:System.Runtime.Serialization.DataContractSerializer> Aşağıdaki örnekte gösterildiği gibi onu oluşturucuya geçirerek kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="969dd-117">Once you have defined a <xref:System.Runtime.Serialization.DataContractResolver> you can use it by passing it to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor as shown in the following example.</span></span>  
  
```csharp
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 <span data-ttu-id="969dd-118"><xref:System.Runtime.Serialization.DataContractResolver> <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType> Aşağıdaki örnekte gösterildiği gibi, veya yöntemlerine bir çağrısında belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="969dd-118">You can specify a <xref:System.Runtime.Serialization.DataContractResolver> in a call to the <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> or <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType> methods, as shown in the following example.</span></span>  
  
```csharp
MemoryStream ms = new MemoryStream();  
DataContractSerializer serializer = new DataContractSerializer(typeof(Customer));  
XmlDictionaryWriter writer = XmlDictionaryWriter.CreateDictionaryWriter(XmlWriter.Create(ms));  
serializer.WriteObject(writer, new Customer(), new MyCustomerResolver());  
writer.Flush();  
ms.Position = 0;  
Console.WriteLine(((Customer)serializer.ReadObject(XmlDictionaryReader.CreateDictionaryReader(XmlReader.Create(ms)), false, new MyCustomerResolver()));  
```  
  
 <span data-ttu-id="969dd-119">Ya da bunu, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> Aşağıdaki örnekte gösterildiği gibi ' de ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="969dd-119">Or you can set it on the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> as shown in the following example.</span></span>  
  
```csharp
ServiceHost host = new ServiceHost(typeof(MyService));  
  
ContractDescription cd = host.Description.Endpoints[0].Contract;  
OperationDescription myOperationDescription = cd.Operations.Find("Echo");  
  
DataContractSerializerOperationBehavior serializerBehavior = myOperationDescription.Behaviors.Find<DataContractSerializerOperationBehavior>();  
if (serializerBehavior == null)  
{  
    serializerBehavior = new DataContractSerializerOperationBehavior(myOperationDescription);  
    myOperationDescription.Behaviors.Add(serializerBehavior);  
}  
  
SerializerBehavior.DataContractResolver = new MyCustomerResolver();  
```  
  
 <span data-ttu-id="969dd-120">Bir hizmete uygulanabilen bir öznitelik uygulayarak bir veri anlaşması çözümleyicisini bildirimli olarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="969dd-120">You can declaratively specify a data contract resolver by implementing an attribute that can be applied to a service.</span></span>  <span data-ttu-id="969dd-121">Daha fazla bilgi için bkz. [KnownAssemblyAttribute](../samples/knownassemblyattribute.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="969dd-121">For more information, see the [KnownAssemblyAttribute](../samples/knownassemblyattribute.md) sample.</span></span> <span data-ttu-id="969dd-122">Bu örnek, hizmetin davranışına özel bir veri sözleşme Çözümleyicisi ekleyen "KnownAssembly" adlı bir öznitelik uygular.</span><span class="sxs-lookup"><span data-stu-id="969dd-122">This sample implements an attribute called "KnownAssembly" that adds a custom data contract resolver to the service’s behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="969dd-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="969dd-123">See also</span></span>

- [<span data-ttu-id="969dd-124">Veri Sözleşmesi Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="969dd-124">Data Contract Known Types</span></span>](data-contract-known-types.md)
- [<span data-ttu-id="969dd-125">DataContractSerializer Örneği</span><span class="sxs-lookup"><span data-stu-id="969dd-125">DataContractSerializer Sample</span></span>](../samples/datacontractserializer-sample.md)
- [<span data-ttu-id="969dd-126">KnownAssemblyAttribute</span><span class="sxs-lookup"><span data-stu-id="969dd-126">KnownAssemblyAttribute</span></span>](../samples/knownassemblyattribute.md)
