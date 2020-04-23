---
title: 'Nasıl Yapılır: Hizmetleri Başlatma'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
author: ghogen
ms.openlocfilehash: 75fd3aba88bdffbe536ad5dab14996913d0a9d22
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053567"
---
# <a name="how-to-start-services"></a><span data-ttu-id="cb1be-102">Nasıl Yapılır: Hizmetleri Başlatma</span><span class="sxs-lookup"><span data-stu-id="cb1be-102">How to: Start Services</span></span>

<span data-ttu-id="cb1be-103">Bir hizmet yüklendikten sonra, başlatılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cb1be-103">After a service is installed, it must be started.</span></span> <span data-ttu-id="cb1be-104">Başlatılıyor <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi hizmet sınıfında çağırır.</span><span class="sxs-lookup"><span data-stu-id="cb1be-104">Starting calls the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method on the service class.</span></span> <span data-ttu-id="cb1be-105">Genellikle, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> yöntemi hizmetin gerçekleştireceği faydalı işleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cb1be-105">Usually, the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method defines the useful work the service will perform.</span></span> <span data-ttu-id="cb1be-106">Bir hizmet başladıktan sonra, el ile duraklatıldığı veya durduruluncaya kadar etkin kalır.</span><span class="sxs-lookup"><span data-stu-id="cb1be-106">After a service starts, it remains active until it is manually paused or stopped.</span></span>

<span data-ttu-id="cb1be-107">Hizmetler, otomatik olarak veya el ile başlayacak şekilde ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="cb1be-107">Services can be set up to start automatically or manually.</span></span> <span data-ttu-id="cb1be-108">Otomatik olarak başlatılan bir hizmet, yüklendiği bilgisayar yeniden başlatıldığında veya ilk açıldığında başlatılır.</span><span class="sxs-lookup"><span data-stu-id="cb1be-108">A service that starts automatically will be started when the computer on which it is installed is rebooted or first turned on.</span></span> <span data-ttu-id="cb1be-109">Bir kullanıcının el ile başlatılan bir hizmeti başlatması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cb1be-109">A user must start a service that starts manually.</span></span>

> [!NOTE]
> <span data-ttu-id="cb1be-110">Varsayılan olarak, Visual Studio ile oluşturulan hizmetler el ile başlayacak şekilde ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="cb1be-110">By default, services created with Visual Studio are set to start manually.</span></span>

<span data-ttu-id="cb1be-111">**Sunucu Gezgini**, **Hizmetler denetim yöneticisinden**veya ' de adlı bir bileşeni kullanarak koddan el ile bir hizmeti başlatabilmeniz için kullanabileceğiniz çeşitli yollar vardır <xref:System.ServiceProcess.ServiceController>.</span><span class="sxs-lookup"><span data-stu-id="cb1be-111">There are several ways you can manually start a service — from **Server Explorer**, from the **Services Control Manager**, or from code using a component called the <xref:System.ServiceProcess.ServiceController>.</span></span>

<span data-ttu-id="cb1be-112">Bir hizmetin el <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> ile mi yoksa <xref:System.ServiceProcess.ServiceInstaller> otomatik olarak mı başlatılacağını öğrenmek için sınıfında özelliğini ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="cb1be-112">You set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property on the <xref:System.ServiceProcess.ServiceInstaller> class to determine whether a service should be started manually or automatically.</span></span>

### <a name="to-specify-how-a-service-should-start"></a><span data-ttu-id="cb1be-113">Bir hizmetin nasıl başlaması gerektiğini belirtmek için</span><span class="sxs-lookup"><span data-stu-id="cb1be-113">To specify how a service should start</span></span>

1. <span data-ttu-id="cb1be-114">Hizmetinizi oluşturduktan sonra, için gerekli yükleyicileri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cb1be-114">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="cb1be-115">Daha fazla bilgi için bkz. [nasıl yapılır: hizmet uygulamanıza yükleyiciler ekleme](how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="cb1be-115">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>

2. <span data-ttu-id="cb1be-116">Tasarımcıda çalıştığınız hizmetin hizmet yükleyicisine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="cb1be-116">In the designer, click the service installer for the service you are working with.</span></span>

3. <span data-ttu-id="cb1be-117">**Özellikler** penceresinde, <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> özelliği aşağıdakilerden biri olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="cb1be-117">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to one of the following:</span></span>

    |<span data-ttu-id="cb1be-118">Hizmetinizin yüklenmesini sağlamak için</span><span class="sxs-lookup"><span data-stu-id="cb1be-118">To have your service install</span></span>|<span data-ttu-id="cb1be-119">Bu değeri ayarla</span><span class="sxs-lookup"><span data-stu-id="cb1be-119">Set this value</span></span>|
    |----------------------------------|--------------------|
    |<span data-ttu-id="cb1be-120">Bilgisayar yeniden başlatıldığında</span><span class="sxs-lookup"><span data-stu-id="cb1be-120">When the computer is restarted</span></span>|<span data-ttu-id="cb1be-121">**Automatic**</span><span class="sxs-lookup"><span data-stu-id="cb1be-121">**Automatic**</span></span>|
    |<span data-ttu-id="cb1be-122">Açık Kullanıcı eylemi hizmeti başlattığında</span><span class="sxs-lookup"><span data-stu-id="cb1be-122">When an explicit user action starts the service</span></span>|<span data-ttu-id="cb1be-123">**El ile**</span><span class="sxs-lookup"><span data-stu-id="cb1be-123">**Manual**</span></span>|

    > [!TIP]
    > <span data-ttu-id="cb1be-124">Hizmetinizin hiç başlatılmasını engellemek için <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> özelliği **devre dışı**olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb1be-124">To prevent your service from being started at all, you can set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to **Disabled**.</span></span> <span data-ttu-id="cb1be-125">Bir sunucuyu birkaç kez yeniden başlatacaksanız ve normalde başlamadan başlayan Hizmetleri kaldırarak zamandan tasarruf etmek istiyorsanız bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb1be-125">You might do this if you are going to reboot a server several times and want to save time by preventing the services that would normally start from starting up.</span></span>

    > [!NOTE]
    > <span data-ttu-id="cb1be-126">Bu ve diğer özellikler, hizmetiniz yüklendikten sonra değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="cb1be-126">These and other properties can be changed after your service is installed.</span></span>

    <span data-ttu-id="cb1be-127">**Sunucu Gezgini**, **Windows Hizmetleri denetim yöneticisinden**veya koddan **el ile** olarak ayarlanmış <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> bir hizmeti başlamanın birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="cb1be-127">There are several ways you can start a service that has its <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> process set to **Manual** — from **Server Explorer**, from the **Windows Services Control Manager**, or from code.</span></span> <span data-ttu-id="cb1be-128">Bu yöntemlerin tümünün hizmeti hizmet **Denetimi Yöneticisi**bağlamında başlatmadığını unutmayın; **Sunucu Gezgini** ve hizmetin başlatılmasına yönelik programlama yöntemleri, denetleyiciyi gerçekten işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="cb1be-128">It is important to note that not all of these methods actually start the service in the context of the **Services Control Manager**; **Server Explorer** and programmatic methods of starting the service actually manipulate the controller.</span></span>

### <a name="to-manually-start-a-service-from-server-explorer"></a><span data-ttu-id="cb1be-129">Sunucu Gezgini bir hizmeti el ile başlatmak için</span><span class="sxs-lookup"><span data-stu-id="cb1be-129">To manually start a service from Server Explorer</span></span>

1. <span data-ttu-id="cb1be-130">**Sunucu Gezgini**, zaten listede yoksa istediğiniz sunucuyu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cb1be-130">In **Server Explorer**, add the server you want if it is not already listed.</span></span> <span data-ttu-id="cb1be-131">Daha fazla bilgi için bkz. nasıl yapılır: erişim ve başlatma Sunucu Gezgini-Veritabanı Gezgini.</span><span class="sxs-lookup"><span data-stu-id="cb1be-131">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>

2. <span data-ttu-id="cb1be-132">**Hizmetler** düğümünü genişletin ve ardından başlatmak istediğiniz hizmeti bulun.</span><span class="sxs-lookup"><span data-stu-id="cb1be-132">Expand the **Services** node, and then locate the service you want to start.</span></span>

3. <span data-ttu-id="cb1be-133">Hizmetin adına sağ tıklayın ve **Başlat**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="cb1be-133">Right-click the name of the service, and click **Start**.</span></span>

### <a name="to-manually-start-a-service-from-services-control-manager"></a><span data-ttu-id="cb1be-134">Hizmet Denetim yöneticisinden bir hizmeti el ile başlatmak için</span><span class="sxs-lookup"><span data-stu-id="cb1be-134">To manually start a service from Services Control Manager</span></span>

1. <span data-ttu-id="cb1be-135">Aşağıdakilerden birini yaparak **Hizmetler denetim yöneticisini** açın:</span><span class="sxs-lookup"><span data-stu-id="cb1be-135">Open the **Services Control Manager** by doing one of the following:</span></span>

    - <span data-ttu-id="cb1be-136">Windows XP ve 2000 Professional 'da, **masaüstünde Bilgisayarım ' a sağ tıklayın ve** ardından **Yönet**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="cb1be-136">In Windows XP and 2000 Professional, right-click **My Computer** on the desktop, and then click **Manage**.</span></span> <span data-ttu-id="cb1be-137">Görüntülenen iletişim kutusunda, **Hizmetler ve uygulamalar** düğümünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="cb1be-137">In the dialog box that appears, expand the **Services and Applications** node.</span></span>

      <span data-ttu-id="cb1be-138">\-veya</span><span class="sxs-lookup"><span data-stu-id="cb1be-138">\- or -</span></span>

    - <span data-ttu-id="cb1be-139">Windows Server 2003 ve Windows 2000 sunucusunda **Başlat**' a tıklayın, **Programlar**' ın üzerine gelin, **Yönetimsel Araçlar**' a ve ardından **Hizmetler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="cb1be-139">In Windows Server 2003 and Windows 2000 Server, click **Start**, point to **Programs**, click **Administrative Tools**, and then click **Services**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="cb1be-140">Windows NT sürüm 4,0 ' de bu iletişim kutusunu **Denetim Masası**'ndan açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb1be-140">In Windows NT version 4.0, you can open this dialog box from **Control Panel**.</span></span>

    <span data-ttu-id="cb1be-141">Şimdi, pencerenin **Hizmetler** bölümünde hizmetinizi görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cb1be-141">You should now see your service listed in the **Services** section of the window.</span></span>

2. <span data-ttu-id="cb1be-142">Listeden hizmetinizi seçin, sağ tıklayın ve ardından **Başlat**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="cb1be-142">Select your service in the list, right-click it, and then click **Start**.</span></span>

### <a name="to-manually-start-a-service-from-code"></a><span data-ttu-id="cb1be-143">Koddan bir hizmeti el ile başlatmak için</span><span class="sxs-lookup"><span data-stu-id="cb1be-143">To manually start a service from code</span></span>

1. <span data-ttu-id="cb1be-144"><xref:System.ServiceProcess.ServiceController> Sınıfının bir örneğini oluşturun ve yönetmek istediğiniz hizmetle etkileşimde bulunmak üzere yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="cb1be-144">Create an instance of the <xref:System.ServiceProcess.ServiceController> class, and configure it to interact with the service you want to administer.</span></span>

2. <span data-ttu-id="cb1be-145">Hizmeti başlatmak <xref:System.ServiceProcess.ServiceController.Start%2A> için yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="cb1be-145">Call the <xref:System.ServiceProcess.ServiceController.Start%2A> method to start the service.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb1be-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb1be-146">See also</span></span>

- [<span data-ttu-id="cb1be-147">Windows Hizmet Uygulamalarına Giriş</span><span class="sxs-lookup"><span data-stu-id="cb1be-147">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="cb1be-148">Nasıl Yapılır: Windows Hizmetleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cb1be-148">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)
- [<span data-ttu-id="cb1be-149">Nasıl Yapılır: Hizmet Uygulamasına Yükleyiciler Ekleme</span><span class="sxs-lookup"><span data-stu-id="cb1be-149">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
