---
description: 'Daha fazla bilgi edinin: sanal dizin kurulum yönergeleri'
title: Sanal Dizin Ayarlama Yönergeleri
ms.date: 03/30/2017
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
ms.openlocfilehash: 4b1a68fb657a59e9858c6efa7931c5d106231605
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755713"
---
# <a name="virtual-directory-setup-instructions"></a><span data-ttu-id="c1db9-103">Sanal Dizin Ayarlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="c1db9-103">Virtual Directory Setup Instructions</span></span>

<span data-ttu-id="c1db9-104">Windows Communication Foundation (WCF) örnekleri,%SystemDrive%\inetpub\wwwroot\servicemodelsamples klasörüne eşlenmiş servicemodelsamples adlı ortak bir sanal dizinin paylaşılması için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c1db9-104">The Windows Communication Foundation (WCF) samples are intended to share a common virtual directory named servicemodelsamples that is mapped to the %SystemDrive%\inetpub\wwwroot\servicemodelsamples folder.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c1db9-105">% SystemDrive%, Internet Information Services (IIS) yüklü olduğu sürücü konumuna bağlı olarak genellikle C: veya D: ' dır.</span><span class="sxs-lookup"><span data-stu-id="c1db9-105">%SystemDrive% is usually C: or D:, depending on the drive location where Internet Information Services (IIS) is installed.</span></span>  
  
 <span data-ttu-id="c1db9-106">Sanal dizini oluşturmak için [Windows Communication Foundation Örnekleri Için tek seferlik kurulum yordamından](one-time-setup-procedure-for-the-wcf-samples.md) Setupvroot.bat ve Cleanupvroot.bat dosyalarını çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1db9-106">You can run the Setupvroot.bat and Cleanupvroot.bat files from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md) to create the virtual directory.</span></span> <span data-ttu-id="c1db9-107">Sanal dizini el ile oluşturmayı tercih ediyorsanız, aşağıdaki yordamları kullanın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-107">If you prefer to create the virtual directory manually, use the following procedures.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="c1db9-108">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="c1db9-108">Procedures</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a><span data-ttu-id="c1db9-109">IIS 7,0 veya 7,5 ' de bir sanal dizin oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c1db9-109">To create a virtual directory in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="c1db9-110">**Başlat** menüsünde **Çalıştır**' a tıklayın ve ardından Internet INFORMATION SERVICES (IIS) MMC ek bileşenini açmak için **inetmgr** yazın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-110">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="c1db9-111">Sol bölmede, bilgisayarın adı ile düğümünü genişletin ve ardından **siteler** düğümünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="c1db9-111">In the left pane, expand the node with the computer's name, and then expand the **Sites** node.</span></span>  
  
3. <span data-ttu-id="c1db9-112">**Varsayılan Web sitesi**' ne sağ tıklayın ve **ardından uygulama Ekle ' yi seçerek** **Uygulama Ekle penceresini** açın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-112">Right-click **Default Web Site**, and then select **Add Application** to open the **Add Application window**.</span></span>  
  
4. <span data-ttu-id="c1db9-113">Penceresinde, `servicemodelsamples` oluşturmakta olduğunuz sanal dizinin diğer adı olarak yazın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-113">In the window, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5. <span data-ttu-id="c1db9-114">Şu dizini oluşturun:%SystemDrive%\inetpub\wwwroot\servicemodelsamples</span><span class="sxs-lookup"><span data-stu-id="c1db9-114">Create the following directory: %SystemDrive%\inetpub\wwwroot\servicemodelsamples</span></span>  
  
6. <span data-ttu-id="c1db9-115">Fiziksel yolu%SystemDrive%\inetpub\wwwroot\servicemodelsamples. olarak ayarla</span><span class="sxs-lookup"><span data-stu-id="c1db9-115">Set the physical path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  <span data-ttu-id="c1db9-116">WCF örneklerinin çoğu yapılandırıldığında bu konuma hizmet yürütülebilir dosyalarını kopyalar.</span><span class="sxs-lookup"><span data-stu-id="c1db9-116">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
7. <span data-ttu-id="c1db9-117">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-117">Click **OK**.</span></span> <span data-ttu-id="c1db9-118">Web uygulaması artık WCF örnekleri için oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="c1db9-118">The Web application is now created for the WCF samples.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c1db9-119">Tüm WCF örnekleri aynı servicemodelsamples Web uygulamasını kullandığından, bu görevin yalnızca bir kez gerçekleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c1db9-119">This task must be performed only once, because all of the WCF samples use the same servicemodelsamples Web application.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c1db9-120">Bu belgenin amacına yönelik terim, `virtual directory` ile eşanlamlıdır `Web application` .</span><span class="sxs-lookup"><span data-stu-id="c1db9-120">For the purpose of this documentation, the term `virtual directory` is synonymous with `Web application`.</span></span>  
  
     <span data-ttu-id="c1db9-121">Sanal dizin oluşturmanın yanı sıra, WCF hizmetlerinin çalışmasını sağlamak için özelliklerini de ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c1db9-121">In addition to creating the virtual directory, you must also set its properties to enable WCF services to run.</span></span> <span data-ttu-id="c1db9-122">Ayrıntılar için aşağıya bakın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-122">See below for details.</span></span>  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a><span data-ttu-id="c1db9-123">IIS 5,1 veya 6,0 ' de bir sanal dizin oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c1db9-123">To create a virtual directory in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="c1db9-124">Bir komut istemi penceresi açın ve `start inetmgr` Internet Information Services (IIS) MMC ek bileşenini açmak için yazın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-124">Open a command prompt window and type `start inetmgr` to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="c1db9-125">Sol bölmede, bilgisayarın adı ile düğümünü genişletin ve ardından **Web siteleri** düğümünü genişletin.</span><span class="sxs-lookup"><span data-stu-id="c1db9-125">In the left pane, expand the node with the computer's name, and then expand the **Web Sites** node.</span></span>  
  
3. <span data-ttu-id="c1db9-126">**Varsayılan Web sitesi** ' ne sağ tıklayın ve **Yeni, sanal dizin** ' i seçerek sanal dizin oluşturma Sihirbazı 'nı açın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-126">Right-click **Default Web Site** and select **New, Virtual Directory** to open the Virtual Directory Creation wizard.</span></span>  
  
4. <span data-ttu-id="c1db9-127">Sihirbazda, `servicemodelsamples` oluşturmakta olduğunuz sanal dizinin diğer adı olarak yazın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-127">In the wizard, type `servicemodelsamples` as the alias for the virtual directory that you are creating.</span></span>  
  
5. <span data-ttu-id="c1db9-128">Yolu%SystemDrive%\inetpub\wwwroot\servicemodelsamples. olarak ayarlayın</span><span class="sxs-lookup"><span data-stu-id="c1db9-128">Set the path to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span> <span data-ttu-id="c1db9-129">WCF örneklerinin çoğu yapılandırıldığında bu konuma hizmet yürütülebilir dosyalarını kopyalar.</span><span class="sxs-lookup"><span data-stu-id="c1db9-129">Most of the WCF samples copy service executable files to this location when built.</span></span>  
  
6. <span data-ttu-id="c1db9-130">**İleri**’ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-130">Click **Next**.</span></span>  
  
7. <span data-ttu-id="c1db9-131">Varsayılan olarak, aşağıdaki onay kutuları seçilidir:</span><span class="sxs-lookup"><span data-stu-id="c1db9-131">By default, the following check boxes are selected:</span></span>  
  
    - <span data-ttu-id="c1db9-132">**Okuyamaz**</span><span class="sxs-lookup"><span data-stu-id="c1db9-132">**Read**</span></span>  
  
    - <span data-ttu-id="c1db9-133">**Betikleri Çalıştır (ASP gibi)**</span><span class="sxs-lookup"><span data-stu-id="c1db9-133">**Run scripts (such as ASP)**</span></span>  
  
8. <span data-ttu-id="c1db9-134">**İleri**' ye tıklayın ve Sihirbazı tamamladıktan sonra **son** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-134">Click **Next**, and then click **Finish** to complete the wizard.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c1db9-135">Tüm WCF örnekleri aynı servicemodelsamples sanal dizinini kullandığından, bu görevin yalnızca bir kez gerçekleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c1db9-135">This task must be performed only once because all of the WCF samples use the same servicemodelsamples virtual directory.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a><span data-ttu-id="c1db9-136">IIS 7,0 veya 7,5 ' de ek sanal dizin özellikleri ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="c1db9-136">To set additional virtual directory properties in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="c1db9-137">Servicemodelsamples düğümüne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-137">Click the servicemodelsamples node.</span></span> <span data-ttu-id="c1db9-138">Pencerenin alt kısmında iki görünüm listelenir.</span><span class="sxs-lookup"><span data-stu-id="c1db9-138">Along the bottom of the window, two views are listed.</span></span> <span data-ttu-id="c1db9-139">Henüz seçili değilse **Özellikler Görünümü** ' nü seçin.</span><span class="sxs-lookup"><span data-stu-id="c1db9-139">Select **Features View** if it isn’t already selected.</span></span>  
  
2. <span data-ttu-id="c1db9-140">**Dizin tarama** girişine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-140">Double-click the entry for **Directory Browsing**.</span></span>  
  
3. <span data-ttu-id="c1db9-141">Eylemler bölmesinde **Etkinleştir** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="c1db9-141">In the Actions pane, select the **Enable** option.</span></span> <span data-ttu-id="c1db9-142">Bu, bir hizmetin Hata ayıklamasında yardımcı olan Internet Explorer 'ı kullanarak dizinin dizinine erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1db9-142">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
 <span data-ttu-id="c1db9-143">Son olarak, servicemodelsamples klasörünün güvenlik özelliklerini diğerlerinin erişmesine izin verecek şekilde ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c1db9-143">Finally, you must set the security properties of the servicemodelsamples folder to allow it to be accessed by others.</span></span> <span data-ttu-id="c1db9-144">Ayrıntılar için aşağıya bakın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-144">See below for details.</span></span>  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a><span data-ttu-id="c1db9-145">IIS 5,1 veya 6,0 ' de ek sanal dizin özellikleri ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="c1db9-145">To set additional virtual directory properties in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="c1db9-146">Servicemodelsamples düğümüne sağ tıklayın ve ardından **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-146">Right-click the servicemodelsamples node and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="c1db9-147">Varsayılan olarak, aşağıdaki onay kutuları seçilidir:</span><span class="sxs-lookup"><span data-stu-id="c1db9-147">By default, the following check boxes are selected:</span></span>  
  
    - <span data-ttu-id="c1db9-148">**Okuyamaz**</span><span class="sxs-lookup"><span data-stu-id="c1db9-148">**Read**</span></span>  
  
    - <span data-ttu-id="c1db9-149">**Günlüğe ziyaretleri Kaydet**</span><span class="sxs-lookup"><span data-stu-id="c1db9-149">**Log visits**</span></span>  
  
    - <span data-ttu-id="c1db9-150">**Bu kaynağı dizine oluştur**</span><span class="sxs-lookup"><span data-stu-id="c1db9-150">**Index this resource**</span></span>  
  
3. <span data-ttu-id="c1db9-151">**Dizin tarama** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="c1db9-151">Select the **Directory browsing** check box.</span></span> <span data-ttu-id="c1db9-152">Bu, bir hizmetin Hata ayıklamasında yardımcı olan Internet Explorer 'ı kullanarak dizinin dizinine erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1db9-152">This enables you to access the directory of the directory by using Internet Explorer, which helps when debugging a service.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a><span data-ttu-id="c1db9-153">IIS 7,0 veya 7,5 ' de klasörün güvenlik özelliklerini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="c1db9-153">To set security properties of the folder in IIS 7.0 or 7.5</span></span>  
  
1. <span data-ttu-id="c1db9-154">%SystemDrive%\inetpub\wwwroot\servicemodelsamples. adresine gidin</span><span class="sxs-lookup"><span data-stu-id="c1db9-154">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2. <span data-ttu-id="c1db9-155">Servicemodelsamples klasörüne sağ tıklayın ve **paylaşma** ya da **paylaşma**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-155">Right-click the servicemodelsamples folder and click **Share** or **Share With**.</span></span>  
  
3. <span data-ttu-id="c1db9-156">**Ekle** düğmesinin solundaki aşağı oka tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-156">Click the down arrow to the left of the **Add** button.</span></span>  
  
4. <span data-ttu-id="c1db9-157">**Find** girişini seçin.</span><span class="sxs-lookup"><span data-stu-id="c1db9-157">Select the **Find** entry.</span></span> <span data-ttu-id="c1db9-158">**Kullanıcıları veya grupları seç** penceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="c1db9-158">The **Select Users or Groups** window opens.</span></span>  
  
5. <span data-ttu-id="c1db9-159">**Gelişmiş**'e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-159">Click **Advanced**.</span></span>  
  
6. <span data-ttu-id="c1db9-160">**Konumlar**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-160">Click **Locations**.</span></span> <span data-ttu-id="c1db9-161">**Konumlar** penceresi artık açıktır.</span><span class="sxs-lookup"><span data-stu-id="c1db9-161">The **Locations** window is now open.</span></span>  
  
7. <span data-ttu-id="c1db9-162">Kullanılan bilgisayar için girişi seçin.</span><span class="sxs-lookup"><span data-stu-id="c1db9-162">Select the entry for the computer being used.</span></span> <span data-ttu-id="c1db9-163">Listelenen herhangi bir etki alanı veya ağ için bir giriş değil, yerel bilgisayarı seçmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="c1db9-163">It is important to select the local computer and not an entry for any domains or networks that are listed.</span></span> <span data-ttu-id="c1db9-164">Bilgisayarı seçtikten sonra **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-164">After you have selected the computer, click **OK**.</span></span>  
  
8. <span data-ttu-id="c1db9-165">**Şimdi bul**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-165">Click **Find Now**.</span></span> <span data-ttu-id="c1db9-166">Bu, arama sonuçlarını yerel bilgisayarla ilişkili nesnelerle doldurur.</span><span class="sxs-lookup"><span data-stu-id="c1db9-166">This populates the search results with objects associated with the local computer.</span></span>  
  
9. <span data-ttu-id="c1db9-167">**Ad (göreli ayırt edici ad)** sütununda **IIS_IUSRS** girdisini bulun.</span><span class="sxs-lookup"><span data-stu-id="c1db9-167">Find the **IIS_IUSRS** entry in the **Name (Relative Distinguished Name)** column.</span></span> <span data-ttu-id="c1db9-168">Bu girişi seçin ve **Tamam** ' a tıklayarak arama sonuçları penceresini kapatın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-168">Select that entry and click **OK** to close the search results window.</span></span>  
  
10. <span data-ttu-id="c1db9-169">**Tamam** ' a tıklayarak **kullanıcıları veya grupları seç** penceresini kapatın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-169">Click **OK** to close the **Select Users or Groups** window.</span></span>  
  
11. <span data-ttu-id="c1db9-170">Değişiklikleri kalıcı hale getirmek için **paylaşma** ' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-170">Click **Share** to persist the changes.</span></span>  
  
12. <span data-ttu-id="c1db9-171">Paylaşımı etkinleştirme değişiklikleri tamamlandıktan sonra, **dosya paylaşımı** penceresini kapatmak için **bitti** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-171">After the changes to enable sharing are complete, click **Done** to close the **File Sharing** window.</span></span>  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a><span data-ttu-id="c1db9-172">IIS 5,1 veya 6,0 ' de klasörün güvenlik özelliklerini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="c1db9-172">To set security properties of the folder in IIS 5.1 or 6.0</span></span>  
  
1. <span data-ttu-id="c1db9-173">%SystemDrive%\inetpub\wwwroot\servicemodelsamples. adresine gidin</span><span class="sxs-lookup"><span data-stu-id="c1db9-173">Navigate to %SystemDrive%\inetpub\wwwroot\servicemodelsamples.</span></span>  
  
2. <span data-ttu-id="c1db9-174">**Servicemodelsamples** klasörüne sağ tıklayın ve ardından **Paylaşım ve güvenlik** ' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-174">Right-click the **servicemodelsamples** folder and then click **Sharing and Security.**</span></span>  
  
3. <span data-ttu-id="c1db9-175">**Güvenlik** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-175">Click the **Security** tab.</span></span>  
  
4. <span data-ttu-id="c1db9-176">IIS 6,0 kullanıyorsanız, **Grup veya Kullanıcı adları** kutusunda **Internet Konuk hesabının** listelenip listelenmediğini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c1db9-176">If you are using IIS 6.0, in the **Group or user names** box, check whether **Internet Guest Account** is listed.</span></span>  
  
     <span data-ttu-id="c1db9-177">Listede yoksa:</span><span class="sxs-lookup"><span data-stu-id="c1db9-177">If it is not listed:</span></span>  
  
    1. <span data-ttu-id="c1db9-178">**Başlat** ' a ve ardından **Denetim Masası**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-178">Click **Start** and then click **Control Panel**.</span></span>  
  
    2. <span data-ttu-id="c1db9-179">**Kullanıcı hesapları** simgesini görmüyorsanız **Kategori görünümüne geç ' e** tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-179">If you do not see the **User Accounts** icon, click **Switch to Category View**.</span></span>  
  
    3. <span data-ttu-id="c1db9-180">**Kullanıcı hesapları** simgesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-180">Click the **User Accounts** icon.</span></span>  
  
    4. <span data-ttu-id="c1db9-181">"Veya bir Denetim Masası simgesi seçin" altında **Kullanıcı hesapları**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-181">Under "or pick a Control Panel icon," click **User Accounts**.</span></span>  
  
    5. <span data-ttu-id="c1db9-182">**Kullanıcı hesapları** Iletişim kutusunda **Gelişmiş** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-182">In the **User Accounts** dialog box, click the **Advanced** tab.</span></span>  
  
    6. <span data-ttu-id="c1db9-183">**Gelişmiş**'e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-183">Click **Advanced**.</span></span>  
  
    7. <span data-ttu-id="c1db9-184">**Yerel kullanıcılar ve gruplar** Iletişim kutusunda **Kullanıcılar** klasörünü genişletmek için tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-184">In the **Local Users and Groups** dialog box, click to expand the **Users** folder.</span></span>  
  
    8. <span data-ttu-id="c1db9-185">Sağ bölmede **Internet Konuk hesabı**' na çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-185">In the right pane, double-click **Internet Guest Account**.</span></span>  
  
    9. <span data-ttu-id="c1db9-186">**Özellikler** iletişim kutusunda, Internet Konuk hesabı olarak kullanılan adı kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-186">In the **Properties** dialog box, copy the name used as the Internet guest account.</span></span> <span data-ttu-id="c1db9-187">Varsayılan olarak, ad "USR_" ile başlar ve ardından bilgisayarın adı gelir.</span><span class="sxs-lookup"><span data-stu-id="c1db9-187">By default, the name begins with "USR_" followed by the name of the computer.</span></span>  
  
    10. <span data-ttu-id="c1db9-188">**Özellikler** iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-188">Close the **Properties** dialog box.</span></span>  
  
    11. <span data-ttu-id="c1db9-189">**Yerel kullanıcılar ve gruplar** iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-189">Close the **Local Users and Groups** dialog box.</span></span>  
  
    12. <span data-ttu-id="c1db9-190">**Kullanıcı hesapları** iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-190">Close the **User Accounts** dialog box.</span></span>  
  
    13. <span data-ttu-id="c1db9-191">Diğer **Kullanıcı hesapları** iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-191">Close the other **User Accounts** dialog box.</span></span>  
  
    14. <span data-ttu-id="c1db9-192">**Servicemodelsamples özellikleri** iletişim kutusunda, **güvenlik** sekmesinde, **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-192">In the **servicemodelsamples Properties** dialog box, on the **Security** tab, click **Add**.</span></span>  
  
    15. <span data-ttu-id="c1db9-193">Bilgisayarın adını ve ters eğik çizgiyi yazın, ardından Internet Kullanıcı hesabının adını yapıştırın, örneğin, myMachineName \\ % InternetGuestAccountName%</span><span class="sxs-lookup"><span data-stu-id="c1db9-193">Type the name of the computer followed by a backslash, then paste the name of the Internet user account, for example, myMachineName\\%InternetGuestAccountName%</span></span>  
  
    16. <span data-ttu-id="c1db9-194">Eklemeyi doğrulamak için **adları denetle** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-194">Click **Check Names** to verify the addition.</span></span> <span data-ttu-id="c1db9-195">Geçerliyse, ad tüm büyük harflerle ve altı çizilir.</span><span class="sxs-lookup"><span data-stu-id="c1db9-195">If it is valid, the name is in all capital letters and is underlined.</span></span>  
  
5. <span data-ttu-id="c1db9-196">IIS 6,0 için, ağ HIZMETI 'nin **Grup veya Kullanıcı adları** kutusunda listelendiğini de denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c1db9-196">For IIS 6.0, also check that NETWORK SERVICE is listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="c1db9-197">Ağ HIZMETI listelenmiyorsa:</span><span class="sxs-lookup"><span data-stu-id="c1db9-197">If NETWORK SERVICE is not listed:</span></span>  
  
    1. <span data-ttu-id="c1db9-198">**Ekle**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-198">Click **Add**.</span></span>  
  
    2. <span data-ttu-id="c1db9-199">**Kullanıcı veya Grup Seç** iletişim kutusunda, bilgisayarın adını ve ardından bir ters eğik çizgi yazın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-199">In the **Select Users or Groups** dialog box, type the name of the computer followed by a backslash.</span></span>  
  
    3. <span data-ttu-id="c1db9-200">Ters eğik çizgiden sonra **hizmet** yazın (boşluk olmadan).</span><span class="sxs-lookup"><span data-stu-id="c1db9-200">Type **service** after the backslash (no space).</span></span>  
  
    4. <span data-ttu-id="c1db9-201">**Adları denetle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-201">Click **Check names**.</span></span>  
  
    5. <span data-ttu-id="c1db9-202">Birden çok ad bulunursa **ağ hizmeti** ' ni seçin ve **Tamam**' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-202">If multiple names are found, select **NETWORK SERVICE** and click **OK**.</span></span>  
  
    6. <span data-ttu-id="c1db9-203">**Tamam** ' a tıklayarak **kullanıcıları veya grupları seç** iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-203">Click **OK** to close the **Select Users or Groups** dialog box.</span></span>  
  
6. <span data-ttu-id="c1db9-204">IIS 5,1 ile Windows XP SP2 kullanıyorsanız, hem Internet Konuk hesabı hem de ASPNET 'in **Grup veya Kullanıcı adları** kutusunda listelendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="c1db9-204">If you are using Windows XP SP2 with IIS 5.1, check that both Internet Guest Account and ASPNET are listed in the **Group or user names** box.</span></span>  
  
     <span data-ttu-id="c1db9-205">ASPNET kullanıcısının yerleşik **Kullanıcılar** güvenlik grubunun bir üyesi olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-205">Note that the ASPNET user may be a member of the built-in **Users** security group.</span></span> <span data-ttu-id="c1db9-206">Bu durumda, **Kullanıcılar** grubu iletişim kutusunda listeleniyorsa, izin verilen kullanıcılar listesine ayrı bir öğe olarak eklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c1db9-206">If so, then if the **Users** group is listed in the dialog box, you do not need to add it as a separate item to the list of permitted users.</span></span>  
  
     <span data-ttu-id="c1db9-207">ASPNET 'in **Kullanıcılar** güvenlik grubunun bir parçası olup olmadığını denetlemek için:</span><span class="sxs-lookup"><span data-stu-id="c1db9-207">To check if ASPNET is part of the **Users** security group:</span></span>  
  
    1. <span data-ttu-id="c1db9-208">**Başlat** menüsünde, **Denetim Masası**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-208">On the **Start** menu, click **Control Panel**.</span></span>  
  
    2. <span data-ttu-id="c1db9-209">**Kullanıcı hesapları** simgesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1db9-209">Click the **User Accounts** icon.</span></span>  
  
    3. <span data-ttu-id="c1db9-210">**Grup** sütununda, **ASPNET** değerinin "kullanıcılar" olup olmadığını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="c1db9-210">In the **Group** column, check that the value for **ASPNET** is "Users."</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1db9-211">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1db9-211">See also</span></span>

- [<span data-ttu-id="c1db9-212">Internet Information Service Barındırma Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="c1db9-212">Internet Information Service Hosting Instructions</span></span>](internet-information-service-hosting-instructions.md)
