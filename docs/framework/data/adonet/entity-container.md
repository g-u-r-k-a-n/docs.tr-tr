---
description: 'Daha fazla bilgi edinin: varlık kapsayıcısı'
title: entity container
ms.date: 03/30/2017
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
ms.openlocfilehash: 1e90190e98ccf6bc6d48193adbe90a9ff31c4711
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672939"
---
# <a name="entity-container"></a>entity container

Bir *varlık kapsayıcısı* , [varlık kümelerinin](entity-set.md), [ilişkilendirme kümelerinin](association-set.md)ve [işlev içeri aktarmalarının](model-declared-function.md)mantıksal gruplandırmasıdır.  
  
 Aşağıdaki bir kavramsal modelde tanımlanan bir varlık kapsayıcısının doğru olması gerekir:  
  
- Her kavramsal modelde en az bir varlık kapsayıcısının tanımlanması gerekir.  
  
- Varlık kapsayıcısının her kavramsal model içinde benzersiz bir adı olmalıdır.  
  
 Bir varlık kapsayıcısı, bir veya daha fazla ad alanında tanımlanan varlık türlerini veya ilişkilerini kullanan varlık kümelerini veya ilişki kümelerini tanımlayabilir. Daha fazla bilgi için bkz. [varlık veri modeli: ad alanları](entity-data-model-namespaces.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki diyagramda üç varlık türü olan kavramsal model gösterilmektedir: `Book` , `Publisher` , ve `Author` .  Daha fazla bilgi için bkz. sonraki örnek.  
  
 ![Üç varlık türüne sahip örnek model](./media/entity-container/example-model-three-entity-types.gif)  
  
 Diyagram varlık kapsayıcı bilgilerini iletmese de, kavramsal model bir varlık kapsayıcısı tanımlamalıdır. [ADO.NET Entity Framework](./ef/index.md) kavramsal modelleri tanımlamak için kavramsal şema tanım dili ([csdl](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) adlı bir DSL kullanır. Aşağıdaki CSDL, Yukarıdaki diyagramda gösterilen kavramsal model için bir varlık kapsayıcısı tanımlar. Varlık kapsayıcısı adının bir XML özniteliğinde tanımlandığını unutmayın.  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varlık Veri Modeli Temel Kavramları](entity-data-model-key-concepts.md)
- [Varlık Veri Modeli](entity-data-model.md)
