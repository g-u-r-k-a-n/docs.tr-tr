---
description: "Hakkında daha fazla bilgi: ' Taksit_sayısı ' bağımsız değişkeni sıfırdan büyük olmalıdır"
title: "' Taksit_sayısı ' bağımsız değişkeni sıfırdan büyük olmalıdır"
ms.date: 07/20/2015
f1_keywords:
- vbrRate_NPerMustBeGTZero
ms.assetid: d49242df-dbd1-4b26-bd8c-ed56d24fdfcd
ms.openlocfilehash: ece5e775e2f05f757b2af53594c626f5a023161e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433414"
---
# <a name="argument-nper-must-be-greater-than-zero"></a><span data-ttu-id="d78d5-103">' Taksit_sayısı ' bağımsız değişkeni sıfırdan büyük olmalıdır</span><span class="sxs-lookup"><span data-stu-id="d78d5-103">Argument 'NPer' must be greater than zero</span></span>

<span data-ttu-id="d78d5-104">`NPer` `Double` Dönemsel sabit ödemeler ve sabit faiz oranına dayanan bir Anüite için dönem sayısını belirten işlevi, sıfırdan büyük bir bağımsız değişken gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d78d5-104">The `NPer` function, which returns a `Double` specifying the number of periods for an annuity based on periodic fixed payments and a fixed interest rate, requires an argument greater than zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d78d5-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d78d5-105">To correct this error</span></span>  
  
- <span data-ttu-id="d78d5-106">İfadedeki bağımsız değişkenlerin yazımını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d78d5-106">Check the spelling of arguments in the expression.</span></span> <span data-ttu-id="d78d5-107">Yanlış yazılmış bir değişken adı, sıfır olarak başlatılan bir sayısal değişkeni örtülü olarak oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="d78d5-107">A misspelled variable name can implicitly create a numeric variable that is initialized to zero.</span></span>  
  
- <span data-ttu-id="d78d5-108">Deyimdeki değişkenlerde, özellikle de diğer yordamlardan bağımsız değişken olarak geçirilen işlemler için önceki işlemleri denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d78d5-108">Check previous operations on variables in the expression, especially those passed into the procedure as arguments from other procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d78d5-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d78d5-109">See also</span></span>

- [<span data-ttu-id="d78d5-110">Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme</span><span class="sxs-lookup"><span data-stu-id="d78d5-110">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
