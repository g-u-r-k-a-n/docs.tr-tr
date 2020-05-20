---
title: Dil bağımsızlığı ve dilden bağımsız bileşenler
description: ".NET ' te C#, C++/CLı, F #, IronPython, VB, Visual COBOL ve PowerShell gibi birçok desteklenen dilden birinde nasıl geliştirme yapabileceğinizi öğrenin."
ms.date: 07/22/2016
dev_langs:
- csharp
- vb
ms.technology: dotnet-standard
ms.assetid: 2dbed1bc-86f5-43cd-9a57-adbb1c5efba4
ms.openlocfilehash: f04ff902743c91147a6f056bca3292ee47952bbd
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420558"
---
# <a name="language-independence-and-language-independent-components"></a><span data-ttu-id="bf1ca-103">Dil bağımsızlığı ve dilden bağımsız bileşenler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-103">Language independence and language-independent components</span></span>

<span data-ttu-id="bf1ca-104">.NET dilden bağımsız.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-104">.NET is language independent.</span></span> <span data-ttu-id="bf1ca-105">Yani, geliştirici olarak C#, F # ve Visual Basic gibi .NET uygulamalarını hedefleyen birçok dilden birinde geliştirme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-105">This means that, as a developer, you can develop in one of the many languages that target .NET implementations, such as C#, F#, and Visual Basic.</span></span> <span data-ttu-id="bf1ca-106">.NET uygulamaları için geliştirilmiş sınıf kitaplıklarının türlerine ve üyelerine, ilk olarak yazıldığı dili ve özgün dilin kurallarından herhangi birini izlemeniz gerekmeden erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-106">You can access the types and members of class libraries developed for .NET implementations without having to know the language in which they were originally written and without having to follow any of the original language's conventions.</span></span> <span data-ttu-id="bf1ca-107">Bileşen geliştiricisiyseniz, kendi dilinden bağımsız olarak, bileşeninize herhangi bir .NET uygulaması tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-107">If you are a component developer, your component can be accessed by any .NET app regardless of its language.</span></span>

> [!NOTE]
> <span data-ttu-id="bf1ca-108">Bu makalenin ilk bölümü, dilden bağımsız bileşenler oluşturmayı, diğer bir deyişle, herhangi bir dilde yazılmış uygulamalar tarafından tüketilen bileşenleri oluşturmayı tartışır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-108">This first part of this article discusses creating language-independent components - that is, components that can be consumed by apps that are written in any language.</span></span> <span data-ttu-id="bf1ca-109">Ayrıca, birden çok dilde yazılmış kaynak kodundan tek bir bileşen veya uygulama oluşturabilirsiniz; Bu makalenin ikinci bölümünde [Diller arası birlikte çalışabilirlik](#cross-language-interoperability) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-109">You can also create a single component or app from source code written in multiple languages; see [Cross-Language Interoperability](#cross-language-interoperability) in the second part of this article.</span></span>

<span data-ttu-id="bf1ca-110">Herhangi bir dilde yazılmış diğer nesnelerle tam olarak etkileşimde bulunmak için, nesneler yalnızca tüm diller için ortak olan özellikleri çağıranlar halinde kullanıma sunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-110">To fully interact with other objects written in any language, objects must expose to callers only those features that are common to all languages.</span></span> <span data-ttu-id="bf1ca-111">Bu ortak özellikler kümesi, oluşturulan derlemeler için uygulanan bir dizi kural olan ortak dil belirtimi (CLS) tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-111">This common set of features is defined by the Common Language Specification (CLS), which is a set of rules that apply to generated assemblies.</span></span> <span data-ttu-id="bf1ca-112">Ortak dil belirtimi, [ECMA-335 Standardı: ortak dil altyapısının](https://www.ecma-international.org/publications/standards/Ecma-335.htm), Bölüm ı, yan tümceler 7 ila 11 ' de tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-112">The Common Language Specification is defined in Partition I, Clauses 7 through 11 of the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>

<span data-ttu-id="bf1ca-113">Bileşeniniz Ortak dil belirtimine uyuyorsa, CLS uyumlu olması garantilenir ve CLS 'yi destekleyen herhangi bir programlama dilinde yazılan derlemelerdeki koddan erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-113">If your component conforms to the Common Language Specification, it is guaranteed to be CLS-compliant and can be accessed from code in assemblies written in any programming language that supports the CLS.</span></span> <span data-ttu-id="bf1ca-114">Kaynak kodunuza [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) özniteliğini uygulayarak, bileşeninizin derleme zamanında ortak dil belirtimine uygun olup olmadığını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-114">You can determine whether your component conforms to the Common Language Specification at compile time by applying the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute to your source code.</span></span> <span data-ttu-id="bf1ca-115">Daha fazla bilgi için bkz. [CLSCompliantAttribute özniteliği](#the-clscompliantattribute-attribute).</span><span class="sxs-lookup"><span data-stu-id="bf1ca-115">For more information, see The [CLSCompliantAttribute attribute](#the-clscompliantattribute-attribute).</span></span>

<span data-ttu-id="bf1ca-116">Bu makalede:</span><span class="sxs-lookup"><span data-stu-id="bf1ca-116">In this article:</span></span>

* [<span data-ttu-id="bf1ca-117">CLS Uyumluluk kuralları</span><span class="sxs-lookup"><span data-stu-id="bf1ca-117">CLS compliance rules</span></span>](#cls-compliance-rules)

  * [<span data-ttu-id="bf1ca-118">Türler ve tür üye imzaları</span><span class="sxs-lookup"><span data-stu-id="bf1ca-118">Types and type member signatures</span></span>](#types-and-type-member-signatures)

  * [<span data-ttu-id="bf1ca-119">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="bf1ca-119">Naming conventions</span></span>](#naming-conventions)

  * [<span data-ttu-id="bf1ca-120">Tür dönüştürme</span><span class="sxs-lookup"><span data-stu-id="bf1ca-120">Type conversion</span></span>](#type-conversion)

  * [<span data-ttu-id="bf1ca-121">Diziler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-121">Arrays</span></span>](#arrays)

  * [<span data-ttu-id="bf1ca-122">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-122">Interfaces</span></span>](#interfaces)

  * [<span data-ttu-id="bf1ca-123">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="bf1ca-123">Enumerations</span></span>](#enumerations)

  * [<span data-ttu-id="bf1ca-124">Genel olarak tür üyeleri</span><span class="sxs-lookup"><span data-stu-id="bf1ca-124">Type members in general</span></span>](#type-members-in-general)

  * [<span data-ttu-id="bf1ca-125">Üye erişilebilirliği</span><span class="sxs-lookup"><span data-stu-id="bf1ca-125">Member accessibility</span></span>](#member-accessibility)

  * [<span data-ttu-id="bf1ca-126">Genel türler ve Üyeler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-126">Generic types and members</span></span>](#generic-types-and-members)

  * [<span data-ttu-id="bf1ca-127">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="bf1ca-127">Constructors</span></span>](#constructors)

  * [<span data-ttu-id="bf1ca-128">Özellikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-128">Properties</span></span>](#properties)

  * [<span data-ttu-id="bf1ca-129">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-129">Events</span></span>](#events)

  * [<span data-ttu-id="bf1ca-130">Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-130">Overloads</span></span>](#overloads)

  * [<span data-ttu-id="bf1ca-131">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="bf1ca-131">Exceptions</span></span>](#exceptions)

  * [<span data-ttu-id="bf1ca-132">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-132">Attributes</span></span>](#attributes)

* [<span data-ttu-id="bf1ca-133">CLSCompliantAttribute özniteliği</span><span class="sxs-lookup"><span data-stu-id="bf1ca-133">CLSCompliantAttribute attribute</span></span>](#the-clscompliantattribute-attribute)

* [<span data-ttu-id="bf1ca-134">Diller Arası Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="bf1ca-134">Cross-Language Interoperability</span></span>](#cross-language-interoperability)

## <a name="cls-compliance-rules"></a><span data-ttu-id="bf1ca-135">CLS Uyumluluk kuralları</span><span class="sxs-lookup"><span data-stu-id="bf1ca-135">CLS compliance rules</span></span>

<span data-ttu-id="bf1ca-136">Bu bölümde, CLS uyumlu bir bileşen oluşturmak için kurallar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-136">This section discusses the rules for creating a CLS-compliant component.</span></span> <span data-ttu-id="bf1ca-137">Kuralların tam bir listesi için, bkz. [ECMA-335 standart: ortak dil altyapısının](https://www.ecma-international.org/publications/standards/Ecma-335.htm)bölüm ı, yan tümcesi 11.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-137">For a complete list of rules, see Partition I, Clause 11 of the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>

> [!NOTE]
> <span data-ttu-id="bf1ca-138">Ortak dil belirtimi, tüketiciler (CLS uyumlu bir bileşene programlı olarak erişen geliştiriciler), çerçeveler (CLS uyumlu kitaplıklar oluşturmak için bir dil derleyicisi kullanan geliştiriciler) ve Extender 'lar (bir dil derleyicisi veya CLS uyumlu bileşenler oluşturan bir kod ayrıştırıcısı gibi bir araç oluşturan geliştiriciler) için geçerli olduğu için her bir kuralı CLS uyumluluğu için tartışır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-138">The Common Language Specification discusses each rule for CLS compliance as it applies to consumers (developers who are programmatically accessing a component that is CLS-compliant), frameworks (developers who are using a language compiler to create CLS-compliant libraries), and extenders (developers who are creating a tool such as a language compiler or a code parser that creates CLS-compliant components).</span></span> <span data-ttu-id="bf1ca-139">Bu makale, çerçeveler için uygulanan kurallara odaklanır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-139">This article focuses on the rules as they apply to frameworks.</span></span> <span data-ttu-id="bf1ca-140">Ancak, Extender 'lara uygulanan kuralların bazılarının, [yansıma. yayma](xref:System.Reflection.Emit)kullanılarak oluşturulan derlemeler için de uygulanabilir olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-140">Note, though, that some of the rules that apply to extenders may also apply to assemblies that are created using [Reflection.Emit](xref:System.Reflection.Emit).</span></span>

<span data-ttu-id="bf1ca-141">Dilden bağımsız bir bileşen tasarlamak için, yalnızca bileşenin ortak arabirimine CLS uyumluluğu için kuralları uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-141">To design a component that is language independent, you only need to apply the rules for CLS compliance to your component's public interface.</span></span> <span data-ttu-id="bf1ca-142">Özel uygulamanızın belirtimine uyması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-142">Your private implementation does not have to conform to the specification.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bf1ca-143">CLS uyumluluğu kuralları yalnızca bileşenin ortak arabirimine uygulanır, özel uygulamasına uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-143">The rules for CLS compliance apply only to a component's public interface, not to its private implementation.</span></span>

<span data-ttu-id="bf1ca-144">Örneğin, [bayt](xref:System.Byte) dışındaki IŞARETSIZ tamsayılar CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-144">For example, unsigned integers other than [Byte](xref:System.Byte) are not CLS-compliant.</span></span> <span data-ttu-id="bf1ca-145">`Person`Aşağıdaki örnekteki sınıf `Age` [UInt16](xref:System.UInt16)türünde bir özelliği kullanıma sunduğundan, aşağıdaki kod bir derleyici uyarısı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-145">Because the `Person` class in the following example exposes an `Age` property of type [UInt16](xref:System.UInt16), the following code displays a compiler warning.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person
{
   private UInt16 personAge = 0;

   public UInt16 Age
   { get { return personAge; } }
}
// The attempt to compile the example displays the following compiler warning:
//    Public1.cs(10,18): warning CS3003: Type of 'Person.Age' is not CLS-compliant
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Person
   Private personAge As UInt16

   Public ReadOnly Property Age As UInt16
      Get
         Return personAge
      End Get
   End Property
End Class
' The attempt to compile the example displays the following compiler warning:
'    Public1.vb(9) : warning BC40027: Return type of function 'Age' is not CLS-compliant.
'
'       Public ReadOnly Property Age As UInt16
'                                ~~~
```

<span data-ttu-id="bf1ca-146">Özelliğin türünü, `Age` `UInt16` CLS uyumlu, 16 bit işaretli bir tamsayı olan [Int16](xref:System.Int16)sürümüne DEĞIŞTIREREK, kişi sınıfını CLS uyumlu hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-146">You can make the Person class CLS-compliant by changing the type of `Age` property from `UInt16` to [Int16](xref:System.Int16), which is a CLS-compliant, 16-bit signed integer.</span></span> <span data-ttu-id="bf1ca-147">Özel alanın türünü değiştirmek zorunda değilsiniz `personAge` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-147">You do not have to change the type of the private `personAge` field.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person
{
   private Int16 personAge = 0;

   public Int16 Age
   { get { return personAge; } }
}
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Person
   Private personAge As UInt16

   Public ReadOnly Property Age As Int16
      Get
         Return CType(personAge, Int16)
      End Get
   End Property
End Class
```

<span data-ttu-id="bf1ca-148">Kitaplığın ortak arabirimi aşağıdakilerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="bf1ca-148">A library's public interface consists of the following:</span></span>

* <span data-ttu-id="bf1ca-149">Ortak sınıfların tanımları.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-149">Definitions of public classes.</span></span>

* <span data-ttu-id="bf1ca-150">Ortak sınıfların genel üyelerinin ve türetilmiş sınıfların erişebileceği üyelerin tanımlarının tanımları (yani, korumalı üyeler).</span><span class="sxs-lookup"><span data-stu-id="bf1ca-150">Definitions of the public members of public classes, and definitions of members accessible to derived classes (that is, protected members).</span></span>

* <span data-ttu-id="bf1ca-151">Ortak sınıfların ortak yöntemlerinin parametreleri ve dönüş türleri, parametreleri ve türetilmiş sınıflar tarafından erişilebilen yöntemlerin dönüş türleri.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-151">Parameters and return types of public methods of public classes, and parameters and return types of methods accessible to derived classes.</span></span>

<span data-ttu-id="bf1ca-152">CLS uyumluluğu kuralları aşağıdaki tabloda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-152">The rules for CLS compliance are listed in the following table.</span></span> <span data-ttu-id="bf1ca-153">Kuralların metni, telif hakkı 2012 olan [ECMA-335 Standardı: ortak dil altyapısından](https://www.ecma-international.org/publications/standards/Ecma-335.htm)(Ecma International göre) alınır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-153">The text of the rules is taken verbatim from the [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), which is Copyright 2012 by Ecma International.</span></span> <span data-ttu-id="bf1ca-154">Bu kurallar hakkında daha ayrıntılı bilgi aşağıdaki bölümlerde bulunur.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-154">More detailed information about these rules is found in the following sections.</span></span>

<span data-ttu-id="bf1ca-155">Kategori</span><span class="sxs-lookup"><span data-stu-id="bf1ca-155">Category</span></span> | <span data-ttu-id="bf1ca-156">Bkz.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-156">See</span></span> | <span data-ttu-id="bf1ca-157">Kural</span><span class="sxs-lookup"><span data-stu-id="bf1ca-157">Rule</span></span> | <span data-ttu-id="bf1ca-158">Kural numarası</span><span class="sxs-lookup"><span data-stu-id="bf1ca-158">Rule Number</span></span>
-------- | --- | ---- | -----------
<span data-ttu-id="bf1ca-159">Erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="bf1ca-159">Accessibility</span></span> | [<span data-ttu-id="bf1ca-160">Üye erişilebilirliği</span><span class="sxs-lookup"><span data-stu-id="bf1ca-160">Member accessibility</span></span>](#member-accessibility) | <span data-ttu-id="bf1ca-161">Erişilebilirlik ile farklı bir derlemeden devralınan bir yöntemi geçersiz kılmanın dışında, devralınan Yöntemler geçersiz kılınırken erişilebilirlik değiştirilmez `family-or-assembly` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-161">Accessibility shall not be changed when overriding inherited methods, except when overriding a method inherited from a different assembly with accessibility `family-or-assembly`.</span></span> <span data-ttu-id="bf1ca-162">Bu durumda, geçersiz kılma erişilebilirliği olacaktır `family` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-162">In this case, the override shall have accessibility `family`.</span></span> | <span data-ttu-id="bf1ca-163">10</span><span class="sxs-lookup"><span data-stu-id="bf1ca-163">10</span></span>
<span data-ttu-id="bf1ca-164">Erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="bf1ca-164">Accessibility</span></span> | [<span data-ttu-id="bf1ca-165">Üye erişilebilirliği</span><span class="sxs-lookup"><span data-stu-id="bf1ca-165">Member accessibility</span></span>](#member-accessibility) | <span data-ttu-id="bf1ca-166">Türlerin ve üyelerin görünürlüğü ve erişilebilirliği, üyenin görünür ve erişilebilir olduğu her üyenin İmzasındaki türlerin görünür ve erişilebilir olması gibi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-166">The visibility and accessibility of types and members shall be such that types in the signature of any member shall be visible and accessible whenever the member itself is visible and accessible.</span></span> <span data-ttu-id="bf1ca-167">Örneğin, kendi derlemesi dışında görünen bir genel yöntem, türü yalnızca derleme içinde görünür olan bir bağımsız değişkene sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-167">For example, a public method that is visible outside its assembly shall not have an argument whose type is visible only within the assembly.</span></span> <span data-ttu-id="bf1ca-168">Herhangi bir Üyenin imzasında kullanılan bir örneklenmiş genel tür oluşturan türlerin görünürlüğü ve erişilebilirliği, üyenin görünür ve erişilebilir olduğu her durumda görünür ve erişilebilir olur.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-168">The visibility and accessibility of types composing an instantiated generic type used in the signature of any member shall be visible and accessible whenever the member itself is visible and accessible.</span></span> <span data-ttu-id="bf1ca-169">Örneğin, kendi derlemesi dışında görünen bir Üyenin imzasında bulunan bir örneklenmiş genel tür, türü yalnızca derleme içinde görünür olan genel bir bağımsız değişkene sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-169">For example, an instantiated generic type present in the signature of a member that is visible outside its assembly shall not have a generic argument whose type is visible only within the assembly.</span></span> | <span data-ttu-id="bf1ca-170">12</span><span class="sxs-lookup"><span data-stu-id="bf1ca-170">12</span></span>
<span data-ttu-id="bf1ca-171">Diziler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-171">Arrays</span></span> | [<span data-ttu-id="bf1ca-172">Diziler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-172">Arrays</span></span>](#arrays) | <span data-ttu-id="bf1ca-173">Diziler CLS uyumlu bir türe sahip öğeler içermelidir ve dizinin tüm boyutları daha düşük sınırlara sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-173">Arrays shall have elements with a CLS-compliant type, and all dimensions of the array shall have lower bounds of zero.</span></span> <span data-ttu-id="bf1ca-174">Yalnızca bir öğenin dizi olması ve dizinin öğe türü, aşırı yüklemeleri ayırt etmek için gerekli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-174">Only the fact that an item is an array and the element type of the array shall be required to distinguish between overloads.</span></span> <span data-ttu-id="bf1ca-175">Aşırı yükleme iki veya daha fazla dizi türünü temel aldığı zaman, öğe türleri adlandırılmış türler olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-175">When overloading is based on two or more array types the element types shall be named types.</span></span> | <span data-ttu-id="bf1ca-176">16</span><span class="sxs-lookup"><span data-stu-id="bf1ca-176">16</span></span>
<span data-ttu-id="bf1ca-177">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-177">Attributes</span></span> | [<span data-ttu-id="bf1ca-178">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-178">Attributes</span></span>](#attributes) | <span data-ttu-id="bf1ca-179">Öznitelikler [System. Attribute](xref:System.Attribute)türünde ya da bundan devralan bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-179">Attributes shall be of type [System.Attribute](xref:System.Attribute), or a type inheriting from it.</span></span> | <span data-ttu-id="bf1ca-180">41</span><span class="sxs-lookup"><span data-stu-id="bf1ca-180">41</span></span>
<span data-ttu-id="bf1ca-181">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-181">Attributes</span></span> | [<span data-ttu-id="bf1ca-182">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-182">Attributes</span></span>](#attributes) | <span data-ttu-id="bf1ca-183">CLS yalnızca özel özniteliklerin kodlamalarının bir alt kümesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-183">The CLS only allows a subset of the encodings of custom attributes.</span></span> <span data-ttu-id="bf1ca-184">Bu kodlarda görünen türler (bkz. Partition IV): [System. Type](xref:System.Type), [System. String](xref:System.String), [System. Char](xref:System.Char), [System. Boolean](xref:System.Boolean), [System. Byte](xref:System.Byte), [System. Int16](xref:System.Int16), [System. Int32](xref:System.Int32), [System. Int64](xref:System.Int64), System. [Single](xref:System.Single), [System. Double](xref:System.Double)ve CLS uyumlu bir taban tamsayı türüne göre herhangi bir numaralandırma türü.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-184">The only types that shall appear in these encodings are (see Partition IV): [System.Type](xref:System.Type), [System.String](xref:System.String), [System.Char](xref:System.Char), [System.Boolean](xref:System.Boolean), [System.Byte](xref:System.Byte), [System.Int16](xref:System.Int16), [System.Int32](xref:System.Int32), [System.Int64](xref:System.Int64), [System.Single](xref:System.Single), [System.Double](xref:System.Double), and any enumeration type based on a CLS-compliant base integer type.</span></span> | <span data-ttu-id="bf1ca-185">34</span><span class="sxs-lookup"><span data-stu-id="bf1ca-185">34</span></span>
<span data-ttu-id="bf1ca-186">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-186">Attributes</span></span> | [<span data-ttu-id="bf1ca-187">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-187">Attributes</span></span>](#attributes) | <span data-ttu-id="bf1ca-188">CLS, herkese açık bir şekilde görünür gerekli değiştiricilere izin vermez (bkz. `modreq` Bölüm II), ancak isteğe bağlı değiştiricilere izin veriyor ( `modopt` , bkz. Bölüm II).</span><span class="sxs-lookup"><span data-stu-id="bf1ca-188">The CLS does not allow publicly visible required modifiers (`modreq`, see Partition II), but does allow optional modifiers (`modopt`, see Partition II) it does not understand.</span></span> | <span data-ttu-id="bf1ca-189">35</span><span class="sxs-lookup"><span data-stu-id="bf1ca-189">35</span></span>
<span data-ttu-id="bf1ca-190">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="bf1ca-190">Constructors</span></span> | [<span data-ttu-id="bf1ca-191">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="bf1ca-191">Constructors</span></span>](#constructors) | <span data-ttu-id="bf1ca-192">Bir nesne Oluşturucusu, devralınan örnek verilerine herhangi bir erişim gerçekleşmeden önce temel sınıfının bazı örnek oluşturucusunu çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-192">An object constructor shall call some instance constructor of its base class before any access occurs to inherited instance data.</span></span> <span data-ttu-id="bf1ca-193">(Bu, oluşturucuların olmaması gereken değer türleri için de geçerlidir.)</span><span class="sxs-lookup"><span data-stu-id="bf1ca-193">(This does not apply to value types, which need not have constructors.)</span></span>  | <span data-ttu-id="bf1ca-194">21</span><span class="sxs-lookup"><span data-stu-id="bf1ca-194">21</span></span>
<span data-ttu-id="bf1ca-195">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="bf1ca-195">Constructors</span></span> | [<span data-ttu-id="bf1ca-196">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="bf1ca-196">Constructors</span></span>](#constructors) | <span data-ttu-id="bf1ca-197">Bir nesne Oluşturucusu, bir nesne oluşturmanın parçası hariç çağrılmamalıdır ve bir nesne iki kez başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-197">An object constructor shall not be called except as part of the creation of an object, and an object shall not be initialized twice.</span></span> | <span data-ttu-id="bf1ca-198">22</span><span class="sxs-lookup"><span data-stu-id="bf1ca-198">22</span></span>
<span data-ttu-id="bf1ca-199">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="bf1ca-199">Enumerations</span></span> | [<span data-ttu-id="bf1ca-200">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="bf1ca-200">Enumerations</span></span>](#enumerations) | <span data-ttu-id="bf1ca-201">Bir numaralandırmanın temel alınan türü yerleşik bir CLS tamsayı türü olacaktır, alanın adı "value__" ve bu alan işaretlenir `RTSpecialName` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-201">The underlying type of an enum shall be a built-in CLS integer type, the name of the field shall be "value__", and that field shall be marked `RTSpecialName`.</span></span> |  <span data-ttu-id="bf1ca-202">7</span><span class="sxs-lookup"><span data-stu-id="bf1ca-202">7</span></span>
<span data-ttu-id="bf1ca-203">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="bf1ca-203">Enumerations</span></span> | [<span data-ttu-id="bf1ca-204">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="bf1ca-204">Enumerations</span></span>](#enumerations) | <span data-ttu-id="bf1ca-205">[System. FlagsAttribute](xref:System.FlagsAttribute) (Bölüm IV kitaplığı) özel özniteliğinin varlığı veya yokluğu tarafından belirtilen iki farklı tür numaralandırmalar vardır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-205">There are two distinct kinds of enums, indicated by the presence or absence of the [System.FlagsAttribute](xref:System.FlagsAttribute) (see Partition IV Library) custom attribute.</span></span> <span data-ttu-id="bf1ca-206">Biri adlandırılmış tamsayı değerlerini temsil eder; diğeri adlandırılmamış bir değer oluşturmak için birleştirilebilen adlandırılmış bit bayraklarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-206">One represents named integer values; the other represents named bit flags that can be combined to generate an unnamed value.</span></span> <span data-ttu-id="bf1ca-207">Öğesinin değeri `enum` belirtilen değerlerle sınırlı değil.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-207">The value of an `enum` is not limited to the specified values.</span></span> |  <span data-ttu-id="bf1ca-208">8</span><span class="sxs-lookup"><span data-stu-id="bf1ca-208">8</span></span>
<span data-ttu-id="bf1ca-209">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="bf1ca-209">Enumerations</span></span> | [<span data-ttu-id="bf1ca-210">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="bf1ca-210">Enumerations</span></span>](#enumerations) | <span data-ttu-id="bf1ca-211">Sabit listesinin değişmez statik alanları, sabit listesinin kendi türüne sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-211">Literal static fields of an enum shall have the type of the enum itself.</span></span> |  <span data-ttu-id="bf1ca-212">9</span><span class="sxs-lookup"><span data-stu-id="bf1ca-212">9</span></span>
<span data-ttu-id="bf1ca-213">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-213">Events</span></span> | [<span data-ttu-id="bf1ca-214">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-214">Events</span></span>](#events) | <span data-ttu-id="bf1ca-215">Bir olayı uygulayan yöntemler `SpecialName` meta verilerde işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-215">The methods that implement an event shall be marked `SpecialName` in the metadata.</span></span> |<span data-ttu-id="bf1ca-216">29</span><span class="sxs-lookup"><span data-stu-id="bf1ca-216">29</span></span>
<span data-ttu-id="bf1ca-217">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-217">Events</span></span> | [<span data-ttu-id="bf1ca-218">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-218">Events</span></span>](#events) | <span data-ttu-id="bf1ca-219">Bir olayın ve erişimcilerinin erişilebilirliği aynı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-219">The accessibility of an event and of its accessors shall be identical.</span></span> |<span data-ttu-id="bf1ca-220">30</span><span class="sxs-lookup"><span data-stu-id="bf1ca-220">30</span></span>
<span data-ttu-id="bf1ca-221">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-221">Events</span></span> | [<span data-ttu-id="bf1ca-222">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-222">Events</span></span>](#events) | <span data-ttu-id="bf1ca-223">`add` `remove` Bir olay için ve yöntemlerinin her ikisi de mevcut ya da yok olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-223">The `add` and `remove` methods for an event shall both either be present or absent.</span></span> |<span data-ttu-id="bf1ca-224">31</span><span class="sxs-lookup"><span data-stu-id="bf1ca-224">31</span></span>
<span data-ttu-id="bf1ca-225">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-225">Events</span></span> | [<span data-ttu-id="bf1ca-226">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-226">Events</span></span>](#events) | <span data-ttu-id="bf1ca-227">`add` `remove` Bir olay için ve yöntemlerinin her biri, türü olay türünü tanımlayan ve [System. Delegate](xref:System.Delegate)'ten türetilebilecek bir parametre alır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-227">The `add` and `remove` methods for an event shall each take one parameter whose type defines the type of the event and that shall be derived from [System.Delegate](xref:System.Delegate).</span></span> |<span data-ttu-id="bf1ca-228">32</span><span class="sxs-lookup"><span data-stu-id="bf1ca-228">32</span></span>
<span data-ttu-id="bf1ca-229">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-229">Events</span></span> | [<span data-ttu-id="bf1ca-230">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-230">Events</span></span>](#events) | <span data-ttu-id="bf1ca-231">Olaylar belirli bir adlandırma düzenine bağlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-231">Events shall adhere to a specific naming pattern.</span></span> <span data-ttu-id="bf1ca-232">CLS kuralı 29 ' da başvurulan SpecialName özniteliği, uygun ad karşılaştırmaları içinde yok sayılacak ve tanımlayıcı kurallarına uymalecektir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-232">The SpecialName attribute referred to in CLS rule 29 shall be ignored in appropriate name comparisons and shall adhere to identifier rules.</span></span>  |<span data-ttu-id="bf1ca-233">33</span><span class="sxs-lookup"><span data-stu-id="bf1ca-233">33</span></span>
<span data-ttu-id="bf1ca-234">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="bf1ca-234">Exceptions</span></span> | [<span data-ttu-id="bf1ca-235">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="bf1ca-235">Exceptions</span></span>](#exceptions) | <span data-ttu-id="bf1ca-236">Oluşturulan nesneler [System. Exception](xref:System.Exception) veya bundan devralan bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-236">Objects that are thrown shall be of type [System.Exception](xref:System.Exception) or a type inheriting from it.</span></span> <span data-ttu-id="bf1ca-237">Nonetheless, diğer özel durum türlerinin yayılmasını engellemek için CLS uyumlu yöntemler gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-237">Nonetheless, CLS-compliant methods are not required to block the propagation of other types of exceptions.</span></span> | <span data-ttu-id="bf1ca-238">40</span><span class="sxs-lookup"><span data-stu-id="bf1ca-238">40</span></span>
<span data-ttu-id="bf1ca-239">Genel</span><span class="sxs-lookup"><span data-stu-id="bf1ca-239">General</span></span> | [<span data-ttu-id="bf1ca-240">CLS Uyumluluk kuralları</span><span class="sxs-lookup"><span data-stu-id="bf1ca-240">CLS compliance rules</span></span>](#cls-compliance-rules) | <span data-ttu-id="bf1ca-241">CLS kuralları yalnızca, tanımlayıcı derlemenin dışında erişilebilen veya görülebilen bir türün bölümleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-241">CLS rules apply only to those parts of a type that are accessible or visible outside of the defining assembly.</span></span> | <span data-ttu-id="bf1ca-242">1</span><span class="sxs-lookup"><span data-stu-id="bf1ca-242">1</span></span>
<span data-ttu-id="bf1ca-243">Genel</span><span class="sxs-lookup"><span data-stu-id="bf1ca-243">General</span></span> | [<span data-ttu-id="bf1ca-244">CLS Uyumluluk kuralları</span><span class="sxs-lookup"><span data-stu-id="bf1ca-244">CLS compliance rules</span></span>](#cls-compliance-rules) | <span data-ttu-id="bf1ca-245">CLS olmayan uyumlu türlerin üyeleri CLS uyumlu olarak işaretlenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-245">Members of non-CLS compliant types shall not be marked CLS-compliant.</span></span> | <span data-ttu-id="bf1ca-246">2</span><span class="sxs-lookup"><span data-stu-id="bf1ca-246">2</span></span>
<span data-ttu-id="bf1ca-247">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-247">Generics</span></span> | [<span data-ttu-id="bf1ca-248">Genel türler ve Üyeler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-248">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="bf1ca-249">İç içe türler, kapsayan tür olarak en az sayıda genel parametreye sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-249">Nested types shall have at least as many generic parameters as the enclosing type.</span></span> <span data-ttu-id="bf1ca-250">İç içe bir türdeki genel parametreler, kapsayan türünün genel parametrelerine konum ile karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-250">Generic parameters in a nested type correspond by position to the generic parameters in its enclosing type.</span></span>  | <span data-ttu-id="bf1ca-251">42</span><span class="sxs-lookup"><span data-stu-id="bf1ca-251">42</span></span>
<span data-ttu-id="bf1ca-252">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-252">Generics</span></span> | [<span data-ttu-id="bf1ca-253">Genel türler ve Üyeler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-253">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="bf1ca-254">Genel bir türün adı, iç içe olmayan türde belirtilen tür parametrelerinin sayısını kodlayıp, yukarıda tanımlanan kurallara göre iç içe geçmiş tür parametrelerinin yeni tanıtılmasıyla belirtilir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-254">The name of a generic type shall encode the number of type parameters declared on the non-nested type, or newly introduced to the type if nested, according to the rules defined above.</span></span> | <span data-ttu-id="bf1ca-255">43</span><span class="sxs-lookup"><span data-stu-id="bf1ca-255">43</span></span>
<span data-ttu-id="bf1ca-256">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-256">Generics</span></span> | [<span data-ttu-id="bf1ca-257">Genel türler ve Üyeler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-257">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="bf1ca-258">Genel bir tür, temel türdeki kısıtlamaların veya arabirimlerin genel tür kısıtlamaları tarafından karşılanabileceğini güvence altına almak için yeterli kısıtlamaları yeniden bildirir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-258">A generic type shall redeclare sufficient constraints to guarantee that any constraints on the base type, or interfaces would be satisfied by the generic type constraints.</span></span> | <span data-ttu-id="bf1ca-259">44</span><span class="sxs-lookup"><span data-stu-id="bf1ca-259">44</span></span>
<span data-ttu-id="bf1ca-260">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-260">Generics</span></span> | [<span data-ttu-id="bf1ca-261">Genel türler ve Üyeler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-261">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="bf1ca-262">Genel parametrelerde kısıtlama olarak kullanılan türler, CLS uyumlu olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-262">Types used as constraints on generic parameters shall themselves be CLS-compliant.</span></span> | <span data-ttu-id="bf1ca-263">45</span><span class="sxs-lookup"><span data-stu-id="bf1ca-263">45</span></span>
<span data-ttu-id="bf1ca-264">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-264">Generics</span></span> | [<span data-ttu-id="bf1ca-265">Genel türler ve Üyeler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-265">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="bf1ca-266">Bir örneklenmiş genel türdeki üyelerin görünürlük ve erişilebilirliği, bir bütün olarak genel tür bildirimi yerine belirli bir örnek oluşturma kapsamına alınır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-266">The visibility and accessibility of members (including nested types) in an instantiated generic type shall be considered to be scoped to the specific instantiation rather than the generic type declaration as a whole.</span></span> <span data-ttu-id="bf1ca-267">Bunun varsayılarak, CLS kuralı 12 ' nin görünürlük ve erişilebilirlik kuralları hala geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-267">Assuming this, the visibility and accessibility rules of CLS rule 12 still apply.</span></span> | <span data-ttu-id="bf1ca-268">46</span><span class="sxs-lookup"><span data-stu-id="bf1ca-268">46</span></span>
<span data-ttu-id="bf1ca-269">Genel Türler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-269">Generics</span></span> | [<span data-ttu-id="bf1ca-270">Genel türler ve Üyeler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-270">Generic types and members</span></span>](#generic-types-and-members) | <span data-ttu-id="bf1ca-271">Her soyut veya sanal genel yöntem için, varsayılan bir somut (soyut olmayan) uygulama olacaktır</span><span class="sxs-lookup"><span data-stu-id="bf1ca-271">For each abstract or virtual generic method, there shall be a default concrete (nonabstract) implementation</span></span> | <span data-ttu-id="bf1ca-272">47</span><span class="sxs-lookup"><span data-stu-id="bf1ca-272">47</span></span>
<span data-ttu-id="bf1ca-273">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-273">Interfaces</span></span> | [<span data-ttu-id="bf1ca-274">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-274">Interfaces</span></span>](#interfaces) | <span data-ttu-id="bf1ca-275">CLS uyumlu arabirimler, CLS uyumlu olmayan yöntemlerin uygulanması için tanımı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-275">CLS-compliant interfaces shall not require the definition of non-CLS compliant methods in order to implement them.</span></span> | <span data-ttu-id="bf1ca-276">18</span><span class="sxs-lookup"><span data-stu-id="bf1ca-276">18</span></span>
<span data-ttu-id="bf1ca-277">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-277">Interfaces</span></span> | [<span data-ttu-id="bf1ca-278">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-278">Interfaces</span></span>](#interfaces) | <span data-ttu-id="bf1ca-279">CLS uyumlu arabirimler statik yöntemler tanımlamaz ve alanları tanımlayamazlar.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-279">CLS-compliant interfaces shall not define static methods, nor shall they define fields.</span></span> | <span data-ttu-id="bf1ca-280">19</span><span class="sxs-lookup"><span data-stu-id="bf1ca-280">19</span></span>
<span data-ttu-id="bf1ca-281">Üyeler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-281">Members</span></span> | [<span data-ttu-id="bf1ca-282">Genel olarak tür üyeleri</span><span class="sxs-lookup"><span data-stu-id="bf1ca-282">Type members in general</span></span>](#type-members-in-general) | <span data-ttu-id="bf1ca-283">Genel statik alanlar ve yöntemler CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-283">Global static fields and methods are not CLS-compliant.</span></span> | <span data-ttu-id="bf1ca-284">36</span><span class="sxs-lookup"><span data-stu-id="bf1ca-284">36</span></span>
<span data-ttu-id="bf1ca-285">Üyeler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-285">Members</span></span> | -- | <span data-ttu-id="bf1ca-286">Bir sabit değer statik değeri, alan başlatma meta verilerinin kullanımı aracılığıyla belirtilir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-286">The value of a literal static is specified through the use of field initialization metadata.</span></span> <span data-ttu-id="bf1ca-287">CLS uyumlu bir sabit değeri, alan başlatma meta verilerinde tam olarak aynı türde (ya da değişmez değer ise) bir değere sahip olmalıdır `enum` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-287">A CLS-compliant literal must have a value specified in field initialization metadata that is of exactly the same type as the literal (or of the underlying type, if that literal is an `enum`).</span></span> | <span data-ttu-id="bf1ca-288">13</span><span class="sxs-lookup"><span data-stu-id="bf1ca-288">13</span></span>
<span data-ttu-id="bf1ca-289">Üyeler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-289">Members</span></span> | [<span data-ttu-id="bf1ca-290">Genel olarak tür üyeleri</span><span class="sxs-lookup"><span data-stu-id="bf1ca-290">Type members in general</span></span>](#type-members-in-general) | <span data-ttu-id="bf1ca-291">Vararg kısıtlaması CLS kapsamında değildir ve CLS tarafından desteklenen tek çağırma kuralı Standart yönetilen çağırma kuralıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-291">The vararg constraint is not part of the CLS, and the only calling convention supported by the CLS is the standard managed calling convention.</span></span> | <span data-ttu-id="bf1ca-292">15</span><span class="sxs-lookup"><span data-stu-id="bf1ca-292">15</span></span>
<span data-ttu-id="bf1ca-293">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="bf1ca-293">Naming conventions</span></span> | [<span data-ttu-id="bf1ca-294">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="bf1ca-294">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="bf1ca-295">Derlemeler, [Unicode normalleştirme formlarında](https://www.unicode.org/unicode/reports/tr15/tr15-18.html)çevrimiçi olarak kullanılabilir olan ve tanımlayıcılara dahil edilip edilmelerine izin verilen karakter kümesini yöneten Unicode standart 3.0 'ın ek 7 Technical Report 15 ' i izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-295">Assemblies shall follow Annex 7 of Technical Report 15 of the Unicode Standard3.0 governing the set of characters permitted to start and be included in identifiers, available online at [Unicode Normalization Forms](https://www.unicode.org/unicode/reports/tr15/tr15-18.html).</span></span> <span data-ttu-id="bf1ca-296">Tanımlayıcılar Unicode normalleştirme biçimi C tarafından tanımlanan kurallı biçimde olacaktır. CLS amacıyla, küçük harfli eşlemelerde (Unicode yerel ayarı duyarsız, bire bir küçük harf eşleştirmelerde belirtildiği gibi) iki tanımlayıcı aynıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-296">Identifiers shall be in the canonical format defined by Unicode Normalization Form C. For CLS purposes, two identifiers are the same if their lowercase mappings (as specified by the Unicode locale-insensitive, one-to-one lowercase mappings) are the same.</span></span> <span data-ttu-id="bf1ca-297">Diğer bir deyişle, iki tanımlayıcı CLS kapsamında farklı olarak kabul edilmelidir, ancak büyük küçük harf bakımından farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-297">That is, for two identifiers to be considered different under the CLS they shall differ in more than simply their case.</span></span> <span data-ttu-id="bf1ca-298">Ancak, devralınan bir tanımı geçersiz kılmak için CLı, özgün bildirimin kesin kodlamasının kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-298">However, in order to override an inherited definition the CLI requires the precise encoding of the original declaration be used.</span></span> | <span data-ttu-id="bf1ca-299">4</span><span class="sxs-lookup"><span data-stu-id="bf1ca-299">4</span></span>
<span data-ttu-id="bf1ca-300">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="bf1ca-300">Overloading</span></span> | [<span data-ttu-id="bf1ca-301">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="bf1ca-301">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="bf1ca-302">CLS uyumlu bir kapsamda sunulan tüm adlar, adların özdeş ve aşırı yükleme yoluyla çözümlenme dışında, türden bağımsız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-302">All names introduced in a CLS-compliant scope shall be distinct independent of kind, except where the names are identical and resolved via overloading.</span></span> <span data-ttu-id="bf1ca-303">Diğer bir deyişle, CTS tek bir türün bir yöntem ve bir alan için aynı adı kullanmasına izin veriyorsa, CLS değildir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-303">That is, while the CTS allows a single type to use the same name for a method and a field, the CLS does not.</span></span> | <span data-ttu-id="bf1ca-304">5</span><span class="sxs-lookup"><span data-stu-id="bf1ca-304">5</span></span>
<span data-ttu-id="bf1ca-305">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="bf1ca-305">Overloading</span></span> | [<span data-ttu-id="bf1ca-306">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="bf1ca-306">Naming conventions</span></span>](#naming-conventions) | <span data-ttu-id="bf1ca-307">CTS ayrı imzaların ayırt etmesine izin verdiğinden bağımsız olarak, alanlar ve iç içe türler tanımlayıcı karşılaştırmaya göre birbirinden ayrı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-307">Fields and nested types shall be distinct by identifier comparison alone, even though the CTS allows distinct signatures to be distinguished.</span></span> <span data-ttu-id="bf1ca-308">Aynı ada (tanımlayıcı karşılaştırmaya göre) sahip Yöntemler, Özellikler ve olaylar, CLS kuralı 39 ' de belirtilmedikçe, yalnızca dönüş türünden daha fazla farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-308">Methods, properties, and events that have the same name (by identifier comparison) shall differ by more than just the return type,except as specified in CLS Rule 39</span></span> | <span data-ttu-id="bf1ca-309">6</span><span class="sxs-lookup"><span data-stu-id="bf1ca-309">6</span></span>
<span data-ttu-id="bf1ca-310">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="bf1ca-310">Overloading</span></span> | [<span data-ttu-id="bf1ca-311">Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-311">Overloads</span></span>](#overloads) | <span data-ttu-id="bf1ca-312">Yalnızca özellikler ve yöntemler aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-312">Only properties and methods can be overloaded.</span></span> | <span data-ttu-id="bf1ca-313">37</span><span class="sxs-lookup"><span data-stu-id="bf1ca-313">37</span></span>
<span data-ttu-id="bf1ca-314">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="bf1ca-314">Overloading</span></span> | [<span data-ttu-id="bf1ca-315">Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-315">Overloads</span></span>](#overloads) |<span data-ttu-id="bf1ca-316">Özellikler ve yöntemler yalnızca parametrelerinin sayısı ve türleri temel alınarak aşırı yüklenebilir, ve adlı dönüştürme işleçleri, `op_Implicit` `op_Explicit` dönüş türlerine göre de aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-316">Properties and methods can be overloaded based only on the number and types of their parameters, except the conversion operators named `op_Implicit` and `op_Explicit`, which can also be overloaded based on their return type.</span></span> | <span data-ttu-id="bf1ca-317">38</span><span class="sxs-lookup"><span data-stu-id="bf1ca-317">38</span></span>
<span data-ttu-id="bf1ca-318">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="bf1ca-318">Overloading</span></span> | -- | <span data-ttu-id="bf1ca-319">Bir tür içinde belirtilen iki veya daha fazla CLS uyumlu Yöntem aynı ada sahiptir ve belirli bir tür örneklemesiyse, aynı parametre ve dönüş türlerine sahiptirler, tüm bu yöntemler bu tür örneklemelerinden anlam açısından eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-319">If two or more CLS-compliant methods declared in a type have the same name and, for a specific set of type instantiations, they have the same parameter and return types, then all these methods shall be semantically equivalent at those type instantiations.</span></span> | <span data-ttu-id="bf1ca-320">48</span><span class="sxs-lookup"><span data-stu-id="bf1ca-320">48</span></span>
<span data-ttu-id="bf1ca-321">Özellikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-321">Properties</span></span> | [<span data-ttu-id="bf1ca-322">Özellikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-322">Properties</span></span>](#properties) | <span data-ttu-id="bf1ca-323">Bir özelliğin alıcı ve ayarlayıcı yöntemlerini uygulayan yöntemler `SpecialName` meta verilerde işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-323">The methods that implement the getter and setter methods of a property shall be marked `SpecialName` in the metadata.</span></span> | <span data-ttu-id="bf1ca-324">24</span><span class="sxs-lookup"><span data-stu-id="bf1ca-324">24</span></span>
<span data-ttu-id="bf1ca-325">Özellikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-325">Properties</span></span> | [<span data-ttu-id="bf1ca-326">Özellikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-326">Properties</span></span>](#properties) | <span data-ttu-id="bf1ca-327">Bir özelliğin erişimcileri statik, hepsi sanal veya hepsi örnek olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-327">A property's accessors shall all be static, all be virtual, or all be instance.</span></span> | <span data-ttu-id="bf1ca-328">26</span><span class="sxs-lookup"><span data-stu-id="bf1ca-328">26</span></span>
<span data-ttu-id="bf1ca-329">Özellikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-329">Properties</span></span> | [<span data-ttu-id="bf1ca-330">Özellikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-330">Properties</span></span>](#properties) | <span data-ttu-id="bf1ca-331">Bir özelliğin türü, alıcının dönüş türü ve ayarlayıcının son bağımsız değişkeninin türü olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-331">The type of a property shall be the return type of the getter and the type of the last argument of the setter.</span></span> <span data-ttu-id="bf1ca-332">Özelliğin parametre türleri, alıcı parametrelerinin türleri ve ayarlayıcının son parametresi hariç tüm türleri olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-332">The types of the parameters of the property shall be the types of the parameters to the getter and the types of all but the final parameter of the setter.</span></span> <span data-ttu-id="bf1ca-333">Bu türlerin hepsi CLS uyumlu olur ve yönetilen işaretçiler olmaz (yani, başvuruya göre geçirilmemelidir).</span><span class="sxs-lookup"><span data-stu-id="bf1ca-333">All of these types shall be CLS-compliant, and shall not be managed pointers (that is, shall not be passed by reference).</span></span> | <span data-ttu-id="bf1ca-334">27</span><span class="sxs-lookup"><span data-stu-id="bf1ca-334">27</span></span>
<span data-ttu-id="bf1ca-335">Özellikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-335">Properties</span></span> | [<span data-ttu-id="bf1ca-336">Özellikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-336">Properties</span></span>](#properties) | <span data-ttu-id="bf1ca-337">Özellikler belirli bir adlandırma düzenine bağlı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-337">Properties shall adhere to a specific naming pattern.</span></span> <span data-ttu-id="bf1ca-338">`SpecialName`CLS kuralı 24 ' te başvuruda bulunulan öznitelik, uygun ad karşılaştırmaları içinde yok sayılacak ve tanımlayıcı kurallarına uymalecektir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-338">The `SpecialName` attribute referred to in CLS rule 24 shall be ignored in appropriate name comparisons and shall adhere to identifier rules.</span></span> <span data-ttu-id="bf1ca-339">Bir özelliğin alıcı yöntemi, ayarlayıcı yöntemi veya her ikisi de olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-339">A property shall have a getter method, a setter method, or both.</span></span> | <span data-ttu-id="bf1ca-340">28</span><span class="sxs-lookup"><span data-stu-id="bf1ca-340">28</span></span>
<span data-ttu-id="bf1ca-341">Tür dönüştürme</span><span class="sxs-lookup"><span data-stu-id="bf1ca-341">Type conversion</span></span> | [<span data-ttu-id="bf1ca-342">Tür dönüştürme</span><span class="sxs-lookup"><span data-stu-id="bf1ca-342">Type conversion</span></span>](#type-conversion) | <span data-ttu-id="bf1ca-343">Op_Implicit veya op_Explicit sağlandıysa, zorlama sağlamak için alternatif bir yol sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-343">If either op_Implicit or op_Explicit is provided, an alternate means of providing the coercion shall be provided.</span></span> | <span data-ttu-id="bf1ca-344">39</span><span class="sxs-lookup"><span data-stu-id="bf1ca-344">39</span></span>
<span data-ttu-id="bf1ca-345">Türler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-345">Types</span></span> | [<span data-ttu-id="bf1ca-346">Türler ve tür üye imzaları</span><span class="sxs-lookup"><span data-stu-id="bf1ca-346">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="bf1ca-347">Paketlenmiş değer türleri CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-347">Boxed value types are not CLS-compliant.</span></span> | <span data-ttu-id="bf1ca-348">3</span><span class="sxs-lookup"><span data-stu-id="bf1ca-348">3</span></span>
<span data-ttu-id="bf1ca-349">Türler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-349">Types</span></span> | [<span data-ttu-id="bf1ca-350">Türler ve tür üye imzaları</span><span class="sxs-lookup"><span data-stu-id="bf1ca-350">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="bf1ca-351">Bir imzada görünen tüm türler CLS uyumlu olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-351">All types appearing in a signature shall be CLS-compliant.</span></span> <span data-ttu-id="bf1ca-352">Örneklenmiş genel bir tür oluşturan tüm türler CLS uyumlu olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-352">All types composing an instantiated generic type shall be CLS-compliant.</span></span> | <span data-ttu-id="bf1ca-353">11</span><span class="sxs-lookup"><span data-stu-id="bf1ca-353">11</span></span>
<span data-ttu-id="bf1ca-354">Türler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-354">Types</span></span> | [<span data-ttu-id="bf1ca-355">Türler ve tür üye imzaları</span><span class="sxs-lookup"><span data-stu-id="bf1ca-355">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="bf1ca-356">Yazılan başvurular CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-356">Typed references are not CLS-compliant.</span></span> | <span data-ttu-id="bf1ca-357">14</span><span class="sxs-lookup"><span data-stu-id="bf1ca-357">14</span></span>
<span data-ttu-id="bf1ca-358">Türler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-358">Types</span></span> | [<span data-ttu-id="bf1ca-359">Türler ve tür üye imzaları</span><span class="sxs-lookup"><span data-stu-id="bf1ca-359">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="bf1ca-360">Yönetilmeyen işaretçi türleri CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-360">Unmanaged pointer types are not CLS-compliant.</span></span> | <span data-ttu-id="bf1ca-361">17</span><span class="sxs-lookup"><span data-stu-id="bf1ca-361">17</span></span>
<span data-ttu-id="bf1ca-362">Türler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-362">Types</span></span> | [<span data-ttu-id="bf1ca-363">Türler ve tür üye imzaları</span><span class="sxs-lookup"><span data-stu-id="bf1ca-363">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="bf1ca-364">CLS uyumlu sınıflar, değer türleri ve arabirimler, CLS uyumlu olmayan üyelerin uygulanmasını gerektirmez</span><span class="sxs-lookup"><span data-stu-id="bf1ca-364">CLS-compliant classes, value types, and interfaces shall not require the implementation of non-CLS-compliant members</span></span> | <span data-ttu-id="bf1ca-365">20</span><span class="sxs-lookup"><span data-stu-id="bf1ca-365">20</span></span>
<span data-ttu-id="bf1ca-366">Türler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-366">Types</span></span> | [<span data-ttu-id="bf1ca-367">Türler ve tür üye imzaları</span><span class="sxs-lookup"><span data-stu-id="bf1ca-367">Types and type member signatures</span></span>](#types-and-type-member-signatures) | <span data-ttu-id="bf1ca-368">[System. Object](xref:System.Object) CLS uyumludur.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-368">[System.Object](xref:System.Object) is CLS-compliant.</span></span> <span data-ttu-id="bf1ca-369">Diğer CLS uyumlu sınıflar, CLS uyumlu bir sınıftan devralınır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-369">Any other CLS-compliant class shall inherit from a CLS-compliant class.</span></span> | <span data-ttu-id="bf1ca-370">23</span><span class="sxs-lookup"><span data-stu-id="bf1ca-370">23</span></span>

### <a name="types-and-type-member-signatures"></a><span data-ttu-id="bf1ca-371">Türler ve tür üye imzaları</span><span class="sxs-lookup"><span data-stu-id="bf1ca-371">Types and type member signatures</span></span>

<span data-ttu-id="bf1ca-372">[System. Object](xref:System.Object) türü CLS uyumludur ve .NET Framework türü sistemindeki tüm nesne türlerinin temel türüdür.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-372">The [System.Object](xref:System.Object) type is CLS-compliant and is the base type of all object types in the .NET Framework type system.</span></span> <span data-ttu-id="bf1ca-373">.NET Framework devralma örtük olarak (örneğin, [dize](xref:System.String) sınıfı dolaylı olarak `Object` sınıftan devralır) veya açık (örneğin, [Kültürenotfoundexception](xref:System.Globalization.CultureNotFoundException) sınıfı açıkça [özel durum](xref:System.Exception) sınıfından devralınan [ArgumentException](xref:System.ArgumentException) sınıfından devralır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-373">Inheritance in the .NET Framework is either implicit (for example, the [String](xref:System.String) class implicitly inherits from the `Object` class) or explicit (for example, the [CultureNotFoundException](xref:System.Globalization.CultureNotFoundException) class explicitly inherits from the [ArgumentException](xref:System.ArgumentException) class, which explicitly inherits from the [Exception](xref:System.Exception) class.</span></span> <span data-ttu-id="bf1ca-374">Türetilmiş bir türün CLS uyumlu olması için, taban türünün de CLS uyumlu olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-374">For a derived type to be CLS compliant, its base type must also be CLS-compliant.</span></span>

<span data-ttu-id="bf1ca-375">Aşağıdaki örnek, temel türü CLS uyumlu olmayan türetilmiş bir türü gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-375">The following example shows a derived type whose base type is not CLS-compliant.</span></span> <span data-ttu-id="bf1ca-376">`Counter`İşaretsiz 32 bitlik bir tamsayıyı sayaç olarak kullanan bir temel sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-376">It defines a base `Counter` class that uses an unsigned 32-bit integer as a counter.</span></span> <span data-ttu-id="bf1ca-377">Sınıfı işaretsiz bir tamsayı sarmalayarak sayaç işlevselliği sağladığından, sınıf CLS uyumlu değil olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-377">Because the class provides counter functionality by wrapping an unsigned integer, the class is marked as non-CLS-compliant.</span></span> <span data-ttu-id="bf1ca-378">Sonuç olarak, türetilmiş bir sınıf `NonZeroCounter` de CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-378">As a result, a derived class, `NonZeroCounter`, is also not CLS-compliant.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

[CLSCompliant(false)]
public class Counter
{
   UInt32 ctr;

   public Counter()
   {
      ctr = 0;
   }

   protected Counter(UInt32 ctr)
   {
      this.ctr = ctr;
   }

   public override string ToString()
   {
      return $"{ctr}). ";
   }

   public UInt32 Value
   {
      get { return ctr; }
   }

   public void Increment()
   {
      ctr += (uint) 1;
   }
}

public class NonZeroCounter : Counter
{
   public NonZeroCounter(int startIndex) : this((uint) startIndex)
   {
   }

   private NonZeroCounter(UInt32 startIndex) : base(startIndex)
   {
   }
}
// Compilation produces a compiler warning like the following:
//    Type3.cs(37,14): warning CS3009: 'NonZeroCounter': base type 'Counter' is not
//            CLS-compliant
//    Type3.cs(7,14): (Location of symbol related to previous warning)
```

```vb
<Assembly: CLSCompliant(True)>

<CLSCompliant(False)> _
Public Class Counter
   Dim ctr As UInt32

   Public Sub New
      ctr = 0
   End Sub

   Protected Sub New(ctr As UInt32)
      ctr = ctr
   End Sub

   Public Overrides Function ToString() As String
      Return $"{ctr}). "
   End Function

   Public ReadOnly Property Value As UInt32
      Get
         Return ctr
      End Get
   End Property

   Public Sub Increment()
      ctr += CType(1, UInt32)
   End Sub
End Class

Public Class NonZeroCounter : Inherits Counter
   Public Sub New(startIndex As Integer)
      MyClass.New(CType(startIndex, UInt32))
   End Sub

   Private Sub New(startIndex As UInt32)
      MyBase.New(CType(startIndex, UInt32))
   End Sub
End Class
' Compilation produces a compiler warning like the following:
'    Type3.vb(34) : warning BC40026: 'NonZeroCounter' is not CLS-compliant
'    because it derives from 'Counter', which is not CLS-compliant.
'
'    Public Class NonZeroCounter : Inherits Counter
'                 ~~~~~~~~~~~~~~
```

<span data-ttu-id="bf1ca-379">Bir yöntemin dönüş türü veya özellik türü de dahil olmak üzere üye imzalarında görünen tüm türler CLS uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-379">All types that appear in member signatures, including a method's return type or a property type, must be CLS-compliant.</span></span> <span data-ttu-id="bf1ca-380">Bunlara ek olarak, genel türler için:</span><span class="sxs-lookup"><span data-stu-id="bf1ca-380">In addition, for generic types:</span></span>

* <span data-ttu-id="bf1ca-381">Bir örneklenmiş genel tür oluşturan tüm türler CLS uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-381">All types that compose an instantiated generic type must be CLS-compliant.</span></span>

* <span data-ttu-id="bf1ca-382">Genel parametrelerde kısıtlama olarak kullanılan tüm türler CLS uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-382">All types used as constraints on generic parameters must be CLS-compliant.</span></span>

<span data-ttu-id="bf1ca-383">.NET [ortak tür sistemi](common-type-system.md) , doğrudan ortak dil çalışma zamanı tarafından desteklenen ve bir derlemenin meta verilerinde özel olarak kodlanmış bir dizi yerleşik tür içerir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-383">The .NET [common type system](common-type-system.md) includes a number of built-in types that are supported directly by the common language runtime and are specially encoded in an assembly's metadata.</span></span> <span data-ttu-id="bf1ca-384">Bu iç türlerin, aşağıdaki tabloda listelenen türler CLS uyumludur.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-384">Of these intrinsic types, the types listed in the following table are CLS-compliant.</span></span>

<span data-ttu-id="bf1ca-385">CLS uyumlu tür</span><span class="sxs-lookup"><span data-stu-id="bf1ca-385">CLS-compliant type</span></span> | <span data-ttu-id="bf1ca-386">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf1ca-386">Description</span></span>
------------------ | -----------
[<span data-ttu-id="bf1ca-387">Bayt</span><span class="sxs-lookup"><span data-stu-id="bf1ca-387">Byte</span></span>](xref:System.Byte) | <span data-ttu-id="bf1ca-388">8 bit işaretsiz tamsayı</span><span class="sxs-lookup"><span data-stu-id="bf1ca-388">8-bit unsigned integer</span></span>
[<span data-ttu-id="bf1ca-389">Int16</span><span class="sxs-lookup"><span data-stu-id="bf1ca-389">Int16</span></span>](xref:System.Int16) | <span data-ttu-id="bf1ca-390">16 bit işaretli tamsayı</span><span class="sxs-lookup"><span data-stu-id="bf1ca-390">16-bit signed integer</span></span>
[<span data-ttu-id="bf1ca-391">Int32</span><span class="sxs-lookup"><span data-stu-id="bf1ca-391">Int32</span></span>](xref:System.Int32) | <span data-ttu-id="bf1ca-392">32-bit işaretli tamsayı</span><span class="sxs-lookup"><span data-stu-id="bf1ca-392">32-bit signed integer</span></span>
[<span data-ttu-id="bf1ca-393">Tutulamaz</span><span class="sxs-lookup"><span data-stu-id="bf1ca-393">Int64</span></span>](xref:System.Int64) | <span data-ttu-id="bf1ca-394">64-bit işaretli tamsayı</span><span class="sxs-lookup"><span data-stu-id="bf1ca-394">64-bit signed integer</span></span>
[<span data-ttu-id="bf1ca-395">Tek</span><span class="sxs-lookup"><span data-stu-id="bf1ca-395">Single</span></span>](xref:System.Single) | <span data-ttu-id="bf1ca-396">Tek duyarlıklı kayan nokta değeri</span><span class="sxs-lookup"><span data-stu-id="bf1ca-396">Single-precision floating-point value</span></span>
[<span data-ttu-id="bf1ca-397">Çift</span><span class="sxs-lookup"><span data-stu-id="bf1ca-397">Double</span></span>](xref:System.Double) | <span data-ttu-id="bf1ca-398">Çift duyarlıklı kayan nokta değeri</span><span class="sxs-lookup"><span data-stu-id="bf1ca-398">Double-precision floating-point value</span></span>
[<span data-ttu-id="bf1ca-399">Boole</span><span class="sxs-lookup"><span data-stu-id="bf1ca-399">Boolean</span></span>](xref:System.Boolean) | <span data-ttu-id="bf1ca-400">doğru veya yanlış değer türü</span><span class="sxs-lookup"><span data-stu-id="bf1ca-400">true or false value type</span></span>
[<span data-ttu-id="bf1ca-401">Char</span><span class="sxs-lookup"><span data-stu-id="bf1ca-401">Char</span></span>](xref:System.Char) | <span data-ttu-id="bf1ca-402">UTF-16 kodlu kod birimi</span><span class="sxs-lookup"><span data-stu-id="bf1ca-402">UTF-16 encoded code unit</span></span>
[<span data-ttu-id="bf1ca-403">Kategori</span><span class="sxs-lookup"><span data-stu-id="bf1ca-403">Decimal</span></span>](xref:System.Decimal) | <span data-ttu-id="bf1ca-404">Kayan nokta olmayan ondalık sayı</span><span class="sxs-lookup"><span data-stu-id="bf1ca-404">Non-floating-point decimal number</span></span>
[<span data-ttu-id="bf1ca-405">Serisi</span><span class="sxs-lookup"><span data-stu-id="bf1ca-405">IntPtr</span></span>](xref:System.IntPtr) | <span data-ttu-id="bf1ca-406">Platform tanımlı boyutun işaretçisi veya işleyicisi</span><span class="sxs-lookup"><span data-stu-id="bf1ca-406">Pointer or handle of a platform-defined size</span></span>
[<span data-ttu-id="bf1ca-407">Dize</span><span class="sxs-lookup"><span data-stu-id="bf1ca-407">String</span></span>](xref:System.String) | <span data-ttu-id="bf1ca-408">Sıfır, bir veya daha fazla Char nesnesi koleksiyonu</span><span class="sxs-lookup"><span data-stu-id="bf1ca-408">Collection of zero, one, or more Char objects</span></span>

<span data-ttu-id="bf1ca-409">Aşağıdaki tabloda listelenen iç türler CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-409">The intrinsic types listed in the following table are not CLS-Compliant.</span></span>

<span data-ttu-id="bf1ca-410">Uyumlu olmayan tür</span><span class="sxs-lookup"><span data-stu-id="bf1ca-410">Non-compliant type</span></span> | <span data-ttu-id="bf1ca-411">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf1ca-411">Description</span></span> | <span data-ttu-id="bf1ca-412">CLS uyumlu alternatif</span><span class="sxs-lookup"><span data-stu-id="bf1ca-412">CLS-compliant alternative</span></span>
------------------ | ----------- | -------------------------
[<span data-ttu-id="bf1ca-413">SByte</span><span class="sxs-lookup"><span data-stu-id="bf1ca-413">SByte</span></span>](xref:System.SByte) | <span data-ttu-id="bf1ca-414">8 bit işaretli tamsayı veri türü</span><span class="sxs-lookup"><span data-stu-id="bf1ca-414">8-bit signed integer data type</span></span> | [<span data-ttu-id="bf1ca-415">Int16</span><span class="sxs-lookup"><span data-stu-id="bf1ca-415">Int16</span></span>](xref:System.Int16)
[<span data-ttu-id="bf1ca-416">UInt16</span><span class="sxs-lookup"><span data-stu-id="bf1ca-416">UInt16</span></span>](xref:System.UInt16) | <span data-ttu-id="bf1ca-417">16 bit işaretsiz tamsayı</span><span class="sxs-lookup"><span data-stu-id="bf1ca-417">16-bit unsigned integer</span></span> | [<span data-ttu-id="bf1ca-418">Int32</span><span class="sxs-lookup"><span data-stu-id="bf1ca-418">Int32</span></span>](xref:System.Int32)
[<span data-ttu-id="bf1ca-419">UInt32</span><span class="sxs-lookup"><span data-stu-id="bf1ca-419">UInt32</span></span>](xref:System.UInt32) | <span data-ttu-id="bf1ca-420">32-bit işaretsiz tamsayı</span><span class="sxs-lookup"><span data-stu-id="bf1ca-420">32-bit unsigned integer</span></span> | [<span data-ttu-id="bf1ca-421">Tutulamaz</span><span class="sxs-lookup"><span data-stu-id="bf1ca-421">Int64</span></span>](xref:System.Int64)
[<span data-ttu-id="bf1ca-422">UInt64</span><span class="sxs-lookup"><span data-stu-id="bf1ca-422">UInt64</span></span>](xref:System.UInt64) | <span data-ttu-id="bf1ca-423">64-bit işaretsiz tamsayı</span><span class="sxs-lookup"><span data-stu-id="bf1ca-423">64-bit unsigned integer</span></span> | <span data-ttu-id="bf1ca-424">[Int64](xref:System.Int64) (taşma olabilir), [BigInteger](xref:System.Numerics.BigInteger)veya [Double](xref:System.Double)</span><span class="sxs-lookup"><span data-stu-id="bf1ca-424">[Int64](xref:System.Int64) (may overflow), [BigInteger](xref:System.Numerics.BigInteger), or [Double](xref:System.Double)</span></span>
[<span data-ttu-id="bf1ca-425">UIntPtr</span><span class="sxs-lookup"><span data-stu-id="bf1ca-425">UIntPtr</span></span>](xref:System.UIntPtr) | <span data-ttu-id="bf1ca-426">İşaretsiz işaretçi veya tanıtıcı</span><span class="sxs-lookup"><span data-stu-id="bf1ca-426">Unsigned pointer or handle</span></span> | [<span data-ttu-id="bf1ca-427">Serisi</span><span class="sxs-lookup"><span data-stu-id="bf1ca-427">IntPtr</span></span>](xref:System.IntPtr)

<span data-ttu-id="bf1ca-428">.NET Framework sınıf kitaplığı veya başka bir sınıf kitaplığı CLS uyumlu olmayan diğer türleri içerebilir; Örneğin:</span><span class="sxs-lookup"><span data-stu-id="bf1ca-428">The .NET Framework Class Library or any other class library may include other types that aren't CLS-compliant; for example:</span></span>

* <span data-ttu-id="bf1ca-429">Paketlenmiş değer türleri.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-429">Boxed value types.</span></span> <span data-ttu-id="bf1ca-430">Aşağıdaki C# örneği, adında ortak bir özelliği olan bir sınıf oluşturur `int*` `Value` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-430">The following C# example creates a class that has a public property of type `int*` named `Value`.</span></span> <span data-ttu-id="bf1ca-431">Bir `int*` paketlenmiş değer türü olduğundan, derleyici onu CLS uyumlu değil olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-431">Because an `int*` is a boxed value type, the compiler flags it as non-CLS-compliant.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public unsafe class TestClass
{
   private int* val;

   public TestClass(int number)
   {
      val = (int*) number;
   }

   public int* Value {
      get { return val; }
   }
}
// The compiler generates the following output when compiling this example:
//        warning CS3003: Type of 'TestClass.Value' is not CLS-compliant
```

* <span data-ttu-id="bf1ca-432">Bir nesneye başvuru ve bir tür başvurusu içeren özel yapılar olan yazılı başvurular.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-432">Typed references, which are special constructs that contain a reference to an object and a reference to a type.</span></span>

<span data-ttu-id="bf1ca-433">Bir tür CLS uyumlu değilse, [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) özniteliğini değerine sahip bir *ısuyumlu* parametresiyle uygulamanız gerekir `false` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-433">If a type is not CLS-compliant, you should apply the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute with an *isCompliant* parameter with a value of `false` to it.</span></span> <span data-ttu-id="bf1ca-434">Daha fazla bilgi için [CLSCompliantAttribute özniteliği](#the-clscompliantattribute-attribute) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-434">For more information, see the [CLSCompliantAttribute attribute](#the-clscompliantattribute-attribute) section.</span></span>

<span data-ttu-id="bf1ca-435">Aşağıdaki örnek, bir yöntem imzasında ve genel tür örnek oluşturmada CLS uyumluluğu sorununu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-435">The following example illustrates the problem of CLS compliance in a method signature and in generic type instantiation.</span></span> <span data-ttu-id="bf1ca-436">`InvoiceItem` [UInt32](xref:System.UInt32)türünde bir özelliği olan bir sınıfı, [null atanabilir](xref:System.Nullable%601)türünde bir özelliği ve ve türünde parametreleri olan bir oluşturucuyu tanımlar `UInt32` `Nullable(Of UInt32)` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-436">It defines an `InvoiceItem` class with a property of type [UInt32](xref:System.UInt32), a property of type [Nullable(Of UInt32)](xref:System.Nullable%601), and a constructor with parameters of type `UInt32` and `Nullable(Of UInt32)`.</span></span> <span data-ttu-id="bf1ca-437">Bu örneği derlemeye çalıştığınızda dört derleyici uyarısı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-437">You get four compiler warnings when you try to compile this example.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class InvoiceItem
{
   private uint invId = 0;
   private uint itemId = 0;
   private Nullable<uint> qty;

   public InvoiceItem(uint sku, Nullable<uint> quantity)
   {
      itemId = sku;
      qty = quantity;
   }

   public Nullable<uint> Quantity
   {
      get { return qty; }
      set { qty = value; }
   }

   public uint InvoiceId
   {
      get { return invId; }
      set { invId = value; }
   }
}
// The attempt to compile the example displays the following output:
//    Type1.cs(13,23): warning CS3001: Argument type 'uint' is not CLS-compliant
//    Type1.cs(13,33): warning CS3001: Argument type 'uint?' is not CLS-compliant
//    Type1.cs(19,26): warning CS3003: Type of 'InvoiceItem.Quantity' is not CLS-compliant
//    Type1.cs(25,16): warning CS3003: Type of 'InvoiceItem.InvoiceId' is not CLS-compliant
```

```vb
<Assembly: CLSCompliant(True)>

Public Class InvoiceItem

   Private invId As UInteger = 0
   Private itemId As UInteger = 0
   Private qty AS Nullable(Of UInteger)

   Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
      itemId = sku
      qty = quantity
   End Sub

   Public Property Quantity As Nullable(Of UInteger)
      Get
         Return qty
      End Get
      Set
         qty = value
      End Set
   End Property

   Public Property InvoiceId As UInteger
      Get
         Return invId
      End Get
      Set
         invId = value
      End Set
   End Property
End Class
' The attempt to compile the example displays output similar to the following:
'    Type1.vb(13) : warning BC40028: Type of parameter 'sku' is not CLS-compliant.
'
'       Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
'                      ~~~
'    Type1.vb(13) : warning BC40041: Type 'UInteger' is not CLS-compliant.
'
'       Public Sub New(sku As UInteger, quantity As Nullable(Of UInteger))
'                                                               ~~~~~~~~
'    Type1.vb(18) : warning BC40041: Type 'UInteger' is not CLS-compliant.
'
'       Public Property Quantity As Nullable(Of UInteger)
'                                               ~~~~~~~~
'    Type1.vb(27) : warning BC40027: Return type of function 'InvoiceId' is not CLS-compliant.
'
'       Public Property InvoiceId As UInteger
```

<span data-ttu-id="bf1ca-438">Derleyici uyarılarını ortadan kaldırmak için, ortak arabirimdeki CLS uyumlu olmayan türleri `InvoiceItem` uyumlu türler ile değiştirin:</span><span class="sxs-lookup"><span data-stu-id="bf1ca-438">To eliminate the compiler warnings, replace the non-CLS-compliant types in the `InvoiceItem` public interface with compliant types:</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class InvoiceItem
{
   private uint invId = 0;
   private uint itemId = 0;
   private Nullable<int> qty;

   public InvoiceItem(int sku, Nullable<int> quantity)
   {
      if (sku <= 0)
         throw new ArgumentOutOfRangeException("The item number is zero or negative.");
      itemId = (uint) sku;

      qty = quantity;
   }

   public Nullable<int> Quantity
   {
      get { return qty; }
      set { qty = value; }
   }

   public int InvoiceId
   {
      get { return (int) invId; }
      set {
         if (value <= 0)
            throw new ArgumentOutOfRangeException("The invoice number is zero or negative.");
         invId = (uint) value; }
   }
}
```

```vb
Assembly: CLSCompliant(True)>

Public Class InvoiceItem

   Private invId As UInteger = 0
   Private itemId As UInteger = 0
   Private qty AS Nullable(Of Integer)

   Public Sub New(sku As Integer, quantity As Nullable(Of Integer))
      If sku <= 0 Then
         Throw New ArgumentOutOfRangeException("The item number is zero or negative.")
      End If
      itemId = CUInt(sku)
      qty = quantity
   End Sub

   Public Property Quantity As Nullable(Of Integer)
      Get
         Return qty
      End Get
      Set
         qty = value
      End Set
   End Property

   Public Property InvoiceId As Integer
      Get
         Return CInt(invId)
      End Get
      Set
         invId = CUInt(value)
      End Set
   End Property
End Class
```

<span data-ttu-id="bf1ca-439">Listelenen belirli türlere ek olarak, bazı tür kategorileri CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-439">In addition to the specific types listed, some categories of types are not CLS compliant.</span></span> <span data-ttu-id="bf1ca-440">Bunlar, yönetilmeyen işaretçi türlerini ve işlev işaretçisi türlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-440">These include unmanaged pointer types and function pointer types.</span></span> <span data-ttu-id="bf1ca-441">Aşağıdaki örnek bir derleyici uyarısı oluşturur çünkü bir tamsayılar dizisi oluşturmak için bir tamsayı işaretçisi kullanır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-441">The following example generates a compiler warning because it uses a pointer to an integer to create an array of integers.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ArrayHelper
{
   unsafe public static Array CreateInstance(Type type, int* ptr, int items)
   {
      Array arr = Array.CreateInstance(type, items);
      int* addr = ptr;
      for (int ctr = 0; ctr < items; ctr++) {
          int value = *addr;
          arr.SetValue(value, ctr);
          addr++;
      }
      return arr;
   }
}
// The attempt to compile this example displays the following output:
//    UnmanagedPtr1.cs(8,57): warning CS3001: Argument type 'int*' is not CLS-compliant
```

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ArrayHelper
{
   unsafe public static Array CreateInstance(Type type, int* ptr, int items)
   {
      Array arr = Array.CreateInstance(type, items);
      int* addr = ptr;
      for (int ctr = 0; ctr < items; ctr++) {
          int value = *addr;
          arr.SetValue(value, ctr);
          addr++;
      }
      return arr;
   }
}
// The attempt to compile this example displays the following output:
//    UnmanagedPtr1.cs(8,57): warning CS3001: Argument type 'int*' is not CLS-compliant
```

<span data-ttu-id="bf1ca-442">CLS uyumlu soyut sınıflar (yani, C# dilinde olarak işaretlenen sınıflar `abstract` ) için, sınıfın tüm üyeleri de CLS uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-442">For CLS-compliant abstract classes (that is, classes marked as `abstract` in C#), all members of the class must also be CLS-compliant.</span></span>

### <a name="naming-conventions"></a><span data-ttu-id="bf1ca-443">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="bf1ca-443">Naming conventions</span></span>

<span data-ttu-id="bf1ca-444">Bazı programlama dilleri büyük/küçük harf duyarsız olduğundan, tanımlayıcılar (ad alanları, türler ve Üyeler adları gibi) büyük/küçük harf bakımından farklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-444">Because some programming languages are case-insensitive, identifiers (such as the names of namespaces, types, and members) must differ by more than case.</span></span> <span data-ttu-id="bf1ca-445">Küçük harfler aynı ise, iki tanımlayıcı eşit kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-445">Two identifiers are considered equivalent if their lowercase mappings are the same.</span></span> <span data-ttu-id="bf1ca-446">Aşağıdaki C# örneği, ve olmak üzere iki ortak sınıfı tanımlar `Person` `person` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-446">The following C# example defines two public classes, `Person` and `person`.</span></span> <span data-ttu-id="bf1ca-447">Yalnızca büyük/küçük harf bakımından farklı olduğundan, C# derleyicisi bunları CLS uyumlu değil olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-447">Because they differ only by case, the C# compiler flags them as not CLS-compliant.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Person : person
{

}

public class person
{

}
// Compilation produces a compiler warning like the following:
//    Naming1.cs(11,14): warning CS3005: Identifier 'person' differing
//                       only in case is not CLS-compliant
//    Naming1.cs(6,14): (Location of symbol related to previous warning)
```

<span data-ttu-id="bf1ca-448">Ad alanları, türler ve üyelerin adları gibi programlama Dil tanımlayıcıları, [Unicode standart 3,0, teknik rapor 15, ek 7](https://www.unicode.org/reports/tr15/tr15-18.html)' ye uymalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-448">Programming language identifiers, such as the names of namespaces, types, and members, must conform to the [Unicode Standard 3.0, Technical Report 15, Annex 7](https://www.unicode.org/reports/tr15/tr15-18.html).</span></span> <span data-ttu-id="bf1ca-449">Bunun anlamı:</span><span class="sxs-lookup"><span data-stu-id="bf1ca-449">This means that:</span></span>

* <span data-ttu-id="bf1ca-450">Bir tanımlayıcının ilk karakteri herhangi bir Unicode büyük harf, küçük harf, başlık harf harf, değiştirici harf, diğer harf veya harf numarası olabilir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-450">The first character of an identifier can be any Unicode uppercase letter, lowercase letter, title case letter, modifier letter, other letter, or letter number.</span></span> <span data-ttu-id="bf1ca-451">Unicode karakter kategorileri hakkında daha fazla bilgi için bkz. [System. Globalization. UnicodeCategory](xref:System.Globalization.UnicodeCategory) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-451">For information on Unicode character categories, see the [System.Globalization.UnicodeCategory](xref:System.Globalization.UnicodeCategory) enumeration.</span></span>

* <span data-ttu-id="bf1ca-452">Sonraki karakterler, ilk karakter olarak kategorilerden herhangi birinden olabilir ve Aralık olmayan işaretler, boşluk birleştirme işaretleri, ondalık sayılar, bağlayıcı noktalamalar ve biçimlendirme kodları da içerebilir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-452">Subsequent characters can be from any of the categories as the first character, and can also include non-spacing marks, spacing combining marks, decimal numbers, connector punctuations, and formatting codes.</span></span>

<span data-ttu-id="bf1ca-453">Tanımlayıcıları karşılaştırmadan önce, tek bir karakter birden çok UTF-16 kodlu kod birimi ile temsil edilebilmesi için biçimlendirme kodlarını filtrelemeniz ve tanımlayıcıları Unicode normalleştirme biçimi C 'ye dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-453">Before you compare identifiers, you should filter out formatting codes and convert the identifiers to Unicode Normalization Form C, because a single character can be represented by multiple UTF-16-encoded code units.</span></span> <span data-ttu-id="bf1ca-454">Unicode normalleştirme biçimi C 'de aynı kod birimlerini üreten karakter dizileri CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-454">Character sequences that produce the same code units in Unicode Normalization Form C are not CLS-compliant.</span></span> <span data-ttu-id="bf1ca-455">Aşağıdaki örnek, bir adlı özelliği tanımlar `Å` , bu, ANGSTROM işareti (u + 212B) karakterini içerir ve ADıNDA `Å` halka olan LATIN büyük harf a karakterini içeren ikinci bir Özellik (u + 00C5).</span><span class="sxs-lookup"><span data-stu-id="bf1ca-455">The following example defines a property named `Å`, which consists of the character ANGSTROM SIGN (U+212B), and a second property named `Å` which consists of the character LATIN CAPITAL LETTER A WITH RING ABOVE (U+00C5).</span></span> <span data-ttu-id="bf1ca-456">C# derleyicisi, kaynak kodu CLS uyumlu değil olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-456">The C# compiler flags the source code as non-CLS-compliant.</span></span>

```csharp
public class Size
{
   private double a1;
   private double a2;

   public double Å
   {
       get { return a1; }
       set { a1 = value; }
   }

   public double Å
   {
       get { return a2; }
       set { a2 = value; }
   }
}
// Compilation produces a compiler warning like the following:
//    Naming2a.cs(16,18): warning CS3005: Identifier 'Size.Å' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(10,18): (Location of symbol related to previous warning)
//    Naming2a.cs(18,8): warning CS3005: Identifier 'Size.Å.get' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(12,8): (Location of symbol related to previous warning)
//    Naming2a.cs(19,8): warning CS3005: Identifier 'Size.Å.set' differing only in case is not
//            CLS-compliant
//    Naming2a.cs(13,8): (Location of symbol related to previous warning)
```

```vb
<Assembly: CLSCompliant(True)>
Public Class Size
   Private a1 As Double
   Private a2 As Double

   Public Property Å As Double
       Get
          Return a1
       End Get
       Set
          a1 = value
       End Set
   End Property

   Public Property Å As Double
       Get
          Return a2
       End Get
       Set
          a2 = value
       End Set
   End Property
End Class
' Compilation produces a compiler warning like the following:
'    Naming1.vb(9) : error BC30269: 'Public Property Å As Double' has multiple definitions
'     with identical signatures.
'
'       Public Property Å As Double
'                       ~
```

<span data-ttu-id="bf1ca-457">Belirli bir kapsamdaki üye adları (derleme içindeki ad alanları, bir ad alanı içindeki türler veya bir tür içindeki Üyeler), aşırı yükleme yoluyla çözümlenen adlar dışında benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-457">Member names within a particular scope (such as the namespaces within an assembly, the types within a namespace, or the members within a type) must be unique except for names that are resolved through overloading.</span></span> <span data-ttu-id="bf1ca-458">Bu gereksinim, bir kapsamdaki birden çok üyenin farklı üye türleri oldukları sürece (örneğin, bir yöntem ve biri bir alandır) aynı adlara sahip olmasını sağlayan ortak tür sisteminden daha sıkı bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-458">This requirement is more stringent than that of the common type system, which allows multiple members within a scope to have identical names as long as they are different kinds of members (for example, one is a method and one is a field).</span></span> <span data-ttu-id="bf1ca-459">Özellikle, tür üyeleri için:</span><span class="sxs-lookup"><span data-stu-id="bf1ca-459">In particular, for type members:</span></span>

* <span data-ttu-id="bf1ca-460">Alanlar ve iç içe türler yalnızca ada göre ayırt edilir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-460">Fields and nested types are distinguished by name alone.</span></span>

* <span data-ttu-id="bf1ca-461">Aynı ada sahip Yöntemler, Özellikler ve olaylar, yalnızca dönüş türünden daha fazla farklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-461">Methods, properties, and events that have the same name must differ by more than just return type.</span></span>

<span data-ttu-id="bf1ca-462">Aşağıdaki örnekte, üye adlarının kapsamları dahilinde benzersiz olması gereken gereksinim gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-462">The following example illustrates the requirement that member names must be unique within their scope.</span></span> <span data-ttu-id="bf1ca-463">Adında dört üye içeren adlı bir sınıfı tanımlar `Converter` `Conversion` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-463">It defines a class named `Converter` that includes four members named `Conversion`.</span></span> <span data-ttu-id="bf1ca-464">Üç yöntem ve biri bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-464">Three are methods, and one is a property.</span></span> <span data-ttu-id="bf1ca-465">Bir parametre içeren Yöntem `Int64` benzersiz olarak adlandırılır, ancak `Int32` dönüş değeri bir üyenin imzasının bir parçası olarak değerlendirilmediğinden parametre ile iki yöntem değildir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-465">The method that includes an `Int64` parameter is uniquely named, but the two methods with an `Int32` parameter are not, because return value is not considered a part of a member's signature.</span></span> <span data-ttu-id="bf1ca-466">`Conversion`Özellikler, aşırı yüklenmiş yöntemlerle aynı ada sahip olmadığından, bu gereksinimi da ihlal ediyor.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-466">The `Conversion` property also violates this requirement, because properties cannot have the same name as overloaded methods.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Converter
{
   public double Conversion(int number)
   {
      return (double) number;
   }

   public float Conversion(int number)
   {
      return (float) number;
   }

   public double Conversion(long number)
   {
      return (double) number;
   }

   public bool Conversion
   {
      get { return true; }
   }
}
// Compilation produces a compiler error like the following:
//    Naming3.cs(13,17): error CS0111: Type 'Converter' already defines a member called
//            'Conversion' with the same parameter types
//    Naming3.cs(8,18): (Location of symbol related to previous error)
//    Naming3.cs(23,16): error CS0102: The type 'Converter' already contains a definition for
//            'Conversion'
//    Naming3.cs(8,18): (Location of symbol related to previous error)
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Converter
   Public Function Conversion(number As Integer) As Double
      Return CDbl(number)
   End Function

   Public Function Conversion(number As Integer) As Single
      Return CSng(number)
   End Function

   Public Function Conversion(number As Long) As Double
      Return CDbl(number)
   End Function

   Public ReadOnly Property Conversion As Boolean
      Get
         Return True
      End Get
   End Property
End Class
' Compilation produces a compiler error like the following:
'    Naming3.vb(8) : error BC30301: 'Public Function Conversion(number As Integer) As Double'
'                    and 'Public Function Conversion(number As Integer) As Single' cannot
'                    overload each other because they differ only by return types.
'
'       Public Function Conversion(number As Integer) As Double
'                       ~~~~~~~~~~
'    Naming3.vb(20) : error BC30260: 'Conversion' is already declared as 'Public Function
'                     Conversion(number As Integer) As Single' in this class.
'
'       Public ReadOnly Property Conversion As Boolean
'                                ~~~~~~~~~~
```

<span data-ttu-id="bf1ca-467">Tek dillerde benzersiz anahtar sözcükler bulunur, bu nedenle ortak dil çalışma zamanını hedefleyen dillerin, anahtar sözcüklerle birlikte bulunan tanımlayıcılara (tür adları gibi) başvurmak için bazı mekanizmalar de sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-467">Individual languages include unique keywords, so languages that target the common language runtime must also provide some mechanism for referencing identifiers (such as type names) that coincide with keywords.</span></span> <span data-ttu-id="bf1ca-468">Örneğin, `case` hem C# hem de Visual Basic bir anahtar sözcüktür.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-468">For example, `case` is a keyword in both C# and Visual Basic.</span></span> <span data-ttu-id="bf1ca-469">Ancak, aşağıdaki Visual Basic örnek, `case` `case` açma ve kapatma küme ayraçlarını kullanarak anahtar sözcükten adlı bir sınıfın ayırt edebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-469">However, the following Visual Basic example is able to disambiguate a class named `case` from the `case` keyword by using opening and closing braces.</span></span> <span data-ttu-id="bf1ca-470">Aksi takdirde, örnek hata iletisi üretir, "anahtar sözcüğü tanımlayıcı olarak geçerli değildir" ve derleme başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-470">Otherwise, the example would produce the error message, "Keyword is not valid as an identifier," and fail to compile.</span></span>

```vb
Public Class [case]
   Private _id As Guid
   Private name As String

   Public Sub New(name As String)
      _id = Guid.NewGuid()
      Me.name = name
   End Sub

   Public ReadOnly Property ClientName As String
      Get
         Return name
      End Get
   End Property
End Class
```

<span data-ttu-id="bf1ca-471">Aşağıdaki C# örneği, `case` Language anahtar sözcüğünden tanımlayıcıyı ayırt etmek için @ sembolünü kullanarak sınıfın örneğini oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-471">The following C# example is able to instantiate the `case` class by using the @ symbol to disambiguate the identifier from the language keyword.</span></span> <span data-ttu-id="bf1ca-472">Bu olmadan, C# derleyicisi iki hata iletisi görüntüler, "tür bekleniyor" ve "geçersiz ifade terimi ' Case '."</span><span class="sxs-lookup"><span data-stu-id="bf1ca-472">Without it, the C# compiler would display two error messages, "Type expected" and "Invalid expression term 'case'."</span></span>

```csharp
using System;

public class Example
{
   public static void Main()
   {
      @case c = new @case("John");
      Console.WriteLine(c.ClientName);
   }
}
```

### <a name="type-conversion"></a><span data-ttu-id="bf1ca-473">Tür dönüştürme</span><span class="sxs-lookup"><span data-stu-id="bf1ca-473">Type conversion</span></span>

<span data-ttu-id="bf1ca-474">Ortak dil belirtimi iki dönüştürme işlecini tanımlar:</span><span class="sxs-lookup"><span data-stu-id="bf1ca-474">The Common Language Specification defines two conversion operators:</span></span>

* <span data-ttu-id="bf1ca-475">`op_Implicit`, veri veya duyarlık kaybına neden olmayan genişletme dönüştürmeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-475">`op_Implicit`, which is used for widening conversions that do not result in loss of data or precision.</span></span> <span data-ttu-id="bf1ca-476">Örneğin, [Decimal](xref:System.Decimal) yapısı `op_Implicit` Integral türlerinin ve [char](xref:System.Char) değerlerinin değerlerini değerlere dönüştürmek için aşırı yüklenmiş bir işleç içerir `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-476">For example, the [Decimal](xref:System.Decimal) structure includes an overloaded `op_Implicit` operator to convert values of integral types and [Char](xref:System.Char) values to `Decimal` values.</span></span>

* <span data-ttu-id="bf1ca-477">`op_Explicit`, büyüklük kaybı ile sonuçlanabilecek dönüştürmeleri daraltmak için kullanılır (bir değer, daha küçük bir aralığa sahip bir değere dönüştürülür) veya duyarlığına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-477">`op_Explicit`, which is used for narrowing conversions that can result in loss of magnitude (a value is converted to a value that has a smaller range) or precision.</span></span> <span data-ttu-id="bf1ca-478">Örneğin, `Decimal` Yapı `op_Explicit` [çift](xref:System.Double) ve [tek](xref:System.Single) değerleri ' a dönüştürmek için `Decimal` ve `Decimal` değerlerini tamsayı değerlerine,, ve değerine dönüştürmek için aşırı yüklenmiş bir işleç içerir `Double` `Single` `Char` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-478">For example, the `Decimal` structure includes an overloaded `op_Explicit` operator to convert [Double](xref:System.Double) and [Single](xref:System.Single) values to `Decimal` and to convert `Decimal` values to integral values, `Double`, `Single`, and `Char`.</span></span>

<span data-ttu-id="bf1ca-479">Ancak, tüm diller operatör aşırı yüklemesini veya özel işleçlerin tanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-479">However, not all languages support operator overloading or the definition of custom operators.</span></span> <span data-ttu-id="bf1ca-480">Bu dönüştürme işleçlerini uygulamayı seçerseniz, dönüştürmeyi gerçekleştirmek için alternatif bir yol da sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-480">If you choose to implement these conversion operators, you should also provide an alternate way to perform the conversion.</span></span> <span data-ttu-id="bf1ca-481">`From`Xxx ve `To` XXX yöntemleri sağlamanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-481">We recommend that you provide `From`Xxx and `To`Xxx methods.</span></span>

<span data-ttu-id="bf1ca-482">Aşağıdaki örnek, CLS uyumlu örtük ve açık dönüştürmeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-482">The following example defines CLS-compliant implicit and explicit conversions.</span></span> <span data-ttu-id="bf1ca-483">`UDouble`İmzalı çift duyarlıklı, kayan noktalı bir sayıyı temsil eden bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-483">It creates a `UDouble` class that represents an signed double-precision, floating-point number.</span></span> <span data-ttu-id="bf1ca-484">' Dan `UDouble` `Double` `UDouble` `Single` , `Double` ' a `UDouble` ve ' `Single` `UDouble` a kadar açık dönüşümlere örtülü dönüşümler sağlar.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-484">It provides for implicit conversions from `UDouble` to `Double` and for explicit conversions from `UDouble` to `Single`, `Double` to `UDouble`, and `Single` to `UDouble`.</span></span> <span data-ttu-id="bf1ca-485">Ayrıca `ToDouble` , örtük dönüştürme işlecine alternatif olarak bir yöntemi ve `ToSingle` ,, `FromDouble` ve `FromSingle` yöntemlerini açık dönüştürme işleçleri alternatifleri olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-485">It also defines a `ToDouble` method as an alternative to the implicit conversion operator and the `ToSingle`, `FromDouble`, and `FromSingle` methods as alternatives to the explicit conversion operators.</span></span>

```csharp
using System;

public struct UDouble
{
   private double number;

   public UDouble(double value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      number = value;
   }

   public UDouble(float value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      number = value;
   }

   public static readonly UDouble MinValue = (UDouble) 0.0;
   public static readonly UDouble MaxValue = (UDouble) Double.MaxValue;

   public static explicit operator Double(UDouble value)
   {
      return value.number;
   }

   public static implicit operator Single(UDouble value)
   {
      if (value.number > (double) Single.MaxValue)
         throw new InvalidCastException("A UDouble value is out of range of the Single type.");

      return (float) value.number;
   }

   public static explicit operator UDouble(double value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      return new UDouble(value);
   }

   public static implicit operator UDouble(float value)
   {
      if (value < 0)
         throw new InvalidCastException("A negative value cannot be converted to a UDouble.");

      return new UDouble(value);
   }

   public static Double ToDouble(UDouble value)
   {
      return (Double) value;
   }

   public static float ToSingle(UDouble value)
   {
      return (float) value;
   }

   public static UDouble FromDouble(double value)
   {
      return new UDouble(value);
   }

   public static UDouble FromSingle(float value)
   {
      return new UDouble(value);
   }
}
```

```vb
Public Structure UDouble
   Private number As Double

   Public Sub New(value As Double)
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      number = value
   End Sub

   Public Sub New(value As Single)
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      number = value
   End Sub

   Public Shared ReadOnly MinValue As UDouble = CType(0.0, UDouble)
   Public Shared ReadOnly MaxValue As UDouble = Double.MaxValue

   Public Shared Widening Operator CType(value As UDouble) As Double
      Return value.number
   End Operator

   Public Shared Narrowing Operator CType(value As UDouble) As Single
      If value.number > CDbl(Single.MaxValue) Then
         Throw New InvalidCastException("A UDouble value is out of range of the Single type.")
      End If
      Return CSng(value.number)
   End Operator

   Public Shared Narrowing Operator CType(value As Double) As UDouble
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      Return New UDouble(value)
   End Operator

   Public Shared Narrowing Operator CType(value As Single) As UDouble
      If value < 0 Then
         Throw New InvalidCastException("A negative value cannot be converted to a UDouble.")
      End If
      Return New UDouble(value)
   End Operator

   Public Shared Function ToDouble(value As UDouble) As Double
      Return CType(value, Double)
   End Function

   Public Shared Function ToSingle(value As UDouble) As Single
      Return CType(value, Single)
   End Function

   Public Shared Function FromDouble(value As Double) As UDouble
      Return New UDouble(value)
   End Function

   Public Shared Function FromSingle(value As Single) As UDouble
      Return New UDouble(value)
   End Function
End Structure
```

### <a name="arrays"></a><span data-ttu-id="bf1ca-486">Diziler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-486">Arrays</span></span>

<span data-ttu-id="bf1ca-487">CLS uyumlu diziler aşağıdaki kurallara uyar:</span><span class="sxs-lookup"><span data-stu-id="bf1ca-487">CLS-compliant arrays conform to the following rules:</span></span>

* <span data-ttu-id="bf1ca-488">Bir dizinin tüm boyutlarının alt sınırı sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-488">All dimensions of an array must have a lower bound of zero.</span></span> <span data-ttu-id="bf1ca-489">Aşağıdaki örnek, bir alt sınırı olan CLS uyumlu olmayan bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-489">The following example creates a non-CLS-compliant array with a lower bound of one.</span></span> <span data-ttu-id="bf1ca-490">[CLSCompliantAttribute](xref:System.CLSCompliantAttribute) özniteliğinin varlığına rağmen derleyicinin yöntemin DÖNDÜRDÜĞÜ dizinin CLS uyumlu olmadığını algılamadığına unutmayın `Numbers.GetTenPrimes` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-490">Note that, despite the presence of the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute, the compiler does not detect that the array returned by the `Numbers.GetTenPrimes` method is not CLS-compliant.</span></span>

  ```csharp
  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static Array GetTenPrimes()
    {
        Array arr = Array.CreateInstance(typeof(Int32), new int[] {10}, new int[] {1});
        arr.SetValue(1, 1);
        arr.SetValue(2, 2);
        arr.SetValue(3, 3);
        arr.SetValue(5, 4);
        arr.SetValue(7, 5);
        arr.SetValue(11, 6);
        arr.SetValue(13, 7);
        arr.SetValue(17, 8);
        arr.SetValue(19, 9);
        arr.SetValue(23, 10);

        return arr;
    }
  }
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Class Numbers
     Public Shared Function GetTenPrimes() As Array
        Dim arr As Array = Array.CreateInstance(GetType(Int32), {10}, {1})
        arr.SetValue(1, 1)
        arr.SetValue(2, 2)
        arr.SetValue(3, 3)
        arr.SetValue(5, 4)
        arr.SetValue(7, 5)
        arr.SetValue(11, 6)
        arr.SetValue(13, 7)
        arr.SetValue(17, 8)
        arr.SetValue(19, 9)
        arr.SetValue(23, 10)
        Return arr
     End Function
  End Class
  ```

* <span data-ttu-id="bf1ca-491">Tüm dizi öğeleri CLS uyumlu türlerden oluşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-491">All array elements must consist of CLS-compliant types.</span></span> <span data-ttu-id="bf1ca-492">Aşağıdaki örnek, CLS uyumlu olmayan diziler döndüren iki yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-492">The following example defines two methods that return non-CLS-compliant arrays.</span></span> <span data-ttu-id="bf1ca-493">İlki [UInt32](xref:System.UInt32) değerlerinin bir dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-493">The first returns an array of [UInt32](xref:System.UInt32) values.</span></span> <span data-ttu-id="bf1ca-494">İkincisi, [Int32](xref:System.Int32) ve değerleri Içeren bir [nesne](xref:System.Object) dizisi döndürür `UInt32` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-494">The second returns an [Object](xref:System.Object) array that includes [Int32](xref:System.Int32) and `UInt32` values.</span></span> <span data-ttu-id="bf1ca-495">Derleyici, türü nedeniyle ilk diziyi uyumsuz olarak tanımlasa da `UInt32` , ikinci DIZININ CLS uyumlu olmayan öğeleri içerdiğini tanıyamaz.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-495">Although the compiler identifies the first array as non-compliant because of its `UInt32` type, it fails to recognize that the second array includes non-CLS-compliant elements.</span></span>

  ```csharp
  using System;

  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static UInt32[] GetTenPrimes()
    {
        uint[] arr = { 1u, 2u, 3u, 5u, 7u, 11u, 13u, 17u, 19u };
        return arr;
    }

    public static Object[] GetFivePrimes()
    {
        Object[] arr = { 1, 2, 3, 5u, 7u };
        return arr;
    }
  }
  // Compilation produces a compiler warning like the following:
  //    Array2.cs(8,27): warning CS3002: Return type of 'Numbers.GetTenPrimes()' is not
  //            CLS-compliant
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Class Numbers
     Public Shared Function GetTenPrimes() As UInt32()
        Return { 1ui, 2ui, 3ui, 5ui, 7ui, 11ui, 13ui, 17ui, 19ui }
     End Function
     Public Shared Function GetFivePrimes() As Object()
        Dim arr() As Object = { 1, 2, 3, 5ui, 7ui }
        Return arr
     End Function
  End Class
  ' Compilation produces a compiler warning like the following:
  '    warning BC40027: Return type of function 'GetTenPrimes' is not CLS-compliant.
  ```

* <span data-ttu-id="bf1ca-496">Dizi parametrelerine sahip yöntemler için aşırı yükleme çözümlemesi, diziler oldukları olguyu ve öğe türlerini temel alır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-496">Overload resolution for methods that have array parameters is based on the fact that they are arrays and on their element type.</span></span> <span data-ttu-id="bf1ca-497">Bu nedenle, aşırı yüklenmiş bir yöntemin aşağıdaki tanımı `GetSquares` CLS uyumludur.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-497">For this reason, the following definition of an overloaded `GetSquares` method is CLS-compliant.</span></span>

  ```csharp
  using System;
  using System.Numerics;

  [assembly: CLSCompliant(true)]

  public class Numbers
  {
    public static byte[] GetSquares(byte[] numbers)
    {
        byte[] numbersOut = new byte[numbers.Length];
        for (int ctr = 0; ctr < numbers.Length; ctr++) {
            int square = ((int) numbers[ctr]) * ((int) numbers[ctr]);
            if (square <= Byte.MaxValue)
                numbersOut[ctr] = (byte) square;
            // If there's an overflow, assign MaxValue to the corresponding
            // element.
            else
                numbersOut[ctr] = Byte.MaxValue;

        }
        return numbersOut;
    }

    public static BigInteger[] GetSquares(BigInteger[] numbers)
  {
        BigInteger[] numbersOut = new BigInteger[numbers.Length];
        for (int ctr = 0; ctr < numbers.Length; ctr++)
            numbersOut[ctr] = numbers[ctr] * numbers[ctr];

       return numbersOut;
    }
  }
  ```

  ```vb
  Imports System.Numerics

  <Assembly: CLSCompliant(True)>

  Public Module Numbers
     Public Function GetSquares(numbers As Byte()) As Byte()
        Dim numbersOut(numbers.Length - 1) As Byte
        For ctr As Integer = 0 To numbers.Length - 1
           Dim square As Integer = (CInt(numbers(ctr)) * CInt(numbers(ctr)))
           If square <= Byte.MaxValue Then
              numbersOut(ctr) = CByte(square)
           ' If there's an overflow, assign MaxValue to the corresponding
           ' element.
           Else
              numbersOut(ctr) = Byte.MaxValue
           End If
        Next
        Return numbersOut
     End Function

     Public Function GetSquares(numbers As BigInteger()) As BigInteger()
         Dim numbersOut(numbers.Length - 1) As BigInteger
         For ctr As Integer = 0 To numbers.Length - 1
            numbersOut(ctr) = numbers(ctr) * numbers(ctr)
         Next
         Return numbersOut
     End Function
  End Module
  ```

### <a name="interfaces"></a><span data-ttu-id="bf1ca-498">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-498">Interfaces</span></span>

<span data-ttu-id="bf1ca-499">CLS uyumlu arabirimler özellikleri, olayları ve sanal yöntemleri (uygulama içermeyen yöntemler) tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-499">CLS-compliant interfaces can define properties, events, and virtual methods (methods with no implementation).</span></span> <span data-ttu-id="bf1ca-500">CLS uyumlu bir arabirim aşağıdakilerden birini içeremez:</span><span class="sxs-lookup"><span data-stu-id="bf1ca-500">A CLS-compliant interface cannot have any of the following:</span></span>

* <span data-ttu-id="bf1ca-501">Statik yöntemler veya statik alanlar.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-501">Static methods or static fields.</span></span> <span data-ttu-id="bf1ca-502">Bir arabirimde statik üye tanımlarsanız C# derleyicisi derleyici hataları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-502">The C# compiler generates compiler errors if you define a static member in an interface.</span></span>

* <span data-ttu-id="bf1ca-503">Alanını.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-503">Fields.</span></span> <span data-ttu-id="bf1ca-504">C# a derleyici, bir arabirimde alan tanımlarsanız derleyici hataları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-504">The C# a compiler generates compiler errors if you define a field in an interface.</span></span>

* <span data-ttu-id="bf1ca-505">CLS uyumlu olmayan yöntemler.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-505">Methods that are not CLS-compliant.</span></span> <span data-ttu-id="bf1ca-506">Örneğin, aşağıdaki arabirim tanımı, `INumber.GetUnsigned` CLS uyumlu olmayan olarak işaretlenen bir yöntemini içerir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-506">For example, the following interface definition includes a method, `INumber.GetUnsigned`, that is marked as non-CLS-compliant.</span></span> <span data-ttu-id="bf1ca-507">Bu örnek bir derleyici uyarısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-507">This example generates a compiler warning.</span></span>

  ```csharp
  using System;

  [assembly:CLSCompliant(true)]

  public interface INumber
  {
      int Length();
      [CLSCompliant(false)] ulong GetUnsigned();
  }
  // Attempting to compile the example displays output like the following:
  //    Interface2.cs(8,32): warning CS3010: 'INumber.GetUnsigned()': CLS-compliant interfaces
  //            must have only CLS-compliant members
  ```

  ```vb
  <Assembly: CLSCompliant(True)>

  Public Interface INumber
    Function Length As Integer
      <CLSCompliant(False)> Function GetUnsigned As ULong
    End Interface
    ' Attempting to compile the example displays output like the following:
    '    Interface2.vb(9) : warning BC40033: Non CLS-compliant 'function' is not allowed in a
    '    CLS-compliant interface.
    '
    '       <CLSCompliant(False)> Function GetUnsigned As ULong
    '                                      ~~~~~~~~~~~
  ```

  <span data-ttu-id="bf1ca-508">Bu kural nedeniyle, CLS uyumlu olmayan üyeleri uygulamak için CLS uyumlu türler gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-508">Because of this rule, CLS-compliant types are not required to implement non-CLS-compliant members.</span></span> <span data-ttu-id="bf1ca-509">CLS uyumlu bir çerçeve CLS uyumlu olmayan bir arabirim uygulayan bir sınıfı kullanıma sunuyorsa, CLS uyumlu olmayan tüm üyelerin somut uygulamalarını da sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-509">If a CLS-compliant framework does expose a class that implements a non-CLS compliant interface, it should also provide concrete implementations of all non-CLS-compliant members.</span></span>

<span data-ttu-id="bf1ca-510">CLS uyumlu dil derleyicileri Ayrıca, bir sınıfın birden fazla arabirimde aynı ada ve imzaya sahip ayrı üye uygulamaları sağlamasına izin vermelidir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-510">CLS-compliant language compilers must also allow a class to provide separate implementations of members that have the same name and signature in multiple interfaces.</span></span> <span data-ttu-id="bf1ca-511">C#, benzer adlandırılmış yöntemlerin farklı uygulamalarını sağlamak için açık arabirim uygulamalarını destekler.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-511">C# supports explicit interface implementations to provide different implementations of identically named methods.</span></span> <span data-ttu-id="bf1ca-512">Aşağıdaki örnek, `Temperature` `ICelsius` ve `IFahrenheit` arabirimlerini açık arabirim uygulamaları olarak uygulayan bir sınıf tanımlayarak bu senaryoyu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-512">The following example illustrates this scenario by defining a `Temperature` class that implements the `ICelsius` and `IFahrenheit` interfaces as explicit interface implementations.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public interface IFahrenheit
{
   decimal GetTemperature();
}

public interface ICelsius
{
   decimal GetTemperature();
}

public class Temperature : ICelsius, IFahrenheit
{
   private decimal _value;

   public Temperature(decimal value)
   {
      // We assume that this is the Celsius value.
      _value = value;
   }

   decimal IFahrenheit.GetTemperature()
   {
      return _value * 9 / 5 + 32;
   }

   decimal ICelsius.GetTemperature()
   {
      return _value;
   }
}
public class Example
{
   public static void Main()
   {
      Temperature temp = new Temperature(100.0m);
      ICelsius cTemp = temp;
      IFahrenheit fTemp = temp;
      Console.WriteLine("Temperature in Celsius: {0} degrees",
                        cTemp.GetTemperature());
      Console.WriteLine("Temperature in Fahrenheit: {0} degrees",
                        fTemp.GetTemperature());
   }
}
// The example displays the following output:
//       Temperature in Celsius: 100.0 degrees
//       Temperature in Fahrenheit: 212.0 degrees
```

```vb
Assembly: CLSCompliant(True)>

Public Interface IFahrenheit
   Function GetTemperature() As Decimal
End Interface

Public Interface ICelsius
   Function GetTemperature() As Decimal
End Interface

Public Class Temperature : Implements ICelsius, IFahrenheit
   Private _value As Decimal

   Public Sub New(value As Decimal)
      ' We assume that this is the Celsius value.
      _value = value
   End Sub

   Public Function GetFahrenheit() As Decimal _
          Implements IFahrenheit.GetTemperature
      Return _value * 9 / 5 + 32
   End Function

   Public Function GetCelsius() As Decimal _
          Implements ICelsius.GetTemperature
      Return _value
   End Function
End Class

Module Example
   Public Sub Main()
      Dim temp As New Temperature(100.0d)
      Console.WriteLine("Temperature in Celsius: {0} degrees",
                        temp.GetCelsius())
      Console.WriteLine("Temperature in Fahrenheit: {0} degrees",
                        temp.GetFahrenheit())
   End Sub
End Module
' The example displays the following output:
'       Temperature in Celsius: 100.0 degrees
'       Temperature in Fahrenheit: 212.0 degrees
```

### <a name="enumerations"></a><span data-ttu-id="bf1ca-513">Numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="bf1ca-513">Enumerations</span></span>

<span data-ttu-id="bf1ca-514">CLS uyumlu numaralandırmalar aşağıdaki kurallara uymalıdır:</span><span class="sxs-lookup"><span data-stu-id="bf1ca-514">CLS-compliant enumerations must follow these rules:</span></span>

* <span data-ttu-id="bf1ca-515">Sabit listesinin temel alınan türü, bir iç CLS uyumlu tamsayı ([byte](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32)veya [Int64](xref:System.Int64)) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-515">The underlying type of the enumeration must be an intrinsic CLS-compliant integer ([Byte](xref:System.Byte), [Int16](xref:System.Int16), [Int32](xref:System.Int32), or [Int64](xref:System.Int64)).</span></span> <span data-ttu-id="bf1ca-516">Örneğin, aşağıdaki kod, temel türü [UInt32](xref:System.UInt32) olan ve bir derleyici uyarısı oluşturan bir sabit listesi tanımlamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-516">For example, the following code tries to define an enumeration whose underlying type is [UInt32](xref:System.UInt32) and generates a compiler warning.</span></span>

    ```csharp
    using System;

    [assembly: CLSCompliant(true)]

    public enum Size : uint {
        Unspecified = 0,
        XSmall = 1,
        Small = 2,
        Medium = 3,
        Large = 4,
        XLarge = 5
    };

    public class Clothing
    {
        public string Name;
        public string Type;
        public string Size;
    }
    // The attempt to compile the example displays a compiler warning like the following:
    //    Enum3.cs(6,13): warning CS3009: 'Size': base type 'uint' is not CLS-compliant
    ```

    ```vb
    <Assembly: CLSCompliant(True)>

    Public Enum Size As UInt32
       Unspecified = 0
       XSmall = 1
       Small = 2
       Medium = 3
       Large = 4
       XLarge = 5
    End Enum

    Public Class Clothing
       Public Name As String
       Public Type As String
       Public Size As Size
    End Class
    ' The attempt to compile the example displays a compiler warning like the following:
    '    Enum3.vb(6) : warning BC40032: Underlying type 'UInt32' of Enum is not CLS-compliant.
    '
    '    Public Enum Size As UInt32
    '                ~~~~
    ```

* <span data-ttu-id="bf1ca-517">Sabit listesi türü, özniteliğiyle işaretlenmiş adlı tek bir örnek alanına sahip olmalıdır `Value__` `FieldAttributes.RTSpecialName` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-517">An enumeration type must have a single instance field named `Value__` that is marked with the `FieldAttributes.RTSpecialName` attribute.</span></span> <span data-ttu-id="bf1ca-518">Bu, alan değerine örtülü olarak başvuru yapmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-518">This enables you to reference the field value implicitly.</span></span>

* <span data-ttu-id="bf1ca-519">Sabit listesi, türleri numaralandırmanın türüyle eşleşen değişmez static alanları içerir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-519">An enumeration includes literal static fields whose types match the type of the enumeration itself.</span></span> <span data-ttu-id="bf1ca-520">Örneğin, `State` ve değerlerini içeren bir sabit listesi tanımlarsanız `State.On` `State.Off` `State.On` ve `State.Off` türü olan değişmez değer statik alanlardır `State` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-520">For example, if you define a `State` enumeration with values of `State.On` and `State.Off`, `State.On` and `State.Off` are both literal static fields whose type is `State`.</span></span>

* <span data-ttu-id="bf1ca-521">İki tür numaralandırma vardır:</span><span class="sxs-lookup"><span data-stu-id="bf1ca-521">There are two kinds of enumerations:</span></span>

  * <span data-ttu-id="bf1ca-522">Birbirini dışlayan, adlandırılmış tamsayı değerleri kümesini temsil eden bir sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-522">An enumeration that represents a set of mutually exclusive, named integer values.</span></span> <span data-ttu-id="bf1ca-523">Bu tür bir numaralandırma [System. FlagsAttribute](xref:System.FlagsAttribute) özel özniteliğinin yokluğuna göre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-523">This type of enumeration is indicated by the absence of the [System.FlagsAttribute](xref:System.FlagsAttribute) custom attribute.</span></span>

  * <span data-ttu-id="bf1ca-524">Adlandırılmamış bir değer oluşturmak için birleştirebileceğiniz bir bit bayrakları kümesini temsil eden bir sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-524">An enumeration that represents a set of bit flags that can combine to generate an unnamed value.</span></span> <span data-ttu-id="bf1ca-525">Bu tür bir numaralandırma [System. FlagsAttribute](xref:System.FlagsAttribute) özel özniteliğinin varlığına göre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-525">This type of enumeration is indicated by the presence of the [System.FlagsAttribute](xref:System.FlagsAttribute) custom attribute.</span></span>

<span data-ttu-id="bf1ca-526">Daha fazla bilgi için bkz. [enum](xref:System.Enum) yapısına yönelik belgeler.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-526">For more information, see the documentation for the [Enum](xref:System.Enum) structure.</span></span>

* <span data-ttu-id="bf1ca-527">Bir numaralandırmanın değeri, belirtilen değerlerinin aralığıyla sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-527">The value of an enumeration is not limited to the range of its specified values.</span></span> <span data-ttu-id="bf1ca-528">Diğer bir deyişle, bir Numaralandırmadaki değer aralığı, temel alınan değerinin aralığıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-528">In other words, the range of values in an enumeration is the range of its underlying value.</span></span> <span data-ttu-id="bf1ca-529">`Enum.IsDefined`Yöntemini, belirtilen değerin bir numaralandırma üyesi olup olmadığını anlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-529">You can use the `Enum.IsDefined` method to determine whether a specified value is a member of an enumeration.</span></span>

### <a name="type-members-in-general"></a><span data-ttu-id="bf1ca-530">Genel olarak tür üyeleri</span><span class="sxs-lookup"><span data-stu-id="bf1ca-530">Type members in general</span></span>

<span data-ttu-id="bf1ca-531">Ortak dil belirtimi, tüm alanlara ve yöntemlere belirli bir sınıfın üyeleri olarak erişilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-531">The Common Language Specification requires all fields and methods to be accessed as members of a particular class.</span></span> <span data-ttu-id="bf1ca-532">Bu nedenle, genel statik alanlar ve Yöntemler (yani, statik alanlar veya bir türden ayrı tanımlanmış yöntemler) CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-532">Therefore, global static fields and methods (that is, static fields or methods that are defined apart from a type) are not CLS-compliant.</span></span> <span data-ttu-id="bf1ca-533">Kaynak kodunuza genel bir alan veya yöntem eklemeyi denerseniz, C# derleyicisi bir derleyici hatası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-533">If you try to include a global field or method in your source code, the C# compiler generates a compiler error.</span></span>

<span data-ttu-id="bf1ca-534">Ortak dil belirtimi yalnızca standart yönetilen çağırma kuralını destekler.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-534">The Common Language Specification supports only the standard managed calling convention.</span></span> <span data-ttu-id="bf1ca-535">Anahtar sözcükle işaretlenmiş bağımsız değişken listeleriyle yönetilmeyen çağırma kurallarını ve yöntemlerini desteklemez `varargs` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-535">It doesn't support unmanaged calling conventions and methods with variable argument lists marked with the `varargs` keyword.</span></span> <span data-ttu-id="bf1ca-536">Standart yönetilen çağırma kuralıyla uyumlu olan değişken bağımsız değişken listeleri için, [ParamArrayAttribute](xref:System.ParamArrayAttribute) `params` C# ' deki anahtar sözcüğü ve `ParamArray` Visual Basic anahtar sözcüğü gibi, ParamArrayAttribute özniteliğini veya bağımsız dilin uygulamasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-536">For variable argument lists that are compatible with the standard managed calling convention, use the [ParamArrayAttribute](xref:System.ParamArrayAttribute) attribute or the individual language's implementation, such as the `params` keyword in C# and the `ParamArray` keyword in Visual Basic.</span></span>

### <a name="member-accessibility"></a><span data-ttu-id="bf1ca-537">Üye erişilebilirliği</span><span class="sxs-lookup"><span data-stu-id="bf1ca-537">Member accessibility</span></span>

<span data-ttu-id="bf1ca-538">Devralınan bir üyenin geçersiz kılınması, o üyenin erişilebilirliğini değiştiremez.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-538">Overriding an inherited member cannot change the accessibility of that member.</span></span> <span data-ttu-id="bf1ca-539">Örneğin, bir temel sınıftaki ortak bir yöntem türetilmiş bir sınıftaki özel bir yöntem tarafından geçersiz kılınamaz.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-539">For example, a public method in a base class cannot be overridden by a private method in a derived class.</span></span> <span data-ttu-id="bf1ca-540">Bir özel durum vardır: bir `protected internal` derlemede (C# ' ta) veya `Protected Friend` (Visual Basic), farklı bir derlemedeki bir tür tarafından geçersiz kılınan bir derlemede üye.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-540">There is one exception: a `protected internal` (in C#) or `Protected Friend` (in Visual Basic) member in one assembly that is overridden by a type in a different assembly.</span></span>  <span data-ttu-id="bf1ca-541">Bu durumda, geçersiz kılma erişilebilirliği olur `Protected` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-541">In that case, the accessibility of the override is `Protected`.</span></span>

<span data-ttu-id="bf1ca-542">Aşağıdaki örnek, [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) özniteliği olarak ayarlandığında oluşturulan hatayı gösterir `true` ve `Person` ' dan türetilmiş bir sınıf olan, `Animal` `Species` özelliğin erişilebilirliğini public iken Private olarak değiştirmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-542">The following example illustrates the error that is generated when the [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute is set to `true`, and `Person`, which is a class derived from `Animal`, tries to change the accessibility of the `Species` property from public to private.</span></span> <span data-ttu-id="bf1ca-543">Bunun erişilebilirliği ortak olarak değiştirilirse örnek başarıyla derlenir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-543">The example compiles successfully if its accessibility is changed to public.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class Animal
{
   private string _species;

   public Animal(string species)
   {
      _species = species;
   }

   public virtual string Species
   {
      get { return _species; }
   }

   public override string ToString()
   {
      return _species;
   }
}

public class Human : Animal
{
   private string _name;

   public Human(string name) : base("Homo Sapiens")
   {
      _name = name;
   }

   public string Name
   {
      get { return _name; }
   }

   private override string Species
   {
      get { return base.Species; }
   }

   public override string ToString()
   {
      return _name;
   }
}

public class Example
{
   public static void Main()
   {
      Human p = new Human("John");
      Console.WriteLine(p.Species);
      Console.WriteLine(p.ToString());
   }
}
// The example displays the following output:
//    error CS0621: 'Human.Species': virtual or abstract members cannot be private
```

```vb
<Assembly: CLSCompliant(True)>

Public Class Animal
   Private _species As String

   Public Sub New(species As String)
      _species = species
   End Sub

   Public Overridable ReadOnly Property Species As String
      Get
         Return _species
      End Get
   End Property

   Public Overrides Function ToString() As String
      Return _species
   End Function
End Class

Public Class Human : Inherits Animal
   Private _name As String

   Public Sub New(name As String)
      MyBase.New("Homo Sapiens")
      _name = name
   End Sub

   Public ReadOnly Property Name As String
      Get
         Return _name
      End Get
   End Property

   Private Overrides ReadOnly Property Species As String
      Get
         Return MyBase.Species
      End Get
   End Property

   Public Overrides Function ToString() As String
      Return _name
   End Function
End Class

Public Module Example
   Public Sub Main()
      Dim p As New Human("John")
      Console.WriteLine(p.Species)
      Console.WriteLine(p.ToString())
   End Sub
End Module
' The example displays the following output:
'     'Private Overrides ReadOnly Property Species As String' cannot override
'     'Public Overridable ReadOnly Property Species As String' because
'      they have different access levels.
'
'         Private Overrides ReadOnly Property Species As String
```

<span data-ttu-id="bf1ca-544">Üyenin İmzasındaki türlere, bu üyeye her erişilebilir her seferinde erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-544">Types in the signature of a member must be accessible whenever that member is accessible.</span></span> <span data-ttu-id="bf1ca-545">Örneğin, bu, ortak bir üyenin türü Private, protected veya internal olan bir parametre içeremeyeceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-545">For example, this means that a public member cannot include a parameter whose type is private, protected, or internal.</span></span> <span data-ttu-id="bf1ca-546">Aşağıdaki örnek, bir `StringWrapper` sınıf Oluşturucusu bir `StringOperationType` dize değerinin nasıl sarmalanması gerektiğini belirleyen bir iç sabit listesi değeri ortaya çıkardığı zaman sonuç veren derleyici hatasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-546">The following example illustrates the compiler error that results when a `StringWrapper` class constructor exposes an internal `StringOperationType` enumeration value that determines how a string value should be wrapped.</span></span>

```csharp
using System;
using System.Text;

public class StringWrapper
{
   string internalString;
   StringBuilder internalSB = null;
   bool useSB = false;

   public StringWrapper(StringOperationType type)
   {
      if (type == StringOperationType.Normal) {
         useSB = false;
      }
      else {
         useSB = true;
         internalSB = new StringBuilder();
      }
   }

   // The remaining source code...
}

internal enum StringOperationType { Normal, Dynamic }
// The attempt to compile the example displays the following output:
//    error CS0051: Inconsistent accessibility: parameter type
//            'StringOperationType' is less accessible than method
//            'StringWrapper.StringWrapper(StringOperationType)'
```

```vb
Imports System.Text

<Assembly:CLSCompliant(True)>

Public Class StringWrapper

   Dim internalString As String
   Dim internalSB As StringBuilder = Nothing
   Dim useSB As Boolean = False

   Public Sub New(type As StringOperationType)
      If type = StringOperationType.Normal Then
         useSB = False
      Else
         internalSB = New StringBuilder()
         useSB = True
      End If
   End Sub

   ' The remaining source code...
End Class

Friend Enum StringOperationType As Integer
   Normal = 0
   Dynamic = 1
End Enum
' The attempt to compile the example displays the following output:
'    error BC30909: 'type' cannot expose type 'StringOperationType'
'     outside the project through class 'StringWrapper'.
'
'       Public Sub New(type As StringOperationType)
'                              ~~~~~~~~~~~~~~~~~~~
```

### <a name="generic-types-and-members"></a><span data-ttu-id="bf1ca-547">Genel türler ve Üyeler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-547">Generic types and members</span></span>

<span data-ttu-id="bf1ca-548">İç içe türler her zaman kapsayan türü olarak en az sayıda genel parametre içermelidir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-548">Nested types always have at least as many generic parameters as their enclosing type.</span></span> <span data-ttu-id="bf1ca-549">Bu, kapsayan türdeki genel parametrelere konuma göre karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-549">These correspond by position to the generic parameters in the enclosing type.</span></span> <span data-ttu-id="bf1ca-550">Genel tür de yeni genel parametreler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-550">The generic type can also include new generic parameters.</span></span>

<span data-ttu-id="bf1ca-551">Kapsayan bir türün genel tür parametreleri ve iç içe geçmiş türleri arasındaki ilişki, tek dillerin sözdizimi tarafından gizlenebilir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-551">The relationship between the generic type parameters of a containing type and its nested types may be hidden by the syntax of individual languages.</span></span> <span data-ttu-id="bf1ca-552">Aşağıdaki örnekte, genel bir tür `Outer<T>` iki iç içe sınıf içerir `Inner1A` ve `Inner1B<U>` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-552">In the following example, a generic type `Outer<T>` contains two nested classes, `Inner1A` and `Inner1B<U>`.</span></span> <span data-ttu-id="bf1ca-553">`ToString`Her sınıfın devraldığı yöntemine yapılan çağrılar, `Object.ToString` her iç içe yerleştirilmiş sınıfın kapsayan sınıfının tür parametrelerini içerdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-553">The calls to the `ToString` method, which each class inherits from `Object.ToString`, show that each nested class includes the type parameters of its containing class.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Outer<T>
{
   T value;

   public Outer(T value)
   {
      this.value = value;
   }

   public class Inner1A : Outer<T>
   {
      public Inner1A(T value) : base(value)
      {  }
   }

   public class Inner1B<U> : Outer<T>
   {
      U value2;

      public Inner1B(T value1, U value2) : base(value1)
      {
         this.value2 = value2;
      }
   }
}

public class Example
{
   public static void Main()
   {
      var inst1 = new Outer<String>("This");
      Console.WriteLine(inst1);

      var inst2 = new Outer<String>.Inner1A("Another");
      Console.WriteLine(inst2);

      var inst3 = new Outer<String>.Inner1B<int>("That", 2);
      Console.WriteLine(inst3);
   }
}
// The example displays the following output:
//       Outer`1[System.String]
//       Outer`1+Inner1A[System.String]
//       Outer`1+Inner1B`1[System.String,System.Int32]
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Outer(Of T)
   Dim value As T

   Public Sub New(value As T)
      Me.value = value
   End Sub

   Public Class Inner1A : Inherits Outer(Of T)
      Public Sub New(value As T)
         MyBase.New(value)
      End Sub
   End Class

   Public Class Inner1B(Of U) : Inherits Outer(Of T)
      Dim value2 As U

      Public Sub New(value1 As T, value2 As U)
         MyBase.New(value1)
         Me.value2 = value2
      End Sub
   End Class
End Class

Public Module Example
   Public Sub Main()
      Dim inst1 As New Outer(Of String)("This")
      Console.WriteLine(inst1)

      Dim inst2 As New Outer(Of String).Inner1A("Another")
      Console.WriteLine(inst2)

      Dim inst3 As New Outer(Of String).Inner1B(Of Integer)("That", 2)
      Console.WriteLine(inst3)
   End Sub
End Module
' The example displays the following output:
'       Outer`1[System.String]
'       Outer`1+Inner1A[System.String]
'       Outer`1+Inner1B`1[System.String,System.Int32]
```

<span data-ttu-id="bf1ca-554">Genel tür adları, '*n*' de, *adın* *tür adı olduğu*, *\`* bir karakter sabit değeri olduğu ve *n* tür üzerinde belirtilen parametre sayısı veya iç içe genel türler için yeni tanıtılan tür parametrelerinin sayısı olarak kodlanır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-554">Generic type names are encoded in the form *name*'*n*, where *name* is the type name, *\`* is a character literal, and *n* is the number of parameters declared on the type, or, for nested generic types, the number of newly introduced type parameters.</span></span> <span data-ttu-id="bf1ca-555">Genel tür adlarının bu kodlaması, bir kitaplıktaki CLS uyumlu Genel türlere erişmek için yansıma kullanan geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-555">This encoding of generic type names is primarily of interest to developers who use reflection to access CLS-complaint generic types in a library.</span></span>

<span data-ttu-id="bf1ca-556">Kısıtlamalar genel bir türe uygulanırsa, kısıtlama olarak kullanılan her türlü tür de CLS uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-556">If constraints are applied to a generic type, any types used as constraints must also be CLS-compliant.</span></span> <span data-ttu-id="bf1ca-557">Aşağıdaki örnek, `BaseClass` CLS uyumlu olmayan adlı bir sınıfı ve tür parametresi türünden türetmelidir adlı bir genel sınıfı tanımlar `BaseCollection` `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-557">The following example defines a class named `BaseClass` that is not CLS-compliant and a generic class named `BaseCollection` whose type parameter must derive from `BaseClass`.</span></span> <span data-ttu-id="bf1ca-558">Ancak, `BaseClass` CLS uyumlu olmadığından, derleyici bir uyarı yayar.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-558">But because `BaseClass` is not CLS-compliant, the compiler emits a warning.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

[CLSCompliant(false)] public class BaseClass
{}

public class BaseCollection<T> where T : BaseClass
{}
// Attempting to compile the example displays the following output:
//    warning CS3024: Constraint type 'BaseClass' is not CLS-compliant
```

```vb
Assembly: CLSCompliant(True)>

<CLSCompliant(False)> Public Class BaseClass
End Class

Public Class BaseCollection(Of T As BaseClass)
End Class
' Attempting to compile the example displays the following output:
'    warning BC40040: Generic parameter constraint type 'BaseClass' is not
'    CLS-compliant.
'
'    Public Class BaseCollection(Of T As BaseClass)
'                                        ~~~~~~~~~
```

<span data-ttu-id="bf1ca-559">Genel bir tür genel bir temel türden türetildiyse, temel türdeki kısıtlamaların da karşılanmasını garanti edebilmesi için herhangi bir kısıtlamayı yeniden bildirmelidir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-559">If a generic type is derived from a generic base type, it must redeclare any constraints so that it can guarantee that constraints on the base type are also satisfied.</span></span> <span data-ttu-id="bf1ca-560">Aşağıdaki örnek, herhangi bir `Number<T>` sayısal türü temsil eden bir tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-560">The following example defines a `Number<T>` that can represent any numeric type.</span></span> <span data-ttu-id="bf1ca-561">Ayrıca `FloatingPoint<T>` , kayan nokta değerini temsil eden bir sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-561">It also defines a `FloatingPoint<T>` class that represents a floating point value.</span></span> <span data-ttu-id="bf1ca-562">Ancak, üzerinde kısıtlama uygulanmadığından kaynak kodu derlenemiyor `Number<T>` (Bu T bir değer türü olmalıdır) `FloatingPoint<T>` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-562">However, the source code fails to compile, because it does not apply the constraint on `Number<T>` (that T must be a value type) to `FloatingPoint<T>`.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Number<T> where T : struct
{
   // use Double as the underlying type, since its range is a superset of
   // the ranges of all numeric types except BigInteger.
   protected double number;

   public Number(T value)
   {
      try {
         this.number = Convert.ToDouble(value);
      }
      catch (OverflowException e) {
         throw new ArgumentException("value is too large.", e);
      }
      catch (InvalidCastException e) {
         throw new ArgumentException("The value parameter is not numeric.", e);
      }
   }

   public T Add(T value)
   {
      return (T) Convert.ChangeType(number + Convert.ToDouble(value), typeof(T));
   }

   public T Subtract(T value)
   {
      return (T) Convert.ChangeType(number - Convert.ToDouble(value), typeof(T));
   }
}

public class FloatingPoint<T> : Number<T>
{
   public FloatingPoint(T number) : base(number)
   {
      if (typeof(float) == number.GetType() ||
          typeof(double) == number.GetType() ||
          typeof(decimal) == number.GetType())
         this.number = Convert.ToDouble(number);
      else
         throw new ArgumentException("The number parameter is not a floating-point number.");
   }
}
// The attempt to compile the example displays the following output:
//       error CS0453: The type 'T' must be a non-nullable value type in
//               order to use it as parameter 'T' in the generic type or method 'Number<T>'
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Number(Of T As Structure)
   ' Use Double as the underlying type, since its range is a superset of
   ' the ranges of all numeric types except BigInteger.
   Protected number As Double

   Public Sub New(value As T)
      Try
         Me.number = Convert.ToDouble(value)
      Catch e As OverflowException
         Throw New ArgumentException("value is too large.", e)
      Catch e As InvalidCastException
         Throw New ArgumentException("The value parameter is not numeric.", e)
      End Try
   End Sub

   Public Function Add(value As T) As T
      Return CType(Convert.ChangeType(number + Convert.ToDouble(value), GetType(T)), T)
   End Function

   Public Function Subtract(value As T) As T
      Return CType(Convert.ChangeType(number - Convert.ToDouble(value), GetType(T)), T)
   End Function
End Class

Public Class FloatingPoint(Of T) : Inherits Number(Of T)
   Public Sub New(number As T)
      MyBase.New(number)
      If TypeOf number Is Single Or
               TypeOf number Is Double Or
               TypeOf number Is Decimal Then
         Me.number = Convert.ToDouble(number)
      Else
         throw new ArgumentException("The number parameter is not a floating-point number.")
      End If
   End Sub
End Class
' The attempt to compile the example displays the following output:
'    error BC32105: Type argument 'T' does not satisfy the 'Structure'
'    constraint for type parameter 'T'.
'
'    Public Class FloatingPoint(Of T) : Inherits Number(Of T)
'                                                          ~
```

<span data-ttu-id="bf1ca-563">Kısıtlama sınıfa eklenirse, örnek başarıyla derlenir `FloatingPoint<T>` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-563">The example compiles successfully if the constraint is added to the `FloatingPoint<T>` class.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public class Number<T> where T : struct
{
   // use Double as the underlying type, since its range is a superset of
   // the ranges of all numeric types except BigInteger.
   protected double number;

   public Number(T value)
   {
      try {
         this.number = Convert.ToDouble(value);
      }
      catch (OverflowException e) {
         throw new ArgumentException("value is too large.", e);
      }
      catch (InvalidCastException e) {
         throw new ArgumentException("The value parameter is not numeric.", e);
      }
   }

   public T Add(T value)
   {
      return (T) Convert.ChangeType(number + Convert.ToDouble(value), typeof(T));
   }

   public T Subtract(T value)
   {
      return (T) Convert.ChangeType(number - Convert.ToDouble(value), typeof(T));
   }
}

public class FloatingPoint<T> : Number<T> where T : struct
{
   public FloatingPoint(T number) : base(number)
   {
      if (typeof(float) == number.GetType() ||
          typeof(double) == number.GetType() ||
          typeof(decimal) == number.GetType())
         this.number = Convert.ToDouble(number);
      else
         throw new ArgumentException("The number parameter is not a floating-point number.");
   }
}
```

```vb
<Assembly:CLSCompliant(True)>

Public Class Number(Of T As Structure)
   ' Use Double as the underlying type, since its range is a superset of
   ' the ranges of all numeric types except BigInteger.
   Protected number As Double

   Public Sub New(value As T)
      Try
         Me.number = Convert.ToDouble(value)
      Catch e As OverflowException
         Throw New ArgumentException("value is too large.", e)
      Catch e As InvalidCastException
         Throw New ArgumentException("The value parameter is not numeric.", e)
      End Try
   End Sub

   Public Function Add(value As T) As T
      Return CType(Convert.ChangeType(number + Convert.ToDouble(value), GetType(T)), T)
   End Function

   Public Function Subtract(value As T) As T
      Return CType(Convert.ChangeType(number - Convert.ToDouble(value), GetType(T)), T)
   End Function
End Class

Public Class FloatingPoint(Of T As Structure) : Inherits Number(Of T)
   Public Sub New(number As T)
      MyBase.New(number)
      If TypeOf number Is Single Or
               TypeOf number Is Double Or
               TypeOf number Is Decimal Then
         Me.number = Convert.ToDouble(number)
      Else
         throw new ArgumentException("The number parameter is not a floating-point number.")
      End If
   End Sub
End Class
```

<span data-ttu-id="bf1ca-564">Ortak dil belirtimi, iç içe türler ve korumalı üyeler için bir örnek oluşturma modeli uygular.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-564">The Common Language Specification imposes a conservative per-instantiation model for nested types and protected members.</span></span> <span data-ttu-id="bf1ca-565">Açık genel türler, iç içe geçmiş, korunan genel bir türün belirli bir örneğini içeren imzalara sahip alanları veya üyeleri gösteremez.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-565">Open generic types cannot expose fields or members with signatures that contain a specific instantiation of a nested, protected generic type.</span></span> <span data-ttu-id="bf1ca-566">Genel bir temel sınıfın veya arabirimin belirli bir örneğini genişleten genel olmayan türler, iç içe geçmiş, korunan genel bir türün farklı bir örneğini içeren imzalara sahip alanları veya üyeleri gösteremez.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-566">Non-generic types that extend a specific instantiation of a generic base class or interface cannot expose fields or members with signatures that contain a different instantiation of a nested, protected generic type.</span></span>

<span data-ttu-id="bf1ca-567">Aşağıdaki örnek genel bir türü, `C1<T>` ve korumalı bir sınıfı tanımlar `C1<T>.N` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-567">The following example defines a generic type, `C1<T>`, and a protected class, `C1<T>.N`.</span></span> <span data-ttu-id="bf1ca-568">`C1<T>`iki yönteme sahiptir `M1` ve `M2` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-568">`C1<T>` has two methods, `M1` and `M2`.</span></span> <span data-ttu-id="bf1ca-569">Ancak, `M1` öğesinden bir nesne döndürmeye çalıştığı IÇIN CLS uyumlu değildir `C1<int>.N` `C1<T>` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-569">However, `M1` is not CLS-compliant because it tries to return a `C1<int>.N` object from `C1<T>`.</span></span> <span data-ttu-id="bf1ca-570">İkinci bir sınıf, `C2` öğesinden türetilir `C1<long>` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-570">A second class, `C2`, is derived from `C1<long>`.</span></span> <span data-ttu-id="bf1ca-571">İki yöntemi vardır `M3` ve `M4` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-571">It has two methods, `M3` and `M4`.</span></span> <span data-ttu-id="bf1ca-572">`M3`, `C1<int>.N` öğesinin bir alt sınıfından bir nesne döndürmeye çalıştığı IÇIN CLS uyumlu değildir `C1<long>` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-572">`M3` is not CLS-compliant because it tries to return a `C1<int>.N` object from a subclass of `C1<long>`.</span></span> <span data-ttu-id="bf1ca-573">Dil derleyicilerinin daha da kısıtlayıcı olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-573">Note that language compilers can be even more restrictive.</span></span> <span data-ttu-id="bf1ca-574">Bu örnekte, derlemeyi denediğinde Visual Basic bir hata görüntüler `M4` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-574">In this example, Visual Basic displays an error when it tries to compile `M4`.</span></span>

```csharp
using System;

[assembly:CLSCompliant(true)]

public class C1<T>
{
   protected class N { }

   protected void M1(C1<int>.N n) { } // Not CLS-compliant - C1<int>.N not
                                      // accessible from within C1<T> in all
                                      // languages
   protected void M2(C1<T>.N n) { }   // CLS-compliant – C1<T>.N accessible
                                      // inside C1<T>
}

public class C2 : C1<long>
{
   protected void M3(C1<int>.N n) { }  // Not CLS-compliant – C1<int>.N is not
                                       // accessible in C2 (extends C1<long>)

   protected void M4(C1<long>.N n) { } // CLS-compliant, C1<long>.N is
                                       // accessible in C2 (extends C1<long>)
}
// Attempting to compile the example displays output like the following:
//       Generics4.cs(9,22): warning CS3001: Argument type 'C1<int>.N' is not CLS-compliant
//       Generics4.cs(18,22): warning CS3001: Argument type 'C1<int>.N' is not CLS-compliant
```

```vb
<Assembly:CLSCompliant(True)>

Public Class C1(Of T)
   Protected Class N
   End Class

   Protected Sub M1(n As C1(Of Integer).N)   ' Not CLS-compliant - C1<int>.N not
                                             ' accessible from within C1(Of T) in all
   End Sub                                   ' languages

   Protected Sub M2(n As C1(Of T).N)     ' CLS-compliant – C1(Of T).N accessible
   End Sub                               ' inside C1(Of T)
End Class

Public Class C2 : Inherits C1(Of Long)
   Protected Sub M3(n As C1(Of Integer).N)   ' Not CLS-compliant – C1(Of Integer).N is not
   End Sub                                   ' accessible in C2 (extends C1(Of Long))

   Protected Sub M4(n As C1(Of Long).N)
   End Sub
End Class
' Attempting to compile the example displays output like the following:
'    error BC30508: 'n' cannot expose type 'C1(Of Integer).N' in namespace
'    '<Default>' through class 'C1'.
'
'       Protected Sub M1(n As C1(Of Integer).N)   ' Not CLS-compliant - C1<int>.N not
'                             ~~~~~~~~~~~~~~~~
'    error BC30389: 'C1(Of T).N' is not accessible in this context because
'    it is 'Protected'.
'
'       Protected Sub M3(n As C1(Of Integer).N)   ' Not CLS-compliant - C1(Of Integer).N is not
'
'                             ~~~~~~~~~~~~~~~~
'
'    error BC30389: 'C1(Of T).N' is not accessible in this context because it is 'Protected'.
'
'       Protected Sub M4(n As C1(Of Long).N)
'                             ~~~~~~~~~~~~~
```

### <a name="constructors"></a><span data-ttu-id="bf1ca-575">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="bf1ca-575">Constructors</span></span>

<span data-ttu-id="bf1ca-576">CLS uyumlu sınıfların ve yapıların içindeki oluşturucular şu kurallara uymalıdır:</span><span class="sxs-lookup"><span data-stu-id="bf1ca-576">Constructors in CLS-compliant classes and structures must follow these rules:</span></span>

* <span data-ttu-id="bf1ca-577">Türetilmiş bir sınıfın Oluşturucusu, devralınan örnek verilerine erişmeden önce temel sınıfının örnek oluşturucusunu çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-577">A constructor of a derived class must call the instance constructor of its base class before it accesses inherited instance data.</span></span> <span data-ttu-id="bf1ca-578">Bu gereksinim, temel sınıf oluşturucularının türetilmiş sınıfları tarafından devralınmasından kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-578">This requirement is due to the fact that base class constructors are not inherited by their derived classes.</span></span> <span data-ttu-id="bf1ca-579">Bu kural, doğrudan devralmayı desteklemeyen yapılar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-579">This rule does not apply to structures, which do not support direct inheritance.</span></span>

  <span data-ttu-id="bf1ca-580">Genellikle, aşağıdaki örnekte gösterildiği gibi, derleyiciler Bu kuralı CLS uyumluluğuna bağımsız olarak uygular.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-580">Typically, compilers enforce this rule independently of CLS compliance, as the following example shows.</span></span> <span data-ttu-id="bf1ca-581">`Doctor`Bir sınıftan türetilmiş bir sınıf oluşturur `Person` , ancak `Doctor` sınıfın `Person` devralınan örnek alanlarını başlatmak için sınıf oluşturucusunu çağırması başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-581">It creates a `Doctor` class that is derived from a `Person` class, but the `Doctor` class fails to call the `Person` class constructor to initialize inherited instance fields.</span></span>

    ```csharp
    using System;

    [assembly: CLSCompliant(true)]

    public class Person
    {
    private string fName, lName, _id;

    public Person(string firstName, string lastName, string id)
    {
        if (String.IsNullOrEmpty(firstName + lastName))
            throw new ArgumentNullException("Either a first name or a last name must be provided.");

        fName = firstName;
        lName = lastName;
        _id = id;
    }

    public string FirstName
    {
        get { return fName; }
    }

    public string LastName
    {
        get { return lName; }
    }

    public string Id
    {
        get { return _id; }
    }

    public override string ToString()
    {
        return String.Format("{0}{1}{2}", fName,
                            String.IsNullOrEmpty(fName) ?  "" : " ",
                            lName);
    }
    }

    public class Doctor : Person
    {
    public Doctor(string firstName, string lastName, string id)
    {
    }

    public override string ToString()
    {
        return "Dr. " + base.ToString();
    }
    }
    // Attempting to compile the example displays output like the following:
    //    ctor1.cs(45,11): error CS1729: 'Person' does not contain a constructor that takes 0
    //            arguments
    //    ctor1.cs(10,11): (Location of symbol related to previous error)
    ```

    ```vb
    <Assembly: CLSCompliant(True)>

    Public Class Person
       Private fName, lName, _id As String

       Public Sub New(firstName As String, lastName As String, id As String)
          If String.IsNullOrEmpty(firstName + lastName) Then
             Throw New ArgumentNullException("Either a first name or a last name must be provided.")
          End If

          fName = firstName
          lName = lastName
          _id = id
       End Sub

       Public ReadOnly Property FirstName As String
          Get
             Return fName
          End Get
       End Property

       Public ReadOnly Property LastName As String
          Get
             Return lName
          End Get
       End Property

       Public ReadOnly Property Id As String
          Get
             Return _id
          End Get
       End Property

       Public Overrides Function ToString() As String
          Return String.Format("{0}{1}{2}", fName,
                               If(String.IsNullOrEmpty(fName), "", " "),
                               lName)
       End Function
    End Class

    Public Class Doctor : Inherits Person
       Public Sub New(firstName As String, lastName As String, id As String)
       End Sub

       Public Overrides Function ToString() As String
          Return "Dr. " + MyBase.ToString()
       End Function
    End Class
    ' Attempting to compile the example displays output like the following:
    '    Ctor1.vb(46) : error BC30148: First statement of this 'Sub New' must be a call
    '    to 'MyBase.New' or 'MyClass.New' because base class 'Person' of 'Doctor' does
    '    not have an accessible 'Sub New' that can be called with no arguments.
    '
    '       Public Sub New()
    '                  ~~~
    ````

* <span data-ttu-id="bf1ca-582">Nesne Oluşturucusu bir nesne oluşturmak hariç çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-582">An object constructor cannot be called except to create an object.</span></span> <span data-ttu-id="bf1ca-583">Ayrıca, bir nesne iki kez başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-583">In addition, an object cannot be initialized twice.</span></span> <span data-ttu-id="bf1ca-584">Örneğin, bu, `Object.MemberwiseClone` oluşturucuları çağırmamalıdır anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-584">For example, this means that `Object.MemberwiseClone` must not call constructors.</span></span>

### <a name="properties"></a><span data-ttu-id="bf1ca-585">Özellikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-585">Properties</span></span>

<span data-ttu-id="bf1ca-586">CLS uyumlu türlerdeki özellikler aşağıdaki kurallara uymalıdır:</span><span class="sxs-lookup"><span data-stu-id="bf1ca-586">Properties in CLS-compliant types must follow these rules:</span></span>

* <span data-ttu-id="bf1ca-587">Özelliğin bir ayarlayıcı, alıcı veya her ikisi de olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-587">A property must have a setter, a getter, or both.</span></span> <span data-ttu-id="bf1ca-588">Bir derlemede, bunlar özel yöntemler olarak uygulanır, yani ayrı yöntemler olarak (alıcı `get` \_ *PropertyName* ve ayarlayıcı, PropertyName olarak adlandırılır `set` \_ *propertyname*) `SpecialName` derlemenin meta verilerinde olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-588">In an assembly, these are implemented as special methods, which means that they will appear as separate methods (the getter is named `get`\_*propertyname* and the setter is `set`\_*propertyname*) marked as `SpecialName` in the assembly's metadata.</span></span> <span data-ttu-id="bf1ca-589">C# derleyicisi, özniteliği uygulamaya gerek olmadan bu kuralı otomatik olarak uygular <xref:System.CLSCompliantAttribute> .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-589">The C# compiler enforces this rule automatically without the need to apply the <xref:System.CLSCompliantAttribute> attribute.</span></span>

* <span data-ttu-id="bf1ca-590">Özelliğin türü, özellik alıcısının dönüş türü ve ayarlayıcının son bağımsız değişkenidir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-590">A property's type is the return type of the property getter and the last argument of the setter.</span></span> <span data-ttu-id="bf1ca-591">Bu türler CLS uyumlu olmalıdır ve bağımsız değişkenler başvuruya göre özelliğe atanamaz (yani, yönetilen işaretçiler olamaz).</span><span class="sxs-lookup"><span data-stu-id="bf1ca-591">These types must be CLS compliant, and arguments cannot be assigned to the property by reference (that is, they cannot be managed pointers).</span></span>

* <span data-ttu-id="bf1ca-592">Bir özelliğin hem alıcı hem de ayarlayıcı varsa, her ikisi de sanal, hem statik hem de her iki örnek olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-592">If a property has both a getter and a setter, they must both be virtual, both static, or both instance.</span></span> <span data-ttu-id="bf1ca-593">C# derleyicisi otomatik olarak bu kuralı özellik tanımı sözdizimi üzerinden zorlar.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-593">The C# compiler automatically enforces this rule through property definition syntax.</span></span>

### <a name="events"></a><span data-ttu-id="bf1ca-594">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-594">Events</span></span>

<span data-ttu-id="bf1ca-595">Bir olay, adı ve türü ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-595">An event is defined by its name and its type.</span></span> <span data-ttu-id="bf1ca-596">Olay türü, olayı göstermek için kullanılan bir temsilcisidir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-596">The event type is a delegate that is used to indicate the event.</span></span> <span data-ttu-id="bf1ca-597">Örneğin, `DbConnection.StateChange` olay türündedir `StateChangeEventHandler` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-597">For example, the `DbConnection.StateChange` event is of type `StateChangeEventHandler`.</span></span> <span data-ttu-id="bf1ca-598">Olayın kendisinin yanı sıra, olay adına göre adlara sahip üç yöntem olayın uygulamasını sağlar ve `SpecialName` derlemenin meta verilerinde olarak işaretlenir:</span><span class="sxs-lookup"><span data-stu-id="bf1ca-598">In addition to the event itself, three methods with names based on the event name provide the event's implementation and are marked as `SpecialName` in the assembly's metadata:</span></span>

* <span data-ttu-id="bf1ca-599">_ EventName adlı bir olay işleyicisi ekleme yöntemi `add` .*EventName*</span><span class="sxs-lookup"><span data-stu-id="bf1ca-599">A method for adding an event handler, named `add`_*EventName*.</span></span> <span data-ttu-id="bf1ca-600">Örneğin, olay için olay aboneliği yöntemi `DbConnection.StateChange` adlandırılır `add_StateChange` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-600">For example, the event subscription method for the `DbConnection.StateChange` event is named `add_StateChange`.</span></span>

* <span data-ttu-id="bf1ca-601">_ EventName adlı bir olay işleyicisini kaldırma yöntemi `remove` .*EventName*</span><span class="sxs-lookup"><span data-stu-id="bf1ca-601">A method for removing an event handler, named `remove`_*EventName*.</span></span> <span data-ttu-id="bf1ca-602">Örneğin, olay için kaldırma yöntemi `DbConnection.StateChange` olarak adlandırılır `remove_StateChange` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-602">For example, the removal method for the `DbConnection.StateChange` event is named `remove_StateChange`.</span></span>

* <span data-ttu-id="bf1ca-603">EventName adlı olayın oluştuğunu belirten bir yöntem `raise` \_ *EventName*.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-603">A method for indicating that the event has occurred, named `raise`\_*EventName*.</span></span>

> [!NOTE]
> <span data-ttu-id="bf1ca-604">Ortak dil belirtiminin olayları ile ilgili kuralları, dil derleyicileri tarafından uygulanır ve bileşen geliştiricileri için saydamdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-604">Most of the Common Language Specification's rules regarding events are implemented by language compilers and are transparent to component developers.</span></span>

<span data-ttu-id="bf1ca-605">Olayı ekleme, kaldırma ve oluşturma yöntemleri aynı erişilebilirliği içermelidir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-605">The methods for adding, removing, and raising the event must have the same accessibility.</span></span> <span data-ttu-id="bf1ca-606">Bunların hepsi de statik, örnek veya sanal olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-606">They must also all be static, instance, or virtual.</span></span> <span data-ttu-id="bf1ca-607">Bir olayı ekleme ve kaldırma yöntemleri, türü olay temsilci türü olan bir parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-607">The methods for adding and removing an event have one parameter whose type is the event delegate type.</span></span> <span data-ttu-id="bf1ca-608">Add ve Remove yöntemlerinin her ikisi de bulunmalıdır ya da her ikisi de olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-608">The add and remove methods must both be present or both be absent.</span></span>

<span data-ttu-id="bf1ca-609">Aşağıdaki örnek, `Temperature` `TemperatureChanged` iki readsler arasındaki sıcaklık değişikliği bir eşik değerini eşitse veya aştığında bir olayı başlatan adlı CLS uyumlu bir sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-609">The following example defines a CLS-compliant class named `Temperature` that raises a `TemperatureChanged` event if the change in temperature between two readings equals or exceeds a threshold value.</span></span> <span data-ttu-id="bf1ca-610">`Temperature`Sınıfı açıkça `raise_TemperatureChanged` olay işleyicilerini yürütebilmesi için bir yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-610">The `Temperature` class explicitly defines a `raise_TemperatureChanged` method so that it can selectively execute event handlers.</span></span>

```csharp
using System;
using System.Collections;
using System.Collections.Generic;

[assembly: CLSCompliant(true)]

public class TemperatureChangedEventArgs : EventArgs
{
   private Decimal originalTemp;
   private Decimal newTemp;
   private DateTimeOffset when;

   public TemperatureChangedEventArgs(Decimal original, Decimal @new, DateTimeOffset time)
   {
      originalTemp = original;
      newTemp = @new;
      when = time;
   }

   public Decimal OldTemperature
   {
      get { return originalTemp; }
   }

   public Decimal CurrentTemperature
   {
      get { return newTemp; }
   }

   public DateTimeOffset Time
   {
      get { return when; }
   }
}

public delegate void TemperatureChanged(Object sender, TemperatureChangedEventArgs e);

public class Temperature
{
   private struct TemperatureInfo
   {
      public Decimal Temperature;
      public DateTimeOffset Recorded;
   }

   public event TemperatureChanged TemperatureChanged;

   private Decimal previous;
   private Decimal current;
   private Decimal tolerance;
   private List<TemperatureInfo> tis = new List<TemperatureInfo>();

   public Temperature(Decimal temperature, Decimal tolerance)
   {
      current = temperature;
      TemperatureInfo ti = new TemperatureInfo();
      ti.Temperature = temperature;
      tis.Add(ti);
      ti.Recorded = DateTimeOffset.UtcNow;
      this.tolerance = tolerance;
   }

   public Decimal CurrentTemperature
   {
      get { return current; }
      set {
         TemperatureInfo ti = new TemperatureInfo();
         ti.Temperature = value;
         ti.Recorded = DateTimeOffset.UtcNow;
         previous = current;
         current = value;
         if (Math.Abs(current - previous) >= tolerance)
            raise_TemperatureChanged(new TemperatureChangedEventArgs(previous, current, ti.Recorded));
      }
   }

   public void raise_TemperatureChanged(TemperatureChangedEventArgs eventArgs)
   {
      if (TemperatureChanged == null)
         return;

      foreach (TemperatureChanged d in TemperatureChanged.GetInvocationList()) {
         if (d.Method.Name.Contains("Duplicate"))
            Console.WriteLine("Duplicate event handler; event handler not executed.");
         else
            d.Invoke(this, eventArgs);
      }
   }
}

public class Example
{
   public Temperature temp;

   public static void Main()
   {
      Example ex = new Example();
   }

   public Example()
   {
      temp = new Temperature(65, 3);
      temp.TemperatureChanged += this.TemperatureNotification;
      RecordTemperatures();
      Example ex = new Example(temp);
      ex.RecordTemperatures();
   }

   public Example(Temperature t)
   {
      temp = t;
      RecordTemperatures();
   }

   public void RecordTemperatures()
   {
      temp.TemperatureChanged += this.DuplicateTemperatureNotification;
      temp.CurrentTemperature = 66;
      temp.CurrentTemperature = 63;
   }

   internal void TemperatureNotification(Object sender, TemperatureChangedEventArgs e)
   {
      Console.WriteLine("Notification 1: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature);
   }

   public void DuplicateTemperatureNotification(Object sender, TemperatureChangedEventArgs e)
   {
      Console.WriteLine("Notification 2: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature);
   }
}
```

```vb
Imports System.Collections
Imports System.Collections.Generic

<Assembly: CLSCompliant(True)>

Public Class TemperatureChangedEventArgs   : Inherits EventArgs
   Private originalTemp As Decimal
   Private newTemp As Decimal
   Private [when] As DateTimeOffset

   Public Sub New(original As Decimal, [new] As Decimal, [time] As DateTimeOffset)
      originalTemp = original
      newTemp = [new]
      [when] = [time]
   End Sub

   Public ReadOnly Property OldTemperature As Decimal
      Get
         Return originalTemp
      End Get
   End Property

   Public ReadOnly Property CurrentTemperature As Decimal
      Get
         Return newTemp
      End Get
   End Property

   Public ReadOnly Property [Time] As DateTimeOffset
      Get
         Return [when]
      End Get
   End Property
End Class

Public Delegate Sub TemperatureChanged(sender As Object, e As TemperatureChangedEventArgs)

Public Class Temperature
   Private Structure TemperatureInfo
      Dim Temperature As Decimal
      Dim Recorded As DateTimeOffset
   End Structure

   Public Event TemperatureChanged As TemperatureChanged

   Private previous As Decimal
   Private current As Decimal
   Private tolerance As Decimal
   Private tis As New List(Of TemperatureInfo)

   Public Sub New(temperature As Decimal, tolerance As Decimal)
      current = temperature
      Dim ti As New TemperatureInfo()
      ti.Temperature = temperature
      ti.Recorded = DateTimeOffset.UtcNow
      tis.Add(ti)
      Me.tolerance = tolerance
   End Sub

   Public Property CurrentTemperature As Decimal
      Get
         Return current
      End Get
      Set
         Dim ti As New TemperatureInfo
         ti.Temperature = value
         ti.Recorded = DateTimeOffset.UtcNow
         previous = current
         current = value
         If Math.Abs(current - previous) >= tolerance Then
            raise_TemperatureChanged(New TemperatureChangedEventArgs(previous, current, ti.Recorded))
         End If
      End Set
   End Property

   Public Sub raise_TemperatureChanged(eventArgs As TemperatureChangedEventArgs)
      If TemperatureChangedEvent Is Nothing Then Exit Sub

      Dim ListenerList() As System.Delegate = TemperatureChangedEvent.GetInvocationList()
      For Each d As TemperatureChanged In TemperatureChangedEvent.GetInvocationList()
         If d.Method.Name.Contains("Duplicate") Then
            Console.WriteLine("Duplicate event handler; event handler not executed.")
         Else
            d.Invoke(Me, eventArgs)
         End If
      Next
   End Sub
End Class

Public Class Example
   Public WithEvents temp As Temperature

   Public Shared Sub Main()
      Dim ex As New Example()
   End Sub

   Public Sub New()
      temp = New Temperature(65, 3)
      RecordTemperatures()
      Dim ex As New Example(temp)
      ex.RecordTemperatures()
   End Sub

   Public Sub New(t As Temperature)
      temp = t
      RecordTemperatures()
   End Sub

   Public Sub RecordTemperatures()
      temp.CurrentTemperature = 66
      temp.CurrentTemperature = 63

   End Sub

   Friend Shared Sub TemperatureNotification(sender As Object, e As TemperatureChangedEventArgs) _
          Handles temp.TemperatureChanged
      Console.WriteLine("Notification 1: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature)
   End Sub

   Friend Shared Sub DuplicateTemperatureNotification(sender As Object, e As TemperatureChangedEventArgs) _
          Handles temp.TemperatureChanged
      Console.WriteLine("Notification 2: The temperature changed from {0} to {1}", e.OldTemperature, e.CurrentTemperature)
   End Sub
End Class
```

### <a name="overloads"></a><span data-ttu-id="bf1ca-611">Aşırı Yüklemeler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-611">Overloads</span></span>

<span data-ttu-id="bf1ca-612">Ortak dil belirtimi, aşırı yüklenmiş üyelere aşağıdaki gereksinimleri uygular:</span><span class="sxs-lookup"><span data-stu-id="bf1ca-612">The Common Language Specification imposes the following requirements on overloaded members:</span></span>

* <span data-ttu-id="bf1ca-613">Üyeler, parametrelerin sayısına ve herhangi bir parametre türüne göre aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-613">Members can be overloaded based on the number of parameters and the type of any parameter.</span></span> <span data-ttu-id="bf1ca-614">Çağırma kuralı, dönüş türü, yönteme veya parametresine uygulanan özel değiştiriciler, bir değere veya başvuruya göre geçirilen parametrelerin, aşırı yüklemeler arasında ayrım yaparken dikkate alınıp alınmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-614">Calling convention, return type, custom modifiers applied to the method or its parameter, and whether parameters are passed by value or by reference are not considered when differentiating between overloads.</span></span> <span data-ttu-id="bf1ca-615">Bir örnek için, [adlandırma kuralları](#naming-conventions) bölümündeki bir kapsam içinde adların benzersiz olması gerekliliğe ilişkin koda bakın.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-615">For an example, see the code for the requirement that names must be unique within a scope in the [Naming conventions](#naming-conventions) section.</span></span>

* <span data-ttu-id="bf1ca-616">Yalnızca özellikler ve yöntemler aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-616">Only properties and methods can be overloaded.</span></span> <span data-ttu-id="bf1ca-617">Alanlar ve olaylar aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-617">Fields and events cannot be overloaded.</span></span>

* <span data-ttu-id="bf1ca-618">Genel yöntemler, genel parametrelerinin sayısına bağlı olarak aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-618">Generic methods can be overloaded based on the number of their generic parameters.</span></span>

> [!NOTE]
> <span data-ttu-id="bf1ca-619">`op_Explicit`Ve `op_Implicit` işleçleri, geri yükleme çözümlemesi için bir yöntem imzasının bir parçası olarak kabul edilen bir kural için özel durumlardır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-619">The `op_Explicit` and `op_Implicit` operators are exceptions to the rule that return value is not considered part of a method signature for overload resolution.</span></span> <span data-ttu-id="bf1ca-620">Bu iki işleç, parametreleri ve dönüş değerleri temel alınarak aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-620">These two operators can be overloaded based on both their parameters and their return value.</span></span>

### <a name="exceptions"></a><span data-ttu-id="bf1ca-621">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="bf1ca-621">Exceptions</span></span>

<span data-ttu-id="bf1ca-622">Özel durum nesnelerinin [sistem. Exception](xref:System.Exception) 'dan veya öğesinden türetilmiş başka bir türden türetilmesi gerekir `System.Exception` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-622">Exception objects must derive from [System.Exception](xref:System.Exception) or from another type derived from `System.Exception`.</span></span> <span data-ttu-id="bf1ca-623">Aşağıdaki örnek, özel bir sınıfı `ErrorClass` özel durum işleme için kullanıldığında oluşan derleyici hatasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-623">The following example illustrates the compiler error that results when a custom class named `ErrorClass` is used for exception handling.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ErrorClass
{
   string msg;

   public ErrorClass(string errorMessage)
   {
      msg = errorMessage;
   }

   public string Message
   {
      get { return msg; }
   }
}

public static class StringUtilities
{
   public static string[] SplitString(this string value, int index)
   {
      if (index < 0 | index > value.Length) {
         ErrorClass badIndex = new ErrorClass("The index is not within the string.");
         throw badIndex;
      }
      string[] retVal = { value.Substring(0, index - 1),
                          value.Substring(index) };
      return retVal;
   }
}
// Compilation produces a compiler error like the following:
//    Exceptions1.cs(26,16): error CS0155: The type caught or thrown must be derived from
//            System.Exception
```

```vb
Imports System.Runtime.CompilerServices

<Assembly: CLSCompliant(True)>

Public Class ErrorClass
   Dim msg As String

   Public Sub New(errorMessage As String)
      msg = errorMessage
   End Sub

   Public ReadOnly Property Message As String
      Get
         Return msg
      End Get
   End Property
End Class

Public Module StringUtilities
   <Extension()> Public Function SplitString(value As String, index As Integer) As String()
      If index < 0 Or index > value.Length Then
         Dim BadIndex As New ErrorClass("The index is not within the string.")
         Throw BadIndex
      End If
      Dim retVal() As String = { value.Substring(0, index - 1),
                                 value.Substring(index) }
      Return retVal
   End Function
End Module
' Compilation produces a compiler error like the following:
'    Exceptions1.vb(27) : error BC30665: 'Throw' operand must derive from 'System.Exception'.
'
'             Throw BadIndex
'             ~~~~~~~~~~~~~~
```

<span data-ttu-id="bf1ca-624">Bu hatayı düzeltmek için, `ErrorClass` sınıfın öğesinden devralması gerekir `System.Exception` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-624">To correct this error, the `ErrorClass` class must inherit from `System.Exception`.</span></span> <span data-ttu-id="bf1ca-625">Ayrıca, Ileti özelliği geçersiz kılınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-625">In addition, the Message property must be overridden.</span></span> <span data-ttu-id="bf1ca-626">Aşağıdaki örnek, CLS uyumlu bir sınıf tanımlamak için bu hataları düzeltir `ErrorClass` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-626">The following example corrects these errors to define an `ErrorClass` class that is CLS-compliant.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

public class ErrorClass : Exception
{
   string msg;

   public ErrorClass(string errorMessage)
   {
      msg = errorMessage;
   }

   public override string Message
   {
      get { return msg; }
   }
}

public static class StringUtilities
{
   public static string[] SplitString(this string value, int index)
   {
      if (index < 0 | index > value.Length) {
         ErrorClass badIndex = new ErrorClass("The index is not within the string.");
         throw badIndex;
      }
      string[] retVal = { value.Substring(0, index - 1),
                          value.Substring(index) };
      return retVal;
   }
}
```

```vb
Imports System.Runtime.CompilerServices

<Assembly: CLSCompliant(True)>

Public Class ErrorClass : Inherits Exception
   Dim msg As String

   Public Sub New(errorMessage As String)
      msg = errorMessage
   End Sub

   Public Overrides ReadOnly Property Message As String
      Get
         Return msg
      End Get
   End Property
End Class

Public Module StringUtilities
   <Extension()> Public Function SplitString(value As String, index As Integer) As String()
      If index < 0 Or index > value.Length Then
         Dim BadIndex As New ErrorClass("The index is not within the string.")
         Throw BadIndex
      End If
      Dim retVal() As String = { value.Substring(0, index - 1),
                                 value.Substring(index) }
      Return retVal
   End Function
End Module
```

### <a name="attributes"></a><span data-ttu-id="bf1ca-627">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bf1ca-627">Attributes</span></span>

<span data-ttu-id="bf1ca-628">Özel öznitelikler, özel öznitelikleri depolamak ve derlemeler, türler, Üyeler ve Yöntem parametreleri gibi programlama nesneleri hakkındaki meta verileri almak için genişletilebilir bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-628">In.NET Framework assemblies, custom attributes provide an extensible mechanism for storing custom attributes and retrieving metadata about programming objects, such as assemblies, types, members, and method parameters.</span></span> <span data-ttu-id="bf1ca-629">Özel öznitelikler [System. Attribute](xref:System.Attribute) veya öğesinden türetilmiş bir türden türetilmelidir `System.Attribute` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-629">Custom attributes must derive from [System.Attribute](xref:System.Attribute) or from a type derived from `System.Attribute`.</span></span>

<span data-ttu-id="bf1ca-630">Aşağıdaki örnek bu kuralı ihlal ediyor.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-630">The following example violates this rule.</span></span> <span data-ttu-id="bf1ca-631">Sınıfından `NumericAttribute` türetilmeyen bir sınıfı tanımlar `System.Attribute` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-631">It defines a `NumericAttribute` class that does not derive from `System.Attribute`.</span></span> <span data-ttu-id="bf1ca-632">Derleyici hatası, sınıf tanımlandığında değil, yalnızca CLS uyumlu olmayan öznitelik uygulandığında oluşur.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-632">Note that a compiler error results only when the non-CLS-compliant attribute is applied, not when the class is defined.</span></span>

```csharp
using System;

[assembly: CLSCompliant(true)]

[AttributeUsageAttribute(AttributeTargets.Class | AttributeTargets.Struct)]
public class NumericAttribute
{
   private bool _isNumeric;

   public NumericAttribute(bool isNumeric)
   {
      _isNumeric = isNumeric;
   }

   public bool IsNumeric
   {
      get { return _isNumeric; }
   }
}

[Numeric(true)] public struct UDouble
{
   double Value;
}
// Compilation produces a compiler error like the following:
//    Attribute1.cs(22,2): error CS0616: 'NumericAttribute' is not an attribute class
//    Attribute1.cs(7,14): (Location of symbol related to previous error)
```

```vb
<Assembly: CLSCompliant(True)>

<AttributeUsageAttribute(AttributeTargets.Class Or AttributeTargets.Struct)> _
Public Class NumericAttribute
   Private _isNumeric As Boolean

   Public Sub New(isNumeric As Boolean)
      _isNumeric = isNumeric
   End Sub

   Public ReadOnly Property IsNumeric As Boolean
      Get
         Return _isNumeric
      End Get
   End Property
End Class

<Numeric(True)> Public Structure UDouble
   Dim Value As Double
End Structure
' Compilation produces a compiler error like the following:
'    error BC31504: 'NumericAttribute' cannot be used as an attribute because it
'    does not inherit from 'System.Attribute'.
'
'    <Numeric(True)> Public Structure UDouble
'     ~~~~~~~~~~~~~
```

<span data-ttu-id="bf1ca-633">CLS uyumlu bir özniteliğin Oluşturucusu veya özellikleri yalnızca aşağıdaki türleri açığa alabilir:</span><span class="sxs-lookup"><span data-stu-id="bf1ca-633">The constructor or the properties of a CLS-compliant attribute can expose only the following types:</span></span>

* [<span data-ttu-id="bf1ca-634">Boole</span><span class="sxs-lookup"><span data-stu-id="bf1ca-634">Boolean</span></span>](xref:System.Boolean)

* [<span data-ttu-id="bf1ca-635">Bayt</span><span class="sxs-lookup"><span data-stu-id="bf1ca-635">Byte</span></span>](xref:System.Byte)

* [<span data-ttu-id="bf1ca-636">Char</span><span class="sxs-lookup"><span data-stu-id="bf1ca-636">Char</span></span>](xref:System.Char)

* [<span data-ttu-id="bf1ca-637">Çift</span><span class="sxs-lookup"><span data-stu-id="bf1ca-637">Double</span></span>](xref:System.Double)

* [<span data-ttu-id="bf1ca-638">Int16</span><span class="sxs-lookup"><span data-stu-id="bf1ca-638">Int16</span></span>](xref:System.Int16)

* [<span data-ttu-id="bf1ca-639">Int32</span><span class="sxs-lookup"><span data-stu-id="bf1ca-639">Int32</span></span>](xref:System.Int32)

* [<span data-ttu-id="bf1ca-640">Tutulamaz</span><span class="sxs-lookup"><span data-stu-id="bf1ca-640">Int64</span></span>](xref:System.Int64)

* [<span data-ttu-id="bf1ca-641">Tek</span><span class="sxs-lookup"><span data-stu-id="bf1ca-641">Single</span></span>](xref:System.Single)

* [<span data-ttu-id="bf1ca-642">Dize</span><span class="sxs-lookup"><span data-stu-id="bf1ca-642">String</span></span>](xref:System.String)

* [<span data-ttu-id="bf1ca-643">Tür</span><span class="sxs-lookup"><span data-stu-id="bf1ca-643">Type</span></span>](xref:System.Type)

* <span data-ttu-id="bf1ca-644">Temel türü,, veya olan herhangi bir numaralandırma türü `Byte` `Int16` `Int32` `Int64` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-644">Any enumeration type whose underlying type is `Byte`, `Int16`, `Int32`, or `Int64`.</span></span>

<span data-ttu-id="bf1ca-645">Aşağıdaki örnek, `DescriptionAttribute` [özniteliğinden](xref:System.Attribute)türetilen bir sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-645">The following example defines a `DescriptionAttribute` class that derives from [Attribute](xref:System.Attribute).</span></span> <span data-ttu-id="bf1ca-646">Sınıf oluşturucusunun türünde bir parametresi vardır, bu `Descriptor` yüzden sınıf CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-646">The class constructor has a parameter of type `Descriptor`, so the class is not CLS-compliant.</span></span> <span data-ttu-id="bf1ca-647">C# derleyicisinin bir uyarı yayar ancak başarıyla derlendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-647">Note that the C# compiler emits a warning but compiles successfully.</span></span>

```csharp
using System;

[assembly:CLSCompliantAttribute(true)]

public enum DescriptorType { type, member };

public class Descriptor
{
   public DescriptorType Type;
   public String Description;
}

[AttributeUsage(AttributeTargets.All)]
public class DescriptionAttribute : Attribute
{
   private Descriptor desc;

   public DescriptionAttribute(Descriptor d)
   {
      desc = d;
   }

   public Descriptor Descriptor
   { get { return desc; } }
}
// Attempting to compile the example displays output like the following:
//       warning CS3015: 'DescriptionAttribute' has no accessible
//               constructors which use only CLS-compliant types
```

```vb
<Assembly:CLSCompliantAttribute(True)>

Public Enum DescriptorType As Integer
   Type = 0
   Member = 1
End Enum

Public Class Descriptor
   Public Type As DescriptorType
   Public Description As String
End Class

<AttributeUsage(AttributeTargets.All)> _
Public Class DescriptionAttribute : Inherits Attribute
   Private desc As Descriptor

   Public Sub New(d As Descriptor)
      desc = d
   End Sub

   Public ReadOnly Property Descriptor As Descriptor
      Get
         Return desc
      End Get
   End Property
End Class
```

## <a name="the-clscompliantattribute-attribute"></a><span data-ttu-id="bf1ca-648">CLSCompliantAttribute özniteliği</span><span class="sxs-lookup"><span data-stu-id="bf1ca-648">The CLSCompliantAttribute attribute</span></span>

<span data-ttu-id="bf1ca-649">[CLSCompliantAttribute](xref:System.CLSCompliantAttribute) özniteliği, bir program öğesinin ortak dil belirtimi ile uyumlu olup olmadığını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-649">The [CLSCompliantAttribute](xref:System.CLSCompliantAttribute) attribute is used to indicate whether a program element complies with the Common Language Specification.</span></span> <span data-ttu-id="bf1ca-650">`CLSCompliantAttribute.CLSCompliantAttribute(Boolean)`Oluşturucu, program ÖĞESININ CLS uyumlu olup olmadığını belirten, *ısuyumlu*tek bir gerekli parametre içerir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-650">The `CLSCompliantAttribute.CLSCompliantAttribute(Boolean)` constructor includes a single required parameter, *isCompliant*, that indicates whether the program element is CLS-compliant.</span></span>

<span data-ttu-id="bf1ca-651">Derleme zamanında derleyici, CLS uyumlu olarak kabul edilen uyumlu olmayan öğeleri algılar ve bir uyarı gönderir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-651">At compile time, the compiler detects non-compliant elements that are presumed to be CLS-compliant and emits a warning.</span></span> <span data-ttu-id="bf1ca-652">Derleyici, açıkça uyumsuz olacak şekilde bildirilmeyen türler veya Üyeler için uyarıları göstermez.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-652">The compiler does not emit warnings for types or members that are explicitly declared to be non-compliant.</span></span>

<span data-ttu-id="bf1ca-653">Bileşen geliştiricileri, `CLSCompliantAttribute` özniteliğini iki şekilde kullanabilir:</span><span class="sxs-lookup"><span data-stu-id="bf1ca-653">Component developers can use the `CLSCompliantAttribute` attribute in two ways:</span></span>

* <span data-ttu-id="bf1ca-654">CLS uyumlu olan ve CLS uyumlu olmayan parçalar içeren bir bileşen tarafından açığa çıkarılan ortak arabirimin parçalarını tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-654">To define the parts of the public interface exposed by a component that are CLS-compliant and the parts that are not CLS-compliant.</span></span> <span data-ttu-id="bf1ca-655">Özniteliği belirli program öğelerini CLS uyumlu olarak işaretlemek için kullanıldığında, bu öğelerin .NET Framework hedef olan tüm diller ve araçlardan erişilebilir olmasını güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-655">When the attribute is used to mark particular program elements as CLS-compliant, its use guarantees that those elements are accessible from all languages and tools that target the .NET Framework.</span></span>

* <span data-ttu-id="bf1ca-656">Bileşen kitaplığının ortak arabiriminin yalnızca CLS uyumlu program öğelerini kullanıma sunduğundan emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-656">To ensure that the component library's public interface exposes only program elements that are CLS-compliant.</span></span> <span data-ttu-id="bf1ca-657">Öğeler CLS uyumlu değilse, derleyiciler genellikle bir uyarı vermez.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-657">If elements are not CLS-compliant, compilers will generally issue a warning.</span></span>

> [!WARNING]
> <span data-ttu-id="bf1ca-658">Bazı durumlarda, dil derleyicileri, özniteliğin kullanılıp kullanılmadığına bakılmaksızın CLS uyumlu kuralları uygular `CLSCompliantAttribute` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-658">In some cases, language compilers enforce CLS-compliant rules regardless of whether the `CLSCompliantAttribute` attribute is used.</span></span> <span data-ttu-id="bf1ca-659">Örneğin, `*static` bir arabirimde bir üyenin TANıMLANMASı CLS kuralını ihlal ediyor.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-659">For example, defining a `*static` member in an interface violates a CLS rule.</span></span> <span data-ttu-id="bf1ca-660">Ancak, `*static` bir arabirimde bir üye tanımlarsanız, C# derleyicisi bir hata iletisi görüntüler ve uygulamayı derlemez.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-660">However, if you define a `*static` member in an interface, the C# compiler displays an error message and fails to compile the app.</span></span>

<span data-ttu-id="bf1ca-661">`CLSCompliantAttribute`Özniteliği değeri olan bir [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) özniteliğiyle işaretlenir `AttributeTargets.All` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-661">The `CLSCompliantAttribute` attribute is marked with an [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) attribute that has a value of `AttributeTargets.All`.</span></span> <span data-ttu-id="bf1ca-662">Bu değer, `CLSCompliantAttribute` özniteliği derlemeler, modüller, türler (sınıflar, yapılar, numaralandırmalar, arabirimler ve temsilciler), tür üyeleri (oluşturucular, Yöntemler, özellikler, alanlar ve olaylar), parametreler, genel parametreler ve dönüş değerleri dahil olmak üzere herhangi bir program öğesine uygulamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-662">This value allows you to apply the `CLSCompliantAttribute` attribute to any program element, including assemblies, modules, types (classes, structures, enumerations, interfaces, and delegates), type members (constructors, methods, properties, fields, and events), parameters, generic parameters, and return values.</span></span> <span data-ttu-id="bf1ca-663">Ancak, uygulamada, özniteliğini yalnızca derlemeler, türler ve tür üyelerine uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-663">However, in practice, you should apply the attribute only to assemblies, types, and type members.</span></span> <span data-ttu-id="bf1ca-664">Aksi takdirde, derleyiciler özniteliği yoksayar ve kitaplığınızın ortak arabirimindeki uyumlu olmayan bir parametre, genel parametre veya dönüş değeri ile karşılaştığında Derleyici uyarıları oluşturmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-664">Otherwise, compilers ignore the attribute and continue to generate compiler warnings whenever they encounter a non-compliant parameter, generic parameter, or return value in your library's public interface.</span></span>

<span data-ttu-id="bf1ca-665">`CLSCompliantAttribute`Özniteliğin değeri kapsanan program öğeleri tarafından devralınır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-665">The value of the `CLSCompliantAttribute` attribute is inherited by contained program elements.</span></span> <span data-ttu-id="bf1ca-666">Örneğin, bir derleme CLS uyumlu olarak işaretlenmişse, türleri de CLS uyumludur.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-666">For example, if an assembly is marked as CLS-compliant, its types are also CLS-compliant.</span></span> <span data-ttu-id="bf1ca-667">Bir tür CLS uyumlu olarak işaretlenmişse, iç içe geçmiş türleri ve üyeleri de CLS uyumludur.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-667">If a type is marked as CLS-compliant, its nested types and members are also CLS-compliant.</span></span>

<span data-ttu-id="bf1ca-668">`CLSCompliantAttribute`Dahil edilen bir program öğesine özniteliğini uygulayarak devralınan uyumluluğu açıkça geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-668">You can explicitly override the inherited compliance by applying the `CLSCompliantAttribute` attribute to a contained program element.</span></span> <span data-ttu-id="bf1ca-669">Örneğin, uyumlu bir `CLSCompliantAttribute` derlemede uyumlu olmayan bir tür tanımlamak Için *ısuyumlu* değeri olan özniteliğini kullanabilirsiniz `false` ve uyumlu olmayan bir derlemede uyumlu bir tür tanımlamak için bir *ısuyumlu* değeri ile özniteliğini kullanabilirsiniz `true` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-669">For example, you can use the `CLSCompliantAttribute` attribute with an *isCompliant* value of `false` to define a non-compliant type in a compliant assembly, and you can use the attribute with an *isCompliant* value of `true` to define a compliant type in a non-compliant assembly.</span></span> <span data-ttu-id="bf1ca-670">Uyumlu olmayan üyeleri, uyumlu bir türde de tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-670">You can also define non-compliant members in a compliant type.</span></span> <span data-ttu-id="bf1ca-671">Ancak, uyumlu olmayan bir tür uyumlu üyelere sahip olamaz, bu yüzden uyumsuz bir türden devralmayı geçersiz kılmak için *ısuyumlu* değeri olan özniteliği kullanamazsınız `true` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-671">However, a non-compliant type cannot have compliant members, so you cannot use the attribute with an *isCompliant* value of `true` to override inheritance from a non-compliant type.</span></span>

<span data-ttu-id="bf1ca-672">Bileşenleri geliştirirken, `CLSCompliantAttribute` derlemenizin, türlerinin ve ÜYELERININ CLS uyumlu olup olmadığını belirtmek için her zaman özniteliğini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-672">When you are developing components, you should always use the `CLSCompliantAttribute` attribute to indicate whether your assembly, its types, and its members are CLS-compliant.</span></span>

<span data-ttu-id="bf1ca-673">CLS uyumlu bileşenler oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="bf1ca-673">To create CLS-compliant components:</span></span>

1. <span data-ttu-id="bf1ca-674">`CLSCompliantAttribute`DERLEMENIZI CLS uyumlu olarak işaretlemek için öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-674">Use the `CLSCompliantAttribute` to mark you assembly as CLS-compliant.</span></span>

2. <span data-ttu-id="bf1ca-675">Derlemede, CLS uyumlu olmayan, genel olarak sunulan herhangi bir türü, uyumsuz olarak işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-675">Mark any publicly exposed types in the assembly that are not CLS-compliant as non-compliant.</span></span>

3. <span data-ttu-id="bf1ca-676">CLS uyumlu türlerde herkese açık olan tüm üyeleri uyumlu değil olarak işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-676">Mark any publicly exposed members in CLS-compliant types as non-compliant.</span></span>

4. <span data-ttu-id="bf1ca-677">CLS uyumlu olmayan üyeler için CLS uyumlu bir alternatif sağlar.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-677">Provide a CLS-compliant alternative for non-CLS-compliant members.</span></span>

<span data-ttu-id="bf1ca-678">Uyumlu olmayan tüm türlerini ve üyelerini başarıyla işaretlediyseniz, derleyicisinde uyumsuz olmayan uyarılar sunulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-678">If you've successfully marked all your non-compliant types and members, your compiler should not emit any non-compliance warnings.</span></span> <span data-ttu-id="bf1ca-679">Ancak, hangi üyelerin CLS uyumlu olmadığını ve ürün belgelerinizde CLS uyumlu alternatiflerini listelemeyeceğini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-679">However, you should indicate which members are not CLS-compliant and list their CLS-compliant alternatives in your product documentation.</span></span>

<span data-ttu-id="bf1ca-680">Aşağıdaki örnek, CLS `CLSCompliantAttribute` uyumlu bir derlemeyi ve `CharacterUtilities` , CLS uyumlu olmayan iki üyeye sahip bir türünü tanımlamak için özniteliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-680">The following example uses the `CLSCompliantAttribute` attribute to define a CLS-compliant assembly and a type, `CharacterUtilities`, that has two non-CLS-compliant members.</span></span> <span data-ttu-id="bf1ca-681">Her iki üye de özniteliğiyle etiketlendiği `CLSCompliant(false)` için derleyici hiçbir uyarı üretmez.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-681">Because both members are tagged with the `CLSCompliant(false)` attribute, the compiler produces no warnings.</span></span> <span data-ttu-id="bf1ca-682">Sınıfı, her iki yöntem için de CLS uyumlu bir alternatif sağlar.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-682">The class also provides a CLS-compliant alternative for both methods.</span></span> <span data-ttu-id="bf1ca-683">Normalde, `ToUTF16` CLS uyumlu alternatifler sağlamak için metoda yalnızca iki aşırı yükleme ekleyeceğiz.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-683">Ordinarily, we would just add two overloads to the `ToUTF16` method to provide CLS-compliant alternatives.</span></span> <span data-ttu-id="bf1ca-684">Ancak, dönüş değerine göre Yöntemler aşırı yüklenemez, CLS uyumlu yöntemlerin adları uyumlu olmayan yöntemlerin adlarından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-684">However, because methods cannot be overloaded based on return value, the names of the CLS-compliant methods are different from the names of the non-compliant methods.</span></span>

```csharp
using System;
using System.Text;

[assembly:CLSCompliant(true)]

public class CharacterUtilities
{
   [CLSCompliant(false)] public static ushort ToUTF16(String s)
   {
      s = s.Normalize(NormalizationForm.FormC);
      return Convert.ToUInt16(s[0]);
   }

   [CLSCompliant(false)] public static ushort ToUTF16(Char ch)
   {
      return Convert.ToUInt16(ch);
   }

   // CLS-compliant alternative for ToUTF16(String).
   public static int ToUTF16CodeUnit(String s)
   {
      s = s.Normalize(NormalizationForm.FormC);
      return (int) Convert.ToUInt16(s[0]);
   }

   // CLS-compliant alternative for ToUTF16(Char).
   public static int ToUTF16CodeUnit(Char ch)
   {
      return Convert.ToInt32(ch);
   }

   public bool HasMultipleRepresentations(String s)
   {
      String s1 = s.Normalize(NormalizationForm.FormC);
      return s.Equals(s1);
   }

   public int GetUnicodeCodePoint(Char ch)
   {
      if (Char.IsSurrogate(ch))
         throw new ArgumentException("ch cannot be a high or low surrogate.");

      return Char.ConvertToUtf32(ch.ToString(), 0);
   }

   public int GetUnicodeCodePoint(Char[] chars)
   {
      if (chars.Length > 2)
         throw new ArgumentException("The array has too many characters.");

      if (chars.Length == 2) {
         if (! Char.IsSurrogatePair(chars[0], chars[1]))
            throw new ArgumentException("The array must contain a low and a high surrogate.");
         else
            return Char.ConvertToUtf32(chars[0], chars[1]);
      }
      else {
         return Char.ConvertToUtf32(chars.ToString(), 0);
      }
   }
}
```

```vb
Imports System.Text

<Assembly:CLSCompliant(True)>

Public Class CharacterUtilities
   <CLSCompliant(False)> Public Shared Function ToUTF16(s As String) As UShort
      s = s.Normalize(NormalizationForm.FormC)
      Return Convert.ToUInt16(s(0))
   End Function

   <CLSCompliant(False)> Public Shared Function ToUTF16(ch As Char) As UShort
      Return Convert.ToUInt16(ch)
   End Function

   ' CLS-compliant alternative for ToUTF16(String).
   Public Shared Function ToUTF16CodeUnit(s As String) As Integer
      s = s.Normalize(NormalizationForm.FormC)
      Return CInt(Convert.ToInt16(s(0)))
   End Function

   ' CLS-compliant alternative for ToUTF16(Char).
   Public Shared Function ToUTF16CodeUnit(ch As Char) As Integer
      Return Convert.ToInt32(ch)
   End Function

   Public Function HasMultipleRepresentations(s As String) As Boolean
      Dim s1 As String = s.Normalize(NormalizationForm.FormC)
      Return s.Equals(s1)
   End Function

   Public Function GetUnicodeCodePoint(ch As Char) As Integer
      If Char.IsSurrogate(ch) Then
         Throw New ArgumentException("ch cannot be a high or low surrogate.")
      End If
      Return Char.ConvertToUtf32(ch.ToString(), 0)
   End Function

   Public Function GetUnicodeCodePoint(chars() As Char) As Integer
      If chars.Length > 2 Then
         Throw New ArgumentException("The array has too many characters.")
      End If
      If chars.Length = 2 Then
         If Not Char.IsSurrogatePair(chars(0), chars(1)) Then
            Throw New ArgumentException("The array must contain a low and a high surrogate.")
         Else
            Return Char.ConvertToUtf32(chars(0), chars(1))
         End If
      Else
         Return Char.ConvertToUtf32(chars.ToString(), 0)
      End If
   End Function
End Class
```

<span data-ttu-id="bf1ca-685">Bir kitaplık yerine bir uygulama geliştiriyorsanız (yani, diğer uygulama geliştiricileri tarafından tüketilen türleri veya üyeleri açığa çıkarmadıysanız), uygulamanızın kullandığı program öğelerinin CLS uyumluluğu yalnızca dilinizin bu işlemleri desteklememesi durumunda ilgilenmektedir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-685">If you are developing an app rather than a library (that is, if you aren't exposing types or members that can be consumed by other app developers), the CLS compliance of the program elements that your app consumes are of interest only if your language does not support them.</span></span> <span data-ttu-id="bf1ca-686">Bu durumda, CLS uyumlu olmayan bir öğeyi kullanmaya çalıştığınızda dil derleyicinizin bir hata üretecektir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-686">In that case, your language compiler will generate an error when you try to use a non-CLS-compliant element.</span></span>

## <a name="cross-language-interoperability"></a><span data-ttu-id="bf1ca-687">Diller Arası Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="bf1ca-687">Cross-Language Interoperability</span></span>

<span data-ttu-id="bf1ca-688">Dil bağımsızlığının birkaç olası anlamı vardır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-688">Language independence has a number of possible meanings.</span></span> <span data-ttu-id="bf1ca-689">Bir anlamı, başka bir dilde yazılmış bir uygulamadan bir dilde yazılmış türleri sorunsuz bir şekilde kullanmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-689">One meaning involves seamlessly consuming types written in one language from an app written in another language.</span></span> <span data-ttu-id="bf1ca-690">Bu makalenin konusu olan ikinci anlamı ise, birden çok dilde yazılmış kodu tek bir .NET Framework derlemesi olarak birleştirmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-690">A second meaning, which is the focus of this article, involves combining code written in multiple languages into a single .NET Framework assembly.</span></span>

<span data-ttu-id="bf1ca-691">Aşağıdaki örnek, iki sınıf içeren Utilities. dll adlı bir sınıf kitaplığı oluşturarak platformlar arası birlikte çalışabilirliği gösterir `NumericLib` ve `StringLib` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-691">The following example illustrates cross-language interoperability by creating a class library named Utilities.dll that includes two classes, `NumericLib` and `StringLib`.</span></span> <span data-ttu-id="bf1ca-692">`NumericLib`Sınıfı C# dilinde yazılır ve `StringLib` sınıf Visual Basic yazılır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-692">The `NumericLib` class is written in C#, and the `StringLib` class is written in Visual Basic.</span></span> <span data-ttu-id="bf1ca-693">`StringUtil.vb`Bu, sınıfının sınıfında tek bir üye içeren kaynak kodu `ToTitleCase` `StringLib` .</span><span class="sxs-lookup"><span data-stu-id="bf1ca-693">Here's the source code for `StringUtil.vb`, which includes a single member, `ToTitleCase`, in its `StringLib` class.</span></span>

```vb
Imports System.Collections.Generic
Imports System.Runtime.CompilerServices

Public Module StringLib
   Private exclusions As List(Of String)

   Sub New()
      Dim words() As String = { "a", "an", "and", "of", "the" }
      exclusions = New List(Of String)
      exclusions.AddRange(words)
   End Sub

   <Extension()> _
   Public Function ToTitleCase(title As String) As String
      Dim words() As String = title.Split()
      Dim result As String = String.Empty

      For ctr As Integer = 0 To words.Length - 1
         Dim word As String = words(ctr)
         If ctr = 0 OrElse Not exclusions.Contains(word.ToLower()) Then
            result += word.Substring(0, 1).ToUpper() + _
                      word.Substring(1).ToLower()
         Else
            result += word.ToLower()
         End If
         If ctr <= words.Length - 1 Then
            result += " "
         End If
      Next
      Return result
   End Function
End Module
```

<span data-ttu-id="bf1ca-694">Aşağıda `NumericLib` ve `IsEven` olmak üzere iki üyesi olan bir `NearZero` sınıfını tanımlayan NumberUtil.cs için kaynak kodu verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-694">Here's the source code for NumberUtil.cs, which defines a `NumericLib` class that has two members, `IsEven` and `NearZero`.</span></span>

```csharp
using System;

public static class NumericLib
{
   public static bool IsEven(this IConvertible number)
   {
      if (number is Byte ||
          number is SByte ||
          number is Int16 ||
          number is UInt16 ||
          number is Int32 ||
          number is UInt32 ||
          number is Int64)
         return ((long) number) % 2 == 0;
      else if (number is UInt64)
         return ((ulong) number) %2 == 0;
      else
         throw new NotSupportedException("IsEven called for a non-integer value.");
   }

   public static bool NearZero(double number)
   {
      return number < .00001;
   }
}
```

<span data-ttu-id="bf1ca-695">İki sınıfı tek bir derlemede paketlemek için, bunları modüller halinde derlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-695">To package the two classes in a single assembly, you must compile them into modules.</span></span> <span data-ttu-id="bf1ca-696">Visual Basic kaynak kodunu bir modül olarak derlemek için bu komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="bf1ca-696">To compile the Visual Basic source code file into a module, use this command:</span></span>

```console
vbc /t:module StringUtil.vb
```

<span data-ttu-id="bf1ca-697">C# kaynak kodunu bir modül olarak derlemek için bu komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="bf1ca-697">To compile the C# source code file into a module, use this command:</span></span>

```console
csc /t:module NumberUtil.cs
```

<span data-ttu-id="bf1ca-698">Daha sonra, iki modülü bir derlemede derlemek için bağlantı aracını (LINK. exe) kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bf1ca-698">You then use the Link tool (Link.exe) to compile the two modules into an assembly:</span></span>

```console
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

<span data-ttu-id="bf1ca-699">Aşağıdaki örnek `NumericLib.NearZero` ve `StringLib.ToTitleCase` yöntemlerini çağırır.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-699">The following example then calls the `NumericLib.NearZero` and `StringLib.ToTitleCase` methods.</span></span> <span data-ttu-id="bf1ca-700">Hem Visual Basic kodunun hem de C# kodunun her iki sınıftaki yöntemlere erişebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bf1ca-700">Note that both the Visual Basic code and the C# code are able to access the methods in both classes.</span></span>

```csharp
using System;

public class Example
{
   public static void Main()
   {
      Double dbl = 0.0 - Double.Epsilon;
      Console.WriteLine(NumericLib.NearZero(dbl));

      string s = "war and peace";
      Console.WriteLine(s.ToTitleCase());
   }
}
// The example displays the following output:
//       True
//       War and Peace
```

```vb
Module Example
   Public Sub Main()
      Dim dbl As Double = 0.0 - Double.Epsilon
      Console.WriteLine(NumericLib.NearZero(dbl))

      Dim s As String = "war and peace"
      Console.WriteLine(s.ToTitleCase())
   End Sub
End Module
' The example displays the following output:
'       True
'       War and Peace
```

<span data-ttu-id="bf1ca-701">Visual Basic kodunu derlemek için bu komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="bf1ca-701">To compile the Visual Basic code, use this command:</span></span>

```console
vbc example.vb /r:UtilityLib.dll
```

<span data-ttu-id="bf1ca-702">C# ile derlemek için, derleyicinin adını vbc 'den CSC 'ye değiştirin ve dosya uzantısını. vb iken. cs olarak değiştirin:</span><span class="sxs-lookup"><span data-stu-id="bf1ca-702">To compile with C#, change the name of the compiler from vbc to csc, and change the file extension from .vb to .cs:</span></span>

```console
csc example.cs /r:UtilityLib.dll
```
