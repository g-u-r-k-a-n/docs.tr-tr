---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: XML belgelerinin dijital Imzalarını doğrulama'
title: 'Nasıl yapılır: XML Belgelerinin Dijital İmzalarını Doğrulama'
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.SignedXml class
- signatures, cryptographic
- System.Security.Cryptography.RSA class
- verifying signatures
- checking signatures
- XML digital signatures
- digital signatures, verifying
ms.assetid: a4d5ceb1-b9f5-47e8-9e4a-a2b39110002f
ms.openlocfilehash: 37ef72c6bedf73ced7c2dde4335034f603190946
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685042"
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a><span data-ttu-id="771be-103">Nasıl yapılır: XML Belgelerinin Dijital İmzalarını Doğrulama</span><span class="sxs-lookup"><span data-stu-id="771be-103">How to: Verify the Digital Signatures of XML Documents</span></span>

<span data-ttu-id="771be-104"><xref:System.Security.Cryptography.Xml>Dijital imzayla IMZALANMıŞ XML verilerini doğrulamak için ad alanındaki sınıfları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="771be-104">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to verify XML data signed with a digital signature.</span></span> <span data-ttu-id="771be-105">XML dijital imzaları (XMLDSIG), imzalandıktan sonra verilerin değiştirilmediğini doğrulamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="771be-105">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span> <span data-ttu-id="771be-106">XMLDSIG standardı hakkında daha fazla bilgi için, bkz. World Wide Web Konsorsiyumu (W3C) belirtimi <https://www.w3.org/TR/xmldsig-core/> .</span><span class="sxs-lookup"><span data-stu-id="771be-106">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) specification at <https://www.w3.org/TR/xmldsig-core/>.</span></span>
  
> [!NOTE]
> <span data-ttu-id="771be-107">Bu makaledeki kod Windows için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="771be-107">The code in this article applies to Windows.</span></span>

<span data-ttu-id="771be-108">Bu yordamdaki kod örneği, bir <> öğesinde bulunan bir XML dijital imzasının nasıl doğrulandığını gösterir `Signature` .</span><span class="sxs-lookup"><span data-stu-id="771be-108">The code example in this procedure demonstrates how to verify an XML digital signature contained in a <`Signature`> element.</span></span>  <span data-ttu-id="771be-109">Örnek, anahtar kapsayıcısından bir RSA ortak anahtarı alır ve ardından imzayı doğrulamak için anahtarı kullanır.</span><span class="sxs-lookup"><span data-stu-id="771be-109">The example retrieves an RSA public key from a key container and then uses the key to verify the signature.</span></span>  
  
<span data-ttu-id="771be-110">Bu tekniği kullanarak doğrulanabilen dijital imza oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: XML belgelerini dijital Imzalarla imzalama](how-to-sign-xml-documents-with-digital-signatures.md).</span><span class="sxs-lookup"><span data-stu-id="771be-110">For information about how create a digital signature that can be verified using this technique, see [How to: Sign XML Documents with Digital Signatures](how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a><span data-ttu-id="771be-111">Bir XML belgesinin dijital imzasını doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="771be-111">To verify the digital signature of an XML document</span></span>  
  
1. <span data-ttu-id="771be-112">Belgeyi doğrulamak için, imzalama için kullanılan asimetrik anahtarı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="771be-112">To verify the document, you must use the same asymmetric key that was used for signing.</span></span>  <span data-ttu-id="771be-113">Bir <xref:System.Security.Cryptography.CspParameters> nesne oluşturun ve imzalanmak üzere kullanılan anahtar kapsayıcısının adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="771be-113">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container that was used for signing.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2. <span data-ttu-id="771be-114">Sınıfını kullanarak ortak anahtarı alın <xref:System.Security.Cryptography.RSACryptoServiceProvider> .</span><span class="sxs-lookup"><span data-stu-id="771be-114">Retrieve the public key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="771be-115">Bu anahtar, nesneyi sınıfının oluşturucusuna geçirdiğinizde anahtar kapsayıcısından ada göre otomatik olarak yüklenir <xref:System.Security.Cryptography.CspParameters> <xref:System.Security.Cryptography.RSACryptoServiceProvider> .</span><span class="sxs-lookup"><span data-stu-id="771be-115">The key is automatically loaded from the key container by name when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3. <span data-ttu-id="771be-116"><xref:System.Xml.XmlDocument>Diskten BIR XML dosyası yükleyerek bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="771be-116">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="771be-117"><xref:System.Xml.XmlDocument>Nesne doğrulanacak olan IMZALANMıŞ XML belgesini içeriyor.</span><span class="sxs-lookup"><span data-stu-id="771be-117">The <xref:System.Xml.XmlDocument> object contains the signed XML document to verify.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4. <span data-ttu-id="771be-118">Yeni bir <xref:System.Security.Cryptography.Xml.SignedXml> nesne oluşturun ve <xref:System.Xml.XmlDocument> nesneyi buna geçirin.</span><span class="sxs-lookup"><span data-stu-id="771be-118">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5. <span data-ttu-id="771be-119"><`signature`> öğesini bulun ve yeni bir nesne oluşturun <xref:System.Xml.XmlNodeList> .</span><span class="sxs-lookup"><span data-stu-id="771be-119">Find the <`signature`> element and create a new <xref:System.Xml.XmlNodeList> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6. <span data-ttu-id="771be-120">İlk <`signature`> ÖĞESININ XML 'sini <xref:System.Security.Cryptography.Xml.SignedXml> nesnesine yükleyin.</span><span class="sxs-lookup"><span data-stu-id="771be-120">Load the XML of the first <`signature`> element into the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7. <span data-ttu-id="771be-121"><xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A>Yöntemi ve RSA ortak anahtarını kullanarak imzayı denetleyin.</span><span class="sxs-lookup"><span data-stu-id="771be-121">Check the signature using the <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> method and the RSA public key.</span></span>  <span data-ttu-id="771be-122">Bu yöntem, başarılı veya başarısız olduğunu belirten bir Boole değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="771be-122">This method returns a Boolean value that indicates success or failure.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="771be-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="771be-123">Example</span></span>

<span data-ttu-id="771be-124">Bu örnek, adlı bir dosyanın `"test.xml"` derlenen programla aynı dizinde bulunduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="771be-124">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="771be-125">Bu `"test.xml"` Dosya, [nasıl yapılır: XML belgelerini dijital Imzalarla imzalama](how-to-sign-xml-documents-with-digital-signatures.md)bölümünde açıklanan teknikler kullanılarak imzalanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="771be-125">The `"test.xml"` file must be signed using the techniques described in [How to: Sign XML Documents with Digital Signatures](how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
[!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
[!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="771be-126">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="771be-126">Compiling the Code</span></span>  
  
- <span data-ttu-id="771be-127">.NET Framework hedefleyen bir projede, öğesine bir başvuru ekleyin `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="771be-127">In a project that targets .NET Framework, include a reference to `System.Security.dll`.</span></span>

- <span data-ttu-id="771be-128">.NET Core veya .NET 5 ' i hedefleyen bir projede NuGet paketi [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml)' yi yükler.</span><span class="sxs-lookup"><span data-stu-id="771be-128">In a project that targets .NET Core or .NET 5, install NuGet package [System.Security.Cryptography.Xml](https://www.nuget.org/packages/System.Security.Cryptography.Xml).</span></span>
  
- <span data-ttu-id="771be-129">Şu ad alanlarını ekleyin: <xref:System.Xml> , <xref:System.Security.Cryptography> , ve <xref:System.Security.Cryptography.Xml> .</span><span class="sxs-lookup"><span data-stu-id="771be-129">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="771be-130">.NET güvenliği</span><span class="sxs-lookup"><span data-stu-id="771be-130">.NET Security</span></span>

<span data-ttu-id="771be-131">Asimetrik anahtar çiftinin özel anahtarını düz metin olarak depolamayın veya aktarmayın.</span><span class="sxs-lookup"><span data-stu-id="771be-131">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="771be-132">Simetrik ve asimetrik şifreleme anahtarları hakkında daha fazla bilgi için bkz. [şifreleme ve şifre çözme Için anahtarlar oluşturma](generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="771be-132">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
<span data-ttu-id="771be-133">Özel anahtarı hiçbir şekilde doğrudan kaynak kodunuza gömmeyin.</span><span class="sxs-lookup"><span data-stu-id="771be-133">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="771be-134">Katıştırılmış anahtarlar [Ildasm.exe (Il ayrıştırma)](../../framework/tools/ildasm-exe-il-disassembler.md) kullanılarak veya derlemeyi Not Defteri gibi bir metin düzenleyicisinde açarak bir derlemeden kolayca okunabilir.</span><span class="sxs-lookup"><span data-stu-id="771be-134">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="771be-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="771be-135">See also</span></span>

- [<span data-ttu-id="771be-136">Şifreleme Modeli</span><span class="sxs-lookup"><span data-stu-id="771be-136">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="771be-137">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="771be-137">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="771be-138">Platformlar arası şifreleme</span><span class="sxs-lookup"><span data-stu-id="771be-138">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="771be-139">Nasıl yapılır: XML Belgelerini Dijital İmzalarla imzalama</span><span class="sxs-lookup"><span data-stu-id="771be-139">How to: Sign XML Documents with Digital Signatures</span></span>](how-to-sign-xml-documents-with-digital-signatures.md)
- [<span data-ttu-id="771be-140">ASP.NET Core veri koruma</span><span class="sxs-lookup"><span data-stu-id="771be-140">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
