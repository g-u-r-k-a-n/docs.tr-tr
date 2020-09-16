---
title: Dosyalardan ve diğer kaynaklardan veri yükleme
description: API kullanarak ML.NET 'ye işleme ve eğitimle ilgili verileri yüklemeyi öğrenin. Veriler dosyalar, veritabanları, JSON, XML veya bellek içi koleksiyonlar halinde depolanır.
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: 5097632ca777403e6073d28b707bdbe653cda8ac
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545031"
---
# <a name="load-data-from-files-and-other-sources"></a><span data-ttu-id="ddb35-104">Dosyalardan ve diğer kaynaklardan veri yükleme</span><span class="sxs-lookup"><span data-stu-id="ddb35-104">Load data from files and other sources</span></span>

<span data-ttu-id="ddb35-105">API kullanarak ML.NET 'ye işleme ve eğitimle ilgili verileri yüklemeyi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="ddb35-105">Learn how to load data for processing and training into ML.NET using the API.</span></span> <span data-ttu-id="ddb35-106">Veriler başlangıçta dosyalar veya veritabanları, JSON, XML veya bellek içi Koleksiyonlar gibi diğer veri kaynaklarında depolanır.</span><span class="sxs-lookup"><span data-stu-id="ddb35-106">The data is originally stored in files or other data sources such as databases, JSON, XML or in-memory collections.</span></span>

<span data-ttu-id="ddb35-107">Model Oluşturucu kullanıyorsanız bkz. [model Oluşturucu 'da eğitim verilerini yükleme](load-data-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="ddb35-107">If you're using Model Builder, see [Load training data into Model Builder](load-data-model-builder.md).</span></span>

## <a name="create-the-data-model"></a><span data-ttu-id="ddb35-108">Veri modelini oluşturma</span><span class="sxs-lookup"><span data-stu-id="ddb35-108">Create the data model</span></span>

<span data-ttu-id="ddb35-109">ML.NET, sınıflar aracılığıyla veri modelleri tanımlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ddb35-109">ML.NET enables you to define data models via classes.</span></span> <span data-ttu-id="ddb35-110">Örneğin, aşağıdaki giriş verileri verildiğinde:</span><span class="sxs-lookup"><span data-stu-id="ddb35-110">For example, given the following input data:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

<span data-ttu-id="ddb35-111">Aşağıdaki kod parçacığını temsil eden bir veri modeli oluşturun:</span><span class="sxs-lookup"><span data-stu-id="ddb35-111">Create a data model that represents the snippet below:</span></span>

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }

    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

### <a name="annotating-the-data-model-with-column-attributes"></a><span data-ttu-id="ddb35-112">Sütun öznitelikleriyle veri modeline açıklama ekleme</span><span class="sxs-lookup"><span data-stu-id="ddb35-112">Annotating the data model with column attributes</span></span>

<span data-ttu-id="ddb35-113">Öznitelikler, veri modeli ve veri kaynağı hakkında ML.NET daha fazla bilgi verir.</span><span class="sxs-lookup"><span data-stu-id="ddb35-113">Attributes give ML.NET more information about the data model and the data source.</span></span>

<span data-ttu-id="ddb35-114">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute)Öznitelik, özelliklerinin sütun dizinlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ddb35-114">The [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute specifies your properties' column indices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ddb35-115">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) yalnızca bir dosyadan veri yüklenirken gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ddb35-115">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) is only required when loading data from a file.</span></span>

<span data-ttu-id="ddb35-116">Sütunları şu şekilde yükle:</span><span class="sxs-lookup"><span data-stu-id="ddb35-116">Load columns as:</span></span>

- <span data-ttu-id="ddb35-117">Sınıfında ve gibi ayrı sütunlar `Size` `CurrentPrices` `HousingData` .</span><span class="sxs-lookup"><span data-stu-id="ddb35-117">Individual columns like `Size` and `CurrentPrices` in the `HousingData` class.</span></span>
- <span data-ttu-id="ddb35-118">Sınıf gibi bir vektör biçiminde tek seferde birden çok sütun `HistoricalPrices` `HousingData` .</span><span class="sxs-lookup"><span data-stu-id="ddb35-118">Multiple columns at a time in the form of a vector like `HistoricalPrices` in the `HousingData` class.</span></span>

<span data-ttu-id="ddb35-119">Vektör özelliği varsa, [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) özniteliğini veri modelinizdeki özelliğe uygulayın.</span><span class="sxs-lookup"><span data-stu-id="ddb35-119">If you have a vector property, apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to the property in your data model.</span></span> <span data-ttu-id="ddb35-120">Vektördeki tüm öğelerin aynı türde olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ddb35-120">It's important to note that all of the elements in the vector need to be the same type.</span></span> <span data-ttu-id="ddb35-121">Sütunların ayrılmış tutulması, özellik mühendisliğinin kolaylığını ve esnekliğini sağlar, ancak çok fazla sayıda sütun için, bireysel sütunlarda çalışan eğitim hızında bir etkiye neden olur.</span><span class="sxs-lookup"><span data-stu-id="ddb35-121">Keeping the columns separated allows for ease and flexibility of feature engineering, but for a very large number of columns, operating on the individual columns causes an impact on training speed.</span></span>

<span data-ttu-id="ddb35-122">ML.NET, sütun adlarıyla çalışır.</span><span class="sxs-lookup"><span data-stu-id="ddb35-122">ML.NET Operates through column names.</span></span> <span data-ttu-id="ddb35-123">Bir sütunun adını özellik adı dışında bir şekilde değiştirmek istiyorsanız, [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ddb35-123">If you want to change the name of a column to something other than the property name, use the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span> <span data-ttu-id="ddb35-124">Bellek içi nesneler oluştururken, hala özellik adını kullanarak nesneler oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="ddb35-124">When creating in-memory objects, you still create objects using the property name.</span></span> <span data-ttu-id="ddb35-125">Ancak, veri işleme ve makine öğrenimi modelleri oluşturma için, ML.NET geçersiz kılar ve özelliği özniteliğinde belirtilen değerle başvurur [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) .</span><span class="sxs-lookup"><span data-stu-id="ddb35-125">However, for data processing and building machine learning models, ML.NET overrides and references the property with the value provided in the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span>

## <a name="load-data-from-a-single-file"></a><span data-ttu-id="ddb35-126">Tek bir dosyadaki verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="ddb35-126">Load data from a single file</span></span>

<span data-ttu-id="ddb35-127">Bir dosyadan veri yüklemek için [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) yöntemini, yüklenecek verilerin veri modeliyle birlikte kullanın.</span><span class="sxs-lookup"><span data-stu-id="ddb35-127">To load data from a file use the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method along with the data model for the data to be loaded.</span></span> <span data-ttu-id="ddb35-128">`separatorChar`Parametre varsayılan olarak sekmeyle ayrılmış olduğundan, bunu veri dosyanız için gereken şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ddb35-128">Since `separatorChar` parameter is tab-delimited by default, change it for your data file as needed.</span></span> <span data-ttu-id="ddb35-129">Dosyanızın bir üstbilgisi varsa, `hasHeader` parametresini `true` dosyadaki ilk satırı yoksayacak şekilde ayarlayın ve ikinci satırdan verileri yüklemeye başlayın.</span><span class="sxs-lookup"><span data-stu-id="ddb35-129">If your file has a header, set the `hasHeader` parameter to `true` to ignore the first line in the file and begin to load data from the second line.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a><span data-ttu-id="ddb35-130">Birden çok dosyadan veri yükleme</span><span class="sxs-lookup"><span data-stu-id="ddb35-130">Load data from multiple files</span></span>

<span data-ttu-id="ddb35-131">Verilerinizin birden çok dosyada depolandığından, veri şeması aynı olduğu sürece, ML.NET aynı dizinde veya birden çok dizinde bulunan birden çok dosyadan veri yüklemenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="ddb35-131">In the event that your data is stored in multiple files, as long as the data schema is the same, ML.NET allows you to load data from multiple files that are either in the same directory or multiple directories.</span></span>

### <a name="load-from-files-in-a-single-directory"></a><span data-ttu-id="ddb35-132">Tek bir dizindeki dosyalardan yükleme</span><span class="sxs-lookup"><span data-stu-id="ddb35-132">Load from files in a single directory</span></span>

<span data-ttu-id="ddb35-133">Tüm veri dosyalarınız aynı dizinde olduğunda, yönteminde joker karakterler kullanın [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) .</span><span class="sxs-lookup"><span data-stu-id="ddb35-133">When all of your data files are in the same directory, use wildcards in the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a><span data-ttu-id="ddb35-134">Birden çok dizindeki dosyalardan yükleme</span><span class="sxs-lookup"><span data-stu-id="ddb35-134">Load from files in multiple directories</span></span>

<span data-ttu-id="ddb35-135">Birden çok dizindeki verileri yüklemek için [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) yöntemini kullanarak bir oluşturun [`TextLoader`](xref:Microsoft.ML.Data.TextLoader) .</span><span class="sxs-lookup"><span data-stu-id="ddb35-135">To load data from multiple directories, use the [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) method to create a [`TextLoader`](xref:Microsoft.ML.Data.TextLoader).</span></span> <span data-ttu-id="ddb35-136">Ardından, yöntemini kullanın [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) ve tek dosya yollarını belirtin (joker karakterler kullanılamaz).</span><span class="sxs-lookup"><span data-stu-id="ddb35-136">Then, use the [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) method and specify the individual file paths (wildcards can't be used).</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a><span data-ttu-id="ddb35-137">İlişkisel veritabanından veri yükleme</span><span class="sxs-lookup"><span data-stu-id="ddb35-137">Load data from a relational database</span></span>

<span data-ttu-id="ddb35-138">ML.NET [`System.Data`](xref:System.Data) , SQL Server, Azure SQL veritabanı, Oracle, SQLite, PostgreSQL, Progress, IBM DB2 ve çok daha fazlasını içeren, tarafından desteklenen çeşitli ilişkisel veritabanlarından veri yüklenmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="ddb35-138">ML.NET supports loading data from a variety of relational databases supported by [`System.Data`](xref:System.Data) that include SQL Server, Azure SQL Database, Oracle, SQLite, PostgreSQL, Progress, IBM DB2, and many more.</span></span>

> [!NOTE]
> <span data-ttu-id="ddb35-139">Kullanmak için `DatabaseLoader` [System. Data. SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) NuGet paketine başvurun.</span><span class="sxs-lookup"><span data-stu-id="ddb35-139">To use `DatabaseLoader`, reference the [System.Data.SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) NuGet package.</span></span>

<span data-ttu-id="ddb35-140">Adlı bir tablo ve aşağıdaki şemaya sahip bir veritabanı verildi `House` :</span><span class="sxs-lookup"><span data-stu-id="ddb35-140">Given a database with a table named `House` and the following schema:</span></span>

```sql
CREATE TABLE [House] (
    [HouseId] INT NOT NULL IDENTITY,
    [Size] INT NOT NULL,
    [NumBed] INT NOT NULL,
    [Price] REAL NOT NULL
    CONSTRAINT [PK_House] PRIMARY KEY ([HouseId])
);
```

<span data-ttu-id="ddb35-141">Veriler, gibi bir sınıfa göre modellenebilir `HouseData` .</span><span class="sxs-lookup"><span data-stu-id="ddb35-141">The data can be modeled by a class like `HouseData`.</span></span>

```csharp
public class HouseData
{
    public float Size { get; set; }

    public float NumBed { get; set; }

    public float Price { get; set; }
}
```

<span data-ttu-id="ddb35-142">Ardından, uygulamanızın içinde bir oluşturun `DatabaseLoader` .</span><span class="sxs-lookup"><span data-stu-id="ddb35-142">Then, inside of your application, create a `DatabaseLoader`.</span></span>

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

<span data-ttu-id="ddb35-143">Bağlantı dizenizi ve veritabanında yürütülecek SQL komutunu ve bir örnek oluşturmayı tanımlayın `DatabaseSource` .</span><span class="sxs-lookup"><span data-stu-id="ddb35-143">Define your connection string as well as the SQL command to be executed on the database and create a `DatabaseSource` instance.</span></span> <span data-ttu-id="ddb35-144">Bu örnek, bir LocalDB SQL Server veritabanını bir dosya yolu ile kullanır.</span><span class="sxs-lookup"><span data-stu-id="ddb35-144">This sample uses a LocalDB SQL Server database with a file path.</span></span> <span data-ttu-id="ddb35-145">Ancak DatabaseLoader, şirket içi ve buluttaki veritabanları için geçerli olan diğer bağlantı dizelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="ddb35-145">However, DatabaseLoader supports any other valid connection string for databases on-premises and in the cloud.</span></span>

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size, CAST(NumBed as REAL) as NumBed, Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance, connectionString, sqlCommand);
```

<span data-ttu-id="ddb35-146">Türünde olmayan sayısal verilerin [`Real`](xref:System.Data.SqlDbType) dönüştürülecek olması gerekiyor [`Real`](xref:System.Data.SqlDbType) .</span><span class="sxs-lookup"><span data-stu-id="ddb35-146">Numerical data that is not of type [`Real`](xref:System.Data.SqlDbType) has to be converted to [`Real`](xref:System.Data.SqlDbType).</span></span> <span data-ttu-id="ddb35-147">[`Real`](xref:System.Data.SqlDbType)Tür tek duyarlıklı kayan nokta değeri veya [`Single`](xref:System.Single) ml.net algoritmaları tarafından beklenen giriş türü olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="ddb35-147">The [`Real`](xref:System.Data.SqlDbType) type is represented as a single-precision floating-point value or [`Single`](xref:System.Single), the input type expected by ML.NET algorithms.</span></span> <span data-ttu-id="ddb35-148">Bu örnekte, `NumBed` sütunu veritabanındaki bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="ddb35-148">In this sample, the `NumBed` column is an integer in the database.</span></span> <span data-ttu-id="ddb35-149">`CAST`Yerleşik işlevi kullanılarak, öğesine dönüştürülür [`Real`](xref:System.Data.SqlDbType) .</span><span class="sxs-lookup"><span data-stu-id="ddb35-149">Using the `CAST` built-in function, it's converted to [`Real`](xref:System.Data.SqlDbType).</span></span> <span data-ttu-id="ddb35-150">Özelliği zaten olduğu için, `Price` özelliği [`Real`](xref:System.Data.SqlDbType) olduğu gibi yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="ddb35-150">Because the `Price` property is already of type [`Real`](xref:System.Data.SqlDbType) it is loaded as is.</span></span>

<span data-ttu-id="ddb35-151">' `Load` A veri yüklemek için yöntemini kullanın [`IDataView`](xref:Microsoft.ML.IDataView) .</span><span class="sxs-lookup"><span data-stu-id="ddb35-151">Use the `Load` method to load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

```csharp
IDataView data = loader.Load(dbSource);
```

## <a name="load-data-from-other-sources"></a><span data-ttu-id="ddb35-152">Diğer kaynaklardan veri yükleme</span><span class="sxs-lookup"><span data-stu-id="ddb35-152">Load data from other sources</span></span>

<span data-ttu-id="ddb35-153">ML.NET, dosyalarda depolanan verileri yüklemeye ek olarak, dahil edilen ancak bunlarla sınırlı olmayan kaynaklardan veri yüklemeyi destekler:</span><span class="sxs-lookup"><span data-stu-id="ddb35-153">In addition to loading data stored in files, ML.NET supports loading data from sources that include but are not limited to:</span></span>

- <span data-ttu-id="ddb35-154">Bellek içi Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="ddb35-154">In-memory collections</span></span>
- <span data-ttu-id="ddb35-155">JSON/XML</span><span class="sxs-lookup"><span data-stu-id="ddb35-155">JSON/XML</span></span>

<span data-ttu-id="ddb35-156">Akış kaynaklarıyla çalışırken ML.NET, girişin bellek içi koleksiyon biçiminde olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="ddb35-156">Note that when working with streaming sources, ML.NET expects input to be in the form of an in-memory collection.</span></span> <span data-ttu-id="ddb35-157">Bu nedenle, JSON/XML gibi kaynaklarla çalışırken, verileri bellek içi bir koleksiyonda biçimlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ddb35-157">Therefore, when working with sources like JSON/XML, make sure to format the data into an in-memory collection.</span></span>

<span data-ttu-id="ddb35-158">Aşağıdaki bellek içi koleksiyon verildiğinde:</span><span class="sxs-lookup"><span data-stu-id="ddb35-158">Given the following in-memory collection:</span></span>

```csharp
HousingData[] inMemoryCollection = new HousingData[]
{
    new HousingData
    {
        Size =700f,
        HistoricalPrices = new float[]
        {
            100000f, 3000000f, 250000f
        },
        CurrentPrice = 500000f
    },
    new HousingData
    {
        Size =1000f,
        HistoricalPrices = new float[]
        {
            600000f, 400000f, 650000f
        },
        CurrentPrice=700000f
    }
};
```

<span data-ttu-id="ddb35-159">Bellek içi toplamayı, yöntemiyle bir öğesine yükleyin [`IDataView`](xref:Microsoft.ML.IDataView) [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) :</span><span class="sxs-lookup"><span data-stu-id="ddb35-159">Load the in-memory collection into an [`IDataView`](xref:Microsoft.ML.IDataView) with the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ddb35-160">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) , ' [`IEnumerable`](xref:System.Collections.IEnumerable) den yüklendiği varsayılmaktadır, iş parçacığı güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="ddb35-160">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) assumes that the [`IEnumerable`](xref:System.Collections.IEnumerable) it loads from is thread-safe.</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```

## <a name="next-steps"></a><span data-ttu-id="ddb35-161">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="ddb35-161">Next steps</span></span>

- <span data-ttu-id="ddb35-162">Verileri temizlemek veya başka bir şekilde işlemek için bkz. [model oluşturmak için veri hazırlama](prepare-data-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="ddb35-162">To clean or otherwise process data, see [Prepare data for building a model](prepare-data-ml-net.md).</span></span>
- <span data-ttu-id="ddb35-163">Model oluşturmaya hazırsanız, bkz. [modeli eğitme ve değerlendirme](train-machine-learning-model-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="ddb35-163">When you're ready to build a model, see [Train and evaluate a model](train-machine-learning-model-ml-net.md).</span></span>
