---
title: 'Nasıl yapılır: DataContractJsonSerializer kullanma'
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 354f0c58a83e07ff3180977311adf85ae306dd21
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976869"
---
# <a name="how-to-use-datacontractjsonserializer"></a>DataContractJsonSerializer 'ı kullanma

> [!NOTE]
> Bu makale <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. JSON serileştirilmesinin ve serisini kaldırma ile ilgili çoğu senaryo için, [System. Text. JSON ad alanındaki](../../../standard/serialization/system-text-json-overview.md)araçları öneririz.

JSON (JavaScript Nesne Gösterimi), istemci tarayıcıları ve AJAX özellikli Web Hizmetleri arasında küçük miktarlarda verilerin hızlı bir şekilde değiş tokuşlanmasını sağlayan etkili bir veri kodlama biçimidir.

Bu makalede, .NET tür nesnelerinin JSON kodlu verilere nasıl serileştirildiğini ve sonra JSON biçimindeki verilerin serisini .NET türlerinin örneklerine nasıl seri hale getirilebileceğini gösterir. Bu örnek, Kullanıcı tanımlı `Person` türünün serileştirilmesi ve serisini göstermek için bir veri sözleşmesi kullanır ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>kullanır.

Genellikle, JSON serileştirme ve seri durumundan çıkarma, AJAX etkin uç noktalar üzerinde kullanıma sunulan hizmet işlemlerinde veri sözleşme türlerini kullandığınızda otomatik olarak Windows Communication Foundation (WCF) tarafından işlenir. Ancak, bazı durumlarda JSON verileriyle doğrudan çalışmanız gerekebilir.

Bu makale, [DataContractJsonSerializer örneğine](../samples/json-serialization.md)dayalıdır.

## <a name="to-define-the-data-contract-for-a-person-type"></a>Bir kişi türü için veri sözleşmesini tanımlamak için

1. <xref:System.Runtime.Serialization.DataContractAttribute> sınıfa ve <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliğine ekleyerek, seri hale getirmek istediğiniz üyelere `Person` için veri sözleşmesini tanımlayın. Veri sözleşmeleri hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri tasarlama](../designing-service-contracts.md).

    ```csharp
    [DataContract]
    internal class Person
    {
        [DataMember]
        internal string name;

        [DataMember]
        internal int age;
    }
    ```

## <a name="to-serialize-an-instance-of-type-person-to-json"></a>Kişi türündeki bir örneği JSON 'a seri hale getirmek için

> [!NOTE]
> Sunucuda giden bir yanıtın serileştirilmesi sırasında veya başka bir nedenle hata oluşursa istemciye hata olarak döndürülmeyebilir.

1. `Person` türünün bir örneğini oluşturun.

    ```csharp
    var p = new Person();
    p.name = "John";
    p.age = 42;
    ```

2. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>kullanarak `Person` nesnesini bir bellek akışına seri hale getirme.

    ```csharp
    var stream1 = new MemoryStream();
    var ser = new DataContractJsonSerializer(typeof(Person));
    ```

3. Akışa JSON verisi yazmak için <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> yöntemini kullanın.

    ```csharp
    ser.WriteObject(stream1, p);
    ```

4. JSON çıkışını göster.

    ```csharp
    stream1.Position = 0;
    var sr = new StreamReader(stream1);
    Console.Write("JSON form of Person object: ");
    Console.WriteLine(sr.ReadToEnd());
    ```

## <a name="to-deserialize-an-instance-of-type-person-from-json"></a>JSON 'dan kişi türündeki bir örnek serisini kaldırmak için

1. JSON kodlu verileri, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> yöntemini kullanarak yeni bir `Person` örneğine serisini kaldırma.

    ```csharp
    stream1.Position = 0;
    var p2 = (Person)ser.ReadObject(stream1);
    ```

2. Sonuçları göster.

    ```csharp
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");
    ```

## <a name="example"></a>Örnek

```csharp
// Create a User object and serialize it to a JSON stream.
public static string WriteFromObject()
{
    // Create User object.
    var user = new User("Bob", 42);

    // Create a stream to serialize the object to.
    var ms = new MemoryStream();

    // Serializer the User object to the stream.
    var ser = new DataContractJsonSerializer(typeof(User));
    ser.WriteObject(ms, user);
    byte[] json = ms.ToArray();
    ms.Close();
    return Encoding.UTF8.GetString(json, 0, json.Length);
}

// Deserialize a JSON stream to a User object.
public static User ReadToObject(string json)
{
    var deserializedUser = new User();
    var ms = new MemoryStream(Encoding.UTF8.GetBytes(json));
    var ser = new DataContractJsonSerializer(deserializedUser.GetType());
    deserializedUser = ser.ReadObject(ms) as User;
    ms.Close();
    return deserializedUser;
}
```

> [!NOTE]
> JSON seri hale getirici, aşağıdaki örnek kodda gösterildiği gibi, aynı ada sahip birden çok üyesi olan veri sözleşmeleri için bir serileştirme özel durumu oluşturur.

```csharp
[DataContract]
public class TestDuplicateDataBase
{
    [DataMember]
    public int field1 = 123;
}

[DataContract]
public class TestDuplicateDataDerived : TestDuplicateDataBase
{
    [DataMember]
    public new int field1 = 999;
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET 'te JSON serileştirme](../../../standard/serialization/system-text-json-overview.md)
