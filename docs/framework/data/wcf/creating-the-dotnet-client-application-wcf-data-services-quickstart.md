---
description: 'Hakkında daha fazla bilgi edinin: .NET Framework Istemci uygulaması oluşturma (WCF Veri Hizmetleri hızlı başlangıç)'
title: .NET Framework Istemci uygulaması oluşturma (WCF Veri Hizmetleri hızlı başlangıç)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
ms.openlocfilehash: 6a397726b0680d4091f7cefd8928e43c74dc08bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766235"
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a>.NET Framework Istemci uygulaması oluşturma (WCF Veri Hizmetleri hızlı başlangıç)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

Bu, WCF Veri Hizmetleri hızlı başlangıcının son görevidir. Bu görevde, çözüme bir konsol uygulaması ekleyecek, bu yeni istemci uygulamasına açık veri Protokolü (OData) akışına bir başvuru ekleyecek ve oluşturulan istemci veri hizmeti sınıflarını ve istemci kitaplıklarını kullanarak istemci uygulamasından OData akışına erişecaksınız.

> [!NOTE]
> Bir veri akışına erişmek için .NET Framework tabanlı bir istemci uygulaması gerekli değildir. Veri hizmetine OData akışı kullanan herhangi bir uygulama bileşeni erişebilir. Daha fazla bilgi için bkz. [Istemci uygulamasında veri hizmeti kullanma](using-a-data-service-in-a-client-application-wcf-data-services.md).

## <a name="to-create-the-client-application-by-using-visual-studio"></a>Visual Studio 'Yu kullanarak istemci uygulaması oluşturmak için

1. **Çözüm Gezgini**, çözüme sağ tıklayın, **Ekle**' ye tıklayın ve ardından **Yeni proje**' ye tıklayın.

2. Sol bölmede, **yüklü** > [**Visual C#** veya **Visual Basic**] > **Windows Desktop**' ı seçin ve ardından **WPF uygulama** şablonunu seçin.

3. `NorthwindClient`Proje adı için yazın ve ardından **Tamam**' a tıklayın.

4. MainWindow. xaml dosyasını açın ve XAML kodunu şu kodla değiştirin:

     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml#window1xaml)]

## <a name="to-add-a-data-service-reference-to-the-project"></a>Projeye veri hizmeti başvurusu eklemek için

1. **Çözüm Gezgini**, NorthwindClient projesine sağ tıklayın, hizmet başvurusu **Ekle**' ye tıklayın  >  ve ardından **bul**' a tıklayın.

     Bu, ilk görevde oluşturduğunuz Northwind veri hizmetini görüntüler.

2. **Ad alanı** metin kutusuna yazın `Northwind` ve ardından **Tamam**' a tıklayın.

     Bu, projeye veri hizmeti kaynaklarına erişmek ve bunlarla etkileşim kurmak için kullanılan veri sınıflarını içeren yeni bir kod dosyası ekler. Veri sınıfları ad alanında oluşturulur `NorthwindClient.Northwind` .

## <a name="to-access-data-service-data-in-the-wpf-application"></a>WPF uygulamasındaki veri hizmeti verilerine erişmek için

1. **NorthwindClient** altında **Çözüm Gezgini** , projeye sağ tıklayın ve **Başvuru Ekle**' ye tıklayın.

2. **Başvuru Ekle** iletişim kutusunda, **.net** sekmesine tıklayın, System.Data.Services.Client.dll derlemeyi seçin ve ardından **Tamam**' a tıklayın.

3. **NorthwindClient** altındaki **Çözüm Gezgini** , MainWindow. xaml dosyası için kod sayfasını açın ve aşağıdaki `using` ifadeyi ekleyin ( `Imports` Visual Basic).

    [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#using)]
    [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#using)]

4. Bu veri hizmetini sorgulayan ve sonucu sınıfına bağlayan aşağıdaki kodu ekleyin <xref:System.Data.Services.Client.DataServiceCollection%601> `MainWindow` :

    > [!NOTE]
    > Ana bilgisayar adını, `localhost:12345` Northwind veri hizmeti örneğinizi barındıran sunucu ve bağlantı noktasıyla değiştirmeniz gerekir.

     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#querycode)]

5. Değişiklikleri sınıfa kaydeden aşağıdaki kodu ekleyin `MainWindow` :

     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#savechanges)]

## <a name="to-build-and-run-the-northwindclient-application"></a>NorthwindClient uygulamasını derlemek ve çalıştırmak için

1. **Çözüm Gezgini**, NorthwindClient projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.

2. Uygulamayı başlatmak için **F5** tuşuna basın.

     Bu, çözümü oluşturur ve istemci uygulamasını başlatır. Veriler hizmetten istenir ve konsolda görüntülenir.

3. Data Grid 'in **Quantity** sütunundaki bir değeri düzenleyin ve ardından **Kaydet**' e tıklayın.

     Değişiklikler veri hizmetine kaydedilir.

    > [!NOTE]
    > NorthwindClient uygulamasının bu sürümü varlıkların eklenmesini ve silinmesini desteklemez.

## <a name="next-steps"></a>Sonraki Adımlar

Örnek Northwind OData akışına erişen istemci uygulamasını başarıyla oluşturdunuz. Ayrıca WCF Veri Hizmetleri hızlı başlangıcı 'nı tamamladınız!

.NET Framework uygulamasından bir OData akışına erişme hakkında daha fazla bilgi için, bkz. [WCF veri Hizmetleri Istemci kitaplığı](wcf-data-services-client-library.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](getting-started-with-wcf-data-services.md)
- [Kaynaklar](wcf-data-services-resources.md)
