---
title: Mac için Visual Studio kullanarak macOS üzerinde .NET Core kullanmaya başlama
description: Bu konu, Mac için Visual Studio ve .NET Core kullanarak basit bir konsol uygulaması oluşturma konusunda size rehberlik eder.
author: mairaw
ms.date: 07/11/2019
ms.custom: seodec18
ms.openlocfilehash: feaed88e902080c5c3b07578b78f8437489a690c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428588"
---
# <a name="get-started-with-net-core-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="1a601-103">Mac için Visual Studio kullanarak macOS üzerinde .NET Core kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="1a601-103">Get started with .NET Core on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="1a601-104">Mac için Visual Studio .NET Core uygulamaları geliştirmek için tam özellikli bir tümleşik geliştirme ortamı (IDE) sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a601-104">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="1a601-105">Bu konu, Mac için Visual Studio ve .NET Core kullanarak basit bir konsol uygulaması oluşturma konusunda size rehberlik eder.</span><span class="sxs-lookup"><span data-stu-id="1a601-105">This topic walks you through building a simple console application using Visual Studio for Mac and .NET Core.</span></span>

> [!NOTE]
> <span data-ttu-id="1a601-106">Geri bildiriminiz çok değerli.</span><span class="sxs-lookup"><span data-stu-id="1a601-106">Your feedback is highly valued.</span></span> <span data-ttu-id="1a601-107">Mac için Visual Studio üzerinde geliştirme ekibine geri bildirimde bulunmak için kullanabileceğiniz iki yol vardır:</span><span class="sxs-lookup"><span data-stu-id="1a601-107">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> * <span data-ttu-id="1a601-108">Mac için Visual Studio, menüden bir **sorun bildirmek** veya hoş geldiniz ekranından bir **sorun** bildirmek için > **Yardım** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="1a601-108">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="1a601-109">Geri bildiriminizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/spaces/8/index.html) portalında izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a601-109">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="1a601-110">Bir öneride bulunmak için, **yardım** > menüden **bir öneri sağlayın** veya hoş geldiniz ekranından bir öneri **sağlayın** ve bu işlem sizi [Mac için Visual Studio Geliştirici topluluğu Web sayfasına](https://developercommunity.visualstudio.com/content/idea/post.html?space=41)götürür.</span><span class="sxs-lookup"><span data-stu-id="1a601-110">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1a601-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="1a601-111">Prerequisites</span></span>

<span data-ttu-id="1a601-112">Bkz. [.NET Core Dependencies ve Requirements](../install/dependencies.md?tabs=netcore30&pivots=os-macos) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="1a601-112">See the [.NET Core dependencies and requirements](../install/dependencies.md?tabs=netcore30&pivots=os-macos) topic.</span></span>

<span data-ttu-id="1a601-113">.NET Core 'un desteklenen bir sürümünü kullandığınızdan emin olmak için [.NET Core destek](/visualstudio/mac/net-core-support) makalesine bakın.</span><span class="sxs-lookup"><span data-stu-id="1a601-113">Check the [.NET Core Support](/visualstudio/mac/net-core-support) article to ensure you're using a supported version of .NET Core.</span></span>

## <a name="get-started"></a><span data-ttu-id="1a601-114">başlarken</span><span class="sxs-lookup"><span data-stu-id="1a601-114">Get started</span></span>

<span data-ttu-id="1a601-115">Önkoşulları ve Mac için Visual Studio zaten yüklediyseniz, bu bölümü atlayın ve [proje oluşturmaya](#creating-a-project)devam edin.</span><span class="sxs-lookup"><span data-stu-id="1a601-115">If you've already installed the prerequisites and Visual Studio for Mac, skip this section and proceed to [Creating a project](#creating-a-project).</span></span> <span data-ttu-id="1a601-116">Önkoşulları ve Mac için Visual Studio yüklemek için şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="1a601-116">Follow these steps to install the prerequisites and Visual Studio for Mac:</span></span>

<span data-ttu-id="1a601-117">[Mac için Visual Studio yükleyicisini](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)indirin.</span><span class="sxs-lookup"><span data-stu-id="1a601-117">Download the [Visual Studio for Mac installer](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="1a601-118">Yükleyiciyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1a601-118">Run the installer.</span></span> <span data-ttu-id="1a601-119">Lisans sözleşmesini okuyun ve kabul edin.</span><span class="sxs-lookup"><span data-stu-id="1a601-119">Read and accept the license agreement.</span></span> <span data-ttu-id="1a601-120">Yüklemesi sırasında .NET Core 'u yüklemek için seçeneği belirleyin.</span><span class="sxs-lookup"><span data-stu-id="1a601-120">During the install, select the option to install .NET Core.</span></span> <span data-ttu-id="1a601-121">Platformlar arası mobil uygulama geliştirme teknolojisi olan Xamarin 'i yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a601-121">You're provided the opportunity to install Xamarin, a cross-platform mobile app development technology.</span></span> <span data-ttu-id="1a601-122">Xamarin ve ilgili bileşenlerinin yüklenmesi .NET Core geliştirmesi için isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1a601-122">Installing Xamarin and its related components is optional for .NET Core development.</span></span> <span data-ttu-id="1a601-123">Mac için Visual Studio yüklemesi işlemini adım adım için [Mac için Visual Studio belgelerine](/visualstudio/mac/)bakın.</span><span class="sxs-lookup"><span data-stu-id="1a601-123">For a walk-through of the Visual Studio for Mac install process, see [Visual Studio for Mac documentation](/visualstudio/mac/).</span></span> <span data-ttu-id="1a601-124">Yüklemesi tamamlandığında Mac için Visual Studio IDE 'yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="1a601-124">When the install is complete, start the Visual Studio for Mac IDE.</span></span>

## <a name="creating-a-project"></a><span data-ttu-id="1a601-125">Proje oluşturma</span><span class="sxs-lookup"><span data-stu-id="1a601-125">Creating a project</span></span>

1. <span data-ttu-id="1a601-126">Başlangıç penceresinde **Yeni** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="1a601-126">Select **New** on the Start Window.</span></span>

   ![Mac için Visual Studio başlangıç ekranında yeni düğme](./media/using-on-mac-vs/visual-studio-mac-new-project.png)

1. <span data-ttu-id="1a601-128">**Yeni proje** iletişim kutusunda, **.NET Core** düğümünün altında **uygulama** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="1a601-128">In the **New Project** dialog, select **App** under the **.NET Core** node.</span></span> <span data-ttu-id="1a601-129">**Konsol uygulaması** şablonunu ve ardından Ileri ' **yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="1a601-129">Select the **Console Application** template followed by **Next**.</span></span>

   ![Yeni proje şablonları listesi](./media/using-on-mac-vs/visual-studio-mac-new-dialog.png)

1. <span data-ttu-id="1a601-131">.NET Core 'un birden fazla sürümü yüklüyse, projeniz için hedef çerçeveyi seçin.</span><span class="sxs-lookup"><span data-stu-id="1a601-131">If you have more than one version of .NET Core installed, select the target framework for your project.</span></span>

1. <span data-ttu-id="1a601-132">**Proje adı**Için "HelloWorld" yazın.</span><span class="sxs-lookup"><span data-stu-id="1a601-132">Type "HelloWorld" for the **Project Name**.</span></span> <span data-ttu-id="1a601-133">**Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="1a601-133">Select **Create**.</span></span>

   ![Yeni konsol uygulamanızı yapılandırma iletişim kutusu](./media/using-on-mac-vs/visual-studio-mac-new-options.png)

1. <span data-ttu-id="1a601-135">Projenin bağımlılıkları geri yüklenirken bekleyin.</span><span class="sxs-lookup"><span data-stu-id="1a601-135">Wait while the project's dependencies are restored.</span></span> <span data-ttu-id="1a601-136">Projenin bir `Main` yöntemi ile C# `Program` sınıfınıiçeren tek bir dosyası vardır.</span><span class="sxs-lookup"><span data-stu-id="1a601-136">The project has a single C# file, *Program.cs*, containing a `Program` class with a `Main` method.</span></span> <span data-ttu-id="1a601-137">`Console.WriteLine` deyimin "Merhaba Dünya!" çıktısı alınacaktır</span><span class="sxs-lookup"><span data-stu-id="1a601-137">The `Console.WriteLine` statement will output "Hello World!"</span></span> <span data-ttu-id="1a601-138">uygulama çalıştırıldığında konsola.</span><span class="sxs-lookup"><span data-stu-id="1a601-138">to the console when the app is run.</span></span>

   ![Program.cs dosyasının açık olduğu ana pencere](./media/using-on-mac-vs/visual-studio-mac-editor.png)

## <a name="run-the-application"></a><span data-ttu-id="1a601-140">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="1a601-140">Run the application</span></span>

<span data-ttu-id="1a601-141">Uygulamayı hata ayıklama modunda ⌘ ↵ (komut + ENTER) kullanarak veya ⌥ ⌘ ↵ (Option + Command + ENTER) kullanarak yayın modunda çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1a601-141">Run the app in Debug mode using ⌘ ↵ (command + enter) or in Release mode using ⌥ ⌘ ↵ (option + command + enter).</span></span>

![Uygulama çıkış bölmesi Merhaba Dünya gösterir!](./media/using-on-mac-vs/visual-studio-mac-output.png)

## <a name="next-step"></a><span data-ttu-id="1a601-143">Sonraki adım</span><span class="sxs-lookup"><span data-stu-id="1a601-143">Next step</span></span>

<span data-ttu-id="1a601-144">[MacOS üzerinde Mac için Visual Studio konu başlığı kullanarak tüm .NET Core çözümü oluşturma](using-on-mac-vs-full-solution.md) , yeniden kullanılabilir bir kitaplık ve birim testi içeren bir .NET Core çözümünün nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="1a601-144">The [Building a complete .NET Core solution on macOS using Visual Studio for Mac](using-on-mac-vs-full-solution.md) topic shows you how to build a complete .NET Core solution that includes a reusable library and unit testing.</span></span>
