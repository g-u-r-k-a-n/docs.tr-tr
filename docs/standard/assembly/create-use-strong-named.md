---
title: Tanımlayıcı adlı ssemblies oluşturma ve kullanma
ms.date: 08/19/2019
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, about strong-named assemblies
- strong-named assemblies
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, scenarios
- assemblies [.NET Framework], strong-named
- strong-named assemblies, loading into trusted application domains
- assembly binding, strong-named
ms.assetid: ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9
ms.openlocfilehash: 700eca16e7755823456c3e3ace17eb5e6b3526ac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122504"
---
# <a name="create-and-use-strong-named-assemblies"></a>Tanımlayıcı adlı derlemeler oluşturma ve kullanma

Tanımlayıcı ad, derleme kimliğinden (basit metin adı, sürüm numarası ve kültür bilgileri (sağlanmışsa) ve bir ortak anahtar ve dijital imza ile oluşur. Karşılık gelen özel anahtar kullanılarak derleme dosyasından oluşturulur. (Derleme dosyası, derlemeyi oluşturan tüm dosyaların adlarını ve karmalarını içeren derleme bildirimini içerir.)

> [!WARNING]
> Güvenlik için tanımlayıcı adlara güvenmeyin. Yalnızca benzersiz bir kimlik sağlarlar.

Tanımlayıcı adlı bir derleme, yalnızca diğer tanımlayıcı adlı derlemelerden türleri kullanabilir. Aksi takdirde, tanımlayıcı adlı derlemenin bütünlüğü tehlikeye girebilir.

> [!NOTE]
> .NET Core, tanımlayıcı adlı derlemeleri desteklese de, .NET Core kitaplığındaki tüm derlemeler imzalansa da, üçüncü taraf derlemelerin çoğunluğunun tanımlayıcı adlara ihtiyacı yoktur. Daha fazla bilgi için bkz. GitHub 'da [tanımlayıcı ad imzalama](https://github.com/dotnet/corefx/blob/master/Documentation/project-docs/strong-name-signing.md) .

## <a name="strong-name-scenario"></a>Tanımlayıcı ad senaryosu

Aşağıdaki senaryo, bir derlemeyi güçlü bir adla imzalama ve daha sonra bu ada göre başvuruda bulunma sürecini özetler.

1. Derleme A, aşağıdaki yöntemlerden biri kullanılarak bir tanımlayıcı ad ile oluşturulur:

    - Visual Studio gibi güçlü adlar oluşturmayı destekleyen bir geliştirme ortamı kullanma.

    - Bir komut satırı derleyicisi veya [derleme Bağlayıcısı (al. exe)](../../framework/tools/al-exe-assembly-linker.md)kullanarak, [tanımlayıcı ad Aracı (sn. exe)](../../framework/tools/sn-exe-strong-name-tool.md) kullanarak bir şifreleme anahtarı çifti oluşturma ve bu anahtar çiftini derlemeye atama. Windows SDK hem sn. exe hem de al. exe sağlar.

2. Geliştirme ortamı veya aracı, geliştiricinin özel anahtarıyla derlemenin bildirimini içeren dosyanın karmasını imzalar. Bu dijital imza, derleme A 'nın bildirimini içeren taşınabilir çalıştırılabilir (PE) dosyasında depolanır.

3. Derleme B, A derlemesi tüketicisidir. Derleme B 'nin bildiriminin başvuru bölümü, derleme A 'nın ortak anahtarını temsil eden bir belirteç içerir. Belirteç, tam ortak anahtarın bir bölümüdür ve alan kazanmak için anahtarın kendisi yerine kullanılır.

4. Ortak dil çalışma zamanı, derleme genel derleme önbelleğine yerleştirildiğinde tanımlayıcı ad imzasını doğrular. Çalışma zamanında tanımlayıcı ada göre bağlamada ortak dil çalışma zamanı, derleme B 'nin bildiriminde depolanan anahtarı, derleme A için tanımlayıcı ad oluşturmak için kullanılan anahtarla karşılaştırır. .NET Framework güvenlik denetimi başarılı olursa ve bağlama başarılı olursa, derleme B, derleme A 'nın bitleri kurcalanmayan ve bu bitlerin aslında A derlemesi geliştiricilerinden geldiği garantisi vardır.

> [!NOTE]
> Bu senaryo güven sorunlarına yönelik değildir. Derlemeler, güçlü bir ada ek olarak tam Microsoft Authenticode imzalarını taşıyabilir. Authenticode imzaları, güven kuran bir sertifika içerir. Tanımlayıcı adların kodun bu şekilde imzalanmasını gerektirmediğini unutmayın. Tanımlayıcı adlar yalnızca benzersiz bir kimlik sağlar.

## <a name="bypass-signature-verification-of-trusted-assemblies"></a>Güvenilen derlemelerin imza doğrulamasını atla

.NET Framework 3,5 hizmet paketi 1 ' den başlayarak, bir derleme tam güvenli uygulama etki alanına yüklendiğinde, `MyComputer` bölgesinin varsayılan uygulama etki alanı gibi tanımlayıcı ad imzaları doğrulanmaz. Bu, tanımlayıcı ad atlama özelliği olarak adlandırılır. Tam güven ortamında, imzaları ne olursa olsun, imzalı, tam güvenle derlemeler için <xref:System.Security.Permissions.StrongNameIdentityPermission> talepleri her zaman başarılı olur. Güçlü ad atlama özelliği, bu durumda derlemelerin daha hızlı yüklenmesine izin vermek için tam güven derlemelerinin tanımlayıcı ad imzası doğrulamasının gereksiz ek yükünü önler.

Atlama özelliği, bir tanımlayıcı ad ile imzalanmış ve aşağıdaki özelliklere sahip olan her derleme için geçerlidir:

- <xref:System.Security.Policy.StrongName> bulgu olmadan tam güvenilir (örneğin, `MyComputer` Zone bulgusu vardır).

- Tam güvenilir bir <xref:System.AppDomain>yüklendi.

- Bu <xref:System.AppDomain><xref:System.AppDomainSetup.ApplicationBase%2A> özelliği altındaki bir konumdan yüklendi.

- Gecikmeli imza değildir.

Bu özellik ayrı uygulamalar veya bir bilgisayar için devre dışı bırakılabilir. Bkz. [nasıl yapılır: güçlü adı atlama özelliğini devre dışı bırakma](disable-strong-name-bypass-feature.md).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Nasıl yapılır: genel-özel anahtar çifti oluşturma](create-public-private-key-pair.md)|Bir derlemeyi imzalamak için bir şifreleme anahtarı çiftinin nasıl oluşturulacağını açıklar.|
|[Nasıl yapılır: bir derlemeyi güçlü bir adla Imzalama](sign-strong-name.md)|Tanımlayıcı adlı derlemenin nasıl oluşturulacağını açıklar.|
|[Gelişmiş tanımlayıcı adlandırma](enhanced-strong-naming.md)|4,5 .NET Framework güçlü adlarla ilgili geliştirmeleri açıklar.|
|[Nasıl yapılır: tanımlayıcı adlı bir derlemeye başvurma](reference-strong-named.md)|Derleme zamanında veya çalışma zamanında tanımlayıcı adlı bir derlemede türlerin veya kaynakların nasıl başvurululacağını açıklar.|
|[Nasıl yapılır: tanımlayıcı adı atlama özelliğini devre dışı bırakma](disable-strong-name-bypass-feature.md)|Tanımlayıcı ad imzalarının doğrulanmasını atlayan özelliğin nasıl devre dışı bırakılacağını açıklar. Bu özellik tüm veya belirli uygulamalar için devre dışı bırakılabilir.|
|[Derlemeler oluştur](create.md)|Tek dosyalı ve çoklu dosya Derlemeleriyle genel bir bakış sağlar.|
|[Visual Studio 'da bir derlemeyi imzalamayı geciktirme](/visualstudio/ide/managing-assembly-and-manifest-signing#how-to-sign-an-assembly-in-visual-studio)|Derleme oluşturulduktan sonra bir derlemeyi güçlü bir adla nasıl imzalayabileceğinizi açıklar.|
|[Sn. exe (tanımlayıcı ad aracı)](../../framework/tools/sn-exe-strong-name-tool.md)|Güçlü adlara sahip derlemeler oluşturulmasına yardımcı olan .NET Framework dahil olan aracı açıklar. Bu araç, temel yönetim, imza oluşturma ve imza doğrulaması için seçenekler sağlar.|
|[Al. exe (bütünleştirilmiş kod bağlayıcı)](../../framework/tools/al-exe-assembly-linker.md)|Modüller veya kaynak dosyalarından derleme bildirimine sahip bir dosya üreten .NET Framework dahil olan aracı açıklar.|
