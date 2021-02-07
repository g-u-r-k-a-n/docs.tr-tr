---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Asimetrik Anahtarlarla XML öğelerinin şifresini çözme'
title: 'Nasıl yapılır: XML Öğelerinin Şifresini Asimetrik Anahtarlarla Çözme'
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.RSA class
- asymmetric keys
- System.Security.Cryptography.EncryptedXml class
- XML encryption
- decryption
ms.assetid: dd5de491-dafe-4b94-966d-99714b2e754a
ms.openlocfilehash: bd3bd142aa5800efa83bc20a4b1af6d5bc61eba2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675578"
---
# <a name="how-to-decrypt-xml-elements-with-asymmetric-keys"></a><span data-ttu-id="5f33e-103">Nasıl yapılır: XML Öğelerinin Şifresini Asimetrik Anahtarlarla Çözme</span><span class="sxs-lookup"><span data-stu-id="5f33e-103">How to: Decrypt XML Elements with Asymmetric Keys</span></span>

<span data-ttu-id="5f33e-104"><xref:System.Security.Cryptography.Xml>BIR XML belgesi içindeki bir öğeyi şifrelemek ve şifrelerini çözmek için ad alanındaki sınıfları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5f33e-104">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to encrypt and decrypt an element within an XML document.</span></span>  <span data-ttu-id="5f33e-105">XML şifrelemesi, kolayca okunan veriler hakkında endişelenmeden şifrelenmiş XML verilerini alışverişi veya depolamayı standart bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="5f33e-105">XML Encryption is a standard way to exchange or store encrypted XML data, without worrying about the data being easily read.</span></span>  <span data-ttu-id="5f33e-106">XML şifreleme standardı hakkında daha fazla bilgi için bkz. World Wide Web Konsorsiyumu (W3C) önerisi [XML Imzası sözdizimi ve işleme](https://www.w3.org/TR/xmldsig-core/).</span><span class="sxs-lookup"><span data-stu-id="5f33e-106">For more information about the XML Encryption standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).</span></span>  

> [!NOTE]
> <span data-ttu-id="5f33e-107">Bu makaledeki kod Windows için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5f33e-107">The code in this article applies to Windows.</span></span>

<span data-ttu-id="5f33e-108">Bu yordamdaki örnek, [nasıl yapılır: XML Öğelerini Asimetrik Anahtarlarla Şifreleme](how-to-encrypt-xml-elements-with-asymmetric-keys.md)bölümünde açıklanan yöntemler kullanılarak ŞIFRELENMIŞ bir XML öğesinin şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="5f33e-108">The example in this procedure decrypts an XML element that was encrypted using the methods described in [How to: Encrypt XML Elements with Asymmetric Keys](how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  <span data-ttu-id="5f33e-109">Bir <`EncryptedData`> öğesi bulur, öğenin şifresini çözer ve sonra öğeyi özgün düz metın XML öğesiyle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="5f33e-109">It finds an <`EncryptedData`> element, decrypts the element, and then replaces the element with the original plaintext XML element.</span></span>  
  
<span data-ttu-id="5f33e-110">Bu örnek, iki anahtar kullanarak bir XML öğesinin şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="5f33e-110">This example decrypts an XML element using two keys.</span></span>  <span data-ttu-id="5f33e-111">Daha önce oluşturulmuş bir RSA özel anahtarını anahtar kapsayıcısından alır ve ardından RSA anahtarını kullanarak `EncryptedKey` <> öğesinin <> öğesinde depolanan bir oturum anahtarının şifresini çözer `EncryptedData` .</span><span class="sxs-lookup"><span data-stu-id="5f33e-111">It retrieves a previously generated RSA private key from a key container, and then uses the RSA key to decrypt a session key stored in the <`EncryptedKey`> element of the <`EncryptedData`> element.</span></span>  <span data-ttu-id="5f33e-112">Daha sonra örnek, XML öğesinin şifresini çözmek için oturum anahtarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5f33e-112">The example then uses the session key to decrypt the XML element.</span></span>  
  
<span data-ttu-id="5f33e-113">Bu örnek, birden fazla uygulamanın şifrelenmiş verileri paylaşması gereken ya da bir uygulamanın, şifrelenen verileri çalıştığı zamanlar arasında kaydetmesi gereken durumlar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="5f33e-113">This example is appropriate for situations where multiple applications have to share encrypted data or where an application has to save encrypted data between the times that it runs.</span></span>  
  
### <a name="to-decrypt-an-xml-element-with-an-asymmetric-key"></a><span data-ttu-id="5f33e-114">Asimetrik anahtarla bir XML öğesinin şifresini çözmek için</span><span class="sxs-lookup"><span data-stu-id="5f33e-114">To decrypt an XML element with an asymmetric key</span></span>  
  
1. <span data-ttu-id="5f33e-115">Bir <xref:System.Security.Cryptography.CspParameters> nesne oluşturun ve anahtar kapsayıcısının adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="5f33e-115">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#2)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#2)]  
  
2. <span data-ttu-id="5f33e-116">Nesneyi kullanarak kapsayıcıdan daha önce oluşturulmuş bir asimetrik anahtar alın <xref:System.Security.Cryptography.RSACryptoServiceProvider> .</span><span class="sxs-lookup"><span data-stu-id="5f33e-116">Retrieve a previously generated asymmetric key from the container using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object.</span></span>  <span data-ttu-id="5f33e-117">Bu anahtar, nesneyi oluşturucuya geçirdiğinizde anahtar kapsayıcısından otomatik olarak alınır <xref:System.Security.Cryptography.CspParameters> <xref:System.Security.Cryptography.RSACryptoServiceProvider> .</span><span class="sxs-lookup"><span data-stu-id="5f33e-117">The key is automatically retrieved from the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the <xref:System.Security.Cryptography.RSACryptoServiceProvider> constructor.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#3)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#3)]  
  
3. <span data-ttu-id="5f33e-118"><xref:System.Security.Cryptography.Xml.EncryptedXml>Belgenin şifresini çözmek için yeni bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5f33e-118">Create a new <xref:System.Security.Cryptography.Xml.EncryptedXml> object to decrypt the document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#5)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#5)]  
  
4. <span data-ttu-id="5f33e-119">RSA anahtarını, şifresi çözülmesi gereken belge içindeki öğeyle ilişkilendirmek için bir anahtar/ad eşlemesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5f33e-119">Add a key/name mapping to associate the RSA key with the element within the document that should be decrypted.</span></span>  <span data-ttu-id="5f33e-120">Belgeyi şifrelediyseniz kullandığınız anahtar için aynı adı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5f33e-120">You must use the same name for the key that you used when you encrypted the document.</span></span>  <span data-ttu-id="5f33e-121">Bu adın, 1. adımda belirtilen anahtar kapsayıcısında anahtarı tanımlamak için kullanılan adından ayrı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5f33e-121">Note that this name is separate from the name used to identify the key in the key container specified in step 1.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#6)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#6)]  
  
5. <span data-ttu-id="5f33e-122"><xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A><> öğesinin şifresini çözmek için yöntemini çağırın `EncryptedData` .</span><span class="sxs-lookup"><span data-stu-id="5f33e-122">Call the <xref:System.Security.Cryptography.Xml.EncryptedXml.DecryptDocument%2A> method to decrypt the <`EncryptedData`> element.</span></span>  <span data-ttu-id="5f33e-123">Bu yöntem, oturum anahtarının şifresini çözmek için RSA anahtarını kullanır ve XML öğesinin şifresini çözmek için oturum anahtarını otomatik olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="5f33e-123">This method uses the RSA key to decrypt the session key and automatically uses the session key to decrypt the XML element.</span></span>  <span data-ttu-id="5f33e-124">Ayrıca, <`EncryptedData`> öğesini özgün düz metin ile otomatik olarak değiştirir.</span><span class="sxs-lookup"><span data-stu-id="5f33e-124">It also automatically replaces the <`EncryptedData`> element with the original plaintext.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#7)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#7)]  
  
6. <span data-ttu-id="5f33e-125">XML belgesini kaydedin.</span><span class="sxs-lookup"><span data-stu-id="5f33e-125">Save the XML document.</span></span>  
  
     [!code-csharp[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#8)]
     [!code-vb[HowToDecryptXMLElementAsymmetric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="5f33e-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="5f33e-126">Example</span></span>

<span data-ttu-id="5f33e-127">Bu örnek, adlı bir dosyanın `test.xml` derlenen programla aynı dizinde bulunduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="5f33e-127">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="5f33e-128">Ayrıca, `test.xml` [nasıl yapılır: XML Öğelerini Asimetrik Anahtarlarla Şifreleme](how-to-encrypt-xml-elements-with-asymmetric-keys.md)bölümünde açıklanan teknikler KULLANıLARAK şifrelenmiş bir XML öğesi içerdiğini varsayar.</span><span class="sxs-lookup"><span data-stu-id="5f33e-128">It also assumes that `test.xml` contains an XML element that was encrypted using the techniques described in [How to: Encrypt XML Elements with Asymmetric Keys](how-to-encrypt-xml-elements-with-asymmetric-keys.md).</span></span>  
  
[!code-csharp[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/cs/sample.cs#1)]
[!code-vb[HowToDecryptXMLElementAsymmetric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToDecryptXMLElementAsymmetric/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5f33e-129">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="5f33e-129">Compiling the Code</span></span>  
  
- <span data-ttu-id="5f33e-130">.NET Framework hedefleyen bir projede, öğesine bir başvuru ekleyin `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="5f33e-130">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="5f33e-131">.NET Core veya .NET 5 ' i hedefleyen bir projede NuGet paketi [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml)' yi yükler.</span><span class="sxs-lookup"><span data-stu-id="5f33e-131">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="5f33e-132">Şu ad alanlarını ekleyin: <xref:System.Xml> , <xref:System.Security.Cryptography> , ve <xref:System.Security.Cryptography.Xml> .</span><span class="sxs-lookup"><span data-stu-id="5f33e-132">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="5f33e-133">.NET güvenliği</span><span class="sxs-lookup"><span data-stu-id="5f33e-133">.NET Security</span></span>  

<span data-ttu-id="5f33e-134">Simetrik bir şifreleme anahtarını düz metin olarak depolamayın veya bir simetrik anahtarı makineler arasında düz metin olarak aktarmayın.</span><span class="sxs-lookup"><span data-stu-id="5f33e-134">Never store a symmetric cryptographic key in plaintext or transfer a symmetric key between machines in plaintext.</span></span>  <span data-ttu-id="5f33e-135">Bunlara ek olarak, asimetrik anahtar çiftinin özel anahtarını düz metin olarak depolamayın veya aktarmayın.</span><span class="sxs-lookup"><span data-stu-id="5f33e-135">Additionally, never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="5f33e-136">Simetrik ve asimetrik şifreleme anahtarları hakkında daha fazla bilgi için bkz. [şifreleme ve şifre çözme Için anahtarlar oluşturma](generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="5f33e-136">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="5f33e-137">Doğrudan kaynak kodunuza bir anahtar gömmeyin.</span><span class="sxs-lookup"><span data-stu-id="5f33e-137">Never embed a key directly into your source code.</span></span>  <span data-ttu-id="5f33e-138">Katıştırılmış anahtarlar [Ildasm.exe (Il ayrıştırma)](../../framework/tools/ildasm-exe-il-disassembler.md) kullanılarak veya derlemeyi Not Defteri gibi bir metin düzenleyicisinde açarak bir derlemeden kolayca okunabilir.</span><span class="sxs-lookup"><span data-stu-id="5f33e-138">Embedded keys can be easily read from an assembly by using [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
 <span data-ttu-id="5f33e-139">Bir şifreleme anahtarı kullanarak işiniz bittiğinde, her baytı sıfıra ayarlayarak veya <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> yönetilen şifreleme sınıfının yöntemini çağırarak bellekten kaldırın.</span><span class="sxs-lookup"><span data-stu-id="5f33e-139">When you are done using a cryptographic key, clear it from memory by setting each byte to zero or by calling the <xref:System.Security.Cryptography.SymmetricAlgorithm.Clear%2A> method of the managed cryptography class.</span></span>  <span data-ttu-id="5f33e-140">Şifreleme anahtarları bazen bir hata ayıklayıcı tarafından bellekten okunabilir veya bellek konumu diske disk belleğine alınmış ise sabit sürücüden okuyabilirler.</span><span class="sxs-lookup"><span data-stu-id="5f33e-140">Cryptographic keys can sometimes be read from memory by a debugger or read from a hard drive if the memory location is paged to disk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f33e-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f33e-141">See also</span></span>

- [<span data-ttu-id="5f33e-142">Şifreleme Modeli</span><span class="sxs-lookup"><span data-stu-id="5f33e-142">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="5f33e-143">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="5f33e-143">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="5f33e-144">Platformlar arası şifreleme</span><span class="sxs-lookup"><span data-stu-id="5f33e-144">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="5f33e-145">Nasıl yapılır: XML Öğelerini Asimetrik Anahtarlarla Şifreleme</span><span class="sxs-lookup"><span data-stu-id="5f33e-145">How to: Encrypt XML Elements with Asymmetric Keys</span></span>](how-to-encrypt-xml-elements-with-asymmetric-keys.md)
- [<span data-ttu-id="5f33e-146">ASP.NET Core veri koruma</span><span class="sxs-lookup"><span data-stu-id="5f33e-146">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
