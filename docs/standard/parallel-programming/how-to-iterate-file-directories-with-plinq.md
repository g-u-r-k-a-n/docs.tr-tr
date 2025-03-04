---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: PLıNQ ile dosya dizinlerini yineleme'
title: 'Nasıl yapılır: PLINQ ile Dosya Dizinlerini Yineleme'
ms.date: 03/30/2017
helpviewer_keywords:
- PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
ms.openlocfilehash: 131350d34694b58ccd3a2e78eb2164495bd20708
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701917"
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>Nasıl yapılır: PLINQ ile Dosya Dizinlerini Yineleme

Bu makalede, dosya dizinlerinde paralel hale getirmek işlemleri için iki yol gösterilmektedir. İlk sorgu, <xref:System.IO.Directory.GetFiles%2A> bir dizin ve tüm alt dizinler içindeki dosya adı dizisini doldurmak için yöntemini kullanır. Bu yöntem, tüm dizi dolduruluncaya kadar döndürülmediği için işlemin başlangıcında gecikme süresini ortaya çıkarabilir. Ancak, dizi doldurulduktan sonra PLıNQ onu paralel olarak hızlı bir şekilde işleyebilir.  
  
İkinci sorgu, <xref:System.IO.Directory.EnumerateDirectories%2A> <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> sonuçları hemen döndürmeye başlayan statik ve yöntemleri kullanır. Büyük dizin ağaçları üzerinde yineleme yaparken bu yaklaşım daha hızlı olabilir, ancak ilk örnekle karşılaştırılan işleme süresi birçok faktöre bağlıdır.  
  
> [!NOTE]
> Bu örnekler kullanımı göstermeye yöneliktir ve eşdeğer sıralı LINQ to Objects sorgusundan daha hızlı çalışmayabilir. Hızlı yedekleme hakkında daha fazla bilgi için bkz. [PLıNQ 'Te hızlı hızlandırı anlama](understanding-speedup-in-plinq.md).  
  
## <a name="getfiles-example"></a>GetFiles örneği

 Bu örnek, ağaçtaki tüm dizinlere erişebilmeniz durumunda dosya boyutlarının basit senaryolarda nasıl yineleneceğini gösterir, dosya boyutları büyük değildir ve erişim süreleri önemli değildir. Bu yaklaşım, dosya adları dizisi oluşturulurken başlangıcında bir gecikme süresi içerir.  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="enumeratefiles-example"></a>EnumerateFiles örneği

 Bu örnek, ağaçtaki tüm dizinlere erişebilmeniz durumunda dosya boyutlarının basit senaryolarda nasıl yineleneceğini gösterir, dosya boyutları büyük değildir ve erişim süreleri önemli değildir. Bu yaklaşım, önceki örnekteki sonuçları daha hızlı üretmeye başlar.  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 Kullanırken <xref:System.IO.Directory.GetFiles%2A> , ağaçtaki tüm dizinlerde yeterli izinlere sahip olduğunuzdan emin olun. Aksi takdirde, bir özel durum oluşturulur ve sonuç döndürülmez. <xref:System.IO.Directory.EnumerateDirectories%2A>BIR PLıNQ sorgusunda kullanırken, yineleme devam etmenizi sağlamak için g/ç özel durumlarını düzgün bir şekilde işlemek sorunlu olur. Kodunuzun g/ç veya yetkisiz erişim özel durumlarını işlemesi gerekiyorsa, [nasıl yapılır: paralel sınıfla dosya dizinlerini yineleme](how-to-iterate-file-directories-with-the-parallel-class.md)bölümünde açıklanan yaklaşımı göz önünde bulundurmanız gerekir.  
  
 G/ç gecikme süresi bir sorun ise (örneğin, ağ üzerinden dosya g/ç 'si), [TPL ve geleneksel .NET zaman uyumsuz programlamada](tpl-and-traditional-async-programming.md) ve bu [blog postasında](https://devblogs.microsoft.com/pfxteam/parallel-extensions-and-io/)açıklanan zaman uyumsuz g/ç tekniklerinden birini kullanmayı göz önünde bulundurun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](introduction-to-plinq.md)
