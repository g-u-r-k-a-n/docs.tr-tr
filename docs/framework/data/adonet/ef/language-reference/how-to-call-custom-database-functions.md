---
title: 'Nasıl yapılır: özel veritabanı Işlevlerini çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
ms.openlocfilehash: e357868361e11dc919fa09db9a36185923a6e40e
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72847090"
---
# <a name="how-to-call-custom-database-functions"></a>Nasıl yapılır: özel veritabanı Işlevlerini çağırma

Bu konu, LINQ to Entities sorguları içinden veritabanında tanımlanan özel işlevlerin nasıl çağrılacağını açıklar.

LINQ to Entities sorgulardan çağrılan veritabanı işlevleri veritabanında yürütülür. Veritabanındaki işlevlerin yürütülmesi, uygulama performansını iyileştirebilir.

Aşağıdaki yordam, özel bir veritabanı işlevini çağırmak için üst düzey bir ana hat sağlar. Aşağıdaki örnek, yordamdaki adımlar hakkında daha fazla ayrıntı sağlar.

## <a name="to-call-custom-functions-that-are-defined-in-the-database"></a>Veritabanında tanımlanan özel işlevleri çağırmak için

1. Veritabanınızda özel bir işlev oluşturun.

     SQL Server özel işlevler oluşturma hakkında daha fazla bilgi için bkz. [create FUNCTION (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkID=139871).

2. . Edmx dosyanızın mağaza şeması tanım dili (SSDL) içinde bir işlev bildirin. İşlevin adı, veritabanında belirtilen işlevin adı ile aynı olmalıdır.

     Daha fazla bilgi için bkz. [Işlev öğesi (ssdl)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).

3. Uygulama kodunuzda bir sınıfa karşılık gelen bir yöntemi ekleyin ve yöntemine bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> uygulayın. özniteliğin <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> ve <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parametrelerinin kavramsal modelin ad alanı adı ve kavramsal modeldeki işlev adı olduğunu unutmayın anı. LINQ için işlev adı çözümlemesi büyük/küçük harfe duyarlıdır.

4. Yöntemi bir LINQ to Entities sorgusunda çağırın.  

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir LINQ to Entities sorgusunun içinden özel bir veritabanı işlevinin nasıl çağrılacağını gösterir. Örnek, okul modelini kullanır. Okul modeli hakkında daha fazla bilgi için bkz. [okul örnek veritabanı oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) ve [okul. edmx dosyası](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100))oluşturma.

Aşağıdaki kod, okul örnek veritabanına `AvgStudentGrade` işlevini ekler.

> [!NOTE]
> Özel bir veritabanı işlevini çağırma adımları veritabanı sunucusundan bağımsız olarak aynıdır. Ancak, aşağıdaki kod SQL Server veritabanında bir işlev oluşturmak için özeldir. Diğer veritabanı sunucularında özel bir işlev oluşturma kodu farklılık gösterebilir.

[!code-sql[DP L2E MapToDBFunction#1](~/samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]

## <a name="example"></a>Örnek

Sonra, *. edmx* dosyanızın mağaza şeması tanım DILI (ssdl) içinde bir işlev bildirin. Aşağıdaki kod, SSDL içinde `AvgStudentGrade` işlevini bildirir:

[!code-xml[DP L2E MapToDBFunction#2](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]

## <a name="example"></a>Örnek

Şimdi bir yöntem oluşturun ve bu yöntemi SSDL öğesinde belirtilen işlevle eşleyin. Aşağıdaki sınıftaki yöntemi, bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>kullanılarak SSDL (yukarıda) içinde tanımlanan işlevle eşlenir. Bu yöntem çağrıldığında, veritabanındaki karşılık gelen işlev yürütülür.

[!code-csharp[DP L2E MapToDBFunction#3](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
[!code-vb[DP L2E MapToDBFunction#3](~/samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]

## <a name="example"></a>Örnek

Son olarak, yöntemi bir LINQ to Entities sorgusunda çağırın. Aşağıdaki kod, öğrenciler için en son adları ve ortalama bir not konsolunu görüntüler:

[!code-csharp[DP L2E MapToDBFunction#4](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
[!code-vb[DP L2E MapToDBFunction#4](~/samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]

## <a name="see-also"></a>Ayrıca bkz.

- [. edmx dosyasına genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [LINQ to Entities Sorguları](queries-in-linq-to-entities.md)
