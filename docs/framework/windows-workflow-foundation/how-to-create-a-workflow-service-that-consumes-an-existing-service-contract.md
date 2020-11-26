---
title: 'Nasıl yapılır: Var olan hizmet anlaşmasını kullanan iş akışı hizmeti oluşturma'
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 05c59bde424049eb5bef8f8bd09c472b58eaa9ef
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248831"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a>Nasıl yapılır: Var olan hizmet anlaşmasını kullanan iş akışı hizmeti oluşturma

.NET Framework 4,5 özelliği, sözleşmenin ilk iş akışı geliştirme biçiminde Web Hizmetleri ve iş akışları arasında daha iyi tümleştirme sunar. Sözleşme-ilk iş akışı geliştirme aracı, sözleşmeyi önce kod içinde tasarlamanızı sağlar. Araç daha sonra, sözleşmede bulunan işlemler için araç kutusunda bir etkinlik şablonu otomatik olarak oluşturur.  
  
> [!NOTE]
> Bu konuda, bir sözleşmenin ilk iş akışı hizmeti oluşturmaya yönelik adım adım yönergeler sağlanmaktadır. Sözleşme-ilk iş akışı hizmeti geliştirme hakkında daha fazla bilgi için bkz. [Ilk Iş akışı hizmeti geliştirmeyi sözleşme](contract-first-workflow-service-development.md).  
  
### <a name="creating-the-workflow-project"></a>İş akışı projesi oluşturma  
  
1. Visual Studio'da, **Dosya**, **Yeni Proje**’yi seçin. **Şablonlar** ağacındaki **C#** düğümünün altında bulunan **WCF** düğümünü seçin ve **WCF iş akışı hizmeti uygulama** şablonunu seçin.  
  
2. Yeni projeyi adlandırın `ContractFirst` ve **Tamam**' a tıklayın.  
  
### <a name="creating-the-service-contract"></a>Hizmet sözleşmesini oluşturma  
  
1. **Çözüm Gezgini** projeye sağ tıklayın ve **Ekle**, **Yeni öğe..**. seçeneğini belirleyin. Sol taraftaki **kod** düğümünü ve sağ taraftaki **sınıf** şablonunu seçin. Yeni sınıfı adlandırın `IBookService` ve **Tamam**' a tıklayın.  
  
2. Görüntülenen kod penceresinin üst kısmında bir using ifadesi ekleyin `System.Servicemodel` .  
  
    ```csharp  
    using System.ServiceModel;  
    ```  
  
3. Örnek sınıf tanımını aşağıdaki arabirim tanımına değiştirin.  
  
    ```csharp  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4. **CTRL + SHIFT + B** tuşlarına basarak projeyi derleyin.  
  
### <a name="importing-the-service-contract"></a>Hizmet sözleşmesini içeri aktarma  
  
1. **Çözüm Gezgini** ' de projeye sağ tıklayın ve **hizmet sözleşmesini içeri aktar**' ı seçin. Altında **\<Current Project>** , tüm alt düğümleri açın ve **IBookService**' i seçin. **Tamam** düğmesine tıklayın.  
  
2. Bir iletişim kutusu açılır, işlemin başarıyla tamamlandığını ve oluşturulan etkinliklerin, projeyi oluşturduktan sonra araç kutusu 'nda gözükgörünmediğini size uyaracaktır. **Tamam** düğmesine tıklayın.  
  
3. İçeri aktarılan etkinliklerin araç kutusunda görünmesi için **CTRL + SHIFT + B** tuşlarına basarak projeyi derleyin.  
  
4. **Çözüm Gezgini**' de, Service1. xamlx ' yi açın. İş akışı hizmeti tasarımcıda görünür.  
  
5. **Sıra** etkinliğini seçin. Özellikler penceresi, **..** . öğesine tıklayın. düğmesine basın. **ImplementedContract** Görüntülenen tür **koleksiyonu Düzenleyicisi** penceresinde, **tür** açılan listesine tıklayın ve **türlere gözatmayı seçin...** girişte. **Bir .NET türü görüntüle ve Seç** iletişim kutusunda, **\<Current Project>** tüm alt düğümler ' i açın ve **IBookService**' i seçin. **Tamam** düğmesine tıklayın. **Tür koleksiyonu Düzenleyicisi** Iletişim kutusunda **Tamam**' a tıklayın.  
  
6. **ReceiveRequest** ve **SendResponse** etkinliklerini seçin ve silin.  
  
7. Araç kutusundan bir **Buy_ReceiveAndSendReply** ve **Checkout_Receive** etkinliğini **sıralı hizmet** etkinliğine sürükleyin.
