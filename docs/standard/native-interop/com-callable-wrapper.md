---
title: COM Aranabilir Sarmalayıcısı
description: Bir COM istemcisi .NET nesnesini çağırdığında, CLR tarafından yönetilen nesne ve COM çağrılabilir bir sarmalayıcı oluşturulur. COM istemcileri nesne için sarmalayıcı çağırır.
ms.date: 10/23/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CCW
- COM interop, COM wrappers
- COM wrappers
- callable wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: d04be3b5-27b9-4f5b-8469-a44149fabf78
ms.openlocfilehash: cc27ba47c88d424a80eb47aaa310bdfd6d18433a
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93187924"
---
# <a name="com-callable-wrapper"></a><span data-ttu-id="d332f-104">COM Aranabilir Sarmalayıcısı</span><span class="sxs-lookup"><span data-stu-id="d332f-104">COM Callable Wrapper</span></span>

<span data-ttu-id="d332f-105">Bir COM istemcisi .NET nesnesini çağırdığında, ortak dil çalışma zamanı, yönetilen nesneyi ve nesne için COM çağrılabilir sarmalayıcı (CCW) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d332f-105">When a COM client calls a .NET object, the common language runtime creates the managed object and a COM callable wrapper (CCW) for the object.</span></span> <span data-ttu-id="d332f-106">Doğrudan bir .NET nesnesine başvuru yapılamıyor COM istemcileri, yönetilen nesne için bir proxy olarak CCW kullanır.</span><span class="sxs-lookup"><span data-stu-id="d332f-106">Unable to reference a .NET object directly, COM clients use the CCW as a proxy for the managed object.</span></span>

<span data-ttu-id="d332f-107">Çalışma zamanı, kendi hizmetlerini isteyen COM istemcilerinin sayısından bağımsız olarak, yönetilen bir nesne için tam olarak bir CCW oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d332f-107">The runtime creates exactly one CCW for a managed object, regardless of the number of COM clients requesting its services.</span></span> <span data-ttu-id="d332f-108">Aşağıdaki çizimde gösterildiği gibi, birden fazla COM istemcisi, INew arabirimini kullanıma sunan CCW bir başvuru tutabilir.</span><span class="sxs-lookup"><span data-stu-id="d332f-108">As the following illustration shows, multiple COM clients can hold a reference to the CCW that exposes the INew interface.</span></span> <span data-ttu-id="d332f-109">CCW, sırasıyla, arabirimini uygulayan ve atık olarak toplanan yönetilen nesneye tek bir başvuru içerir.</span><span class="sxs-lookup"><span data-stu-id="d332f-109">The CCW, in turn, holds a single reference to the managed object that implements the interface and is garbage collected.</span></span> <span data-ttu-id="d332f-110">Hem COM hem de .NET istemcileri aynı yönetilen nesne üzerinde aynı anda istek yapabilir.</span><span class="sxs-lookup"><span data-stu-id="d332f-110">Both COM and .NET clients can make requests on the same managed object simultaneously.</span></span>

![INew 'yi ortaya çıkaran CCW başvurusunu tutan birden fazla COM istemcisi.](./media/com-callable-wrapper/com-callable-wrapper-clients.gif)

<span data-ttu-id="d332f-112">COM çağrılabilir sarmalayıcılar, .NET çalışma zamanı içinde çalışan diğer sınıfların görünmez hale gelir.</span><span class="sxs-lookup"><span data-stu-id="d332f-112">COM callable wrappers are invisible to other classes running within the .NET runtime.</span></span> <span data-ttu-id="d332f-113">Birincil amacı yönetilen ve yönetilmeyen kod arasındaki çağrıları sıralayamaz; Ancak CCWs, sardıkları yönetilen nesnelerin nesne kimliğini ve nesne ömrünü de yönetebilir.</span><span class="sxs-lookup"><span data-stu-id="d332f-113">Their primary purpose is to marshal calls between managed and unmanaged code; however, CCWs also manage the object identity and object lifetime of the managed objects they wrap.</span></span>

## <a name="object-identity"></a><span data-ttu-id="d332f-114">Nesne Kimliği</span><span class="sxs-lookup"><span data-stu-id="d332f-114">Object Identity</span></span>

<span data-ttu-id="d332f-115">Çalışma zamanı, bir .NET nesnesi için bellek ayırır ve bu, çalışma zamanının nesneyi gerektiği şekilde belleğin etrafında taşımasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d332f-115">The runtime allocates memory for the .NET object from its garbage-collected heap, which enables the runtime to move the object around in memory as necessary.</span></span> <span data-ttu-id="d332f-116">Buna karşılık, çalışma zamanı, toplanan bir yığından CCW için bellek ayırır ve COM istemcilerinin doğrudan sarmalayıcı 'a başvurmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d332f-116">In contrast, the runtime allocates memory for the CCW from a noncollected heap, making it possible for COM clients to reference the wrapper directly.</span></span>

## <a name="object-lifetime"></a><span data-ttu-id="d332f-117">Nesne ömrü</span><span class="sxs-lookup"><span data-stu-id="d332f-117">Object Lifetime</span></span>

<span data-ttu-id="d332f-118">Sarmaladığı .NET istemcisinin aksine, CCW başvurusu geleneksel COM olarak sayılır.</span><span class="sxs-lookup"><span data-stu-id="d332f-118">Unlike the .NET client it wraps, the CCW is reference-counted in traditional COM fashion.</span></span> <span data-ttu-id="d332f-119">CCW üzerindeki başvuru sayısı sıfıra ulaştığında, sarmalayıcı yönetilen nesne üzerinde başvurusunu serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="d332f-119">When the reference count on the CCW reaches zero, the wrapper releases its reference on the managed object.</span></span> <span data-ttu-id="d332f-120">Sonraki atık toplama çevrimi sırasında kalan başvuruları olmayan yönetilen bir nesne toplanır.</span><span class="sxs-lookup"><span data-stu-id="d332f-120">A managed object with no remaining references is collected during the next garbage-collection cycle.</span></span>

## <a name="simulating-com-interfaces"></a><span data-ttu-id="d332f-121">COM arabirimlerinin benzetimi yapma</span><span class="sxs-lookup"><span data-stu-id="d332f-121">Simulating COM interfaces</span></span>

<span data-ttu-id="d332f-122">CCW tüm genel, COM görünebilir arabirimleri, veri türlerini ve dönüş değerlerini com istemcilerine COM 'un arabirim tabanlı etkileşim zorlaması ile tutarlı bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="d332f-122">CCW exposes all public, COM-visible interfaces, data types, and return values to COM clients in a manner that is consistent with COM's enforcement of interface-based interaction.</span></span> <span data-ttu-id="d332f-123">Bir COM istemcisi için, bir .NET nesnesi üzerinde Yöntemler çağırma bir COM nesnesi üzerinde Yöntemler çağırma ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="d332f-123">For a COM client, invoking methods on a .NET object is identical to invoking methods on a COM object.</span></span>

<span data-ttu-id="d332f-124">Bu sorunsuz yaklaşımı oluşturmak için CCW, **IUnknown** ve **ıDISPATCH** gibi geleneksel com arabirimleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d332f-124">To create this seamless approach, the CCW manufactures traditional COM interfaces, such as **IUnknown** and **IDispatch** .</span></span> <span data-ttu-id="d332f-125">Aşağıdaki çizimde gösterildiği gibi CCW, sarmaladığı .NET nesnesinde tek bir başvuru tutar.</span><span class="sxs-lookup"><span data-stu-id="d332f-125">As the following illustration shows, the CCW maintains a single reference on the .NET object that it wraps.</span></span> <span data-ttu-id="d332f-126">Hem COM istemcisi hem de .NET nesnesi, CCW için proxy ve saplama oluşturma aracılığıyla birbirleriyle etkileşime geçer.</span><span class="sxs-lookup"><span data-stu-id="d332f-126">Both the COM client and the .NET object interact with each other through the proxy and stub construction of the CCW.</span></span>

![CCW 'in COM arabirimlerini nasıl kullandığını gösteren diyagram.](./media/com-callable-wrapper/com-callable-wrapper-interfaces.gif)

<span data-ttu-id="d332f-128">.NET çalışma zamanı, yönetilen ortamdaki bir sınıf tarafından açıkça uygulanan arabirimleri açığa çıkarmasına ek olarak, nesne adına aşağıdaki tabloda listelenen COM arabirimlerinin uygulamalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d332f-128">In addition to exposing the interfaces that are explicitly implemented by a class in the managed environment, the .NET runtime supplies implementations of the COM interfaces listed in the following table on behalf of the object.</span></span> <span data-ttu-id="d332f-129">.NET sınıfı, bu arabirimlerin kendi uygulamasını sağlayarak varsayılan davranışı geçersiz kılabilir.</span><span class="sxs-lookup"><span data-stu-id="d332f-129">A .NET class can override the default behavior by providing its own implementation of these interfaces.</span></span> <span data-ttu-id="d332f-130">Ancak çalışma zamanı her zaman **IUnknown** ve **IDispatch** arabirimlerinin uygulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d332f-130">However, the runtime always provides the implementation for the **IUnknown** and **IDispatch** interfaces.</span></span>

|<span data-ttu-id="d332f-131">Arabirim</span><span class="sxs-lookup"><span data-stu-id="d332f-131">Interface</span></span>|<span data-ttu-id="d332f-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d332f-132">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="d332f-133">**IDispatch**</span><span class="sxs-lookup"><span data-stu-id="d332f-133">**IDispatch**</span></span>|<span data-ttu-id="d332f-134">Türe geç bağlama için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="d332f-134">Provides a mechanism for late binding to type.</span></span>|
|<span data-ttu-id="d332f-135">**IErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="d332f-135">**IErrorInfo**</span></span>|<span data-ttu-id="d332f-136">Hatanın metinsel bir açıklamasını, kaynağını, bir yardım dosyasını, yardım bağlamını ve hatayı tanımlayan arabirimin GUID 'sini (her zaman .NET sınıfları için **GUID_NULL** ) sağlar.</span><span class="sxs-lookup"><span data-stu-id="d332f-136">Provides a textual description of the error, its source, a Help file, Help context, and the GUID of the interface that defined the error (always **GUID_NULL** for .NET classes).</span></span>|
|<span data-ttu-id="d332f-137">**IProvideClassInfo**</span><span class="sxs-lookup"><span data-stu-id="d332f-137">**IProvideClassInfo**</span></span>|<span data-ttu-id="d332f-138">COM istemcilerinin yönetilen bir sınıf tarafından uygulanan **ITypeInfo** arabirimine erişim sağlamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d332f-138">Enables COM clients to gain access to the **ITypeInfo** interface implemented by a managed class.</span></span> <span data-ttu-id="d332f-139">`COR_E_NOTSUPPORTED`Com 'dan içeri aktarılmayan türler için .NET Core ' u döndürür.</span><span class="sxs-lookup"><span data-stu-id="d332f-139">Returns `COR_E_NOTSUPPORTED` on .NET Core for types not imported from COM.</span></span> |
|<span data-ttu-id="d332f-140">**Iupporterrorınfo**</span><span class="sxs-lookup"><span data-stu-id="d332f-140">**ISupportErrorInfo**</span></span>|<span data-ttu-id="d332f-141">Bir COM istemcisinin, yönetilen nesnenin **IErrorInfo** arabirimini destekleyip desteklemediğini belirlemesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d332f-141">Enables a COM client to determine whether the managed object supports the **IErrorInfo** interface.</span></span> <span data-ttu-id="d332f-142">Bu durumda, istemcinin en son özel durum nesnesine bir işaretçi almasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d332f-142">If so, enables the client to obtain a pointer to the latest exception object.</span></span> <span data-ttu-id="d332f-143">Tüm yönetilen türler **IErrorInfo** arabirimini destekler.</span><span class="sxs-lookup"><span data-stu-id="d332f-143">All managed types support the **IErrorInfo** interface.</span></span>|
|<span data-ttu-id="d332f-144">**ITypeInfo** (yalnızca .NET Framework)</span><span class="sxs-lookup"><span data-stu-id="d332f-144">**ITypeInfo** (.NET Framework only)</span></span>|<span data-ttu-id="d332f-145">Tlbexp.exe tarafından üretilen tür bilgileriyle tam olarak aynı olan bir sınıf için tür bilgisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d332f-145">Provides type information for a class that is exactly the same as the type information produced by Tlbexp.exe.</span></span>|
|<span data-ttu-id="d332f-146">**IUnknown**</span><span class="sxs-lookup"><span data-stu-id="d332f-146">**IUnknown**</span></span>|<span data-ttu-id="d332f-147">, COM istemcisinin CCW ömrünü yönettiği ve tür zorlaması sağladığı **IUnknown** arabiriminin standart uygulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d332f-147">Provides the standard implementation of the **IUnknown** interface with which the COM client manages the lifetime of the CCW and provides type coercion.</span></span>|

 <span data-ttu-id="d332f-148">Yönetilen bir sınıf, aşağıdaki tabloda açıklanan COM arabirimlerini de sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="d332f-148">A managed class can also provide the COM interfaces described in the following table.</span></span>

|<span data-ttu-id="d332f-149">Arabirim</span><span class="sxs-lookup"><span data-stu-id="d332f-149">Interface</span></span>|<span data-ttu-id="d332f-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d332f-150">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="d332f-151">( \_ *ClassName* ) sınıf arabirimi</span><span class="sxs-lookup"><span data-stu-id="d332f-151">The (\_*classname* ) class interface</span></span>|<span data-ttu-id="d332f-152">Çalışma zamanı tarafından sunulan ve açıkça tanımlanmamış, tüm genel arabirimleri, yöntemleri, özellikleri ve yönetilen bir nesne üzerinde açık olarak açık olan alanları sunan arabirim.</span><span class="sxs-lookup"><span data-stu-id="d332f-152">Interface, exposed by the runtime and not explicitly defined, that exposes all public interfaces, methods, properties, and fields that are explicitly exposed on a managed object.</span></span>|
|<span data-ttu-id="d332f-153">**Inewctionpoint** ve **IConnectionPointContainer**</span><span class="sxs-lookup"><span data-stu-id="d332f-153">**IConnectionPoint** and **IConnectionPointContainer**</span></span>|<span data-ttu-id="d332f-154">Temsilci tabanlı Olaylar (Olay aboneleri kaydetmek için bir arabirim) olan nesneler için arabirim.</span><span class="sxs-lookup"><span data-stu-id="d332f-154">Interface for objects that source delegate-based events (an interface for registering event subscribers).</span></span>|
|<span data-ttu-id="d332f-155">**IDispatchEx** (yalnızca .NET Framework)</span><span class="sxs-lookup"><span data-stu-id="d332f-155">**IDispatchEx** (.NET Framework only)</span></span>|<span data-ttu-id="d332f-156">Sınıf **IBir** uygularsa çalışma zamanı tarafından sağlanan arabirim.</span><span class="sxs-lookup"><span data-stu-id="d332f-156">Interface supplied by the runtime if the class implements **IExpando** .</span></span> <span data-ttu-id="d332f-157">**IDispatchEx** **arabirimi IDispatch arabiriminin bir** uzantısıdır. Bu, **IDispatch** 'in aksine numaralandırma, ekleme, silme ve büyük/küçük harf duyarlı üyelerin çağrılmasını mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="d332f-157">The **IDispatchEx** interface is an extension of the **IDispatch** interface that, unlike **IDispatch** , enables enumeration, addition, deletion, and case-sensitive calling of members.</span></span>|
|<span data-ttu-id="d332f-158">**IEnumVariant**</span><span class="sxs-lookup"><span data-stu-id="d332f-158">**IEnumVARIANT**</span></span>|<span data-ttu-id="d332f-159">Sınıf **IEnumerable** uygularsa koleksiyondaki nesneleri numaralandırır koleksiyon türü sınıfları için arabirim.</span><span class="sxs-lookup"><span data-stu-id="d332f-159">Interface for collection-type classes, which enumerates the objects in the collection if the class implements **IEnumerable** .</span></span>|

## <a name="introducing-the-class-interface"></a><span data-ttu-id="d332f-160">Sınıf arabirimine giriş</span><span class="sxs-lookup"><span data-stu-id="d332f-160">Introducing the class interface</span></span>

<span data-ttu-id="d332f-161">Yönetilen kodda açıkça tanımlanmayan sınıf arabirimi, tüm ortak Yöntemler, özellikler, alanlar ve .NET nesnesi üzerinde açık olarak açık olan olayları kullanıma sunan bir arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="d332f-161">The class interface, which is not explicitly defined in managed code, is an interface that exposes all public methods, properties, fields, and events that are explicitly exposed on the .NET object.</span></span> <span data-ttu-id="d332f-162">Bu arabirim, bir çift veya salt dağıtım arabirimi olabilir.</span><span class="sxs-lookup"><span data-stu-id="d332f-162">This interface can be a dual or dispatch-only interface.</span></span> <span data-ttu-id="d332f-163">Sınıf arabirimi, öncesinde bir alt çizgi gelen .NET sınıfının adını alır.</span><span class="sxs-lookup"><span data-stu-id="d332f-163">The class interface receives the name of the .NET class itself, preceded by an underscore.</span></span> <span data-ttu-id="d332f-164">Örneğin, Mammal sınıfı için sınıf arabirimi Mammal ' dir \_ .</span><span class="sxs-lookup"><span data-stu-id="d332f-164">For example, for class Mammal, the class interface is \_Mammal.</span></span>

<span data-ttu-id="d332f-165">Türetilmiş sınıflar için, sınıf arabirimi de temel sınıfın tüm ortak yöntemlerini, özelliklerini ve alanlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d332f-165">For derived classes, the class interface also exposes all public methods, properties, and fields of the base class.</span></span> <span data-ttu-id="d332f-166">Türetilmiş sınıf Ayrıca her temel sınıf için bir sınıf arabirimi sunar.</span><span class="sxs-lookup"><span data-stu-id="d332f-166">The derived class also exposes a class interface for each base class.</span></span> <span data-ttu-id="d332f-167">Örneğin, Mammal sınıfı Mammalsüper sınıfını genişleterek System. Object ' i genişletir. .NET nesnesi, COM istemcilerinin \_ Mammal, \_ mammalsüper ve nesne adlı üç sınıf arabirimine sahip olduğunu gösterir \_ .</span><span class="sxs-lookup"><span data-stu-id="d332f-167">For example, if class Mammal extends class MammalSuperclass, which itself extends System.Object, the .NET object exposes to COM clients three class interfaces named \_Mammal, \_MammalSuperclass, and \_Object.</span></span>

<span data-ttu-id="d332f-168">Örneğin, aşağıdaki .NET sınıfını göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="d332f-168">For example, consider the following .NET class:</span></span>

```vb
' Applies the ClassInterfaceAttribute to set the interface to dual.
<ClassInterface(ClassInterfaceType.AutoDual)> _
' Implicitly extends System.Object.
Public Class Mammal
    Sub Eat()
    Sub Breathe()
    Sub Sleep()
End Class
```

```csharp
// Applies the ClassInterfaceAttribute to set the interface to dual.
[ClassInterface(ClassInterfaceType.AutoDual)]
// Implicitly extends System.Object.
public class Mammal
{
    public void Eat() {}
    public void Breathe() {}
    public void Sleep() {}
}
```

<span data-ttu-id="d332f-169">COM istemcisi adlı bir sınıf arabirimine bir işaretçi alabilir `_Mammal` .</span><span class="sxs-lookup"><span data-stu-id="d332f-169">The COM client can obtain a pointer to a class interface named `_Mammal`.</span></span> <span data-ttu-id="d332f-170">.NET Framework, arabirim tanımını içeren bir tür kitaplığı oluşturmak için [tür kitaplığı verme programı (Tlbexp.exe)](../../framework/tools/tlbexp-exe-type-library-exporter.md) aracını kullanabilirsiniz `_Mammal` .</span><span class="sxs-lookup"><span data-stu-id="d332f-170">On .NET Framework, you can use the [Type Library Exporter (Tlbexp.exe)](../../framework/tools/tlbexp-exe-type-library-exporter.md) tool to generate a type library containing the `_Mammal` interface definition.</span></span> <span data-ttu-id="d332f-171">Tür kitaplığı verme programı .NET Core 'da desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="d332f-171">The Type Library Exporter is not supported on .NET Core.</span></span> <span data-ttu-id="d332f-172">`Mammal`Sınıf bir veya daha fazla arabirim uyguladıysanız, arabirimler coclass altında görünür.</span><span class="sxs-lookup"><span data-stu-id="d332f-172">If the `Mammal` class implemented one or more interfaces, the interfaces would appear under the coclass.</span></span>

```console
[odl, uuid(…), hidden, dual, nonextensible, oleautomation]
interface _Mammal : IDispatch
{
    [id(0x00000000), propget] HRESULT ToString([out, retval] BSTR*
        pRetVal);
    [id(0x60020001)] HRESULT Equals([in] VARIANT obj, [out, retval]
        VARIANT_BOOL* pRetVal);
    [id(0x60020002)] HRESULT GetHashCode([out, retval] short* pRetVal);
    [id(0x60020003)] HRESULT GetType([out, retval] _Type** pRetVal);
    [id(0x6002000d)] HRESULT Eat();
    [id(0x6002000e)] HRESULT Breathe();
    [id(0x6002000f)] HRESULT Sleep();
}
[uuid(…)]
coclass Mammal
{
    [default] interface _Mammal;
}
```

<span data-ttu-id="d332f-173">Sınıf arabiriminin oluşturulması isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d332f-173">Generating the class interface is optional.</span></span> <span data-ttu-id="d332f-174">Varsayılan olarak COM birlikte çalışması, bir tür kitaplığına verdiğiniz her sınıf için yalnızca bir dağıtım arabirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d332f-174">By default, COM interop generates a dispatch-only interface for each class you export to a type library.</span></span> <span data-ttu-id="d332f-175">Sınıfınıza uygulayarak bu arabirimin otomatik olarak oluşturulmasını engelleyebilir veya değiştirebilirsiniz <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> .</span><span class="sxs-lookup"><span data-stu-id="d332f-175">You can prevent or modify the automatic creation of this interface by applying the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> to your class.</span></span> <span data-ttu-id="d332f-176">Sınıf arabirimi yönetilen sınıfları COM 'a gösterme görevini kolaylaştırabilir, ancak kullanımları sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="d332f-176">Although the class interface can ease the task of exposing managed classes to COM, its uses are limited.</span></span>

> [!CAUTION]
> <span data-ttu-id="d332f-177">Kendi kendinizinkini açıkça tanımlamak yerine sınıf arabirimini kullanarak, yönetilen sınıfınızın gelecek sürümü oluşturma sürecini karmaşıklaştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d332f-177">Using the class interface, instead of explicitly defining your own, can complicate the future versioning of your managed class.</span></span> <span data-ttu-id="d332f-178">Sınıf arabirimini kullanmadan önce lütfen aşağıdaki yönergeleri okuyun.</span><span class="sxs-lookup"><span data-stu-id="d332f-178">Please read the following guidelines before using the class interface.</span></span>

### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a><span data-ttu-id="d332f-179">COM istemcilerinin sınıf arabirimini oluşturmak yerine kullanması için açık bir arabirim tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="d332f-179">Define an explicit interface for COM clients to use rather than generating the class interface.</span></span>

<span data-ttu-id="d332f-180">COM birlikte çalışması otomatik olarak bir sınıf arabirimi oluşturduğundan, sınıfınıza sürüm sonrası değişiklikler ortak dil çalışma zamanı tarafından sunulan sınıf arabiriminin yerleşimini değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="d332f-180">Because COM interop generates a class interface automatically, post-version changes to your class can alter the layout of the class interface exposed by the common language runtime.</span></span> <span data-ttu-id="d332f-181">COM istemcileri, bir arabirimin düzeninde değişiklikleri işlemeye yönelik olarak hazırlanmamış olduğundan, sınıfın üye yerleşimini değiştirirseniz bunlar kesilir.</span><span class="sxs-lookup"><span data-stu-id="d332f-181">Since COM clients are typically unprepared to handle changes in the layout of an interface, they break if you change the member layout of the class.</span></span>

<span data-ttu-id="d332f-182">Bu kılavuz, COM istemcilerine sunulan arabirimlerin değiştirilemeyen şekilde kalmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d332f-182">This guideline reinforces the notion that interfaces exposed to COM clients must remain unchangeable.</span></span> <span data-ttu-id="d332f-183">Arabirim yerleşimini yanlışlıkla yeniden sıralayarak COM istemcilerinin bölünmesi riskini azaltmak için, arabirimleri açıkça tanımlayarak arabirim düzeninden sınıftaki tüm değişiklikleri yalıtın.</span><span class="sxs-lookup"><span data-stu-id="d332f-183">To reduce the risk of breaking COM clients by inadvertently reordering the interface layout, isolate all changes to the class from the interface layout by explicitly defining interfaces.</span></span>

<span data-ttu-id="d332f-184">Sınıf arabiriminin otomatik olarak oluşturulmasını ve aşağıdaki kod parçasının gösterdiği gibi sınıf için açık bir arabirim uygulamayı sağlamak için **ClassInterfaceAttribute** kullanın:</span><span class="sxs-lookup"><span data-stu-id="d332f-184">Use the **ClassInterfaceAttribute** to disengage the automatic generation of the class interface and implement an explicit interface for the class, as the following code fragment shows:</span></span>

```vb
<ClassInterface(ClassInterfaceType.None)>Public Class LoanApp
    Implements IExplicit
    Sub M() Implements IExplicit.M
…
End Class
```

```csharp
[ClassInterface(ClassInterfaceType.None)]
public class LoanApp : IExplicit
{
    int IExplicit.M() { return 0; }
}
```

<span data-ttu-id="d332f-185">**ClassInterfaceType. None** değeri, sınıf meta verileri bir tür kitaplığına aktarıldığında sınıf arabiriminin oluşturulmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="d332f-185">The **ClassInterfaceType.None** value prevents the class interface from being generated when the class metadata is exported to a type library.</span></span> <span data-ttu-id="d332f-186">Yukarıdaki örnekte, COM istemcileri `LoanApp` sınıfına yalnızca arabirim aracılığıyla erişebilir `IExplicit` .</span><span class="sxs-lookup"><span data-stu-id="d332f-186">In the preceding example, COM clients can access the `LoanApp` class only through the `IExplicit` interface.</span></span>

### <a name="avoid-caching-dispatch-identifiers-dispids"></a><span data-ttu-id="d332f-187">Dağıtım tanımlayıcılarını (dispIDs) önbelleğe almayı önleyin</span><span class="sxs-lookup"><span data-stu-id="d332f-187">Avoid caching dispatch identifiers (DispIds)</span></span>

<span data-ttu-id="d332f-188">Sınıf arabirimini kullanmak, komut dosyalı istemciler, Microsoft Visual Basic 6,0 istemcileri veya arabirim üyelerinin Depıd 'leri önbelleğe Mayan herhangi bir geç bağlanan istemci için kabul edilebilir bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="d332f-188">Using the class interface is an acceptable option for scripted clients, Microsoft Visual Basic 6.0 clients, or any late-bound client that does not cache the DispIds of interface members.</span></span> <span data-ttu-id="d332f-189">DispIDs, geç bağlamayı etkinleştirmek için arabirim üyelerini belirler.</span><span class="sxs-lookup"><span data-stu-id="d332f-189">DispIds identify interface members to enable late binding.</span></span>

<span data-ttu-id="d332f-190">Sınıf arabirimi için, dispIDs oluşturma işlemi, arabirimindeki üyenin konumunu temel alır.</span><span class="sxs-lookup"><span data-stu-id="d332f-190">For the class interface, generation of DispIds is based on the position of the member in the interface.</span></span> <span data-ttu-id="d332f-191">Üyenin sırasını değiştirir ve sınıfı bir tür kitaplığına dışarı aktardığınızda, sınıf arabiriminde oluşturulan dispID 'leri değiştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d332f-191">If you change the order of the member and export the class to a type library, you will alter the DispIds generated in the class interface.</span></span>

<span data-ttu-id="d332f-192">Sınıf arabirimini kullanırken, geç bağlantılı COM istemcilerinin kesilmesini önlemek için classınterfacbir **. oto dağıtım** değeri Ile **ClassInterfaceAttribute** uygulayın.</span><span class="sxs-lookup"><span data-stu-id="d332f-192">To avoid breaking late-bound COM clients when using the class interface, apply the **ClassInterfaceAttribute** with the **ClassInterfaceType.AutoDispatch** value.</span></span> <span data-ttu-id="d332f-193">Bu değer yalnızca bir dağıtım sınıfı arabirimini uygular, ancak tür kitaplığından arabirim açıklamasını atlar.</span><span class="sxs-lookup"><span data-stu-id="d332f-193">This value implements a dispatch-only class interface, but omits the interface description from the type library.</span></span> <span data-ttu-id="d332f-194">Arabirim açıklaması olmadan istemciler, derleme zamanında dispID 'leri önbelleğe alamıyor.</span><span class="sxs-lookup"><span data-stu-id="d332f-194">Without an interface description, clients are unable to cache DispIds at compile time.</span></span> <span data-ttu-id="d332f-195">Bu, sınıf arabirimi için varsayılan arabirim türü olsa da, öznitelik değerini açık bir şekilde uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d332f-195">Although this is the default interface type for the class interface, you can apply the attribute value explicitly.</span></span>

```vb
<ClassInterface(ClassInterfaceType.AutoDispatch)> Public Class LoanApp
    Implements IAnother
    Sub M() Implements IAnother.M
…
End Class
```

```csharp
[ClassInterface(ClassInterfaceType.AutoDispatch)]
public class LoanApp
{
    public int M() { return 0; }
}
```

<span data-ttu-id="d332f-196">Çalışma zamanında bir arabirim üyesinin DISPID 'sini almak için, COM istemcileri **IDispatch. GetIDsOfNames** ' i çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="d332f-196">To get the DispId of an interface member at run time, COM clients can call **IDispatch.GetIdsOfNames** .</span></span> <span data-ttu-id="d332f-197">Arabirimdeki bir yöntemi çağırmak için, döndürülen DISPID 'yi **IDispatch. Invoke** öğesine bir bağımsız değişken olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="d332f-197">To invoke a method on the interface, pass the returned DispId as an argument to **IDispatch.Invoke** .</span></span>

### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a><span data-ttu-id="d332f-198">Sınıf arabirimi için Dual Interface seçeneğini kullanarak kısıtlayın.</span><span class="sxs-lookup"><span data-stu-id="d332f-198">Restrict using the dual interface option for the class interface.</span></span>

<span data-ttu-id="d332f-199">Çift arabirimler, COM istemcilerine göre arabirim üyelerine erken ve geç bağlamayı etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="d332f-199">Dual interfaces enable early and late binding to interface members by COM clients.</span></span> <span data-ttu-id="d332f-200">Tasarım zamanında ve test sırasında, sınıf arabirimini çift olarak ayarlamayı yararlı bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d332f-200">At design time and during testing, you might find it useful to set the class interface to dual.</span></span> <span data-ttu-id="d332f-201">Hiçbir değişiklik olmayacak yönetilen bir sınıf (ve temel sınıfları) için, bu seçenek de kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="d332f-201">For a managed class (and its base classes) that will never be modified, this option is also acceptable.</span></span> <span data-ttu-id="d332f-202">Diğer tüm durumlarda, sınıf arabirimini çift olarak ayarlamaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="d332f-202">In all other cases, avoid setting the class interface to dual.</span></span>

<span data-ttu-id="d332f-203">Otomatik olarak oluşturulan bir çift arabirim ender durumlarda uygun olabilir; Ancak, daha sık, sürümle ilgili karmaşıklık oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d332f-203">An automatically generated dual interface might be appropriate in rare cases; however, more often it creates version-related complexity.</span></span> <span data-ttu-id="d332f-204">Örneğin, türetilmiş bir sınıfın sınıf arabirimini kullanan COM istemcileri, temel sınıftaki değişikliklerle kolayca kesilebilir.</span><span class="sxs-lookup"><span data-stu-id="d332f-204">For example, COM clients using the class interface of a derived class can easily break with changes to the base class.</span></span> <span data-ttu-id="d332f-205">Üçüncü bir taraf temel sınıfı sağlıyorsa, sınıf arabiriminin düzeni denetimiden oluşur.</span><span class="sxs-lookup"><span data-stu-id="d332f-205">When a third party provides the base class, the layout of the class interface is out of your control.</span></span> <span data-ttu-id="d332f-206">Ayrıca, yalnızca bir dağıtım arabiriminden farklı olarak, bir çift arabirim ( **ClassInterfaceType. oto Dual** ), içe aktarılmış tür kitaplığındaki sınıf arabiriminin bir açıklamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d332f-206">Further, unlike a dispatch-only interface, a dual interface ( **ClassInterfaceType.AutoDual** ) provides a description of the class interface in the exported type library.</span></span> <span data-ttu-id="d332f-207">Bu tür bir açıklama, geç bağlantılı istemcileri derleme zamanında dispID 'leri önbelleğe almak üzere önerir.</span><span class="sxs-lookup"><span data-stu-id="d332f-207">Such a description encourages late-bound clients to cache DispIds at compile time.</span></span>

### <a name="ensure-that-all-com-event-notifications-are-late-bound"></a><span data-ttu-id="d332f-208">Tüm COM olay bildirimlerinin geç bağlandığına emin olun.</span><span class="sxs-lookup"><span data-stu-id="d332f-208">Ensure that all COM event notifications are late-bound.</span></span>

<span data-ttu-id="d332f-209">Varsayılan olarak, COM tür bilgileri doğrudan yönetilen derlemelere katıştırılır ve bu da birincil birlikte çalışma derlemeleri (PIA 'lar) gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d332f-209">By default, COM type information is embedded directly into managed assemblies, which eliminates the need for primary interop assemblies (PIAs).</span></span> <span data-ttu-id="d332f-210">Ancak, gömülü tür bilgisinin kısıtlamalarından biri, COM olay bildirimlerinin erken bağlanan vtable çağrılarına teslimini desteklemediğine karşın yalnızca geç bağlanan `IDispatch::Invoke` çağrıları destekler.</span><span class="sxs-lookup"><span data-stu-id="d332f-210">However, one of the limitations of embedded type information is that it does not support delivery of COM event notifications by early-bound vtable calls, but only supports late-bound `IDispatch::Invoke` calls.</span></span>

<span data-ttu-id="d332f-211">Uygulamanız COM olay arabirimi yöntemlerine erken bağlantılı çağrılar gerektiriyorsa, Visual Studio 'daki **birlikte çalışma türlerini katıştır** özelliğini olarak ayarlayabilir `true` veya aşağıdaki öğeyi proje dosyanıza dahil edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d332f-211">If your application requires early-bound calls to COM event interface methods, you can set the **Embed Interop Types** property in Visual Studio to `true`, or include the following element in your project file:</span></span>

```xml
<EmbedInteropTypes>True</EmbedInteropTypes>
```

## <a name="see-also"></a><span data-ttu-id="d332f-212">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d332f-212">See also</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [<span data-ttu-id="d332f-213">COM sarmalayıcıları</span><span class="sxs-lookup"><span data-stu-id="d332f-213">COM Wrappers</span></span>](com-wrappers.md)
- [<span data-ttu-id="d332f-214">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="d332f-214">Exposing .NET Framework Components to COM</span></span>](../../framework/interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="d332f-215">.NET Core Bileşenlerini COM’da Gösterme</span><span class="sxs-lookup"><span data-stu-id="d332f-215">Exposing .NET Core Components to COM</span></span>](../../core/native-interop/expose-components-to-com.md)
- [<span data-ttu-id="d332f-216">Birlikte Çalışma için Niteleyici .NET Türleri</span><span class="sxs-lookup"><span data-stu-id="d332f-216">Qualifying .NET Types for Interoperation</span></span>](qualify-net-types-for-interoperation.md)
- [<span data-ttu-id="d332f-217">Çalışma Zamanı Aranabilir Sarmalayıcısı</span><span class="sxs-lookup"><span data-stu-id="d332f-217">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)
