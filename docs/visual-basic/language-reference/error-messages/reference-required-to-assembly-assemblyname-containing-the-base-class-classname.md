---
title: "'<assemblyname>' temel sınıfını içeren '<classname>' derlemesine başvuru gereklidir"
ms.date: 07/20/2015
f1_keywords:
- bc30007
- vbc30007
helpviewer_keywords:
- BC30007
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
ms.openlocfilehash: 07c09d0dfcb374b974fbda9099c4e85d6d054753
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870908"
---
# <a name="reference-required-to-assembly-assemblyname-containing-the-base-class-classname"></a><span data-ttu-id="2e236-102">'\<assemblyname>' temel sınıfını içeren '\<classname>' derlemesine başvuru gereklidir</span><span class="sxs-lookup"><span data-stu-id="2e236-102">Reference required to assembly '\<assemblyname>' containing the base class '\<classname>'</span></span>

<span data-ttu-id="2e236-103">' ' \<assemblyname> Temel sınıfını içeren ' ' derlemesine başvuru gerekiyor \<classname> .</span><span class="sxs-lookup"><span data-stu-id="2e236-103">Reference required to assembly '\<assemblyname>' containing the base class '\<classname>'.</span></span> <span data-ttu-id="2e236-104">Projenize bir tane ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2e236-104">Add one to your project.</span></span>  
  
 <span data-ttu-id="2e236-105">Sınıfı, projenizde doğrudan başvurulmayan bir dinamik bağlantı kitaplığı (DLL) veya bütünleştirilmiş kodda tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="2e236-105">The class is defined in a dynamic-link library (DLL) or assembly that is not directly referenced in your project.</span></span> <span data-ttu-id="2e236-106">Visual Basic derleyici, sınıfın birden fazla DLL veya derlemede tanımlanması durumunda belirsizlik olmaması için bir başvuru gerektirir.</span><span class="sxs-lookup"><span data-stu-id="2e236-106">The Visual Basic compiler requires a reference to avoid ambiguity in case the class is defined in more than one DLL or assembly.</span></span>  
  
 <span data-ttu-id="2e236-107">**Hata kimliği:** BC30007</span><span class="sxs-lookup"><span data-stu-id="2e236-107">**Error ID:** BC30007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2e236-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="2e236-108">To correct this error</span></span>  
  
- <span data-ttu-id="2e236-109">Başvurulmayan DLL veya derlemenin adını Proje başvurularında ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2e236-109">Include the name of the unreferenced DLL or assembly in your project references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e236-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e236-110">See also</span></span>

- [<span data-ttu-id="2e236-111">Bir projedeki başvuruları yönetme</span><span class="sxs-lookup"><span data-stu-id="2e236-111">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="2e236-112">Bozuk Başvurularda Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="2e236-112">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
