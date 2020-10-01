---
title: 'Nasıl yapılır: Windows Hizmet Uygulamalarında Hata Ayıklama'
description: Diğer Visual Studio uygulama türleri olarak hata ayıklama yapmak için basit olmayan Windows hizmeti uygulamalarında hata ayıklamayı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- Windows NT services, debugging
- Windows Service applications, debugging
- services, debugging
ms.assetid: 63ab0800-0f05-4f1e-88e6-94c73fd920a2
ms.openlocfilehash: 2657d83f39b60be84846fb784a06e71f6dd46179
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609739"
---
# <a name="how-to-debug-windows-service-applications"></a>Nasıl yapılır: Windows Hizmet Uygulamalarında Hata Ayıklama
Bir hizmet, Visual Studio 'nun içinden değil, hizmetler Denetim Yöneticisi bağlamı içinden çalıştırılmalıdır. Bu nedenle, bir hizmetin hata ayıklaması, diğer Visual Studio Uygulama türlerinde hata ayıklama kadar basit değildir. Bir hizmette hata ayıklamak için hizmeti başlatmanız ve sonra çalıştığı işleme bir hata ayıklayıcı bağlamanız gerekir. Daha sonra Visual Studio 'nun tüm standart hata ayıklama işlevselliğini kullanarak uygulamanızda hata ayıklaması yapabilirsiniz.  
  
> [!CAUTION]
> İşlemin ne olduğunu bilmiyorsanız bir işleme iliştirmemelisiniz ve bu işlemi, büyük olasılıkla bu süreci sonlandırmanız ve muhtemelen sonlandırmasına ilişkin sonuçları anlamadığınız sürece. Örneğin, WinLogon işlemine ekler ve ardından hata ayıklamayı durdurursanız, sistem WinLogon olmadan çalışamadığı için sistem durur.  
  
 Hata ayıklayıcıyı yalnızca çalışan bir hizmete ekleyebilirsiniz. Ek işlemi, hizmetinizin geçerli çalışmasını keser; hizmetin işlemesini gerçekten durdurmaz veya duraklatmaz. Diğer bir deyişle, hizmetiniz hata ayıklamaya başladığınızda çalışıyorsa, hata ayıkladığınızda hala çalışmaya devam eder ancak işlem askıya alınır.  
  
 İşleme iliştirdikten sonra kesme noktaları ayarlayabilir ve kodunuzda hata ayıklamak için bunları kullanabilirsiniz. İşleme iliştirmek için kullandığınız iletişim kutusundan çıktıktan sonra, hata ayıklama modunda etkin bir şekilde yapılır. Service Control Manager 'ı kullanarak hizmetinizi başlatabilir, durdurabilir, duraklatabilir ve devam edebilir, böylece ayarladığınız kesme noktalarına vurulacaksınız. Hata ayıklama başarılı olduktan sonra bu kukla hizmeti daha sonra kaldırabilirsiniz.  
  
 Bu makalede, yerel bilgisayarda çalışan bir hizmetin hata ayıklaması ele alınmaktadır, ancak uzak bir bilgisayarda çalışan Windows hizmetlerinde de hata ayıklaması yapabilirsiniz. Bkz. [Uzaktan hata ayıklama](/visualstudio/debugger/debug-installed-app-package).  
  
> [!NOTE]
> <xref:System.ServiceProcess.ServiceBase.OnStart%2A>Service Control Manager bir hizmeti başlatmaya yönelik tüm denemelerde 30 saniyelik bir sınır sağladığından metodun hata ayıklaması zor olabilir. Daha fazla bilgi için bkz. [sorun giderme: Windows hizmetlerinde hata ayıklama](troubleshooting-debugging-windows-services.md).  
  
> [!WARNING]
> Hata ayıklama ile ilgili anlamlı bilgiler almak için, Visual Studio hata ayıklayıcının ayıklanmakta olan ikililerin sembol dosyalarını bulması gerekir. Visual Studio 'da oluşturduğunuz bir hizmette hata ayıklaması yapıyorsanız, sembol dosyaları (. pdb dosyaları) yürütülebilir veya kitaplıkla aynı klasörde bulunur ve hata ayıklayıcı bunları otomatik olarak yükler. Derlemediğiniz bir hizmette hata ayıklaması yapıyorsanız, öncelikle hizmetin sembollerini bulmalı ve hata ayıklayıcı tarafından bulunduklarında emin olmanız gerekir. Bkz. [Visual Studio hata ayıklayıcısında simge (. pdb) ve kaynak dosyaları belirtme](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger). Bir sistem işleminde hata ayıklaması yapıyorsanız veya hizmetinizdeki Sistem çağrılarına yönelik simgelere sahip olmak istiyorsanız, Microsoft sembol sunucularını eklemeniz gerekir. Bkz. [hata ayıklama sembolleri](/windows/desktop/DxTechArts/debugging-with-symbols).  
  
### <a name="to-debug-a-service"></a>Bir hizmette hata ayıklamak için  
  
1. Hata ayıklama yapılandırmasında hizmetinizi derleyin.  
  
2. Hizmetinizi yükler. Daha fazla bilgi için bkz. [nasıl yapılır: Hizmetleri yükleme ve kaldırma](how-to-install-and-uninstall-services.md).  
  
3. Hizmetinizi, hizmet **Denetim Yöneticisi**'nden, **Sunucu Gezgini**veya koddan başlatın. Daha fazla bilgi için bkz. [nasıl yapılır: Hizmetleri başlatma](how-to-start-services.md).  
  
4. Sistem işlemlerine iliştirebilmeniz için Visual Studio 'Yu yönetici kimlik bilgileriyle başlatın.  
  
5. Seçim Visual Studio menü çubuğunda **Araçlar**, **Seçenekler**' i seçin. **Seçenekler** iletişim kutusunda, **hata ayıklama**, **semboller**' i seçin, **Microsoft sembol sunucuları** onay kutusunu seçin ve **Tamam** düğmesini seçin.  
  
6. Menü çubuğunda, **Hata Ayıkla** veya **Araçlar** menüsünden **İşleme İliştir** ' i seçin. (Klavye: Ctrl + Alt + P)  
  
     **Süreçler** iletişim kutusu görüntülenir.  
  
7. **Tüm kullanıcılardan Işlem göster** onay kutusunu seçin.  
  
8. **Kullanılabilir işlemler** bölümünde hizmetinize yönelik işlemi seçin ve ardından **Ekle**' yi seçin.  
  
    > [!TIP]
    > İşlem hizmetinize ait yürütülebilir dosya ile aynı ada sahip olacaktır.  
  
     **Işleme İliştir** iletişim kutusu görüntülenir.  
  
9. Uygun seçenekleri belirleyin ve ardından iletişim kutusunu kapatmak için **Tamam** ' ı seçin.  
  
    > [!NOTE]
    > Artık hata ayıklama modundasınız.  
  
10. Kodunuzda kullanmak istediğiniz kesme noktalarını ayarlayın.  
  
11. Hizmet Denetim Yöneticisi 'Ne erişin ve hizmetinizi değiştirin, durdur, Duraklat ve devam et komutlarını göndererek kesme noktalarınıza ulaşıldı. Hizmetler Denetim Yöneticisi 'ni çalıştırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Hizmetleri başlatma](how-to-start-services.md). Ayrıca bkz. [sorun giderme: Windows hizmetlerinde hata ayıklama](troubleshooting-debugging-windows-services.md).  
  
## <a name="debugging-tips-for-windows-services"></a>Windows Hizmetleri için hata ayıklama Ipuçları  
 Hizmetin işlemine iliştirme, bu hizmet için kodun tümünü değil, çoğu hata ayıklamanıza olanak tanır. Örneğin, hizmet zaten başlatılmış olduğundan, hizmetin <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemindeki kodda veya `Main` hizmeti bu şekilde yüklemek için kullanılan yöntemdeki kodda hata ayıklayamazsınız. Bu sınırlamaya geçici çözüm sağlamanın bir yolu, hizmet uygulamanızda yalnızca hata ayıklamaya yardımcı olmak için olan geçici bir ikinci hizmet oluşturmaktır. Her iki hizmeti de yükleyebilir ve ardından hizmet sürecini yüklemek için bu kukla hizmeti başlatabilirsiniz. Geçici hizmet işlemi başlatduktan sonra, hizmet işlemine iliştirmek için Visual Studio 'daki **hata ayıklama** menüsünü kullanabilirsiniz.  
  
 <xref:System.Threading.Thread.Sleep%2A>İşleme iliştirebilmeniz için, eyleme çağrı eklemeyi deneyin.  
  
 Programı bir normal konsol uygulamasına değiştirmeyi deneyin. Bunu yapmak için `Main` yöntemi, nasıl başlatıldığına bağlı olarak hem Windows hizmeti hem de konsol uygulaması olarak çalıştırabilmeniz için aşağıdaki gibi yeniden yazın.  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a>Nasıl yapılır: bir Windows hizmetini konsol uygulaması olarak çalıştırma  
  
1. Hizmetinize ve yöntemlerini çalıştıran bir yöntem ekleyin <xref:System.ServiceProcess.ServiceBase.OnStart%2A> <xref:System.ServiceProcess.ServiceBase.OnStop%2A> :  
  
    ```csharp  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2. `Main`Yöntemi aşağıdaki gibi yeniden yazın:  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        if (Environment.UserInteractive)  
        {  
            MyNewService service1 = new MyNewService(args);  
            service1.TestStartupAndStop(args);  
        }  
        else  
        {  
            // Put the body of your old Main method here.  
        }  
    }
    ```  
  
3. Projenin özelliklerinin **uygulama** sekmesinde, **çıkış türünü** **konsol uygulaması**olarak ayarlayın.  
  
4. **Hata ayıklamayı Başlat** (F5) seçeneğini belirleyin.  
  
5. Programı yeniden bir Windows hizmeti olarak çalıştırmak için, uygulamayı yükleyip Windows hizmeti için her zamanki gibi başlatın. Bu değişiklikleri tersine çevirmek gerekli değildir.  
  
 Bazı durumlarda, örneğin yalnızca sistem başlangıcında oluşan bir sorunu ayıklamak istediğinizde, Windows hata ayıklayıcıyı kullanmanız gerekir. [Windows Sürücü Seti 'ni (WDK) indirin](/windows-hardware/drivers/download-the-wdk) ve bkz. [Windows hizmetlerinde hata ayıklama](https://support.microsoft.com/kb/824344).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Hizmet Uygulamalarına Giriş](introduction-to-windows-service-applications.md)
- [Nasıl yapılır: Hizmetleri Yükleme ve Kaldırma](how-to-install-and-uninstall-services.md)
- [Nasıl yapılır: Hizmetleri Başlatma](how-to-start-services.md)
- [Bir hizmette hata ayıklama](/windows/desktop/Services/debugging-a-service)
