---
title: 'Nasıl Yapılır: Windows Hizmet Uygulamalarında Hata Ayıklama'
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- Windows NT services, debugging
- Windows Service applications, debugging
- services, debugging
ms.assetid: 63ab0800-0f05-4f1e-88e6-94c73fd920a2
author: ghogen
ms.openlocfilehash: 860f2ae22eb6510dc1f1a454ae3e51ccb366078b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053620"
---
# <a name="how-to-debug-windows-service-applications"></a><span data-ttu-id="7d057-102">Nasıl Yapılır: Windows Hizmet Uygulamalarında Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7d057-102">How to: Debug Windows Service Applications</span></span>
<span data-ttu-id="7d057-103">Bir hizmet, Visual Studio 'nun içinden değil, hizmetler Denetim Yöneticisi bağlamı içinden çalıştırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7d057-103">A service must be run from within the context of the Services Control Manager rather than from within Visual Studio.</span></span> <span data-ttu-id="7d057-104">Bu nedenle, bir hizmetin hata ayıklaması, diğer Visual Studio Uygulama türlerinde hata ayıklama kadar basit değildir.</span><span class="sxs-lookup"><span data-stu-id="7d057-104">For this reason, debugging a service is not as straightforward as debugging other Visual Studio application types.</span></span> <span data-ttu-id="7d057-105">Bir hizmette hata ayıklamak için hizmeti başlatmanız ve sonra çalıştığı işleme bir hata ayıklayıcı bağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d057-105">To debug a service, you must start the service and then attach a debugger to the process in which it is running.</span></span> <span data-ttu-id="7d057-106">Daha sonra Visual Studio 'nun tüm standart hata ayıklama işlevselliğini kullanarak uygulamanızda hata ayıklaması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d057-106">You can then debug your application by using all of the standard debugging functionality of Visual Studio.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="7d057-107">İşlemin ne olduğunu bilmiyorsanız bir işleme iliştirmemelisiniz ve bu işlemi, büyük olasılıkla bu süreci sonlandırmanız ve muhtemelen sonlandırmasına ilişkin sonuçları anlamadığınız sürece.</span><span class="sxs-lookup"><span data-stu-id="7d057-107">You should not attach to a process unless you know what the process is and understand the consequences of attaching to and possibly killing that process.</span></span> <span data-ttu-id="7d057-108">Örneğin, WinLogon işlemine ekler ve ardından hata ayıklamayı durdurursanız, sistem WinLogon olmadan çalışamadığı için sistem durur.</span><span class="sxs-lookup"><span data-stu-id="7d057-108">For example, if you attach to the WinLogon process and then stop debugging, the system will halt because it can’t operate without WinLogon.</span></span>  
  
 <span data-ttu-id="7d057-109">Hata ayıklayıcıyı yalnızca çalışan bir hizmete ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d057-109">You can attach the debugger only to a running service.</span></span> <span data-ttu-id="7d057-110">Ek işlemi, hizmetinizin geçerli çalışmasını keser; hizmetin işlemesini gerçekten durdurmaz veya duraklatmaz.</span><span class="sxs-lookup"><span data-stu-id="7d057-110">The attachment process interrupts the current functioning of your service; it doesn’t actually stop or pause the service's processing.</span></span> <span data-ttu-id="7d057-111">Diğer bir deyişle, hizmetiniz hata ayıklamaya başladığınızda çalışıyorsa, hata ayıkladığınızda hala çalışmaya devam eder ancak işlem askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="7d057-111">That is, if your service is running when you begin debugging, it is still technically in the Started state as you debug it, but its processing has been suspended.</span></span>  
  
 <span data-ttu-id="7d057-112">İşleme iliştirdikten sonra kesme noktaları ayarlayabilir ve kodunuzda hata ayıklamak için bunları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d057-112">After attaching to the process, you can set breakpoints and use these to debug your code.</span></span> <span data-ttu-id="7d057-113">İşleme iliştirmek için kullandığınız iletişim kutusundan çıktıktan sonra, hata ayıklama modunda etkin bir şekilde yapılır.</span><span class="sxs-lookup"><span data-stu-id="7d057-113">Once you exit the dialog box you use to attach to the process, you are effectively in debug mode.</span></span> <span data-ttu-id="7d057-114">Service Control Manager 'ı kullanarak hizmetinizi başlatabilir, durdurabilir, duraklatabilir ve devam edebilir, böylece ayarladığınız kesme noktalarına vurulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="7d057-114">You can use the Services Control Manager to start, stop, pause and continue your service, thus hitting the breakpoints you've set.</span></span> <span data-ttu-id="7d057-115">Hata ayıklama başarılı olduktan sonra bu kukla hizmeti daha sonra kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d057-115">You can later remove this dummy service after debugging is successful.</span></span>  
  
 <span data-ttu-id="7d057-116">Bu makalede, yerel bilgisayarda çalışan bir hizmetin hata ayıklaması ele alınmaktadır, ancak uzak bir bilgisayarda çalışan Windows hizmetlerinde de hata ayıklaması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d057-116">This article covers debugging a service that's running on the local computer, but you can also debug Windows Services that are running on a remote computer.</span></span> <span data-ttu-id="7d057-117">Bkz. [Uzaktan hata ayıklama](/visualstudio/debugger/debug-installed-app-package).</span><span class="sxs-lookup"><span data-stu-id="7d057-117">See [Remote Debugging](/visualstudio/debugger/debug-installed-app-package).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7d057-118">Service Control <xref:System.ServiceProcess.ServiceBase.OnStart%2A> Manager bir hizmeti başlatmaya yönelik tüm denemelerde 30 saniyelik bir sınır sağladığından metodun hata ayıklaması zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="7d057-118">Debugging the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method can be difficult because the Services Control Manager imposes a 30-second limit on all attempts to start a service.</span></span> <span data-ttu-id="7d057-119">Daha fazla bilgi için bkz. [sorun giderme: Windows hizmetlerinde hata ayıklama](troubleshooting-debugging-windows-services.md).</span><span class="sxs-lookup"><span data-stu-id="7d057-119">For more information, see [Troubleshooting: Debugging Windows Services](troubleshooting-debugging-windows-services.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="7d057-120">Hata ayıklama ile ilgili anlamlı bilgiler almak için, Visual Studio hata ayıklayıcının ayıklanmakta olan ikililerin sembol dosyalarını bulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d057-120">To get meaningful information for debugging, the Visual Studio debugger needs to find symbol files for the binaries that are being debugged.</span></span> <span data-ttu-id="7d057-121">Visual Studio 'da oluşturduğunuz bir hizmette hata ayıklaması yapıyorsanız, sembol dosyaları (. pdb dosyaları) yürütülebilir veya kitaplıkla aynı klasörde bulunur ve hata ayıklayıcı bunları otomatik olarak yükler.</span><span class="sxs-lookup"><span data-stu-id="7d057-121">If you are debugging a service that you built in Visual Studio, the symbol files (.pdb files) are in the same folder as the executable or library, and the debugger loads them automatically.</span></span> <span data-ttu-id="7d057-122">Derlemediğiniz bir hizmette hata ayıklaması yapıyorsanız, öncelikle hizmetin sembollerini bulmalı ve hata ayıklayıcı tarafından bulunduklarında emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d057-122">If you are debugging a service that you didn't build, you should first find symbols for the service and make sure they can be found by the debugger.</span></span> <span data-ttu-id="7d057-123">Bkz. [Visual Studio hata ayıklayıcısında simge (. pdb) ve kaynak dosyaları belirtme](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span><span class="sxs-lookup"><span data-stu-id="7d057-123">See [Specify Symbol (.pdb) and Source Files in the Visual Studio Debugger](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span></span> <span data-ttu-id="7d057-124">Bir sistem işleminde hata ayıklaması yapıyorsanız veya hizmetinizdeki Sistem çağrılarına yönelik simgelere sahip olmak istiyorsanız, Microsoft sembol sunucularını eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d057-124">If you're debugging a system process or want to have symbols for system calls in your services, you should add the Microsoft Symbol Servers.</span></span> <span data-ttu-id="7d057-125">Bkz. [hata ayıklama sembolleri](/windows/desktop/DxTechArts/debugging-with-symbols).</span><span class="sxs-lookup"><span data-stu-id="7d057-125">See [Debugging Symbols](/windows/desktop/DxTechArts/debugging-with-symbols).</span></span>  
  
### <a name="to-debug-a-service"></a><span data-ttu-id="7d057-126">Bir hizmette hata ayıklamak için</span><span class="sxs-lookup"><span data-stu-id="7d057-126">To debug a service</span></span>  
  
1. <span data-ttu-id="7d057-127">Hata ayıklama yapılandırmasında hizmetinizi derleyin.</span><span class="sxs-lookup"><span data-stu-id="7d057-127">Build your service in the Debug configuration.</span></span>  
  
2. <span data-ttu-id="7d057-128">Hizmetinizi yükler.</span><span class="sxs-lookup"><span data-stu-id="7d057-128">Install your service.</span></span> <span data-ttu-id="7d057-129">Daha fazla bilgi için bkz. [nasıl yapılır: Hizmetleri yükleme ve kaldırma](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="7d057-129">For more information, see [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).</span></span>  
  
3. <span data-ttu-id="7d057-130">Hizmetinizi, hizmet **Denetim Yöneticisi**'nden, **Sunucu Gezgini**veya koddan başlatın.</span><span class="sxs-lookup"><span data-stu-id="7d057-130">Start your service, either from **Services Control Manager**, **Server Explorer**, or from code.</span></span> <span data-ttu-id="7d057-131">Daha fazla bilgi için bkz. [nasıl yapılır: Hizmetleri başlatma](how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="7d057-131">For more information, see [How to: Start Services](how-to-start-services.md).</span></span>  
  
4. <span data-ttu-id="7d057-132">Sistem işlemlerine iliştirebilmeniz için Visual Studio 'Yu yönetici kimlik bilgileriyle başlatın.</span><span class="sxs-lookup"><span data-stu-id="7d057-132">Start Visual Studio with administrative credentials so you can attach to system processes.</span></span>  
  
5. <span data-ttu-id="7d057-133">Seçim Visual Studio menü çubuğunda **Araçlar**, **Seçenekler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="7d057-133">(Optional) On the Visual Studio menu bar, choose **Tools**, **Options**.</span></span> <span data-ttu-id="7d057-134">**Seçenekler** iletişim kutusunda, **hata ayıklama**, **semboller**' i seçin, **Microsoft sembol sunucuları** onay kutusunu seçin ve **Tamam** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="7d057-134">In the **Options** dialog box, choose **Debugging**, **Symbols**, select the **Microsoft Symbol Servers** check box, and then choose the **OK** button.</span></span>  
  
6. <span data-ttu-id="7d057-135">Menü çubuğunda, **Hata Ayıkla** veya **Araçlar** menüsünden **İşleme İliştir** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="7d057-135">On the menu bar, choose **Attach to Process** from the **Debug** or **Tools** menu.</span></span> <span data-ttu-id="7d057-136">(Klavye: Ctrl + Alt + P)</span><span class="sxs-lookup"><span data-stu-id="7d057-136">(Keyboard: Ctrl+Alt+P)</span></span>  
  
     <span data-ttu-id="7d057-137">**Süreçler** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7d057-137">The **Processes** dialog box appears.</span></span>  
  
7. <span data-ttu-id="7d057-138">**Tüm kullanıcılardan Işlem göster** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="7d057-138">Select the **Show processes from all users** check box.</span></span>  
  
8. <span data-ttu-id="7d057-139">**Kullanılabilir işlemler** bölümünde hizmetinize yönelik işlemi seçin ve ardından **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="7d057-139">In the **Available Processes** section, choose the process for your service, and then choose **Attach**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="7d057-140">İşlem hizmetinize ait yürütülebilir dosya ile aynı ada sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="7d057-140">The process will have the same name as the executable file for your service.</span></span>  
  
     <span data-ttu-id="7d057-141">**Işleme İliştir** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7d057-141">The **Attach to Process** dialog box appears.</span></span>  
  
9. <span data-ttu-id="7d057-142">Uygun seçenekleri belirleyin ve ardından iletişim kutusunu kapatmak için **Tamam** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="7d057-142">Choose the appropriate options, and then choose **OK** to close the dialog box.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7d057-143">Artık hata ayıklama modundasınız.</span><span class="sxs-lookup"><span data-stu-id="7d057-143">You are now in debug mode.</span></span>  
  
10. <span data-ttu-id="7d057-144">Kodunuzda kullanmak istediğiniz kesme noktalarını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7d057-144">Set any breakpoints you want to use in your code.</span></span>  
  
11. <span data-ttu-id="7d057-145">Hizmet Denetim Yöneticisi 'Ne erişin ve hizmetinizi değiştirin, durdur, Duraklat ve devam et komutlarını göndererek kesme noktalarınıza ulaşıldı.</span><span class="sxs-lookup"><span data-stu-id="7d057-145">Access the Services Control Manager and manipulate your service, sending stop, pause, and continue commands to hit your breakpoints.</span></span> <span data-ttu-id="7d057-146">Hizmetler Denetim Yöneticisi 'ni çalıştırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Hizmetleri başlatma](how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="7d057-146">For more information about running the Services Control Manager, see [How to: Start Services](how-to-start-services.md).</span></span> <span data-ttu-id="7d057-147">Ayrıca bkz. [sorun giderme: Windows hizmetlerinde hata ayıklama](troubleshooting-debugging-windows-services.md).</span><span class="sxs-lookup"><span data-stu-id="7d057-147">Also, see [Troubleshooting: Debugging Windows Services](troubleshooting-debugging-windows-services.md).</span></span>  
  
## <a name="debugging-tips-for-windows-services"></a><span data-ttu-id="7d057-148">Windows Hizmetleri için hata ayıklama Ipuçları</span><span class="sxs-lookup"><span data-stu-id="7d057-148">Debugging Tips for Windows Services</span></span>  
 <span data-ttu-id="7d057-149">Hizmetin işlemine iliştirme, bu hizmet için kodun tümünü değil, çoğu hata ayıklamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7d057-149">Attaching to the service's process allows you to debug most, but not all, the code for that service.</span></span> <span data-ttu-id="7d057-150">Örneğin, hizmet zaten başlatılmış olduğundan, hizmetin <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemindeki kodda veya hizmeti bu şekilde yüklemek için kullanılan `Main` yöntemdeki kodda hata ayıklayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="7d057-150">For example, because the service has already been started, you cannot debug the code in the service's <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method or the code in the `Main` method that is used to load the service this way.</span></span> <span data-ttu-id="7d057-151">Bu sınırlamaya geçici çözüm sağlamanın bir yolu, hizmet uygulamanızda yalnızca hata ayıklamaya yardımcı olmak için olan geçici bir ikinci hizmet oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="7d057-151">One way to work around this limitation is to create a temporary second service in your service application that exists only to aid in debugging.</span></span> <span data-ttu-id="7d057-152">Her iki hizmeti de yükleyebilir ve ardından hizmet sürecini yüklemek için bu kukla hizmeti başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d057-152">You can install both services, and then start this dummy service to load the service process.</span></span> <span data-ttu-id="7d057-153">Geçici hizmet işlemi başlatduktan sonra, hizmet işlemine iliştirmek için Visual Studio 'daki **hata ayıklama** menüsünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d057-153">Once the temporary service has started the process, you can use the **Debug** menu in Visual Studio to attach to the service process.</span></span>  
  
 <span data-ttu-id="7d057-154">İşleme iliştirebilmeniz için, <xref:System.Threading.Thread.Sleep%2A> eyleme çağrı eklemeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="7d057-154">Try adding calls to the <xref:System.Threading.Thread.Sleep%2A> method to delay action until you’re able to attach to the process.</span></span>  
  
 <span data-ttu-id="7d057-155">Programı bir normal konsol uygulamasına değiştirmeyi deneyin.</span><span class="sxs-lookup"><span data-stu-id="7d057-155">Try changing the program to a regular console application.</span></span> <span data-ttu-id="7d057-156">Bunu yapmak için `Main` yöntemi, nasıl başlatıldığına bağlı olarak hem Windows hizmeti hem de konsol uygulaması olarak çalıştırabilmeniz için aşağıdaki gibi yeniden yazın.</span><span class="sxs-lookup"><span data-stu-id="7d057-156">To do this, rewrite the `Main` method as follows so it can run both as a Windows Service and as a console application, depending on how it's started.</span></span>  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a><span data-ttu-id="7d057-157">Nasıl yapılır: bir Windows hizmetini konsol uygulaması olarak çalıştırma</span><span class="sxs-lookup"><span data-stu-id="7d057-157">How to: Run a Windows Service as a console application</span></span>  
  
1. <span data-ttu-id="7d057-158">Hizmetinize <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ve <xref:System.ServiceProcess.ServiceBase.OnStop%2A> yöntemlerini çalıştıran bir yöntem ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7d057-158">Add a method to your service that runs the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods:</span></span>  
  
    ```csharp  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2. <span data-ttu-id="7d057-159">`Main` Yöntemi aşağıdaki gibi yeniden yazın:</span><span class="sxs-lookup"><span data-stu-id="7d057-159">Rewrite the `Main` method as follows:</span></span>  
  
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
  
3. <span data-ttu-id="7d057-160">Projenin özelliklerinin **uygulama** sekmesinde, **çıkış türünü** **konsol uygulaması**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7d057-160">In the **Application** tab of the project's properties, set the **Output type** to **Console Application**.</span></span>  
  
4. <span data-ttu-id="7d057-161">**Hata ayıklamayı Başlat** (F5) seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="7d057-161">Choose **Start Debugging** (F5).</span></span>  
  
5. <span data-ttu-id="7d057-162">Programı yeniden bir Windows hizmeti olarak çalıştırmak için, uygulamayı yükleyip Windows hizmeti için her zamanki gibi başlatın.</span><span class="sxs-lookup"><span data-stu-id="7d057-162">To run the program as a Windows Service again, install it and start it as usual for a Windows Service.</span></span> <span data-ttu-id="7d057-163">Bu değişiklikleri tersine çevirmek gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="7d057-163">It's not necessary to reverse these changes.</span></span>  
  
 <span data-ttu-id="7d057-164">Bazı durumlarda, örneğin yalnızca sistem başlangıcında oluşan bir sorunu ayıklamak istediğinizde, Windows hata ayıklayıcıyı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d057-164">In some cases, such as when you want to debug an issue that occurs only on system startup, you have to use the Windows debugger.</span></span> <span data-ttu-id="7d057-165">[Windows Sürücü Seti 'ni (WDK) indirin](/windows-hardware/drivers/download-the-wdk) ve bkz. [Windows hizmetlerinde hata ayıklama](https://support.microsoft.com/kb/824344).</span><span class="sxs-lookup"><span data-stu-id="7d057-165">[Download the Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk) and see [How to debug Windows Services](https://support.microsoft.com/kb/824344).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d057-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d057-166">See also</span></span>

- [<span data-ttu-id="7d057-167">Windows Hizmet Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="7d057-167">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="7d057-168">Nasıl Yapılır: Hizmetleri Yükleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="7d057-168">How to: Install and Uninstall Services</span></span>](how-to-install-and-uninstall-services.md)
- [<span data-ttu-id="7d057-169">Nasıl Yapılır: Hizmetleri Başlatma</span><span class="sxs-lookup"><span data-stu-id="7d057-169">How to: Start Services</span></span>](how-to-start-services.md)
- [<span data-ttu-id="7d057-170">Bir hizmette hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="7d057-170">Debugging a Service</span></span>](/windows/desktop/Services/debugging-a-service)
