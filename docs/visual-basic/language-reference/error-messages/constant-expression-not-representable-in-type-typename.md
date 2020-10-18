---
title: Sabit ifade '<typename>' türünde gösterilemez
ms.date: 07/20/2015
f1_keywords:
- bc30439
- vbc30439
helpviewer_keywords:
- BC30439
ms.assetid: 0a842906-3bc5-4946-8a37-3e3da883ef63
ms.openlocfilehash: e18f05c0d6a37ac4563b554d7ba943ba21131f85
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163174"
---
# <a name="bc30439-constant-expression-not-representable-in-type-typename"></a><span data-ttu-id="dd482-102">BC30439: sabit ifade ' ' türünde gösterilemez \<typename></span><span class="sxs-lookup"><span data-stu-id="dd482-102">BC30439: Constant expression not representable in type '\<typename>'</span></span>

<span data-ttu-id="dd482-103">Genellikle aralığı taşdığı için hedef türüne sığmayan bir sabiti değerlendirmeye çalışıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="dd482-103">You are trying to evaluate a constant that will not fit into the target type, usually because it is overflowing the range.</span></span>

 <span data-ttu-id="dd482-104">**Hata kimliği:** BC30439</span><span class="sxs-lookup"><span data-stu-id="dd482-104">**Error ID:** BC30439</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="dd482-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="dd482-105">To correct this error</span></span>

1. <span data-ttu-id="dd482-106">Hedef türünü, sabiti işleyebilen bir olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="dd482-106">Change the target type to one that can handle the constant.</span></span>

## <a name="see-also"></a><span data-ttu-id="dd482-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd482-107">See also</span></span>

- [<span data-ttu-id="dd482-108">Sabitlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="dd482-108">Constants Overview</span></span>](../../programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="dd482-109">Sabitler ve numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="dd482-109">Constants and Enumerations</span></span>](../constants-and-enumerations.md)
