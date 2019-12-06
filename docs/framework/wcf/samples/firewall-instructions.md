---
title: Güvenlik Duvarı Yönergeleri
ms.date: 03/30/2017
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
ms.openlocfilehash: 3c94f0edbb244b6c378cc32f05c34fd029d253ff
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837850"
---
# <a name="firewall-instructions"></a><span data-ttu-id="16014-102">Güvenlik Duvarı Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="16014-102">Firewall Instructions</span></span>
<span data-ttu-id="16014-103">Windows Communication Foundation (WCF) örneklerinin çalışabilmesi için güvenlik duvarındaki çeşitli bağlantı noktalarını veya programları etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="16014-103">You must enable several ports or programs in the firewall so that the Windows Communication Foundation (WCF) samples can function.</span></span> <span data-ttu-id="16014-104">Örneklerin birçoğu 8000-8003 aralığındaki bağlantı noktalarını ve bağlantı noktası 9000 ' yi kullanarak iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="16014-104">Many of the samples communicate by using ports in the range 8000-8003, and port 9000.</span></span> <span data-ttu-id="16014-105">Güvenlik Duvarı varsayılan olarak açıktır ve bu bağlantı noktalarına erişimi engeller.</span><span class="sxs-lookup"><span data-stu-id="16014-105">The firewall is turned on by default and prevents access to these ports.</span></span> <span data-ttu-id="16014-106">Örneklere yönelik güvenlik duvarını etkinleştirmek için, gereksinimlerinize ve güvenlik ortamınıza bağlı olarak aşağıdaki yordamlardan birini yapın:</span><span class="sxs-lookup"><span data-stu-id="16014-106">To enable the firewall for the samples, complete one of the following procedures, depending on your requirements and security environment:</span></span>  
  
- <span data-ttu-id="16014-107">Seçenek 1: çalışırken örnekleri etkileşimli olarak etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="16014-107">Option 1: Interactively enable samples while running.</span></span> <span data-ttu-id="16014-108">Güvenlik Duvarı yapılandırmanızda hiçbir değişiklik yapmayın ve örnekleri oluşturmaya ve çalıştırmaya devam edin.</span><span class="sxs-lookup"><span data-stu-id="16014-108">Make no advance changes to your firewall configuration and proceed to start building and running the samples.</span></span> <span data-ttu-id="16014-109">Bir örnek çalıştırıldığında, bir **Windows Güvenlik Uyarısı** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="16014-109">When a sample is run, a **Windows Security Alert** dialog box appears.</span></span> <span data-ttu-id="16014-110">Söz konusu örnek program, engeli kaldırılmış bir listeye etkileşimli olarak eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="16014-110">The sample program in question can then be added interactively to an unblocked list.</span></span> <span data-ttu-id="16014-111">Bu yordamla, örneği yeniden başlatmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="16014-111">With this procedure, you may have to then restart the sample.</span></span>  
  
- <span data-ttu-id="16014-112">2\. seçenek: örnek programları önceden etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="16014-112">Option 2: Enable sample programs in advance.</span></span> <span data-ttu-id="16014-113">**Windows Güvenlik Duvarı Denetim Masası** uygulamasını başlatın ve çalıştırmayı planladığınız örnek programları etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="16014-113">Start the **Windows Firewall Control Panel** applet and enable the sample programs you plan to run.</span></span> <span data-ttu-id="16014-114">Yürütülebilir dosyaların mevcut olması için önce programları derlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="16014-114">You must build the programs first so the executable files exist.</span></span> <span data-ttu-id="16014-115">Daha ayrıntılı yönergeleri aşağıdaki yordamda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16014-115">You can find more detailed instructions in the following procedure.</span></span>  
  
- <span data-ttu-id="16014-116">Seçenek 3: bir bağlantı noktası aralığını önceden etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="16014-116">Option 3: Enable a port range in advance.</span></span> <span data-ttu-id="16014-117">**Windows Güvenlik Duvarı** **Denetim Masası** uygulamasını başlatın ve örnekler tarafından kullanılan 80, 443, 8000-8003 ve 9000 bağlantı noktalarını etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="16014-117">Start the **Windows Firewall** **Control Panel** applet and enable ports 80, 443, 8000-8003 and 9000, which are used by the samples.</span></span> <span data-ttu-id="16014-118">Daha ayrıntılı yönergeleri aşağıdaki yordamda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16014-118">You can find more detailed instructions in the following procedure.</span></span> <span data-ttu-id="16014-119">Bu seçenek, yalnızca örnekleri değil, herhangi bir programın bu bağlantı noktalarını kullanmasına izin verdiğinden, diğerlerinden daha az güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="16014-119">This option is less secure than the others because it allows any program to use these ports, not just the samples.</span></span>  
  
 <span data-ttu-id="16014-120">Hangi yordamın kullanılacağı konusunda emin değilseniz, ilk seçeneği belirleyin.</span><span class="sxs-lookup"><span data-stu-id="16014-120">If you are unsure of which procedure to use, choose the first option.</span></span> <span data-ttu-id="16014-121">Başka bir satıcıdan güvenlik duvarı çalıştırıyorsanız, benzer değişiklikler yapmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="16014-121">If you are running a firewall from another vendor, you might need to make similar changes.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="16014-122">Güvenlik duvarı yapılandırmanızı değiştirmek güvenliği etkiler.</span><span class="sxs-lookup"><span data-stu-id="16014-122">Changing your firewall configuration affects your security.</span></span> <span data-ttu-id="16014-123">Yaptığınız değişiklikleri kaydetmeniz ve örneklerle çalışmayı bitirdiğinizde onları kaldırmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="16014-123">It is recommended that you record the changes you make and remove them when you are finished working with the samples.</span></span>  
  
### <a name="to-enable-samples-programs-in-advance"></a><span data-ttu-id="16014-124">Örnek programları önceden etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="16014-124">To enable samples programs in advance</span></span>  
  
1. <span data-ttu-id="16014-125">Örneği derleyin.</span><span class="sxs-lookup"><span data-stu-id="16014-125">Build the sample.</span></span>  
  
2. <span data-ttu-id="16014-126">**Başlat**' a tıklayın, **Çalıştır**' a tıklayın ve `firewall.cpl`yazın.</span><span class="sxs-lookup"><span data-stu-id="16014-126">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="16014-127">Bu, **Windows Güvenlik Duvarı Denetim Masası** uygulamasını açar.</span><span class="sxs-lookup"><span data-stu-id="16014-127">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="16014-128">Windows Güvenlik Duvarı üzerinden iletişim kurmayı gerektiren örnekleri çalıştırmak için güvenlik duvarı ayarlarını değiştirme izninizin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="16014-128">You must have permission to change the Firewall settings to run samples that require the ability to communicate through the Windows Firewall.</span></span> <span data-ttu-id="16014-129">Bazı güvenlik duvarı ayarları kullanılamaz durumdaysa ve bilgisayarınız bir etki alanına bağlıysa, sistem yöneticiniz bu ayarları grup ilkesi aracılığıyla denetliyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="16014-129">If some firewall settings are unavailable and your computer is connected to a domain, your system administrator might be controlling these settings through Group Policy.</span></span>  
  
3. <span data-ttu-id="16014-130">Windows Güvenlik Duvarı aracılığıyla bir programa izin vermek için aşağıdaki işletim özel adımlardan birini doldurun:</span><span class="sxs-lookup"><span data-stu-id="16014-130">Complete one of the following operating specific steps to allow a program through the Windows Firewall:</span></span>  
  
    - <span data-ttu-id="16014-131">Windows 7 veya Windows Server 2008 R2 'de **Windows Güvenlik Duvarı üzerinden programa veya özelliğe Izin ver**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="16014-131">On Windows 7 or Windows Server 2008 r2, click **Allow a program or feature through Windows Firewall**.</span></span> <span data-ttu-id="16014-132">**Ayarları Değiştir**' e tıklayın, **başka bir programa izin verin...** .</span><span class="sxs-lookup"><span data-stu-id="16014-132">Click **Change Settings**, Allow **Another Program…**.</span></span>  
  
    - <span data-ttu-id="16014-133">Windows Vista veya [!INCLUDE[lserver](../../../../includes/lserver-md.md)], **Windows Güvenlik Duvarı üzerinden programa Izin ver**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="16014-133">On Windows Vista or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], click **Allow a program through Windows Firewall**.</span></span>  
  
4. <span data-ttu-id="16014-134">**Özel durumlar** sekmesinde **Program Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="16014-134">On the **Exceptions** tab, click **Add Program**.</span></span>  
  
5. <span data-ttu-id="16014-135">**Araştır** düğmesine tıklayın ve çalıştırmayı planladığınız örneğin çalıştırılabilir dosyasını seçin.</span><span class="sxs-lookup"><span data-stu-id="16014-135">Click the **Browse** button and select the executable file of the sample you plan to run.</span></span>  
  
6. <span data-ttu-id="16014-136">Çalıştırmayı planladığınız tüm örneklerin yürütülebilir dosyalarını ekleyinceye kadar 4 ve 5. adımları tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="16014-136">Repeat steps 4 and 5 until you have added the executable files of all the samples you plan to run.</span></span>  
  
7. <span data-ttu-id="16014-137">Güvenlik Duvarı uygulamasını kapatmak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="16014-137">Click **OK** to close the firewall applet.</span></span>  
  
### <a name="to-enable-a-port-range-in-advance"></a><span data-ttu-id="16014-138">Bir bağlantı noktası aralığını önceden etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="16014-138">To enable a port range in advance</span></span>  
  
1. <span data-ttu-id="16014-139">**Başlat**' a tıklayın, **Çalıştır**' a tıklayın ve `firewall.cpl`yazın.</span><span class="sxs-lookup"><span data-stu-id="16014-139">Click **Start**, click **Run**, and type `firewall.cpl`.</span></span> <span data-ttu-id="16014-140">Bu, **Windows Güvenlik Duvarı Denetim Masası** uygulamasını açar.</span><span class="sxs-lookup"><span data-stu-id="16014-140">This opens the **Windows Firewall Control Panel** applet.</span></span>  
  
2. <span data-ttu-id="16014-141">Windows 7 veya Windows Server 2008 R2 'de, aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="16014-141">On Windows 7 or Windows Server 2008 R2, follow these steps.</span></span>  
  
    1. <span data-ttu-id="16014-142">Windows Güvenlik Duvarı penceresinin sol sütununda **Gelişmiş ayarlar** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="16014-142">Click **Advanced settings** in the left column of the Windows Firewall window.</span></span>  
  
    2. <span data-ttu-id="16014-143">Sol sütundaki **gelen kurallar** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="16014-143">Click **Inbound Rules** in the left column.</span></span>  
  
    3. <span data-ttu-id="16014-144">Sağ sütundaki **yeni kurallar** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="16014-144">Click **New Rules** in the right column.</span></span>  
  
    4. <span data-ttu-id="16014-145">**Bağlantı noktasını** seçin ve **İleri**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="16014-145">Select **Port** and click **next**.</span></span>  
  
    5. <span data-ttu-id="16014-146">**TCP** ' yi seçin ve **belirli yerel bağlantı noktaları** alanına `8000, 8001, 8002, 8003, 9000, 80, 443` girin.</span><span class="sxs-lookup"><span data-stu-id="16014-146">Select **TCP** and enter `8000, 8001, 8002, 8003, 9000, 80, 443` in the **Specific local ports** field.</span></span>  
  
    6. <span data-ttu-id="16014-147">**İleri**'ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="16014-147">Click **Next**.</span></span>  
  
    7. <span data-ttu-id="16014-148">**Bağlantıya Izin ver**' i seçin ve **İleri** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="16014-148">Select **Allow the connection**, and click **Next** .</span></span>  
  
    8. <span data-ttu-id="16014-149">**Etki alanı** ve **özel**' i seçin ve **İleri**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="16014-149">Select **Domain** and **Private**, and click **Next**.</span></span>  
  
    9. <span data-ttu-id="16014-150">Bu kuralı `WCF-WF 4.0 Samples`adlandırın ve **son**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="16014-150">Name this rule `WCF-WF 4.0 Samples`, and click **Finish**.</span></span>  
  
    10. <span data-ttu-id="16014-151">**Giden kuralları** ' na tıklayın ve adımları c-h olarak tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="16014-151">Click **Outbound Rules** and repeat steps c to h.</span></span>  
  
3. <span data-ttu-id="16014-152">Windows Vista veya [!INCLUDE[lserver](../../../../includes/lserver-md.md)]'de, aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="16014-152">On Windows Vista or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], follow these steps.</span></span>  
  
    1. <span data-ttu-id="16014-153">**Windows Güvenlik Duvarı üzerinden programa Izin ver**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="16014-153">Click **Allow a program through Windows Firewall**.</span></span>  
  
    2. <span data-ttu-id="16014-154">**Özel durumlar** sekmesinde, **bağlantı noktası Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="16014-154">On the **Exceptions** tab, click **Add Port**.</span></span>  
  
    3. <span data-ttu-id="16014-155">Bir ad girin, bağlantı noktası numarası olarak 8000 girin ve **TCP** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="16014-155">Enter a name, enter 8000 as the port number, and select the **TCP** option.</span></span>  
  
    4. <span data-ttu-id="16014-156">**Kapsamı Değiştir** düğmesine tıklayın, yalnızca ağ (alt ağ) seçeneğini belirleyin ve **Tamam**' **a** tıklayın.</span><span class="sxs-lookup"><span data-stu-id="16014-156">Click the **Change Scope** button, select the **My Network** (subnet) only option, and click **OK**.</span></span>  
  
    5. <span data-ttu-id="16014-157">8001, 8002, 8003, 9000, 80 ve 443 bağlantı noktaları için b ile d arasındaki adımları yineleyin.</span><span class="sxs-lookup"><span data-stu-id="16014-157">Repeat steps b to d for ports 8001, 8002, 8003, 9000, 80, and 443.</span></span>  
  
4. <span data-ttu-id="16014-158">Güvenlik Duvarı uygulamasını kapatmak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="16014-158">Click **OK** to close the firewall applet.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="16014-159">Örneklerle çalışmayı bitirdiğinizde tüm güvenlik duvarı özel durumlarını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="16014-159">Remove any firewall exceptions when you are finished working with the samples.</span></span> <span data-ttu-id="16014-160">Bunu yapmak için, **Windows Güvenlik Duvarı Denetim Masası** uygulamasını açın ve önceki yordamlar tarafından eklenen tüm programları veya bağlantı noktası girişlerini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="16014-160">To do so, open the **Windows Firewall Control Panel** applet and remove any programs or port entries that were added by the previous procedures.</span></span>
