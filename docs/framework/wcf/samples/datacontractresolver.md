---
title: DataContractResolver
ms.date: 03/30/2017
ms.assetid: 6c200c02-bc14-4b8d-bbab-9da31185b805
ms.openlocfilehash: 6c04a055a5ce87ac285d05b086c22b900bc92145
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253654"
---
# <a name="datacontractresolver"></a><span data-ttu-id="4f794-102">DataContractResolver</span><span class="sxs-lookup"><span data-stu-id="4f794-102">DataContractResolver</span></span>

<span data-ttu-id="4f794-103">Bu örnek, serileştirme ve seri kaldırma işlemlerinin sınıfı kullanılarak nasıl özelleştirilebileceğini gösterir <xref:System.Runtime.Serialization.DataContractResolver> .</span><span class="sxs-lookup"><span data-stu-id="4f794-103">This sample demonstrates how the serialization and deserialization processes can be customized by using the <xref:System.Runtime.Serialization.DataContractResolver> class.</span></span> <span data-ttu-id="4f794-104">Bu örnek, serileştirme ve seri durumundan çıkarma sırasında CLR türlerini bir xsi: tür gösterimine eşlemek için bir DataContractResolver 'ın nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f794-104">This sample shows how to use a DataContractResolver to map CLR types to and from an xsi:type representation during serialization and deserialization.</span></span>

## <a name="sample-details"></a><span data-ttu-id="4f794-105">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="4f794-105">Sample Details</span></span>

 <span data-ttu-id="4f794-106">Örnek, aşağıdaki CLR türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4f794-106">The sample defines the following CLR types.</span></span>

```csharp
using System;
using System.Runtime.Serialization;

namespace Types
{
    [DataContract]
    public class Customer
    {
        [DataMember]
        public string Name { get; set; }
    }

    [DataContract]
    public class VIPCustomer : Customer
    {
        [DataMember]
        public string VipInfo { get; set; }
    }

    [DataContract]
    public class RegularCustomer : Customer
    {
    }

    [DataContract]
    public class PreferredVIPCustomer : VIPCustomer
    {
    }
}
```

 <span data-ttu-id="4f794-107">Örnek, derlemeyi yükler, bu türlerin her birini ayıklar ve sonra bunları seri hale getirir ve onları yeniden sıralar.</span><span class="sxs-lookup"><span data-stu-id="4f794-107">The sample loads the assembly, extracts each of these types, and then serializes and deserializes them.</span></span> <span data-ttu-id="4f794-108">, <xref:System.Runtime.Serialization.DataContractResolver> <xref:System.Runtime.Serialization.DataContractResolver> <xref:System.Runtime.Serialization.DataContractSerializer> Aşağıdaki örnekte gösterildiği gibi, türetilmiş sınıfın bir örneğini oluşturucuya geçirerek serileştirme işlemine takılır.</span><span class="sxs-lookup"><span data-stu-id="4f794-108">The <xref:System.Runtime.Serialization.DataContractResolver> is plugged into the serialization process by passing an instance of the <xref:System.Runtime.Serialization.DataContractResolver>-derived class to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor, as shown in the following example.</span></span>

```csharp
this.serializer = new DataContractSerializer(typeof(Object), null, int.MaxValue, false, true, null, new MyDataContractResolver(assembly));
```

 <span data-ttu-id="4f794-109">Örnek, aşağıdaki kod örneğinde gösterildiği gibi CLR türlerini seri hale getirir.</span><span class="sxs-lookup"><span data-stu-id="4f794-109">The sample then serializes the CLR types as shown in the following code example.</span></span>

```csharp
Assembly assembly = Assembly.Load(new AssemblyName("Types"));

public void serialize(Type type)
{
    Object instance = Activator.CreateInstance(type);

    Console.WriteLine("----------------------------------------");
    Console.WriteLine();
    Console.WriteLine("Serializing type: {0}", type.Name);
    Console.WriteLine();
    this.buffer = new StringBuilder();
    using (XmlWriter xmlWriter = XmlWriter.Create(this.buffer))
    {
        try
        {
            this.serializer.WriteObject(xmlWriter, instance);
        }
        catch (SerializationException error)
        {
            Console.WriteLine(error.ToString());
        }
    }
    Console.WriteLine(this.buffer.ToString());
}
```

 <span data-ttu-id="4f794-110">Örnek, aşağıdaki kod örneğinde gösterildiği gibi xsi: Types öğesini de kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4f794-110">The sample then deserializes the xsi:types as shown in the following code example.</span></span>

```csharp
public void deserialize(Type type)
{
    Console.WriteLine();
    Console.WriteLine("Deserializing type: {0}", type.Name);
    Console.WriteLine();
    using (XmlReader xmlReader = XmlReader.Create(new StringReader(this.buffer.ToString())))
    {
        Object obj = this.serializer.ReadObject(xmlReader);
    }
}
```

 <span data-ttu-id="4f794-111">Özel, <xref:System.Runtime.Serialization.DataContractResolver> oluşturucuya geçirildiğinden, <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> SERILEŞTIRME sırasında bir clr türünü eşdeğer olarak eşlemek için çağrılır `xsi:type` .</span><span class="sxs-lookup"><span data-stu-id="4f794-111">Since the custom <xref:System.Runtime.Serialization.DataContractResolver> is passed in to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor, the <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> is called during serialization to map a CLR type to an equivalent `xsi:type`.</span></span> <span data-ttu-id="4f794-112">Benzer şekilde, <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> `xsi:type` BIR eşdeğer clr türüne eşlemek için seri durumundan çıkarma sırasında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="4f794-112">Similarly the <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> is called during deserialization to map the `xsi:type` to an equivalent CLR type.</span></span> <span data-ttu-id="4f794-113">Bu örnekte, <xref:System.Runtime.Serialization.DataContractResolver> Aşağıdaki örnekte gösterildiği gibi tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4f794-113">In this sample, the <xref:System.Runtime.Serialization.DataContractResolver> is defined as shown in the following example.</span></span>

 <span data-ttu-id="4f794-114">Aşağıdaki kod örneği, öğesinden türetilen bir sınıftır <xref:System.Runtime.Serialization.DataContractResolver> .</span><span class="sxs-lookup"><span data-stu-id="4f794-114">The following code example is a class deriving from <xref:System.Runtime.Serialization.DataContractResolver>.</span></span>

```csharp
class MyDataContractResolver : DataContractResolver
{
    private Dictionary<string, XmlDictionaryString> dictionary = new Dictionary<string, XmlDictionaryString>();
    Assembly assembly;

    public MyDataContractResolver(Assembly assembly)
    {
        this.assembly = assembly;
    }

    // Used at deserialization
    // Allows users to map xsi:type name to any Type
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)
    {
        XmlDictionaryString tName;
        XmlDictionaryString tNamespace;
        if (dictionary.TryGetValue(typeName, out tName) && dictionary.TryGetValue(typeNamespace, out tNamespace))
        {
            return this.assembly.GetType(tNamespace.Value + "." + tName.Value);
        }
        else
        {
            return null;
        }
    }

    // Used at serialization
    // Maps any Type to a new xsi:type representation
    public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)
    {
        string name = dataContractType.Name;
        string namesp = dataContractType.Namespace;
        typeName = new XmlDictionaryString(XmlDictionary.Empty, name, 0);
        typeNamespace = new XmlDictionaryString(XmlDictionary.Empty, namesp, 0);
        if (!dictionary.ContainsKey(dataContractType.Name))
        {
            dictionary.Add(name, typeName);
        }
        if (!dictionary.ContainsKey(dataContractType.Namespace))
        {
            dictionary.Add(namesp, typeNamespace);
        }
    }
}
```

 <span data-ttu-id="4f794-115">Örneğin, Types projesi, derlemeyi Bu örnekte kullanılan tüm türlerle oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4f794-115">As part of the sample, the Types project generates the assembly with all the types that are used in this sample.</span></span> <span data-ttu-id="4f794-116">Bu projeyi, serileştirilecek türleri eklemek, kaldırmak veya değiştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="4f794-116">Use this project to add, remove or modify the types that will be serialized.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="4f794-117">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="4f794-117">To use this sample</span></span>

1. <span data-ttu-id="4f794-118">Visual Studio 2012 kullanarak DCRSample. sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="4f794-118">Using Visual Studio 2012, open the DCRSample.sln solution file.</span></span>

2. <span data-ttu-id="4f794-119">Çözümü çalıştırmak için F5 'e basın</span><span class="sxs-lookup"><span data-stu-id="4f794-119">To run the solution, press F5</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4f794-120">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="4f794-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4f794-121">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4f794-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="4f794-122">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4f794-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4f794-123">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="4f794-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractResolver`  
  
## <a name="see-also"></a><span data-ttu-id="4f794-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f794-124">See also</span></span>

- [<span data-ttu-id="4f794-125">Veri Sözleşmesi Çözücü Kullanma</span><span class="sxs-lookup"><span data-stu-id="4f794-125">Using a Data Contract Resolver</span></span>](../feature-details/using-a-data-contract-resolver.md)
