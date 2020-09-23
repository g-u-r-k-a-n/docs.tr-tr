---
title: -highentropyva
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
ms.openlocfilehash: 4d88c302281097fabd0eb361d60319bc8a0daf8d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058072"
---
# <a name="-highentropyva-visual-basic"></a><span data-ttu-id="ee450-102">-highentropyva (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee450-102">-highentropyva (Visual Basic)</span></span>

<span data-ttu-id="ee450-103">64 bitlik bir yürütülebilirin veya [-Platform: anycpu](platform.md) derleyici seçeneği tarafından işaretlenen bir yürütülebilir dosyanın yüksek Entroksiz adres alanı düzeni rastgele SEÇIMINI (ASLR) destekleyip desteklemediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee450-103">Indicates whether a 64-bit executable or an executable that's marked by the [-platform:anycpu](platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee450-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ee450-104">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ee450-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="ee450-105">Arguments</span></span>  

 <span data-ttu-id="ee450-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="ee450-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="ee450-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ee450-107">Optional.</span></span> <span data-ttu-id="ee450-108">Seçeneği varsayılan olarak veya öğesini belirtirseniz kapalıdır `-highentropyva-` .</span><span class="sxs-lookup"><span data-stu-id="ee450-108">The option is off by default or if you specify `-highentropyva-`.</span></span> <span data-ttu-id="ee450-109">Veya belirtirseniz seçeneği açık olur `-highentropyva` `-highentropyva+` .</span><span class="sxs-lookup"><span data-stu-id="ee450-109">The option is on if you specify `-highentropyva` or `-highentropyva+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee450-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ee450-110">Remarks</span></span>  

 <span data-ttu-id="ee450-111">Bu seçeneği belirtirseniz, Windows çekirdeğinin uyumlu sürümleri, çekirdek ASLR 'in bir parçası olarak bir işlemin adres alanı yerleşimini rasgele hale geldiğinde daha yüksek sayıda entropi kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="ee450-111">If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="ee450-112">Çekirdek daha yüksek bir entropi kullanıyorsa, yığınlar ve yığınlar gibi bellek bölgelerine daha fazla sayıda adres tahsis edilebilir.</span><span class="sxs-lookup"><span data-stu-id="ee450-112">If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="ee450-113">Sonuç olarak, belirli bir bellek bölgesinin konumunu tahmin etmek daha zordur.</span><span class="sxs-lookup"><span data-stu-id="ee450-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="ee450-114">Seçenek açık olduğunda, hedef yürütülebilir dosya ve bağımlı olduğu tüm modüller, bu modüller 64 bit işlem olarak çalışırken 4 gigabayttan (GB) büyük olan işaretçi değerlerini işleyebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="ee450-114">When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee450-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee450-115">See also</span></span>

- [<span data-ttu-id="ee450-116">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="ee450-116">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="ee450-117">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="ee450-117">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
