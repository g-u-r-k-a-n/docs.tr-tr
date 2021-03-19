---
title: CorFlags.exe (CorFlags Dönüştürme Aracı)
description: CorFlags dönüştürme aracı CorFlags.exe anlayın. Bu araç taşınabilir bir yürütülebilir görüntünün üst bilgisinin CorFlags bölümünü yapılandırmanızı sağlar.
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
ms.openlocfilehash: 2b801ba28e0513c899123daa98fd649cbc3d9c28
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104654173"
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="958ee-104">CorFlags.exe (CorFlags Dönüştürme Aracı)</span><span class="sxs-lookup"><span data-stu-id="958ee-104">CorFlags.exe (CorFlags Conversion Tool)</span></span>

<span data-ttu-id="958ee-105">CorFlags Dönüştürme aracı, taşınabilir çalıştırılabilir bir görüntünün üstbilgisinin CorFlags bölümünü yapılandırmanıza olanak verir.</span><span class="sxs-lookup"><span data-stu-id="958ee-105">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="958ee-106">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="958ee-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="958ee-107">Aracı çalıştırmak için [Visual studio Geliştirici komut istemi veya Visual Studio Geliştirici PowerShell](/visualstudio/ide/reference/command-prompt-powershell)kullanın.</span><span class="sxs-lookup"><span data-stu-id="958ee-107">To run the tool, use [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span>  
  
 <span data-ttu-id="958ee-108">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="958ee-108">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="958ee-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="958ee-109">Syntax</span></span>  
  
```console  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="958ee-110">Parametreler</span><span class="sxs-lookup"><span data-stu-id="958ee-110">Parameters</span></span>  
  
|<span data-ttu-id="958ee-111">Gerekli parametre</span><span class="sxs-lookup"><span data-stu-id="958ee-111">Required parameter</span></span>|<span data-ttu-id="958ee-112">Description</span><span class="sxs-lookup"><span data-stu-id="958ee-112">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="958ee-113">CorFlags'in yapılandırılacağı derlemenin adı.</span><span class="sxs-lookup"><span data-stu-id="958ee-113">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="958ee-114">Seçenek</span><span class="sxs-lookup"><span data-stu-id="958ee-114">Option</span></span>|<span data-ttu-id="958ee-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="958ee-115">Description</span></span>|  
|:------------|-----------------|  
|`-32BIT[REQ]+`|<span data-ttu-id="958ee-116">32BITREQUIRED bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="958ee-116">Sets the 32BITREQUIRED flag.</span></span>|  
|`-32BIT[REQ]-`|<span data-ttu-id="958ee-117">32BITREQUIRED bayrağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="958ee-117">Clears the 32BITREQUIRED flag.</span></span>|  
|`-32BITPREF+`|<span data-ttu-id="958ee-118">32BITPREFERRED bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="958ee-118">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="958ee-119">Uygulama 64-bit platformlarda dahi 32-bit işlem olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="958ee-119">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="958ee-120">Bu bayrağı yalnızca EXE dosyalarında ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="958ee-120">Set this flag only on EXE files.</span></span> <span data-ttu-id="958ee-121">Bayrak DLL üzerinde ayarlandıysa, DLL 64-bit işlemlerde yüklenemez ve bir <xref:System.BadImageFormatException> özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="958ee-121">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="958ee-122">Bu bayrağı içeren bir EXE dosyası bir 64-bit işleme yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="958ee-122">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="958ee-123">.NET Framework 4,5 ' de yenidir.</span><span class="sxs-lookup"><span data-stu-id="958ee-123">New in the .NET Framework 4.5.</span></span>|  
|`-32BITPREF-`|<span data-ttu-id="958ee-124">32BITPREFERRED bayrağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="958ee-124">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="958ee-125">.NET Framework 4,5 ' de yenidir.</span><span class="sxs-lookup"><span data-stu-id="958ee-125">New in the .NET Framework 4.5.</span></span>|  
|`-?`|<span data-ttu-id="958ee-126">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="958ee-126">Displays command syntax and options for the tool.</span></span>|  
|`-Force`|<span data-ttu-id="958ee-127">Derleme bir tanımlayıcı adla adlandırılmış olsa da bir güncelleştirmenin yapılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="958ee-127">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="958ee-128">**Önemli:**  Tanımlayıcı adlı bir derlemeyi güncelleştirirseniz kodu yürütmeden önce yeniden imzalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="958ee-128">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|`-help`|<span data-ttu-id="958ee-129">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="958ee-129">Displays command syntax and options for the tool.</span></span>|  
|`-ILONLY+`|<span data-ttu-id="958ee-130">ILONLY bayrağını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="958ee-130">Sets the ILONLY flag.</span></span>|  
|`-ILONLY-`|<span data-ttu-id="958ee-131">ILONLY bayrağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="958ee-131">Clears the ILONLY flag.</span></span>|  
|`-nologo`|<span data-ttu-id="958ee-132">Microsoft başlangıç başlığı görüntüsünü bastırır.</span><span class="sxs-lookup"><span data-stu-id="958ee-132">Suppresses the Microsoft startup banner display.</span></span>|  
|`-RevertCLRHeader`|<span data-ttu-id="958ee-133">CLR üstbilgisini 2.0 sürümüne döndürür.</span><span class="sxs-lookup"><span data-stu-id="958ee-133">Reverts the CLR header version to 2.0.</span></span>|  
|`-UpgradeCLRHeader`|<span data-ttu-id="958ee-134">CLR üstbilgisini 2.5 sürümüne yükseltir.</span><span class="sxs-lookup"><span data-stu-id="958ee-134">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="958ee-135">**Note:**  Derlemeler yerel olarak çalıştırmak için 2,5 veya daha büyük bir CLR üstbilgi sürümüne sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="958ee-135">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="958ee-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="958ee-136">Remarks</span></span>  

 <span data-ttu-id="958ee-137">Hiçbir seçenek belirtilmezse, CorFlags Dönüştürme aracı belirtilen derleme için bayrakları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="958ee-137">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="958ee-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="958ee-138">See also</span></span>

- [<span data-ttu-id="958ee-139">Araçlar</span><span class="sxs-lookup"><span data-stu-id="958ee-139">Tools</span></span>](index.md)
- [<span data-ttu-id="958ee-140">64 bit Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="958ee-140">64-bit Applications</span></span>](../64-bit-apps.md)
- [<span data-ttu-id="958ee-141">Geliştirici komut satırı kabukları</span><span class="sxs-lookup"><span data-stu-id="958ee-141">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
