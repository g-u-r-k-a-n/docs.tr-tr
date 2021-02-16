---
description: 'Hakkında daha fazla bilgi edinin: User-Defined sabitler (Visual Basic)'
title: Kullanıcı Tanımlı Sabitler
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: 290d4122249315ae3c6dc5e18ca4faefecb72044
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100485230"
---
# <a name="user-defined-constants-visual-basic"></a>Kullanıcı Tanımlı Sabitler (Visual Basic)

Sabit, değişmez bir sayının veya dizenin yerini alan anlamlı bir addır. Adın gösterdiği gibi sabitler depolama değerleri, bir uygulamanın yürütülmesi boyunca sabit kalır. Üzerinde çalıştığınız denetimler veya bileşenler tarafından tanımlanan sabitleri kullanabilir veya kendi kendinize de oluşturabilirsiniz. Kendi oluşturduğunuz sabitler *Kullanıcı tanımlı* olarak açıklanmaktadır.  
  
 `Const`Bir değişken adı oluşturmak için kullandığınız yönergeleri kullanarak ifadesiyle bir sabit değeri bildirirsiniz. `Option Strict`İse `On` , sabit türü açıkça bildirmeniz gerekir.  
  
## <a name="const-statement-usage"></a>Const deyimin kullanımı  

 Bir `Const` ifade matematiksel veya tarih/saat sayısını temsil edebilir:  
  
 [!code-vb[VbEnumsTask#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#10)]  
  
 Ayrıca, sabitleri tanımlayabilir `String` :  
  
 [!code-vb[VbEnumsTask#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#13)]  
  
 Eşittir işaretinin () sağ tarafındaki ifade `=` genellikle bir sayı veya sabit dizedir, ancak aynı zamanda sayı veya dize ile sonuçlanan bir ifade da olabilir (Bu ifade işlevlere çağrılar içeremez). Sabitleri, daha önce tanımlanmış sabitler bakımından bile tanımlayabilirsiniz:  
  
 [!code-vb[VbEnumsTask#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#15)]  
  
## <a name="scope-of-user-defined-constants"></a>User-Defined sabitleri kapsamı  

 Bir `Const` deyimin kapsamı aynı konumda bildirildiği bir değişkenle aynıdır. Kapsamı aşağıdaki yollarla belirtebilirsiniz:  
  
- Yalnızca bir yordamda var olan bir sabit oluşturmak için, bu yordamın içinde bildirin.  
  
- Bir sınıf içindeki tüm yordamlar için kullanılabilen, ancak bu modül dışındaki hiçbir koda yönelik bir sabit oluşturmak için, sınıfın Bildirimler bölümünde bildirin.  
  
- Bir derlemenin tüm üyeleri için kullanılabilen, ancak derlemenin dış istemcilerine yönelik bir sabit oluşturmak için, `Friend` sınıfının bildirimler bölümündeki anahtar sözcüğünü kullanarak bildirin.  
  
- Uygulama genelinde kullanılabilir bir sabit oluşturmak için, `Public` sınıfının bildirimler bölümündeki anahtar sözcüğünü kullanarak bildirin.  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: bir sabit bildirme](how-to-declare-a-constant.md).  
  
### <a name="avoiding-circular-references"></a>Döngüsel başvuruların kaçınma  

 Sabitler diğer sabitler açısından tanımlanabileceğinden, iki veya daha fazla sabitler arasında yanlışlıkla bir *döngü* veya döngüsel başvuru oluşturmak mümkündür. İki veya daha fazla ortak sabitiniz olduğunda, her biri diğeri farklı olduğunda, aşağıdaki örnekte olduğu gibi bir döngüden oluşur:  
  
 [!code-vb[VbEnumsTask#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#16)]  
[!code-vb[VbEnumsTask#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#17)]  
  
 Bir döngüyle karşılaşırsanız Visual Basic bir derleyici hatası oluşturur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Const Deyimi](../../../language-reference/statements/const-statement.md)
- [Sabit ve Değişmez Değerli Veri Türleri](constant-and-literal-data-types.md)
- [Sabitler ve numaralandırmalar](index.md)
- [Sabitler ve numaralandırmalar](../../../language-reference/constants-and-enumerations.md)
- [Sabit Listelerine Genel Bakış](enumerations-overview.md)
- [Sabitlere Genel Bakış](constants-overview.md)
- [Nasıl yapılır: numaralandırma bildirme](how-to-declare-enumerations.md)
- [Sabit Listeleri ve Ad Niteliği](enumerations-and-name-qualification.md)
- [Option Strict Deyimi](../../../language-reference/statements/option-strict-statement.md)
