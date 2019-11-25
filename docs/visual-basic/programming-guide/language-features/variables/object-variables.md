---
title: Nesne Değişkenleri
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: 7eb860bc732f923316b8ce1d7b94ecdb368bfec3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351789"
---
# <a name="object-variables-in-visual-basic"></a><span data-ttu-id="51490-102">Visual Basic'de Nesne Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="51490-102">Object Variables in Visual Basic</span></span>

<span data-ttu-id="51490-103">In addition to storing values directly, a variable can refer to an object.</span><span class="sxs-lookup"><span data-stu-id="51490-103">In addition to storing values directly, a variable can refer to an object.</span></span> <span data-ttu-id="51490-104">You assign an object to a variable for the same reasons you assign any value to a variable:</span><span class="sxs-lookup"><span data-stu-id="51490-104">You assign an object to a variable for the same reasons you assign any value to a variable:</span></span>

- <span data-ttu-id="51490-105">A variable name is often shorter and easier to remember than the full path of methods and properties necessary to access the object itself.</span><span class="sxs-lookup"><span data-stu-id="51490-105">A variable name is often shorter and easier to remember than the full path of methods and properties necessary to access the object itself.</span></span>

- <span data-ttu-id="51490-106">Using a variable that refers to an object is more efficient than repeatedly accessing the object itself through the necessary methods or properties.</span><span class="sxs-lookup"><span data-stu-id="51490-106">Using a variable that refers to an object is more efficient than repeatedly accessing the object itself through the necessary methods or properties.</span></span>

- <span data-ttu-id="51490-107">You can change a variable to refer to other objects while your code is running.</span><span class="sxs-lookup"><span data-stu-id="51490-107">You can change a variable to refer to other objects while your code is running.</span></span>

## <a name="making-code-shorter"></a><span data-ttu-id="51490-108">Making Code Shorter</span><span class="sxs-lookup"><span data-stu-id="51490-108">Making Code Shorter</span></span>

<span data-ttu-id="51490-109">You can use object variables to shorten the code you have to type.</span><span class="sxs-lookup"><span data-stu-id="51490-109">You can use object variables to shorten the code you have to type.</span></span> <span data-ttu-id="51490-110">The following example uses the full path of methods and properties to access a <xref:System.Windows.Forms.Control> object.</span><span class="sxs-lookup"><span data-stu-id="51490-110">The following example uses the full path of methods and properties to access a <xref:System.Windows.Forms.Control> object.</span></span>

```vb
' Assume Me is a valid Form, or replace Me with a valid Form.
Me.ActiveForm.ActiveControl.Text = "Test"
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)
Me.ActiveForm.ActiveControl.Show()
```

<span data-ttu-id="51490-111">You can shorten this code, and speed up execution, if you use an object variable for the control.</span><span class="sxs-lookup"><span data-stu-id="51490-111">You can shorten this code, and speed up execution, if you use an object variable for the control.</span></span> <span data-ttu-id="51490-112">You should declare the object variable with the specific class that you intend to assign to it (`Control` in this case).</span><span class="sxs-lookup"><span data-stu-id="51490-112">You should declare the object variable with the specific class that you intend to assign to it (`Control` in this case).</span></span> <span data-ttu-id="51490-113">Once you assign an object to the variable, you can treat it exactly the same as you treat the object to which it refers.</span><span class="sxs-lookup"><span data-stu-id="51490-113">Once you assign an object to the variable, you can treat it exactly the same as you treat the object to which it refers.</span></span> <span data-ttu-id="51490-114">You can set or retrieve the properties of the object or use any of its methods.</span><span class="sxs-lookup"><span data-stu-id="51490-114">You can set or retrieve the properties of the object or use any of its methods.</span></span> <span data-ttu-id="51490-115">The following example uses an object variable to simplify the code in the preceding example.</span><span class="sxs-lookup"><span data-stu-id="51490-115">The following example uses an object variable to simplify the code in the preceding example.</span></span>

```vb
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl
ctrlActv.Text = "Test"
ctrlActv.Location = New Point(100, 100)
ctrlActv.Show()
```

## <a name="see-also"></a><span data-ttu-id="51490-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51490-116">See also</span></span>

- [<span data-ttu-id="51490-117">Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="51490-117">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="51490-118">Nasıl yapılır: Uzun Bir Nitelenmiş Yola Sahip Nesneye Erişimi Hızlandırma</span><span class="sxs-lookup"><span data-stu-id="51490-118">How to: Speed Up Access to an Object with a Long Qualification Path</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [<span data-ttu-id="51490-119">Nesne Değişken Bildirimi</span><span class="sxs-lookup"><span data-stu-id="51490-119">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="51490-120">Nesne Değişkeni Ataması</span><span class="sxs-lookup"><span data-stu-id="51490-120">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="51490-121">Nesne Değişkeni Değerleri</span><span class="sxs-lookup"><span data-stu-id="51490-121">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
