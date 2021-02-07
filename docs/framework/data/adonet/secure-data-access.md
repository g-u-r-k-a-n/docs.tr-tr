---
description: 'Daha fazla bilgi edinin: güvenli veri erişimi'
title: Güvenli Veri Erişimi
ms.date: 03/30/2017
ms.assetid: 473ebd69-21a3-4627-b95e-4e04d035c56f
ms.openlocfilehash: 0f14f271dda9d07ba1efdea2328a5b3e30d14849
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718895"
---
# <a name="secure-data-access"></a>Güvenli Veri Erişimi

Güvenli ADO.NET kodu yazmak için, temel alınan veri deposunda veya veritabanında bulunan güvenlik mekanizmalarını anlamanız gerekir. Uygulamanızın içerebileceği diğer özelliklerin veya bileşenlerin güvenlik etkilerine de dikkat etmeniz gerekir.  
  
## <a name="authentication-authorization-and-permissions"></a>Kimlik doğrulama, yetkilendirme ve Izinler  

 Microsoft SQL Server bağlanırken, tümleşik güvenlik olarak da bilinen, bir kullanıcı KIMLIĞI ve parola geçirmek yerine geçerli etkin Windows kullanıcısının kimliğini kullanan Windows kimlik doğrulaması 'nı kullanabilirsiniz. Kullanıcı kimlik bilgileri bağlantı dizesinde gösterilmediğinden Windows kimlik doğrulamasının kullanılması önemle önerilir. SQL Server bağlanmak için Windows kimlik doğrulamasını kullanmıyorsanız, kullanarak çalışma zamanında bağlantı dizeleri oluşturmayı düşünün <xref:System.Data.SqlClient.SqlConnectionStringBuilder> .  
  
 Kimlik doğrulaması için kullanılan kimlik bilgilerinin, uygulama türüne bağlı olarak farklı şekilde işlenmesi gerekir. Örneğin, Windows Forms bir uygulamada, kullanıcıdan kimlik doğrulama bilgilerini sağlaması istenebilir veya kullanıcının Windows kimlik bilgileri kullanılabilir. Ancak, bir Web uygulaması genellikle, Kullanıcı tarafından değil uygulamanın kendisi tarafından sağlanan kimlik bilgilerini kullanarak verilere erişir.  
  
 Kullanıcıların kimliği doğrulandıktan sonra, eylemlerinin kapsamı kendilerine verilen izinlere göre değişir. Her zaman en az ayrıcalık ilkesini izleyin ve yalnızca kesinlikle gerekli izinleri verin.  
  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Bağlantı Bilgilerini Koruma](protecting-connection-information.md)|Bağlantı dizelerini şifrelemek için korumalı yapılandırma kullanma gibi, bağlantı bilgilerini korumak için en iyi güvenlik uygulamalarını ve tekniklerini açıklar.|  
|[Veri erişimi stratejileri için öneriler](/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))|Verilere erişmek ve veritabanı işlemlerini gerçekleştirmek için öneriler sağlar.|  
|[Bağlantı Dizesi Oluşturucular](connection-string-builders.md)|Çalışma zamanında Kullanıcı girişinden bağlantı dizeleri oluşturmayı açıklar.|  
|[SQL Server Güvenliğine Genel Bakış](./sql/overview-of-sql-server-security.md)|SQL Server güvenlik mimarisini açıklar.|  
  
## <a name="parameterized-commands-and-sql-injection"></a>Parametreli Komutlar ve SQL ekleme  

 Parametreli komutların kullanılması SQL ekleme saldırılarına karşı koruma sağlamaya yardımcı olur. Bu, bir saldırgan "bir komutu sunucuda güvenliği tehlikeye atacak bir SQL ifadesine" çıkarır ". Parametreli Komutlar bir dış kaynaktan alınan değerlerin Transact-SQL ifadesinin bir parçası değil yalnızca değer olarak geçirilmesini sağlayarak SQL ekleme saldırılarına karşı koruma sağlar. Sonuç olarak, bir değere eklenen Transact-SQL komutları veri kaynağında yürütülmez. Bunun yerine, yalnızca bir parametre değeri olarak değerlendirilir. Güvenlik avantajlarına ek olarak, Parametreli Komutlar bir Transact-SQL ifadesiyle veya bir saklı yordama geçirilen değerleri düzenlemek için kullanışlı bir yöntem sağlar.  
  
 Parametreli komutları kullanma hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[DataAdapter Parametreleri](dataadapter-parameters.md)|Parametrelerinin ile nasıl kullanılacağını açıklar `DataAdapter` .|  
|[Saklı Yordamlarla Verileri Değiştirme](modifying-data-with-stored-procedures.md)|Parametrelerin nasıl belirtileceğini ve bir dönüş değeri elde edileceğini açıklar.|  
|[SQL Server'da Saklı Yordam İzinlerini Yönetme](./sql/managing-permissions-with-stored-procedures-in-sql-server.md)|Veri erişimini kapsüllemek için SQL Server saklı yordamların nasıl kullanılacağını açıklar.|  
  
## <a name="script-exploits"></a>Betiği kötüye  

 Betik kullanımı, bir Web sayfasına eklenen kötü amaçlı karakterleri kullanan başka bir ekleme biçimidir. Tarayıcı, ekli karakterleri doğrulamaz ve sayfanın bir parçası olarak bunları işler.  
  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Betikte kötüye bakış](/previous-versions/aspnet/w1sw53ds(v=vs.100))|Komut dosyası ve SQL deyimlerinin kötüye kullanımı ile nasıl korunılacağını açıklar.|  
  
## <a name="probing-attacks"></a>Yoklama saldırıları  

 Saldırganlar, sisteminize bir saldırı bağlamak için genellikle sunucu, veritabanı veya tablonuzun adı gibi bir özel durum bilgilerini kullanır. Özel durumlar uygulamanız veya veri kaynağınız hakkında belirli bilgiler içerebildiğinden, yalnızca istemciye önemli bilgiler sunarak uygulamanızın ve veri kaynağınızın korunmasını daha iyi korumaya yardımcı olabilirsiniz.  
  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[.NET 'te özel durumları işleme ve atma](../../../standard/exceptions/index.md)|Try/catch/finally yapılandırılmış özel durum işlemenin temel biçimlerini açıklar.|  
|[Özel Durumlar için En İyi Yöntemler](../../../standard/exceptions/best-practices-for-exceptions.md)|Özel durumları işlemek için en iyi yöntemleri açıklar.|  
  
## <a name="protecting-microsoft-access-and-excel-data-sources"></a>Microsoft Access ve Excel veri kaynaklarını koruma  

 Microsoft Access ve Microsoft Excel, güvenlik gereksinimleri minimal veya varolmayan bir ADO.NET uygulaması için veri deposu olarak davranabilir. Güvenlik özellikleri Deterrence için geçerlidir, ancak bilinçli olmayan kullanıcılar tarafından daha fazla bilgi almak zorunda değildir. Access ve Excel için fiziksel veri dosyaları dosya sisteminde bulunur ve tüm kullanıcılar tarafından erişilebilir olmalıdır. Bu, dosyaların kolayca kopyalanabilmesi veya değiştirilemeyeceği için hırsızlık veya veri kaybına neden olabilecek saldırılara karşı savunmasız hale getirir. Sağlam güvenlik gerektiğinde, SQL Server veya fiziksel veri dosyalarının dosya sisteminden okunmayan başka bir sunucu tabanlı veritabanı kullanın.  
  
 Erişimi ve Excel verilerini koruma hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Access 2007 için güvenlik konuları ve Kılavuzu](/previous-versions/office/developer/office-2007/bb421308(v=office.12))|Access 2007 ' de, bu tür dosyaları şifrelemek, parolaları yönetmek, veritabanlarını yeni ACCDB ve ACCDE biçimlerine dönüştürmek ve diğer güvenlik seçeneklerini kullanmak için güvenlik tekniklerini açıklar.|  
|[Erişim 2010 güvenliğine giriş](https://support.office.com/article/Introduction-to-Access-2010-security-CAE6D764-0318-4622-955F-68D9F186D6CA)|Access 2010 tarafından sunulan güvenlik özelliklerine genel bir bakış sağlar.|  

## <a name="enterprise-services"></a>Kurumsal Hizmetler  

 COM+, Windows NT hesaplarına ve işlem/iş parçacığı kimliğe bürünmeye dayalı kendi güvenlik modelini içerir. <xref:System.EnterpriseServices>Ad alanı, .NET uygulamalarının sınıf aracılığıyla com+ güvenlik hizmetleriyle yönetilen kodu tümleştirmesine izin veren sarmalayıcılar sağlar <xref:System.EnterpriseServices.ServicedComponent> .  
  
 Daha fazla bilgi için aşağıdaki kaynağa bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Rol tabanlı güvenlik](/previous-versions/dotnet/netframework-1.1/s6y8k15h(v=vs.71))|Yönetilen kodun COM+ güvenlik hizmetleriyle nasıl tümleştirileceğini açıklar.|  
  
## <a name="interoperating-with-unmanaged-code"></a>Yönetilmeyen Kod ile Birlikte Çalışma  

 .NET Framework, COM bileşenleri, COM+ Hizmetleri, dış tür kitaplıkları ve birçok işletim sistemi hizmeti de dahil olmak üzere, yönetilmeyen kod ile etkileşim sağlar. Yönetilmeyen kodla çalışma, yönetilen kod için güvenlik çevre 'nın dışına geçiyor. Kodunuzun ve ona çağıran tüm kodlar, yönetilmeyen kod iznine sahip olmalıdır ( <xref:System.Security.Permissions.SecurityPermission> <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> belirtilen bayrağıyla birlikte). Yönetilmeyen kod, uygulamanızda istenmeyen güvenlik açıklarını ortaya çıkarabilir. Bu nedenle, kesinlikle gerekli olmadığı takdirde yönetilmeyen kodla birlikte çalışmaya engel olmanız gerekir.  
  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Yönetilmeyen Kod ile Birlikte Çalışma](../../interop/index.md)|COM bileşenlerinin .NET Framework ve COM 'a .NET Framework bileşenlerin nasıl sunulebileceği hakkında konuları içerir.|
|[Gelişmiş COM birlikte çalışabilirlik](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))|Birincil birlikte çalışma derlemeleri, iş parçacığı oluşturma ve özel sıralama gibi gelişmiş konuları içerir.|

## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](securing-ado-net-applications.md)
- [SQL Server Güvenliği](./sql/sql-server-security.md)
- [Veri erişimi stratejileri için öneriler](/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))
- [Bağlantı Bilgilerini Koruma](protecting-connection-information.md)
- [Bağlantı Dizesi Oluşturucular](connection-string-builders.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
