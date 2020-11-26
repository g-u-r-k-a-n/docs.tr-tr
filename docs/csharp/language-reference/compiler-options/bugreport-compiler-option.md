---
description: -bugreport (C# derleyici seçenekleri)
title: -bugreport (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 1fb2efc9b12680e95767746c7e4e1ddacbdd2594
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "93281512"
---
# <a name="-bugreport-c-compiler-options"></a><span data-ttu-id="e7045-103">-bugreport (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="e7045-103">-bugreport (C# Compiler Options)</span></span>

<span data-ttu-id="e7045-104">Hata ayıklama bilgilerinin daha sonra analiz edilmek üzere bir dosyaya yerleştirilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e7045-104">Specifies that debug information should be placed in a file for later analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7045-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e7045-105">Syntax</span></span>  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="e7045-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="e7045-106">Arguments</span></span>  

 `file`  
 <span data-ttu-id="e7045-107">Hata raporunuzu içermesini istediğiniz dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="e7045-107">The name of the file that you want to contain your bug report.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7045-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7045-108">Remarks</span></span>  

 <span data-ttu-id="e7045-109">**-Bugreport** seçeneği aşağıdaki bilgilerin yerleştirilmesi gerektiğini belirtir `file` :</span><span class="sxs-lookup"><span data-stu-id="e7045-109">The **-bugreport** option specifies that the following information should be placed in `file`:</span></span>  
  
- <span data-ttu-id="e7045-110">Derlemedeki tüm kaynak kodu dosyalarının bir kopyası.</span><span class="sxs-lookup"><span data-stu-id="e7045-110">A copy of all source code files in the compilation.</span></span>  
  
- <span data-ttu-id="e7045-111">Derlemede kullanılan derleyici seçeneklerinin bir listesi.</span><span class="sxs-lookup"><span data-stu-id="e7045-111">A listing of the compiler options used in the compilation.</span></span>  
  
- <span data-ttu-id="e7045-112">Derleyici, çalışma zamanı ve işletim sistemi ile ilgili sürüm bilgileri.</span><span class="sxs-lookup"><span data-stu-id="e7045-112">Version information about your compiler, run time, and operating system.</span></span>  
  
- <span data-ttu-id="e7045-113">Başvurulan derlemeler ve modüller, .NET ve .NET SDK ile gönderilen derlemeler hariç, onaltılık basamaklar olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="e7045-113">Referenced assemblies and modules, saved as hexadecimal digits, except assemblies that are shipped with .NET and the .NET SDK.</span></span>  
  
- <span data-ttu-id="e7045-114">Varsa derleyici çıkışı.</span><span class="sxs-lookup"><span data-stu-id="e7045-114">Compiler output, if any.</span></span>  
  
- <span data-ttu-id="e7045-115">Probleme için sizden sorulacak bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="e7045-115">A description of the problem, which you will be prompted for.</span></span>  
  
- <span data-ttu-id="e7045-116">Sorunun düzeltilmesi hakkında bir açıklama ve sizden istenir.</span><span class="sxs-lookup"><span data-stu-id="e7045-116">A description of how you think the problem should be fixed, which you will be prompted for.</span></span>  
  
 <span data-ttu-id="e7045-117">Bu seçenek **-errorreport: Prompt** veya **-errorreport: Send** ile kullanılırsa, dosyadaki bilgiler Microsoft Corporation 'a gönderilir.</span><span class="sxs-lookup"><span data-stu-id="e7045-117">If this option is used with **-errorreport:prompt** or **-errorreport:send**, the information in the file will be sent to Microsoft Corporation.</span></span>  
  
 <span data-ttu-id="e7045-118">Tüm kaynak kodu dosyalarının bir kopyası içine yerleştirilecek `file` , olası en kısa programda şüpheli kod hatasını yeniden oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7045-118">Because a copy of all source code files will be placed in `file`, you might want to reproduce the suspected code defect in the shortest possible program.</span></span>  
  
 <span data-ttu-id="e7045-119">Bu derleyici seçeneği Visual Studio 'da kullanılamaz ve program aracılığıyla değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="e7045-119">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
 <span data-ttu-id="e7045-120">Oluşturulan dosyanın içeriğinin, yanlışlıkla bilginin açığa çıkmasına neden olabilecek kaynak kodu kullanıma sunduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="e7045-120">Notice that contents of the generated file expose source code that could result in inadvertent information disclosure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7045-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7045-121">See also</span></span>

- [<span data-ttu-id="e7045-122">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e7045-122">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="e7045-123">-errorreport (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="e7045-123">-errorreport (C# Compiler Options)</span></span>](./errorreport-compiler-option.md)
- [<span data-ttu-id="e7045-124">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="e7045-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
