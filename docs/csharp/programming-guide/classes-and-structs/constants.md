---
title: Sabitler- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
ms.openlocfilehash: 0abb728c58d50e3d7709d680dd91794c4be6afef
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705749"
---
# <a name="constants-c-programming-guide"></a>Sabitler (C# Programlama Kılavuzu)
Sabitler, derleme zamanında bilinen ve programın ömrü boyunca değişmeyen sabit değerlerdir. Sabitler [const](../../language-reference/keywords/const.md) değiştiricisi ile bildirilmiştir. Yalnızca C# yerleşik türler (<xref:System.Object?displayProperty=nameWithType>hariç) `const`olarak bildirilemez. Yerleşik türlerin listesi için bkz. [Yerleşik türler tablosu](../../language-reference/keywords/built-in-types-table.md). Sınıflar, yapılar ve diziler dahil Kullanıcı tanımlı türler `const`olamaz. Çalışma zamanında bir kez başlatılan bir sınıf, yapı veya dizi oluşturmak için [salt okunur](../../language-reference/keywords/readonly.md) değiştiricisini kullanın (örneğin, bir oluşturucuda) ve bundan sonra değiştirilemez.  
  
 C#`const` yöntemleri, özellikleri veya olayları desteklemez.  
  
 Sabit listesi türü, integral yerleşik türler (örneğin `int`, `uint`, `long`vb.) için adlandırılmış sabitler tanımlamanızı sağlar. Daha fazla bilgi için bkz. [enum](../../language-reference/builtin-types/enum.md).  
  
 Sabitler, bildirildiği için başlatılmalıdır. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#64](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#64)]  
  
 Bu örnekte, sabit `months` her zaman 12 ' dir ve sınıfın kendisi tarafından bile değiştirilemez. Aslında, derleyici C# kaynak kodunda bir sabit tanımlayıcıyla karşılaştığında (örneğin, `months`), değişmez değer değerini doğrudan ürettiği ara DIL (IL) koduna koyar. Çalışma zamanında bir sabitle ilişkili değişken adresi olmadığından `const` alanlar başvuruya göre geçirilemez ve bir ifadede l değeri olarak görünemez.  
  
> [!NOTE]
> Dll 'Ler gibi başka bir kodda tanımlanan sabit değerlere başvurduğunuzda dikkatli olun. Yeni bir DLL sürümü sabit için yeni bir değer tanımlıyorsa, programınız yeni sürüme yeniden derlenene kadar eski değişmez değeri de tutar.  
  
 Aynı türden birden fazla sabit aynı anda bildirilebilecek, örneğin:  
  
 [!code-csharp[csProgGuideObjects#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#65)]  
  
 Bir sabiti başlatmak için kullanılan ifade, döngüsel başvuru oluşturmayan başka bir sabite başvurabilir. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#66](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#66)]  
  
 Sabitler, [genel](../../language-reference/keywords/public.md), [özel](../../language-reference/keywords/private.md), [korumalı](../../language-reference/keywords/protected.md), [dahili](../../language-reference/keywords/internal.md), [korunan iç](../../language-reference/keywords/protected-internal.md) veya [özel korumalı](../../language-reference/keywords/private-protected.md)olarak işaretlenebilir. Bu erişim değiştiricileri, sınıfın kullanıcılarının sabitine nasıl erişekullanabileceğinizi tanımlar. Daha fazla bilgi için bkz. [erişim değiştiricileri](./access-modifiers.md).  
  
 Sabitlere [statik](../../language-reference/keywords/static.md) alanlar gibi erişilir çünkü sabit değeri, türün tüm örnekleri için aynı. Bunları bildirmek için `static` anahtar sözcüğünü kullanmayın. Sabiti tanımlayan sınıfta olmayan ifadeler, sabit erişim için sınıf adı, nokta ve sabitin adını kullanmalıdır. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#67](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#67)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](./index.md)
- [Veri Erişimi](./properties.md)
- [Türler](../types/index.md)
- [readonly](../../language-reference/keywords/readonly.md)
- [Birinci C# bölümde kullanılabilirlik kullanılabilirliği: tür değiştirici kullanılabilirliği](https://blogs.msdn.microsoft.com/ericlippert/2007/11/13/immutability-in-c-part-one-kinds-of-immutability)
