---
title: "'Dir' işlevi önce bir 'PathName' bağımsız değişkeni ile çağrılmalıdır"
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 7f8191b0ef5452fcf6f3a20c3e0f28ca84ef9c4a
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163434"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a><span data-ttu-id="6697b-102">'Dir' işlevi önce bir 'PathName' bağımsız değişkeni ile çağrılmalıdır</span><span class="sxs-lookup"><span data-stu-id="6697b-102">'Dir' function must first be called with a 'PathName' argument</span></span>

<span data-ttu-id="6697b-103">İşlevin ilk çağrısı `Dir` `PathName` bağımsız değişkeni içermez.</span><span class="sxs-lookup"><span data-stu-id="6697b-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="6697b-104">İlk çağrısının `Dir` bir içermesi gerekir `PathName` , ancak `Dir` sonraki bir sonraki öğeyi almak için sonraki çağrıların parametreleri içermesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6697b-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="6697b-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="6697b-105">To correct this error</span></span>

- <span data-ttu-id="6697b-106">`PathName`İşlev çağrısında bir bağımsız değişken sağlayın.</span><span class="sxs-lookup"><span data-stu-id="6697b-106">Supply a `PathName` argument in the function call.</span></span>

## <a name="see-also"></a><span data-ttu-id="6697b-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6697b-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
