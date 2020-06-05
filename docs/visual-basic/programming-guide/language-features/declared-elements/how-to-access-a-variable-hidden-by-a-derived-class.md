---
title: 'Nasıl yapılır: Türetilmiş Sınıf Tarafından Gizlenen Bir Değişkene Erişme'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: c5ff802a0f6e081acd00d7cdfab4a8296b4daad9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392863"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a><span data-ttu-id="edc7b-102">Nasıl yapılır: Türetilmiş Sınıf Tarafından Gizlenen Bir Değişkene Erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="edc7b-102">How to: Access a Variable Hidden by a Derived Class (Visual Basic)</span></span>

<span data-ttu-id="edc7b-103">Türetilmiş bir sınıftaki kod bir değişkene eriştiğinde, derleyici normal olarak en yakın erişilebilen sürüme (diğer bir deyişle, erişim sınıfından geri doğru olan erişilebilir sürüme) başvuruyu çözümler.</span><span class="sxs-lookup"><span data-stu-id="edc7b-103">When code in a derived class accesses a variable, the compiler normally resolves the reference to the closest accessible version, that is, the accessible version the fewest derivational steps backward from the accessing class.</span></span> <span data-ttu-id="edc7b-104">Değişken türetilmiş sınıfta tanımlanmışsa, kod normalde bu tanıma erişir.</span><span class="sxs-lookup"><span data-stu-id="edc7b-104">If the variable is defined in the derived class, the code normally accesses that definition.</span></span>

<span data-ttu-id="edc7b-105">Türetilmiş sınıf değişkeni, temel sınıftaki bir değişkeni göltiği takdirde, temel sınıf sürümünü gizler.</span><span class="sxs-lookup"><span data-stu-id="edc7b-105">If the derived class variable shadows a variable in the base class, it hides the base class version.</span></span> <span data-ttu-id="edc7b-106">Ancak, anahtar sözcüğü ile niteleyerek temel sınıf değişkenine erişebilirsiniz `MyBase` .</span><span class="sxs-lookup"><span data-stu-id="edc7b-106">However, you can access the base class variable by qualifying it with the `MyBase` keyword.</span></span>

### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a><span data-ttu-id="edc7b-107">Türetilmiş bir sınıf tarafından gizlenen bir taban sınıf değişkenine erişmek için</span><span class="sxs-lookup"><span data-stu-id="edc7b-107">To access a base class variable hidden by a derived class</span></span>

- <span data-ttu-id="edc7b-108">Bir ifade veya atama deyiminde, değişken adından önce `MyBase` anahtar sözcüğü ve nokta ( `.` ) koyun.</span><span class="sxs-lookup"><span data-stu-id="edc7b-108">In an expression or assignment statement, precede the variable name with the `MyBase` keyword and a period (`.`).</span></span>

    <span data-ttu-id="edc7b-109">Derleyici, değişkenin temel sınıf sürümüne başvuruyu çözer.</span><span class="sxs-lookup"><span data-stu-id="edc7b-109">The compiler resolves the reference to the base class version of the variable.</span></span>

    <span data-ttu-id="edc7b-110">Aşağıdaki örnek, devralma yoluyla gölgelendirmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="edc7b-110">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="edc7b-111">Biri, gölgeleme değişkenine erişen diğeri de gölgelendirmeyi atlayan iki başvuru yapar.</span><span class="sxs-lookup"><span data-stu-id="edc7b-111">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>

    ```vb
    Public Class shadowBaseClass
        Public shadowString As String = "This is the base class string."
    End Class
    Public Class shadowDerivedClass
        Inherits shadowBaseClass
        Public Shadows shadowString As String = "This is the derived class string."
        Public Sub showStrings()
            Dim s As String = "Unqualified shadowString: " & shadowString &
                vbCrLf & "MyBase.shadowString: " & MyBase.shadowString
            MsgBox(s)
        End Sub
    End Class
    ```

    <span data-ttu-id="edc7b-112">Önceki örnek, değişkeni `shadowString` temel sınıfta bildirir ve türetilmiş sınıfta gölgeleri.</span><span class="sxs-lookup"><span data-stu-id="edc7b-112">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="edc7b-113">`showStrings`Türetilmiş sınıftaki yordamda, ad uygun olmadığında dizenin gölgeleme sürümü görüntülenir `shadowString` .</span><span class="sxs-lookup"><span data-stu-id="edc7b-113">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="edc7b-114">Ardından, `shadowString` anahtar sözcüğü ile nitelendirilmeden gölgeli sürümü görüntüler `MyBase` .</span><span class="sxs-lookup"><span data-stu-id="edc7b-114">It then displays the shadowed version when `shadowString` is qualified with the `MyBase`  keyword.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="edc7b-115">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="edc7b-115">Robust Programming</span></span>

<span data-ttu-id="edc7b-116">Gölgelendirilmiş bir değişkenin istenmeyen bir sürümüne başvurma riskini azaltmak için, tüm başvuruları gölgelendirilmiş bir değişkene tamamen niteleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="edc7b-116">To lower the risk of referring to an unintended version of a shadowed variable, you can fully qualify all references to a shadowed variable.</span></span> <span data-ttu-id="edc7b-117">Gölgeleme aynı ada sahip bir değişkenin birden fazla sürümünü tanıtır.</span><span class="sxs-lookup"><span data-stu-id="edc7b-117">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="edc7b-118">Bir kod açıklaması değişken adına başvurduğunda, derleyicinin başvuruyu çözümleyen sürüm, kod ifadesinin konumu ve uygun bir dizenin varlığı gibi faktörlere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="edc7b-118">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="edc7b-119">Bu, değişkenin yanlış sürümüne başvurma riskini artırabilir.</span><span class="sxs-lookup"><span data-stu-id="edc7b-119">This can increase the risk of referring to the wrong version of the variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="edc7b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edc7b-120">See also</span></span>

- [<span data-ttu-id="edc7b-121">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="edc7b-121">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="edc7b-122">Visual Basic'de Gölgeleme</span><span class="sxs-lookup"><span data-stu-id="edc7b-122">Shadowing in Visual Basic</span></span>](shadowing.md)
- [<span data-ttu-id="edc7b-123">Gölgeleme ve Geçersiz Kılma Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="edc7b-123">Differences Between Shadowing and Overriding</span></span>](differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="edc7b-124">Nasıl yapılır: Değişkeninizle Aynı Adı Taşıyan Bir Değişkeni Gizleme</span><span class="sxs-lookup"><span data-stu-id="edc7b-124">How to: Hide a Variable with the Same Name as Your Variable</span></span>](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="edc7b-125">Nasıl yapılır: Devralınmış Değişkeni Gizleme</span><span class="sxs-lookup"><span data-stu-id="edc7b-125">How to: Hide an Inherited Variable</span></span>](how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="edc7b-126">Shadows</span><span class="sxs-lookup"><span data-stu-id="edc7b-126">Shadows</span></span>](../../../language-reference/modifiers/shadows.md)
- [<span data-ttu-id="edc7b-127">Geçersiz Kılmalar</span><span class="sxs-lookup"><span data-stu-id="edc7b-127">Overrides</span></span>](../../../language-reference/modifiers/overrides.md)
- [<span data-ttu-id="edc7b-128">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="edc7b-128">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="edc7b-129">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="edc7b-129">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
