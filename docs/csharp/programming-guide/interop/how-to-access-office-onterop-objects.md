---
title: Office birlikte çalışma nesnelerine erişme-C# Programlama Kılavuzu
description: Office API nesnelerine erişimi kolaylaştıran C# özellikleri hakkında bilgi edinin. Excel çalışma sayfası oluşturan ve görüntüleyen bir kod yazmak için yeni özellikleri kullanın.
ms.date: 07/20/2015
helpviewer_keywords:
- optional parameters [C#], Office programming
- named and optional arguments [C#], Office programming
- dynamic [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
- Office programming [C#]
ms.assetid: 041b25c2-3512-4e0f-a4ea-ceb2999e4d5e
ms.openlocfilehash: 6c2c49a9fd55c406b69c02586a9b0e4a1d16ccd4
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103479930"
---
# <a name="how-to-access-office-interop-objects-c-programming-guide"></a><span data-ttu-id="590dc-104">Office birlikte çalışma nesnelerine erişim (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="590dc-104">How to access Office interop objects (C# Programming Guide)</span></span>

<span data-ttu-id="590dc-105">C# ' de Office API nesnelerine erişimi basitleştiren özellikler vardır.</span><span class="sxs-lookup"><span data-stu-id="590dc-105">C# has features that simplify access to Office API objects.</span></span> <span data-ttu-id="590dc-106">Yeni özellikler adlandırılmış ve isteğe bağlı bağımsız değişkenler, yeni bir tür adı `dynamic` ve com yöntemlerindeki başvuru parametrelerine bağımsız değişkenleri değer parametreleri gibi geçirme özelliği içerir.</span><span class="sxs-lookup"><span data-stu-id="590dc-106">The new features include named and optional arguments, a new type called `dynamic`, and the ability to pass arguments to reference parameters in COM methods as if they were value parameters.</span></span>

<span data-ttu-id="590dc-107">Bu konu başlığında, Microsoft Office bir Excel çalışma sayfası oluşturan ve görüntüleyen kod yazmak için yeni özellikleri kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="590dc-107">In this topic you will use the new features to write code that creates and displays a Microsoft Office Excel worksheet.</span></span> <span data-ttu-id="590dc-108">Daha sonra, Excel çalışma sayfasına bağlı bir simge içeren bir Office Word belgesi eklemek için kod yazacaksınız.</span><span class="sxs-lookup"><span data-stu-id="590dc-108">You will then write code to add an Office Word document that contains an icon that is linked to the Excel worksheet.</span></span>

<span data-ttu-id="590dc-109">Bu yönergeyi tamamlamak için, bilgisayarınızda yüklü Microsoft Office Excel 2007 ve Microsoft Office Word 2007 veya sonraki sürümlerin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="590dc-109">To complete this walkthrough, you must have Microsoft Office Excel 2007 and Microsoft Office Word 2007, or later versions, installed on your computer.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a><span data-ttu-id="590dc-110">Yeni bir konsol uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="590dc-110">To create a new console application</span></span>

1. <span data-ttu-id="590dc-111">Visual Studio’yu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="590dc-111">Start Visual Studio.</span></span>

2. <span data-ttu-id="590dc-112">**Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="590dc-112">On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="590dc-113">**Yeni Proje** iletişim kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="590dc-113">The **New Project** dialog box appears.</span></span>

3. <span data-ttu-id="590dc-114">**Yüklü şablonlar** bölmesinde, **Visual C#** öğesini genişletin ve ardından **Windows**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="590dc-114">In the **Installed Templates** pane, expand **Visual C#**, and then click **Windows**.</span></span>

4. <span data-ttu-id="590dc-115">**.NET Framework 4** ' ün (veya sonraki bir sürüm) hedef çerçeve olarak seçildiğinden emin olmak Için **Yeni proje** iletişim kutusunun üst kısmına bakın.</span><span class="sxs-lookup"><span data-stu-id="590dc-115">Look at the top of the **New Project** dialog box to make sure that **.NET Framework 4** (or later version) is selected as a target framework.</span></span>

5. <span data-ttu-id="590dc-116">**Şablonlar** bölmesinde **konsol uygulaması**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="590dc-116">In the **Templates** pane, click **Console Application**.</span></span>

6. <span data-ttu-id="590dc-117">**Ad** alanına projeniz için bir ad yazın.</span><span class="sxs-lookup"><span data-stu-id="590dc-117">Type a name for your project in the **Name** field.</span></span>

7. <span data-ttu-id="590dc-118">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="590dc-118">Click **OK**.</span></span>

     <span data-ttu-id="590dc-119">Yeni proje **Çözüm Gezgini** görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="590dc-119">The new project appears in **Solution Explorer**.</span></span>

## <a name="to-add-references"></a><span data-ttu-id="590dc-120">Başvuru eklemek için</span><span class="sxs-lookup"><span data-stu-id="590dc-120">To add references</span></span>

1. <span data-ttu-id="590dc-121">**Çözüm Gezgini**, projenizin adına sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="590dc-121">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="590dc-122">**Başvuru Ekle** iletişim kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="590dc-122">The **Add Reference** dialog box appears.</span></span>

2. <span data-ttu-id="590dc-123">**Derlemeler** sayfasında, **bileşen adı** listesinde **Microsoft. Office. Interop. Word** ' ü seçin ve ardından CTRL tuşunu basılı tutarak **Microsoft. Office. Interop. Excel**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="590dc-123">On the **Assemblies**  page, select **Microsoft.Office.Interop.Word** in the **Component Name** list, and then hold down the CTRL key and select **Microsoft.Office.Interop.Excel**.</span></span>  <span data-ttu-id="590dc-124">Derlemeleri görmüyorsanız bunların yüklendiğinden ve görüntülendiğinden emin olmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="590dc-124">If you do not see the assemblies, you may need to ensure they are installed and displayed.</span></span> <span data-ttu-id="590dc-125">Bkz. [nasıl yapılır: Office birincil birlikte çalışma derlemelerini yüklemek](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies).</span><span class="sxs-lookup"><span data-stu-id="590dc-125">See [How to: Install Office Primary Interop Assemblies](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies).</span></span>

3. <span data-ttu-id="590dc-126">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="590dc-126">Click **OK**.</span></span>

## <a name="to-add-necessary-using-directives"></a><span data-ttu-id="590dc-127">Gerekli yönergeleri kullanarak ekleme</span><span class="sxs-lookup"><span data-stu-id="590dc-127">To add necessary using directives</span></span>

1. <span data-ttu-id="590dc-128">**Çözüm Gezgini**, *program.cs* dosyasına sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="590dc-128">In **Solution Explorer**, right-click the *Program.cs* file and then click **View Code**.</span></span>

2. <span data-ttu-id="590dc-129">Aşağıdaki `using` yönergeleri kod dosyasının en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="590dc-129">Add the following `using` directives to the top of the code file:</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#1)]

## <a name="to-create-a-list-of-bank-accounts"></a><span data-ttu-id="590dc-130">Banka hesaplarının bir listesini oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="590dc-130">To create a list of bank accounts</span></span>

1. <span data-ttu-id="590dc-131">Aşağıdaki sınıf tanımını sınıfının altına **program.cs** yapıştırın `Program` .</span><span class="sxs-lookup"><span data-stu-id="590dc-131">Paste the following class definition into **Program.cs**, under the `Program` class.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#2)]

2. <span data-ttu-id="590dc-132">`Main`İki hesap içeren bir liste oluşturmak için yöntemine aşağıdaki kodu ekleyin `bankAccounts` .</span><span class="sxs-lookup"><span data-stu-id="590dc-132">Add the following code to the `Main` method to create a `bankAccounts` list that contains two accounts.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#3)]

## <a name="to-declare-a-method-that-exports-account-information-to-excel"></a><span data-ttu-id="590dc-133">Excel 'e hesap bilgilerini veren bir yöntem bildirmek için</span><span class="sxs-lookup"><span data-stu-id="590dc-133">To declare a method that exports account information to Excel</span></span>

1. <span data-ttu-id="590dc-134">`Program`Bir Excel çalışma sayfası ayarlamak için aşağıdaki yöntemi sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="590dc-134">Add the following method to the `Program` class to set up an Excel worksheet.</span></span>

     <span data-ttu-id="590dc-135">Yöntemin <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> belirli bir şablonu belirtmek için isteğe bağlı bir parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="590dc-135">Method <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> has an optional parameter for specifying a particular template.</span></span> <span data-ttu-id="590dc-136">C# 4 ' te yeni olan isteğe bağlı parametreler, parametrenin varsayılan değerini kullanmak istiyorsanız bu parametreye ilişkin bağımsız değişkeni atlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="590dc-136">Optional parameters, new in C# 4, enable you to omit the argument for that parameter if you want to use the parameter's default value.</span></span> <span data-ttu-id="590dc-137">Aşağıdaki kodda bir bağımsız değişken gönderilmediğinden, `Add` varsayılan şablonu kullanır ve yeni bir çalışma kitabı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="590dc-137">Because no argument is sent in the following code, `Add` uses the default template and creates a new workbook.</span></span> <span data-ttu-id="590dc-138">C# ' nin önceki sürümlerindeki denk ifade, bir yer tutucu bağımsız değişkeni gerektirir: `ExcelApp.Workbooks.Add(Type.Missing)` .</span><span class="sxs-lookup"><span data-stu-id="590dc-138">The equivalent statement in earlier versions of C# requires a placeholder argument: `ExcelApp.Workbooks.Add(Type.Missing)`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#4)]

2. <span data-ttu-id="590dc-139">Aşağıdaki kodu sonuna ekleyin `DisplayInExcel` .</span><span class="sxs-lookup"><span data-stu-id="590dc-139">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="590dc-140">Kod, çalışma sayfasının ilk satırının ilk iki sütununa değer ekler.</span><span class="sxs-lookup"><span data-stu-id="590dc-140">The code inserts values into the first two columns of the first row of the worksheet.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#5)]

3. <span data-ttu-id="590dc-141">Aşağıdaki kodu sonuna ekleyin `DisplayInExcel` .</span><span class="sxs-lookup"><span data-stu-id="590dc-141">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="590dc-142">`foreach`Döngü, hesap listesindeki bilgileri, çalışma sayfasının Art arda gelen satırlarının ilk iki sütununa yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="590dc-142">The `foreach` loop puts the information from the list of accounts into the first two columns of successive rows of the worksheet.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#7)]

4. <span data-ttu-id="590dc-143">`DisplayInExcel`Sütunun genişliğini içeriğe sığacak şekilde ayarlamak için aşağıdaki kodu sonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="590dc-143">Add the following code at the end of `DisplayInExcel` to adjust the column widths to fit the content.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#13)]

     <span data-ttu-id="590dc-144">Önceki C# sürümleri bu işlemler için açık atama gerektirir çünkü `ExcelApp.Columns[1]` bir `Object` , ve bir `AutoFit` Excel <xref:Microsoft.Office.Interop.Excel.Range> yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="590dc-144">Earlier versions of C# require explicit casting for these operations because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel <xref:Microsoft.Office.Interop.Excel.Range> method.</span></span> <span data-ttu-id="590dc-145">Aşağıdaki satırlarda atama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="590dc-145">The following lines show the casting.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

     <span data-ttu-id="590dc-146">C# 4 ve sonraki sürümleri, `Object` `dynamic` Derleme [**EmbedInteropTypes**](../../language-reference/compiler-options/inputs.md#embedinteroptypes) derleyici seçeneği tarafından başvuruluyorsa veya equivalently, Excel **birlikte çalışma türleri** özelliği true olarak ayarlandıysa, döndürülen öğesini otomatik olarak dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="590dc-146">C# 4, and later versions, converts the returned `Object` to `dynamic` automatically if the assembly is referenced by the [**EmbedInteropTypes**](../../language-reference/compiler-options/inputs.md#embedinteroptypes) compiler option or, equivalently, if the Excel **Embed Interop Types** property is set to true.</span></span> <span data-ttu-id="590dc-147">True, bu özellik için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="590dc-147">True is the default value for this property.</span></span>

## <a name="to-run-the-project"></a><span data-ttu-id="590dc-148">Projeyi çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="590dc-148">To run the project</span></span>

1. <span data-ttu-id="590dc-149">Aşağıdaki satırı sonuna ekleyin `Main` .</span><span class="sxs-lookup"><span data-stu-id="590dc-149">Add the following line at the end of `Main`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#8)]

2. <span data-ttu-id="590dc-150">CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="590dc-150">Press CTRL+F5.</span></span>

     <span data-ttu-id="590dc-151">İki hesaptan gelen verileri içeren bir Excel çalışma sayfası görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="590dc-151">An Excel worksheet appears that contains the data from the two accounts.</span></span>

## <a name="to-add-a-word-document"></a><span data-ttu-id="590dc-152">Word belgesi eklemek için</span><span class="sxs-lookup"><span data-stu-id="590dc-152">To add a Word document</span></span>

1. <span data-ttu-id="590dc-153">C# 4 ve sonraki sürümlerin, Office programlama 'yi geliştiren ek yollarını göstermek için aşağıdaki kod bir Word uygulaması açar ve Excel çalışma sayfasına bağlanan bir simge oluşturur.</span><span class="sxs-lookup"><span data-stu-id="590dc-153">To illustrate additional ways in which C# 4, and later versions, enhances Office programming, the following code opens a Word application and creates an icon that links to the Excel worksheet.</span></span>

     <span data-ttu-id="590dc-154">`CreateIconInWordDoc`Daha sonra bu adımda sunulan yöntemi `Program` sınıfına yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="590dc-154">Paste method `CreateIconInWordDoc`, provided later in this step, into the `Program` class.</span></span> <span data-ttu-id="590dc-155">`CreateIconInWordDoc` , ve için metot çağrılarının karmaşıklığını azaltmak için adlandırılmış ve isteğe bağlı bağımsız değişkenleri <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> kullanır <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A> .</span><span class="sxs-lookup"><span data-stu-id="590dc-155">`CreateIconInWordDoc` uses named and optional arguments to reduce the complexity of the method calls to <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> and <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>.</span></span> <span data-ttu-id="590dc-156">Bu çağrılar, C# 4 ' te sunulan ve başvuru parametrelerine sahip COM yöntemlerine yapılan çağrıları kolaylaştıran iki yeni özelliği dahil ediyor.</span><span class="sxs-lookup"><span data-stu-id="590dc-156">These calls incorporate two other new features introduced in C# 4 that simplify calls to COM methods that have reference parameters.</span></span> <span data-ttu-id="590dc-157">İlk olarak, başvuru parametrelerine bağımsız değişkenleri değer parametreleriniz gibi gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="590dc-157">First, you can send arguments to the reference parameters as if they were value parameters.</span></span> <span data-ttu-id="590dc-158">Diğer bir deyişle, her başvuru parametresi için bir değişken oluşturmadan doğrudan değerleri gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="590dc-158">That is, you can send values directly, without creating a variable for each reference parameter.</span></span> <span data-ttu-id="590dc-159">Derleyici bağımsız değişken değerlerini tutacak geçici değişkenler oluşturur ve çağrıdan geri döndüğünüzde değişkenleri atar.</span><span class="sxs-lookup"><span data-stu-id="590dc-159">The compiler generates temporary variables to hold the argument values, and discards the variables when you return from the call.</span></span> <span data-ttu-id="590dc-160">İkinci olarak, `ref` bağımsız değişken listesindeki anahtar sözcüğü atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="590dc-160">Second, you can omit the `ref` keyword in the argument list.</span></span>

     <span data-ttu-id="590dc-161">`Add`Yönteminin tümü isteğe bağlı dört başvuru parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="590dc-161">The `Add` method has four reference parameters, all of which are optional.</span></span> <span data-ttu-id="590dc-162">C# 4,0 ve sonraki sürümlerinde, varsayılan değerlerini kullanmak istiyorsanız parametrelerin herhangi biri veya tümü için bağımsız değişkenleri atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="590dc-162">In C# 4.0 and later versions, you can omit arguments for any or all of the parameters if you want to use their default values.</span></span> <span data-ttu-id="590dc-163">C# 3,0 ve önceki sürümlerinde, her bir parametre için bir bağımsız değişken sağlanmalı ve parametreler başvuru parametreleri olduğundan bağımsız değişken bir değişken olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="590dc-163">In C# 3.0 and earlier versions, an argument must be provided for each parameter, and the argument must be a variable because the parameters are reference parameters.</span></span>

     <span data-ttu-id="590dc-164">`PasteSpecial`Yöntemi panonun içeriğini ekler.</span><span class="sxs-lookup"><span data-stu-id="590dc-164">The `PasteSpecial` method inserts the contents of the Clipboard.</span></span> <span data-ttu-id="590dc-165">Yönteminde, hepsi isteğe bağlı yedi başvuru parametresi vardır.</span><span class="sxs-lookup"><span data-stu-id="590dc-165">The method has seven reference parameters, all of which are optional.</span></span> <span data-ttu-id="590dc-166">Aşağıdaki kod, bu iki öğenin bağımsız değişkenlerini belirtir: `Link` , pano içeriklerinin kaynağına bir bağlantı oluşturmak ve `DisplayAsIcon` bağlantıyı bir simge olarak göstermek için.</span><span class="sxs-lookup"><span data-stu-id="590dc-166">The following code specifies arguments for two of them: `Link`, to create a link to the source of the Clipboard contents, and `DisplayAsIcon`, to display the link as an icon.</span></span> <span data-ttu-id="590dc-167">C# 4,0 ve sonraki sürümlerinde, bu ikisi için adlandırılmış bağımsız değişkenleri kullanabilir ve diğerlerini atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="590dc-167">In C# 4.0 and later versions, you can use named arguments for those two and omit the others.</span></span> <span data-ttu-id="590dc-168">Bunların başvuru parametreleri olmasına karşın, `ref` anahtar sözcüğünü kullanmanız veya bağımsız değişken olarak gönderilmek üzere değişkenler oluşturmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="590dc-168">Although these are reference parameters, you do not have to use the `ref` keyword, or to create variables to send in as arguments.</span></span> <span data-ttu-id="590dc-169">Değerleri doğrudan gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="590dc-169">You can send the values directly.</span></span> <span data-ttu-id="590dc-170">C# 3,0 ve önceki sürümlerde, her başvuru parametresi için bir değişken bağımsız değişkeni sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="590dc-170">In C# 3.0 and earlier versions, you must supply a variable argument for each reference parameter.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#9)]

     <span data-ttu-id="590dc-171">C# 3,0 ve önceki dil sürümlerinde, aşağıdaki daha karmaşık kod gereklidir.</span><span class="sxs-lookup"><span data-stu-id="590dc-171">In C# 3.0 and earlier versions of the language, the following more complex code is required.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#10)]

2. <span data-ttu-id="590dc-172">Aşağıdaki ifadesini sonuna ekleyin `Main` .</span><span class="sxs-lookup"><span data-stu-id="590dc-172">Add the following statement at the end of `Main`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#11)]

3. <span data-ttu-id="590dc-173">Aşağıdaki ifadesini sonuna ekleyin `DisplayInExcel` .</span><span class="sxs-lookup"><span data-stu-id="590dc-173">Add the following statement at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="590dc-174">`Copy`Yöntemi, çalışma sayfasını panoya ekler.</span><span class="sxs-lookup"><span data-stu-id="590dc-174">The `Copy` method adds the worksheet to the Clipboard.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#12)]

4. <span data-ttu-id="590dc-175">CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="590dc-175">Press CTRL+F5.</span></span>

     <span data-ttu-id="590dc-176">Bir simge içeren bir Word belgesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="590dc-176">A Word document appears that contains an icon.</span></span> <span data-ttu-id="590dc-177">Çalışma sayfasını ön plana getirmek için simgeye çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="590dc-177">Double-click the icon to bring the worksheet to the foreground.</span></span>

## <a name="to-set-the-embed-interop-types-property"></a><span data-ttu-id="590dc-178">Birlikte çalışma türlerini katıştır özelliğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="590dc-178">To set the Embed Interop Types property</span></span>

1. <span data-ttu-id="590dc-179">Çalışma zamanında birincil birlikte çalışma derlemesi (PIA) gerektirmeyen bir COM türünü çağırdığınızda ek geliştirmeler yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="590dc-179">Additional enhancements are possible when you call a COM type that does not require a primary interop assembly (PIA) at run time.</span></span> <span data-ttu-id="590dc-180">PIA 'ların bağımlılığını kaldırmak sürüm bağımsızlık ve daha kolay dağıtıma neden olur.</span><span class="sxs-lookup"><span data-stu-id="590dc-180">Removing the dependency on PIAs results in version independence and easier deployment.</span></span> <span data-ttu-id="590dc-181">PIA olmadan programlamanın avantajları hakkında daha fazla bilgi için bkz. [Izlenecek yol: yönetilen derlemelerden tür ekleme](../../../standard/assembly/embed-types-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="590dc-181">For more information about the advantages of programming without PIAs, see [Walkthrough: Embedding Types from Managed Assemblies](../../../standard/assembly/embed-types-visual-studio.md).</span></span>

     <span data-ttu-id="590dc-182">Ayrıca, gerekli ve COM yöntemleri tarafından döndürülen türler yerine türü kullanılarak gösterilebildiğinden programlama daha kolay olur `dynamic` `Object` .</span><span class="sxs-lookup"><span data-stu-id="590dc-182">In addition, programming is easier because the types that are required and returned by COM methods can be represented by using the type `dynamic` instead of `Object`.</span></span> <span data-ttu-id="590dc-183">Türü olan değişkenler `dynamic` çalışma zamanına kadar değerlendirilmez ve bu da açık atama gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="590dc-183">Variables that have type `dynamic` are not evaluated until run time, which eliminates the need for explicit casting.</span></span> <span data-ttu-id="590dc-184">Daha fazla bilgi için bkz. [dinamik tür kullanımı](../types/using-type-dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="590dc-184">For more information, see [Using Type dynamic](../types/using-type-dynamic.md).</span></span>

     <span data-ttu-id="590dc-185">C# 4 ' te, PIA kullanımı yerine tür bilgilerini katıştırma varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="590dc-185">In C# 4, embedding type information instead of using PIAs is default behavior.</span></span> <span data-ttu-id="590dc-186">Bu varsayılan nedenle, açık atama gerekli olmadığından önceki örneklerden bazıları basitleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="590dc-186">Because of that default, several of the previous examples are simplified because explicit casting is not required.</span></span> <span data-ttu-id="590dc-187">Örneğin, içindeki bildirimi yerine `worksheet` `DisplayInExcel` olarak yazılır `Excel._Worksheet workSheet = excelApp.ActiveSheet` `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet` .</span><span class="sxs-lookup"><span data-stu-id="590dc-187">For example, the declaration of `worksheet` in `DisplayInExcel` is written as `Excel._Worksheet workSheet = excelApp.ActiveSheet` rather than `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`.</span></span> <span data-ttu-id="590dc-188">Aynı yöntemde yapılan çağrılar, `AutoFit` varsayılan değer olmadan açık atama gerektirir, çünkü `ExcelApp.Columns[1]` bir `Object` , döndürür ve `AutoFit` bir Excel yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="590dc-188">The calls to `AutoFit` in the same method also would require explicit casting without the default, because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel  method.</span></span> <span data-ttu-id="590dc-189">Aşağıdaki kod, atama gösterir.</span><span class="sxs-lookup"><span data-stu-id="590dc-189">The following code shows the casting.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

2. <span data-ttu-id="590dc-190">Tür bilgilerini gömmek yerine varsayılan değer değiştirmek ve PIA 'leri kullanmak için, **Çözüm Gezgini** ' deki **Başvurular** düğümünü genişletin ve ardından **Microsoft. Office. Interop. Excel** veya **Microsoft. Office. Interop. Word** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="590dc-190">To change the default and use PIAs instead of embedding type information, expand the **References** node in **Solution Explorer** and then select **Microsoft.Office.Interop.Excel** or **Microsoft.Office.Interop.Word**.</span></span>

3. <span data-ttu-id="590dc-191">**Özellikler** penceresini göremiyorsanız **F4** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="590dc-191">If you cannot see the **Properties** window, press **F4**.</span></span>

4. <span data-ttu-id="590dc-192">Özellik listesine **birlikte çalışma türlerini katıştır** ' ı bulun ve değerini **false** olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="590dc-192">Find **Embed Interop Types** in the list of properties, and change its value to **False**.</span></span> <span data-ttu-id="590dc-193">Equivalently, komut isteminde [**EmbedInteropTypes**](../../language-reference/compiler-options/inputs.md#embedinteroptypes) yerine [**References**](../../language-reference/compiler-options/inputs.md#references) derleyici seçeneğini kullanarak derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="590dc-193">Equivalently, you can compile by using the [**References**](../../language-reference/compiler-options/inputs.md#references) compiler option instead of [**EmbedInteropTypes**](../../language-reference/compiler-options/inputs.md#embedinteroptypes) at a command prompt.</span></span>

## <a name="to-add-additional-formatting-to-the-table"></a><span data-ttu-id="590dc-194">Tabloya ek biçimlendirme eklemek için</span><span class="sxs-lookup"><span data-stu-id="590dc-194">To add additional formatting to the table</span></span>

1. <span data-ttu-id="590dc-195">İçindeki iki çağrısı `AutoFit` `DisplayInExcel` aşağıdaki ifadesiyle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="590dc-195">Replace the two calls to `AutoFit` in `DisplayInExcel` with the following statement.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#15)]

     <span data-ttu-id="590dc-196"><xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A>Yöntemi, hepsi isteğe bağlı yedi değer parametresine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="590dc-196">The <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method has seven value parameters, all of which are optional.</span></span> <span data-ttu-id="590dc-197">Adlandırılmış ve isteğe bağlı bağımsız değişkenler hiçbiri, bazıları veya tümü için bağımsız değişkenler sağlamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="590dc-197">Named and optional arguments enable you to provide arguments for none, some, or all of them.</span></span> <span data-ttu-id="590dc-198">Önceki ifadede, parametrelerden yalnızca biri için bir bağımsız değişken sağlanır `Format` .</span><span class="sxs-lookup"><span data-stu-id="590dc-198">In the previous statement, an argument is supplied for only one of the parameters, `Format`.</span></span> <span data-ttu-id="590dc-199">, `Format` Parametre listesindeki ilk parametre olduğundan, parametre adını belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="590dc-199">Because `Format` is the first parameter in the parameter list, you do not have to provide the parameter name.</span></span> <span data-ttu-id="590dc-200">Ancak, aşağıdaki kodda gösterildiği gibi, deyimin parametre adının dahil edilip edilmediğini anlamak daha kolay olabilir.</span><span class="sxs-lookup"><span data-stu-id="590dc-200">However, the statement might be easier to understand if the parameter name is included, as is shown in the following code.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#16)]

2. <span data-ttu-id="590dc-201">Sonucu görmek için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="590dc-201">Press CTRL+F5 to see the result.</span></span> <span data-ttu-id="590dc-202">Diğer biçimler, <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> numaralandırmada listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="590dc-202">Other formats are listed in the <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> enumeration.</span></span>

3. <span data-ttu-id="590dc-203">Adım 1 ' deki ifadesini, C# 3,0 ve önceki sürümlerde gerekli olan bağımsız değişkenleri gösteren aşağıdaki kodla karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="590dc-203">Compare the statement in step 1 with the following code, which shows the arguments that are required in C# 3.0 and earlier versions.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#17)]

## <a name="example"></a><span data-ttu-id="590dc-204">Örnek</span><span class="sxs-lookup"><span data-stu-id="590dc-204">Example</span></span>

<span data-ttu-id="590dc-205">Aşağıdaki kod, tüm örneği göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="590dc-205">The following code shows the complete example.</span></span>

[!code-csharp[csProgGuideOfficeHowTo#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/walkthrough.cs#18)]

## <a name="see-also"></a><span data-ttu-id="590dc-206">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="590dc-206">See also</span></span>

- <xref:System.Type.Missing?displayProperty=nameWithType>
- [<span data-ttu-id="590dc-207">dynamic</span><span class="sxs-lookup"><span data-stu-id="590dc-207">dynamic</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="590dc-208">Tür dinamiği kullanma</span><span class="sxs-lookup"><span data-stu-id="590dc-208">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="590dc-209">Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="590dc-209">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="590dc-210">Office programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanma</span><span class="sxs-lookup"><span data-stu-id="590dc-210">How to use named and optional arguments in Office programming</span></span>](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
