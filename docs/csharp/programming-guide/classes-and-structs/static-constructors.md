---
title: Statik oluşturucular-C# Programlama Kılavuzu
description: C# ' de statik bir Oluşturucu statik verileri başlatır veya ilk örnek oluşturulmadan veya statik üyelere başvurulduktan önce yalnızca bir kez yapılan bir eylem gerçekleştirir.
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: e324b2aa968ff5fdf9c268fa3891f67e8530ff87
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863988"
---
# <a name="static-constructors-c-programming-guide"></a>Statik Oluşturucular (C# Programlama Kılavuzu)
Statik bir Oluşturucu, herhangi bir [statik](../../language-reference/keywords/static.md) veriyi başlatmak veya yalnızca bir kez gerçekleştirilmesi gereken belirli bir eylemi gerçekleştirmek için kullanılır. İlk örnek oluşturulmadan veya herhangi bir statik üyeye başvurulmadan önce bu otomatik olarak çağrılır.  
  
 [!code-csharp[csProgGuideObjects#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#14)]  

## <a name="remarks"></a>Açıklamalar
Statik oluşturucular aşağıdaki özelliklere sahiptir:  
  
- Statik bir Oluşturucu erişim değiştiricileri almaz veya parametrelere sahip değildir.  

- Bir sınıf veya yapı birimi yalnızca bir statik oluşturucuya sahip olabilir.

- Statik oluşturucular devralınamaz veya aşırı yüklenemez.

- Statik bir Oluşturucu doğrudan çağrılamaz ve yalnızca ortak dil çalışma zamanı (CLR) tarafından çağrılabilir. Otomatik olarak çağrılır.

- Programda statik Oluşturucu yürütüldüğünde kullanıcının denetimi yoktur.
  
- Statik bir Oluşturucu, ilk örnek oluşturulmadan veya herhangi bir statik üyeye başvurulmadan önce [sınıfı](../../language-reference/keywords/class.md) başlatmak için otomatik olarak çağrılır. Bir statik oluşturucu, örnek oluşturucudan önce çalışacaktır. Bir olaya atanan statik bir yöntem veya temsilci atandığında, bir türün statik Oluşturucusu çağrılır. Statik alan değişkeni başlatıcıları statik oluşturucunun sınıfında mevcutsa, statik oluşturucunun yürütülmesinden hemen önce sınıf bildiriminde göründükleri metin sırasına göre yürütülür.

- Statik alanları başlatmak için statik bir Oluşturucu sağlamazsanız, tüm statik alanlar varsayılan değer olan [C# türlerinin varsayılan değerlerinde](../../language-reference/builtin-types/default-values.md)listelendiği şekilde başlatılır.
  
- Statik bir Oluşturucu bir özel durum oluşturursa, çalışma zamanı ikinci bir kez çağrılmaz ve programınızın çalıştığı uygulama etki alanının ömrü boyunca tür başlatılmamış olarak kalır. En yaygın olarak, <xref:System.TypeInitializationException> statik bir Oluşturucu bir tür örneklememediğinde veya statik oluşturucu içinde oluşan işlenmeyen bir özel durum için bir özel durum oluşturulur. Kaynak kodunda açıkça tanımlanmayan örtük statik oluşturucular için, sorun giderme ara dil (IL) kodunu denetlemesini gerektirebilir.

- Statik bir oluşturucunun varlığı <xref:System.Reflection.TypeAttributes.BeforeFieldInit> tür özniteliğinin eklenmesini engeller. Bu, çalışma zamanının iyileştirmesini sınırlandırır.

- Olarak belirtilen bir alan `static readonly` , bildiriminin bir parçası olarak veya bir statik oluşturucuda atanabilir. Açık bir statik Oluşturucu gerekli olmadığında, daha iyi çalışma zamanı iyileştirmesi için bir statik Oluşturucu yerine bildiriminde statik alanları başlatın.

> [!Note]
> Doğrudan erişilemeyen halde, açık bir statik oluşturucunun varlığı, başlatma özel durumlarının giderilmesi için yardımcı olmak üzere açıklanmalıdır.

### <a name="usage"></a>Kullanım

- Statik oluşturucuların tipik kullanımı, sınıfın bir günlük dosyası kullanıldığı ve oluşturucunun bu dosyaya giriş yazmak için kullanıldığı durumlarda kullanılır.  
- Statik oluşturucular, Oluşturucu yöntemi çağırabilmesini, yönetilmeyen kod için sarmalayıcı sınıflar oluştururken de kullanışlıdır `LoadLibrary` .  

- Statik oluşturucular, derleme zamanında kısıtlama aracılığıyla denetlenemeyen tür parametresinde çalışma zamanı denetimlerini zorlamak için de kullanışlı bir yerdir (tür parametresi kısıtlamaları).

## <a name="example"></a>Örnek
 Bu örnekte, sınıfının `Bus` statik bir Oluşturucusu vardır. İlk örneği `Bus` oluşturulduğunda ( `bus1` ), sınıfı başlatmak için statik oluşturucu çağrılır. Örnek çıktı, statik oluşturucunun, iki örneği `Bus` oluşturulsa ve örnek Oluşturucu çalışmadan önce çalışmasına rağmen yalnızca bir kez çalıştığını doğrular.  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]

## <a name="c-language-specification"></a>C# dili belirtimi
Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [statik oluşturucular](~/_csharplang/spec/classes.md#static-constructors) bölümüne bakın.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve yapılar](./index.md)
- [Oluşturucular](./constructors.md)
- [Statik Sınıflar ve Statik Sınıf Üyeleri](./static-classes-and-static-class-members.md)
- [Sonlandırıcılar](./destructors.md)
- [Oluşturucu tasarım yönergeleri](../../../standard/design-guidelines/constructor.md#type-constructor-guidelines)
- [Güvenlik Uyarısı-CA2121: statik oluşturucular özel olmalıdır](https://docs.microsoft.com/visualstudio/code-quality/ca2121-static-constructors-should-be-private)
