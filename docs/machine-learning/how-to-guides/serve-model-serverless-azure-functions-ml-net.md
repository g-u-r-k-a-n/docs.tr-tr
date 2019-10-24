---
title: Modeli Azure İşlevleri’ne dağıtma
description: Azure Işlevleri 'ni kullanarak Internet üzerinden tahmin için ML.NET yaklaşım analizi makine öğrenimi modelini sunar
ms.date: 09/12/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 4f805c638df9e60160c27fa08995ce393e59d007
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774524"
---
# <a name="deploy-a-model-to-azure-functions"></a><span data-ttu-id="95826-103">Modeli Azure İşlevleri’ne dağıtma</span><span class="sxs-lookup"><span data-stu-id="95826-103">Deploy a model to Azure Functions</span></span>

<span data-ttu-id="95826-104">Azure Işlevleri sunucusuz bir ortam aracılığıyla HTTP üzerinden tahmin için önceden eğitilen ML.NET makine öğrenimi modelini dağıtmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="95826-104">Learn how to deploy a pre-trained ML.NET machine learning model for predictions over HTTP through an Azure Functions serverless environment.</span></span>

> [!NOTE]
> <span data-ttu-id="95826-105">`PredictionEnginePool` hizmet uzantısı Şu anda önizleme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="95826-105">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="95826-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="95826-106">Prerequisites</span></span>

- <span data-ttu-id="95826-107">".NET Core platformlar arası geliştirme" iş yükü ve "Azure geliştirme" yüklü [Visual Studio 2017 sürüm 15,6 veya üzeri](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) .</span><span class="sxs-lookup"><span data-stu-id="95826-107">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload and "Azure development" installed.</span></span>
- <span data-ttu-id="95826-108">Microsoft. NET. SDK. Functions NuGet paketi sürüm 1.0.28 +.</span><span class="sxs-lookup"><span data-stu-id="95826-108">Microsoft.NET.Sdk.Functions NuGet Package version 1.0.28+.</span></span>
- [<span data-ttu-id="95826-109">Azure Işlevleri araçları</span><span class="sxs-lookup"><span data-stu-id="95826-109">Azure Functions Tools</span></span>](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- <span data-ttu-id="95826-110">PowerShell</span><span class="sxs-lookup"><span data-stu-id="95826-110">Powershell</span></span>
- <span data-ttu-id="95826-111">Önceden eğitilen model.</span><span class="sxs-lookup"><span data-stu-id="95826-111">Pre-trained model.</span></span> <span data-ttu-id="95826-112">Kendi modelinizi derlemek için [ML.NET yaklaşım Analizi öğreticisini](../tutorials/sentiment-analysis.md) kullanın veya bu [önceden eğitilen yaklaşım Analizi Machine Learning modelini](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip) indirin</span><span class="sxs-lookup"><span data-stu-id="95826-112">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="95826-113">Azure Işlevleri projesi oluştur</span><span class="sxs-lookup"><span data-stu-id="95826-113">Create Azure Functions project</span></span>

1. <span data-ttu-id="95826-114">Visual Studio 2017 ' i açın.</span><span class="sxs-lookup"><span data-stu-id="95826-114">Open Visual Studio 2017.</span></span> <span data-ttu-id="95826-115">Menü çubuğundan **dosya** > **Yeni** > **Proje** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-115">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="95826-116">**Yeni proje** iletişim kutusunda, **Visual C#**  düğümünü ve ardından **bulut** düğümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-116">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="95826-117">Ardından **Azure işlevleri** proje şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-117">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="95826-118">**Ad** metin kutusuna "SentimentAnalysisFunctionsApp" yazın ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-118">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="95826-119">**Yeni proje** iletişim kutusunda, proje seçeneklerinin üzerindeki açılan menüyü açın ve **Azure işlevleri v2 (.NET Core)** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="95826-119">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="95826-120">Ardından, **http tetikleyicisi** projesini seçin ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-120">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="95826-121">Modelinize kaydetmek için projenizde *Mlmodeller* adlı bir dizin oluşturun:</span><span class="sxs-lookup"><span data-stu-id="95826-121">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="95826-122">**Çözüm Gezgini**, projenize sağ tıklayın ve ardından  > **Yeni klasör** **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-122">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="95826-123">"Mlmodeller" yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="95826-123">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="95826-124">**Microsoft.ml NuGet paketini**yükler:</span><span class="sxs-lookup"><span data-stu-id="95826-124">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="95826-125">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-125">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="95826-126">Paket kaynağı olarak "nuget.org" öğesini seçin, araştır sekmesini seçin, **Microsoft.ml**için arama yapın, listeden bu paketi seçin ve sonra da **Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-126">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="95826-127">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-127">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="95826-128">**Microsoft. Azure. Functions. Extensions NuGet paketini**yükler:</span><span class="sxs-lookup"><span data-stu-id="95826-128">Install the **Microsoft.Azure.Functions.Extensions NuGet Package**:</span></span>

    <span data-ttu-id="95826-129">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-129">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="95826-130">Paket kaynağı olarak "nuget.org" öğesini seçin, gözden geçirme sekmesini seçin, **Microsoft. Azure. Functions. Extensions**araması yapın, listeden bu paketi seçin ve sonra da **Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-130">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Azure.Functions.Extensions**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="95826-131">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-131">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="95826-132">**Microsoft.Extensions.ml NuGet paketini**yükler:</span><span class="sxs-lookup"><span data-stu-id="95826-132">Install the **Microsoft.Extensions.ML NuGet Package**:</span></span>

    <span data-ttu-id="95826-133">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-133">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="95826-134">Paket kaynağı olarak "nuget.org" öğesini seçin, araştır sekmesini seçin, **Microsoft.Extensions.ml**için arama yapın, listeden bu paketi seçin ve sonra da **Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-134">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="95826-135">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-135">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="95826-136">**Microsoft. net. SDK. Functions NuGet paketini** 1.0.28 + sürümüne güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="95826-136">Update the **Microsoft.NET.Sdk.Functions NuGet Package** to version 1.0.28+:</span></span>

    <span data-ttu-id="95826-137">Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-137">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="95826-138">Paket kaynağı olarak "nuget.org" öğesini seçin, yüklü sekmesini seçin, **Microsoft. net. SDK. Functions**araması yapın, listeden bu paketi seçin, sürüm açılan menüsünde 1.0.28 veya üzeri ' i seçin ve **Güncelleştir** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-138">Choose "nuget.org" as the Package source, select the Installed tab, search for **Microsoft.NET.Sdk.Functions**, select that package in the list, select 1.0.28 or later from the Version dropdown, and select the **Update** button.</span></span> <span data-ttu-id="95826-139">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-trained-model-to-project"></a><span data-ttu-id="95826-140">Projeye önceden eğitilen Model Ekle</span><span class="sxs-lookup"><span data-stu-id="95826-140">Add pre-trained model to project</span></span>

1. <span data-ttu-id="95826-141">Önceden oluşturulmuş modelinizi *Mlmodeller* klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="95826-141">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="95826-142">Çözüm Gezgini, önceden oluşturulmuş model dosyanıza sağ tıklayıp **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-142">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="95826-143">**Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="95826-143">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-azure-function-to-analyze-sentiment"></a><span data-ttu-id="95826-144">Yaklaşımı çözümlemek için Azure Işlevi oluşturma</span><span class="sxs-lookup"><span data-stu-id="95826-144">Create Azure Function to analyze sentiment</span></span>

<span data-ttu-id="95826-145">Yaklaşımı tahmin etmek için bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="95826-145">Create a class to predict sentiment.</span></span> <span data-ttu-id="95826-146">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="95826-146">Add a new class to your project:</span></span>

1. <span data-ttu-id="95826-147">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından  > **Yeni öğe** **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-147">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="95826-148">**Yeni öğe Ekle** Iletişim kutusunda **Azure işlevi** ' ni seçin ve **ad** alanını *AnalyzeSentiment.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="95826-148">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="95826-149">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-149">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="95826-150">**Yeni Azure işlevi** Iletişim kutusunda **http tetikleyicisi**' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-150">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="95826-151">Ardından **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-151">Then, select the **OK** button.</span></span>

    <span data-ttu-id="95826-152">*AnalyzeSentiment.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="95826-152">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="95826-153">Aşağıdaki `using` ifadesini *AnalyzeSentiment.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="95826-153">Add the following `using` statement to the top of *AnalyzeSentiment.cs*:</span></span>

    [!code-csharp [AnalyzeUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L1-L11)]

    <span data-ttu-id="95826-154">Varsayılan olarak, `AnalyzeSentiment` sınıfı `static` ' dir.</span><span class="sxs-lookup"><span data-stu-id="95826-154">By default, the `AnalyzeSentiment` class is `static`.</span></span> <span data-ttu-id="95826-155">Sınıf tanımından `static` anahtar sözcüğünü kaldırdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="95826-155">Make sure to remove the `static` keyword from the class definition.</span></span>

    ```csharp
    public class AnalyzeSentiment
    {

    }
    ```

## <a name="create-data-models"></a><span data-ttu-id="95826-156">Veri modelleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="95826-156">Create data models</span></span>

<span data-ttu-id="95826-157">Giriş verileriniz ve tahminlerinizi için bazı sınıflar oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="95826-157">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="95826-158">Projenize yeni bir sınıf ekleyin:</span><span class="sxs-lookup"><span data-stu-id="95826-158">Add a new class to your project:</span></span>

1. <span data-ttu-id="95826-159">Projenizde veri modellerinizi kaydetmek için *datamodeller* adlı bir dizin oluşturun: Çözüm Gezgini, projenize sağ tıklayın ve **> yeni klasör ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-159">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="95826-160">"Datamodeller" yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="95826-160">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="95826-161">Çözüm Gezgini, *veri modelleri* dizinine sağ tıklayın ve sonra **> yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-161">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="95826-162">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *SentimentData.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="95826-162">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="95826-163">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-163">Then, select the **Add** button.</span></span>

    <span data-ttu-id="95826-164">*SentimentData.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="95826-164">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="95826-165">Aşağıdaki using ifadesini *SentimentData.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="95826-165">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp [SentimentDataUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L1)]

    <span data-ttu-id="95826-166">Mevcut sınıf tanımını kaldırın ve aşağıdaki kodu *SentimentData.cs* dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="95826-166">Remove the existing class definition and add the following code to the *SentimentData.cs* file:</span></span>

    [!code-csharp [SentimentData](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L5-L13)]

4. <span data-ttu-id="95826-167">Çözüm Gezgini, *veri modelleri* dizinine sağ tıklayın ve sonra **> yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-167">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="95826-168">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *SentimentPrediction.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="95826-168">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="95826-169">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-169">Then, select the **Add** button.</span></span> <span data-ttu-id="95826-170">*SentimentPrediction.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="95826-170">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="95826-171">Aşağıdaki using ifadesini *SentimentPrediction.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="95826-171">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    [!code-csharp [SentimentPredictionUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L1)]

    <span data-ttu-id="95826-172">Mevcut sınıf tanımını kaldırın ve aşağıdaki kodu *SentimentPrediction.cs* dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="95826-172">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    [!code-csharp [SentimentPrediction](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L5-L14)]

    <span data-ttu-id="95826-173">`SentimentPrediction`, `SentimentText` özelliğindeki özgün verilere ve model tarafından oluşturulan çıktıya erişim sağlayan `SentimentData` ' den devralır.</span><span class="sxs-lookup"><span data-stu-id="95826-173">`SentimentPrediction` inherits from `SentimentData` which provides access to the original data in the `SentimentText` property as well as the output generated by the model.</span></span>

## <a name="register-predictionenginepool-service"></a><span data-ttu-id="95826-174">PredictionEnginePool hizmetini Kaydet</span><span class="sxs-lookup"><span data-stu-id="95826-174">Register PredictionEnginePool service</span></span>

<span data-ttu-id="95826-175">Tek bir tahmin yapmak için bir [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="95826-175">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="95826-176">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) , iş parçacığı açısından güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="95826-176">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="95826-177">Ayrıca, uygulamanızın içinde gerek duyduğu her yerde bir örneği oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="95826-177">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="95826-178">Uygulamanız büyüdükçe, bu işlem yönetilebilir hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="95826-178">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="95826-179">Daha iyi performans ve iş parçacığı güvenliği için, uygulamanız genelinde kullanılmak üzere bir [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) nesnesi oluşturan bağımlılık ekleme ve `PredictionEnginePool` hizmeti birleşimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="95826-179">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

<span data-ttu-id="95826-180">Aşağıdaki bağlantı, [bağımlılık ekleme](https://en.wikipedia.org/wiki/Dependency_injection)hakkında daha fazla bilgi edinmek istiyorsanız daha fazla bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="95826-180">The following link provides more information if you want to learn more about [dependency injection](https://en.wikipedia.org/wiki/Dependency_injection).</span></span>

1. <span data-ttu-id="95826-181">**Çözüm Gezgini**, projeye sağ tıklayın ve ardından  > **Yeni öğe** **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-181">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="95826-182">**Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *Startup.cs*olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="95826-182">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *Startup.cs*.</span></span> <span data-ttu-id="95826-183">Sonra **Ekle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="95826-183">Then, select the **Add** button.</span></span>

    <span data-ttu-id="95826-184">*Startup.cs* dosyası kod düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="95826-184">The *Startup.cs* file opens in the code editor.</span></span> <span data-ttu-id="95826-185">Aşağıdaki using ifadesini *Startup.cs*öğesinin en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="95826-185">Add the following using statement to the top of *Startup.cs*:</span></span>

    ```csharp
    using Microsoft.Azure.Functions.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisFunctionsApp;
    using SentimentAnalysisFunctionsApp.DataModels;
    ```

    <span data-ttu-id="95826-186">Using deyimlerinin altındaki mevcut kodu kaldırın ve *Startup.cs* dosyasına aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="95826-186">Remove the existing code below the using statements and add the following code to the *Startup.cs* file:</span></span>

    ```csharp
    [assembly: FunctionsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        public class Startup : FunctionsStartup
        {
            public override void Configure(IFunctionsHostBuilder builder)
            {
                builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
                    .FromFile(modelName: "SentimentAnalysisModel", filePath:"MLModels/sentiment_model.zip", watchForChanges: true);
            }
        }
    }
    ```

<span data-ttu-id="95826-187">Yüksek düzeyde, bu kod, uygulama tarafından el ile yapmak yerine, daha sonra kullanmak üzere nesne ve hizmetleri otomatik olarak başlatır.</span><span class="sxs-lookup"><span data-stu-id="95826-187">At a high level, this code initializes the objects and services automatically for later use when requested by the application instead of having to manually do it.</span></span>

<span data-ttu-id="95826-188">Makine öğrenimi modelleri statik değildir.</span><span class="sxs-lookup"><span data-stu-id="95826-188">Machine learning models are not static.</span></span> <span data-ttu-id="95826-189">Yeni eğitim verileri kullanılabilir hale geldiğinde, model geri çekme ve yeniden dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="95826-189">As new training data becomes available, the model is retrained and redeployed.</span></span> <span data-ttu-id="95826-190">Bir modelin en son sürümünü uygulamanıza almanın bir yolu, uygulamanın tamamını yeniden dağıtmaktan biridir.</span><span class="sxs-lookup"><span data-stu-id="95826-190">One way to get the latest version of the model into your application is to redeploy the entire application.</span></span> <span data-ttu-id="95826-191">Ancak bu, uygulama kapalı kalma süresini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="95826-191">However, this introduces application downtime.</span></span> <span data-ttu-id="95826-192">@No__t_0 hizmeti, uygulamanızı kapatmak zorunda kalmadan güncelleştirilmiş bir modeli yeniden yükleme mekanizması sağlar.</span><span class="sxs-lookup"><span data-stu-id="95826-192">The `PredictionEnginePool` service provides a mechanism to reload an updated model without taking your application down.</span></span>

<span data-ttu-id="95826-193">@No__t_0 parametresini `true` olarak ayarlayın ve `PredictionEnginePool` dosya sistemi değişiklik bildirimlerini dinleyen ve dosyada değişiklik olduğunda olay başlatan bir [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) başlatır.</span><span class="sxs-lookup"><span data-stu-id="95826-193">Set the `watchForChanges` parameter to `true`, and the `PredictionEnginePool` starts a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) that listens to the file system change notifications and raises events when there is a change to the file.</span></span> <span data-ttu-id="95826-194">Bu, modeli otomatik olarak yeniden yüklemek için `PredictionEnginePool` ' a sorar.</span><span class="sxs-lookup"><span data-stu-id="95826-194">This prompts the `PredictionEnginePool` to automatically reload the model.</span></span>

<span data-ttu-id="95826-195">Model `modelName` parametresiyle tanımlanır, böylece değişiklik yapıldığında uygulama başına birden fazla model yeniden yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="95826-195">The model is identified by the `modelName` parameter so that more than one model per application can be reloaded upon change.</span></span>

> [!TIP]
> <span data-ttu-id="95826-196">Alternatif olarak, uzaktan depolanan modellerle çalışırken `FromUri` yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95826-196">Alternatively, you can use the `FromUri` method when working with models stored remotely.</span></span> <span data-ttu-id="95826-197">Dosya değiştirilen olayları izlemek yerine `FromUri`, uzak konumu değişiklikler için yoklar.</span><span class="sxs-lookup"><span data-stu-id="95826-197">Rather than watching for file changed events, `FromUri` polls the remote location for changes.</span></span> <span data-ttu-id="95826-198">Yoklama aralığı varsayılan olarak 5 dakikadır.</span><span class="sxs-lookup"><span data-stu-id="95826-198">The polling interval defaults to 5 minutes.</span></span> <span data-ttu-id="95826-199">Uygulama gereksinimlerine bağlı olarak yoklama aralığını artırabilir veya azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95826-199">You can increase or decrease the polling interval based on your application's requirements.</span></span> <span data-ttu-id="95826-200">Aşağıdaki kod örneğinde, `PredictionEnginePool` her dakikada belirtilen URI 'de depolanan modeli yoklar.</span><span class="sxs-lookup"><span data-stu-id="95826-200">In the code sample below, the `PredictionEnginePool` polls the model stored at the specified URI every minute.</span></span>
>
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="load-the-model-into-the-function"></a><span data-ttu-id="95826-201">Modeli işleve yükleme</span><span class="sxs-lookup"><span data-stu-id="95826-201">Load the model into the function</span></span>

<span data-ttu-id="95826-202">Aşağıdaki kodu, *çözümleyiciler* sınıfının içine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="95826-202">Insert the following code inside the *AnalyzeSentiment* class:</span></span>

[!code-csharp [AnalyzeCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L18-L24)]

<span data-ttu-id="95826-203">Bu kod, bağımlılığı ekleme yoluyla aldığınız işlevin oluşturucusuna geçirerek `PredictionEnginePool` ' a atar.</span><span class="sxs-lookup"><span data-stu-id="95826-203">This code assigns the `PredictionEnginePool` by passing it to the function's constructor which you get via dependency injection.</span></span>

## <a name="use-the-model-to-make-predictions"></a><span data-ttu-id="95826-204">Tahminleri yapmak için modeli kullanın</span><span class="sxs-lookup"><span data-stu-id="95826-204">Use the model to make predictions</span></span>

<span data-ttu-id="95826-205">*Çözümleyiciler* sınıfında bulunan *Run* yönteminin mevcut uygulamasını aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="95826-205">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

```csharp
[FunctionName("AnalyzeSentiment")]
public async Task<IActionResult> Run(
[HttpTrigger(AuthorizationLevel.Function, "post", Route = null)] HttpRequest req,
ILogger log)
{
    log.LogInformation("C# HTTP trigger function processed a request.");

    //Parse HTTP Request Body
    string requestBody = await new StreamReader(req.Body).ReadToEndAsync();
    SentimentData data = JsonConvert.DeserializeObject<SentimentData>(requestBody);

    //Make Prediction
    SentimentPrediction prediction = _predictionEnginePool.Predict(modelName: "SentimentAnalysisModel", example: data);

    //Convert prediction to string
    string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

    //Return Prediction
    return (ActionResult)new OkObjectResult(sentiment);
}
```

<span data-ttu-id="95826-206">@No__t_0 yöntemi yürütüldüğünde, HTTP isteğinden gelen veriler seri durumdan çıkarılacak ve `PredictionEnginePool` giriş olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="95826-206">When the `Run` method executes, the incoming data from the HTTP request is deserialized and used as input for the `PredictionEnginePool`.</span></span> <span data-ttu-id="95826-207">@No__t_0 yöntemi daha sonra, `Startup` sınıfına kayıtlı `SentimentAnalysisModel` kullanarak tahmine dayalı hale getirmek için çağrılır ve başarılı olursa sonuçları kullanıcıya geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="95826-207">The `Predict` method is then called to make predictions using the `SentimentAnalysisModel` registered in the `Startup` class and returns the results back to the user if successful.</span></span>

## <a name="test-locally"></a><span data-ttu-id="95826-208">Yerel olarak test etme</span><span class="sxs-lookup"><span data-stu-id="95826-208">Test locally</span></span>

<span data-ttu-id="95826-209">Her şey ayarlandığına göre, uygulamayı test etmek zaman alabilir:</span><span class="sxs-lookup"><span data-stu-id="95826-209">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="95826-210">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="95826-210">Run the application</span></span>
1. <span data-ttu-id="95826-211">PowerShell 'i açın ve kodu, uygulamanızın üzerinde çalıştığı bağlantı noktası olan bağlantı noktasının bulunduğu istemine girin.</span><span class="sxs-lookup"><span data-stu-id="95826-211">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="95826-212">Genellikle bağlantı noktası 7071 ' dir.</span><span class="sxs-lookup"><span data-stu-id="95826-212">Typically the port is 7071.</span></span>

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="95826-213">Başarılı olursa, çıkış aşağıdaki metne benzer görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="95826-213">If successful, the output should look similar to the text below:</span></span>

    ```powershell
    Negative
    ```

<span data-ttu-id="95826-214">Mühendisi!</span><span class="sxs-lookup"><span data-stu-id="95826-214">Congratulations!</span></span> <span data-ttu-id="95826-215">Azure Işlevi kullanarak, internet üzerinden tahmine dayalı hale getirmek için modelinizi başarıyla sundu.</span><span class="sxs-lookup"><span data-stu-id="95826-215">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="95826-216">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="95826-216">Next Steps</span></span>

- [<span data-ttu-id="95826-217">Azure’a dağıtma</span><span class="sxs-lookup"><span data-stu-id="95826-217">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)
