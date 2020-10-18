---
title: İfade, içeren '<propertyname>' özelliğini tekrar tekrar çağırır
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: f5b8b226d46afa0555559de0930f20025ba27f2b
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162771"
---
# <a name="bc42026-expression-recursively-calls-the-containing-property-propertyname"></a><span data-ttu-id="d598e-102">BC42026: Ifade, kapsayan ' ' özelliğini yinelemeli olarak çağırıyor \<propertyname></span><span class="sxs-lookup"><span data-stu-id="d598e-102">BC42026: Expression recursively calls the containing property '\<propertyname>'</span></span>

<span data-ttu-id="d598e-103">`Set`Özellik tanımı yordamındaki bir ifade, özelliğin adına bir değer depolar.</span><span class="sxs-lookup"><span data-stu-id="d598e-103">A statement in the `Set` procedure of a property definition stores a value into the name of the property.</span></span>

 <span data-ttu-id="d598e-104">Bir özelliğin değerini tutmak için önerilen yaklaşım, `Private` özelliğin kapsayıcısında bir değişken tanımlamak ve hem hem de `Get` `Set` yordamlarında kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="d598e-104">The recommended approach to holding the value of a property is to define a `Private` variable in the property's container and use it in both the `Get` and `Set` procedures.</span></span> <span data-ttu-id="d598e-105">`Set`Yordamın bu değişkende gelen değeri depolaması gerekir `Private` .</span><span class="sxs-lookup"><span data-stu-id="d598e-105">The `Set` procedure should then store the incoming value in this `Private` variable.</span></span>

 <span data-ttu-id="d598e-106">`Get`Yordam, bir yordam gibi davranır `Function` , bu nedenle özellik adına bir değer atayabilir ve deyimden yararlanarak denetim getirebilirsiniz `End Get` .</span><span class="sxs-lookup"><span data-stu-id="d598e-106">The `Get` procedure behaves like a `Function` procedure, so it can assign a value to the property name and return control by encountering the `End Get` statement.</span></span> <span data-ttu-id="d598e-107">Ancak önerilen yaklaşım, `Private` değişkeni bir [Return ifadesine](../statements/return-statement.md)değer olarak dahil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d598e-107">The recommended approach, however, is to include the `Private` variable as the value in a [Return Statement](../statements/return-statement.md).</span></span>

 <span data-ttu-id="d598e-108">`Set`Yordam `Sub` , bir değer döndürmeyen bir yordam gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="d598e-108">The `Set` procedure behaves like a `Sub` procedure, which does not return a value.</span></span> <span data-ttu-id="d598e-109">Bu nedenle, yordam veya özellik adının bir yordam içinde özel bir anlamı yoktur `Set` ve buna bir değer depolayamezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d598e-109">Therefore, the procedure or property name has no special meaning within a `Set` procedure, and you cannot store a value into it.</span></span>

 <span data-ttu-id="d598e-110">Aşağıdaki örnekte, bu hataya neden olabilecek yaklaşım ve önerilen yaklaşım gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d598e-110">The following example illustrates the approach that can cause this error, followed by the recommended approach.</span></span>

```vb
Public Class illustrateProperties
' The code in the following property causes this error.
    Public Property badProp() As Char
        Get
            Dim charValue As Char
            ' Insert code to update charValue.
            badProp = charValue
        End Get
        Set(ByVal Value As Char)
            ' The following statement causes this error.
            badProp = Value
            ' The value stored in the local variable badProp
            ' is not used by the Get procedure in this property.
        End Set
    End Property
' The following code uses the recommended approach.
    Private propValue As Char
    Public Property goodProp() As Char
        Get
            ' Insert code to update propValue.
            Return propValue
        End Get
        Set(ByVal Value As Char)
            propValue = Value
        End Set
    End Property
End Class
```

 <span data-ttu-id="d598e-111">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="d598e-111">By default, this message is a warning.</span></span> <span data-ttu-id="d598e-112">Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için lütfen bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d598e-112">For more information about hiding warnings or treating warnings as errors, please see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="d598e-113">**Hata kimliği:** BC42026</span><span class="sxs-lookup"><span data-stu-id="d598e-113">**Error ID:** BC42026</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d598e-114">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d598e-114">To correct this error</span></span>

- <span data-ttu-id="d598e-115">Önceki örnekte gösterildiği gibi önerilen yaklaşımı kullanmak için özellik tanımını yeniden yazın.</span><span class="sxs-lookup"><span data-stu-id="d598e-115">Rewrite the property definition to use the recommended approach as illustrated in the preceding example.</span></span>

## <a name="see-also"></a><span data-ttu-id="d598e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d598e-116">See also</span></span>

- [<span data-ttu-id="d598e-117">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="d598e-117">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="d598e-118">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="d598e-118">Property Statement</span></span>](../statements/property-statement.md)
- [<span data-ttu-id="d598e-119">Set deyimleri</span><span class="sxs-lookup"><span data-stu-id="d598e-119">Set Statement</span></span>](../statements/set-statement.md)
