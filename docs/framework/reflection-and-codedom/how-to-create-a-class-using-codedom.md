---
title: 'Nasıl yapılır: CodeDOM Kullanarak Sınıf Oluşturma'
description: Kod Belge Nesne Modeli (CodeDOM) kullanarak bir sınıfın nasıl oluşturulacağını açıklayan ayrıntılı bir örneğe bakın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Code Document Object Model, graphs
- Code Document Object Model, creating classes
- graphing with CodeDOM
- CodeDOM, creating classes
- CodeDOM, graphs
ms.assetid: 0ceb70fe-36e1-49bb-922b-e9f615c20a14
ms.openlocfilehash: 7c2cda2bb7cbdb93c27aef91c08f7c7227da7eed
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235707"
---
# <a name="how-to-create-a-class-using-codedom"></a>Nasıl yapılır: CodeDOM Kullanarak Sınıf Oluşturma

Aşağıdaki yordamlarda, iki alanı, üç özellik, bir yöntemi, oluşturucuyu ve bir giriş noktasını içeren bir sınıf üreten bir CodeDOM grafiği oluşturma ve derleme işlemleri gösterilmektedir.  
  
1. Bir sınıf için kaynak kodu oluşturmak üzere CodeDOM kodunu kullanacak bir konsol uygulaması oluşturun.  
  
     Bu örnekte, üretilen sınıf adlandırılır `Sample` ve oluşturulan kod, `CodeDOMCreatedClass` SampleCode adlı bir dosyada adlı bir sınıftır.  
  
2. Oluşturma sınıfında, CodeDOM grafiğini başlatın ve oluşturulan sınıfın üyelerini, oluşturucusunu ve giriş noktasını (yöntemini) tanımlamak için CodeDOM yöntemlerini kullanın `Main` .  
  
     Bu örnekte, oluşturulan sınıfın iki alanı, üç özelliği, bir Oluşturucu, bir yöntemi ve `Main` yöntemi vardır.  
  
3. Oluşturma sınıfında, bir dile özgü kod sağlayıcı oluşturun ve bu kodu <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> grafikten kodu oluşturmak için metodunu çağırın.  
  
4. Kodu oluşturmak için uygulamayı derleyin ve yürütün.  
  
     Bu örnekte, oluşturulan kod SampleCode adlı bir dosyadır. Örnek çıktıyı görmek için kodu derleyin ve yürütün.  
  
### <a name="to-create-the-application-that-will-execute-the-codedom-code"></a>CodeDOM kodunu yürütecek uygulamayı oluşturmak için  
  
- CodeDOM kodunu içeren bir konsol uygulaması sınıfı oluşturun. Sınıfta () ve sınıfına () başvurmak için kullanılan genel alanları tanımlayın <xref:System.CodeDom.CodeCompileUnit> <xref:System.CodeDom.CodeTypeDeclaration> , oluşturulan kaynak dosyanın adını belirtin ve `Main` yöntemi bildirin.  
  
     [!code-csharp[CodeDOM Class Sample Main#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)]
     [!code-vb[CodeDOM Class Sample Main#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]  
  
### <a name="to-initialize-the-codedom-graph"></a>CodeDOM grafiğini başlatmak için  
  
- Konsol uygulaması sınıfının oluşturucusunda, derlemeyi ve sınıfını başlatın ve CodeDOM grafiğine uygun bildirimleri ekleyin.  
  
     [!code-csharp[CodeDOM Class Sample#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)]
     [!code-vb[CodeDOM Class Sample#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]  
  
### <a name="to-add-members-to-the-codedom-graph"></a>CodeDOM grafiğine üye eklemek için  
  
- Sınıfının özelliğine nesneler ekleyerek CodeDOM grafiğine alanlar ekleyin <xref:System.CodeDom.CodeMemberField> <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> .  
  
     [!code-csharp[CodeDOM Class Sample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)]
     [!code-vb[CodeDOM Class Sample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]  
  
- Sınıfının özelliğine nesneler ekleyerek CodeDOM grafiğine özellikler ekleyin <xref:System.CodeDom.CodeMemberProperty> <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> .  
  
     [!code-csharp[CodeDOM Class Sample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)]
     [!code-vb[CodeDOM Class Sample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]  
  
- Sınıfının özelliğine bir nesne ekleyerek CodeDOM grafiğine bir yöntem ekleyin <xref:System.CodeDom.CodeMemberMethod> <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> .  
  
     [!code-csharp[CodeDOM Class Sample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)]
     [!code-vb[CodeDOM Class Sample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]  
  
- Sınıfının özelliğine bir nesne ekleyerek CodeDOM grafiğine bir Oluşturucu ekleyin <xref:System.CodeDom.CodeConstructor> <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> .  
  
     [!code-csharp[CodeDOM Class Sample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)]
     [!code-vb[CodeDOM Class Sample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]  
  
- Sınıfının özelliğine bir nesne ekleyerek CodeDOM grafiğine bir giriş noktası ekleyin <xref:System.CodeDom.CodeEntryPointMethod> <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> .  
  
     [!code-csharp[CodeDOM Class Sample#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)]
     [!code-vb[CodeDOM Class Sample#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]  
  
### <a name="to-generate-the-code-from-the-codedom-graph"></a>CodeDOM grafiğinden kodu oluşturmak için  
  
- Yöntemini çağırarak CodeDOM grafiğinden kaynak kodu oluşturun <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> .  
  
     [!code-csharp[CodeDOM Class Sample#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)]
     [!code-vb[CodeDOM Class Sample#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]  
  
### <a name="to-create-the-graph-and-generate-the-code"></a>Grafiği oluşturmak ve kodu oluşturmak için  
  
1. Önceki adımlarda oluşturulan yöntemleri `Main` ilk adımda tanımlanan yönteme ekleyin.  
  
     [!code-csharp[CodeDOM Class Sample#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)]
     [!code-vb[CodeDOM Class Sample#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]  
  
2. Oluşturulan sınıfı derleyin ve yürütün.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod örneği, önceki adımlardan kodu gösterir.  
  
 [!code-csharp[CodeDOM Class Sample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)]
 [!code-vb[CodeDOM Class Sample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]  
  
 Yukarıdaki örnek derlenip yürütüldüğünde, aşağıdaki kaynak kodu üretir.  
  
 [!code-csharp[CodeDOM Class Sample#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)]
 [!code-vb[CodeDOM Class Sample#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]  
  
 Oluşturulan kaynak kodu derlendiğinde ve yürütüldüğünde aşağıdaki çıktıyı üretir.  
  
```output
The object:  
 width = 5.3,  
 height = 6.9,  
 area = 36.57  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- Bu kod örneği, `FullTrust` izin kümesinin başarıyla yürütülmesine gerek duyar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [CodeDOM'yi Kullanma](using-the-codedom.md)
- [CodeDOM Grafiğinden Kaynak Kodu Oluşturma ve Derleme](generating-and-compiling-source-code-from-a-codedom-graph.md)
