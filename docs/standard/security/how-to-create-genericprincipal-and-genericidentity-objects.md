---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: GenericPrincipal ve GenericIdentity nesneleri oluşturma'
title: 'Nasıl yapılır: GenericPrincipal ve GenericIdentity Nesneleri Oluşturma'
ms.date: 07/15/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Creating Generic Identity Objects
- GenericPrincipal Objects
- Creating GenericPrincipal Objects
- GenericIdentity Objects
ms.assetid: 465694cf-258b-4747-9dae-35b01a5bcdbb
ms.openlocfilehash: 8c77a9afec7bd166a71abb6af19d8766b02d0523
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685224"
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a>Nasıl yapılır: GenericPrincipal ve GenericIdentity Nesneleri Oluşturma

> [!NOTE]
> Bu makale Windows için geçerlidir.
>
> ASP.NET Core hakkında bilgi için bkz. [ASP.NET Core güvenliğine genel bakış](/aspnet/core/security/).

<xref:System.Security.Principal.GenericIdentity> <xref:System.Security.Principal.GenericPrincipal> Bir Windows etki alanından bağımsız olarak bulunan bir yetkilendirme şeması oluşturmak için sınıfını sınıfıyla birlikte kullanabilirsiniz.

### <a name="to-create-a-genericprincipal-object"></a>GenericPrincipal nesnesi oluşturmak için

1. Identity sınıfının yeni bir örneğini oluşturun ve onu tutmak istediğiniz adla başlatın. Aşağıdaki kod, yeni bir **GenericIdentity** nesnesi oluşturur ve adı ile başlatır `MyUser` .

    ```vb
    Dim myIdentity As New GenericIdentity("MyUser")
    ```

    ```csharp
    GenericIdentity myIdentity = new GenericIdentity("MyUser");
    ```

2. **GenericPrincipal** sınıfının yeni bir örneğini oluşturun ve daha önce oluşturulan **GenericIdentity** nesnesiyle ve bu sorumluya ilişkilendirilmesini istediğiniz rolleri temsil eden dizeler dizisiyle başlatın. Aşağıdaki kod örneği, bir yönetici rolünü ve Kullanıcı rolünü temsil eden dizelerin dizisini belirtir. **GenericPrincipal** daha sonra önceki **GenericIdentity** ve String dizisi ile başlatılır.

    ```vb
    Dim myStringArray As String() = {"Manager", "Teller"}
    DIm myPrincipal As New GenericPrincipal(myIdentity, myStringArray)
    ```

    ```csharp
    String[] myStringArray = {"Manager", "Teller"};
    GenericPrincipal myPrincipal = new GenericPrincipal(myIdentity, myStringArray);
    ```

3. Geçerli iş parçacığına asıl eklemek için aşağıdaki kodu kullanın. Bu, sorumlunun birkaç kez doğrulanması gerektiği durumlarda faydalıdır, bu, uygulamanızda çalışan diğer kod tarafından doğrulanması veya bir nesne tarafından doğrulanması gerekir <xref:System.Security.Permissions.PrincipalPermission> . Principal nesnesinde, iş parçacığına iliştirmeden rol tabanlı doğrulama işlemi gerçekleştirmeye devam edebilirsiniz. Daha fazla bilgi için bkz. [Principal nesnesini değiştirme](replacing-a-principal-object.md).

    ```vb
    Thread.CurrentPrincipal = myPrincipal
    ```

    ```csharp
    Thread.CurrentPrincipal = myPrincipal;
    ```

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, **GenericPrincipal** ve **GenericIdentity**'nin bir örneğinin nasıl oluşturulacağını göstermektedir. Bu kod, bu nesnelerin değerlerini konsola görüntüler.

```vb
Imports System.Security.Principal
Imports System.Threading

Public Class Class1

    Public Shared Sub Main()
        ' Create generic identity.
        Dim myIdentity As New GenericIdentity("MyIdentity")

        ' Create generic principal.
        Dim myStringArray As String() =  {"Manager", "Teller"}
        Dim myPrincipal As New GenericPrincipal(myIdentity, myStringArray)

        ' Attach the principal to the current thread.
        ' This is not required unless repeated validation must occur,
        ' other code in your application must validate, or the
        ' PrincipalPermission object is used.
        Thread.CurrentPrincipal = myPrincipal

        ' Print values to the console.
        Dim name As String = myPrincipal.Identity.Name
        Dim auth As Boolean = myPrincipal.Identity.IsAuthenticated
        Dim isInRole As Boolean = myPrincipal.IsInRole("Manager")

        Console.WriteLine("The name is: {0}", name)
        Console.WriteLine("The isAuthenticated is: {0}", auth)
        Console.WriteLine("Is this a Manager? {0}", isInRole)

    End Sub

End Class
```

```csharp
using System;
using System.Security.Principal;
using System.Threading;

public class Class1
{
    public static int Main(string[] args)
    {
    // Create generic identity.
    GenericIdentity myIdentity = new GenericIdentity("MyIdentity");

    // Create generic principal.
    String[] myStringArray = {"Manager", "Teller"};
    GenericPrincipal myPrincipal =
        new GenericPrincipal(myIdentity, myStringArray);

    // Attach the principal to the current thread.
    // This is not required unless repeated validation must occur,
    // other code in your application must validate, or the
    // PrincipalPermission object is used.
    Thread.CurrentPrincipal = myPrincipal;

    // Print values to the console.
    String name =  myPrincipal.Identity.Name;
    bool auth =  myPrincipal.Identity.IsAuthenticated;
    bool isInRole =  myPrincipal.IsInRole("Manager");

    Console.WriteLine("The name is: {0}", name);
    Console.WriteLine("The isAuthenticated is: {0}", auth);
    Console.WriteLine("Is this a Manager? {0}", isInRole);

    return 0;
    }
}
```

Yürütüldüğünde, uygulama aşağıdakine benzer bir çıktı görüntüler.

```console
The Name is: MyIdentity
The IsAuthenticated is: True
Is this a Manager? True
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Principal.GenericIdentity>
- <xref:System.Security.Principal.GenericPrincipal>
- <xref:System.Security.Permissions.PrincipalPermission>
- [Asıl Nesneyi Değiştirme](replacing-a-principal-object.md)
- [Asıl ve Kimlik Nesneleri](principal-and-identity-objects.md)
