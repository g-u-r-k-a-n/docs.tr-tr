---
title: 'Nasıl yapılır: X.509 Sertifikalarını WCF için Erişilebilir Hale Getirme'
description: X. 509.440 sertifikasını WCF 'ye erişilebilir hale getirme hakkında bilgi edinin. Uygulama kodu, sertifika deposu adını ve konumunu belirtmelidir. Başka gereksinimler olabilir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
ms.openlocfilehash: 06a6167f0ad352955eb6b764ef8bfdb1394f4ed9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279746"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="db026-105">Nasıl yapılır: X.509 Sertifikalarını WCF için Erişilebilir Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="db026-105">How to: Make X.509 Certificates Accessible to WCF</span></span>

<span data-ttu-id="db026-106">X. 509.440 sertifikasını Windows Communication Foundation (WCF) erişilebilir hale getirmek için, uygulama kodunun sertifika depolama adını ve konumunu belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="db026-106">To make an X.509 certificate accessible to Windows Communication Foundation (WCF), application code must specify the certificate store name and location.</span></span> <span data-ttu-id="db026-107">Bazı durumlarda, işlem kimliğinin X. 509.952 sertifikasıyla ilişkili özel anahtarı içeren dosyaya erişimi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="db026-107">In certain circumstances, the process identity must have access to the file that contains the private key associated with the X.509 certificate.</span></span> <span data-ttu-id="db026-108">Bir sertifika deposundaki bir X. 509.440 sertifikasıyla ilişkili özel anahtarı almak için, WCF 'nin bunu yapması için izni olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="db026-108">To obtain the private key associated with an X.509 certificate in a certificate store, WCF must have permission to do so.</span></span> <span data-ttu-id="db026-109">Varsayılan olarak, yalnızca sahip ve sistem hesabı bir sertifikanın özel anahtarına erişebilir.</span><span class="sxs-lookup"><span data-stu-id="db026-109">By default, only the owner and the System account can access the private key of a certificate.</span></span>  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a><span data-ttu-id="db026-110">X. 509.440 sertifikalarını WCF 'ye erişilebilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="db026-110">To make X.509 certificates accessible to WCF</span></span>  
  
1. <span data-ttu-id="db026-111">WCF 'nin, X. 509.952 sertifikasıyla ilişkili özel anahtarı içeren dosyaya okuma erişiminin çalıştığı hesaba izin verin.</span><span class="sxs-lookup"><span data-stu-id="db026-111">Give the account under which WCF is running read access to the file that contains the private key associated with the X.509 certificate.</span></span>  
  
    1. <span data-ttu-id="db026-112">WCF 'nin X. 509.952 sertifikası için özel anahtara okuma erişimi gerektirip gerektirmediğini belirleme.</span><span class="sxs-lookup"><span data-stu-id="db026-112">Determine whether WCF requires read access to the private key for the X.509 certificate.</span></span>  
  
         <span data-ttu-id="db026-113">Aşağıdaki tabloda, bir X. 509.440 sertifikası kullanılırken özel bir anahtarın kullanılabilir olup olmadığı ayrıntılı olarak verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="db026-113">The following table details whether a private key must be available when using an X.509 certificate.</span></span>  
  
        |<span data-ttu-id="db026-114">X. 509.440 sertifika kullanımı</span><span class="sxs-lookup"><span data-stu-id="db026-114">X.509 certificate use</span></span>|<span data-ttu-id="db026-115">Özel anahtar</span><span class="sxs-lookup"><span data-stu-id="db026-115">Private key</span></span>|  
        |---------------------------|-----------------|  
        |<span data-ttu-id="db026-116">Giden bir SOAP iletisini dijital olarak imzalama.</span><span class="sxs-lookup"><span data-stu-id="db026-116">Digitally signing an outbound SOAP message.</span></span>|<span data-ttu-id="db026-117">Evet</span><span class="sxs-lookup"><span data-stu-id="db026-117">Yes</span></span>|  
        |<span data-ttu-id="db026-118">Gelen SOAP iletisinin imzası doğrulanıyor.</span><span class="sxs-lookup"><span data-stu-id="db026-118">Verifying the signature of an inbound SOAP message.</span></span>|<span data-ttu-id="db026-119">Hayır</span><span class="sxs-lookup"><span data-stu-id="db026-119">No</span></span>|  
        |<span data-ttu-id="db026-120">Giden bir SOAP iletisi şifreleniyor.</span><span class="sxs-lookup"><span data-stu-id="db026-120">Encrypting an outbound SOAP message.</span></span>|<span data-ttu-id="db026-121">Hayır</span><span class="sxs-lookup"><span data-stu-id="db026-121">No</span></span>|  
        |<span data-ttu-id="db026-122">Gelen SOAP iletisinin şifresini çözme.</span><span class="sxs-lookup"><span data-stu-id="db026-122">Decrypting an inbound SOAP message.</span></span>|<span data-ttu-id="db026-123">Evet</span><span class="sxs-lookup"><span data-stu-id="db026-123">Yes</span></span>|  
  
    2. <span data-ttu-id="db026-124">Sertifika depolama konumunu ve sertifikanın depolandığı adı saptayın.</span><span class="sxs-lookup"><span data-stu-id="db026-124">Determine the certificate store location and name in which the certificate is stored.</span></span>  
  
         <span data-ttu-id="db026-125">Sertifikanın depolandığı sertifika depolama alanı, uygulama kodunda ya da yapılandırmada belirtilir.</span><span class="sxs-lookup"><span data-stu-id="db026-125">The certificate store in which the certificate is stored is specified either in application code or in configuration.</span></span> <span data-ttu-id="db026-126">Örneğin, aşağıdaki örnek, sertifikanın `CurrentUser` adlı sertifika deposunda bulunduğunu belirtir `My` .</span><span class="sxs-lookup"><span data-stu-id="db026-126">For example, the following example specifies that the certificate is located in the `CurrentUser` certificate store named `My`.</span></span>  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. <span data-ttu-id="db026-127">Sertifika için özel anahtarın, [FindPrivateKey](../samples/findprivatekey.md) aracını kullanarak bilgisayarda bulunduğunu belirleme.</span><span class="sxs-lookup"><span data-stu-id="db026-127">Determine where the private key for the certificate is located on the computer by using the [FindPrivateKey](../samples/findprivatekey.md) tool.</span></span>  
  
         <span data-ttu-id="db026-128">[FindPrivateKey](../samples/findprivatekey.md) aracı sertifika depolama adı, sertifika depolama konumu ve sertifikayı benzersiz olarak tanımlayan bir şeyi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="db026-128">The [FindPrivateKey](../samples/findprivatekey.md) tool requires the certificate store name, certificate store location, and something that uniquely identifies the certificate.</span></span> <span data-ttu-id="db026-129">Araç, sertifikanın konu adını ya da parmak izini benzersiz bir tanımlayıcı olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="db026-129">The tool accepts either the certificate's subject name or its thumbprint as a unique identifier.</span></span> <span data-ttu-id="db026-130">Bir sertifikanın parmak izini belirleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir sertifikanın parmak Izini alma](how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="db026-130">For more information about how to determine the thumbprint for a certificate, see [How to: Retrieve the Thumbprint of a Certificate](how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
         <span data-ttu-id="db026-131">Aşağıdaki kod örneği, [FindPrivateKey](../samples/findprivatekey.md) `My` `CurrentUser` bir parmak izine sahip içindeki depodaki bir sertifika için özel anahtar konumunu tespit etmek üzere FindPrivateKey aracını kullanır `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d` .</span><span class="sxs-lookup"><span data-stu-id="db026-131">The following code example uses the [FindPrivateKey](../samples/findprivatekey.md) tool to determine the location of the private key for a certificate in the `My` store in `CurrentUser` with a thumbprint of `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.</span></span>  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. <span data-ttu-id="db026-132">WCF 'nin altında çalıştığı hesabı belirleme.</span><span class="sxs-lookup"><span data-stu-id="db026-132">Determine the account that WCF is running under.</span></span>  
  
         <span data-ttu-id="db026-133">Aşağıdaki tabloda, belirli bir senaryo için WCF 'nin çalıştığı hesabın ayrıntıları verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="db026-133">The following table details the account under which WCF is running for a given scenario.</span></span>  
  
        |<span data-ttu-id="db026-134">Senaryo</span><span class="sxs-lookup"><span data-stu-id="db026-134">Scenario</span></span>|<span data-ttu-id="db026-135">İşlem kimliği</span><span class="sxs-lookup"><span data-stu-id="db026-135">Process identity</span></span>|  
        |--------------|----------------------|  
        |<span data-ttu-id="db026-136">İstemci (konsol veya WinForms uygulaması).</span><span class="sxs-lookup"><span data-stu-id="db026-136">Client (console or WinForms application).</span></span>|<span data-ttu-id="db026-137">Şu anda oturum açmış olan kullanıcı.</span><span class="sxs-lookup"><span data-stu-id="db026-137">Currently logged in user.</span></span>|  
        |<span data-ttu-id="db026-138">Kendi kendine barındırılan hizmet.</span><span class="sxs-lookup"><span data-stu-id="db026-138">Service that is self-hosted.</span></span>|<span data-ttu-id="db026-139">Şu anda oturum açmış olan kullanıcı.</span><span class="sxs-lookup"><span data-stu-id="db026-139">Currently logged in user.</span></span>|  
        |<span data-ttu-id="db026-140">IIS 6,0 (Windows Server 2003) veya IIS 7,0 (Windows Vista) içinde barındırılan hizmet.</span><span class="sxs-lookup"><span data-stu-id="db026-140">Service that is hosted in IIS 6.0 (Windows Server 2003) or IIS 7.0 (Windows Vista).</span></span>|<span data-ttu-id="db026-141">AĞ HIZMETI</span><span class="sxs-lookup"><span data-stu-id="db026-141">NETWORK SERVICE</span></span>|  
        |<span data-ttu-id="db026-142">IIS 5. X (Windows XP) içinde barındırılan hizmet.</span><span class="sxs-lookup"><span data-stu-id="db026-142">Service that is hosted in IIS 5.X (Windows XP).</span></span>|<span data-ttu-id="db026-143">`<processModel>`Machine.config dosyasındaki öğe tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="db026-143">Controlled by the `<processModel>` element in the Machine.config file.</span></span> <span data-ttu-id="db026-144">Varsayılan hesap ASPNET ' dir.</span><span class="sxs-lookup"><span data-stu-id="db026-144">The default account is ASPNET.</span></span>|  
  
    5. <span data-ttu-id="db026-145">icacls.exe gibi bir araç kullanarak WCF 'nin altında çalıştığı hesaba özel anahtarı içeren dosyaya okuma erişimi verin.</span><span class="sxs-lookup"><span data-stu-id="db026-145">Grant read access to the file that contains the private key to the account that WCF is running under, using a tool such as icacls.exe.</span></span>  
  
         <span data-ttu-id="db026-146">Aşağıdaki kod örneği, ağ HIZMETI hesabına dosyaya okuma (: R) erişimi vermek için belirtilen dosya için isteğe bağlı erişim denetimi listesini (DACL) düzenler.</span><span class="sxs-lookup"><span data-stu-id="db026-146">The following code example edits the discretionary access control list (DACL) for the specified file to grant the NETWORK SERVICE account read (:R) access to the file.</span></span>  
  
        ```console
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="db026-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db026-147">See also</span></span>

- [<span data-ttu-id="db026-148">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="db026-148">FindPrivateKey</span></span>](../samples/findprivatekey.md)
- [<span data-ttu-id="db026-149">Nasıl yapılır: Bir Sertifikanın Parmak İzini Alma</span><span class="sxs-lookup"><span data-stu-id="db026-149">How to: Retrieve the Thumbprint of a Certificate</span></span>](how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [<span data-ttu-id="db026-150">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="db026-150">Working with Certificates</span></span>](working-with-certificates.md)
