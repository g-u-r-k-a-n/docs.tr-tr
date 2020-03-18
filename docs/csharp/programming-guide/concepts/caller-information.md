---
title: Arayan Bilgileri (C#)
ms.date: 07/20/2015
ms.assetid: ffad3d24-2fb7-4641-9124-53b5bc91d339
ms.openlocfilehash: 4b2c34945b47db01b0e655f68f92e4dae7445c2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595344"
---
# <a name="caller-information-c"></a><span data-ttu-id="80608-102">Arayan Bilgileri (C#)</span><span class="sxs-lookup"><span data-stu-id="80608-102">Caller Information (C#)</span></span>

<span data-ttu-id="80608-103">Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80608-103">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="80608-104">Kaynak kodunun dosya yolunu, kaynak kodundaki satır numarasını ve arayanın üye adını alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80608-104">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="80608-105">Bu bilgiler, tanılama araçlarının izlenmesine, oluşturulmasına ve bu araçlarda hata ayıklanmasına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="80608-105">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="80608-106">Bu bilgileri elde etmek için her biri varsayılan değere sahip isteğe bağlı parametrelere uygulanan öznitelikler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80608-106">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="80608-107">Aşağıdaki <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> tabloda, ad alanında tanımlanan Arayan Bilgileri öznitelikleri listelenir:</span><span class="sxs-lookup"><span data-stu-id="80608-107">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="80608-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="80608-108">Attribute</span></span>|<span data-ttu-id="80608-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80608-109">Description</span></span>|<span data-ttu-id="80608-110">Tür</span><span class="sxs-lookup"><span data-stu-id="80608-110">Type</span></span>|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="80608-111">Kaynak dosyasının arayanı içeren tam yolu.</span><span class="sxs-lookup"><span data-stu-id="80608-111">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="80608-112">Bu, derleme zamanındaki dosya yoludur.</span><span class="sxs-lookup"><span data-stu-id="80608-112">This is the file path at compile time.</span></span>|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="80608-113">Yöntemin çağrıldığı kaynak dosyadaki satır numarası.</span><span class="sxs-lookup"><span data-stu-id="80608-113">Line number in the source file at which the method is called.</span></span>|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="80608-114">Arayanın yöntemi veya özellik adı.</span><span class="sxs-lookup"><span data-stu-id="80608-114">Method or property name of the caller.</span></span> <span data-ttu-id="80608-115">Bu konunun ilerleyen saatlerinde [Üye Adları'na](#member-names) bakın.</span><span class="sxs-lookup"><span data-stu-id="80608-115">See [Member Names](#member-names) later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="80608-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="80608-116">Example</span></span>

<span data-ttu-id="80608-117">Aşağıdaki örnekte, Arayanın Bilgisi özniteliklerinin nasıl kullanılacağı gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="80608-117">The following example shows how to use Caller Info attributes.</span></span> <span data-ttu-id="80608-118">`TraceMessage` Yönteme yapılan her çağrıda, arayan bilgileri isteğe bağlı parametrelere bağımsız değişken olarak ikame edilir.</span><span class="sxs-lookup"><span data-stu-id="80608-118">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>

```csharp
public void DoProcessing()
{
    TraceMessage("Something happened.");
}

public void TraceMessage(string message,
        [System.Runtime.CompilerServices.CallerMemberName] string memberName = "",
        [System.Runtime.CompilerServices.CallerFilePath] string sourceFilePath = "",
        [System.Runtime.CompilerServices.CallerLineNumber] int sourceLineNumber = 0)
{
    System.Diagnostics.Trace.WriteLine("message: " + message);
    System.Diagnostics.Trace.WriteLine("member name: " + memberName);
    System.Diagnostics.Trace.WriteLine("source file path: " + sourceFilePath);
    System.Diagnostics.Trace.WriteLine("source line number: " + sourceLineNumber);
}

// Sample Output:
//  message: Something happened.
//  member name: DoProcessing
//  source file path: c:\Visual Studio Projects\CallerInfoCS\CallerInfoCS\Form1.cs
//  source line number: 31
```

## <a name="remarks"></a><span data-ttu-id="80608-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="80608-119">Remarks</span></span>

<span data-ttu-id="80608-120">Her isteğe bağlı parametre için açık bir varsayılan değer belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="80608-120">You must specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="80608-121">İsteğe bağlı olarak belirtilmeyen parametrelere Arayan Bilgisi özniteliklerini uygulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="80608-121">You can't apply Caller Info attributes to parameters that aren't specified as optional.</span></span>

<span data-ttu-id="80608-122">Arayan Bilgisi öznitelikleri, bir parametreyi isteğe bağlı hale getirmez.</span><span class="sxs-lookup"><span data-stu-id="80608-122">The Caller Info attributes don't make a parameter optional.</span></span> <span data-ttu-id="80608-123">Bunun yerine, bağımsız değişken atlandığında geçirilen varsayılan değeri etkilerler.</span><span class="sxs-lookup"><span data-stu-id="80608-123">Instead, they affect the default value that's passed in when the argument is omitted.</span></span>

<span data-ttu-id="80608-124">Arayan Bilgisi değerleri, derleme zamanında Ara Dile (IL) değişmez değerler olarak verilir.</span><span class="sxs-lookup"><span data-stu-id="80608-124">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="80608-125"><xref:System.Exception.StackTrace%2A> Özel durumlar için özelliğin sonuçlarının aksine, sonuçlar gizlemeden etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="80608-125">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="80608-126">Arayan bilgisini denetlemek veya gizlemek için isteğe bağlı bağımsız değişkenleri açıkça sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80608-126">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

### <a name="member-names"></a><span data-ttu-id="80608-127">Üye adları</span><span class="sxs-lookup"><span data-stu-id="80608-127">Member names</span></span>

<span data-ttu-id="80608-128">Özniteliği, `CallerMemberName` üye adı niçin çağrılması `String` metoduna bağımsız değişken olarak belirtmemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80608-128">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="80608-129">Bu tekniği kullanarak, **Yeniden Adlandırma Değerlerini** değiştirmez `String` sorunu önlemek.</span><span class="sxs-lookup"><span data-stu-id="80608-129">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="80608-130">Bu, özellikle aşağıdaki görevler için yararlı olur:</span><span class="sxs-lookup"><span data-stu-id="80608-130">This benefit is especially useful for the following tasks:</span></span>

- <span data-ttu-id="80608-131">İzleme ve tanılama yordamlarını kullanma.</span><span class="sxs-lookup"><span data-stu-id="80608-131">Using tracing and diagnostic routines.</span></span>

- <span data-ttu-id="80608-132">Verileri bağlarken <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi uygulama.</span><span class="sxs-lookup"><span data-stu-id="80608-132">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="80608-133">Bu arabirim, bir nesnenin özelliğinin bağlama denetimine özelliğin değiştirildiğini bildirmesini ve böylece denetimin güncelleştirilmiş bilgileri görüntüleyebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="80608-133">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="80608-134">`CallerMemberName` Öznitelik olmadan, özellik adını gerçek olarak belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="80608-134">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="80608-135">Aşağıdaki grafik, özniteliği kullandığınızda `CallerMemberName` döndürülen üye adları gösterir.</span><span class="sxs-lookup"><span data-stu-id="80608-135">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>

|<span data-ttu-id="80608-136">Çağrının oluştuğu yer</span><span class="sxs-lookup"><span data-stu-id="80608-136">Calls occurs within</span></span>|<span data-ttu-id="80608-137">Üye adı sonucu</span><span class="sxs-lookup"><span data-stu-id="80608-137">Member name result</span></span>|
|-|-|
|<span data-ttu-id="80608-138">Yöntem, özellik veya olay</span><span class="sxs-lookup"><span data-stu-id="80608-138">Method, property, or event</span></span>|<span data-ttu-id="80608-139">Yöntemin, özelliğin veya aramanın kaynaklandığı olayın adı.</span><span class="sxs-lookup"><span data-stu-id="80608-139">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="80608-140">Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="80608-140">Constructor</span></span>|<span data-ttu-id="80608-141">".ctor" dizesi</span><span class="sxs-lookup"><span data-stu-id="80608-141">The string ".ctor"</span></span>|
|<span data-ttu-id="80608-142">Statik oluşturucu</span><span class="sxs-lookup"><span data-stu-id="80608-142">Static constructor</span></span>|<span data-ttu-id="80608-143">".cctor" dizesi</span><span class="sxs-lookup"><span data-stu-id="80608-143">The string ".cctor"</span></span>|
|<span data-ttu-id="80608-144">Yok edici</span><span class="sxs-lookup"><span data-stu-id="80608-144">Destructor</span></span>|<span data-ttu-id="80608-145">"Finalize" dizesi</span><span class="sxs-lookup"><span data-stu-id="80608-145">The string "Finalize"</span></span>|
|<span data-ttu-id="80608-146">Kullanıcı tanımlı işleçler veya dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="80608-146">User-defined operators or conversions</span></span>|<span data-ttu-id="80608-147">Üye için oluşturulan "op_Addition" gibi bir ad.</span><span class="sxs-lookup"><span data-stu-id="80608-147">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="80608-148">Öznitelik oluşturucu</span><span class="sxs-lookup"><span data-stu-id="80608-148">Attribute constructor</span></span>|<span data-ttu-id="80608-149">Özniteliğin uygulandığı yöntemin veya özelliğin adı.</span><span class="sxs-lookup"><span data-stu-id="80608-149">The name of the method or property to which the attribute is applied.</span></span> <span data-ttu-id="80608-150">Öznitelik bir üye içerisindeki herhangi bir öğeyse (parametre, dönüş değeri veya genel tür parametresi gibi), bu sonuç bu öğeyle ilişkili öğenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="80608-150">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="80608-151">İçeren üye yok (örneğin, derleme düzeyi veya türlere uygulanan öznitelikler)</span><span class="sxs-lookup"><span data-stu-id="80608-151">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="80608-152">İsteğe bağlı parametrenin varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="80608-152">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="80608-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80608-153">See also</span></span>

- [<span data-ttu-id="80608-154">Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="80608-154">Attributes (C#)</span></span>](./attributes/index.md)
- [<span data-ttu-id="80608-155">Ortak Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="80608-155">Common Attributes (C#)</span></span>](./attributes/common-attributes.md)
- [<span data-ttu-id="80608-156">Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="80608-156">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="80608-157">Programlama Kavramları (C#)</span><span class="sxs-lookup"><span data-stu-id="80608-157">Programming Concepts (C#)</span></span>](./index.md)
