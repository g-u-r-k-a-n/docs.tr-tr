---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir proje veri kaynağı kullanarak veri bağlama (WCF Veri Hizmetleri)'
title: 'Nasıl yapılır: bir proje veri kaynağı kullanarak veri bağlama (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: 2477af0a-676f-44f7-b73d-e66208785509
ms.openlocfilehash: 42efbfcd241487e9e729c0d0bf2eba1f8f20d996
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765717"
---
# <a name="how-to-bind-data-using-a-project-data-source-wcf-data-services"></a>Nasıl yapılır: bir proje veri kaynağı kullanarak veri bağlama (WCF Veri Hizmetleri)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

Bir WCF Veri Hizmetleri istemci uygulamasındaki oluşturulan veri nesnelerine dayalı veri kaynakları oluşturabilirsiniz. **Hizmet başvurusu Ekle** iletişim kutusunu kullanarak bir veri hizmetine bir başvuru eklediğinizde, oluşturulan istemci veri sınıflarıyla birlikte bir proje veri kaynağı oluşturulur. Veri hizmetinin sunduğu her bir varlık kümesi için bir veri kaynağı oluşturulur. Bu veri kaynağı öğelerini tasarımcıda veri **kaynakları** penceresinden sürükleyerek, hizmetten veri görüntüleyen formlar oluşturabilirsiniz. Bu öğeler veri kaynağına bağlanan denetimler haline gelir. Yürütme sırasında, bu veri kaynağı, <xref:System.Data.Services.Client.DataServiceCollection%601> veri hizmetine bir sorgu tarafından döndürülen nesnelerle doldurulan bir sınıfının örneğine bağlanır. Daha fazla bilgi için bkz. [verileri denetimlere bağlama](binding-data-to-controls-wcf-data-services.md).

 Bu konudaki örneklerde, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıfları kullanılır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.

## <a name="use-a-project-data-source-in-a-wpf-window"></a>WPF penceresinde bir proje veri kaynağı kullanma

1. Visual Studio 'da, bir WPF projesinde, Northwind Data Service 'e bir başvuru ekleyin. Daha fazla bilgi için bkz. [nasıl yapılır: veri hizmeti başvurusu ekleme](how-to-add-a-data-service-reference-wcf-data-services.md).

2. **Veri kaynakları** penceresinde, `Customers` **NorthwindEntities** proje veri kaynağındaki düğümünü genişletin.

3. **MüşteriNo** öğesine tıklayın, listeden **ComboBox** ' ı seçin ve **MüşteriNo** öğesini **müşteriler** düğümünden tasarımcıya sürükleyin.

     Bu, pencere için XAML dosyasında aşağıdaki nesne öğelerini oluşturur:

    - <xref:System.Windows.Data.CollectionViewSource>Adlı bir öğe `customersViewSource` . <xref:System.Windows.FrameworkElement.DataContext%2A>Üst düzey <xref:System.Windows.Controls.Grid> nesne öğesinin özelliği bu yeni olarak ayarlanmıştır <xref:System.Windows.Data.CollectionViewSource> .

    - Adlı bir veri ile <xref:System.Windows.Controls.ComboBox> bağlantılı `CustomerID` .

    - Bir <xref:System.Windows.Controls.Label>.

4. **Orders** Navigation özelliğini tasarımcıya sürükleyin.

     Bu, pencere için XAML dosyasında aşağıdaki ek nesne öğelerini oluşturur:

    - Adlı ikinci bir <xref:System.Windows.Data.CollectionViewSource> öğesi, `customersOrdersViewSource` ' nin kaynağı `customerViewSource` .

    - Adlı veri bağlantılı <xref:System.Windows.Controls.DataGrid> Denetim `ordersDataGrid` .

5. Seçim **Müşteriler** düğümündeki ek öğeleri tasarımcıya sürükleyin.

6. Form için kod sayfasını açın ve aşağıdaki `using` deyimleri ekleyin ( `Imports` Visual Basic):

     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf2.xaml.cs#customersordersusingwpf)]

7. Formu tanımlayan kısmi sınıfta, bir <xref:System.Data.Objects.ObjectContext> örnek oluşturan ve sabiti tanımlayan aşağıdaki kodu ekleyin `customerID` .

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf2.xaml.cs#customersordersdefinitionwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf2.xaml.vb#customersordersdefinitionwpf)]

8. Tasarımcıda pencereyi seçin.

    > [!NOTE]
    > Penceredeki içeriği seçmek yerine pencerenin kendisini seçtiğinizden emin olun. Pencere seçilirse, **Özellikler** penceresinin üst kısmındaki **ad** metin kutusu pencerenin adını içermelidir.

9. **Özellikler** penceresinde, **Olaylar** düğmesini seçin.

10. **Yüklenen** olayı bulun ve ardından bu olayın yanındaki açılan listeye çift tıklayın.

     Visual Studio, pencere için arka plan kod dosyasını açar ve bir <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisi oluşturur.

11. Yeni oluşturulan <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisinde aşağıdaki kodu kopyalayın ve yapıştırın.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf2.xaml.cs#customersordersdatabindingwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf2.xaml.vb#customersordersdatabindingwpf)]

12. Bu kod, <xref:System.Data.Services.Client.DataServiceCollection%601> `Customers` <xref:System.Collections.Generic.IEnumerable%601> `Customers` `Orders` Northwind Data Service 'ten ilgili nesnelerle birlikte ve ' a bağlayan bir LINQ sorgusunun yürütülmesini temel alan tür için bir örneği oluşturur `customersViewSource` .

## <a name="use-a-project-data-source-in-a-windows-form"></a>Bir Windows formunda bir proje veri kaynağı kullanma

1. **Veri kaynakları** penceresinde, **NorthwindEntities** proje veri kaynağındaki **müşteriler** düğümünü genişletin.

2. **MüşteriNo** öğesine tıklayın, listeden **ComboBox** ' ı seçin ve **MüşteriNo** öğesini **müşteriler** düğümünden tasarımcıya sürükleyin.

     Bu, formunda aşağıdaki denetimleri oluşturur:

    - Adlandırılmış bir örneği <xref:System.Windows.Forms.BindingSource> `customersBindingSource` .

    - Adlandırılmış bir örneği <xref:System.Windows.Forms.BindingNavigator> `customersBindingNavigator` . Gerekli olacağı için bu denetimi silebilirsiniz.

    - Adlı bir veri ile <xref:System.Windows.Forms.ComboBox> bağlantılı `CustomerID` .

    - Bir <xref:System.Windows.Forms.Label>.

3. **Orders** Navigation özelliğini forma sürükleyin.

4. Bu, denetimin `ordersBindingSource` <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliği olan `customersBindingSource` ve <xref:System.Windows.Forms.BindingSource.DataMember%2A> özelliği olarak ayarlanmış olan denetimi oluşturur `Customers` . Ayrıca `ordersDataGridView` , düzgün bir şekilde adlandırılmış etiket denetimiyle birlikte, formda veriye bağlı denetimi oluşturur.

5. Seçim **Müşteriler** düğümündeki ek öğeleri tasarımcıya sürükleyin.

6. Form için kod sayfasını açın ve aşağıdaki `using` deyimleri ekleyin ( `Imports` Visual Basic):

     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersusing)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersusing)]

7. Formu tanımlayan kısmi sınıfta, bir <xref:System.Data.Objects.ObjectContext> örnek oluşturan ve sabiti tanımlayan aşağıdaki kodu ekleyin `customerID` .

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersdefinition)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersdefinition)]

8. Form tasarımcısında, forma çift tıklayın.

     Bu, formun kod sayfasını açar ve formun olayını işleyen yöntemi oluşturur `Load` .

9. `Load`Olay işleyicisinde aşağıdaki kodu kopyalayın ve yapıştırın.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersdatabinding)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersdatabinding)]

10. Bu kod, <xref:System.Data.Services.Client.DataServiceCollection%601> `Customers` <xref:System.Data.Services.Client.DataServiceQuery%601> <xref:System.Collections.Generic.IEnumerable%601> `Customers` Northwind Data Service 'ten ' i döndüren ve ' a bağlayan bir öğesinin yürütülmesini temel alan türü için bir örneği oluşturur `customersBindingSource` .

## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
- [Nasıl yapılır: Windows Presentation Foundation Öğelerine Veri Bağlama](bind-data-to-wpf-elements-wcf-data-services.md)
