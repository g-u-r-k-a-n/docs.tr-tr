---
description: 'Daha fazla bilgi edinin: nesne materialization (WCF Veri Hizmetleri)'
title: Nesne materialization (WCF Veri Hizmetleri)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
ms.assetid: f0dbf7b0-0292-4e31-9ae4-b98288336dc1
ms.openlocfilehash: 4beb72b9fb4402ee9a751b870f012bfa2cf15951
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794981"
---
# <a name="object-materialization-wcf-data-services"></a>Nesne materialization (WCF Veri Hizmetleri)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

.NET Framework tabanlı bir istemci uygulamasında açık veri Protokolü (OData) akışını tüketmek için **hizmet başvurusu Ekle** iletişim kutusunu kullandığınızda, akış tarafından kullanıma sunulan veri modelindeki her bir varlık türü için eşdeğer veri sınıfları oluşturulur. Daha fazla bilgi için bkz. [veri hizmeti Istemci kitaplığı oluşturma](generating-the-data-service-client-library-wcf-data-services.md). Bir sorgu tarafından döndürülen varlık verileri, bu oluşturulan istemci veri hizmeti sınıflarından birinin bir örneğine getirilir. İzlenen nesneler için birleştirme seçenekleri ve kimlik çözümlemesi hakkında daha fazla bilgi için bkz. [veri hizmeti bağlamını yönetme](managing-the-data-service-context-wcf-data-services.md).

WCF Veri Hizmetleri, araç tarafından oluşturulan veri sınıflarını kullanmak yerine kendi istemci veri hizmeti sınıflarınızı tanımlamanızı da sağlar. Bu, "düz eski CLR nesnesi" (POCO) veri sınıfları olarak da bilinen kendi veri sınıflarınızı kullanmanıza olanak sağlar. Bu tür özel veri sınıfları kullanılırken, ya da veri sınıfını, <xref:System.Data.Services.Common.DataServiceKeyAttribute> ya da veya <xref:System.Data.Services.Common.DataServiceEntityAttribute> istemci üzerindeki tür adlarının veri hizmetinin veri modelindeki tür adlarıyla eşleştiğinden emin olmalısınız.

Kitaplık sorgu yanıt iletisini aldıktan sonra, OData akışından döndürülen verileri sorgu türünde olan istemci veri hizmeti sınıflarının örneklerine çıkarır. Bu nesneleri üreten genel süreç aşağıdaki gibidir:

1. İstemci kitaplığı, `entry` yanıt iletisi akışındaki öğeden serileştirilmiş türü okur ve aşağıdaki yollarla doğru türün yeni bir örneğini oluşturmaya çalışır:

    - Akışta belirtilen tür, türüyle aynı ada sahip olduğunda <xref:System.Data.Services.Client.DataServiceQuery%601> , bu türün yeni bir örneği boş Oluşturucu kullanılarak oluşturulur.

    - Akışta belirtilen tür, türünden türetilmiş bir türle aynı ada sahip olduğunda <xref:System.Data.Services.Client.DataServiceQuery%601> , bu türetilmiş türün yeni bir örneği boş Oluşturucu kullanılarak oluşturulur.

    - Akışta belirtilen tür ya da türetilmiş türlerin türüyle eşleştirilemezse <xref:System.Data.Services.Client.DataServiceQuery%601> , sorgulanan türün yeni bir örneği boş Oluşturucu kullanılarak oluşturulur.

    - <xref:System.Data.Services.Client.DataServiceContext.ResolveType%2A>Özellik ayarlandığında, sağlanan temsilci varsayılan ad tabanlı tür eşlemesini geçersiz kılmak için çağrılır ve bunun yerine tarafından döndürülen türün yeni bir örneği <xref:System.Func%602> oluşturulur. Bu temsilci null değer döndürürse, bunun yerine sorgulanan türün yeni bir örneği oluşturulur. Devralma senaryolarını desteklemek için varsayılan ad tabanlı tür adı eşlemesini geçersiz kılmak gerekebilir.

2. İstemci kitaplığı, `id` `entry` varlığının kimlik değeri olan ÖĞESININ öğesinden URI değerini okur. Bir değeri kullanılmadığı takdirde, ' <xref:System.Data.Services.Client.DataServiceContext.MergeOption%2A> <xref:System.Data.Services.Client.MergeOption.NoTracking> de nesnesini izlemek için kimlik değeri kullanılır <xref:System.Data.Services.Client.DataServiceContext> . Kimlik değeri, bir varlık sorgu yanıtında birden çok kez döndürüldüğünde bile yalnızca tek bir varlık örneğinin oluşturulmasını sağlamak için de kullanılır.

3. İstemci kitaplığı, akış girdisinden özellikleri okur ve yeni oluşturulan nesnede karşılık gelen özellikleri ayarlar. Aynı kimlik değerine sahip bir nesne öğesinde zaten gerçekleşirse, <xref:System.Data.Services.Client.DataServiceContext> özellikleri ayarına göre ayarlanır <xref:System.Data.Services.Client.MergeOption> <xref:System.Data.Services.Client.DataServiceContext> . Yanıt, karşılık gelen bir özelliğin istemci türünde gerçekleşmeyeceği özellik değerlerini içerebilir. Bu gerçekleştiğinde eylem, özelliğinin değerine bağlıdır <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> <xref:System.Data.Services.Client.DataServiceContext> . Bu özellik olarak ayarlandığında `true` , eksik özellik yok sayılır. Aksi takdirde bir hata oluşur. Özellikler aşağıdaki gibi ayarlanır:

    - Skalar özellikler, yanıt iletisindeki girişte karşılık gelen değere ayarlanır.

    - Karmaşık özellikler, yanıttan karmaşık türün özellikleriyle ayarlanan yeni bir karmaşık tür örneğine ayarlanır.

    - İlgili varlıkların bir koleksiyonunu döndüren gezinti özellikleri yeni veya var olan bir örneğine ayarlanır; <xref:System.Collections.Generic.ICollection%601> burada `T` ilgili varlık türüdür. İlgili nesneler öğesine yüklenmediği müddetçe bu koleksiyon boştur <xref:System.Data.Services.Client.DataServiceContext> . Daha fazla bilgi için bkz. [ertelenmiş Içerik yükleme](loading-deferred-content-wcf-data-services.md).

      > [!NOTE]
      > Oluşturulan istemci veri sınıfları veri bağlamayı destekledikleri zaman, gezinti özellikleri <xref:System.Data.Services.Client.DataServiceCollection%601> bunun yerine sınıfının örneklerini döndürür. Daha fazla bilgi için bkz. [verileri denetimlere bağlama](binding-data-to-controls-wcf-data-services.md).

4. <xref:System.Data.Services.Client.DataServiceContext.ReadingEntity>Olay tetiklenir.

5. İstemci kitaplığı, nesnesini öğesine ekler <xref:System.Data.Services.Client.DataServiceContext> . Nesnesi, olduğunda eklenmez <xref:System.Data.Services.Client.MergeOption> <xref:System.Data.Services.Client.MergeOption.NoTracking> .

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Hizmetini Sorgulama](querying-the-data-service-wcf-data-services.md)
- [Sorgu Projeksiyonları](query-projections-wcf-data-services.md)
