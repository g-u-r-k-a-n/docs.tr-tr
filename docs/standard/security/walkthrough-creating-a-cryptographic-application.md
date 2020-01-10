---
title: 'İzlenecek Yol: Şifreleme Uygulaması Oluşturma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [NET Framework], example
- cryptography [NET Framework], cryptographic application example
- cryptography [NET Framework], application example
ms.assetid: abf48c11-1e72-431d-9562-39cf23e1a8ff
ms.openlocfilehash: 6e2d9b8bebdfd2ea5d5507cc73d444fa8bf785fb
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705840"
---
# <a name="walkthrough-creating-a-cryptographic-application"></a><span data-ttu-id="abf26-102">İzlenecek Yol: Şifreleme Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="abf26-102">Walkthrough: Creating a Cryptographic Application</span></span>
<span data-ttu-id="abf26-103">Bu izlenecek yol, içerik şifrelemesini ve şifresini çözmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="abf26-103">This walkthrough demonstrates how to encrypt and decrypt content.</span></span> <span data-ttu-id="abf26-104">Kod örnekleri, Windows Forms bir uygulama için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="abf26-104">The code examples are designed for a Windows Forms application.</span></span> <span data-ttu-id="abf26-105">Bu uygulama, akıllı kartlar kullanma gibi gerçek dünyada senaryolar göstermez.</span><span class="sxs-lookup"><span data-stu-id="abf26-105">This application does not demonstrate real world scenarios, such as using smart cards.</span></span> <span data-ttu-id="abf26-106">Bunun yerine, şifreleme ve şifre çözme temellerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="abf26-106">Instead, it demonstrates the fundamentals of encryption and decryption.</span></span>  
  
 <span data-ttu-id="abf26-107">Bu izlenecek yol, şifreleme için aşağıdaki yönergeleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="abf26-107">This walkthrough uses the following guidelines for encryption:</span></span>  
  
- <span data-ttu-id="abf26-108">Otomatik olarak oluşturulan <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> ve <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>kullanarak verileri şifrelemek ve şifrelerini çözmek için <xref:System.Security.Cryptography.RijndaelManaged> sınıfını bir simetrik algoritma kullanın.</span><span class="sxs-lookup"><span data-stu-id="abf26-108">Use the <xref:System.Security.Cryptography.RijndaelManaged> class, a symmetric algorithm, to encrypt and decrypt data by using its automatically generated <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> and <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.</span></span>  
  
- <span data-ttu-id="abf26-109"><xref:System.Security.Cryptography.RijndaelManaged>tarafından şifrelenen verilerle anahtarı şifrelemek ve şifresini çözmek için <xref:System.Security.Cryptography.RSACryptoServiceProvider>asimetrik bir algoritma kullanın.</span><span class="sxs-lookup"><span data-stu-id="abf26-109">Use the <xref:System.Security.Cryptography.RSACryptoServiceProvider>, an asymmetric algorithm, to encrypt and decrypt the key to the data encrypted by <xref:System.Security.Cryptography.RijndaelManaged>.</span></span> <span data-ttu-id="abf26-110">Asimetrik algoritmalar, anahtar gibi daha küçük miktarlarda veri için en iyi şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="abf26-110">Asymmetric algorithms are best used for smaller amounts of data, such as a key.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="abf26-111">Diğer kişilerle şifrelenmiş içerik alışverişi yerine bilgisayarınızdaki verileri korumak istiyorsanız, <xref:System.Security.Cryptography.ProtectedData> veya <xref:System.Security.Cryptography.ProtectedMemory> sınıflarını kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="abf26-111">If you want to protect data on your computer instead of exchanging encrypted content with other people, consider using the <xref:System.Security.Cryptography.ProtectedData> or <xref:System.Security.Cryptography.ProtectedMemory> classes.</span></span>  
  
 <span data-ttu-id="abf26-112">Aşağıdaki tabloda bu konudaki şifreleme görevleri özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="abf26-112">The following table summarizes the cryptographic tasks in this topic.</span></span>  
  
|<span data-ttu-id="abf26-113">Görev</span><span class="sxs-lookup"><span data-stu-id="abf26-113">Task</span></span>|<span data-ttu-id="abf26-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="abf26-114">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="abf26-115">Windows Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="abf26-115">Creating a Windows Forms application</span></span>|<span data-ttu-id="abf26-116">Uygulamayı çalıştırmak için gereken denetimleri listeler.</span><span class="sxs-lookup"><span data-stu-id="abf26-116">Lists the controls that are required to run the application.</span></span>|  
|<span data-ttu-id="abf26-117">Genel nesneleri bildirme</span><span class="sxs-lookup"><span data-stu-id="abf26-117">Declaring global objects</span></span>|<span data-ttu-id="abf26-118">Dize yol değişkenlerini, <xref:System.Security.Cryptography.CspParameters>ve <xref:System.Security.Cryptography.RSACryptoServiceProvider> <xref:System.Windows.Forms.Form> sınıfının genel bağlamına sahip olacak şekilde bildirir.</span><span class="sxs-lookup"><span data-stu-id="abf26-118">Declares string path variables, the <xref:System.Security.Cryptography.CspParameters>, and the <xref:System.Security.Cryptography.RSACryptoServiceProvider> to have global context of the <xref:System.Windows.Forms.Form> class.</span></span>|  
|<span data-ttu-id="abf26-119">Asimetrik anahtar oluşturma</span><span class="sxs-lookup"><span data-stu-id="abf26-119">Creating an asymmetric key</span></span>|<span data-ttu-id="abf26-120">Asimetrik ortak ve özel anahtar değer çifti oluşturur ve bir anahtar kapsayıcısı adı atar.</span><span class="sxs-lookup"><span data-stu-id="abf26-120">Creates an asymmetric public and private key value pair and assigns it a key container name.</span></span>|  
|<span data-ttu-id="abf26-121">Dosya şifreleme</span><span class="sxs-lookup"><span data-stu-id="abf26-121">Encrypting a file</span></span>|<span data-ttu-id="abf26-122">Şifreleme için bir dosya seçmek üzere bir iletişim kutusu görüntüler ve dosyayı şifreler.</span><span class="sxs-lookup"><span data-stu-id="abf26-122">Displays a dialog box to select a file for encryption and encrypts the file.</span></span>|  
|<span data-ttu-id="abf26-123">Dosya şifresini çözme</span><span class="sxs-lookup"><span data-stu-id="abf26-123">Decrypting a file</span></span>|<span data-ttu-id="abf26-124">Şifre çözme için şifrelenmiş bir dosya seçmek ve dosyanın şifresini çözmek için bir iletişim kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="abf26-124">Displays a dialog box to select an encrypted file for decryption and decrypts the file.</span></span>|  
|<span data-ttu-id="abf26-125">Özel anahtar alma</span><span class="sxs-lookup"><span data-stu-id="abf26-125">Getting a private key</span></span>|<span data-ttu-id="abf26-126">Anahtar kapsayıcısı adını kullanarak tam anahtar çiftini alır.</span><span class="sxs-lookup"><span data-stu-id="abf26-126">Gets the full key pair using the key container name.</span></span>|  
|<span data-ttu-id="abf26-127">Ortak anahtar dışarı aktarılıyor</span><span class="sxs-lookup"><span data-stu-id="abf26-127">Exporting a public key</span></span>|<span data-ttu-id="abf26-128">Anahtarı yalnızca ortak parametrelere sahip bir XML dosyasına kaydeder.</span><span class="sxs-lookup"><span data-stu-id="abf26-128">Saves the key to an XML file with only public parameters.</span></span>|  
|<span data-ttu-id="abf26-129">Ortak anahtar içeri aktarılıyor</span><span class="sxs-lookup"><span data-stu-id="abf26-129">Importing a public key</span></span>|<span data-ttu-id="abf26-130">Anahtarı bir XML dosyasından anahtar kapsayıcısına yükler.</span><span class="sxs-lookup"><span data-stu-id="abf26-130">Loads the key from an XML file into the key container.</span></span>|  
|<span data-ttu-id="abf26-131">Uygulamayı test etme</span><span class="sxs-lookup"><span data-stu-id="abf26-131">Testing the application</span></span>|<span data-ttu-id="abf26-132">Bu uygulamayı test etmek için yordamları listeler.</span><span class="sxs-lookup"><span data-stu-id="abf26-132">Lists procedures for testing this application.</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="abf26-133">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="abf26-133">Prerequisites</span></span>  
 <span data-ttu-id="abf26-134">Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="abf26-134">You need the following components to complete this walkthrough:</span></span>  
  
- <span data-ttu-id="abf26-135"><xref:System.IO> ve <xref:System.Security.Cryptography> ad alanlarına başvurular.</span><span class="sxs-lookup"><span data-stu-id="abf26-135">References to the <xref:System.IO> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
## <a name="creating-a-windows-forms-application"></a><span data-ttu-id="abf26-136">Windows Forms uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="abf26-136">Creating a Windows Forms Application</span></span>  
 <span data-ttu-id="abf26-137">Bu izlenecek yolda bulunan kod örneklerinin çoğu düğme denetimleri için olay işleyicileri olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="abf26-137">Most of the code examples in this walkthrough are designed to be event handlers for button controls.</span></span> <span data-ttu-id="abf26-138">Aşağıdaki tabloda, örnek uygulama için gereken denetimler ve kod örnekleriyle eşleşmesi için gereken adlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="abf26-138">The following table lists the controls required for the sample application and their required names to match the code examples.</span></span>  
  
|<span data-ttu-id="abf26-139">Denetim</span><span class="sxs-lookup"><span data-stu-id="abf26-139">Control</span></span>|<span data-ttu-id="abf26-140">Name</span><span class="sxs-lookup"><span data-stu-id="abf26-140">Name</span></span>|<span data-ttu-id="abf26-141">Metin özelliği (gerektiğinde)</span><span class="sxs-lookup"><span data-stu-id="abf26-141">Text property (as needed)</span></span>|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|<span data-ttu-id="abf26-142">Dosyayı şifreleyin</span><span class="sxs-lookup"><span data-stu-id="abf26-142">Encrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|<span data-ttu-id="abf26-143">Dosya şifresini çöz</span><span class="sxs-lookup"><span data-stu-id="abf26-143">Decrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|<span data-ttu-id="abf26-144">Anahtar oluştur</span><span class="sxs-lookup"><span data-stu-id="abf26-144">Create Keys</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|<span data-ttu-id="abf26-145">Ortak anahtarı dışarı aktar</span><span class="sxs-lookup"><span data-stu-id="abf26-145">Export Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|<span data-ttu-id="abf26-146">Ortak anahtarı içeri aktar</span><span class="sxs-lookup"><span data-stu-id="abf26-146">Import Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|<span data-ttu-id="abf26-147">Özel anahtar al</span><span class="sxs-lookup"><span data-stu-id="abf26-147">Get Private Key</span></span>|  
|<xref:System.Windows.Forms.Label>|`label1`|<span data-ttu-id="abf26-148">Anahtar ayarlanmadı</span><span class="sxs-lookup"><span data-stu-id="abf26-148">Key not set</span></span>|  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 <span data-ttu-id="abf26-149">Olay işleyicilerini oluşturmak için Visual Studio tasarımcısında düğmelere çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="abf26-149">Double-click the buttons in the  Visual Studio designer to create their event handlers.</span></span>  
  
## <a name="declaring-global-objects"></a><span data-ttu-id="abf26-150">Genel nesneleri bildirme</span><span class="sxs-lookup"><span data-stu-id="abf26-150">Declaring Global Objects</span></span>  
 <span data-ttu-id="abf26-151">Form yapıcısına aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="abf26-151">Add the following code to the Form's constructor.</span></span> <span data-ttu-id="abf26-152">Ortamınız ve tercihleriniz için dize değişkenlerini düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="abf26-152">Edit the string variables for your environment and preferences.</span></span>  
  
 [!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
 [!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a><span data-ttu-id="abf26-153">Asimetrik anahtar oluşturma</span><span class="sxs-lookup"><span data-stu-id="abf26-153">Creating an Asymmetric Key</span></span>  
 <span data-ttu-id="abf26-154">Bu görev <xref:System.Security.Cryptography.RijndaelManaged> anahtarını şifreleyen ve şifresini çözdüğü bir asimetrik anahtar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="abf26-154">This task creates an asymmetric key that encrypts and decrypts the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span> <span data-ttu-id="abf26-155">Bu anahtar, içeriği şifrelemek için kullanıldı ve etiket denetimindeki anahtar kapsayıcısı adını görüntülüyor.</span><span class="sxs-lookup"><span data-stu-id="abf26-155">This key was used to encrypt the content and it displays the key container name on the label control.</span></span>  
  
 <span data-ttu-id="abf26-156">Aşağıdaki kodu `Create Keys` düğmesi için `Click` olay işleyicisi olarak ekleyin (`buttonCreateAsmKeys_Click`).</span><span class="sxs-lookup"><span data-stu-id="abf26-156">Add the following code as the `Click` event handler for the `Create Keys` button (`buttonCreateAsmKeys_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a><span data-ttu-id="abf26-157">Dosya şifreleme</span><span class="sxs-lookup"><span data-stu-id="abf26-157">Encrypting a File</span></span>  
 <span data-ttu-id="abf26-158">Bu görev iki yöntem içerir: `Encrypt File` düğmenin (`buttonEncryptFile_Click`) ve `EncryptFile` yönteminin olay işleyicisi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="abf26-158">This task involves two methods: the event handler method for the `Encrypt File` button (`buttonEncryptFile_Click`) and the `EncryptFile` method.</span></span> <span data-ttu-id="abf26-159">İlk yöntem, bir dosya seçmek için bir iletişim kutusu görüntüler ve dosya adını şifrelemeyi gerçekleştiren ikinci yönteme geçirir.</span><span class="sxs-lookup"><span data-stu-id="abf26-159">The first method displays a dialog box for selecting a file and passes the file name to the second method, which performs the encryption.</span></span>  
  
 <span data-ttu-id="abf26-160">Şifrelenmiş içerik, anahtar ve IV, şifreleme paketi olarak adlandırılan tek bir <xref:System.IO.FileStream>kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="abf26-160">The encrypted content, key, and IV are all saved to one <xref:System.IO.FileStream>, which is referred to as the encryption package.</span></span>  
  
 <span data-ttu-id="abf26-161">`EncryptFile` yöntemi aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="abf26-161">The `EncryptFile` method does the following:</span></span>  
  
1. <span data-ttu-id="abf26-162">İçeriği şifrelemek için <xref:System.Security.Cryptography.RijndaelManaged> simetrik bir algoritma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="abf26-162">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to encrypt the content.</span></span>  
  
2. <span data-ttu-id="abf26-163"><xref:System.Security.Cryptography.RijndaelManaged> anahtarını şifrelemek için bir <xref:System.Security.Cryptography.RSACryptoServiceProvider> nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="abf26-163">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to encrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
3. <span data-ttu-id="abf26-164">, Kaynak dosyanın <xref:System.IO.FileStream> bayt blokları içinde, şifrelenen dosya için hedef <xref:System.IO.FileStream> nesnesine okumak ve şifrelemek için bir <xref:System.Security.Cryptography.CryptoStream> nesnesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="abf26-164">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and encrypt the <xref:System.IO.FileStream> of the source file, in blocks of bytes, into a destination <xref:System.IO.FileStream> object for the encrypted file.</span></span>  
  
4. <span data-ttu-id="abf26-165">Şifrelenmiş anahtarın ve IV 'nin uzunluklarının sayısını belirler ve uzunluk değerlerinin bayt dizilerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="abf26-165">Determines the lengths of the encrypted key and IV, and creates byte arrays of their length values.</span></span>  
  
5. <span data-ttu-id="abf26-166">Anahtarı, IV ve bunların uzunluk değerlerini şifreli pakete yazar.</span><span class="sxs-lookup"><span data-stu-id="abf26-166">Writes the Key, IV, and their length values to the encrypted package.</span></span>  
  
 <span data-ttu-id="abf26-167">Şifreleme paketi aşağıdaki biçimi kullanır:</span><span class="sxs-lookup"><span data-stu-id="abf26-167">The encryption package uses the following format:</span></span>  
  
- <span data-ttu-id="abf26-168">Anahtar uzunluğu, bayt 0-3</span><span class="sxs-lookup"><span data-stu-id="abf26-168">Key length, bytes 0 - 3</span></span>  
  
- <span data-ttu-id="abf26-169">IV uzunluğu, bayt 4-7</span><span class="sxs-lookup"><span data-stu-id="abf26-169">IV length, bytes 4 - 7</span></span>  
  
- <span data-ttu-id="abf26-170">Şifrelenmiş anahtar</span><span class="sxs-lookup"><span data-stu-id="abf26-170">Encrypted key</span></span>  
  
- <span data-ttu-id="abf26-171">IV</span><span class="sxs-lookup"><span data-stu-id="abf26-171">IV</span></span>  
  
- <span data-ttu-id="abf26-172">Şifre metni</span><span class="sxs-lookup"><span data-stu-id="abf26-172">Cipher text</span></span>  
  
 <span data-ttu-id="abf26-173">Daha sonra dosyanın şifresini çözmek için kullanılabilecek, şifreleme paketinin tüm bölümlerinin başlangıç noktalarını ve uzunluklarının belirlenmesi için anahtar ve IV uzunluğunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abf26-173">You can use the lengths of the key and IV to determine the starting points and lengths of all parts of the encryption package, which can then be used to decrypt the file.</span></span>  
  
 <span data-ttu-id="abf26-174">Aşağıdaki kodu `Encrypt File` düğmesi için `Click` olay işleyicisi olarak ekleyin (`buttonEncryptFile_Click`).</span><span class="sxs-lookup"><span data-stu-id="abf26-174">Add the following code as the `Click` event handler for the `Encrypt File` button (`buttonEncryptFile_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 <span data-ttu-id="abf26-175">Aşağıdaki `EncryptFile` yöntemini forma ekleyin.</span><span class="sxs-lookup"><span data-stu-id="abf26-175">Add the following `EncryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a><span data-ttu-id="abf26-176">Dosya şifresini çözme</span><span class="sxs-lookup"><span data-stu-id="abf26-176">Decrypting a File</span></span>  
 <span data-ttu-id="abf26-177">Bu görev, `Decrypt File` düğmesi (`buttonDecryptFile_Click`) ve `DecryptFile` yöntemi için olay işleyicisi yöntemi olmak üzere iki yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="abf26-177">This task involves two methods, the event handler method for the `Decrypt File` button (`buttonDecryptFile_Click`), and the `DecryptFile` method.</span></span> <span data-ttu-id="abf26-178">İlk yöntem bir dosya seçmek için bir iletişim kutusu görüntüler ve dosya adını şifre çözme işlemini gerçekleştiren ikinci yönteme geçirir.</span><span class="sxs-lookup"><span data-stu-id="abf26-178">The first method displays a dialog box for selecting a file and passes its file name to the second method, which performs the decryption.</span></span>  
  
 <span data-ttu-id="abf26-179">`Decrypt` yöntemi aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="abf26-179">The `Decrypt` method does the following:</span></span>  
  
1. <span data-ttu-id="abf26-180">İçeriğin şifresini çözmek için <xref:System.Security.Cryptography.RijndaelManaged> simetrik bir algoritma oluşturur.</span><span class="sxs-lookup"><span data-stu-id="abf26-180">Creates a <xref:System.Security.Cryptography.RijndaelManaged> symmetric algorithm to decrypt the content.</span></span>  
  
2. <span data-ttu-id="abf26-181">Şifrelenmiş anahtarın ve IV 'nin uzunluklarının elde edileceği şekilde, şifrelenmiş paketin <xref:System.IO.FileStream> ilk sekiz baytını bayt dizileri olarak okur.</span><span class="sxs-lookup"><span data-stu-id="abf26-181">Reads the first eight bytes of the <xref:System.IO.FileStream> of the encrypted package into byte arrays to obtain the lengths of the encrypted key and the IV.</span></span>  
  
3. <span data-ttu-id="abf26-182">Anahtar ve IV 'yi şifreleme paketinden bayt dizilerine ayıklar.</span><span class="sxs-lookup"><span data-stu-id="abf26-182">Extracts the key and IV from the encryption package into byte arrays.</span></span>  
  
4. <span data-ttu-id="abf26-183"><xref:System.Security.Cryptography.RijndaelManaged> anahtarının şifresini çözmek için bir <xref:System.Security.Cryptography.RSACryptoServiceProvider> nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="abf26-183">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to decrypt the <xref:System.Security.Cryptography.RijndaelManaged> key.</span></span>  
  
5. <span data-ttu-id="abf26-184">, <xref:System.IO.FileStream> şifreleme paketinin şifreleme metni bölümünü, şifresi çözülmüş dosyanın <xref:System.IO.FileStream> nesnesine okumak ve şifresini çözmek için bir <xref:System.Security.Cryptography.CryptoStream> nesnesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="abf26-184">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and decrypt the cipher text section of the <xref:System.IO.FileStream> encryption package, in blocks of bytes, into the <xref:System.IO.FileStream> object for the decrypted file.</span></span> <span data-ttu-id="abf26-185">Bu tamamlandığında şifre çözme işlemi tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="abf26-185">When this is finished, the decryption is completed.</span></span>  
  
 <span data-ttu-id="abf26-186">Aşağıdaki kodu `Decrypt File` düğmesi için `Click` olay işleyicisi olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="abf26-186">Add the following code as the `Click` event handler for the `Decrypt File` button.</span></span>  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 <span data-ttu-id="abf26-187">Aşağıdaki `DecryptFile` yöntemini forma ekleyin.</span><span class="sxs-lookup"><span data-stu-id="abf26-187">Add the following `DecryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a><span data-ttu-id="abf26-188">Ortak anahtar dışarı aktarılıyor</span><span class="sxs-lookup"><span data-stu-id="abf26-188">Exporting a Public Key</span></span>  
 <span data-ttu-id="abf26-189">Bu görev `Create Keys` düğmesi tarafından oluşturulan anahtarı bir dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="abf26-189">This task saves the key created by the `Create Keys` button to a file.</span></span> <span data-ttu-id="abf26-190">Yalnızca ortak parametreleri dışarı aktarır.</span><span class="sxs-lookup"><span data-stu-id="abf26-190">It exports only the public parameters.</span></span>  
  
 <span data-ttu-id="abf26-191">Bu görev, Gamze 'nin kendi ortak anahtarını veren senaryosuna benzetir. böylece, dosyaları şifreleyebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="abf26-191">This task simulates the scenario of Alice giving Bob her public key so that he can encrypt files for her.</span></span> <span data-ttu-id="abf26-192">Ortak anahtara sahip olan kişiler ve özel parametrelerle tam anahtar çiftine sahip olmadıkları için şifrelerini çözemeyecektir.</span><span class="sxs-lookup"><span data-stu-id="abf26-192">He and others who have that public key will not be able to decrypt them because they do not have the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="abf26-193">Aşağıdaki kodu `Export Public Key` düğmesi için `Click` olay işleyicisi olarak ekleyin (`buttonExportPublicKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="abf26-193">Add the following code as the `Click` event handler for the `Export Public Key` button (`buttonExportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
 [!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a><span data-ttu-id="abf26-194">Ortak anahtar içeri aktarılıyor</span><span class="sxs-lookup"><span data-stu-id="abf26-194">Importing a Public Key</span></span>  
 <span data-ttu-id="abf26-195">Bu görev, anahtarı `Export Public Key` düğmesi tarafından oluşturulan yalnızca ortak parametrelerle yükler ve anahtar kapsayıcısı adı olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="abf26-195">This task loads the key with only public parameters, as created by the `Export Public Key` button, and sets it as the key container name.</span></span>  
  
 <span data-ttu-id="abf26-196">Bu görev, can 'ın, dosyalarını şifreleyebilmesi için Çiğdem 'in anahtarını yalnızca ortak parametrelerle yükleyen emre 'nin senaryosuna benzetir.</span><span class="sxs-lookup"><span data-stu-id="abf26-196">This task simulates the scenario of Bob loading Alice's key with only public parameters so he can encrypt files for her.</span></span>  
  
 <span data-ttu-id="abf26-197">Aşağıdaki kodu `Import Public Key` düğmesi için `Click` olay işleyicisi olarak ekleyin (`buttonImportPublicKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="abf26-197">Add the following code as the `Click` event handler for the `Import Public Key` button (`buttonImportPublicKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
 [!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a><span data-ttu-id="abf26-198">Özel anahtar alma</span><span class="sxs-lookup"><span data-stu-id="abf26-198">Getting a Private Key</span></span>  
 <span data-ttu-id="abf26-199">Bu görev, `Create Keys` düğmesini kullanarak anahtar kapsayıcısı adını oluşturulan anahtarın adına ayarlar.</span><span class="sxs-lookup"><span data-stu-id="abf26-199">This task sets the key container name to the name of the key created by using the `Create Keys` button.</span></span> <span data-ttu-id="abf26-200">Anahtar kapsayıcısı, özel parametrelerle tam anahtar çiftini içerir.</span><span class="sxs-lookup"><span data-stu-id="abf26-200">The key container will contain the full key pair with private parameters.</span></span>  
  
 <span data-ttu-id="abf26-201">Bu görev, Bob tarafından şifrelenen dosyaların şifresini çözmek için özel anahtarını kullanarak Gamze 'nin senaryosuna benzetir.</span><span class="sxs-lookup"><span data-stu-id="abf26-201">This task simulates the scenario of Alice using her private key to decrypt files encrypted by Bob.</span></span>  
  
 <span data-ttu-id="abf26-202">Aşağıdaki kodu `Get Private Key` düğmesi için `Click` olay işleyicisi olarak ekleyin (`buttonGetPrivateKey_Click`).</span><span class="sxs-lookup"><span data-stu-id="abf26-202">Add the following code as the `Click` event handler for the `Get Private Key` button (`buttonGetPrivateKey_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
 [!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="abf26-203">Uygulamayı Test Etme</span><span class="sxs-lookup"><span data-stu-id="abf26-203">Testing the Application</span></span>  
 <span data-ttu-id="abf26-204">Uygulamayı oluşturduktan sonra, aşağıdaki test senaryolarını gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="abf26-204">After you have built the application, perform the following testing scenarios.</span></span>  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a><span data-ttu-id="abf26-205">Anahtar oluşturmak, şifrelemek ve şifresini çözmek için</span><span class="sxs-lookup"><span data-stu-id="abf26-205">To create keys, encrypt, and decrypt</span></span>  
  
1. <span data-ttu-id="abf26-206">`Create Keys` düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="abf26-206">Click the `Create Keys` button.</span></span> <span data-ttu-id="abf26-207">Etiket, anahtar adını gösterir ve tam bir anahtar çifti olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="abf26-207">The label displays the key name and shows that it is a full key pair.</span></span>  
  
2. <span data-ttu-id="abf26-208">`Export Public Key` düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="abf26-208">Click the `Export Public Key` button.</span></span> <span data-ttu-id="abf26-209">Ortak anahtar parametrelerini dışa aktarmanın geçerli anahtarı değiştirmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="abf26-209">Note that exporting the public key parameters does not change the current key.</span></span>  
  
3. <span data-ttu-id="abf26-210">`Encrypt File` düğmesine tıklayın ve bir dosya seçin.</span><span class="sxs-lookup"><span data-stu-id="abf26-210">Click the `Encrypt File` button and select a file.</span></span>  
  
4. <span data-ttu-id="abf26-211">`Decrypt File` düğmesine tıklayın ve yeni şifrelenen dosyayı seçin.</span><span class="sxs-lookup"><span data-stu-id="abf26-211">Click the `Decrypt File` button and select the file just encrypted.</span></span>  
  
5. <span data-ttu-id="abf26-212">Yalnızca şifresi çözülen dosyayı inceleyin.</span><span class="sxs-lookup"><span data-stu-id="abf26-212">Examine the file just decrypted.</span></span>  
  
6. <span data-ttu-id="abf26-213">Uygulamayı kapatın ve sonraki senaryoda kalıcı anahtar kapsayıcıları almayı sınamak için yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="abf26-213">Close the application and restart it to test retrieving persisted key containers in the next scenario.</span></span>  
  
#### <a name="to-encrypt-using-the-public-key"></a><span data-ttu-id="abf26-214">Ortak anahtar kullanarak şifrelemek için</span><span class="sxs-lookup"><span data-stu-id="abf26-214">To encrypt using the public key</span></span>  
  
1. <span data-ttu-id="abf26-215">`Import Public Key` düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="abf26-215">Click the `Import Public Key` button.</span></span> <span data-ttu-id="abf26-216">Etiket, anahtar adını görüntüler ve yalnızca ortak olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="abf26-216">The label displays the key name and shows that it is public only.</span></span>  
  
2. <span data-ttu-id="abf26-217">`Encrypt File` düğmesine tıklayın ve bir dosya seçin.</span><span class="sxs-lookup"><span data-stu-id="abf26-217">Click the `Encrypt File` button and select a file.</span></span>  
  
3. <span data-ttu-id="abf26-218">`Decrypt File` düğmesine tıklayın ve yeni şifrelenen dosyayı seçin.</span><span class="sxs-lookup"><span data-stu-id="abf26-218">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="abf26-219">Bu işlem başarısız olur çünkü şifresini çözmek için özel anahtarınız olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="abf26-219">This will fail because you must have the private key to decrypt.</span></span>  
  
 <span data-ttu-id="abf26-220">Bu senaryoda, bir dosyayı başka bir kişiye şifrelemek için yalnızca ortak anahtarın bulunması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="abf26-220">This scenario demonstrates having only the public key to encrypt a file for another person.</span></span> <span data-ttu-id="abf26-221">Genellikle bu kişi size yalnızca ortak anahtar verir ve şifre çözme için özel anahtarı karıştı.</span><span class="sxs-lookup"><span data-stu-id="abf26-221">Typically that person would give you only the public key and withhold the private key for decryption.</span></span>  
  
#### <a name="to-decrypt-using-the-private-key"></a><span data-ttu-id="abf26-222">Özel anahtarı kullanarak şifresini çözmek için</span><span class="sxs-lookup"><span data-stu-id="abf26-222">To decrypt using the private key</span></span>  
  
1. <span data-ttu-id="abf26-223">`Get Private Key` düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="abf26-223">Click the `Get Private Key` button.</span></span> <span data-ttu-id="abf26-224">Etiket, anahtar adını görüntüler ve tam anahtar çifti olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="abf26-224">The label displays the key name and shows whether it is the full key pair.</span></span>  
  
2. <span data-ttu-id="abf26-225">`Decrypt File` düğmesine tıklayın ve yeni şifrelenen dosyayı seçin.</span><span class="sxs-lookup"><span data-stu-id="abf26-225">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="abf26-226">Şifresini çözmek için tam anahtar çiftine sahip olduğunuzdan bu işlem başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="abf26-226">This will be successful because you have the full key pair to decrypt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abf26-227">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abf26-227">See also</span></span>

- [<span data-ttu-id="abf26-228">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="abf26-228">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
