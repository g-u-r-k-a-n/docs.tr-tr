---
title: "'<membername>', devralınmış '<interfacename1>' ve '<interfacename2>' arabirimleri arasında belirsiz"
ms.date: 07/20/2015
f1_keywords:
- vbc30685
- bc30685
helpviewer_keywords:
- BC30685
ms.assetid: 756add7a-23d5-4b4f-a48d-8297d6459c73
ms.openlocfilehash: f666bf380f8b94c50c2bc5fd865b37d96e92991f
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162446"
---
# <a name="bc30685-membername-is-ambiguous-across-the-inherited-interfaces-interfacename1-and-interfacename2"></a><span data-ttu-id="9a7cb-102">BC30685: ' ' \<membername> , devralınmış ' \<interfacename1> ' ve ' ' arabirimleri arasında belirsiz \<interfacename2></span><span class="sxs-lookup"><span data-stu-id="9a7cb-102">BC30685: '\<membername>' is ambiguous across the inherited interfaces '\<interfacename1>' and '\<interfacename2>'</span></span>

<span data-ttu-id="9a7cb-103">Arabirim, birden çok arabirimden aynı ada sahip iki veya daha fazla üyeyi devralır.</span><span class="sxs-lookup"><span data-stu-id="9a7cb-103">The interface inherits two or more members with the same name from multiple interfaces.</span></span>

 <span data-ttu-id="9a7cb-104">**Hata kimliği:** BC30685</span><span class="sxs-lookup"><span data-stu-id="9a7cb-104">**Error ID:** BC30685</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="9a7cb-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="9a7cb-105">To correct this error</span></span>

- <span data-ttu-id="9a7cb-106">Değerini kullanmak istediğiniz temel arabirime atayın; Örneğin:</span><span class="sxs-lookup"><span data-stu-id="9a7cb-106">Cast the value to the base interface that you want to use; for example:</span></span>

    ```vb
    Interface Left
        Sub MySub()
    End Interface

    Interface Right
        Sub MySub()
    End Interface

    Interface LeftRight
        Inherits Left, Right
    End Interface

    Module test
        Sub Main()
            Dim x As LeftRight
            ' x.MySub()  'x is ambiguous.
            CType(x, Left).MySub() ' Cast to base type.
            CType(x, Right).MySub() ' Call the other base type.
        End Sub
    End Module
    ```

## <a name="see-also"></a><span data-ttu-id="9a7cb-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a7cb-107">See also</span></span>

- [<span data-ttu-id="9a7cb-108">Arabirimler</span><span class="sxs-lookup"><span data-stu-id="9a7cb-108">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
