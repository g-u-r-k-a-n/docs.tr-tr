---
title: Derleme yüklerini çözme
description: Bu makalede .NET AppDomain. AssemblyResolve olayı açıklanır. Bu olayı, derleme yüklemesi üzerinde denetim gerektiren uygulamalar için kullanın.
ms.date: 12/15/2020
helpviewer_keywords:
- assemblies [.NET], resolving loads
- application domains, loading assemblies
- resolving assembly loads
- assemblies [.NET], loading
- application domains, resolving assembly loads
ms.assetid: 5099e549-f4fd-49fb-a290-549edd456c6a
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 63545db31a4290ce933da45c0957dfdb2a00701c
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97593870"
---
# <a name="resolve-assembly-loads"></a><span data-ttu-id="f1340-104">Derleme yüklerini çözme</span><span class="sxs-lookup"><span data-stu-id="f1340-104">Resolve assembly loads</span></span>

<span data-ttu-id="f1340-105">.NET, <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> derleme yüklemesi üzerinde daha fazla denetim gerektiren uygulamalar için olayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1340-105">.NET provides the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event for applications that require greater control over assembly loading.</span></span> <span data-ttu-id="f1340-106">Uygulamanız, bu olayı işleyerek, yük bağlamına normal yoklama yollarının dışından bir derleme yükleyebilir, kaç tane derleme sürümünden hangilerinin yükleneceğini seçebilir, dinamik bir derlemeyi yayarak ve bu şekilde devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="f1340-106">By handling this event, your application can load an assembly into the load context from outside the normal probing paths, select which of several assembly versions to load, emit a dynamic assembly and return it, and so on.</span></span> <span data-ttu-id="f1340-107">Bu konu, olayı işlemeye yönelik rehberlik sağlar <xref:System.AppDomain.AssemblyResolve> .</span><span class="sxs-lookup"><span data-stu-id="f1340-107">This topic provides guidance for handling the <xref:System.AppDomain.AssemblyResolve> event.</span></span>

> [!NOTE]
> <span data-ttu-id="f1340-108">Yalnızca yansıma bağlamındaki derleme yüklerini çözümlemek için, <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> bunun yerine olayını kullanın.</span><span class="sxs-lookup"><span data-stu-id="f1340-108">For resolving assembly loads in the reflection-only context, use the <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> event instead.</span></span>

## <a name="how-the-assemblyresolve-event-works"></a><span data-ttu-id="f1340-109">AssemblyResolve olayı nasıl kullanılır?</span><span class="sxs-lookup"><span data-stu-id="f1340-109">How the AssemblyResolve event works</span></span>

<span data-ttu-id="f1340-110">Olay için bir işleyici kaydettiğinizde <xref:System.AppDomain.AssemblyResolve> , çalışma zamanı bir derlemeye ada göre bağlama başarısız olduğunda işleyici çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f1340-110">When you register a handler for the <xref:System.AppDomain.AssemblyResolve> event, the handler is invoked whenever the runtime fails to bind to an assembly by name.</span></span> <span data-ttu-id="f1340-111">Örneğin, aşağıdaki yöntemleri kullanıcı kodundan çağırmak olayın oluşturulmasına neden olabilir <xref:System.AppDomain.AssemblyResolve> :</span><span class="sxs-lookup"><span data-stu-id="f1340-111">For example, calling the following methods from user code can cause the <xref:System.AppDomain.AssemblyResolve> event to be raised:</span></span>

- <span data-ttu-id="f1340-112"><xref:System.AppDomain.Load%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> İlk bağımsız değişkeni, yüklenecek derlemenin görünen adını temsil eden bir dize olan bir yöntem aşırı yüklemesi veya yöntem aşırı yüklemesi (yani, özelliği tarafından döndürülen dize <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> ).</span><span class="sxs-lookup"><span data-stu-id="f1340-112">An <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> method overload or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overload whose first argument is a string that represents the display name of the assembly to load (that is, the string returned by the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property).</span></span>

- <span data-ttu-id="f1340-113"><xref:System.AppDomain.Load%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> İlk bağımsız değişkeni yüklenecek derlemeyi tanımlayan bir nesne olan bir yöntem aşırı yüklemesi veya yöntem aşırı yüklemesi <xref:System.Reflection.AssemblyName> .</span><span class="sxs-lookup"><span data-stu-id="f1340-113">An <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> method overload or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overload whose first argument is an <xref:System.Reflection.AssemblyName> object that identifies the assembly to load.</span></span>

- <span data-ttu-id="f1340-114">Bir <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> yöntem aşırı yüklemesi.</span><span class="sxs-lookup"><span data-stu-id="f1340-114">An <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> method overload.</span></span>

- <span data-ttu-id="f1340-115"><xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType>Başka bir <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> uygulama etki alanındaki bir nesneyi örnekleyen bir veya yöntem aşırı yüklemesi.</span><span class="sxs-lookup"><span data-stu-id="f1340-115">An <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> method overload that instantiates an object in another application domain.</span></span>

## <a name="what-the-event-handler-does"></a><span data-ttu-id="f1340-116">Olay işleyicisinin yaptığı</span><span class="sxs-lookup"><span data-stu-id="f1340-116">What the event handler does</span></span>

<span data-ttu-id="f1340-117">Olay işleyicisi, <xref:System.AppDomain.AssemblyResolve> özelliğindeki, yüklenecek derlemenin görünen adını alır <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f1340-117">The handler for the <xref:System.AppDomain.AssemblyResolve> event receives the display name of the assembly to be loaded, in the <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="f1340-118">İşleyici derleme adını tanımıyorsa, `null` (C#), `Nothing` (Visual Basic) veya `nullptr` (Visual C++) döndürür.</span><span class="sxs-lookup"><span data-stu-id="f1340-118">If the handler does not recognize the assembly name, it returns `null` (C#), `Nothing` (Visual Basic), or `nullptr` (Visual C++).</span></span>

<span data-ttu-id="f1340-119">İşleyici derleme adını tanırsa, isteği karşılayan bir derlemeyi yükleyebilir ve döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="f1340-119">If the handler recognizes the assembly name, it can load and return an assembly that satisfies the request.</span></span> <span data-ttu-id="f1340-120">Aşağıdaki listede bazı örnek senaryolar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f1340-120">The following list describes some sample scenarios.</span></span>

- <span data-ttu-id="f1340-121">İşleyici derlemenin bir sürümünün konumunu biliyorsa, veya yöntemini kullanarak derlemeyi yükleyebilir <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> ve başarılı olursa yüklenen derlemeyi döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="f1340-121">If the handler knows the location of a version of the assembly, it can load the assembly by using the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> method, and can return the loaded assembly if successful.</span></span>

- <span data-ttu-id="f1340-122">İşleyicinin bayt dizileri olarak depolanan derlemelerin bir veritabanına erişimi varsa, bir bayt dizisi alan aşırı yüklerden birini kullanarak bir bayt dizisi yükleyebilir <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f1340-122">If the handler has access to a database of assemblies stored as byte arrays, it can load a byte array by using one of the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overloads that take a byte array.</span></span>

- <span data-ttu-id="f1340-123">İşleyici dinamik bir derleme üretebilir ve döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="f1340-123">The handler can generate a dynamic assembly and return it.</span></span>

> [!NOTE]
> <span data-ttu-id="f1340-124">İşleyici, derlemeyi yük bağlamı içine, yük bağlamına veya Bağlamsız olarak yüklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1340-124">The handler must load the assembly into the load-from context, into the load context, or without context.</span></span> <span data-ttu-id="f1340-125">İşleyici, veya yöntemini kullanarak derlemeyi yalnızca yansıma bağlamına yüklerse, <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> olayı oluşturan yükleme girişimi <xref:System.AppDomain.AssemblyResolve> başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="f1340-125">If the handler loads the assembly into the reflection-only context by using the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> or the <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> method, the load attempt that raised the <xref:System.AppDomain.AssemblyResolve> event fails.</span></span>

<span data-ttu-id="f1340-126">Bu, uygun bir derlemeyi döndürecek olay işleyicisinin sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="f1340-126">It is the responsibility of the event handler to return a suitable assembly.</span></span> <span data-ttu-id="f1340-127">İşleyici, özellik değerini oluşturucuya geçirerek, istenen derlemenin görünen adını ayrıştırtırabilir <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> .</span><span class="sxs-lookup"><span data-stu-id="f1340-127">The handler can parse the display name of the requested assembly by passing the <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> property value to the <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> constructor.</span></span> <span data-ttu-id="f1340-128">.NET Framework 4 ' ten başlayarak, işleyici, <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> geçerli isteğin başka bir derlemenin bağımlılığı olup olmadığını bulmak için özelliğini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="f1340-128">Beginning with the .NET Framework 4, the handler can use the <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property to determine whether the current request is a dependency of another assembly.</span></span> <span data-ttu-id="f1340-129">Bu bilgiler, bağımlılığı karşılayan bir derlemeyi belirlemesine yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f1340-129">This information can help identify an assembly that will satisfy the dependency.</span></span>

<span data-ttu-id="f1340-130">Olay işleyicisi derlemenin farklı bir sürümünü istenen sürümden döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="f1340-130">The event handler can return a different version of the assembly than the version that was requested.</span></span>

<span data-ttu-id="f1340-131">Çoğu durumda, işleyici tarafından döndürülen derleme, işleyicinin onu içine yüklediği bağlamdan bağımsız olarak yükleme bağlamında görünür.</span><span class="sxs-lookup"><span data-stu-id="f1340-131">In most cases, the assembly that is returned by the handler appears in the load context, regardless of the context the handler loads it into.</span></span> <span data-ttu-id="f1340-132">Örneğin, işleyici <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> bir derlemeyi yük-from bağlamına yüklemek için yöntemini kullanıyorsa, işleyici onu döndürdüğünde, derleme yükleme bağlamında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f1340-132">For example, if the handler uses the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method to load an assembly into the load-from context, the assembly appears in the load context when the handler returns it.</span></span> <span data-ttu-id="f1340-133">Ancak, aşağıdaki örnekte, işleyici onu döndürdüğünde derleme bağlam olmadan görünür:</span><span class="sxs-lookup"><span data-stu-id="f1340-133">However, in the following case the assembly appears without context when the handler returns it:</span></span>

- <span data-ttu-id="f1340-134">İşleyici bağlamı olmayan bir derlemeyi yükler.</span><span class="sxs-lookup"><span data-stu-id="f1340-134">The handler loads an assembly without context.</span></span>

- <span data-ttu-id="f1340-135"><xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType>Özellik null değil.</span><span class="sxs-lookup"><span data-stu-id="f1340-135">The <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property is not null.</span></span>

- <span data-ttu-id="f1340-136">İstekte bulunan derleme (diğer bir deyişle, özelliği tarafından döndürülen derleme), <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> bağlamı olmadan yükleniydi.</span><span class="sxs-lookup"><span data-stu-id="f1340-136">The requesting assembly (that is, the assembly that is returned by the <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property) was loaded without context.</span></span>

<span data-ttu-id="f1340-137">Bağlamlar hakkında bilgi için bkz <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> . yöntem aşırı yüklemesi.</span><span class="sxs-lookup"><span data-stu-id="f1340-137">For information about contexts, see the <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> method overload.</span></span>

<span data-ttu-id="f1340-138">Aynı derlemenin birden çok sürümü aynı uygulama etki alanına yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="f1340-138">Multiple versions of the same assembly can be loaded into the same application domain.</span></span> <span data-ttu-id="f1340-139">Tür atama sorunlarına yol açabildiğinden bu uygulama önerilmez.</span><span class="sxs-lookup"><span data-stu-id="f1340-139">This practice is not recommended, because it can lead to type assignment problems.</span></span> <span data-ttu-id="f1340-140">Bkz. [derleme yüklemesi Için en iyi uygulamalar](../../framework/deployment/best-practices-for-assembly-loading.md).</span><span class="sxs-lookup"><span data-stu-id="f1340-140">See [Best practices for assembly loading](../../framework/deployment/best-practices-for-assembly-loading.md).</span></span>

## <a name="what-the-event-handler-should-not-do"></a><span data-ttu-id="f1340-141">Olay işleyicisinin yapması gereken</span><span class="sxs-lookup"><span data-stu-id="f1340-141">What the event handler should not do</span></span>

<span data-ttu-id="f1340-142">Olayı işlemeye yönelik birincil kural, <xref:System.AppDomain.AssemblyResolve> tanımadığınız bir derlemeyi döndürmeye çalışmayın.</span><span class="sxs-lookup"><span data-stu-id="f1340-142">The primary rule for handling the <xref:System.AppDomain.AssemblyResolve> event is that you should not try to return an assembly you do not recognize.</span></span> <span data-ttu-id="f1340-143">İşleyiciyi yazdığınızda hangi derlemelerin olay oluşturulmasına neden olabileceğini bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1340-143">When you write the handler, you should know which assemblies might cause the event to be raised.</span></span> <span data-ttu-id="f1340-144">İşleyiciniz diğer derlemeler için null değer döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="f1340-144">Your handler should return null for other assemblies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f1340-145">.NET Framework 4 ' ten başlayarak, <xref:System.AppDomain.AssemblyResolve> etkinlik uydu derlemeleri için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f1340-145">Beginning with the .NET Framework 4, the <xref:System.AppDomain.AssemblyResolve> event is raised for satellite assemblies.</span></span> <span data-ttu-id="f1340-146">Bu değişiklik, işleyici tüm derleme yükleme isteklerini çözümlemeye çalışırsa .NET Framework önceki bir sürümü için yazılmış bir olay işleyicisini etkiler.</span><span class="sxs-lookup"><span data-stu-id="f1340-146">This change affects an event handler that was written for an earlier version of the .NET Framework, if the handler tries to resolve all assembly load requests.</span></span> <span data-ttu-id="f1340-147">Tanımadığı derlemeleri yoksaymayan olay işleyicileri bu değişiklikten etkilenmez: döndürürler `null` ve normal geri dönüş mekanizmaları izlenir.</span><span class="sxs-lookup"><span data-stu-id="f1340-147">Event handlers that ignore assemblies they do not recognize are not affected by this change: They return `null`, and normal fallback mechanisms are followed.</span></span>

<span data-ttu-id="f1340-148">Bir derlemeyi yüklerken olay işleyicisi, <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> olayın yinelemeli olarak oluşturulmasına neden olabilecek bir veya yöntem aşırı yüklerini kullanmamalıdır <xref:System.AppDomain.AssemblyResolve> , çünkü bu bir yığın taşmasına yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="f1340-148">When loading an assembly, the event handler must not use any of the <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overloads that can cause the <xref:System.AppDomain.AssemblyResolve> event to be raised recursively, because this can lead to a stack overflow.</span></span> <span data-ttu-id="f1340-149">(Bu konunun önceki kısımlarında sunulan listeye bakın.) Tüm olay işleyicileri döndürülünceye kadar hiçbir özel durum oluşturulmadığından, yükleme isteği için özel durum işleme sağlıyorsanız bile bu durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="f1340-149">(See the list provided earlier in this topic.) This happens even if you provide exception handling for the load request, because no exception is thrown until all event handlers have returned.</span></span> <span data-ttu-id="f1340-150">Bu nedenle, aşağıdaki kod, bulunmazsa bir yığın taşmasına neden `MyAssembly` olur:</span><span class="sxs-lookup"><span data-stu-id="f1340-150">Thus, the following code results in a stack overflow if `MyAssembly` is not found:</span></span>

```csharp
using System;
using System.Reflection;

class BadExample
{
    static void Main()
    {
        AppDomain ad = AppDomain.CreateDomain("Test");
        ad.AssemblyResolve += MyHandler;

        try
        {
            object obj = ad.CreateInstanceAndUnwrap(
                "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
                "MyType");
        }
        catch (Exception ex)
        {
            Console.WriteLine(ex.Message);
        }
    }

    static Assembly MyHandler(object source, ResolveEventArgs e)
    {
        Console.WriteLine("Resolving {0}", e.Name);
        // DO NOT DO THIS: This causes a StackOverflowException
        return Assembly.Load(e.Name);
    }
}

/* This example produces output similar to the following:

Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
...
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null

Process is terminated due to StackOverflowException.
 */
```

```vb
Imports System.Reflection

Class BadExample

    Shared Sub Main()

        Dim ad As AppDomain = AppDomain.CreateDomain("Test")
        AddHandler ad.AssemblyResolve, AddressOf MyHandler

        Try
            Dim obj As object = ad.CreateInstanceAndUnwrap(
                "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
                "MyType")
        Catch ex As Exception
            Console.WriteLine(ex.Message)
        End Try
    End Sub

    Shared Function MyHandler(ByVal source As Object, _
                              ByVal e As ResolveEventArgs) As Assembly
        Console.WriteLine("Resolving {0}", e.Name)
        // DO NOT DO THIS: This causes a StackOverflowException
        Return Assembly.Load(e.Name)
    End Function
End Class

' This example produces output similar to the following:
'
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'...
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'
'Process is terminated due to StackOverflowException.
```

```cpp
using namespace System;
using namespace System::Reflection;

ref class Example
{
internal:
    static Assembly^ MyHandler(Object^ source, ResolveEventArgs^ e)
    {
        Console::WriteLine("Resolving {0}", e->Name);
        // DO NOT DO THIS: This causes a StackOverflowException
        return Assembly::Load(e->Name);
    }
};

void main()
{
    AppDomain^ ad = AppDomain::CreateDomain("Test");
    ad->AssemblyResolve += gcnew ResolveEventHandler(&Example::MyHandler);

    try
    {
        Object^ obj = ad->CreateInstanceAndUnwrap(
            "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
            "MyType");
    }
    catch (Exception^ ex)
    {
        Console::WriteLine(ex->Message);
    }
}

/* This example produces output similar to the following:

Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
...
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null

Process is terminated due to StackOverflowException.
*/
```

### <a name="the-correct-way-to-handle-assemblyresolve"></a><span data-ttu-id="f1340-151">AssemblyResolve işlemenin doğru yolu</span><span class="sxs-lookup"><span data-stu-id="f1340-151">The correct way to handle AssemblyResolve</span></span>

<span data-ttu-id="f1340-152"><xref:System.AppDomain.AssemblyResolve>Olay işleyiciden derlemeler çözümlenirken, <xref:System.StackOverflowException> işleyicinin <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> veya yöntem çağrılarını kullanması durumunda, bir sonuç olarak oluşturulur <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f1340-152">When resolving assemblies from the <xref:System.AppDomain.AssemblyResolve> event handler, a <xref:System.StackOverflowException> will eventually be thrown if the handler uses the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> method calls.</span></span> <span data-ttu-id="f1340-153">Bunun yerine, <xref:System.Reflection.Assembly.LoadFile%2A> <xref:System.Reflection.Assembly.LoadFrom%2A> olayı yükseltmediğinden veya yöntemlerini kullanın `AssemblyResolve` .</span><span class="sxs-lookup"><span data-stu-id="f1340-153">Instead, use <xref:System.Reflection.Assembly.LoadFile%2A> or <xref:System.Reflection.Assembly.LoadFrom%2A> methods, as they do not raise the `AssemblyResolve` event.</span></span>

<span data-ttu-id="f1340-154">`MyAssembly.dll`Yürütülen derlemenin yakınında, bilinen bir konumda bulunan, derlemenin yolu kullanılarak çözülebildiği hakkında düşünün `Assembly.LoadFile` .</span><span class="sxs-lookup"><span data-stu-id="f1340-154">Imagine that `MyAssembly.dll` is located near the executing assembly, in a known location, it can be resolved using `Assembly.LoadFile` given the path to the assembly.</span></span>

```csharp
using System;
using System.IO;
using System.Reflection;

class CorrectExample
{
    static void Main()
    {
        AppDomain ad = AppDomain.CreateDomain("Test");
        ad.AssemblyResolve += MyHandler;

        try
        {
            object obj = ad.CreateInstanceAndUnwrap(
                "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
                "MyType");
        }
        catch (Exception ex)
        {
            Console.WriteLine(ex.Message);
        }
    }

    static Assembly MyHandler(object source, ResolveEventArgs e)
    {
        Console.WriteLine("Resolving {0}", e.Name);

        var path = Path.GetFullPath("../../MyAssembly.dll");
        return Assembly.LoadFile(path);
     }
}
```

```vb
Imports System.IO
Imports System.Reflection

Class CorrectExample

    Shared Sub Main()

        Dim ad As AppDomain = AppDomain.CreateDomain("Test")
        AddHandler ad.AssemblyResolve, AddressOf MyHandler

        Try
            Dim obj As Object = ad.CreateInstanceAndUnwrap(
                "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
                "MyType")
        Catch ex As Exception
            Console.WriteLine(ex.Message)
        End Try
    End Sub

    Shared Function MyHandler(ByVal source As Object,
                              ByVal e As ResolveEventArgs) As Assembly
        Console.WriteLine("Resolving {0}", e.Name)

        Dim fullPath = Path.GetFullPath("../../MyAssembly.dll")
        Return Assembly.LoadFile(fullPath)
    End Function
End Class
```

```cpp
using namespace System;
using namespace System::IO;
using namespace System::Reflection;

ref class Example
{
internal:
    static Assembly^ MyHandler(Object^ source, ResolveEventArgs^ e)
    {
        Console::WriteLine("Resolving {0}", e->Name);

        String^ fullPath = Path::GetFullPath("../../MyAssembly.dll");
        return Assembly::LoadFile(fullPath);
    }
};

void main()
{
    AppDomain^ ad = AppDomain::CreateDomain("Test");
    ad->AssemblyResolve += gcnew ResolveEventHandler(&Example::MyHandler);

    try
    {
        Object^ obj = ad->CreateInstanceAndUnwrap(
            "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
            "MyType");
    }
    catch (Exception^ ex)
    {
        Console::WriteLine(ex->Message);
    }
}
```

## <a name="see-also"></a><span data-ttu-id="f1340-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1340-155">See also</span></span>

- [<span data-ttu-id="f1340-156">Derleme yükleme için en iyi uygulamalar</span><span class="sxs-lookup"><span data-stu-id="f1340-156">Best practices for assembly loading</span></span>](../../framework/deployment/best-practices-for-assembly-loading.md)
- [<span data-ttu-id="f1340-157">Uygulama etki alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="f1340-157">Use application domains</span></span>](../../framework/app-domains/use.md)
