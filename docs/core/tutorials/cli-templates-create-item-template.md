---
title: Dotnet yeni - .NET Core CLI için bir öğe şablonu oluşturma
description: dotnet yeni komutu için bir öğe şablonu oluşturmayı öğrenin. Öğe şablonları herhangi bir sayıda dosya içerebilir.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 5f4038e863d9bb59df470d3516c08fd2ad29c078
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503560"
---
# <a name="tutorial-create-an-item-template"></a><span data-ttu-id="1bce7-104">Öğretici: Öğe şablonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="1bce7-104">Tutorial: Create an item template</span></span>

<span data-ttu-id="1bce7-105">.NET Core ile, projeler, dosyalar ve hatta kaynaklar oluşturan şablonlar oluşturabilir ve dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bce7-105">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="1bce7-106">Bu öğretici, `dotnet new` komutla birlikte şablon oluşturma, yükleme ve kaldırma yı öğreten bir serinin parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="1bce7-106">This tutorial is part one of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="1bce7-107">Serinin bu bölümünde, nasıl öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="1bce7-107">In this part of the series, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="1bce7-108">Öğe şablonu için sınıf oluşturma</span><span class="sxs-lookup"><span data-stu-id="1bce7-108">Create a class for an item template</span></span>
> * <span data-ttu-id="1bce7-109">Şablon config klasörünü ve dosyasını oluşturma</span><span class="sxs-lookup"><span data-stu-id="1bce7-109">Create the template config folder and file</span></span>
> * <span data-ttu-id="1bce7-110">Dosya yolundan şablon yükleme</span><span class="sxs-lookup"><span data-stu-id="1bce7-110">Install a template from a file path</span></span>
> * <span data-ttu-id="1bce7-111">Öğe şablonu test edin</span><span class="sxs-lookup"><span data-stu-id="1bce7-111">Test an item template</span></span>
> * <span data-ttu-id="1bce7-112">Öğe şablonu kaldırma</span><span class="sxs-lookup"><span data-stu-id="1bce7-112">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1bce7-113">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="1bce7-113">Prerequisites</span></span>

* <span data-ttu-id="1bce7-114">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümler.</span><span class="sxs-lookup"><span data-stu-id="1bce7-114">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
* <span data-ttu-id="1bce7-115">Başvuru makalesini okuyun [Dotnet yeni için özel şablonlar](../tools/custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="1bce7-115">Read the reference article [Custom templates for dotnet new](../tools/custom-templates.md).</span></span>

  <span data-ttu-id="1bce7-116">Başvuru makalesi, şablonlar ve bunların nasıl bir araya getirilenlerle ilgili temel bilgileri açıklar.</span><span class="sxs-lookup"><span data-stu-id="1bce7-116">The reference article explains the basics about templates and how they're put together.</span></span> <span data-ttu-id="1bce7-117">Bu bilgilerin bir kısmı burada yinelenecektir.</span><span class="sxs-lookup"><span data-stu-id="1bce7-117">Some of this information will be reiterated here.</span></span>

* <span data-ttu-id="1bce7-118">Bir terminal açın ve _çalışma\şablonlar_ klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="1bce7-118">Open a terminal and navigate to the _working\templates_ folder.</span></span>

## <a name="create-the-required-folders"></a><span data-ttu-id="1bce7-119">Gerekli klasörleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="1bce7-119">Create the required folders</span></span>

<span data-ttu-id="1bce7-120">Bu seri, şablon kaynağınızın bulunduğu bir "çalışma klasörü" ve şablonlarınızı sınamak için kullanılan bir "test klasörü" kullanır.</span><span class="sxs-lookup"><span data-stu-id="1bce7-120">This series uses a "working folder" where your template source is contained and a "testing folder" used to test your templates.</span></span> <span data-ttu-id="1bce7-121">Çalışma klasörü ve sınayın klasörü aynı üst klasör altında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1bce7-121">The working folder and testing folder should be under the same parent folder.</span></span>

<span data-ttu-id="1bce7-122">İlk olarak, üst klasörü oluşturmak, adı önemli değil.</span><span class="sxs-lookup"><span data-stu-id="1bce7-122">First, create the parent folder, the name does not matter.</span></span> <span data-ttu-id="1bce7-123">Ardından, _çalışma_adlı bir alt klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1bce7-123">Then, create a subfolder named _working_.</span></span> <span data-ttu-id="1bce7-124">_Çalışma_ klasörünün içinde _şablonlar_adlı bir alt klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1bce7-124">Inside of the _working_ folder, create a subfolder named _templates_.</span></span>

<span data-ttu-id="1bce7-125">Ardından, _test_adlı üst klasörün altında bir klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1bce7-125">Next, create a folder under the parent folder named _test_.</span></span> <span data-ttu-id="1bce7-126">Klasör yapısı aşağıdaki gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="1bce7-126">The folder structure should look like the following.</span></span>

```console
parent_folder
├───test
└───working
    └───templates
```

## <a name="create-an-item-template"></a><span data-ttu-id="1bce7-127">Öğe şablonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="1bce7-127">Create an item template</span></span>

<span data-ttu-id="1bce7-128">Öğe şablonu, bir veya daha fazla dosya içeren belirli bir şablon türüdür.</span><span class="sxs-lookup"><span data-stu-id="1bce7-128">An item template is a specific type of template that contains one or more files.</span></span> <span data-ttu-id="1bce7-129">Bu tür şablonlar, config, kod veya çözüm dosyası gibi bir şey oluşturmak istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="1bce7-129">These types of templates are useful when you want to generate something like a config, code, or solution file.</span></span> <span data-ttu-id="1bce7-130">Bu örnekte, dize türüne uzantı yöntemi ekleyen bir sınıf oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="1bce7-130">In this example, you'll create a class that adds an extension method to the string type.</span></span>

<span data-ttu-id="1bce7-131">Terminalinizde, _çalışma\şablonlar_ klasörüne gidin ve _uzantılar_adlı yeni bir alt klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1bce7-131">In your terminal, navigate to the _working\templates_ folder and create a new subfolder named _extensions_.</span></span> <span data-ttu-id="1bce7-132">Klasörü girin.</span><span class="sxs-lookup"><span data-stu-id="1bce7-132">Enter the folder.</span></span>

```console
working
└───templates
    └───extensions
```

<span data-ttu-id="1bce7-133">_CommonExtensions.cs_ adlı yeni bir dosya oluşturun ve sık kullanılan metin düzenleyicisiyle açın.</span><span class="sxs-lookup"><span data-stu-id="1bce7-133">Create a new file named _CommonExtensions.cs_ and open it with your favorite text editor.</span></span> <span data-ttu-id="1bce7-134">Bu sınıf, bir dize içeriğini tersine çeviren adlı `Reverse` bir uzantı yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1bce7-134">This class will provide an extension method named `Reverse` that reverses the contents of a string.</span></span> <span data-ttu-id="1bce7-135">Aşağıdaki kodu yapıştırın ve dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="1bce7-135">Paste in the following code and save the file:</span></span>

```csharp
using System;

namespace System
{
    public static class StringExtensions
    {
        public static string Reverse(this string value)
        {
            var tempArray = value.ToCharArray();
            Array.Reverse(tempArray);
            return new string(tempArray);
        }
    }
}
```

<span data-ttu-id="1bce7-136">Oluşturulan şablonun içeriğine sahip olduğunuza göre, şablonun kök klasöründe şablon config'ini oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1bce7-136">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="1bce7-137">Şablon config oluşturma</span><span class="sxs-lookup"><span data-stu-id="1bce7-137">Create the template config</span></span>

<span data-ttu-id="1bce7-138">Şablonlar .NET Core'da şablonunuzun kökünde bulunan özel bir klasör ve config dosyası tarafından tanınır.</span><span class="sxs-lookup"><span data-stu-id="1bce7-138">Templates are recognized in .NET Core by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="1bce7-139">Bu öğreticide, şablon klasörünüz _çalışma\templates\extensions_adresinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="1bce7-139">In this tutorial, your template folder is located at _working\templates\extensions_.</span></span>

<span data-ttu-id="1bce7-140">Bir şablon oluşturduğunuzda, şablon klasöründeki tüm dosya ve klasörler özel config klasörü dışında şablonun bir parçası olarak dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="1bce7-140">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="1bce7-141">Bu config klasörü _.template.config_olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="1bce7-141">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="1bce7-142">İlk olarak, _.template.config_adlı yeni bir alt klasör oluşturun, girin.</span><span class="sxs-lookup"><span data-stu-id="1bce7-142">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="1bce7-143">Ardından, _template.json_adında yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1bce7-143">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="1bce7-144">Klasör yapınız şu şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="1bce7-144">Your folder structure should look like this:</span></span>

```console
working
└───templates
    └───extensions
        └───.template.config
                template.json
```

<span data-ttu-id="1bce7-145">En sevdiğiniz metin düzenleyicisi ile _template.json'u_ açın ve aşağıdaki JSON koduna yapıştırın ve kaydedin.</span><span class="sxs-lookup"><span data-stu-id="1bce7-145">Open the _template.json_ with your favorite text editor and paste in the following JSON code and save it.</span></span>

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Me",
  "classifications": [ "Common", "Code" ],
  "identity": "ExampleTemplate.StringExtensions",
  "name": "Example templates: string extensions",
  "shortName": "stringext",
  "tags": {
    "language": "C#",
    "type": "item"
  }
}
```

<span data-ttu-id="1bce7-146">Bu config dosyası şablonunuzun tüm ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="1bce7-146">This config file contains all the settings for your template.</span></span> <span data-ttu-id="1bce7-147">Temel ayarları görebilirsiniz, gibi `name` `shortName`ve , ama aynı `tags/type` zamanda ayarlanmış `item`bir değer var.</span><span class="sxs-lookup"><span data-stu-id="1bce7-147">You can see the basic settings, such as `name` and `shortName`, but there's also a `tags/type` value that is set to `item`.</span></span> <span data-ttu-id="1bce7-148">Bu, şablonunuzu öğe şablonu olarak kategorilere ayırıyor.</span><span class="sxs-lookup"><span data-stu-id="1bce7-148">This categorizes your template as an item template.</span></span> <span data-ttu-id="1bce7-149">Oluşturduğunuz şablon türünde herhangi bir kısıtlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="1bce7-149">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="1bce7-150">Ve `item` `project` değerler, kullanıcıların aradıkları şablon türünü kolayca filtreleyebilmeleri için .NET Core'un önerdiği ortak adlardır.</span><span class="sxs-lookup"><span data-stu-id="1bce7-150">The `item` and `project` values are common names that .NET Core recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="1bce7-151">Öğe, `classifications` çalıştırdığınızda `dotnet new` ve şablonların listesini aldığınızda gördüğünüz **etiketler** sütununa temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1bce7-151">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="1bce7-152">Kullanıcılar sınıflandırma etiketlerine göre de arama yapabilir.</span><span class="sxs-lookup"><span data-stu-id="1bce7-152">Users can also search based on classification tags.</span></span> <span data-ttu-id="1bce7-153">.json dosyasındaki `tags` \*özelliği `classifications` etiket listesiyle karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="1bce7-153">Don't confuse the `tags` property in the \*.json file with the `classifications` tags list.</span></span> <span data-ttu-id="1bce7-154">Ne yazık ki benzer adlı iki farklı şey konum.</span><span class="sxs-lookup"><span data-stu-id="1bce7-154">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="1bce7-155">*template.json* dosyası için tam şema [JSON Schema Store'da](http://json.schemastore.org/template)bulunur.</span><span class="sxs-lookup"><span data-stu-id="1bce7-155">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="1bce7-156">*template.json* dosyası hakkında daha fazla bilgi [için, dotnet templating wiki](https://github.com/dotnet/templating/wiki)bakın.</span><span class="sxs-lookup"><span data-stu-id="1bce7-156">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="1bce7-157">Artık geçerli bir _.template.config/template.json_ dosyanız olduğuna göre, şablonunuz yüklenmeye hazırdır.</span><span class="sxs-lookup"><span data-stu-id="1bce7-157">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="1bce7-158">Terminalinizde _uzantılar_ klasörüne gidin ve geçerli klasörde bulunan şablonu yüklemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="1bce7-158">In your terminal, navigate to the  _extensions_ folder and run the following command to install the template located at the current folder:</span></span>

* <span data-ttu-id="1bce7-159">**Windows'da**:`dotnet new -i .\`</span><span class="sxs-lookup"><span data-stu-id="1bce7-159">**On Windows**: `dotnet new -i .\`</span></span>
* <span data-ttu-id="1bce7-160">**Linux veya macOS üzerinde:**`dotnet new -i ./`</span><span class="sxs-lookup"><span data-stu-id="1bce7-160">**On Linux or macOS**: `dotnet new -i ./`</span></span>

<span data-ttu-id="1bce7-161">Bu komut, sizinkini içermesi gereken yüklü şablonlar listesini çıkartır.</span><span class="sxs-lookup"><span data-stu-id="1bce7-161">This command outputs the list of templates installed, which should include yours.</span></span>

```console
C:\working\templates\extensions> dotnet new -i .\
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Example templates: string extensions              stringext             [C#]              Common/Code
Console Application                               console               [C#], F#, VB      Common/Console
Class library                                     classlib              [C#], F#, VB      Common/Library
WPF Application                                   wpf                   [C#], VB          Common/WPF
Windows Forms (WinForms) Application              winforms              [C#], VB          Common/WinForms
Worker Service                                    worker                [C#]              Common/Worker/Web
```

## <a name="test-the-item-template"></a><span data-ttu-id="1bce7-162">Öğe şablonu test edin</span><span class="sxs-lookup"><span data-stu-id="1bce7-162">Test the item template</span></span>

<span data-ttu-id="1bce7-163">Artık yüklü bir öğe şablonu var, test edin.</span><span class="sxs-lookup"><span data-stu-id="1bce7-163">Now that you have an item template installed, test it.</span></span> <span data-ttu-id="1bce7-164">_Test/_ klasöre gidin ve `dotnet new console`yeni bir konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1bce7-164">Navigate to the _test/_ folder and create a new console application with `dotnet new console`.</span></span> <span data-ttu-id="1bce7-165">Bu `dotnet run` komutu ile kolayca test edebilirsiniz çalışan bir proje oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1bce7-165">This generates a working project you can easily test with the `dotnet run` command.</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="1bce7-166">Aşağıdakine benzer çıktı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="1bce7-166">You get output similar to the following.</span></span>

```console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\test\test.csproj...
  Restore completed in 54.82 ms for C:\test\test.csproj.

Restore succeeded.
```

<span data-ttu-id="1bce7-167">Projeyi ile çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1bce7-167">Run the project with.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="1bce7-168">Aşağıdaki çıktıyı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="1bce7-168">You get the following output.</span></span>

```console
Hello World!
```

<span data-ttu-id="1bce7-169">Ardından, `dotnet new stringext` şablondan _CommonExtensions.cs_ oluşturmak için çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1bce7-169">Next, run `dotnet new stringext` to generate the _CommonExtensions.cs_ from the template.</span></span>

```dotnetcli
dotnet new stringext
```

<span data-ttu-id="1bce7-170">Aşağıdaki çıktıyı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="1bce7-170">You get the following output.</span></span>

```console
The template "Example templates: string extensions" was created successfully.
```

<span data-ttu-id="1bce7-171">Şablon tarafından _Program.cs_ sağlanan uzantı `"Hello World"` yöntemiyle dizeyi tersine çevirmek için Program.cs kodu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1bce7-171">Change the code in _Program.cs_ to reverse the `"Hello World"` string with the extension method provided by the template.</span></span>

```csharp
Console.WriteLine("Hello World!".Reverse());
```

<span data-ttu-id="1bce7-172">Programı yeniden çalıştırın ve sonucun tersine çevrildiğini görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="1bce7-172">Run the program again and you'll see that the result is reversed.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="1bce7-173">Aşağıdaki çıktıyı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="1bce7-173">You get the following output.</span></span>

```console
!dlroW olleH
```

<span data-ttu-id="1bce7-174">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="1bce7-174">Congratulations!</span></span> <span data-ttu-id="1bce7-175">.NET Core ile bir öğe şablonu oluşturdunuz ve dağıttınız.</span><span class="sxs-lookup"><span data-stu-id="1bce7-175">You created and deployed an item template with .NET Core.</span></span> <span data-ttu-id="1bce7-176">Bu öğretici serinin bir sonraki bölümüne hazırlık olarak, oluşturduğunuz şablonu kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1bce7-176">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="1bce7-177">Test klasöründeki tüm _test_ dosyaları da sildiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="1bce7-177">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="1bce7-178">Bu, bu öğreticinin bir sonraki ana bölümü için hazır temiz bir duruma geri dönecektir.</span><span class="sxs-lookup"><span data-stu-id="1bce7-178">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

## <a name="uninstall-the-template"></a><span data-ttu-id="1bce7-179">Şablonu kaldırma</span><span class="sxs-lookup"><span data-stu-id="1bce7-179">Uninstall the template</span></span>

<span data-ttu-id="1bce7-180">Şablonu dosya yoluna göre yüklediğiniz için, **şablonu mutlak** dosya yolu ile kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1bce7-180">Because you installed the template by file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="1bce7-181">`dotnet new -u` Komutu çalıştırarak yüklenen şablonların listesini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bce7-181">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="1bce7-182">Şablonunuzun en son listelenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1bce7-182">Your template should be listed last.</span></span> <span data-ttu-id="1bce7-183">Komutla `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` şablonunuzu kaldırmak için listelenen yolu kullanın.</span><span class="sxs-lookup"><span data-stu-id="1bce7-183">Use the path listed to uninstall your template with the `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` command.</span></span>

```dotnetcli
dotnet new -u
```

<span data-ttu-id="1bce7-184">Aşağıdakine benzer çıktı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="1bce7-184">You get output similar to the following.</span></span>

```console
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ItemTemplates
    Templates:
      dotnet gitignore file (gitignore)
      global.json file (globaljson)
      NuGet Config (nugetconfig)
      Solution File (sln)
      Dotnet local tool manifest file (tool-manifest)
      Web Config (webconfig)

... cut to save space ...

  NUnit3.DotNetNew.Template
    Templates:
      NUnit 3 Test Project (nunit) C#
      NUnit 3 Test Item (nunit-test) C#
      NUnit 3 Test Project (nunit) F#
      NUnit 3 Test Item (nunit-test) F#
      NUnit 3 Test Project (nunit) VB
      NUnit 3 Test Item (nunit-test) VB
  C:\working\templates\extensions
    Templates:
      Example templates: string extensions (stringext) C#
```

<span data-ttu-id="1bce7-185">Şablonu kaldırmak için aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1bce7-185">To uninstall a template, run the following command.</span></span>

```dotnetcli
dotnet new -u C:\working\templates\extensions
```

## <a name="next-steps"></a><span data-ttu-id="1bce7-186">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="1bce7-186">Next steps</span></span>

<span data-ttu-id="1bce7-187">Bu öğreticide, bir öğe şablonu oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="1bce7-187">In this tutorial, you created an item template.</span></span> <span data-ttu-id="1bce7-188">Proje şablonu oluşturmayı öğrenmek için bu öğretici seriye devam edin.</span><span class="sxs-lookup"><span data-stu-id="1bce7-188">To learn how to create a project template, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1bce7-189">Proje şablonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="1bce7-189">Create a project template</span></span>](cli-templates-create-project-template.md)
