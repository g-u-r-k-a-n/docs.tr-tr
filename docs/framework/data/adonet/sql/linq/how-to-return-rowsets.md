---
description: ': Nasıl yapılır: satır kümelerini döndürme hakkında daha fazla bilgi edinin'
title: 'Nasıl yapılır: Satır Kümeleri Döndürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
ms.openlocfilehash: b799ce82542e6929f42485508b3a2c36cc42ee60
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723393"
---
# <a name="how-to-return-rowsets"></a><span data-ttu-id="58f3e-103">Nasıl yapılır: Satır Kümeleri Döndürme</span><span class="sxs-lookup"><span data-stu-id="58f3e-103">How to: Return Rowsets</span></span>

<span data-ttu-id="58f3e-104">Bu örnek, veritabanından bir satır kümesi döndürür ve sonucu filtrelemek için bir giriş parametresi içerir.</span><span class="sxs-lookup"><span data-stu-id="58f3e-104">This example returns a rowset from the database, and includes an input parameter to filter the result.</span></span>  
  
 <span data-ttu-id="58f3e-105">Bir satır kümesi döndüren bir saklı yordamı çalıştırdığınızda, saklı yordamdaki dönüşleri depolayan bir *sonuç* sınıfı kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="58f3e-105">When you execute a stored procedure that returns a rowset, you use a *result* class that stores the returns from the stored procedure.</span></span> <span data-ttu-id="58f3e-106">Daha fazla bilgi için bkz. [LINQ to SQL kaynak kodu çözümleme](analyzing-linq-to-sql-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="58f3e-106">For more information, see [Analyzing LINQ to SQL Source Code](analyzing-linq-to-sql-source-code.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="58f3e-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="58f3e-107">Example</span></span>  

 <span data-ttu-id="58f3e-108">Aşağıdaki örnek, müşteri satırları döndüren bir saklı yordamı temsil eder ve yalnızca müşteri şehri olarak "Londra" listesini içeren satırları döndürmek için bir giriş parametresi kullanır.</span><span class="sxs-lookup"><span data-stu-id="58f3e-108">The following example represents a stored procedure that returns rows of customers and uses an input parameter to return only those rows that list "London" as the customer city.</span></span> <span data-ttu-id="58f3e-109">Örnek, sıralanabilir bir `CustomersByCityResult` sınıfı varsayar.</span><span class="sxs-lookup"><span data-stu-id="58f3e-109">The example assumes an enumerable `CustomersByCityResult` class.</span></span>  
  
```sql  
CREATE PROCEDURE [dbo].[Customers By City]  
    (@param1 NVARCHAR(20))  
AS  
BEGIN  
    -- SET NOCOUNT ON added to prevent extra result sets from  
    -- interfering with SELECT statements.  
    SET NOCOUNT ON;  
    SELECT CustomerID, ContactName, CompanyName, City from Customers  
        as c where c.City=@param1  
END  
```  
  
 [!code-csharp[DLinqSprox#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#1)]
 [!code-vb[DLinqSprox#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="58f3e-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58f3e-110">See also</span></span>

- [<span data-ttu-id="58f3e-111">Saklı yordamlar</span><span class="sxs-lookup"><span data-stu-id="58f3e-111">Stored Procedures</span></span>](stored-procedures.md)
- [<span data-ttu-id="58f3e-112">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="58f3e-112">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
