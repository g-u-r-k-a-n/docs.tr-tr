---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: ertelenmiş yüklemeyi kapatma'
title: 'Nasıl yapılır: Geciktirilmiş Yüklemeyi Kapatma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: 739c9b0b65eda73d6c504409395eb805b0c02873
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785841"
---
# <a name="how-to-turn-off-deferred-loading"></a>Nasıl yapılır: Geciktirilmiş Yüklemeyi Kapatma

Giderek ertelenmiş yüklemeyi devre dışı bırakabilirsiniz <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> `false` . Daha fazla bilgi için bkz. [ertelenmiş ve hemen yükleme](deferred-versus-immediate-loading.md).  
  
> [!NOTE]
> Ertelenmiş yükleme, nesne izleme kapalıyken etkili bir şekilde kapalıdır. Daha fazla bilgi için bkz. [nasıl yapılır: bilgileri salt okuma olarak alma](how-to-retrieve-information-as-read-only.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, ' i ' ye ayarlayarak ertelenmiş yüklemenin nasıl kapatılacağı <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> gösterilmektedir `false` .  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](query-concepts.md)
- [Veritabanını Sorgulama](querying-the-database.md)
