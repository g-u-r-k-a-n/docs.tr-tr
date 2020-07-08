---
title: 'İzlenecek yol: COM Nesneleri Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: 6ff23f73af384a1440bcebd4b6bac21714e01756
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051486"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a>İzlenecek yol: Visual Basic ile COM Nesneleri Oluşturma
Yeni uygulamalar veya bileşenler oluştururken .NET Framework derlemeleri oluşturmak en iyisidir. Ancak Visual Basic Ayrıca, bir .NET Framework bileşenini COM 'da kullanıma sunmayı da kolaylaştırır. Bu, COM bileşenleri gerektiren önceki uygulama paketleri için yeni bileşenler sağlamanıza olanak sağlar. Bu izlenecek yol, .NET Framework nesnelerini com nesneleri olarak göstermek için Visual Basic, hem hem de COM sınıf şablonuyla birlikte kullanmak için nasıl kullanılacağını gösterir.  
  
 COM nesnelerini kullanıma almanın en kolay yolu COM sınıf şablonunu kullanmaktır. Bu şablon yeni bir sınıf oluşturur, sonra projenizi bir COM nesnesi olarak birlikte çalışabilirlik katmanıyla oluşturacak şekilde yapılandırır ve işletim sistemine kaydeder.  
  
> [!NOTE]
> Yönetilmeyen kodun kullanması için Visual Basic bir COM nesnesi olarak oluşturulan bir sınıfı kullanıma sunabilseniz de, bu gerçek bir COM nesnesi değildir ve Visual Basic tarafından kullanılamaz. Daha fazla bilgi için bkz. [.NET Framework uygulamalarda com birlikte çalışabilirliği](com-interoperability-in-net-framework-applications.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a>COM sınıf şablonunu kullanarak bir COM nesnesi oluşturmak için  
  
1. Yeni **Proje**' ye tıklayarak **Dosya** menüsünden Yeni bir Windows uygulaması projesi açın.  
  
2. **Proje türleri** alanının altındaki **Yeni proje** iletişim kutusunda, Windows 'un seçili olduğunu kontrol edin. **Şablonlar** listesinden **sınıf kitaplığı** ' nı seçin ve ardından **Tamam**' a tıklayın. Yeni proje görüntülenir.  
  
3. **Proje** menüsünden **Yeni öğe Ekle** ' yi seçin. **Yeni Öğe Ekle** iletişim kutusu görüntülenir.  
  
4. **Şablonlar** listesinden **com sınıfı** ' nı seçin ve ardından **Ekle**' ye tıklayın. Visual Basic yeni bir sınıf ekler ve COM birlikte çalışması için yeni projeyi yapılandırır.  
  
5. COM sınıfına özellikler, Yöntemler ve olaylar gibi bir kod ekleyin.  
  
6. **Build** menüsünden **Build ClassLibrary1** öğesini seçin. Visual Basic derlemeyi oluşturur ve COM nesnesini işletim sistemiyle kaydeder.  
  
## <a name="creating-com-objects-without-the-com-class-template"></a>Com sınıf şablonu olmadan COM nesneleri oluşturma  
 COM sınıfı şablonunu kullanmak yerine el ile bir COM sınıfı da oluşturabilirsiniz. Bu yordam, komut satırından çalışırken veya COM nesnelerinin nasıl tanımlandığı hakkında daha fazla denetim istediğinizde yararlıdır.  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a>Projenizi bir COM nesnesi oluşturacak şekilde ayarlamak için  
  
1. **NewProject**' i tıklatarak **Dosya** menüsünden Yeni bir Windows uygulaması projesi açın.  
  
2. **Proje türleri** alanının altındaki **Yeni proje** iletişim kutusunda, Windows 'un seçili olduğunu kontrol edin. **Şablonlar** listesinden **sınıf kitaplığı** ' nı seçin ve ardından **Tamam**' a tıklayın. Yeni proje görüntülenir.  
  
3. **Çözüm Gezgini**, projenize sağ tıklayın ve ardından **Özellikler**' e tıklayın. **Proje Tasarımcısı** görüntülenir.  
  
4. **Derle** sekmesine tıklayın.  
  
5. **Com birlikte çalışması Için kaydol** onay kutusunu seçin.  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a>Bir COM nesnesi oluşturmak için sınıfınıza kodu ayarlamak için  
  
1. **Çözüm Gezgini**, kodunu göstermek için **Class1. vb** öğesine çift tıklayın.  
  
2. Sınıfını olarak yeniden adlandırın `ComClass1` .  
  
3. Aşağıdaki sabitleri öğesine ekleyin `ComClass1` . Bunlar, COM nesnelerinin sahip olması için gerekli olan genel benzersiz tanımlayıcı (GUID) sabitlerini depolayacaktır.  
  
     [!code-vb[VbVbalrInterop#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#2)]  
  
4. **Araçlar** menüsünde **GUID oluştur**' a tıklayın. **GUID oluştur** iletişim kutusunda, **kayıt defteri biçimi** ' ne ve ardından **Kopyala**' ya tıklayın. **Çıkış**'a tıklayın.  
  
5. İçin boş dizeyi `ClassId` GUID ile değiştirin, baştaki ve sondaki ayraçları kaldırır. Örneğin, Guidgen tarafından belirtilen GUID ise `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` kodunuzun aşağıdaki gibi görünmesi gerekir.  
  
     [!code-vb[VbVbalrInterop#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#3)]  
  
6. `InterfaceId`Aşağıdaki örnekte olduğu gibi, ve sabitleri için önceki adımları tekrarlayın `EventsId` .  
  
     [!code-vb[VbVbalrInterop#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#4)]  
  
    > [!NOTE]
    > GUID 'lerin yeni ve benzersiz olduğundan emin olun; Aksi halde, COM bileşeniniz diğer COM bileşenleriyle çakışabilir.  
  
7. `ComClass` `ComClass1` Aşağıdaki örnekte olduğu gıbı sınıf kimliği, arabirim kimliği ve olay kimliği Için GUID 'leri belirterek özniteliğini öğesine ekleyin:  
  
     [!code-vb[VbVbalrInterop#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#5)]  
  
8. COM sınıflarının parametresiz bir oluşturucusu olmalıdır `Public Sub New()` veya sınıf doğru şekilde kayıt olmayacaktır. Sınıfına parametresiz bir Oluşturucu ekleyin:  
  
     [!code-vb[VbVbalrInterop#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#6)]  
  
9. Sınıfa özellikler, Yöntemler ve olaylar ekleyin ve bir `End Class` ifadesiyle biter. **Build** menüsünden **Build Solution** öğesini seçin. Visual Basic derlemeyi oluşturur ve COM nesnesini işletim sistemiyle kaydeder.  
  
    > [!NOTE]
    > Visual Basic ile oluşturduğunuz COM nesneleri, doğru COM nesneleri olmadığından diğer Visual Basic uygulamalar tarafından kullanılamaz. Bu tür COM nesnelerine başvuru ekleme girişimleri bir hata oluşturacak. Ayrıntılar için bkz. [.NET Framework uygulamalarda com birlikte çalışabilirliği](com-interoperability-in-net-framework-applications.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ComClassAttribute>
- [COM birlikte çalışma](index.md)
- [İzlenecek yol: COM Nesnelerinde Kalıtım Uygulama](walkthrough-implementing-inheritance-with-com-objects.md)
- [#Region yönergesi](../../language-reference/directives/region-directive.md)
- [.NET Framework Uygulamalarında COM Birlikte Çalışabilirliği](com-interoperability-in-net-framework-applications.md)
- [Birlikte Çalışabilirlik İle İlgili Sorun Giderme](troubleshooting-interoperability.md)
