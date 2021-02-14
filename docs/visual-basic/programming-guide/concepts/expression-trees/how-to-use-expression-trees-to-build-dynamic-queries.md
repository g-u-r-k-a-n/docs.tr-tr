---
description: 'Daha fazla bilgi edinin: nasıl yapılır: dinamik sorgular oluşturmak için Ifade ağaçları kullanma (Visual Basic)'
title: 'Nasıl yapılır: Dinamik Sorgular Derlemek için İfade Ağaçları Kullanma'
ms.date: 07/20/2015
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: bb8abb22749cbf7c15b72632f60a5bd08287378d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100423101"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a>Nasıl yapılır: dinamik sorgular oluşturmak için Ifade ağaçları kullanma (Visual Basic)

LINQ içinde, ifade ağaçları, uygulayan veri kaynaklarını hedefleyen yapılandırılmış sorguları temsil etmek için kullanılır <xref:System.Linq.IQueryable%601> . Örneğin, LINQ sağlayıcısı <xref:System.Linq.IQueryable%601> ilişkisel veri depolarını sorgulamak için arabirimini uygular. Visual Basic Derleyicisi, bu tür veri kaynaklarını hedefleyen sorguları, çalışma zamanında bir ifade ağacı oluşturan koda derler. Sorgu sağlayıcısı daha sonra ifade ağacı veri yapısına çapraz geçiş yapabilir ve veri kaynağı için uygun bir sorgu diline çevirebilir.

İfade ağaçları Ayrıca LINQ 'te tür değişkenlerine atanan Lambda ifadelerini temsil etmek için de kullanılır <xref:System.Linq.Expressions.Expression%601> .

Bu konu başlığı altında, dinamik LINQ sorguları oluşturmak için ifade ağaçlarının nasıl kullanılacağı açıklanmaktadır. Dinamik sorgular, bir sorgunun özelliklerinin derleme zamanında bilinmediği durumlarda faydalıdır. Örneğin, bir uygulama, son kullanıcının verileri filtrelemek için bir veya daha fazla koşul belirtmesini sağlayan bir kullanıcı arabirimi sağlayabilir. Bu tür bir uygulamanın, sorgulama için LINQ kullanabilmesi amacıyla, çalışma zamanında LINQ sorgusu oluşturmak için ifade ağaçları kullanması gerekir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir veri kaynağına yönelik sorgu oluşturmak ve ardından yürütmek için ifade ağaçlarının nasıl kullanılacağını gösterir `IQueryable` . Kod, aşağıdaki sorguyu temsil etmek için bir ifade ağacı oluşturur:

`companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`

Ad alanındaki Fabrika yöntemleri, <xref:System.Linq.Expressions> genel sorguyu oluşturan ifadeleri temsil eden ifade ağaçları oluşturmak için kullanılır. Standart sorgu operatörü yöntemlerine yapılan çağrıları temsil eden ifadeler, <xref:System.Linq.Queryable> Bu yöntemlerin uygulamalarına başvurur. Son ifade ağacı, <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> `IQueryable` türünde çalıştırılabilir bir sorgu oluşturmak için veri kaynağının sağlayıcısı uygulamasına geçirilir `IQueryable` . Sonuçlar, bu sorgu değişkeni numaralandırıldığı için alınır.

```vb
' Add an Imports statement for System.Linq.Expressions.

Dim companies =
    {"Consolidated Messenger", "Alpine Ski House", "Southridge Video", "City Power & Light",
     "Coho Winery", "Wide World Importers", "Graphic Design Institute", "Adventure Works",
     "Humongous Insurance", "Woodgrove Bank", "Margie's Travel", "Northwind Traders",
     "Blue Yonder Airlines", "Trey Research", "The Phone Company",
     "Wingtip Toys", "Lucerne Publishing", "Fourth Coffee"}

' The IQueryable data to query.
Dim queryableData As IQueryable(Of String) = companies.AsQueryable()

' Compose the expression tree that represents the parameter to the predicate.
Dim pe As ParameterExpression = Expression.Parameter(GetType(String), "company")

' ***** Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16) *****
' Create an expression tree that represents the expression: company.ToLower() = "coho winery".
Dim left As Expression = Expression.Call(pe, GetType(String).GetMethod("ToLower", System.Type.EmptyTypes))
Dim right As Expression = Expression.Constant("coho winery")
Dim e1 As Expression = Expression.Equal(left, right)

' Create an expression tree that represents the expression: company.Length > 16.
left = Expression.Property(pe, GetType(String).GetProperty("Length"))
right = Expression.Constant(16, GetType(Integer))
Dim e2 As Expression = Expression.GreaterThan(left, right)

' Combine the expressions to create an expression tree that represents the
' expression: company.ToLower() = "coho winery" OrElse company.Length > 16).
Dim predicateBody As Expression = Expression.OrElse(e1, e2)

' Create an expression tree that represents the expression:
' queryableData.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16)
Dim whereCallExpression As MethodCallExpression = Expression.Call(
        GetType(Queryable),
        "Where",
        New Type() {queryableData.ElementType},
        queryableData.Expression,
        Expression.Lambda(Of Func(Of String, Boolean))(predicateBody, New ParameterExpression() {pe}))
' ***** End Where *****

' ***** OrderBy(Function(company) company) *****
' Create an expression tree that represents the expression:
' whereCallExpression.OrderBy(Function(company) company)
Dim orderByCallExpression As MethodCallExpression = Expression.Call(
        GetType(Queryable),
        "OrderBy",
        New Type() {queryableData.ElementType, queryableData.ElementType},
        whereCallExpression,
        Expression.Lambda(Of Func(Of String, String))(pe, New ParameterExpression() {pe}))
' ***** End OrderBy *****

' Create an executable query from the expression tree.
Dim results As IQueryable(Of String) = queryableData.Provider.CreateQuery(Of String)(orderByCallExpression)

' Enumerate the results.
For Each company As String In results
    Console.WriteLine(company)
Next

' This code produces the following output:
'
' Blue Yonder Airlines
' City Power & Light
' Coho Winery
' Consolidated Messenger
' Graphic Design Institute
' Humongous Insurance
' Lucerne Publishing
' Northwind Traders
' The Phone Company
' Wide World Importers
```

Bu kod, metoduna geçirilen koşuldaki sabit sayıda ifadeyi kullanır `Queryable.Where` . Ancak, kullanıcı girişine bağlı bir değişken sayıda koşul ifadesini birleştiren bir uygulama yazabilirsiniz. Ayrıca, kullanıcının girişine bağlı olarak sorguda çağrılan standart sorgu işleçlerini da değiştirebilirsiniz.

## <a name="compile-the-code"></a>Kodu derle

- Yeni bir **konsol uygulaması** projesi oluşturun.

- System. Linq. Ifadeler ad alanını ekleyin.

- Örnekteki kodu kopyalayın ve `Main` `Sub` yordama yapıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [İfade ağaçları (Visual Basic)](index.md)
- [Nasıl yapılır: Ifade ağaçlarını yürütme (Visual Basic)](how-to-execute-expression-trees.md)
