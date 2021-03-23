---
title: 'Öğretici: model Oluşturucu ile gerileme kullanarak fiyatları tahmin etme'
description: Bu öğreticide, özellikle New York City taksi Fares fiyatlarını tahmin etmek için ml.net model Oluşturucu kullanarak bir gerileme modeli oluşturma gösterilmektedir.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc, mlnet-tooling
ms.openlocfilehash: c34586014b5617f7712a4b708cb2e4a4814da684
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874764"
---
# <a name="tutorial-predict-prices-using-regression-with-model-builder"></a>Öğretici: model Oluşturucu ile gerileme kullanarak fiyatları tahmin etme

Fiyatları tahmin etmek için bir gerileme modeli oluşturmak üzere ML.NET model Oluşturucu 'Yu nasıl kullanacağınızı öğrenin.  Bu öğreticide geliştirdiğiniz .NET konsol uygulaması, geçmiş New York taksi tarifeli havayolu verilerine dayalı olarak taksi Fares 'yi tahmin eder.

Model Oluşturucu fiyat tahmin şablonu, sayısal tahmin değeri gerektiren herhangi bir senaryo için kullanılabilir. Örnek senaryolar şunlardır: ev fiyat tahmini, talep tahmini ve satış tahmini.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
> [!div class="checklist"]
>
> - Verileri hazırlama ve anlama
> - Senaryo seçin
> - Verileri yükleme
> - Modeli eğitme
> - Modeli değerlendirme
> - Tahmin için modeli kullanma

> [!NOTE]
> Model Oluşturucu Şu anda önizleme aşamasındadır.

## <a name="pre-requisites"></a>Ön koşullar

Önkoşul ve Yükleme yönergelerinin bir listesi için [model Oluşturucu Yükleme Kılavuzu](../how-to-guides/install-model-builder.md)' nu ziyaret edin.

## <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. "Taxifaretahmine" adlı bir **C# .NET Core konsol uygulaması** oluşturun. **Çözümün ve projenin aynı dizine yerleştirdiğinizden** emin **olun (vs** 2019) veya **çözüm için dizin oluşturma** **denetlenir** (vs 2017).

## <a name="prepare-and-understand-the-data"></a>Verileri hazırlama ve anlama

1. Veri kümesi dosyalarını depolamak için projenizde *veri* adlı bir dizin oluşturun.

1. Machine Learning modelini eğmekte ve değerlendirmek için kullanılan veri kümesi, ilk olarak NYC TLC TAXI seyahat veri kümesinden.

    1. Veri kümesini indirmek için [taxi-fare-train.csv indirme bağlantısına](https://raw.githubusercontent.com/dotnet/machinelearning/main/test/data/taxi-fare-train.csv)gidin.

    1. Sayfa yüklendiğinde, sayfada herhangi bir yere sağ tıklayın ve **farklı kaydet**' i seçin.

    1. Dosyayı önceki adımda oluşturduğunuz *veri* klasörüne kaydetmek Için **Farklı Kaydet iletişim kutusunu** kullanın.

1. **Çözüm Gezgini**, *taxi-fare-train.csv* dosyasına sağ tıklayın ve **Özellikler**' i seçin. **Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala** olarak değiştirin.

Veri kümesindeki her satır `taxi-fare-train.csv` bir TAXI tarafından yapılan gelişlerin ayrıntılarını içerir.

1. **taxi-fare-train.csv** veri kümesini aç

    Belirtilen veri kümesi şu sütunları içerir:

    - **vendor_id:** Taxı satıcısının KIMLIĞI bir özelliktir.
    - **rate_code:** Taxı seyahati 'ın hız türü bir özelliktir.
    - **passenger_count:** Seyahat üzerindeki pascuların sayısı bir özelliktir.
    - **trip_time_in_secs:** Seyahati için geçen süre. Seyahat tamamlanmadan önce seyahat tarifeli havayolu tahmin etmek istiyorsunuz. Bu anda seyahati ne kadar süreyle yapılacağını bilemezsiniz. Bu nedenle, seyahat süresi bir özellik değildir ve bu sütunu modelden dışlayabilirsiniz.
    - **trip_distance:** Seyahat uzaklığı bir özelliktir.
    - **payment_type:** Ödeme yöntemi (nakit veya kredi kartı) bir özelliktir.
    - **fare_amount:** Ödenen toplam TAXI tarifeli havayolu etikettir.

`label`Tahmin etmek istediğiniz sütundur. Regresyon görevi gerçekleştirirken, amaç sayısal bir değeri tahmin etmek için kullanılır. Bu fiyat tahmin senaryosunda, bir TAXI arttırıldığında 'nın maliyeti tahmin ediliyor. Bu nedenle, **fare_amount** etikettir. `features`, Modeli tahmin etmek için size izin verdiğiniz girişlerdir `label` . Bu durumda, **trip_time_in_secs** özel durumuna sahip sütunların geri kalanı, tarifeli havayolu tutarını tahmin etmek için özellik veya giriş olarak kullanılır.

## <a name="choose-a-scenario"></a>Senaryo seçin

Modelinize eğitebilmeniz için, model Oluşturucu tarafından sağlanan kullanılabilir makine öğrenimi senaryoları listesinden seçim yapmanız gerekir. Bu durumda senaryo `Price Prediction` .

1. **Çözüm Gezgini**, *taxifaretahmin* projesine sağ tıklayın ve Machine Learning Ekle ' yi seçin   >  .
1. Model Oluşturucu aracının senaryo adımında *fiyat tahmini* senaryosu ' nı seçin.

## <a name="load-the-data"></a>Verileri yükleme

Model Oluşturucu, bir SQL Server veritabanı veya CSV ya da TSV biçimindeki yerel bir dosya olan iki kaynaktan verileri kabul eder.

1. Model Oluşturucu aracının veri adımında, veri kaynağı açılır listesinden *Dosya* ' yı seçin.
1. *Dosya Seç* metin kutusunun yanındaki düğmeyi seçin ve *veri* dizinindeki *taxi-fare-test.csv* taramak ve seçmek için dosya Gezgini 'ni kullanın
1. *Tahmin edilecek (etiket) açılan sütundaki* *fare_amount* seçin.
1. *Giriş sütunları (Özellikler)* açılır listesini genişletin ve eğitim sırasında bir özellik olarak dışlamak için *trip_time_in_secs* sütununun işaretini kaldırın.  Model Oluşturucu aracının eğitme adımına gidin.

## <a name="train-the-model"></a>Modeli eğitme

Bu öğreticide fiyat tahmin modelini eğitmek için kullanılan makine öğrenimi görevi gerileme. Model oluşturma işlemi sırasında model Oluşturucu, veri kümeniz için en iyi işlem modelini bulmak üzere farklı gerileme algoritmaları ve ayarları kullanarak modelleri ayrı ayrı işler.

Modelin eğitilmesi için gereken süre, veri miktarına müşterinizin istekleriyle orantılı. Model Oluşturucu, veri kaynağınızın boyutuna bağlı olarak, **tren süresi (saniye)** için varsayılan bir değer seçer.

1. Daha uzun bir süre eğmemeyi tercih etmediğiniz sürece varsayılan değeri *eğitme süresi (saniye)* olarak bırakın.
2. *Eğitimi Başlat*' ı seçin.

Eğitim süreci boyunca, ilerleme verileri `Progress` eğitme adımının bölümünde görüntülenir.

- Durum, eğitim sürecinin tamamlanma durumunu görüntüler.
- En iyi doğruluk, şu ana kadar model Oluşturucu tarafından bulunan en iyi şekilde oluşan modelin doğruluğunu gösterir. Daha yüksek doğruluk, modelin test verilerinde daha doğru tahmin edilen anlamına gelir.
- En iyi algoritma, şu ana kadar model Oluşturucu tarafından bulunan en iyi şekilde gerçekleştirilen algoritmanın adını görüntüler.
- Son algoritma modeli eğitmek için model Oluşturucu tarafından en son kullanılan algoritmanın adını görüntüler.

Eğitim tamamlandıktan sonra değerlendir adımına gidin.

## <a name="evaluate-the-model"></a>Modeli değerlendirme

Eğitim adımının sonucu, en iyi performansa sahip bir model olacaktır. Model Oluşturucu aracının değerlendir adımında, çıkış *bölümü en iyi model girişinde en* iyi işlem modeli tarafından kullanılan algoritmayı *(RKARE)* içerir. Ayrıca, ilk beş modeli ve bunların ölçümlerini içeren bir Özet tablosu.

Doğruluk ölçümlerinizi tatmin ediyorsanız, model doğruluğunu denemeye yönelik bazı kolay yollar, modelin eğilmesi veya daha fazla veri kullanmak için zaman miktarını artırmaktır. Aksi takdirde, kod adımına gidin.

## <a name="add-the-code-to-make-predictions"></a>Tahminleri yapmak için kodu ekleyin

Eğitim sürecinin bir sonucu olarak iki proje oluşturulacaktır.

- TaxiFarePredictionML. ConsoleApp: model eğitimi ve örnek tüketim kodu içeren bir .NET Core konsol uygulaması.
- TaxiFarePredictionML. Model: giriş ve çıkış modeli verilerinin şemasını tanımlayan veri modellerini, eğitim sırasında en iyi gerçekleştirme modelinin kaydedilmiş sürümünü ve tahmin yapmak için çağrılan bir yardımcı sınıfı içeren .NET Standard bir sınıf kitaplığı `ConsumeModel` .

1. Model Oluşturucu aracının kod adımında, otomatik olarak oluşturulan projeleri çözüme eklemek için **Proje Ekle** ' yi seçin.
1. *Taxifaretahmin* projesinde *program. cs* dosyasını açın.
1. *TaxiFarePredictionML. model* projesine başvurmak için aşağıdaki using ifadesini ekleyin:

    ```csharp
    using System;
    using TaxiFarePredictionML.Model;
    ```

1. Modeli kullanarak yeni verileri tahmin etmek için, `ModelInput` uygulamanızın yöntemi içinde sınıfın yeni bir örneğini oluşturun `Main` . Tarifeli havayolu tutarının girişin bir parçası olmadığına dikkat edin. Bunun nedeni, modelin tahmin oluşturması olacaktır.

    ```csharp
    // Create sample data
    ModelInput input = new ModelInput()
    {
        Vendor_id = "CMT",
        Rate_code = 1,
        Passenger_count = 1,
        Trip_distance = 3.8f,
        Payment_type = "CRD"
    };
    ```

1. `Predict`Sınıfından yöntemi kullanın `ConsumeModel` . `Predict`Yöntemi, eğitilen modeli yükler, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) model için oluşturun ve yeni verilerde tahmine dayalı hale getirmek için onu kullanır.

    ```csharp
    // Make prediction
    ModelOutput prediction = ConsumeModel.Predict(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

1. Uygulamayı çalıştırın.

    Program tarafından oluşturulan çıkış aşağıdaki kod parçacığına benzemelidir:

    ```bash
    Predicted Fare: 14.96086
    ```

Oluşturulan projelere başka bir çözümün içinde daha sonraki bir zamanda başvurmanız gerekirse, bunları dizin içinde bulabilirsiniz `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` .

## <a name="next-steps"></a>Sonraki Adımlar

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> - Verileri hazırlama ve anlama
> - Senaryo seçin
> - Verileri yükleme
> - Modeli eğitme
> - Modeli değerlendirme
> - Tahmin için modeli kullanma

### <a name="additional-resources"></a>Ek Kaynaklar

Bu öğreticide bahsedilen konular hakkında daha fazla bilgi edinmek için aşağıdaki kaynakları ziyaret edin:

- [Model Oluşturucu senaryoları](../automate-training-with-model-builder.md#scenario)
- [Regresyon](../resources/glossary.md#regression)
- [Regresyon modeli ölçümleri](../resources/metrics.md#evaluation-metrics-for-regression-and-recommendation)
- [NYC TLC TAXI seyahat veri kümesi](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
