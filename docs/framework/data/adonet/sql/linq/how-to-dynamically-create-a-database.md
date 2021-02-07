---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: dinamik olarak veritabanı oluşturma'
title: 'Nasıl yapılır: Dinamik Olarak Veritabanı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
ms.openlocfilehash: b9addce6befc63f91358d6ecae57e40d6123b200
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738981"
---
# <a name="how-to-dynamically-create-a-database"></a><span data-ttu-id="e78a5-103">Nasıl yapılır: Dinamik Olarak Veritabanı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e78a5-103">How to: Dynamically Create a Database</span></span>

<span data-ttu-id="e78a5-104">LINQ to SQL, bir nesne modeli ilişkisel veritabanıyla eşlenir.</span><span class="sxs-lookup"><span data-stu-id="e78a5-104">In LINQ to SQL, an object model is mapped to a relational database.</span></span> <span data-ttu-id="e78a5-105">Eşleme, ilişkisel veritabanının yapısını betimleyen öznitelik tabanlı eşleme veya bir dış eşleme dosyası kullanılarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e78a5-105">Mapping is enabled by using attribute-based mapping or an external mapping file to describe the structure of the relational database.</span></span> <span data-ttu-id="e78a5-106">Her iki senaryoda da, yöntemini kullanarak veritabanının yeni bir örneğini oluşturabileceğiniz ilişkisel veritabanı hakkında yeterli bilgi vardır <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e78a5-106">In both scenarios, there is enough information about the relational database that you can create a new instance of the database using the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="e78a5-107"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>Yöntemi, veritabanının bir çoğaltmasını yalnızca nesne modelinde kodlanan bilgilerin kapsamına oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e78a5-107">The <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method creates a replica of the database only to the extent of the information encoded in the object model.</span></span> <span data-ttu-id="e78a5-108">Nesne modelinizdeki dosya ve öznitelikleri eşleme, var olan bir veritabanının yapısıyla ilgili her şeyi kodlayamayabilir.</span><span class="sxs-lookup"><span data-stu-id="e78a5-108">Mapping files and attributes from your object model might not encode everything about the structure of an existing database.</span></span> <span data-ttu-id="e78a5-109">Eşleme bilgileri Kullanıcı tanımlı işlevlerin, saklı yordamların, tetikleyicilerin veya denetim kısıtlamalarının içeriğini temsil etmez.</span><span class="sxs-lookup"><span data-stu-id="e78a5-109">Mapping information does not represent the contents of user-defined functions, stored procedures, triggers, or check constraints.</span></span> <span data-ttu-id="e78a5-110">Bu davranış çeşitli veritabanları için yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="e78a5-110">This behavior is sufficient for a variety of databases.</span></span>  
  
 <span data-ttu-id="e78a5-111"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>Yöntemi, özellikle de Microsoft SQL Server 2008 gibi bilinen bir veri sağlayıcısı varsa dilediğiniz sayıda senaryoda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e78a5-111">You can use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method in any number of scenarios, especially if a known data provider like Microsoft SQL Server 2008 is available.</span></span> <span data-ttu-id="e78a5-112">Tipik senaryolar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e78a5-112">Typical scenarios include the following:</span></span>  
  
- <span data-ttu-id="e78a5-113">Kendisini bir müşteri sistemine otomatik olarak yükleyen bir uygulama derleniyor.</span><span class="sxs-lookup"><span data-stu-id="e78a5-113">You are building an application that automatically installs itself on a customer system.</span></span>  
  
- <span data-ttu-id="e78a5-114">Çevrimdışı durumunu kaydetmek için yerel bir veritabanına ihtiyacı olan bir istemci uygulaması derleniyor.</span><span class="sxs-lookup"><span data-stu-id="e78a5-114">You are building a client application that needs a local database to save its offline state.</span></span>  
  
 <span data-ttu-id="e78a5-115">Ayrıca, <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> bağlantı dizeniz temelinde bir. mdf dosyası veya bir katalog adı kullanarak SQL Server yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e78a5-115">You can also use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method with SQL Server by using an .mdf file or a catalog name, depending on your connection string.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="e78a5-116">oluşturulacak veritabanını ve veritabanının oluşturulacağı sunucuyu tanımlamak için bağlantı dizesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e78a5-116">uses the connection string to define the database to be created and on which server the database is to be created.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e78a5-117">Mümkün olduğunda, bağlantı dizesinde parolaların gerekli olmaması için veritabanına bağlanmak üzere Windows tümleşik güvenliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="e78a5-117">Whenever possible, use Windows Integrated Security to connect to the database so that passwords are not required in the connection string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e78a5-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="e78a5-118">Example</span></span>  

 <span data-ttu-id="e78a5-119">Aşağıdaki kod, MyDVD 'Ler. mdf adlı yeni bir veritabanının nasıl oluşturulacağı hakkında bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="e78a5-119">The following code provides an example of how to create a new database named MyDVDs.mdf.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="e78a5-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="e78a5-120">Example</span></span>  

 <span data-ttu-id="e78a5-121">Aşağıdaki işlemleri yaparak bir veritabanı oluşturmak için nesne modelini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e78a5-121">You can use the object model to create a database by doing the following:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="e78a5-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="e78a5-122">Example</span></span>  

 <span data-ttu-id="e78a5-123">Kendisini bir müşteri sistemine otomatik olarak yükleyen bir uygulama oluştururken, veritabanının zaten var olup olmadığını ve yeni bir tane oluşturmadan önce onu bırakıp bırakmaya bakın.</span><span class="sxs-lookup"><span data-stu-id="e78a5-123">When building an application that automatically installs itself on a  customer system, see if the database already exists and drop it before creating a new one.</span></span> <span data-ttu-id="e78a5-124"><xref:System.Data.Linq.DataContext>Sınıfı, <xref:System.Data.Linq.DataContext.DatabaseExists%2A> <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> Bu işlemle ilgili size yardımcı olmak için ve yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e78a5-124">The <xref:System.Data.Linq.DataContext> class provides the <xref:System.Data.Linq.DataContext.DatabaseExists%2A> and <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> methods to help you with this process.</span></span>  
  
 <span data-ttu-id="e78a5-125">Aşağıdaki örnek bu yaklaşımı uygulamak için bu yöntemlerin kullanılabileceği bir yolu göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="e78a5-125">The following example shows one way these methods can be used to implement this approach:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="e78a5-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e78a5-126">See also</span></span>

- [<span data-ttu-id="e78a5-127">Öznitelik Tabanlı Eşleme</span><span class="sxs-lookup"><span data-stu-id="e78a5-127">Attribute-Based Mapping</span></span>](attribute-based-mapping.md)
- [<span data-ttu-id="e78a5-128">Dış Eşleme</span><span class="sxs-lookup"><span data-stu-id="e78a5-128">External Mapping</span></span>](external-mapping.md)
- [<span data-ttu-id="e78a5-129">SQL-CLR Tür Eşlemesi</span><span class="sxs-lookup"><span data-stu-id="e78a5-129">SQL-CLR Type Mapping</span></span>](sql-clr-type-mapping.md)
- [<span data-ttu-id="e78a5-130">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="e78a5-130">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="e78a5-131">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="e78a5-131">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
