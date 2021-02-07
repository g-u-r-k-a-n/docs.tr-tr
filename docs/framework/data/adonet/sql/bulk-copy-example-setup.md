---
description: 'Daha fazla bilgi edinin: toplu kopyalama örnek kurulumu'
title: Toplu Kopyalama Örnek Kurulumu
ms.date: 03/30/2017
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
ms.openlocfilehash: ae05dfa5f1ab19a3021b2b79ecd2bbee6a3ecae1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718557"
---
# <a name="bulk-copy-example-setup"></a><span data-ttu-id="625cd-103">Toplu Kopyalama Örnek Kurulumu</span><span class="sxs-lookup"><span data-stu-id="625cd-103">Bulk Copy Example Setup</span></span>

<span data-ttu-id="625cd-104"><xref:System.Data.SqlClient.SqlBulkCopy>Sınıfı yalnızca SQL Server tablolarına veri yazmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="625cd-104">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="625cd-105">Bu konuda gösterilen kod örnekleri, **AdventureWorks** SQL Server örnek veritabanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="625cd-105">The code samples shown in this topic use the SQL Server sample database, **AdventureWorks**.</span></span> <span data-ttu-id="625cd-106">Mevcut tabloların değiştirilmesini önlemek için, önce oluşturmanız gereken tablolara veri yazar.</span><span class="sxs-lookup"><span data-stu-id="625cd-106">To avoid altering the existing tables code samples write data to tables that you must create first.</span></span>  
  
 <span data-ttu-id="625cd-107">**BulkCopyDemoMatchingColumns** ve **Bulkcopydemofarklıentcolumns** tabloları, hem **AdventureWorks** **Production. Products** tablosuna dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="625cd-107">The **BulkCopyDemoMatchingColumns** and **BulkCopyDemoDifferentColumns** tables are both based on the **AdventureWorks** **Production.Products** table.</span></span> <span data-ttu-id="625cd-108">Bu tabloları kullanan kod örneklerinde, veriler **üretim. Products** tablosundan bu örnek tablolardan birine eklenir.</span><span class="sxs-lookup"><span data-stu-id="625cd-108">In code samples that use these tables, data is added from the **Production.Products** table to one of these sample tables.</span></span> <span data-ttu-id="625cd-109">Örnek, kaynak verilerden hedef tabloya sütunların nasıl eşlendiğini gösteren **Bulkcopydemofarklıya sütunları** tablosu kullanılır; Diğer çoğu örnek için **BulkCopyDemoMatchingColumns** kullanılır.</span><span class="sxs-lookup"><span data-stu-id="625cd-109">The **BulkCopyDemoDifferentColumns** table is used when the sample illustrates how to map columns from the source data to the destination table; **BulkCopyDemoMatchingColumns** is used for most other samples.</span></span>  
  
 <span data-ttu-id="625cd-110">Kod örneklerinin birkaçı, bir <xref:System.Data.SqlClient.SqlBulkCopy> sınıfın birden çok tabloya yazmak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="625cd-110">A few of the code samples demonstrate how to use one <xref:System.Data.SqlClient.SqlBulkCopy> class to write to multiple tables.</span></span> <span data-ttu-id="625cd-111">Bu örnekler için, **BulkCopyDemoOrderHeader** ve **BulkCopyDemoOrderDetail** tabloları hedef tabloları olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="625cd-111">For these samples, the **BulkCopyDemoOrderHeader** and **BulkCopyDemoOrderDetail** tables are used as the destination tables.</span></span> <span data-ttu-id="625cd-112">Bu tablolar, **AdventureWorks** içindeki **Sales. SalesOrderHeader** ve **Sales. SalesOrderDetail** tablolarını temel alır.</span><span class="sxs-lookup"><span data-stu-id="625cd-112">These tables are based on the **Sales.SalesOrderHeader** and **Sales.SalesOrderDetail** tables in **AdventureWorks**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="625cd-113">**SqlBulkCopy** kod örnekleri yalnızca **SqlBulkCopy** kullanma sözdizimini göstermek için verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="625cd-113">The **SqlBulkCopy** code samples are provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="625cd-114">Kaynak ve hedef tablolar aynı SQL Server örneğinde yer alıyorsa, verileri kopyalamak için Transact-SQL ifadesinin kullanılması daha kolay ve hızlıdır `INSERT … SELECT` .</span><span class="sxs-lookup"><span data-stu-id="625cd-114">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
## <a name="table-setup"></a><span data-ttu-id="625cd-115">Tablo kurulumu</span><span class="sxs-lookup"><span data-stu-id="625cd-115">Table Setup</span></span>  

 <span data-ttu-id="625cd-116">Kod örneklerinin düzgün çalışması için gereken tabloları oluşturmak için aşağıdaki Transact-SQL deyimlerini bir SQL Server veritabanında çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="625cd-116">To create the tables necessary for the code samples to run correctly, you must run the following Transact-SQL statements in a SQL Server database.</span></span>  
  
```sql
USE AdventureWorks  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoMatchingColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoMatchingColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoMatchingColumns]([ProductID] [int] IDENTITY(1,1) NOT NULL,  
    [Name] [nvarchar](50) NOT NULL,  
    [ProductNumber] [nvarchar](25) NOT NULL,  
 CONSTRAINT [PK_ProductID] PRIMARY KEY CLUSTERED  
(  
    [ProductID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoDifferentColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoDifferentColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoDifferentColumns]([ProdID] [int] IDENTITY(1,1) NOT NULL,  
    [ProdNum] [nvarchar](25) NOT NULL,  
    [ProdName] [nvarchar](50) NOT NULL,  
 CONSTRAINT [PK_ProdID] PRIMARY KEY CLUSTERED  
(  
    [ProdID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderHeader]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderHeader]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderHeader]([SalesOrderID] [int] IDENTITY(1,1) NOT NULL,  
    [OrderDate] [datetime] NOT NULL,  
    [AccountNumber] [nvarchar](15) NULL,  
 CONSTRAINT [PK_SalesOrderID] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderDetail]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderDetail]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderDetail]([SalesOrderID] [int] NOT NULL,  
    [SalesOrderDetailID] [int] NOT NULL,  
    [OrderQty] [smallint] NOT NULL,  
    [ProductID] [int] NOT NULL,  
    [UnitPrice] [money] NOT NULL,  
 CONSTRAINT [PK_LineNumber] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC,  
    [SalesOrderDetailID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
```  
  
## <a name="see-also"></a><span data-ttu-id="625cd-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="625cd-117">See also</span></span>

- [<span data-ttu-id="625cd-118">SQL Server’da Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="625cd-118">Bulk Copy Operations in SQL Server</span></span>](bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="625cd-119">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="625cd-119">ADO.NET Overview</span></span>](../ado-net-overview.md)
