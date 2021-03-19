---
title: Gacutil.exe (Genel Derleme Önbelleği Aracı)
description: Genel derleme önbelleği aracı Gacutil.exe hakkındaki ayrıntıları alın. Bu araç, genel derleme önbelleğini görüntülemenizi ve düzenlemenizi sağlar ve önbelleği indirin.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- global assembly cache, manipulating contents
- GAC (global assembly cache), Gacutil.exe
- Gacutil.exe
- GAC (global assembly cache), viewing contents
- installing assemblies into global assembly cache
- removing assemblies from global assembly cache
- list of assemblies in global assembly cache
- cache [.NET Framework], global assembly cache
- GAC (global assembly cache), manipulating contents
- global assembly cache, Gacutil.exe
- Global Assembly Cache tool
ms.assetid: 4c7be9c8-72ae-481f-a01c-1a4716806e99
ms.openlocfilehash: 68a85b74333e978adc0b9953d408b36d5e91738f
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104654147"
---
# <a name="gacutilexe-global-assembly-cache-tool"></a>Gacutil.exe (genel derleme önbelleği aracı)

Genel Bütünleştirilmiş Kod Önbelleği aracı genel bütünleştirilmiş kod önbelleğinin ve indirme önbelleğinin içeriğini görüntülemenize ve değiştirmenize olanak sağlar.

Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için [Visual studio Geliştirici komut istemi veya Visual Studio Geliştirici PowerShell](/visualstudio/ide/reference/command-prompt-powershell)kullanın.

Komut satırına şunu yazın:

## <a name="syntax"></a>Sözdizimi

```console
gacutil [options] [assemblyName | assemblyPath | assemblyListFile]
```

## <a name="parameters"></a>Parametreler

|Bağımsız Değişken|Description|
|--------------|-----------------|
|*assemblyName*|Bir derlemenin adı. Gibi kısmen belirtilen bir derleme adı ya da gibi tam olarak `myAssembly` belirtilen bir derleme adı sağlayabilirsiniz `myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5` .|
|*assemblyPath*|Bir derleme bildirimi içeren dosyanın adı.|
|*assemblyListFile*|Yüklenecek veya kaldırılacak derlemeleri listeleyen bir ANSI metin dosyasının yolu. Derlemeleri yüklemek üzere metin dosyası kullanmak için, dosyada her derleme için ayrı bir satırda yolu belirtin. Araç, *AssemblyListFile* konumuna göre göreli yolları yorumlar. Derlemeleri kaldırmak üzere bir metin dosyası kullanmak için, dosyada her derleme için ayrı bir satırda tam derleme adını belirtin. Bu konunun ilerleyen kısımlarında *AssemblyListFile* içerik örneklerine bakın.|

|Seçenek|Açıklama|
|------------|-----------------|
|**/CDL**|İndirme önbelleğinin içeriğini siler.|
|**/f**|Bir derlemeyi yeniden yüklemeye zorlamak için bu seçeneği **/ı** veya **/Il** seçenekleriyle belirtin. Eğer genel bütünleştirilmiş kod önbelleğinde aynı ada sahip bir derleme zaten bulunuyorsa, araç onun üzerine yazar.|
|**/h**[**ELP**]|Araç için komut sözdizimini ve seçenekleri görüntüler.|
|**/I** *assemblyPath*|Genel bütünleştirilmiş kod önbelleğine bir derleme yükler.|
|**/IF**  *assemblyPath*|Genel bütünleştirilmiş kod önbelleğine bir derleme yükler. Eğer genel bütünleştirilmiş kod önbelleğinde aynı ada sahip bir derleme zaten bulunuyorsa, araç onun üzerine yazar.<br /><br /> Bu seçeneği belirtmek, **/i** ve **/f** seçeneklerini birlikte belirtmeye eşdeğerdir.|
|**/Il** *AssemblyListFile*|*AssemblyListFile* içinde belirtilen bir veya daha fazla derlemeyi genel bütünleştirilmiş kod önbelleğine yükleme.|
|**/IR**  *assemblyPath*<br /><br /> *Şemadaki*<br /><br /> *id*<br /><br /> *açıklaması*|Bir derlemeyi genel bütünleştirilmiş kod önbelleğine yükler ve derlemeyi saymak için bir başvuru ekler. Bu seçenekle *assemblyPath*, *Scheme*, *ID* ve *Description* parametrelerini belirtmeniz gerekir. Bu parametreler için belirtebileceğiniz geçerli değerlerin bir açıklaması için **/r** seçeneğine bakın.<br /><br /> Bu seçeneği belirtmek, **/i** ve **/r** seçeneklerini birlikte belirtmeye eşdeğerdir.|
|**/l** [*AssemblyName*]|Genel bütünleştirilmiş kod önbelleğinin içeriğini listeler. *AssemblyName* parametresini belirtirseniz, araç yalnızca o adla eşleşen derlemeleri listeler.|
|**/LDL**|İndirilen dosyalar önbelleğinin içeriğini listeler.|
|**/LR** [*AssemblyName*]|Tüm derlemeleri ve karşılık gelen başvuru sayılarını listeler. *AssemblyName* parametresini belirtirseniz, araç yalnızca o adla eşleşen derlemeleri ve bunlara karşılık gelen başvuru sayılarını listeler.|
|**/nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|
|**/r** [*AssemblyName &#124; assemblyPath*]<br /><br /> *Şemadaki*<br /><br /> *id*<br /><br /> *açıklaması*|Yüklenecek veya kaldırılacak bir derleme veya derlemeler için izlenen bir başvuru belirtir. **/I**, **/Il**, **/u** veya **/ul** seçenekleriyle bu seçeneği belirtin.<br /><br /> Bir derlemeyi yüklemek için, bu seçenekle *assemblyPath*, *Scheme*, *ID* ve *Description* parametrelerini belirtin. Bir derlemeyi kaldırmak için *AssemblyName*, *Scheme*, *ID* ve *Description* parametrelerini belirtin.<br /><br /> Bir derlemeye yönelik bir başvuruyu kaldırmak için, derleme yüklenirken **/i** ve **/r** (veya **/ir**) seçenekleriyle belirtilen aynı *Düzen*, *kimlik* ve *Açıklama* parametrelerini belirtmeniz gerekir. Eğer bir derlemeyi kaldırıyorsanız, eğer kaldırılacak son başvuruysa ve Windows Installer'ın o derlemeye hiçbir başvurusu yok ise araç derlemeyi genel bütünleştirilmiş kod önbelleğinden de kaldırır.<br /><br /> *Scheme* parametresi, yükleme düzeninin türünü belirtir. Aşağıdaki değerlerden birini belirleyebilirsiniz.<br /><br /> -UNINSTALL_KEY: yükleyici uygulamayı Microsoft Windows 'da Program Ekle/Kaldır 'a eklerse bu değeri belirtin. Uygulamalar HKLM\Software\Microsoft\Windows\CurrentVersion içine bir kayıt defteri anahtarı ekleyerek kendilerini Program Ekle/Kaldır'a ekler.<br />-FILEPATH: yükleyici uygulamayı Program Ekle/Kaldır 'a eklememezse bu değeri belirtin.<br />-DONUK: bir kayıt defteri anahtarı sağlamak veya yükleme senaryonuz için dosya yolu yoksa, bu değeri belirtin. Bu değer, *ID* parametresi için özel bilgi belirtmenize olanak tanır.<br /><br /> *ID* parametresi için belirtme değeri, *Düzen* parametresi için belirtilen değere bağlıdır:<br /><br /> - *Düzen* parametresi için UNINSTALL_KEY belirtirseniz, HKLM\Software\Microsoft\Windows\CurrentVersion kayıt defteri anahtarında ayarlanan uygulamanın adını belirtin. Örneğin, kayıt defteri anahtarı HKLM\Software\Microsoft\Windows\CurrentVersion\MyApp ise *ID* parametresi için MyApp ' i belirtin.<br />- *Düzen* PARAMETRESI için FILEPATH belirtirseniz, derlemeyi *ID* parametresi olarak yükleyen yürütülebilir dosyanın tam yolunu belirtin.<br />- *Düzen* PARAMETRESI için donuk belirtirseniz, herhangi bir veri parçasını *ID* parametresi olarak sağlayabilirsiniz. Belirttiğiniz veri tırnak işaretleri ("") arasına alınmalıdır.<br /><br /> *Description* parametresi, yüklenecek uygulama hakkında açıklayıcı bir metin belirtmenize olanak tanır. Bu bilgi başvurular numaralandığında görüntülenir.|
|**/silent**|Tüm çıktıların görüntülenmesini bastırır.|
|**/U**  *AssemblyName*|Genel bütünleştirilmiş kod önbelleğinden bir derlemeyi kaldırır.|
|**/UF**  *AssemblyName*|Belirtilen bir derlemenin tüm başvurularını kaldırarak derlemeyi kaldırmaya zorlar.<br /><br /> Bu seçeneği belirtmek, **/u** ve **/f** seçeneklerini birlikte belirtmeye eşdeğerdir. **Note:**  Microsoft Windows Installer kullanılarak yüklenen bir derlemeyi kaldırmak için bu seçeneği kullanamazsınız. Eğer bu işlemi yapmayı denerseniz, araç bir hata iletisi görüntüler.|
|**/ul** *AssemblyListFile*|*AssemblyListFile* içinde belirtilen bir veya daha fazla derlemeyi genel bütünleştirilmiş kod önbelleğinden kaldırır.|
|**/u**[**Ngen**] *AssemblyName*|Belirtilen bir derlemeyi genel bütünleştirilmiş kod önbelleğinden kaldırır. Eğer belirtilen derlemenin varolan başvuru sayısı varsa, araç başvuru sayılarını görüntüler ve derlemeyi genel bütünleştirilmiş kod önbelleğinden kaldırmaz. **Note:**  .NET Framework sürüm 2,0 ' de `/ungen` desteklenmez. Bunun yerine, `uninstall` [Ngen.exe (yerel görüntü Oluşturucu)](ngen-exe-native-image-generator.md)komutunu kullanın. <br /><br /> .NET Framework sürüm 1,0 ve 1,1 ' de, **/ungen** belirtme, derlemeyi yerel görüntü önbelleğinden kaldırmak için Gacutil.exe nedenler. Bu önbellek, [Ngen.exe (yerel görüntü Oluşturucu)](ngen-exe-native-image-generator.md)kullanılarak oluşturulan derlemelerin yerel görüntülerini depolar.|
|**/ur**  *AssemblyName*<br /><br /> *Şemadaki*<br /><br /> *id*<br /><br /> *açıklaması*|Belirtilen bir derleme için genel bütünleştirilmiş kod önbelleğinden bir başvuru kaldırır. Bir derlemeye yönelik bir başvuruyu kaldırmak için, derleme yüklenirken **/i** ve **/r** (veya **/ir)** seçenekleriyle belirtilen aynı *Düzen*, *kimlik* ve *Açıklama* parametrelerini belirtmeniz gerekir. Bu parametreler için belirtebileceğiniz geçerli değerlerin bir açıklaması için **/r** seçeneğine bakın.<br /><br /> Bu seçeneği belirtmek, **/u** ve **/r** seçeneklerini birlikte belirtmeye eşdeğerdir.|
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|

## <a name="remarks"></a>Açıklamalar

> [!NOTE]
> Gacutil.exe'yi kullanabilmek için yönetici ayrıcalıklarınız olmalıdır.

Özellikle, Gacutil.exe önbelleğe derlemeler yüklemenize, önbellekten derlemeleri kaldırmanıza ve önbelleğin içeriğini listelemenize olanak sağlar.

Gacutil.exe, Windows Installer tarafından desteklenen başvuru sayma düzenine benzer başvuru saymayı destekleyen seçenekler sağlar. Gacutil.exe'yi kullanarak aynı derlemeyi yükleyen iyi uygulamayı yükleyebilirsiniz: araç o derlemeye olan başvuruların sayısını takip eder. Sonuç olarak, derleme iki uygulama da kaldırılana kadar bilgisayarda kalır. Eğer Gacutil.exe'yi gerçek ürün yüklemelerinde kullanıyorsanız, başvuru saymayı destekleyen seçenekleri kullanın. Bir derlemeyi yüklemek ve saymak için bir başvuru eklemek için **/i** ve **/r** seçeneklerini birlikte kullanın. Bir derlemenin başvuru sayısını kaldırmak için **/u** ve **/r** seçeneklerini birlikte kullanın. Yalnızca **/ı** ve **/u** seçeneklerinin kullanılması, başvuru saymayı desteklememe durumunu unutmayın. Bu seçenekler uygulama geliştirme süresince kullanılmaya uygundur ancak gerçek ürün yüklemelerinde uygun değildir.

Bir ANSI metin dosyasında depolanan derlemelerin listesini yüklemek veya kaldırmak için **/İl** veya **/ul** seçeneklerini kullanın. Metin dosyasının içeriği doğru şekilde biçimlendirilmelidir. Derlemeleri yüklemek üzere metin dosyası kullanmak için, dosyada her derleme için ayrı bir satırda yolu belirtin. Aşağıdaki örnek yüklenecek derlemeleri içeren bir dosyanın içeriğini gösterir.

```text
myAssembly1.dll
myAssembly2.dll
myAssembly3.dll
```

Derlemeleri kaldırmak üzere bir metin dosyası kullanmak için, dosyada her derleme için ayrı bir satırda tam derleme adını belirtin. Aşağıdaki örnek kaldırılacak derlemeleri içeren bir dosyanın içeriğini gösterir.

```text
myAssembly1,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab
myAssembly2,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab
myAssembly3,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab
```

> [!NOTE]
> 79 ve 91 karakterlerinden (dosya uzantısı hariç) daha uzun bir dosya adı ile derleme yüklenmeye çalışılması aşağıdaki hatayla sonuçlanabilir:
>
> ```output
> Failure adding assembly to the cache:   The file name is too long.
> ```
>
> Bunun nedeni, dahili Gacutil.exe aşağıdaki öğelerden oluşan MAX_PATH karakterlik bir yol oluşturur:
>
> - GAC root-34 karakterleri (IE `C:\Windows\Microsoft.NET\assembly\` )
> - Mimari-7 veya 9 karakter (IE. `GAC_32\` , `GAC_64\` , `GAC_MSIL` )
> - Diğer öğelerin boyutuna bağlı olarak, en fazla 91 karakter olan AssemblyName (örn. `System.Xml.Linq\`)
> - AssemblyInfo-31-48 karakter veya daha fazlası:
>   - Framework-5 karakter (örn. `v4.0_`)
>   - AssemblyVersion-8 ile 24 karakter (örn. `9.0.1000.0_`)
>   - AssemblyLanguage-1 ile 8 karakter (örn. `de_`, `sr-Cyrl_`)
>   - PublicKey-17 karakter (örn. `31bf3856ad364e35\`)
> - DllFileName-en fazla 91 + 4 karakter (IE `<AssemblyName>.dll` )

## <a name="examples"></a>Örnekler

Aşağıdaki komut, derlemeyi `mydll.dll` genel derleme önbelleğine yüklenir.

```console
gacutil /i mydll.dll
```

Aşağıdaki komut, derleme `hello` için başvuru sayısı bulunmadığı sürece derlemeyi genel bütünleştirilmiş kod önbelleğinden kaldırır.

```console
gacutil /u hello
```

Önceki komutun, derleme adı tam olarak belirtilmediği için derleme önbelleğinden birden fazla derleme kaldırabileceğine dikkat edin. Örneğin, hem 1.0.0.0 hem de 3.2.2.1 of sürümü `hello` önbellekte yüklüyse, komut `gacutil /u hello` her iki derlemeyi de kaldırır.

Birden fazla derlemeyi kaldırmayı önlemek için aşağıdaki örneği kullanın. Bu komut yalnızca `hello` tam olarak belirtilen sürüm numarası, kültür ve ortak anahtarla eşleşen derlemeyi kaldırır.

```console
gacutil /u hello, Version=1.0.0.1, Culture="de",PublicKeyToken=45e343aae32233ca
```

Aşağıdaki komut, dosyasında belirtilen derlemeleri `assemblyList.txt` genel bütünleştirilmiş kod önbelleğine yüklenir.

```console
gacutil /il assemblyList.txt
```

Aşağıdaki komut, dosyasında belirtilen derlemeleri `assemblyList.txt` genel bütünleştirilmiş kod önbelleğinden kaldırır.

```console
gacutil /ul assemblyList.txt
```

Aşağıdaki komut `myDll.dll` genel derleme önbelleğine yüklenir ve saymak için bir başvuru ekler. Derleme, `myDll.dll` uygulama tarafından kullanılır `MyApp` . `UNINSTALL_KEY MyApp`Parametresi, `MyApp` Windows 'Da Program Ekle/Kaldır 'a ekleyen kayıt defteri anahtarını belirtir. Description parametresi olarak belirtilir `My Application Description` .

```console
gacutil /i /r myDll.dll UNINSTALL_KEY MyApp "My Application Description"
```

Aşağıdaki komut `myDll.dll` genel derleme önbelleğine yüklenir ve saymak için bir başvuru ekler. Düzen parametresi, `FILEPATH` ve ID parametresi, `c:\applications\myApp\myApp.exe` Açıklama parametresini yükleyen uygulamanın yolunu belirtin `myDll.dll.` `MyApp` .

```console
gacutil /i /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp
```

Aşağıdaki komut `myDll.dll` genel derleme önbelleğine yüklenir ve saymak için bir başvuru ekler. Düzen parametresi, `OPAQUE` kimlik ve açıklama parametrelerini özelleştirmenize olanak sağlar.

```console
gacutil /i /r mydll.dll OPAQUE "Insert custom application details here" "Insert Custom description information here"
```

Aşağıdaki komut, başvurusunu `myDll.dll` uygulama tarafından kaldırır `myApp` . Eğer bu, derleme için olan son başvuruysa, derlemeyi ayrıca genel bütünleştirilmiş kod önbelleğinden de kaldırır.

```console
gacutil /u /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp
```

Aşağıdaki komut genel bütünleştirilmiş kod önbelleğinin içeriğini listeler.

```console
gacutil /l
```

## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Genel Derleme Önbelleği](../app-domains/gac.md)
- [Regasm.exe (derleme kayıt aracı)](regasm-exe-assembly-registration-tool.md)
- [Geliştirici komut satırı kabukları](/visualstudio/ide/reference/command-prompt-powershell)
