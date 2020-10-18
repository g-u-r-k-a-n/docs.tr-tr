---
title: "'<typename1>' türünün değeri '<typename2>' olarak değiştirilemez"
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: a4aab83fd5695633a660eab00a5032ffbe45f326
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161328"
---
# <a name="bc30955-value-of-type-typename1-cannot-be-converted-to-typename2"></a><span data-ttu-id="ac787-102">BC30955: ' ' türünün değeri \<typename1> ' ' olarak dönüştürülemez \<typename2></span><span class="sxs-lookup"><span data-stu-id="ac787-102">BC30955: Value of type '\<typename1>' cannot be converted to '\<typename2>'</span></span>

<span data-ttu-id="ac787-103">' ' Türünün değeri \<typename1> ' ' olarak dönüştürülemez \<typename2> .</span><span class="sxs-lookup"><span data-stu-id="ac787-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="ac787-104">Tür uyumsuzluğu, ' ' derlemesine bir proje başvurusuyla bir dosya başvurusunun karıştırılması nedeniyle olabilir \<assemblyname> .</span><span class="sxs-lookup"><span data-stu-id="ac787-104">Type mismatch could be due to the mixing of a file reference with a project reference to assembly '\<assemblyname>'.</span></span> <span data-ttu-id="ac787-105">' ' Projesindeki ' ' adlı dosya başvurusunu ' ' \<filepath> \<projectname1> için bir proje başvurusuyla değiştirmeyi deneyin \<projectname2> .</span><span class="sxs-lookup"><span data-stu-id="ac787-105">Try replacing the file reference to '\<filepath>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>

 <span data-ttu-id="ac787-106">Bir projenin hem bir proje başvurusu hem de bir dosya başvurusu yaptığı durumlarda, derleyici bir türün diğerine dönüştürülebileceğini garanti edemez.</span><span class="sxs-lookup"><span data-stu-id="ac787-106">In a situation where a project makes both a project reference and a file reference, the compiler cannot guarantee that one type can be converted to another.</span></span>

 <span data-ttu-id="ac787-107">Aşağıdaki sözde kod, bu hatayı oluşturabilecek bir durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac787-107">The following pseudo-code illustrates a situation that can generate this error.</span></span>

 `' ================ Visual Basic project P1 ================`

 `'        P1 makes a PROJECT REFERENCE to project P2`

 `'        and a FILE REFERENCE to project P3.`

 `Public commonObject As P3.commonClass`

 `commonObject = P2.getCommonClass()`

 `' ================ Visual Basic project P2 ================`

 `'        P2 makes a PROJECT REFERENCE to project P3`

 `Public Function getCommonClass() As P3.commonClass`

 `Return New P3.commonClass`

 `End Function`

 `' ================ Visual Basic project P3 ================`

 `Public Class commonClass`

 `End Class`

 <span data-ttu-id="ac787-108">Project `P1` , proje aracılığıyla dolaylı bir proje başvurusunu `P2` `P3` ve ayrıca öğesine doğrudan bir dosya başvurusu yapar `P3` .</span><span class="sxs-lookup"><span data-stu-id="ac787-108">Project `P1` makes an indirect project reference through project `P2` to project `P3`, and also a direct file reference to `P3`.</span></span> <span data-ttu-id="ac787-109">Bildirimi, için `commonObject` Dosya başvurusunu kullanır `P3` , ancak öğesine yapılan çağrı, `P2.getCommonClass` proje başvurusunu kullanır `P3` .</span><span class="sxs-lookup"><span data-stu-id="ac787-109">The declaration of `commonObject` uses the file reference to `P3`, while the call to `P2.getCommonClass` uses the project reference to `P3`.</span></span>

 <span data-ttu-id="ac787-110">Bu durumda, dosya başvurusunun çıkış dosyası (genellikle p3.dll) için bir dosya yolu ve adı ve proje, proje `P3` adına göre kaynak projeyi ( `P3` ) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ac787-110">The problem in this situation is that the file reference specifies a file path and name for the output file of `P3` (typically p3.dll), while the project references identify the source project (`P3`) by project name.</span></span> <span data-ttu-id="ac787-111">Bu nedenle, derleyici türün `P3.commonClass` iki farklı başvuru aracılığıyla aynı kaynak kodundan geldiğini garanti edemez.</span><span class="sxs-lookup"><span data-stu-id="ac787-111">Because of this, the compiler cannot guarantee that the type `P3.commonClass` comes from the same source code through the two different references.</span></span>

 <span data-ttu-id="ac787-112">Bu durum genellikle proje başvuruları ve dosya başvuruları karmaysa oluşur.</span><span class="sxs-lookup"><span data-stu-id="ac787-112">This situation typically occurs when project references and file references are mixed.</span></span> <span data-ttu-id="ac787-113">Önceki çizimde, `P1` `P3` bir dosya başvurusu yerine öğesine doğrudan proje başvurusu yapıldıysa sorun oluşmaz.</span><span class="sxs-lookup"><span data-stu-id="ac787-113">In the preceding illustration, the problem would not occur if `P1` made a direct project reference to `P3` instead of a file reference.</span></span>

 <span data-ttu-id="ac787-114">**Hata kimliği:** BC30955</span><span class="sxs-lookup"><span data-stu-id="ac787-114">**Error ID:** BC30955</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ac787-115">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="ac787-115">To correct this error</span></span>

- <span data-ttu-id="ac787-116">Dosya başvurusunu bir proje başvurusuyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ac787-116">Change the file reference to a project reference.</span></span>

## <a name="see-also"></a><span data-ttu-id="ac787-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac787-117">See also</span></span>

- [<span data-ttu-id="ac787-118">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="ac787-118">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="ac787-119">Bir projedeki başvuruları yönetme</span><span class="sxs-lookup"><span data-stu-id="ac787-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
