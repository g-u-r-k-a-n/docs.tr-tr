---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: WindowsPrincipal nesnesi oluşturma'
title: 'Nasıl yapılır: WindowsPrincipal Nesnesi Oluşturma'
ms.date: 07/15/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsPrincipal objects, creating
- security [.NET], creating a WindowsPrincipal object
- security [.NET], principals
- principal objects, creating
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
ms.openlocfilehash: eee33eb419e8626b8b7f627b9ab1e46ea8dceab5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685237"
---
# <a name="how-to-create-a-windowsprincipal-object"></a><span data-ttu-id="fd4b5-103">Nasıl yapılır: WindowsPrincipal Nesnesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fd4b5-103">How to: Create a WindowsPrincipal Object</span></span>

> [!NOTE]
> <span data-ttu-id="fd4b5-104">Bu makale Windows için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fd4b5-104">This article applies to Windows.</span></span>
>
> <span data-ttu-id="fd4b5-105">ASP.NET Core hakkında bilgi için bkz. [ASP.NET Core Security](/aspnet/core/security/).</span><span class="sxs-lookup"><span data-stu-id="fd4b5-105">For information about ASP.NET Core, see [ASP.NET Core Security](/aspnet/core/security/).</span></span>

<span data-ttu-id="fd4b5-106"><xref:System.Security.Principal.WindowsPrincipal>Kodun, tekrar tekrar rol tabanlı doğrulama yapıp gerçekleştirmeyeceğini veya yalnızca bir kez yerine getirmeniz gerektiğini bağlı olarak, bir nesne oluşturmanın iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="fd4b5-106">There are two ways to create a <xref:System.Security.Principal.WindowsPrincipal> object, depending on whether code must repeatedly perform role-based validation or must perform it only once.</span></span>  
  
<span data-ttu-id="fd4b5-107">Kodun sürekli olarak rol tabanlı doğrulama yapması gerekiyorsa, aşağıdaki yordamların ilki daha az ek yük üretir.</span><span class="sxs-lookup"><span data-stu-id="fd4b5-107">If code must repeatedly perform role-based validation, the first of the following procedures produces less overhead.</span></span> <span data-ttu-id="fd4b5-108">Kodun rol tabanlı doğrulamaları yalnızca bir kez yapması gerektiğinde, <xref:System.Security.Principal.WindowsPrincipal> Aşağıdaki yordamların ikincisini kullanarak bir nesne oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd4b5-108">When code needs to make role-based validations only once, you can create a <xref:System.Security.Principal.WindowsPrincipal> object by using the second of the following procedures.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a><span data-ttu-id="fd4b5-109">Yinelenen doğrulama için bir WindowsPrincipal nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fd4b5-109">To create a WindowsPrincipal object for repeated validation</span></span>  
  
1. <span data-ttu-id="fd4b5-110"><xref:System.AppDomain.SetPrincipalPolicy%2A> <xref:System.AppDomain> Static özelliği tarafından döndürülen nesnede yöntemini çağırın <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> , yöntemi, <xref:System.Security.Principal.PrincipalPolicy> yeni ilkenin ne olması gerektiğini belirten bir numaralandırma değeri geçirerek.</span><span class="sxs-lookup"><span data-stu-id="fd4b5-110">Call the <xref:System.AppDomain.SetPrincipalPolicy%2A> method on the <xref:System.AppDomain> object that is returned by the static <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> property, passing the method a <xref:System.Security.Principal.PrincipalPolicy> enumeration value that indicates what the new policy should be.</span></span> <span data-ttu-id="fd4b5-111">Desteklenen değerler <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal> , <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal> , ve <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal> .</span><span class="sxs-lookup"><span data-stu-id="fd4b5-111">Supported values are <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, and <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span></span> <span data-ttu-id="fd4b5-112">Aşağıdaki kod bu yöntem çağrısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fd4b5-112">The following code demonstrates this method call.</span></span>  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2. <span data-ttu-id="fd4b5-113">İlke kümesiyle, <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> geçerli Windows kullanıcısını kapsülleyen sorumluyu almak için static özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="fd4b5-113">With the policy set, use the static <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> property to retrieve the principal that encapsulates the current Windows user.</span></span> <span data-ttu-id="fd4b5-114">Özellik dönüş türü olduğundan <xref:System.Security.Principal.IPrincipal> , sonucu bir <xref:System.Security.Principal.WindowsPrincipal> türe atamalısınız.</span><span class="sxs-lookup"><span data-stu-id="fd4b5-114">Because the property return type is <xref:System.Security.Principal.IPrincipal>, you must cast the result to a <xref:System.Security.Principal.WindowsPrincipal> type.</span></span> <span data-ttu-id="fd4b5-115">Aşağıdaki kod, <xref:System.Security.Principal.WindowsPrincipal> geçerli iş parçacığıyla ilişkili sorumlu değerine yeni bir nesnesi başlatır.</span><span class="sxs-lookup"><span data-stu-id="fd4b5-115">The following code initializes a new <xref:System.Security.Principal.WindowsPrincipal> object to the value of the principal associated with the current thread.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal =
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim myPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)
    ```  
  
3. <span data-ttu-id="fd4b5-116">Asıl nesne oluşturulduğunda, doğrulamak için birkaç yöntemden birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd4b5-116">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a><span data-ttu-id="fd4b5-117">Tek bir doğrulama için bir WindowsPrincipal nesnesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fd4b5-117">To create a WindowsPrincipal object for a single validation</span></span>  
  
1. <span data-ttu-id="fd4b5-118"><xref:System.Security.Principal.WindowsIdentity> <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> Geçerli Windows hesabını sorgulayan ve bu hesapla ilgili bilgileri yeni oluşturulan kimlik nesnesine yerleştiren statik yöntemini çağırarak yeni bir nesne başlatın.</span><span class="sxs-lookup"><span data-stu-id="fd4b5-118">Initialize a new <xref:System.Security.Principal.WindowsIdentity> object by calling the static <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> method, which queries the current Windows account and places information about that account into the newly created identity object.</span></span> <span data-ttu-id="fd4b5-119">Aşağıdaki kod yeni bir nesne oluşturur <xref:System.Security.Principal.WindowsIdentity> ve bunu geçerli kimliği doğrulanmış kullanıcı için başlatır.</span><span class="sxs-lookup"><span data-stu-id="fd4b5-119">The following code creates a new <xref:System.Security.Principal.WindowsIdentity> object and initializes it to the current authenticated user.</span></span>  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2. <span data-ttu-id="fd4b5-120">Yeni bir <xref:System.Security.Principal.WindowsPrincipal> nesne oluşturun ve <xref:System.Security.Principal.WindowsIdentity> önceki adımda oluşturulan nesnenin değerini geçirin.</span><span class="sxs-lookup"><span data-stu-id="fd4b5-120">Create a new <xref:System.Security.Principal.WindowsPrincipal> object and pass it the value of the <xref:System.Security.Principal.WindowsIdentity> object created in the preceding step.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3. <span data-ttu-id="fd4b5-121">Asıl nesne oluşturulduğunda, doğrulamak için birkaç yöntemden birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd4b5-121">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd4b5-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd4b5-122">See also</span></span>

- [<span data-ttu-id="fd4b5-123">Asıl ve Kimlik Nesneleri</span><span class="sxs-lookup"><span data-stu-id="fd4b5-123">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
- [<span data-ttu-id="fd4b5-124">ASP.NET Core güvenliği</span><span class="sxs-lookup"><span data-stu-id="fd4b5-124">ASP.NET Core Security</span></span>](/aspnet/core/security/)
