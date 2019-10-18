---
title: 'Nasıl yapılır: imzalı arkadaş derlemeleri oluşturma'
ms.date: 08/19/2019
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
dev_langs:
- csharp
- vb
ms.openlocfilehash: 3bf71adc694f3c6e072990717198b4f2003cd503
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523892"
---
# <a name="how-to-create-signed-friend-assemblies"></a><span data-ttu-id="ddfb5-102">Nasıl yapılır: imzalı arkadaş derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="ddfb5-102">How to: Create signed friend assemblies</span></span>
<span data-ttu-id="ddfb5-103">Bu örnek, friend derlemelerinin tanımlayıcı adlara sahip Derlemelerle nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ddfb5-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="ddfb5-104">Her iki derlemenin de tanımlayıcı adlandırılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ddfb5-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="ddfb5-105">Bu örnekteki her iki derleme de aynı anahtarları kullanmasına karşın, iki derleme için farklı anahtarlar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ddfb5-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
## <a name="create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="ddfb5-106">İmzalı derleme ve arkadaş derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="ddfb5-106">Create a signed assembly and a friend assembly</span></span>  
  
1. <span data-ttu-id="ddfb5-107">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="ddfb5-107">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="ddfb5-108">Anahtar oluşturma ve ortak anahtarını görüntüleme için tanımlayıcı ad aracı ile aşağıdaki komut dizisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ddfb5-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="ddfb5-109">Daha fazla bilgi için bkz. [sn. exe (tanımlayıcı ad aracı)](../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="ddfb5-109">For more information, see [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
    1. <span data-ttu-id="ddfb5-110">Bu örnek için bir tanımlayıcı ad anahtarı oluşturun ve *FriendAssemblies. snk*dosyasında depolayın:</span><span class="sxs-lookup"><span data-stu-id="ddfb5-110">Generate a strong-name key for this example and store it in the file *FriendAssemblies.snk*:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2. <span data-ttu-id="ddfb5-111">Ortak anahtarı *FriendAssemblies. snk* konumundan ayıklayın ve *FriendAssemblies. PublicKey*dosyasına yerleştirin:</span><span class="sxs-lookup"><span data-stu-id="ddfb5-111">Extract the public key from *FriendAssemblies.snk* and put it into *FriendAssemblies.publickey*:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. <span data-ttu-id="ddfb5-112">*FriendAssemblies. PublicKey*dosyasında depolanan ortak anahtarı görüntüle:</span><span class="sxs-lookup"><span data-stu-id="ddfb5-112">Display the public key stored in the file *FriendAssemblies.publickey*:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. <span data-ttu-id="ddfb5-113">Aşağıdaki kodu C# içeren *friend_signed_A* adlı bir veya Visual Basic dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ddfb5-113">Create a C# or Visual Basic file named *friend_signed_A* that contains the following code.</span></span> <span data-ttu-id="ddfb5-114">Kod, *friend_signed_B* bir Friend derlemesi olarak bildirmek için <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ddfb5-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_signed_B* as a friend assembly.</span></span>  
   
   <span data-ttu-id="ddfb5-115">Tanımlayıcı ad aracı her çalıştığında yeni bir ortak anahtar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ddfb5-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="ddfb5-116">Bu nedenle, aşağıdaki örnekte gösterildiği gibi aşağıdaki koddaki ortak anahtarı yeni oluşturduğunuz ortak anahtarla değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="ddfb5-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  
   
   ```csharp  
   // friend_signed_A.cs  
   // Compile with:   
   // csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   using System.Runtime.CompilerServices;  
   
   [assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")]  
   class Class1  
   {  
       public void Test()  
       {  
           System.Console.WriteLine("Class1.Test");  
           System.Console.ReadLine();  
       }  
   }  
   ```  
   
   ```vb  
   ' friend_signed_A.vb  
   ' Compile with:   
   ' Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   Imports System.Runtime.CompilerServices  
   
   <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>   
   Public Class Class1  
       Public Sub Test()  
           System.Console.WriteLine("Class1.Test")  
           System.Console.ReadLine()  
       End Sub  
   End Class  
   ```  
   
4. <span data-ttu-id="ddfb5-117">Aşağıdaki komutu kullanarak *friend_signed_A* derleyin ve imzalayın.</span><span class="sxs-lookup"><span data-stu-id="ddfb5-117">Compile and sign *friend_signed_A* by using the following command.</span></span>  
   
   ```csharp
   csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   ```  
   
   ```vb
   Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   ```  
   
5. <span data-ttu-id="ddfb5-118">Aşağıdaki kodu C# içeren *friend_signed_B* adlı bir veya Visual Basic dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ddfb5-118">Create a C# or Visual Basic file named *friend_signed_B* that contains the following code.</span></span> <span data-ttu-id="ddfb5-119">*Friend_signed_A* , bir Friend derlemesi olarak *friend_signed_B* belirttiğinden, *friend_signed_B* içindeki kod `internal` (C#) veya `Friend` (Visual Basic) türlerine ve *friend_signed_A*' den üyelere erişebilir.</span><span class="sxs-lookup"><span data-stu-id="ddfb5-119">Because *friend_signed_A* specifies *friend_signed_B* as a friend assembly, the code in *friend_signed_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_signed_A*.</span></span> <span data-ttu-id="ddfb5-120">Dosya aşağıdaki kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="ddfb5-120">The file contains the following code.</span></span>  
   
   ```csharp  
   // friend_signed_B.cs  
   // Compile with:   
   // csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   public class Program  
   {  
       static void Main()  
       {  
           Class1 inst = new Class1();  
           inst.Test();  
       }  
   }  
   ```  
   
   ```vb  
   ' friend_signed_B.vb  
   ' Compile with:   
   ' Vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   Module Sample  
       Public Sub Main()  
           Dim inst As New Class1  
           inst.Test()  
       End Sub  
   End Module  
   ```  
   
6. <span data-ttu-id="ddfb5-121">Aşağıdaki komutu kullanarak *friend_signed_B* derleyin ve imzalayın.</span><span class="sxs-lookup"><span data-stu-id="ddfb5-121">Compile and sign *friend_signed_B* by using the following command.</span></span>  
   
   ```csharp
   csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   ```  
   
   ```vb
   vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   ```  
   
   <span data-ttu-id="ddfb5-122">Derleyici tarafından oluşturulan derlemenin adı, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliğine geçirilen arkadaş derleme adıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="ddfb5-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="ddfb5-123">@No__t_2 derleyici seçeneğini kullanarak çıkış derlemesinin ( *. exe* veya *. dll*) adını açıkça belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ddfb5-123">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `/out` compiler option.</span></span> <span data-ttu-id="ddfb5-124">Daha fazla bilgi için bkz. [/OutC# (derleyici seçenekleri)](../../csharp/language-reference/compiler-options/out-compiler-option.md) veya [-Out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="ddfb5-124">For more information, see [/out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>  
   
7. <span data-ttu-id="ddfb5-125">*Friend_signed_B. exe* dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ddfb5-125">Run the *friend_signed_B.exe* file.</span></span>  
   
   <span data-ttu-id="ddfb5-126">Program **Class1. test**dizesini çıktı.</span><span class="sxs-lookup"><span data-stu-id="ddfb5-126">The program outputs the string **Class1.Test**.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="ddfb5-127">.NET güvenliği</span><span class="sxs-lookup"><span data-stu-id="ddfb5-127">.NET security</span></span>  
 <span data-ttu-id="ddfb5-128">@No__t_0 özniteliği ve <xref:System.Security.Permissions.StrongNameIdentityPermission> sınıfı arasında benzerlikler vardır.</span><span class="sxs-lookup"><span data-stu-id="ddfb5-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="ddfb5-129">Temel fark, <xref:System.Security.Permissions.StrongNameIdentityPermission> kodun belirli bir bölümünü çalıştırmak için güvenlik izinleri talep edebilir, ancak <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelik `internal` (C#) veya `Friend` (Visual Basic) türlerinin ve üyelerinin görünürlüğünü denetler.</span><span class="sxs-lookup"><span data-stu-id="ddfb5-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddfb5-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ddfb5-130">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="ddfb5-131">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="ddfb5-131">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="ddfb5-132">Arkadaş derlemeleri</span><span class="sxs-lookup"><span data-stu-id="ddfb5-132">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="ddfb5-133">Nasıl yapılır: imzasız arkadaş derlemeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="ddfb5-133">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="ddfb5-134">-keyfile (C#)</span><span class="sxs-lookup"><span data-stu-id="ddfb5-134">-keyfile (C#)</span></span>](../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [<span data-ttu-id="ddfb5-135">-keyfile (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ddfb5-135">-keyfile (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="ddfb5-136">Sn. exe (tanımlayıcı ad aracı)</span><span class="sxs-lookup"><span data-stu-id="ddfb5-136">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="ddfb5-137">Tanımlayıcı adlı derlemeler oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="ddfb5-137">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="ddfb5-138">C#Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ddfb5-138">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="ddfb5-139">Programlama kavramları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ddfb5-139">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
