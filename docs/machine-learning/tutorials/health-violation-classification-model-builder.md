---
title: 'Öğretici: model Oluşturucu ile sistem durumu ihlallerini sınıflandırma'
description: Bu öğreticide, San Francisco 'da Restoran sistem durumu ihlali önem derecesine göre sınıflandırmak için ML.NET model Oluşturucu kullanılarak birden çok Lass sınıflandırma modelinin nasıl oluşturulduğu gösterilmektedir.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc,mlnet-tooling
ms.openlocfilehash: 468d09510cb55971d25877e40b7c54aae479ac84
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875622"
---
# <a name="tutorial-classify-the-severity-of-restaurant-health-violations-with-model-builder"></a>Öğretici: model Oluşturucu ile Restoran sistem durumu ihlallerinin önem derecesini sınıflandırma

Sistem durumu incelemeleri sırasında bulunan restoran ihlallerinin risk düzeyini kategorilere ayırmak için model Oluşturucu kullanarak birden çok Lass sınıflandırma modeli oluşturmayı öğrenin.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
>
> - Verileri hazırlama ve anlama
> - Senaryo seçin
> - Veritabanından veri yükleme
> - Modeli eğitme
> - Modeli değerlendirme
> - Tahmin için modeli kullanma

> [!NOTE]
> Model Oluşturucu Şu anda önizleme aşamasındadır.

## <a name="prerequisites"></a>Önkoşullar

Önkoşul ve Yükleme yönergelerinin bir listesi için [model Oluşturucu Yükleme Kılavuzu](../how-to-guides/install-model-builder.md)' nu ziyaret edin.

## <a name="model-builder-multiclass-classification-overview"></a>Model Oluşturucu birden çok Lass sınıflandırmasına genel bakış

Bu örnek, model Oluşturucu ile oluşturulmuş bir makine öğrenimi modeli kullanarak sistem durumu ihlalleri riskini kategorilere ayırır ve bir C# .NET Core konsol uygulaması oluşturur. Bu öğreticinin kaynak kodunu [DotNet/machinöğrenim-Samples](https://github.com/dotnet/machinelearning-samples/tree/main/samples/modelbuilder/MulticlassClassification_RestaurantViolations) GitHub deposunda bulabilirsiniz.

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. "Restoran Antihlalleri" adlı bir **C# .NET Core konsol uygulaması** oluşturun. **Çözümün ve projenin aynı dizine yerleştirdiğinizden** emin **olun (vs** 2019) veya **çözüm için dizin oluşturma** **denetlenir** (vs 2017).

## <a name="prepare-and-understand-the-data"></a>Verileri hazırlama ve anlama

> Machine Learning modelini eğmekte ve değerlendirmek için kullanılan veri kümesi, başlangıçta [genel sağlık restoranın güvenlik puanlarından oluşan San Francisco departmanından](https://www.sfdph.org/dph/EH/Food/score/default.asp). Kolaylık olması için veri kümesi, yalnızca modeli eğmeyle ilgili sütunları içerecek şekilde yoğunlaştırılmış ve tahmin edilebilir. [Veri kümesi](https://data.sfgov.org/Health-and-Social-Services/Restaurant-Scores-LIVES-Standard/pyih-qa8i?row_index=0)hakkında daha fazla bilgi edinmek için aşağıdaki Web sitesini ziyaret edin.

[Restoran güvenlik puanları veri kümesini indirin](https://github.com/luisquintanilla/machinelearning-samples/raw/AB1608219/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantScores.zip) ve sıkıştırmayı açın.

Veri kümesindeki her bir satır, sistem durumu departmanından bir inceleme sırasında gözlemlendiği ihlallerle ilgili bilgiler ve bu ihlallerin genel durum ve güvenlik konusunda yer aldığı tehdidi risk değerlendirmesi hakkında bilgi içerir.

| Inspectiontype | ViolationDescription | RiskCategory |
| --- | --- | --- |
| Rutin-zamanlanmamış | Yetersiz Temizlenen veya ayıklanmış yiyecek iletişim yüzeyleri | Orta risk |
| Yeni sahiplik | Yüksek riskli Vermin ve daha fazla bildirim | Yüksek riskli |
| Rutin-zamanlanmamış | Temizleyen giyme yok veya düzgün şekilde depolanmıyor ya da yetersiz bir temizleme işlemi | Düşük risk |

- **Inspectiontype**: inceleme türü. Bu, yeni bir oluşturma, bir denetim, bir şikayet denetimi ve birçok diğer tür için ilk kez inceleme olabilir.
- **ViolationDescription**: İnceleme sırasında bulunan ihlalin bir açıklaması.
- **RiskCategory**: risk önem derecesi, bir ihlalin genel sistem durumu ve güvenliği doğurur.

`label`Tahmin etmek istediğiniz sütundur. Bir sınıflandırma görevi gerçekleştirirken, hedef bir kategori (metin veya sayısal) olarak atanır. Bu sınıflandırma senaryosunda, ihlalin önem derecesine düşük, orta veya yüksek riskli değer atanır. Bu nedenle, **RiskCategory** etikettir. , `features` Modeli size tahmin etmek için verdiğiniz girişlerdir `label` . Bu durumda, **ınspectiontype** ve **ViolationDescription** , **RiskCategory** tahmin etmek için özellik veya giriş olarak kullanılır.

## <a name="choose-a-scenario"></a>Senaryo seçin

![Visual Studio 'da model Oluşturucu Sihirbazı](./media/sentiment-analysis-model-builder/model-builder-screen.png)

Modelinize eğitebilmeniz için, model Oluşturucu tarafından sağlanan kullanılabilir makine öğrenimi senaryoları listesinden seçin. Bu durumda senaryo, *sorun sınıflandırması* olur.

1. **Çözüm Gezgini**, *Restoran antihlalleri* projesine sağ tıklayın ve Machine Learning Ekle ' yi seçin   >  .
1. Bu örnek için, senaryo birden çok sınıf sınıflandırmasıdır. Model oluşturucunun *senaryo* adımında, **sorun sınıflandırması** senaryosunu seçin.

## <a name="load-the-data"></a>Verileri yükleme

Model Oluşturucu bir SQL Server veritabanından veya yerel bir dosyadan veya biçiminde verileri kabul `csv` eder `tsv` .

1. Model Oluşturucu aracının veri adımında veri kaynağı açılır listesinden **SQL Server** ' yi seçin.
1. **SQL Server veritabanına Bağlan** metin kutusunun yanındaki düğmeyi seçin.
    1. **Veri Seç** iletişim kutusunda **Microsoft SQL Server veritabanı dosyası**' nı seçin.
    1. **Her zaman bu seçimi kullan** onay kutusunu temizleyin ve **devam**' ı seçin.
    1. **Bağlantı özellikleri** iletişim kutusunda, **Araştır** ' ı seçin ve indirilen *restoranın. mdf* dosyasını seçin.
    1. **Tamam**’ı seçin.
1. **Tablo adı** açılır listesinden **ihlaller** ' i seçin.
1. **Tahmin edilecek (etiket)** aşağı açılan sütunda **RiskCategory** öğesini seçin.
1. Varsayılan sütun seçimlerini, **ınspectiontype** ve **ViolationDescription** **giriş sütunları (Özellikler)** açılır listesine iade edin.
1. Model Oluşturucu 'daki sonraki adıma geçmek için **eğitme** bağlantısını seçin.

## <a name="train-the-model"></a>Modeli eğitme

Bu öğreticide sorun sınıflandırma modelini eğitmek için kullanılan makine öğrenimi görevi birden çok Lass sınıflandırmasıdır. Model oluşturma işlemi sırasında model Oluşturucu, veri kümeniz için en iyi işlem modelini bulmak üzere farklı bir çok Lass sınıflandırma algoritması ve ayarı kullanarak modelleri ayrı ayrı işler.

Modelin eğmesi için gereken süre, veri miktarıyla orantılıdır. Model Oluşturucu, veri kaynağınızın boyutuna bağlı olarak, **tren süresi (saniye)** için varsayılan bir değer seçer.

1. Model Oluşturucu değeri, " **saniye)** ila 10 saniye arasında bir süre olarak ayarlasa da, 30 saniyeye yükseltin. Daha uzun bir süre için eğitim, model oluşturucunun en iyi modeli aramada daha fazla sayıda algoritmaların ve parametrelerin birleşimini keşfetmesine olanak tanır.
1. **Eğitimi Başlat**' ı seçin.

    Eğitim süreci boyunca, ilerleme verileri `Progress` eğitme adımının bölümünde görüntülenir.

    - **Durum** , eğitim sürecinin tamamlanma durumunu görüntüler.
    - **En iyi doğruluk**   Model Oluşturucu tarafından şu ana kadar bulunan en iyi yöntem modelinin doğruluğunu görüntüler. Daha yüksek doğruluk, modelin test verilerinde daha doğru tahmin edilen anlamına gelir.
    - **En iyi algoritma**   Model Oluşturucu tarafından şu ana kadar bulunan en iyi şekilde gerçekleştiren algoritmanın adını görüntüler.
    - **Son algoritma**   modeli eğitmek için model Oluşturucu tarafından en son kullanılan algoritmanın adını görüntüler.

1. Eğitim tamamlandıktan sonra bir sonraki adıma geçmek için bağlantıyı **değerlendir** ' i seçin.

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Eğitim adımının sonucu en iyi performansa sahip bir modeldir. Model oluşturucunun değerlendir adımında çıkış bölümü **, en iyi model girişinde en** iyi şekilde kullanılan model tarafından kullanılan algoritmayı ve **En Iyi model doğruluğunun** ölçümlerini içerir. Ayrıca, araştırılan en fazla beş model içeren bir Özet tablosu ve bunların ölçümleri görüntülenir.

Doğruluk ölçümlerinizi tatmin ediyorsanız, model doğruluğunu artırmak için bazı kolay yollar, modelin eğilmesi veya daha fazla veri kullanmak için zaman miktarını artırmaktır. Aksi takdirde, model Oluşturucu 'daki son adıma geçmek için **kod** bağlantısını seçin.

## <a name="add-the-code-to-make-predictions"></a>Tahminleri yapmak için kodu ekleyin

Eğitim sürecinin bir sonucu olarak iki proje oluşturulur.

- RestaurantViolationsML. ConsoleApp: model eğitimi ve örnek tüketim kodu içeren bir C# .NET Core konsol uygulaması.
- RestaurantViolationsML. Model: giriş ve çıkış modeli verilerinin şemasını tanımlayan veri modellerini, eğitim sırasında en iyi gerçekleştirme modelinin kaydedilmiş sürümünü ve tahmin yapmak için çağrılan bir yardımcı sınıfı içeren .NET Standard bir sınıf kitaplığı `ConsumeModel` .

1. Model oluşturucunun kod adımında, otomatik olarak oluşturulan projeleri çözüme eklemek için **Proje Ekle** ' yi seçin.
1. *Program. cs* dosyasını *Restoran antihlalleri* projesinde açın.
1. *RestaurantViolationsML. model* projesine başvurmak için aşağıdaki using ifadesini ekleyin:

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L2)]

1. Modeli kullanarak yeni verileri tahmin etmek için, `ModelInput` uygulamanızın yöntemi içinde sınıfın yeni bir örneğini oluşturun `Main` . Risk kategorisinin girişin bir parçası olmadığına dikkat edin. Bunun nedeni, modelin tahmin oluşturması.

    [!code-csharp [TestData](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L11-L15)]

1. `Predict`Sınıfından yöntemi kullanın `ConsumeModel` . `Predict`Yöntemi, eğitilen modeli yükler, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) model için bir oluşturur ve yeni verilerde tahmine dayalı hale getirmek için onu kullanır.

    [!code-csharp [Prediction](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L17-L24)]

1. Uygulamayı çalıştırın.

    Program tarafından oluşturulan çıkış aşağıdaki kod parçacığına benzemelidir:

    ```bash
    Inspection Type: Complaint
    Violation Description: Inadequate sewage or wastewater disposal
    Risk Category: Moderate Risk
    ```

Oluşturulan projelere başka bir çözümün içinde daha sonraki bir zamanda başvurmanız gerekirse, bunları dizin içinde bulabilirsiniz `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` .

Tebrikler! Model Oluşturucu kullanarak sistem durumu ihlallerinin riskini kategorize etmek için bir makine öğrenimi modelini başarıyla oluşturdunuz. Bu öğreticinin kaynak kodunu [DotNet/machinöğrenim-Samples](https://github.com/dotnet/machinelearning-samples/tree/main/samples/modelbuilder/MulticlassClassification_RestaurantViolations) GitHub deposunda bulabilirsiniz.

## <a name="additional-resources"></a>Ek kaynaklar

Bu öğreticide bahsedilen konular hakkında daha fazla bilgi edinmek için aşağıdaki kaynakları ziyaret edin:

- [Model Oluşturucu senaryoları](../automate-training-with-model-builder.md#scenario)
- [Birden çok Lass sınıflandırması](../resources/glossary.md#multiclass-classification)
- [Birden çok Lass sınıflandırma modeli ölçümleri](../resources/metrics.md#evaluation-metrics-for-multi-class-classification)
