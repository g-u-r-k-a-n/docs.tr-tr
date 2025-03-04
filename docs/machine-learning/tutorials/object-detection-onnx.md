---
title: 'Öğretici: ONNX derin öğrenme modeli kullanarak nesneleri algılama'
description: Bu öğreticide, görüntülerdeki nesneleri algılamak için ML.NET ' de önceden eğitilen ONNX derin öğrenme modelinin nasıl kullanılacağı gösterilmektedir.
author: luisquintanilla
ms.author: luquinta
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 305a440634120395dba6881584b2ff46646da211
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653588"
---
# <a name="tutorial-detect-objects-using-onnx-in-mlnet"></a>Öğretici: ML.NET 'de ONNX kullanarak nesneleri algılama

Görüntülerdeki nesneleri saptamak için ML.NET ' de önceden eğitilen bir ONNX modeli kullanmayı öğrenin.

Bir nesne algılama modelini sıfırdan eğitmek için milyonlarca parametre, büyük miktarda etiketli eğitim verisi ve çok miktarda bilgi işlem kaynağı (yüzlerce GPU saati) ayarlanması gerekir. Önceden eğitilen bir modelin kullanılması, eğitim sürecini kısayola etmenizi sağlar.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
> [!div class="checklist"]
>
> - Sorunu anlama
> - ONNX 'in ne olduğunu ve ML.NET ile nasıl çalıştığını öğrenin
> - Modeli anlama
> - Önceden eğitilen modeli yeniden kullanma
> - Yüklü bir modelle nesneleri Algıla

## <a name="pre-requisites"></a>Ön koşullar

- [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) veya üzeri ya da visual Studio 2017 sürüm 15,6 veya üzeri, ".NET Core platformlar arası geliştirme" iş yükü yüklendi.
- [Microsoft.ML NuGet paketi](https://www.nuget.org/packages/Microsoft.ML/)
- [Microsoft. ML. ımageanalytics NuGet paketi](https://www.nuget.org/packages/Microsoft.ML.ImageAnalytics/)
- [Microsoft. ML. OnnxTransformer NuGet paketi](https://www.nuget.org/packages/Microsoft.ML.OnnxTransformer/)
- [Küçük YOLOv2 önceden eğitilen model](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny-yolov2)
- [Netron](https://github.com/lutzroeder/netron) (isteğe bağlı)

## <a name="onnx-object-detection-sample-overview"></a>ONNX nesne algılama örneğine genel bakış

Bu örnek, önceden eğitilen derinlemesine öğrenme ONNX modelini kullanarak bir görüntüdeki nesneleri algılayan bir .NET Core konsol uygulaması oluşturur. Bu örneğin kodu, GitHub 'daki [DotNet/machinöğrenim-örnekleri deposunda](https://github.com/dotnet/machinelearning-samples/tree/main/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) bulunabilir.

## <a name="what-is-object-detection"></a>Nesne algılama nedir?

Nesne algılama bir bilgisayar vizyonu sorunudur. Görüntü sınıflandırmasıyla yakından ilgili olarak, nesne algılama görüntü sınıflandırmasını daha ayrıntılı bir ölçekte gerçekleştirir. Nesne algılama hem görüntüler içindeki varlıkları bulur _hem_ de kategorilere ayırır. Görüntüler farklı türlerde birden çok nesne içerdiğinde nesne algılamayı kullanın.

![Resim sınıflandırmasına karşı nesne sınıflandırmasına karşı ekran görüntüleri.](./media/object-detection-onnx/img-classification-obj-detection.png)

Nesne algılama için bazı kullanım örnekleri şunları içerir:

- Self-Driving otomobiller
- Robotics
- Yüz Algılama
- Çalışma alanı güvenliği
- Nesne sayımı
- Etkinlik tanıma

## <a name="select-a-deep-learning-model"></a>Derin öğrenme modeli seçin

Derin öğrenme, Machine Learning 'in bir alt kümesidir. Derin öğrenme modellerini eğmek için, büyük miktarlarda veri gerekir. Verilerdeki desenler, bir dizi katman tarafından temsil edilir. Verilerdeki ilişkiler, ağırlık içeren katmanlar arasında bağlantı olarak kodlanır. Ağırlığa göre daha güçlü olan ilişki. Toplu olarak, bu katman ve bağlantı serisi yapay sinir Networks olarak bilinir. Bir ağdaki daha fazla katman, "daha derin" ve bunu derin bir sinir ağı yapıyor.

Farklı türlerde sinir Networks, en yaygın çok katmanlı Perceptron (MLP), evsel sinir ağı (CNN) ve yinelenen sinir ağı (RNN). En temel, bir giriş kümesini bir çıktı kümesine eşleyen MLP 'dir. Bu sinir ağı, verilerin bir uzamsal veya zaman bileşeni olmadığında iyidir. CNN, veride bulunan uzamsal bilgileri işlemek için evsel katmanların kullanımını sağlar. CNNs için iyi bir kullanım örneği, bir görüntünün bölgesindeki bir özelliğin varlığını algılamak için görüntü işleme 'dir (örneğin, bir görüntünün merkezinde bir burun mu var?). Son olarak, RNNs durum veya belleğin girdi olarak kullanılmasına izin verir. RNNs, sıralı sıralama ve olayların bağlamı önemli olduğu zaman serisi analizi için kullanılır.

### <a name="understand-the-model"></a>Modeli anlama

Nesne algılama bir görüntü işleme görevidir. Bu nedenle, bu sorunu çözmek için eğitilen çoğu derin öğrenme modeli CNNs ' dir. Bu öğreticide kullanılan model, YOLOv2 modelinin ["YOLO9000: daha iyi, daha hızlı, daha güçlü", Redmon ve Farhadi tarafından](https://arxiv.org/pdf/1612.08242.pdf)tanımlanan daha kompakt bir sürümü olan küçük YOLOv2 modelidir. Küçük YOLOv2, Pascal VOC veri kümesi üzerinde eğitilir ve 20 farklı nesne sınıfı tahmin edebilen 15 katmandan oluşur. Küçük YOLOv2 özgün YOLOv2 modelinin sıkıştırılmış bir sürümü olduğundan, hız ve doğruluk arasında bir zorunluluğunu getirir yapılır. Modeli oluşturan farklı katmanlar netron gibi araçlar kullanılarak görselleştirilir. Modelin araştırılama, her katmanın, ilgili giriş/çıkış boyutlarıyla birlikte katman adını içerdiği sinir ağını oluşturan tüm katmanlar arasında bağlantı eşlemesini elde edecektir. Modelin girişlerini ve çıkışlarını tanımlamakta kullanılan veri yapıları, teniler olarak bilinir. Teniler, verileri N boyutlu bir şekilde depolayan kapsayıcılar olarak düşünülebilir. Küçük YOLOv2 durumunda, giriş katmanının adı olur `image` ve bir boyut gerektirir `3 x 416 x 416` . Çıktı katmanının adı olur `grid` ve boyutların bir çıkış eğilimi oluşturur `125 x 13 x 13` .

![Gizli katmanlara bölünmekte olan giriş katmanı, çıkış katmanı](./media/object-detection-onnx/netron-model-map-layers.png)

YOLO modeli bir görüntü alır `3(RGB) x 416px x 416px` . Model bu girişi alır ve bir çıktı üretmek için farklı katmanlardan geçirir. Çıktı, giriş görüntüsünü `13 x 13` kılavuzdaki her hücreyle değerleri içeren bir kılavuza böler `125` .

### <a name="what-is-an-onnx-model"></a>ONNX modeli nedir?

Open sinir Network Exchange (ONNX), AI modelleri için açık kaynak biçimidir. ONNX çerçeveler arasında birlikte çalışabilirliği destekler. Bu, bir modeli PyTorch gibi birçok popüler makine öğrenimi çerçevelerinden birinde eğitebileceğiniz anlamına gelir, ONNX biçimine dönüştürebilir ve ML.NET gibi farklı bir çerçevede ONNX modelini kullanabilirsiniz. Daha fazla bilgi edinmek için [Onnx Web sitesini](https://onnx.ai/)ziyaret edin.

![Kullanılan ONNX desteklenen biçimlerin diyagramı.](./media/object-detection-onnx/onnx-supported-formats.png)

Önceden eğitilen küçük YOLOv2 modeli, katmanların serileştirilmiş bir gösterimi ve bu katmanların öğrenilen desenleri ile ONNX biçiminde depolanır. ML.NET ' de, ONNX ile birlikte çalışabilirlik, [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) ve [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) NuGet paketleriyle birlikte sağlanır. Paket, bir [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) görüntüyü alan ve bir tahmin veya eğitim işlem hattına giriş olarak kullanılabilecek sayısal değerlere kodlayan bir dizi dönüştürme içerir. Paket onnx [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) çalışma zamanından yararlanır ve belirtilen girişe göre tahmine dayalı hale getirmek için bu modeli kullanır.

![ONNX dosyasının ONNX çalışma zamanına veri akışı.](./media/object-detection-onnx/onnx-ml-net-integration.png)

## <a name="set-up-the-net-core-project"></a>.NET Core projesini ayarlama

Artık ONNX 'in ne olduğuna ve küçük YOLOv2 nasıl çalıştığına ilişkin genel bir bilgiye sahip olduğunuza göre, uygulamanın derlenmesi zaman vardır.

### <a name="create-a-console-application"></a>Konsol uygulaması oluşturma

1. "ObjectDetection" adlı bir **.NET Core konsol uygulaması** oluşturun.

1. **Microsoft.ml NuGet paketini** yükler:

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    - Çözüm Gezgini, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.
    - Paket kaynağı olarak "nuget.org" öğesini seçin, gözden geçirme sekmesini seçin, **Microsoft.ml** için arama yapın.
    - **Install** düğmesini seçin.
    - **Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.
    - **Microsoft. ml. ımageanalytics**, **Microsoft. ml. OnnxTransformer** ve **Microsoft. ml. onnxruntime** için bu adımları tekrarlayın.

### <a name="prepare-your-data-and-pre-trained-model"></a>Verilerinizi hazırlayın ve önceden eğitilen modeli

1. [Proje Varlıkları Dizin ZIP dosyasını](https://github.com/dotnet/machinelearning-samples/raw/main/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) indirin ve sıkıştırmayı açın.

1. `assets`Dizini *objectdetection* proje dizininize kopyalayın. Bu dizin ve alt dizinleri, bu öğretici için gerekli olan resim dosyalarını (küçük YOLOv2 modeli dışında, indirecek ve sonraki adımda ekleyeceğiniz) içerir.

1. [Onnx model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny-yolov2)ve unzip 'Ten [küçük YOLOv2 modelini](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) indirin.

    Komut istemi ' ni açın ve şu komutu girin:

    ```shell
    tar -xvzf tiny_yolov2.tar.gz
    ```

1. Ayıklanan `model.onnx` dosyayı Dizin Içinden *objectdetection* proje `assets\Model` dizininize kopyalayın ve olarak yeniden adlandırın `TinyYolo2_model.onnx` . Bu dizin, bu öğretici için gereken modeli içerir.

1. Çözüm Gezgini, varlık dizinindeki ve alt dizinlerde bulunan dosyaların her birine sağ tıklayın ve **Özellikler**' i seçin. **Gelişmiş**' in altında, **Çıkış Dizinine Kopyala** değerini **daha yeniyse kopyala** olarak değiştirin.

### <a name="create-classes-and-define-paths"></a>Sınıf oluşturma ve yollar tanımlama

*Program. cs* dosyasını açın ve aşağıdaki ek `using` deyimlerini dosyanın en üstüne ekleyin:

[!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L1-L7)]

Ardından, çeşitli varlıkların yollarını tanımlayın.

1. İlk olarak, yöntemi `GetAbsolutePath` sınıfındaki yönteminin altına ekleyin `Main` `Program` .

    [!code-csharp [GetAbsolutePath](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L66-L74)]

1. Ardından, yöntemi içinde `Main` varlıklarınızın konumunu depolamak için alanlar oluşturun.

    [!code-csharp [AssetDefinition](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L17-L21)]

Giriş verilerinizi ve tahmin sınıflarınızı depolamak için projenize yeni bir dizin ekleyin.

**Çözüm Gezgini**, projeye sağ tıklayın ve ardından   >  **Yeni klasör** Ekle ' yi seçin. Yeni klasör Çözüm Gezgini göründüğünde, "Datayapýlarý" olarak adlandırın.

Yeni oluşturulan *Datayapýlarý* dizininde giriş veri sınıfınızı oluşturun.

1. **Çözüm Gezgini**, *datayapýlarý* dizinine sağ tıklayıp   >  **Yeni öğe** Ekle ' yi seçin.
1. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *ımagenetdata. cs* olarak değiştirin. Sonra **Ekle** düğmesini seçin.

    *Imagenetdata. cs* dosyası kod düzenleyicisinde açılır. Aşağıdaki `using` Ifadeyi *Imagenetdata. cs*' nin üst kısmına ekleyin:

    [!code-csharp [ImageNetDataUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L1-L4)]

    Mevcut sınıf tanımını kaldırın ve sınıf için aşağıdaki kodu `ImageNetData` *ımagenetdata. cs* dosyasına ekleyin:

    [!code-csharp [ImageNetDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L8-L23)]

    `ImageNetData` , giriş resmi veri sınıfıdır ve aşağıdaki <xref:System.String> alanlara sahiptir:

    - `ImagePath` görüntünün depolandığı yolu içerir.
    - `Label` dosyanın adını içerir.

    Ayrıca, `ImageNetData` `ReadFromFile` belirtilen yolda depolanan birden çok resim dosyasını yükleyen `imageFolder` ve bunları bir nesne koleksiyonu olarak döndüren bir yöntemi içerir `ImageNetData` .

*Veri yapıları* dizininde tahmin sınıfınızı oluşturun.

1. **Çözüm Gezgini**, *datayapýlarý* dizinine sağ tıklayıp   >  **Yeni öğe** Ekle ' yi seçin.
1. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *ımagenettahmine. cs* olarak değiştirin. Sonra **Ekle** düğmesini seçin.

    *Imagenettahminini. cs* dosyası kod düzenleyicisinde açılır. Aşağıdaki `using` Ifadeyi *ımagenettahmine. cs*' nin üst kısmına ekleyin:

    [!code-csharp [ImageNetPredictionUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L1)]

    Mevcut sınıf tanımını kaldırın ve sınıf için aşağıdaki kodu `ImageNetPrediction` *ımagenettahmine. cs* dosyasına ekleyin:

    [!code-csharp [ImageNetPredictionClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L5-L9)]

    `ImageNetPrediction` , tahmin verileri sınıfıdır ve şu `float[]` alana sahiptir:

    - `PredictedLabel` görüntüde algılanan her bir sınırlayıcı kutu için boyutları, objectlik Puanını ve sınıf olasılıkları içerir.

### <a name="initialize-variables-in-main"></a>Değişkenleri ana olarak Başlat

[Mlcontext sınıfı](xref:Microsoft.ML.MLContext) tüm ml.NET işlemleri için bir başlangıç noktasıdır ve başlatılıyor, `mlContext` model oluşturma iş akışı nesneleri genelinde paylaşılabilen yeni bir ml.net ortamı oluşturur. Entity Framework, kavramsal olarak da benzerdir `DBContext` .

`mlContext` `MLContext` Aşağıdaki satırı, `Main` alanının altındaki *program. cs* yöntemine ekleyerek değişkeni yeni bir örneğiyle başlatın `outputFolder` .

[!code-csharp [InitMLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L24)]

## <a name="create-a-parser-to-post-process-model-outputs"></a>İşlem sonrası model çıkışları için bir Ayrıştırıcı oluşturun

Model, `13 x 13` her kılavuz hücresinin bulunduğu bir görüntüyü kılavuza böler `32px x 32px` . Her kılavuz hücresi, 5 olası nesne sınırlayıcı kutusu içerir. Bir sınırlayıcı kutusunda 25 öğe vardır:

![Sol taraftaki kılavuz örneği ve sağ taraftaki sınırlayıcı kutu örneği](./media/object-detection-onnx/model-output-description.png)

- `x` sınırlama kutusu merkezinin ilişkilendirildiği kılavuz hücresine göre x konumu.
- `y` sınırlama kutusu merkezinin ilişkilendirildiği kılavuz hücresine göre y konumu.
- `w` sınırlayıcı kutunun genişliği.
- `h` sınırlayıcı kutunun yüksekliği.
- `o` bir nesnenin, sınırlayıcı kutusunda bulunduğu güven değeri, aynı zamanda objectlik puanı olarak da bilinir.
- `p1-p20` model tarafından tahmin edilen 20 sınıfın her biri için sınıf olasılıkların.

Toplamda, 5 sınırlayıcı kutulardan her birini tanımlayan 25 öğe, her kılavuz hücresinde bulunan 125 öğelerini yapar.

Önceden eğitilen ONNX modeli tarafından oluşturulan çıkış, `21125` boyutlarla birlikte bir ön sor öğelerinin öğelerini temsil eden bir float dizisidir `125 x 13 x 13` . Model tarafından oluşturulan tahminleri bir tencursor 'a dönüştürmek için bazı işleme sonrası işler gereklidir. Bunu yapmak için, çıktıyı ayrıştırmaya yardımcı olmak üzere bir sınıf kümesi oluşturun.

Ayrıştırıcı sınıfları kümesini düzenlemek için projenize yeni bir dizin ekleyin.

1. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından   >  **Yeni klasör** Ekle ' yi seçin. Yeni klasör Çözüm Gezgini göründüğünde, "YoloParser" olarak adlandırın.

### <a name="create-bounding-boxes-and-dimensions"></a>Sınırlayıcı kutular ve boyutlar oluşturma

Modelin veri çıktısı, görüntü içindeki nesnelerin sınırlayıcı kutularının koordinatlarını ve boyutlarını içerir. Boyutlar için bir temel sınıf oluşturun.

1. **Çözüm Gezgini**, *yoloparser* dizinine sağ tıklayın ve sonra   >  **Yeni öğe** Ekle ' yi seçin.
1. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *dimensionsbase. cs* olarak değiştirin. Sonra **Ekle** düğmesini seçin.

    *Dimensionsbase. cs* dosyası kod düzenleyicisinde açılır. Tüm `using` deyimlerini ve varolan sınıf tanımını kaldırın.

    Sınıfı için aşağıdaki kodu `DimensionsBase` *Dimensionsbase. cs* dosyasına ekleyin:

    [!code-csharp [DimensionsBaseClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/DimensionsBase.cs#L3-L9)]

    `DimensionsBase` aşağıdaki özelliklere sahiptir `float` :

    - `X` nesnenin x ekseni üzerindeki konumunu içerir.
    - `Y` nesnenin y ekseni üzerinde konumunu içerir.
    - `Height` nesnenin yüksekliğini içerir.
    - `Width` nesnenin genişliğini içerir.

Ardından, sınırlayıcı kutularınız için bir sınıf oluşturun.

1. **Çözüm Gezgini**, *yoloparser* dizinine sağ tıklayın ve sonra   >  **Yeni öğe** Ekle ' yi seçin.
1. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *yoloboundingbox. cs* olarak değiştirin. Sonra **Ekle** düğmesini seçin.

    *Yoloboundingbox. cs* dosyası kod düzenleyicisinde açılır. Aşağıdaki `using` Ifadeyi *Yoloboundingbox. cs*' nin üst kısmına ekleyin:

    [!code-csharp [YoloBoundingBoxUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L1)]

    Mevcut sınıf tanımının hemen üzerinde, `BoundingBoxDimensions` `DimensionsBase` ilgili sınırlayıcı kutusunun boyutlarını içerecek şekilde sınıfından devralan adlı yeni bir sınıf tanımı ekleyin.

    [!code-csharp [BoundingBoxDimClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L5)]

    Mevcut `YoloBoundingBox` sınıf tanımını kaldırın ve sınıf için aşağıdaki kodu `YoloBoundingBox` *Yoloboundingbox. cs* dosyasına ekleyin:

    [!code-csharp [YoloBoundingBoxClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L7-L21)]

    `YoloBoundingBox` aşağıdaki özelliklere sahiptir:

    - `Dimensions` sınırlayıcı kutunun boyutlarını içerir.
    - `Label` sınırlayıcı kutusunda algılanan nesne sınıfını içerir.
    - `Confidence` sınıfının güvenini içerir.
    - `Rect` sınırlayıcı kutunun boyutlarının dikdörtgen gösterimini içerir.
    - `BoxColor` görüntüde çizim yapmak için kullanılan ilgili sınıfla ilişkili rengi içerir.

### <a name="create-the-parser"></a>Ayrıştırıcı oluşturma

Artık boyut ve sınırlama kutuları için sınıflar oluşturuldığına göre, ayrıştırıcısı oluşturma zamanı.

1. **Çözüm Gezgini**, *yoloparser* dizinine sağ tıklayın ve sonra   >  **Yeni öğe** Ekle ' yi seçin.
1. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *yolooutputparser. cs* olarak değiştirin. Sonra **Ekle** düğmesini seçin.

    *Yolooutputparser. cs* dosyası kod düzenleyicisinde açılır. Aşağıdaki `using` Ifadeyi *Yolooutputparser. cs*' nin üst kısmına ekleyin:

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L1-L4)]

    Varolan `YoloOutputParser` sınıf tanımının içinde, görüntüdeki her bir hücrenin boyutlarını içeren bir iç içe sınıf ekleyin. Sınıf `CellDimensions` `DimensionsBase` tanımının en üstündeki sınıftan devralan sınıf için aşağıdaki kodu ekleyin `YoloOutputParser` .

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L10)]

1. `YoloOutputParser`Sınıf tanımı içinde, aşağıdaki sabitleri ve alanları ekleyin.

    [!code-csharp [ParserVarDefinitions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L12-L21)]

    - `ROW_COUNT` , görüntüdeki görüntünün bölüneceğini, ızgaradaki satır sayısıdır.
    - `COL_COUNT` , görüntüde bölünen, kılavuzdaki sütun sayısıdır.
    - `CHANNEL_COUNT` kılavuzun tek bir hücresinde bulunan toplam değer sayısıdır.
    - `BOXES_PER_CELL` , bir hücredeki sınırlayıcı kutuların sayısıdır,
    - `BOX_INFO_FEATURE_COUNT` , bir kutu içinde (x, y, Height, Width, güvenirlik) bulunan özelliklerin sayısıdır.
    - `CLASS_COUNT` , her bir sınırlayıcı kutusunda bulunan sınıf tahminleri sayısıdır.
    - `CELL_WIDTH` , görüntü kılavuzundaki bir hücrenin genişliğidir.
    - `CELL_HEIGHT` , görüntü kılavuzundaki bir hücrenin yüksekliğidir.
    - `channelStride` Kılavuzdaki geçerli hücrenin başlangıç konumudur.

    Model, Puanlama olarak da bilinen bir tahmin yaptığında, `416px x 416px` giriş görüntüsünü boyutunun bir hücre kılavuzuna böler `13 x 13` . Her hücre içerir `32px x 32px` . Her hücrede, 5 Özellik (x, y, Width, Height, güvenirlik) içeren 5 sınırlayıcı kutu vardır. Bunlara ek olarak, her bir sınırlayıcı kutu her bir sınıfın olasılığını içerir, bu durumda 20 olur. Bu nedenle, her hücre 125 bilgi parçasını içerir (5 özellik + 20 sınıf olasılıkların).

Tüm 5 sınırlayıcı kutular için aşağıdan bir çıpası listesi oluşturun `channelStride` :

[!code-csharp [ParserAnchors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L23-L26)]

Bağlayıcıların sınırlayıcı kutuların önceden tanımlanmış yükseklik ve genişlik oranları vardır. Bir model tarafından algılanan çoğu nesne veya sınıfın benzer oranları vardır. Bu, sınırlayıcı kutular oluşturmak için kullanışlıdır. Sınırlayıcı kutuları tahmin etmek yerine, önceden tanımlanmış boyutlardan olan fark, bu nedenle, sınırlayıcı kutuyu tahmin etmek için gereken hesaplamayı azaltmak için hesaplanır. Genellikle bu bağlantı oranları, kullanılan veri kümesi temel alınarak hesaplanır. Bu durumda, veri kümesi bilindiği ve değerler önceden hesaplandığından, bağlantılar sabit kodlanmış olabilir.

Ardından, modelin tahmin edecek etiketleri veya sınıfları tanımlayın. Bu model, özgün YOLOv2 modeli tarafından tahmin edilen toplam sınıf sayısının bir alt kümesi olan 20 sınıfı tahmin eder.

Altına etiket listenizi ekleyin `anchors` .

[!code-csharp [ParserLabels](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L28-L34)]

Sınıfların her biriyle ilişkili renkler vardır. Sınıf renklerinizi aşağıdaki gibi atayın `labels` :

[!code-csharp [ParserColors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L36-L59)]

### <a name="create-helper-functions"></a>Yardımcı işlevler oluşturma

İşleme sonrası aşamasında yer alan bir dizi adım vardır. Bu konuda yardımcı olmak için birkaç yardımcı yöntem kullanılabilir.

Ayrıştırıcı tarafından kullanılan yardımcı yöntemler şunlardır:

- `Sigmoid` 0 ile 1 arasında bir sayı çıkışı yapan sigmoıd işlevini uygular.
- `Softmax` bir giriş vektörünü bir olasılık dağıtımına normalleştirir.
- `GetOffset` tek boyutlu model çıkışındaki öğeleri bir tencursor içindeki ilgili konuma eşler `125 x 13 x 13` .
- `ExtractBoundingBoxes` Model çıktısından yöntemi kullanarak sınırlama kutusu boyutlarını ayıklar `GetOffset` .
- `GetConfidence` modelin bir nesne algıladığı ve `Sigmoid` bunu bir yüzdeye dönüştürmek için işlevini kullandığı emin olan güvenirlik değerini ayıklar.
- `MapBoundingBoxToCell` , sınırlayıcı kutu boyutlarını kullanır ve bunları görüntünün içindeki ilgili hücresiyle eşler.
- `ExtractClasses` yöntemi kullanarak model çıktısından sınırlama kutusu için sınıf tahminlerini ayıklar `GetOffset` ve yöntemi kullanarak bunları bir olasılık dağıtımına dönüştürür `Softmax` .
- `GetTopResult` en yüksek olasılığa sahip tahmin edilen sınıflar listesinden sınıfı seçer.
- `IntersectionOverUnion` daha düşük olasılıklara sahip sınırlayıcı kutuları filtreler.

Listenizin altındaki tüm yardımcı yöntemleri için kodu ekleyin `classColors` .

[!code-csharp [ParserHelperMethods](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L61-L151)]

Tüm yardımcı yöntemlerini tanımladıktan sonra, model çıkışını işlemek için bunları kullanma zamanı da vardır.

Yönteminin altında `IntersectionOverUnion` , `ParseOutputs` model tarafından oluşturulan çıktıyı işlemek için yöntemi oluşturun.

```csharp
public IList<YoloBoundingBox> ParseOutputs(float[] yoloModelOutputs, float threshold = .3F)
{

}
```

Sınırlayıcı kutularınızı depolamak ve yöntemin içinde değişkenleri tanımlamak için bir liste oluşturun `ParseOutputs` .

[!code-csharp [BBoxList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L155)]

Her resim bir hücre kılavuzuna bölünmüştür `13 x 13` . Her hücrede beş sınırlayıcı kutu bulunur. Değişkenin altında `boxes` , her hücrenin içindeki tüm kutuları işlemek için kod ekleyin.

```csharp
for (int row = 0; row < ROW_COUNT; row++)
{
    for (int column = 0; column < COL_COUNT; column++)
    {
        for (int box = 0; box < BOXES_PER_CELL; box++)
        {

        }
    }
}
```

En içteki döngünün içinde, tek boyutlu model çıkışı içindeki geçerli kutunun başlangıç konumunu hesaplayın.

[!code-csharp [ChannelDef](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L163)]

Doğrudan altında, `ExtractBoundingBoxDimensions` geçerli sınırlayıcı kutusunun boyutlarını almak için yöntemini kullanın.

[!code-csharp [GetBBoxDims](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L165)]

Ardından, `GetConfidence` geçerli sınırlayıcı kutusunun güvenini almak için yöntemini kullanın.

[!code-csharp [GetConfidence](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L167)]

Bundan sonra, `MapBoundingBoxToCell` geçerli sınırlayıcı kutuyu işlenmekte olan geçerli hücreyle eşlemek için yöntemini kullanın.

[!code-csharp [MapBoundingBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L169)]

Daha fazla işlem yapmadan önce, güven değerinin sağlanan eşikten büyük olup olmadığını kontrol edin. Aksi takdirde, sonraki sınırlayıcı kutuyu işleyin.

[!code-csharp [CheckThreshold1](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L171-L172)]

Aksi takdirde, çıktıyı işlemeye devam edin. Sonraki adımda, yöntemi kullanılarak geçerli sınırlayıcı kutu için öngörülen sınıfların olasılık dağılımı alınır `ExtractClasses` .

[!code-csharp [ExtractClasses](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L174)]

Daha sonra, `GetTopResult` Geçerli kutu için en yüksek olasılığa sahip sınıfın değerini ve dizinini almak ve Puanını hesaplamak için yöntemini kullanın.

[!code-csharp [GetTopResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L176-L177)]

' İ `topScore` bir kez daha kullanarak yalnızca belirtilen eşiğin üzerinde olan sınırlayıcı kutuları saklayın.

[!code-csharp [CheckThreshold2](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L179-L180)]

Son olarak, geçerli sınırlayıcı kutusu eşiği aşarsa, yeni bir `BoundingBox` nesne oluşturun ve `boxes` listeye ekleyin.

[!code-csharp [AddBBoxToList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L182-L194)]

Görüntüdeki tüm hücreler işlendikten sonra listeyi geri döndürün `boxes` . Aşağıdaki return ifadesini yöntemine en dıştaki for-Loop altına ekleyin `ParseOutputs` .

[!code-csharp [ReturnBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L198)]

### <a name="filter-overlapping-boxes"></a>Çakışan kutuları filtrele

Artık yüksek oranda uygun sınırlama kutularının tümü model çıktısından ayıklandığına göre, çakışan görüntüleri kaldırmak için ek filtrelemenin yapılması gerekir. Yönteminin altına adlı bir yöntem ekleyin `FilterBoundingBoxes` `ParseOutputs` :

```csharp
public IList<YoloBoundingBox> FilterBoundingBoxes(IList<YoloBoundingBox> boxes, int limit, float threshold)
{

}
```

Yöntemi içinde `FilterBoundingBoxes` , algılanan kutuların boyutuna eşit bir dizi oluşturarak ve tüm yuvaları etkin veya işleme hazırmış olarak işaretleyerek devre dışı bırakın.

[!code-csharp [InitActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L203-L207)]

Ardından, sınırlayıcı kutularınızı içeren listeyi güvenle azalan sırada sıralayın.

[!code-csharp [SortBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L209-L211)]

Bundan sonra filtrelenmiş sonuçları tutacak bir liste oluşturun.

[!code-csharp [InitFilterResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L213)]

Her bir sınırlayıcı kutunun her biri üzerinde yinelenerek her bir sınırlayıcı kutuyu işlemeye başlayın.

```csharp
for (int i = 0; i < boxes.Count; i++)
{

}
```

Bu for-döngüsünün içinde, geçerli sınırlayıcı kutusunun işlenip işlenemeyeceğini kontrol edin.

```csharp
if (isActiveBoxes[i])
{

}
```

Bu durumda, sınırlama kutusunu sonuçlar listesine ekleyin. Sonuçlar Ayıklanacak belirlenen kutu sınırını aşarsa döngüyü sonlandırın. Aşağıdaki kodu if-deyimin içine ekleyin.

[!code-csharp [AddFirstBBoxToResults](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L219-L223)]

Aksi takdirde, bitişik sınırlayıcı kutulara bakın. Aşağıdaki kodu Box limit denetiminin altına ekleyin.

```csharp
for (var j = i + 1; j < boxes.Count; j++)
{

}
```

İlk kutu gibi, bitişik kutu etkin veya işlenmek üzere hazırsanız, `IntersectionOverUnion` ilk kutunun ve ikinci kutunun belirtilen eşiği aşıp aşmadığını denetlemek için yöntemini kullanın. Aşağıdaki kodu en içteki for-loop ' a ekleyin.

[!code-csharp [IOUBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L227-L239)]

Bitişik sınırlayıcı kutuları denetleyen en büyük for-Loop dışında, işlenmek üzere kalan herhangi bir sınırlama kutusu olup olmadığına bakın. Aksi takdirde, için dış döngüden çıkar.

[!code-csharp [CheckActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L242-L243)]

Son olarak, yöntemin ilk döngüsü dışında, `FilterBoundingBoxes` sonuçları döndürün:

[!code-csharp [ReturnFilteredBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L246)]

Harika! Artık bu kodu Puanlama modeliyle birlikte kullanmanın zamanı.

## <a name="use-the-model-for-scoring"></a>Puanlama için modeli kullanma

İşlem sonrasında olduğu gibi, Puanlama adımlarında birkaç adım vardır. Bu konuda yardım almak için, projenize Puanlama mantığını içerecek bir sınıf ekleyin.

1. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından   >  **Yeni öğe** Ekle ' yi seçin.
1. **Yeni öğe Ekle** Iletişim kutusunda **sınıf** ' ı seçin ve **ad** alanını *OnnxModelScorer. cs* olarak değiştirin. Sonra **Ekle** düğmesini seçin.

    *OnnxModelScorer. cs* dosyası kod düzenleyicisinde açılır. Aşağıdaki `using` Ifadeyi *OnnxModelScorer. cs*' nin en üstüne ekleyin:

    [!code-csharp [ScorerUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L1-L7)]

    `OnnxModelScorer`Sınıf tanımı içinde aşağıdaki değişkenleri ekleyin.

    [!code-csharp [InitScorerVars](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L13-L17)]

    Doğrudan altında, `OnnxModelScorer` daha önce tanımlanmış değişkenleri başlatacak sınıf için bir Oluşturucu oluşturun.

    [!code-csharp [ScorerCtor](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L19-L24)]

    Oluşturucuyu oluşturduktan sonra, görüntü ve model ayarlarıyla ilgili değişkenleri içeren birkaç yapı tanımlayın. `ImageNetSettings`Model için girdi olarak beklenen yüksekliği ve genişliği içeren bir struct oluşturun.

    [!code-csharp [ImageNetSettingStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L26-L30)]

    Bundan sonra, `TinyYoloModelSettings` modelin giriş ve çıkış katmanlarının adlarını içeren adlı başka bir struct oluşturun. Modelin giriş ve çıkış katmanlarının adını görselleştirmek için, [netron](https://github.com/lutzroeder/netron)gibi bir araç kullanabilirsiniz.

    [!code-csharp [YoloSettingsStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L32-L43)]

    Ardından, Puanlama için kullanılan ilk yöntem kümesini oluşturun. `LoadModel`Sınıfınızın içindeki yöntemi oluşturun `OnnxModelScorer` .

    ```csharp
    private ITransformer LoadModel(string modelLocation)
    {

    }
    ```

    Yöntemi içinde `LoadModel` günlüğe kaydetmek için aşağıdaki kodu ekleyin.

    [!code-csharp [LoadModelLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L47-L49)]

    ML.NET işlem hatları, yöntemi çağrıldığında üzerinde çalışılacak veri şemasını bilmelidir [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit%2A) . Bu durumda, eğitimle benzer bir süreç kullanılacaktır. Ancak, hiçbir gerçek eğitim gerçekleşmediğinden boş kullanılması kabul edilebilir [`IDataView`](xref:Microsoft.ML.IDataView) . [`IDataView`](xref:Microsoft.ML.IDataView)Boş bir listeden işlem hattı için yeni bir oluştur.

    [!code-csharp [LoadEmptyIDV](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L52)]

    Bunun altında, işlem hattını tanımlayın. İşlem hattı dört dönüşümden oluşur.

    - [`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages%2A) görüntüyü bir bit eşlem olarak yükler.
    - [`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages%2A) görüntüyü belirtilen boyuta ölçeklendirin (Bu durumda, `416 x 416` ).
    - [`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels%2A) görüntünün piksel temsilini bir bit eşlemden sayısal bir Vector öğesine değiştirir.
    - [`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel%2A) ONNX modelini yükler ve belirtilen verileri öğrenmek için onu kullanır.

    İşlem hattınızı `LoadModel` değişkenin altındaki yöntemde tanımlayın `data` .

    [!code-csharp [ScoringPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L55-L58)]

    Şimdi Puanlama için model oluşturma zamanı. İşlem hattında [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit%2A) yöntemi çağırın ve daha fazla işleme için döndürün.

    [!code-csharp [FitReturnModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L61-L63)]

Model yüklendikten sonra tahmin yapmak için kullanılabilir. Bu işlemi kolaylaştırmak için yönteminin altında adlı bir yöntem oluşturun `PredictDataUsingModel` `LoadModel` .

```csharp
private IEnumerable<float[]> PredictDataUsingModel(IDataView testData, ITransformer model)
{

}
```

İçinde `PredictDataUsingModel` , günlüğe kaydetmek için aşağıdaki kodu ekleyin.

[!code-csharp [PredictDataLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L68-L71)]

Ardından, [`Transform`](xref:Microsoft.ML.ITransformer.Transform%2A) verileri öğrenmek için yöntemini kullanın.

[!code-csharp [ScoreImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L73)]

Tahmin edilen olasılıkların ayıklanmasını ayıklayın ve bunları ek işleme için geri döndürün.

[!code-csharp [ReturnModelOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L75-L77)]

Her iki adım de ayarlandığına göre, bunları tek bir yöntemde birleştirin. Yönteminin altında `PredictDataUsingModel` adlı yeni bir yöntem ekleyin `Score` .

[!code-csharp [ScoreMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L80-L85)]

Neredeyse bitti! Şimdi bunu tüm kullanıma yerleştirme zamanı.

## <a name="detect-objects"></a>Nesneleri Algıla

Tüm kurulumun tamamlandığına göre, bazı nesneleri algılamaya zaman atalım. *Program. cs* sınıfınıza scorer ve ayrıştırıcıya başvurular ekleyerek başlayın.

[!code-csharp [ReferenceScorerParser](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L8-L9)]

### <a name="score-and-parse-model-outputs"></a>Model çıkışlarını puan ve ayrıştırma

`Main` *Program. cs* sınıfınızın yöntemi içinde, bir try-catch ifadesini ekleyin.

```csharp
try
{

}
catch (Exception ex)
{
    Console.WriteLine(ex.ToString());
}
```

`try`Bloğun içinde, nesne algılama mantığını uygulamaya başlayın. İlk olarak, verileri bir öğesine yükleyin [`IDataView`](xref:Microsoft.ML.IDataView) .

[!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L29-L30)]

Ardından, bir örneği oluşturun `OnnxModelScorer` ve yüklenen verileri almak için onu kullanın.

[!code-csharp [ScoreData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L33-L36)]

Şimdi işleme sonrası adımının zamanı. Bir örneği oluşturun `YoloOutputParser` ve model çıkışını işlemek için onu kullanın.

[!code-csharp [ParsePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L39-L44)]

Model çıkışı işlendikten sonra, görüntülerde sınırlayıcı kutuları çizmeniz zaman alır.

### <a name="visualize-predictions"></a>Tahminleri görselleştirin

Model, görüntüleri puanladıktan ve çıktılar işlendikten sonra, görüntü üzerinde sınırlayıcı kutular çizmelidir. Bunu yapmak için, `DrawBoundingBox` `GetAbsolutePath` *program. cs* içindeki yönteminin altına adlı bir yöntem ekleyin.

```csharp
private static void DrawBoundingBox(string inputImageLocation, string outputImageLocation, string imageName, IList<YoloBoundingBox> filteredBoundingBoxes)
{

}
```

İlk olarak, görüntüyü yükleyin ve yöntemdeki yükseklik ve genişlik boyutlarını alın `DrawBoundingBox` .

[!code-csharp [LoadImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L78-L81)]

Ardından, model tarafından algılanan her bir sınırlayıcı kutu üzerinde yinelemek için her bir For-Each döngüsü oluşturun.

```csharp
foreach (var box in filteredBoundingBoxes)
{

}
```

For-each döngüsünün içinde, sınırlayıcı kutunun boyutlarını alın.

[!code-csharp [GetBBoxDimensions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L86-L89)]

Sınırlayıcı kutunun boyutları model girişine karşılık geldiğinden `416 x 416` , sınırlayıcı kutu boyutlarını görüntünün gerçek boyutuyla eşleşecek şekilde ölçeklendirin.

[!code-csharp [ScaleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L92-L95)]

Ardından, her bir sınırlayıcı kutusunun üzerinde görünecek metin için bir şablon tanımlayın. Metin, ilgili sınırlayıcı kutusunun içindeki nesnenin sınıfını ve güveni içerir.

[!code-csharp [DefineBBoxText](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L98)]

Görüntüde çizim yapmak için bir [`Graphics`](xref:System.Drawing.Graphics) nesneye dönüştürün.

```csharp
using (Graphics thumbnailGraphic = Graphics.FromImage(image))
{

}
```

`using`Kod bloğunun içinde, grafiğin [`Graphics`](xref:System.Drawing.Graphics) nesne ayarlarını ayarlayın.

[!code-csharp [TuneGraphicSettings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L102-L104)]

Bunun altında metin ve sınırlayıcı kutusu için yazı tipi ve renk seçeneklerini ayarlayın.

[!code-csharp [SetColorOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L106-L114)]

Yöntemi kullanarak metni içermesi için sınırlayıcı kutunun üzerindeki bir dikdörtgeni oluşturun ve girin [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle%2A) . Bu, metnin karşıtlığına ve okunabilirliği iyileştirmenize yardımcı olur.

[!code-csharp [DrawTextBackground](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L117)]

Ardından, ve yöntemlerini kullanarak görüntüye metin ve sınırlayıcı kutusunu çizin [`DrawString`](xref:System.Drawing.Graphics.DrawString%2A) [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle%2A) .

[!code-csharp [DrawClassAndBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L118-L121)]

For-each döngüsünün dışında, içindeki görüntüleri kaydetmek için kod ekleyin `outputDirectory` .

[!code-csharp [SaveImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L125-L130)]

Uygulamanın çalışma zamanında beklendiği gibi tahmine dayalı hale getiren ek geri bildirimde bulunmak için, `LogDetectedObjects` `DrawBoundingBox` algılanan nesneleri konsola çıkarmak üzere *program. cs* dosyasındaki yönteminin altına adlı bir yöntem ekleyin.

[!code-csharp [LogOutputs](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L133-L143)]

Tahmine dayalı olarak görsel geri bildirim oluşturmaya yönelik yardımcı yöntemlere sahip olduğunuza göre, her bir puanlanmış görüntünün üzerinde yinelemek için bir for döngüsü ekleyin.

```csharp
for (var i = 0; i < images.Count(); i++)
{

}
```

For döngüsü içinde, görüntü dosyasının adını ve onunla ilişkili sınırlayıcı kutuları alın.

[!code-csharp [GetImageFileName](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L49-L50)]

Bunun altında, `DrawBoundingBox` görüntüdeki sınırlayıcı kutuları çizmek için yöntemini kullanın.

[!code-csharp [DrawBBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L52)]

Son olarak,, tahmine dayalı olarak `LogDetectedObjects` konsola çıkış yapmak için yöntemini kullanın.

[!code-csharp [LogPredictionsOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L54)]

Try-catch ifadesinden sonra, işlemin çalıştığını göstermek için ek mantık ekleyin.

[!code-csharp [EndProcessLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L62-L63)]

İşte bu kadar!

## <a name="results"></a>Sonuçlar

Önceki adımları uyguladıktan sonra konsol uygulamanızı çalıştırın (CTRL + F5). Sonuçlarınız aşağıdaki çıktıya benzer olmalıdır. Uyarıları veya işlem iletilerini görebilirsiniz, ancak bu iletiler netme için aşağıdaki sonuçlardan kaldırılmıştır.

```console
=====Identify the objects in the images=====

.....The objects in the image image1.jpg are detected as below....
car and its Confidence score: 0.9697262
car and its Confidence score: 0.6674225
person and its Confidence score: 0.5226039
car and its Confidence score: 0.5224892
car and its Confidence score: 0.4675332

.....The objects in the image image2.jpg are detected as below....
cat and its Confidence score: 0.6461141
cat and its Confidence score: 0.6400049

.....The objects in the image image3.jpg are detected as below....
chair and its Confidence score: 0.840578
chair and its Confidence score: 0.796363
diningtable and its Confidence score: 0.6056048
diningtable and its Confidence score: 0.3737402

.....The objects in the image image4.jpg are detected as below....
dog and its Confidence score: 0.7608147
person and its Confidence score: 0.6321323
dog and its Confidence score: 0.5967442
person and its Confidence score: 0.5730394
person and its Confidence score: 0.5551759

========= End of Process..Hit any Key ========
```

Sınırlayıcı kutuları olan görüntüleri görmek için `assets/images/output/` dizine gidin. Aşağıda, işlenen görüntülerden birindeki bir örnek verilmiştir.

![Bir dinleme odasının örnek işlenmiş görüntüsü](./media/object-detection-onnx/dinning-room-table-chairs.png)

Tebrikler! Artık ML.NET ' de önceden eğitilen bir modeli yeniden çalıştırarak nesne algılama için bir makine öğrenimi modelini başarıyla oluşturdunuz `ONNX` .

Bu öğreticinin kaynak kodunu [DotNet/machinöğrenim-örnekleri](https://github.com/dotnet/machinelearning-samples/tree/main/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) deposunda bulabilirsiniz.

Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:
> [!div class="checklist"]
>
> - Sorunu anlama
> - ONNX 'in ne olduğunu ve ML.NET ile nasıl çalıştığını öğrenin
> - Modeli anlama
> - Önceden eğitilen modeli yeniden kullanma
> - Yüklü bir modelle nesneleri Algıla

Genişletilmiş bir nesne algılama örneğini araştırmak için Machine Learning örnekleri GitHub deposuna göz atın.
> [!div class="nextstepaction"]
> [DotNet/machinöğrenim-Samples GitHub deposu](https://github.com/dotnet/machinelearning-samples/tree/main/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx)
