---
title: Ayrıntılı XAML Sözdizimi
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- XAML [WPF], parsing of attributes
- parsing of attributes [WPF]
- XAML [WPF], markup extensions
- attached properties [WPF]
- tag syntax [XAML]
- markup extensions [WPF]
- XAML [WPF], object element syntax
- XAML [WPF], syntax terminology
- attached events [WPF]
- lookup semantics [WPF]
- XAML [WPF], attached events
- XAML [WPF], content syntax
- XAML [WPF], lookup semantics
- content syntax [WPF]
- object element syntax [WPF]
- syntax terminology [XAML]
- XAML [WPF], attached properties
- attributes [XAML], parsing
- XAML [WPF], tag syntax
- XAML [WPF], attribute syntax
- property element syntax [WPF]
- terminology [XAML]
- namespaces [WPF], XML
- attribute syntax [XAML]
- XAML [WPF], property element syntax
ms.assetid: 67cce290-ca26-4c41-a797-b68aabc45479
ms.openlocfilehash: 38c77086075e79c0ec5b4b1564ed753eded23b34
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124500"
---
# <a name="xaml-syntax-in-detail"></a>Ayrıntılı XAML Sözdizimi
Bu konuda, XAML söz dizimi öğelerini tanımlamakta kullanılan terimler tanımlanmaktadır. Bu terimler, hem WPF belgeleri için hem de XAML kullanan diğer çerçeveler veya System. xaml düzeyinde XAML dil desteği tarafından etkinleştirilen temel XAML kavramlarını için bu belgenin geri kalanında sık kullanılır. Bu konu, [xaml genel bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)konu başlığında sunulan temel terminoloji üzerinde genişletilir.  

<a name="the_xaml_language_specification"></a>   
## <a name="the-xaml-language-specification"></a>XAML dil belirtimi  
 Burada tanımlanan XAML sözdizimi terimleri XAML dil belirtimi içinde de tanımlanır veya başvurulur. XAML, XML tabanlı bir dildir ve XML yapısal kurallarına göre aşağıdaki veya genişler. Terminolojilerin bazıları, XML dilini veya XML belgesi nesne modelini açıklayarak yaygın olarak kullanılan terimlere göre veya ' dan paylaşılır.  
  
 XAML dil belirtimi hakkında daha fazla bilgi için, Microsoft Indirme Merkezi ' nden [\[MS-XAML\]](https://download.microsoft.com/download/0/A/6/0A6F7755-9AF5-448B-907D-13985ACCF53E/[MS-XAML].pdf) indirin.  
  
<a name="xaml_and_clr"></a>   
## <a name="xaml-and-clr"></a>XAML ve CLR  
 XAML bir biçimlendirme dilidir. Ortak dil çalışma zamanı (CLR), adı tarafından belirtildiği gibi, çalışma zamanı yürütmeyi sunar. XAML, CLR çalışma zamanı tarafından doğrudan tüketilen ortak dillerden birine göre değil. Bunun yerine, XAML 'yi kendi tür sistemini destekleyecek şekilde düşünebilirsiniz. WPF tarafından kullanılan belirli XAML ayrıştırma sistemi CLR ve CLR tür sistemi üzerine kurulmuştur. XAML türleri, WPF için XAML ayrıştırıldığında bir çalışma zamanı gösteriminin örneklemesi için CLR türleriyle eşlenir. Bu nedenle, XAML dil belirtiminde denk sözdizimi tartışmaları olmasa dahi, bu belgede söz dizimi tartışması geri kalanı CLR türü sistemine başvurular içerecektir. (XAML dil belirtimi düzeyi için XAML türleri, CLR olmaması gerekmeyen, ancak farklı XAML ayrıştırıcısının oluşturulmasını ve kullanılmasını gerektiren diğer tür sistemleri ile eşleştirilebilir.)  
  
#### <a name="members-of-types-and-class-inheritance"></a>Türlerin üyeleri ve sınıf devralma  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir türün XAML üyeleri olarak göründükleri Özellikler ve olaylar genellikle temel türlerden devralınır. Örneğin, şu örneği göz önünde bulundurun: `<Button Background="Blue" .../>`. <xref:System.Windows.Controls.Control.Background%2A> özelliği, sınıf tanımına, yansıma sonuçlarına veya belgelere baktığınızda, <xref:System.Windows.Controls.Button> sınıfında anında bildirilmemiş bir özellik değildir. Bunun yerine, <xref:System.Windows.Controls.Control.Background%2A> taban <xref:System.Windows.Controls.Control> sınıfından devralınır.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML öğelerinin sınıf devralma davranışı, XML işaretlemesi için şema tarafından zorlanan bir yorumdan önemli bir kavadır. Sınıf devralma karmaşık olabilir, özellikle ara temel sınıflar soyut olduğunda veya arabirimler dahil edildiğinde karmaşık hale gelebilir. Bu, XAML öğeleri kümesinin ve izin verilen özniteliklerinin, genellikle DTD veya XSD biçimi gibi XML programlama için kullanılan şema türlerini doğru ve tamamen temsil etmesi zor bir nedenidir. Diğer bir nedenden dolayı, XAML dilinin genişletilebilirlik ve tür eşleme özelliklerinin, izin verilen türlerin ve üyelerin herhangi bir sabit gösteriminden daha da karmaşık olmasını sağlamak.  
  
<a name="object_element_syntax"></a>   
## <a name="object-element-syntax"></a>Nesne öğesi sözdizimi  
 *Nesne öğesi sözdizimi* , bir XML öğesi BILDIREREK bir clr sınıfı veya yapısını ÖRNEKLEYEN XAML biçimlendirme sözdizimidir. Bu söz dizimi, HTML gibi diğer biçimlendirme dillerinin öğe sözdizimine benzer. Nesne öğesi sözdizimi sol açılı köşeli ayraç (\<) ile başlar ve ardından, oluşturulan sınıfın veya yapının tür adı tarafından hemen izlenir. Sıfır veya daha fazla boşluk tür adını izleyebilir ve bir veya daha fazla öznitelik, her öznitelik adı = "Value" çiftini ayıran bir veya daha fazla boşluk ile nesne öğesinde de bildirilemez. Son olarak, aşağıdakilerden biri doğru olmalıdır:  
  
- Öğe ve etiket bir eğik çizgi (/) ile hemen arkasından sağ açılı ayraç (>) ile kapatılmalıdır.  
  
- Açma etiketi sağ açılı ayraç (>) ile tamamlanmalıdır. Diğer nesne öğeleri, özellik öğeleri veya iç metin, açma etiketini izleyebilir. Burada tam olarak hangi içeriklerin dahil olabileceği, genellikle öğenin nesne modeliyle kısıtlanır. Nesne öğesi için eşdeğer kapanış etiketi, doğru iç içe geçme ve diğer açılış ve kapanış etiketi çiftleriyle dengede bulunmalıdır.  
  
 .NET tarafından uygulanan XAML, nesne öğelerini türler, öznitelikler veya olaylar ve XAML ad alanları ile CLR ad alanları ve derleme öğelerine eşleyen bir kurallar kümesine sahiptir. WPF ve .NET için XAML nesne öğeleri, başvurulan derlemelerde tanımlanan .NET türleriyle eşlenir ve öznitelikler bu türlerin üyeleriyle eşlenir. XAML 'de bir CLR türüne başvurduğunuzda, bu türdeki devralınan üyelere de erişebilirsiniz.  
  
 Örneğin, aşağıdaki örnek, <xref:System.Windows.Controls.Button> sınıfının yeni bir örneğini örnekleyen ve ayrıca bu öznitelik için bir <xref:System.Windows.FrameworkElement.Name%2A> özniteliği ve bir değer belirten nesne öğesi sözdizimidir:  
  
 [!code-xaml[XAMLOvwSupport#SyntaxOE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxoe)]  
  
 Aşağıdaki örnek, XAML içerik özelliği sözdizimi de içeren nesne öğesi söz dizimine sahiptir. İçinde yer alan iç metin, <xref:System.Windows.Controls.TextBox.Text%2A><xref:System.Windows.Controls.TextBox> XAML içerik özelliği ayarlamak için kullanılacaktır.  
  
 [!code-xaml[XAMLOvwSupport#ThisIsATextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#thisisatextbox)]  
  
### <a name="content-models"></a>İçerik modelleri  
 Bir sınıf, sözdizimi bakımından XAML nesne öğesi olarak kullanımı destekleyebilir, ancak bu öğe, genel içerik modelinin veya öğe ağacının beklenen konumuna yerleştirildiğinde yalnızca bir uygulamada veya sayfada düzgün şekilde çalışır. Örneğin, bir <xref:System.Windows.Controls.MenuItem> genellikle yalnızca <xref:System.Windows.Controls.Menu>gibi <xref:System.Windows.Controls.Primitives.MenuBase> türetilmiş bir sınıfın alt öğesi olarak yerleştirilmelidir. Belirli öğeler için içerik modelleri, XAML öğeleri olarak kullanılabilecek denetimler ve diğer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sınıfları için sınıf sayfalarında açıklamalarının bir parçası olarak belgelenmiştir.  
  
<a name="properties_of_object_elements"></a>   
## <a name="properties-of-object-elements"></a>Nesne öğelerinin özellikleri  
 XAML 'deki özellikler, çeşitli olası sözdizimleri tarafından ayarlanır. Belirli bir özellik için hangi sözdizimi kullanılabilecek, ayarladığınız özelliğin temel alınan tür sistemi özelliklerine göre değişiklik gösterecektir.  
  
 Özelliklerin değerlerini ayarlayarak, nesnelere çalışma zamanı nesne grafiğinde var olan özellikleri veya özellikleri ekleyin. Bir nesne öğesinden oluşturulan nesnenin ilk durumu parametresiz Oluşturucu davranışına göre belirlenir. Genellikle, uygulamanız herhangi bir nesne için tamamen varsayılan bir örnek dışında bir şey kullanacaktır.  
  
<a name="attribute_syntax_properties"></a>   
## <a name="attribute-syntax-properties"></a>Öznitelik sözdizimi (Özellikler)  
 Öznitelik sözdizimi, varolan bir nesne öğesinde bir özniteliği bildirerek bir özellik için değer ayarlayan XAML biçimlendirme sözdizimidir. Öznitelik adı, ilgili nesne öğesini yedekleyen sınıfın özelliğinin CLR üye adı ile aynı olmalıdır. Öznitelik adının ardından bir atama işleci (=) gelir. Öznitelik değeri tırnak içine alınmış bir dize olmalıdır.  
  
> [!NOTE]
> Bir özniteliğe sabit bir tırnak işareti koymak için alternatif tırnakları kullanabilirsiniz. Örneğin, içinde çift tırnak karakteri içeren bir dize bildirmek için tek tırnakları bir yol olarak kullanabilirsiniz. Tek veya çift tırnak işareti kullanıp kullanmayacağınızı, öznitelik değer dizesini açmak ve kapatmak için eşleşen bir çift kullanmanız gerekir. Ayrıca, belirli XAML söz dizimi tarafından uygulanan karakter kısıtlamaları etrafında çalışan kaçış dizileri veya diğer teknikler de mevcuttur. Bkz. [XML karakter varlıkları ve xaml](../../../desktop-wpf/xaml-services/xml-character-entities.md).  
  
 Öznitelik sözdizimi ile ayarlanbilmek için bir özelliğin ortak olması ve yazılabilir olması gerekir. Yedekleme türü sistemindeki özelliğinin değeri bir değer türü olmalıdır veya ilgili yedekleme türüne erişirken bir XAML işlemcisi tarafından örneklenmiş veya başvurulabilen bir başvuru türü olmalıdır.  
  
 WPF XAML olayları için, öznitelik adı olarak başvurulan olayın ortak olması ve genel bir temsilcisi olması gerekir.  
  
 Özellik veya olay, kapsayan nesne öğesi tarafından oluşturulan sınıfın veya yapının bir üyesi olmalıdır.  
  
### <a name="processing-of-attribute-values"></a>Öznitelik değerlerini işleme  
 Açma ve kapatma tırnak işaretlerinin içinde yer alan dize değeri bir XAML işlemcisi tarafından işlenir. Özellikler için, varsayılan işleme davranışı temeldeki CLR özelliğinin türüne göre belirlenir.  
  
 Öznitelik değeri, bu işleme sırası kullanılarak, aşağıdakilerden biri ile doldurulur:  
  
1. XAML işlemcisi bir küme ayracı veya <xref:System.Windows.Markup.MarkupExtension>türetilen bir nesne öğesi ile karşılaştığında, başvurulan biçimlendirme uzantısı değeri bir dize olarak işlemek yerine önce değerlendirilir ve biçimlendirme uzantısı tarafından döndürülen nesne değer olarak kullanılır. Birçok durumda, bir işaretleme uzantısı tarafından döndürülen nesne varolan bir nesneye ya da çalışma zamanına kadar değerlendirmeyi yapan bir ifadeye veya yeni bir örneklenmiş nesne değil.  
  
2. Özelliği öznitelikli bir <xref:System.ComponentModel.TypeConverter>ile bildirilirse veya özelliğin değer türü öznitelikli bir <xref:System.ComponentModel.TypeConverter>ile bildirilirse, özniteliğin dize değeri bir dönüştürme girişi olarak tür dönüştürücüsüne gönderilir ve dönüştürücü yeni bir nesne örneği döndürür.  
  
3. <xref:System.ComponentModel.TypeConverter>yoksa, özellik türüne doğrudan dönüştürme denenir. Bu son düzey, XAML dil temel türleri arasındaki ayrıştırıcının yerel değerindeki doğrudan dönüştürmedir veya bir Numaralandırmadaki adlandırılmış sabitlerin adlarını denetler (ayrıştırıcı daha sonra eşleşen değerlere erişir).  
  
#### <a name="enumeration-attribute-values"></a>Sabit Listesi öznitelik değerleri  
 XAML 'deki numaralandırmalar XAML Çözümleyicileri tarafından doğası gereği işlenir ve sabit listesinin adlandırılmış sabitlerinden birinin dize adı belirtilerek bir numaralandırma üyeleri belirtilmelidir.  
  
 Bayrak olmayan numaralandırma değerleri için, yerel davranış bir öznitelik değerinin dizesini işlemek ve sabit listesi değerlerinden birine çözmadır. Sabit listesini biçim *numaralandırmasında*belirtmeyin. *Değer*, kodda yaptığınız gibi. Bunun yerine, yalnızca *değeri*belirtirsiniz ve *sabit listesi* , ayarladığınız özelliğin türü tarafından algılanır. *Numaralandırmada*bir özniteliği belirtirseniz. *Değer* formu, doğru çözümlenmeyecektir.  
  
 Flagwise Numaralandırmalar için davranış <xref:System.Enum.Parse%2A?displayProperty=nameWithType> yöntemi temel alır. Her değeri virgülle ayırarak, bir flagwise numaralandırması için birden fazla değer belirtebilirsiniz. Ancak, flagwise olmayan numaralandırma değerlerini birleştiremezsiniz. Örneğin, bayrak olmayan bir numaralandırmanın birden çok koşulu üzerinde davranan bir <xref:System.Windows.Trigger> oluşturmayı denemek için virgül sözdizimini kullanamazsınız:  
  
```xaml  
<!--This will not compile, because Visibility is not a flagwise enumeration.-->  
...  
<Trigger Property="Visibility" Value="Collapsed,Hidden">  
  <Setter ... />  
</Trigger>  
...  
```  
  
 XAML 'de ayarlanabilir öznitelikleri destekleyen flagwise numaralandırmalar WPF içinde nadir bir durumdur. Ancak, bu tür bir numaralandırma <xref:System.Windows.Media.StyleSimulations>. Örneğin, <xref:System.Windows.Documents.Glyphs> sınıfı için açıklamalardır belirtilen örneği değiştirmek için virgülle ayrılmış flagwise öznitelik sözdizimini kullanabilirsiniz; `StyleSimulations = "BoldSimulation"` `StyleSimulations = "BoldSimulation,ItalicSimulation"`hale gelebilir. <xref:System.Windows.Input.KeyBinding.Modifiers%2A?displayProperty=nameWithType> birden fazla numaralandırma değerinin belirtilebileceği başka bir özelliktir. Ancak, <xref:System.Windows.Input.ModifierKeys> numaralandırması kendi tür dönüştürücüsünü desteklediğinden, bu özellik özel bir durum gibi olur. Değiştiriciler için tür dönüştürücüsü, virgül (,) yerine sınırlayıcı olarak bir artı işareti (+) kullanır. Bu dönüştürme, Microsoft Windows programlama 'de "Ctrl + alt" gibi temel bileşimleri temsil eden daha geleneksel sözdizimini destekler.  
  
### <a name="properties-and-event-member-name-references"></a>Özellikler ve olay üyesi adı başvuruları  
 Bir öznitelik belirtirken, içeren nesne öğesi için örnekettiğiniz CLR türünün bir üyesi olarak var olan herhangi bir özelliğe veya olaya başvurabilirsiniz.  
  
 Ya da, ekli nesne öğesinden bağımsız olarak iliştirilmiş bir özelliğe veya ekli olaya başvurabilirsiniz. (Ekli Özellikler yaklaşan bölümde ele alınmıştır.)  
  
 Ayrıca, bir *TypeName*kullanarak, varsayılan ad alanı aracılığıyla erişilebilen herhangi bir nesneden herhangi bir olayı da yazabilirsiniz. *olay* kısmen nitelenmiş adı; Bu sözdizimi, işleyicinin alt öğelerinden olay yönlendirmeyi işlemeye yönelik olduğu, ancak üst öğenin üye tablosunda da bu olayı içermediği yönlendirilmiş olaylar için işleyicileri eklemeyi destekler. Bu söz dizimi ekli bir olay sözdizimine benzer, ancak buradaki olay, doğru bir ekli olay değildir. Bunun yerine, nitelikli bir ada sahip bir olaya başvuruyorsunuz. Daha fazla bilgi için bkz. [yönlendirilmiş olaylara genel bakış](routed-events-overview.md).  
  
 Bazı senaryolarda, özellik adları bazen öznitelik adı yerine bir özniteliğin değeri olarak sağlanır. Bu özellik adı, *OwnerType*biçiminde belirtilen özellik gibi niteleyiciler de içerebilir. *dependencyPropertyName*. Bu senaryo, XAML 'de stil veya şablon yazarken yaygındır. Öznitelik değeri olarak belirtilen özellik adlarına yönelik işleme kuralları farklıdır ve ayarlanan özelliğin türüne veya belirli WPF alt sistemlerinin davranışlarına tabidir. Ayrıntılar için bkz. [Stil oluşturma ve şablon](../controls/styling-and-templating.md)oluşturma.  
  
 Özellik adları için başka bir kullanım, bir öznitelik değeri özellik özelliği ilişkisini açıkladığı zaman. Bu özellik veri bağlama ve görsel taslak hedefleri için kullanılır ve <xref:System.Windows.PropertyPath> sınıfı ve tür dönüştürücüsü tarafından etkinleştirilir. Arama semantiğinin daha ayrıntılı bir açıklaması için bkz. [PROPERTYPATH XAML sözdizimi](propertypath-xaml-syntax.md).  
  
<a name="property_element_syntax"></a>   
## <a name="property-element-syntax"></a>Özellik öğesi sözdizimi  
 *Özellik öğesi sözdizimi* , öğeleri IÇIN temel XML sözdizimi kurallarından biraz ayrılan bir sözdizimidir. XML 'de, bir özniteliğin değeri, tek bir dize kodlama biçiminin kullanıldığı tek bir çeşitle bir dizedir. XAML 'de, diğer nesne öğelerini bir özelliğin değeri olacak şekilde atayabilirsiniz. Bu yetenek, özellik öğesi sözdizimi tarafından etkinleştirilir. Özelliği, öğe etiketi içindeki bir öznitelik olarak belirtilen özellik yerine, *elementTypeName*içindeki bir açýlýþ element etiketi kullanılarak belirtilir. *PropertyName* formu, özelliğin değeri içinde belirtilir ve sonra Property öğesi kapalıdır.  
  
 Özellikle, sözdizimi sol açılı köşeli ayraç (\<) ile başlar ve ardından özellik öğesi sözdiziminin içinde bulunduğu sınıfın veya yapının tür adı tarafından hemen izlenir. Bu, hemen sonra tek bir nokta (.), ardından bir özelliğin adı ve sağ açılı ayraç (>) ile izlenir. Öznitelik sözdiziminde olduğu gibi, bu özellik belirtilen türdeki ortak Üyeler içinde bulunmalıdır. Özelliğe atanacak değer, özellik öğesinin içinde yer alır. Genellikle değer bir veya daha fazla nesne öğesi olarak verilir, çünkü nesneleri değer olarak belirtmek, özellik öğesi sözdiziminin ele hazırlandığı senaryodur. Son olarak, aynı *elementTypeName*öğesini belirten eşdeğer bir kapanış etiketi. *PropertyName* birleşiminin, doğru iç içe geçme ve diğer öğe etiketleriyle dengelenmesi sağlanmalıdır.  
  
 Örneğin, aşağıdaki, bir <xref:System.Windows.Controls.Button><xref:System.Windows.FrameworkElement.ContextMenu%2A> özelliği için özellik öğesi sözdizimidir.  
  
 [!code-xaml[XAMLOvwSupport#ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#contextmenu)]  
  
 Bir özellik öğesi içindeki değer ayrıca iç metin olarak verilebilir, çünkü belirtilen özellik türü, <xref:System.String>gibi bir temel değer türüdür veya bir adın belirtildiği bir sabit değerdir. Bu iki kullanım çok nadir bir durumdur, çünkü bu durumların her biri daha basit bir öznitelik sözdizimi de kullanabilir. Bir dize ile bir özellik öğesinin doldurulmasıyla ilgili bir senaryo XAML içerik özelliği olmayan, ancak UI metninin temsili için hala kullanılan özellikler içindir ve bu kullanıcı arabirimi metninde satır akışları gibi belirli boşluk öğelerinin görünmesi gerekir. Öznitelik sözdizimi, satır beslemelerini koruyamaz, ancak özellik öğesi söz dizimi, önemli beyaz alan koruması etkin olduğu sürece (Ayrıntılar için bkz. [xaml 'de beyaz boşluk işleme](../../../desktop-wpf/xaml-services/white-space-processing.md)). Başka bir senaryo ise, [X:Uid yönergesinin](../../../desktop-wpf/xaml-services/xuid-directive.md) Özellik öğesine uygulanabilmesi ve bu sayede değeri WPF çıkış BAML 'de veya başka teknikler için yerelleştirilmesi gereken bir değer olarak işaretlemenize olanak sağlar.  
  
 Bir özellik öğesi WPF mantıksal ağacında temsil edilmez. Özellik öğesi, bir özelliği ayarlamaya yönelik yalnızca belirli bir sözdizimidir ve bir örnek veya nesne çalıştıran bir öğe değildir. (Mantıksal ağaç kavramıyla ilgili ayrıntılar için bkz. [WPF 'de ağaçlar](trees-in-wpf.md).)  
  
 Hem öznitelik hem de Özellik öğesi sözdiziminin desteklendiği özellikler için, iki sözdizimi genellikle aynı sonuca sahiptir, ancak beyaz boşluk işleme gibi alt tlelikler sözdizimleri arasında biraz farklılık gösterebilir.  
  
<a name="collection_syntax"></a>   
## <a name="collection-syntax"></a>Koleksiyon sözdizimi  
 XAML belirtimi, XAML işlemci uygulamalarının değer türünün bir koleksiyon olduğu özellikleri belirlemesini gerektirir. .NET 'teki Genel XAML işlemci uygulamaları, yönetilen kodu ve CLR 'yi temel alır ve koleksiyon türlerini aşağıdakilerden biri aracılığıyla tanımlar:  
  
- Tür <xref:System.Collections.IList>uygular.  
  
- Tür <xref:System.Collections.IDictionary>uygular.  
  
- Türü <xref:System.Array> türetiliyor (XAML içindeki diziler hakkında daha fazla bilgi için bkz. [X:Array Markup Extension](../../../desktop-wpf/xaml-services/xarray-markup-extension.md).)  
  
 Bir özelliğin türü bir koleksiyon ise, gösterilen koleksiyon türünün bir nesne öğesi olarak İşaretlemede belirtilmesi gerekmez. Bunun yerine, koleksiyonda öğeler haline gelmesi amaçlanan öğeler, Property öğesinin bir veya daha fazla alt öğesi olarak belirtilir. Bu tür öğeler, yükleme sırasında bir nesne olarak değerlendirilir ve kapsanan koleksiyonun `Add` yöntemi çağırarak koleksiyona eklenir. Örneğin, <xref:System.Windows.Style> <xref:System.Windows.Style.Triggers%2A> özelliği, <xref:System.Collections.IList>uygulayan <xref:System.Windows.TriggerCollection>özel koleksiyon türünü alır. İşaretlemede <xref:System.Windows.TriggerCollection> nesne öğesi örneği oluşturmak gerekli değildir. Bunun yerine, <xref:System.Windows.Trigger> (veya türetilmiş bir sınıf) türü kesin belirlenmiş ve örtük <xref:System.Windows.TriggerCollection>için öğe türü olarak beklenen tür olan `Style.Triggers` Özellik öğesi içinde öğe olarak bir veya daha fazla <xref:System.Windows.Trigger> öğesi belirtirsiniz.  
  
 [!code-xaml[XAMLOvwSupport#SyntaxPECollection](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxpecollection)]  
  
 Bir özellik, bu konunun sonraki bölümünde ele alınan bu tür ve türetilmiş türler için hem koleksiyon türü hem de XAML içerik özelliği olabilir.  
  
 Örtük bir koleksiyon öğesi, İşaretlemede bir öğe olarak görünmese de, mantıksal ağaç gösteriminde bir üye oluşturur. Genellikle üst türün Oluşturucusu, özelliklerinden biri olan koleksiyon için örnek oluşturmayı gerçekleştirir ve başlangıçta boş koleksiyon, nesne ağacının bir parçası haline gelir.  
  
> [!NOTE]
> Genel liste ve sözlük arabirimleri (<xref:System.Collections.Generic.IList%601> ve <xref:System.Collections.Generic.IDictionary%602>) koleksiyon algılama için desteklenmez. Ancak, doğrudan <xref:System.Collections.IDictionary> uyguladığından, <xref:System.Collections.IList> doğrudan veya temel sınıf olarak <xref:System.Collections.Generic.Dictionary%602> uyguladığından <xref:System.Collections.Generic.List%601> sınıfını temel sınıf olarak kullanabilirsiniz.  
  
 Koleksiyon türleri için .NET başvuru sayfalarında, bir koleksiyon için nesne öğesinin bilinçli atlanmasına sahip bu sözdizimi zaman zaman örtük koleksiyon sözdizimi olarak XAML sözdizimi bölümlerinde belirtilmiştir.  
  
 Kök öğesi hariç olmak üzere, başka bir öğenin alt öğesi olarak iç içe yerleştirilmiş bir XAML dosyasındaki her nesne öğesi gerçekten aşağıdaki durumlardan biri veya her ikisi olan bir öğedir: üst öğesinin örtük bir koleksiyon özelliğinin üyesi ya da üst öğe için XAML içerik özelliğinin değerini belirten bir öğesi (XAML içerik özellikleri yaklaşan bir bölümde ele alınacaktır). Diğer bir deyişle, bir biçimlendirme sayfasındaki üst öğe ve alt öğe öğelerinin ilişkisi aslında tek bir nesnedir ve kök altındaki her nesne öğesi, üst öğenin özellik değerini sağlayan tek bir örnek veya bir Col içindeki öğelerden biridir Ayrıca, üst öğenin koleksiyon türü özellik değeri de vardır. Bu tek köklü kavram XML ile yaygındır ve <xref:System.Windows.Markup.XamlReader.Load%2A>gibi XAML yükleyen API 'lerin davranışında genellikle yeniden zorlanır.  
  
 Aşağıdaki örnek, açıkça belirtilen bir koleksiyonun (<xref:System.Windows.Media.GradientStopCollection>) nesne öğesi ile bir sözdizimidir.  
  
```xaml  
<LinearGradientBrush>  
  <LinearGradientBrush.GradientStops>  
    <GradientStopCollection>  
      <GradientStop Offset="0.0" Color="Red" />  
      <GradientStop Offset="1.0" Color="Blue" />  
    </GradientStopCollection>  
  </LinearGradientBrush.GradientStops>  
</LinearGradientBrush>  
```  
  
 Koleksiyonu açıkça bildirmek için her zaman mümkün olmadığına unutmayın. Örneğin, daha önce gösterilen <xref:System.Windows.Style.Triggers%2A> örneğinde <xref:System.Windows.TriggerCollection> açıkça bildirmeye çalışılması başarısız olur. Koleksiyonu açıkça bildirmek için koleksiyon sınıfının parametresiz bir oluşturucuyu desteklemesi ve <xref:System.Windows.TriggerCollection> parametresiz bir Oluşturucusu olmaması gerekir.  
  
<a name="xaml_content_properties"></a>   
## <a name="xaml-content-properties"></a>XAML Içerik özellikleri  
 XAML içerik sözdizimi, sınıf bildiriminin parçası olarak <xref:System.Windows.Markup.ContentPropertyAttribute> belirten sınıflarda etkinleştirilen bir sözdizimidir. <xref:System.Windows.Markup.ContentPropertyAttribute>, bu öğe türünün (türetilmiş sınıflar dahil) içerik özelliği olan özellik adına başvurur. Bir XAML işlemcisi tarafından işlendiğinde, nesne öğesinin açılış ve kapanış etiketleri arasında bulunan herhangi bir alt öğe veya iç metin, bu nesne için XAML içerik özelliğinin değeri olacak şekilde atanır. İçerik özelliği için açık özellik öğeleri belirtmenize izin verilir, ancak bu kullanım genellikle .NET başvurusunun XAML söz dizimi bölümlerinde gösterilmez. Açık/ayrıntılı teknikte, biçimlendirme netliği için zaman zaman değeri veya biçimlendirme stili olması gerekir, ancak genellikle bir içerik özelliğinin amacı, üst-alt öğe ile ilgili olan öğelerin doğrudan iç içe yerleştirilebilmesi için biçimlendirmeyi kolaylaştırmaktır. Bir öğedeki diğer özellikler için özellik öğesi etiketleri, katı bir XAML dil tanımı başına "içerik" olarak atanmaz; daha önce XAML ayrıştırıcısının işleme sırasında işlenir ve "içerik" olarak kabul edilmez.  
  
### <a name="xaml-content-property-values-must-be-contiguous"></a>XAML Içerik özelliği değerleri bitişik olmalıdır  
 XAML içerik özelliğinin değeri, nesne öğesindeki diğer herhangi bir özellik öğesinden tamamen önce veya tamamen bir değere verilmelidir. Bu, XAML içerik özelliği değerinin bir dize olarak mı yoksa bir veya daha fazla nesne olarak mı belirtilmeliyse geçerlidir. Örneğin, aşağıdaki biçimlendirme ayrıştırılmadı:  
  
```xaml  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 Bu geçersizdir çünkü bu sözdizimi, içerik özelliği için özellik öğesi söz dizimi kullanılarak açık hale getirilmiş olduğundan, içerik özelliği iki kez ayarlanabilir:  
  
```xaml  
<Button>  
  <Button.Content>I am a </Button.Content>  
  <Button.Background>Blue</Button.Background>  
  <Button.Content> blue button</Button.Content>  
</Button>  
```  
  
 Benzer şekilde geçersiz bir örnek, içerik özelliğinin bir koleksiyon olması ve alt öğelerin özellik öğeleriyle birlikte nasıl karışılyadır.  
  
```xaml  
<StackPanel>  
  <Button>This example</Button>  
  <StackPanel.Resources>  
    <SolidColorBrush x:Key="BlueBrush" Color="Blue"/>  
  </StackPanel.Resources>  
  <Button>... is illegal XAML</Button>  
</StackPanel>  
```  
  
<a name="content_properties_and_collection_syntax_combined"></a>   
## <a name="content-properties-and-collection-syntax-combined"></a>İçerik özellikleri ve koleksiyon sözdizimi birleştirildi  
 İçerik olarak birden fazla nesne öğesini kabul etmek için, içerik özelliğinin türü özel olarak bir koleksiyon türü olmalıdır. Koleksiyon türleri için özellik öğesi söz dizimine benzer şekilde, bir XAML işlemcisi koleksiyon türleri olan türleri tanımmalıdır. Bir öğenin XAML içerik özelliği varsa ve XAML içerik özelliğinin türü bir koleksiyon ise, kapsanan koleksiyon türünün bir nesne öğesi olarak biçimlendirmesinde belirtilmesi gerekmez ve XAML içerik özelliğinin bir özellik el ile belirtilmesi gerekmez. etim. Bu nedenle, biçimlendirmede görünen içerik modeli artık içerik olarak atanmış birden fazla alt öğe içerebilir. <xref:System.Windows.Controls.Panel> türetilmiş bir sınıf için içerik sözdizimi aşağıda verilmiştir. Tüm <xref:System.Windows.Controls.Panel> türetilmiş sınıflar XAML içerik özelliğini <xref:System.Windows.Controls.Panel.Children%2A>, bu da <xref:System.Windows.Controls.UIElementCollection>türünde bir değer gerektirir.  
  
 [!code-xaml[XAMLOvwSupport#SyntaxContent](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page5.xaml#syntaxcontent)]  
  
 Biçimlendirme içinde <xref:System.Windows.Controls.UIElementCollection> için <xref:System.Windows.Controls.Panel.Children%2A> veya öğesi için özellik öğesi gerekmediği unutulmamalıdır. Bu, XAML 'in tasarım özelliğidir ve bu sayede, bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] tanımlayan öğeler, doğrudan üst-alt öğe ilişkilerinden oluşan iç içe geçmiş öğelerin bir ağacı olarak temsil edilir ve özellik öğesi etiketleri veya koleksiyon nesneleri dahil değildir. Aslında <xref:System.Windows.Controls.UIElementCollection>, tasarıma göre bir nesne öğesi olarak biçimlendirme içinde açıkça belirtilemez. Yalnızca amaçlanan kullanım örtük bir koleksiyon olduğundan <xref:System.Windows.Controls.UIElementCollection> Ortak parametresiz bir Oluşturucu sunmaz ve bu nedenle bir nesne öğesi olarak başlatılamaz.  
  
### <a name="mixing-property-elements-and-object-elements-in-an-object-with-a-content-property"></a>Içerik özelliği ile nesne içindeki özellik öğelerini ve nesne öğelerini karıştırma  
 XAML belirtimi, bir XAML işlemcisinin bir nesne öğesi içindeki XAML içerik özelliğini doldurmakta kullanılan nesne öğelerinin bitişik olması ve karışık olmaması gerektiğini bildirir. Özellik öğelerini ve içeriği karıştırmaya yönelik bu kısıtlama [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML işlemcileri tarafından zorlanır.  
  
 Bir nesne öğesi içindeki ilk anında biçimlendirme olarak bir alt nesne öğesi olabilir. Daha sonra özellik öğeleri ekleyebilirsiniz. Ya da bir veya daha fazla özellik öğesi, içerik ve daha fazla özellik öğesi de belirtebilirsiniz. Ancak, bir özellik öğesi içeriğe ulaştıktan sonra, başka bir içerik getiremezsiniz, ancak özellik öğeleri ekleyebilirsiniz.  
  
 Bu içerik/özellik öğesi sırası gereksinimi içerik olarak kullanılan iç metin için uygulanabilir değil. Ancak, iç metni sürekli tutmak için iyi bir biçimlendirme stilidir, çünkü özellik öğeleri iç metinle birlikte ayarlandığında, biçimlendirme içinde görsel olarak algılanmaları zor olur.  
  
<a name="xaml_namespaces"></a>   
## <a name="xaml-namespaces"></a>XAML Ad Uzayları  
 Önceki söz dizimi örneklerinden hiçbiri varsayılan XAML ad alanı dışında bir XAML ad alanı belirtbelirtti. Tipik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalarda, varsayılan XAML ad alanı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ad alanı olarak belirtilir. Varsayılan XAML ad alanı dışında XAML ad alanları belirtebilir ve yine de benzer sözdizimini kullanabilirsiniz. Ancak, varsayılan XAML ad alanı içinde erişilebilir olmayan bir sınıfın adlandırıldığını her yerde, bu sınıf adı, karşılık gelen CLR ad alanına eşlenmiş şekilde XAML ad alanının öneki olmalıdır. Örneğin, `<custom:Example/>`, bu sınıfı içeren CLR ad alanı (ve muhtemelen Yedekleme türlerini içeren dış derleme bilgileri), daha önce `custom` ön ekine eşlendiği `Example` sınıfının bir örneğini başlatmak için nesne öğesi sözdizimidir.  
  
 XAML ad alanları hakkında daha fazla bilgi için bkz. [WPF XAML Için xaml ad alanları ve ad alanı eşlemesi](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>İşaretleme Uzantıları  
 XAML, dize özniteliği değerlerinin veya nesne öğelerinin normal XAML işlemci işlemesini sağlayan bir işaretleme uzantısı programlama varlığı tanımlar ve işlemeyi bir yedekleme sınıfına erteler. Öznitelik sözdizimi kullanılırken bir XAML işlemcisine bir biçimlendirme uzantısı tanımlayan karakter, bir kapanış küme ayracı ({) ve ardından bir kapatma küme ayracı (}) dışında bir karakter. Açma küme ayracından sonraki ilk dize, söz konusu alt dize doğru sınıf adının bir parçasıysa, başvurunun "Extension" alt dizesini ayırabileceği belirli uzantı davranışını sağlayan sınıfa başvurmalıdır. Bundan sonra, tek bir boşluk görünebilir ve sonra, kapatma büyük ayraçına ulaşana kadar, her bir sonraki karakter uzantı uygulamasıyla giriş olarak kullanılır.  
  
 .NET XAML uygulama, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tarafından desteklenen tüm biçimlendirme uzantılarının yanı sıra diğer çerçeveler veya teknolojiler için <xref:System.Windows.Markup.MarkupExtension> soyut sınıfını kullanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özel olarak uygulanan biçimlendirme uzantıları genellikle, diğer mevcut nesnelere başvurmak için bir yol sağlamak veya çalışma zamanında değerlendirilecek nesnelere ertelenmiş başvurular yapmak için tasarlanmıştır. Örneğin, bir Basit WPF veri bağlama, belirli bir özelliğin normalde aldığı değerin yerine `{Binding}` biçimlendirme uzantısı belirtilerek gerçekleştirilir. WPF biçimlendirme uzantılarının birçoğu, bir öznitelik sözdiziminin mümkün olmaması için öznitelik sözdizimini etkinleştirir. Örneğin, <xref:System.Windows.Style> nesnesi, iç içe geçmiş nesne ve özellik serisini içeren görece karmaşık bir türdür. WPF 'deki stiller genellikle <xref:System.Windows.ResourceDictionary>bir kaynak olarak tanımlanır ve sonra bir kaynak isteyen iki WPF biçimlendirme uzantılarından biri ile başvurulur. Biçimlendirme uzantısı, özellik değerinin değerlendirmesini bir kaynak aramasına erteler ve aşağıdaki örnekte gösterildiği gibi <xref:System.Windows.FrameworkElement.Style%2A> özelliğinin değerini, öznitelik söz dizimine <xref:System.Windows.Style>almak için sağlar:  
  
 `<Button Style="{StaticResource MyStyle}">My button</Button>`  
  
 Burada, `StaticResource` biçimlendirme uzantısı uygulamasını sağlayan <xref:System.Windows.StaticResourceExtension> sınıfını tanımlar. Sonraki dize `MyStyle`, uzantı dizesinden alınan parametrenin istenen <xref:System.Windows.ResourceKey>bildirdiği varsayılan olmayan <xref:System.Windows.StaticResourceExtension> Oluşturucu için giriş olarak kullanılır. `MyStyle`, kaynak olarak tanımlanan bir <xref:System.Windows.Style> [X:Key](../../../desktop-wpf/xaml-services/xkey-directive.md) değeri olması beklenir. [StaticResource biçimlendirme uzantısı](staticresource-markup-extension.md) kullanımı, kaynağın, yükleme zamanında statik kaynak arama mantığı aracılığıyla <xref:System.Windows.Style> özellik değerini sağlamak için kullanılmasını ister.  
  
 Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md). Biçimlendirme uzantıları ve genel .NET XAML uygulamasında etkin olan diğer XAML programlama özellikleri başvurusu için bkz. [xaml ad alanı (x:) Dil özellikleri](../../../desktop-wpf/xaml-services/namespace-language-features.md). WPF 'e özgü biçimlendirme uzantıları için bkz. [WPF XAML uzantıları](wpf-xaml-extensions.md).  
  
<a name="attached_properties"></a>   
## <a name="attached-properties"></a>Ekli Özellikler  
 İliştirilmiş özellikler XAML 'de sunulan ve belirli bir türe sahip olan, ancak herhangi bir öğe üzerinde öznitelikler veya özellik öğeleri olarak ayarlanan bir programlama kavramıdır. İliştirilmiş özelliklerin için tasarlanan birincil senaryo, bir biçimlendirme yapısındaki alt öğelerin, tüm öğelerde yaygın olarak paylaşılan bir nesne modeli gerekmeden bilgileri bir üst öğeye bildirmektir. Buna karşılık, ekli özellikler üst öğeler tarafından, bilgileri alt öğelere raporlamak için kullanılabilir. Ekli özelliklerin amacı ve kendi ekli özelliklerinizi oluşturma hakkında daha fazla bilgi için bkz. [ekli özelliklere genel bakış](attached-properties-overview.md).  
  
 İliştirilmiş özellikler, superficially benzer özellik öğesi sözdizimine sahip bir sözdizimi kullanır, bu da bir *TypeName*de belirtebilirsiniz. *PropertyName* birleşimi. İki önemli fark vardır:  
  
- *TypeName*kullanabilirsiniz. öznitelik söz dizimi aracılığıyla iliştirilmiş bir özelliği ayarlarken bile *PropertyName* birleşimi. İliştirilmiş özellikler, özellik adının öznitelik sözdiziminde bir gereksinim olması gereken tek durumdur.  
  
- İliştirilmiş özellikler için özellik öğesi sözdizimini de kullanabilirsiniz. Ancak, tipik özellik öğesi söz dizimi için belirttiğiniz *TypeName* , Property öğesini içeren Object öğesidir. Ekli bir özelliğe başvuruyorsanız *TypeName* , içerilen nesne öğesi değil, ekli özelliği tanımlayan sınıftır.  
  
<a name="attached_events"></a>   
## <a name="attached-events"></a>Ekli Olaylar  
 Ekli olaylar XAML 'de sunulan ve olayların belirli bir tür tarafından tanımlanbildiği, ancak işleyicilerin herhangi bir nesne öğesine eklenmiş olabileceği başka bir programlama kavramıdır. WOF uygulamasında, genellikle ekli olayı tanımlayan tür bir hizmeti tanımlayan statik bir türdür ve bazen bu ekli olaylar, hizmeti kullanıma sunan türlerde bir yönlendirilmiş olay diğer adı tarafından gösterilir. Ekli olaylara yönelik işleyiciler öznitelik sözdizimi aracılığıyla belirtilir. Ekli olaylarda olduğu gibi, öznitelik sözdizimi bir *TypeName*'e izin vermek için eklenmiş olaylar için genişletilir. *EventName* kullanımı, *TypeName* , ekli olay altyapısı için `Add` ve `Remove` olay işleyicisi erişimcileri sağlayan sınıftır ve *EventName* olay adıdır.  
  
<a name="anatomy_of_a_xaml_page_root_element"></a>   
## <a name="anatomy-of-a-xaml-root-element"></a>XAML kök öğesinin anatomumu  
 Aşağıdaki tabloda, bir kök öğenin belirli özniteliklerinin gösterildiği tipik bir XAML kök öğe gösterilmektedir:  
  
|||  
|-|-|  
|`<Page`|Kök öğenin nesne öğesi açılıyor|  
|`xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`|Varsayılan ([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]) XAML ad alanı|  
|`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`|XAML Language XAML ad alanı|  
|`x:Class="ExampleNamespace.ExampleCode"`|Biçimlendirmeyi kısmi sınıf için tanımlanan herhangi bir koda bağlayan kısmi sınıf bildirimi|  
|`>`|Kök için nesne öğesi sonu. Öğe, alt öğeler içerdiğinden henüz kapatılmadı|  
  
<a name="optional_and_nonrecommended_xaml_usages"></a>   
## <a name="optional-and-nonrecommended-xaml-usages"></a>İsteğe bağlı ve önerilmeyen XAML kullanımları  
 Aşağıdaki bölümlerde, xaml işlemciler tarafından Teknik olarak desteklenen XAML kullanımları açıklanır, ancak XAML kaynakları içeren uygulamalar geliştirirken, daha fazla ayrıntı veya diğer Aesthetic Characteristics sorunları yaşabilir.  
  
### <a name="optional-property-element-usages"></a>İsteğe bağlı özellik öğesi kullanımları  
 İsteğe bağlı özellik öğesi kullanımları, XAML işlemcisinin örtük olarak niteledüğü öğe içeriği özelliklerinin açıkça yazılmasını içerir. Örneğin, bir <xref:System.Windows.Controls.Menu>içeriğini bildirdiğinizde, bir <xref:System.Windows.Controls.MenuItem> öğesinin tüm alt öğelerinin bir `<Menu.Items>`olması ve <xref:System.Windows.Controls.Menu> koleksiyonuna yerleştirilmesi gereken örtük XAML işlemci davranışını kullanmak yerine, <xref:System.Windows.Controls.Menu> <xref:System.Windows.Controls.ItemsControl.Items%2A> koleksiyonunu bir `<Menu.Items>` Özellik öğesi etiketi olarak açıkça bildirmeyi ve her bir <xref:System.Windows.Controls.MenuItem> <xref:System.Windows.Controls.ItemsControl.Items%2A> içine yerleştirmeyi seçebilirsiniz. Bazen isteğe bağlı kullanımlar, biçimlendirme içinde temsil edildiği şekilde nesne yapısını görsel açıdan açıklığa kavuşturmanıza yardımcı olabilir. Ya da bazen bir açık özellik öğesi kullanımı, bir öznitelik değeri içinde iç içe geçmiş biçimlendirme uzantıları gibi teknik olarak işlev gösteren ancak görsel açıdan karmaşık olan işaretlemeleri önleyebilir.  
  
### <a name="full-typenamemembername-qualified-attributes"></a>Tam typeName. memberName nitelenmiş öznitelikler  
 *TypeName*. bir öznitelik için *ÜyeForm* aslında yalnızca yönlendirilmiş olay durumundan daha fazla evrensel olarak çalışmaktadır. Ancak, formun gereksiz olduğu ve yalnızca biçimlendirme stili ve okunabilirlik nedenleriyle bu durumda kaçınmalısınız. Aşağıdaki örnekte, <xref:System.Windows.Controls.Control.Background%2A> özniteliğine yapılan üç başvuru tamamen eşdeğerdir:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenameprop)]  
  
 `Button.Background`, <xref:System.Windows.Controls.Button> üzerinde bu özellik için tam arama başarılı olduğundan (<xref:System.Windows.Controls.Control.Background%2A> denetimden Devralındığı için) ve <xref:System.Windows.Controls.Button> nesne öğesinin ya da bir temel sınıfın sınıfı olduğundan işe yarar. `Control.Background`, <xref:System.Windows.Controls.Control> sınıfı gerçekten <xref:System.Windows.Controls.Control.Background%2A> tanımladığından ve <xref:System.Windows.Controls.Control> <xref:System.Windows.Controls.Button> temel sınıfı olduğundan, bu işe yarar.  
  
 Ancak, aşağıdaki *TypeName*. *MemberName* form örneği çalışmıyor ve bu nedenle açıklama gösteriliyor:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameBadProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenamebadprop)]  
  
 <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Control>başka bir türetilmiş sınıftır ve <xref:System.Windows.Controls.Label> nesne öğesi içinde `Label.Background` belirtseydi, bu kullanım çalıştık. Ancak, <xref:System.Windows.Controls.Label> sınıfı veya temel <xref:System.Windows.Controls.Button>sınıfı olmadığından, belirtilen XAML işlemcisi davranışı, daha sonra `Label.Background` iliştirilmiş bir özellik olarak İşlidir. `Label.Background`, kullanılabilir bir ekli özellik değildir ve bu kullanım başarısız olur.  
  
### <a name="basetypenamemembername-property-elements"></a>baseTypeName. memberName özellik öğeleri  
 *TypeName*öğesine benzer bir şekilde. *MemberName* formu, *temel bir typeName*olan öznitelik sözdizimi için kullanılır. *MemberName* sözdizimi Özellik öğesi sözdizimi için geçerlidir. Örneğin, aşağıdaki sözdizimi işe yarar:  
  
 [!code-xaml[XAMLOvwSupport#GoofyPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofype)]  
  
 Burada Özellik öğesi `Button`içerilse de `Control.Background` olarak verilmiştir.  
  
 Yalnızca *TypeName*gibi. öznitelikler için *ÜyeForm* , *BaseTypeName*. *MemberName* , biçimlendirmede zayıf bir stil ve bundan kaçınılmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [XAML Ad Alanı (x:) Dil Özellikleri](../../../desktop-wpf/xaml-services/namespace-language-features.md)
- [WPF XAML Uzantıları](wpf-xaml-extensions.md)
- [Bağımlılık Özelliklerine Genel Bakış](dependency-properties-overview.md)
- [TypeConverters ve XAML](typeconverters-and-xaml.md)
- [WPF için XAML ve Özel Sınıflar](xaml-and-custom-classes-for-wpf.md)
