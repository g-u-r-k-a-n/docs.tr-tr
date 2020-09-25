---
title: İfade Yorumlama
description: Bir ifade ağacının yapısını incelemek için kod yazmayı öğrenin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: adf73dde-1e52-4df3-9929-2e0670e28e16
ms.openlocfilehash: 960d72384a7e5f570fc1f94200a7d3b2179343fd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173314"
---
# <a name="interpreting-expressions"></a><span data-ttu-id="1a956-103">İfade Yorumlama</span><span class="sxs-lookup"><span data-stu-id="1a956-103">Interpreting Expressions</span></span>

[<span data-ttu-id="1a956-104">Önceki--Ifadeler yürütülüyor</span><span class="sxs-lookup"><span data-stu-id="1a956-104">Previous -- Executing Expressions</span></span>](expression-trees-execution.md)

<span data-ttu-id="1a956-105">Şimdi bir *ifade ağacının*yapısını incelemek için bazı kodlar yazalım.</span><span class="sxs-lookup"><span data-stu-id="1a956-105">Now, let's write some code to examine the structure of an *expression tree*.</span></span> <span data-ttu-id="1a956-106">Bir ifade ağacındaki her düğüm, öğesinden türetilmiş bir sınıfın nesnesi olur `Expression` .</span><span class="sxs-lookup"><span data-stu-id="1a956-106">Every node in an expression tree will be an object of a class that is derived from `Expression`.</span></span>

<span data-ttu-id="1a956-107">Bu tasarım, bir ifade ağacındaki tüm düğümleri görece düz ileri özyinelemeli bir işlem olarak ziyaret etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a956-107">That design makes visiting all the nodes in an expression tree a relatively straight forward recursive operation.</span></span> <span data-ttu-id="1a956-108">Genel strateji, kök düğümde başlamak ve ne tür bir düğüm olduğunu belirlemektir.</span><span class="sxs-lookup"><span data-stu-id="1a956-108">The general strategy is to start at the root node and determine what kind of node it is.</span></span>

<span data-ttu-id="1a956-109">Düğüm türünün alt öğeleri varsa, yinelemeli olarak alt öğeleri ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="1a956-109">If the node type has children, recursively visit the children.</span></span> <span data-ttu-id="1a956-110">Her alt düğümde, kök düğümde kullanılan işlemi yineleyin: türü belirleme ve türün alt öğeleri varsa, alt öğelerin her birini ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="1a956-110">At each child node, repeat the process used at the root node: determine the type, and if the type has children, visit each of the children.</span></span>

## <a name="examining-an-expression-with-no-children"></a><span data-ttu-id="1a956-111">Alt öğe Içermeyen bir Ifadeyi İnceleme</span><span class="sxs-lookup"><span data-stu-id="1a956-111">Examining an Expression with No Children</span></span>

<span data-ttu-id="1a956-112">Basit bir ifade ağacındaki her bir düğümü ziyaret ederek başlayalım.</span><span class="sxs-lookup"><span data-stu-id="1a956-112">Let's start by visiting each node in a simple expression tree.</span></span>
<span data-ttu-id="1a956-113">Sabit bir ifade oluşturan ve sonra özelliklerini incelediği kod aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1a956-113">Here's the code that creates a constant expression and then examines its properties:</span></span>

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

<span data-ttu-id="1a956-114">Bu işlem şunları yazdırır:</span><span class="sxs-lookup"><span data-stu-id="1a956-114">This will print the following:</span></span>

```output
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

<span data-ttu-id="1a956-115">Şimdi, bu ifadeyi inceleyecek ve ilgili bazı önemli özellikleri yazacak olan kodu yazalım.</span><span class="sxs-lookup"><span data-stu-id="1a956-115">Now, let's write the code that would examine this expression and write out some important properties about it.</span></span> <span data-ttu-id="1a956-116">Bu kod şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="1a956-116">Here's that code:</span></span>

## <a name="examining-a-simple-addition-expression"></a><span data-ttu-id="1a956-117">Basit bir toplama Ifadesi İnceleme</span><span class="sxs-lookup"><span data-stu-id="1a956-117">Examining a simple Addition Expression</span></span>

<span data-ttu-id="1a956-118">Bu bölüme giriş bölümünde ek örnekle başlayalım.</span><span class="sxs-lookup"><span data-stu-id="1a956-118">Let's start with the addition sample from the introduction to this section.</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> <span data-ttu-id="1a956-119">`var`Atamanın sağ tarafı örtük olarak yazıldığından, bu ifade ağacını bildirmek için kullanmıyorum.</span><span class="sxs-lookup"><span data-stu-id="1a956-119">I'm not using `var` to declare this expression tree, as it is not possible because the right-hand side of the assignment is implicitly typed.</span></span>

<span data-ttu-id="1a956-120">Kök düğüm bir `LambdaExpression` .</span><span class="sxs-lookup"><span data-stu-id="1a956-120">The root node is a `LambdaExpression`.</span></span> <span data-ttu-id="1a956-121">İşlecin sağ tarafındaki ilginç kodu almak için, `=>` öğesinin alt öğelerinden birini bulmanız gerekir `LambdaExpression` .</span><span class="sxs-lookup"><span data-stu-id="1a956-121">In order to get the interesting code on the right-hand side of the `=>` operator, you need to find one of the children of the `LambdaExpression`.</span></span> <span data-ttu-id="1a956-122">Bu bölümdeki tüm ifadelerle bunu yapacağız.</span><span class="sxs-lookup"><span data-stu-id="1a956-122">We'll do that with all the expressions in this section.</span></span> <span data-ttu-id="1a956-123">Üst düğüm, öğesinin dönüş türünü bulmamıza yardımcı olur `LambdaExpression` .</span><span class="sxs-lookup"><span data-stu-id="1a956-123">The parent node does help us find the return type of the `LambdaExpression`.</span></span>

<span data-ttu-id="1a956-124">Bu ifadedeki her bir düğümü incelemek için, bir dizi düğümü yinelemeli olarak ziyaret etmemiz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1a956-124">To examine each node in this expression, we'll need to recursively visit a number of nodes.</span></span> <span data-ttu-id="1a956-125">Basit bir ilk uygulama aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1a956-125">Here's a simple first implementation:</span></span>

```csharp
Expression<Func<int, int, int>> addition = (a, b) => a + b;

Console.WriteLine($"This expression is a {addition.NodeType} expression type");
Console.WriteLine($"The name of the lambda is {((addition.Name == null) ? "<null>" : addition.Name)}");
Console.WriteLine($"The return type is {addition.ReturnType.ToString()}");
Console.WriteLine($"The expression has {addition.Parameters.Count} arguments. They are:");
foreach(var argumentExpression in addition.Parameters)
{
    Console.WriteLine($"\tParameter Type: {argumentExpression.Type.ToString()}, Name: {argumentExpression.Name}");
}

var additionBody = (BinaryExpression)addition.Body;
Console.WriteLine($"The body is a {additionBody.NodeType} expression");
Console.WriteLine($"The left side is a {additionBody.Left.NodeType} expression");
var left = (ParameterExpression)additionBody.Left;
Console.WriteLine($"\tParameter Type: {left.Type.ToString()}, Name: {left.Name}");
Console.WriteLine($"The right side is a {additionBody.Right.NodeType} expression");
var right= (ParameterExpression)additionBody.Right;
Console.WriteLine($"\tParameter Type: {right.Type.ToString()}, Name: {right.Name}");
```

<span data-ttu-id="1a956-126">Bu örnek aşağıdaki çıktıyı yazdırır:</span><span class="sxs-lookup"><span data-stu-id="1a956-126">This sample prints the following output:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 arguments. They are:
        Parameter Type: System.Int32, Name: a
        Parameter Type: System.Int32, Name: b
The body is a/an Add expression
The left side is a Parameter expression
        Parameter Type: System.Int32, Name: a
The right side is a Parameter expression
        Parameter Type: System.Int32, Name: b
```

<span data-ttu-id="1a956-127">Yukarıdaki kod örneğinde çok fazla yineleme olduğunu fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="1a956-127">You'll notice a lot of repetition in the code sample above.</span></span>
<span data-ttu-id="1a956-128">Bunu temizleyelim ve daha genel amaçlı bir ifade düğümü ziyaretçisi oluşturalım.</span><span class="sxs-lookup"><span data-stu-id="1a956-128">Let's clean that up and build a more general purpose expression node visitor.</span></span> <span data-ttu-id="1a956-129">Bu, özyinelemeli bir algoritma yazmamızı gerektireceğiz.</span><span class="sxs-lookup"><span data-stu-id="1a956-129">That's going to require us to write a recursive algorithm.</span></span> <span data-ttu-id="1a956-130">Herhangi bir düğüm, alt öğelerine sahip olabilecek bir türde olabilir.</span><span class="sxs-lookup"><span data-stu-id="1a956-130">Any node could be of a type that might have children.</span></span>
<span data-ttu-id="1a956-131">Alt öğeleri olan herhangi bir düğüm, bu alt öğeleri ziyaret etmemizi ve bu düğümün ne olduğunu belirlemenizi ister.</span><span class="sxs-lookup"><span data-stu-id="1a956-131">Any node that has children requires us to visit those children and determine what that node is.</span></span> <span data-ttu-id="1a956-132">Ek işlemleri ziyaret eden özyineleme kullanan temizlenmiş bir sürüm aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1a956-132">Here's the cleaned up version that utilizes recursion to visit the addition operations:</span></span>

```csharp
// Base Visitor class:
public abstract class Visitor
{
    private readonly Expression node;

    protected Visitor(Expression node)
    {
        this.node = node;
    }

    public abstract void Visit(string prefix);

    public ExpressionType NodeType => this.node.NodeType;
    public static Visitor CreateFromExpression(Expression node)
    {
        switch(node.NodeType)
        {
            case ExpressionType.Constant:
                return new ConstantVisitor((ConstantExpression)node);
            case ExpressionType.Lambda:
                return new LambdaVisitor((LambdaExpression)node);
            case ExpressionType.Parameter:
                return new ParameterVisitor((ParameterExpression)node);
            case ExpressionType.Add:
                return new BinaryVisitor((BinaryExpression)node);
            default:
                Console.Error.WriteLine($"Node not processed yet: {node.NodeType}");
                return default(Visitor);
        }
    }
}

// Lambda Visitor
public class LambdaVisitor : Visitor
{
    private readonly LambdaExpression node;
    public LambdaVisitor(LambdaExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression type");
        Console.WriteLine($"{prefix}The name of the lambda is {((node.Name == null) ? "<null>" : node.Name)}");
        Console.WriteLine($"{prefix}The return type is {node.ReturnType.ToString()}");
        Console.WriteLine($"{prefix}The expression has {node.Parameters.Count} argument(s). They are:");
        // Visit each parameter:
        foreach (var argumentExpression in node.Parameters)
        {
            var argumentVisitor = Visitor.CreateFromExpression(argumentExpression);
            argumentVisitor.Visit(prefix + "\t");
        }
        Console.WriteLine($"{prefix}The expression body is:");
        // Visit the body:
        var bodyVisitor = Visitor.CreateFromExpression(node.Body);
        bodyVisitor.Visit(prefix + "\t");
    }
}

// Binary Expression Visitor:
public class BinaryVisitor : Visitor
{
    private readonly BinaryExpression node;
    public BinaryVisitor(BinaryExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This binary expression is a {NodeType} expression");
        var left = Visitor.CreateFromExpression(node.Left);
        Console.WriteLine($"{prefix}The Left argument is:");
        left.Visit(prefix + "\t");
        var right = Visitor.CreateFromExpression(node.Right);
        Console.WriteLine($"{prefix}The Right argument is:");
        right.Visit(prefix + "\t");
    }
}

// Parameter visitor:
public class ParameterVisitor : Visitor
{
    private readonly ParameterExpression node;
    public ParameterVisitor(ParameterExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This is an {NodeType} expression type");
        Console.WriteLine($"{prefix}Type: {node.Type.ToString()}, Name: {node.Name}, ByRef: {node.IsByRef}");
    }
}

// Constant visitor:
public class ConstantVisitor : Visitor
{
    private readonly ConstantExpression node;
    public ConstantVisitor(ConstantExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This is an {NodeType} expression type");
        Console.WriteLine($"{prefix}The type of the constant value is {node.Type}");
        Console.WriteLine($"{prefix}The value of the constant value is {node.Value}");
    }
}
```

<span data-ttu-id="1a956-133">Bu algoritma, rastgele bir şekilde ziyaret edebildikleri bir algoritmanın temelini oluşturur `LambdaExpression` .</span><span class="sxs-lookup"><span data-stu-id="1a956-133">This algorithm is the basis of an algorithm that can visit any arbitrary `LambdaExpression`.</span></span> <span data-ttu-id="1a956-134">Çok sayıda delik vardır; Yani, oluşturduğum kodun yalnızca, karşılaşabileceği ifade ağacı düğümlerinin olası kümelerinin çok küçük bir örneğini arar.</span><span class="sxs-lookup"><span data-stu-id="1a956-134">There are many holes, namely that the code I created only looks for a very small sample of the possible sets of expression tree nodes that it may encounter.</span></span> <span data-ttu-id="1a956-135">Bununla birlikte, ne kadar çok şey ürettiğini de öğrenirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a956-135">However, you can still learn quite a bit from what it produces.</span></span> <span data-ttu-id="1a956-136">(Yönteminde varsayılan durum, `Visitor.CreateFromExpression` Yeni bir düğüm türüyle karşılaşıldığında hata konsoluna bir ileti yazdırır.</span><span class="sxs-lookup"><span data-stu-id="1a956-136">(The default case in the `Visitor.CreateFromExpression` method prints a message to the error console when a new node type is encountered.</span></span> <span data-ttu-id="1a956-137">Bu şekilde, yeni bir ifade türü eklemeyi bilirsiniz.)</span><span class="sxs-lookup"><span data-stu-id="1a956-137">That way, you know to add a new expression type.)</span></span>

<span data-ttu-id="1a956-138">Yukarıda gösterilen ekleme ifadesinde bu ziyaretçisini çalıştırdığınızda aşağıdaki çıktıyı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="1a956-138">When you run this visitor on the addition expression shown above, you get the following output:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
        This is an Parameter expression type
        Type: System.Int32, Name: b, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This is an Parameter expression type
                Type: System.Int32, Name: a, ByRef: False
        The Right argument is:
                This is an Parameter expression type
                Type: System.Int32, Name: b, ByRef: False
```

<span data-ttu-id="1a956-139">Artık daha genel bir ziyaretçi uygulamasına sahip olduğunuza göre, daha birçok farklı tür ifadeyi ziyaret edebilir ve işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a956-139">Now that you've built a more general visitor implementation, you can visit and process many more different types of expressions.</span></span>

## <a name="examining-an-addition-expression-with-many-levels"></a><span data-ttu-id="1a956-140">Birçok düzey içeren bir toplama Ifadesi inceleniyor</span><span class="sxs-lookup"><span data-stu-id="1a956-140">Examining an Addition Expression with Many Levels</span></span>

<span data-ttu-id="1a956-141">Daha karmaşık bir örnek deneyelim, ancak yine de düğüm türlerini yalnızca ekleme ile sınırlandıralım:</span><span class="sxs-lookup"><span data-stu-id="1a956-141">Let's try a more complicated example, yet still limit the node types to addition only:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

<span data-ttu-id="1a956-142">Bunu ziyaretçi algoritmasında çalıştırmadan önce, çıktının ne kadar olabileceğini öğrenmek için düşündüyü deneyin.</span><span class="sxs-lookup"><span data-stu-id="1a956-142">Before you run this on the visitor algorithm, try a thought exercise to work out what the output might be.</span></span> <span data-ttu-id="1a956-143">`+`İşlecin bir *ikili işleç*olduğunu unutmayın: sol ve sağ işlenenleri temsil eden iki alt öğeye sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1a956-143">Remember that the `+` operator is a *binary operator*: it must have two children, representing the left and right operands.</span></span> <span data-ttu-id="1a956-144">Doğru olabilecek bir ağaç oluşturmak için birkaç olası yol vardır:</span><span class="sxs-lookup"><span data-stu-id="1a956-144">There are several possible ways to construct a tree that could be correct:</span></span>

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

<span data-ttu-id="1a956-145">En fazla taahhüdün vurgulanmasını sağlamak için ayrımı iki olası yanıt halinde görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a956-145">You can see the separation into two possible answers to highlight the most promising.</span></span> <span data-ttu-id="1a956-146">İlki, *doğru ilişkilendirilebilir* ifadeleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1a956-146">The first represents *right associative* expressions.</span></span> <span data-ttu-id="1a956-147">İkincisi *sol ilişkilendirilebilir* ifadeleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1a956-147">The second represent *left associative* expressions.</span></span>
<span data-ttu-id="1a956-148">Bu iki biçimin her ikisi de, biçimin rastgele herhangi bir dizi ek ifadeye ölçeklenmesinin avantajına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1a956-148">The advantage of both of those two formats is that the format scales to any arbitrary number of addition expressions.</span></span>

<span data-ttu-id="1a956-149">Bu ifadeyi ziyaretçi aracılığıyla çalıştırırsanız, bu çıktıyı görürsünüz ve basit toplama ifadesinin *ilişkilendirilebilir*olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="1a956-149">If you do run this expression through the visitor, you will see this output, verifying that the simple addition expression is *left associative*.</span></span>

<span data-ttu-id="1a956-150">Bu örneği çalıştırmak ve tam ifade ağacına bakmak için kaynak ifade ağacında bir değişiklik yapmam gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="1a956-150">In order to run this sample, and see the full expression tree, I had to make one change to the source expression tree.</span></span> <span data-ttu-id="1a956-151">İfade ağacı tüm sabitleri içerdiğinde, sonuçta elde edilen ağaç yalnızca sabit değerini içerir `10` .</span><span class="sxs-lookup"><span data-stu-id="1a956-151">When the expression tree contains all constants, the resulting tree simply contains the constant value of `10`.</span></span> <span data-ttu-id="1a956-152">Derleyici tüm ekleme işlemini gerçekleştirir ve ifadeyi en basit biçimine düşürür.</span><span class="sxs-lookup"><span data-stu-id="1a956-152">The compiler performs all the addition and reduces the expression to its simplest form.</span></span> <span data-ttu-id="1a956-153">Özgün ağacı görmek için ifadede yalnızca bir değişken eklemek yeterlidir:</span><span class="sxs-lookup"><span data-stu-id="1a956-153">Simply adding one variable in the expression is sufficient to see the original tree:</span></span>

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

<span data-ttu-id="1a956-154">Bu Sum için bir ziyaretçi oluşturun ve ziyaretçi çalıştırın bu çıktıyı görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="1a956-154">Create a visitor for this sum and run the visitor you'll see this output:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 1 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This binary expression is a Add expression
                        The Left argument is:
                                This is an Constant expression type
                                The type of the constant value is System.Int32
                                The value of the constant value is 1
                        The Right argument is:
                                This is an Parameter expression type
                                Type: System.Int32, Name: a, ByRef: False
                The Right argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 3
        The Right argument is:
                This is an Constant expression type
                The type of the constant value is System.Int32
                The value of the constant value is 4
```

<span data-ttu-id="1a956-155">Diğer örneklerden herhangi birini ziyaretçi kodu aracılığıyla da çalıştırabilir ve hangi ağacın temsil ettiğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a956-155">You can also run any of the other samples through the visitor code and see what tree it represents.</span></span> <span data-ttu-id="1a956-156">`sum3`Yukarıdaki ifadeye örnek olarak (derleyicinin sabiti bilgi işlem yapmasını engellemek için ek bir parametre ile):</span><span class="sxs-lookup"><span data-stu-id="1a956-156">Here's an example of the `sum3` expression above (with an additional parameter to prevent the compiler from computing the constant):</span></span>

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

<span data-ttu-id="1a956-157">Ziyaretçinin çıkışı şöyledir:</span><span class="sxs-lookup"><span data-stu-id="1a956-157">Here's the output from the visitor:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
        This is an Parameter expression type
        Type: System.Int32, Name: b, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 1
                The Right argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: a, ByRef: False
        The Right argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 3
                The Right argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: b, ByRef: False
```

<span data-ttu-id="1a956-158">Ayraçların çıktının parçası olmadığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1a956-158">Notice that the parentheses are not part of the output.</span></span> <span data-ttu-id="1a956-159">İfade ağacında giriş ifadesindeki ayraçları temsil eden hiçbir düğüm yok.</span><span class="sxs-lookup"><span data-stu-id="1a956-159">There are no nodes in the expression tree that represent the parentheses in the input expression.</span></span> <span data-ttu-id="1a956-160">İfade ağacının yapısı, önceliği iletmek için gereken tüm bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="1a956-160">The structure of the expression tree contains all the information necessary to communicate the precedence.</span></span>

## <a name="extending-from-this-sample"></a><span data-ttu-id="1a956-161">Bu örnekten genişletme</span><span class="sxs-lookup"><span data-stu-id="1a956-161">Extending from this sample</span></span>

<span data-ttu-id="1a956-162">Örnek yalnızca en ilkel ifade ağaçları ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="1a956-162">The sample deals with only the most rudimentary expression trees.</span></span> <span data-ttu-id="1a956-163">Bu bölümde gördüğünüz kod yalnızca sabit tamsayıları ve ikili `+` işleci işler.</span><span class="sxs-lookup"><span data-stu-id="1a956-163">The code you've seen in this section only handles constant integers and the binary `+` operator.</span></span> <span data-ttu-id="1a956-164">Son bir örnek olarak, ziyaretçisini daha karmaşık bir ifadeyi işleyecek şekilde güncelleştirelim.</span><span class="sxs-lookup"><span data-stu-id="1a956-164">As a final sample, let's update the visitor to handle a more complicated expression.</span></span> <span data-ttu-id="1a956-165">Bunun için bu işi yapalim:</span><span class="sxs-lookup"><span data-stu-id="1a956-165">Let's make it work for this:</span></span>

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ?
    1 :
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

<span data-ttu-id="1a956-166">Bu kod matematik *çarpınımı* işlevi için olası bir uygulamayı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1a956-166">This code represents one possible implementation for the mathematical *factorial* function.</span></span> <span data-ttu-id="1a956-167">Bu kodu yazdığım şekilde, deyimlere lambda ifadeleri atayarak ifade ağaçları oluşturmanın iki sınırlaması vurgulanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1a956-167">The way I've written this code highlights two limitations of building expression trees by assigning lambda expressions to Expressions.</span></span> <span data-ttu-id="1a956-168">İlk olarak, ifade lambdaları kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1a956-168">First, statement lambdas are not allowed.</span></span> <span data-ttu-id="1a956-169">Bu, döngüleri, blokları, if/else deyimlerini ve C# dilinde ortak olan diğer denetim yapılarını kullanmıyorum anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1a956-169">That means I can't use loops, blocks, if / else statements, and other control structures common in C#.</span></span> <span data-ttu-id="1a956-170">İfadeleri kullanma sınırlıyorum.</span><span class="sxs-lookup"><span data-stu-id="1a956-170">I'm limited to using expressions.</span></span> <span data-ttu-id="1a956-171">İkinci olarak aynı ifadeyi özyinelemeli olarak çağıramıyorum.</span><span class="sxs-lookup"><span data-stu-id="1a956-171">Second, I can't recursively call the same expression.</span></span>
<span data-ttu-id="1a956-172">Ben zaten bir temsilciyiysem, ancak ifade ağaç biçiminde çağıramıyorum.</span><span class="sxs-lookup"><span data-stu-id="1a956-172">I could if it were already a delegate, but I can't call it in its expression tree form.</span></span> <span data-ttu-id="1a956-173">[İfade ağaçları oluşturma](expression-trees-building.md)bölümünde bu sınırlamaları aşmaya yönelik teknikler öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="1a956-173">In the section on [building expression trees](expression-trees-building.md), you'll learn techniques to overcome these limitations.</span></span>

<span data-ttu-id="1a956-174">Bu ifadede, tüm bu türlerin düğümleri ile karşılaşırsınız:</span><span class="sxs-lookup"><span data-stu-id="1a956-174">In this expression, you'll encounter nodes of all these types:</span></span>

1. <span data-ttu-id="1a956-175">Eşittir (ikili ifade)</span><span class="sxs-lookup"><span data-stu-id="1a956-175">Equal (binary expression)</span></span>
2. <span data-ttu-id="1a956-176">Çarp (ikili ifade)</span><span class="sxs-lookup"><span data-stu-id="1a956-176">Multiply (binary expression)</span></span>
3. <span data-ttu-id="1a956-177">Koşullu (?</span><span class="sxs-lookup"><span data-stu-id="1a956-177">Conditional (the ?</span></span> <span data-ttu-id="1a956-178">ifadesini</span><span class="sxs-lookup"><span data-stu-id="1a956-178">: expression)</span></span>
4. <span data-ttu-id="1a956-179">Yöntem çağrısı Ifadesi (çağrı `Range()` ve çağırma `Aggregate()` )</span><span class="sxs-lookup"><span data-stu-id="1a956-179">Method Call Expression (calling `Range()` and `Aggregate()`)</span></span>

<span data-ttu-id="1a956-180">Ziyaretçi algoritmasını değiştirmek için bir yol, bunu yürütmeyi sürdürmek ve yan tümcesine her ulaştığınızda düğüm türünü yazmaktır `default` .</span><span class="sxs-lookup"><span data-stu-id="1a956-180">One way to modify the visitor algorithm is to keep executing it, and write the node type every time you reach your `default` clause.</span></span> <span data-ttu-id="1a956-181">Birkaç yinelemeden sonra potansiyel düğümlerin her birini gördünüz.</span><span class="sxs-lookup"><span data-stu-id="1a956-181">After a few iterations, you'll have seen each of the potential nodes.</span></span> <span data-ttu-id="1a956-182">Ardından, ihtiyacınız olan her şey vardır.</span><span class="sxs-lookup"><span data-stu-id="1a956-182">Then, you have all you need.</span></span> <span data-ttu-id="1a956-183">Sonuç şuna benzer olacaktır:</span><span class="sxs-lookup"><span data-stu-id="1a956-183">The result would be something like this:</span></span>

```csharp
public static Visitor CreateFromExpression(Expression node)
{
    switch(node.NodeType)
    {
        case ExpressionType.Constant:
            return new ConstantVisitor((ConstantExpression)node);
        case ExpressionType.Lambda:
            return new LambdaVisitor((LambdaExpression)node);
        case ExpressionType.Parameter:
            return new ParameterVisitor((ParameterExpression)node);
        case ExpressionType.Add:
        case ExpressionType.Equal:
        case ExpressionType.Multiply:
            return new BinaryVisitor((BinaryExpression)node);
        case ExpressionType.Conditional:
            return new ConditionalVisitor((ConditionalExpression)node);
        case ExpressionType.Call:
            return new MethodCallVisitor((MethodCallExpression)node);
        default:
            Console.Error.WriteLine($"Node not processed yet: {node.NodeType}");
            return default(Visitor);
    }
}
```

<span data-ttu-id="1a956-184">ConditionalVisitor ve MethodCallVisitor bu iki düğümü işler:</span><span class="sxs-lookup"><span data-stu-id="1a956-184">The ConditionalVisitor and MethodCallVisitor process those two nodes:</span></span>

```csharp
public class ConditionalVisitor : Visitor
{
    private readonly ConditionalExpression node;
    public ConditionalVisitor(ConditionalExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression");
        var testVisitor = Visitor.CreateFromExpression(node.Test);
        Console.WriteLine($"{prefix}The Test for this expression is:");
        testVisitor.Visit(prefix + "\t");
        var trueVisitor = Visitor.CreateFromExpression(node.IfTrue);
        Console.WriteLine($"{prefix}The True clause for this expression is:");
        trueVisitor.Visit(prefix + "\t");
        var falseVisitor = Visitor.CreateFromExpression(node.IfFalse);
        Console.WriteLine($"{prefix}The False clause for this expression is:");
        falseVisitor.Visit(prefix + "\t");
    }
}

public class MethodCallVisitor : Visitor
{
    private readonly MethodCallExpression node;
    public MethodCallVisitor(MethodCallExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression");
        if (node.Object == null)
            Console.WriteLine($"{prefix}This is a static method call");
        else
        {
            Console.WriteLine($"{prefix}The receiver (this) is:");
            var receiverVisitor = Visitor.CreateFromExpression(node.Object);
            receiverVisitor.Visit(prefix + "\t");
        }

        var methodInfo = node.Method;
        Console.WriteLine($"{prefix}The method name is {methodInfo.DeclaringType}.{methodInfo.Name}");
        // There is more here, like generic arguments, and so on.
        Console.WriteLine($"{prefix}The Arguments are:");
        foreach(var arg in node.Arguments)
        {
            var argVisitor = Visitor.CreateFromExpression(arg);
            argVisitor.Visit(prefix + "\t");
        }
    }
}
```

<span data-ttu-id="1a956-185">Ve ifade ağacı için çıkış şu şekilde olur:</span><span class="sxs-lookup"><span data-stu-id="1a956-185">And the output for the expression tree would be:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 1 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: n, ByRef: False
The expression body is:
        This expression is a Conditional expression
        The Test for this expression is:
                This binary expression is a Equal expression
                The Left argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: n, ByRef: False
                The Right argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 0
        The True clause for this expression is:
                This is an Constant expression type
                The type of the constant value is System.Int32
                The value of the constant value is 1
        The False clause for this expression is:
                This expression is a Call expression
                This is a static method call
                The method name is System.Linq.Enumerable.Aggregate
                The Arguments are:
                        This expression is a Call expression
                        This is a static method call
                        The method name is System.Linq.Enumerable.Range
                        The Arguments are:
                                This is an Constant expression type
                                The type of the constant value is System.Int32
                                The value of the constant value is 1
                                This is an Parameter expression type
                                Type: System.Int32, Name: n, ByRef: False
                        This expression is a Lambda expression type
                        The name of the lambda is <null>
                        The return type is System.Int32
                        The expression has 2 arguments. They are:
                                This is an Parameter expression type
                                Type: System.Int32, Name: product, ByRef: False
                                This is an Parameter expression type
                                Type: System.Int32, Name: factor, ByRef: False
                        The expression body is:
                                This binary expression is a Multiply expression
                                The Left argument is:
                                        This is an Parameter expression type
                                        Type: System.Int32, Name: product, ByRef: False
                                The Right argument is:
                                        This is an Parameter expression type
                                        Type: System.Int32, Name: factor, ByRef: False
```

## <a name="extending-the-sample-library"></a><span data-ttu-id="1a956-186">Örnek kitaplığı genişletme</span><span class="sxs-lookup"><span data-stu-id="1a956-186">Extending the Sample Library</span></span>

<span data-ttu-id="1a956-187">Bu bölümdeki örneklerde, bir ifade ağacındaki düğümleri ziyaret etmek ve incelemek için temel teknikler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1a956-187">The samples in this section show the core techniques to visit and examine nodes in an expression tree.</span></span> <span data-ttu-id="1a956-188">Bir ifade ağacındaki düğümleri ziyaret ederek ve bunlara erişen temel görevlere odaklanmak için ihtiyacınız olabilecek çok sayıda eylemi glossed.</span><span class="sxs-lookup"><span data-stu-id="1a956-188">I glossed over many actions you might need in order to concentrate on the core tasks of visiting and accessing nodes in an expression tree.</span></span>

<span data-ttu-id="1a956-189">Birincisi, ziyaretçiler yalnızca tamsayı olan sabitleri işler.</span><span class="sxs-lookup"><span data-stu-id="1a956-189">First, the visitors only handle constants that are integers.</span></span> <span data-ttu-id="1a956-190">Sabit değerler başka herhangi bir sayısal tür olabilir ve C# dili bu türler arasındaki dönüşümleri ve yükseltmeleri destekler.</span><span class="sxs-lookup"><span data-stu-id="1a956-190">Constant values could be any other numeric type, and the C# language supports conversions and promotions between those types.</span></span> <span data-ttu-id="1a956-191">Bu kodun daha sağlam bir sürümü tüm bu özellikleri yansıtır.</span><span class="sxs-lookup"><span data-stu-id="1a956-191">A more robust version of this code would mirror all those capabilities.</span></span>

<span data-ttu-id="1a956-192">Son örnek bile olası düğüm türlerinin bir alt kümesini tanır.</span><span class="sxs-lookup"><span data-stu-id="1a956-192">Even the last example recognizes a subset of the possible node types.</span></span>
<span data-ttu-id="1a956-193">Yine de, başarısız olmasına neden olacak çok sayıda ifade akışı yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a956-193">You can still feed it many expressions that will cause it to fail.</span></span>
<span data-ttu-id="1a956-194">Tam bir uygulama, .NET Standard adı altında bulunur <xref:System.Linq.Expressions.ExpressionVisitor> ve tüm olası düğüm türlerini işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="1a956-194">A full implementation is included in the .NET Standard under the name <xref:System.Linq.Expressions.ExpressionVisitor> and can handle all the possible node types.</span></span>

<span data-ttu-id="1a956-195">Son olarak, bu makalede kullandığım kitaplık tanıtım ve öğrenme için oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="1a956-195">Finally, the library I used in this article was built for demonstration and learning.</span></span> <span data-ttu-id="1a956-196">En iyi duruma getirilmemiştir.</span><span class="sxs-lookup"><span data-stu-id="1a956-196">It's not optimized.</span></span> <span data-ttu-id="1a956-197">Bu yapıyı, yapıları ve düğümleri ziyaret etmek ve ne olduğunu çözümlemek için kullanılan teknikleri vurgulamak için yazdım.</span><span class="sxs-lookup"><span data-stu-id="1a956-197">I wrote it to make the structures used clear, and to highlight the techniques used to visit the nodes and analyze what's there.</span></span> <span data-ttu-id="1a956-198">Bir üretim uygulamasının performanstan daha fazla dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1a956-198">A production implementation would pay more attention to performance than I have.</span></span>

<span data-ttu-id="1a956-199">Bu sınırlamalara rağmen, ifade ağaçlarını okuyan ve anlayan algoritmalar yazmak için size iyi bir yol olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1a956-199">Even with those limitations, you should be well on your way to writing algorithms that read and understand expression trees.</span></span>

[<span data-ttu-id="1a956-200">Next--Ifadeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="1a956-200">Next -- Building Expressions</span></span>](expression-trees-building.md)
