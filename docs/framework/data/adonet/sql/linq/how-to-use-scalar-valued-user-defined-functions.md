---
title: 'Nasıl yapılır: Skaler Değerli Kullanıcı Tanımlı İşlevler Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: faf8d6e94c88575f6cb73003fa5bed87650d7d54
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91196942"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a>Nasıl yapılır: Skaler Değerli Kullanıcı Tanımlı İşlevler Kullanma

Özniteliğini kullanarak, bir sınıfta tanımlanan istemci yöntemini Kullanıcı tanımlı bir işlev ile eşleyebilirsiniz <xref:System.Data.Linq.Mapping.FunctionAttribute> . Yöntemin gövdesi, yöntem çağrısının amacını yakalayan bir ifade oluşturur ve bu ifadeyi <xref:System.Data.Linq.DataContext> çeviri ve yürütmeye geçirir.  
  
> [!NOTE]
> Doğrudan yürütme yalnızca işlev bir sorgu dışında çağrıldığında gerçekleşir. Daha fazla bilgi için bkz. [nasıl yapılır: Kullanıcı tanımlı Işlevleri Iç satır Içinde çağırma](how-to-call-user-defined-functions-inline.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki SQL kodu, skaler değerli Kullanıcı tanımlı bir işlev gösterir `ReverseCustName()` .  
  
```sql  
CREATE FUNCTION ReverseCustName(@string varchar(100))  
RETURNS varchar(100)  
AS  
BEGIN  
    DECLARE @custName varchar(100)  
    -- Implementation left as exercise for users.  
    RETURN @custName  
END  
```  
  
 Bu kod için aşağıdaki gibi bir istemci yöntemi eşleyebilirsiniz:  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanıcı tanımlı Işlevler](user-defined-functions.md)
