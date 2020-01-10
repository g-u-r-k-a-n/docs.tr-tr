---
title: Arabirimler- C# Programlama Kılavuzu
ms.date: 08/21/2018
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
ms.openlocfilehash: 3187b8b94c6e46ec13312fc31ac1ed9852199d6b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714619"
---
# <a name="interfaces-c-programming-guide"></a>Arabirimler (C# Programlama Kılavuzu)

Bir arabirim, soyut olmayan bir [sınıfın](../../language-reference/keywords/class.md) veya [yapının](../../language-reference/keywords/struct.md) uygulanması gereken ilgili işlevler grubu için tanımlar içerir.
  
Arabirimleri kullanarak, örneğin, bir sınıftaki birden çok kaynaktan davranış ekleyebilirsiniz. Dil, sınıfların birden çok C# devralınmasını desteklemediğinden bu özellik önemlidir. Bunlara ek olarak, başka bir struct veya sınıftan gerçekten devralmadıklarından yapılar için devralmayı taklit etmek istiyorsanız bir arabirim kullanmanız gerekir.  
  
[Arabirim anahtar sözcüğünü](../../language-reference/keywords/interface.md) kullanarak bir arabirim tanımlarsınız. Aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[csProgGuideInheritance#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#47)]  

Yapının adı geçerli C# bir [tanımlayıcı adı](../inside-a-program/identifier-names.md)olmalıdır. Kural gereği, arabirim adları büyük `I`başlar.

<xref:System.IEquatable%601> arabirimini uygulayan herhangi bir sınıf veya yapı, arabirimin belirttiği imzayla eşleşen bir <xref:System.IEquatable%601.Equals%2A> yöntemi tanımı içermelidir. Sonuç olarak, sınıfının bir örneğinin aynı sınıfın başka bir örneğine eşit olup olmadığını belirleyebildiği bir `Equals` yöntemi içermesi için `IEquatable<T>` uygulayan bir sınıf üzerinde sayım yapabilirsiniz.  
  
`IEquatable<T>` tanımı `Equals`için bir uygulama sağlamaz. Bir sınıf veya yapı birden çok arabirim uygulayabilir, ancak bir sınıf yalnızca tek bir sınıftan devralınabilir.
  
Soyut sınıflar hakkında daha fazla bilgi için bkz. [soyut ve korumalı sınıflar ve sınıf üyeleri](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
Arabirimler Yöntemler, özellikler, olaylar, Dizin oluşturucular veya bu dört üye türlerinin herhangi bir birleşimini içerebilir. Örneklere bağlantılar için [Ilgili bölümler](./index.md#BKMK_RelatedSections)bölümüne bakın. Arabirim, sabitler, alanlar, işleçler, örnek oluşturucular, sonlandırıcılar veya türler içeremez. Arabirim üyeleri otomatik olarak geneldir ve erişim değiştiricileri içeremez. Üyeler de [statik](../../language-reference/keywords/static.md)olamaz.  
  
Bir arabirim üyesini uygulamak için, uygulama sınıfının karşılık gelen üyesi ortak, statik değil olmalıdır ve arabirim üyesiyle aynı ada ve imzaya sahip olmalıdır.  
  
Bir sınıf veya yapı bir arabirim uygularsa, sınıf veya yapı, arabirimin tanımladığı tüm Üyeler için bir uygulama sağlamalıdır. Arabirimin kendisi bir sınıf veya yapının, temel sınıf işlevini devraldığı şekilde devraldığı bir işlevsellik sağlamaz. Ancak, bir temel sınıf bir arabirim uygularsa, taban sınıftan türetilmiş herhangi bir sınıf bu uygulamayı devralır.  
  
Aşağıdaki örnek, <xref:System.IEquatable%601> arabiriminin bir uygulamasını gösterir. Uygulama sınıfı `Car`, <xref:System.IEquatable%601.Equals%2A> yönteminin bir uygulamasını sağlamalıdır.  
  
 [!code-csharp[csProgGuideInheritance#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#48)]  
  
Bir sınıfın özellikleri ve Dizin oluşturucular, bir arabirimde tanımlı bir özellik veya Dizin Oluşturucu için ek erişimciler tanımlayabilir. Örneğin, bir arabirim bir [Get](../../language-reference/keywords/get.md) erişimcisine sahip bir özellik bildirebilir. Arabirimini uygulayan sınıf, hem `get` hem de [set](../../language-reference/keywords/set.md) erişimcisi ile aynı özelliği bildirebilir. Ancak, özellik veya Dizin Oluşturucu açık uygulama kullanıyorsa, erişimcilerinin eşleşmesi gerekir. Açık uygulama hakkında daha fazla bilgi için bkz. [Açık arabirim uygulama](explicit-interface-implementation.md) ve [arabirim özellikleri](../classes-and-structs/interface-properties.md).  

Arabirimler, diğer arabirimlerden devralınabilir. Bir sınıf, devraldığı temel sınıflar veya diğer arabirimlerin devraldığı arabirimler aracılığıyla birden çok kez arabirim içerebilir. Ancak, sınıfı bir arabirimin uygulamasını yalnızca bir kez ve yalnızca sınıf sınıfın tanımının bir parçası olarak bildirir (`class ClassName : InterfaceName`). Arabirimi uygulayan bir temel sınıf devralmış olduğunuz için arabirim devralınmışsa, taban sınıf arabirimin üyelerinin uygulanmasını sağlar. Ancak, türetilen sınıf devralınan uygulamayı kullanmak yerine herhangi bir sanal arabirim üyesini yeniden uygulayabilir.  
  
Bir temel sınıf, sanal Üyeler kullanarak arabirim üyeleri de uygulayabilir. Bu durumda, türetilmiş bir sınıf sanal üyeleri geçersiz kılarak arabirim davranışını değiştirebilir. Sanal üyeler hakkında daha fazla bilgi için bkz. çok [biçimlilik](../classes-and-structs/polymorphism.md).  
  
## <a name="interfaces-summary"></a>Arabirimler Özeti

Bir arabirim aşağıdaki özelliklere sahiptir:  

- Bir arabirim, yalnızca soyut üyelere sahip bir soyut temel sınıf gibidir. Arabirimi uygulayan herhangi bir sınıf veya yapının tüm üyelerini uygulaması gerekir.
- Arabirim doğrudan başlatılamaz. Üyeleri, arabirimini uygulayan herhangi bir sınıf veya yapı tarafından uygulanır.
- Arabirimler olay, Dizin oluşturucular, Yöntemler ve özellikler içerebilir.
- Arabirimler yöntemlerin bir uygulamasını içermez (8,0 sürümünde C# arabirimler [Yöntemler için varsayılan uygulamaya](../../whats-new/csharp-8.md#default-interface-methods)sahip olabilir).
- Bir sınıf veya yapı, birden çok arabirim uygulayabilir. Bir sınıf bir temel sınıfı devralınabilir ve ayrıca bir veya daha fazla arabirim uygulayabilir.

## <a name="in-this-section"></a>Bu bölümde

[Belirtik Arabirim Kullanma](explicit-interface-implementation.md)  
 Bir arabirime özgü bir sınıf üyesinin nasıl oluşturulacağını açıklar.  
  
 [Arabirim üyelerini açıkça uygulama](how-to-explicitly-implement-interface-members.md)  
 Arabirimlerin üyelerini açıkça nasıl uygulayacağınızı gösteren bir örnek sağlar.  
  
 [İki arabirimin üyelerini açıkça uygulama](how-to-explicitly-implement-members-of-two-interfaces.md)  
 Devralma ile arabirimlerin üyelerini açıkça nasıl uygulayabileceğinizi gösteren bir örnek sağlar.  
  
## <a name="BKMK_RelatedSections"></a>İlgili bölümler

- [Arabirim Özellikleri](../classes-and-structs/interface-properties.md)  
- [Arabirimlerdeki Dizin Oluşturucular](../indexers/indexers-in-interfaces.md)  
- [Arabirim olaylarını uygulama](../events/how-to-implement-interface-events.md)
- [Sınıflar ve Yapılar](../classes-and-structs/index.md)  
- [Devralma](../classes-and-structs/inheritance.md)  
- [Yöntemler](../classes-and-structs/methods.md)  
- [Çok biçimlilik](../classes-and-structs/polymorphism.md)  
- [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [Veri Erişimi](../classes-and-structs/properties.md)  
- [Olaylar](../events/index.md)  
- [Dizin Oluşturucular](../indexers/index.md)  
  
## <a name="featured-book-chapter"></a>Öne çıkan kitap bölümü

[Öğrenme C# 3,0 ' deki arabirimler: C# 3,0 temelleri ana](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v%253dorm.10%29) [](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652489%28v%3Dorm.10%29)

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Devralma](../classes-and-structs/inheritance.md)
- [Tanımlayıcı adları](../inside-a-program/identifier-names.md)
