---
title: 'Öğretici: yaklaşım-ikili sınıflandırmayı çözümle'
description: Bu öğreticide, Web sitesi açıklamalarından yaklaşımı sınıflandırın bir Razor Pages uygulamasının nasıl oluşturulacağı ve uygun eylemin nasıl yapılacağı gösterilmektedir. İkili yaklaşım Sınıflandırıcısı, Visual Studio 'da model Oluşturucu kullanır.
ms.date: 11/21/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc,mlnet-tooling
ms.openlocfilehash: 7761240055c90ae9c713b1c460e9e83316d256f9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/29/2020
ms.locfileid: "81278957"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a>Öğretici: ML.NET model Oluşturucu kullanarak Web uygulamasındaki Web sitesindeki açıklamaları çözümleme

Bir Web uygulamasının içinde gerçek zamanlı açıklamalardan yaklaşımı çözümlemeyi öğrenin.

Bu öğreticide, Web sitesi açıklamalarından gerçek zamanlı olarak yaklaşım sınıflandıran bir ASP.NET Core Razor Pages uygulamasının nasıl oluşturulacağı gösterilmektedir.

Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:

> [!div class="checklist"]
>
> - ASP.NET Core Razor Pages uygulaması oluşturma
> - Verileri hazırlama ve anlama
> - Senaryo seçin
> - Verileri yükleme
> - Modeli eğitme
> - Modeli değerlendirme
> - Tahmin için modeli kullanma

> [!NOTE]
> Model Oluşturucu Şu anda önizleme aşamasındadır.

Bu öğreticinin kaynak kodunu [DotNet/machinöğrenim-örnekleri](https://github.com/dotnet/machinelearning-samples) deposunda bulabilirsiniz.

## <a name="pre-requisites"></a>Ön koşullar

Önkoşul ve Yükleme yönergelerinin bir listesi için [model Oluşturucu Yükleme Kılavuzu](../how-to-guides/install-model-builder.md)' nu ziyaret edin.

## <a name="create-a-razor-pages-application"></a>Razor Pages uygulaması oluşturma

1. ASP.NET Core bir **Razor Pages uygulaması** oluşturun.

    1. Visual Studio 'Yu açın ve menü çubuğundan **dosya > yeni > projesi** öğesini seçin.
    1. Yeni proje iletişim kutusunda, **Visual C#** düğümünü ve ardından **Web** düğümünü seçin.
    1. **ASP.NET Core Web uygulaması** proje şablonunu seçin.
    1. **Ad** metin kutusuna "SentimentRazor" yazın.
    1. **Çözümün ve projenin aynı dizine yerleştirdiğinizden** emin **olun (vs** 2019) veya **çözüm için dizin oluşturma** **denetlenir** (vs 2017).
    1. **Tamam** düğmesini seçin.
    1. Pencerede farklı ASP.NET Core proje türlerini görüntüleyen **Web uygulaması** ' nı seçin ve ardından **Tamam** düğmesini seçin.

## <a name="prepare-and-understand-the-data"></a>Verileri hazırlama ve anlama

[Vikipedi Detox veri kümesini](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)indirin. Web sayfası açıldığında, sayfaya sağ tıklayın, **farklı kaydet** ' i seçin ve dosyayı bilgisayarınızda herhangi bir yere kaydedin.

*Vivtox-250-Line-Data. tsv* veri kümesindeki her satır, visede bir kullanıcı tarafından bırakılan farklı bir gözden geçirmeyi temsil eder. İlk sütun metnin (0-Toxic, 1 ' in Toxic) yaklaşımını temsil eder ve ikinci sütun Kullanıcı tarafından bırakılan yorumu temsil eder. Sütunlar sekmelerle ayrılır. Veriler aşağıdaki gibi görünür:

| Yaklaşım | Sentimentmetni |
| :---: | :---: |
1 | = = İşlenmemiş = = dude, o Carl resmini geri yüklemeniz veya başka bir şey yapmanız gerekir.
1 | = = TAMAM! = = ıM, DAHA SONRA BIR WIKI 'YI DAHA SONRA!!!
0 | Bunu umuyoruz.

## <a name="choose-a-scenario"></a>Senaryo seçin

![Visual Studio 'da model Oluşturucu Sihirbazı](./media/sentiment-analysis-model-builder/model-builder-screen.png)

Modelinize eğitebilmeniz için, model Oluşturucu tarafından sağlanan kullanılabilir makine öğrenimi senaryoları listesinden seçim yapmanız gerekir.

1. **Çözüm Gezgini**, *SentimentRazor* projesine sağ tıklayın ve Machine Learning Ekle ' yi seçin **Add**  >  **Machine Learning**.
1. Bu örnek için senaryo, yaklaşım analiziydi. Model Oluşturucu aracının *senaryo* adımında **yaklaşım Analizi** senaryosunu seçin.

## <a name="load-the-data"></a>Verileri yükleme

Model Oluşturucu iki kaynaktan (bir SQL Server veritabanı ya da yerel bir dosya) veya biçimdeki verileri kabul eder `csv` `tsv` .

1. Model Oluşturucu aracının veri adımında, veri kaynağı açılır listesinden **Dosya** ' yı seçin.
1. **Dosya seçin** metin kutusunun yanındaki düğmeyi seçin ve dosya Gezgini 'ni kullanarak, *vibtox-250-Line-Data. tsv* dosyasına gidin ve seçin.
1. **Tahmin edilecek sütun (etiket)** açılan **listesini seçin.**
1. **Giriş sütunları (Özellikler)** açılır menüsü için varsayılan değerleri bırakın.
1. Model Oluşturucu aracında bir sonraki adıma geçmek için **eğitme** bağlantısını seçin.

## <a name="train-the-model"></a>Modeli eğitme

Bu öğreticide yaklaşım Analizi modelini eğitmek için kullanılan makine öğrenimi görevi ikili sınıflandırmasıdır. Model oluşturma işlemi sırasında model Oluşturucu, veri kümeniz için en iyi işlem modelini bulmak üzere farklı ikili sınıflandırma algoritmalarını ve ayarlarını kullanarak modelleri ayrı ayrı işler.

Modelin eğitilmesi için gereken süre, veri miktarına müşterinizin istekleriyle orantılı. Model Oluşturucu, veri kaynağınızın boyutuna bağlı olarak, **tren süresi (saniye)** için varsayılan bir değer seçer.

1. Model Oluşturucu değeri, " **saniye)** ila 10 saniye arasında bir süre olarak ayarlasa da, 30 saniyeye yükseltin. Daha uzun bir süre için eğitim, model oluşturucunun en iyi modeli aramada daha fazla sayıda algoritmaların ve parametrelerin birleşimini keşfetmesine olanak tanır.
1. **Eğitimi Başlat**' ı seçin.

    Eğitim süreci boyunca, ilerleme verileri `Progress` eğitme adımının bölümünde görüntülenir.

    - Durum, eğitim sürecinin tamamlanma durumunu görüntüler.
    - En iyi doğruluk, şu ana kadar model Oluşturucu tarafından bulunan en iyi şekilde oluşan modelin doğruluğunu gösterir. Daha yüksek doğruluk, modelin test verilerinde daha doğru tahmin edilen anlamına gelir.
    - En iyi algoritma, şu ana kadar model Oluşturucu tarafından bulunan en iyi şekilde gerçekleştirilen algoritmanın adını görüntüler.
    - Son algoritma modeli eğitmek için model Oluşturucu tarafından en son kullanılan algoritmanın adını görüntüler.

1. Eğitim tamamlandıktan sonra bir sonraki adıma geçmek için bağlantıyı **değerlendir** ' i seçin.

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Eğitim adımının sonucu, en iyi performansa sahip bir model olacaktır. Model Oluşturucu aracının değerlendir adımında, çıkış bölümü **en iyi model girişinde en** iyi işlem modeli için kullanılan algoritmayı ve **En Iyi model doğruluğunun** ölçümlerini içerir. Ayrıca, ilk beş modeli ve bunların ölçümlerini içeren bir Özet tablosu gösterilir.

Doğruluk ölçümlerinizi tatmin ediyorsanız, model doğruluğunu artırmak için bazı kolay yollar, modelin eğilmesi veya daha fazla veri kullanmak için zaman miktarını artırmaktır. Aksi takdirde, model Oluşturucu aracında son adıma geçmek için **kod** bağlantısını seçin.

## <a name="add-the-code-to-make-predictions"></a>Tahminleri yapmak için kodu ekleyin

Eğitim sürecinin bir sonucu olarak iki proje oluşturulacaktır.

### <a name="reference-the-trained-model"></a>Eğitilen modele başvur

1. Model Oluşturucu aracının *kod* adımında, otomatik olarak oluşturulan projeleri çözüme eklemek Için **Proje Ekle** ' yi seçin.

    Aşağıdaki projeler **Çözüm Gezgini** görünmelidir:

    - *SentimentRazorML. ConsoleApp*: model eğitimi ve tahmin kodunu içeren bir .NET Core konsol uygulaması.
    - *SentimentRazorML. model*: giriş ve çıkış modeli verilerinin şemasını tanımlayan veri modellerini ve eğitim sırasında en iyi uygulanan modelin kaydedilmiş sürümünü içeren .NET Standard bir sınıf kitaplığı.

    Bu öğretici için, *SentimentRazorML. model* projesi yalnızca, tahmine dayalı olarak konsolu yerine *SentimentRazor* Web uygulamasında yapılabilmesi için kullanılır. *SentimentRazorML. ConsoleApp* , Puanlama için kullanılmayacak olsa da, daha sonra yeni verileri kullanarak modeli yeniden eğitebilmek için kullanılabilir. Yeniden eğitim, Bu öğreticinin kapsamı dışındadır.

### <a name="configure-the-predictionengine-pool"></a>PredictionEngine havuzunu yapılandırma

Tek bir tahmin yapmak için, oluşturmanız gerekir <xref:Microsoft.ML.PredictionEngine%602> . <xref:Microsoft.ML.PredictionEngine%602> , iş parçacığı açısından güvenli değildir. Ayrıca, uygulamanız içinde gerek duyduğu her yerde bir örneği oluşturmanız gerekir. Uygulamanız büyüdükçe, bu işlem yönetilebilir hale gelebilir. Daha iyi performans ve iş parçacığı güvenliği için, `PredictionEnginePool` <xref:Microsoft.Extensions.ObjectPool.ObjectPool%601> <xref:Microsoft.ML.PredictionEngine%602> uygulamanız genelinde kullanılacak nesneleri oluşturan bağımlılık ekleme ve hizmetin bir birleşimini kullanın.

1. *Microsoft.Extensions.ml* NuGet paketini yükler:

    1. **Çözüm Gezgini**, projeye sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.
    1. Paket kaynağı olarak "nuget.org" öğesini seçin.
    1. **Araştır** sekmesini seçin ve **Microsoft.Extensions.ml** için arama yapın.
    1. Listeden paketi seçin ve ardından **Install** düğmesini seçin.
    1. **Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin
    1. Listelenen paketlerin lisans koşullarını kabul ediyorsanız, **Lisans kabulü** Iletişim kutusunda **kabul ediyorum** düğmesini seçin.

1. *SentimentRazor* projesindeki *Startup.cs* dosyasını açın.
1. *Microsoft.Extensions.ml* NuGet paketini ve *SentimentRazorML. model* projesine başvurmak için aşağıdaki using deyimlerini ekleyin:

    ```csharp
    using System.IO;
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

1. Eğitilen model dosyasının konumunu depolamak için genel bir değişken oluşturun.

    ```csharp
    private readonly string _modelPath;
    ```

1. Model dosyası, uygulamanızın derleme dosyalarının yanı sıra derleme dizininde depolanır. Daha kolay erişim sağlamak için, `GetAbsolutePath` yönteminden sonra adlı bir yardımcı yöntem oluşturun `Configure`

    ```csharp
    public static string GetAbsolutePath(string relativePath)
    {
        FileInfo _dataRoot = new FileInfo(typeof(Program).Assembly.Location);
        string assemblyFolderPath = _dataRoot.Directory.FullName;

        string fullPath = Path.Combine(assemblyFolderPath, relativePath);
        return fullPath;
    }
    ```

1. Öğesini `GetAbsolutePath` `Startup` ayarlamak için sınıf oluşturucusunda metodunu kullanın `_modelPath` .

    ```csharp
    _modelPath = GetAbsolutePath("MLModel.zip");
    ```

1. `PredictionEnginePool`Yöntemi için uygulamanızı için yapılandırın `ConfigureServices` :

    ```csharp
    services.AddPredictionEnginePool<ModelInput, ModelOutput>()
            .FromFile(_modelPath);
    ```

### <a name="create-sentiment-analysis-handler"></a>Yaklaşım Analizi işleyicisi oluşturma

Tahmine dayalı, uygulamanın ana sayfasında yapılır. Bu nedenle, Kullanıcı girişini alan ve `PredictionEnginePool` bir tahmin eklenmesi için kullanması gereken bir yöntem.

1. *Pages* dizininde bulunan *Index.cshtml.cs* dosyasını açın ve aşağıdaki using deyimlerini ekleyin:

    ```csharp
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

    `PredictionEnginePool` `Startup` Sınıfında yapılandırılan ' ı kullanmak için, onu kullanmak istediğiniz modelin oluşturucusuna eklemek gerekir.

1. Sınıfının içine başvurmak için bir değişken ekleyin `PredictionEnginePool` `IndexModel` .

    ```csharp
    private readonly PredictionEnginePool<ModelInput, ModelOutput> _predictionEnginePool;
    ```

1. Sınıfında bir Oluşturucu oluşturun `IndexModel` ve `PredictionEnginePool` hizmeti ona ekleyin.

    ```csharp
    public IndexModel(PredictionEnginePool<ModelInput, ModelOutput> predictionEnginePool)
    {
        _predictionEnginePool = predictionEnginePool;
    }
    ```

1. `PredictionEnginePool`Web sayfasından alınan Kullanıcı girişinden tahminleri yapmak için öğesini kullanan bir yöntem işleyicisi oluşturun.

    1. Yönteminin altında `OnGet` , adlı yeni bir yöntem oluşturun `OnGetAnalyzeSentiment`

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. Yöntemi içinde `OnGetAnalyzeSentiment` , kullanıcının girişi boş veya null olduğunda *nötr* yaklaşım döndürün.

        ```csharp
        if (String.IsNullOrEmpty(text)) return Content("Neutral");
        ```

    1. Geçerli bir giriş verildiğinde yeni bir örneğini oluşturun `ModelInput` .

        ```csharp
        var input = new ModelInput { SentimentText = text };
        ```

    1. Yaklaşımı `PredictionEnginePool` tahmin etmek için kullanın.

        ```csharp
        var prediction = _predictionEnginePool.Predict(input);
        ```

    1. Tahmin edilen `bool` değeri, aşağıdaki kodla birlikte Toxic öğesine dönüştürün.

        ```csharp
        var sentiment = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";
        ```

    1. Son olarak, yaklaşımı Web sayfasına geri döndürün.

        ```csharp
        return Content(sentiment);
        ```

### <a name="configure-the-web-page"></a>Web sayfasını yapılandırma

Tarafından döndürülen sonuçlar, `OnGetAnalyzeSentiment` Web sayfasında dinamik olarak görüntülenir `Index` .

1. *Pages* dizinindeki *Index. cshtml* dosyasını açın ve içeriğini şu kodla değiştirin:

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. Ardından, *wwwroot\css* dizinindeki *site. css* sayfasının sonuna CSS stil oluşturma kodu ekleyin:

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. Bundan sonra, Web sayfasından işleyiciye giriş göndermek için kod ekleyin `OnGetAnalyzeSentiment` .

    1. *Wwwroot\js* dizininde bulunan *site.js* dosyasında, `getSentiment` işleyiciye Kullanıcı girişiyle bir http isteği almak için adlı bir işlev oluşturun `OnGetAnalyzeSentiment` .

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. Bunun altında, yaklaşım `updateMarker` tahmin edildiğinde Web sayfasındaki işaretin konumunu dinamik olarak güncelleştirmek için adlı başka bir işlev ekleyin.

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. Kullanıcıdan girişi almak için çağrılan bir olay işleyici işlevi oluşturun `updateSentiment` , `OnGetAnalyzeSentiment` işlevi kullanarak işleve gönderin `getSentiment` ve işaretleyiciyi `updateMarker` işlevle güncelleştirin.

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. Son olarak, olay işleyicisini kaydedin ve `textarea` özniteliği ile öğesine bağlayın `id=Message` .

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a>Uygulamayı çalıştırma

Uygulamanız ayarlandığına göre, tarayıcınızda başlatması gereken uygulamayı çalıştırın.

Uygulama başlatıldığında, *model Oluşturucu* seyrek erişimli yazın! metin alanına. Görünen tahmini yaklaşım, *Toxic* olmamalıdır.

![Tahmin edilen yaklaşım penceresiyle pencere çalıştırma](./media/sentiment-analysis-model-builder/web-app.png)

Model Oluşturucu tarafından oluşturulan projelere daha sonra başka bir çözümün içinde başvurulmaları gerekiyorsa, bunları dizin içinde bulabilirsiniz `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` .

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> - ASP.NET Core Razor Pages uygulaması oluşturma
> - Verileri hazırlama ve anlama
> - Senaryo seçin
> - Verileri yükleme
> - Modeli eğitme
> - Modeli değerlendirme
> - Tahmin için modeli kullanma

### <a name="additional-resources"></a>Ek Kaynaklar

Bu öğreticide bahsedilen konular hakkında daha fazla bilgi edinmek için aşağıdaki kaynakları ziyaret edin:

- [Model Oluşturucu senaryoları](../automate-training-with-model-builder.md#scenario)
- [İkili sınıflandırma](../resources/glossary.md#binary-classification)
- [İkili sınıflandırma modeli ölçümleri](../resources/metrics.md#evaluation-metrics-for-binary-classification)
