---
description: 'Daha fazla bilgi edinin: nasıl yapılır: Visual Basic dosya yükleme'
title: 'Nasıl yapılır: Karşıya Dosya Yükleme'
ms.date: 07/20/2015
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
ms.openlocfilehash: d38820cda6a143cf3f06bf6a2ca72cba5a9f3aef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675409"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a><span data-ttu-id="54131-103">Nasıl Yapılır: Visual Basic'te Karşıya Dosya Yükleme</span><span class="sxs-lookup"><span data-stu-id="54131-103">How to: Upload a File in Visual Basic</span></span>

<span data-ttu-id="54131-104"><xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>Yöntemi bir dosyayı karşıya yüklemek ve uzak bir konuma depolamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="54131-104">The <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> method can be used to upload a file and store it to a remote location.</span></span> <span data-ttu-id="54131-105">`ShowUI`Parametresi olarak ayarlanırsa `True` , karşıya yüklemenin ilerlemesini gösteren bir iletişim kutusu görüntülenir ve kullanıcıların işlemi iptal etmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="54131-105">If the `ShowUI` parameter is set to `True`, a dialog box is displayed that shows the progress of the upload and allows users to cancel the operation.</span></span>  
  
### <a name="to-upload-a-file"></a><span data-ttu-id="54131-106">Bir dosyayı karşıya yüklemek için</span><span class="sxs-lookup"><span data-stu-id="54131-106">To upload a file</span></span>  
  
- <span data-ttu-id="54131-107">`UploadFile`Kaynak dosyanın konumunu ve hedef dizin konumunu dize veya URI (Tekdüzen Kaynak tanımlayıcısı) olarak belirterek bir dosyayı karşıya yüklemek için yöntemini kullanın. Bu örnek dosyasını ' `Order.txt` ye yükler `http://www.cohowinery.com/uploads.aspx` .</span><span class="sxs-lookup"><span data-stu-id="54131-107">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI (Uniform Resource Identifier).This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`.</span></span>  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a><span data-ttu-id="54131-108">Bir dosyayı karşıya yüklemek ve işlemin ilerlemesini göstermek için</span><span class="sxs-lookup"><span data-stu-id="54131-108">To upload a file and show the progress of the operation</span></span>  
  
- <span data-ttu-id="54131-109">`UploadFile`Kaynak dosyanın konumunu ve hedef dizin konumunu dize veya URI olarak belirterek bir dosyayı karşıya yüklemek için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="54131-109">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI.</span></span> <span data-ttu-id="54131-110">Bu örnek, `Order.txt` `http://www.cohowinery.com/uploads.aspx` bir Kullanıcı adı veya parola sağlamadan dosyayı karşıya yükler, karşıya yüklemenin ilerlemesini gösterir ve 500 milisaniyelik zaman aşımı aralığına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="54131-110">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx` without supplying a user name or password, shows the progress of the upload, and has a time-out interval of 500 milliseconds.</span></span>  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="54131-111">Bir dosyayı karşıya yüklemek için Kullanıcı adı ve parola sağlama</span><span class="sxs-lookup"><span data-stu-id="54131-111">To upload a file, supplying a user name and password</span></span>  
  
- <span data-ttu-id="54131-112">`UploadFile`Kaynak dosyanın konumunu ve hedef dizin konumunu bir dize veya URI olarak belirterek ve Kullanıcı adını ve parolayı belirterek bir dosyayı karşıya yüklemek için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="54131-112">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI, and specifying the user name and the password.</span></span> <span data-ttu-id="54131-113">Bu örnek `Order.txt` `http://www.cohowinery.com/uploads.aspx` , Kullanıcı adı `anonymous` ve boş bir parola sağlayarak dosyayı öğesine yükler.</span><span class="sxs-lookup"><span data-stu-id="54131-113">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`, supplying the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="54131-114">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="54131-114">Robust Programming</span></span>  

 <span data-ttu-id="54131-115">Aşağıdaki koşullar bir özel durum oluşturabilir:</span><span class="sxs-lookup"><span data-stu-id="54131-115">The following conditions may throw an exception:</span></span>  
  
- <span data-ttu-id="54131-116">Yerel dosya yolu geçerli değil ( <xref:System.ArgumentException> ).</span><span class="sxs-lookup"><span data-stu-id="54131-116">The local file path is not valid (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="54131-117">Kimlik doğrulama başarısız oldu ( <xref:System.Security.SecurityException> ).</span><span class="sxs-lookup"><span data-stu-id="54131-117">Authentication failed (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="54131-118">Bağlantı zaman aşımına uğradı ( <xref:System.TimeoutException> ).</span><span class="sxs-lookup"><span data-stu-id="54131-118">The connection timed out (<xref:System.TimeoutException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54131-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54131-119">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [<span data-ttu-id="54131-120">Nasıl yapılır: Dosya İndirme</span><span class="sxs-lookup"><span data-stu-id="54131-120">How to: Download a File</span></span>](how-to-download-a-file.md)
- [<span data-ttu-id="54131-121">Nasıl yapılır: Dosya Yollarını Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="54131-121">How to: Parse File Paths</span></span>](../drives-directories-files/how-to-parse-file-paths.md)
