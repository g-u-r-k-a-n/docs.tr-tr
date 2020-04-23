---
title: Giriş Noktası Belirtme
ms.date: 03/30/2017
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
ms.openlocfilehash: c5f8f735dd3e8c359f88044a532c29303237acc8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181306"
---
# <a name="specifying-an-entry-point"></a><span data-ttu-id="c4cef-102">Giriş Noktası Belirtme</span><span class="sxs-lookup"><span data-stu-id="c4cef-102">Specifying an Entry Point</span></span>

<span data-ttu-id="c4cef-103">Bir giriş noktası, bir işlevin bir DLL içindeki konumunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c4cef-103">An entry point identifies the location of a function in a DLL.</span></span> <span data-ttu-id="c4cef-104">Yönetilen bir proje içinde, bir hedef işlevin özgün adı veya sıra giriş noktası, birlikte çalışabilirlik sınırında bu işlevi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c4cef-104">Within a managed project, the original name or ordinal entry point of a target function identifies that function across the interoperation boundary.</span></span> <span data-ttu-id="c4cef-105">Ayrıca, işlemi etkin şekilde yeniden adlandırarak giriş noktasını farklı bir adla eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4cef-105">Further, you can map the entry point to a different name, effectively renaming the function.</span></span>  
  
 <span data-ttu-id="c4cef-106">Bir DLL işlevini yeniden adlandırmak için olası nedenlerinin bir listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c4cef-106">The following is a list of possible reasons to rename a DLL function:</span></span>  
  
- <span data-ttu-id="c4cef-107">Büyük/küçük harf duyarlı API işlev adlarını kullanmaktan kaçınmak için</span><span class="sxs-lookup"><span data-stu-id="c4cef-107">To avoid using case-sensitive API function names</span></span>  
  
- <span data-ttu-id="c4cef-108">Varolan adlandırma standartlarına uymak için</span><span class="sxs-lookup"><span data-stu-id="c4cef-108">To comply with existing naming standards</span></span>  
  
- <span data-ttu-id="c4cef-109">Farklı veri türleri alan işlevleri barındırmak için (aynı DLL işlevinin birden çok sürümünü bildirerek)</span><span class="sxs-lookup"><span data-stu-id="c4cef-109">To accommodate functions that take different data types (by declaring multiple versions of the same DLL function)</span></span>  
  
- <span data-ttu-id="c4cef-110">ANSI ve Unicode sürümlerini içeren API'leri kullanmayı kolaylaştırmak için</span><span class="sxs-lookup"><span data-stu-id="c4cef-110">To simplify using APIs that contain ANSI and Unicode versions</span></span>  
  
 <span data-ttu-id="c4cef-111">Bu konu, bir DLL işlevinin yönetilen kod içinde nasıl yeniden adlandıracağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4cef-111">This topic demonstrates how to rename a DLL function in managed code.</span></span>  
  
## <a name="renaming-a-function-in-visual-basic"></a><span data-ttu-id="c4cef-112">Visual Basic'te bir İşlevi Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="c4cef-112">Renaming a Function in Visual Basic</span></span>  

<span data-ttu-id="c4cef-113">Visual Basic, <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> alanı ayarlamak için **Declare** deyimindeki **Function** anahtar sözcüğünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4cef-113">Visual Basic uses the **Function** keyword in the **Declare** statement to set the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field.</span></span> <span data-ttu-id="c4cef-114">Aşağıdaki örnek, temel bir bildirimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4cef-114">The following example shows a basic declaration.</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
<span data-ttu-id="c4cef-115">Aşağıdaki örnekte gösterildiği gibi, tanımınıza **diğer ad** anahtar sözcüğünü ekleyerek **MessageBox** giriş noktasını **MsgBox** ile değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4cef-115">You can replace the **MessageBox** entry point with **MsgBox** by including the **Alias** keyword in your definition, as shown in the following example.</span></span> <span data-ttu-id="c4cef-116">Her iki örnekte de **Auto** anahtar sözcüğü, giriş noktasının karakter kümesi sürümünü belirtme gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c4cef-116">In both examples the **Auto** keyword eliminates the need to specify the character-set version of the entry point.</span></span> <span data-ttu-id="c4cef-117">Bir karakter kümesi seçme hakkında daha fazla bilgi için bkz. [bir karakter kümesi belirtme](specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="c4cef-117">For more information about selecting a character set, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MsgBox _
        Lib "user32.dll" Alias "MessageBox" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="renaming-a-function-in-c-and-c"></a><span data-ttu-id="c4cef-118">C# ve C++'de bir İşlevi Yeniden Adlandırma</span><span class="sxs-lookup"><span data-stu-id="c4cef-118">Renaming a Function in C# and C++</span></span>  
 <span data-ttu-id="c4cef-119">Bir DLL işlevini ada veya sıraya göre belirtmek için <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> alanını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4cef-119">You can use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field to specify a DLL function by name or ordinal.</span></span> <span data-ttu-id="c4cef-120">Yöntem tanımınızdaki işlevin adı DLL 'deki giriş noktasıyla aynıysa, işlevi **entryPoint** alanı ile açıkça belirlemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c4cef-120">If the name of the function in your method definition is the same as the entry point in the DLL, you do not have to explicitly identify the function with the **EntryPoint** field.</span></span> <span data-ttu-id="c4cef-121">Aksi halde, bir ad veya sıra belirtmek için aşağıdaki öznitelik biçimlerinden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="c4cef-121">Otherwise, use one of the following attribute forms to indicate a name or ordinal:</span></span>  
  
```csharp
[DllImport("DllName", EntryPoint = "Functionname")]
[DllImport("DllName", EntryPoint = "#123")]
```
  
 <span data-ttu-id="c4cef-122">Bir sıralı sayıyı (#) işareti ile kullanmanız gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c4cef-122">Notice that you must prefix an ordinal with the pound sign (#).</span></span>  
  
 <span data-ttu-id="c4cef-123">Aşağıdaki örnek, **giriş noktası** alanını kullanarak kodunuzda bir **MsgBox** ile **MessageBoxA** 'nın nasıl değiştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4cef-123">The following example demonstrates how to replace **MessageBoxA** with **MsgBox** in your code by using the **EntryPoint** field.</span></span>  
  
```csharp
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
{
    [DllImport("user32.dll", EntryPoint = "MessageBoxA")]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```
  
```cpp
using namespace System;
using namespace System::Runtime::InteropServices;

typedef void* HWND;
[DllImport("user32", EntryPoint = "MessageBoxA")]
extern "C" int MsgBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="see-also"></a><span data-ttu-id="c4cef-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4cef-124">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="c4cef-125">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c4cef-125">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="c4cef-126">Platform Çağırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="c4cef-126">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="c4cef-127">Platform Çağırma ile Veri Sıralama</span><span class="sxs-lookup"><span data-stu-id="c4cef-127">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
