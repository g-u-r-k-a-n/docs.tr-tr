---
description: "Daha fazla bilgi edinin: BC30007: <assemblyname> ' ' temel sınıfını içeren ' ' derlemesine başvuru gereklidir <classname>"
title: "'<assemblyname>' temel sınıfını içeren '<classname>' derlemesine başvuru gereklidir"
ms.date: 07/20/2015
f1_keywords:
- bc30007
- vbc30007
helpviewer_keywords:
- BC30007
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
ms.openlocfilehash: e6d4cf660453078d9a0f9825bc81bb990c1f55b9
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100456893"
---
# <a name="bc30007-reference-required-to-assembly-assemblyname-containing-the-base-class-classname"></a>BC30007: \<assemblyname> ' ' temel sınıfını içeren ' ' derlemesine başvuru gerekiyor \<classname>

' ' \<assemblyname> Temel sınıfını içeren ' ' derlemesine başvuru gerekiyor \<classname> . Projenize bir tane ekleyin.

 Sınıfı, projenizde doğrudan başvurulmayan bir dinamik bağlantı kitaplığı (DLL) veya bütünleştirilmiş kodda tanımlanır. Visual Basic derleyici, sınıfın birden fazla DLL veya derlemede tanımlanması durumunda belirsizlik olmaması için bir başvuru gerektirir.

 **Hata kimliği:** BC30007

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Başvurulmayan DLL veya derlemenin adını Proje başvurularında ekleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project)
- [Bozuk Başvurularda Sorun Giderme](/visualstudio/ide/troubleshooting-broken-references)
