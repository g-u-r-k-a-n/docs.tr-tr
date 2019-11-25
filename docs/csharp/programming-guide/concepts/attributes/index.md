---
title: Öznitelikler (C#)
ms.date: 04/26/2018
ms.openlocfilehash: 2a07035ea97bb0ff1a8f4793fe8a30d3a42c34a7
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141557"
---
# <a name="attributes-c"></a>Öznitelikler (C#)

Öznitelikler, meta verileri veya bildirime dayalı bilgilerin kod (derlemeler, türler, Yöntemler, özellikler, vb.) ile ilişkilendirilmesi için güçlü bir yöntem sağlar. Bir öznitelik bir program varlığıyla ilişkilendirildikten sonra, çalışma zamanında, *yansıma*adlı bir teknik kullanarak öznitelik sorgulanabilir. Daha fazla bilgi için bkz. [yansımaC#()](../reflection.md).

Öznitelikler aşağıdaki özelliklere sahiptir:

- Öznitelikler, programınıza meta veri ekler. *Meta veriler* , bir programda tanımlanan türlerle ilgili bilgiler. Tüm .NET derlemeleri, derlemede tanımlanan türleri ve tür üyelerini açıklayan, belirtilen meta veri kümesini içerir. Gerekli ek bilgileri belirtmek için özel öznitelikler ekleyebilirsiniz. Daha fazla bilgi için bkz. [özel öznitelikler (C#) oluşturma](creating-custom-attributes.md).
- Tüm derlemeler, modüller veya sınıflar ve özellikler gibi daha küçük program öğelerine bir veya daha fazla öznitelik uygulayabilirsiniz.
- Öznitelikler bağımsız değişkenleri Yöntemler ve özelliklerle aynı şekilde kabul edebilir.
- Programınız, yansıma kullanarak kendi meta verilerini veya diğer programlardaki meta verileri inceleyebilir. Daha fazla bilgi için bkz. [Reflection (C#) kullanarak özniteliklere erişme](accessing-attributes-by-using-reflection.md).

## <a name="using-attributes"></a>Öznitelikleri kullanma

Öznitelikler, her bir bildirime yerleştirilebilecek, ancak belirli bir öznitelik, geçerli olduğu bildirimlerin türlerini kısıtlayabilir. ' C#De, geçerli olduğu varlık bildiriminin üzerine köşeli ayraç ([]) içine alınmış özniteliğin adını yerleştirerek bir özniteliği belirtirsiniz.

Bu örnekte, bir sınıfa belirli bir özelliği uygulamak için <xref:System.SerializableAttribute> özniteliği kullanılır:

[!code-csharp[Using the serializable attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

<xref:System.Runtime.InteropServices.DllImportAttribute> özniteliğine sahip bir yöntem aşağıdaki örnekte olduğu gibi bildirilmiştir:

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

Aşağıdaki örnekte gösterildiği gibi, bir bildirime birden fazla öznitelik yerleştirilebilecek:

[!code-csharp[Including the interop namespace](~/samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](~/samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

Bazı öznitelikler, belirli bir varlık için birden çok kez belirtilebilir. Bu tür bir çok kullanım özniteliğine örnek <xref:System.Diagnostics.ConditionalAttribute>:

[!code-csharp[Using the conditional attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> Kurala göre, tüm öznitelik adları, bunları .NET kitaplıklarında diğer öğelerden ayırt etmek için "Attribute" kelimesiyle biter. Ancak, koddaki öznitelikleri kullanırken öznitelik sonekini belirtmeniz gerekmez. Örneğin, `[DllImport]` `[DllImportAttribute]`eşdeğerdir, ancak `DllImportAttribute` özniteliğin .NET Framework sınıf kitaplığındaki gerçek adıdır.

### <a name="attribute-parameters"></a>Öznitelik parametreleri

Birçok özniteliğin, konumsal, adlandırılmamış veya adlandırılmış olabilecek parametreleri vardır. Herhangi bir Konumsal parametre belirli bir sırada belirtilmelidir ve atlanamaz. Adlandırılmış parametreler isteğe bağlıdır ve herhangi bir sırada belirtilebilir. Konumsal parametreler önce belirtilmiştir. Örneğin, bu üç öznitelik eşdeğerdir:

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

İlk parametre olan DLL adı, konumsal ve her zaman ilk olarak gelir; diğerleri olarak adlandırılır. Bu durumda, her ikisi de varsayılan olarak false değerine sahiptir, bu nedenle bu parametreler atlanabilir. Konumsal parametreler öznitelik oluşturucusunun parametrelerine karşılık gelir. Adlandırılmış ya da isteğe bağlı parametreler, özelliğin özelliklerine veya alanlarına karşılık gelir. Varsayılan parametre değerleri hakkında bilgi için bağımsız özniteliğin belgelerine bakın.

### <a name="attribute-targets"></a>Öznitelik hedefleri

Bir özniteliğin *hedefi* , özniteliğin uygulandığı varlıktır. Örneğin, bir öznitelik bir sınıfa, belirli bir yönteme veya bir derlemenin tamamına uygulanabilir. Varsayılan olarak, bir öznitelik, onu izleyen öğesi için geçerlidir. Ancak, bir özniteliğin bir yönteme mi, yoksa parametresine mi, yoksa dönüş değerine mi uygulanacağını de açıkça belirleyebilirsiniz.

Bir öznitelik hedefini açıkça tanımlamak için aşağıdaki sözdizimini kullanın:

```csharp
[target : attribute-list]
```

Olası `target` değerleri listesi aşağıdaki tabloda gösterilmiştir.

|Hedef değer|Uygulandığı öğe:|
|------------------|----------------|
|`assembly`|Tüm derleme|
|`module`|Geçerli derleme modülü|
|`field`|Bir sınıf veya yapı içindeki alan|
|`event`|Olay|
|`method`|Yöntem veya `get` ve `set` Özellik erişimcileri|
|`param`|Yöntem parametreleri veya `set` özellik erişimcisi parametreleri|
|`property`|Özellik|
|`return`|Metodun, özellik dizin oluşturucusunun veya `get` Özellik erişimcisinin dönüş değeri|
|`type`|Struct, Class, Interface, Enum veya Delegate|

[Otomatik uygulanan bir özellik](../../../properties.md)için oluşturulan yedekleme alanına bir öznitelik uygulamak üzere `field` Target değerini belirtirsiniz.

Aşağıdaki örnek, derlemeler ve modüllere özniteliklerin nasıl uygulanacağını gösterir. Daha fazla bilgi için bkz. [ortak özniteliklerC#()](common-attributes.md).

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

Aşağıdaki örnek, içindeki C#yöntemlere, yöntem parametrelerine ve yöntem dönüş değerlerine özniteliklerin nasıl uygulanacağını gösterir.

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> `ValidatedContract` tanımlanan hedeflerden bağımsız olarak, `ValidatedContract` yalnızca dönüş değerleri uygulamak üzere tanımlansa bile `return` hedefi belirtilmelidir. Diğer bir deyişle, derleyici belirsiz öznitelik hedeflerini çözümlemek için `AttributeUsage` bilgilerini kullanmaz. Daha fazla bilgi için bkz. [AttributeUsageC#()](attributeusage.md).

## <a name="common-uses-for-attributes"></a>Öznitelikler için ortak kullanımlar

Aşağıdaki listede, kod içindeki özniteliklerin yaygın kullanımları yer almaktadır:

- Metodun SOAP protokolü üzerinden çağrılabilir olması gerektiğini göstermek için Web hizmetlerindeki `WebMethod` özniteliğini kullanarak yöntemleri işaretleme. Daha fazla bilgi için bkz. <xref:System.Web.Services.WebMethodAttribute>.
- Yerel kodla birlikte çalışırken yöntem parametrelerinin nasıl hazırlanacağını açıklama. Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.MarshalAsAttribute>.
- Sınıflar, Yöntemler ve arabirimler için COM özelliklerini açıklama.
- Yönetilmeyen kod <xref:System.Runtime.InteropServices.DllImportAttribute> sınıfını kullanarak çağrılıyor.
- Derlemenizi başlık, sürüm, açıklama veya ticari marka açısından açıklama.
- Bir sınıfın kalıcılığı için hangi üyelerin serileştirmek gerektiğini açıklama.
- XML ile serileştirme için sınıf üyeleri ve XML düğümleri arasında nasıl eşleme yapılacağı açıklanır.
- Yöntemler için güvenlik gereksinimlerini açıklama.
- Güvenliği zorlamak için kullanılan özellikleri belirtme.
- Tam zamanında (JıT) derleyicisine yönelik iyileştirmeler denetleniyor, böylece kod hata ayıklama için kolay kalır.
- Bir yönteme arayan hakkında bilgi alma.

## <a name="related-sections"></a>İlgili bölümler

Daha fazla bilgi için bkz.:

- [Özel öznitelikler (C#) oluşturma](creating-custom-attributes.md)  
- [Yansıma (C#) kullanarak özniteliklere erişme](accessing-attributes-by-using-reflection.md)  
- [Öznitelikleri kullanarak C/C++ Union oluşturma ()C#](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [Ortak öznitelikler (C#)](common-attributes.md)  
- [Arayan bilgileri (C#)](../caller-information.md)  

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../index.md)
- [Yansıma (C#)](../reflection.md)
- [Öznitelikler](../../../../standard/attributes/index.md)
- [İçindeki öznitelikleri kullanmaC#](../../../tutorials/attributes.md)
