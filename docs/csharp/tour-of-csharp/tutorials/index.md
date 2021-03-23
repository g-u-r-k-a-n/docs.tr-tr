---
title: C# etkileşimli öğreticilerine giriş
description: Tarayıcınızda C# öğrenin ve kendi geliştirme ortamınızı kullanmaya başlayın
ms.date: 02/02/2021
ms.custom: mvc
ms.openlocfilehash: ed869271cd6f4ec13f769f46d41aefae9e1dad8d
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872424"
---
# <a name="introduction-to-c"></a>C 'ye giriş\#

C# öğreticilerine giriş konusuna hoş geldiniz. Bu dersler, tarayıcınızda çalıştırabileceğiniz etkileşimli kodla başlar. Bu etkileşimli dersleri başlatmadan önce [C# 101 video serisinde](https://aka.ms/dotnet3-csharp) c# temel bilgilerini öğrenebilirsiniz.

<!--markdownlint-disable MD034 -->
> [!VIDEO https://channel9.msdn.com/Series/CSharp-101/What-is-C/player]

İlk dersler, kodun küçük kod parçacıklarını kullanarak C# kavramlarını açıklamaktadır. C# sözdiziminin temel bilgilerini ve dizeler, sayılar ve Boole değerleri gibi veri türleriyle nasıl çalışacağınızı öğreneceksiniz. Bu, tüm etkileşimlidir ve dakikalar içinde kod yazmak ve çalıştırmak isteyeceksiniz. Bu ilk dersler, programlama veya C# dilinin önceki bir bilgisine sahip olmadığını varsayar.

Bu öğreticileri farklı ortamlarda deneyebilirsiniz. Öğrentireceğiz kavramlar aynı. Fark, tercih ettiğiniz deneyimdir:

- [Tarayıcınızda, docs platformunda](hello-world.yml): Bu deneyim, docs sayfalarında bir çalıştırılabilir C# kod penceresi katıştırır. Tarayıcıda C# kodu yazın ve yürütün.
- [Microsoft Learn deneyimidir](/learn/paths/csharp-first-steps/). Bu öğrenme yolu, C# temel bilgilerini öğreten birkaç modül içerir.
- [Ciltçide jupi 'de](https://mybinder.org/v2/gh/dotnet/try-samples/master?filepath=hello-csharp%2Fhello-world.ipynb). Ciltçideki bir Jupyter not defterinde C# kodu deneyebilirsiniz.
- [Yerel makinenizde](numbers-in-csharp-local.md). Çevrimiçi araştırdıktan sonra, .NET Core SDK [yükleyebilir](https://dotnet.microsoft.com/download) ve makinenizde programları oluşturabilirsiniz.

Merhaba Dünya dersi izleyen tüm giriş öğreticileri, çevrimiçi tarayıcı deneyimi veya [kendi yerel geliştirme ortamınızda](local-environment.md)bulunabilir. Her öğreticinin sonunda, çevrimiçi olarak veya kendi makinenizde bir sonraki ders ile devam etmek istediğinize karar verirsiniz. Ortamınızı ayarlamanıza ve makinenizde bir sonraki öğreticiye devam etmenize yardımcı olacak bağlantılar vardır.

## <a name="hello-world"></a>[Merhaba Dünya](hello-world.yml)

[Merhaba Dünya](hello-world.yml) öğreticisinde en temel C# programını oluşturacaksınız. `string`Türü ve metinle çalışmayı inceleyebilirsiniz. Ayrıca, bağlayıcı üzerinde [Microsoft Learn](/learn/paths/csharp-first-steps/) veya [Jupyıter](https://mybinder.org/v2/gh/dotnet/try-samples/master?filepath=hello-csharp%2Fhello-world.ipynb)üzerindeki yolu da kullanabilirsiniz.

## <a name="numbers-in-c"></a>[C# numaraları](numbers-in-csharp.yml)

C# öğreticisindeki [sayılarda](numbers-in-csharp.yml) , bilgisayarların sayıları nasıl depolayacağınızı ve farklı sayısal türlerle hesaplamaların nasıl gerçekleştirileceğini öğreneceksiniz. Yuvarlama hakkında temel bilgileri ve C# kullanarak matematik hesaplamaları yapmayı öğreneceksiniz. Bu öğretici, [makinenizde yerel olarak çalışmak için](numbers-in-csharp-local.md)de kullanılabilir.

Bu öğreticide, [Merhaba Dünya](hello-world.yml) dersi tamamladığınız varsayılmaktadır.

## <a name="branches-and-loops"></a>[Dal ve döngüler](branches-and-loops.yml)

[Dallar ve döngüler](branches-and-loops.yml) öğreticisinde, değişkenlerde depolanan değerlere göre farklı kod yürütme yolları seçmenin temelleri öğretilir. Denetim akışının temel bilgilerini öğrenirsiniz. Bu, programların kararlar alma ve farklı eylemler seçme işlemlerinin temelini oluşturur. Bu öğretici, [makinenizde yerel olarak çalışmak için](branches-and-loops-local.md)de kullanılabilir.

Bu öğreticide, C# derslerde [Merhaba Dünya](hello-world.yml) ve [rakamları](numbers-in-csharp.yml) tamamladığınız varsayılmaktadır.

## <a name="list-collection"></a>[Liste koleksiyonu](list-collection.yml)

[Liste koleksiyonu](list-collection.yml) dersi, veri dizilerini depolayan liste koleksiyonu türünün bir turuna sahip olmanızı sağlar. Öğe ekleme ve kaldırma, öğe arama ve listeleri sıralama hakkında bilgi edineceksiniz. Farklı liste türleri keşfedebilirsiniz. Bu öğretici, [makinenizde yerel olarak çalışmak için](arrays-and-collections.md)de kullanılabilir.

Bu öğreticide, yukarıda listelenen dersleri tamamladığınız varsayılmaktadır.

## <a name="101-linq-samples"></a>[101 LINQ örnekleri](https://github.com/dotnet/try-samples/tree/main/101-linq-samples)

Bu örnek [DotNet-TRY](https://github.com/dotnet/try/blob/main/README.md#setup) küresel aracını gerektirir. Aracı yükledikten ve [TRY-Samples](https://github.com/dotnet/try-samples) deposunu kopyaladıktan sonra, etkileşimli olarak çalıştırabileceğiniz bir dizi 101 örneği aracılığıyla dil Ile tümleşik sorgu (LINQ) hakkında bilgi edinebilirsiniz. Veri dizilerini sorgulamak, araştırmak ve dönüştürmek için kullanabileceğiniz farklı yolları keşfedebilirsiniz.
