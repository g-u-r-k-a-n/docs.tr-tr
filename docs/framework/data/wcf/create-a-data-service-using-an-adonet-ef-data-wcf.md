---
title: 'Nasıl yapılır: bir ADO.NET Entity Framework veri kaynağı kullanarak veri hizmeti oluşturma (WCF Veri Hizmetleri)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
ms.openlocfilehash: 0aea4c21b5ea34cb0e8d944d37c879e918d6b27e
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800597"
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a>Nasıl yapılır: bir ADO.NET Entity Framework veri kaynağı kullanarak veri hizmeti oluşturma (WCF Veri Hizmetleri)

WCF Veri Hizmetleri, veri hizmeti olarak varlık verilerini gösterir. Veri kaynağı ilişkisel bir veritabanı olduğunda, bu varlık verileri ADO. NETEntity Framework tarafından sağlanır. Bu konu başlığı altında, var olan bir veritabanını temel alan Visual Studio Web uygulamasında Entity Framework tabanlı bir veri modeli oluşturma ve bu veri modelini kullanarak yeni bir veri hizmeti oluşturma işlemi gösterilmektedir.

Entity Framework Ayrıca, Visual Studio projesi dışında bir Entity Framework modeli oluşturabilen bir komut satırı aracı sağlar. Daha fazla bilgi için bkz. [nasıl yapılır: EdmGen. exe kullanarak model ve eşleme dosyaları oluşturma](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).

## <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a>Var olan bir veritabanını varolan bir Web uygulamasına dayalı bir Entity Framework modeli eklemek için

1. **Proje** menüsünde > **Yeni öğe** **Ekle** ' ye tıklayın.

2. **Şablonlar** bölmesinde, **veri** kategorisine ve sonra **ADO.net varlık veri modeli**' yi seçin.

3. Model adını girip **Ekle**' ye tıklayın.

     Varlık Veri Modeli sihirbazının ilk sayfası görüntülenir.

4. **Model Içeriğini seçin** iletişim kutusunda, **veritabanından oluştur**' u seçin. Sonra **İleri**'ye tıklayın.

5. **Yeni bağlantı** düğmesine tıklayın.

6. **Bağlantı özellikleri** iletişim kutusunda sunucu adınızı yazın, kimlik doğrulama yöntemini seçin, veritabanı adını yazın ve ardından **Tamam**' a tıklayın.

     **Veri bağlantınızı seçin** iletişim kutusu, veritabanı bağlantı ayarlarınızla güncelleştirilir.

7. **App. config dosyasındaki varlık bağlantısı ayarlarını kaydet:** onay kutusunun işaretli olduğundan emin olun. Sonra **İleri**'ye tıklayın.

8. **Veritabanı nesnelerinizi seçin** iletişim kutusunda, veri hizmetinde kullanıma sunmayı planladığınız tüm veritabanı nesnelerini seçin.

    > [!NOTE]
    > Veri modeline eklenen nesneler veri hizmeti tarafından otomatik olarak gösterilmez. Bunlar, hizmetin kendisi tarafından açıkça gösterilmelidir. Daha fazla bilgi için bkz. [veri hizmetini yapılandırma](configuring-the-data-service-wcf-data-services.md).

9. Sihirbazı tamamlamak için **Son**'a tıklayın.

     Bu, belirli bir veritabanını temel alan varsayılan bir veri modeli oluşturur. Entity Framework veri modelini özelleştirmesini sağlar. Daha fazla bilgi için bkz. [varlık veri modeli araçları görevleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738480(v=vs.100)).

## <a name="to-create-the-data-service-by-using-the-new-data-model"></a>Yeni veri modelini kullanarak veri hizmetini oluşturmak için

1. Visual Studio 'da, veri modelini temsil eden. edmx dosyasını açın.

2. **Model tarayıcısında**modele sağ tıklayın, **Özellikler**' e tıklayın ve ardından varlık kapsayıcısının adını aklınızda edin.

3. **Çözüm Gezgini**, ASP.net projenizin adına sağ tıklayın ve ardından > **Yeni öğe** **Ekle** ' ye tıklayın.

4. **Yeni öğe Ekle** iletişim kutusunda, **Web** kategorisindeki **WCF veri hizmeti** şablonunu seçin.

   ![Visual Studio 2015 ' de WCF veri hizmeti öğe şablonu](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **WCF veri hizmeti** şablonu visual Studio 2015 'de kullanılabilir, ancak visual Studio 2017 veya üzeri sürümlerde kullanılabilir.

5. Hizmet için bir ad sağlayın ve ardından **Tamam**' a tıklayın.

     Visual Studio, yeni hizmet için XML işaretlemesini ve kod dosyalarını oluşturur. Varsayılan olarak, kod Düzenleyicisi penceresi açılır.

6. Veri Hizmeti kodunda, <xref:System.Data.Objects.ObjectContext> sınıfından devralan ve veri modelinin varlık kapsayıcısı olan ve adım 2 ' de belirtilen tür ile veri hizmetini tanımlayan sınıfın tanımındaki açıklama `/* TODO: put your data source class name here */` değiştirin.

7. Veri Hizmeti kodunda, yetkili istemcilerin veri hizmetinin sunduğu varlık kümelerine erişmesine izin vermek için etkinleştirin. Daha fazla bilgi için bkz. [veri hizmeti oluşturma](creating-the-data-service.md).

8. Northwind. svc veri hizmetini bir Web tarayıcısı kullanarak test etmek için [bir Web tarayıcısından hizmete erişme](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)konusundaki yönergeleri izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetlerini Tanımlama](defining-wcf-data-services.md)
- [Veri Hizmetleri Sağlayıcıları](data-services-providers-wcf-data-services.md)
- [Nasıl yapılır: Yansıma Sağlayıcısını Kullanarak Veri Hizmeti Oluşturma](create-a-data-service-using-rp-wcf-data-services.md)
- [Nasıl yapılır: LINQ to SQL Veri Kaynağı Kullanarak Veri Hizmeti Oluşturma](create-a-data-service-using-linq-to-sql-wcf.md)
