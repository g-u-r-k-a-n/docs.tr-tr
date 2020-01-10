---
title: 'Öğretici: gerileme kullanarak fiyatları tahmin etme'
description: Bu öğreticide, özellikle New York City taksi Fares fiyatlarını tahmin etmek için ml.NET kullanarak bir gerileme modelinin nasıl oluşturulacağı gösterilmektedir.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: e4014dbdfb81af65c35d2f7693ef2c57885303ff
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711629"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a>Öğretici: ML.NET ile gerileme kullanarak fiyatları tahmin etme

Bu öğreticide, özellikle New York City taksi Fares fiyatlarını tahmin etmek için ml.NET kullanarak bir [gerileme modelinin](../resources/glossary.md#regression) nasıl oluşturulacağı gösterilmektedir.

Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:
> [!div class="checklist"]
>
> * Verileri hazırlama ve anlama
> * Verileri yükleme ve dönüştürme
> * Bir öğrenme algoritması seçin
> * Modeli eğitme
> * Modeli değerlendirme
> * Tahmin için modeli kullanma

## <a name="prerequisites"></a>Prerequisites

* [Visual Studio 2017 sürüm 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ".NET Core platformlar arası geliştirme" iş yükü yüklendi.

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. "Taxifaretahminini" adlı bir **.NET Core konsol uygulaması** oluşturun.

1. Veri kümesi ve model dosyalarını depolamak için projenizde *veri* adlı bir dizin oluşturun.

1. **Microsoft.ml** NuGet paketini yükler:

    **Çözüm Gezgini**, projeye sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin. Paket kaynağı olarak "nuget.org" öğesini seçin, **Araştır** sekmesini seçin, **Microsoft.ml**için arama yapın, listeden paketi seçin ve sonra da **Install** düğmesini seçin. **Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin. **Microsoft. ml. FastTree** NuGet paketi için de aynısını yapın.

## <a name="prepare-and-understand-the-data"></a>Verileri hazırlama ve anlama

1. [Taxi-fare-train. csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) ve [Taxi-fare-test. csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) veri kümelerini indirin ve önceki adımda oluşturduğunuz *veri* klasörüne kaydedin. Machine Learning modelini eğitmek için bu veri kümelerini kullanıyoruz ve sonra modelin ne kadar doğru olduğunu değerlendirin. Bu veri kümeleri başlangıçta [NYC TLC TAXI seyahat veri kümesinden](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)alınır.

1. **Çözüm Gezgini**, \*. csv dosyalarının her birine sağ tıklayın ve **Özellikler**' i seçin. **Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.

1. **Taxi-fare-train. csv** veri kümesini açın ve ilk satırdaki sütun başlıklarına bakın. Her sütuna göz atın. Verileri anlayın ve hangi sütunların **Özellikler** olduğunu ve hangisinin **etiket**olduğunu belirleyin.

`label`, tahmin etmek istediğiniz sütundur. Tanımlanan `Features`, modele `Label`tahmin etmek için verdiğiniz girişlerdir.

Belirtilen veri kümesi şu sütunları içerir:

* **vendor_id:** Taxı satıcısının KIMLIĞI bir özelliktir.
* **rate_code:** Taxı seyahati 'ın hız türü bir özelliktir.
* **passenger_count:** Seyahat üzerindeki pascuların sayısı bir özelliktir.
* **trip_time_in_secs:** Seyahati için geçen süre. Seyahat tamamlanmadan önce seyahat tarifeli havayolu tahmin etmek istiyorsunuz. Bu sırada, seyahati ne kadar süreyle yapılacağını bilemezsiniz. Bu nedenle, seyahat süresi bir özellik değildir ve bu sütunu modelden dışlayabilirsiniz.
* **trip_distance:** Seyahat uzaklığı bir özelliktir.
* **payment_type:** Ödeme yöntemi (nakit veya kredi kartı) bir özelliktir.
* **fare_amount:** Ödenen toplam TAXI tarifeli havayolu etikettir.

## <a name="create-data-classes"></a>Veri sınıfları oluşturma

Giriş verileri ve tahminleri için sınıflar oluşturun:

1. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından > **Yeni öğe** **Ekle** ' yi seçin.
1. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *TaxiTrip.cs*olarak değiştirin. Sonra **Ekle** düğmesini seçin.
1. Aşağıdaki `using` yönergelerini yeni dosyaya ekleyin:

   [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

Mevcut sınıf tanımını kaldırın ve *TaxiTrip.cs* dosyasına `TaxiTrip` ve `TaxiTripFarePrediction`iki sınıfa sahip aşağıdaki kodu ekleyin:

[!code-csharp[DefineTaxiTrip](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip`, giriş veri sınıfıdır ve veri kümesi sütunlarının her biri için tanımlar içerir. Veri kümesindeki kaynak sütunlarının dizinlerini belirtmek için <xref:Microsoft.ML.Data.LoadColumnAttribute> özniteliğini kullanın.

`TaxiTripFarePrediction` sınıfı tahmin edilen sonuçları temsil eder. Tek bir float alanına sahiptir ve bir `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> özniteliği uygulanmış `FareAmount`. Regresyon görevi söz konusu olduğunda, **puan** sütunu tahmin edilen etiket değerlerini içerir.

> [!NOTE]
> Giriş ve tahmin veri sınıflarında kayan nokta değerlerini göstermek için `float` türünü kullanın.

### <a name="define-data-and-model-paths"></a>Veri ve model yollarını tanımlama

Aşağıdaki ek `using` deyimlerini *program.cs* dosyasının en üstüne ekleyin:

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

Veri kümelerine sahip dosyaların yollarını tutmak için üç alan oluşturmanız ve modelin kaydedileceği dosyanın olması gerekir:

* `_trainDataPath`, modeli eğitmek için kullanılan veri kümesiyle dosyanın yolunu içerir.
* `_testDataPath`, modeli değerlendirmek için kullanılan veri kümesi ile dosyanın yolunu içerir.
* `_modelPath`, eğitilen modelin depolandığı dosyanın yolunu içerir.

Bu yolları ve `_textLoader` değişkenini belirtmek için `Main` yönteminin üstüne aşağıdaki kodu ekleyin:

[!code-csharp[InitializePaths](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

Tüm ML.NET işlemleri [Mlcontext sınıfında](xref:Microsoft.ML.MLContext)başlar. `mlContext` başlatmak, model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ML.NET ortamı oluşturur. Benzer, kavramsal olarak, Entity Framework `DBContext`.

### <a name="initialize-variables-in-main"></a>Değişkenleri ana olarak Başlat

`mlContext` değişkenini bildirmek ve başlatmak için `Main` yöntemindeki `Console.WriteLine("Hello World!")` satırı aşağıdaki kodla değiştirin:

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

`Train` yöntemini çağırmak için `Main` metoduna sonraki kod satırı olarak aşağıdakini ekleyin:

[!code-csharp[Train](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

`Train()` yöntemi aşağıdaki görevleri yürütür:

* Verileri yükler.
* Verileri ayıklar ve dönüştürür.
* Modeli TRAIN.
* Modeli döndürür.

`Train` yöntemi modeli trafelar. Aşağıdaki kodu kullanarak bu yöntemi hemen `Main`aşağıda oluşturun:

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a>Verileri yükleme ve dönüştürme

ML.NET, sayısal veya metin tablolu verileri tanımlamaya yönelik esnek ve verimli bir yöntem olarak [ıdataview sınıfını](xref:Microsoft.ML.IDataView) kullanır. `IDataView` metin dosyalarını veya gerçek zamanlı olarak yükleyebilirsiniz (örneğin, SQL veritabanı veya günlük dosyaları). `Train()` yönteminin ilk satırı olarak aşağıdaki kodu ekleyin:

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

Taxı seyahat tarifeli havayolu tahmin etmek istediğiniz gibi `FareAmount` sütunu, tahmin ettiğiniz `Label` (modelin çıktısı) olur. `FareAmount`kopyalamak için `CopyColumnsEstimator` Transformation sınıfını kullanın ve aşağıdaki kodu ekleyin:

[!code-csharp[CopyColumnsEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

Modeli gösteren algoritma **sayısal** Özellikler gerektirir, bu nedenle kategorik verileri (`VendorId`, `RateCode`ve `PaymentType`) değerlerini sayılara (`VendorIdEncoded`, `RateCodeEncoded`ve `PaymentTypeEncoded`) dönüştürmeniz gerekir. Bunu yapmak için, sütunların her birinde farklı değerlere farklı sayısal anahtar değerleri atayan [Onehotencodingtransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) dönüştürme sınıfını kullanın ve aşağıdaki kodu ekleyin:

[!code-csharp[OneHotEncodingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

Veri hazırlığının son adımı, tüm özellik sütunlarını `mlContext.Transforms.Concatenate` dönüştürme sınıfını kullanarak **Özellikler** sütunuyla birleştirir. Varsayılan olarak, bir öğrenme algoritması yalnızca **Özellikler** sütunundaki özellikleri işler. Aşağıdaki kodu ekleyin:

[!code-csharp[ColumnConcatenatingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a>Bir öğrenme algoritması seçin

Bu sorun, New York şehrinde bir TAXI seyahat tarifeli havayolu tahmin etmeye yönelik olarak tasarlanmıştır. İlk bakışta, yalnızca seyahat mesafesini temel alan görünebilir. Ancak, New York 'taki TAXI satıcıları, ek Pastörler veya nakit yerine kredi kartıyla ödeme yapma gibi diğer faktörlere göre farklılık gösteren ücretler ücretlendirir. Veri kümesindeki diğer faktörlere bağlı olarak gerçek bir değer olan fiyat değerini tahmin etmek istiyorsunuz. Bunu yapmak için bir [gerileme](../resources/glossary.md#regression) makine öğrenimi görevi seçersiniz.

Aşağıdaki `Train()`kod satırı olarak aşağıdakini ekleyerek [Fasttreeregressiontrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) Machine Learning görevini veri dönüştürme tanımlarına ekleyin:

[!code-csharp[FastTreeRegressionTrainer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a>Modeli eğitme

Modeli eğitim `dataview` sığdırın ve aşağıdaki kod satırını `Train()` yöntemine ekleyerek eğitilen modeli döndürün:

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

[Fit ()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) yöntemi, veri kümesini dönüştürerek ve eğitimi uygulayarak modelinizi eğitme.

`Train()` yönteminde aşağıdaki kod satırıyla eğitilen modeli döndürün:

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Daha sonra, kalite güvencesi ve doğrulama için test verilerinize ait model performansınızı değerlendirin. Aşağıdaki kodla `Train()`hemen sonra `Evaluate()` yöntemini oluşturun:

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

`Evaluate` yöntemi aşağıdaki görevleri yürütür:

* Test veri kümesini yükler.
* Regresyon Değerlendiricisi oluşturur.
* Modeli değerlendirir ve ölçümler oluşturur.
* Ölçümleri görüntüler.

Aşağıdaki kodu kullanarak, `Train` yöntemi çağrısının altına sağ `Main` yönteminden yeni yönteme bir çağrı ekleyin:

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

[Loadfromtextfile ()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) yöntemini kullanarak test veri kümesini yükleyin. `Evaluate` yöntemine aşağıdaki kodu ekleyerek bu veri kümesini bir kalite denetimi olarak kullanarak modeli değerlendirin:

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

Ardından, aşağıdaki kodu `Evaluate()`ekleyerek `Test` verileri dönüştürün:

[!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

[Transform ()](xref:Microsoft.ML.ITransformer.Transform%2A) yöntemi, test veri kümesi giriş satırları için tahminleri yapar.

`RegressionContext.Evaluate` yöntemi, belirtilen veri kümesini kullanarak `PredictionModel` için kalite ölçümlerini hesaplar. Regresyon değerlendiricileri tarafından hesaplanan genel ölçümleri içeren bir <xref:Microsoft.ML.Data.RegressionMetrics> nesnesi döndürür.

Modelin kalitesini belirlemede bunları göstermek için öncelikle ölçümleri almanız gerekir. Aşağıdaki kodu `Evaluate` yönteminin sonraki satırı olarak ekleyin:

[!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

Tahmin kümesine sahip olduktan sonra, tahmin edilen değerleri test veri kümesindeki gerçek `Labels` karşılaştıran ve modelin nasıl çalıştığı hakkında ölçümler döndüren [değerlendir ()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) yöntemi, modeli değerlendirir.

Modeli değerlendirmek ve değerlendirme ölçümlerini oluşturmak için aşağıdaki kodu ekleyin:

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

[RKARE](../resources/glossary.md#coefficient-of-determination) , regresyon modellerinin başka bir değerlendirme ölçümdür. RKARE 0 ile 1 arasında değerleri alır. Daha yakın değeri 1 ' dir, model daha iyidir. RKARE değerini göstermek için `Evaluate` yöntemine aşağıdaki kodu ekleyin:

[!code-csharp[DisplayRSquared](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

[RMS](../resources/glossary.md#root-of-mean-squared-error-rmse) , regresyon modelinin değerlendirme ölçümlerinden biridir. Bunun ne kadar küçük olması, modelin ne kadar iyi olduğu. RMS değerini göstermek için `Evaluate` yöntemine aşağıdaki kodu ekleyin:

[!code-csharp[DisplayRMS](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a>Tahmin için modeli kullanma

Aşağıdaki kodu kullanarak, `Evaluate` yönteminden hemen sonra `TestSinglePrediction` yöntemini oluşturun:

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

`TestSinglePrediction` yöntemi aşağıdaki görevleri yürütür:

* Test verileri için tek bir açıklama oluşturur.
* Sınama verilerine göre tarifeli havayolu miktarını tahmin eder.
* Raporlama için test verilerini ve tahminleri birleştirir.
* Tahmin edilen sonuçları görüntüler.

Aşağıdaki kodu kullanarak, `Evaluate` yöntemi çağrısının altına sağ `Main` yönteminden yeni yönteme bir çağrı ekleyin:

[!code-csharp[CallTestSinglePrediction](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

Aşağıdaki kodu `TestSinglePrediction()`ekleyerek tarifeli havayolu tahmin etmek için `PredictionEngine` kullanın:

[!code-csharp[MakePredictionEngine](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştirmenize olanak tanıyan, KULLANıŞLı bir API 'dir. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) , iş parçacığı açısından güvenli değildir. Tek iş parçacıklı veya prototip ortamlarında kullanılması kabul edilebilir. Üretim ortamlarında geliştirilmiş performans ve iş parçacığı güvenliği için, uygulamanız genelinde kullanılmak üzere [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nesnelerinin bir [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) oluşturan `PredictionEnginePool` hizmetini kullanın. [ASP.NET Core Web API 'sindeki `PredictionEnginePool` kullanma](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)hakkında bu kılavuza bakın.

> [!NOTE]
> `PredictionEnginePool` hizmet uzantısı Şu anda önizleme aşamasındadır.

Bu öğretici, bu sınıf içinde bir test yolculuğu kullanır. Daha sonra, modelle denemeler yapmak için başka senaryolar da ekleyebilirsiniz. Bir `TaxiTrip`örneği oluşturarak eğitilen modelin Maliyet tahminini `TestSinglePrediction()` yönteminde test etmek için bir seyahat ekleyin:

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

Ardından, tarifeli havayolu yöntemine bir sonraki `TestSinglePrediction()` kod satırı olarak ekleyerek, bir TAXI seyahat verisinin tek bir örneğine göre ' yi tahmin edin ve `PredictionEngine` geçirin:

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

[Tahmin ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) işlevi, verilerin tek bir örneğini tahmin eder.

Belirtilen yolculuğa ait tahmini tarifeli havayolu göstermek için `TestSinglePrediction` yöntemine aşağıdaki kodu ekleyin:

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

Test çalışmanıza yönelik tahmini TAXI tarifeli havayolu görmek için programı çalıştırın.

Tebrikler! Artık TAXI seyahat Fares 'yi tahmin etmek için bir makine öğrenimi modelini başarıyla oluşturdunuz, doğruluğu değerlendirildi ve tahmine dayalı hale getirmek için kullandınız. Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub deposunda bulabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:

> [!div class="checklist"]
>
> * Verileri hazırlama ve anlama
> * Öğrenme işlem hattı oluşturma
> * Verileri yükleme ve dönüştürme
> * Bir öğrenme algoritması seçin
> * Modeli eğitme
> * Modeli değerlendirme
> * Tahmin için modeli kullanma

Daha fazla bilgi edinmek için sonraki öğreticiye ilerleyin.

> [!div class="nextstepaction"]
> [Iris kümelemesi](iris-clustering.md)
