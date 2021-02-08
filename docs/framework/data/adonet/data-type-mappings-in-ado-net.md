---
description: 'Hakkında daha fazla bilgi edinin: ADO.NET içinde veri türü eşlemeleri'
title: Veri Türü Eşlemeleri
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: c1829fdc2ebc053d1fd3a76e827a81e582572233
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786452"
---
# <a name="data-type-mappings-in-adonet"></a><span data-ttu-id="1beb6-103">ADO.NET’te Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="1beb6-103">Data Type Mappings in ADO.NET</span></span>

<span data-ttu-id="1beb6-104">.NET Framework, çalışma zamanında türlerin nasıl bildirildiği, kullanıldığı ve yönetildiğini tanımlayan ortak tür sistemine dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="1beb6-104">The .NET Framework is based on the common type system, which defines how types are declared, used, and managed in the runtime.</span></span> <span data-ttu-id="1beb6-105">Her ikisi de temel türden türetilen değer türleri ve başvuru türlerinden oluşur <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="1beb6-105">It consists of both value types and reference types, which all derive from the <xref:System.Object> base type.</span></span> <span data-ttu-id="1beb6-106">Bir veri kaynağıyla çalışırken, açıkça belirtilmemişse veri türü veri sağlayıcısından algılanır.</span><span class="sxs-lookup"><span data-stu-id="1beb6-106">When working with a data source, the data type is inferred from the data provider if it is not explicitly specified.</span></span> <span data-ttu-id="1beb6-107">Örneğin, bir <xref:System.Data.DataSet> nesne belirli bir veri kaynağından bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="1beb6-107">For example, a <xref:System.Data.DataSet> object is independent of any specific data source.</span></span> <span data-ttu-id="1beb6-108">İçindeki veriler bir `DataSet` veri kaynağından alınır ve değişiklikler bir kullanılarak veri kaynağına geri kaydedilir `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="1beb6-108">Data in a `DataSet` is retrieved from a data source, and changes are persisted back to the data source by using a `DataAdapter`.</span></span> <span data-ttu-id="1beb6-109">Yani `DataAdapter` <xref:System.Data.DataTable> , bir `DataSet` veri kaynağından değerleri olan bir ile bir doldurduğunda, içindeki sütunların sonuç veri türleri, `DataTable` veri kaynağına bağlanmak için kullanılan .NET Framework veri sağlayıcısına özgü türler yerine .NET Framework türlerdir.</span><span class="sxs-lookup"><span data-stu-id="1beb6-109">This means that when a `DataAdapter` fills a <xref:System.Data.DataTable> in a `DataSet` with values from a data source, the resulting data types of the columns in the `DataTable` are .NET Framework types, instead of types specific to the .NET Framework data provider that is used to connect to the data source.</span></span>  
  
 <span data-ttu-id="1beb6-110">Benzer şekilde, bir `DataReader` veri kaynağından bir değer döndürdüğünde, sonuçta elde edilen değer .NET Framework türüne sahip yerel bir değişkende depolanır.</span><span class="sxs-lookup"><span data-stu-id="1beb6-110">Likewise, when a `DataReader` returns a value from a data source, the resulting value is stored in a local variable that has a .NET Framework type.</span></span> <span data-ttu-id="1beb6-111">Ve yöntemlerinin her ikisi için `Fill` `DataAdapter` `Get` `DataReader` , .NET Framework türü .NET Framework veri sağlayıcısından döndürülen değerden çıkarsanamıyor.</span><span class="sxs-lookup"><span data-stu-id="1beb6-111">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the .NET Framework type is inferred from the value returned from the .NET Framework data provider.</span></span>  
  
 <span data-ttu-id="1beb6-112">Gösterilen veri türüne güvenmek yerine, `DataReader` döndürülmekte olan değerin belirli bir türünü bildiğiniz zaman türü belirlenmiş erişimci yöntemlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1beb6-112">Instead of relying on the inferred data type, you can use the typed accessor methods of the `DataReader` when you know the specific type of the value being returned.</span></span> <span data-ttu-id="1beb6-113">Türü belirlenmiş erişimci yöntemleri, bir değeri belirli bir .NET Framework türüne döndürerek daha iyi performans sağlar ve bu da ek tür dönüştürme gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1beb6-113">Typed accessor methods give you better performance by returning a value as a specific .NET Framework type, which eliminates the need for additional type conversion.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1beb6-114">.NET Framework veri sağlayıcısı veri türleri için null değerler tarafından temsil edilir `DBNull.Value` .</span><span class="sxs-lookup"><span data-stu-id="1beb6-114">Null values for .NET Framework data provider data types are represented by `DBNull.Value`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1beb6-115">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1beb6-115">In This Section</span></span>  

 [<span data-ttu-id="1beb6-116">SQL Server Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="1beb6-116">SQL Server Data Type Mappings</span></span>](sql-server-data-type-mappings.md)  
 <span data-ttu-id="1beb6-117">İçin gösterilen veri türü eşlemelerini ve veri erişimcisi yöntemlerini listeler <xref:System.Data.SqlClient> .</span><span class="sxs-lookup"><span data-stu-id="1beb6-117">Lists inferred data type mappings and data accessor methods for <xref:System.Data.SqlClient>.</span></span>  
  
 [<span data-ttu-id="1beb6-118">OLE DB Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="1beb6-118">OLE DB Data Type Mappings</span></span>](ole-db-data-type-mappings.md)  
 <span data-ttu-id="1beb6-119">İçin gösterilen veri türü eşlemelerini ve veri erişimcisi yöntemlerini listeler <xref:System.Data.OleDb> .</span><span class="sxs-lookup"><span data-stu-id="1beb6-119">Lists inferred data type mappings and data accessor methods for <xref:System.Data.OleDb>.</span></span>  
  
 [<span data-ttu-id="1beb6-120">ODBC Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="1beb6-120">ODBC Data Type Mappings</span></span>](odbc-data-type-mappings.md)  
 <span data-ttu-id="1beb6-121">İçin gösterilen veri türü eşlemelerini ve veri erişimcisi yöntemlerini listeler <xref:System.Data.Odbc> .</span><span class="sxs-lookup"><span data-stu-id="1beb6-121">Lists inferred data type mappings and data accessor methods for <xref:System.Data.Odbc>.</span></span>  
  
 [<span data-ttu-id="1beb6-122">Oracle Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="1beb6-122">Oracle Data Type Mappings</span></span>](oracle-data-type-mappings.md)  
 <span data-ttu-id="1beb6-123">İçin gösterilen veri türü eşlemelerini ve veri erişimcisi yöntemlerini listeler <xref:System.Data.OracleClient> .</span><span class="sxs-lookup"><span data-stu-id="1beb6-123">Lists inferred data type mappings and data accessor methods for <xref:System.Data.OracleClient>.</span></span>  
  
 [<span data-ttu-id="1beb6-124">Kayan Noktalı Sayılar</span><span class="sxs-lookup"><span data-stu-id="1beb6-124">Floating-Point Numbers</span></span>](floating-point-numbers.md)  
 <span data-ttu-id="1beb6-125">Kayan nokta numaralarıyla çalışırken geliştiricilerin sıkça karşılaştığı sorunları açıklar.</span><span class="sxs-lookup"><span data-stu-id="1beb6-125">Describes issues that developers frequently encounter when working with floating-point numbers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1beb6-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1beb6-126">See also</span></span>

- [<span data-ttu-id="1beb6-127">SQL Server Veri Türleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1beb6-127">SQL Server Data Types and ADO.NET</span></span>](./sql/sql-server-data-types.md)
- [<span data-ttu-id="1beb6-128">Parametreleri ve Parametre Veri Türlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1beb6-128">Configuring Parameters and Parameter Data Types</span></span>](configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="1beb6-129">Veritabanı Şema Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="1beb6-129">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)
- [<span data-ttu-id="1beb6-130">Ortak tür sistemi</span><span class="sxs-lookup"><span data-stu-id="1beb6-130">Common Type System</span></span>](../../../standard/base-types/common-type-system.md)
- <span data-ttu-id="1beb6-131">[Türleri dönüştürme](/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="1beb6-131">[Converting Types](/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))</span></span>
- [<span data-ttu-id="1beb6-132">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1beb6-132">ADO.NET Overview</span></span>](ado-net-overview.md)
