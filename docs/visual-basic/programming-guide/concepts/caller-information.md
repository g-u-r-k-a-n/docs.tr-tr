---
title: Arayan Bilgileri
ms.date: 07/20/2015
ms.assetid: 15d556eb-4d0c-4497-98a3-7f60abb7d6a1
ms.openlocfilehash: 7c87b540a68f4d0219918fed66de6c1b635104a9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349469"
---
# <a name="caller-information-visual-basic"></a><span data-ttu-id="af4ff-102">Arayan bilgileri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af4ff-102">Caller Information (Visual Basic)</span></span>
<span data-ttu-id="af4ff-103">Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af4ff-103">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="af4ff-104">Kaynak kodunun dosya yolunu, kaynak kodundaki satır numarasını ve arayanın üye adını alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af4ff-104">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="af4ff-105">Bu bilgiler, tanılama araçlarının izlenmesine, oluşturulmasına ve bu araçlarda hata ayıklanmasına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="af4ff-105">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>  
  
 <span data-ttu-id="af4ff-106">Bu bilgileri elde etmek için her biri varsayılan değere sahip isteğe bağlı parametrelere uygulanan öznitelikler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af4ff-106">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="af4ff-107">Aşağıdaki tabloda <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanında tanımlanan çağıran bilgi öznitelikleri listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="af4ff-107">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="af4ff-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="af4ff-108">Attribute</span></span>|<span data-ttu-id="af4ff-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="af4ff-109">Description</span></span>|<span data-ttu-id="af4ff-110">Type</span><span class="sxs-lookup"><span data-stu-id="af4ff-110">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="af4ff-111">Kaynak dosyasının arayanı içeren tam yolu.</span><span class="sxs-lookup"><span data-stu-id="af4ff-111">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="af4ff-112">Bu, derleme zamanındaki dosya yoludur.</span><span class="sxs-lookup"><span data-stu-id="af4ff-112">This is the file path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="af4ff-113">Yöntemin çağrıldığı kaynak dosyadaki satır numarası.</span><span class="sxs-lookup"><span data-stu-id="af4ff-113">Line number in the source file at which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="af4ff-114">Arayanın yöntemi veya özellik adı.</span><span class="sxs-lookup"><span data-stu-id="af4ff-114">Method or property name of the caller.</span></span> <span data-ttu-id="af4ff-115">Bu konunun devamındaki [üye adları](#MEMBERNAMES) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="af4ff-115">See [Member Names](#MEMBERNAMES) later in this topic.</span></span>|`String`|  
  
## <a name="example"></a><span data-ttu-id="af4ff-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="af4ff-116">Example</span></span>  
 <span data-ttu-id="af4ff-117">Aşağıdaki örnekte, Arayanın Bilgisi özniteliklerinin nasıl kullanılacağı gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="af4ff-117">The following example shows how to use Caller Info attributes.</span></span> <span data-ttu-id="af4ff-118">`TraceMessage` yöntemine yapılan her çağrıda, çağıran bilgileri isteğe bağlı parametrelere bağımsız değişkenler olarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="af4ff-118">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>  
  
```vb  
Private Sub DoProcessing()  
    TraceMessage("Something happened.")  
End Sub  
  
Public Sub TraceMessage(message As String,  
        <System.Runtime.CompilerServices.CallerMemberName> Optional memberName As String = Nothing,  
        <System.Runtime.CompilerServices.CallerFilePath> Optional sourcefilePath As String = Nothing,  
        <System.Runtime.CompilerServices.CallerLineNumber()> Optional sourceLineNumber As Integer = 0)  
  
    System.Diagnostics.Trace.WriteLine("message: " & message)  
    System.Diagnostics.Trace.WriteLine("member name: " & memberName)  
    System.Diagnostics.Trace.WriteLine("source file path: " & sourcefilePath)  
    System.Diagnostics.Trace.WriteLine("source line number: " & sourceLineNumber)  
End Sub  
  
' Sample output:  
'   message: Something happened.  
'   member name: DoProcessing  
'   source file path: C:\Users\username\Documents\Visual Studio 2012\Projects\CallerInfoVB\CallerInfoVB\Form1.vb  
'   source line number: 15  
```  
  
## <a name="remarks"></a><span data-ttu-id="af4ff-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="af4ff-119">Remarks</span></span>  
 <span data-ttu-id="af4ff-120">Her isteğe bağlı parametre için açık bir varsayılan değer belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="af4ff-120">You must specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="af4ff-121">İsteğe bağlı olarak belirtilmeyen parametrelere Arayan Bilgisi özniteliklerini uygulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="af4ff-121">You can't apply Caller Info attributes to parameters that aren't specified as optional.</span></span>  
  
 <span data-ttu-id="af4ff-122">Arayan Bilgisi öznitelikleri, bir parametreyi isteğe bağlı hale getirmez.</span><span class="sxs-lookup"><span data-stu-id="af4ff-122">The Caller Info attributes don't make a parameter optional.</span></span> <span data-ttu-id="af4ff-123">Bunun yerine, bağımsız değişken atlandığında geçirilen varsayılan değeri etkilerler.</span><span class="sxs-lookup"><span data-stu-id="af4ff-123">Instead, they affect the default value that's passed in when the argument is omitted.</span></span>  
  
 <span data-ttu-id="af4ff-124">Arayan Bilgisi değerleri, derleme zamanında Ara Dile (IL) değişmez değerler olarak verilir.</span><span class="sxs-lookup"><span data-stu-id="af4ff-124">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="af4ff-125">Özel durumlar için <xref:System.Exception.StackTrace%2A> özelliğinin sonuçlarının aksine, sonuçlar gizleme tarafından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="af4ff-125">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span>  
  
 <span data-ttu-id="af4ff-126">Arayan bilgisini denetlemek veya gizlemek için isteğe bağlı bağımsız değişkenleri açıkça sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af4ff-126">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>  
  
### <a name="MEMBERNAMES"></a><span data-ttu-id="af4ff-127">Üye adları</span><span class="sxs-lookup"><span data-stu-id="af4ff-127">Member Names</span></span>  
 <span data-ttu-id="af4ff-128">Üyenin adını çağrılan metoda bir `String` bağımsız değişkeni olarak belirtmekten kaçınmak için `CallerMemberName` özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af4ff-128">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="af4ff-129">Bu tekniği kullanarak, **yeniden düzenlemeyi yeniden adlandırma** sorununun `String` değerleri değiştirmediğini önleyin.</span><span class="sxs-lookup"><span data-stu-id="af4ff-129">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="af4ff-130">Bu, özellikle aşağıdaki görevler için yararlı olur:</span><span class="sxs-lookup"><span data-stu-id="af4ff-130">This benefit is especially useful for the following tasks:</span></span>  
  
- <span data-ttu-id="af4ff-131">İzleme ve tanılama yordamlarını kullanma.</span><span class="sxs-lookup"><span data-stu-id="af4ff-131">Using tracing and diagnostic routines.</span></span>  
  
- <span data-ttu-id="af4ff-132">Verileri bağlarken <xref:System.ComponentModel.INotifyPropertyChanged> arabirimini uygulama.</span><span class="sxs-lookup"><span data-stu-id="af4ff-132">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="af4ff-133">Bu arabirim, bir nesnenin özelliğinin bağlama denetimine özelliğin değiştirildiğini bildirmesini ve böylece denetimin güncelleştirilmiş bilgileri görüntüleyebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="af4ff-133">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="af4ff-134">`CallerMemberName` özniteliği olmadan, özellik adını bir sabit değer olarak belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="af4ff-134">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>  
  
 <span data-ttu-id="af4ff-135">Aşağıdaki grafikte `CallerMemberName` özniteliğini kullandığınızda döndürülen üye adları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="af4ff-135">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>  
  
|<span data-ttu-id="af4ff-136">Çağrının oluştuğu yer</span><span class="sxs-lookup"><span data-stu-id="af4ff-136">Calls occurs within</span></span>|<span data-ttu-id="af4ff-137">Üye adı sonucu</span><span class="sxs-lookup"><span data-stu-id="af4ff-137">Member name result</span></span>|  
|-------------------------|------------------------|  
|<span data-ttu-id="af4ff-138">Yöntem, özellik veya olay</span><span class="sxs-lookup"><span data-stu-id="af4ff-138">Method, property, or event</span></span>|<span data-ttu-id="af4ff-139">Yöntemin, özelliğin veya aramanın kaynaklandığı olayın adı.</span><span class="sxs-lookup"><span data-stu-id="af4ff-139">The name of the method, property, or event from which the call originated.</span></span>|  
|<span data-ttu-id="af4ff-140">Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="af4ff-140">Constructor</span></span>|<span data-ttu-id="af4ff-141">".ctor" dizesi</span><span class="sxs-lookup"><span data-stu-id="af4ff-141">The string ".ctor"</span></span>|  
|<span data-ttu-id="af4ff-142">Statik oluşturucu</span><span class="sxs-lookup"><span data-stu-id="af4ff-142">Static constructor</span></span>|<span data-ttu-id="af4ff-143">".cctor" dizesi</span><span class="sxs-lookup"><span data-stu-id="af4ff-143">The string ".cctor"</span></span>|  
|<span data-ttu-id="af4ff-144">Yok edici</span><span class="sxs-lookup"><span data-stu-id="af4ff-144">Destructor</span></span>|<span data-ttu-id="af4ff-145">"Finalize" dizesi</span><span class="sxs-lookup"><span data-stu-id="af4ff-145">The string "Finalize"</span></span>|  
|<span data-ttu-id="af4ff-146">Kullanıcı tanımlı işleçler veya dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="af4ff-146">User-defined operators or conversions</span></span>|<span data-ttu-id="af4ff-147">Üye için oluşturulan "op_Addition" gibi bir ad.</span><span class="sxs-lookup"><span data-stu-id="af4ff-147">The generated name for the member, for example, "op_Addition".</span></span>|  
|<span data-ttu-id="af4ff-148">Öznitelik oluşturucu</span><span class="sxs-lookup"><span data-stu-id="af4ff-148">Attribute constructor</span></span>|<span data-ttu-id="af4ff-149">Özniteliğin uygulandığı üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="af4ff-149">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="af4ff-150">Öznitelik bir üye içerisindeki herhangi bir öğeyse (parametre, dönüş değeri veya genel tür parametresi gibi), bu sonuç bu öğeyle ilişkili öğenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="af4ff-150">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|  
|<span data-ttu-id="af4ff-151">İçeren üye yok (örneğin, derleme düzeyi veya türlere uygulanan öznitelikler)</span><span class="sxs-lookup"><span data-stu-id="af4ff-151">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="af4ff-152">İsteğe bağlı parametrenin varsayılan değeri.</span><span class="sxs-lookup"><span data-stu-id="af4ff-152">The default value of the optional parameter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="af4ff-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af4ff-153">See also</span></span>

- [<span data-ttu-id="af4ff-154">Öznitelikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af4ff-154">Attributes (Visual Basic)</span></span>](../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="af4ff-155">Ortak öznitelikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af4ff-155">Common Attributes (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)
- [<span data-ttu-id="af4ff-156">İsteğe Bağlı Parametreler</span><span class="sxs-lookup"><span data-stu-id="af4ff-156">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="af4ff-157">Programlama kavramları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af4ff-157">Programming Concepts (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/index.md)
