---
title: Arayüz üyeleri nasıl açıkça uygulanır - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: dff094aca237ed6146bd9b52813c40549bc99b9b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627791"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="f1cd9-102">Arayüz üyeleri açıkça nasıl uygulanır (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f1cd9-102">How to explicitly implement interface members (C# Programming Guide)</span></span>
<span data-ttu-id="f1cd9-103">Bu `IDimensions`örnek, [arabirim](../../language-reference/keywords/interface.md)üyelerini `GetLength` açıkça uygulayan bir arabirim ve bir `GetWidth`sınıf `Box`bildirir.</span><span class="sxs-lookup"><span data-stu-id="f1cd9-103">This example declares an [interface](../../language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `GetLength` and `GetWidth`.</span></span> <span data-ttu-id="f1cd9-104">Üyelere arayüz örneği `dimensions`üzerinden erişilir.</span><span class="sxs-lookup"><span data-stu-id="f1cd9-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1cd9-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1cd9-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="f1cd9-106">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="f1cd9-106">Robust Programming</span></span>  
  
- <span data-ttu-id="f1cd9-107">`Main` Derleme hataları oluşturabilecekleri için yöntemde aşağıdaki satırların yorumlandığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f1cd9-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="f1cd9-108">Açıkça uygulanan bir arabirim üyesine [bir sınıf](../../language-reference/keywords/class.md) örneğinden erişilemez:</span><span class="sxs-lookup"><span data-stu-id="f1cd9-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- <span data-ttu-id="f1cd9-109">Yöntemde `Main` aşağıdaki satırların, yöntemler arabirimin bir örneğinden çağrıldığı için kutunun boyutlarını başarıyla yazdırdığı na dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="f1cd9-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a><span data-ttu-id="f1cd9-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1cd9-110">See also</span></span>

- [<span data-ttu-id="f1cd9-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f1cd9-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f1cd9-112">Sınıflar ve Structs</span><span class="sxs-lookup"><span data-stu-id="f1cd9-112">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="f1cd9-113">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="f1cd9-113">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="f1cd9-114">İki arabirimin üyelerini açıkça uygulama</span><span class="sxs-lookup"><span data-stu-id="f1cd9-114">How to explicitly implement members of two interfaces</span></span>](./how-to-explicitly-implement-members-of-two-interfaces.md)
