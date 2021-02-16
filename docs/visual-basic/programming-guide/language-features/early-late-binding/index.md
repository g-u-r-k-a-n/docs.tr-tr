---
description: 'Daha fazla bilgi edinin: erken ve geç bağlama (Visual Basic)'
title: Erken ve Geç Bağlama
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- objects [Visual Basic], late-bound
- objects [Visual Basic], early-bound
- objects [Visual Basic], late bound
- early binding [Visual Basic], Visual Basic compiler
- binding [Visual Basic], late and early
- objects [Visual Basic], early bound
- Visual Basic compiler, early and late binding
- late binding [Visual Basic]
- late binding [Visual Basic], Visual Basic compiler
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
ms.openlocfilehash: 1cdffe70035630ec56de04c54d7861283e1b5599
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475636"
---
# <a name="early-and-late-binding-visual-basic"></a><span data-ttu-id="ed6dd-103">Erken ve Geç Bağlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed6dd-103">Early and Late Binding (Visual Basic)</span></span>

<span data-ttu-id="ed6dd-104">Visual Basic derleyici bir nesne değişkenine bir nesne atandığında çağrılan bir işlem gerçekleştirir `binding` .</span><span class="sxs-lookup"><span data-stu-id="ed6dd-104">The Visual Basic compiler performs a process called `binding` when an object is assigned to an object variable.</span></span> <span data-ttu-id="ed6dd-105">Bir nesne, belirli bir nesne türü olarak belirtilen bir değişkene atandığında *erken bağlanır* .</span><span class="sxs-lookup"><span data-stu-id="ed6dd-105">An object is *early bound* when it is assigned to a variable declared to be of a specific object type.</span></span> <span data-ttu-id="ed6dd-106">Erken bağlantılı nesneler, derleyicinin bellek ayırmasını ve uygulama yürütmeden önce diğer iyileştirmeler gerçekleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed6dd-106">Early bound objects allow the compiler to allocate memory and perform other optimizations before an application executes.</span></span> <span data-ttu-id="ed6dd-107">Örneğin, aşağıdaki kod parçası türünde bir değişken bildirir <xref:System.IO.FileStream> :</span><span class="sxs-lookup"><span data-stu-id="ed6dd-107">For example, the following code fragment declares a variable to be of type <xref:System.IO.FileStream>:</span></span>  
  
 [!code-vb[VbVbalrOOP#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#90)]  
  
 <span data-ttu-id="ed6dd-108"><xref:System.IO.FileStream>, Belirli bir nesne türü olduğundan, öğesine atanan örnek erken bir şekilde `FS` bağlanır.</span><span class="sxs-lookup"><span data-stu-id="ed6dd-108">Because <xref:System.IO.FileStream> is a specific object type, the instance assigned to `FS` is early bound.</span></span>  
  
 <span data-ttu-id="ed6dd-109">Buna karşılık, bir nesne, türü olarak belirtilen bir değişkene atandığında *geç bağlanır* `Object` .</span><span class="sxs-lookup"><span data-stu-id="ed6dd-109">By contrast, an object is *late bound* when it is assigned to a variable declared to be of type `Object`.</span></span> <span data-ttu-id="ed6dd-110">Bu türdeki nesneler herhangi bir nesneye başvuruları tutabilir, ancak erken bağlantılı nesnelerin avantajlarından birçoğuna sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="ed6dd-110">Objects of this type can hold references to any object, but lack many of the advantages of early-bound objects.</span></span> <span data-ttu-id="ed6dd-111">Örneğin, aşağıdaki kod parçası, işlev tarafından döndürülen bir nesneyi tutacak bir nesne değişkeni bildirir `CreateObject` :</span><span class="sxs-lookup"><span data-stu-id="ed6dd-111">For example, the following code fragment declares an object variable to hold an object returned by the `CreateObject` function:</span></span>  
  
 [!code-vb[VbVbalrOOP#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/LateBinding.vb#91)]  
  
## <a name="advantages-of-early-binding"></a><span data-ttu-id="ed6dd-112">Erken bağlamanın avantajları</span><span class="sxs-lookup"><span data-stu-id="ed6dd-112">Advantages of Early Binding</span></span>  

 <span data-ttu-id="ed6dd-113">Derleyicinin daha verimli uygulamalar sunan önemli iyileştirmeler yapmasına izin verdiklerinden, mümkün olduğunda erken bağlanan nesneleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed6dd-113">You should use early-bound objects whenever possible, because they allow the compiler to make important optimizations that yield more efficient applications.</span></span> <span data-ttu-id="ed6dd-114">Erken bağlantılı nesneler, geç bağlantılı nesnelerden önemli ölçüde daha hızlıdır ve tam olarak hangi tür nesnelerin kullanıldığını belirterek kodunuzun okunmasını ve bakımını daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="ed6dd-114">Early-bound objects are significantly faster than late-bound objects and make your code easier to read and maintain by stating exactly what kind of objects are being used.</span></span> <span data-ttu-id="ed6dd-115">Erken bağlamanın bir diğer avantajı da, kodu düzenlerken Visual Studio tümleşik geliştirme ortamı (IDE) tam olarak ne tür bir nesne olduğunu belirleyebildiğinden otomatik kod tamamlama ve dinamik yardım gibi yararlı özelliklerden yararlanmasıdır.</span><span class="sxs-lookup"><span data-stu-id="ed6dd-115">Another advantage to early binding is that it enables useful features such as automatic code completion and Dynamic Help because the Visual Studio integrated development environment (IDE) can determine exactly what type of object you are working with as you edit the code.</span></span> <span data-ttu-id="ed6dd-116">Erken bağlama, bir program derlendiğinde derleyicinin hata raporlenmesini sağladığından, çalışma zamanı hatalarının sayısını ve önem derecesini azaltır.</span><span class="sxs-lookup"><span data-stu-id="ed6dd-116">Early binding reduces the number and severity of run-time errors because it allows the compiler to report errors when a program is compiled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ed6dd-117">Geç bağlama yalnızca, olarak belirtilen tür üyelerine erişmek için kullanılabilir `Public` .</span><span class="sxs-lookup"><span data-stu-id="ed6dd-117">Late binding can only be used to access type members that are declared as `Public`.</span></span> <span data-ttu-id="ed6dd-118">`Friend` `Protected Friend` Bir çalışma zamanı hatası olarak belirtilen üyelere erişme.</span><span class="sxs-lookup"><span data-stu-id="ed6dd-118">Accessing members declared as `Friend` or `Protected Friend` results in a run-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed6dd-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed6dd-119">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>
- [<span data-ttu-id="ed6dd-120">Nesne Ömrü: Nesneleri Oluşturma ve Yok Etme</span><span class="sxs-lookup"><span data-stu-id="ed6dd-120">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [<span data-ttu-id="ed6dd-121">Nesne Veri Türü</span><span class="sxs-lookup"><span data-stu-id="ed6dd-121">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
