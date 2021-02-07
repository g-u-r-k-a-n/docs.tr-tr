---
description: 'Daha fazla bilgi edinin: Group by yan tümcesi (Visual Basic)'
title: Group By Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QueryGroupByInto
- vb.QueryGroupBy
- vb.QueryGroupRef
- vb.QueryGroupInto
- vb.QueryGroup
helpviewer_keywords:
- queries [Visual Basic], Group By
- Group By statement [Visual Basic]
- Group By clause [Visual Basic]
ms.assetid: b1b5dcea-6654-473b-a2db-01f7e4c265d7
ms.openlocfilehash: f5cfb76b0f4b1d191f959ae1812140c6872e93bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700513"
---
# <a name="group-by-clause-visual-basic"></a>Group By Tümcesi (Visual Basic)

Bir sorgu sonucunun öğelerini gruplandırır. , Her gruba toplam işlevleri uygulamak için de kullanılabilir. Gruplandırma işlemi bir veya daha fazla anahtara göre belirlenir.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a>Bölümler  
  
- `listField1`, `listField2`  
  
     İsteğe bağlı. Gruplanmış sonuca dahil edilecek alanları açıkça tanımlayan sorgu değişkeninin veya değişkenlerinin bir veya daha fazla alanı. Hiçbir alan belirtilmemişse, sorgu değişkeni veya değişkenlerinin tüm alanları gruplanmış sonuca dahil edilir.  
  
- `keyExp1`  
  
     Gereklidir. Öğe gruplarını belirlemekte kullanılacak anahtarı tanımlayan bir ifade. Bileşik bir anahtar belirtmek için birden fazla anahtar belirtebilirsiniz.  
  
- `keyExp2`  
  
     İsteğe bağlı. Bileşik anahtar oluşturmak için ile birlikte birleştirilmiş bir veya daha fazla ek anahtar `keyExp1` .  
  
- `aggregateList`  
  
     Gereklidir. Grupların nasıl toplanacağına ilişkin bir veya daha fazla ifade. Gruplanmış sonuçların üye adını belirlemek için, `Group` aşağıdaki biçimlerden birinde olabilecek anahtar sözcüğünü kullanın:  
  
    ```vb  
    Into Group  
    ```  
  
     -veya-  
  
    ```vb  
    Into <alias> = Group  
    ```  
  
     Gruba uygulanacak toplama işlevlerini de ekleyebilirsiniz.  
  
## <a name="remarks"></a>Açıklamalar  

 `Group By`Bir sorgunun sonuçlarını gruplara bölmek için yan tümcesini kullanabilirsiniz. Gruplandırma bir anahtara veya birden çok anahtardan oluşan bileşik anahtara göre belirlenir. Eşleşen anahtar değerleriyle ilişkili öğeler aynı gruba dahil edilir.  
  
 `aggregateList` `Into` `Group` Gruba başvurmak için kullanılan üye adını tanımlamak için yan tümcesinin ve anahtar sözcüğünün parametresini kullanırsınız. `Into`Gruplanmış öğeler için değerleri hesaplamak üzere yan tümcesine toplama işlevleri de ekleyebilirsiniz. Standart toplama işlevlerinin bir listesi için bkz. [Aggregate yan tümcesi](aggregate-clause.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod örneği, konumlarına (ülke/bölge) göre müşterilerin bir listesini gruplandırır ve her bir gruptaki müşterilerin sayısını sağlar. Sonuçlar ülke/bölge adına göre sıralanır. Gruplanmış sonuçlar şehir adına göre sıralanır.  
  
 [!code-vb[VbSimpleQuerySamples#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de LINQ'e Giriş](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](index.md)
- [Select yan tümcesi](select-clause.md)
- [From yan tümcesi](from-clause.md)
- [Order by yan tümcesi](order-by-clause.md)
- [Aggregate Yan Tümcesi](aggregate-clause.md)
- [Group Join Yan Tümcesi](group-join-clause.md)
