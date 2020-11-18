---
title: Asıl ve Kimlik Nesneleri
description: .NET 'teki kullanıcıları temsil eden Identity Objects hakkında bilgi edinin. Ayrıca, bir rolün & bir kimlik nesnesini kapsülleyen Principal nesneleri hakkında bilgi edinin.
ms.date: 07/15/2020
helpviewer_keywords:
- WindowsIdentity objects
- GenericIdentity objects
- GenericPrincipal objects
- identity objects, about identity objects
- security [.NET], identity objects
- principal objects, about principal objects
- security [.NET], principals
- WindowsPrincipal objects
ms.assetid: aa5930ad-f3d7-40aa-b6f6-c6edcd5c64f7
ms.openlocfilehash: cfda506fc29e9a86e97b3c99faf2d4155c894f03
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824245"
---
# <a name="principal-and-identity-objects"></a>Asıl ve Kimlik Nesneleri

> [!NOTE]
> Bu makale Windows için geçerlidir.
>
> ASP.NET Core hakkında bilgi için bkz. [ASP.NET Core Security](/aspnet/core/security/).

Yönetilen kod, bir <xref:System.Security.Principal.IPrincipal> nesneye yönelik bir başvuru içeren bir nesne aracılığıyla bir Sorumlunun kimliğini veya rolünü bulabilir <xref:System.Security.Principal.IIdentity> . Kimlik ve asıl nesneleri kullanıcı ve grup hesapları gibi tanıdık kavramlarla karşılaştırmak faydalı olabilir. Çoğu ağ ortamında, Kullanıcı hesapları kişileri veya programları temsil ederken grup hesapları bazı kullanıcı kategorilerini ve sahip oldukları hakları temsil eder. Benzer şekilde, .NET Identity nesneleri kullanıcıları temsil ederken roller de üyelikleri ve güvenlik bağlamlarını temsil eder. .NET ' te, Principal nesnesi hem bir kimlik nesnesini hem de bir rolü kapsar. .NET uygulamaları, kimlik veya daha yaygın olarak rolün üyeliği temelinde sorumlu için haklar verir.  
  
## <a name="identity-objects"></a>Kimlik nesneleri

Identity nesnesi doğrulanan kullanıcı veya varlıkla ilgili bilgileri kapsüller. En temel seviyesindeki kimlik nesnelerinde bir ad ve kimlik doğrulama türü bulunur. Ad, bir kullanıcının adı ya da bir Windows hesabının adı olabilir, ancak kimlik doğrulama türü Kerberos V5 gibi desteklenen bir oturum açma Protokolü veya özel bir değer olabilir. .NET, <xref:System.Security.Principal.GenericIdentity> <xref:System.Security.Principal.WindowsIdentity> Uygulamanızın Windows kimlik doğrulamasına dayanmasını istediğinizde kullanılabilecek, çoğu özel oturum açma senaryosu ve daha özelleştirilmiş bir nesne için kullanılabilecek bir nesne tanımlar. Ayrıca, Özel Kullanıcı bilgilerini kapsülleyen kendi kimlik sınıfınızı tanımlayabilirsiniz.  
  
<xref:System.Security.Principal.IIdentity>Arabirim, Kerberos V5 veya NTLM gibi bir ad ve kimlik doğrulama türüne erişim için özellikleri tanımlar. Tüm **kimlik** sınıfları **IIdentity** arabirimini uygular. Bir iş parçacığının çalıştırıldığı bir **kimlik** nesnesi ve Windows NT işlem belirteci arasında gerekli bir ilişki yoktur. Ancak, **kimlik** nesnesi bir **WindowsIdentity** Nesnecidir, kimliğin bir Windows NT güvenlik belirtecini temsil ettiği varsayılır.  
  
## <a name="principal-objects"></a>Principal nesneleri

Principal nesnesi, kodun çalıştığı güvenlik bağlamını temsil eder. Rol tabanlı güvenlik uygulayan uygulamalar, bir asıl nesneyle ilişkili role dayalı olarak haklar verir. Kimlik nesnelerine benzer şekilde, .NET de bir <xref:System.Security.Principal.GenericPrincipal> nesne ve <xref:System.Security.Principal.WindowsPrincipal> nesne sağlar. Ayrıca, kendi özel asıl sınıflarınızı tanımlayabilirsiniz.  
  
<xref:System.Security.Principal.IPrincipal>Arabirim, ilişkili bir **kimlik** nesnesine erişmek için bir özellik ve **asıl** nesne tarafından tanımlanan kullanıcının belirli bir rolün üyesi olup olmadığını belirlemek için bir yöntem tanımlar. Tüm **asıl** sınıflar, gereken ek özellikleri ve yöntemleri de, **IPrincipal** arabirimini ve uygular. Örneğin, ortak dil çalışma zamanı, Windows NT veya Windows 2000 Grup üyeliğini rollere eşlemek için ek işlevsellik uygulayan **WindowsPrincipal** sınıfını sağlar.  
  
Bir **Principal** nesnesi, <xref:System.Runtime.Remoting.Messaging.CallContext> bir uygulama etki alanı () içindeki bir çağrı bağlamı () nesnesine bağlanır <xref:System.AppDomain> . Her yeni **AppDomain** ile her zaman bir varsayılan çağrı bağlamı oluşturulur, bu nedenle **asıl** nesneyi kabul etmek için her zaman bir çağrı bağlamı bulunur. Yeni bir iş parçacığı oluşturulduğunda iş parçacığı için bir **CallContext** nesnesi de oluşturulur. **Asıl** nesne başvurusu, oluşturma iş parçacığından yeni Iş parçacığının **CallContext**'e otomatik olarak kopyalanır. Çalışma zamanı hangi **asıl** nesnenin iş parçacığı oluşturucusuna ait olduğunu Belirleyeleyemiyorsa, **asıl** ve **kimlik** nesnesi oluşturma için varsayılan ilkeyi izler.  
  
Yapılandırılabilir bir uygulama etki alanına özgü ilke, yeni bir uygulama etki alanıyla hangi tür **asıl** nesnenin ilişkilendirileceğine karar verme kurallarını tanımlar. Güvenlik ilkesinin izin verdiği durumlarda çalışma zamanı, yürütmenin geçerli iş parçacığıyla ilişkili işletim sistemi belirtecini yansıtan **asıl** ve **kimlik** nesneleri oluşturabilir. Varsayılan olarak, çalışma zamanı kimliği doğrulanmamış kullanıcıları temsil eden **asıl** ve **kimlik** nesnelerini kullanır. Çalışma zamanı, kod onlara erişmeye çalışana kadar bu varsayılan **sorumlusu** ve **kimlik** nesnelerini oluşturmaz.  
  
Bir uygulama etki alanı oluşturan güvenilir kod, varsayılan **asıl** ve **kimlik** nesnelerinin oluşturulmasını denetleyen uygulama etki alanı ilkesini ayarlayabilir. Bu uygulama etki alanına özgü ilke, bu uygulama etki alanındaki tüm yürütme iş parçacıkları için geçerlidir. Yönetilmeyen ve güvenilen bir ana bilgisayar kendiliğinden bu ilkeyi ayarlayabilme özelliğine sahiptir, ancak bu ilkeyi ayarlayan yönetilen kodun <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> etki alanı ilkesini denetleme için olması gerekir.  
  
**Ana** nesne, uygulama etki alanları arasında, ancak aynı işlem içinde (ve dolayısıyla aynı bilgisayarda) iletilirken, uzaktan iletişim altyapısı, çağıran bağlamı Ile ilişkili **Principal** nesnesine bir başvuru kopyalar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: WindowsPrincipal Nesnesi Oluşturma](how-to-create-a-windowsprincipal-object.md)
- [Nasıl yapılır: GenericPrincipal ve GenericIdentity Nesneleri Oluşturma](how-to-create-genericprincipal-and-genericidentity-objects.md)
- [Asıl Nesneyi Değiştirme](replacing-a-principal-object.md)
- [Kimliğe Bürünme ve Geri Alma](impersonating-and-reverting.md)
- [Rol tabanlı güvenlik](role-based-security.md)
- [Temel Güvenlik Kavramları](key-security-concepts.md)
- [ASP.NET Core güvenliği](/aspnet/core/security/)
