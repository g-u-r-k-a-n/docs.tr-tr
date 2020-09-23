---
title: 'Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: 2686a4d9dc10cde209f558771feeb5ba4f4ccb21
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075011"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a><span data-ttu-id="bac97-102">Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bac97-102">How to: Call a Procedure that Does Not Return a Value (Visual Basic)</span></span>

<span data-ttu-id="bac97-103">`Sub`Yordam, çağırma koduna bir değer döndürmez.</span><span class="sxs-lookup"><span data-stu-id="bac97-103">A `Sub` procedure does not return a value to the calling code.</span></span> <span data-ttu-id="bac97-104">Bunu tek başına çağırma ifadesiyle açıkça çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bac97-104">You call it explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="bac97-105">Bunu yalnızca bir ifade içinde adını kullanarak çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="bac97-105">You cannot call it by simply using its name within an expression.</span></span>  
  
### <a name="to-call-a-sub-procedure"></a><span data-ttu-id="bac97-106">Bir alt yordamı çağırmak için</span><span class="sxs-lookup"><span data-stu-id="bac97-106">To call a Sub procedure</span></span>  
  
1. <span data-ttu-id="bac97-107">Yordamın adını belirtin `Sub` .</span><span class="sxs-lookup"><span data-stu-id="bac97-107">Specify the name of the `Sub` procedure.</span></span>  
  
2. <span data-ttu-id="bac97-108">Bağımsız değişken listesini çevrelemek için, parantez ile yordam adını izleyin.</span><span class="sxs-lookup"><span data-stu-id="bac97-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="bac97-109">Bağımsız değişken yoksa, isteğe bağlı olarak ayraçları atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bac97-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="bac97-110">Ancak, parantezleri kullanmak kodunuzun okunmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="bac97-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="bac97-111">Bağımsız değişkenleri virgülle ayırarak parantez içindeki bağımsız değişken listesine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="bac97-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="bac97-112">Bağımsız değişkenleri `Sub` yordamın ilgili parametreleri tanımladığı sırada girdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="bac97-112">Be sure you supply the arguments in the same order that the `Sub` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="bac97-113">Aşağıdaki örnek, <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> bir uygulama penceresini etkinleştirmek için Visual Basic işlevini çağırır.</span><span class="sxs-lookup"><span data-stu-id="bac97-113">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> function to activate an application window.</span></span> <span data-ttu-id="bac97-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> pencere başlığını tek bağımsız değişkeni olarak alır.</span><span class="sxs-lookup"><span data-stu-id="bac97-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> takes the window title as its sole argument.</span></span> <span data-ttu-id="bac97-115">Çağıran koda bir değer döndürmez.</span><span class="sxs-lookup"><span data-stu-id="bac97-115">It does not return a value to the calling code.</span></span> <span data-ttu-id="bac97-116">Bir not defteri işlemi çalışmıyorsa, örnek bir oluşturur <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="bac97-116">If a Notepad process is not running, the example throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="bac97-117">`Shell`Yordam, uygulamaların belirtilen yollarda olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="bac97-117">The `Shell` procedure assumes the applications are in the paths specified.</span></span>  
  
     [!code-vb[VbVbalrCatRef#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCatRef/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="bac97-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bac97-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:System.ArgumentException>
- [<span data-ttu-id="bac97-119">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="bac97-119">Procedures</span></span>](./index.md)
- [<span data-ttu-id="bac97-120">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="bac97-120">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="bac97-121">Yordam Parametreleri ve Bağımsız Değişkenleri</span><span class="sxs-lookup"><span data-stu-id="bac97-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="bac97-122">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="bac97-122">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="bac97-123">Nasıl yapılır: Yordam Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bac97-123">How to: Create a Procedure</span></span>](./how-to-create-a-procedure.md)
- [<span data-ttu-id="bac97-124">Nasıl yapılır: Değer Döndüren Bir Yordam Çağırma</span><span class="sxs-lookup"><span data-stu-id="bac97-124">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="bac97-125">Nasıl yapılır: Olay İşleyicisi Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bac97-125">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
