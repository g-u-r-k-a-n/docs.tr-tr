---
title: CBC şifre çözme güvenlik açığı
description: Doldurma kullanarak şifreleme blok zincirleme (CBC) modu simetrik şifre çözme ile zamanlama güvenlik açıklarını algılamayı ve etkilerini öğrenin.
ms.date: 06/12/2018
author: blowdart
ms.openlocfilehash: 4616ef9015b47ff232a17f058c7a0f1449f42e81
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159968"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a><span data-ttu-id="3fc32-103">Doldurmayı kullanarak CBC modunda simetrik şifre çözmedeki zamanlama açıkları</span><span class="sxs-lookup"><span data-stu-id="3fc32-103">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>

<span data-ttu-id="3fc32-104">Microsoft, yalnızca belirli bir durum dışında, şifreli doldurma uygulandığında, şifreli şifrelemenin Şifre blok zincirleme (CBC) moduyla şifrelenmiş verilerin şifresinin çözülmesi için artık güvenli olduğunu düşünmektedir durumlarda.</span><span class="sxs-lookup"><span data-stu-id="3fc32-104">Microsoft believes that it's no longer safe to decrypt data encrypted with the Cipher-Block-Chaining (CBC) mode of symmetric encryption when verifiable padding has been applied without first ensuring the integrity of the ciphertext, except for very specific circumstances.</span></span> <span data-ttu-id="3fc32-105">Bu, şu anda bilinen şifreleme araştırmasını temel alır.</span><span class="sxs-lookup"><span data-stu-id="3fc32-105">This judgement is based on currently known cryptographic research.</span></span>

## <a name="introduction"></a><span data-ttu-id="3fc32-106">Giriş</span><span class="sxs-lookup"><span data-stu-id="3fc32-106">Introduction</span></span>

<span data-ttu-id="3fc32-107">Oracle saldırısı doldurma, şifrelenmiş verilere yönelik bir saldırı türüdür ve bu, anahtarı bilmeden, saldırganın verilerin içeriğini çözmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3fc32-107">A padding oracle attack is a type of attack against encrypted data that allows the attacker to decrypt the contents of the data, without knowing the key.</span></span>

<span data-ttu-id="3fc32-108">Bir Oracle, yürütmekte olduğu eylemin doğru olup olmadığı hakkında bir saldırgan bilgisi veren bir "söyleme" anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-108">An oracle refers to a "tell" which gives an attacker information about whether the action they're executing is correct or not.</span></span> <span data-ttu-id="3fc32-109">Bir pano veya kart oyununu bir alt öğe ile çalınmasını düşünün.</span><span class="sxs-lookup"><span data-stu-id="3fc32-109">Imagine playing a board or card game with a child.</span></span> <span data-ttu-id="3fc32-110">Yüz, büyük bir gülümseme ile ışıkdığında, bu, bir Oracle olan iyi bir taşıma yapmak üzere olduğunu düşündü.</span><span class="sxs-lookup"><span data-stu-id="3fc32-110">When her face lights up with a big smile because she thinks she's about to make a good move, that's an oracle.</span></span> <span data-ttu-id="3fc32-111">Bu şekilde, rakip olarak bir sonraki taşımayı uygun şekilde planlamak için bu Oracle 'ı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fc32-111">You, as the opponent, can use this oracle to plan your next move appropriately.</span></span>

<span data-ttu-id="3fc32-112">Doldurma, belirli bir şifreleme terimidir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-112">Padding is a specific cryptographic term.</span></span> <span data-ttu-id="3fc32-113">Verilerinizi şifrelemek için kullanılan algoritmalar olan bazı şifrelemeler, her bloğun sabit boyutta olduğu veri blokları üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="3fc32-113">Some ciphers, which are the algorithms used to encrypt your data, work on blocks of data where each block is a fixed size.</span></span> <span data-ttu-id="3fc32-114">Şifrelemek istediğiniz veriler blokları dolduracak doğru boyutta değilse, verileriniz tamamlanana kadar doldurulur.</span><span class="sxs-lookup"><span data-stu-id="3fc32-114">If the data you want to encrypt isn't the right size to fill the blocks, your data is padded until it does.</span></span> <span data-ttu-id="3fc32-115">Birçok doldurma formu, özgün giriş doğru boyutta olsa bile, her zaman doldurma gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-115">Many forms of padding require that padding to always be present, even if the original input was of the right size.</span></span> <span data-ttu-id="3fc32-116">Bu, verilerin şifre çözme sırasında her zaman güvenli bir şekilde kaldırılmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3fc32-116">This allows the padding to always be safely removed upon decryption.</span></span>

<span data-ttu-id="3fc32-117">İki şeyi birlikte koymak, Oracle içeren bir yazılım uygulamasının, şifresi çözülmüş verilerin geçerli bir doldurma içerip içermediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-117">Putting the two things together, a software implementation with a padding oracle reveals whether decrypted data has valid padding.</span></span> <span data-ttu-id="3fc32-118">Oracle, "Geçersiz doldurma" ya da geçersiz bir bloğun aksine geçerli bir blok işlemek için farklı bir zaman yaşamları gibi bir değer döndürmek gibi basit bir şey olabilir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-118">The oracle could be something as simple as returning a value that says "Invalid padding" or something more complicated like taking a measurably different time to process a valid block as opposed to an invalid block.</span></span>

<span data-ttu-id="3fc32-119">Blok tabanlı şifrelemeler, ikinci bloktaki verilerin ilk bloğundaki verilerin ilişkisini belirleyen, mod adlı başka bir özelliğe sahiptir ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="3fc32-119">Block-based ciphers have another property, called the mode, which determines the relationship of data in the first block to the data in the second block, and so on.</span></span> <span data-ttu-id="3fc32-120">En yaygın olarak kullanılan modlardan biri CBC ' dir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-120">One of the most commonly used modes is CBC.</span></span> <span data-ttu-id="3fc32-121">CBC, başlatma vektörü (IV) olarak bilinen bir başlangıç rastgele bloğunu tanıtır ve önceki bloğu, aynı anahtarla aynı iletiyi şifrelemek için aynı şifrelenmiş çıktıyı her zaman üretmediği için statik şifrelemenin sonucuyla birleştirir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-121">CBC introduces an initial random block, known as the Initialization Vector (IV), and combines the previous block with the result of static encryption to make it such that encrypting the same message with the same key doesn't always produce the same encrypted output.</span></span>

<span data-ttu-id="3fc32-122">Bir saldırgan, CBC verilerinin nasıl yapılandırıldığı, Oracle 'ı kullanıma açan koda kısmen değiştirilen iletileri gönderme ve Oracle 'ın verilerin doğru olduğunu söyleene kadar veri göndermeye devam eden bir Oracle ile birlikte bir doldurma kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-122">An attacker can use a padding oracle, in combination with how CBC data is structured, to send slightly changed messages to the code that exposes the oracle, and keep sending data until the oracle tells them the data is correct.</span></span> <span data-ttu-id="3fc32-123">Bu yanıttan saldırgan, ileti baytının bayt olarak şifresini çözebilir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-123">From this response, the attacker can decrypt the message byte by byte.</span></span>

<span data-ttu-id="3fc32-124">Modern bilgisayar ağları, bir saldırganın uzak sistemlerde yürütme sırasında çok küçük (0,1 MS 'den az) farklılık algılayabildiği yüksek kaliteden oluşur.</span><span class="sxs-lookup"><span data-stu-id="3fc32-124">Modern computer networks are of such high quality that an attacker can detect very small (less than 0.1 ms) differences in execution time on remote systems.</span></span><span data-ttu-id="3fc32-125"> Başarılı bir şifre çözme işleminin yalnızca verilerin üzerinde oynanmadığı durumlarda olabileceği, başarılı ve şifre çözme farklılıklarını gözlemleyecek şekilde tasarlanan araçların saldırılarına karşı savunmasız olduğu varsayılarak uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="3fc32-125"> Applications that are assuming that a successful decryption can only happen when the data wasn't tampered with may be vulnerable to attack from tools that are designed to observe differences in successful and unsuccessful decryption.</span></span> <span data-ttu-id="3fc32-126">Bu zamanlama farkı, bazı dillerde veya kitaplıklarda diğerlerinden daha önemli olabilir, ancak bu durum, uygulamanın hata yanıtı hesaba alındıktan sonra bu, tüm diller ve kitaplıklar için pratik bir tehdit olduğunu düşünülüyor.</span><span class="sxs-lookup"><span data-stu-id="3fc32-126">While this timing difference may be more significant in some languages or libraries than others, it's now believed that this is a practical threat for all languages and libraries when the application's response to failure is taken into account.</span></span>

<span data-ttu-id="3fc32-127">Bu saldırı, şifrelenen verileri değiştirme ve sonucu Oracle ile test etme yeteneğine bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="3fc32-127">This attack relies on the ability to change the encrypted data and test the result with the oracle.</span></span> <span data-ttu-id="3fc32-128">Saldırıyı tamamen hafifletmenin tek yolu, şifrelenen verilerde yapılan değişiklikleri algılamadır ve üzerinde herhangi bir işlem gerçekleştirmeyi reddeder.</span><span class="sxs-lookup"><span data-stu-id="3fc32-128">The only way to fully mitigate the attack is to detect changes to the encrypted data and refuse to perform any actions on it.</span></span> <span data-ttu-id="3fc32-129">Bunu yapmanın standart yolu, veriler için bir imza oluşturmak ve herhangi bir işlem gerçekleştirilmeden önce imzayı doğrulamak içindir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-129">The standard way to do this is to create a signature for the data and validate that signature before any operations are performed.</span></span> <span data-ttu-id="3fc32-130">İmza doğrulanabilir olmalıdır, saldırgan tarafından oluşturulamaz, aksi takdirde şifrelenmiş verileri değiştirebilir, ardından değiştirilen verilere göre yeni bir imza hesaplar.</span><span class="sxs-lookup"><span data-stu-id="3fc32-130">The signature must be verifiable, it cannot be created by the attacker, otherwise they'd change the encrypted data, then compute a new signature based on the changed data.</span></span> <span data-ttu-id="3fc32-131">Bir ortak uygun imza türü, anahtarlı karma ileti kimlik doğrulama kodu (HMAC) olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-131">One common type of appropriate signature is known as a keyed-hash message authentication code (HMAC).</span></span> <span data-ttu-id="3fc32-132">HMAC, yalnızca HMAC 'yi üreten kişi tarafından bilinen ve bunu doğrulayan kişiye ait gizli anahtar alan bir sağlama toplamıyla farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-132">An HMAC differs from a checksum in that it takes a secret key, known only to the person producing the HMAC and to the person validating it.</span></span> <span data-ttu-id="3fc32-133">Anahtarı elinde bulunmadan doğru bir HMAC oluşturamıyoruz.</span><span class="sxs-lookup"><span data-stu-id="3fc32-133">Without possession of the key, you can't produce a correct HMAC.</span></span> <span data-ttu-id="3fc32-134">Verilerinizi aldığınızda, sizin ve gönderen paylaşımının gizli anahtarını kullanarak HMAC 'yi bağımsız olarak hesapladıktan sonra, sizin oluşturduğunuz bir parola ile gönderilen HMAC 'yi karşılaştırırsınız.</span><span class="sxs-lookup"><span data-stu-id="3fc32-134">When you receive your data, you'd take the encrypted data, independently compute the HMAC using the secret key you and the sender share, then compare the HMAC they sent against the one you computed.</span></span> <span data-ttu-id="3fc32-135">Bu karşılaştırma sabit zamanlı olmalıdır, aksi takdirde başka bir algılanabilir Oracle eklediniz, farklı bir tür saldırıya izin verir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-135">This comparison must be constant time, otherwise you've added another detectable oracle, allowing a different type of attack.</span></span>

<span data-ttu-id="3fc32-136">Özet ' te, doldurulmuş CBC blok şifrelemelerini güvenle kullanmak için, verilerin şifresini çözmeyi denemeden önce sabit bir zaman karşılaştırması kullanarak doğruladığınız bir HMAC (veya başka bir veri bütünlüğü denetimi) ile birleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-136">In summary, to use padded CBC block ciphers safely, you must combine them with an HMAC (or another data integrity check) that you validate using a constant time comparison before trying to decrypt the data.</span></span> <span data-ttu-id="3fc32-137">Değiştirilen tüm iletiler yanıt üretmek için aynı miktarda zaman aldığı için, saldırı engellenir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-137">Since all altered messages take the same amount time to produce a response, the attack is prevented.</span></span>

## <a name="who-is-vulnerable"></a><span data-ttu-id="3fc32-138">Güvenlik açığı kimler</span><span class="sxs-lookup"><span data-stu-id="3fc32-138">Who is vulnerable</span></span>

<span data-ttu-id="3fc32-139">Bu güvenlik açığı, kendi şifrelemesini ve şifre çözmeyi gerçekleştiren hem yönetilen hem de yerel uygulamalar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-139">This vulnerability applies to both managed and native applications that are performing their own encryption and decryption.</span></span> <span data-ttu-id="3fc32-140">Bu, örneğin:</span><span class="sxs-lookup"><span data-stu-id="3fc32-140">This includes, for example:</span></span>

- <span data-ttu-id="3fc32-141">Daha sonra sunucuda şifresinin çözülmesi için bir tanımlama bilgisi şifreleyen uygulama.</span><span class="sxs-lookup"><span data-stu-id="3fc32-141">An application that encrypts a cookie for later decryption on the server.</span></span>
- <span data-ttu-id="3fc32-142">Kullanıcıların, sütunları daha sonra şifresi çözülen bir tabloya veri eklemesine olanak sağlayan bir veritabanı uygulaması.</span><span class="sxs-lookup"><span data-stu-id="3fc32-142">A database application that provides the ability for users to insert data into a table whose columns are later decrypted.</span></span>
- <span data-ttu-id="3fc32-143">Geçiş sırasında verileri korumak için paylaşılan bir anahtar kullanarak şifrelemeye dayalı bir veri aktarma uygulaması.</span><span class="sxs-lookup"><span data-stu-id="3fc32-143">A data transfer application that relies on encryption using a shared key to protect the data in transit.</span></span>
- <span data-ttu-id="3fc32-144">TLS tünelinin "içindeki" iletilerini şifreleyen ve şifresini çözdüğü bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="3fc32-144">An application that encrypts and decrypts messages "inside" the TLS tunnel.</span></span>

<span data-ttu-id="3fc32-145">Bu senaryolarda yalnızca TLS kullanmanın sizi koruyamadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3fc32-145">Note that using TLS alone may not protect you in these scenarios.</span></span>

<span data-ttu-id="3fc32-146">Savunmasız bir uygulama:</span><span class="sxs-lookup"><span data-stu-id="3fc32-146">A vulnerable application:</span></span>

- <span data-ttu-id="3fc32-147">, BHŞIFRE modunu kullanarak, PKCS # 7 veya ANSI X. 923 gibi bir doğrulanabilen doldurma moduyla verilerin şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="3fc32-147">Decrypts data using the CBC cipher mode with a verifiable padding mode, such as PKCS#7 or ANSI X.923.</span></span>
- <span data-ttu-id="3fc32-148">Veri bütünlüğü denetimi gerçekleştirmeden (MAC veya asimetrik dijital imza aracılığıyla) şifre çözme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-148">Performs the decryption without having performed a data integrity check (via a MAC or an asymmetric digital signature).</span></span>

<span data-ttu-id="3fc32-149">Bu, şifreleme Iletisi sözdizimi (PKCS # 7/CMS) EnvelopedData yapısı gibi bu temel elemanların üst kısmında oluşturulan uygulamalar için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-149">This also applies to applications built on top of abstractions over top of these primitives, such as the Cryptographic Message Syntax (PKCS#7/CMS) EnvelopedData structure.</span></span>

## <a name="related-areas-of-concern"></a><span data-ttu-id="3fc32-150">İlgili sorun bölgeleri</span><span class="sxs-lookup"><span data-stu-id="3fc32-150">Related areas of concern</span></span>

<span data-ttu-id="3fc32-151">Araştırma, Microsoft 'un, iletinin iyi bilinen veya öngörülebilir bir altbilgi yapısına sahip olduğu durumlarda ISO 10126 ile doldurulmuş CBC iletileri hakkında daha fazla endişeniz olduğunu fark etti.</span><span class="sxs-lookup"><span data-stu-id="3fc32-151">Research has led Microsoft to be further concerned about CBC messages that are padded with ISO 10126-equivalent padding when the message has a well-known or predictable footer structure.</span></span> <span data-ttu-id="3fc32-152">Örneğin, W3C XML şifreleme söz dizimi ve Işleme önerisi (xmlenc, EncryptedXml) kuralları altında hazırlanan içerik.</span><span class="sxs-lookup"><span data-stu-id="3fc32-152">For example, content prepared under the rules of the W3C XML Encryption Syntax and Processing Recommendation (xmlenc, EncryptedXml).</span></span> <span data-ttu-id="3fc32-153">İletiyi imzalamak için W3C Kılavuzu, daha sonra şifreleyin ve bu süre içinde uygun kabul edilse de, Microsoft artık her zaman şifrelemeden sonra-ENTER ' ı önerir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-153">While the W3C guidance to sign the message then encrypt was considered appropriate at the time, Microsoft now recommends always doing encrypt-then-sign.</span></span>

<span data-ttu-id="3fc32-154">Asimetrik bir anahtarla rastgele bir ileti arasında herhangi bir güven ilişkisi bulunmadığından, uygulama geliştiricileri her zaman asimetrik imza anahtarının uygulanabilirliğini doğrulamak için en az olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3fc32-154">Application developers should always be mindful of verifying the applicability of an asymmetric signature key, as there's no inherent trust relationship between an asymmetric key and an arbitrary message.</span></span>

## <a name="details"></a><span data-ttu-id="3fc32-155">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="3fc32-155">Details</span></span>

<span data-ttu-id="3fc32-156">Tarihsel olarak, HMAC veya RSA imzaları gibi yollarla önemli verileri şifrelemek ve kimliklerini doğrulamak için önemli bir sorun oluştu.</span><span class="sxs-lookup"><span data-stu-id="3fc32-156">Historically, there has been consensus that it's important to both encrypt and authenticate important data, using means such as HMAC or RSA signatures.</span></span> <span data-ttu-id="3fc32-157">Ancak, şifreleme ve kimlik doğrulama işlemlerinin nasıl dizilebileceğine ilişkin daha az açık yönergeler vardır.</span><span class="sxs-lookup"><span data-stu-id="3fc32-157">However, there has been less clear guidance as to how to sequence the encryption and authentication operations.</span></span> <span data-ttu-id="3fc32-158">Bu makalede açıklanan güvenlik açığı nedeniyle, Microsoft 'un artık "şifreleyin-then-imzala" paradigmasını her zaman kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-158">Due to the vulnerability detailed in this article, Microsoft's guidance is now to always use the "encrypt-then-sign" paradigm.</span></span> <span data-ttu-id="3fc32-159">Diğer bir deyişle, önce simetrik anahtar kullanarak verileri şifreler, sonra şifreli bir MAC veya asimetrik imza (şifrelenmiş veriler) üzerinden işlem yapın.</span><span class="sxs-lookup"><span data-stu-id="3fc32-159">That is, first encrypt data using a symmetric key, then compute a MAC or asymmetric signature over the ciphertext (encrypted data).</span></span> <span data-ttu-id="3fc32-160">Verilerin şifresini çözerken, ters işlemini gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="3fc32-160">When decrypting data, perform the reverse.</span></span> <span data-ttu-id="3fc32-161">İlk olarak, şifreli nesnelerin MAC veya imzasını onaylayın ve sonra şifresini çözün.</span><span class="sxs-lookup"><span data-stu-id="3fc32-161">First, confirm the MAC or signature of the ciphertext, then decrypt it.</span></span>

<span data-ttu-id="3fc32-162">"Oracle saldırılarını doldurma" olarak bilinen bir güvenlik açığı sınıfı, 10 yıldan fazla bir süredir mevcut olduğu bilinmektedir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-162">A class of vulnerabilities known as "padding oracle attacks" have been known to exist for over 10 years.</span></span> <span data-ttu-id="3fc32-163">Bu güvenlik açıkları, bir saldırganın her veri bloğu için 4096 ' den fazla girişim kullanılarak AES ve 3DES gibi simetrik blok algoritmalarıyla şifrelenmiş verilerin şifresini çözmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3fc32-163">These vulnerabilities allow an attacker to decrypt data encrypted by symmetric block algorithms, such as AES and 3DES, using no more than 4096 attempts per block of data.</span></span> <span data-ttu-id="3fc32-164">Bu güvenlik açıkları, şifrelemelerin blok verileri sonunda en sık kullanılan doğrulanabilir doldurma verileriyle kullanımını engeller.</span><span class="sxs-lookup"><span data-stu-id="3fc32-164">These vulnerabilities make use of the fact that block ciphers are most frequently used with verifiable padding data at the end.</span></span> <span data-ttu-id="3fc32-165">Bir saldırgan şifreli ile oynayabilir ve yapılan bir hatanın sonda bir hata nedeniyle başarısız olup olmadığını fark etmeksizin, saldırganın verilerin şifresini çözebilmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fc32-165">It was found that if an attacker can tamper with ciphertext and find out whether the tampering caused an error in the format of the padding at the end, the attacker can decrypt the data.</span></span>

<span data-ttu-id="3fc32-166">Başlangıçta pratik saldırılar, ASP.NET güvenlik açığı [MS10-070](/security-updates/SecurityBulletins/2010/ms10-070)gibi doldurma 'nın geçerli olup olmadığına göre farklı hata kodları döndüren hizmetlere dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3fc32-166">Initially, practical attacks were based on services that would return different error codes based on whether padding was valid, such as the ASP.NET vulnerability [MS10-070](/security-updates/SecurityBulletins/2010/ms10-070).</span></span> <span data-ttu-id="3fc32-167">Bununla birlikte, Microsoft artık işleme geçerli ve geçersiz doldurma arasındaki farkları kullanarak benzer saldırıları gerçekleştirmek için pratik olduğunu düşünmektedir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-167">However, Microsoft now believes that it's practical to conduct similar attacks using only the differences in timing between processing valid and invalid padding.</span></span>

<span data-ttu-id="3fc32-168">Şifreleme şeması bir imza kullanır ve imza doğrulamasının belirli bir veri uzunluğu (içeriğinden bağımsız olarak) için sabit bir çalışma zamanı ile gerçekleştirildiğinden, veri bütünlüğü bir saldırgana bir [taraf kanal](https://en.wikipedia.org/wiki/Side-channel_attack)aracılığıyla herhangi bir bilgi yaymadan doğrulanabilir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-168">Provided that the encryption scheme employs a signature and that the signature verification is performed with a fixed runtime for a given length of data (irrespective of the contents), the data integrity can be verified without emitting any information to an attacker via a [side channel](https://en.wikipedia.org/wiki/Side-channel_attack).</span></span> <span data-ttu-id="3fc32-169">Bütünlük denetimi, değiştirilen iletileri reddettiğinde, Oracle tehdidi doldurma işlemi azaltılmış olur.</span><span class="sxs-lookup"><span data-stu-id="3fc32-169">Since the integrity check rejects any tampered messages, the padding oracle threat is mitigated.</span></span>

## <a name="guidance"></a><span data-ttu-id="3fc32-170">Rehber</span><span class="sxs-lookup"><span data-stu-id="3fc32-170">Guidance</span></span>

<span data-ttu-id="3fc32-171">İlk ve daha önce, Microsoft, gizlilik ihtiyaçlarına sahip tüm verilerin Aktarım Katmanı Güvenliği (TLS) üzerinden aktarılması ve Güvenli Yuva Katmanı (SSL) ' nin ardıl olması önerilir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-171">First and foremost, Microsoft recommends that any data that has confidentiality needs be transmitted over Transport Layer Security (TLS), the successor to Secure Sockets Layer (SSL).</span></span>

<span data-ttu-id="3fc32-172">Sonra, uygulamanızı şu şekilde çözümleyin:</span><span class="sxs-lookup"><span data-stu-id="3fc32-172">Next, analyze your application to:</span></span>

- <span data-ttu-id="3fc32-173">Hangi şifrelemeyi tam olarak kullandığınızı ve kullanmakta olduğunuz platformlar ve API 'Ler tarafından hangi şifrelemenin sağlandığını anlayın.</span><span class="sxs-lookup"><span data-stu-id="3fc32-173">Understand precisely what encryption you're performing and what encryption is being provided by the platforms and APIs you're using.</span></span>
- <span data-ttu-id="3fc32-174">Bir simetrik [blok şifre algoritmasındaki](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers)AES ve 3DES gibi her bir kullanımın, bir gizli anahtar veri bütünlüğü denetimi (asimetrik Imza, HMAC veya şifre modunu, GCM veya CCM gibi [kimliği doğrulanmış şifreleme](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE) modu olarak değiştirme) dahil edin.</span><span class="sxs-lookup"><span data-stu-id="3fc32-174">Be certain that each usage at each layer of a symmetric [block cipher algorithm](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers), such as AES and 3DES, in CBC mode incorporate the use of a secret-keyed data integrity check (an asymmetric signature, an HMAC, or to change the cipher mode to an [authenticated encryption](https://en.wikipedia.org/wiki/Authenticated_encryption) (AE) mode such as GCM or CCM).</span></span>

<span data-ttu-id="3fc32-175">Geçerli araştırmayı temel alan genellikle, kimlik doğrulama ve şifreleme adımları AE olmayan şifreleme modları için bağımsız olarak gerçekleştirildiğinde, en iyi genel seçenektir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-175">Based on the current research, it's generally believed that when the authentication and encryption steps are performed independently for non-AE modes of encryption, authenticating the ciphertext (encrypt-then-sign) is the best general option.</span></span> <span data-ttu-id="3fc32-176">Bununla birlikte, şifrelemeye en uygun yanıt yoktur ve bu Genelleştirme, profesyonel bir cryptotlv ile yönlendirilmiş tavsiyeler kadar iyi değildir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-176">However, there's no one-size-fits-all correct answer to cryptography and this generalization isn't as good as directed advice from a professional cryptographer.</span></span>

<span data-ttu-id="3fc32-177">Mesajlaşma biçimini değiştiremedik ancak kimliği doğrulanmamış CBC şifre çözme işlemini gerçekleştirmeye yönelik uygulamalar, şu gibi azaltıcı etkenleri kullanmayı denemenize önerilir:</span><span class="sxs-lookup"><span data-stu-id="3fc32-177">Applications that are unable to change their messaging format but perform unauthenticated CBC decryption are encouraged to try to incorporate mitigations such as:</span></span>

- <span data-ttu-id="3fc32-178">Şifre çözme, şifre çözücü 'ın doldurmayı doğrulamasına veya kaldırmasına izin vermeden çözülür:</span><span class="sxs-lookup"><span data-stu-id="3fc32-178">Decrypt without allowing the decryptor to verify or remove padding:</span></span>
  - <span data-ttu-id="3fc32-179">Uygulanan herhangi bir doldurma hala kaldırılmalı veya yoksayıldı, bu da yükü uygulamanıza taşıyor olursunuz.</span><span class="sxs-lookup"><span data-stu-id="3fc32-179">Any padding that was applied still needs to be removed or ignored, you're moving the burden into your application.</span></span>
  - <span data-ttu-id="3fc32-180">Bu avantaj, doldurma doğrulamanın ve kaldırmanın diğer uygulama verileri doğrulama mantığına dahil edilebilir olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-180">The benefit is that the padding verification and removal can be incorporated into other application data verification logic.</span></span> <span data-ttu-id="3fc32-181">Doldurma doğrulaması ve veri doğrulaması sabit zamanlı olarak yapılabiliyorsanız, tehdit azalır.</span><span class="sxs-lookup"><span data-stu-id="3fc32-181">If the padding verification and data verification can be done in constant time, the threat is reduced.</span></span>
  - <span data-ttu-id="3fc32-182">Doldurma yorumu algılanan ileti uzunluğunu değiştirdiği için, bu yaklaşımdan alınan zamanlama bilgileri yine de olabilir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-182">Since the interpretation of the padding changes the perceived message length, there may still be timing information emitted from this approach.</span></span>
- <span data-ttu-id="3fc32-183">Şifre çözme doldurma modunu ISO10126 olarak değiştirin:</span><span class="sxs-lookup"><span data-stu-id="3fc32-183">Change the decryption padding mode to ISO10126:</span></span>
  - <span data-ttu-id="3fc32-184">ISO10126 şifre çözme dolgusu, hem PKCS7 şifreleme dolgusu hem de ANSIX923 şifreleme dolgusu ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="3fc32-184">ISO10126 decryption padding is compatible with both PKCS7 encryption padding and ANSIX923 encryption padding.</span></span>
  - <span data-ttu-id="3fc32-185">Modunun değiştirilmesi, Oracle bilgisinin tüm blok yerine 1 bayta doldurmasını azaltır.</span><span class="sxs-lookup"><span data-stu-id="3fc32-185">Changing the mode reduces the padding oracle knowledge to 1 byte instead of the entire block.</span></span> <span data-ttu-id="3fc32-186">Ancak içeriğin, kapanış XML öğesi gibi iyi bilinen bir altbilgisi varsa ilgili saldırılar da iletinin geri kalanına saldırmak için devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-186">However, if the content has a well-known footer, such as a closing XML element, related attacks can continue to attack the rest of the message.</span></span>
  - <span data-ttu-id="3fc32-187">Bu Ayrıca, saldırganın aynı düz metin ile farklı bir ileti kaymasıyla birden çok kez şifrelenmesini engelleyebileceği durumlarda düz metin kurtarmayı engellemez.</span><span class="sxs-lookup"><span data-stu-id="3fc32-187">This also doesn't prevent plaintext recovery in situations where the attacker can coerce the same plaintext to be encrypted multiple times with a different message offset.</span></span>
- <span data-ttu-id="3fc32-188">Zamanlama sinyalini sönmek için bir şifre çözme çağrısının değerlendirilmesine geçit:</span><span class="sxs-lookup"><span data-stu-id="3fc32-188">Gate the evaluation of a decryption call to dampen the timing signal:</span></span>
  - <span data-ttu-id="3fc32-189">Saklama zamanı hesaplamasının, doldurma işleminin bulunduğu tüm veri kesimlerine yönelik olarak en fazla bir şifre çözme işleminin gerçekleşmesi için en az sürede olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-189">The computation of hold time must have a minimum in excess of the maximum amount of time the decryption operation would take for any data segment that contains padding.</span></span>
  - <span data-ttu-id="3fc32-190">Zaman hesaplamaları, <xref:System.Environment.TickCount?displayProperty=nameWithType> (kullanıma alma/taşma) veya iki sistem zaman damgasını (NTP ayarlama hatalarıyla ilgili olarak) değil, [yüksek çözünürlüklü zaman damgaları](/windows/desktop/sysinfo/acquiring-high-resolution-time-stamps)elde etmek için yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3fc32-190">Time computations should be done according to the guidance in [Acquiring high-resolution time stamps](/windows/desktop/sysinfo/acquiring-high-resolution-time-stamps), not by using <xref:System.Environment.TickCount?displayProperty=nameWithType> (subject to roll-over/overflow) or subtracting two system timestamps (subject to NTP adjustment errors).</span></span>
  - <span data-ttu-id="3fc32-191">Zaman hesaplamaları, yalnızca sonuna kadar değil, yönetilen veya C++ uygulamalardaki tüm olası özel durumlar dahil olmak üzere şifre çözme işleminin yerine eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-191">Time computations must be inclusive of the decryption operation including all potential exceptions in managed or C++ applications, not just padded onto the end.</span></span>
  - <span data-ttu-id="3fc32-192">Başarı veya başarısızlık henüz belirlendiyse, zaman aşımı kapısı zaman aşımına uğradığında hata döndürmemelidir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-192">If success or failure has been determined yet, the timing gate needs to return failure when it expires.</span></span>
- <span data-ttu-id="3fc32-193">Kimliği doğrulanmamış bir şifre çözme işlemi gerçekleştiren hizmetler, "geçersiz" iletilerinin bir taşın bir şekilde gelip gelmediğini tespit etmek için izlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-193">Services that are performing unauthenticated decryption should have monitoring in place to detect that a flood of "invalid" messages has come through.</span></span>
  - <span data-ttu-id="3fc32-194">Bu sinyalin, hem hatalı pozitif sonuçları (meşru olmayan veriler) hem de yanlış negatifleri (atlatabilir algılama için çok uzun bir süre boyunca saldırıyı yayma) taşıdığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3fc32-194">Bear in mind that this signal carries both false positives (legitimately corrupted data) and false negatives (spreading out the attack over a sufficiently long time to evade detection).</span></span>

## <a name="finding-vulnerable-code---native-applications"></a><span data-ttu-id="3fc32-195">Savunmasız koda yerel uygulamalar bulma</span><span class="sxs-lookup"><span data-stu-id="3fc32-195">Finding vulnerable code - native applications</span></span>

<span data-ttu-id="3fc32-196">Windows şifrelemesi: yeni nesil (CNG) kitaplığı 'nda oluşturulan programlar için:</span><span class="sxs-lookup"><span data-stu-id="3fc32-196">For programs built against the Windows Cryptography: Next Generation (CNG) library:</span></span>

- <span data-ttu-id="3fc32-197">Şifre çözme çağrısı, `BCRYPT_BLOCK_PADDING` bayrağını belirterek [Bcryptşifre çözmeye](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt)yapılır.</span><span class="sxs-lookup"><span data-stu-id="3fc32-197">The decryption call is to [BCryptDecrypt](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptdecrypt), specifying the `BCRYPT_BLOCK_PADDING` flag.</span></span>
- <span data-ttu-id="3fc32-198">Anahtar tanıtıcısı, [BCRYPT_CHAINING_MODE](/windows/desktop/SecCNG/cng-property-identifiers#BCRYPT_CHAINING_MODE) `BCRYPT_CHAIN_MODE_CBC`olarak ayarlanmış [bcryptsetproperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) çağırarak başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="3fc32-198">The key handle has been initialized by calling [BCryptSetProperty](/windows/desktop/api/bcrypt/nf-bcrypt-bcryptsetproperty) with [BCRYPT_CHAINING_MODE](/windows/desktop/SecCNG/cng-property-identifiers#BCRYPT_CHAINING_MODE) set to `BCRYPT_CHAIN_MODE_CBC`.</span></span>
  - <span data-ttu-id="3fc32-199">`BCRYPT_CHAIN_MODE_CBC` varsayılan olduğundan, etkilenen kod `BCRYPT_CHAINING_MODE`için herhangi bir değer atamalamayabilir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-199">Since `BCRYPT_CHAIN_MODE_CBC` is the default, affected code may not have assigned any value for `BCRYPT_CHAINING_MODE`.</span></span>

<span data-ttu-id="3fc32-200">Eski Windows şifreleme API 'sine karşı oluşturulan programlar için:</span><span class="sxs-lookup"><span data-stu-id="3fc32-200">For programs built against the older Windows Cryptographic API:</span></span>

- <span data-ttu-id="3fc32-201">Şifre çözme çağrısı, `Final=TRUE`ile [Cryptşifre çözme](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) işlemi yapılır.</span><span class="sxs-lookup"><span data-stu-id="3fc32-201">The decryption call is to [CryptDecrypt](/windows/desktop/api/wincrypt/nf-wincrypt-cryptdecrypt) with `Final=TRUE`.</span></span>
- <span data-ttu-id="3fc32-202">Anahtar tanıtıcısı, `CRYPT_MODE_CBC`olarak ayarlanmış [KP_MODE](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam) [Cryptsetkeyparad](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) çağırarak başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="3fc32-202">The key handle has been initialized by calling [CryptSetKeyParam](/windows/desktop/api/wincrypt/nf-wincrypt-cryptsetkeyparam) with [KP_MODE](/windows/desktop/api/wincrypt/nf-wincrypt-cryptgetkeyparam) set to `CRYPT_MODE_CBC`.</span></span>
  - <span data-ttu-id="3fc32-203">`CRYPT_MODE_CBC` varsayılan olduğundan, etkilenen kod `KP_MODE`için herhangi bir değer atamalamayabilir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-203">Since `CRYPT_MODE_CBC` is the default, affected code may not have assigned any value for `KP_MODE`.</span></span>

## <a name="finding-vulnerable-code---managed-applications"></a><span data-ttu-id="3fc32-204">Savunmasız koda göre yönetilen uygulamalar bulma</span><span class="sxs-lookup"><span data-stu-id="3fc32-204">Finding vulnerable code - managed applications</span></span>

- <span data-ttu-id="3fc32-205">Şifre çözme çağrısı, <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType><xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> veya <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> yöntemlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3fc32-205">The decryption call is to the <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor> or <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])> methods on <xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="3fc32-206">Bu, .NET içinde aşağıdaki türetilmiş türleri içerir, ancak üçüncü taraf türlerini de içerebilir:</span><span class="sxs-lookup"><span data-stu-id="3fc32-206">This includes the following derived types within the .NET, but may also include third-party types:</span></span>
    - <xref:System.Security.Cryptography.Aes>
    - <xref:System.Security.Cryptography.AesCng>
    - <xref:System.Security.Cryptography.AesCryptoServiceProvider>
    - <xref:System.Security.Cryptography.AesManaged>
    - <xref:System.Security.Cryptography.DES>
    - <xref:System.Security.Cryptography.DESCryptoServiceProvider>
    - <xref:System.Security.Cryptography.RC2>
    - <xref:System.Security.Cryptography.RC2CryptoServiceProvider>
    - <xref:System.Security.Cryptography.Rijndael>
    - <xref:System.Security.Cryptography.RijndaelManaged>
    - <xref:System.Security.Cryptography.TripleDES>
    - <xref:System.Security.Cryptography.TripleDESCng>
    - <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>
- <span data-ttu-id="3fc32-207"><xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> özelliği <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>veya <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>olarak ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3fc32-207">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>, <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>, or <xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="3fc32-208"><xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> varsayılan olduğundan, etkilenen koda hiçbir şekilde <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> özelliği atanmayabilir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-208">Since <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType> property.</span></span>
- <span data-ttu-id="3fc32-209"><xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> özelliği <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="3fc32-209">The <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property was set to <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType></span></span>
  - <span data-ttu-id="3fc32-210"><xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> varsayılan olduğundan, etkilenen koda hiçbir şekilde <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> özelliği atanmayabilir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-210">Since <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType> is the default, affected code may never have assigned the <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType> property.</span></span>

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a><span data-ttu-id="3fc32-211">Güvenlik açığı kodu bulma-şifreleme iletisi sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3fc32-211">Finding vulnerable code - cryptographic message syntax</span></span>

<span data-ttu-id="3fc32-212">Şifrelenmiş içeriği AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) veya RC2 (1.2.840.113549.3.2) için CBC modunu kullanan, kimliği doğrulanmamış bir CMS EnvelopedData iletisi Ayrıca, CBC modunda başka bir blok şifre algoritmasını kullanan iletiler ve güvenlik açığı.</span><span class="sxs-lookup"><span data-stu-id="3fc32-212">An unauthenticated CMS EnvelopedData message whose encrypted content uses the CBC mode of AES (2.16.840.1.101.3.4.1.2, 2.16.840.1.101.3.4.1.22, 2.16.840.1.101.3.4.1.42), DES (1.3.14.3.2.7), 3DES (1.2.840.113549.3.7) or RC2 (1.2.840.113549.3.2) is vulnerable, as well as messages using any other block cipher algorithms in CBC mode.</span></span>

<span data-ttu-id="3fc32-213">Akış şifrelemeleri bu belirli güvenlik açığına karşı savunmasız olmasa da, Microsoft, her zaman ContentEncryptionAlgorithm değerini inceleyerek verilerin kimlik doğrulamasını önerir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-213">While stream ciphers aren't susceptible to this particular vulnerability, Microsoft recommends always authenticating the data over inspecting the ContentEncryptionAlgorithm value.</span></span>

<span data-ttu-id="3fc32-214">Yönetilen uygulamalar için, <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>iletilen herhangi bir değer olarak bir CMS EnvelopedData blobu algılanabilir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-214">For managed applications, a CMS EnvelopedData blob can be detected as any value that is passed to <xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>.</span></span>

<span data-ttu-id="3fc32-215">Yerel uygulamalar için, bir CMS EnvelopedData blobu, elde edilen [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) `CMSG_ENVELOPED` ve/veya CMS tanıtıcısı daha sonra [cryptmsgcontrol](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol)aracılığıyla bir `CMSG_CTRL_DECRYPT` yönergesini gönderdiyse [CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) aracılığıyla bir CMS tanıtıcısına sağlanan herhangi bir değer olarak algılanabilir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-215">For native applications, a CMS EnvelopedData blob can be detected as any value provided to a CMS handle via [CryptMsgUpdate](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgupdate) whose resulting [CMSG_TYPE_PARAM](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsggetparam) is `CMSG_ENVELOPED` and/or the CMS handle is later sent a `CMSG_CTRL_DECRYPT` instruction via [CryptMsgControl](/windows/desktop/api/wincrypt/nf-wincrypt-cryptmsgcontrol).</span></span>

## <a name="vulnerable-code-example---managed"></a><span data-ttu-id="3fc32-216">Güvenlik açığı bulunan kod örneği-yönetilen</span><span class="sxs-lookup"><span data-stu-id="3fc32-216">Vulnerable code example - managed</span></span>

<span data-ttu-id="3fc32-217">Bu yöntem bir tanımlama bilgisini okur ve şifresini çözer ve veri bütünlüğü denetimi görünmez.</span><span class="sxs-lookup"><span data-stu-id="3fc32-217">This method reads a cookie and decrypts it and no data integrity check is visible.</span></span> <span data-ttu-id="3fc32-218">Bu nedenle, bu yöntem tarafından okunan bir tanımlama bilgisinin içeriği, kendisini alan Kullanıcı tarafından veya şifrelenmiş tanımlama bilgisi değerini almış olan herhangi bir saldırgan tarafından saldırıya uğrayılabilir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-218">Therefore, the contents of a cookie that is read by this method can be attacked by the user who received it, or by any attacker who has obtained the encrypted cookie value.</span></span>

```csharp
private byte[] DecryptCookie(string cookieName)
{
    HttpCookie cookie = Request.Cookies[cookieName];

    if (cookie == null)
    {
        return null;
    }

    using (ICryptoTransform decryptor = _aes.CreateDecryptor())
    using (MemoryStream memoryStream = new MemoryStream())
    using (CryptoStream cryptoStream =
        new CryptoStream(memoryStream, decryptor, CryptoStreamMode.Write))
    {
        byte[] readCookie = Convert.FromBase64String(cookie.Value);
        cryptoStream.Write(readCookie, 0, readCookie.Length);
        cryptoStream.FlushFinalBlock();
        return memoryStream.ToArray();
    }
}
```

## <a name="example-code-following-recommended-practices---managed"></a><span data-ttu-id="3fc32-219">Önerilen uygulamalar-yönetilen örnek kodu</span><span class="sxs-lookup"><span data-stu-id="3fc32-219">Example code following recommended practices - managed</span></span>

<span data-ttu-id="3fc32-220">Aşağıdaki örnek kod standart olmayan bir ileti biçimi kullanır</span><span class="sxs-lookup"><span data-stu-id="3fc32-220">The following sample code uses a non-standard message format of</span></span>

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

<span data-ttu-id="3fc32-221">`cipher_algorithm_id` ve `hmac_algorithm_id` algoritma tanımlayıcıları, bu algoritmaların uygulama yerel (Standart olmayan) temsilleridir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-221">where the `cipher_algorithm_id` and `hmac_algorithm_id` algorithm identifiers are application-local (non-standard) representations of those algorithms.</span></span> <span data-ttu-id="3fc32-222">Bu tanımlayıcılar, tam olarak birleştirilmiş bir bytestream yerine mevcut mesajlaşma protokolünün diğer bölümlerinde anlamlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-222">These identifiers may make sense in other parts of your existing messaging protocol instead of as a bare concatenated bytestream.</span></span>

<span data-ttu-id="3fc32-223">Bu örnek ayrıca bir şifreleme anahtarı ve HMAC anahtarı türetmek için tek bir ana anahtar kullanır.</span><span class="sxs-lookup"><span data-stu-id="3fc32-223">This example also uses a single master key to derive both an encryption key and an HMAC key.</span></span> <span data-ttu-id="3fc32-224">Bu, listedir anahtarlı bir uygulamayı çift anahtarlı bir uygulamaya açmak ve iki anahtarı farklı değerler olarak korumak için kolaylık olarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="3fc32-224">This is provided both as a convenience for turning a singly-keyed application into a dual-keyed application, and to encourage keeping the two keys as different values.</span></span> <span data-ttu-id="3fc32-225">Bu, HMAC anahtar ve şifreleme anahtarının eşitlememe dışı olmasını da güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="3fc32-225">It further guarantees that the HMAC key and encryption key can't get out of synchronization.</span></span>

<span data-ttu-id="3fc32-226">Bu örnek, şifreleme veya şifre çözme için <xref:System.IO.Stream> kabul etmez.</span><span class="sxs-lookup"><span data-stu-id="3fc32-226">This sample doesn't accept a <xref:System.IO.Stream> for either encryption or decryption.</span></span> <span data-ttu-id="3fc32-227">Geçerli veri biçimi, `hmac_tag` değeri, şifreli dosyadan önce olduğundan tek geçişli şifrelemeyi zorlaştırır.</span><span class="sxs-lookup"><span data-stu-id="3fc32-227">The current data format makes one-pass encrypt difficult because the `hmac_tag` value precedes the ciphertext.</span></span> <span data-ttu-id="3fc32-228">Ancak, bu biçim, ayrıştırıcının daha kolay tutulmasını sağlamak için başındaki tüm sabit boyutlu öğeleri sakladığı için seçilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-228">However, this format was chosen because it keeps all of the fixed-size elements at the beginning to keep the parser simpler.</span></span> <span data-ttu-id="3fc32-229">Bu veri biçimiyle, tek taramalı şifre çözme mümkün olsa da, bir uygulayıcının GetHashAndReset çağrısına ve TransformFinalBlock çağrılmadan önce sonucu doğrulamaya yönelik bir sorun vardır.</span><span class="sxs-lookup"><span data-stu-id="3fc32-229">With this data format, one-pass decrypt is possible, though an implementer is cautioned to call GetHashAndReset and verify the result before calling TransformFinalBlock.</span></span> <span data-ttu-id="3fc32-230">Akış şifrelemesi önemliyse, farklı bir AE modu gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="3fc32-230">If streaming encryption is important, then a different AE mode may be required.</span></span>

```csharp
// ==++==
//
//   Copyright (c) Microsoft Corporation.  All rights reserved.
//
//   Shared under the terms of the Microsoft Public License,
//   https://opensource.org/licenses/MS-PL
//
// ==--==

using System;
using System.Diagnostics;
using System.IO;
using System.Runtime.CompilerServices;
using System.Security.Cryptography;

namespace Microsoft.Examples.Cryptography
{
    public enum AeCipher : byte
    {
        Unknown,
        Aes256CbcPkcs7,
    }

    public enum AeMac : byte
    {
        Unknown,
        HMACSHA256,
        HMACSHA384,
    }

    /// <summary>
    /// Provides extension methods to make HashAlgorithm look like .NET Core's
    /// IncrementalHash
    /// </summary>
    internal static class IncrementalHashExtensions
    {
        public static void AppendData(this HashAlgorithm hash, byte[] data)
        {
            hash.TransformBlock(data, 0, data.Length, null, 0);
        }

        public static void AppendData(
            this HashAlgorithm hash,
            byte[] data,
            int offset,
            int length)
        {
            hash.TransformBlock(data, offset, length, null, 0);
        }

        public static byte[] GetHashAndReset(this HashAlgorithm hash)
        {
            hash.TransformFinalBlock(Array.Empty<byte>(), 0, 0);
            return hash.Hash;
        }
    }

    public static partial class AuthenticatedEncryption
    {
        /// <summary>
        /// Use <paramref name="masterKey"/> to derive two keys (one cipher, one HMAC)
        /// to provide authenticated encryption for <paramref name="message"/>.
        /// </summary>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <param name="message">The message to encrypt</param>
        /// <returns>
        /// A concatenation of
        /// [cipher algorithm+chainmode+padding][mac algorithm][authtag][IV][ciphertext],
        /// suitable to be passed to <see cref="Decrypt"/>.
        /// </returns>
        /// <remarks>
        /// <paramref name="masterKey"/> should be a 128-bit (or bigger) value generated
        /// by a secure random number generator, such as the one returned from
        /// <see cref="RandomNumberGenerator.Create()"/>.
        /// This implementation chooses to block deficient inputs by length, but does not
        /// make any attempt at discerning the randomness of the key.
        ///
        /// If the master key is being input by a prompt (like a password/passphrase)
        /// then it should be properly turned into keying material via a Key Derivation
        /// Function like PBKDF2, represented by Rfc2898DeriveBytes. A 'password' should
        /// never be simply turned to bytes via an Encoding class and used as a key.
        /// </remarks>
        public static byte[] Encrypt(byte[] masterKey, byte[] message)
        {
            if (masterKey == null)
                throw new ArgumentNullException(nameof(masterKey));
            if (masterKey.Length < 16)
                throw new ArgumentOutOfRangeException(
                    nameof(masterKey),
                    "Master Key must be at least 128 bits (16 bytes)");
            if (message == null)
                throw new ArgumentNullException(nameof(message));

            // First, choose an encryption scheme.
            AeCipher aeCipher = AeCipher.Aes256CbcPkcs7;

            // Second, choose an authentication (message integrity) scheme.
            //
            // In this example we use the master key length to change from HMACSHA256 to
            // HMACSHA384, but that is completely arbitrary. This mostly represents a
            // "cryptographic needs change over time" scenario.
            AeMac aeMac = masterKey.Length < 48 ? AeMac.HMACSHA256 : AeMac.HMACSHA384;

            // It's good to be able to identify what choices were made when a message was
            // encrypted, so that the message can later be decrypted. This allows for
            // future versions to add support for new encryption schemes, but still be
            // able to read old data. A practice known as "cryptographic agility".
            //
            // This is similar in practice to PKCS#7 messaging, but this uses a
            // private-scoped byte rather than a public-scoped Object IDentifier (OID).
            // Please note that the scheme in this example adheres to no particular
            // standard, and is unlikely to survive to a more complete implementation in
            // the .NET Framework.
            //
            // You may be well-served by prepending a version number byte to this
            // message, but may want to avoid the value 0x30 (the leading byte value for
            // DER-encoded structures such as X.509 certificates and PKCS#7 messages).
            byte[] algorithmChoices = { (byte)aeCipher, (byte)aeMac };
            byte[] iv;
            byte[] cipherText;
            byte[] tag;

            // Using our algorithm choices, open an HMAC (as an authentication tag
            // generator) and a SymmetricAlgorithm which use different keys each derived
            // from the same master key.
            //
            // A custom implementation may very well have distinctly managed secret keys
            // for the MAC and cipher, this example merely demonstrates the master to
            // derived key methodology to encourage key separation from the MAC and
            // cipher keys.
            using (HMAC tagGenerator = GetMac(aeMac, masterKey))
            {
                using (SymmetricAlgorithm cipher = GetCipher(aeCipher, masterKey))
                using (ICryptoTransform encryptor = cipher.CreateEncryptor())
                {
                    // Since no IV was provided, a random one has been generated
                    // during the call to CreateEncryptor.
                    //
                    // But note that it only does the auto-generation once. If the cipher
                    // object were used again, a call to GenerateIV would have been
                    // required.
                    iv = cipher.IV;

                    cipherText = Transform(encryptor, message, 0, message.Length);
                }

                // The IV and ciphertest both need to be included in the MAC to prevent
                // tampering.
                //
                // By including the algorithm identifiers, we have technically moved from
                // simple Authenticated Encryption (AE) to Authenticated Encryption with
                // Additional Data (AEAD). By including the algorithm identifiers in the
                // MAC, it becomes harder for an attacker to change them as an attempt to
                // perform a downgrade attack.
                //
                // If you've added a data format version field, it can also be included
                // in the MAC to further inhibit an attacker's options for confusing the
                // data processor into believing the tampered message is valid.
                tagGenerator.AppendData(algorithmChoices);
                tagGenerator.AppendData(iv);
                tagGenerator.AppendData(cipherText);
                tag = tagGenerator.GetHashAndReset();
            }

            // Build the final result as the concatenation of everything except the keys.
            int totalLength =
                algorithmChoices.Length +
                tag.Length +
                iv.Length +
                cipherText.Length;

            byte[] output = new byte[totalLength];
            int outputOffset = 0;

            Append(algorithmChoices, output, ref outputOffset);
            Append(tag, output, ref outputOffset);
            Append(iv, output, ref outputOffset);
            Append(cipherText, output, ref outputOffset);

            Debug.Assert(outputOffset == output.Length);
            return output;
        }

        /// <summary>
        /// Reads a message produced by <see cref="Encrypt"/> after verifying it hasn't
        /// been tampered with.
        /// </summary>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <param name="cipherText">
        /// The output of <see cref="Encrypt"/>: a concatenation of a cipher ID, mac ID,
        /// authTag, IV, and cipherText.
        /// </param>
        /// <returns>The decrypted content.</returns>
        /// <exception cref="ArgumentNullException">
        /// <paramref name="masterKey"/> is <c>null</c>.
        /// </exception>
        /// <exception cref="ArgumentNullException">
        /// <paramref name="cipherText"/> is <c>null</c>.
        /// </exception>
        /// <exception cref="CryptographicException">
        /// <paramref name="cipherText"/> identifies unknown algorithms, is not long
        /// enough, fails a data integrity check, or fails to decrypt.
        /// </exception>
        /// <remarks>
        /// <paramref name="masterKey"/> should be a 128-bit (or larger) value
        /// generated by a secure random number generator, such as the one returned from
        /// <see cref="RandomNumberGenerator.Create()"/>. This implementation chooses to
        /// block deficient inputs by length, but doesn't make any attempt at
        /// discerning the randomness of the key.
        ///
        /// If the master key is being input by a prompt (like a password/passphrase),
        /// then it should be properly turned into keying material via a Key Derivation
        /// Function like PBKDF2, represented by Rfc2898DeriveBytes. A 'password' should
        /// never be simply turned to bytes via an Encoding class and used as a key.
        /// </remarks>
        public static byte[] Decrypt(byte[] masterKey, byte[] cipherText)
        {
            // This example continues the .NET practice of throwing exceptions for
            // failures. If you consider message tampering to be normal (and thus
            // "not exceptional") behavior, you may like the signature
            // bool Decrypt(byte[] messageKey, byte[] cipherText, out byte[] message)
            // better.
            if (masterKey == null)
                throw new ArgumentNullException(nameof(masterKey));
            if (masterKey.Length < 16)
                throw new ArgumentOutOfRangeException(
                    nameof(masterKey),
                    "Master Key must be at least 128 bits (16 bytes)");
            if (cipherText == null)
                throw new ArgumentNullException(nameof(cipherText));

            // The format of this message is assumed to be public, so there's no harm in
            // saying ahead of time that the message makes no sense.
            if (cipherText.Length < 2)
            {
                throw new CryptographicException();
            }

            // Use the message algorithm headers to determine what cipher algorithm and
            // MAC algorithm are going to be used. Since the same Key Derivation
            // Functions (KDFs) are being used in Decrypt as Encrypt, the keys are also
            // the same.
            AeCipher aeCipher = (AeCipher)cipherText[0];
            AeMac aeMac = (AeMac)cipherText[1];

            using (SymmetricAlgorithm cipher = GetCipher(aeCipher, masterKey))
            using (HMAC tagGenerator = GetMac(aeMac, masterKey))
            {
                int blockSizeInBytes = cipher.BlockSize / 8;
                int tagSizeInBytes = tagGenerator.HashSize / 8;
                int headerSizeInBytes = 2;
                int tagOffset = headerSizeInBytes;
                int ivOffset = tagOffset + tagSizeInBytes;
                int cipherTextOffset = ivOffset + blockSizeInBytes;
                int cipherTextLength = cipherText.Length - cipherTextOffset;
                int minLen = cipherTextOffset + blockSizeInBytes;

                // Again, the minimum length is still assumed to be public knowledge,
                // nothing has leaked out yet. The minimum length couldn't just be calculated
                // without reading the header.
                if (cipherText.Length < minLen)
                {
                    throw new CryptographicException();
                }

                // It's very important that the MAC be calculated and verified before
                // proceeding to decrypt the ciphertext, as this prevents any sort of
                // information leaking out to an attacker.
                //
                // Don't include the tag in the calculation, though.

                // First, everything before the tag (the cipher and MAC algorithm ids)
                tagGenerator.AppendData(cipherText, 0, tagOffset);

                // Skip the data before the tag and the tag, then read everything that
                // remains.
                tagGenerator.AppendData(
                    cipherText,
                    tagOffset + tagSizeInBytes,
                    cipherText.Length - tagSizeInBytes - tagOffset);

                byte[] generatedTag = tagGenerator.GetHashAndReset();

                // The time it took to get to this point has so far been a function only
                // of the length of the data, or of non-encrypted values (e.g. it could
                // take longer to prepare the *key* for the HMACSHA384 MAC than the
                // HMACSHA256 MAC, but the algorithm choice wasn't a secret).
                //
                // If the verification of the authentication tag aborts as soon as a
                // difference is found in the byte arrays then your program may be
                // acting as a timing oracle which helps an attacker to brute-force the
                // right answer for the MAC. So, it's very important that every possible
                // "no" (2^256-1 of them for HMACSHA256) be evaluated in as close to the
                // same amount of time as possible. For this, we call CryptographicEquals
                if (!CryptographicEquals(
                    generatedTag,
                    0,
                    cipherText,
                    tagOffset,
                    tagSizeInBytes))
                {
                    // Assuming every tampered message (of the same length) took the same
                    // amount of time to process, we can now safely say
                    // "this data makes no sense" without giving anything away.
                    throw new CryptographicException();
                }

                // Restore the IV into the symmetricAlgorithm instance.
                byte[] iv = new byte[blockSizeInBytes];
                Buffer.BlockCopy(cipherText, ivOffset, iv, 0, iv.Length);
                cipher.IV = iv;

                using (ICryptoTransform decryptor = cipher.CreateDecryptor())
                {
                    return Transform(
                        decryptor,
                        cipherText,
                        cipherTextOffset,
                        cipherTextLength);
                }
            }
        }

        private static byte[] Transform(
            ICryptoTransform transform,
            byte[] input,
            int inputOffset,
            int inputLength)
        {
            // Many of the implementations of ICryptoTransform report true for
            // CanTransformMultipleBlocks, and when the entire message is available in
            // one shot this saves on the allocation of the CryptoStream and the
            // intermediate structures it needs to properly chunk the message into blocks
            // (since the underlying stream won't always return the number of bytes
            // needed).
            if (transform.CanTransformMultipleBlocks)
            {
                return transform.TransformFinalBlock(input, inputOffset, inputLength);
            }

            // If our transform couldn't do multiple blocks at once, let CryptoStream
            // handle the chunking.
            using (MemoryStream messageStream = new MemoryStream())
            using (CryptoStream cryptoStream =
                new CryptoStream(messageStream, transform, CryptoStreamMode.Write))
            {
                cryptoStream.Write(input, inputOffset, inputLength);
                cryptoStream.FlushFinalBlock();
                return messageStream.ToArray();
            }
        }

        /// <summary>
        /// Open a properly configured <see cref="SymmetricAlgorithm"/> conforming to the
        /// scheme identified by <paramref name="aeCipher"/>.
        /// </summary>
        /// <param name="aeCipher">The cipher mode to open.</param>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <returns>
        /// A SymmetricAlgorithm object with the right key, cipher mode, and padding
        /// mode; or <c>null</c> on unknown algorithms.
        /// </returns>
        private static SymmetricAlgorithm GetCipher(AeCipher aeCipher, byte[] masterKey)
        {
            SymmetricAlgorithm symmetricAlgorithm;

            switch (aeCipher)
            {
                case AeCipher.Aes256CbcPkcs7:
                    symmetricAlgorithm = Aes.Create();
                    // While 256-bit, CBC, and PKCS7 are all the default values for these
                    // properties, being explicit helps comprehension more than it hurts
                    // performance.
                    symmetricAlgorithm.KeySize = 256;
                    symmetricAlgorithm.Mode = CipherMode.CBC;
                    symmetricAlgorithm.Padding = PaddingMode.PKCS7;
                    break;
                default:
                    // An algorithm we don't understand
                    throw new CryptographicException();
            }

            // Instead of using the master key directly, derive a key for our chosen
            // HMAC algorithm based upon the master key.
            //
            // Since none of the symmetric encryption algorithms currently in .NET
            // support key sizes greater than 256-bit, we can use HMACSHA256 with
            // NIST SP 800-108 5.1 (Counter Mode KDF) to derive a value that is
            // no smaller than the key size, then Array.Resize to trim it down as
            // needed.

            using (HMAC hmac = new HMACSHA256(masterKey))
            {
                // i=1, Label=ASCII(cipher)
                byte[] cipherKey = hmac.ComputeHash(
                    new byte[] { 1, 99, 105, 112, 104, 101, 114 });

                // Resize the array to the desired keysize. KeySize is in bits,
                // and Array.Resize wants the length in bytes.
                Array.Resize(ref cipherKey, symmetricAlgorithm.KeySize / 8);

                symmetricAlgorithm.Key = cipherKey;
            }

            return symmetricAlgorithm;
        }

        /// <summary>
        /// Open a properly configured <see cref="HMAC"/> conforming to the scheme
        /// identified by <paramref name="aeMac"/>.
        /// </summary>
        /// <param name="aeMac">The message authentication mode to open.</param>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <returns>
        /// An HMAC object with the proper key, or <c>null</c> on unknown algorithms.
        /// </returns>
        private static HMAC GetMac(AeMac aeMac, byte[] masterKey)
        {
            HMAC hmac;

            switch (aeMac)
            {
                case AeMac.HMACSHA256:
                    hmac = new HMACSHA256();
                    break;
                case AeMac.HMACSHA384:
                    hmac = new HMACSHA384();
                    break;
                default:
                    // An algorithm we don't understand
                    throw new CryptographicException();
            }

            // Instead of using the master key directly, derive a key for our chosen
            // HMAC algorithm based upon the master key.
            // Since the output size of the HMAC is the same as the ideal key size for
            // the HMAC, we can use the master key over a fixed input once to perform
            // NIST SP 800-108 5.1 (Counter Mode KDF):
            hmac.Key = masterKey;

            // i=1, Context=ASCII(MAC)
            byte[] newKey = hmac.ComputeHash(new byte[] { 1, 77, 65, 67 });

            hmac.Key = newKey;
            return hmac;
        }

        // A simple helper method to ensure that the offset (writePos) always moves
        // forward with new data.
        private static void Append(byte[] newData, byte[] combinedData, ref int writePos)
        {
            Buffer.BlockCopy(newData, 0, combinedData, writePos, newData.Length);
            writePos += newData.Length;
        }

        /// <summary>
        /// Compare the contents of two arrays in an amount of time which is only
        /// dependent on <paramref name="length"/>.
        /// </summary>
        /// <param name="a">An array to compare to <paramref name="b"/>.</param>
        /// <param name="aOffset">
        /// The starting position within <paramref name="a"/> for comparison.
        /// </param>
        /// <param name="b">An array to compare to <paramref name="a"/>.</param>
        /// <param name="bOffset">
        /// The starting position within <paramref name="b"/> for comparison.
        /// </param>
        /// <param name="length">
        /// The number of bytes to compare between <paramref name="a"/> and
        /// <paramref name="b"/>.</param>
        /// <returns>
        /// <c>true</c> if both <paramref name="a"/> and <paramref name="b"/> have
        /// sufficient length for the comparison and all of the applicable values are the
        /// same in both arrays; <c>false</c> otherwise.
        /// </returns>
        /// <remarks>
        /// An "insufficient data" <c>false</c> response can happen early, but otherwise
        /// a <c>true</c> or <c>false</c> response take the same amount of time.
        /// </remarks>
        [MethodImpl(MethodImplOptions.NoInlining | MethodImplOptions.NoOptimization)]
        private static bool CryptographicEquals(
            byte[] a,
            int aOffset,
            byte[] b,
            int bOffset,
            int length)
        {
            Debug.Assert(a != null);
            Debug.Assert(b != null);
            Debug.Assert(length >= 0);

            int result = 0;

            if (a.Length - aOffset < length || b.Length - bOffset < length)
            {
                return false;
            }

            unchecked
            {
                for (int i = 0; i < length; i++)
                {
                    // Bitwise-OR of subtraction has been found to have the most
                    // stable execution time.
                    //
                    // This cannot overflow because bytes are 1 byte in length, and
                    // result is 4 bytes.
                    // The OR propagates all set bytes, so the differences are only
                    // present in the lowest byte.
                    result = result | (a[i + aOffset] - b[i + bOffset]);
                }
            }

            return result == 0;
        }
    }
}
```
