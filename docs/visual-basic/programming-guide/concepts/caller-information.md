---
description: 'Daha fazla bilgi edinin: arayan bilgileri (Visual Basic)'
title: Arayan Bilgileri
ms.date: 07/20/2015
ms.assetid: 15d556eb-4d0c-4497-98a3-7f60abb7d6a1
ms.openlocfilehash: bcb4f553a9840a76f24825c3c2b7e2e98914abc2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100437715"
---
# <a name="caller-information-visual-basic"></a>Arayan bilgileri (Visual Basic)

Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz. Kaynak kodunun dosya yolunu, kaynak kodundaki satır numarasını ve arayanın üye adını alabilirsiniz. Bu bilgiler, tanılama araçlarının izlenmesine, oluşturulmasına ve bu araçlarda hata ayıklanmasına yardımcı olur.  
  
 Bu bilgileri elde etmek için her biri varsayılan değere sahip isteğe bağlı parametrelere uygulanan öznitelikler kullanabilirsiniz. Aşağıdaki tabloda, ad alanında tanımlanan arayan bilgileri öznitelikleri listelenmektedir <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> :  
  
|Öznitelik|Açıklama|Tür|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Kaynak dosyasının arayanı içeren tam yolu. Bu, derleme zamanındaki dosya yoludur.|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Yöntemin çağrıldığı kaynak dosyadaki satır numarası.|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Arayanın yöntemi veya özellik adı. Bu konunun devamındaki [üye adları](#MEMBERNAMES) bölümüne bakın.|`String`|  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnekte, Arayanın Bilgisi özniteliklerinin nasıl kullanılacağı gösterilmiştir. Yöntemine yapılan her çağrıda `TraceMessage` , çağıran bilgileri isteğe bağlı parametrelere bağımsız değişkenler olarak değiştirilir.  
  
```vb  
Private Sub DoProcessing()  
    TraceMessage("Something happened.")  
End Sub  
  
Public Sub TraceMessage(message As String,  
        <System.Runtime.CompilerServices.CallerMemberName> Optional memberName As String = Nothing,  
        <System.Runtime.CompilerServices.CallerFilePath> Optional sourcefilePath As String = Nothing,  
        <System.Runtime.CompilerServices.CallerLineNumber()> Optional sourceLineNumber As Integer = 0)  
  
    System.Diagnostics.Trace.WriteLine("message: " & message)  
    System.Diagnostics.Trace.WriteLine("member name: " & memberName)  
    System.Diagnostics.Trace.WriteLine("source file path: " & sourcefilePath)  
    System.Diagnostics.Trace.WriteLine("source line number: " & sourceLineNumber)  
End Sub  
  
' Sample output:  
'   message: Something happened.  
'   member name: DoProcessing  
'   source file path: C:\Users\username\Documents\Visual Studio 2012\Projects\CallerInfoVB\CallerInfoVB\Form1.vb  
'   source line number: 15  
```  
  
## <a name="remarks"></a>Açıklamalar  

 Her isteğe bağlı parametre için açık bir varsayılan değer belirtmeniz gerekir. İsteğe bağlı olarak belirtilmeyen parametrelere Arayan Bilgisi özniteliklerini uygulayamazsınız.  
  
 Arayan Bilgisi öznitelikleri, bir parametreyi isteğe bağlı hale getirmez. Bunun yerine, bağımsız değişken atlandığında geçirilen varsayılan değeri etkilerler.  
  
 Arayan Bilgisi değerleri, derleme zamanında Ara Dile (IL) değişmez değerler olarak verilir. <xref:System.Exception.StackTrace%2A>Özel durumlar için özellik sonuçlarının aksine, sonuçlar gizleme tarafından etkilenmez.  
  
 Arayan bilgisini denetlemek veya gizlemek için isteğe bağlı bağımsız değişkenleri açıkça sağlayabilirsiniz.  
  
### <a name="member-names"></a><a name="MEMBERNAMES"></a> Üye adları  

 `CallerMemberName`Özniteliği, çağrılan yönteme bir bağımsız değişken olarak üye adını belirtmekten kaçınmak için kullanabilirsiniz `String` . Bu tekniği kullanarak **yeniden düzenlemeyi yeniden adlandırma** sorunu, `String` değerleri değiştirmez. Bu, özellikle aşağıdaki görevler için yararlı olur:  
  
- İzleme ve tanılama yordamlarını kullanma.  
  
- <xref:System.ComponentModel.INotifyPropertyChanged>Verileri bağlarken arabirimi uygulama. Bu arabirim, bir nesnenin özelliğinin bağlama denetimine özelliğin değiştirildiğini bildirmesini ve böylece denetimin güncelleştirilmiş bilgileri görüntüleyebilmesini sağlar. Özniteliği olmadan `CallerMemberName` , özellik adını bir sabit değer olarak belirtmeniz gerekir.  
  
 Aşağıdaki grafikte, özniteliğini kullandığınızda döndürülen üye adları gösterilmektedir `CallerMemberName` .  
  
|Çağrının oluştuğu yer|Üye adı sonucu|  
|-------------------------|------------------------|  
|Yöntem, özellik veya olay|Yöntemin, özelliğin veya aramanın kaynaklandığı olayın adı.|  
|Oluşturucu|".ctor" dizesi|  
|Statik oluşturucu|".cctor" dizesi|  
|Yok edici|"Finalize" dizesi|  
|Kullanıcı tanımlı işleçler veya dönüştürmeler|Üye için oluşturulan "op_Addition" gibi bir ad.|  
|Öznitelik oluşturucu|Özniteliğin uygulandığı üyenin adı. Öznitelik bir üye içerisindeki herhangi bir öğeyse (parametre, dönüş değeri veya genel tür parametresi gibi), bu sonuç bu öğeyle ilişkili öğenin adıdır.|  
|İçeren üye yok (örneğin, derleme düzeyi veya türlere uygulanan öznitelikler)|İsteğe bağlı parametrenin varsayılan değeri.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öznitelikler (Visual Basic)](../../language-reference/attributes.md)
- [Ortak öznitelikler (Visual Basic)](attributes/common-attributes.md)
- [İsteğe Bağlı Parametreler](../language-features/procedures/optional-parameters.md)
- [Programlama kavramları (Visual Basic)](index.md)
