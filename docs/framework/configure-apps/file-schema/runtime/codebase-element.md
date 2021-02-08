---
description: 'Daha fazla bilgi edinin: <codeBase> öğesi'
title: <codeBase> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
ms.openlocfilehash: 714392444d3ee3db9126e9fe67832cb5f0bf5e3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795124"
---
# <a name="codebase-element"></a>\<codeBase> Öğesi

Ortak dil çalışma zamanının bir derlemeyi bulabilecekleri yeri belirtir.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<codeBase>**

## <a name="syntax"></a>Syntax

```xml
   <codeBase
        version="Assembly version"
        href="URL of assembly"/>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`href`|Gerekli öznitelik.<br /><br /> Çalışma zamanının belirtilen derleme sürümünü bulabileceği URL 'YI belirtir.|
|`version`|Gerekli öznitelik.<br /><br /> Kod temelinin uygulandığı derlemenin sürümünü belirtir. Bütünleştirilmiş kod sürümü numarası, *birincil. ikincil. derleme. düzeltme*.|

## <a name="version-attribute"></a>sürüm özniteliği

|Değer|Açıklama|
|-----------|-----------------|
|Sürüm numarasının her bir bölümü için geçerli değerler 0 ile 65535 arasında geçerlidir.|Geçerli değildir.|

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`buildproviders`|Özel kaynak dosyalarını derlemek için kullanılan yapı sağlayıcılarının koleksiyonunu tanımlar. Herhangi bir sayıda derleme sağlayıcısına sahip olabilirsiniz.|
|`compilation`|ASP.NET tarafından kullanılan tüm derleme ayarlarını yapılandırır.|
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|
|`System.web`|ASP.NET yapılandırma bölümünün kök öğesini belirtir.|

## <a name="remarks"></a>Açıklamalar

Çalışma zamanının **\<codeBase>** bir makine yapılandırma dosyası veya yayımcı ilke dosyasında ayarı kullanması için, dosyanın derleme sürümünü de yeniden yönlendirmesi gerekir. Uygulama yapılandırma dosyaları, derleme sürümünü yönlendirmeksizin bir kod temeli ayarına sahip olabilir. Hangi derleme sürümünün kullanılacağını belirledikten sonra, çalışma zamanı sürümü belirleyen dosyadan kod temeli ayarını uygular. Kod temeli belirtilmemişse, çalışma zamanı derleme için her zamanki şekilde araştırılmış.

Derlemenin tanımlayıcı bir adı varsa, kod temeli ayarı yerel intranette veya Internet 'te herhangi bir yerde olabilir. Derleme özel bir derlemedir, kod temeli ayarı uygulamanın dizinine göreli bir yol olmalıdır.

Tanımlayıcı adı olmayan derlemeler için sürüm yok sayılır ve yükleyici içindeki ilk görünümü kullanır \<codebase> \<dependentAssembly> . Uygulama yapılandırma dosyasında bağlamayı başka bir derlemeye yönlendiren bir giriş varsa, derleme sürümü bağlama isteğiyle eşleşmezse bile yeniden yönlendirme öncelikli olur.

## <a name="example"></a>Örnek

Aşağıdaki örnek, çalışma zamanının bir derlemeyi bulabileceği yeri nasıl belirtbileceğinizi gösterir.

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
         <dependentAssembly>
            <assemblyIdentity name="myAssembly"
                              publicKeyToken="32ab4ba45e0a69a1"
                              culture="neutral" />
            <codeBase version="2.0.0.0"
                      href="http://www.litwareinc.com/myAssembly.dll"/>
         </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)
- [Bir derlemenin konumunu belirtin](../../../../standard/assembly/location.md)
- [Çalışma zamanının derlemeleri nasıl konumlandırır](../../../deployment/how-the-runtime-locates-assemblies.md)
