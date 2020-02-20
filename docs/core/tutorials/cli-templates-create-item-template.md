---
title: DotNet New-.NET Core CLI için bir öğe şablonu oluşturun
description: DotNet New komutu için bir öğe şablonu oluşturmayı öğrenin. Öğe şablonları, herhangi bir sayıda dosya içerebilir.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 5f4038e863d9bb59df470d3516c08fd2ad29c078
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503560"
---
# <a name="tutorial-create-an-item-template"></a><span data-ttu-id="73273-104">Öğretici: öğe şablonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="73273-104">Tutorial: Create an item template</span></span>

<span data-ttu-id="73273-105">.NET Core ile projeler, dosyalar, hatta kaynaklar üreten şablonlar oluşturabilir ve dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73273-105">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="73273-106">Bu öğretici, `dotnet new` komutuyla kullanılmak üzere şablonlar oluşturmayı, yüklemeyi ve kaldırmayı öğretir.</span><span class="sxs-lookup"><span data-stu-id="73273-106">This tutorial is part one of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="73273-107">Serinin bu bölümünde şunları yapmayı öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="73273-107">In this part of the series, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="73273-108">Öğe şablonu için bir sınıf oluşturma</span><span class="sxs-lookup"><span data-stu-id="73273-108">Create a class for an item template</span></span>
> * <span data-ttu-id="73273-109">Şablon yapılandırma klasörünü ve dosyasını oluşturma</span><span class="sxs-lookup"><span data-stu-id="73273-109">Create the template config folder and file</span></span>
> * <span data-ttu-id="73273-110">Dosya yolundan şablon yükler</span><span class="sxs-lookup"><span data-stu-id="73273-110">Install a template from a file path</span></span>
> * <span data-ttu-id="73273-111">Bir öğe şablonunu test etme</span><span class="sxs-lookup"><span data-stu-id="73273-111">Test an item template</span></span>
> * <span data-ttu-id="73273-112">Öğe şablonunu kaldırma</span><span class="sxs-lookup"><span data-stu-id="73273-112">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="73273-113">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="73273-113">Prerequisites</span></span>

* <span data-ttu-id="73273-114">[.NET Core 2,2 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümleri.</span><span class="sxs-lookup"><span data-stu-id="73273-114">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
* <span data-ttu-id="73273-115">[DotNet New Için özel şablonlar](../tools/custom-templates.md)başvuru makalesine okuyun.</span><span class="sxs-lookup"><span data-stu-id="73273-115">Read the reference article [Custom templates for dotnet new](../tools/custom-templates.md).</span></span>

  <span data-ttu-id="73273-116">Başvuru makalesinde şablonlar ve bunların nasıl birlikte yerleştirildikleri hakkında temel bilgiler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73273-116">The reference article explains the basics about templates and how they're put together.</span></span> <span data-ttu-id="73273-117">Bu bilgilerden bazıları burada yeniden tekrarlandırılır.</span><span class="sxs-lookup"><span data-stu-id="73273-117">Some of this information will be reiterated here.</span></span>

* <span data-ttu-id="73273-118">Bir Terminal açın ve _working\templates_ klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="73273-118">Open a terminal and navigate to the _working\templates_ folder.</span></span>

## <a name="create-the-required-folders"></a><span data-ttu-id="73273-119">Gerekli klasörleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="73273-119">Create the required folders</span></span>

<span data-ttu-id="73273-120">Bu seri, şablon kaynağınızın bulunduğu bir "çalışma klasörü" ve şablonlarınızı test etmek için kullanılan bir "test klasörü" kullanır.</span><span class="sxs-lookup"><span data-stu-id="73273-120">This series uses a "working folder" where your template source is contained and a "testing folder" used to test your templates.</span></span> <span data-ttu-id="73273-121">Çalışma klasörü ve test klasörü aynı üst klasörde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73273-121">The working folder and testing folder should be under the same parent folder.</span></span>

<span data-ttu-id="73273-122">İlk olarak, üst klasörü oluşturun, ad önemlidir.</span><span class="sxs-lookup"><span data-stu-id="73273-122">First, create the parent folder, the name does not matter.</span></span> <span data-ttu-id="73273-123">Ardından, _çalışıyor_adlı bir alt klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="73273-123">Then, create a subfolder named _working_.</span></span> <span data-ttu-id="73273-124">_Çalışma_ klasörünün içinde _Şablonlar_adlı bir alt klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="73273-124">Inside of the _working_ folder, create a subfolder named _templates_.</span></span>

<span data-ttu-id="73273-125">Sonra, _Test_adlı üst klasör altında bir klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="73273-125">Next, create a folder under the parent folder named _test_.</span></span> <span data-ttu-id="73273-126">Klasör yapısı aşağıdaki gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="73273-126">The folder structure should look like the following.</span></span>

```console
parent_folder
├───test
└───working
    └───templates
```

## <a name="create-an-item-template"></a><span data-ttu-id="73273-127">Öğe şablonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="73273-127">Create an item template</span></span>

<span data-ttu-id="73273-128">Öğe şablonu, bir veya daha fazla dosya içeren belirli bir şablon türüdür.</span><span class="sxs-lookup"><span data-stu-id="73273-128">An item template is a specific type of template that contains one or more files.</span></span> <span data-ttu-id="73273-129">Bu tür şablonlar, bir yapılandırma, kod veya çözüm dosyası gibi bir şey oluşturmak istediğinizde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="73273-129">These types of templates are useful when you want to generate something like a config, code, or solution file.</span></span> <span data-ttu-id="73273-130">Bu örnekte, dize türüne bir genişletme yöntemi ekleyen bir sınıf oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="73273-130">In this example, you'll create a class that adds an extension method to the string type.</span></span>

<span data-ttu-id="73273-131">Terminalinizde, _working\templates_ klasörüne gidin ve _Uzantılar_adlı yeni bir alt klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="73273-131">In your terminal, navigate to the _working\templates_ folder and create a new subfolder named _extensions_.</span></span> <span data-ttu-id="73273-132">Klasörü girin.</span><span class="sxs-lookup"><span data-stu-id="73273-132">Enter the folder.</span></span>

```console
working
└───templates
    └───extensions
```

<span data-ttu-id="73273-133">_CommonExtensions.cs_ adlı yeni bir dosya oluşturun ve bu dosyayı en sevdiğiniz metin düzenleyicinizle açın.</span><span class="sxs-lookup"><span data-stu-id="73273-133">Create a new file named _CommonExtensions.cs_ and open it with your favorite text editor.</span></span> <span data-ttu-id="73273-134">Bu sınıf, bir dizenin içeriğini tersine çevirecek `Reverse` adlı bir genişletme yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="73273-134">This class will provide an extension method named `Reverse` that reverses the contents of a string.</span></span> <span data-ttu-id="73273-135">Aşağıdaki kodu yapıştırın ve dosyayı kaydedin:</span><span class="sxs-lookup"><span data-stu-id="73273-135">Paste in the following code and save the file:</span></span>

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

<span data-ttu-id="73273-136">Artık oluşturulan şablonun içeriğine sahip olduğunuza göre, şablonun kök klasöründe şablon yapılandırmasını oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="73273-136">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="73273-137">Şablon yapılandırması oluşturma</span><span class="sxs-lookup"><span data-stu-id="73273-137">Create the template config</span></span>

<span data-ttu-id="73273-138">Şablonlar, .NET Core 'da şablonunuzun kökünde bulunan özel bir klasör ve yapılandırma dosyası tarafından tanınır.</span><span class="sxs-lookup"><span data-stu-id="73273-138">Templates are recognized in .NET Core by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="73273-139">Bu öğreticide, şablon klasörünüz _working\templates\extensions_konumunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="73273-139">In this tutorial, your template folder is located at _working\templates\extensions_.</span></span>

<span data-ttu-id="73273-140">Bir şablon oluşturduğunuzda, şablon klasöründeki tüm dosyalar ve klasörler, özel yapılandırma klasörü hariç, şablonun bir parçası olarak dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="73273-140">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="73273-141">Bu yapılandırma klasörü _. Template. config_olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="73273-141">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="73273-142">İlk olarak, _. Template. config_adlı yeni bir alt klasör oluşturun, bunu girin.</span><span class="sxs-lookup"><span data-stu-id="73273-142">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="73273-143">Ardından, _Template. JSON_adlı yeni bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="73273-143">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="73273-144">Klasör yapınız şöyle görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="73273-144">Your folder structure should look like this:</span></span>

```console
working
└───templates
    └───extensions
        └───.template.config
                template.json
```

<span data-ttu-id="73273-145">En sevdiğiniz metin düzenleyicinizle _Template. JSON_ ' i açın ve aşağıdaki JSON kodunu yapıştırın ve kaydedin.</span><span class="sxs-lookup"><span data-stu-id="73273-145">Open the _template.json_ with your favorite text editor and paste in the following JSON code and save it.</span></span>

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

<span data-ttu-id="73273-146">Bu yapılandırma dosyası, şablonunuz için tüm ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="73273-146">This config file contains all the settings for your template.</span></span> <span data-ttu-id="73273-147">`name` ve `shortName`gibi temel ayarları görebilirsiniz, ancak `item`olarak ayarlanmış bir `tags/type` değeri de vardır.</span><span class="sxs-lookup"><span data-stu-id="73273-147">You can see the basic settings, such as `name` and `shortName`, but there's also a `tags/type` value that is set to `item`.</span></span> <span data-ttu-id="73273-148">Bu, şablonunuzu bir öğe şablonu olarak sınıflandırır.</span><span class="sxs-lookup"><span data-stu-id="73273-148">This categorizes your template as an item template.</span></span> <span data-ttu-id="73273-149">Oluşturduğunuz şablon türü üzerinde hiçbir kısıtlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="73273-149">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="73273-150">`item` ve `project` değerleri, .NET Core 'un arama yapmakta oldukları şablonun türünü kolayca filtreleyebilmesi için .NET Core 'un önerdiği yaygın adlardır.</span><span class="sxs-lookup"><span data-stu-id="73273-150">The `item` and `project` values are common names that .NET Core recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="73273-151">`classifications` öğesi, `dotnet new` çalıştırdığınız ve şablonların bir listesini alacağınız zaman gördüğünüz **Etiketler** sütununu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="73273-151">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="73273-152">Kullanıcılar ayrıca sınıflandırma etiketlerine göre arama yapabilir.</span><span class="sxs-lookup"><span data-stu-id="73273-152">Users can also search based on classification tags.</span></span> <span data-ttu-id="73273-153">\*. JSON dosyasındaki `tags` özelliğini `classifications` Etiketler listesiyle karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="73273-153">Don't confuse the `tags` property in the \*.json file with the `classifications` tags list.</span></span> <span data-ttu-id="73273-154">Benzer şekilde adlandırılan iki farklı şey vardır.</span><span class="sxs-lookup"><span data-stu-id="73273-154">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="73273-155">*Template. JSON* dosyasının tam şeması [JSON Şema deposunda](http://json.schemastore.org/template)bulunur.</span><span class="sxs-lookup"><span data-stu-id="73273-155">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="73273-156">*Template. JSON* dosyası hakkında daha fazla bilgi için bkz. [DotNet şablon oluşturma wiki](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="73273-156">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="73273-157">Artık geçerli bir _. Template. config/Template. JSON_ dosyanız olduğuna göre, şablonunuz yüklenmeye hazırdır.</span><span class="sxs-lookup"><span data-stu-id="73273-157">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="73273-158">Terminalinizde, _Uzantılar_ klasörüne gidin ve geçerli klasörde bulunan şablonu yüklemek için şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="73273-158">In your terminal, navigate to the  _extensions_ folder and run the following command to install the template located at the current folder:</span></span>

* <span data-ttu-id="73273-159">**Windows üzerinde**: `dotnet new -i .\`</span><span class="sxs-lookup"><span data-stu-id="73273-159">**On Windows**: `dotnet new -i .\`</span></span>
* <span data-ttu-id="73273-160">**Linux veya macOS 'ta**: `dotnet new -i ./`</span><span class="sxs-lookup"><span data-stu-id="73273-160">**On Linux or macOS**: `dotnet new -i ./`</span></span>

<span data-ttu-id="73273-161">Bu komut, yüklenmiş şablonların listesini verir ve bunları içermelidir.</span><span class="sxs-lookup"><span data-stu-id="73273-161">This command outputs the list of templates installed, which should include yours.</span></span>

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

## <a name="test-the-item-template"></a><span data-ttu-id="73273-162">Öğe şablonunu test etme</span><span class="sxs-lookup"><span data-stu-id="73273-162">Test the item template</span></span>

<span data-ttu-id="73273-163">Artık bir öğe şablonu yükleolduğunuza göre, test edin.</span><span class="sxs-lookup"><span data-stu-id="73273-163">Now that you have an item template installed, test it.</span></span> <span data-ttu-id="73273-164">_Teste/_ klasöre gidin ve `dotnet new console`yeni bir konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="73273-164">Navigate to the _test/_ folder and create a new console application with `dotnet new console`.</span></span> <span data-ttu-id="73273-165">Bu, `dotnet run` komutuyla kolayca test edebileceğiniz bir çalışan proje oluşturur.</span><span class="sxs-lookup"><span data-stu-id="73273-165">This generates a working project you can easily test with the `dotnet run` command.</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="73273-166">Aşağıdakine benzer bir çıktı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="73273-166">You get output similar to the following.</span></span>

```console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\test\test.csproj...
  Restore completed in 54.82 ms for C:\test\test.csproj.

Restore succeeded.
```

<span data-ttu-id="73273-167">Projeyi ile çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="73273-167">Run the project with.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="73273-168">Aşağıdaki çıktıyı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="73273-168">You get the following output.</span></span>

```console
Hello World!
```

<span data-ttu-id="73273-169">Sonra, şablondan _CommonExtensions.cs_ oluşturmak için `dotnet new stringext` çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="73273-169">Next, run `dotnet new stringext` to generate the _CommonExtensions.cs_ from the template.</span></span>

```dotnetcli
dotnet new stringext
```

<span data-ttu-id="73273-170">Aşağıdaki çıktıyı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="73273-170">You get the following output.</span></span>

```console
The template "Example templates: string extensions" was created successfully.
```

<span data-ttu-id="73273-171">`"Hello World"` dizesini, şablon tarafından sağlanmış uzantı yöntemiyle tersine çevirmek için _program.cs_ içindeki kodu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="73273-171">Change the code in _Program.cs_ to reverse the `"Hello World"` string with the extension method provided by the template.</span></span>

```csharp
Console.WriteLine("Hello World!".Reverse());
```

<span data-ttu-id="73273-172">Programı yeniden çalıştırın ve sonucun tersine çevrilip çevrilmediğini görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="73273-172">Run the program again and you'll see that the result is reversed.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="73273-173">Aşağıdaki çıktıyı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="73273-173">You get the following output.</span></span>

```console
!dlroW olleH
```

<span data-ttu-id="73273-174">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="73273-174">Congratulations!</span></span> <span data-ttu-id="73273-175">.NET Core ile bir öğe şablonu oluşturup dağıttıysanız.</span><span class="sxs-lookup"><span data-stu-id="73273-175">You created and deployed an item template with .NET Core.</span></span> <span data-ttu-id="73273-176">Bu öğretici serisinin bir sonraki kısmına hazırlanın, oluşturduğunuz şablonu kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="73273-176">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="73273-177">Tüm dosyaları da _Test_ klasöründen sildiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="73273-177">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="73273-178">Bu, Bu öğreticinin bir sonraki ana kısmına yönelik temiz bir duruma geri dönebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73273-178">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

## <a name="uninstall-the-template"></a><span data-ttu-id="73273-179">Şablonu kaldırma</span><span class="sxs-lookup"><span data-stu-id="73273-179">Uninstall the template</span></span>

<span data-ttu-id="73273-180">Şablonu dosya yoluna göre yükletiğinden, **mutlak** dosya yolu ile kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="73273-180">Because you installed the template by file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="73273-181">`dotnet new -u` komutunu çalıştırarak, yüklenmiş şablonların listesini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73273-181">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="73273-182">Şablonunuzun son listelenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="73273-182">Your template should be listed last.</span></span> <span data-ttu-id="73273-183">`dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` komutuyla şablonunuzu kaldırmak için listelenen yolu kullanın.</span><span class="sxs-lookup"><span data-stu-id="73273-183">Use the path listed to uninstall your template with the `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` command.</span></span>

```dotnetcli
dotnet new -u
```

<span data-ttu-id="73273-184">Aşağıdakine benzer bir çıktı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="73273-184">You get output similar to the following.</span></span>

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

<span data-ttu-id="73273-185">Bir şablonu kaldırmak için aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="73273-185">To uninstall a template, run the following command.</span></span>

```dotnetcli
dotnet new -u C:\working\templates\extensions
```

## <a name="next-steps"></a><span data-ttu-id="73273-186">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="73273-186">Next steps</span></span>

<span data-ttu-id="73273-187">Bu öğreticide bir öğe şablonu oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="73273-187">In this tutorial, you created an item template.</span></span> <span data-ttu-id="73273-188">Proje şablonu oluşturmayı öğrenmek için bu öğretici serisine devam edin.</span><span class="sxs-lookup"><span data-stu-id="73273-188">To learn how to create a project template, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="73273-189">Proje şablonu oluşturma</span><span class="sxs-lookup"><span data-stu-id="73273-189">Create a project template</span></span>](cli-templates-create-project-template.md)
