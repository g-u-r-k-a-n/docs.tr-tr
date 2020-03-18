---
title: Örtülü olarak yazılan lambda ifadeleri
description: Lambda ifadesini bildirmek için neden örtülü olarak yazılan değişken bildirimi ni yazamayacağınızı öğrenin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: ef437ef961210290db4150a8a5cfb70e01aee958
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79145728"
---
# <a name="implicitly-typed-lambda-expressions"></a><span data-ttu-id="42777-103">Örtülü olarak yazılan lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="42777-103">Implicitly typed lambda expressions</span></span>

<span data-ttu-id="42777-104">Lambda ifadesini bildirmek için örtülü olarak yazılan değişken bildirimi kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="42777-104">You can't use an implicitly typed variable declaration to declare a lambda expression.</span></span>
<span data-ttu-id="42777-105">Derleyici için dairesel bir mantık sorunu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="42777-105">It creates a circular logic problem for the compiler.</span></span> <span data-ttu-id="42777-106">Bildirim, `var` derleyiciye atama işlecinin sağ tarafındaki ifade türünden değişkenin türünü belirlemesini söyler.</span><span class="sxs-lookup"><span data-stu-id="42777-106">The `var` declaration tells the compiler to figure out the type of the variable from the type of expression on the right hand side of the assignment operator.</span></span> <span data-ttu-id="42777-107">Lambda ifadesi derleme zaman türüne sahip değildir, ancak eşleşen herhangi bir temsilci veya ifade türüne dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="42777-107">A lambda expression does not have a compile time type, but is convertible to any matching delegate or expression type.</span></span> <span data-ttu-id="42777-108">Bir temsilci veya ifade türü değişkenine lambda ifadesini atadığınızda, derleyiciye lambda ifadesini 'atanan' değişkenin imzasına uyan bir ifadeye veya temsilciye dönüştürmeyi denemesini söylersiniz.</span><span class="sxs-lookup"><span data-stu-id="42777-108">When you assign a lambda expression to a variable of a delegate or expression type, you tell the compiler to try and convert the lambda expression into an expression or delegate that matches the signature of the 'assigned to' variable.</span></span> <span data-ttu-id="42777-109">Derleyici, atamanın sağ tarafındaki şeyi atamanın sol tarafındaki türle eşleştirmeye çalışmalıdır.</span><span class="sxs-lookup"><span data-stu-id="42777-109">The compiler must try to make the thing on the right hand side of the assignment match the type on the left hand side of the assignment.</span></span>

<span data-ttu-id="42777-110">Atamanın her iki tarafı da derleyiciye atama işlecinin diğer tarafındaki nesneye bakmasını ve türümün türümün eşleşip eşleşmeyeceğini görmesini söyleyemez.</span><span class="sxs-lookup"><span data-stu-id="42777-110">Both sides of the assignment can't be telling the compiler to look at the object on the other side of the assignment operator and see if my type matches.</span></span>

<span data-ttu-id="42777-111">C# dilinin bu davranışı neden belirttiği hakkında daha fazla bilgi bu [makaleyi](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) okuyarak (PDF indir) alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42777-111">You can get even more details on why the C# language specifies that behavior by reading [this article](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (PDF download).</span></span>
