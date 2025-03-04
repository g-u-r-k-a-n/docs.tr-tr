---
title: Oracle ve ADO.NET
description: Oracle Çağrı arabirimini kullanarak Oracle veritabanına erişim sağlayan Oracle için .NET Framework Veri Sağlayıcısı özellikleri ve davranışları hakkında bilgi edinin.
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: 736b8dc5179a15ec219c1dae06b9ee6b5d6c3ef3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166631"
---
# <a name="oracle-and-adonet"></a>Oracle ve ADO.NET

> [!NOTE]
> İçindeki türler <xref:System.Data.OracleClient> kullanım dışıdır. Türler geçerli sürüm of.NET çerçevesinde desteklenmeye devam eder, ancak gelecekteki bir sürümde kaldırılacaktır. Microsoft, üçüncü taraf bir Oracle sağlayıcısı kullanmanızı önerir.  
  
 Bu bölümde, Oracle için .NET Framework Veri Sağlayıcısı özgü özellikler ve davranışlar açıklanmaktadır.  
  
 Oracle için .NET Framework Veri Sağlayıcısı Oracle Istemci yazılımı tarafından sağlanan Oracle Çağrı arabirimini (OCı) kullanarak bir Oracle veritabanına erişim sağlar. Veri sağlayıcısının işlevselliği, SQL Server, OLE DB ve ODBC için .NET Framework veri sağlayıcılarından benzer olacak şekilde tasarlanmıştır.  
  
 Oracle için .NET Framework Veri Sağlayıcısı kullanmak için, bir uygulamanın <xref:System.Data.OracleClient> ad alanına aşağıdaki şekilde başvurması gerekir:  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 Kodunuzu derlerken DLL 'ye bir başvuru de eklemeniz gerekir. Örneğin, bir C# programı derlerken komut satırlarınız şunları içermelidir:  
  
```console
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Sistem Gereksinimleri](system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 Oracle için .NET Framework Veri Sağlayıcısı kullanma gereksinimlerini açıklar ve bunu kullanırken bilinmesi gereken birçok sorunu açıklar.  
  
 [Oracle BFILE](oracle-bfiles.md)  
 <xref:System.Data.OracleClient.OracleBFile>Oracle BDOSYA veri türüyle çalışmak için kullanılan sınıfını açıklar.  
  
 [Oracle LOB](oracle-lobs.md)  
 <xref:System.Data.OracleClient.OracleLob>Oracle LOB veri türleriyle çalışmak için kullanılan sınıfını açıklar.  
  
 [Oracle REF CURSOR](oracle-ref-cursors.md)  
 Oracle REF CURSOR veri türü için desteği açıklar.  
  
 [OracleTypes](oracletypes.md)  
 Ve dahil Oracle veri türleriyle çalışmak için kullanabileceğiniz yapıları açıklar <xref:System.Data.OracleClient.OracleNumber> <xref:System.Data.OracleClient.OracleString> .  
  
 [Oracle Dizileri](oracle-sequences.md)  
 Sunucu tarafından oluşturulan anahtar Oracle sıra değerlerini alma desteğini açıklar.  
  
 [Oracle Veri Türü Eşlemeleri](oracle-data-type-mappings.md)  
 Oracle veri türlerini ve bunların eşlemelerini listeler <xref:System.Data.OracleClient.OracleDataReader> .  
  
 [Oracle Dağıtılmış İşlemleri](oracle-distributed-transactions.md)  
 <xref:System.Data.OracleClient.OracleConnection>Bir işlemin etkin olduğunu belirlerse, nesnenin var olan bir dağıtılmış işlemde otomatik olarak nasıl listeleneceğini açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  

 [ADO.NET Uygulamalarının Güvenliğini Sağlama](securing-ado-net-applications.md)  
 ADO.NET kullanılırken güvenli kodlama uygulamalarını açıklar.  
  
 [DataSets, DataTables ve DataViews](./dataset-datatable-dataview/index.md)  
 ' Nin nasıl oluşturulduğunu ve kullanılacağını açıklar, `DataSets` türü, `DataSets` `DataTables` ve `DataViews` .  
  
 [ADO.NET’te Veri Alma ve Değiştirme](retrieving-and-modifying-data.md)  
 ADO.NET içindeki verilerle nasıl çalışabileceğinizi açıklar.  
  
 [SQL Server ve ADO.NET](./sql/index.md)  
 SQL Server özgü özellikler ve işlevlerle nasıl çalışabileceğinizi açıklar.  
  
 [DbProviderFactories](dbproviderfactories.md)  
 ADO.NET ' de sağlayıcıya bağımsız kod yazmanıza izin veren genel sınıfları açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET](index.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
