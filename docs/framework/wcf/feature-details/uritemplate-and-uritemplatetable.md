---
title: UriTemplate ve UriTemplateTable
ms.date: 03/30/2017
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
ms.openlocfilehash: 212cc0a7f90ac2e74837118a905519148ddc089d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289678"
---
# <a name="uritemplate-and-uritemplatetable"></a>UriTemplate ve UriTemplateTable

Web geliştiricileri, hizmetlerinin yanıt verdiği URI 'lerin şeklini ve yerleşimini betimleyebilme olanağı gerektirir. Windows Communication Foundation (WCF), geliştiricilerin URI 'lerinde denetim sağlamak için iki yeni sınıf ekledi. <xref:System.UriTemplate> ve <xref:System.UriTemplateTable> WCF 'de URI tabanlı dağıtım altyapısının temelini oluşturur. Bu sınıflar kendi kendilerine de kullanılabilir, geliştiricilerin bir WCF hizmeti uygulamadan şablonlardan ve URI eşleme mekanizmasından yararlanmasını sağlar.  
  
## <a name="templates"></a>Şablonlar  

 Şablon, göreli URI 'lerin bir kümesini tanımlamaya yönelik bir yoldur. Aşağıdaki tabloda yer alan URI şablonları kümesi, çeşitli hava durumu bilgilerini alan bir sistemin nasıl tanımlanabilir olduğunu gösterir.  
  
|Veriler|Şablon|  
|----------|--------------|  
|Ulusal tahmin|Hava durumu/Ulusal|  
|Durum tahmini|Hava durumu/{State}|  
|Şehir tahmini|Hava durumu/{State}/{City}|  
|Etkinlik tahmini|Hava durumu/{State}/{City}/{Activity}|  
  
 Bu tablo yapısal olarak benzer URI 'Ler kümesini açıklar. Her giriş bir URI şablonudur. Küme ayraçları içindeki segmentler değişkenleri anlatmaktadır. Küme ayraçları içinde olmayan kesimler, değişmez dizeleri tanımlıyor. WCF şablon sınıfları, bir geliştiricinin gelen URI 'yi (örneğin, "/Weather/WA/Seattle/Cycling") alıp onu açıklayan bir şablonla eşleştirmek için "/dalgalı ther/{State}/{City}/{Activity}" sağlar.  
  
## <a name="uritemplate"></a>UriTemplate  

 <xref:System.UriTemplate> , bir URI şablonunu kapsülleyen bir sınıftır. Oluşturucu, şablonu tanımlayan bir dize parametresi alır. Bu dize, sonraki bölümde açıklanan biçimdeki şablonu içerir. Sınıfı, bir <xref:System.UriTemplate> şablon için gelen URI 'yi eşleştirmek, bir ŞABLONDAN URI oluşturmak, şablonda kullanılan değişken adlarından oluşan bir koleksiyonu almak, iki şablonun eşdeğer olup olmadığını tespit etmek ve şablonun dizesini döndürmeksizin yöntemler sağlar.  
  
 <xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> temel bir adresi ve aday URI 'yi alır ve URI 'yi şablonla eşleştirmeye çalışır. Eşleşme başarılı olursa bir <xref:System.UriTemplateMatch> örnek döndürülür. <xref:System.UriTemplateMatch>Nesne bir temel URI içerir, aday URI, sorgu parametrelerinin ad/değer koleksiyonu, göreli yol segmentlerinin bir dizisi, eşleşen değişkenlerin bir adı/değer koleksiyonu, <xref:System.UriTemplate> karşılamanın yerine getirmek için kullanılan örnek, aday URI 'sinin eşleşmeyen herhangi bir bölümünü (şablon bir joker karakter olduğunda kullanılır) ve şablonla ilişkili bir nesneyi içeren bir dize.  
  
> [!NOTE]
> <xref:System.UriTemplate>Sınıf, bir aday URI 'yi bir şablonla eşleştirirken düzen ve bağlantı noktası numarasını yoksayar.  
  
 Bir şablondan URI oluşturmanıza izin veren iki yöntem vardır <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> ve <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> . <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> bir taban adresi ve parametrelerin ad/değer koleksiyonunu alır. Bu parametreler, şablon bağlandığında değişkenler için değiştirilir. <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> ad/değer çiftlerini alır ve bunları soldan sağa koyar.  
  
 <xref:System.UriTemplate.ToString> Şablon dizesini döndürür.  
  
 <xref:System.UriTemplate.PathSegmentVariableNames%2A>Özelliği, şablon dizesindeki yol kesimleri içinde kullanılan değişkenlerin adlarının bir koleksiyonunu içerir.  
  
 <xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> bir <xref:System.UriTemplate> parametresini parametre olarak alır ve iki şablonun eşdeğer olup olmadığını belirten bir Boole değeri döndürür. Daha fazla bilgi için bu konunun ilerleyen kısımlarında yer alarak şablon denklik bölümüne bakın.  
  
 <xref:System.UriTemplate> , HTTP URI dilbilgisine uygun herhangi bir URI şeması ile çalışacak şekilde tasarlanmıştır. Aşağıda desteklenen URI düzenlerinin örnekleri verilmiştir.  
  
- `http://`  
  
- `https://`  
  
- `net.tcp://`  
  
- `net.pipe://`  
  
- `sb://`  
  
 File://ve urn://gibi düzenler HTTP URI dilbilgisine uymuyor ve URI şablonlarıyla birlikte kullanıldığında öngörülemeyen sonuçlara neden olur.  
  
### <a name="template-string-syntax"></a>Şablon dizesi sözdizimi  

 Şablon üç bölümden oluşur: yol, isteğe bağlı sorgu ve isteğe bağlı bir parça. Bir örnek için, aşağıdaki şablona bakın:  
  
`"/weather/{state}/{city}?forecast={length)#frag1`  
  
 Yol "/dalgalı ther/{State}/{City}" bilgisinden oluşur, sorgu "? tahmine = {length} ve parça" #frag1 "bilgisinden oluşur.  
  
 Yol ifadesinde öndeki ve sondaki eğik çizgiler isteğe bağlıdır. Hem sorgu hem de parça ifadeleri tamamen atlanabilir. Bir yol, '/' ile ayrılmış bir dizi kesimden oluşur, her segment bir sabit değer, değişken adı ({küme ayraçları} içinde yazılmış) veya joker karakter (' ' olarak yazılmış \* ) olabilir. Önceki şablonda, "{State}" ve "{City}" değişkenleri olan "\dalgalı ther\ segmenti değişmez değer değeridir. Değişkenler, bunların adlarını kendi küme ayraçları içeriğinden alır ve daha sonra *kapalı bır URI* oluşturmak için somut bir değer ile değiştirilebilir. Joker karakter isteğe bağlıdır, ancak yalnızca URI sonunda görünebilir, burada "yolun geri kalanı" ile mantıksal olarak eşleşir.  
  
 Sorgu ifadesi varsa, ' & ' ile ayrılmış bir sıralı ad/değer çiftleri serisi belirtir. Sorgu ifadesinin öğeleri, sabit değer çiftleri (x = 2) veya bir değişken çifti (x = {var}) olabilir. Sorgunun yalnızca sağ tarafında bir değişken ifadesi olabilir. ({someName} = {someValue} öğesine izin verilmiyor. Eşlenmemiş değerlere (? x) izin verilmez. Boş bir sorgu ifadesi ve yalnızca tek bir '? ' içeren bir sorgu ifadesi arasında fark yoktur (her ikisi de "herhangi bir sorgu").  
  
 Parça ifadesi bir değişmez değerden oluşabilir, hiçbir değişkene izin verilmez.  
  
 Bir şablon dizesi içindeki tüm şablon değişken adları benzersiz olmalıdır. Şablon değişken adları büyük/küçük harfe duyarlıdır.  
  
 Geçerli şablon dizeleri örnekleri:  
  
- ""  
  
- "/Shoe"  
  
- "/Shoe/ \* "  
  
- "{Shoe}/bot"  
  
- "{Shoe}/{Boat}/Bed/{Quilt}"  
  
- "Shoe/{bot}"  
  
- "Shoe/{bot}/ \* "  
  
- "Shoe/bot? x = 2"  
  
- "Shoe/{bot}? x = {yatak}"  
  
- "Shoe/{bot}? x = {yatak} &y = bant"  
  
- "? x = {Shoe}"  
  
- "Shoe? x = 3&y = {var}  
  
 Geçersiz şablon dizeleri örnekleri:  
  
- "{Shoe}/{SHOE}/x = 2" – yinelenen değişken adları.  
  
- "{Shoe}/Boat/? yatak = {Shoe}"-yinelenen değişken adları.  
  
- "? x = 2&x = 3" – bir sorgu dizesi içindeki ad/değer çiftleri, değişmez değerler olsa bile benzersiz olmalıdır.  
  
- "? x = 2&" – sorgu dizesi hatalı biçimlendirilmiş.  
  
- "? 2&x = {Shoe}" – sorgu dizesi ad/değer çiftleri olmalıdır.  
  
- "? y = 2&&X = 3" – sorgu dizesi ad değer çiftleri olmalıdır, adlar ' & ' ile başlayamaz.  
  
### <a name="compound-path-segments"></a>Bileşik yol kesimleri  

 Bileşik yol kesimleri, tek bir URI yol segmentinin birden çok değişken ve değişmez değerler ile birleştirilmiş değişkenler içermesini sağlar. Aşağıda geçerli bileşik yol segmentlerinin örnekleri verilmiştir.  
  
- kısaltın. {ext}/  
  
- /{filename}.exe jpg/  
  
- kısaltın. {ext}/  
  
- a. {b} someLiteral {c} ({d})/  
  
 Aşağıda geçersiz yol kesimlerinin örnekleri verilmiştir.  
  
- / {} -Değişkenlerin adlandırılması gerekir.  
  
- /{Shoe}{Boat}-değişkenlerin bir sabit değer ile ayrılması gerekir.  
  
### <a name="matching-and-compound-path-segments"></a>Eşleşen ve bileşik yol kesimleri  

 Bileşik yol kesimleri, tek bir yol segmentinde birden çok değişken içeren bir UriTemplate tanımlamanızı sağlar. Örneğin, şu şablon dizesinde: "adresler/{State}. {City} "iki değişken (eyalet ve şehir) aynı segment içinde tanımlanır. Bu şablon gibi bir URL ile eşleşir `http://example.com/Washington.Redmond` , ancak aynı zamanda gibi BIR URL ile eşleşir `http://example.com/Washington.Redmond.Microsoft` . İkinci durumda, durum değişkeni "Washington" ve City değişkeni "Redmond. Microsoft" içerecektir. Bu durumda, herhangi bir metin ('/' hariç) {City} değişkeniyle eşleşir. "Ekstra" metinle eşleşmeyen bir şablon istiyorsanız, değişkeni ayrı bir şablon kesimine yerleştirin, örneğin: "adresler/{State}/{City}.  
  
### <a name="named-wildcard-segments"></a>Adlandırılmış joker kesimleri  

 Adlandırılmış joker karakter segmenti, değişken adı ' ' joker karakteriyle başlayan herhangi bir yol değişkeni segmentdir \* . Aşağıdaki şablon dizesi "Shoe" adlı adlandırılmış bir joker karakter segmentini içerir.  
  
`"literal/{*shoe}"`  
  
 Joker karakter kesimleri aşağıdaki kurallara uymalıdır:  
  
- Her bir şablon dizesi için en fazla bir adlandırılmış joker karakter segmenti olabilir.  
  
- Adlandırılmış bir joker karakter segmenti, yoldaki en sağ kesimde görünmelidir.  
  
- Adlandırılmış bir joker karakter segmenti aynı şablon dizesinde anonim bir joker karakterle birlikte bulunamaz.  
  
- Adlandırılmış bir joker karakter kesiminin adı benzersiz olmalıdır.  
  
- Adlandırılmış joker karakter kesimleri varsayılan değerlere sahip olamaz.  
  
- Adlandırılmış joker kesimleri "/" ile bitemez.  
  
### <a name="default-variable-values"></a>Varsayılan değişken değerleri  

 Varsayılan değişken değerleri bir şablon içindeki değişkenler için varsayılan değerleri belirtmenize izin verir. Varsayılan değişkenler, değişkeni bildiren küme ayraçları ile veya UriTemplate oluşturucusuna geçirilen bir koleksiyon olarak belirtilebilir. Aşağıdaki şablonda, <xref:System.UriTemplate> varsayılan değerleri olan değişkenleri içeren bir belirtmek için iki yol gösterilmektedir.  
  
```csharp
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 Bu şablon, varsayılan değeri olan adlı bir değişken `a` `1` ve `b` varsayılan değeri olan adlı bir değişken bildirir `5` .  
  
> [!NOTE]
> Yalnızca yol kesimi değişkenlerinin varsayılan değerlere sahip olmasına izin verilir. Sorgu dizesi değişkenleri, bileşik kesim değişkenleri ve adlandırılmış joker dizeler varsayılan değerlere sahip olamaz.  
  
 Aşağıdaki kod, bir aday URI ile eşleştirilirken varsayılan değişken değerlerinin nasıl işlendiğini gösterir.  
  
```csharp
Uri baseAddress = new Uri("http://localhost:8000/");

UriTemplate t = new UriTemplate("/{state=WA}/{city=Redmond}/", true);
Uri candidate = new Uri("http://localhost:8000/OR");

UriTemplateMatch m1 = t.Match(baseAddress, candidate);

Console.WriteLine($"Template: {t}");
Console.WriteLine($"Candidate URI: {candidate}");

// Display contents of BoundVariables
Console.WriteLine("BoundVariables:");
foreach (string key in m1.BoundVariables.AllKeys)
{
    Console.WriteLine($"\t{key}={m1.BoundVariables[key]}");
}
// The output of the above code is  
// Template: /{state=WA}/{city=Redmond}/
// Candidate URI: http://localhost:8000/OR
// BoundVariables:
//         STATE=OR
//         CITY=Redmond
```  
  
> [!NOTE]
> Gibi bir URI `http://localhost:8000///` , önceki kodda listelenen şablonla eşleşmez, ancak gibi BIR URI `http://localhost:8000/` .  
  
 Aşağıdaki kod, bir şablon ile URI oluştururken varsayılan değişken değerlerinin nasıl işlendiğini gösterir.  
  
```csharp
Uri baseAddress = new Uri("http://localhost:8000/");  
Dictionary<string,string> defVals = new Dictionary<string,string> {{"a","1"}, {"b", "5"}};  
UriTemplate t = new UriTemplate("/test/{a}/{b}", defVals);  
NameValueCollection vals = new NameValueCollection();  
vals.Add("a", "10");  
  
Uri boundUri = t.BindByName(baseAddress, vals);  
Console.WriteLine("BaseAddress: {0}", baseAddress);  
Console.WriteLine("Template: {0}", t.ToString());  
  
Console.WriteLine("Values: ");  
foreach (string key in vals.AllKeys)  
{  
    Console.WriteLine("\tKey = {0}, Value = {1}", key, vals[key]);  
}  
Console.WriteLine("Bound URI: {0}", boundUri);  
  
// The output of the preceding code is  
// BaseAddress: http://localhost:8000/  
// Template: /test/{a}/{b}  
// Values:  
//     Key = a, Value = 10  
// Bound URI: http://localhost:8000/test/10/5  
```  
  
Bir değişkene varsayılan değer verildiğinde, `null` bazı ek kısıtlamalar vardır. Değişken, `null` şablon dizesinin en sağ alt segmentinde yer alıyorsa veya segmentin sağ tarafındaki tüm segmentlerin varsayılan değerleri içeriyorsa, bir değişken varsayılan değeri olabilir `null` . Aşağıda varsayılan değerleri olan geçerli şablon dizeleri verilmiştir `null` :  
  
- `UriTemplate t = new UriTemplate("shoe/{boat=null}");`

- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");`
  
- `UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");`

 Varsayılan değerleri geçersiz olan şablon dizeleri aşağıda verilmiştir `null` :  
  
- `UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment`
  
- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value`

### <a name="default-values-and-matching"></a>Varsayılan değerler ve eşleştirme  

 Bir aday URI 'yi varsayılan değerlere sahip bir şablonla eşleştirirken, <xref:System.UriTemplateMatch.BoundVariables%2A> aday URI 'sinde değerler belirtilmemişse varsayılan değerler koleksiyona yerleştirilir.  
  
### <a name="template-equivalence"></a>Şablon denklik  

 Tüm şablonların sabit değerleri eşleşiyorsa ve aynı kesimlerde değişkenler olduğunda, iki şablon *yapısal olarak eşdeğer* olarak kabul edilir. Örneğin, aşağıdaki şablonlar yapısal olarak eşdeğerdir:  
  
- /a/{var1}/b b/{var2}? x = 1&y = 2  
  
- a/{x}/b% 20B/{var1}? y = 2&x = 1  
  
- a/{y}/B% 20B/{z}/? y = 2&x = 1  
  
 Dikkat etmeniz gereken birkaç nokta vardır:  
  
- Bir şablon önünde eğik çizgi içeriyorsa, yalnızca ilki yok sayılır.  
  
- Yapısal denklik için şablon dizelerini karşılaştırırken, değişken adları ve yol kesimleri için durum yoksayıldı, sorgu dizeleri büyük/küçük harfe duyarlıdır.  
  
- Sorgu dizeleri sırasız.  
  
## <a name="uritemplatetable"></a>UriTemplateTable  

 <xref:System.UriTemplateTable>Sınıfı, <xref:System.UriTemplate> geliştiricinin seçme nesnesine bağlantılı nesnelerin ilişkilendirilebilir tablosunu temsil eder. ' Nin <xref:System.UriTemplateTable> çağrılmadan önce en az bir tane içermesi gerekir <xref:System.UriTemplate> <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> . Bir öğesinin içeriği <xref:System.UriTemplateTable> <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> çağrılana kadar değiştirilebilir. Çağrıldığında doğrulama gerçekleştirilir <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> . Gerçekleştirilen doğrulamanın türü, parametresinin değerine bağlıdır `allowMultiple` <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> .  
  
 <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>İçinde geçirme çağrıldığında, `false` <xref:System.UriTemplateTable> tabloda hiçbir şablon olmadığından emin olmak için kontrol eder. Yapısal olarak eşdeğer şablonlar bulursa, bir özel durum oluşturur. Bu, bir <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> gelen URI ile eşleşen yalnızca bir şablonun olduğundan emin olmak istediğiniz zaman ile birlikte kullanılır.  
  
 <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>İçinde geçirme çağrıldığında `true` , <xref:System.UriTemplateTable> birden çok, yapısal olarak denk şablonların bir içinde yer almasına izin verir <xref:System.UriTemplateTable> .  
  
 <xref:System.UriTemplate>Bir nesne kümesine eklenen bir <xref:System.UriTemplateTable> sorgu dizesi varsa, bunların belirsiz olmaması gerekir. Özdeş sorgu dizelerine izin verilir.  
  
> [!NOTE]
> HTTP dışındaki <xref:System.UriTemplateTable> şemaları kullanan temel adreslere izin verdiğinden, aday URI 'leri şablonlarla eşleştirilirken düzen ve bağlantı noktası numarası yok sayılır.  
  
### <a name="query-string-ambiguity"></a>Sorgu dizesi belirsizlik  

 Bir eşdeğer yolu paylaşan şablonlar, birden fazla şablonla eşleşen bir URI varsa belirsiz sorgu dizeleri içerir.  
  
 Aşağıdaki sorgu dizeleri kümeleri kendi içinde belirsiz:  
  
- ? x = 1  
  
- ? x = 2  
  
- ? x = 3  
  
- ? x = 1&y = {var}  
  
- ? x = 2&z = {var}  
  
- ? x = 3  
  
- ? x = 1  
  
- ?  
  
- ? x = {var}  
  
- ?  
  
- ? m = Get&c = RSS  
  
- ? m = put&c = RSS  
  
- ? m = Get&c = atom  
  
- ? m = put&c = atom  
  
 Aşağıdaki sorgu dizesi şablonları kümeleri kendileri içinde belirsizdir:  
  
- ? x = 1  
  
- ? x = {var}  
  
 "x = 1"-her iki şablon da eşleşir.  
  
- ? x = 1  
  
- ? y = 2  
  
 "x = 1&y = 2", her iki şablonlarla de eşleşir. Bunun nedeni, bir sorgu dizesinin daha fazla sorgu dizesi değişkeni içermesi olabilir ve bundan sonra eşleşen şablondur.  
  
- ? x = 1  
  
- ? x = 1&y = {var}  
  
 "x = 1&y = 3" her iki şablonlarla de eşleşir.  
  
- ? x = 3&y = 4  
  
- ? x = 3&z = 5  
  
> [!NOTE]
> Á ve Á karakterleri, bir URI yolu veya yol segmenti değişmez değerinin bir parçası olarak görüntülendiklerinde farklı karakterler olarak değerlendirilir <xref:System.UriTemplate> (ancak a ve a karakterleri aynı olduğu kabul edilir). Á ve Á karakterleri, bir <xref:System.UriTemplate> {VariableName} veya bir sorgu dizesinin (ve ' de aynı karakterler olarak kabul edilir) bir parçası olarak göründükleri karakterlerle aynı karakterler olarak değerlendirilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Web HTTP Programlama Modeli Genel Bakış](wcf-web-http-programming-model-overview.md)
- [WCF Web HTTP Programlama Nesnesi Modeli](wcf-web-http-programming-object-model.md)
- [UriTemplate](../samples/uritemplate-sample.md)
- [UriTemplate Tablosu](../samples/uritemplate-table-sample.md)
- [UriTemplate Tablosu Dağıtıcısı](../samples/uritemplate-table-dispatcher-sample.md)
