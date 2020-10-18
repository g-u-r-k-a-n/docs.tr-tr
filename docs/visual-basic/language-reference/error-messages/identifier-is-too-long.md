---
title: Tanımlayıcı çok uzun
ms.date: 07/20/2015
f1_keywords:
- bc30033
- vbc30033
helpviewer_keywords:
- BC30033
ms.assetid: 3d07f6d0-9a2f-49ca-94e8-1e354932e855
ms.openlocfilehash: eafcb2fdf706e12fa606a442ad577c88ed5a7427
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162862"
---
# <a name="bc30033-identifier-is-too-long"></a><span data-ttu-id="90336-102">BC30033: tanımlayıcı çok uzun</span><span class="sxs-lookup"><span data-stu-id="90336-102">BC30033: Identifier is too long</span></span>

<span data-ttu-id="90336-103">Her programlama öğesinin adı veya tanımlayıcı 1023 karakterle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="90336-103">The name, or identifier, of every programming element is limited to 1023 characters.</span></span> <span data-ttu-id="90336-104">Ayrıca, tam nitelikli ad 1023 karakterden uzun olamaz.</span><span class="sxs-lookup"><span data-stu-id="90336-104">In addition, a fully qualified name cannot exceed 1023 characters.</span></span> <span data-ttu-id="90336-105">Bu, tüm tanımlayıcı dizesinin ( `<namespace>.<...>.<namespace>.<class>.<element>` ), üye erişim işleci () karakterleri dahil 1023 karakterden uzun olamayacağı anlamına gelir `.` .</span><span class="sxs-lookup"><span data-stu-id="90336-105">This means that the entire identifier string (`<namespace>.<...>.<namespace>.<class>.<element>`) cannot be more than 1023 characters long, including the member-access operator (`.`) characters.</span></span>

 <span data-ttu-id="90336-106">**Hata kimliği:** BC30033</span><span class="sxs-lookup"><span data-stu-id="90336-106">**Error ID:** BC30033</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="90336-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="90336-107">To correct this error</span></span>

- <span data-ttu-id="90336-108">Tanımlayıcının uzunluğunu azaltın.</span><span class="sxs-lookup"><span data-stu-id="90336-108">Reduce the length of the identifier.</span></span>

## <a name="see-also"></a><span data-ttu-id="90336-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90336-109">See also</span></span>

- [<span data-ttu-id="90336-110">Bildirilen Öğe Adları</span><span class="sxs-lookup"><span data-stu-id="90336-110">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
