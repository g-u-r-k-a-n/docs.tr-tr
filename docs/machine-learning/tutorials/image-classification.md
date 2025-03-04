---
title: "Öğretici: TensorFlow 'dan ML.NET görüntü sınıflandırma modeli"
description: Mevcut bir TensorFlow modelinden yeni bir ML.NET görüntü sınıflandırma modeline bilgi aktarmayı öğrenin. TensorFlow modeli görüntüleri bin kategoride sınıflandırmakta eğitildi. ML.NET modeli görüntüleri daha az daha geniş kategoriler halinde sınıflandırmak için aktarım öğrenimini kullanır.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: b3e5617979d1635248f87db6008d3e234bb3ffc5
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104877039"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a>Öğretici: önceden eğitilen bir TensorFlow modelinden ML.NET görüntü sınıflandırma modeli oluşturma

Mevcut bir TensorFlow modelinden yeni bir ML.NET görüntü sınıflandırma modeline bilgi aktarmayı öğrenin.

TensorFlow modeli görüntüleri bin kategoride sınıflandırmakta eğitildi. ML.NET modeli, görüntüleri 3 kategoride sınıflandırmak üzere bir modeli eğitemak için, ardışık düzeninde TensorFlow modelinin bir parçasını kullanır.

[Görüntü sınıflandırma](https://en.wikipedia.org/wiki/Outline_of_object_recognition) modelini sıfırdan eğitmek için milyonlarca parametre, bir dizi etiketli eğitim verisi ve çok miktarda bilgi işlem kaynağı (yüzlerce GPU saati) ayarlanması gerekir. Özel bir modeli sıfırdan eğitmek kadar etkili olmasa da, aktarım öğrenimi, binlerce görüntüde ve oldukça hızlı bir şekilde özelleştirilmiş bir model (GPU olmayan bir saat içinde) kullanarak bu işlemi kısayolmanıza olanak sağlar. Bu öğreticide, yalnızca bir düzine eğitim görüntüsü kullanılarak bu işlem daha da ayrıntılı şekilde ölçeklendirilir.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
> [!div class="checklist"]
>
> * Sorunu anlama
> * Önceden eğitilen TensorFlow modelini ML.NET işlem hattına ekleyin
> * ML.NET modelini eğitme ve değerlendirme
> * Test görüntüsünü sınıflandır

Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/TransferLearningTF) deposunda bulabilirsiniz. Varsayılan olarak, Bu öğreticinin .NET proje yapılandırmasında .NET Core 2,2 ' i hedeflediğini unutmayın.

## <a name="what-is-transfer-learning"></a>Öğrenme aktarımı nedir?

Aktarım öğrenimi, bir sorunu çözerken ve ilgili başka bir soruna uygulanarak bilgi elde edilen bilgileri kullanma işlemidir.

Bu öğretici için, görüntüleri 3 kategoriye göre sınıflandıran bir ML.NET modelinde resimleri bin kategoride sınıflandırmakta olan bir TensorFlow modelinin bir bölümünü kullanırsınız.

## <a name="prerequisites"></a>Önkoşullar

* [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya üzeri ya da visual Studio 2017 sürüm 15,6 veya üzeri, ".NET Core platformlar arası geliştirme" iş yükü yüklendi.
* [Öğretici varlıkları dizini. ZIP dosyası](https://github.com/dotnet/samples/blob/main/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)
* [InceptionV1 Machine Learning modeli](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a>Doğru makine öğrenimi görevini seçin

### <a name="deep-learning"></a>Derin öğrenme

[Derin öğrenme](https://en.wikipedia.org/wiki/Deep_learning) , görüntü işleme ve konuşma tanıma gibi revolutionizing alan Machine Learning bir alt kümesidir.

Derin öğrenme modelleri, birden fazla öğrenme katmanı içeren büyük ölçekli [veri](https://en.wikipedia.org/wiki/Labeled_data) ve [sinir Networks](https://en.wikipedia.org/wiki/Artificial_neural_network) kümeleri kullanılarak eğitilir. Derin öğrenme:

* Görüntü İşleme gibi bazı görevlerde daha iyi çalışır.
* Çok büyük miktarlarda eğitim verisi gerektirir.

Görüntü sınıflandırması, görüntüleri otomatik olarak kategoriler halinde sınıflandırmamızı sağlayan ortak bir Machine Learning görevdir:

* Görüntüde insan yüzü algılanıyor.
* Kediler ve köpekler algılanıyor.

 Aşağıdaki görüntülerde olduğu gibi, bir resmin (n) yiyecek, oyunı veya gereç olduğunu belirleme:

![Pizza Image ](./media/image-classification/220px-Pepperoni_pizza.jpg)
 ![ oyuncak ayı görüntüsü ](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
 ![ Toaster görüntüsü](./media/image-classification/193px-Broodrooster.jpg)

>[!Note]
> Önceki görüntüler Wikimedia Commons ' a aittir ve aşağıdaki gibi verilmiştir:
>
> * "220px-Pepperoni_pizza.jpg" ortak etki alanı <https://commons.wikimedia.org/w/index.php?curid=79505> ,
> * "119px-Nalle_-_a_small_brown_teddy_bear.jpg", [Jonık](https://commons.wikimedia.org/wiki/User:Jonik) -Self-PHOTOGRAFIĞI, CC BY-SA 2,0, <https://commons.wikimedia.org/w/index.php?curid=48166> .
> * "193px-Broodrooster.jpg", [a. Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) -kendi Iş, CC BY-SA 3,0, <https://commons.wikimedia.org/w/index.php?curid=27403>

`Inception model`Görüntüleri bin kategoride sınıflandırıp, ancak bu öğreticide, görüntüleri daha küçük bir kategori kümesinde ve yalnızca bu kategorilerden sınıflandırmanız gerekir. Parçasını girin `transfer` `transfer learning` . `Inception model`Özel görüntü sınıflandırıcınızın yeni sınırlı kategorilerine görüntü tanıma ve sınıflandırma özelliğini aktarabilirsiniz.

* Yemek
* Cağı
* Elektrikli

Bu öğretici, veri kümesinde eğitilen popüler bir görüntü tanıma modeli olan TensorFlow [Inception modeli](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) derin öğrenme modelini kullanır `ImageNet` . TensorFlow modeli, tüm görüntüleri "şemsiye", "Jersey" ve "Dishronı" gibi binlik bir sınıfa göre sınıflandırır.

, `Inception model` Binlerce farklı görüntüde önceden eğitildiğinden, dahili olarak görüntü tanımlama için gereken [görüntü özelliklerini](https://en.wikipedia.org/wiki/Feature_(computer_vision)) içerir. En az sınıfa sahip yeni bir modeli eğitebilmeniz için modelde bu iç görüntü özelliklerinden yararlanabilirsiniz.

Aşağıdaki diyagramda gösterildiği gibi, .NET Core veya .NET Framework uygulamalarında ML.NET NuGet paketlerine bir başvuru eklersiniz. ML.NET dahil olmak `TensorFlow` üzere, var olan eğitilen bir model dosyasını yükleyen kodu yazmanıza izin veren yerel kitaplığı içerir ve başvurur `TensorFlow` .

![TensorFlow Transform ML.NET yay diyagramı](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a>Birden çok Lass sınıflandırması

Klasik makine öğrenimi algoritması için giriş olarak uygun özellikleri ayıklamak üzere TensorFlow kullanım modelini kullandıktan sonra, ML.NET [çok sınıflı bir sınıflandırıcı](../resources/tasks.md#multiclass-classification)ekleyeceğiz.

Bu durumda kullanılan belirli bir eğitmen, [ÇOKTERİMLİ lojistik regresyon algoritmasıdır](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).

Bu eğitimci tarafından uygulanan algoritma, görüntü verilerinde çalışan derin bir öğrenme modelinin durumu olan çok sayıda özellik ile ilgili sorunları iyi gerçekleştirir.

### <a name="data"></a>Veriler

İki veri kaynağı vardır: `.tsv` dosya ve resim dosyaları.  `tags.tsv`Dosya iki sütun içerir: ilki olarak tanımlanır `ImagePath` ve ikinci tane `Label` görüntüye karşılık gelir. Aşağıdaki örnek dosya bir başlık satırına sahip değildir ve şuna benzer:

<!-- markdownlint-disable MD010 -->
```tsv
broccoli.jpg    food
pizza.jpg   food
pizza2.jpg  food
teddy2.jpg  toy
teddy3.jpg  toy
teddy4.jpg  toy
toaster.jpg appliance
toaster2.png    appliance
```
<!-- markdownlint-enable MD010 -->

Eğitim ve test görüntüleri, bir ZIP dosyasında indirileceği varlıklar klasörlerinde bulunur. Bu görüntüler Wikimedia Commons ' a aittir.
> *[Wkımedıa Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), ücretsiz medya deposu.* 10:48 Ekim, 2018: <https://commons.wikimedia.org/wiki/Pizza>
> <https://commons.wikimedia.org/wiki/Toaster>
> <https://commons.wikimedia.org/wiki/Teddy_bear>

## <a name="setup"></a>Kurulum

### <a name="create-a-project"></a>Proje oluşturma

1. "TransferLearningTF" adlı bir **.NET Core konsol uygulaması** oluşturun.

1. **Microsoft.ml NuGet paketini** yükler:

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    * Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.
    * Paket kaynağı olarak "nuget.org" öğesini seçin, gözden geçirme sekmesini seçin, **Microsoft.ml** için arama yapın.
    * **Install** düğmesini seçin.
    * **Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin.
    * Listelenen paketlerin lisans koşullarını kabul ediyorsanız, **Lisans kabulü** Iletişim kutusunda **kabul ediyorum** düğmesini seçin.
    * **Microsoft. ml. ımageanalytics**, **SciSharp. TensorFlow. Redist** ve **Microsoft. ml. TensorFlow** için bu adımları yineleyin.

### <a name="download-assets"></a>Varlıkları indir

1. [Proje Varlıkları Dizin ZIP dosyasını](https://github.com/dotnet/samples/blob/main/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)indirin ve sıkıştırmayı açın.

1. `assets`Dizini *Transferlearningtf* proje dizininize kopyalayın. Bu dizin ve alt dizinleri, bu öğretici için gerekli olan veri ve destek dosyalarını (bir sonraki adımda indirecek ve ekleyeceğiniz bir model hariç) içerir.

1. [Inception modelini](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)indirin ve sıkıştırmayı açın.

1. `inception5h`Dizinin Içeriğini *Transferlearningtf* proje dizininize kopyalamanız yeterlidir `assets/inception` . Bu dizin, aşağıdaki görüntüde gösterildiği gibi, bu öğretici için gereken modeli ve ek destek dosyalarını içerir:

   ![Dizin içeriğini geçersiz kılma](./media/image-classification/inception-files.png)

1. Çözüm Gezgini, varlık dizinindeki ve alt dizinlerde bulunan dosyaların her birine sağ tıklayın ve **Özellikler**' i seçin. **Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala** olarak değiştirin.

### <a name="create-classes-and-define-paths"></a>Sınıf oluşturma ve yollar tanımlama

1. Aşağıdaki ek `using` deyimlerini *program. cs* dosyasının en üstüne ekleyin:

    [!code-csharp[AddUsings](./snippets/image-classification/csharp/Program.cs#AddUsings)]

1. Varlık yollarını belirtmek için aşağıdaki kodu metodun hemen üstüne ekleyin `Main` :

    [!code-csharp[DeclareGlobalVariables](./snippets/image-classification/csharp/Program.cs#DeclareGlobalVariables)]

1. Giriş verileriniz ve tahminler için sınıflar oluşturun.

    [!code-csharp[DeclareImageData](./snippets/image-classification/csharp/Program.cs#DeclareImageData)]

    `ImageData` , giriş resmi veri sınıfıdır ve aşağıdaki <xref:System.String> alanlara sahiptir:

    * `ImagePath` görüntü dosyası adını içerir.
    * `Label` resim etiketi için bir değer içerir.

1. Projenize yeni bir sınıf ekleyin `ImagePrediction` :

    [!code-csharp[DeclareImagePrediction](./snippets/image-classification/csharp/Program.cs#DeclareImagePrediction)]

    `ImagePrediction` , görüntü tahmin sınıfıdır ve aşağıdaki alanlara sahiptir:

    * `Score` belirli bir görüntü sınıflandırması için güven yüzdesini içerir.
    * `PredictedLabelValue` tahmin edilen görüntü sınıflandırma etiketi için bir değer içerir.

    `ImagePrediction` , model eğitilen bir tahmin için kullanılan sınıftır. `string` `ImagePath` Görüntü yolu için bir () içerir. , `Label` Modeli yeniden kullanmak ve eğitme yapmak için kullanılır. , `PredictedLabelValue` Tahmin ve değerlendirme sırasında kullanılır. Değerlendirme için eğitim verileri olan bir giriş, tahmin edilen değerler ve model kullanılır.

### <a name="initialize-variables-in-main"></a>Değişkenleri ana olarak Başlat

1. `mlContext`Değişkeni yeni bir örneğiyle başlatın `MLContext` .  Satırı, `Console.WriteLine("Hello World!")` yöntemindeki aşağıdaki kodla değiştirin `Main` :

    [!code-csharp[CreateMLContext](./snippets/image-classification/csharp/Program.cs#CreateMLContext)]

    [Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır ve başlatılıyor, `mlContext` model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ml.net ortamı oluşturur. Entity Framework, kavramsal olarak da benzerdir `DBContext` .

### <a name="create-a-struct-for-inception-model-parameters"></a>Inception model parametreleri için bir struct oluşturun

1. Inception modelinde, geçirmeniz gereken birkaç parametre vardır. Aşağıdaki kodla parametre değerlerini kolay adlarla eşlemek için bir struct oluşturun, yalnızca `Main()` yönteminden sonra:

    [!code-csharp[InceptionSettings](./snippets/image-classification/csharp/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a>Görüntüleme yardımcı programı yöntemi oluşturma

Görüntü verilerini ve ilgili tahminleri birden çok kez görüntüleyenden sonra, görüntüyü ve tahmin sonuçlarını görüntülemeyi işlemek için bir görüntüleme yardımcı programı yöntemi oluşturun.

1. `DisplayResults()`Aşağıdaki kodu kullanarak, yapının hemen ardından yöntemi oluşturun `InceptionSettings` :

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. Metodun gövdesini girin `DisplayResults` :

    [!code-csharp[DisplayPredictions](./snippets/image-classification/csharp/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a>. Tsv dosya yardımcı programı yöntemi oluşturma

1. `ReadFromTsv()`Aşağıdaki kodu kullanarak yönteminden hemen sonra yöntemini oluşturun `DisplayResults()` :

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. Metodun gövdesini girin `ReadFromTsv` :

    [!code-csharp[ReadFromTsv](./snippets/image-classification/csharp/Program.cs#ReadFromTsv)]

    Kod, dosya yolunu, `tags.tsv` özelliğin görüntü dosyası adına eklemek `ImagePath` ve bir nesnesine yüklemek için dosyasını ayrıştırır `Label` `ImageData` .

### <a name="create-a-method-to-make-a-prediction"></a>Tahmin yapmak için bir yöntem oluşturma

1. Yöntemi, `ClassifySingleImage()` `DisplayResults()` aşağıdaki kodu kullanarak yönteminden hemen önce oluşturun:

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. `ImageData`Tek için tam yolu ve resim dosyası adını içeren bir nesne oluşturun `ImagePath` . Aşağıdaki kodu yöntemine bir sonraki satır olarak ekleyin `ClassifySingleImage()` :

    [!code-csharp[LoadImageData](./snippets/image-classification/csharp/Program.cs#LoadImageData)]

1. Aşağıdaki kodu yöntemine bir sonraki satıra ekleyerek tek bir tahmin yapın `ClassifySingleImage` :

    [!code-csharp[PredictSingle](./snippets/image-classification/csharp/Program.cs#PredictSingle)]

    Tahmin sağlamak için, [tahmin ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) yöntemini kullanın. [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) , tek bir veri örneğinde tahmin gerçekleştirmenize olanak tanıyan, KULLANıŞLı bir API 'dir. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) , iş parçacığı açısından güvenli değildir. Tek iş parçacıklı veya prototip ortamlarında kullanılması kabul edilebilir. Üretim ortamlarında geliştirilmiş performans ve iş parçacığı güvenliği için, `PredictionEnginePool` [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) uygulamanız genelinde kullanılacak nesneleri oluşturan hizmetini kullanın. [ `PredictionEnginePool` ASP.NET Core Web API 'sinde kullanma](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)hakkında bu kılavuza bakın.

    > [!NOTE]
    > `PredictionEnginePool` Hizmet Uzantısı Şu anda önizleme aşamasındadır.

1. Yöntem içindeki bir sonraki kod satırı olarak tahmin sonucunu görüntüleyin `ClassifySingleImage()` :

   [!code-csharp[DisplayPrediction](./snippets/image-classification/csharp/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a>ML.NET model işlem hattını oluşturma

Bir ML.NET model işlem hattı, bir tahmin zinciri zinciridir. İşlem hattı oluşturma sırasında yürütmenin gerçekleşmediğini unutmayın. Tahmin aracı nesneleri oluşturulur ancak yürütülmez.

1. Modeli oluşturmak için bir yöntem ekleyin

    Bu yöntem, öğreticinin kalbidir. Model için bir işlem hattı oluşturur ve ML.NET modelini oluşturmak için işlem hattını trafelar. Ayrıca, modeli daha önce görülmeyen test verilerine karşı değerlendirir.

    `GenerateModel()` `InceptionSettings` Aşağıdaki kodu kullanarak, yapının hemen ardından ve yönteminden hemen önce yöntemini oluşturun `DisplayResults()` :

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. Görüntü verilerinden pikselleri yüklemek, yeniden boyutlandırmak ve çıkarmak için tahmini ekleyin:

    [!code-csharp[ImageTransforms](./snippets/image-classification/csharp/Program.cs#ImageTransforms)]

    Görüntü verilerinin, TensorFlow modelinin beklediği biçimde işlenmesi gerekir. Bu durumda, görüntüler belleğe yüklenir, tutarlı bir boyuta yeniden boyutlandırılır ve pikseller sayısal bir vektörde ayıklanır.

1. TensorFlow modelini yüklemek için tahmin Aracı ' ı ekleyin ve puan edin:

    [!code-csharp[ScoreTensorFlowModel](./snippets/image-classification/csharp/Program.cs#ScoreTensorFlowModel)]

    İşlem hattındaki bu aşamada, TensorFlow modeli belleğe yüklenir ve ardından, Masorflow model ağı aracılığıyla piksel değerleri vektörü işlenir. Ayrıntılı bir öğrenme modeline giriş uygulama ve modeli kullanarak bir çıktı oluşturma, **Puanlama** olarak adlandırılır. Model tamamen kullanılırken, Puanlama bir çıkarım veya tahmin yapar.

    Bu durumda, çıkarım yapan katman olan son katman dışındaki tüm TensorFlow modelini kullanırsınız. Penultimate katmanının çıkışı etiketlidir `softmax_2_preactivation` . Bu katmanın çıktısı, orijinal giriş görüntülerini niteleyen özelliklerin bir vektörüdür.

    TensorFlow modeli tarafından oluşturulan bu özellik vektörü, bir ML.NET eğitim algoritmasına giriş olarak kullanılacaktır.

1. Eğitim verilerinde dize etiketlerini tamsayı anahtar değerleriyle eşlemek için tahmin aracı 'ı ekleyin:

    [!code-csharp[MapValueToKey](./snippets/image-classification/csharp/Program.cs#MapValueToKey)]

    Sonraki eklenen ml.net eğitmen, etiketlerinin `key` rastgele dizeler yerine biçiminde olmasını gerektirir. Anahtar, bir dize değerine bire bir eşleme içeren bir sayıdır.

1. ML.NET eğitim algoritmasını ekleyin:

    [!code-csharp[AddTrainer](./snippets/image-classification/csharp/Program.cs#AddTrainer)]

1. Tahmin edilen anahtar değerini bir dizeye geri eşlemek için tahmin aracı ekleyin:

    [!code-csharp[MapKeyToValue](./snippets/image-classification/csharp/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a>Modeli eğitme

1. [Loadfromtextfile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) sarmalayıcısı kullanarak eğitim verilerini yükleyin. Aşağıdaki kodu yönteminin sonraki satırı olarak ekleyin `GenerateModel()` :

    [!code-csharp[LoadData](./snippets/image-classification/csharp/Program.cs#LoadData "Load the data")]

    ML.NET içindeki veriler [ıdataview sınıfı](xref:Microsoft.ML.IDataView)olarak temsil edilir. `IDataView` , tablo verilerini (sayısal ve metin) tanımlamaya yönelik esnek ve verimli bir yoldur. Veriler bir metin dosyasından veya gerçek zamanlı olarak (örneğin, SQL veritabanı veya günlük dosyaları) bir `IDataView` nesneye yüklenebilir.

1. Modeli yukarıda yüklenen verilerle eğitme:

    [!code-csharp[TrainModel](./snippets/image-classification/csharp/Program.cs#TrainModel)]

    `Fit()`Yöntemi, eğitim veri kümesini işlem hattına uygulayarak modelinizi ister.

## <a name="evaluate-the-accuracy-of-the-model"></a>Modelin doğruluğunu değerlendirin

1. Aşağıdaki kodu yönteminin bir sonraki satırına ekleyerek test verilerini yükleyin ve dönüştürün `GenerateModel` :

    [!code-csharp[LoadAndTransformTestData](./snippets/image-classification/csharp/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    Modeli değerlendirmek için kullanabileceğiniz birkaç örnek görüntü vardır. Eğitim verileri gibi, bunların `IDataView` model tarafından dönüştürülebilmeleri için bir ' a yüklenmesi gerekir.

1. `GenerateModel()`Modeli değerlendirmek için yöntemine aşağıdaki kodu ekleyin:

    [!code-csharp[Evaluate](./snippets/image-classification/csharp/Program.cs#Evaluate)]

    Tahmin kümesinden sonra, [değerlendir ()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) yöntemi:

    * Model değerlendirir (tahmin edilen değerleri test veri kümesiyle karşılaştırır `labels` ).
    * Model performans ölçümlerini döndürür.

1. Model doğruluk ölçümlerini görüntüleme

    Ölçümleri göstermek, sonuçları paylaşmak ve sonra bunlar üzerinde işlem yapmak için aşağıdaki kodu kullanın:

    [!code-csharp[DisplayMetrics](./snippets/image-classification/csharp/Program.cs#DisplayMetrics)]

    Aşağıdaki ölçümler görüntü sınıflandırması için değerlendirilir:

    * `Log-loss` - [günlük kaybını](../resources/glossary.md#log-loss)görüntüleyin. Günlük kaybını mümkün olduğunca sıfıra yakın olacak şekilde istiyorsunuz.
    * `Per class Log-loss`. Her sınıf günlük kaybını, mümkün olduğunca sıfıra yakın olacak şekilde istiyorsunuz.

1. Eğitilen modeli sonraki satır olarak döndürmek için aşağıdaki kodu ekleyin:

    [!code-csharp[SaveModel](./snippets/image-classification/csharp/Program.cs#ReturnModel)]

## <a name="run-the-application"></a>Uygulamayı çalıştırın!

1. `GenerateModel` `Main` Mlcontext sınıfının oluşturulmasından sonra yönteminde öğesine çağrısını ekleyin:

    [!code-csharp[CallGenerateModel](./snippets/image-classification/csharp/Program.cs#CallGenerateModel)]

1. Yöntemine yapılan çağrıyı yönteme `ClassifySingleImage()` bir sonraki kod satırı olarak ekleyin `Main` :

    [!code-csharp[CallClassifySingleImage](./snippets/image-classification/csharp/Program.cs#CallClassifySingleImage)]

1. Konsol uygulamanızı çalıştırın (CTRL + F5). Sonuçlarınız aşağıdaki çıktıya benzer olmalıdır.  Uyarıları veya işlem iletilerini görebilirsiniz, ancak bu iletiler netme için aşağıdaki sonuçlardan kaldırılmıştır.

    ```console
    =============== Training classification model ===============
    Image: broccoli2.jpg predicted as: food with score: 0.8955513
    Image: pizza3.jpg predicted as: food with score: 0.9667718
    Image: teddy6.jpg predicted as: toy with score: 0.9797683
    =============== Classification metrics ===============
    LogLoss is: 0.0653774699265059
    PerClassLogLoss is: 0.110315812569315 , 0.0204391272836966 , 0
    =============== Making single image classification ===============
    Image: toaster3.jpg predicted as: appliance with score: 0.9646884
    ```

Tebrikler! Artık ML.NET içindeki bir modele aktarım öğrenimi uygulayarak görüntü sınıflandırması için bir makine öğrenimi modeli oluşturdunuz `TensorFlow` .

Bu öğreticinin kaynak kodunu [DotNet/Samples](https://github.com/dotnet/samples/tree/main/machine-learning/tutorials/TransferLearningTF) deposunda bulabilirsiniz.

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> * Sorunu anlama
> * Önceden eğitilen TensorFlow modelini ML.NET işlem hattına ekleyin
> * ML.NET modelini eğitme ve değerlendirme
> * Test görüntüsünü sınıflandır

Genişletilmiş bir görüntü sınıflandırma örneğini araştırmak için Machine Learning örnekleri GitHub deposuna göz atın.
> [!div class="nextstepaction"]
> [DotNet/machinöğrenim-Samples GitHub deposu](https://github.com/dotnet/machinelearning-samples/)
