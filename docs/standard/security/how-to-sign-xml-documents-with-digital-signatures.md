---
title: 'Nasıl yapılır: XML Belgelerini Dijital İmzalarla imzalama'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signatures, XML signing
- System.Security.Cryptography.SignedXml class
- digital signatures, XML signing
- System.Security.Cryptography.RSACryptoServiceProvider class
- XML digital signatures
- XML signing
- signing XML
ms.assetid: 99692ac1-d8c9-42d7-b1bf-2737b01037e4
ms.openlocfilehash: 81fa5e4c503f26dc13758090f845fd8387287084
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277186"
---
# <a name="how-to-sign-xml-documents-with-digital-signatures"></a><span data-ttu-id="b4d64-102">Nasıl yapılır: XML Belgelerini Dijital İmzalarla imzalama</span><span class="sxs-lookup"><span data-stu-id="b4d64-102">How to: Sign XML Documents with Digital Signatures</span></span>
<span data-ttu-id="b4d64-103">Bir <xref:System.Security.Cryptography.Xml> XML belgesini veya BIR XML belgesinin bir kısmını dijital imzaya imzalamak için ad alanındaki sınıfları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4d64-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to sign an XML document or part of an XML document with a digital signature.</span></span>  <span data-ttu-id="b4d64-104">XML dijital imzaları (XMLDSIG), imzalandıktan sonra verilerin değiştirilmediğini doğrulamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4d64-104">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span>  <span data-ttu-id="b4d64-105">XMLDSIG standardı hakkında daha fazla bilgi için, World Wide Web Konsorsiyumu (W3C) önerisi [XML Imzası sözdizimi ve işleme](https://www.w3.org/TR/xmldsig-core/)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="b4d64-105">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).</span></span>  
  
 <span data-ttu-id="b4d64-106">Bu yordamdaki kod örneği, bir XML belgesinin tamamını dijital olarak imzalamayı ve bir <> öğesindeki imzayı belgeye eklemeyi gösterir `Signature` .</span><span class="sxs-lookup"><span data-stu-id="b4d64-106">The code example in this procedure demonstrates how to digitally sign an entire XML document and attach the signature to the document in a <`Signature`> element.</span></span>  <span data-ttu-id="b4d64-107">Örnek, bir RSA imzalama anahtarı oluşturur, anahtarı güvenli bir anahtar kapsayıcısına ekler ve ardından bir XML belgesini dijital olarak imzalamak için anahtarı kullanır.</span><span class="sxs-lookup"><span data-stu-id="b4d64-107">The example creates an RSA signing key, adds the key to a secure key container, and then uses the key to digitally sign an XML document.</span></span>  <span data-ttu-id="b4d64-108">Anahtar daha sonra XML dijital imzasını doğrulamak için alınabilir veya başka bir XML belgesi imzalamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4d64-108">The key can then be retrieved to verify the XML digital signature, or can be used to sign another XML document.</span></span>  
  
 <span data-ttu-id="b4d64-109">Bu yordam kullanılarak oluşturulan bir XML dijital imzasını doğrulama hakkında daha fazla bilgi için bkz. [nasıl yapılır: XML belgelerinin dijital Imzalarını doğrulama](how-to-verify-the-digital-signatures-of-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="b4d64-109">For information about how to verify an XML digital signature that was created using this procedure, see [How to: Verify the Digital Signatures of XML Documents](how-to-verify-the-digital-signatures-of-xml-documents.md).</span></span>  
  
### <a name="to-digitally-sign-an-xml-document"></a><span data-ttu-id="b4d64-110">Bir XML belgesini dijital olarak imzalamak için</span><span class="sxs-lookup"><span data-stu-id="b4d64-110">To digitally sign an XML document</span></span>  
  
1. <span data-ttu-id="b4d64-111">Bir <xref:System.Security.Cryptography.CspParameters> nesne oluşturun ve anahtar kapsayıcısının adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="b4d64-111">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToSignXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#2)]  
  
2. <span data-ttu-id="b4d64-112">Sınıfını kullanarak asimetrik bir anahtar oluşturun <xref:System.Security.Cryptography.RSACryptoServiceProvider> .</span><span class="sxs-lookup"><span data-stu-id="b4d64-112">Generate an asymmetric key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="b4d64-113">Anahtar, nesneyi sınıfının oluşturucusuna geçirdiğinizde anahtar kapsayıcıya otomatik olarak kaydedilir <xref:System.Security.Cryptography.CspParameters> <xref:System.Security.Cryptography.RSACryptoServiceProvider> .</span><span class="sxs-lookup"><span data-stu-id="b4d64-113">The key is automatically saved to the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="b4d64-114">Bu anahtar, XML belgesini imzalamak için kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="b4d64-114">This key will be used to sign the XML document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToSignXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#3)]  
  
3. <span data-ttu-id="b4d64-115"><xref:System.Xml.XmlDocument>Diskten BIR XML dosyası yükleyerek bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b4d64-115">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="b4d64-116"><xref:System.Xml.XmlDocument>Nesne ŞIFRELENECEK XML öğesini içeriyor.</span><span class="sxs-lookup"><span data-stu-id="b4d64-116">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToSignXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#4)]  
  
4. <span data-ttu-id="b4d64-117">Yeni bir <xref:System.Security.Cryptography.Xml.SignedXml> nesne oluşturun ve <xref:System.Xml.XmlDocument> nesneyi buna geçirin.</span><span class="sxs-lookup"><span data-stu-id="b4d64-117">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToSignXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#5)]  
  
5. <span data-ttu-id="b4d64-118">Nesneye imzalama RSA anahtarını ekleyin <xref:System.Security.Cryptography.Xml.SignedXml> .</span><span class="sxs-lookup"><span data-stu-id="b4d64-118">Add the signing RSA key to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToSignXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#6)]  
  
6. <span data-ttu-id="b4d64-119"><xref:System.Security.Cryptography.Xml.Reference>İmzalanacak öğeleri açıklayan bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b4d64-119">Create a <xref:System.Security.Cryptography.Xml.Reference> object that describes what to sign.</span></span>  <span data-ttu-id="b4d64-120">Tüm belgeyi imzalamak için <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> özelliğini olarak ayarlayın `""` .</span><span class="sxs-lookup"><span data-stu-id="b4d64-120">To sign the entire document, set the <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> property to `""`.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToSignXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#7)]  
  
7. <span data-ttu-id="b4d64-121">Nesnesine bir <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> nesne ekleyin <xref:System.Security.Cryptography.Xml.Reference> .</span><span class="sxs-lookup"><span data-stu-id="b4d64-121">Add an <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> object to the <xref:System.Security.Cryptography.Xml.Reference> object.</span></span>  <span data-ttu-id="b4d64-122">Bir dönüşüm, doğrulayıcının XML verilerini imzalayan tarafından aynı şekilde temsil etmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b4d64-122">A transformation allows the verifier to represent the XML data in the identical manner that the signer used.</span></span>  <span data-ttu-id="b4d64-123">XML verileri farklı yollarla temsil edilebilir, bu nedenle doğrulama için bu adım önemlidir.</span><span class="sxs-lookup"><span data-stu-id="b4d64-123">XML data can be represented in different ways, so this step is vital to verification.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToSignXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#8)]  
  
8. <span data-ttu-id="b4d64-124">Nesnesini <xref:System.Security.Cryptography.Xml.Reference> <xref:System.Security.Cryptography.Xml.SignedXml> nesnesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b4d64-124">Add the <xref:System.Security.Cryptography.Xml.Reference> object to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#9)]
     [!code-vb[HowToSignXMLDocumentRSA#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#9)]  
  
9. <span data-ttu-id="b4d64-125">Yöntemi çağırarak imzayı hesaplama <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> .</span><span class="sxs-lookup"><span data-stu-id="b4d64-125">Compute the signature by calling the <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> method.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#10)]
     [!code-vb[HowToSignXMLDocumentRSA#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#10)]  
  
10. <span data-ttu-id="b4d64-126">İmzanın XML temsilini (bir <`Signature`> öğesi) alın ve yeni bir <xref:System.Xml.XmlElement> nesneye kaydedin.</span><span class="sxs-lookup"><span data-stu-id="b4d64-126">Retrieve the XML representation of the signature (a <`Signature`> element) and save it to a new <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#11)]
     [!code-vb[HowToSignXMLDocumentRSA#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#11)]  
  
11. <span data-ttu-id="b4d64-127">Öğesini <xref:System.Xml.XmlDocument> nesnesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b4d64-127">Append the element to the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#12)]
     [!code-vb[HowToSignXMLDocumentRSA#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#12)]  
  
12. <span data-ttu-id="b4d64-128">Belgeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="b4d64-128">Save the document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#13)]
     [!code-vb[HowToSignXMLDocumentRSA#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="b4d64-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="b4d64-129">Example</span></span>  
 <span data-ttu-id="b4d64-130">Bu örnek, adlı bir dosyanın `test.xml` derlenen programla aynı dizinde bulunduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="b4d64-130">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="b4d64-131">Aşağıdaki XML 'i adlı bir dosyaya yerleştirebilir `test.xml` ve bu örnekle birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4d64-131">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToSignXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToSignXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b4d64-132">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b4d64-132">Compiling the Code</span></span>  
  
- <span data-ttu-id="b4d64-133">Bu örneği derlemek için, öğesine bir başvuru eklemeniz gerekir `System.Security.dll` .</span><span class="sxs-lookup"><span data-stu-id="b4d64-133">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="b4d64-134">Şu ad alanlarını ekleyin: <xref:System.Xml> , <xref:System.Security.Cryptography> , ve <xref:System.Security.Cryptography.Xml> .</span><span class="sxs-lookup"><span data-stu-id="b4d64-134">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b4d64-135">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="b4d64-135">.NET Framework Security</span></span>  
 <span data-ttu-id="b4d64-136">Asimetrik anahtar çiftinin özel anahtarını düz metin olarak depolamayın veya aktarmayın.</span><span class="sxs-lookup"><span data-stu-id="b4d64-136">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="b4d64-137">Simetrik ve asimetrik şifreleme anahtarları hakkında daha fazla bilgi için bkz. [şifreleme ve şifre çözme Için anahtarlar oluşturma](generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="b4d64-137">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="b4d64-138">Özel anahtarı hiçbir şekilde doğrudan kaynak kodunuza gömmeyin.</span><span class="sxs-lookup"><span data-stu-id="b4d64-138">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="b4d64-139">Gömülü anahtarlar [ıldadsm. exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) kullanılarak veya derlemeyi Not Defteri gibi bir metin düzenleyicisinde açarak bir derlemeden kolayca okunabilir.</span><span class="sxs-lookup"><span data-stu-id="b4d64-139">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4d64-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4d64-140">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="b4d64-141">Nasıl yapılır: XML Belgelerinin Dijital İmzalarını Doğrulama</span><span class="sxs-lookup"><span data-stu-id="b4d64-141">How to: Verify the Digital Signatures of XML Documents</span></span>](how-to-verify-the-digital-signatures-of-xml-documents.md)
