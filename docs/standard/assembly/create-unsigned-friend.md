---
title: 'Nasıl yapılır: imzasız arkadaş derlemeleri oluşturma'
ms.date: 08/19/2019
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
dev_langs:
- csharp
- vb
ms.openlocfilehash: d8fdc3061067d85498dc5bbed7bf324f99169a36
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774342"
---
# <a name="how-to-create-unsigned-friend-assemblies"></a><span data-ttu-id="6af7f-102">Nasıl yapılır: imzasız arkadaş derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="6af7f-102">How to: Create unsigned friend assemblies</span></span>

<span data-ttu-id="6af7f-103">Bu örnekte, friend derlemelerinin imzasız Derlemelerle nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6af7f-103">This example shows how to use friend assemblies with assemblies that are unsigned.</span></span>

## <a name="create-an-assembly-and-a-friend-assembly"></a><span data-ttu-id="6af7f-104">Derleme ve arkadaş derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="6af7f-104">Create an assembly and a friend assembly</span></span>

1. <span data-ttu-id="6af7f-105">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="6af7f-105">Open a command prompt.</span></span>

2. <span data-ttu-id="6af7f-106">Aşağıdaki kodu C# içeren *friend_unsigned_A* adlı bir veya Visual Basic dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6af7f-106">Create a C# or Visual Basic file named *friend_unsigned_A* that contains the following code.</span></span> <span data-ttu-id="6af7f-107">Kod, *friend_unsigned_B* bir Friend derlemesi olarak bildirmek için <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="6af7f-107">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_unsigned_B* as a friend assembly.</span></span>

   ```csharp
   // friend_unsigned_A.cs
   // Compile with:
   // csc /target:library friend_unsigned_A.cs
   using System.Runtime.CompilerServices;
   using System;

   [assembly: InternalsVisibleTo("friend_unsigned_B")]

   // Type is internal by default.
   class Class1
   {
       public void Test()
       {
           Console.WriteLine("Class1.Test");
       }
   }

   // Public type with internal member.
   public class Class2
   {
       internal void Test()
       {
           Console.WriteLine("Class2.Test");
       }
   }
   ```

   ```vb
   ' friend_unsigned_A.vb
   ' Compile with:
   ' vbc -target:library friend_unsigned_A.vb
   Imports System.Runtime.CompilerServices
   Imports System

   <Assembly: InternalsVisibleTo("friend_unsigned_B")>

   ' Friend type.
   Friend Class Class1
       Public Sub Test()
           Console.WriteLine("Class1.Test")
       End Sub
   End Class

   ' Public type with Friend member.
   Public Class Class2
       Friend Sub Test()
           Console.WriteLine("Class2.Test")
       End Sub
   End Class
   ```

3. <span data-ttu-id="6af7f-108">Aşağıdaki komutu kullanarak *friend_unsigned_A* derleyin ve imzalayın:</span><span class="sxs-lookup"><span data-stu-id="6af7f-108">Compile and sign *friend_unsigned_A* by using the following command:</span></span>

   ```csharp
   csc /target:library friend_unsigned_A.cs
   ```

   ```vb
   vbc -target:library friend_unsigned_A.vb
   ```

4. <span data-ttu-id="6af7f-109">Aşağıdaki kodu C# içeren *friend_unsigned_B* adlı bir veya Visual Basic dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6af7f-109">Create a C# or Visual Basic file named *friend_unsigned_B* that contains the following code.</span></span> <span data-ttu-id="6af7f-110">*Friend_unsigned_A* , bir Friend derlemesi olarak *Friend_unsigned_B* belirttiğinden, *friend_unsigned_B* içindeki kod `internal` (C#) veya`Friend`(Visual Basic) türlerine ve *friend_unsigned_A*' den üyelere erişebilir.</span><span class="sxs-lookup"><span data-stu-id="6af7f-110">Because *friend_unsigned_A* specifies *friend_unsigned_B* as a friend assembly, the code in *friend_unsigned_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_unsigned_A*.</span></span>

   ```csharp
   // friend_unsigned_B.cs
   // Compile with:
   // csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   public class Program
   {
       static void Main()
       {
           // Access an internal type.
           Class1 inst1 = new Class1();
           inst1.Test();

           Class2 inst2 = new Class2();
           // Access an internal member of a public type.
           inst2.Test();

           System.Console.ReadLine();
       }
   }
   ```

   ```vb
   ' friend_unsigned_B.vb
   ' Compile with:
   ' vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   Module Module1
       Sub Main()
           ' Access a Friend type.
           Dim inst1 As New Class1()
           inst1.Test()

           Dim inst2 As New Class2()
           ' Access a Friend member of a public type.
           inst2.Test()

           System.Console.ReadLine()
       End Sub
   End Module
   ```

5. <span data-ttu-id="6af7f-111">Aşağıdaki komutu kullanarak *friend_unsigned_B* derleyin.</span><span class="sxs-lookup"><span data-stu-id="6af7f-111">Compile *friend_unsigned_B* by using the following command.</span></span>

   ```csharp
   csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   ```

   ```vb
   vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   ```

   <span data-ttu-id="6af7f-112">Derleyici tarafından oluşturulan derlemenin adı, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliğine geçirilen arkadaş derleme adı ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6af7f-112">The name of the assembly that is generated by the compiler must match the friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="6af7f-113">`-out` derleyici seçeneğini kullanarak çıkış derlemesinin ( *. exe* veya *. dll*) adını açıkça belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6af7f-113">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `-out` compiler option.</span></span> <span data-ttu-id="6af7f-114">Daha fazla bilgi için bkz. [-OutC# (derleyici seçenekleri)](../../csharp/language-reference/compiler-options/out-compiler-option.md) veya [-Out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..</span><span class="sxs-lookup"><span data-stu-id="6af7f-114">For more information, see [-out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..</span></span>

6. <span data-ttu-id="6af7f-115">*Friend_unsigned_B. exe* dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6af7f-115">Run the *friend_unsigned_B.exe* file.</span></span>

   <span data-ttu-id="6af7f-116">Program iki dizeyi çıktı: **Class1. test** ve **Class2. test**.</span><span class="sxs-lookup"><span data-stu-id="6af7f-116">The program outputs two strings: **Class1.Test** and **Class2.Test**.</span></span>

## <a name="net-security"></a><span data-ttu-id="6af7f-117">.NET güvenliği</span><span class="sxs-lookup"><span data-stu-id="6af7f-117">.NET security</span></span>

<span data-ttu-id="6af7f-118">@No__t_0 özniteliği ve <xref:System.Security.Permissions.StrongNameIdentityPermission> sınıfı arasında benzerlikler vardır.</span><span class="sxs-lookup"><span data-stu-id="6af7f-118">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="6af7f-119">Temel fark, <xref:System.Security.Permissions.StrongNameIdentityPermission> kodun belirli bir bölümünü çalıştırmak için güvenlik izinleri talep edebilir, ancak <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelik `internal` veya `Friend` (Visual Basic) türlerinin ve üyelerinin görünürlüğünü denetler.</span><span class="sxs-lookup"><span data-stu-id="6af7f-119">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal`  or `Friend` (Visual Basic) types and members.</span></span>

## <a name="see-also"></a><span data-ttu-id="6af7f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6af7f-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="6af7f-121">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="6af7f-121">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="6af7f-122">Arkadaş derlemeleri</span><span class="sxs-lookup"><span data-stu-id="6af7f-122">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="6af7f-123">Nasıl yapılır: imzalı arkadaş derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="6af7f-123">How to: Create signed friend assemblies</span></span>](create-signed-friend.md)
- [<span data-ttu-id="6af7f-124">C#Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6af7f-124">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="6af7f-125">Programlama kavramları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6af7f-125">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
