---
title: ASP.NET’te System.Transactions kullanma
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: 2bddebc13897408839e18f42b17a9fbaefdc5b87
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040418"
---
# <a name="using-systemtransactions-in-aspnet"></a><span data-ttu-id="bcecd-102">ASP.NET’te System.Transactions kullanma</span><span class="sxs-lookup"><span data-stu-id="bcecd-102">Using System.Transactions in ASP.NET</span></span>
<span data-ttu-id="bcecd-103">Bu konu, bir ASP.NET uygulamasının içinde <xref:System.Transactions> başarıyla kullanabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="bcecd-103">This topic describes how you can successfully use <xref:System.Transactions> inside an ASP.NET application.</span></span>

## <a name="enable-distributedtransactionpermission-in-aspnet"></a><span data-ttu-id="bcecd-104">ASP.NET 'de DistributedTransactionPermission 'ı etkinleştir</span><span class="sxs-lookup"><span data-stu-id="bcecd-104">Enable DistributedTransactionPermission in ASP.NET</span></span>
 <span data-ttu-id="bcecd-105"><xref:System.Transactions> kısmen güvenilen çağıranları destekler ve `AllowPartiallyTrustedCallers` özniteliğiyle (APTCA) işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="bcecd-105"><xref:System.Transactions> supports partially trusted callers and is marked with the `AllowPartiallyTrustedCallers` attribute (APTCA).</span></span> <span data-ttu-id="bcecd-106"><xref:System.Transactions> için güven düzeyleri, <xref:System.Transactions> kullanıma sunduğu (örneğin, sistem belleği, paylaşılan işlem genelindeki kaynaklar, sistem genelinde kaynaklar ve diğer kaynaklar) temel alınarak tanımlanır ve bu kaynaklara erişmek için gerekli olan güven düzeyini kaynakların.</span><span class="sxs-lookup"><span data-stu-id="bcecd-106">The trust levels for <xref:System.Transactions> are defined based on the types of resources (for example, system memory, shared process-wide resources, system-wide resources, and other resources) that <xref:System.Transactions> exposes and the level of trust that should be required to access those resources.</span></span> <span data-ttu-id="bcecd-107">Kısmi güven ortamında, tam olmayan bir güven derlemesi yalnızca uygulama etki alanı içindeki işlemleri kullanabilir (Bu durumda, korunan tek kaynak sistem belleğidir), çünkü <xref:System.Transactions.DistributedTransactionPermission> verilmez.</span><span class="sxs-lookup"><span data-stu-id="bcecd-107">In a partial-trust environment, a non-full trust assembly can only use transactions within the Application Domain (in this case, the only resource being protected is system memory), unless it is granted the <xref:System.Transactions.DistributedTransactionPermission>.</span></span>

 <span data-ttu-id="bcecd-108"><xref:System.Transactions.DistributedTransactionPermission>, işlem yönetiminin Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) tarafından yönetilmek üzere ilerletilidiğinde talep edilir.</span><span class="sxs-lookup"><span data-stu-id="bcecd-108"><xref:System.Transactions.DistributedTransactionPermission> is demanded whenever transaction management is escalated to be managed by the Microsoft Distributed Transaction Coordinator (MSDTC).</span></span> <span data-ttu-id="bcecd-109">Bu tür bir senaryo işlemi genelinde kaynakları ve MSDTC günlüğünde ayrılmış alandır özellikle bir genel kaynağı kullanır.</span><span class="sxs-lookup"><span data-stu-id="bcecd-109">This kind of scenario utilizes process-wide resources and particularly a global resource, which is the reserved space in the MSDTC log.</span></span> <span data-ttu-id="bcecd-110">Bir Web ön uç bir veritabanı veya veritabanı sağladığı hizmetler bir parçası olarak kullanan bir uygulama için bu kullanım örneğidir.</span><span class="sxs-lookup"><span data-stu-id="bcecd-110">An example of this usage is a Web front-end to a database or an application that uses a database as part of the services it provides.</span></span>

 <span data-ttu-id="bcecd-111">ASP.NET kendi güven düzeylerine sahiptir ve ilke dosyaları aracılığıyla bu güven düzeyleriyle belirli bir izin kümesini ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="bcecd-111">ASP.NET has its own set of trust levels and associates a specific set of permissions with these trust levels through policy files.</span></span> <span data-ttu-id="bcecd-112">Daha fazla bilgi için bkz. [ASP.net Trust Levels and Policy Files](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="bcecd-112">For more information, see [ASP.NET Trust Levels and Policy Files](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100)).</span></span> <span data-ttu-id="bcecd-113">Windows SDK ilk yüklediğinizde, varsayılan ASP.NET ilke dosyalarından hiçbiri <xref:System.Transactions.DistributedTransactionPermission> ilişkilendirilmez.</span><span class="sxs-lookup"><span data-stu-id="bcecd-113">When you initially install the Windows SDK, none of the default ASP.NET policy files are associated with the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="bcecd-114">Bu nedenle, bir ASP.NET uygulamasındaki işleminizi MSDTC tarafından yönetilmek üzere ilerlediğinde, yükseltme işlemi <xref:System.Transactions.DistributedTransactionPermission> yoğun bir <xref:System.Security.SecurityException> ile başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="bcecd-114">As such, when your transaction in an ASP.NET application is escalated to be managed by the MSDTC, the escalation fails with a <xref:System.Security.SecurityException> upon demanding the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="bcecd-115">ASP.NET kısmi güven ortamında işlem yükseltme işlemini etkinleştirmek için, <xref:System.Transactions.DistributedTransactionPermission> <xref:System.Data.SqlClient.SqlClientPermission> aynı varsayılan güven düzeylerinde vermelisiniz.</span><span class="sxs-lookup"><span data-stu-id="bcecd-115">To enable transaction escalation in an ASP.NET partial trust environment, you should grant the <xref:System.Transactions.DistributedTransactionPermission> in the same default trust levels as those of <xref:System.Data.SqlClient.SqlClientPermission>.</span></span> <span data-ttu-id="bcecd-116">Bunu desteklemek için kendi özel güven düzeyinizi ve ilke dosyanızı yapılandırabilir ya da **Web_hightrust. config** ve **Web_mediumtrust. config**olan varsayılan ilke dosyalarını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bcecd-116">You can either configure your own custom trust level and policy file to support this, or you can modify the default policy files, which are **Web_hightrust.config** and **Web_mediumtrust.config**.</span></span>

 <span data-ttu-id="bcecd-117">İlke dosyalarını değiştirmek için, `PolicyLevel` öğesinin altındaki `SecurityClasses` öğesine `DistributedTransactionPermission` için bir `SecurityClass` öğesi ekleyin ve System. Transactions için ASP.NET `IPermission` altına karşılık gelen bir `NamedPermissionSet` öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bcecd-117">To modify the policy files, add a `SecurityClass` element for `DistributedTransactionPermission` to the `SecurityClasses` element under the `PolicyLevel` element and add a corresponding `IPermission` element under the ASP.NET `NamedPermissionSet` for System.Transactions.</span></span> <span data-ttu-id="bcecd-118">Aşağıdaki yapılandırma dosyası bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="bcecd-118">The following configuration file demonstrates this.</span></span>

```xml
<SecurityClasses>
   <SecurityClass Name="DistributedTransactionPermission" Description="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
...
</SecurityClasses>

<PermissionSet
  class="NamedPermissionSet"
  version="1"
  Name="ASP.Net">
     <IPermission
        class="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
        version="1"
        Unrestricted="true"
     />
...
</PermissionSet>
```

 <span data-ttu-id="bcecd-119">ASP.NET güvenlik ilkesi hakkında daha fazla bilgi için bkz. [SecurityPolicy öğesi (ASP.NET Settings şeması)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="bcecd-119">For more information about ASP.NET security policy, see [securityPolicy Element (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).</span></span>

## <a name="dynamic-compilation"></a><span data-ttu-id="bcecd-120">Dinamik derleme</span><span class="sxs-lookup"><span data-stu-id="bcecd-120">Dynamic Compilation</span></span>
 <span data-ttu-id="bcecd-121">Erişim üzerinde dinamik olarak derlenen bir ASP.NET uygulamasında <xref:System.Transactions> alıp kullanmak istiyorsanız, yapılandırma dosyasındaki <xref:System.Transactions> derlemesine bir başvuru yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bcecd-121">If you want to import and use <xref:System.Transactions> in an ASP.NET application that is dynamically compiled on access, you should place a reference to the <xref:System.Transactions> assembly in the configuration file.</span></span> <span data-ttu-id="bcecd-122">Özellikle başvuru, varsayılan kök **Web. config** yapılandırma dosyasının `compilation/assemblies` bölümü veya belirli bir Web uygulamasının yapılandırma dosyası altına eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="bcecd-122">Specifically, the reference should be added under the `compilation/assemblies` section of the default root **Web.config** configuration file, or a specific Web application's configuration file.</span></span> <span data-ttu-id="bcecd-123">Aşağıdaki örnek bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="bcecd-123">The following example demonstrates this.</span></span>

```xml
<configuration>
   <system.web>
      <compilation>
         <assemblies>
      <add assembly="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
         </assemblies>
      </compilation>
   </system.web>
</configuration>
```

 <span data-ttu-id="bcecd-124">Daha fazla bilgi için bkz. [derleme için derlemeler Için öğe ekleme (ASP.NET Settings şeması)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="bcecd-124">For more information, see [add Element for assemblies for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="bcecd-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bcecd-125">See also</span></span>

- <span data-ttu-id="bcecd-126">[ASP.NET güven düzeyleri ve Ilke dosyaları](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bcecd-126">[ASP.NET Trust Levels and Policy Files](https://docs.microsoft.com/previous-versions/aspnet/wyts434y(v=vs.100))</span></span>
- <span data-ttu-id="bcecd-127">[securityPolicy öğesi (ASP.NET Settings şeması)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bcecd-127">[securityPolicy Element (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))</span></span>
- [<span data-ttu-id="bcecd-128">İşlem Yönetimi Yükseltme</span><span class="sxs-lookup"><span data-stu-id="bcecd-128">Transaction Management Escalation</span></span>](transaction-management-escalation.md)
