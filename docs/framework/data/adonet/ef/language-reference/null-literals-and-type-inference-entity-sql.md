---
description: 'Daha fazla bilgi: null değişmez değerler ve tür çıkarımı (Entity SQL)'
title: Null değişmez değerler ve tür çıkarımı (Entity SQL)
ms.date: 03/30/2017
ms.assetid: edd56afb-af1b-4e7d-b210-cb8998143426
ms.openlocfilehash: 3b3474ea9841a34970d2269173d263fda2eb1789
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802144"
---
# <a name="null-literals-and-type-inference-entity-sql"></a>Null değişmez değerler ve tür çıkarımı (Entity SQL)

Null sabit değerleri tür sistemindeki herhangi bir türle uyumludur [!INCLUDE[esql](../../../../../../includes/esql-md.md)] . Ancak, doğru bir sabit değerin doğru bir şekilde çıkarsanmayacak şekilde, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] null bir sabit değerin kullanılabileceği belirli kısıtlamaları uygular.  
  
## <a name="typed-nulls"></a>Yazılan null değerler  

 Yazılan boş değerler her yerde kullanılabilir. Tür bilindiğinden tür çıkarımı türü belirtilmiş null değerler için gerekli değildir. Örneğin, aşağıdaki yapı ile Int16 türünde bir null oluşturabilirsiniz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] :  
  
 `(cast(null as Int16))`  
  
## <a name="free-floating-null-literals"></a>Null değişmez değerleri Free-Floating  

 Serbest kayan null sabit değerleri aşağıdaki bağlamlarda kullanılabilir:  
  
- ATAMA veya Işleme ifadesine bir bağımsız değişken olarak. Bu, türü belirtilmiş null bir ifade oluşturmak için önerilen yoldur.  
  
- Bir yönteme veya işleve bağımsız değişken olarak. Standart aşırı yükleme kuralları geçerlidir.  
  
- Bağımsız değişkenlerden biri olarak +,-, veya/gibi bir aritmetik ifadeye. Diğer bağımsız değişkenler null sabit değerler olamaz, aksi takdirde tür çıkarımı mümkün değildir.  
  
- Bir mantıksal ifadeye bağımsız değişkenlerden biri olarak (ve, veya DEĞIL). Tüm bağımsız değişkenlerin Boole türünde olduğu bilinmektedir.  
  
- Bağımsız değişkeni NULL veya NULL ifade DEĞIL.  
  
- BENZER bir ifadeye bir veya daha fazla bağımsız değişken olarak. Tüm bağımsız değişkenlerin dize olması beklenir.  
  
- Adlandırılmış tür oluşturucusuna bir veya daha fazla bağımsız değişken olarak.  
  
- Bir çok kümeli oluşturucuya bağımsız değişkenlerden biri veya birkaçı. Çoklu küme oluşturucusuna en az bir bağımsız değişken null değişmez değer olmayan bir ifade olmalıdır.  
  
- Bir CASE ifadesinde bir veya daha fazla ifade veya ELSE ifadesi olarak. CASE ifadesinde en az bir tane ya da ELSE ifadesi null değişmez değer dışında bir ifade olmalıdır.  
  
 Serbest kayan null sabit değerleri diğer senaryolarda kullanılamaz. Örneğin, bir satır oluşturucusunda bağımsız değişken olarak kullanılamaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
