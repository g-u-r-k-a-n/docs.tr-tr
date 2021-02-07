---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: veri bağlama davranışlarını özelleştirme (WCF Veri Hizmetleri)'
title: 'Nasıl yapılır: veri bağlama davranışlarını özelleştirme (WCF Veri Hizmetleri)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, data binding
ms.assetid: 40476b89-8941-4771-8d21-2fe430c85a9d
ms.openlocfilehash: 60c8808f90f8e0a824a8b2b641508c0fe33f14cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765691"
---
# <a name="how-to-customize-data-binding-behaviors-wcf-data-services"></a>Nasıl yapılır: veri bağlama davranışlarını özelleştirme (WCF Veri Hizmetleri)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

WCF Veri Hizmetleri ile, <xref:System.Data.Services.Client.DataServiceCollection%601> bağlama koleksiyonuna bir nesne eklendiğinde veya kaldırıldığında ya da bir özellik değişikliği algılandığında tarafından çağrılan özel mantık sağlayabilirsiniz. Bu özel mantık, <xref:System.Func%602> `false` özel yöntem tamamlandığında ve `true` olayın sonraki işlenmesi durdurulduğunda varsayılan davranışın ne zaman gerçekleştirilmesi gerektiğini belirten bir değeri döndüren, temsilciler olarak başvurulan yöntemler olarak sağlanır.  
  
 Bu konudaki örnekler, ve parametreleri için özel yöntemler sağlar `entityChanged` `entityCollectionChanged` <xref:System.Data.Services.Client.DataServiceCollection%601> . Bu konudaki örneklerde, Northwind örnek veri hizmeti ve otomatik olarak istemci veri hizmeti sınıfları kullanılır. Bu hizmet ve istemci veri sınıfları, [WCF veri hizmetleri hızlı](quickstart-wcf-data-services.md)başlangıcı 'nı tamamladığınızda oluşturulur.  
  
## <a name="example"></a>Örnek  

 XAML dosyası için aşağıdaki arka plan kod sayfası, <xref:System.Data.Services.Client.DataServiceCollection%601> bağlama koleksiyonuna bağlanan verilerde değişiklik olduğunda çağrılan özel yöntemlerle birlikte oluşturur. <xref:System.Collections.ObjectModel.ObservableCollection%601.CollectionChanged>Olay gerçekleştiğinde, sağlanan yöntem, bağlama koleksiyonundan kaldırılmış bir öğenin veri hizmetinden silinmesini engeller. <xref:System.Collections.ObjectModel.ObservableCollection%601.PropertyChanged>Olay gerçekleştiğinde `ShipDate` değer, zaten sevk edilen siparişlerde değişiklik yapılmadığından emin olmak için onaylanır.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#wpfdatabindingcustom)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki XAML, önceki örneğe ait pencereyi tanımlar.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingCustomXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml#wpfdatabindingcustomxaml)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
