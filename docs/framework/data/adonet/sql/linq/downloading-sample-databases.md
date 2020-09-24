---
title: ADO.NET kod örnekleri için örnek SQL Server veritabanlarını alın
description: ADO.NET belgelerindeki kod örneklerinde kullanılan örnek SQL Server veritabanlarını ve ayrıca SQL Server ve yönetim araçlarını indirin
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: f7c0d1eb0089a6bfabc92e1deecf563c3e59cc6a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156062"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a><span data-ttu-id="a35b8-103">ADO.NET kod örnekleri için örnek veritabanlarını al</span><span class="sxs-lookup"><span data-stu-id="a35b8-103">Get the sample databases for ADO.NET code samples</span></span>

<span data-ttu-id="a35b8-104">Belgelerde birçok örnek ve İzlenecek yol, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] örnek SQL Server veritabanları ve SQL Server Express kullanır.</span><span class="sxs-lookup"><span data-stu-id="a35b8-104">A number of examples and walkthroughs in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation use sample SQL Server databases and SQL Server Express.</span></span> <span data-ttu-id="a35b8-105">Bu ürünleri Microsoft 'tan ücretsiz olarak indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a35b8-105">You can download these products free of charge from Microsoft.</span></span>

## <a name="get-the-northwind-sample-database-for-sql-server"></a><span data-ttu-id="a35b8-106">SQL Server için Northwind örnek veritabanını alın</span><span class="sxs-lookup"><span data-stu-id="a35b8-106">Get the Northwind sample database for SQL Server</span></span>

<span data-ttu-id="a35b8-107">`instnwnd.sql`SQL Server Için Northwind örnek veritabanı oluşturmak ve yüklemek üzere aşağıdaki GitHub deposundan betiği indirin:</span><span class="sxs-lookup"><span data-stu-id="a35b8-107">Download the script `instnwnd.sql` from the following GitHub repository to create and load the Northwind sample database for SQL Server:</span></span>

[<span data-ttu-id="a35b8-108">Microsoft SQL Server için Northwind ve pubs örnek veritabanları</span><span class="sxs-lookup"><span data-stu-id="a35b8-108">Northwind and pubs sample databases for Microsoft SQL Server</span></span>](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

<span data-ttu-id="a35b8-109">Northwind veritabanını kullanabilmeniz `instnwnd.sql` için, [SQL Server Management Studio](#get_ssms) veya benzer bir aracı kullanarak veritabanını bir SQL Server örneğine yeniden oluşturmak üzere indirilen betik dosyasını çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a35b8-109">Before you can use the Northwind database, you have to run the downloaded `instnwnd.sql` script file to recreate the database on an instance of SQL Server by using [SQL Server Management Studio](#get_ssms) or a similar tool.</span></span> <span data-ttu-id="a35b8-110">Depodaki Benioku dosyasındaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a35b8-110">Follow the instructions in the Readme file in the repository.</span></span>

> [!TIP]
> <span data-ttu-id="a35b8-111">Microsoft Access için Northwind veritabanına bakıyorsanız, bkz. [Microsoft Access Için Northwind örnek veritabanını Install](#northwind_access).</span><span class="sxs-lookup"><span data-stu-id="a35b8-111">If you're looking for the Northwind database for Microsoft Access, see [Install the Northwind sample database for Microsoft Access](#northwind_access).</span></span>

## <a name="get-the-northwind-sample-database-for-microsoft-access"></a><a name="northwind_access"></a> <span data-ttu-id="a35b8-112">Microsoft Access için Northwind örnek veritabanını alın</span><span class="sxs-lookup"><span data-stu-id="a35b8-112">Get the Northwind sample database for Microsoft Access</span></span>

<span data-ttu-id="a35b8-113">Microsoft Access için Northwind örnek veritabanı Microsoft Indirme Merkezi ' nde bulunmamaktadır.</span><span class="sxs-lookup"><span data-stu-id="a35b8-113">The Northwind sample database for Microsoft Access is not available on the Microsoft Download Center.</span></span> <span data-ttu-id="a35b8-114">Northwind 'yi doğrudan erişim içinden yüklemek için aşağıdaki işlemleri yapın:</span><span class="sxs-lookup"><span data-stu-id="a35b8-114">To install Northwind directly from within Access, do the following things:</span></span>

1. <span data-ttu-id="a35b8-115">Açık erişim.</span><span class="sxs-lookup"><span data-stu-id="a35b8-115">Open Access.</span></span>

1. <span data-ttu-id="a35b8-116">**Çevrimiçi şablon ara** kutusuna **Northwind** girin ve ardından **ENTER**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="a35b8-116">Enter **Northwind** in the **Search for Online Templates** box, and then select **Enter**.</span></span>

1. <span data-ttu-id="a35b8-117">Sonuçlar ekranında **Northwind**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="a35b8-117">On the results screen, select **Northwind**.</span></span> <span data-ttu-id="a35b8-118">Northwind veritabanının açıklamasıyla birlikte yeni bir pencere açılır.</span><span class="sxs-lookup"><span data-stu-id="a35b8-118">A new window opens with a description of the Northwind database.</span></span>

1. <span data-ttu-id="a35b8-119">Yeni pencerede, **dosya adı** metin kutusunda, Northwind veritabanının kopyası için bir dosya adı belirtin.</span><span class="sxs-lookup"><span data-stu-id="a35b8-119">In the new window, in the **File Name** text box, provide a filename for your copy of the Northwind database.</span></span>

1. <span data-ttu-id="a35b8-120">**Oluştur**’u seçin.</span><span class="sxs-lookup"><span data-stu-id="a35b8-120">Select **Create**.</span></span> <span data-ttu-id="a35b8-121">Access, Northwind veritabanını indirir ve dosyayı hazırlar.</span><span class="sxs-lookup"><span data-stu-id="a35b8-121">Access downloads the Northwind database and prepares the file.</span></span>

1. <span data-ttu-id="a35b8-122">Bu işlem tamamlandığında, veritabanı bir karşılama ekranı ile açılır.</span><span class="sxs-lookup"><span data-stu-id="a35b8-122">When this process is complete, the database opens with a Welcome screen.</span></span>

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="a35b8-123">SQL Server için AdventureWorks örnek veritabanını al</span><span class="sxs-lookup"><span data-stu-id="a35b8-123">Get the AdventureWorks sample database for SQL Server</span></span>

<span data-ttu-id="a35b8-124">Aşağıdaki GitHub deposundan SQL Server için AdventureWorks örnek veritabanını indirin:</span><span class="sxs-lookup"><span data-stu-id="a35b8-124">Download the AdventureWorks sample database for SQL Server from the following GitHub repository:</span></span>

[<span data-ttu-id="a35b8-125">AdventureWorks örnek veritabanları</span><span class="sxs-lookup"><span data-stu-id="a35b8-125">AdventureWorks sample databases</span></span>](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

<span data-ttu-id="a35b8-126">Veritabanı yedekleme ( \* . bak) dosyalarından birini indirdikten sonra, SQL Server Management Studio (SSMS) kullanarak SQL Server bir örneğine yedeklemeyi geri yükleyin.</span><span class="sxs-lookup"><span data-stu-id="a35b8-126">After you download one of the database backup (\*.bak) files, restore the backup to an instance of SQL Server by using SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="a35b8-127">Bkz. [Get SQL Server Management Studio](#get_ssms).</span><span class="sxs-lookup"><span data-stu-id="a35b8-127">See [Get SQL Server Management Studio](#get_ssms).</span></span>

## <a name="get-sql-server-management-studio"></a><a name="get_ssms"></a> <span data-ttu-id="a35b8-128">SQL Server Management Studio al</span><span class="sxs-lookup"><span data-stu-id="a35b8-128">Get SQL Server Management Studio</span></span>

<span data-ttu-id="a35b8-129">İndirdiğiniz bir veritabanını görüntülemek veya değiştirmek istiyorsanız, SQL Server Management Studio (SSMS) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a35b8-129">If you want to view or modify a database that you've downloaded, you can use SQL Server Management Studio (SSMS).</span></span> <span data-ttu-id="a35b8-130">SSMS 'yi aşağıdaki sayfadan indirin:</span><span class="sxs-lookup"><span data-stu-id="a35b8-130">Download SSMS from the following page:</span></span>

[<span data-ttu-id="a35b8-131">SQL Server Management Studio’yu (SSMS) İndirme</span><span class="sxs-lookup"><span data-stu-id="a35b8-131">Download SQL Server Management Studio (SSMS)</span></span>](/sql/ssms/download-sql-server-management-studio-ssms)

<span data-ttu-id="a35b8-132">Ayrıca, Visual Studio tümleşik geliştirme ortamında (IDE) veritabanlarını görüntüleyebilir ve yönetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a35b8-132">You can also view and manage databases in the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="a35b8-133">[Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)'da **SQL Server Nesne Gezgini**veritabanına bağlanın veya **Sunucu Gezgini**veritabanında veritabanına bir veri bağlantısı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a35b8-133">In [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019), connect to the database from **SQL Server Object Explorer**, or create a Data Connection to the database in **Server Explorer**.</span></span> <span data-ttu-id="a35b8-134">**Görünüm** menüsünden bu gezgin bölmelerini açın.</span><span class="sxs-lookup"><span data-stu-id="a35b8-134">Open these explorer panes from the **View** menu.</span></span>

## <a name="get-sql-server-express"></a><a name="get_sql"></a> <span data-ttu-id="a35b8-135">SQL Server Express al</span><span class="sxs-lookup"><span data-stu-id="a35b8-135">Get SQL Server Express</span></span>

<span data-ttu-id="a35b8-136">SQL Server Express, uygulamalarla yeniden dağıtacağınız SQL Server ücretsiz, giriş düzeyi bir sürümdür.</span><span class="sxs-lookup"><span data-stu-id="a35b8-136">SQL Server Express is a free, entry-level edition of SQL Server that you can redistribute with applications.</span></span> <span data-ttu-id="a35b8-137">Aşağıdaki sayfadan SQL Server Express indirin:</span><span class="sxs-lookup"><span data-stu-id="a35b8-137">Download SQL Server Express from the following page:</span></span>
  
[<span data-ttu-id="a35b8-138">SQL Server Express sürümü</span><span class="sxs-lookup"><span data-stu-id="a35b8-138">SQL Server Express Edition</span></span>](https://www.microsoft.com/sql-server/sql-server-editions-express)

<span data-ttu-id="a35b8-139">[Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)kullanıyorsanız, SQL Server Express LocalDB, Visual Studio 'Nun ücretsiz topluluk sürümüne, Ayrıca profesyonel ve daha yüksek sürümlere dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a35b8-139">If you're using [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019), SQL Server Express LocalDB is included in the free Community edition of Visual Studio, as well as the Professional and higher editions.</span></span>  

## <a name="see-also"></a><span data-ttu-id="a35b8-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a35b8-140">See also</span></span>

- [<span data-ttu-id="a35b8-141">Başlarken</span><span class="sxs-lookup"><span data-stu-id="a35b8-141">Getting Started</span></span>](getting-started.md)
