---
description: 'Hakkında daha fazla bilgi edinin: SQL Server uygulama rolleri oluşturma'
title: SQL Server’da Uygulama Rolleri Oluşturma
ms.date: 03/30/2017
ms.assetid: 27442435-dfb2-4062-8c59-e2960833a638
ms.openlocfilehash: 20047d12a004230aebca1cf9d42b3893d36f3844
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786166"
---
# <a name="creating-application-roles-in-sql-server"></a>SQL Server’da Uygulama Rolleri Oluşturma

Uygulama rolleri, bir veritabanı rolü veya Kullanıcı yerine bir uygulamaya izin atamak için bir yol sağlar. Kullanıcılar veritabanına bağlanabilir, uygulama rolünü etkinleştirebilir ve uygulamaya verilen izinleri varsayabilir. Uygulama rolüne verilen izinler bağlantı süresine zorlanır.  
  
> [!IMPORTANT]
> Bir istemci uygulama, bağlantı dizesinde bir uygulama rolü adı ve parola sağlarsa uygulama rolleri etkinleştirilir. Parolanın istemci bilgisayarda depolanması gerektiğinden, iki katmanlı bir uygulamada güvenlik açığı vardır. Üç katmanlı bir uygulamada, uygulamanın kullanıcıları tarafından erişilebilmesi için parolayı kaydedebilirsiniz.  
  
## <a name="application-role-features"></a>Uygulama rolü özellikleri  

 Uygulama rolleri aşağıdaki özelliklere sahiptir:  
  
- Veritabanı rollerinin aksine, uygulama rollerinin hiçbir üye içermemesi gerekir.  
  
- Uygulama rolleri uygulama rolü adı ve sistem saklı yordamının parolasını sağladığı zaman etkinleştirilir `sp_setapprole` .  
  
- Parolanın istemci bilgisayarda depolanması ve çalışma zamanında sağlanması gerekir; uygulama rolü SQL Server içinden etkinleştirilemez.  
  
- Parola şifrelenmedi. Parametre parolası tek yönlü bir karma olarak depolanır.  
  
- Etkinleştirildikten sonra, uygulama rolü aracılığıyla alınan izinler bağlantı süresince etkin kalır.  
  
- Uygulama rolü role verilen izinleri devralır `public` .  
  
- `sysadmin`Sabit sunucu rolünün bir üyesi bir uygulama rolünü etkinleştirdiğinde, güvenlik bağlamı bağlantı süresince uygulama rolü ' ne geçer.  
  
- `guest`Uygulama rolüne sahip bir veritabanında bir hesap oluşturursanız, uygulama rolü veya onu çağıran oturum açma işlemleri için bir veritabanı kullanıcı hesabı oluşturmanız gerekmez. Uygulama rolleri yalnızca `guest` ikinci veritabanında bir hesap varsa, başka bir veritabanına doğrudan erişebilir  
  
- SYSTEM_USER gibi oturum açma adlarını döndüren yerleşik işlevler, uygulama rolünü çağıran oturum açmanın adını döndürür. Veritabanı kullanıcı adlarını döndüren yerleşik işlevler, uygulama rolünün adını döndürür.  
  
### <a name="the-principle-of-least-privilege"></a>En az ayrıcalık Ilkesi  

 Parolanın tehlikeye düşmesi durumunda uygulama rollerine yalnızca gerekli izinler verilmelidir. Rol izinleri, `public` uygulama rolü kullanılarak herhangi bir veritabanında iptal edilmelidir. `guest`Uygulama rolü çağıranlarının erişimine sahip olmasını istemediğiniz herhangi bir veritabanında hesabı devre dışı bırakın.  
  
### <a name="application-role-enhancements"></a>Uygulama rolü geliştirmeleri  

 Yürütme bağlamı, uygulama rolü etkinleştirildikten sonra özgün çağırana geri dönebilir ve bağlantı havuzunu devre dışı bırakma ihtiyacını ortadan kaldırır. `sp_setapprole`Yordam, çağıran ile ilgili bağlam bilgilerini içeren bir tanımlama bilgisi oluşturan yeni bir seçeneğe sahiptir. Yordamı çağırarak ve `sp_unsetapprole` tanımlama bilgisini geçirerek oturumu döndürebilirsiniz.  
  
## <a name="application-role-alternatives"></a>Uygulama rolü alternatifleri  

 Uygulama rolleri, olası bir güvenlik açığı sunan bir parolanın güvenliğine bağlıdır. Parolalar, uygulama koduna katıştırılmakta veya diske kaydedildiğinden gösterilebilir.  
  
 Aşağıdaki alternatifleri düşünmek isteyebilirsiniz.  
  
- EXECUTE AS WITH WITH using WITH WITH COOKIE yan tümceleri ile bağlam geçişini kullanın. Bir oturum açma ile eşlenmeyen bir veritabanında bir kullanıcı hesabı oluşturabilirsiniz. Daha sonra bu hesaba izinler atarsınız. FARKLı ÇALıŞTıR kullanımı, parola tabanlı değil, izin tabanlı olduğundan daha güvenlidir. Daha fazla bilgi için bkz. [SQL Server Içindeki kimliğe bürünme Ile Izinleri özelleştirme](customizing-permissions-with-impersonation-in-sql-server.md).  
  
- Saklı yordamları sertifikalarla imzalama ve yalnızca yordamları yürütmek için izin verme. Daha fazla bilgi için bkz. [SQL Server saklı yordamları imzalama](signing-stored-procedures-in-sql-server.md).  
  
## <a name="external-resources"></a>Dış Kaynaklar  

 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Uygulama rolleri](/sql/relational-databases/security/authentication-access/application-roles)|SQL Server 2008 ' de uygulama rollerinin nasıl oluşturulduğunu ve kullanılacağını açıklar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../securing-ado-net-applications.md)
- [SQL Server Güvenliğine Genel Bakış](overview-of-sql-server-security.md)
- [SQL Server'da Uygulama Güvenliği Senaryoları](application-security-scenarios-in-sql-server.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
