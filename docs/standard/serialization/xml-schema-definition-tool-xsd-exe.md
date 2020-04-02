---
title: XML şema tanımı Aracı (XSD.exe'nin)
ms.date: 03/30/2017
ms.assetid: a6e6e65c-347f-4494-9457-653bf29baac2
ms.openlocfilehash: cd017eb1866fff2ce8fd7a858b184351ef13e815
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588343"
---
# <a name="xml-schema-definition-tool-xsdexe"></a>XML şema tanımı Aracı (XSD.exe'nin)

XML şema tanımı (XSD.exe'nin) aracı XDR, XML ve XSD dosyalarından veya bir çalışma zamanı derleme sınıflarda XML Şeması veya ortak dil çalışma zamanı sınıflar oluşturur.

## <a name="syntax"></a>Sözdizimi

Aracı komut satırından çalıştırın.

```console
xsd file.xdr [-outputdir:directory][/parameters:file.xml]
xsd file.xml [-outputdir:directory] [/parameters:file.xml]
xsd file.xsd {/classes | /dataset} [/element:element]
             [/enableLinqDataSet] [/language:language]
                          [/namespace:namespace] [-outputdir:directory] [URI:uri]
                          [/parameters:file.xml]
xsd {file.dll | file.exe} [-outputdir:directory] [/type:typename [...]][/parameters:file.xml]
```
  
> [!TIP]
> .NET Framework araçlarının düzgün çalışması için `Path`, `Include`ve `Lib` çevre değişkenlerinizi doğru ayarlamanız gerekir. \<SDK>\v2.0\Bin dizininde bulunan SDKVars.bat'ı çalıştırarak bu ortam değişkenlerini ayarlayın. Her komut kabuğu'nu SDKVars.bat yürütülmelidir.

## <a name="argument"></a>Bağımsız Değişken

|Bağımsız Değişken|Açıklama|
|--------------|-----------------|
|*file.extension*|Dönüştürülecek giriş dosyasını belirtir. Uzantıyı aşağıdakilerden biri olarak belirtmeniz gerekir: .xdr, .xml, .xsd, .dll veya .exe.<br /><br /> XDR şema dosyası (.xdr uzantısı) belirtirseniz, xsd.exe'nin bir XSD şemasına XDR şeması dönüştürür. Çıkış dosyası XDR şeması, ancak .xsd uzantısı ile aynı ada sahip.<br /><br /> Bir XML dosyası (.xml uzantısı) belirtirseniz, xsd.exe'nin veri dosyasındaki bir şema öğesinin ve bir XSD şeması üretir. Çıkış dosyası XML dosyası olarak, ancak .xsd uzantısı ile aynı ada sahip.<br /><br /> Bir XML şema dosyası (.xsd uzantısı) belirtirseniz, xsd.exe'nin için XML Şeması karşılık gelen çalışma zamanı nesneler için kaynak kodu oluşturur.<br /><br /> Bir çalışma zamanı derleme dosyası (.exe veya .dll uzantısı) belirtirseniz, xsd.exe'nin şemaları bir veya daha fazla türleri için bu derlemede oluşturur. Kullanabilirsiniz `/type` şemaları oluşturulacak türlerini belirtmek için seçeneği. Çıkış şemaları schema0.xsd, schema1.xsd vb. adlandırılır. Xsd.exe, yalnızca verilen türler `XMLRoot` özel özniteliğini kullanarak bir ad alanı belirtirse birden çok şema üretir.|

## <a name="general-options"></a>Genel seçenekleri

|Seçenek|Açıklama|
|------------|-----------------|
|**/h\[elp\]**|Araç için komut sözdizimini ve seçenekleri görüntüler.|
|**/o\[utputdir\]:**_dizin_|Çıktı dosyaları dizinini belirtir. Bu bağımsız değişken yalnızca bir kez görünebilir. Geçerli dizin varsayılandır.|
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|
|**/p\[\]arameters :**_file.xml_|Çeşitli işlem modları için seçenekler belirtilen .xml dosyasından okuyun. Kısa form `/p:`. Daha fazla bilgi için [Açıklamalar](#remarks) bölümüne bakın.|

## <a name="xsd-file-options"></a>XSD dosyası seçenekleri
 .Xsd dosyaları için aşağıdaki seçeneklerden birini belirtmelisiniz.

|Seçenek|Açıklama|
|------------|-----------------|
|**/c\[lasses\]**|Belirtilen şemaya karşılık gelen sınıflar oluşturur. XML verilerini nesneye okumak için <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A?displayProperty=nameWithType> yöntemi kullanın.|
|**/d\[ataset\]**|Türetilen bir sınıf oluşturur <xref:System.Data.DataSet> belirtilen şemaya karşılık gelir. XML verilerini türetilmiş sınıfa <xref:System.Data.DataSet.ReadXml%2A?displayProperty=nameWithType> okumak için yöntemi kullanın.|

 .Xsd dosyaları için aşağıdaki seçeneklerden birini belirleyebilirsiniz.

|Seçenek|Açıklama|
|------------|-----------------|
|**/e\[lement\]:**_eleman_|Öğe için kod oluşturmak için şema belirtir. Varsayılan olarak tüm öğeler yazılmalıdır. Bu bağımsız değişken birden çok kez belirtebilirsiniz.|
|**/enableDataBinding**|Uygular <xref:System.ComponentModel.INotifyPropertyChanged> veri bağlama etkinleştirmek için oluşturulan tüm türleri arabirimi. Kısa form `/edb`.|
|**/enableLinqDataSet**|(Kısa form: `/eld`.) Oluşturulan DataSet'in LINQ'dan DataSet'e karşı sorgulanabileceğini belirtir. Bu seçenek /dataset seçeneği de belirtildiğinde kullanılır. Daha fazla bilgi için [LINQ to DataSet Genel Bakış](../../../docs/framework/data/adonet/linq-to-dataset-overview.md) ve [Yazılı Veri Kümelerini Sorgula'ya](../../../docs/framework/data/adonet/querying-typed-datasets.md)bakın. LINQ kullanımı hakkında genel bilgi için bkz: [Dil-Tümleşik Sorgu (LINQ) - C#](../../csharp/programming-guide/concepts/linq/index.md) veya [Dil-Tümleşik Sorgu (LINQ) - Visual Basic](../../visual-basic/programming-guide/concepts/linq/index.md).|
|**/f\[ields\]**|Alanları özellikleri yerine oluşturur. Varsayılan olarak, özellikleri üretilir.|
|**/l\[\]anguage :**_dil_|Kullanmak için programlama dilini belirtir. Aralarından seçim `CS` (C varsayılan değer olan #), `VB` (Visual Basic) `JS` (JScript) veya `VJS` (Visual J#). Ayrıca bir sınıf uygulamak için tam bir ad belirtin<xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>|
|**/n\[amespace\]:**_namespace_|Oluşturulan türleri için çalışma zamanı ad alanını belirtir. Varsayılan ad alanı `Schemas`.|
|**/nologo**|Başlık göstermez.|
|**/sipariş**|Tüm parçacık üyeleri açık sipariş tanımlayıcılarını oluşturur.|
|**/o\[\]ut :**_directoryName_|Dosyalarında yerleştirmek için çıktı dizini belirtir. Geçerli dizin varsayılandır.|
|**/u\[\]ri :**_uri_|Öğeler için URI için kod oluşturmak için şema belirtir. Bu URI varsa, ile belirtilen tüm öğelere uygulanır `/element` seçeneği.|

## <a name="dll-and-exe-file-options"></a>DLL ve EXE dosya seçenekleri

|Seçenek|Açıklama|
|------------|-----------------|
|**/t\[ype\]:** yazı_adı_|Şema için oluşturulacak tür adını belirtir. Birden çok tür bağımsız değişkeni belirtebilirsiniz. *Ad adı* bir ad alanı belirtmiyorsa, Xsd.exe belirtilen türile montajdaki tüm türleri eşleşir. *Tür adı* bir ad alanı belirtirse, yalnızca bu tür eşleşir. *Tür adı* yıldız karakteriyle biterse (\*), araç . \* Unutursanız, `/type` seçeneği XSD.exe'nin derlemesinde tüm türler için şemalar oluşturur.|

## <a name="remarks"></a>Açıklamalar

Aşağıdaki tablo operasyonları XSD.exe'nin gerçekleştireceğini gösterir.

| | |
|------------|-----------------|
|XDR XSD için|Bir XML şeması bir XML veri azaltılmış şema dosyasından oluşturur. XDR erken bir XML tabanlı şema biçimidir.|
|XML için XSD|Bir XML Şeması XML dosyasından oluşturur.|
|Veri kümesi için XSD|Ortak dil çalışma zamanı oluşturur <xref:System.Data.DataSet> bir XSD şema dosyasından sınıfları. Oluşturulan sınıflar için normal XML verileri zengin nesne modeli sağlar.|
|XSD sınıflar için|Bir XSD şema dosyasından çalışma zamanı sınıflar oluşturur. Oluşturulan sınıflar birlikte kullanılabilecek <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> okuma ve yazma şema izleyen XML kodu.|
|XSD için sınıflar| Bir XML şeması bir türü veya türleri bir çalışma zamanı derleme dosyası oluşturur. Oluşturulan şema tarafından kullanılan XML biçimini <xref:System.Xml.Serialization.XmlSerializer>tanımlar.|

 XSD.exe'nin yalnızca World Wide Web Konsorsiyumu (W3C) tarafından önerilen XML şema tanımı (XSD) dil izleyin XML şemaları yönetmenize olanak sağlar. XML Şema Tanımı önerisi veya XML standardı hakkında <https://w3.org>daha fazla bilgi için bkz.

## <a name="setting-options-with-an-xml-file"></a>Bir XML dosyası ile seçenekleri ayarlama

`/parameters` Anahtarı kullanarak, çeşitli seçenekler ayarlayan tek bir XML dosyası belirtebilirsiniz. Nasıl XSD.exe'nin aracını kullanarak ayarlayabilirsiniz seçenekler bağlıdır. Seçenekler şunlardır şemaları oluşturmak, kod dosyaları oluşturmak veya dahil kod dosyaları oluşturmak `DataSet` özellikleri. Örneğin, ayarlayabilirsiniz `<assembly>` öğesi için bir yürütülebilir (.exe) veya bir şema oluşturulurken türü kitaplık (.dll) dosyası, ancak bir kod dosyası değil oluşturulurken adı. Aşağıdaki XML nasıl kullanılacağı gösterilmiştir `<generateSchemas>` belirtilen yürütülebilir öğe:

```xml
<!-- This is in a file named GenerateSchemas.xml. -->
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateSchemas>
   <assembly>ConsoleApplication1.exe</assembly>
</generateSchemas>
</xsd>
```

Önceki XML GenerateSchemas.xml adlı bir dosyada yer alıyorsa, komut isteminde aşağıdakileri yazarak ve `/parameters` **Enter**tuşuna basarak anahtarı kullanın:

```console
 xsd /p:GenerateSchemas.xml
```

Diğer yandan, derlemede bulunan tek bir tür için bir şema oluşturuyorsanız, aşağıdaki XML kullanabilirsiniz:

```xml
<!-- This is in a file named GenerateSchemaFromType.xml. -->
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateSchemas>
   <type>IDItems</type>
</generateSchemas>
</xsd>
```

Ancak, önceki kodu kullanmak için da komut isteminde derlemenin adı sağlamanız gerekir. Komut istemine aşağıdakileri girin (XML dosyasının GenerateSchemaFromType.xml olarak adlandırılacağı varsayılmıştır):

```console
xsd /p:GenerateSchemaFromType.xml ConsoleApplication1.exe
```

İçin aşağıdaki seçeneklerden birini belirtmelisiniz `<generateSchemas>` öğesi.

|Öğe|Açıklama|
|-------------|-----------------|
|\<montaj>|Şema oluşturmak için bir derleme belirtir.|
|\<> yazın|Bir türü için bir şema oluşturmak için bir derleme bulundu belirtir.|
|\<xml>|Bir XML dosyası için bir şema oluşturmak için belirtir.|
|\<xdr>|İçin bir şema oluşturmak için bir XDR dosyasını belirtir.|

Bir kod dosyası oluşturmak için kullanılan `<generateClasses>` öğesi. Aşağıdaki örnek, bir kod dosyası oluşturur. Oluşturulan dosyanın programlama dilini ve ad alanını ayarlamanızı sağlayan iki öznitelik de gösterildiğini unutmayın.

```xml
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateClasses language='VB' namespace='Microsoft.Serialization.Examples'/>
</xsd>
<!-- You must supply an .xsd file when typing in the command line.-->
<!-- For example: xsd /p:genClasses mySchema.xsd -->
```

 Seçenekleri için Ayarla `<generateClasses>` öğesi şunlar.

|Öğe|Açıklama|
|-------------|-----------------|
|\<eleman>|Bir öğe için kod oluşturmak üzere .xsd dosyasını belirtir.|
|\<şemaImporterExtensions>|Türetilen bir türü belirtiyor. <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> sınıfı.|
|\<şema>|Kodunu oluşturmak için bir XML şema dosyası belirtir. Birden çok XML Şema dosyaları \<birden çok şema> öğeleri kullanılarak belirtilebilir.|

Aşağıdaki tabloda `<generateClasses>` öğe yle birlikte kullanılabilecek öznitelikler gösterilmektedir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|language|Kullanmak için programlama dilini belirtir. Aralarından seçim `CS` (C#, varsayılan), `VB` (Visual Basic) `JS` (JScript) veya `VJS` (Visual J#). Ayrıca uygulayan bir sınıf için tam bir ad belirtin <xref:System.CodeDom.Compiler.CodeDomProvider>.|
|ad alanı|Oluşturulan kodun ad alanını belirtir. Ad alanı CLR standartları (örneğin, boşluk veya ters eğik çizgi karakterleri) uyması gerekir.|
|seçenekler|`none`Aşağıdaki değerlerden biri: `properties` , (ortak alanlar yerine `order`özellikler `enableDataBinding` oluşturur), `/order` `/enableDataBinding` veya (bkz. önceki XSD Dosya Seçenekleri bölümündeki ve anahtarlar.|

 Ayrıca, öğeyi `DataSet` kullanarak kodun `<generateDataSet>` nasıl oluşturulduğunu da denetleyebilirsiniz. Aşağıdaki XML, oluşturulan kodun belirli `DataSet` bir öğe <xref:System.Data.DataTable> için Visual Basic kodu oluşturmak için yapıları (sınıf gibi) kullandığını belirtir. Oluşturulan DataSet yapıları LINQ sorgularını destekler.

 ```xml
 <xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
     <generateDataSet language='VB' namespace='Microsoft.Serialization.Examples' enableLinqDataSet='true'>
     </generateDataSet>
 </xsd>
```

Seçenekleri için Ayarla `<generateDataSet>` öğesi şunlar.

|Öğe|Açıklama|
|-------------|-----------------|
|\<şema>|Kodunu oluşturmak için bir XML şeması dosyasını belirtir. Birden çok XML Şema dosyaları \<birden çok şema> öğeleri kullanılarak belirtilebilir.|

 Aşağıdaki tablo, `<generateDataSet>` öğeyle birlikte kullanılabilecek öznitelikleri gösterir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|enableLinqDataSet|Oluşturulan veri kümesi LINQ to DataSet kullanarak karşı sorgulanabilir belirtir. Varsayılan değer false'tur.|
|language|Kullanmak için programlama dilini belirtir. Aralarından seçim `CS` (C#, varsayılan), `VB` (Visual Basic) `JS` (JScript) veya `VJS` (Visual J#). Ayrıca uygulayan bir sınıf için tam bir ad belirtin <xref:System.CodeDom.Compiler.CodeDomProvider>.|
|ad alanı|Oluşturulan kodun ad alanını belirtir. Ad alanı CLR standartları (örneğin, boşluk veya ters eğik çizgi karakterleri) uyması gerekir.|

 En üst düzey `<xsd>` öğeüzerinde ayarlayabileceğiniz öznitelikler vardır. Herhangi bir alt öğelerinin bu seçenekler kullanılabilir (`<generateSchemas>`, `<generateClasses>` veya `<generateDataSet>`). Aşağıdaki XML kodu "MyOutputDirectory" adlı Çıktı dizininde "IDItems" adlı bir öğe için kod oluşturur.

```xml
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/' output='MyOutputDirectory'>
<generateClasses>
    <element>IDItems</element>
</generateClasses>
</xsd>
```

Aşağıdaki tabloda `<xsd>` öğe yle birlikte kullanılabilecek öznitelikler gösterilmektedir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|çıkış|Oluşturulan şema veya kod dosyanın yerleştirileceği bir dizinin adı.|
|nologo|Başlık göstermez. Ayarlanan `true` veya `false`.|
|Yardım|Araç için komut sözdizimini ve seçenekleri görüntüler. Ayarlanan `true` veya `false`.|

## <a name="examples"></a>Örnekler
 Aşağıdaki komutu bir XML şema oluşturur `myFile.xdr` ve geçerli dizine kaydeder.

```console
xsd myFile.xdr
```

Aşağıdaki komutu bir XML şema oluşturur `myFile.xml` ve belirtilen dizine kaydeder.

```console
xsd myFile.xml /outputdir:myOutputDir
```

Aşağıdaki komutu olarak kaydeder ve C# dili belirtilen şemada karşılık gelen bir veri kümesi oluşturur `XSDSchemaFile.cs` geçerli dizin.

```console
xsd /dataset /language:CS XSDSchemaFile.xsd
```

Aşağıdaki komutu tüm türleri için XML şemaları derlemesinde oluşturur `myAssembly.dll` ve bunları olarak kaydeder `schema0.xsd` geçerli dizin.

```console
xsd myAssembly.dll
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataSet>
- <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
- [Araçlar](../../../docs/framework/tools/index.md)
- [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
- [LINQ to DataSet Genel Bakış](../../../docs/framework/data/adonet/linq-to-dataset-overview.md)
- [Türü Belirtilmiş DataSet’leri Sorgulama](../../../docs/framework/data/adonet/querying-typed-datasets.md)
- [LINQ (Dil-Entegre Sorgu) (C#)](../../csharp/programming-guide/concepts/linq/index.md)
- [LINQ (Dil-Entegre Sorgu) (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/index.md)
