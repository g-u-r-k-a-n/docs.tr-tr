---
title: 'Azaltma: Uygulama Etki Alanlarında Nesneleri Seri Durumdan Çıkarma'
ms.date: 03/30/2017
ms.assetid: 30c2d66c-04a8-41a5-ad31-646b937f61b5
ms.openlocfilehash: 43a1a045560b54cc831e69f9e1d4dba76a8569e1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126248"
---
# <a name="mitigation-deserialization-of-objects-across-app-domains"></a><span data-ttu-id="82f6e-102">Azaltma: Uygulama Etki Alanlarında Nesneleri Seri Durumdan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="82f6e-102">Mitigation: Deserialization of Objects Across App Domains</span></span>
<span data-ttu-id="82f6e-103">Bazı durumlarda, bir uygulama farklı uygulama temeli kullanan iki veya daha fazla uygulama etki alanı kullandığında, uygulama etki alanları arasında nesnelerin mantıksal çağrı bağlamında serisini kaldırma girişimi özel bir durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="82f6e-103">In some cases, when an app uses two or more app domains with different application bases, the attempt to deserialize objects in the logical call context across app domains throws an exception.</span></span>  
  
## <a name="diagnosing-the-issue"></a><span data-ttu-id="82f6e-104">Sorunu tanılama</span><span class="sxs-lookup"><span data-stu-id="82f6e-104">Diagnosing the issue</span></span>  
 <span data-ttu-id="82f6e-105">Sorun, sırasıyla aşağıdaki koşullar altında ortaya çıkar:</span><span class="sxs-lookup"><span data-stu-id="82f6e-105">The issue arises under the following sequence of conditions:</span></span>  
  
1. <span data-ttu-id="82f6e-106">Bir uygulama, farklı uygulama temel dizini kullanan iki veya daha fazla uygulama etki alanı kullanır.</span><span class="sxs-lookup"><span data-stu-id="82f6e-106">An app uses two or more app domains with different application bases.</span></span>  
  
2. <span data-ttu-id="82f6e-107">Bazı türler, <xref:System.Runtime.Remoting.Messaging.LogicalCallContext> veya <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> gibi bir yöntem çağrılarak açıkça <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType> içine eklenir.</span><span class="sxs-lookup"><span data-stu-id="82f6e-107">Some types are explicitly added to the <xref:System.Runtime.Remoting.Messaging.LogicalCallContext> by calling a method such as <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> or <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="82f6e-108">Bu türler seri hale getirilebilir olarak işaretlenmez ve genel bütünleştirilmiş derleme önbelleği içinde saklanmaz.</span><span class="sxs-lookup"><span data-stu-id="82f6e-108">These types are not marked as serializable and are not stored in the global assembly cache.</span></span>  
  
3. <span data-ttu-id="82f6e-109">Daha sonra, varsayılan olmayan uygulama etki alanında çalışan kod, bir yapılandırma dosyasından değer okumayı veya bir nesnenin serisini kaldırmak için XML kullanmayı dener.</span><span class="sxs-lookup"><span data-stu-id="82f6e-109">Later, code running in the non-default app domain tries to read a value from a configuration file or use XML to deserialize an object.</span></span>  
  
4. <span data-ttu-id="82f6e-110">Bir yapılandırma dosyasından okumak veya nesnenin serisini kaldırmak için, bir <xref:System.Xml.XmlReader> nesnesi yapılandırma sistemine erişmeyi dener.</span><span class="sxs-lookup"><span data-stu-id="82f6e-110">In order to read from a configuration file or deserialize the object, an <xref:System.Xml.XmlReader> object tries to access the configuration system.</span></span>  
  
5. <span data-ttu-id="82f6e-111">Eğer yapılandırma sistemi daha başlatılmadıysa, başlatılmasını tamamlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="82f6e-111">If the configuration system has not already been initialized, it must complete its initialization.</span></span> <span data-ttu-id="82f6e-112">Bu, diğer şeylerin yanı sıra, çalışma zamanının bir yapılandırma sistemi için tutarlı bir yol oluşturması gerektiği anlamına gelir ki bunu aşağıdaki şekilde gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="82f6e-112">This means, among other things, that the runtime has to create a stable path for a configuration system, which it does as follows:</span></span>  
  
    1. <span data-ttu-id="82f6e-113">Varsayılan olmayan uygulama etki alanı için kanıt arar.</span><span class="sxs-lookup"><span data-stu-id="82f6e-113">It looks for evidence for the non-default app domain.</span></span>  
  
    2. <span data-ttu-id="82f6e-114">Varsayılan uygulama etki alanını temel alarak, varsayılan olmayan etki alanı için olan kanıtları hesaplamayı dener.</span><span class="sxs-lookup"><span data-stu-id="82f6e-114">It tries to calculate the evidence for the non-default app domain based on the default app domain.</span></span>  
  
    3. <span data-ttu-id="82f6e-115">Varsayılan uygulama etki alanı için kanıt alma çağrısı, varsayılan olmayan uygulama etki alanından varsayılan uygulama etki alanına, uygulama etki alanları arasında bir çağrıyı tetikler.</span><span class="sxs-lookup"><span data-stu-id="82f6e-115">The call to get evidence for the default app domain triggers a cross-app domain call from the non-default app domain to the default app domain.</span></span>  
  
    4. <span data-ttu-id="82f6e-116">.NET Framework'teki uygulama etki alanları arası anlaşması kapsamında, mantıksal çağrı bağlamının içeriğinin uygulama etki alanı sınırları arasında sıralanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="82f6e-116">As part of the cross-app domain contract in the .NET Framework, the contents of the logical call context also have to be marshaled across app domain boundaries.</span></span>  
  
6. <span data-ttu-id="82f6e-117">Mantıksal çağrı bağlamındaki türler varsayılan uygulama etki alanında çözümlenemediği için, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="82f6e-117">Because the types that are in the logical call context cannot be resolved in the default app domain, an exception is thrown.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="82f6e-118">Azaltma</span><span class="sxs-lookup"><span data-stu-id="82f6e-118">Mitigation</span></span>  
 <span data-ttu-id="82f6e-119">Bu sorunun geçici çözümü için, aşağıdakini yapın</span><span class="sxs-lookup"><span data-stu-id="82f6e-119">To work around this issue, do the following</span></span>  
  
1. <span data-ttu-id="82f6e-120">Özel durumun oluşturulduğu çağrı yığınındaki `get_Evidence` çağrısını bulun.</span><span class="sxs-lookup"><span data-stu-id="82f6e-120">Look for the call to `get_Evidence` in the call stack when the exception is thrown.</span></span> <span data-ttu-id="82f6e-121">Özel durum, <xref:System.IO.FileNotFoundException> ve <xref:System.Runtime.Serialization.SerializationException> dahil birçok özel durumun ait olduğu büyük bir alt kümedeki özel durumlardan herhangi biri olabilir.</span><span class="sxs-lookup"><span data-stu-id="82f6e-121">The exception can be any of a large subset of exceptions, including <xref:System.IO.FileNotFoundException> and <xref:System.Runtime.Serialization.SerializationException>.</span></span>  
  
2. <span data-ttu-id="82f6e-122">Uygulamada mantıksal çağrı bağlamına hiçbir nesnenin eklenmediği yeri bulun ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="82f6e-122">Identify the place in the app where no objects are added to the logical call context and add the following code:</span></span>  
  
    ```csharp
    System.Configuration.ConfigurationManager.GetSection("system.xml/xmlReader");  
    ```
  
## <a name="see-also"></a><span data-ttu-id="82f6e-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82f6e-123">See also</span></span>

- [<span data-ttu-id="82f6e-124">Çalışma Zamanı Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="82f6e-124">Runtime Changes</span></span>](runtime-changes-in-the-net-framework-4-5-1.md)
