---
description: 'Daha fazla bilgi edinin: DataContract yedeği'
title: DataContract Yedeği
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: 739471efcea1d04752f3065c7a28f55f9ff9a0f8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755830"
---
# <a name="datacontract-surrogate"></a><span data-ttu-id="46e08-103">DataContract Yedeği</span><span class="sxs-lookup"><span data-stu-id="46e08-103">DataContract Surrogate</span></span>

<span data-ttu-id="46e08-104">Bu örnek, bir veri sözleşmesi yedek sınıfı kullanılarak serileştirme, seri durumdan çıkarma, şema dışarı aktarma ve şema içeri aktarma gibi işlemlerin nasıl özelleştirilebileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="46e08-104">This sample demonstrates how processes like serialization, deserialization, schema export, and schema import can be customized using a data contract surrogate class.</span></span> <span data-ttu-id="46e08-105">Bu örnek, verilerin serileştirildiği ve bir Windows Communication Foundation (WCF) istemci ve hizmeti arasında aktarıldığı bir istemci ve sunucu senaryosunda bir vekil 'in nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="46e08-105">This sample shows how to use a surrogate in a client and server scenario where data is serialized and transmitted between a Windows Communication Foundation (WCF) client and service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="46e08-106">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="46e08-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="46e08-107">Örnek, aşağıdaki hizmet sözleşmesini kullanır:</span><span class="sxs-lookup"><span data-stu-id="46e08-107">The sample uses the following service contract:</span></span>  
  
```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[AllowNonSerializableTypes]  
public interface IPersonnelDataService  
{  
    [OperationContract]  
    void AddEmployee(Employee employee);  
  
    [OperationContract]  
    Employee GetEmployee(string name);  
}  
```  
  
 <span data-ttu-id="46e08-108">`AddEmployee`İşlem, kullanıcıların yeni çalışanlar hakkında veri eklemesine izin verir ve `GetEmployee` işlem, ad temelinde çalışanları aramayı destekler.</span><span class="sxs-lookup"><span data-stu-id="46e08-108">The `AddEmployee` operation allows users to add data about new employees and the `GetEmployee` operation supports search for employees based on name.</span></span>  
  
 <span data-ttu-id="46e08-109">Bu işlemler aşağıdaki veri türünü kullanır:</span><span class="sxs-lookup"><span data-stu-id="46e08-109">These operations use the following data type:</span></span>  
  
```csharp
[DataContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
class Employee  
{  
    [DataMember]  
    public DateTime dateHired;  
  
    [DataMember]  
    public Decimal salary;  
  
    [DataMember]  
    public Person person;  
}  
```  
  
 <span data-ttu-id="46e08-110">`Employee`Türünde, `Person` Sınıf (Aşağıdaki örnek kodda gösterilen), <xref:System.Runtime.Serialization.DataContractSerializer> geçerli bir veri sözleşmesi sınıfı olmadığından tarafından serileştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="46e08-110">In the `Employee` type, the `Person` class (shown in the following sample code) cannot be serialized by the <xref:System.Runtime.Serialization.DataContractSerializer> because it is not a valid data contract class.</span></span>  
  
```csharp
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 <span data-ttu-id="46e08-111"><xref:System.Runtime.Serialization.DataContractAttribute>Özniteliğini `Person` sınıfına uygulayabilirsiniz, ancak bu her zaman mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="46e08-111">You can apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the `Person` class, but this is not always possible.</span></span> <span data-ttu-id="46e08-112">Örneğin, sınıfı, `Person` denetiminiz olmayan ayrı bir derlemede tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="46e08-112">For example, the `Person` class can be defined in a separate assembly over which you have no control.</span></span>  
  
 <span data-ttu-id="46e08-113">Bu kısıtlama verildiğinde, sınıfı seri hale getirmenin bir yolu, öğesini `Person` ile işaretlenen başka bir sınıfla yerine <xref:System.Runtime.Serialization.DataContractAttribute> Yeni sınıfa, gerekli verilerin üzerine kopyalamasıdır.</span><span class="sxs-lookup"><span data-stu-id="46e08-113">Given this restriction, one way to serialize the `Person` class is to substitute it with another class that is marked with <xref:System.Runtime.Serialization.DataContractAttribute> and copy over necessary data to the new class.</span></span> <span data-ttu-id="46e08-114">Amaç, `Person` sınıfın bir DataContract olarak görünmesini sağlar <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="46e08-114">The objective is to make the `Person` class appear as a DataContract to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="46e08-115">Bu, veri olmayan sözleşme sınıflarını serileştirmenin bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="46e08-115">Note that this is one way to serialize non-data contract classes.</span></span>  
  
 <span data-ttu-id="46e08-116">Örnek, `Person` sınıfının adlı farklı bir sınıfla mantıksal olarak yerini alır `PersonSurrogated` .</span><span class="sxs-lookup"><span data-stu-id="46e08-116">The sample logically replaces the `Person` class with a different class named `PersonSurrogated`.</span></span>  
  
```csharp
[DataContract(Name="Person", Namespace = "http://Microsoft.ServiceModel.Samples")]  
public class PersonSurrogated  
{  
    [DataMember]  
    public string FirstName;  
  
    [DataMember]  
    public string LastName;  
  
    [DataMember]  
    public int Age;  
}  
```  
  
 <span data-ttu-id="46e08-117">Bu değişikliği başarmak için veri sözleşmesi yedeği kullanılır.</span><span class="sxs-lookup"><span data-stu-id="46e08-117">The data contract surrogate is used to achieve this replacement.</span></span> <span data-ttu-id="46e08-118">Veri anlaşması yedeği, uygulayan bir sınıftır <xref:System.Runtime.Serialization.IDataContractSurrogate> .</span><span class="sxs-lookup"><span data-stu-id="46e08-118">A data contract surrogate is a class that implements <xref:System.Runtime.Serialization.IDataContractSurrogate>.</span></span> <span data-ttu-id="46e08-119">Bu örnekte, `AllowNonSerializableTypesSurrogate` sınıfı bu arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="46e08-119">In this sample, the `AllowNonSerializableTypesSurrogate` class implements this interface.</span></span>  
  
 <span data-ttu-id="46e08-120">Arabirim uygulamasında ilk görev, öğesinden öğesine bir tür eşlemesi oluşturmak için kullanılır `Person` `PersonSurrogated` .</span><span class="sxs-lookup"><span data-stu-id="46e08-120">In the interface implementation, the first task is to establish a type mapping from `Person` to `PersonSurrogated`.</span></span> <span data-ttu-id="46e08-121">Bu, hem serileştirme zamanında hem de şema dışa aktarma zamanında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="46e08-121">This is used both at serialization time as well as at schema export time.</span></span> <span data-ttu-id="46e08-122">Bu eşleme yöntemi uygulayarak elde edilir <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> .</span><span class="sxs-lookup"><span data-stu-id="46e08-122">This mapping is achieved by implementing the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> method.</span></span>  
  
```csharp
public Type GetDataContractType(Type type)  
{  
    if (typeof(Person).IsAssignableFrom(type))  
    {  
        return typeof(PersonSurrogated);  
    }  
    return type;  
}  
```  
  
 <span data-ttu-id="46e08-123"><xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29>Yöntemi, `Person` `PersonSurrogated` Aşağıdaki örnek kodda gösterildiği gibi serileştirme sırasında bir örneği bir örneğe eşler.</span><span class="sxs-lookup"><span data-stu-id="46e08-123">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> method maps a `Person` instance to a `PersonSurrogated` instance during serialization, as shown in the following sample code.</span></span>  
  
```csharp
public object GetObjectToSerialize(object obj, Type targetType)  
{  
    if (obj is Person)  
    {  
        Person person = (Person)obj;  
        PersonSurrogated personSurrogated = new PersonSurrogated();  
        personSurrogated.FirstName = person.firstName;  
        personSurrogated.LastName = person.lastName;  
        personSurrogated.Age = person.age;  
        return personSurrogated;  
    }  
    return obj;  
}  
```  
  
 <span data-ttu-id="46e08-124"><xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29>Yöntemi, aşağıdaki örnek kodda gösterildiği gibi, seri durumdan çıkarma için ters eşlemeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="46e08-124">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> method provides the reverse mapping for deserialization, as shown in the following sample code.</span></span>  
  
```csharp
public object GetDeserializedObject(object obj,
Type targetType)  
{  
    if (obj is PersonSurrogated)  
    {  
        PersonSurrogated personSurrogated = (PersonSurrogated)obj;  
        Person person = new Person();  
        person.firstName = personSurrogated.FirstName;  
        person.lastName = personSurrogated.LastName;  
        person.age = personSurrogated.Age;  
        return person;  
    }  
    return obj;  
}  
```  
  
 <span data-ttu-id="46e08-125">`PersonSurrogated`Şema içeri aktarma sırasında veri sözleşmesini varolan sınıfla eşlemek için, `Person` örneği <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> Aşağıdaki örnek kodda gösterildiği gibi yöntemini uygular.</span><span class="sxs-lookup"><span data-stu-id="46e08-125">To map the `PersonSurrogated` data contract to the existing `Person` class during schema import, the sample implements the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> method, as shown in the following sample code.</span></span>  
  
```csharp
public Type GetReferencedTypeOnImport(string typeName,
               string typeNamespace, object customData)  
{  
if (  
typeNamespace.Equals("http://schemas.datacontract.org/2004/07/DCSurrogateSample")  
)  
    {  
         if (typeName.Equals("PersonSurrogated"))  
        {  
             return typeof(Person);  
        }  
     }  
     return null;  
}  
```  
  
 <span data-ttu-id="46e08-126">Aşağıdaki örnek kod, arabiriminin uygulamasını tamamlar <xref:System.Runtime.Serialization.IDataContractSurrogate> .</span><span class="sxs-lookup"><span data-stu-id="46e08-126">The following sample code completes the implementation of the <xref:System.Runtime.Serialization.IDataContractSurrogate> interface.</span></span>  
  
```csharp
public System.CodeDom.CodeTypeDeclaration ProcessImportedType(  
          System.CodeDom.CodeTypeDeclaration typeDeclaration,
          System.CodeDom.CodeCompileUnit compileUnit)  
{  
    return typeDeclaration;  
}  
public object GetCustomDataToExport(Type clrType,
                               Type dataContractType)  
{  
    return null;  
}  
  
public object GetCustomDataToExport(  
System.Reflection.MemberInfo memberInfo, Type dataContractType)  
{  
    return null;  
}  
public void GetKnownCustomDataTypes(  
        KnownTypeCollection customDataTypes)  
{  
    // It does not matter what we do here.  
    throw new NotImplementedException();  
}  
```  
  
 <span data-ttu-id="46e08-127">Bu örnekte, yedek, ServiceModel içinde adlı bir öznitelik tarafından etkinleştirilir `AllowNonSerializableTypesAttribute` .</span><span class="sxs-lookup"><span data-stu-id="46e08-127">In this sample, the surrogate is enabled in ServiceModel by an attribute called `AllowNonSerializableTypesAttribute`.</span></span> <span data-ttu-id="46e08-128">Geliştiricilerin, yukarıdaki hizmet sözleşmesinde gösterildiği gibi bu özniteliği hizmet sözleşmelerine uygulaması gerekir `IPersonnelDataService` .</span><span class="sxs-lookup"><span data-stu-id="46e08-128">Developers would need to apply this attribute on their service contract as shown on the `IPersonnelDataService` service contract above.</span></span> <span data-ttu-id="46e08-129">Bu öznitelik `IContractBehavior` , ve yöntemlerinde işlemleri uygular ve üzerinde yedek ayarlar `ApplyClientBehavior` `ApplyDispatchBehavior` .</span><span class="sxs-lookup"><span data-stu-id="46e08-129">This attribute implements `IContractBehavior` and sets up the surrogate on operations in its `ApplyClientBehavior` and `ApplyDispatchBehavior` methods.</span></span>  
  
 <span data-ttu-id="46e08-130">Bu örnekte öznitelik gerekli değildir-bu örnekteki tanıtım amaçlarıyla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="46e08-130">The attribute is not necessary in this case - it is used for demonstration purposes in this sample.</span></span> <span data-ttu-id="46e08-131">Kullanıcılar ayrıca, el ile benzer `IContractBehavior` `IEndpointBehavior` veya `IOperationBehavior` kod kullanarak ya da yapılandırma kullanarak bir yedeği etkinleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="46e08-131">Users can alternatively enable a surrogate by manually adding a similar `IContractBehavior`, `IEndpointBehavior` or `IOperationBehavior` using code or using configuration.</span></span>  
  
 <span data-ttu-id="46e08-132">`IContractBehavior`Uygulama, kayıtlı olup olmadığını denetleyerek DataContract kullanan işlemlere bakar `DataContractSerializerOperationBehavior` .</span><span class="sxs-lookup"><span data-stu-id="46e08-132">The `IContractBehavior` implementation looks for operations that use DataContract by checking if they have a `DataContractSerializerOperationBehavior` registered.</span></span> <span data-ttu-id="46e08-133">Bu durumda, `DataContractSurrogate` özelliği o davranışa ayarlar.</span><span class="sxs-lookup"><span data-stu-id="46e08-133">If they do, it sets the `DataContractSurrogate` property on that behavior.</span></span> <span data-ttu-id="46e08-134">Aşağıdaki örnek kod, bunun nasıl yapıldığını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="46e08-134">The following sample code shows how this is done.</span></span> <span data-ttu-id="46e08-135">Bu işlem davranışında yedeği ayarlamak, serileştirme ve seri durumdan çıkarma için izin vermez.</span><span class="sxs-lookup"><span data-stu-id="46e08-135">Setting the surrogate on this operation behavior enables it for serialization and deserialization.</span></span>  
  
```csharp
public void ApplyClientBehavior(ContractDescription description, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.ClientRuntime proxy)  
{  
    foreach (OperationDescription opDesc in description.Operations)  
    {  
        ApplyDataContractSurrogate(opDesc);  
    }  
}  
  
public void ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.DispatchRuntime dispatch)  
{  
    foreach (OperationDescription opDesc in description.Operations)  
    {  
        ApplyDataContractSurrogate(opDesc);  
    }  
}  
  
private static void ApplyDataContractSurrogate(OperationDescription description)  
{  
    DataContractSerializerOperationBehavior dcsOperationBehavior = description.Behaviors.Find<DataContractSerializerOperationBehavior>();  
    if (dcsOperationBehavior != null)  
    {  
        if (dcsOperationBehavior.DataContractSurrogate == null)  
            dcsOperationBehavior.DataContractSurrogate = new AllowNonSerializableTypesSurrogate();  
    }  
}  
```  
  
 <span data-ttu-id="46e08-136">Meta veri oluşturma sırasında kullanılmak üzere yedeği eklemek için ek adımların alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="46e08-136">Additional steps need to be taken to plug in the surrogate for use during metadata generation.</span></span> <span data-ttu-id="46e08-137">Bunu yapmak için bir mekanizma, `IWsdlExportExtension` Bu örneğin gösterdiği şeydir.</span><span class="sxs-lookup"><span data-stu-id="46e08-137">One mechanism to do this is to provide an `IWsdlExportExtension` which is what this sample demonstrates.</span></span> <span data-ttu-id="46e08-138">Başka bir yol da doğrudan değiştirmektir `WsdlExporter` .</span><span class="sxs-lookup"><span data-stu-id="46e08-138">Another way is to modify the `WsdlExporter` directly.</span></span>  
  
 <span data-ttu-id="46e08-139">`AllowNonSerializableTypesAttribute`Özniteliği ve uygular `IWsdlExportExtension` `IContractBehavior` .</span><span class="sxs-lookup"><span data-stu-id="46e08-139">The `AllowNonSerializableTypesAttribute` attribute implements `IWsdlExportExtension` and `IContractBehavior`.</span></span> <span data-ttu-id="46e08-140">Uzantı ya da `IContractBehavior` `IEndpointBehavior` Bu durumda olabilir.</span><span class="sxs-lookup"><span data-stu-id="46e08-140">The extension can be either an `IContractBehavior` or `IEndpointBehavior` in this case.</span></span> <span data-ttu-id="46e08-141">`IWsdlExportExtension.ExportContract`Yöntem uygulama, `XsdDataContractExporter` DataContract için şema oluşturma sırasında kullanılan öğesine ekleyerek yedeği sağlar.</span><span class="sxs-lookup"><span data-stu-id="46e08-141">Its `IWsdlExportExtension.ExportContract` method implementation enables the surrogate by adding it to the `XsdDataContractExporter` used during schema generation for DataContract.</span></span> <span data-ttu-id="46e08-142">Aşağıdaki kod parçacığında bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="46e08-142">The following code snippet shows how to do this.</span></span>  
  
```csharp
public void ExportContract(WsdlExporter exporter, WsdlContractConversionContext context)  
{  
    if (exporter == null)  
        throw new ArgumentNullException("exporter");  
  
    object dataContractExporter;  
    XsdDataContractExporter xsdDCExporter;  
    if (!exporter.State.TryGetValue(typeof(XsdDataContractExporter), out dataContractExporter))  
    {  
        xsdDCExporter = new XsdDataContractExporter(exporter.GeneratedXmlSchemas);  
        exporter.State.Add(typeof(XsdDataContractExporter), xsdDCExporter);  
    }  
    else  
    {  
        xsdDCExporter = (XsdDataContractExporter)dataContractExporter;  
    }  
    if (xsdDCExporter.Options == null)  
        xsdDCExporter.Options = new ExportOptions();  
  
    if (xsdDCExporter.Options.DataContractSurrogate == null)  
        xsdDCExporter.Options.DataContractSurrogate = new AllowNonSerializableTypesSurrogate();  
}  
```  
  
 <span data-ttu-id="46e08-143">Örneği çalıştırdığınızda, istemci, ilk çağrının başarılı olup olmadığını denetlemek için bir GetEmployee çağrısı tarafından izlenen AddEmployee öğesini çağırır.</span><span class="sxs-lookup"><span data-stu-id="46e08-143">When you run the sample, the client calls AddEmployee followed by a GetEmployee call to check if the first call was successful.</span></span> <span data-ttu-id="46e08-144">GetEmployee işlem isteğinin sonucu istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="46e08-144">The result of the GetEmployee operation request is displayed in the client console window.</span></span> <span data-ttu-id="46e08-145">GetEmployee işlemi, çalışanı bulma ve "Found" Yazdırma işleminde başarılı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="46e08-145">The GetEmployee operation must succeed in finding the employee and print "found".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="46e08-146">Bu örnek, seri hale getirme, seri durumdan çıkarma ve meta veri oluşturma için bir vekil nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="46e08-146">This sample shows how to plug in a surrogate for serialize, deserialize and metadata generation.</span></span> <span data-ttu-id="46e08-147">Meta verilerden kod üretimi için bir yedeği nasıl bir fişe ekleneceğini göstermez.</span><span class="sxs-lookup"><span data-stu-id="46e08-147">It does not show how to plug in a surrogate for code generation from metadata.</span></span> <span data-ttu-id="46e08-148">Bir vekil 'in istemci kod üretimini eklemek için nasıl kullanılabileceği hakkında bir örnek görmek için bkz. [özel wsdl yayınlama](custom-wsdl-publication.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="46e08-148">To see a sample of how a surrogate can be used to plug into client code generation, see the [Custom WSDL Publication](custom-wsdl-publication.md) sample.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="46e08-149">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="46e08-149">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="46e08-150">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="46e08-150">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="46e08-151">Çözümün C# sürümünü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="46e08-151">To build the C# edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="46e08-152">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="46e08-152">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="46e08-153">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="46e08-153">The samples may already be installed on your machine.</span></span> <span data-ttu-id="46e08-154">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="46e08-154">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="46e08-155">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="46e08-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="46e08-156">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="46e08-156">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
