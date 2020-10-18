---
title: <namespacename> kök ad alanındaki <fullnamespacename> adı CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
ms.openlocfilehash: 48e020cb74641279a4f402e47034514d78dfc4fc
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160216"
---
# <a name="bc40039-name-namespacename-in-the-root-namespace-fullnamespacename-is-not-cls-compliant"></a>BC40039: \<namespacename> kök ad alanındaki ad \<fullnamespacename> CLS uyumlu değil

Bir derleme olarak işaretlenir `<CLSCompliant(True)>` , ancak kök ad alanı adının bir öğesi bir alt çizgi () ile başlar `_` .

 Bir programlama öğesi bir veya daha fazla alt çizgi içerebilir, ancak [Dil bağımsızlığı ve Language-Independent bileşenleri](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu olmak için bir alt çizgiyle başlamamalıdır. Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).

 <xref:System.CLSCompliantAttribute>' I bir programlama öğesine uyguladığınızda, ya `isCompliant` da `True` `False` Uyumluluk veya uyumsuzluk olduğunu göstermek için özniteliğin parametresini veya olarak ayarlayın. Bu parametre için varsayılan yoktur ve bir değer belirtmeniz gerekir.

 <xref:System.CLSCompliantAttribute>Öğesini bir öğesine uygulamazsanız, uyumsuz olduğu kabul edilir.

 Bu ileti, varsayılan olarak bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).

 **Hata kimliği:** BC40039

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- CLS uyumluluğu gerekiyorsa, kök ad alanı adını değiştirerek öğelerinden hiçbiri alt çizgiyle başlamaktadır.

- Ad alanı adının değişmeden kalmasını gerektiriyorsa, <xref:System.CLSCompliantAttribute> derlemeyi derlemeden kaldırın veya olarak işaretleyin `<CLSCompliant(False)>` .

## <a name="see-also"></a>Ayrıca bkz.

- [Namespace Deyimi](../statements/namespace-statement.md)
- [Visual Basic'de Ad Alanları](../../programming-guide/program-structure/namespaces.md)
- [-rootnamespace](../../reference/command-line-compiler/rootnamespace.md)
- [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Bildirilen Öğe Adları](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [Visual Basic Adlandırma Kuralları](../../programming-guide/program-structure/naming-conventions.md)
