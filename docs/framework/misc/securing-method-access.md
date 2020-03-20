---
title: Yöntem Erişiminin Güvenliğini Sağlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, method access
- secure coding, method access
- security [.NET Framework], method access
- method access security
ms.assetid: f7c2d6ec-3b18-4e0e-9991-acd97189d818
ms.openlocfilehash: a9e1226483eaa02dc8dc3dfb741e3df6b2985fbe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181151"
---
# <a name="securing-method-access"></a><span data-ttu-id="ed3a3-102">Yöntem Erişiminin Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="ed3a3-102">Securing Method Access</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="ed3a3-103">Bazı yöntemler, rasgele güvenilmeyen kodun çağrılmasını sağlamak için uygun olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-103">Some methods might not be suitable to allow arbitrary untrusted code to call.</span></span> <span data-ttu-id="ed3a3-104">Bu tür yöntemler çeşitli riskler oluşturmaktadır: Yöntem bazı sınırlı bilgiler sağlayabilir; ona aktarılan herhangi bir bilginin olduğuna inanabilir; parametreleri üzerinde hata denetimi yapmayabilir; veya yanlış parametrelerle arızalanabilir veya zararlı bir şey yapabilir.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-104">Such methods pose several risks: The method might provide some restricted information; it might believe any information passed to it; it might not do error checking on the parameters; or with the wrong parameters, it might malfunction or do something harmful.</span></span> <span data-ttu-id="ed3a3-105">Bu durumların farkında olmalı ve yöntemi korumaya yardımcı olmak için harekete geçmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-105">You should be aware of these cases and take action to help protect the method.</span></span>  
  
 <span data-ttu-id="ed3a3-106">Bazı durumlarda, genel kullanıma yönelik olmayan ancak yine de herkese açık olması gereken yöntemleri kısıtlamanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-106">In some cases, you might need to restrict methods that are not intended for public use but still must be public.</span></span> <span data-ttu-id="ed3a3-107">Örneğin, kendi DL'leriniz arasında çağrılması gereken bir arabiriminiz olabilir ve bu nedenle herkese açık olması gerekir, ancak müşterilerin kullanmasını önlemek veya kötü amaçlı kodun bileşeninize giriş noktasını kullanmasını önlemek için bu arabirimi herkese açık hale getirmek istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-107">For example, you might have an interface that needs to be called across your own DLLs and hence must be public, but you do not want to expose it publicly to prevent customers from using it or to prevent malicious code from exploiting the entry point into your component.</span></span> <span data-ttu-id="ed3a3-108">Genel kullanım için tasarlanmamış bir yöntemi kısıtlamak için başka bir yaygın neden (ancak ortak olmalıdır) belgelemek ve çok iç arabirim olabilir desteklemek zorunda önlemektir.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-108">Another common reason to restrict a method not intended for public use (but that must be public) is to avoid having to document and support what might be a very internal interface.</span></span>  
  
 <span data-ttu-id="ed3a3-109">Yönetilen kod, yöntem erişimini kısıtlamanın çeşitli yollarını sunar:</span><span class="sxs-lookup"><span data-stu-id="ed3a3-109">Managed code offers several ways to restrict method access:</span></span>  
  
- <span data-ttu-id="ed3a3-110">Güvenilen sınıf, derleme veya türetilmiş sınıflar için erişilebilirlik kapsamını sınırlayın.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-110">Limit the scope of accessibility to the class, assembly, or derived classes, if they can be trusted.</span></span> <span data-ttu-id="ed3a3-111">Yöntem erişimini sınırlamanın en basit yolu budur.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-111">This is the simplest way to limit method access.</span></span> <span data-ttu-id="ed3a3-112">Türemiş sınıfların, bazı durumlarda üst sınıfın kimliğini paylaşmalarına rağmen, türedikleri sınıfların türetildiği sınıftan daha az güvenilir olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-112">Note that, in general, derived classes can be less trustworthy than the class they derive from, though in some cases they share the parent class's identity.</span></span> <span data-ttu-id="ed3a3-113">Özellikle, güvenlik bağlamında mutlaka kullanılmayan **korumalı**anahtar kelimeden güven çıkarmayın.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-113">In particular, do not infer trust from the keyword **protected**, which is not necessarily used in the security context.</span></span>  
  
- <span data-ttu-id="ed3a3-114">Yöntem erişimini belirli bir kimliği arayanlarla (temelde, seçtiğiniz belirli [bir kanıt,](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) yayımcı, bölge vb.) sınırlandırın.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-114">Limit the method access to callers of a specified identity--essentially, any particular [evidence](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (strong name, publisher, zone, and so on) you choose.</span></span>  
  
- <span data-ttu-id="ed3a3-115">Yöntem erişimini, seçtiğiniz izinlere sahip olan arayanlarla sınırlandırın.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-115">Limit the method access to callers having whatever permissions you select.</span></span>  
  
 <span data-ttu-id="ed3a3-116">Benzer şekilde, bildirimsel güvenlik sınıfların devralma denetlemek için izin verir.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-116">Similarly, declarative security allows you to control inheritance of classes.</span></span> <span data-ttu-id="ed3a3-117">Aşağıdakileri yapmak için **InheritanceDemand'ı** kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ed3a3-117">You can use **InheritanceDemand** to do the following:</span></span>  
  
- <span data-ttu-id="ed3a3-118">Türetilen sınıfların belirli bir kimliğe veya izne sahip olmasını zorunlu kılmasını zorunlu kınla.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-118">Require derived classes to have a specified identity or permission.</span></span>  
  
- <span data-ttu-id="ed3a3-119">Belirli bir kimliğe veya izine sahip olmak için belirli yöntemleri geçersiz kılan türemiş sınıflar gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-119">Require derived classes that override specific methods to have a specified identity or permission.</span></span>  
  
 <span data-ttu-id="ed3a3-120">Aşağıdaki örnek, arayanların belirli bir güçlü adla imzalanmasını gerekterek, sınırlı erişim için ortak bir sınıfın korunmasına nasıl yardımcı olabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-120">The following example shows how to help protect a public class for limited access by requiring that callers be signed with a particular strong name.</span></span> <span data-ttu-id="ed3a3-121">Bu örnek, <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> güçlü ad için bir **Talep** ile kullanır.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-121">This example uses the <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> with a **Demand** for the strong name.</span></span> <span data-ttu-id="ed3a3-122">Güçlü bir ada sahip bir derlemenin nasıl imzalatılılabildiğini anlatan görev tabanlı bilgiler için [bkz.](../../standard/assembly/create-use-strong-named.md)</span><span class="sxs-lookup"><span data-stu-id="ed3a3-122">For task-based information on how to sign an assembly with a strong name, see [Creating and Using Strong-Named Assemblies](../../standard/assembly/create-use-strong-named.md).</span></span>  
  
```vb  
<StrongNameIdentityPermissionAttribute(SecurityAction.Demand, PublicKey := "…hex…", Name := "App1", Version := "0.0.0.0")>  _  
Public Class Class1  
End Class  
```  
  
```csharp  
[StrongNameIdentityPermissionAttribute(SecurityAction.Demand, PublicKey="…hex…", Name="App1", Version="0.0.0.0")]  
public class Class1  
{  
  
}
```  
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a><span data-ttu-id="ed3a3-123">Güvenilmeyen Kodla Sınıfları ve Üyeleri Kullanımdan Dışlama</span><span class="sxs-lookup"><span data-stu-id="ed3a3-123">Excluding Classes and Members from Use by Untrusted Code</span></span>  
 <span data-ttu-id="ed3a3-124">Belirli sınıfların ve yöntemlerin yanı sıra özelliklerin ve olayların kısmen güvenilen kodtarafından kullanılmasını önlemek için bu bölümde gösterilen bildirimleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-124">Use the declarations shown in this section to prevent specific classes and methods, as well as properties and events, from being used by partially trusted code.</span></span> <span data-ttu-id="ed3a3-125">Bu bildirimleri bir sınıfa uygulayarak, korumayı tüm yöntemlerine, özelliklerine ve olaylarına uygularsınız; ancak, alan erişiminin bildirimsel güvenliktarafından etkilenmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-125">By applying these declarations to a class, you apply the protection to all its methods, properties, and events; however, note that field access is not affected by declarative security.</span></span> <span data-ttu-id="ed3a3-126">Ayrıca, bağlantı taleplerinin yalnızca acil arayanlara karşı korunmaya yardımcı olduğunu ve yine de cezbetme saldırılarına maruz kabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-126">Note also that link demands help protect against only the immediate callers and might still be subject to luring attacks.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ed3a3-127">.NET Framework 4'te yeni bir şeffaflık modeli tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-127">A new transparency model has been introduced in the .NET Framework 4.</span></span> <span data-ttu-id="ed3a3-128">[Güvenlik-Saydam Kod, Düzey 2](security-transparent-code-level-2.md) modeli öznitelik ile <xref:System.Security.SecurityCriticalAttribute> güvenli kodu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-128">The [Security-Transparent Code, Level 2](security-transparent-code-level-2.md) model identifies secure code with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="ed3a3-129">Güvenlik açısından kritik kod, hem arayanların hem de devralanların tam olarak güvenilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-129">Security-critical code requires both callers and inheritors to be fully trusted.</span></span> <span data-ttu-id="ed3a3-130">Önceki .NET Framework sürümlerinden kod erişim güvenlik kuralları altında çalışan derlemeler düzey 2 derlemelerini çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-130">Assemblies that are running under the code access security rules from earlier .NET Framework versions can call level 2 assemblies.</span></span> <span data-ttu-id="ed3a3-131">Bu durumda, güvenlik açısından kritik öznitelikler tam güven için bağlantı talepleri olarak kabul edilecektir.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-131">In this case, the security-critical attributes will be treated as link demands for full trust.</span></span>  
  
 <span data-ttu-id="ed3a3-132">Güçlü adlandırılmış derlemelerde, [bir LinkDemand,](link-demands.md) bunların kullanımını tam olarak güvenilen arayanlara kısıtlamak için tüm genel olarak erişilebilen yöntemlere, özelliklere ve olaylara uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-132">In strong-named assemblies, a [LinkDemand](link-demands.md) is applied to all publicly accessible methods, properties, and events therein to restrict their use to fully trusted callers.</span></span> <span data-ttu-id="ed3a3-133">Bu özelliği devre dışı kalmak <xref:System.Security.AllowPartiallyTrustedCallersAttribute> için özniteliği uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-133">To disable this feature, you must apply the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="ed3a3-134">Bu nedenle, güvenilmeyen arayanları hariç tutmak için sınıfları açıkça işaretlemeyalnızca bu özniteliğe sahip imzalanmamış derlemeler veya derlemeler için gereklidir; bu bildirimleri, güvenilmeyen arayanlar için tasarlanmayan türlerin bir alt kümesini işaretlemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-134">Thus, explicitly marking classes to exclude untrusted callers is necessary only for unsigned assemblies or assemblies with this attribute; you can use these declarations to mark a subset of types therein that are not intended for untrusted callers.</span></span>  
  
 <span data-ttu-id="ed3a3-135">Aşağıdaki örnekler, sınıfların ve üyelerin güvenilmeyen kod tarafından kullanılmasını nasıl önleyeceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-135">The following examples show how to prevent classes and members from being used by untrusted code.</span></span>  
  
 <span data-ttu-id="ed3a3-136">Kamu mühürsüz sınıflar için:</span><span class="sxs-lookup"><span data-stu-id="ed3a3-136">For public nonsealed classes:</span></span>  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name := "FullTrust"), _
System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
Public Class CanDeriveFromMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public class CanDeriveFromMe  
{  
}  
```  
  
 <span data-ttu-id="ed3a3-137">Kamu mühürlü sınıflar için:</span><span class="sxs-lookup"><span data-stu-id="ed3a3-137">For public sealed classes:</span></span>  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
NotInheritable Public Class CannotDeriveFromMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public sealed class CannotDeriveFromMe  
{  
}  
```  
  
 <span data-ttu-id="ed3a3-138">Genel soyut sınıflar için:</span><span class="sxs-lookup"><span data-stu-id="ed3a3-138">For public abstract classes:</span></span>  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name := "FullTrust"), _  
System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
MustInherit Public Class CannotCreateInstanceOfMe_CanCastToMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public abstract class CannotCreateInstanceOfMe_CanCastToMe {}  
```  
  
 <span data-ttu-id="ed3a3-139">Genel sanal işlevler için:</span><span class="sxs-lookup"><span data-stu-id="ed3a3-139">For public virtual functions:</span></span>  
  
```vb  
Class Base1
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Overridable Sub CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe  
End Class 'Base1  
```  
  
```csharp  
class Base1
{  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
    public virtual void CanOverrideOrCallMe() {}  
}  
```  
  
 <span data-ttu-id="ed3a3-140">Genel soyut işlevler için:</span><span class="sxs-lookup"><span data-stu-id="ed3a3-140">For public abstract functions:</span></span>  
  
```vb  
MustInherit Class Base2  
    <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Sub MustOverrideMe()  
    End Sub  
End Class 'Base2  
```  
  
```csharp  
abstract class Base2 {  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
public abstract void MustOverrideMe();  
}  
```  
  
 <span data-ttu-id="ed3a3-141">Taban sınıfın tam güven gerektirmediği genel geçersiz kılma işlevleri için:</span><span class="sxs-lookup"><span data-stu-id="ed3a3-141">For public override functions where the base class does not demand full trust:</span></span>  
  
```vb  
Class Derived  
    Inherits Base1  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.Demand, Name:="FullTrust")> _  
    Public Overrides Sub CanOverrideOrCallMe()  
        MyBase.CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe  
End Class 'Derived  
```  
  
```csharp  
class Derived : Base1  
{
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.Demand, Name="FullTrust")]
    public override void CanOverrideOrCallMe()
    {  
        base.CanOverrideOrCallMe();  
    }  
}  
```  
  
 <span data-ttu-id="ed3a3-142">Taban sınıfın tam güven gerektirdiği genel geçersiz kılma işlevleri için:</span><span class="sxs-lookup"><span data-stu-id="ed3a3-142">For public override functions where the base class demands full trust:</span></span>  
  
```vb  
Class Derived  
    Inherits Base1  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Overrides Sub CanOverrideOrCallMe()  
        MyBase.CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe
End Class 'Derived  
```  
  
```csharp  
class Derived : Base1  
{
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]
    public override void CanOverrideOrCallMe()
    {  
        base.CanOverrideOrCallMe();  
    }  
}  
```  
  
 <span data-ttu-id="ed3a3-143">Ortak arabirimler için:</span><span class="sxs-lookup"><span data-stu-id="ed3a3-143">For public interfaces:</span></span>  
  
```vb  
Public Interface ICanCastToMe  
    <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust")> _  
    Sub CanImplementMe()  
End Interface 'ICanCastToMe  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust")> _  
Class Implemented  
    Implements ICanCastToMe  
    Public Sub CanImplementMe()  
    End Sub 'CanImplementMe  
```  
  
```csharp  
public interface ICanCastToMe
{  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
void CanImplementMe();  
}  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
class Implemented : ICanCastToMe  
{  
    public void CanImplementMe()  
    {  
    }  
}  
```  
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a><span data-ttu-id="ed3a3-144">Sanal İç Geçersiz Kılmalar veya Geçersiz Kılınabilir Kolay Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="ed3a3-144">Virtual Internal Overrides or Overloads Overridable Friend</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ed3a3-145">Bu bölüm, bir yöntemi hem `virtual` de `internal` (Visual`Overloads` `Overridable` `Friend` Basic'te) olarak bildirirken bir güvenlik sorunu hakkında uyarır.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-145">This section warns about a security issue when declaring a method as both `virtual` and `internal` (`Overloads` `Overridable` `Friend` in Visual Basic).</span></span> <span data-ttu-id="ed3a3-146">Bu uyarı yalnızca .NET Framework sürümleri 1.0 ve 1.1 için geçerlidir, sonraki sürümler için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-146">This warning applies only to the .NET Framework versions 1.0 and 1.1, it does not apply to later versions.</span></span>  
  
 <span data-ttu-id="ed3a3-147">.NET Framework sürümleri 1.0 ve 1.1'de, kodunuzu diğer derlemeler tarafından kullanılamıyorsa onaylarken tür sistemi erişilebilirliğinin bir nüansını fark etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-147">In the .NET Framework versions 1.0 and 1.1, you must be aware of a nuance of the type system accessibility when confirming that your code is unavailable to other assemblies.</span></span> <span data-ttu-id="ed3a3-148">**Sanal** ve **dahili** olarak bildirilen bir yöntem (Visual Basic'te**Overridable Friend Overloads)** üst sınıfın vtable girişini geçersiz kılabilir ve yalnızca aynı derleme nin içinden kullanılabilir, çünkü dahilidir.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-148">A method that is declared **virtual** and **internal** (**Overloads Overridable Friend** in Visual Basic) can override the parent class's vtable entry and can be used only from within the same assembly because it is internal.</span></span> <span data-ttu-id="ed3a3-149">Ancak, geçersiz kılma için erişilebilirlik **sanal** anahtar kelime tarafından belirlenir ve bu kod sınıfın kendisine erişimi olduğu sürece başka bir derleme geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-149">However, the accessibility for overriding is determined by the **virtual** keyword, and this can be overridden from another assembly as long as that code has access to the class itself.</span></span> <span data-ttu-id="ed3a3-150">Geçersiz kılma olasılığı bir sorun teşkil ediyorsa, bunu düzeltmek için bildirimsel güvenliği kullanın veya kesinlikle gerekli değilse **sanal** anahtar sözcüğü kaldırın.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-150">If the possibility of an override presents a problem, use declarative security to fix it, or remove the **virtual** keyword if it is not strictly required.</span></span>  
  
 <span data-ttu-id="ed3a3-151">Bir dil derleyicisi bir derleme hatası ile bu geçersiz kılmaları önlerse bile, diğer derleyicilerle yazılmış kodun geçersiz kılınmasını mümkün olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-151">Note that even if a language compiler prevents these overrides with a compilation error, it is possible for code written with other compilers to override.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed3a3-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed3a3-152">See also</span></span>

- [<span data-ttu-id="ed3a3-153">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ed3a3-153">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
