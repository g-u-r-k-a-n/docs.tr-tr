---
title: <Type> öğesi (.NET Native)
ms.date: 03/30/2017
ms.assetid: 1e88d368-a886-4f1e-8eb6-6127979a9fce
ms.openlocfilehash: 4e88b49b82513079ddcf6f0bafe02d44235a406a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091850"
---
# <a name="type-element-net-native"></a>\<türü > öğesi (.NET Native)

Çalışma zamanı ilkesini sınıf veya yapı gibi belirli bir türe uygular.

## <a name="syntax"></a>Sözdizimi

```xml
<Type Name="type_name"
      Activate="policy_type"
      Browse="policy_type"
      Dynamic="policy_type"
      Serialize="policy_type"
      DataContractSerializer="policy_setting"
      DataContractJsonSerializer="policy_setting"
      XmlSerializer="policy_setting"
      MarshalObject="policy_setting"
      MarshalDelegate="policy_setting"
      MarshalStructure="policy_setting" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Öznitelik türü|Açıklama|
|---------------|--------------------|-----------------|
|`Name`|Genel|Gerekli öznitelik. Tür adını belirtir.|
|`Activate`|Yansıma|İsteğe bağlı öznitelik. Örneklerin etkinleştirilmesini sağlamak için oluşturuculara çalışma zamanı erişimini denetler.|
|`Browse`|Yansıma|İsteğe bağlı öznitelik. Program öğeleri hakkında bilgi sorgulamayı denetler, ancak hiçbir çalışma zamanı erişimini etkinleştirmez.|
|`Dynamic`|Yansıma|İsteğe bağlı öznitelik. Dinamik programlamayı etkinleştirmek için oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar dahil olmak üzere tüm tür üyelerine çalışma zamanı erişimini denetler.|
|`Serialize`|Serileştirme|İsteğe bağlı öznitelik. Tür örneklerinin, Newtonsoft JSON serileştirici gibi kitaplıklar tarafından serileştirilmesi ve seri durumdan çıkarılmakta olması için oluşturuculara, alanlara ve özelliklere çalışma zamanı erişimini denetler.|
|`DataContractSerializer`|Serileştirme|İsteğe bağlı öznitelik. <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfını kullanan serileştirme için ilkeyi denetler.|
|`DataContractJsonSerializer`|Serileştirme|İsteğe bağlı öznitelik. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> sınıfını kullanan JSON serileştirme için ilkeyi denetler.|
|`XmlSerializer`|Serileştirme|İsteğe bağlı öznitelik. <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfını kullanan XML serileştirme ilkesini denetler.|
|`MarshalObject`|Interop|İsteğe bağlı öznitelik. Windows Çalışma Zamanı ve COM 'a başvuru türlerini hazırlama ilkesini denetler.|
|`MarshalDelegate`|Interop|İsteğe bağlı öznitelik. Temsilci türlerini yerel koda işlev işaretçileri olarak hazırlama ilkesini denetler.|
|`MarshalStructure`|Interop|İsteğe bağlı öznitelik. Değer türlerini yerel koda hazırlama ilkesini denetler.|

## <a name="name-attribute"></a>Ad özniteliği

|Değer|Açıklama|
|-----------|-----------------|
|*type_name*|Tür adı. Bu `<Type>` öğesi, bir [\<ad alanı >](namespace-element-net-native.md) öğesi veya başka bir `<Type>` öğesi alt öğesi ise, *type_name* ad alanı olmadan türün adını içerebilir. Aksi halde, *type_name* tam nitelikli tür adını içermelidir.|

## <a name="all-other-attributes"></a>Diğer tüm öznitelikler

|Değer|Açıklama|
|-----------|-----------------|
|*policy_setting*|Bu ilke türüne uygulanacak ayar. Olası değerler şunlardır `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`ve `Required All`. Daha fazla bilgi için bkz. [çalışma zamanı yönergesi Ilke ayarları](runtime-directive-policy-settings.md).|

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<Attribute>](attributeimplies-element-net-native.md)|Kapsayan tür bir öznitelik ise, özniteliğin uygulandığı kod öğeleri için çalışma zamanı ilkesini tanımlar.|
|[\<olayı >](event-element-net-native.md)|Bu türe ait bir olaya yansıma ilkesi uygular.|
|[\<alan >](field-element-net-native.md)|Bu türe ait olan bir alana yansıma ilkesi uygular.|
|[\<GenericParameter >](genericparameter-element-net-native.md)|İlkeyi genel bir türün parametre türüne uygular.|
|[\<ımpliestype >](impliestype-element-net-native.md)|İlke, kapsayan `<Type>` öğesi tarafından temsil edilen türe uygulanmışsa ilkeyi bir türe uygular.|
|[\<yöntemi >](method-element-net-native.md)|Bu türe ait bir yönteme yansıma ilkesi uygular.|
|[\<Methodörneklemesi >](methodinstantiation-element-net-native.md)|Bu türe ait oluşturulmuş bir genel metoda yansıma ilkesi uygular.|
|[\<Özellik >](property-element-net-native.md)|Yansıma ilkesini bu türe ait olan bir özelliğe uygular.|
|[\<alt türleri >](subtypes-element-net-native.md)|Çalışma zamanı ilkesini, kapsayan türden devralınan tüm sınıflara uygular.|
|`<Type>`|Yansıtma ilkesini iç içe bir türe uygular.|
|[\<Typeörneklemesi >](typeinstantiation-element-net-native.md)|Yansıma ilkesini oluşturulmuş genel bir türe uygular.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<uygulama >](application-element-net-native.md)|Uygulama genelinde türler için bir kapsayıcı görevi görür ve meta verileri çalışma zamanında yansıma için kullanılabilir olan üyeleri yazın.|
|[Derleme > \<](assembly-element-net-native.md)|Belirtilen derlemedeki tüm türlere yansıma ilkesi uygular.|
|[\<kitaplığı >](library-element-net-native.md)|Meta verileri çalışma zamanında yansıma için kullanılabilir olan türleri ve tür üyelerini içeren derlemeyi tanımlar.|
|[\<ad alanı >](namespace-element-net-native.md)|Bir ad alanındaki tüm türlere yansıma ilkesi uygular.|
|`<Type>`|Yansıma ilkesini bir türe ve tüm üyelerine uygular.|
|[\<Typeörneklemesi >](typeinstantiation-element-net-native.md)|Oluşturulan genel türe ve tüm üyelerine yansıma ilkesi uygular.|

## <a name="remarks"></a>Açıklamalar

Yansıma, serileştirme ve birlikte çalışma özniteliklerinin tümü isteğe bağlıdır. Hiçbiri yoksa `<Type>` öğesi, alt türleri ayrı Üyeler için ilke tanımlayan bir kapsayıcı görevi görür.

Bir `<Type>` öğesi [\<bütünleştirilmiş kod >](assembly-element-net-native.md), [\<ad alanı >](namespace-element-net-native.md), `<Type>`veya [\<typeörneklemesi >](typeinstantiation-element-net-native.md) öğesi ise, üst öğe tarafından tanımlanan ilke ayarlarını geçersiz kılar.

Genel bir türün `<Type>` öğesi, kendi ilkesi olmayan tüm örneklemelerde ilkesini uygular. Oluşturulan genel türlerin ilkesi [\<Typeörneklemesi >](typeinstantiation-element-net-native.md) öğesi tarafından tanımlanır.

Tür genel bir tür ise, adı bir aksan işareti simgesiyle (\`) ve ardından Genel parametrelerin sayısı ile donatılmış olur. Örneğin, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> sınıfı için bir `<Type>` öğesinin `Name` özniteliği ``Name="System.Collections.Generic.List`1"``olarak görünür.

## <a name="example"></a>Örnek

Aşağıdaki örnek, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> sınıfının alanları, özellikleri ve yöntemleri hakkındaki bilgileri göstermek için yansımayı kullanır. Örnekte `b` değişkeni bir <xref:Windows.UI.Xaml.Controls.TextBlock> denetimidir. Örnek yalnızca tür bilgilerini aldığından meta verilerin kullanılabilirliği `Browse` ilkesi ayarı tarafından denetlenir.

 [!code-csharp[ProjectN_Reflection#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/browsegenerictype1.cs#3)]

 <xref:System.Collections.Generic.List%601> sınıfının meta verileri .NET Native araç zinciri tarafından otomatik olarak dahil edilmediğinden, örnek, istenen üye bilgilerini çalışma zamanında görüntüleyemez. Gerekli meta verileri sağlamak için, aşağıdaki `<Type>` öğesini çalışma zamanı yönergeleri dosyasına ekleyin. Bir üst [< ad alanı\>](namespace-element-net-native.md) öğesi sağladığımızda, `<Type>` öğesinde tam nitelikli bir tür adı sunduğumuz için unutmayın.

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="*Application*" Dynamic="Required All" />
      <Namespace Name ="System.Collections.Generic" >
        <Type Name="List`1" Browse="Required All" />
     </Namespace>
   </Application>
</Directives>
```

## <a name="example"></a>Örnek
 Aşağıdaki örnek, <xref:System.String.Chars%2A?displayProperty=nameWithType> özelliğini temsil eden <xref:System.Reflection.PropertyInfo> nesnesini almak için yansıma kullanır. Daha sonra, bir dizedeki yedinci karakterin değerini almak ve dizedeki tüm karakterleri göstermek için <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntemini kullanır. Örnekte `b` değişkeni bir <xref:Windows.UI.Xaml.Controls.TextBlock> denetimidir.

 [!code-csharp[ProjectN_Reflection#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/propertyinfo1.cs#1)]

 <xref:System.String> nesnesinin meta verileri kullanılamadığından, <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> yöntemine yapılan çağrı, .NET Native araç zinciri ile derlenerek çalışma zamanında bir <xref:System.NullReferenceException> özel durumu oluşturur. Özel durumu ortadan kaldırmak ve gerekli meta verileri sağlamak için, aşağıdaki `<Type>` öğesini çalışma zamanı yönergeleri dosyasına ekleyin:

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
    <Assembly Name="*Application*" Dynamic="Required All" />
    <Type Name="System.String" Dynamic="Required Public"/> -->
  </Application>
</Directives>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
- [Çalışma Zamanı Yönerge İlkesi Ayarları](runtime-directive-policy-settings.md)
