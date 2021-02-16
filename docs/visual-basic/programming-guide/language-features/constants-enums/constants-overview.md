---
description: 'Daha fazla bilgi edinin: sabitlere genel bakış (Visual Basic)'
title: Sabitlere Genel Bakış
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic]
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
ms.openlocfilehash: af5a64339c04306538fe1b9dc195a044aa89ab9f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475454"
---
# <a name="constants-overview-visual-basic"></a>Sabitlere Genel Bakış (Visual Basic)

Sabit, değişmez bir sayının veya dizenin yerini alan anlamlı bir addır. Adın gösterdiği gibi sabitler depolama değerleri, uygulamanın yürütülmesi boyunca aynı kalır. Kodunuzun okunabilirliğini büyük ölçüde geliştirebilirsiniz ve sabitleri kullanarak daha kolay koruma sağlayabilirsiniz. Bunları yeniden görüntülenen veya belirgin bir anlamı olmayan belirli numaralara bağlı olan değerleri içeren kodda kullanın.  
  
## <a name="how-to-create-and-use-constants"></a>Sabitleri oluşturma ve kullanma  

 Visual Basic, genellikle yazdırma ve görüntüleme için kullanılan bir dizi önceden tanımlanmış sabitler içerir. Ayrıca, `Const` bir değişken adı oluşturmak için kullandığınız yönergeleri kullanarak deyimle kendi sabitlerinizi de oluşturabilirsiniz. `Option Strict`İse `On` , sabit türü açıkça bildirmeniz gerekir.  
  
 Bir sabitin, adını nitelemeden kendisine başvurabilen tüm kod kümesi, aynı konumda bildirildiği değişkenle aynı. Belirli bir yordamın kapsamında var olan bir sabit oluşturmak için, bu yordamın içinde bildirin. Bir uygulamanın tamamında kullanılabilir bir sabit oluşturmak için, `Public` sınıfının bildirimler bölümündeki anahtar sözcüğünü kullanarak bunu bildirin.  
  
> [!NOTE]
> Sabitler değişkenlere benzer olsa da, değişkenleri değiştiremeyeceğiniz sürece bunları değiştiremez veya yeni değerler atayamazsınız.  
  
 Kodunuzda kullandığınız sabitler, birlikte çalıştığınız denetimler veya bileşenler için nesne modeli tarafından tanımlanabilir veya Kullanıcı tanımlı (diğer bir deyişle, sizin oluşturduğunuz) olabilir.  
  
## <a name="compile-time-and-run-time-constants"></a>Derleme zamanı ve çalışma zamanı sabitleri  

 Derleme zamanı sabiti, kodun derlenmesi sırasında hesaplanır, ancak bir çalışma zamanı sabiti yalnızca uygulama çalışırken hesaplanabilir. Bir derleme zamanı sabiti her seferinde aynı değere sahip olacaktır, ancak bir çalışma zamanı sabiti her seferinde değişebilir. Dizi sınırları, Case ifadeleri veya Numaralandırıcı başlatıcıları gibi durumlar için derleme zamanı sabitleri gereklidir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|Tanım|Süre|  
|---|---|  
|[Nasıl yapılır: Bir Sabit Bildirme](how-to-declare-a-constant.md)|Bir sabiti `Const` bildirmek ve değerini ayarlamak için ifadesinin nasıl kullanılacağını açıklar; bir sabiti bildirerek değere anlamlı bir ad atarsınız.|  
|[Kullanıcı Tanımlı Sabitler](user-defined-constants.md)|Kapsam ve dairesel başvuruların nasıl engelleneceği hakkında bilgiler de dahil olmak üzere kendi sabitlerinizi oluşturmayı açıklar.|  
|[Sabit ve Değişmez Değerli Veri Türleri](constant-and-literal-data-types.md)|Kapatıldığında Visual Basic derleyicisinin sabitleri nasıl Başlatan hakkında bilgi sağlar `Option Explicit` .|  
|[Nasıl yapılır: İlgili Sabit Değerleri Birlikte Gruplandırma](how-to-group-related-constant-values-together.md)|İlgili sabit değerlerin nasıl gruplandırılacağını gösterir.|  
  
## <a name="reference"></a>Başvuru  
  
|Tanım|Süre|  
|---|---|  
|[Sabitler ve numaralandırmalar](../../../language-reference/constants-and-enumerations.md)|Visual Basic tarafından önceden tanımlanan sabitleri listeler.|  
|[Const Deyimi](../../../language-reference/statements/const-statement.md)|`Const`İfadesini ve kullanımını açıklar.|  
|[Option Strict Deyimi](../../../language-reference/statements/option-strict-statement.md)|`Option Strict`İfadesini ve kullanımını açıklar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sabit Listelerine Genel Bakış](enumerations-overview.md)
- [Nasıl yapılır: Visual Basic'te Dizi Değişkeni Başlatma](../arrays/how-to-initialize-an-array-variable.md)
