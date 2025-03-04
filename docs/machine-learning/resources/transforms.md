---
title: Veri dönüşümleri
description: ML.NET sürümünde desteklenen özellik Mühendisliği bileşenlerini gezin.
ms.date: 03/31/2021
ms.openlocfilehash: da03c738e268b8230e9f3bfd3c3919f64b5f5fc4
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122722"
---
# <a name="data-transformations"></a>Veri dönüşümleri

Veri dönüştürmeleri şu şekilde kullanılır:

- Model eğitimi için verileri hazırlama
- bir içeri aktarılan modeli TensorFlow veya ONNX biçiminde uygulama
- bir modelden geçtikten sonra işlem sonrası veriler

Bu kılavuzdaki dönüşümler, [ıestimator](xref:Microsoft.ML.IEstimator%601) arabirimini uygulayan sınıflar döndürüyor. Veri dönüştürmeleri birlikte zincirlenebilir. Her bir dönüşüm, bağlantılı başvuru belgelerinde belirtilen belirli tür ve biçimlerin verilerini bekler ve üretir.

Bazı veri dönüştürmeleri, parametrelerini hesaplamak için eğitim verileri gerektirir. Örneğin: transformatör, <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> işlem sırasında eğitim verilerinin ortalama ve varyansını hesaplar `Fit()` ve bu parametreleri `Transform()` işleminde kullanır.

Diğer veri dönüştürmeleri eğitim verileri gerektirmez. Örneğin: dönüştürme işlemi <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale%2A> `Transform()` sırasında herhangi bir eğitim verisi görünmeden işlemi gerçekleştirebilir `Fit()` .

## <a name="column-mapping-and-grouping"></a>Sütun eşleme ve gruplama

| Dönüşüm | Tanım | ONNX dışarı aktarılabilir |
| --- | --- | --- |
| <xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A> | Bir veya daha fazla giriş sütununu yeni bir çıktı sütununa birleştirme | Yes |
| <xref:Microsoft.ML.TransformExtensionsCatalog.CopyColumns%2A> | Bir veya daha fazla giriş sütununu kopyalama ve yeniden adlandırma | Yes |
| <xref:Microsoft.ML.TransformExtensionsCatalog.DropColumns%2A> | Bir veya daha fazla giriş sütununu bırakma | Yes |
| <xref:Microsoft.ML.TransformExtensionsCatalog.SelectColumns%2A> | Giriş verilerinden tutulacak bir veya daha fazla sütun seçin | Yes |

## <a name="normalization-and-scaling"></a>Normalleştirme ve ölçekleme

| Dönüşüm | Tanım | ONNX dışarı aktarılabilir |
| --- | --- | --- |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> | Ortalama (eğitim verileri) çıkarın ve varyansı (eğitim verileri) göre bölün | Yes |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLogMeanVariance%2A> | Eğitim verilerinin logaritmasını temel alarak normalleştirin | Yes |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLpNorm%2A> | Giriş vektörlerini [LP-norm](https://en.wikipedia.org/wiki/Lp_space#The_p-norm_in_finite_dimensions)olarak ölçeklendirin, p 1, 2 veya Infinity. Varsayılan değer L2 (Euclidea Distance) norm | Yes |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeGlobalContrast%2A> | Satır verilerinin ortalama değerini çıkararak bir satırdaki her değeri ölçeklendirin ve standart sapma veya L2-norm (satır verilerinin) ile bölün ve yapılandırılabilir bir ölçek faktörü (varsayılan 2) ile çarpın | Yes |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A> | Giriş değerini bir bin dizinine atayın ve 0 ile 1 arasında bir float değeri üretmek için bölme sayısına göre bölün. Bölme sınırları, eğitim verilerini depo gözleri arasında eşit olarak dağıtmak için hesaplanır |  Yes |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeSupervisedBinning%2A> | Etiket sütunuyla bağıntı temelinde bir sepete giriş değeri ata | Yes |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A> | Eğitim verilerinde minimum ve maksimum değerler arasındaki farka göre girişi ölçeklendirin | Yes |

## <a name="conversions-between-data-types"></a>Veri türleri arasındaki dönüşümler

| Dönüşüm | Tanım | ONNX dışarı aktarılabilir |
| --- | --- | --- |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.ConvertType%2A> | Giriş sütununun türünü yeni bir türe Dönüştür | Yes |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValue%2A> | Değerleri, eşlemelerin sağlanan sözlüğüne göre anahtarlar (kategoriler) ile eşleyin | No |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> | Giriş verilerinden eşleme oluşturarak değerleri anahtarlar (kategoriler) ile eşleyin | Yes |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A> | Anahtarları özgün değerlerine geri Dönüştür | Yes |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToVector%2A> | Anahtarları özgün değerlerin vektörlerine geri Dönüştür | Yes |
| <xref:Microsoft.ML.ConversionsCatalog.MapKeyToBinaryVector%2A> | Anahtarları özgün değerlerin ikili vektörüne geri Dönüştür | No |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A> | Giriş sütunundaki değeri karma olarak | Yes |

## <a name="text-transformations"></a>Metin dönüştürmeleri

| Dönüşüm | Tanım | ONNX dışarı aktarılabilir |
| --- | --- | --- |
| <xref:Microsoft.ML.TextCatalog.FeaturizeText%2A> | Metin sütununu normalleştirilmiş Ngram ve karakter-gram sayıları float dizisine Dönüştür | No |
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A> | Bir veya daha fazla metin sütununu tekil sözcüklere Böl | Yes |
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoCharactersAsKeys%2A> | Bir veya daha fazla metin sütununu bir konu kümesi üzerinde ayrı karakterlere böler | Yes |
| <xref:Microsoft.ML.TextCatalog.NormalizeText%2A> | Durumu değiştir, aksanlı işaretleri, noktalama işaretlerini ve sayıları kaldır | Yes |
| <xref:Microsoft.ML.TextCatalog.ProduceNgrams%2A> | Metin sütununu Ngram sayısı (ardışık sözcüklerin dizileri) için bir paket olarak Dönüştür| Yes |
| <xref:Microsoft.ML.TextCatalog.ProduceWordBags%2A> | Metin sütununu Ngram vektörü sayısı için bir paket olarak Dönüştür | No |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedNgrams%2A> | Metin sütununu karma Ngram sayımlarının vektörüne Dönüştür | No |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedWordBags%2A> | Metin sütununu karma Ngram sayımlarının bir torba Dönüştür | Yes |
| <xref:Microsoft.ML.TextCatalog.RemoveDefaultStopWords%2A>  | Giriş sütunlarından belirtilen dilin varsayılan durdurma sözcüklerini kaldır | Yes |
| <xref:Microsoft.ML.TextCatalog.RemoveStopWords%2A> | Giriş sütunlarından belirtilen durdurma sözcüklerini kaldırır | Yes |
| <xref:Microsoft.ML.TextCatalog.LatentDirichletAllocation%2A> | Bir belge (float vektörü olarak gösterilir), bir konu kümesi üzerinde kayan bir vektöre dönüştürme | Yes |
| <xref:Microsoft.ML.TextCatalog.ApplyWordEmbedding%2A> | Önceden eğitilen bir model kullanarak metin belirteçlerinin vektörlerini tümce vektörlerine dönüştürme | No |

## <a name="image-transformations"></a>Görüntü dönüşümleri

| Dönüşüm | Tanım | ONNX dışarı aktarılabilir |
| --- | --- | --- |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale%2A> | Bir görüntüyü gri tonlamaya Dönüştür | No |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToImage%2A> | Piksel vektörünü Dönüştür <xref:Microsoft.ML.Transforms.Image.ImageDataViewType> | No |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels%2A> | Giriş görüntüsünden pikselleri sayı vektörüne Dönüştür | No |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages%2A> | Bir klasörden belleğe görüntü yükleme | No |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages%2A> | Görüntüleri yeniden boyutlandırma | No |
| <xref:Microsoft.ML.OnnxCatalog.DnnFeaturizeImage%2A> | Bir giriş görüntüsünü Özellik vektörüne dönüştürmek için önceden eğitilen derin sinir ağı (DNN) modeli uygular | No |

## <a name="categorical-data-transformations"></a>Kategorik veri dönüştürmeleri

| Dönüşüm | Tanım | ONNX dışarı aktarılabilir |
| --- | --- | --- |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A> | Bir veya daha fazla metin sütununu [tek yönlü](https://en.wikipedia.org/wiki/One-hot) kodlanmış vektöre dönüştürme | Yes |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotHashEncoding%2A> | Bir veya daha fazla metin sütununu karma tabanlı tek başına kodlanmış vektöre dönüştürme | No |

## <a name="time-series-data-transformations"></a>Zaman serisi veri dönüştürmeleri

| Dönüşüm | Tanım | ONNX dışarı aktarılabilir |
| --- | --- | --- |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectAnomalyBySrCnn%2A> | Spectral artımı (SR) algoritmasını kullanarak giriş zamanı serisi verilerinde bozukluklar algılayın | No |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectChangePointBySsa%2A> | Tekil spekme Analizi (SSA) kullanarak zaman serisi verilerinde değişiklik noktalarını Algıla | No |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectIidChangePoint%2A> | Uyarlamalı Çekirdek yoğunluğu tahminleri ve Martingale puanlarını kullanarak bağımsız ve özdeş dağıtılmış (IID) zaman serisi verilerinde değişiklik noktalarını Algıla | No |
| <xref:Microsoft.ML.TimeSeriesCatalog.ForecastBySsa%2A> | Tekil spekme Analizi (SSA) kullanarak zaman serisi verilerini tahmin etme | No |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectSpikeBySsa%2A> | Tekil spekme Analizi (SSA) kullanarak zaman serisi verilerinde ani artışları Algıla | No |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectIidSpike%2A> | Uyarlamalı Çekirdek yoğunluğu tahminleri ve Martingale puanlarını kullanarak bağımsız ve özdeş dağıtılmış (IID) zaman serisi verilerinde artışlar Algıla | No |

## <a name="missing-values"></a>Eksik değerler

| Dönüşüm | Tanım | ONNX dışarı aktarılabilir |
| --- | --- | --- |
| <xref:Microsoft.ML.ExtensionsCatalog.IndicateMissingValues%2A> | Yeni bir Boole çıkış sütunu oluşturun, giriş sütunundaki değer eksik olduğunda true değerine sahip olur | Yes |
| <xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A> | Değer giriş sütununda eksikse, varsayılan değer olarak ayarlanan değeri, aksi takdirde giriş sütununda olmayan yeni bir çıkış sütunu oluşturun | Yes |

## <a name="feature-selection"></a>Özellik seçimi

| Dönüşüm | Tanım | ONNX dışarı aktarılabilir |
| --- | --- | --- |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnCount%2A> | Varsayılan olmayan değerleri eşikten büyük olan özellikleri seçin | Yes |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnMutualInformation%2A> | Etiket sütunundaki verilerin en bağlı olduğu özellikleri seçin | Yes |

## <a name="feature-transformations"></a>Özellik dönüşümleri

| Dönüşüm | Tanım | ONNX dışarı aktarılabilir |
| --- | --- | --- |
| <xref:Microsoft.ML.KernelExpansionCatalog.ApproximatedKernelMap%2A> | Her giriş vektörünü, iç ürünlerin bir çekirdek işlevini yaklaşık bir şekilde tahmin ettiği, bu sayede özelliklerin doğrusal algoritmalara giriş olarak kullanılabilmesi için, daha düşük boyutlu bir özellik alanı üzerine eşleyin | No |
| <xref:Microsoft.ML.PcaCatalog.ProjectToPrincipalComponents%2A> | Asıl bileşen çözümleme algoritmasını uygulayarak giriş özelliği vektörünün boyutlarını azaltma |

## <a name="explainability-transformations"></a>Explainability dönüşümler

| Dönüşüm | Tanım | ONNX dışarı aktarılabilir |
| --- | --- |  --- |
| <xref:Microsoft.ML.ExplainabilityCatalog.CalculateFeatureContribution%2A> | Bir özellik vektörünün her bir öğesi için katkı puanlarını hesaplama | No |

## <a name="calibration-transformations"></a>Ayarlama dönüşümleri

| Dönüşüm | Tanım | ONNX dışarı aktarılabilir |
| --- | --- |--- |
|<xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Platt%28System.String%2CSystem.String%2CSystem.String%29> | Eğitim verilerini kullanarak tahmini parametrelerle Lojistik gerileme kullanarak bir ikili sınıflandırıcının ham Puanını bir sınıf olasılığa dönüştürür | Yes |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Platt%28System.Double%2CSystem.Double%2CSystem.String%29> | Sabit parametrelerle Lojistik gerileme kullanarak bir ikili sınıflandırıcının ham Puanını bir sınıf olasılığa dönüştürür | Yes |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Naive%2A> | Bir ikili sınıflandırıcının ham Puanını, depo gözlerine puan atayarak bir sınıf olasılığa dönüştürür ve bu da depo gözleri arasındaki dağıtıma göre olasılığı hesaplıyor | Yes |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Isotonic%2A> | Bir ikili sınıflandırıcının ham Puanını, sınırların konumunun ve depo gözlerinin boyutunun eğitim verileri aracılığıyla tahmin edildiği yerlere puan atayarak bir sınıf olasılığa dönüştürür  | No |

## <a name="deep-learning-transformations"></a>Derin öğrenme dönüşümleri

| Dönüşüm | Tanım | ONNX dışarı aktarılabilir |
| --- | --- | --- |
| <xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel%2A> | Giriş verilerini içeri aktarılan bir ONNX modeliyle Dönüştür | No |
| <xref:Microsoft.ML.TensorflowCatalog.LoadTensorFlowModel%2A> | Giriş verilerini içeri aktarılan bir TensorFlow modeliyle Dönüştür | No |

## <a name="custom-transformations"></a>Özel dönüştürmeler

| Dönüşüm | Tanım | ONNX dışarı aktarılabilir |
| --- | --- | --- |
| <xref:Microsoft.ML.CustomMappingCatalog.CustomMapping%2A> | Varolan sütunları Kullanıcı tanımlı eşleme ile yeni olanlarla Dönüştür | Hayır |
