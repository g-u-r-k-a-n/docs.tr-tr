---
title: korumalı iç C# başvuru
ms.custom: seodec18
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 6e5a4c6e63c2c05df54df6bed542eab3f43f9272
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422580"
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="6b356-102">korumalı iç (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="6b356-102">protected internal (C# Reference)</span></span>

<span data-ttu-id="6b356-103">`protected internal` anahtar sözcük birleşimi bir üye erişim değiştiricisidir.</span><span class="sxs-lookup"><span data-stu-id="6b356-103">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="6b356-104">Korunan bir iç üyeye geçerli derlemeden veya kapsayan sınıftan türetilmiş türlerden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="6b356-104">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="6b356-105">Diğer erişim değiştiricilerine sahip `protected internal` bir karşılaştırması için bkz. [Erişilebilirlik düzeyleri](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="6b356-105">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="6b356-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="6b356-106">Example</span></span>

<span data-ttu-id="6b356-107">Bir temel sınıfın korunan iç üyesine, kendisini içeren derleme içindeki herhangi bir türden erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="6b356-107">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="6b356-108">Ayrıca, başka bir derlemede bulunan türetilmiş bir sınıfta, yalnızca erişim türetilmiş sınıf türünün bir değişkeniyle gerçekleşirse erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="6b356-108">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="6b356-109">Örneğin, aşağıdaki kod kesimini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="6b356-109">For example, consider the following code segment:</span></span>

```csharp
// Assembly1.cs
// Compile with: /target:library
public class BaseClass
{
   protected internal int myValue = 0;
}

class TestAccess
{
    void Access()
    {
        var baseObject = new BaseClass();
        baseObject.myValue = 5;
    }
}
```

```csharp
// Assembly2.cs
// Compile with: /reference:Assembly1.dll
class DerivedClass : BaseClass
{
    static void Main()
    {
        var baseObject = new BaseClass();
        var derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10;

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
}
```

<span data-ttu-id="6b356-110">Bu örnek, `Assembly1.cs` ve `Assembly2.cs`iki dosya içerir.</span><span class="sxs-lookup"><span data-stu-id="6b356-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="6b356-111">İlk dosya, `TestAccess`bir ortak temel sınıf, `BaseClass`ve başka bir sınıf içerir.</span><span class="sxs-lookup"><span data-stu-id="6b356-111">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="6b356-112">`BaseClass`, `TestAccess` türü tarafından erişilen korumalı bir dahili üyeye sahip `myValue`sahip.</span><span class="sxs-lookup"><span data-stu-id="6b356-112">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span>
<span data-ttu-id="6b356-113">İkinci dosyada, bir `BaseClass` örneği üzerinden `myValue` erişme girişimi bir hata üretir, bu üyeye türetilmiş bir sınıfın bir örneği aracılığıyla erişim elde edilir `DerivedClass` başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="6b356-113">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span>

<span data-ttu-id="6b356-114">Struct devralınamadığı için yapı üyeleri `protected internal` olamaz.</span><span class="sxs-lookup"><span data-stu-id="6b356-114">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6b356-115">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="6b356-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="6b356-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b356-116">See also</span></span>

- [<span data-ttu-id="6b356-117">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="6b356-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6b356-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6b356-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6b356-119">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="6b356-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6b356-120">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="6b356-120">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="6b356-121">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="6b356-121">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="6b356-122">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="6b356-122">Modifiers</span></span>](index.md)
- [<span data-ttu-id="6b356-123">public</span><span class="sxs-lookup"><span data-stu-id="6b356-123">public</span></span>](public.md)
- [<span data-ttu-id="6b356-124">private</span><span class="sxs-lookup"><span data-stu-id="6b356-124">private</span></span>](private.md)
- [<span data-ttu-id="6b356-125">internal</span><span class="sxs-lookup"><span data-stu-id="6b356-125">internal</span></span>](internal.md)
- <span data-ttu-id="6b356-126">[İç sanal anahtar sözcüklere yönelik güvenlik sorunları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6b356-126">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
