---
description: 'Daha fazla bilgi edinin: özniteliklere genel bakış (Visual Basic)'
title: Özniteliklere genel bakış
ms.date: 07/20/2015
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
ms.openlocfilehash: f25e69452f0af1c89af667619e673f8906704d1f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100437728"
---
# <a name="attributes-overview-visual-basic"></a>Özniteliklere genel bakış (Visual Basic)

Öznitelikler, meta verileri veya bildirime dayalı bilgilerin kod (derlemeler, türler, Yöntemler, özellikler, vb.) ile ilişkilendirilmesi için güçlü bir yöntem sağlar. Bir öznitelik bir program varlığıyla ilişkilendirildikten sonra, çalışma zamanında, *yansıma* adlı bir teknik kullanarak öznitelik sorgulanabilir. Daha fazla bilgi için bkz. [yansıma (Visual Basic)](../reflection.md).

Öznitelikler aşağıdaki özelliklere sahiptir:

- Öznitelikler, programınıza meta veri ekler. *Meta veriler* , bir programda tanımlanan türlerle ilgili bilgiler. Tüm .NET derlemeleri, derlemede tanımlanan türleri ve tür üyelerini açıklayan, belirtilen meta veri kümesini içerir. Gerekli ek bilgileri belirtmek için özel öznitelikler ekleyebilirsiniz. Daha fazla bilgi için bkz. [özel öznitelikler oluşturma (Visual Basic)](creating-custom-attributes.md).

- Tüm derlemeler, modüller veya sınıflar ve özellikler gibi daha küçük program öğelerine bir veya daha fazla öznitelik uygulayabilirsiniz.

- Öznitelikler bağımsız değişkenleri Yöntemler ve özelliklerle aynı şekilde kabul edebilir.

- Programınız, yansıma kullanarak kendi meta verilerini veya diğer programlardaki meta verileri inceleyebilir. Daha fazla bilgi için bkz. [yansıma kullanarak özniteliklere erişme (Visual Basic)](accessing-attributes-by-using-reflection.md).

## <a name="using-attributes"></a>Öznitelikleri Kullanma

Öznitelikler, her bir bildirime yerleştirilebilecek, ancak belirli bir öznitelik, geçerli olduğu bildirimlerin türlerini kısıtlayabilir. Visual Basic, bir öznitelik açılı ayraçlar () içine alınır \< > . Aynı satırda, uygulandığı öğeden hemen önce gelmelidir.

Bu örnekte, <xref:System.SerializableAttribute> özniteliği bir sınıfa belirli bir özelliği uygulamak için kullanılır:

```vb
<System.Serializable()> Public Class SampleClass
    ' Objects of this type can be serialized.
End Class
```

 Özniteliğine sahip bir yöntem <xref:System.Runtime.InteropServices.DllImportAttribute> şöyle bildirilmiştir:

```vb
Imports System.Runtime.InteropServices
```

```vb
<System.Runtime.InteropServices.DllImport("user32.dll")>
Sub SampleMethod()
End Sub
```

Bir bildirime birden fazla öznitelik yerleştirilebilecek:

```vb
Imports System.Runtime.InteropServices
```

```vb
Sub MethodA(<[In](), Out()> ByVal x As Double)
End Sub
Sub MethodB(<Out(), [In]()> ByVal x As Double)
End Sub
```

Bazı öznitelikler, belirli bir varlık için birden çok kez belirtilebilir. Bu tür bir çok kullanım özniteliğine örnek <xref:System.Diagnostics.ConditionalAttribute> :

```vb
<Conditional("DEBUG"), Conditional("TEST1")>
Sub TraceMethod()
End Sub
```

> [!NOTE]
> Kurala göre, tüm öznitelik adları, .NET Framework diğer öğelerden ayırt edilebilmesi için "Attribute" kelimesiyle biter. Ancak, koddaki öznitelikleri kullanırken öznitelik sonekini belirtmeniz gerekmez. Örneğin, `[DllImport]` öğesine eşdeğerdir `[DllImportAttribute]` , ancak `DllImportAttribute` .NET Framework özniteliğin gerçek adıdır.

### <a name="attribute-parameters"></a>Öznitelik parametreleri

Birçok özniteliğin, konumsal, adlandırılmamış veya adlandırılmış olabilecek parametreleri vardır. Herhangi bir Konumsal parametre belirli bir sırada belirtilmelidir ve atlanamaz; Adlandırılmış parametreler isteğe bağlıdır ve herhangi bir sırada belirtilebilir. Konumsal parametreler önce belirtilmiştir. Örneğin, bu üç öznitelik eşdeğerdir:

```vb
<DllImport("user32.dll")>
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>
```

İlk parametre olan DLL adı, konumsal ve her zaman ilk olarak gelir; diğerleri olarak adlandırılır. Bu durumda, her ikisi de varsayılan olarak false değerine sahiptir, bu nedenle bu parametreler atlanabilir. Varsayılan parametre değerleri hakkında bilgi için bağımsız özniteliğin belgelerine bakın.

### <a name="attribute-targets"></a>Öznitelik Hedefleri

Bir özniteliğin *hedefi* , özniteliğin uygulandığı varlıktır. Örneğin, bir öznitelik bir sınıfa, belirli bir yönteme veya bir derlemenin tamamına uygulanabilir. Varsayılan olarak, bir öznitelik, kendisinden önce gelen öğe için geçerlidir. Ancak, bir özniteliğin bir yönteme mi, yoksa parametresine mi, yoksa dönüş değerine mi uygulanacağını de açıkça belirleyebilirsiniz.

Bir öznitelik hedefini açıkça tanımlamak için aşağıdaki sözdizimini kullanın:

```vb
<target : attribute-list>
```

Olası `target` değerler listesi aşağıdaki tabloda gösterilmiştir.

|Hedef değer|Şunlara uygulanır|
|------------------|----------------|
|`assembly`|Tüm derleme|
|`module`|Geçerli derleme modülü (bir Visual Basic modülünden farklı)|

 Aşağıdaki örnek, derlemeler ve modüllere özniteliklerin nasıl uygulanacağını gösterir. Daha fazla bilgi için bkz. [ortak öznitelikler (Visual Basic)](common-attributes.md).

```vb
Imports System.Reflection
<Assembly: AssemblyTitleAttribute("Production assembly 4"),
Module: CLSCompliant(True)>
```

## <a name="common-uses-for-attributes"></a>Öznitelikler için ortak kullanımlar

Aşağıdaki listede, kod içindeki özniteliklerin yaygın kullanımları yer almaktadır:

- `WebMethod`YÖNTEMIN SOAP protokolü üzerinden çağrılabilir olması gerektiğini göstermek Için Web hizmetlerindeki özniteliği kullanılarak yöntemleri işaretleme. Daha fazla bilgi için bkz. <xref:System.Web.Services.WebMethodAttribute>.

- Yerel kodla birlikte çalışırken yöntem parametrelerinin nasıl hazırlanacağını açıklama. Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.MarshalAsAttribute>.

- Sınıflar, Yöntemler ve arabirimler için COM özelliklerini açıklama.

- Sınıfını kullanarak yönetilmeyen kodu çağırma <xref:System.Runtime.InteropServices.DllImportAttribute> .

- Derlemenizi başlık, sürüm, açıklama veya ticari marka açısından açıklama.

- Bir sınıfın kalıcılığı için hangi üyelerin serileştirmek gerektiğini açıklama.

- XML ile serileştirme için sınıf üyeleri ve XML düğümleri arasında nasıl eşleme yapılacağı açıklanır.

- Yöntemler için güvenlik gereksinimlerini açıklama.

- Güvenliği zorlamak için kullanılan özellikleri belirtme.

- Tam zamanında (JıT) derleyicisine yönelik iyileştirmeler denetleniyor, böylece kod hata ayıklama için kolay kalır.

- Bir yönteme arayan hakkında bilgi alma.

## <a name="related-sections"></a>İlgili Bölümler

Daha fazla bilgi için bkz.

- [Özel öznitelikler oluşturma (Visual Basic)](creating-custom-attributes.md)

- [Yansıma kullanarak özniteliklere erişme (Visual Basic)](accessing-attributes-by-using-reflection.md)

- [Nasıl yapılır: öznitelikleri kullanarak C/C++ birleşimi oluşturma (Visual Basic)](how-to-create-a-c-cpp-union-by-using-attributes.md)

- [Ortak öznitelikler (Visual Basic)](common-attributes.md)

- [Arayan bilgileri (Visual Basic)](../caller-information.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Programlama Kılavuzu](../../index.md)
- [Yansıma (Visual Basic)](../reflection.md)
- [Öznitelikler](../../../../standard/attributes/index.md)
