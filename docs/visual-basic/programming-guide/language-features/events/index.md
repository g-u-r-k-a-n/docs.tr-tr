---
title: Olaylar
ms.date: 07/20/2015
helpviewer_keywords:
- events [Visual Basic], about events
- events [Visual Basic]
ms.assetid: 8fb0353a-e41b-4e23-b78f-da65db832f70
ms.openlocfilehash: 666e138a747c480ef9e8b593f8c6233105fcdc93
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345113"
---
# <a name="events-visual-basic"></a>Olaylar (Visual Basic)
Bir Visual Studio projesini bir dizide yürütülen bir dizi yordam olarak görselleştirirken, gerçekte çoğu program olay odaklı olur, yani yürütme akışı *Olaylar*olarak adlandırılan dış oluşumlara göre belirlenir.  
  
 Bir olay, bir uygulamaya önemli bir şeyi oluştuğunu bildiren sinyaldir. Örneğin, Kullanıcı formdaki bir denetime tıkladığında, form `Click` bir olay oluşturabilir ve olayı işleyen bir yordamı çağırabilir. Olaylar ayrıca ayrı görevlerin iletişim kurmasına izin verir. Örneğin, uygulamanızın ana uygulamadan ayrı bir sıralama görevi gerçekleştirmesini söyleyin. Kullanıcı sıralamayı iptal ederse, uygulamanız sıralama işlemini durdurmak için bir iptal olayı gönderebilir.  
  
## <a name="event-terms-and-concepts"></a>Olay terimleri ve kavramlar  
 Bu bölümde, Visual Basic olaylar ile kullanılan hüküm ve kavramlar açıklanmaktadır.  
  
### <a name="declaring-events"></a>Olayları Bildirme  
 Aşağıdaki örnekte olduğu gibi `Event` anahtar sözcüğünü kullanarak sınıflar, yapılar, modüller ve arabirimler içindeki olayları bildirebilirsiniz:  
  
 [!code-vb[VbVbalrEvents#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#24)]  
  
### <a name="raising-events"></a>Olayları yükseltme  
 Bir olay, önemli bir şeyin oluştuğunu bildiren bir ileti gibidir. İletiyi yayınlama eylemi olayı *oluşturma olarak adlandırılır* . Visual Basic, aşağıdaki örnekte olduğu gibi `RaiseEvent` ifadesiyle olayları oluşturursunuz:  
  
 [!code-vb[VbVbalrEvents#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#25)]  
  
 Olayların bildirildiği sınıf, modül veya yapının kapsamı içinde oluşturulması gerekir. Örneğin, türetilmiş bir sınıf temel sınıftan devralınan olayları tetiklemez.  
  
### <a name="event-senders"></a>Olay Gönderenler  
 Olayı tetiklenebilecek herhangi bir nesne, *olay kaynağı*olarak da bilinen bir *olay gönderisine*sahiptir. Formlar, denetimler ve Kullanıcı tanımlı nesneler, olay gönderenlerin örnekleridir.  
  
### <a name="event-handlers"></a>Olay İşleyicileri  
 *Olay işleyicileri* , karşılık gelen bir olay gerçekleştiğinde çağrılan yordamlardır. Eşleşen imzaya sahip herhangi bir geçerli alt yordamı olay işleyicisi olarak kullanabilirsiniz. Bir işlevi olay işleyicisi olarak kullanamazsınız, ancak olay kaynağına bir değer döndüremez.  
  
 Visual Basic, olay işleyicileri için, olay göndericisinin adını, alt çizgi ve olay adını birleştiren standart bir adlandırma kuralı kullanır. Örneğin, `button1` adlı bir düğmenin `Click` olayı `Sub button1_Click`olarak adlandırılır.  
  
> [!NOTE]
> Kendi olaylarınız için olay işleyicilerini tanımlarken bu adlandırma kuralını kullanmanızı öneririz, ancak gerekli değildir; geçerli bir altyordam adı kullanabilirsiniz.  
  
## <a name="associating-events-with-event-handlers"></a>Olayları olay Işleyicileriyle ilişkilendirme  
 Bir olay işleyicisi kullanılabilir hale gelmeden önce, `Handles` ya da `AddHandler` ifadesini kullanarak onu bir olayla ilişkilendirmeniz gerekir.  
  
### <a name="withevents-and-the-handles-clause"></a>WithEvents ve Handles yan tümcesi  
 `WithEvents` deyimi ve `Handles` yan tümcesi, olay işleyicilerini belirtmenin bildirim temelli bir yöntemini sağlar. `WithEvents` anahtar sözcüğüyle belirtilen bir nesne tarafından oluşturulan bir olay, aşağıdaki örnekte gösterildiği gibi, bu olay için `Handles` ifadesiyle herhangi bir yordam tarafından işlenebilir:  
  
 [!code-vb[VbVbalrEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#1)]  
  
 `WithEvents` deyimi ve `Handles` yan tümcesi genellikle olay işleyicileri için en iyi seçenektir çünkü kullandıkları bildirime dayalı sözdizimi, kod, okuma ve hata ayıklama işlemlerini daha kolay hale getirir. Ancak `WithEvents` değişkenlerinin kullanımıyla ilgili aşağıdaki sınırlamalara dikkat edin:  
  
- Bir `WithEvents` değişkenini nesne değişkeni olarak kullanamazsınız. Diğer bir deyişle, `Object`olarak bildiremezsiniz; değişkeni bildirdiğinizde sınıf adını belirtmeniz gerekir.  
  
- Paylaşılan olaylar sınıf örneklerine bağlı olmadığından, paylaşılan olayları bildirimli olarak işlemek için `WithEvents` kullanamazsınız. Benzer şekilde, bir `Structure`olayları işlemek için `WithEvents` veya `Handles` kullanamazsınız. Her iki durumda da, bu olayları işlemek için `AddHandler` ifadesini kullanabilirsiniz.  
  
- `WithEvents` değişkenlerinin dizilerini oluşturamazsınız.  
  
 `WithEvents` değişkenleri, tek bir olay işleyicisinin bir veya daha fazla olay türünü işlemesini veya aynı olay türünü işlemesini sağlamak için bir veya daha fazla olay işleyicisine izin verir.  
  
 `Handles` yan tümcesi bir olayı bir olay işleyicisiyle ilişkilendirmenin standart yoludur, ancak derleme zamanında olayları olay işleyicilerle ilişkilendirme sınırlıdır.  
  
 Form veya denetimlerle ilişkili olaylar gibi bazı durumlarda, boş bir olay işleyicisini otomatik olarak ve bir olayla ilişkilendirir Visual Basic. Örneğin, Tasarım modunda bir form üzerindeki bir komut düğmesine çift tıkladığınızda Visual Basic, aşağıdaki kodda olduğu gibi, komut düğmesi için boş bir olay işleyicisi ve bir `WithEvents` değişkeni oluşturur:  
  
 [!code-vb[VbVbalrEvents#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#26)]  
  
### <a name="addhandler-and-removehandler"></a>AddHandler ve RemoveHandler  
 `AddHandler` deyimi, ' de bir olay işleyicisi belirtmenize izin veren `Handles` yan tümcesine benzerdir. Ancak, `RemoveHandler`kullanılan `AddHandler`, `Handles` yan tümcesinden daha fazla esneklik sağlar ve bir olayla ilişkili olay işleyicisini dinamik olarak eklemenize, kaldırmanıza ve değiştirmenize izin verir. Bir yapıdaki paylaşılan olayları veya olayları işlemek istiyorsanız `AddHandler`kullanmanız gerekir.  
  
 `AddHandler` iki bağımsız değişkeni alır: bir olay göndericisinden bir olayın adı ve bir temsilci olarak değerlendirilen bir ifade. `AddressOf` deyimin her zaman temsilciye bir başvuru döndürdüğünden, `AddHandler`kullanırken temsilci sınıfını açık bir şekilde belirtmeniz gerekmez. Aşağıdaki örnek bir olay işleyicisini bir nesne tarafından oluşturulan bir olayla ilişkilendirir:  
  
 [!code-vb[VbVbalrEvents#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#28)]  
  
 olay işleyiciden bir olayın bağlantısını kesten `RemoveHandler`, `AddHandler`ile aynı sözdizimini kullanır. Örneğin:  
  
 [!code-vb[VbVbalrEvents#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#29)]  
  
 Aşağıdaki örnekte, bir olay işleyicisi bir olayla ilişkilendirilir ve olay tetiklenir. Olay işleyicisi olayı yakalar ve bir ileti görüntüler.  
  
 Ardından, ilk olay işleyicisi kaldırılır ve olayla ilişkili farklı bir olay işleyicisi olur. Olay yeniden oluşturulduğunda, farklı bir ileti görüntülenir.  
  
 Son olarak, ikinci olay işleyicisi kaldırılır ve olay üçüncü bir kez tetiklenir. Artık olayla ilişkili bir olay işleyicisi olmadığından, hiçbir işlem yapılmaz.  
  
 [!code-vb[VbVbalrEvents#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class2.vb#38)]  
  
## <a name="handling-events-inherited-from-a-base-class"></a>Temel sınıftan devralınan olayları işleme  
 *Türetilmiş sınıflar*— bir temel sınıftan özellikleri miras alan sınıflar — `Handles MyBase` ifadesini kullanarak temel sınıfları tarafından oluşturulan olayları işleyebilir.  
  
### <a name="to-handle-events-from-a-base-class"></a>Bir temel sınıftan olayları işlemek için  
  
- Olay işleyicisi prosedürünün bildirim satırına bir `Handles MyBase.`*EventName* bildirimi ekleyerek türetilmiş sınıfta bir olay işleyicisi bildirin; burada *EventName* , işlemekte olduğunuz temel sınıftaki olayın adıdır. Örneğin:  
  
     [!code-vb[VbVbalrEvents#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#12)]  
  
## <a name="related-sections"></a>İlgili Bölümler  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[İzlenecek yol: Olay Bildirme ve Oluşturma](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)|Bir sınıf için olayların nasıl bildirilemeyeceğini ve tetiklemeyeceğini gösteren adım adım bir açıklama sağlar.|  
|[İzlenecek yol: Olayları İşleme](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)|Bir olay işleyicisi yordamının nasıl yazılacağını gösterir.|  
|[Nasıl yapılır: Engellemekten Kaçınacak Şekilde Özel Olayları Bildirme](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)|Olay işleyicilerinin zaman uyumsuz olarak çağrılmasına izin veren özel bir olayın nasıl tanımlanacağını gösterir.|  
|[Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)|Yalnızca olay işlendiği zaman belleği kullanan özel bir olayın nasıl tanımlanacağını gösterir.|  
|[Visual Basic devralınan olay Işleyicileriyle ilgili sorunları giderme](../../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)|Devralınan bileşenlerde olay işleyicileriyle ortaya çıkan yaygın sorunları listeler.|  
|[Olaylar](../../../../standard/events/index.md)|.NET Framework içindeki olay modeli için genel bir bakış sağlar.|  
|[Windows Forms'ta Olay İşleyicileri Oluşturma](../../../../framework/winforms/creating-event-handlers-in-windows-forms.md)|Windows Forms nesneleriyle ilişkili olaylarla nasıl çalışabileceğinizi açıklar.|  
|[Temsilciler](../../../../visual-basic/programming-guide/language-features/delegates/index.md)|Visual Basic temsilcileri için bir genel bakış sağlar.|
