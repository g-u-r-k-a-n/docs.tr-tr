---
description: 'Hakkında daha fazla bilgi edinin: örnek: verileri bağlamada özel durumları Işleme'
title: 'Örnek: Veri Bağlama Sırasında Özel Durum İşleme'
ms.date: 03/30/2017
ms.assetid: bd63ed96-9853-46dc-ade5-7bd1b0f39110
ms.openlocfilehash: 434520e42afa3e1ab7c453c3ddf41863ceb62eb6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747900"
---
# <a name="example-handling-exceptions-when-binding-data"></a>Örnek: Veri Bağlama Sırasında Özel Durum İşleme

> [!NOTE]
> Bu konu, yayın öncesi yazılım olan .NET Native geliştirici önizlemesine başvurur. Önizlemeyi [Microsoft Connect Web sitesinden](https://go.microsoft.com/fwlink/?LinkId=394611) indirebilirsiniz (kayıt gerekir).  
  
 Aşağıdaki örnek, .NET Native araç zinciri ile derlenen bir uygulama verileri bağlamayı denediğinde oluşan bir [MissingMetadataException](missingmetadataexception-class-net-native.md) özel durumunun nasıl çözümlendiğini gösterir. Özel durum bilgileri aşağıda verilmiştir:  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:
App.ViewModels.MainPageVM  
```  
  
 İlişkili çağrı yığını aşağıda verilmiştir:  
  
```output
Reflection::Execution::ReflectionDomainSetupImplementation.CreateNonInvokabilityException+0x238  
Reflection::Core::ReflectionDomain.CreateNonInvokabilityException+0x2e  
Reflection::Core::Execution::ExecutionEnvironment.+0x316  
System::Reflection::Runtime::PropertyInfos::RuntimePropertyInfo.GetValue+0x1cb  
System::Reflection::PropertyInfo.GetValue+0x22  
System::Runtime::InteropServices::WindowsRuntime::CustomPropertyImpl.GetValue+0x42  
App!$66_Interop::McgNative.Func_IInspectable_IInspectable+0x158  
App!$66_Interop::McgNative::__vtable_Windows_UI_Xaml_Data__ICustomProperty.GetValue__STUB+0x46  
Windows_UI_Xaml!DirectUI::PropertyProviderPropertyAccess::GetValue+0x3f
Windows_UI_Xaml!DirectUI::PropertyAccessPathStep::GetValue+0x31
Windows_UI_Xaml!DirectUI::PropertyPathListener::ConnectPathStep+0x113  
```  
  
## <a name="what-was-the-app-doing"></a>Uygulama ne yapıyordu?  

 Yığının tabanında, <xref:Windows.UI.Xaml?displayProperty=nameWithType> ad alanındaki Çerçeveler XAML işleme altyapısının çalıştığını gösterir.   Yönteminin kullanımı, <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> meta verileri kaldırılmış olan türdeki bir özelliğin değerinin yansıma tabanlı bir aramasını gösterir.  
  
 Meta veri yönergesini sağlamanın ilk adımı, `serialize` özelliklerinin tümünün erişilebilir olması için türün meta verilerini eklemektir:  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a>Bu yalıtılmış bir durumdur mi?  

 Bu senaryoda, veri bağlamasında bir tane için eksik meta veriler varsa, `ViewModel` diğerleri de olabilir.  Kod, uygulamanın görünüm modellerinin ad alanında yer aldığı bir şekilde yapılandırılmış ise `App.ViewModels` , daha genel bir çalışma zamanı yönergesi kullanabilirsiniz:  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a>Kod, yansıma kullanmadan yeniden yazılabilir mi?  

 Veri bağlama yansıma yoğun olduğundan, yansımayı önlemek için kodun değiştirilmesi uygun değildir.  
  
 Ancak, `ViewModel` araç zincirinin derleme zamanında doğru türle Özellik bağlamalarını ilişkilendirebilmesi ve bir çalışma zamanı yönergesi kullanmadan meta verileri tutması IÇIN xaml sayfasına belirtmek için bazı yollar vardır.  Örneğin, özelliğini <xref:Windows.UI.Xaml.Data.BindableAttribute?displayProperty=nameWithType> özelliklerine uygulayabilirsiniz. Bu, XAML derleyicisinin gerekli arama bilgilerini oluşturmasına ve Default.rd.xml dosyasında bir çalışma zamanı yönergesi gerektirmesine neden olur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](getting-started-with-net-native.md)
- [Örnek: Dinamik Programlama Sorunlarını Giderme](example-troubleshooting-dynamic-programming.md)
