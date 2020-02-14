---
title: Kod Erişim Güvenlik İlkesi Uyumluluğu ve Geçiş
ms.date: 03/30/2017
helpviewer_keywords:
- policy migration, compatibility
- CLR policy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
ms.openlocfilehash: 949739b3336a9182eef583cc405e60e09d7ec09d
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217157"
---
# <a name="code-access-security-policy-compatibility-and-migration"></a>Kod Erişim Güvenlik İlkesi Uyumluluğu ve Geçiş

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Kod erişim güvenliği (CAS) ilke bölümü .NET Framework 4 ' te kullanımdan kaldırılmıştır. Sonuç olarak, eski ilke türlerini ve üyelerini [açıkça](#explicit_use) veya [örtük](#implicit_use) olarak çağırırsanız (diğer türler ve Üyeler aracılığıyla) derleme uyarıları ve çalışma zamanı özel durumları ile karşılaşabilirsiniz.

Uyarıları ve hataları aşağıdakilerden birini yaparak önleyebilirsiniz:

- Kullanılmayan çağrılar için .NET Framework 4 yerine [geçme](#migration) .

   \- veya-

- Eski CAS ilkesi davranışını kabul etmek için [\<NetFx40_LegacySecurityPolicy > yapılandırma öğesini](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) kullanma.

Bu konu aşağıdaki bölümleri içermektedir:

- [Açık kullanım](#explicit_use)

- [Örtülü kullanım](#implicit_use)

- [Hatalar ve Uyarılar](#errors_and_warnings)

- [Geçiş: eski çağrılar için değiştirme](#migration)

- [Uyumluluk: CAS Ilkesi eski seçeneğini kullanma](#compatibility)

<a name="explicit_use"></a>

## <a name="explicit-use"></a>Açık kullanım

Güvenlik ilkesini doğrudan işleyen veya korumalı alan için CAS ilkesi gerektiren Üyeler artık kullanılmıyor ve varsayılan olarak hata üretecektir.

Bunlara şunlar örnek verilmiştir:

- <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.HostSecurityManager.DomainPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.Policy.PolicyLevel.CreateAppDomainLevel%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.LoadPolicyLevelFromString%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.LoadPolicyLevelFromFile%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolveSystemPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolvePolicyGroups%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.PolicyHierarchy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.SavePolicy%2A?displayProperty=nameWithType>

<a name="implicit_use"></a>

## <a name="implicit-use"></a>Örtülü kullanım

Çeşitli derleme yükleme aşırı yüklemeleri, CAS ilkesinin örtük kullanımları nedeniyle hata üretir. Bu aşırı yüklemeler, CAS ilkesini çözümlemek ve bir derleme için izin verme kümesi sağlamak için kullanılan bir <xref:System.Security.Policy.Evidence> parametresi alır.

Bazı örnekler aşağıda verilmiştir. Kullanılmayan aşırı yüklemeler parametre olarak <xref:System.Security.Policy.Evidence> alan olanlardır:

- <xref:System.Activator.CreateInstanceFrom%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.ExecuteAssemblyByName%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

<a name="errors_and_warnings"></a>

## <a name="errors-and-warnings"></a>Hatalar ve Uyarılar

Kullanılmayan türler ve Üyeler, kullanıldıkları zaman aşağıdaki hata iletilerini oluşturur. <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> türünün kendisi kullanımdan kaldırılmadığını unutmayın.

Derleme zamanı uyarısı:

`warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`

Çalışma zamanı özel durumu:

<xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`

<a name="migration"></a>

## <a name="migration-replacement-for-obsolete-calls"></a>Geçiş: eski çağrılar için değiştirme

### <a name="determining-an-assemblys-trust-level"></a>Derlemenin güven düzeyini belirleme

CAS ilkesi, genellikle bir derlemenin veya uygulama etki alanının izin verme kümesini veya güven düzeyini belirlemede kullanılır. .NET Framework 4, güvenlik ilkesini çözümlemek zorunda olmayan aşağıdaki yararlı özellikleri sunar:

- <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>

### <a name="application-domain-sandboxing"></a>Uygulama etki alanı korumalı alana alma

<xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> yöntemi, genellikle bir uygulama etki alanındaki derlemeler korumalı alana alma için kullanılır. .NET Framework 4, bu amaçla <xref:System.Security.Policy.PolicyLevel> kullanmak zorunda olmayan üyeleri kullanıma sunar. Daha fazla bilgi için bkz. [nasıl yapılır: bir korumalı alana kısmen güvenilen kod çalıştırma](how-to-run-partially-trusted-code-in-a-sandbox.md).

### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a>Kısmen güvenilen kod için güvenli veya makul bir Izin kümesi belirleme

Ana bilgisayarların, genellikle korumalı alana alma barındırılan kodu için uygun izinleri belirlemesi gerekir. .NET Framework 4 ' den önce, CAS ilkesi bunu <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> yöntemiyle yapmak için bir yol sağladı. Bunun yerine, .NET Framework 4, sağlanan kanıt için güvenli, standart bir izin kümesi döndüren <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> yöntemini sağlar.

### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a>Korumalı alana alma olmayan senaryolar: derleme yükleri için aşırı yüklemeler

Derleme yükü aşırı yüklemesi kullanmanın nedeni, derleme korumalı alana alma yerine, aksi durumda kullanılamayan parametreleri kullanmak olabilir. .NET Framework 4 ' den başlayarak, bir parametre olarak bir <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> nesnesi gerektirmeyen derleme yükü aşırı yüklemeleri, örneğin <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, bu senaryoyu etkinleştirin.

Bir derlemenin korumalı alanını istiyorsanız, <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> aşırı yüklemeyi kullanın.

<a name="compatibility"></a>

## <a name="compatibility-using-the-cas-policy-legacy-option"></a>Uyumluluk: CAS Ilkesi eski seçeneğini kullanma

[\<NetFx40_LegacySecurityPolicy > yapılandırma öğesi](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) , bir işlemin veya KITAPLıĞıN eski CAS ilkesini kullanmasını belirtmenize olanak tanır. Bu öğeyi etkinleştirdiğinizde, ilke ve kanıt aşırı yüklemeleri Framework 'ün önceki sürümlerinde olduğu gibi çalışacaktır.

> [!NOTE]
> CAS ilkesi davranışı çalışma zamanı sürümü temelinde belirtilmiştir, bu nedenle bir çalışma zamanı sürümü için CAS ilkesini değiştirmek, başka bir sürümün CAS ilkesini etkilemez.

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: bir korumalı alanda kısmen güvenilen kod çalıştırma](how-to-run-partially-trusted-code-in-a-sandbox.md)
- [Güvenli Kodlama Yönergeleri](../../standard/security/secure-coding-guidelines.md)
