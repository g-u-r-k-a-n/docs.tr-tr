---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: ServiceContractGenerator için uzantı yazma'
title: 'Nasıl yapılır: ServiceContractGenerator için Uzantı Yazma'
ms.date: 03/30/2017
ms.assetid: 876ca823-bd16-4bdf-9e0f-02092df90e51
ms.openlocfilehash: 29d6d65cc3f9d29009f72b9a0c81b6cb1f472ac9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99644209"
---
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="2bd81-103">Nasıl yapılır: ServiceContractGenerator için Uzantı Yazma</span><span class="sxs-lookup"><span data-stu-id="2bd81-103">How to: Write an Extension for the ServiceContractGenerator</span></span>

<span data-ttu-id="2bd81-104">Bu konuda, için bir uzantısının nasıl yazılacağı açıklanmaktadır <xref:System.ServiceModel.Description.ServiceContractGenerator> .</span><span class="sxs-lookup"><span data-stu-id="2bd81-104">This topic describes how to write an extension for the <xref:System.ServiceModel.Description.ServiceContractGenerator>.</span></span> <span data-ttu-id="2bd81-105">Bu <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> işlem, arabirimi bir işlem davranışına uygulayarak veya <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> arabirimi bir sözleşme davranışına uygulayarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="2bd81-105">This can be done by implementing the <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> interface on an operation behavior or implementing the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span> <span data-ttu-id="2bd81-106">Bu konu başlığı altında, <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> arabirimin bir sözleşme davranışında nasıl uygulanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2bd81-106">This topic shows how to implement the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span>  
  
 <span data-ttu-id="2bd81-107">, <xref:System.ServiceModel.Description.ServiceContractGenerator> Ve örneklerinden hizmet sözleşmeleri, istemci türleri ve istemci yapılandırması oluşturur <xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.Description.ContractDescription> <xref:System.ServiceModel.Channels.Binding> .</span><span class="sxs-lookup"><span data-stu-id="2bd81-107">The <xref:System.ServiceModel.Description.ServiceContractGenerator> generates service contracts, client types, and client configurations from <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances.</span></span> <span data-ttu-id="2bd81-108">Genellikle,, <xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.Description.ContractDescription> ve <xref:System.ServiceModel.Channels.Binding> örneklerini hizmet meta verilerinden içeri aktarır ve ardından hizmeti çağırmak üzere kod oluşturmak için bu örnekleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="2bd81-108">Typically, you import <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances from service metadata and then use these instances to generate code to call the service.</span></span> <span data-ttu-id="2bd81-109">Bu örnekte, <xref:System.ServiceModel.Description.IWsdlImportExtension> WSDL ek açıklamalarını işlemek için bir uygulama kullanılır ve ardından oluşturulan koda yorum üretmek için, içeri aktarılan sözleşmelere kod oluşturma uzantıları eklenir.</span><span class="sxs-lookup"><span data-stu-id="2bd81-109">In this example, an <xref:System.ServiceModel.Description.IWsdlImportExtension> implementation is used to process WSDL annotations and then add code generation extensions to the imported contracts to generate comments on the generated code.</span></span>  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="2bd81-110">ServiceContractGenerator için bir uzantı yazmak için</span><span class="sxs-lookup"><span data-stu-id="2bd81-110">To write an extension for the ServiceContractGenerator</span></span>  
  
1. <span data-ttu-id="2bd81-111">Uygulayın <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> .</span><span class="sxs-lookup"><span data-stu-id="2bd81-111">Implement <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="2bd81-112">Oluşturulan hizmet sözleşmesini değiştirmek için <xref:System.ServiceModel.Description.ServiceContractGenerationContext> metoduna geçirilen örneği kullanın <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> .</span><span class="sxs-lookup"><span data-stu-id="2bd81-112">To modify the generated service contract, use the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> instance passed into the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> method.</span></span>  
  
    ```csharp
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
        context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2. <span data-ttu-id="2bd81-113"><xref:System.ServiceModel.Description.IWsdlImportExtension>Aynı sınıfa uygulayın.</span><span class="sxs-lookup"><span data-stu-id="2bd81-113">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension> on the same class.</span></span> <span data-ttu-id="2bd81-114"><xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29>Yöntemi, içeri aktarılan örneğe bir kod oluşturma uzantısı ekleyerek belirli BIR WSDL uzantısını işleyebilir (Bu durumda WSDL ek açıklamaları) <xref:System.ServiceModel.Description.ContractDescription> .</span><span class="sxs-lookup"><span data-stu-id="2bd81-114">The <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> method can process a specific WSDL extension (WSDL annotations in this case) by adding a code generation extension to the imported <xref:System.ServiceModel.Description.ContractDescription> instance.</span></span>  
  
    ```csharp
    public void ImportContract(WsdlImporter importer, WsdlContractConversionContext context)
    {
        // Contract documentation
        if (context.WsdlPortType.Documentation != null)
        {
            context.Contract.Behaviors.Add(new WsdlDocumentationImporter(context.WsdlPortType.Documentation));
        }
        // Operation documentation
        foreach (Operation operation in context.WsdlPortType.Operations)
        {
            if (operation.Documentation != null)
            {
                OperationDescription operationDescription = context.Contract.Operations.Find(operation.Name);
                if (operationDescription != null)
                {
                    operationDescription.Behaviors.Add(new WsdlDocumentationImporter(operation.Documentation));
                }
            }
        }
    }
    public void BeforeImport(ServiceDescriptionCollection wsdlDocuments, XmlSchemaSet xmlSchemas, ICollection<XmlElement> policy)
    {
        Console.WriteLine("BeforeImport called.");
    }

    public void ImportEndpoint(WsdlImporter importer, WsdlEndpointConversionContext context)
    {
        Console.WriteLine("ImportEndpoint called.");
    }
    ```  
  
3. <span data-ttu-id="2bd81-115">İstemci yapılandırmanıza WSDL İçeri Aktarıcı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2bd81-115">Add the WSDL importer to your client configuration.</span></span>  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4. <span data-ttu-id="2bd81-116">İstemci kodunda bir `MetadataExchangeClient` ve çağrısı oluşturun `GetMetadata` .</span><span class="sxs-lookup"><span data-stu-id="2bd81-116">In the client code, create a `MetadataExchangeClient` and call `GetMetadata`.</span></span>  
  
    ```csharp
    var mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5. <span data-ttu-id="2bd81-117">`WsdlImporter`Ve çağrısı oluşturun `ImportAllContracts` .</span><span class="sxs-lookup"><span data-stu-id="2bd81-117">Create a `WsdlImporter` and call `ImportAllContracts`.</span></span>  
  
    ```csharp
    var importer = new WsdlImporter(metaDocs);
    System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6. <span data-ttu-id="2bd81-118">`ServiceContractGenerator`Her sözleşme için bir ve çağrısı oluşturun `GenerateServiceContractType` .</span><span class="sxs-lookup"><span data-stu-id="2bd81-118">Create a `ServiceContractGenerator` and call `GenerateServiceContractType` for each contract.</span></span>  
  
    ```csharp
    var generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7. <span data-ttu-id="2bd81-119"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> , uygulayan belirli bir sözleşmede her bir sözleşme davranışı için otomatik olarak çağrılır <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> .</span><span class="sxs-lookup"><span data-stu-id="2bd81-119"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> is called automatically for each contract behavior on a given contract that implements <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="2bd81-120">Bu yöntem daha sonra <xref:System.ServiceModel.Description.ServiceContractGenerationContext> geçirilmiş ' i değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="2bd81-120">This method can then modify the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> passed in.</span></span> <span data-ttu-id="2bd81-121">Bu örnekte, açıklamalar eklenir.</span><span class="sxs-lookup"><span data-stu-id="2bd81-121">In this example comments are added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bd81-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2bd81-122">See also</span></span>

- [<span data-ttu-id="2bd81-123">Meta veri</span><span class="sxs-lookup"><span data-stu-id="2bd81-123">Metadata</span></span>](../feature-details/metadata.md)
- [<span data-ttu-id="2bd81-124">Nasıl yapılır: Özel WSDL İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="2bd81-124">How to: Import Custom WSDL</span></span>](how-to-import-custom-wsdl.md)
