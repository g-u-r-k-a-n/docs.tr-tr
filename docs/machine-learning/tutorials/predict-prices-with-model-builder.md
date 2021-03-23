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
# <a name="tutorial-predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="a4a6f-103">Öğretici: model Oluşturucu ile gerileme kullanarak fiyatları tahmin etme</span><span class="sxs-lookup"><span data-stu-id="a4a6f-103">Tutorial: Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="a4a6f-104">Fiyatları tahmin etmek için bir gerileme modeli oluşturmak üzere ML.NET model Oluşturucu 'Yu nasıl kullanacağınızı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-104">Learn how to use ML.NET Model Builder to build a regression model to predict prices.</span></span>  <span data-ttu-id="a4a6f-105">Bu öğreticide geliştirdiğiniz .NET konsol uygulaması, geçmiş New York taksi tarifeli havayolu verilerine dayalı olarak taksi Fares 'yi tahmin eder.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="a4a6f-106">Model Oluşturucu fiyat tahmin şablonu, sayısal tahmin değeri gerektiren herhangi bir senaryo için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="a4a6f-107">Örnek senaryolar şunlardır: ev fiyat tahmini, talep tahmini ve satış tahmini.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="a4a6f-108">Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="a4a6f-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="a4a6f-109">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="a4a6f-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="a4a6f-110">Senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="a4a6f-110">Choose a scenario</span></span>
> - <span data-ttu-id="a4a6f-111">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="a4a6f-111">Load the data</span></span>
> - <span data-ttu-id="a4a6f-112">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="a4a6f-112">Train the model</span></span>
> - <span data-ttu-id="a4a6f-113">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="a4a6f-113">Evaluate the model</span></span>
> - <span data-ttu-id="a4a6f-114">Tahmin için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="a4a6f-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="a4a6f-115">Model Oluşturucu Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="a4a6f-116">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="a4a6f-116">Pre-requisites</span></span>

<span data-ttu-id="a4a6f-117">Önkoşul ve Yükleme yönergelerinin bir listesi için [model Oluşturucu Yükleme Kılavuzu](../how-to-guides/install-model-builder.md)' nu ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="a4a6f-118">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="a4a6f-118">Create a console application</span></span>

1. <span data-ttu-id="a4a6f-119">"Taxifaretahmine" adlı bir **C# .NET Core konsol uygulaması** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-119">Create a **C# .NET Core Console Application** called "TaxiFarePrediction".</span></span> <span data-ttu-id="a4a6f-120">**Çözümün ve projenin aynı dizine yerleştirdiğinizden** emin **olun (vs** 2019) veya **çözüm için dizin oluşturma** **denetlenir** (vs 2017).</span><span class="sxs-lookup"><span data-stu-id="a4a6f-120">Make sure **Place solution and project in the same directory** is **unchecked** (VS 2019), or **Create directory for solution** is **checked** (VS 2017).</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="a4a6f-121">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="a4a6f-121">Prepare and understand the data</span></span>

1. <span data-ttu-id="a4a6f-122">Veri kümesi dosyalarını depolamak için projenizde *veri* adlı bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-122">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="a4a6f-123">Machine Learning modelini eğmekte ve değerlendirmek için kullanılan veri kümesi, ilk olarak NYC TLC TAXI seyahat veri kümesinden.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-123">The data set used to train and evaluate the machine learning model is originally from the NYC TLC Taxi Trip data set.</span></span>

    1. <span data-ttu-id="a4a6f-124">Veri kümesini indirmek için [taxi-fare-train.csv indirme bağlantısına](https://raw.githubusercontent.com/dotnet/machinelearning/main/test/data/taxi-fare-train.csv)gidin.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-124">To download the data set, navigate to the [taxi-fare-train.csv download link](https://raw.githubusercontent.com/dotnet/machinelearning/main/test/data/taxi-fare-train.csv).</span></span>

    1. <span data-ttu-id="a4a6f-125">Sayfa yüklendiğinde, sayfada herhangi bir yere sağ tıklayın ve **farklı kaydet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-125">When the page loads, right-click anywhere on the page and select **Save as**.</span></span>

    1. <span data-ttu-id="a4a6f-126">Dosyayı önceki adımda oluşturduğunuz *veri* klasörüne kaydetmek Için **Farklı Kaydet iletişim kutusunu** kullanın.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-126">Use the **Save As Dialog** to save the file in the *Data* folder you created at the previous step.</span></span>

1. <span data-ttu-id="a4a6f-127">**Çözüm Gezgini**, *taxi-fare-train.csv* dosyasına sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-127">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="a4a6f-128">**Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala** olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-128">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="a4a6f-129">Veri kümesindeki her satır `taxi-fare-train.csv` bir TAXI tarafından yapılan gelişlerin ayrıntılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-129">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span>

1. <span data-ttu-id="a4a6f-130">**taxi-fare-train.csv** veri kümesini aç</span><span class="sxs-lookup"><span data-stu-id="a4a6f-130">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="a4a6f-131">Belirtilen veri kümesi şu sütunları içerir:</span><span class="sxs-lookup"><span data-stu-id="a4a6f-131">The provided data set contains the following columns:</span></span>

    - <span data-ttu-id="a4a6f-132">**vendor_id:** Taxı satıcısının KIMLIĞI bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-132">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    - <span data-ttu-id="a4a6f-133">**rate_code:** Taxı seyahati 'ın hız türü bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-133">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    - <span data-ttu-id="a4a6f-134">**passenger_count:** Seyahat üzerindeki pascuların sayısı bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-134">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    - <span data-ttu-id="a4a6f-135">**trip_time_in_secs:** Seyahati için geçen süre.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-135">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="a4a6f-136">Seyahat tamamlanmadan önce seyahat tarifeli havayolu tahmin etmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-136">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="a4a6f-137">Bu anda seyahati ne kadar süreyle yapılacağını bilemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-137">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="a4a6f-138">Bu nedenle, seyahat süresi bir özellik değildir ve bu sütunu modelden dışlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-138">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
    - <span data-ttu-id="a4a6f-139">**trip_distance:** Seyahat uzaklığı bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-139">**trip_distance:** The distance of the trip is a feature.</span></span>
    - <span data-ttu-id="a4a6f-140">**payment_type:** Ödeme yöntemi (nakit veya kredi kartı) bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-140">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    - <span data-ttu-id="a4a6f-141">**fare_amount:** Ödenen toplam TAXI tarifeli havayolu etikettir.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-141">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="a4a6f-142">`label`Tahmin etmek istediğiniz sütundur.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-142">The `label` is the column you want to predict.</span></span> <span data-ttu-id="a4a6f-143">Regresyon görevi gerçekleştirirken, amaç sayısal bir değeri tahmin etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-143">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="a4a6f-144">Bu fiyat tahmin senaryosunda, bir TAXI arttırıldığında 'nın maliyeti tahmin ediliyor.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-144">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="a4a6f-145">Bu nedenle, **fare_amount** etikettir.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-145">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="a4a6f-146">`features`, Modeli tahmin etmek için size izin verdiğiniz girişlerdir `label` .</span><span class="sxs-lookup"><span data-stu-id="a4a6f-146">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="a4a6f-147">Bu durumda, **trip_time_in_secs** özel durumuna sahip sütunların geri kalanı, tarifeli havayolu tutarını tahmin etmek için özellik veya giriş olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-147">In this case, the rest of the columns with the exception of **trip_time_in_secs** are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="a4a6f-148">Senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="a4a6f-148">Choose a scenario</span></span>

<span data-ttu-id="a4a6f-149">Modelinize eğitebilmeniz için, model Oluşturucu tarafından sağlanan kullanılabilir makine öğrenimi senaryoları listesinden seçim yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-149">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="a4a6f-150">Bu durumda senaryo `Price Prediction` .</span><span class="sxs-lookup"><span data-stu-id="a4a6f-150">In this case, the scenario is `Price Prediction`.</span></span>

1. <span data-ttu-id="a4a6f-151">**Çözüm Gezgini**, *taxifaretahmin* projesine sağ tıklayın ve Machine Learning Ekle ' yi seçin   >  .</span><span class="sxs-lookup"><span data-stu-id="a4a6f-151">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="a4a6f-152">Model Oluşturucu aracının senaryo adımında *fiyat tahmini* senaryosu ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-152">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="a4a6f-153">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="a4a6f-153">Load the data</span></span>

<span data-ttu-id="a4a6f-154">Model Oluşturucu, bir SQL Server veritabanı veya CSV ya da TSV biçimindeki yerel bir dosya olan iki kaynaktan verileri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-154">Model Builder accepts data from two sources, a SQL Server database or a local file in csv or tsv format.</span></span>

1. <span data-ttu-id="a4a6f-155">Model Oluşturucu aracının veri adımında, veri kaynağı açılır listesinden *Dosya* ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-155">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="a4a6f-156">*Dosya Seç* metin kutusunun yanındaki düğmeyi seçin ve *veri* dizinindeki *taxi-fare-test.csv* taramak ve seçmek için dosya Gezgini 'ni kullanın</span><span class="sxs-lookup"><span data-stu-id="a4a6f-156">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="a4a6f-157">*Tahmin edilecek (etiket) açılan sütundaki* *fare_amount* seçin.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-157">Choose *fare_amount* in the *Column to Predict (Label)* dropdown.</span></span>
1. <span data-ttu-id="a4a6f-158">*Giriş sütunları (Özellikler)* açılır listesini genişletin ve eğitim sırasında bir özellik olarak dışlamak için *trip_time_in_secs* sütununun işaretini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-158">Expand the *Input Columns (Features)* dropdown and uncheck the *trip_time_in_secs* column to exclude it as a feature during training.</span></span>  <span data-ttu-id="a4a6f-159">Model Oluşturucu aracının eğitme adımına gidin.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-159">Navigate to the train step of the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="a4a6f-160">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="a4a6f-160">Train the model</span></span>

<span data-ttu-id="a4a6f-161">Bu öğreticide fiyat tahmin modelini eğitmek için kullanılan makine öğrenimi görevi gerileme.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-161">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="a4a6f-162">Model oluşturma işlemi sırasında model Oluşturucu, veri kümeniz için en iyi işlem modelini bulmak üzere farklı gerileme algoritmaları ve ayarları kullanarak modelleri ayrı ayrı işler.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-162">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="a4a6f-163">Modelin eğitilmesi için gereken süre, veri miktarına müşterinizin istekleriyle orantılı.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-163">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="a4a6f-164">Model Oluşturucu, veri kaynağınızın boyutuna bağlı olarak, **tren süresi (saniye)** için varsayılan bir değer seçer.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-164">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="a4a6f-165">Daha uzun bir süre eğmemeyi tercih etmediğiniz sürece varsayılan değeri *eğitme süresi (saniye)* olarak bırakın.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-165">Leave the default value as is for *Time to train (seconds)* unless you prefer to train for a longer time.</span></span>
2. <span data-ttu-id="a4a6f-166">*Eğitimi Başlat*' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-166">Select *Start Training*.</span></span>

<span data-ttu-id="a4a6f-167">Eğitim süreci boyunca, ilerleme verileri `Progress` eğitme adımının bölümünde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-167">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="a4a6f-168">Durum, eğitim sürecinin tamamlanma durumunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-168">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="a4a6f-169">En iyi doğruluk, şu ana kadar model Oluşturucu tarafından bulunan en iyi şekilde oluşan modelin doğruluğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-169">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="a4a6f-170">Daha yüksek doğruluk, modelin test verilerinde daha doğru tahmin edilen anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-170">Higher accuracy means the model predicted more correctly on test data.</span></span>
- <span data-ttu-id="a4a6f-171">En iyi algoritma, şu ana kadar model Oluşturucu tarafından bulunan en iyi şekilde gerçekleştirilen algoritmanın adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-171">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="a4a6f-172">Son algoritma modeli eğitmek için model Oluşturucu tarafından en son kullanılan algoritmanın adını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-172">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="a4a6f-173">Eğitim tamamlandıktan sonra değerlendir adımına gidin.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-173">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="a4a6f-174">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="a4a6f-174">Evaluate the model</span></span>

<span data-ttu-id="a4a6f-175">Eğitim adımının sonucu, en iyi performansa sahip bir model olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-175">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="a4a6f-176">Model Oluşturucu aracının değerlendir adımında, çıkış *bölümü en iyi model girişinde en* iyi işlem modeli tarafından kullanılan algoritmayı *(RKARE)* içerir.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-176">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="a4a6f-177">Ayrıca, ilk beş modeli ve bunların ölçümlerini içeren bir Özet tablosu.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-177">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="a4a6f-178">Doğruluk ölçümlerinizi tatmin ediyorsanız, model doğruluğunu denemeye yönelik bazı kolay yollar, modelin eğilmesi veya daha fazla veri kullanmak için zaman miktarını artırmaktır.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-178">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="a4a6f-179">Aksi takdirde, kod adımına gidin.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-179">Otherwise, navigate to the code step.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="a4a6f-180">Tahminleri yapmak için kodu ekleyin</span><span class="sxs-lookup"><span data-stu-id="a4a6f-180">Add the code to make predictions</span></span>

<span data-ttu-id="a4a6f-181">Eğitim sürecinin bir sonucu olarak iki proje oluşturulacaktır.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-181">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="a4a6f-182">TaxiFarePredictionML. ConsoleApp: model eğitimi ve örnek tüketim kodu içeren bir .NET Core konsol uygulaması.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-182">TaxiFarePredictionML.ConsoleApp: A .NET Core Console application that contains the model training and sample consumption code.</span></span>
- <span data-ttu-id="a4a6f-183">TaxiFarePredictionML. Model: giriş ve çıkış modeli verilerinin şemasını tanımlayan veri modellerini, eğitim sırasında en iyi gerçekleştirme modelinin kaydedilmiş sürümünü ve tahmin yapmak için çağrılan bir yardımcı sınıfı içeren .NET Standard bir sınıf kitaplığı `ConsumeModel` .</span><span class="sxs-lookup"><span data-stu-id="a4a6f-183">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data, the saved version of the best performing model during training and a helper class called `ConsumeModel` to make predictions.</span></span>

1. <span data-ttu-id="a4a6f-184">Model Oluşturucu aracının kod adımında, otomatik olarak oluşturulan projeleri çözüme eklemek için **Proje Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-184">In the code step of the Model Builder tool, select **Add Projects** to add the auto-generated projects to the solution.</span></span>
1. <span data-ttu-id="a4a6f-185">*Taxifaretahmin* projesinde *program. cs* dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-185">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
1. <span data-ttu-id="a4a6f-186">*TaxiFarePredictionML. model* projesine başvurmak için aşağıdaki using ifadesini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a4a6f-186">Add the following using statement to reference the *TaxiFarePredictionML.Model* project:</span></span>

    ```csharp
    using System;
    using TaxiFarePredictionML.Model;
    ```

1. <span data-ttu-id="a4a6f-187">Modeli kullanarak yeni verileri tahmin etmek için, `ModelInput` uygulamanızın yöntemi içinde sınıfın yeni bir örneğini oluşturun `Main` .</span><span class="sxs-lookup"><span data-stu-id="a4a6f-187">To make a prediction on new data using the model, create a new instance of the `ModelInput` class inside the `Main` method of your application.</span></span> <span data-ttu-id="a4a6f-188">Tarifeli havayolu tutarının girişin bir parçası olmadığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-188">Notice that the fare amount is not part of the input.</span></span> <span data-ttu-id="a4a6f-189">Bunun nedeni, modelin tahmin oluşturması olacaktır.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-189">This is because the model will generate the prediction for it.</span></span>

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

1. <span data-ttu-id="a4a6f-190">`Predict`Sınıfından yöntemi kullanın `ConsumeModel` .</span><span class="sxs-lookup"><span data-stu-id="a4a6f-190">Use the `Predict` method from the `ConsumeModel` class.</span></span> <span data-ttu-id="a4a6f-191">`Predict`Yöntemi, eğitilen modeli yükler, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) model için oluşturun ve yeni verilerde tahmine dayalı hale getirmek için onu kullanır.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-191">The `Predict` method loads the trained model, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model and uses it to make predictions on new data.</span></span>

    ```csharp
    // Make prediction
    ModelOutput prediction = ConsumeModel.Predict(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

1. <span data-ttu-id="a4a6f-192">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a4a6f-192">Run the application.</span></span>

    <span data-ttu-id="a4a6f-193">Program tarafından oluşturulan çıkış aşağıdaki kod parçacığına benzemelidir:</span><span class="sxs-lookup"><span data-stu-id="a4a6f-193">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 14.96086
    ```

<span data-ttu-id="a4a6f-194">Oluşturulan projelere başka bir çözümün içinde daha sonraki bir zamanda başvurmanız gerekirse, bunları dizin içinde bulabilirsiniz `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` .</span><span class="sxs-lookup"><span data-stu-id="a4a6f-194">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a4a6f-195">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="a4a6f-195">Next Steps</span></span>

<span data-ttu-id="a4a6f-196">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="a4a6f-196">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="a4a6f-197">Verileri hazırlama ve anlama</span><span class="sxs-lookup"><span data-stu-id="a4a6f-197">Prepare and understand the data</span></span>
> - <span data-ttu-id="a4a6f-198">Senaryo seçin</span><span class="sxs-lookup"><span data-stu-id="a4a6f-198">Choose a scenario</span></span>
> - <span data-ttu-id="a4a6f-199">Verileri yükleme</span><span class="sxs-lookup"><span data-stu-id="a4a6f-199">Load the data</span></span>
> - <span data-ttu-id="a4a6f-200">Modeli eğitme</span><span class="sxs-lookup"><span data-stu-id="a4a6f-200">Train the model</span></span>
> - <span data-ttu-id="a4a6f-201">Modeli değerlendirme</span><span class="sxs-lookup"><span data-stu-id="a4a6f-201">Evaluate the model</span></span>
> - <span data-ttu-id="a4a6f-202">Tahmin için modeli kullanma</span><span class="sxs-lookup"><span data-stu-id="a4a6f-202">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a4a6f-203">Ek Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="a4a6f-203">Additional Resources</span></span>

<span data-ttu-id="a4a6f-204">Bu öğreticide bahsedilen konular hakkında daha fazla bilgi edinmek için aşağıdaki kaynakları ziyaret edin:</span><span class="sxs-lookup"><span data-stu-id="a4a6f-204">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="a4a6f-205">Model Oluşturucu senaryoları</span><span class="sxs-lookup"><span data-stu-id="a4a6f-205">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenario)
- [<span data-ttu-id="a4a6f-206">Regresyon</span><span class="sxs-lookup"><span data-stu-id="a4a6f-206">Regression</span></span>](../resources/glossary.md#regression)
- [<span data-ttu-id="a4a6f-207">Regresyon modeli ölçümleri</span><span class="sxs-lookup"><span data-stu-id="a4a6f-207">Regression Model Metrics</span></span>](../resources/metrics.md#evaluation-metrics-for-regression-and-recommendation)
- [<span data-ttu-id="a4a6f-208">NYC TLC TAXI seyahat veri kümesi</span><span class="sxs-lookup"><span data-stu-id="a4a6f-208">NYC TLC Taxi Trip data set</span></span>](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
