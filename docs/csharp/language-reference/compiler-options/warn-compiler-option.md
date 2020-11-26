---
description: -warn (C# derleyici seçenekleri)
title: -warn (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /warn
helpviewer_keywords:
- warning level [C#]
- /w compiler option [C#]
- -w compiler option [C#]
- -warn compiler option [C#]
- /warn compiler option [C#]
- w compiler option [C#]
- warn compiler option [C#]
ms.custom: updateeachrelease
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
ms.openlocfilehash: d59274423e6f9844d3ab22f3ac513ba1a05d7f07
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "91171357"
---
# <a name="-warn-c-compiler-options"></a><span data-ttu-id="6a1b4-103">-warn (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="6a1b4-103">-warn (C# Compiler Options)</span></span>

<span data-ttu-id="6a1b4-104">**-Warn** seçeneği derleyicinin görüntüleyeceği uyarı düzeyini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a1b4-104">The **-warn** option specifies the warning level for the compiler to display.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a1b4-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6a1b4-105">Syntax</span></span>  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="6a1b4-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="6a1b4-106">Arguments</span></span>  

 `option`  
 <span data-ttu-id="6a1b4-107">Derleme için görüntülenmesini istediğiniz uyarı düzeyi: daha düşük sayılar yalnızca yüksek önem derecesine sahip uyarıları gösterir; daha yüksek numaralar daha fazla uyarı gösterir.</span><span class="sxs-lookup"><span data-stu-id="6a1b4-107">The warning level you want displayed for the compilation: Lower numbers show only high severity warnings; higher numbers show more warnings.</span></span> <span data-ttu-id="6a1b4-108">Değer sıfır veya pozitif bir tamsayı olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="6a1b4-108">The value must be zero or a positive integer:</span></span>

|<span data-ttu-id="6a1b4-109">Uyarı düzeyi</span><span class="sxs-lookup"><span data-stu-id="6a1b4-109">Warning level</span></span>|<span data-ttu-id="6a1b4-110">Anlamı</span><span class="sxs-lookup"><span data-stu-id="6a1b4-110">Meaning</span></span>|
|-------------------|-------------|
|<span data-ttu-id="6a1b4-111">0</span><span class="sxs-lookup"><span data-stu-id="6a1b4-111">0</span></span>|<span data-ttu-id="6a1b4-112">Tüm uyarı iletilerinin emisyonunu kapatır.</span><span class="sxs-lookup"><span data-stu-id="6a1b4-112">Turns off emission of all warning messages.</span></span>|
|<span data-ttu-id="6a1b4-113">1</span><span class="sxs-lookup"><span data-stu-id="6a1b4-113">1</span></span>|<span data-ttu-id="6a1b4-114">Ciddi uyarı iletileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6a1b4-114">Displays severe warning messages.</span></span>|  
|<span data-ttu-id="6a1b4-115">2</span><span class="sxs-lookup"><span data-stu-id="6a1b4-115">2</span></span>|<span data-ttu-id="6a1b4-116">Düzey 1 uyarılarını ve sınıf üyelerini gizleme hakkında uyarılar gibi bazı, daha az önemli uyarıları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6a1b4-116">Displays level 1 warnings plus certain, less-severe warnings, such as warnings about hiding class members.</span></span>|  
|<span data-ttu-id="6a1b4-117">3</span><span class="sxs-lookup"><span data-stu-id="6a1b4-117">3</span></span>|<span data-ttu-id="6a1b4-118">Düzey 2 uyarılarını ve her zaman veya olarak değerlendirme yapan ifadeler hakkında uyarılar gibi bazı, daha az önemli uyarıları görüntüler `true` `false` .</span><span class="sxs-lookup"><span data-stu-id="6a1b4-118">Displays level 2 warnings plus certain, less-severe warnings, such as warnings about expressions that always evaluate to `true` or `false`.</span></span>|  
|<span data-ttu-id="6a1b4-119">4 (varsayılan)</span><span class="sxs-lookup"><span data-stu-id="6a1b4-119">4 (the default)</span></span>|<span data-ttu-id="6a1b4-120">Tüm düzey 3 uyarılarını ve bilgilendirici uyarıları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6a1b4-120">Displays all level 3 warnings plus informational warnings.</span></span>|
|<span data-ttu-id="6a1b4-121">5</span><span class="sxs-lookup"><span data-stu-id="6a1b4-121">5</span></span>|<span data-ttu-id="6a1b4-122">4. düzey uyarıları ve C# 9,0 ile gönderilen derleyicinin [ek uyarılarını](https://github.com/dotnet/roslyn/blob/a6013f3213c902c0973b2d371c3007217d610533/docs/compilers/CSharp/Warnversion%20Warning%20Waves.md) görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6a1b4-122">Displays level 4 warnings plus [additional warnings](https://github.com/dotnet/roslyn/blob/a6013f3213c902c0973b2d371c3007217d610533/docs/compilers/CSharp/Warnversion%20Warning%20Waves.md) from the compiler shipped with C# 9.0.</span></span>|
|<span data-ttu-id="6a1b4-123">5 ' ten büyük</span><span class="sxs-lookup"><span data-stu-id="6a1b4-123">Greater than 5</span></span>|<span data-ttu-id="6a1b4-124">5 ' ten büyük bir değer 5 olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="6a1b4-124">Any value greater than 5 will be treated as 5.</span></span> <span data-ttu-id="6a1b4-125">Genellikle rastgele büyük bir değer (örneğin,), `9999` derleyici yeni uyarı düzeyleriyle güncelleştirilirse her zaman tüm uyarılara sahip olduğunuzdan emin olmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6a1b4-125">You generally put arbitrary large value (for example, `9999`) to make sure you always have all warnings if the compiler is updated with new warning levels.</span></span>|
  
## <a name="remarks"></a><span data-ttu-id="6a1b4-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a1b4-126">Remarks</span></span>  

 <span data-ttu-id="6a1b4-127">Bir hata veya uyarı hakkında bilgi almak için yardım dizinindeki hata kodunu arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6a1b4-127">To get information about an error or warning, you can look up the error code in the Help Index.</span></span> <span data-ttu-id="6a1b4-128">Bir hata veya uyarı hakkında bilgi almanın diğer yolları için bkz. [C# derleyici hataları](../compiler-messages/index.md).</span><span class="sxs-lookup"><span data-stu-id="6a1b4-128">For other ways to get information about an error or warning, see [C# Compiler Errors](../compiler-messages/index.md).</span></span>  
  
 <span data-ttu-id="6a1b4-129">Tüm uyarıları hata olarak değerlendirmek için [-warnaserror](./warnaserror-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="6a1b4-129">Use [-warnaserror](./warnaserror-compiler-option.md) to treat all warnings as errors.</span></span> <span data-ttu-id="6a1b4-130">Belirli uyarıları devre dışı bırakmak için [-nowarn](./nowarn-compiler-option.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="6a1b4-130">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
 <span data-ttu-id="6a1b4-131">**-w** , **-Warn** kısa biçimidir.</span><span class="sxs-lookup"><span data-stu-id="6a1b4-131">**-w** is the short form of **-warn**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="6a1b4-132">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="6a1b4-132">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="6a1b4-133">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="6a1b4-133">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="6a1b4-134">**Yapı** özelliği sayfasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="6a1b4-134">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="6a1b4-135">**Uyarı düzeyi** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6a1b4-135">Modify the **Warning Level** property.</span></span>  
  
 <span data-ttu-id="6a1b4-136">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A> ..</span><span class="sxs-lookup"><span data-stu-id="6a1b4-136">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a1b4-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="6a1b4-137">Example</span></span>  

 <span data-ttu-id="6a1b4-138">Derleyin `in.cs` ve derleyicinin yalnızca düzey 1 uyarılarını görüntülemesini sağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6a1b4-138">Compile `in.cs` and have the compiler only display level 1 warnings:</span></span>  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="6a1b4-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a1b4-139">See also</span></span>

- [<span data-ttu-id="6a1b4-140">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6a1b4-140">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="6a1b4-141">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="6a1b4-141">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
