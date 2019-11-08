---
title: Varlık Veri Modeli
ms.date: 03/30/2017
ms.assetid: 2dda3d5b-4582-4ba0-a91d-fcd7a1498137
ms.openlocfilehash: ed834c57104e9f03ac337f6c1d30a0498bd42a06
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738418"
---
# <a name="entity-data-model"></a>Varlık Veri Modeli
Varlık Veri Modeli (EDM), depolanan formdan bağımsız olarak verilerin yapısını tanımlayan bir kavram kümesidir. Varlık ilişkisi modelinden 1976 ' de Peter Chen tarafından tanımlanan EDM bulunamadığında, ancak aynı zamanda varlık ilişkisi modelinde oluşturulup geleneksel kullanımları genişletiyor.  
  
 EDM, verilerin birçok biçimde depolanmasından kaynaklanan zorlukları ele alır. Örneğin, verileri ilişkisel veritabanlarında, metin dosyalarında, XML dosyalarında, elektronik tablolarda ve raporlarda depolayan bir işletmeyi düşünün. Bu, veri modellemesi, uygulama tasarımı ve veri erişimi konularında önemli zorluk gösterir. Veri odaklı bir uygulama tasarlarken, sınama, verimli veri erişimi, depolama ve ölçeklenebilirlik olmadan verimli ve sürdürülebilir kodlar yazmak olacaktır. Veriler ilişkisel bir yapıya sahip olduğunda, veri erişimi, depolama ve ölçeklenebilirlik oldukça etkilidir, ancak verimli ve sürdürülebilir kod yazmak daha zor hale gelir. Verilerin bir nesne yapısına sahip olduğu durumlarda, denge ters kaydedilir: etkili ve sürdürülebilir kodun yazılması, verimli veri erişimi, depolama ve ölçeklenebilirlik maliyetlerine gelir. Bu denge arasındaki doğru denge bulunabildiğinden bile, veriler bir formdan diğerine taşındığında yeni sorunlar oluşur. Varlık Veri Modeli, verilerin yapısını herhangi bir depolama şemadan bağımsız olan varlıklar ve ilişkiler bakımından açıklayarak bu zorlukları ele alır. Bu, depolanmış veri formunu uygulama tasarımı ve geliştirmeyle ilgisiz hale getirir. Ayrıca, varlıklar ve ilişkiler bir uygulamada (saklı form değil) kullanılan verilerin yapısını açıkladığı için, bir uygulama geliştikçe gelişir.  
  
 `conceptual model`, verilerin yapısının varlık ve ilişkiler olarak belirli bir gösterimidir ve genellikle EDM kavramlarını uygulayan, etki alanına özgü bir dilde (DSL) tanımlanır. [Kavramsal şema tanım dili (csdl)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec) , bu tür bir etki alanına özgü dilin bir örneğidir. Kavramsal modelde tanımlanan varlıklar ve ilişkiler, bir uygulamadaki nesne ve ilişkilerin soyutlamalarını olarak düşünülebilir. Bu, geliştiricilerin depolama şemasına gerek kalmadan kavramsal modele odaklanmasını sağlar ve verimlilik ve bakımsız kod yazmasına izin verir. Bu arada, depolama şeması tasarımcıları veri erişimi, depolama ve ölçeklenebilirlik verimliliğine odaklanabilir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 Bu bölümdeki konular Varlık Veri Modeli kavramlarını anlatmaktadır. EDM 'yi uygulayan herhangi bir DSL, burada açıklanan kavramları içermelidir. [ADO.NET Entity Framework](./ef/index.md) 'nin, kavramsal modelleri tanımlamak için csdl kullandığını unutmayın. Daha fazla bilgi için bkz. [csdl belirtimi](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).  
  
 [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)  
  
 [Varlık Veri Modeli: Ad Alanları](entity-data-model-namespaces.md)  
  
 [Varlık Veri Modeli: Basit Veri Türleri](entity-data-model-primitive-data-types.md)  
  
 [Varlık Veri Modeli: Devralma](entity-data-model-inheritance.md)  
  
 [association end](association-end.md)  
  
 [association end multiplicity](association-end-multiplicity.md)  
  
 [association set](association-set.md)  
  
 [association set end](association-set-end.md)  
  
 [association type](association-type.md)  
  
 [complex type](complex-type.md)  
  
 [entity container](entity-container.md)  
  
 [entity key](entity-key.md)  
  
 [entity set](entity-set.md)  
  
 [entity type](entity-type.md)  
  
 [facet](facet.md)  
  
 [foreign key property](foreign-key-property.md)  
  
 [model-declared function](model-declared-function.md)  
  
 [model-defined function](model-defined-function.md)  
  
 [navigation property](navigation-property.md)  
  
 [property](property.md)  
  
 [referential integrity constraint](referential-integrity-constraint.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Varlık Veri Modeli araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [. edmx dosyasına genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [CSDL Belirtimi](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
