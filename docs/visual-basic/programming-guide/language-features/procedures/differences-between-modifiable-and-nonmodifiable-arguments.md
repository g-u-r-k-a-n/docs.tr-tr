---
description: 'Daha fazla bilgi: değiştirilebilir ve değiştirilemeyen bağımsız değişkenler arasındaki farklar (Visual Basic)'
title: Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: 8d83802b4b8830a17412fdef44eabd2e5b8a7f2d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472637"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a>Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar (Visual Basic)

Bir yordamı çağırdığınızda, genellikle bir veya daha fazla bağımsız değişken geçirin. Her bağımsız değişken temeldeki bir programlama öğesine karşılık gelir. Hem temel alınan öğeler hem de bağımsız değişkenler değiştirilebilir ya da değiştirilebilir olabilir.  
  
## <a name="modifiable-and-nonmodifiable-elements"></a>Değiştirilebilir ve değiştirilemeyen öğeler  

 Bir programlama öğesi, değeri değişmiş olabilen *değiştirilebilir bir öğe* ya da oluşturulduktan sonra sabit bir değere sahip *değiştirilemeyen bir öğe* olabilir.  
  
 Aşağıdaki tabloda değiştirilebilir ve değiştirilemeyen programlama öğeleri listelenmektedir.  
  
|Değiştirilebilir öğeler|Değiştirilemeyen öğeler|  
|-------------------------|----------------------------|  
|Salt okunurdur hariç olmak üzere, nesne değişkenleri dahil olmak üzere yerel değişkenler (yordamlar içinde bildirilmiştir)|Salt okuma değişkenleri, alanları ve özellikleri|  
|Alanlar (modül, sınıf ve yapıların üye değişkenleri), salt okunurdur hariç|Sabitler ve sabit değerler|  
|Özellikler, salt okunurdur hariç|Listeleme üyeleri|  
|Dizi öğeleri|İfadeler (öğeleri değiştirilebilir olsa bile)|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a>Değiştirilebilir ve değiştirilemeyen bağımsız değişkenler  

 *Değiştirilebilir bir bağımsız değişken* değiştirilebilir bir temel öğe. Çağıran kod herhangi bir zamanda yeni bir değer saklayabilir ve [ByRef](../../../language-reference/modifiers/byref.md)bağımsız değişkenini geçirirseniz, yordamdaki kod, çağıran kodda temel alınan öğeyi de değiştirebilir.  
  
 *Değiştirilemeyen bir bağımsız değişken* , değiştirilemeyen temel olmayan bir öğeye sahiptir veya [ByVal](../../../language-reference/modifiers/byval.md)' a geçirilir. Yordam, değiştirilebilir bir öğe olsa bile, çağıran kodda temeldeki öğeyi değiştiremez. Değiştirilemeyen bir öğe ise, çağıran kodun kendisi üzerinde değişiklik yapılamaz.  
  
 Çağrılan yordam, değiştirilemeyen bir bağımsız değişkenin yerel kopyasını değiştirebilir, ancak bu değişiklik çağıran koddaki temeldeki öğeyi etkilemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme](./how-to-pass-arguments-to-a-procedure.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)
- [Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme](./how-to-change-the-value-of-a-procedure-argument.md)
- [Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme](./passing-arguments-by-position-and-by-name.md)
- [Değer türleri ve başvuru türleri](../data-types/value-types-and-reference-types.md)
