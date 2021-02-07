---
description: 'Daha fazla bilgi edinin: genişletilmiş koruma kimlik doğrulama örneği için ReadMe'
title: Genişletilmiş Koruma Kimlik Doğrulama için Beni Oku Örnek
ms.date: 03/30/2017
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
ms.openlocfilehash: edab04c7762bf8964f634107debd3de35a7702ab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733313"
---
# <a name="readme-for-extended-protection-authentication-sample"></a><span data-ttu-id="a4b20-103">Genişletilmiş Koruma Kimlik Doğrulama için Beni Oku Örnek</span><span class="sxs-lookup"><span data-stu-id="a4b20-103">ReadMe for Extended Protection Authentication Sample</span></span>

<span data-ttu-id="a4b20-104">Genişletilmiş koruma, bir saldırganın ("ortadaki adam") bir istemcinin kimlik bilgilerini aldığı ve istemcinin hedeflenen sunucusundaki güvenli kaynaklara erişmek için bunları kullandığı, ortadaki adam (MITı) saldırılarına karşı koruma sağlayan bir güvenlik girişimidir.</span><span class="sxs-lookup"><span data-stu-id="a4b20-104">Extended Protection is a security initiative to protect against man-in-the-middle (MITM) attacks, in which an attacker (the "man-in-the-middle") intercepts a client’s credentials and uses them to access secure resources on the client’s intended server.</span></span>

<span data-ttu-id="a4b20-105">Daha fazla bilgi için bkz. [kimlik doğrulaması için genişletilmiş koruma genel bakış](extended-protection-for-authentication-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a4b20-105">For more information, see [Extended Protection for Authentication Overview](extended-protection-for-authentication-overview.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a4b20-106">Bu örnek yalnızca IIS üzerinde barındırıldığında geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a4b20-106">This sample only works when hosted on IIS.</span></span> <span data-ttu-id="a4b20-107">Bu, HTTPS 'yi desteklemediğinden, Visual Studio geliştirme sunucusu üzerinde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="a4b20-107">It does not work on Visual Studio Development Server because that does not support HTTPS.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a4b20-108">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a4b20-108">To Set Up, Build, and Run the Sample</span></span>

1. <span data-ttu-id="a4b20-109">Program Ekle/Kaldır-> Windows Özellikleri ' nden makineye IIS 'yi yükler.</span><span class="sxs-lookup"><span data-stu-id="a4b20-109">Install IIS on the machine from Add/Remove Programs -> Windows Features.</span></span>

2. <span data-ttu-id="a4b20-110">Windows özelliklerinde Windows kimlik doğrulamasını aç: Internet Information Services > World Wide Web Hizmetleri-> güvenlik-> Windows kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="a4b20-110">Turn on Windows Authentication in Windows features: Internet Information Services -> World Wide Web Services -> Security -> Windows Authentication.</span></span>

3. <span data-ttu-id="a4b20-111">Windows özelliklerinde HTTP etkinleştirmesini aç: Microsoft .NET Framework 3.5.1-> Windows Communication Foundation HTTP etkinleştirmesi.</span><span class="sxs-lookup"><span data-stu-id="a4b20-111">Turn on HTTP Activation in Windows features: Microsoft .NET Framework 3.5.1 -> Windows Communication Foundation HTTP Activation.</span></span>

4. <span data-ttu-id="a4b20-112">Bu örnek, istemcisinin sunucu ile güvenli bir kanal kurmasını ve bu nedenle Internet Information Services (IIS) yöneticisinden yüklenebilen bir sunucu sertifikası olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a4b20-112">This sample requires the client to establish a secure channel with the server and so it requires the presence of a server certificate which can be installed from Internet Information Services (IIS) Manager.</span></span>

    1. <span data-ttu-id="a4b20-113">IIS Yöneticisi-> sunucusu sertifikalarını açın (Özellik görünümü sekmesinden).</span><span class="sxs-lookup"><span data-stu-id="a4b20-113">Open the IIS manager -> Server certificates (from the feature view tab).</span></span>

    2. <span data-ttu-id="a4b20-114">Bu örneği test etmek amacıyla kendinden imzalı bir sertifika oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4b20-114">For the purpose of testing this sample, you can create a self-signed certificate.</span></span> <span data-ttu-id="a4b20-115">(Internet Explorer 'ın sertifikayı güvenli hale getirmek için size sormasını istemiyorsanız, güvenilir sertifika kök yetkilisi deposuna yükleyebilirsiniz).</span><span class="sxs-lookup"><span data-stu-id="a4b20-115">(If you don’t want Internet Explorer to prompt you about the certificate not being secure, you can install it in the Trusted Certificate Root authority store).</span></span>

5. <span data-ttu-id="a4b20-116">Varsayılan Web sitesi için eylemler bölmesine gidin.</span><span class="sxs-lookup"><span data-stu-id="a4b20-116">Go to the Actions pane for the Default Web site.</span></span> <span data-ttu-id="a4b20-117">Site > bağlamalarını Düzenle ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a4b20-117">Click Edit Site -> Bindings.</span></span> <span data-ttu-id="a4b20-118">Zaten mevcut değilse HTTPS 'yi bir tür olarak ekleyin, bağlantı noktası numarası 443 ve yukarıdaki adımda oluşturulan SSL sertifikasını atayın.</span><span class="sxs-lookup"><span data-stu-id="a4b20-118">Add HTTPS as a type if it is not already present, with port number 443, and assign the SSL certificate created in the above step.</span></span>

6. <span data-ttu-id="a4b20-119">Hizmeti oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a4b20-119">Build the service.</span></span> <span data-ttu-id="a4b20-120">Bu, IIS 'de sizin için bir sanal dizin oluşturur (proje özelliklerinde belirtilen derleme sonrası eyleminden) ve bir hizmetin Web 'de barındırılması için gerektiğinde dll,. svc ve yapılandırma dosyalarını kopyalar.</span><span class="sxs-lookup"><span data-stu-id="a4b20-120">This creates a virtual directory in IIS for you (from the post build action specified in the project properties) and copies the dll, .svc and config files as needed for a service to be Web hosted.</span></span>

7. <span data-ttu-id="a4b20-121">IIS Yöneticisi 'Ni açın.</span><span class="sxs-lookup"><span data-stu-id="a4b20-121">Open the IIS Manager.</span></span> <span data-ttu-id="a4b20-122">Önceki adımda oluşturduğunuz sanal dizine (ExtendedProtection) sağ tıklayın ve uygulamaya Dönüştür ' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="a4b20-122">Right-click the virtual directory (ExtendedProtection) that you created in the previous step and select Convert to Application.</span></span>

8. <span data-ttu-id="a4b20-123">Bu sanal dizin için IIS Yöneticisi 'nde kimlik doğrulama modülünü açın ve Windows kimlik doğrulamasını etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="a4b20-123">Open the Authentication module in IIS Manager for this virtual directory and enable Windows Authentication.</span></span>

9. <span data-ttu-id="a4b20-124">Bu sanal dizin için Windows kimlik doğrulaması için Gelişmiş ayarlar ' ı açın ve gerekli olarak ayarlayın, çünkü örnekte ilgili ExtendedProtection ayarı her zaman olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a4b20-124">Open the Advanced Settings for Windows Authentication for this virtual directory and set it to Required, since, in the sample, the corresponding ExtendedProtection setting is set to Always.</span></span>

10. <span data-ttu-id="a4b20-125">Bir tarayıcı penceresinden URL 'ye erişerek hizmeti test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4b20-125">You can test the service by accessing the URL from a browser window.</span></span> <span data-ttu-id="a4b20-126">Bu URL 'YI bir çapraz makineden erişmek istiyorsanız, tüm gelen HTTP ve HTTPS bağlantıları için güvenlik duvarının açık olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a4b20-126">If you want to access this URL from a cross machine, make sure that the firewall is opened for all incoming HTTP and HTTPS connections.</span></span>

11. <span data-ttu-id="a4b20-127">İstemci yapılandırma dosyasını açın ve \<client>  -  \<endpoint> yerine-address özniteliği için tam makine adı girin \<full_machine_name> .</span><span class="sxs-lookup"><span data-stu-id="a4b20-127">Open the client config file and provide a full machine name for the \<client> - \<endpoint> - address attribute, replacing \<full_machine_name>.</span></span>

12. <span data-ttu-id="a4b20-128">İstemcisini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a4b20-128">Run the client.</span></span> <span data-ttu-id="a4b20-129">İstemci, güvenli bir kanal kurarak ve bunların altında genişletilmiş koruma kullanarak hizmetle iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="a4b20-129">The client communicates to the service by establishing a secure channel and using extended protection under the covers.</span></span>
