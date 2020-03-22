---
title: Panoya veri depolama ve Panodan okuma
ms.date: 07/20/2015
helpviewer_keywords:
- Clipboard, storing data to (My.Computer.Clipboard)
- Clipboard, reading from (My.Computer.Clipboard)
- Clipboard
- My.Computer.Clipboard object, tasks
- data [Visual Basic], Clipboard
- reading data, from Clipboard
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
ms.openlocfilehash: 243fb237f3f9ba53f8b29079df08531c102c78dd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74349726"
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a><span data-ttu-id="9c81d-102">Panoya veri depolama ve Panodan okuma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c81d-102">Storing data to and reading from the Clipboard (Visual Basic)</span></span>

<span data-ttu-id="9c81d-103">Pano, metin ve resim gibi verileri depolamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9c81d-103">The Clipboard can be used to store data, such as text and images.</span></span> <span data-ttu-id="9c81d-104">Pano tüm etkin işlemler tarafından paylaşıldığından, aralarındaveri aktarmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9c81d-104">Because the Clipboard is shared by all active processes, it can be used to transfer data between them.</span></span> <span data-ttu-id="9c81d-105">Nesne, `My.Computer.Clipboard` Pano'ya kolayca erişmenizi ve panodan okumanızı ve ona yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9c81d-105">The `My.Computer.Clipboard` object allows you to easily access the Clipboard and to read from and write to it.</span></span>  
  
## <a name="reading-from-the-clipboard"></a><span data-ttu-id="9c81d-106">Panodan Okuma</span><span class="sxs-lookup"><span data-stu-id="9c81d-106">Reading from the Clipboard</span></span>  

 <span data-ttu-id="9c81d-107">Panodaki <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> metni okumak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="9c81d-107">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> method to read the text in the Clipboard.</span></span> <span data-ttu-id="9c81d-108">Aşağıdaki kod metni okur ve bir ileti kutusunda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9c81d-108">The following code reads the text and displays it in a message box.</span></span> <span data-ttu-id="9c81d-109">Örneğin düzgün çalışması için Pano'da kayıtlı metin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9c81d-109">There must be text stored on the Clipboard for the example to run correctly.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#4)]  
  
 <span data-ttu-id="9c81d-110">Bu kod örneği, IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9c81d-110">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="9c81d-111">Kod snippet picker, Windows Forms **Uygulamaları > Pano**bulunur.</span><span class="sxs-lookup"><span data-stu-id="9c81d-111">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.</span></span> <span data-ttu-id="9c81d-112">Daha fazla bilgi için [Kod Parçacıkları'na](/visualstudio/ide/code-snippets)bakın.</span><span class="sxs-lookup"><span data-stu-id="9c81d-112">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="9c81d-113">Pano'dan <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> görüntü almak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="9c81d-113">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> method to retrieve an image from the Clipboard.</span></span> <span data-ttu-id="9c81d-114">Bu örnek, Pano'yu almadan ve `PictureBox1`atamadan önce Pano'da bir görüntü olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="9c81d-114">This example checks to see if there is an image on the Clipboard before retrieving it and assigning it to `PictureBox1`.</span></span>  
  
 [!code-vb[VbResourceTasks#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#16)]  
  
 <span data-ttu-id="9c81d-115">Bu kod örneği, IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9c81d-115">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="9c81d-116">Kod snippet picker, Windows Forms **Uygulamaları > Pano**bulunur. Daha fazla bilgi için [Kod Parçacıkları'na](/visualstudio/ide/code-snippets)bakın.</span><span class="sxs-lookup"><span data-stu-id="9c81d-116">In the code snippet picker, it is located in **Windows Forms Applications > Clipboard**.For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="9c81d-117">Panoya yerleştirilen öğeler, uygulama kapatıldıktan sonra bile devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="9c81d-117">Items placed on the Clipboard will persist even after the application is shut down.</span></span>  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a><span data-ttu-id="9c81d-118">Panoda depolanan dosya türünü belirleme</span><span class="sxs-lookup"><span data-stu-id="9c81d-118">Determining the type of file stored in the Clipboard</span></span>  

 <span data-ttu-id="9c81d-119">Panodaki veriler metin, ses dosyası veya görüntü gibi çeşitli formlar alabilir.</span><span class="sxs-lookup"><span data-stu-id="9c81d-119">Data on the Clipboard may take a number of different forms, such as text, an audio file, or an image.</span></span> <span data-ttu-id="9c81d-120">Panoda ne tür bir dosya olduğunu belirlemek <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>için , , <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>ve <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c81d-120">In order to determine what sort of file is on the Clipboard, you can use methods such as <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, and <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>.</span></span> <span data-ttu-id="9c81d-121">Denetlemek <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> istediğiniz özel bir biçiminiz varsa yöntem kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9c81d-121">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> method can be used if you have a custom format that you want to check.</span></span>  
  
 <span data-ttu-id="9c81d-122">Panoda `ContainsImage` bulunan verilerin bir görüntü olup olmadığını belirlemek için işlevi kullanın.</span><span class="sxs-lookup"><span data-stu-id="9c81d-122">Use the `ContainsImage` function to determine whether the data contained on the Clipboard is an image.</span></span> <span data-ttu-id="9c81d-123">Aşağıdaki kod, verilerin bir görüntü olup olmadığını denetler ve buna göre raporlar.</span><span class="sxs-lookup"><span data-stu-id="9c81d-123">The following code checks to see whether the data is an image and reports accordingly.</span></span>  
  
 [!code-vb[VbResourceTasks#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#13)]  
  
## <a name="clearing-the-clipboard"></a><span data-ttu-id="9c81d-124">Panoyu Temizleme</span><span class="sxs-lookup"><span data-stu-id="9c81d-124">Clearing the Clipboard</span></span>  

 <span data-ttu-id="9c81d-125">Yöntem <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> Pano'yu temizler.</span><span class="sxs-lookup"><span data-stu-id="9c81d-125">The <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> method clears the Clipboard.</span></span> <span data-ttu-id="9c81d-126">Pano diğer işlemler tarafından paylaşıldığından, temizlemenin bu işlemler üzerinde bir etkisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="9c81d-126">Because the Clipboard is shared by other processes, clearing it may have an impact on those processes.</span></span>  
  
 <span data-ttu-id="9c81d-127">Aşağıdaki kod yöntemin nasıl `Clear` kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9c81d-127">The following code shows how to use the `Clear` method.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#3)]  
  
## <a name="writing-to-the-clipboard"></a><span data-ttu-id="9c81d-128">Panoya Yazma</span><span class="sxs-lookup"><span data-stu-id="9c81d-128">Writing to the Clipboard</span></span>  

 <span data-ttu-id="9c81d-129">Panoya <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> metin yazmak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="9c81d-129">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> method to write text to the Clipboard.</span></span> <span data-ttu-id="9c81d-130">Aşağıdaki kod Panoya "Bu bir test dizesidir" dizesini yazar.</span><span class="sxs-lookup"><span data-stu-id="9c81d-130">The following code writes the string "This is a test string" to the Clipboard.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#1)]  
  
 <span data-ttu-id="9c81d-131">Yöntem, `SetText` <xref:System.Windows.Forms.TextDataFormat>bir tür .</span><span class="sxs-lookup"><span data-stu-id="9c81d-131">The `SetText` method can accept a format parameter that contains a type of <xref:System.Windows.Forms.TextDataFormat>.</span></span> <span data-ttu-id="9c81d-132">Aşağıdaki kod, PANOYA RTF metni olarak "Bu bir test dizesidir" dizesini yazar.</span><span class="sxs-lookup"><span data-stu-id="9c81d-132">The following code writes the string "This is a test string" to the Clipboard as RTF text.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#2)]  
  
 <span data-ttu-id="9c81d-133">Panoya <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> veri yazmak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="9c81d-133">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> method to write data to the Clipboard.</span></span> <span data-ttu-id="9c81d-134">Bu örnek, `DataObject` `dataChunk` panoya özel biçimde `specialFormat`yazar.</span><span class="sxs-lookup"><span data-stu-id="9c81d-134">This example writes the `DataObject` `dataChunk` to the Clipboard in the custom format `specialFormat`.</span></span>  
  
 [!code-vb[VbVbcnMyClipboard#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#7)]  
  
 <span data-ttu-id="9c81d-135">Panoya <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> ses verileri yazmak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="9c81d-135">Use the <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> method to write audio data to the Clipboard.</span></span> <span data-ttu-id="9c81d-136">Bu örnek bayt dizisini `musicReader`oluşturur, `cool.wav` dosyayı içine okur ve panoya yazar.</span><span class="sxs-lookup"><span data-stu-id="9c81d-136">This example creates the byte array `musicReader`, reads the file `cool.wav` into it, and then writes it to the Clipboard.</span></span>  
  
 [!code-vb[VbResourceTasks#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#5)]  
  
> [!IMPORTANT]
> <span data-ttu-id="9c81d-137">Panoya diğer kullanıcılar erişebildiği için, parolalar veya gizli veriler gibi hassas bilgileri depolamak için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="9c81d-137">Because the Clipboard can be accessed by other users, do not use it to store sensitive information, such as passwords or confidential data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c81d-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c81d-138">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>
- [<span data-ttu-id="9c81d-139">Nasıl kullanılır: XML Dosyasından Nesne Verilerini Okuma</span><span class="sxs-lookup"><span data-stu-id="9c81d-139">How to: Read Object Data from an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="9c81d-140">Nasıl kullanılır: Nesne Verilerini XML Dosyasına Yazma</span><span class="sxs-lookup"><span data-stu-id="9c81d-140">How to: Write Object Data to an XML File</span></span>](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
