---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Kullanıcı bilgilerini grup bağlantılarına atama'
title: 'Nasıl yapılır: Bağlantıları Gruplandırmak için Kullanıcı Bilgileri Atama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ce550d6-8f7c-4ea7-add8-5bc27a7b51be
ms.openlocfilehash: 2af901b91c561f5f46c63ed627cbd0053d30e624
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729269"
---
# <a name="how-to-assign-user-information-to-group-connections"></a>Nasıl yapılır: Bağlantıları Gruplandırmak için Kullanıcı Bilgileri Atama

 Aşağıdaki örnek, bu kodun bu bölümü çağrılmadan ve *Kullanıcı adının* benzersiz olması Için uygulamanın *UserName*, *securelyStoredPassword* ve *Domain* değişkenlerini ayarladığını varsayarak, Kullanıcı bilgilerinin grup bağlantılarına nasıl atanacağını gösterir.  
  
### <a name="to-assign-user-information-to-a-group-connection"></a>Kullanıcı bilgilerini bir grup bağlantısına atamak için  
  
1. Bir bağlantı grubu adı oluşturun.  
  
    ```csharp  
    SHA1Managed Sha1 = new SHA1Managed();  
    Byte[] updHash = Sha1.ComputeHash(Encoding.UTF8.GetBytes(UserName + SecurelyStoredPassword + Domain));  
    String secureGroupName = Encoding.Default.GetString(updHash);  
    ```  
  
    ```vb  
    Dim Sha1 As New SHA1Managed()  
    Dim updHash As [Byte]() = Sha1.ComputeHash(Encoding.UTF8.GetBytes((UserName + SecurelyStoredPassword + Domain)))  
    Dim secureGroupName As [String] = Encoding.Default.GetString(updHash)  
    ```  
  
2. Belirli bir URL için bir istek oluşturun. Örneğin, aşağıdaki kod URL için bir istek oluşturur `http://www.contoso.com.`  
  
    ```csharp  
    WebRequest myWebRequest=WebRequest.Create("http://www.contoso.com");  
    ```  
  
    ```vb  
    Dim myWebRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
    ```  
  
3. Web isteği için kimlik bilgilerini ve bağlantı grubuadı ' nı ayarlayın ve bir **WebResponse** nesnesi almak Için **GetResponse** öğesini çağırın.  
  
    ```csharp  
    myWebRequest.Credentials = new NetworkCredential(UserName, SecurelyStoredPassword, Domain);
    myWebRequest.ConnectionGroupName = secureGroupName;  
  
    WebResponse myWebResponse=myWebRequest.GetResponse();  
    ```  
  
    ```vb  
    myWebRequest.Credentials = New NetworkCredential(UserName, SecurelyStoredPassword, Domain)  
    myWebRequest.ConnectionGroupName = secureGroupName  
  
    Dim myWebResponse As WebResponse = myWebRequest.GetResponse()  
    ```  
  
4. Webrespoz nesnesini kullandıktan sonra yanıt akışını kapatın.  
  
    ```csharp  
    MyWebResponse.Close();  
    ```  
  
    ```vb  
    MyWebResponse.Close()  
    ```  
  
 Örnek  
  
```csharp  
// Create a connection group name.  
SHA1Managed Sha1 = new SHA1Managed();  
Byte[] updHash = Sha1.ComputeHash(Encoding.UTF8.GetBytes(UserName + SecurelyStoredPassword + Domain));  
String secureGroupName = Encoding.Default.GetString(updHash);  
  
// Create a request for a specific URL.  
WebRequest myWebRequest=WebRequest.Create("http://www.contoso.com");  
  
myWebRequest.Credentials = new NetworkCredential(UserName, SecurelyStoredPassword, Domain);
myWebRequest.ConnectionGroupName = secureGroupName;  
  
WebResponse myWebResponse=myWebRequest.GetResponse();  
  
// Insert the code that uses myWebResponse.  
  
MyWebResponse.Close();  
```  
  
```vb  
' Create a secure group name.  
Dim Sha1 As New SHA1Managed()  
Dim updHash As [Byte]() = Sha1.ComputeHash(Encoding.UTF8.GetBytes((UserName + SecurelyStoredPassword + Domain)))  
Dim secureGroupName As [String] = Encoding.Default.GetString(updHash)  
  
' Create a request for a specific URL.  
Dim myWebRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
  
myWebRequest.Credentials = New NetworkCredential(UserName, SecurelyStoredPassword, Domain)  
myWebRequest.ConnectionGroupName = secureGroupName  
  
Dim myWebResponse As WebResponse = myWebRequest.GetResponse()  
  
' Insert the code that uses myWebResponse.  
MyWebResponse.Close()  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantıları Yönetme](managing-connections.md)
- [Bağlantı Gruplandırma](connection-grouping.md)
