---
title: .NET Framework Araçları
ms.date: 03/30/2017
helpviewer_keywords:
- command line, .NET Framework tools
- .NET Framework, tools
- tools [.NET Framework]
- running .NET Framework tools
ms.assetid: a2ca532d-91f7-426a-9303-417c2ee1247c
ms.openlocfilehash: 4503e2cff18f4aa901d20c76cfe4076a7fed3600
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715776"
---
# <a name="net-framework-tools"></a>.NET Framework Araçları

.NET Framework araçları, .NET Framework'ü hedefleyen uygulamaları ve bileşenleri oluşturmayı, dağıtmayı ve yönetmeyi kolaylaştırmayı sağlar.

Bu bölümde açıklanan .NET Framework Araçlarının çoğu Visual Studio ile otomatik olarak yüklenir. Visual Studio'yu indirmek için [Visual Studio İndirmeler](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) sayfasını ziyaret edin.

Derleme Önbellek Görüntüleyici (*Shfusion.dll)* dışında komut satırından tüm araçları çalıştırabilirsiniz. Dosya Gezgini'nden *Shfusion.dll'ye* erişmelisiniz.
  
Komut satırı araçlarını çalıştırmanın en iyi yolu, Visual Studio için Geliştirici Komut İstemini kullanmaktır. Bu yardımcı programlar, yükleme klasörüne gitmeden araçları kolayca çalıştırmanıza olanak sağlar. Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.

> [!NOTE]
> Bazı araçlar, 32-bit bilgisayarlar veya 64-bit bilgisayarlar için özeldir. Bilgisayarınız için aracın uygun sürümünü çalıştırdığınızdan emin olun.

## <a name="in-this-section"></a>Bu bölümde

- [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](al-exe-assembly-linker.md)  
Modüller ya da kaynak dosyalarından derleme bildirimi içeren bir dosya oluşturur.

- [Aximp.exe (Windows Forms ActiveX Denetim İçeri Aktarıcı)](aximp-exe-windows-forms-activex-control-importer.md)  
Bir ActiveX denetimi için bir COM tür kitaplığındaki tür tanımlarını bir Windows Forms denetimine dönüştürür.

- [Caspol.exe (Kod Erişimi Güvenliği İlke Aracı)](caspol-exe-code-access-security-policy-tool.md)  
Makine ilke düzeyi, kullanıcı ilke düzeyi ve kurumsal ilke düzeyi için güvenlik ilkesi görüntülemenize ve yapılandırmanıza olanak tanır. .NET Framework 4 ve sonraki sürümlerinde [ \<CasPolicy> öğesi](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) ayarlanmadığı sürece bu araç `true`kod erişim güvenliği (CAS) ilkesini etkilemez. Daha fazla bilgi için [Güvenlik Değişiklikleri'ne](../security/security-changes.md)bakın.

- [Cert2spc.exe (Yazılım Yayımcısı Sertifika Test Aracı)](cert2spc-exe-software-publisher-certificate-test-tool.md)  
Bir veya daha fazla X.509 sertifikasından bir Yazılım Yayımcıları Sertifikası (SPC) oluşturur. Bu araç yalnızca test içindir.

- [Certmgr.exe (Sertifika Yönetim Aracı)](certmgr-exe-certificate-manager-tool.md)  
Sertifikaları, sertifika güven listelerini (CTL) ve sertifika çağırma listelerini (CRL) yönetir.

- [Clrver.exe (CLR Sürüm Aracı)](clrver-exe-clr-version-tool.md)  
Bilgisayarda ortak dil çalışma zamanının (CLR) tüm yüklü sürümlerini raporlar.

- [Komut İstemleri](developer-command-prompt-for-vs.md)  
.NET Framework araçlarını daha kolay kullanmanızı sağlar. Belirli ortam değişkenlerini otomatik olarak ayarlayan bir komut istemidir.

- [CorFlags.exe (CorFlags Dönüştürme Aracı)](corflags-exe-corflags-conversion-tool.md)  
Taşınabilir çalıştırılabilir (PE) görüntüsünün üstbilgisine ait CorFlags bölümünü yapılandırmanıza olanak sağlar.

- [Fuslogvw.exe (Bütünleştirilmiş Kod Bağlaması Günlük Görüntüleyici)](fuslogvw-exe-assembly-binding-log-viewer.md)  
Derleme hakkında, .NET Framework'ün çalışma zamanında neden derlemeyi bulamadığını tanılamanıza yardımcı olacak bilgiler görüntüler.

- [Gacutil.exe (Genel Derleme Önbelleği Aracı)](gacutil-exe-gac-tool.md)  
Genel derleme önbelleğinin içeriğini görüntülemenize, kullanmanıza ve önbelleği indirmenize olanak sağlar.

- [Ilasm.exe (IL Derleyici)](ilasm-exe-il-assembler.md)  
Ara dil'den (IL) taşınabilir çalıştırılabilir bir (PE) dosya oluşturur. IL'in beklendiği gibi çalışıp çalışmadığını belirlemek için elde edilen çalıştırılabilir dosyayı çalıştırabilirsiniz.

- [Ildasm.exe (IL Ayrıştırıcı)](ildasm-exe-il-disassembler.md)  
Ara dil (IL) kodunu içeren taşınabilir, çalıştırılabilir (PE) dosyayı alır ve IL Derleyicisi'ne (Ilasm.exe) girdi olmaya uygun bir metin dosyası oluşturur.

- [Installutil.exe (Yükleme Aracı)](installutil-exe-installer-tool.md)  
Belirtilen bir derlemedeki yükleyici bileşenlerini yürüterek sunucu kaynaklarını yüklemenize ve kaldırmanıza olanak verir. <xref:System.Configuration.Install> (Ad alanında sınıflarla çalışır.)

- [Lc.exe (Lisans Derleyici)](lc-exe-license-compiler.md)  
Lisans bilgileri içeren metin dosyalarını okur ve kaynak olarak çalıştırılabilir ortak bir dilde çalıştırılabilir bir *.licenses* dosyası üretir.

- [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](mage-exe-manifest-generation-and-editing-tool.md)  
Uygulama ve dağıtım bildirimleri oluşturmanıza, düzenlemenize ve imzalamanıza olanak verir. Komut satırı aracı olarak *Mage.exe,* hem toplu komut dosyalarından hem de ASP.NET uygulamaları da dahil olmak üzere diğer Windows tabanlı uygulamalardan çalıştırılabilir.

- [MageUI.exe (Bildirim Üretme ve Düzenleme Aracı, Grafik İstemci)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)  
Komut satırı aracı Mage.exe ile aynı işlevselliği destekler, ancak Windows tabanlı bir kullanıcı arabirimi (UI) kullanır. Komut satırı aracı *Mage.exe*ile aynı işlevselliği destekler, ancak Windows tabanlı bir kullanıcı arabirimi (UI) kullanır.

- [MDbg.exe (.NET Framework Komut Satırı Hata Ayıklayıcı)](mdbg-exe.md)  
Araç satıcılarının ve uygulama geliştiricilerin, .NET Framework ortak dil çalışma zamanını hedefleyen programlardaki hataları bulmalarına ve düzeltmelerine yardımcı olur. Bu araç, hata ayıklama hizmetleri sağlamak için çalışma zamanı hata ayıklama API kullanır.

- [Mgmtclassgen.exe (Yönetim Türü Kesin Belirlenmiş Sınıf Oluşturucu)](mgmtclassgen-exe.md)  
Belirtilen bir Windows Yönetim Araçları (WMI) sınıfı için bir erken bağlanan bir yönetilen sınıf oluşturmanıza olanak sağlar.

- [Mpgo.exe (Yönetilen Profil Temelli İyileştirme Aracı)](mpgo-exe-managed-profile-guided-optimization-tool.md)  
Yaygın son kullanıcı senaryolarını kullanarak yerel görüntü derlemelerini ayarlamanıza olanak verir. Mpgo.exe, uygulama geliştiricisi tarafından seçilen eğitim senaryolarını kullanarak yerel görüntü uygulama derlemeleri (.NET Framework derlemeleri değil) için profil verileri oluşturmasına ve bunların kullanılmasına olanak verir.

- [Ngen.exe (Yerel Görüntü Oluşturucu)](ngen-exe-native-image-generator.md)  
Yerel görüntüler (işlemciye özel derlenmiş makine kodu içeren dosyalar) kullanarak yönetilen uygulamaların performansını artırır. Çalışma zamanı orijinal derlemeyi derlemek için anlık (JIT) derleyiciyi kullanmak yerine önbellekteki yerel görüntüleri kullanabilir.

- [Peverify.exe (PEVerify Aracı)](peverify-exe-peverify-tool.md)  
Microsoft ara dil (MSIL) kodunuzun ve ilişkili meta verilerinizin tür güvenlik gereksinimlerini karşılamasına yardımcı olur.

- [Regasm.exe (Derleme Kayıt Aracı)](regasm-exe-assembly-registration-tool.md)  
Bir derleme içindeki meta veriyi okur ve gerekli girişleri kayıt defterine ekler. Bu, COM istemcilerinin .NET Framework sınıfları olarak görünmesini sağlar.

- [Regsvcs.exe (.NET Hizmetleri Yükleme Aracı)](regsvcs-exe-net-services-installation-tool.md)  
Bir derlemeyi yükler ve kaydettirir, bir tür kitaplığı oluşturur ve belirtilen bir COM+ sürümü 1.0 uygulamasına yükler, bir sınıfa programlı şekilde eklediğiniz hizmetleri yapılandırır.

- [Resgen.exe (Kaynak Dosya Oluşturucu)](resgen-exe-resource-file-generator.md)  
Metin *(.txt* veya *.restext*) dosyalarını ve XML tabanlı kaynak biçimini (*.resx*) dosyalarını çalışma zamanı ikilisine *(.kaynaklar)* dönüştüren ve çalışma zamanı ikili yürütülebilir veya uydu derlemelerine derlen dosyalara.

- [SecAnnotate.exe (.NET Güvenlik Not Ekleyici Aracı)](secannotate-exe-net-security-annotator-tool.md)  
Derlemenin `SecurityCritical` `SecuritySafeCritical` bölümlerini ve bölümlerini tanımlar.

- [SignTool.exe (İmza Aracı)](signtool-exe.md)  
Dosyaları dijital olarak imzalar, dosyalardaki imzaları doğrular ve dosyalara zaman damgası ekler.

- [Sn.exe (Tanımlayıcı Ad Aracı)](sn-exe-strong-name-tool.md)  
Derlemelerin tanımlayıcı adlarla oluşturulmasına yardımcı olur. Bu araç, temel yönetim, imza oluşturma ve imza doğrulaması için seçenekler sağlar.

- [SOS.dll (SOS Hata Ayıklama Uzantısı)](sos-dll-sos-debugging-extension.md)  
İç ortak dil çalışma zamanı (CLR) ortamıyla ilgili bilgi sağlayarak, WinDbg.exe hata ayıklayıcısındaki ve Visual Studio'daki yönetilen programlarda hata ayıklamanıza yardımcı olur.

- [SqlMetal.exe (Kod Üretme Aracı)](sqlmetal-exe-code-generation-tool.md)  
.NET Framework'ün LINQ-SQL bileşenine kod ve eşleme oluşturur.

- [Storeadm.exe (Yalıtılmış Depolama Aracı)](storeadm-exe-isolated-storage-tool.md)  
Yalıtılmış depolamayı yönetir; kullanıcının mağazalarını listeleyen ve bunları silen seçenekler sağlar.

- [Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)](tlbexp-exe-type-library-exporter.md)  
Bir ortak dil çalışma zamanı derlemesinde tanımlanan türleri açıklayan bir tür kitaplığı oluşturur.

- [Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)](tlbimp-exe-type-library-importer.md)  
Bir COM tür kitaplığında bulunan tür tanımlarını bir ortak dil çalışma zamanı derlemesindeki eşdeğer tanımlara dönüştürür.

- [Winmdexp.exe (Windows Çalışma Zamanı Meta Veri Dışarı Aktarma Aracı)](winmdexp-exe-windows-runtime-metadata-export-tool.md)  
*.winmdobj* dosyası olarak derlenen ve hem Windows Runtime meta verilerini hem de uygulama bilgilerini içeren *bir .winmd* dosyası olarak paketlenmiş bir Windows Runtime bileşenine bir .NET Framework derlemesi dışa aktarın.

- [Winres.exe (Windows Forms Kaynak Düzenleyici)](winres-exe-windows-forms-resource-editor.md)  
Windows Forms tarafından kullanılan kullanıcı arabirimi (UI) kaynaklarını *(.resx* veya *.resources* files) yerelleştirmenize yardımcı olur. Dizeleri çevirebilir ve ardından yerelleştirilmiş dizeleri içerecek şekilde denetimleri boyutlandırabilir, taşıyabilir ve gizleyebilirsiniz.

## <a name="related-sections"></a>İlgili bölümler

- [WPF Araçları](https://docs.microsoft.com/previous-versions/ms742404(v=vs.110))  
isXPS Uygunluk aracı (isXPS.exe) ve performans profil oluşturma araçları gibi araçları içerir.

- [Windows Communication Foundation Araçları](../wcf/tools.md)  
Windows Communication Foundation (WCF) uygulamalarını oluşturmanızı, dağıtmanızı ve yönetmenizi kolaylaştıran araçlar içerir.
