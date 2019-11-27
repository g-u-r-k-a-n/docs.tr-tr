---
title: Mpgo.exe (Yönetilen Profil Temelli İyileştirme Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- Mpgo.exe
- training scenarios, generating profiles with
- Managed Profile Guided Optimization Tool
- Ngen.exe
- Ngen.exe, profilers and native images
ms.assetid: f6976502-a000-4fbe-aaf5-a7aab9ce4ec2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a5ab3040a246a135771c45b2639567db9ab510e3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447964"
---
# <a name="mpgoexe-managed-profile-guided-optimization-tool"></a>Mpgo.exe (Yönetilen Profil Temelli İyileştirme Aracı)

Yönetilen profil temelli Iyileştirme Aracı (Mpgo. exe), [Yerel Görüntü Oluşturucu (Ngen. exe)](ngen-exe-native-image-generator.md)tarafından oluşturulan yerel görüntü derlemelerini iyileştirmek için ortak Son Kullanıcı senaryolarını kullanan bir komut satırı aracıdır. Bu araç, profil verilerini oluşturan eğitim senaryolarını çalıştırmanızı sağlar. [Yerel Görüntü Oluşturucu (Ngen. exe)](ngen-exe-native-image-generator.md) , oluşturulan yerel görüntü uygulama derlemelerini iyileştirmek için bu verileri kullanır. Eğitim senaryosu, uygulamanızın beklenen bir kullanımına ilişkin denemedir. Mpgo.exe, Visual Studio Ultimate 2012 ve sonraki sürümlerinde kullanılabilir. Visual Studio 2013 başlayarak, Mpgo. exe ' yi kullanarak Windows 8. x mağaza uygulamalarını de iyileştirebilirsiniz.  
  
Profil destekli en iyi duruma getirme süreci, eğitim senaryolarından veri toplayıp yerel görüntülerin düzenini en iyi duruma getirmek üzere onları kullanarak verimi, bellek kullanımını (çalışma kümesi boyutu) ve uygulama başlatma süresini iyileştirir.  
  
Ara Dil (IL) derlemeleri için başlatma süresi ve çalışma kümesi boyutuyla ilgili performansı sorunlarıyla karşılaştığınızda, just-in-time (JIT) (tam zamanında) derleme maliyetlerini ortadan kaldırmak ve kod paylaşımını kolaylaştırmak için ilk Ngen.exe'yi kullanmanızı öneririz. Ek geliştirmeler gerekiyorsa, uygulamanızı daha ileri düzeyde iyi hale getirmek etmek için Mpgo.exe kullanabilirsiniz. Performans artışlarını değerlendirmek için temel olarak, en iyi duruma getirilmemiş yerel görüntü derlemelerindeki performans verilerini kullanabilirsiniz. Mpgo.exe kullanıldığında soğuk başlangıç sürelerinde kısalma ve çalışma kümesi boyutunda azalma görülebilir. Mpgo.exe, en iyi duruma getirilmiş yerel görüntü derlemeleri oluşturmak için Ngen.exe'yi kullanan IL derlemelerine bilgi ekler. Daha fazla bilgi için bkz. .NET blogda [Masaüstü uygulamalarınız Için başlatma performansını iyileştirme](https://devblogs.microsoft.com/dotnet/improving-launch-performance-for-your-desktop-applications/) girişi.  
  
Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, yönetici kimlik bilgileriyle Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın ve komut istemine aşağıdakini yazın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).  
  
Masaüstü uygulamaları için:  
  
```console  
mpgo –Scenario <command> [-Import <directory>] –AssemblyList <assembly1>  <assembly2> ... -OutDir <directory> [options]  
```  
  
Windows 8. x Mağazası uygulamaları için:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
mpgo –Scenario <packageName> -AppID <appId> -Timeout <seconds>  
```  
  
## <a name="parameters"></a>Parametreler  
 Mpgo.exe için tüm bağımsız değişkenler büyük/küçük harfe duyarsızdır. Komutlara önek olarak bir tire işareti eklenir.  
  
> [!NOTE]
> Gerekli bir komut olarak `–Scenario` ya da `–Import` kullanabilirsiniz, ancak her ikisini birden kullanamazsınız. `–Reset` seçeneğini belirtirseniz gerekli parametrelerin hiçbiri kullanılmaz.

|Gerekli parametre|Açıklama|
|------------------------|-----------------|
|`-Scenario` \<*komutu*><br /><br /> —veya—<br /><br /> \<*packageName*> `-Scenario`<br /><br /> veya<br /><br /> *dizin*> `-Import` \<|Masaüstü uygulamaları için, tüm komut satırı bağımsız değişkenleri dahil olmak üzere iyileştirmek istediğiniz uygulamayı çalıştırmak için komutu belirtmek üzere `–Scenario` kullanın. Boşluklar içeren bir yol belirtiyorsa *komut* etrafında üç çift tırnak işareti kümesini kullanın; Örneğin: `mpgo.exe -scenario """C:\My App\myapp.exe""" -assemblylist """C:\My App\myapp.exe""" -outdir "C:\optimized files"`. Çift tırnak işareti kullanmayın; *komut* boşluk içeriyorsa, bunlar düzgün çalışmayacaktır.<br /><br /> veya<br /><br /> Windows 8. x Mağazası uygulamaları için, profil bilgilerini oluşturmak istediğiniz paketi belirtmek üzere `–Scenario` kullanın. Tam paket adı yerine, paketin görünen adını veya paket aile adını belirtirseniz ve yalnızca tek bir eşleşme varsa Mpgo.exe sağladığınız adla eşleşen paketi seçer. Belirtilen adla eşleşen birden çok paket varsa, Mpgo.exe sizden bir paket seçmenizi ister.<br /><br /> —veya—<br /><br /> `-AssemblyList`derlemeleri iyileştirmek için önceden iyileştirilmiş derlemelerin en iyi duruma getirme verilerinin kullanılması gerektiğini belirtmek için `-Import` kullanın. *Dizin* , önceden iyileştirilmiş dosyaları içeren dizini belirtir. `–AssemblyList` veya `–AssemblyListFile` ' de belirtilen derlemeler, içeri aktarılan dosyalardaki veriler kullanılarak en iyi duruma getirilecek derlemelerin yeni sürümleridir. Derlemelerin eski sürümlerine ait en iyi duruma getirme verilerini kullanmak, senaryoyu yeniden çalıştırmadan derlemelerin yeni sürümlerini en iyi duruma getirmenizi sağlar.  Ancak, içe aktarılan ve hedef derlemeler önemli ölçüde farklı kodlar içeriyorsa, en iyi duruma getirme verileri etkisiz olur. `–AssemblyList` veya `–AssemblyListFile` içinde belirtilen derleme adları `–Import`*Dizin*tarafından belirtilen dizinde bulunmalıdır. Boşluk içeren bir yol belirtiyorsa *Dizin* etrafında üç çift tırnak işareti kümesini kullanın.<br /><br /> `–Scenario` ya da `–Import`belirtmelisiniz, ancak her iki parametreyi de belirtmemelidir.|
|*dizin*> `-OutDir` \<|En iyi duruma getirilmiş derlemelerin yerleştirileceği dizin. Çıkış dizini klasöründe bir derleme zaten varsa, yeni bir kopya oluşturulur ve adına bir dizin numarası eklenir; Örneğin: *AssemblyName*-1. exe. Boşluk içeren bir yol belirtiyorsa *Dizin* etrafında çift tırnak işareti kullanın.|
|`-AssemblyList` \<*Assembly1 Assembly2...* ><br /><br /> —veya—<br /><br /> `-AssemblyListFile` \<*dosya*>|Hakkında profil bilgileri toplamak istediğiniz derlemeleri (.exe ve .dll dosyaları gibi) boşluklarla ayrılmış olarak içeren bir liste. Belirtilen veya geçerli çalışma dizinindeki tüm derlemeleri seçmek için `C:\Dir\*.dll` veya `*.dll` belirtebilirsiniz. Daha fazla bilgi için Açıklamalar bölümüne bakın.<br /><br /> —veya—<br /><br /> Her satırda bir derleme olacak şekilde, hakkında profil bilgileri toplamak istediğiniz derlemelerin listesini içeren bir metin dosyası. Bir derleme adı tire işareti (-) ile başlıyorsa, bir derleme dosyası listesi kullanın veya derlemeyi yeniden adlandırın.|
|`-AppID` \<*appıd*>|Belirtilen paketteki uygulamanın kimliği. Joker karakter (\*) kullanırsanız, Mpgo. exe paketteki Appıds değerlerini numaralandırmaya çalışır ve > *package_family_name*\<geri dönecektir! Uygulama başarısız olursa. Başında önek olarak ünlem işareti (!) konmuş bir dize belirtirseniz, Mpgo.exe paket aile adını sağlanan bağımsız değişkenle birleştirir.|
|`-Timeout` \<*saniye*>|Uygulama gelmeden önce Windows 8. x Mağazası uygulamasının çalışmasına izin verme süresi.|

|İsteğe bağlı parametre|Açıklama|
|------------------------|-----------------|
|`-64bit`|64-bit sistemler için derlemeleri kullanır.  Derlemeniz kendisini 64-bit olarak bildiriyor olsa da 64-bit derlemeler için bu parametreyi belirtmelisiniz.|
|`-ExeConfig` \<*dosya adı*>|Senaryonuzun sürüm ve yükleyici bilgilerini sağlamak üzere kullandığı yapılandırma dosyasını belirtir.|
|`-f`|İmzalanmış olsa da, ikili bir derlemeye profil verilerinin eklenmesini sağlar.  Derleme imzalanmışsa, yeniden imzalanması gerekir; aksi takdirde derleme yüklenemez ve çalıştırılamaz.|
|`-Reset`|İptal edilen bir profil oluşturma oturumunun derlemelerinizi etkilemediğinden emin olmak için ortamı sıfırlar ve ardından çıkış yapar. Ortam varsayılan olarak bir profil oluşturma oturumundan önce ve sonra sıfırlanır.|
|*saniye cinsinden* `-Timeout` \<süresi>|Profil oluşturma süresini saniye cinsinden belirtir. GUI uygulamaları için, gözlemlenen başlangıç zamanlarınızdan biraz daha büyük bir değer kullanın. Uygulama çalışmaya devam etse de, zaman aşımı süresinin sonunda profil verileri kaydedilir. Bu seçeneği ayarlamazsanız, profil oluşturma işlemi uygulamayı kapanana kadar devam eder, ardından veriler kaydedilir.|
|`-LeaveNativeImages`|Kullanılan yerel görüntülerin senaryo çalıştırıldıktan sonra kaldırılmayacağını belirtir. Bu seçenek öncelikle senaryo için belirttiğiniz uygulamayı çalıştırırken kullanılır. Mpgo.exe'nin sonraki çalışmaları için yerel görüntülerin yeniden oluşturulmasını önler. Bu seçeneği belirtirseniz, uygulamanızı çalıştırmayı tamamladığınızda, önbellekte üst öğesi olmayan yerel görüntüler olabilir. Bu durumda, Mpgo. exe ' yi aynı senaryo ve derleme listesi ile çalıştırın ve bu yerel görüntüleri kaldırmak için `–RemoveNativeImages` parametresini kullanın.|
|`-RemoveNativeImages`|`–LeaveNativeImages` belirtildiği bir çalıştırıldan temizler. `-RemoveNativeImages`belirtirseniz, Mpgo. exe `-64bit` ve `–AssemblyList`dışındaki tüm bağımsız değişkenleri yoksayar ve tüm belgelenmiş yerel görüntüleri kaldırdıktan sonra çıkar.|

## <a name="remarks"></a>Açıklamalar
 Komut satırında hem `–AssemblyList` hem de `- AssemblyListFile` birden çok kez kullanabilirsiniz.

 Derlemeleri belirtirken tam yol adları belirtmezseniz, Mpgo.exe geçerli dizinde arar. Yanlış bir yol belirtirseniz, Mpgo.exe bir hata iletisi görüntüler, ancak diğer derlemeler için veri oluşturmaya devam eder. Eğitim senaryosu sırasında yüklenmemiş bir derleme belirtirseniz, o derleme için eğitim verisi oluşturulmaz.

 Listedeki bir derleme genel derleme önbelleğinde ise, profil bilgilerini içerecek şekilde güncelleştirilmez.  Profil bilgilerini toplamak için onu genel derleme önbelleğinden kaldırın.

 Ngen.exe ve Mpgo.exe'nin kullanılması yalnızca yönetilen büyük uygulamalar için önerilir, çünkü önceden derlenmiş yerel görüntülerin yararı genellikle yalnızca çalışma zamanında önemli ölçüde JIT derlemesini kaldırdığında görülür. Yoğun şekilde ayarlı olmayan "Merhaba Dünya" stil uygulamalarında Mpgo. exe ' yi çalıştırmak hiçbir avantaj sağlamayacaktır ve Mpgo. exe, profil verilerini toplayamayabilir.

> [!NOTE]
> Ngen.exe ve Mpgo.exe, ASP.NET uygulamaları ve Windows Communication Foundation (WCF) hizmetleri için önerilmez.  
  
## <a name="to-use-mpgoexe"></a>Mpgo.exe'yi kullanmak için  
  
1. Visual Studio Ultimate 2012 ve uygulamanızın yüklü olduğu bir bilgisayar kullanın.  
  
2. Mpgo.exe'yi bir yönetici olarak gerekli parametrelerle çalıştırın.  Örnek komutlar için sonraki bölüme bakın.  
  
     İyileştirilmiş ara dil (IL) derlemeleri `–OutDir` parametresi tarafından belirtilen klasörde oluşturulur (örneklerde, bu `C:\Optimized` klasörüdür).  
  
3. Ngen. exe için kullandığınız Il derlemelerini, `–OutDir`tarafından belirtilen dizinden profil bilgilerini içeren yeni Il Derlemeleriyle değiştirin.  
  
4. Mpgo.exe tarafından sağlanan görüntüleri kullanan uygulama kurulumu en iyi duruma getirilmiş yerel görüntüleri yükler.  
  
## <a name="suggested-workflow"></a>Önerilen İş Akışı  
  
1. Mpgo. exe ' yi `–Scenario` parametresiyle kullanarak, iyileştirilmiş bir IL derlemeleri kümesi oluşturun.  
  
2. En iyi duruma getirilmiş IL derlemelerini kaynak denetime girin.  
  
3. Derleme sürecinde, Ngen. exe ' ye geçirilecek iyileştirilmiş Il görüntüleri oluşturmak için `–Import` parametresiyle Mpgo. exe ' yi çağırın.  
  
 Bu işlem tüm derlemelerin en iyi duruma getirilmiş verilere sahip olmasını sağlar. Güncelleştirilmiş en iyi duruma getirilmiş derlemeleri daha sık iade ederseniz (1. ve 2. adım), tüm üretim geliştirme sürecinde performans numaraları daha tutarlı olur.  
  
## <a name="using-mpgoexe-from-visual-studio"></a>Visual Studio'dan Mpgo.exe'yi kullanma  
 Mpgo. exe dosyasını Visual Studio 'dan çalıştırabilirsiniz (bkz. [nasıl yapılır: yapı olaylarını belirtmeC#()](/visualstudio/ide/how-to-specify-build-events-csharp)) aşağıdaki kısıtlamalara göre:  
  
- Visual Studio makroları aynı zamanda varsayılan olarak sonlarında eğik çizgiler içerdiğinden, sonda eğik çizgileri olan tırnak işaretli yollar kullanamazsınız. (Örneğin, `–OutDir "C:\Output Folder\"` geçersiz.) Bu kısıtlamayı geçici olarak çözmek için sondaki eğik çizgiden çıkma yapabilirsiniz. (Örneğin, bunun yerine `-OutDir "$(OutDir)\"` kullanın.)  
  
- Varsayılan olarak, Mpgo.exe Visual Studio yapı yolu üzerinde değildir. Yolu Visual Studio'ya eklemeli ya da Mpgo komut satırında tam yolu belirtmelisiniz. Visual Studio 'da derleme sonrası olayında `–Scenario` veya `–Import` parametresini kullanabilirsiniz. Ancak, tipik işlem, Visual Studio Geliştirici Komut İstemi bir kez `–Scenario` ve ardından her derlemeden sonra iyileştirilmiş derlemeleri güncelleştirmek için `–Import` kullanır; Örneğin: `"C:\Program Files\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\mpgo.exe" -import "$(OutDir)tmp" -assemblylist "$(TargetPath)" -outdir "$(OutDir)\"`.  
  
<a name="samples"></a>   
## <a name="examples"></a>Örnekler  
 Visual Studio için Geliştirici Komut İstemi aşağıdaki Mpgo. exe komutu bir vergi uygulamasını iyileştirir:  
  
```console  
mpgo –scenario "C:\MyApp\MyTax.exe /params par" –AssemblyList Mytax.dll MyTaxUtil2011.dll –OutDir C:\Optimized –TimeOut 15  
```  
  
 Aşağıdaki Mpgo.exe komut bir ses uygulamasını en iyi duruma getirir:  
  
```console  
mpgo –scenario "C:\MyApp\wav2wma.exe –input song1.wav –output song1.wma" –AssemblyList transcode.dll –OutDir C:\Optimized –TimeOut 15  
```  
  
 Aşağıdaki Mpgo.exe komutu yeni sürümleri en iyi duruma getirmek için daha önce en iyi duruma getirilmiş derlemelere ait verileri kullanır:  
  
```console  
mpgo.exe -import "C:\Optimized" -assemblylist "C:\MyApp\MyTax.dll" "C:\MyApp\MyTaxUtil2011.dll" -outdir C:\ReOptimized  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ngen.exe (Yerel Görüntü Oluşturucu)](ngen-exe-native-image-generator.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
- [Masaüstü uygulamalarınız için başlatma performansını artırma](https://devblogs.microsoft.com/dotnet/improving-launch-performance-for-your-desktop-applications/)
- [.NET 4,5 performans Iyileştirmelerine genel bakış](https://docs.microsoft.com/archive/msdn-magazine/2012/april/clr-an-overview-of-performance-improvements-in-net-4-5)
