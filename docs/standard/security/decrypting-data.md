---
title: Verilerin Şifresini Çözme
description: Simetrik bir algoritma veya asimetrik algoritma kullanarak .NET 'teki verilerin şifrelerini çözmeyi öğrenin.
ms.date: 07/16/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [.NET], decryption
- symmetric decryption
- asymmetric decryption
- decryption
ms.assetid: 9b266b6c-a9b2-4d20-afd8-b3a0d8fd48a0
ms.openlocfilehash: 7e8fe5a8b7ed7c217a31a8ee91a5d111257fed45
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440991"
---
# <a name="decrypting-data"></a>Verilerin Şifresini Çözme

Şifre çözme, şifreleme işleminin tersidir. Gizli anahtar şifrelemesi için, verileri şifrelemek için kullanılan anahtarı ve IV 'yi bilmeniz gerekir. Ortak anahtar şifrelemesi için, ortak anahtarı (verileri özel anahtar kullanılarak şifrelendiyse) veya özel anahtarı (verileri ortak anahtar kullanılarak şifrelendiyse) bilmeniz gerekir.

## <a name="symmetric-decryption"></a>Simetrik şifre çözme

Simetrik algoritmalarla şifrelenen verilerin şifresinin çözülmesi, simetrik algoritmalarla verileri şifrelemek için kullanılan işleme benzerdir. <xref:System.Security.Cryptography.CryptoStream>Sınıfı, yönetilen herhangi bir Stream nesnesinden okunan verilerin şifresini çözmek için .NET tarafından sunulan simetrik şifreleme sınıflarıyla birlikte kullanılır.

Aşağıdaki örnek, algoritma için varsayılan uygulama sınıfının yeni bir örneğinin nasıl oluşturulacağını göstermektedir <xref:System.Security.Cryptography.Aes> . Örnek, bir nesnesinde şifre çözme gerçekleştirmek için kullanılır <xref:System.Security.Cryptography.CryptoStream> . Bu örnek ilk olarak uygulama sınıfının yeni bir örneğini oluşturur <xref:System.Security.Cryptography.Aes> . Yönetilen bir akış değişkeninden başlatma vektörü (IV) değerini okur `myStream` . Sonra bir nesnesi oluşturur <xref:System.Security.Cryptography.CryptoStream> ve örneğin değerini başlatır `myStream` . <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor%2A?displayProperty=nameWithType>Örnekten yöntemi, <xref:System.Security.Cryptography.Aes> IV değerini ve şifreleme için kullanılan anahtarı geçti.

```vb
Dim aes As Aes = Aes.Create()
Dim cryptStream As New CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read)
```

```csharp
Aes aes = Aes.Create();
CryptoStream cryptStream = new CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read);
```

Aşağıdaki örnek, bir akış oluşturma, akışın şifresini çözme, akıştan okuma ve akışları kapatma sürecinin tamamını gösterir. *TestData.txt* adlı bir dosyayı okuyan bir dosya akışı nesnesi oluşturulur. Daha sonra **CryptoStream** sınıfı ve **AES** sınıfı kullanılarak dosya akışının şifresi çözülür. Bu örnek, [verileri şifrelemek](encrypting-data.md)için simetrik şifreleme örneğinde kullanılan anahtar değerini belirtir. Bu değerleri şifrelemek ve aktarmak için gereken kodu göstermez.

:::code language="csharp" source="snippets/decrypting-data/csharp/aes-decrypt.cs":::
:::code language="vb" source="snippets/decrypting-data/vb/aes-decrypt.vb":::

Yukarıdaki örnekte, [verileri şifrelemek](encrypting-data.md)için simetrik şifreleme örneğinde kullanılan anahtar ve algoritma kullanılmaktadır. Bu örnek tarafından oluşturulan *TestData.txt* dosyanın şifresini çözer ve konsolundaki özgün metni görüntüler.

## <a name="asymmetric-decryption"></a>Asimetrik şifre çözme

Genellikle, bir taraf (parti A) hem ortak hem de özel anahtar oluşturur ve anahtarı bellekte ya da bir şifreleme anahtarı kapsayıcısında depolar. Böylece bir taraf, ortak anahtarı başka bir tarafa (B partisi) gönderir. Ortak anahtarı kullanarak, B partisi verileri şifreler ve verileri A tarafına geri gönderir. Veriler alındıktan sonra, parti A 'nın, karşılık gelen özel anahtarı kullanarak şifresini çözer. Şifre çözme işlemi, yalnızca A tarafı, verileri şifrelemek için kullanılan ortak anahtar tarafı B 'ye karşılık gelen özel anahtarı kullanıyorsa başarılı olur.

Güvenli şifreleme anahtarı kapsayıcısında asimetrik anahtar depolama ve daha sonra asimetrik anahtarı alma hakkında bilgi için bkz. [nasıl yapılır: asimetrik anahtarları bir anahtar kapsayıcısında depolama](how-to-store-asymmetric-keys-in-a-key-container.md).

Aşağıdaki örnek, bir simetrik anahtarı ve IV 'yi temsil eden iki dizi baytlık şifre çözmeyi gösterir. <xref:System.Security.Cryptography.RSA>Bir üçüncü tarafa kolayca gönderebileceğiniz biçimdeki asimetrik ortak anahtarı nesneden ayıklama hakkında bilgi için bkz. [verileri şifreleme](encrypting-data.md).

```vb
'Create a new instance of the RSA class.
Dim rsa As RSA = RSA.Create()

' Export the public key information and send it to a third party.
' Wait for the third party to encrypt some data and send it back.

'Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, RSAEncryptionPadding.Pkcs1)
symmetricIV = rsa.Decrypt(encryptedSymmetricIV, RSAEncryptionPadding.Pkcs1)
```

```csharp
//Create a new instance of the RSA class.
RSA rsa = RSA.Create();

// Export the public key information and send it to a third party.
// Wait for the third party to encrypt some data and send it back.

//Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, RSAEncryptionPadding.Pkcs1);
symmetricIV = rsa.Decrypt(encryptedSymmetricIV , RSAEncryptionPadding.Pkcs1);
```

## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme ve Şifre Çözme için Anahtarlar Oluşturma](generating-keys-for-encryption-and-decryption.md)
- [Veri Şifreleme](encrypting-data.md)
- [Şifreleme Hizmetleri](cryptographic-services.md)
- [Şifreleme Modeli](cryptography-model.md)
- [Platformlar arası şifreleme](cross-platform-cryptography.md)
- [Doldurmayı kullanarak CBC modunda simetrik şifre çözmedeki zamanlama açıkları](vulnerabilities-cbc-mode.md)
- [ASP.NET Core veri koruma](/aspnet/core/security/data-protection/introduction)
