---
title: Office programlama- C# programlama kılavuzunda adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanma
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
ms.openlocfilehash: d7efd13f26912f8cd944bcbc5568e9bbca92c3a0
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970500"
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a><span data-ttu-id="d9f7f-102">Office Programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="d9f7f-102">How to use named and optional arguments in Office programming (C# Programming Guide)</span></span>

<span data-ttu-id="d9f7f-103">Adlandırılmış bağımsız değişkenler ve isteğe bağlı bağımsız değişkenler C# , 4 ' te tanıtılan ve C# programlamada kolaylık, esneklik ve okunabilirliği geliştirir.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-103">Named arguments and optional arguments, introduced in C# 4, enhance convenience, flexibility, and readability in C# programming.</span></span> <span data-ttu-id="d9f7f-104">Ayrıca, bu özellikler Microsoft Office Automation API 'Leri gibi COM arabirimlerine erişimi büyük ölçüde kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-104">In addition, these features greatly facilitate access to COM interfaces such as the Microsoft Office automation APIs.</span></span>

<span data-ttu-id="d9f7f-105">Aşağıdaki örnekte, [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) yönteminin sütun ve satır sayısı, biçimlendirme, kenarlık, yazı tipi ve renkler gibi bir tablonun özelliklerini temsil eden on altı parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-105">In the following example, method [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) has sixteen parameters that represent characteristics of a table, such as number of columns and rows, formatting, borders, fonts, and colors.</span></span> <span data-ttu-id="d9f7f-106">Tüm on altı parametresi isteğe bağlıdır, çünkü çoğu zaman belirli değerleri belirtmek istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-106">All sixteen parameters are optional, because most of the time you do not want to specify particular values for all of them.</span></span> <span data-ttu-id="d9f7f-107">Ancak, adlandırılmış ve isteğe bağlı bağımsız değişkenler olmadan her bir parametre için bir değer veya yer tutucu değeri sağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-107">However, without named and optional arguments, a value or a placeholder value has to be provided for each parameter.</span></span> <span data-ttu-id="d9f7f-108">Adlandırılmış ve isteğe bağlı bağımsız değişkenlerle, yalnızca projeniz için gerekli olan parametrelerin değerlerini belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-108">With named and optional arguments, you specify values only for the parameters that are required for your project.</span></span>

<span data-ttu-id="d9f7f-109">Bu yordamları gerçekleştirmek için bilgisayarınızda Microsoft Office Word yüklü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-109">You must have Microsoft Office Word installed on your computer to complete these procedures.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a><span data-ttu-id="d9f7f-110">Yeni bir konsol uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d9f7f-110">To create a new console application</span></span>

1. <span data-ttu-id="d9f7f-111">Visual Studio 'Yu başlatın.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-111">Start Visual Studio.</span></span>

2. <span data-ttu-id="d9f7f-112">**Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-112">On the **File** menu, point to **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="d9f7f-113">**Şablonlar kategorileri** bölmesinde, **görsel C#** ' i genişletin ve ardından **Windows**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-113">In the **Templates Categories** pane, expand **Visual C#**, and then click **Windows**.</span></span>

4. <span data-ttu-id="d9f7f-114">**.NET Framework 4** ' ün **hedef çerçeve** kutusunda göründüğünden emin olmak için **Şablonlar** bölmesinin üst kısmına bakın.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-114">Look in the top of the **Templates** pane to make sure that **.NET Framework 4** appears in the **Target Framework** box.</span></span>

5. <span data-ttu-id="d9f7f-115">**Şablonlar** bölmesinde **konsol uygulaması**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-115">In the **Templates** pane, click **Console Application**.</span></span>

6. <span data-ttu-id="d9f7f-116">**Ad** alanına projeniz için bir ad yazın.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-116">Type a name for your project in the **Name** field.</span></span>

7. <span data-ttu-id="d9f7f-117">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-117">Click **OK**.</span></span>

     <span data-ttu-id="d9f7f-118">Yeni proje **Çözüm Gezgini**görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-118">The new project appears in **Solution Explorer**.</span></span>

## <a name="to-add-a-reference"></a><span data-ttu-id="d9f7f-119">Başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="d9f7f-119">To add a reference</span></span>

1. <span data-ttu-id="d9f7f-120">**Çözüm Gezgini**, projenizin adına sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-120">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="d9f7f-121">**Başvuru Ekle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-121">The **Add Reference** dialog box appears.</span></span>

2. <span data-ttu-id="d9f7f-122">**.Net** sayfasında, **bileşen adı** listesinde **Microsoft. Office. Interop. Word** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-122">On the **.NET** page, select **Microsoft.Office.Interop.Word** in the **Component Name** list.</span></span>

3. <span data-ttu-id="d9f7f-123">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-123">Click **OK**.</span></span>

## <a name="to-add-necessary-using-directives"></a><span data-ttu-id="d9f7f-124">Gerekli yönergeleri kullanarak ekleme</span><span class="sxs-lookup"><span data-stu-id="d9f7f-124">To add necessary using directives</span></span>

1. <span data-ttu-id="d9f7f-125">**Çözüm Gezgini**, *program.cs* dosyasına sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-125">In **Solution Explorer**, right-click the *Program.cs* file and then click **View Code**.</span></span>

2. <span data-ttu-id="d9f7f-126">Aşağıdaki `using` yönergelerini kod dosyasının en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d9f7f-126">Add the following `using` directives to the top of the code file:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#4)]

## <a name="to-display-text-in-a-word-document"></a><span data-ttu-id="d9f7f-127">Bir Word belgesinde metin göstermek için</span><span class="sxs-lookup"><span data-stu-id="d9f7f-127">To display text in a Word document</span></span>

1. <span data-ttu-id="d9f7f-128">*Program.cs*içindeki `Program` sınıfında, bir Word uygulaması ve Word belgesi oluşturmak için aşağıdaki yöntemi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-128">In the `Program` class in *Program.cs*, add the following method to create a Word application and a Word document.</span></span> <span data-ttu-id="d9f7f-129">[Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) yönteminde dört isteğe bağlı parametre vardır.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-129">The [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) method has four optional parameters.</span></span> <span data-ttu-id="d9f7f-130">Bu örnek, varsayılan değerlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-130">This example uses their default values.</span></span> <span data-ttu-id="d9f7f-131">Bu nedenle, çağırma ifadesinde herhangi bir bağımsız değişken gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-131">Therefore, no arguments are necessary in the calling statement.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#6)]

2. <span data-ttu-id="d9f7f-132">İçinde metnin nerede görüntüleneceğini ve hangi metnin görüntüleneceğini tanımlamak için yönteminin sonuna aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d9f7f-132">Add the following code at the end of the method to define where to display text in the document, and what text to display:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#7)]

## <a name="to-run-the-application"></a><span data-ttu-id="d9f7f-133">Uygulamayı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="d9f7f-133">To run the application</span></span>

1. <span data-ttu-id="d9f7f-134">Aşağıdaki ifadeyi Main öğesine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d9f7f-134">Add the following statement to Main:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#8)]

2. <span data-ttu-id="d9f7f-135">Projeyi çalıştırmak için <kbd>CTRL</kbd>+<kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-135">Press <kbd>CTRL</kbd>+<kbd>F5</kbd> to run the project.</span></span> <span data-ttu-id="d9f7f-136">Belirtilen metni içeren bir Word belgesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-136">A Word document appears that contains the specified text.</span></span>

## <a name="to-change-the-text-to-a-table"></a><span data-ttu-id="d9f7f-137">Metni bir tabloya dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="d9f7f-137">To change the text to a table</span></span>
  
1. <span data-ttu-id="d9f7f-138">Metni bir tabloya kapsamak için `ConvertToTable` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-138">Use the `ConvertToTable` method to enclose the text in a table.</span></span> <span data-ttu-id="d9f7f-139">Yönteminde on altı isteğe bağlı parametre vardır.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-139">The method has sixteen optional parameters.</span></span> <span data-ttu-id="d9f7f-140">IntelliSense, aşağıdaki çizimde gösterildiği gibi isteğe bağlı parametreleri köşeli ayraç içine alır.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-140">IntelliSense encloses optional parameters in brackets, as shown in the following illustration.</span></span>

     ![ConvertToTable yöntemi için parametrelerin listesi](./media/how-to-use-named-and-optional-arguments-in-office-programming/convert-table-parameters.png)

     <span data-ttu-id="d9f7f-142">Adlandırılmış ve isteğe bağlı bağımsız değişkenler yalnızca değiştirmek istediğiniz parametrelerin değerlerini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-142">Named and optional arguments enable you to specify values for only the parameters that you want to change.</span></span> <span data-ttu-id="d9f7f-143">Basit bir tablo oluşturmak için `DisplayInWord` yönteminin sonuna aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-143">Add the following code to the end of method `DisplayInWord` to create a simple table.</span></span> <span data-ttu-id="d9f7f-144">Bağımsız değişkeni, `range` içindeki metin dizesindeki virgüllerin tablonun hücrelerini ayırabelirtir.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-144">The argument specifies that the commas in the text string in `range` separate the cells of the table.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#9)]

     <span data-ttu-id="d9f7f-145">Önceki sürümlerinde C#, aşağıdaki kodda gösterildiği gibi, `ConvertToTable` çağrısı her parametre için bir başvuru bağımsız değişkeni gerektirir:</span><span class="sxs-lookup"><span data-stu-id="d9f7f-145">In earlier versions of C#, the call to `ConvertToTable` requires a reference argument for each parameter, as shown in the following code:</span></span>
  
     [!code-csharp[csProgGuideNamedAndOptional#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#14)]

2. <span data-ttu-id="d9f7f-146">Projeyi çalıştırmak için <kbd>CTRL</kbd>+<kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-146">Press <kbd>CTRL</kbd>+<kbd>F5</kbd> to run the project.</span></span>

## <a name="to-experiment-with-other-parameters"></a><span data-ttu-id="d9f7f-147">Diğer parametrelerle denemek için</span><span class="sxs-lookup"><span data-stu-id="d9f7f-147">To experiment with other parameters</span></span>

1. <span data-ttu-id="d9f7f-148">Tabloyu tek bir sütuna ve üç satıra sahip olacak şekilde değiştirmek için `DisplayInWord` son satırını aşağıdaki deyimle değiştirin ve ardından <kbd>CTRL</kbd>+<kbd>F5</kbd>yazın.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-148">To change the table so that it has one column and three rows, replace the last line in `DisplayInWord` with the following statement and then type <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span>  

     [!code-csharp[csProgGuideNamedAndOptional#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#10)]

2. <span data-ttu-id="d9f7f-149">Tablo için önceden tanımlanmış bir biçim belirtmek üzere `DisplayInWord` son satırını aşağıdaki deyimle değiştirin ve ardından <kbd>CTRL</kbd>+<kbd>F5</kbd>yazın.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-149">To specify a predefined format for the table, replace the last line in `DisplayInWord` with the following statement and then type <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span> <span data-ttu-id="d9f7f-150">Biçim, [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) sabitlerinden herhangi biri olabilir.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-150">The format can be any of the [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) constants.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#11)]

## <a name="example"></a><span data-ttu-id="d9f7f-151">Örnek</span><span class="sxs-lookup"><span data-stu-id="d9f7f-151">Example</span></span>

<span data-ttu-id="d9f7f-152">Aşağıdaki kod tam örneği içerir:</span><span class="sxs-lookup"><span data-stu-id="d9f7f-152">The following code includes the full example:</span></span>

 [!code-csharp[csProgGuideNamedAndOptional#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#12)]

## <a name="see-also"></a><span data-ttu-id="d9f7f-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9f7f-153">See also</span></span>

- [<span data-ttu-id="d9f7f-154">Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="d9f7f-154">Named and Optional Arguments</span></span>](./named-and-optional-arguments.md)
