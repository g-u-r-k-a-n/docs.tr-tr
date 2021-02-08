---
description: 'Hakkında daha fazla bilgi için: nasıl yapılır: Visual Basic Ikili dosyalardan okuma'
title: 'Nasıl yapılır: İkili Dosyalardan Okuma'
ms.date: 07/20/2015
helpviewer_keywords:
- binary files [Visual Basic], reading from
- I/O [Visual Basic], reading from binary files
- ReadAllBytes method [Visual Basic], reading from binary files
- My.Computer.FileSystem object, reading from binary files
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
ms.openlocfilehash: 0d522c6f55c0ef2e39437ba732040afdf5113d7a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797516"
---
# <a name="how-to-read-from-binary-files-in-visual-basic"></a><span data-ttu-id="7c033-103">Nasıl Yapılır: Visual Basic'te İkili Dosyaları Okuma</span><span class="sxs-lookup"><span data-stu-id="7c033-103">How to: Read From Binary Files in Visual Basic</span></span>

<span data-ttu-id="7c033-104">`My.Computer.FileSystem`Nesnesi, `ReadAllBytes` ikili dosyalardan okumak için yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c033-104">The `My.Computer.FileSystem` object provides the `ReadAllBytes` method for reading from binary files.</span></span>  
  
### <a name="to-read-from-a-binary-file"></a><span data-ttu-id="7c033-105">İkili dosyadan okumak için</span><span class="sxs-lookup"><span data-stu-id="7c033-105">To read from a binary file</span></span>  
  
- <span data-ttu-id="7c033-106">`ReadAllBytes`Bir dosyanın içeriğini bayt dizisi olarak döndüren yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7c033-106">Use the `ReadAllBytes` method, which returns the contents of a file as a byte array.</span></span> <span data-ttu-id="7c033-107">Bu örnek dosyadan okur `C:/Documents and Settings/selfportrait.jpg` .</span><span class="sxs-lookup"><span data-stu-id="7c033-107">This example reads from the file `C:/Documents and Settings/selfportrait.jpg`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#78)]  
  
- <span data-ttu-id="7c033-108">Büyük ikili dosyalar için, <xref:System.IO.FileStream.Read%2A> <xref:System.IO.FileStream> tek seferde yalnızca belirtilen bir miktarı dosyadan okumak için nesnesinin yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c033-108">For large binary files, you can use the <xref:System.IO.FileStream.Read%2A> method of the <xref:System.IO.FileStream> object to read from the file only a specified amount at a time.</span></span> <span data-ttu-id="7c033-109">Böylece, her okuma işlemi için dosyanın belleğe ne kadarının yüklendiğini sınırlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c033-109">You can then limit how much of the file is loaded into memory for each read operation.</span></span> <span data-ttu-id="7c033-110">Aşağıdaki kod örneği bir dosyayı kopyalar ve çağıranın okuma işlemi başına ne kadar dosyanın belleğe okunduğunu belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c033-110">The following code example copies a file and allows the caller to specify how much of the file is read into memory per read operation.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#91)]  
  
## <a name="robust-programming"></a><span data-ttu-id="7c033-111">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="7c033-111">Robust Programming</span></span>  

 <span data-ttu-id="7c033-112">Aşağıdaki koşullar bir özel durumun oluşturulmasına neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="7c033-112">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="7c033-113">Yol, aşağıdaki nedenlerden biri için geçerli değil: sıfır uzunluklu bir dizedir, yalnızca boşluk içeriyor, geçersiz karakterler içeriyor veya bir cihaz yolu ( <xref:System.ArgumentException> ).</span><span class="sxs-lookup"><span data-stu-id="7c033-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="7c033-114">Yol () olduğu için geçerli değil `Nothing` <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="7c033-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="7c033-115">Dosya yok ( <xref:System.IO.FileNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="7c033-115">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="7c033-116">Dosya başka bir işlem tarafından kullanılıyor veya bir g/ç hatası oluştu ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="7c033-116">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="7c033-117">Yol, sistem tarafından tanımlanan uzunluk üst sınırını ( <xref:System.IO.PathTooLongException> ) aşıyor.</span><span class="sxs-lookup"><span data-stu-id="7c033-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="7c033-118">Yoldaki bir dosya veya dizin adı iki nokta içerir (:) ya da geçersiz bir biçimde ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="7c033-118">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="7c033-119">Dizeyi arabelleğe () yazmak için yeterli bellek yok <xref:System.OutOfMemoryException> .</span><span class="sxs-lookup"><span data-stu-id="7c033-119">There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).</span></span>  
  
- <span data-ttu-id="7c033-120">Kullanıcı, () yolunu görüntülemek için gerekli izinlere sahip değil <xref:System.Security.SecurityException> .</span><span class="sxs-lookup"><span data-stu-id="7c033-120">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
 <span data-ttu-id="7c033-121">Dosya adına dayanarak dosyanın içeriği ile ilgili kararlar vermeyin.</span><span class="sxs-lookup"><span data-stu-id="7c033-121">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="7c033-122">Örneğin, Form1. vb dosyası bir Visual Basic kaynak dosyası olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="7c033-122">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="7c033-123">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="7c033-123">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="7c033-124">Dosyanın içeriği beklendiği gibi olmayabilir ve dosyadan okuma yöntemleri başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="7c033-124">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c033-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c033-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [<span data-ttu-id="7c033-126">Dosyalardan Okuma</span><span class="sxs-lookup"><span data-stu-id="7c033-126">Reading from Files</span></span>](reading-from-files.md)
- [<span data-ttu-id="7c033-127">Nasıl yapılır: Birden Çok Biçimli Metin Dosyalarından Okuma</span><span class="sxs-lookup"><span data-stu-id="7c033-127">How to: Read From Text Files with Multiple Formats</span></span>](how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="7c033-128">Verileri Panoda Depolama ve Panodan Okuma</span><span class="sxs-lookup"><span data-stu-id="7c033-128">Storing Data to and Reading from the Clipboard</span></span>](../computer-resources/storing-data-to-and-reading-from-the-clipboard.md)
