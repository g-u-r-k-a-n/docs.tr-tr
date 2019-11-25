---
title: Model oluşturmaya yönelik verileri hazırlama
description: Ek işleme veya model oluşturmaya yönelik verileri işlemek ve hazırlamak için ML.NET içindeki dönüştürmeleri nasıl kullanacağınızı öğrenin.
author: luisquintanilla
ms.author: luquinta
ms.date: 09/11/2019
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: e9bfad4724b353b0f3bfc615a40f1d72b80a2cd4
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976974"
---
# <a name="prepare-data-for-building-a-model"></a><span data-ttu-id="22292-103">Model oluşturmaya yönelik verileri hazırlama</span><span class="sxs-lookup"><span data-stu-id="22292-103">Prepare data for building a model</span></span>

<span data-ttu-id="22292-104">ML.NET kullanarak ek işleme veya bir model oluşturmaya yönelik verileri hazırlama hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="22292-104">Learn how to use ML.NET to prepare data for additional processing or building a model.</span></span>

<span data-ttu-id="22292-105">Veriler genellikle temiz ve seyrek yapılır.</span><span class="sxs-lookup"><span data-stu-id="22292-105">Data is often unclean and sparse.</span></span> <span data-ttu-id="22292-106">ML.NET Machine Learning algoritmaları, giriş veya özelliklerin tek bir sayısal vektörde olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="22292-106">ML.NET machine learning algorithms expect input or features to be in a single numerical vector.</span></span> <span data-ttu-id="22292-107">Benzer şekilde, tahmin edilecek değer (etiket), özellikle de kategorik veriler, kodlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="22292-107">Similarly, the value to predict (label), especially when it's categorical data, has to be encoded.</span></span> <span data-ttu-id="22292-108">Bu nedenle, veri hazırlama amaçlarından biri, verileri ML.NET algoritmaları tarafından beklenen biçimde almak.</span><span class="sxs-lookup"><span data-stu-id="22292-108">Therefore one of the goals of data preparation is to get the data into the format expected by ML.NET algorithms.</span></span>

## <a name="filter-data"></a><span data-ttu-id="22292-109">Verileri Filtrele</span><span class="sxs-lookup"><span data-stu-id="22292-109">Filter data</span></span>

<span data-ttu-id="22292-110">Bazen, bir veri kümesindeki tüm veriler Analize uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="22292-110">Sometimes, not all data in a dataset is relevant for analysis.</span></span> <span data-ttu-id="22292-111">İlgisiz verileri kaldırma yaklaşımı filtreleniyor.</span><span class="sxs-lookup"><span data-stu-id="22292-111">An approach to remove irrelevant data is filtering.</span></span> <span data-ttu-id="22292-112">[`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) , tüm verileri içeren bir [`IDataView`](xref:Microsoft.ML.IDataView) alıp yalnızca ilgilendiğiniz veri noktalarını içeren bir [ıdataview](xref:Microsoft.ML.IDataView) döndüren bir filtre işlemleri kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="22292-112">The [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) contains a set of filter operations that take in an [`IDataView`](xref:Microsoft.ML.IDataView) containing all of the data and return an [IDataView](xref:Microsoft.ML.IDataView) containing only the data points of interest.</span></span> <span data-ttu-id="22292-113">Filtre işlemleri [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog)gibi bir [`IEstimator`](xref:Microsoft.ML.IEstimator%601) veya [`ITransformer`](xref:Microsoft.ML.ITransformer) olmadığından, [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) veya [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) veri hazırlama işlem hattının parçası olarak dahil edilemez olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="22292-113">It's important to note that because filter operations are not an [`IEstimator`](xref:Microsoft.ML.IEstimator%601) or [`ITransformer`](xref:Microsoft.ML.ITransformer) like those in the [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), they cannot be included as part of an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) or [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) data preparation pipeline.</span></span>

<span data-ttu-id="22292-114">Bir [`IDataView`](xref:Microsoft.ML.IDataView)yüklenen aşağıdaki giriş verilerini kullanma:</span><span class="sxs-lookup"><span data-stu-id="22292-114">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms=1f,
        Price=100000f
    },
    new HomeData
    {
        NumberOfBedrooms=2f,
        Price=300000f
    },
    new HomeData
    {
        NumberOfBedrooms=6f,
        Price=600000f
    }
};
```

<span data-ttu-id="22292-115">Bir sütunun değerine göre verileri filtrelemek için [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="22292-115">To filter data based on the value of a column, use the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) method.</span></span>

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

<span data-ttu-id="22292-116">Yukarıdaki örnek, 200000 ile 1000000 arasında bir fiyata sahip veri kümesindeki satırları alır.</span><span class="sxs-lookup"><span data-stu-id="22292-116">The sample above takes rows in the dataset with a price between 200000 and 1000000.</span></span> <span data-ttu-id="22292-117">Bu filtreyi uygulamanın sonucu yalnızca verilerdeki son iki satırı döndürür ve fiyatı 100000 olduğundan ve belirtilen Aralık arasında olmadığından ilk satırı dışlayacak.</span><span class="sxs-lookup"><span data-stu-id="22292-117">The result of applying this filter would return only the last two rows in the data and exclude the first row because its price is 100000 and not between the specified range.</span></span>

## <a name="replace-missing-values"></a><span data-ttu-id="22292-118">Eksik değerleri Değiştir</span><span class="sxs-lookup"><span data-stu-id="22292-118">Replace missing values</span></span>

<span data-ttu-id="22292-119">Eksik değerler veri kümelerinde yaygın bir oluşumlardır.</span><span class="sxs-lookup"><span data-stu-id="22292-119">Missing values are a common occurrence in datasets.</span></span> <span data-ttu-id="22292-120">Eksik değerlerle ilgilenmeye yönelik bir yaklaşım, veri içindeki ortalama değer gibi herhangi bir veya başka bir anlamlı değer varsa, bunları verilen türün varsayılan değeriyle değiştirecektir.</span><span class="sxs-lookup"><span data-stu-id="22292-120">One approach to dealing with missing values is to replace them with the default value for the given type if any or another meaningful value such as the mean value in the data.</span></span>

<span data-ttu-id="22292-121">Bir [`IDataView`](xref:Microsoft.ML.IDataView)yüklenen aşağıdaki giriş verilerini kullanma:</span><span class="sxs-lookup"><span data-stu-id="22292-121">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms=1f,
        Price=100000f
    },
    new HomeData
    {
        NumberOfBedrooms=2f,
        Price=300000f
    },
    new HomeData
    {
        NumberOfBedrooms=6f,
        Price=float.NaN
    }
};
```

<span data-ttu-id="22292-122">Listemizdeki son öğenin `Price`için eksik bir değere sahip olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="22292-122">Notice that the last element in our list has a missing value for `Price`.</span></span> <span data-ttu-id="22292-123">`Price` sütununda eksik değerleri değiştirmek için [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) metodunu kullanarak eksik değeri girin.</span><span class="sxs-lookup"><span data-stu-id="22292-123">To replace the missing values in the `Price` column, use the [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) method to fill in that missing value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="22292-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) yalnızca sayısal verilerle birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="22292-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues*) only works with numerical data.</span></span>

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

<span data-ttu-id="22292-125">ML.NET çeşitli [değiştirme modlarını](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode)destekler.</span><span class="sxs-lookup"><span data-stu-id="22292-125">ML.NET supports various [replacement modes](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span></span> <span data-ttu-id="22292-126">Yukarıdaki örnek, bu sütunun ortalama değeriyle eksik değeri dolduracak `Mean` değiştirme modunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="22292-126">The sample above uses the `Mean` replacement mode which will fill in the missing value with that column's average value.</span></span> <span data-ttu-id="22292-127">Değiştirme işleminin sonucu, 100.000 ve 300.000 ortalaması olduğundan, 200.000 ile verilerdeki son öğenin `Price` özelliğini doldurur.</span><span class="sxs-lookup"><span data-stu-id="22292-127">The replacement 's result fills in the `Price` property for the last element in our data with 200,000 since it's the average of 100,000 and 300,000.</span></span>

## <a name="use-normalizers"></a><span data-ttu-id="22292-128">Normalleyiciler kullanma</span><span class="sxs-lookup"><span data-stu-id="22292-128">Use normalizers</span></span>

<span data-ttu-id="22292-129">[Normalleştirme](https://en.wikipedia.org/wiki/Feature_scaling) , algoritmaların daha hızlı yakınsamasını sağlayan, aynı ölçekte olmayan özellikleri standartlaştırmak için kullanılan bir veri ön işleme tekniğidir.</span><span class="sxs-lookup"><span data-stu-id="22292-129">[Normalization](https://en.wikipedia.org/wiki/Feature_scaling) is a data pre-processing technique used to standardize features that are not on the same scale which helps algorithms converge faster.</span></span> <span data-ttu-id="22292-130">Örneğin, yaş ve gelir gibi değerlerin aralıkları genellikle, 0-100 ve gelirin genellikle sıfır-binlerce aralığında olması bakımından yaş açısından önemli ölçüde farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="22292-130">For example, the ranges for values like age and income vary significantly with age generally being in the range of 0-100 and income generally being in the range of zero to thousands.</span></span> <span data-ttu-id="22292-131">Daha ayrıntılı bir liste ve normalleştirme dönüştürmelerini açıklaması için [dönüşümler sayfasını](../resources/transforms.md) ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="22292-131">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of normalization transforms.</span></span>

### <a name="min-max-normalization"></a><span data-ttu-id="22292-132">Minimum-en fazla normalleştirme</span><span class="sxs-lookup"><span data-stu-id="22292-132">Min-Max normalization</span></span>

<span data-ttu-id="22292-133">Bir [`IDataView`](xref:Microsoft.ML.IDataView)yüklenen aşağıdaki giriş verilerini kullanma:</span><span class="sxs-lookup"><span data-stu-id="22292-133">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms = 2f,
        Price = 200000f
    },
    new HomeData
    {
        NumberOfBedrooms = 1f,
        Price = 100000f
    }
};
```

<span data-ttu-id="22292-134">Normalleştirme, tek bir sayısal değere ve vektörlerine sahip sütunlara uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="22292-134">Normalization can be applied to columns with single numerical values as well as vectors.</span></span> <span data-ttu-id="22292-135">`Price` sütunundaki verileri, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) yöntemiyle Min-Max normalleştirmesini kullanarak normalleştirin.</span><span class="sxs-lookup"><span data-stu-id="22292-135">Normalize the data in the `Price` column using min-max normalization with the [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) method.</span></span>

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

<span data-ttu-id="22292-136">`[200000,100000]` orijinal fiyat değerleri, 0-1 aralığında çıkış değerleri üreten `MinMax` normalleştirme formülü kullanılarak `[ 1, 0.5 ]` dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="22292-136">The original price values `[200000,100000]` are converted to `[ 1, 0.5 ]` using the `MinMax` normalization formula which generates output values in the range of 0-1.</span></span>

### <a name="binning"></a><span data-ttu-id="22292-137">Gruplama</span><span class="sxs-lookup"><span data-stu-id="22292-137">Binning</span></span>

<span data-ttu-id="22292-138">[Binme](https://en.wikipedia.org/wiki/Data_binning) , sürekli değerleri girişin ayrı bir gösterimine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="22292-138">[Binning](https://en.wikipedia.org/wiki/Data_binning) converts continuous values into a discrete representation of the input.</span></span> <span data-ttu-id="22292-139">Örneğin, özelliklerden birinin yaş olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="22292-139">For example, suppose one of your features is age.</span></span> <span data-ttu-id="22292-140">Bini gerçek yaş değerini kullanmak yerine, bu değer için aralıklar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="22292-140">Instead of using the actual age value,  binning creates ranges for that value.</span></span> <span data-ttu-id="22292-141">0-18 bir bin olabilir, diğeri 19-35 olabilir ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="22292-141">0-18 could be one bin, another could be 19-35 and so on.</span></span>

<span data-ttu-id="22292-142">Bir [`IDataView`](xref:Microsoft.ML.IDataView)yüklenen aşağıdaki giriş verilerini kullanma:</span><span class="sxs-lookup"><span data-stu-id="22292-142">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms=1f,
        Price=100000f
    },
    new HomeData
    {
        NumberOfBedrooms=2f,
        Price=300000f
    },
    new HomeData
    {
        NumberOfBedrooms=6f,
        Price=600000f
    }
};
```

<span data-ttu-id="22292-143">[`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning*) yöntemi kullanarak verileri depo gözleri halinde normalleştirin.</span><span class="sxs-lookup"><span data-stu-id="22292-143">Normalize the data into bins using the [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning*) method.</span></span> <span data-ttu-id="22292-144">`maximumBinCount` parametresi, verilerinizi sınıflandırmak için gereken bölme sayısını belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="22292-144">The `maximumBinCount` parameter enables you to specify the number of bins needed to classify your data.</span></span> <span data-ttu-id="22292-145">Bu örnekte, veriler iki bölme içine alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="22292-145">In this example, data will be put into two bins.</span></span>

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

<span data-ttu-id="22292-146">Binme sonucu `[0,200000,Infinity]`bin sınırlarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="22292-146">The result of binning creates bin bounds of `[0,200000,Infinity]`.</span></span> <span data-ttu-id="22292-147">Bu nedenle, ilk gözlem 0-200000 arasında ve diğerleri 200000 ' den büyük ancak sonsuz ' dan az olduğu için ortaya çıkan depo gözleri `[0,1,1]`.</span><span class="sxs-lookup"><span data-stu-id="22292-147">Therefore the resulting bins are `[0,1,1]` because the first observation is between 0-200000 and the others are greater than 200000 but less than infinity.</span></span>

## <a name="work-with-categorical-data"></a><span data-ttu-id="22292-148">Kategorik verilerle çalışma</span><span class="sxs-lookup"><span data-stu-id="22292-148">Work with categorical data</span></span>

<span data-ttu-id="22292-149">Sayısal olmayan kategorik verilerin bir makine öğrenimi modeli oluşturmak için kullanılmadan önce bir sayıya dönüştürülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="22292-149">Non-numeric categorical data needs to be converted to a number before being used to build a machine learning model.</span></span>

<span data-ttu-id="22292-150">Bir [`IDataView`](xref:Microsoft.ML.IDataView)yüklenen aşağıdaki giriş verilerini kullanma:</span><span class="sxs-lookup"><span data-stu-id="22292-150">Using the following input data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

```csharp
CarData[] cars = new CarData[]
{
    new CarData
    {
        Color="Red",
        VehicleType="SUV"
    },
    new CarData
    {
        Color="Blue",
        VehicleType="Sedan"
    },
    new CarData
    {
        Color="Black",
        VehicleType="SUV"
    }
};
```

<span data-ttu-id="22292-151">Kategorik `VehicleType` özelliği [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*) yöntemi kullanılarak bir sayıya dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="22292-151">The categorical `VehicleType` property can be converted into a number using the [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding*) method.</span></span>

```csharp
// Define categorical transform estimator
var categoricalEstimator = mlContext.Transforms.Categorical.OneHotEncoding("VehicleType");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer categoricalTransformer = categoricalEstimator.Fit(data);

// Transform Data
IDataView transformedData = categoricalTransformer.Transform(data);
```

<span data-ttu-id="22292-152">Elde edilen dönüştürme `VehicleType` metin değerini bir sayıya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="22292-152">The resulting transform converts the text value of `VehicleType` to a number.</span></span> <span data-ttu-id="22292-153">`VehicleType` sütunundaki girdiler, dönüşüm uygulandığında aşağıdakiler olur:</span><span class="sxs-lookup"><span data-stu-id="22292-153">The entries in the `VehicleType` column become the following when the transform is applied:</span></span>

```text
[
    1, // SUV
    2, // Sedan
    1 // SUV
]
```

## <a name="work-with-text-data"></a><span data-ttu-id="22292-154">Metin verileriyle çalışma</span><span class="sxs-lookup"><span data-stu-id="22292-154">Work with text data</span></span>

<span data-ttu-id="22292-155">Bir makine öğrenimi modeli oluşturmak için, metin verilerinin kullanılmadan önce sayılara dönüştürülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="22292-155">Text data needs to be transformed into numbers before using it to build a machine learning model.</span></span> <span data-ttu-id="22292-156">Daha ayrıntılı bir liste ve metin dönüştürmelerini açıklaması için [dönüşümler sayfasını](../resources/transforms.md) ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="22292-156">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of text transforms.</span></span>

<span data-ttu-id="22292-157">Bir [`IDataView`](xref:Microsoft.ML.IDataView)yüklenmiş olan veriler gibi verileri kullanma:</span><span class="sxs-lookup"><span data-stu-id="22292-157">Using data like the data below that has been loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

```csharp
ReviewData[] reviews = new ReviewData[]
{
    new ReviewData
    {
        Description="This is a good product",
        Rating=4.7f
    },
    new ReviewData
    {
        Description="This is a bad product",
        Rating=2.3f
    }
};
```

<span data-ttu-id="22292-158">Metni sayısal bir vektör gösterimine dönüştürmek için gereken en düşük adım [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) yöntemi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="22292-158">The minimum step to convert text to a numerical vector representation is to use the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) method.</span></span> <span data-ttu-id="22292-159">[`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) dönüşümünü kullanarak, giriş metin sütununa bir dizi dönüştürme uygulandıktan sonra, LP normalleştirilmiş kelime ve karakter Ngram sayısını temsil eden sayısal bir vektör elde edilir.</span><span class="sxs-lookup"><span data-stu-id="22292-159">By using the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) transform, a series of transformations is applied to the input text column resulting in a numerical vector representing the lp-normalized word and character ngrams.</span></span>

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

<span data-ttu-id="22292-160">Elde edilen dönüşüm, `Description` sütunundaki metin değerlerini aşağıdaki çıkışa benzer bir sayısal vector öğesine dönüştürür:</span><span class="sxs-lookup"><span data-stu-id="22292-160">The resulting transform would convert the text values in the `Description` column to a numerical vector that looks similar to the output below:</span></span>

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

<span data-ttu-id="22292-161">Paraziti kaldırmak için karmaşık metin işleme adımlarını bir [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) birleştirin ve gereken işlem kaynakları miktarını gerektiği gibi azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22292-161">Combine complex text processing steps into an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) to remove noise and potentially reduce the amount of required processing resources as needed.</span></span>

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

<span data-ttu-id="22292-162">`textEstimator`, [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) yöntemi tarafından gerçekleştirilen işlemlerin bir alt kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="22292-162">`textEstimator` contains a subset of operations performed by the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText*) method.</span></span> <span data-ttu-id="22292-163">Daha karmaşık bir işlem hattının avantajı, verilere uygulanan dönüşümlere göre denetim ve görünürlük sağlar.</span><span class="sxs-lookup"><span data-stu-id="22292-163">The benefit of a more complex pipeline is control and visibility over the transformations applied to the data.</span></span>

<span data-ttu-id="22292-164">Örnek olarak ilk girdiyi kullanarak aşağıda, `textEstimator`tarafından tanımlanan dönüştürme adımları tarafından oluşturulan sonuçların ayrıntılı bir açıklaması verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="22292-164">Using the first entry as an example, the following is a detailed description of the results produced by the transformation steps defined by `textEstimator`:</span></span>

<span data-ttu-id="22292-165">**Özgün metin: Bu iyi bir üründür**</span><span class="sxs-lookup"><span data-stu-id="22292-165">**Original Text: This is a good product**</span></span>

|<span data-ttu-id="22292-166">Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="22292-166">Transform</span></span> | <span data-ttu-id="22292-167">Açıklama</span><span class="sxs-lookup"><span data-stu-id="22292-167">Description</span></span> | <span data-ttu-id="22292-168">Sonuç</span><span class="sxs-lookup"><span data-stu-id="22292-168">Result</span></span>
|--|--|--|
|<span data-ttu-id="22292-169">1. NormalizeText</span><span class="sxs-lookup"><span data-stu-id="22292-169">1. NormalizeText</span></span> | <span data-ttu-id="22292-170">Varsayılan olarak tüm harfleri küçük harfe dönüştürür</span><span class="sxs-lookup"><span data-stu-id="22292-170">Converts all letters to lowercase by default</span></span> | <span data-ttu-id="22292-171">Bu iyi bir üründür</span><span class="sxs-lookup"><span data-stu-id="22292-171">this is a good product</span></span>
|<span data-ttu-id="22292-172">2. TokenizeWords</span><span class="sxs-lookup"><span data-stu-id="22292-172">2. TokenizeWords</span></span> | <span data-ttu-id="22292-173">Dizeyi tek tek sözcüklere böler</span><span class="sxs-lookup"><span data-stu-id="22292-173">Splits string into individual words</span></span> | <span data-ttu-id="22292-174">["This", "dir", "a", "iyidir", "Product"]</span><span class="sxs-lookup"><span data-stu-id="22292-174">["this","is","a","good","product"]</span></span>
|<span data-ttu-id="22292-175">3. Removedefaultstopkelimeleri</span><span class="sxs-lookup"><span data-stu-id="22292-175">3. RemoveDefaultStopWords</span></span> | <span data-ttu-id="22292-176">*Ve gibi* stopsözcüklerini *kaldırır.*</span><span class="sxs-lookup"><span data-stu-id="22292-176">Removes stopwords like *is* and *a*.</span></span> | <span data-ttu-id="22292-177">["iyi", "ürün"]</span><span class="sxs-lookup"><span data-stu-id="22292-177">["good","product"]</span></span>
|<span data-ttu-id="22292-178">4. MapValueToKey</span><span class="sxs-lookup"><span data-stu-id="22292-178">4. MapValueToKey</span></span> | <span data-ttu-id="22292-179">Değerleri, giriş verilerine göre anahtarlar (kategoriler) ile eşler</span><span class="sxs-lookup"><span data-stu-id="22292-179">Maps the values to keys (categories) based on the input data</span></span> |  <span data-ttu-id="22292-180">[1, 2]</span><span class="sxs-lookup"><span data-stu-id="22292-180">[1,2]</span></span>
|<span data-ttu-id="22292-181">5. ProduceNGrams</span><span class="sxs-lookup"><span data-stu-id="22292-181">5. ProduceNGrams</span></span> | <span data-ttu-id="22292-182">Metni birbirini izleyen sözcüklerin sıralamasına dönüştürür</span><span class="sxs-lookup"><span data-stu-id="22292-182">Transforms text into sequence of consecutive words</span></span> | <span data-ttu-id="22292-183">[1, 1, 1, 0, 0]</span><span class="sxs-lookup"><span data-stu-id="22292-183">[1,1,1,0,0]</span></span>
|<span data-ttu-id="22292-184">6. NormalizeLpNorm</span><span class="sxs-lookup"><span data-stu-id="22292-184">6. NormalizeLpNorm</span></span> | <span data-ttu-id="22292-185">Girdileri LP-norm olarak ölçeklendirin</span><span class="sxs-lookup"><span data-stu-id="22292-185">Scale inputs by their lp-norm</span></span> | <span data-ttu-id="22292-186">[0,577350529, 0,577350529, 0,577350529, 0, 0]</span><span class="sxs-lookup"><span data-stu-id="22292-186">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span></span>
