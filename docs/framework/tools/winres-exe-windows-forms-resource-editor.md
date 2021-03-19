---
title: Winres.exe (Windows kaynak yerelleştirme Düzenleyicisi)
description: Windows kaynak yerelleştirme Düzenleyicisi Winres.exe kullanın. Bu görsel düzen Aracı, yerelleştirme uzmanlarının Forms tarafından kullanılan Kullanıcı arabirimi kaynaklarını Windows Forms Yerelleştirmesine yardımcı olur.
ms.date: 08/15/2018
helpviewer_keywords:
- Winres.exe
- Windows Forms Resource Editor
- Windows Resource Localization Editor
- localization
- Windows Forms, localization
- forms, localizing
- resx files
- .resx files
ms.assetid: cb8bc835-9221-4888-af53-1a4f5fad6c48
ms.openlocfilehash: 2d66fd0d395f9d03b34c09304ce01d9c859da532
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653354"
---
# <a name="winresexe-windows-resource-localization-editor"></a>Winres.exe (Windows kaynak yerelleştirme Düzenleyicisi)

Windows kaynak yerelleştirme Düzenleyicisi Winres.exe, yerelleştirme uzmanlarının formlar tarafından kullanılan Kullanıcı arabirimi (UI) kaynaklarını yerelWindows Forms leştirebilmenizi sağlayan bir görsel düzen aracıdır. Winres.exe için girdi olarak kullanılan .resx veya .resources dosyaları Microsoft Visual Studio gibi bir görsel tasarım ortamı kullanarak oluşturulabilir. .NET Framework uygulamalarında kaynakları dağıtma hakkında daha fazla bilgi için bkz. [Masaüstü uygulamalarındaki kaynaklar](../resources/index.md).

Winres.exe, Visual Studio ile birlikte yüklenir. Aracı çalıştırmak için [Visual studio Geliştirici komut istemi veya Visual Studio Geliştirici PowerShell](/visualstudio/ide/reference/command-prompt-powershell)kullanın.

## <a name="syntax"></a>Söz dizimi

```console
winres resourceFile
winres /?
```

## <a name="arguments"></a>Bağımsız değişkenler

|Bağımsız Değişken|Description|
|--------------|-----------------|
|`resourceFile`|Yerelleştirilecek kaynak dosyası. Bu dosya, Visual Studio tasarımcısı tarafından oluşturulan Windows Forms formu .resx veya .resources dosyası olmalıdır. Winres.exe genel .resx veya .resources dosyalarını açamaz.|

|Seçenek|Açıklama|
|------------|-----------------|
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|

## <a name="remarks"></a>Açıklamalar

Bir Windows Forms projesindeki formda bulunan arabirim öğelerinin durumu genellikle kaynak dosyalarında depolanır; bunlar .resx uzantılı XML tabanlı dosyalar veya karşılık gelen derlenmiş, .resources uzantılı ikili sürümlerdir. Winres.exe, her iki dosya türünün Visual Studio tasarım ortamı dışında sınırlı şekilde düzenlenmesine olanak veren bir araçtır. Özellikle aşağıdaki türden düzenleme işlemlerine izin verir:

- Bir nötr veya belirli kültür kaynak dosyası, formun arabirim özelliklerini veya denetimlerini (metin, boyut veya konum gibi) değiştirecek şekilde düzenlenebilir.

- Nötr veya belirli kültür kaynak dosyaları varsayılan kaynak dosyasından oluşturulabilir.

- Bir kültür kaynak dosyası başka bir kültür kaynak dosyası olarak kaydedilebilir. Örneğin, İngilizce (ABD) kaynak dosyası Lehçe kaynak dosyası olarak kaydedilebilir. Genellikle yeni dosya daha sonra yeni kültür ile uyumlu olacak şekilde düzenlenir.

Ayrıca, yerelleştirme için kaynakların [hiyerarşik organizasyonu](/previous-versions/visualstudio/visual-studio-2012/756hydy4(v=vs.110)) veya [Yerelleştirme Için hiyerarşik kaynak organizasyonu](/previous-versions/visualstudio/visual-studio-2013/756hydy4(v=vs.120))bölümüne bakın.

Winres.exe, bir .resx dosyasını karşılık gelen .resources dosyasına dönüştüremez; bunun yerine Resgen.exe aracını kullanmalısınız. Resgen.exe hakkında daha fazla bilgi için bkz. [Resgen.exe (kaynak dosya Oluşturucu)](resgen-exe-resource-file-generator.md).

Winres.exe, kaynak koduna erişmeden bir Windows Forms formunun tasarım zamanı sürümünü yalnızca kaynak dosyasından yeniden oluşturan grafiksel bir uygulamadır. Winres.exe, Visual Studio 'nun **Windows Forms form Tasarımcısı** ve **Özellikler** penceresini barındırır. Bu özellikler, Windows Forms formu içeren bir .resources veya .resx dosyasının görsel olarak düzenlenmesine olanak verir. Genellikle, yerelleştiriciler denetim etiketlerini düzenlemek ve denetimlerin konumunu ve boyutunu hedef kültürün etiketlerine uyacak şekilde ayarlamak için Winres.exe kullanır.

Winres.exe bir denetimin türünü çözümleyemezse, yerelleştirilmiş .resx veya .resources dosyasında bir yer tutucu denetimi oluşturur. Yer tutucu denetimi Windows Forms formunda taranmış bir pencere olarak görüntülenir. Taranmış pencerenin boyutu ve konumu gerçek denetiminkilerle aynıdır. Yer tutucu denetimi için kullanılabilir tüm yerelleştirilebilir özellikler, **Özellikler** penceresinde görünür. Yer tutucu denetiminde yaptığınız tüm değişiklikler asıl denetim için kaydedilir.

## <a name="winresexe-versus-visual-studio"></a>Winres.exe ve Visual Studio

Genel olarak, bir uygulamanın Windows Forms formlarını yerelleştirmeye başlamadan önce, yerelleştirme aracı olarak Visual Studio'yu mu yoksa Winres.exe'yi mi kullanmak istediğinize karar vermelisiniz. Sürüm uyumluluğu, daha sonra açıklandığı gibi, bir araçtan diğerine geçiş yapmasını engelleyebilir.

Visual Studio'nun avantajı, bir uygulamayı hem geliştirmek hem de yerelleştirmek için kullanabilmenizdedir. Bir formu yerelleştirmek için, geliştirme tamamlandıktan sonra formun <xref:System.ComponentModel.LocalizableAttribute> ( **Özellikler** düzenleyicisinde **yerelleştirilebilir** özelliği) öğesini olarak ayarlayın `true` ve **Language** özelliğini istenen hedef kültür olarak değiştirin. Daha sonra, dizeleri düzenleyin ve denetimlerin konumu ile boyutunu hedef kültürün dizelerine uygun olacak şekilde ayarlayın. Yerelleştirilmiş .resx dosyasını kaydettiğinizde, Visual Studio dosyaya yalnızca yerelleştirilebilir özellikleri (hedef kültürde değiştirilen özellikler) yazar. Visual Studio, yerelleştirilmiş .resx dosyası için bir uydu derlemesini doğru dizin konumunda otomatik olarak oluşturur.

Visual Studio tümleşik bir geliştirme ve yerelleştirme ortamı sağlasa da, yerelleştirme üçüncü taraf Yereller tarafından yapıldığında kullanılması önerilen araç Winres.exe. Winres.exe yalnızca bir yerelleştirme aracı olduğu için, bir uygulamanın kodu ile yerelleştirilecek formlar arasında daha net bir ayrım sağlar, ki bu da büyük projeleri yönetirken daha büyük bir kolaylık demektir.

## <a name="using-winresexe"></a>Winres.exe'yi kullanma

Winres.exe kullanarak yerelleştirmek için, ilk olarak Visual Studio 'daki **Windows Form Tasarımcısı** gibi bir görsel tasarımcı kullanarak bir uygulama geliştirmeniz gerekir. Geliştirme tamamlandığında, formun <xref:System.ComponentModel.LocalizableAttribute> ( **Özellikler** düzenleyicisinde **yerelleştirilebilir** özelliği) öğesini olarak ayarlayın `true` ve ardından varsayılan kültür için. resx dosyasını bir üçüncü taraf yerelleştiriciye bırakın. Bu .resx dosyası özgün formun tasarım zamanı sürümünü yeniden oluşturmak için Winres.exe'nin kullandığı ek bilgileri içerir.

> [!NOTE]
> Winres.exe varsayılan kaynak dosyayı düzenlemek için kullanılamaz. Winres.exe, değişen tüm özellikleri yerelleştirilmiş özellikler olarak yorumlar ve bunları hedef kültür kaynak dosyasına kaydeder.

Kültür kaynak dosyalarının son sürümleri son olarak uygulamanın yerelleştirilmiş sürümlerini oluşturmak için kullanılabilir. Daha fazla bilgi için bkz. [Masaüstü uygulamalarındaki kaynaklar](../resources/index.md).

Winres.exe aşağıdaki özelliklere ve özelliklere sahiptir:

- Winres Tek Dosya Modu'nda (SFM) veya Visual Studio Dosya Modu'nda (VSFM) çalışabilir. SFM, form ve içeriği hakkındaki tüm bilgilerin kaynak dosyada depolandığı eski moddur. VSFM kültürel değişiklikleri yalnızca kaynak dosyasında depolar.

- Ana pencerenin sol alt kısmına yerleştirilen bir hata raporlama penceresi.

- Kısayol tuşları, yinelemeler için denetlenebilir: **Biçim** menüsünde, **kısayol tuşlarını denetle** komutuna tıklayın.

## <a name="version-compatibility"></a>Sürüm Uyumluluğu

Kullanmakta olduğunuz .NET Framework birlikte yayınlanan Winres.exe sürümünü kullanmalısınız. Aşağıdaki tabloda uyumlu sürümler listelenmiştir:

|Visual Studio|.NET Framework|Winres.exe|
|-------------------|--------------------|----------------|
|Visual Studio .NET 2002|1.0|1.0|
|Visual Studio .NET 2003|1.1|1.1|
|Visual Studio 2005|2.0|2.0|
|Visual Studio 2008|3.0 ve 3.5|3.0 ve 3.5|
|Visual Studio 2010|4.0|4.0|
|Visual Studio 2017|4,6|4,6|

> [!NOTE]
> VSFM'de, Visual Studio ile uyumluluk avantajı bulunuyor olsa da, kaynak dosyaya yalnızca değiştirilmiş değerleri depoladığından, Winres.exe geçerli kaynak dosyanın üst öğelerinin aynı dizinde bulunmasını gerektirir. Örneğin, `TestApp.de-DE.resources` Almanya kaynak dosyasındaki bir Almanca, varsayılan kaynak dosyası, `TestApp.resx` ve muhtemelen kültür bağımsız kaynak dosyası olması gerekir `TestApp.de.resources` .

## <a name="examples"></a>Örnekler

### <a name="to-localize-a-resx-or-resources-file-associated-with-a-form"></a>Bir formla ilişkili .resx veya .resources dosyasını yerelleştirmek için

1. `winres`Winres.exe çalıştırmak için geliştirici komut istemine yazın.

2. Yerelleştirmek üzere bir formun varsayılan kaynaklarını açmak için **Dosya** menüsünde **Aç** komutuna tıklayın ve dosyayı açmak için dosyaya gidin.

     -veya-

     Winres.exe'yi başlattığınızda komut satırında açılacak dosyayı belirtin.

     Aşağıdaki komut Winres.exe başlatır ve form tasarımcısında ile ilişkili formu yükler `TestApp.resx` .

    ```console
    winres TestApp.resx
    ```

     Aşağıdaki komut Winres.exe başlatır ve form tasarımcısında ile ilişkili formu yükler `TestApp.resources` .

    ```console
    winres TestApp.resources
    ```

    > [!NOTE]
    > Kaynaklarını düzenlediğiniz form devralınmış bir form ise, hem formun içindeki derleme hem de devralan (türetilmiş) formu içeren derleme Genel Derleme Önbelleği'ne (GAC) kaydettirilmeli veya WinRes.exe ile aynı dizinde bulunmalıdır. GAC 'ye .NET Framework bileşenleri yükleme hakkında daha fazla bilgi için bkz. [genel derleme önbelleği](../app-domains/gac.md).

3. Formdaki denetimleri seçin ve <xref:System.Windows.Forms.Control.Text%2A> diğer özelliklerini yerelleştirilmiş kültürü ve dilini yansıtacak şekilde değiştirin. Yerelleştirilmiş metnin sığmasını sağlayacak şekilde denetimleri gerektiği gibi taşıyın veya yeniden boyutlandırın.

4. . Resx veya. resources dosyasının yerelleştirilmiş sürümünü kaydetmek için, **Dosya** menüsünde **Kaydet** simgesine veya aynı komuta tıklayın. Araç, **kültür Seç** penceresini görüntüler.

5. Uygun kültürü ve dosya modunu seçip **Tamam**' a tıklayın.

   Araç dosyayı, çalışma zamanının yerelleştirilmiş kaynak dosyaları için beklediği adlandırma kuralını kullanarak kaydeder. Örneğin, `TestApp.resources` Almanya 'Da Almanca için yerelleştirmeniz halinde, araç dosyayı olarak kaydeder `TestApp.de-DE.resources` . `TestApp.resx`Almanya 'Da Almanca için yerelleştirmeniz durumunda, araç dosyayı olarak kaydeder `TestApp.de-DE.resx` . Kaynak adlandırma kuralları hakkında daha fazla bilgi için bkz. [kaynakları paketleme ve dağıtma](../resources/packaging-and-deploying-resources-in-desktop-apps.md). Çalışma zamanı tarafından kullanılan önceden tanımlanmış kültür adlarının bir listesi için, <xref:System.Globalization.CultureInfo> sınıfına bakın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.LocalizableAttribute>
- <xref:System.Globalization.CultureInfo>
- <xref:System.Resources.ResourceManager>
- <xref:System.Resources.ResourceReader>
- <xref:System.Resources.ResourceWriter>
- [Araçlar](index.md)
- [Masaüstü uygulamalarındaki kaynaklar](../resources/index.md)
- [Genelleştirme ve yerelleştirme](../../standard/globalization-localization/index.md)
