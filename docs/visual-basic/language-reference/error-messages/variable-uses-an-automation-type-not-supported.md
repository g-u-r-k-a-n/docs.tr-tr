---
title: Değişken, desteklenmeyen bir Otomasyon türünü kullanıyor
ms.date: 07/20/2015
f1_keywords:
- vbrID458
ms.assetid: bde4f4da-493b-452c-b6e4-1d370edba4cd
ms.openlocfilehash: 944c0c63cd0d7ae7f9ff770fd123231464af1eaf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344837"
---
# <a name="variable-uses-an-automation-type-not-supported-in-visual-basic"></a><span data-ttu-id="5d8bd-102">Değişken, Visual Basic'de desteklenmeyen bir Otomasyon türünü kullanıyor</span><span class="sxs-lookup"><span data-stu-id="5d8bd-102">Variable uses an Automation type not supported in Visual Basic</span></span>

<span data-ttu-id="5d8bd-103">Visual Basic tarafından desteklenmeyen bir veri türüne sahip bir tür kitaplığında veya nesne kitaplığında tanımlanan bir değişken kullanmayı denediniz.</span><span class="sxs-lookup"><span data-stu-id="5d8bd-103">You tried to use a variable defined in a type library or object library that has a data type not supported by Visual Basic.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="5d8bd-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="5d8bd-104">To correct this error</span></span>

- <span data-ttu-id="5d8bd-105">Visual Basic tarafından tanınan bir tür değişkeni kullanın.</span><span class="sxs-lookup"><span data-stu-id="5d8bd-105">Use a variable of a type recognized by Visual Basic.</span></span>

     <span data-ttu-id="5d8bd-106">veya</span><span class="sxs-lookup"><span data-stu-id="5d8bd-106">-or-</span></span>

- <span data-ttu-id="5d8bd-107">`FileGet` veya `FileGetObject`kullanırken bu hatayla karşılaşırsanız, kullanmaya çalıştığınız dosyanın `FilePut` veya `FilePutObject`ile yazıldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="5d8bd-107">If you encounter this error while using `FileGet` or `FileGetObject`, make sure the file you are trying to use was written to with `FilePut` or `FilePutObject`.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d8bd-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d8bd-108">See also</span></span>

- [<span data-ttu-id="5d8bd-109">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="5d8bd-109">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
