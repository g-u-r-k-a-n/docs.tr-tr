---
title: Apache Spark için .NET ile çalışmaya başlama
description: Windows 'da .NET Core kullanarak Apache Spark uygulaması için .NET çalıştırmayı öğrenin.
ms.date: 06/27/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 19efc8412d834d73069c61e1cc1ccd9e5eb8593b
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774371"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a><span data-ttu-id="6094c-103">Öğretici: Apache Spark için .NET ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="6094c-103">Tutorial: Get started with .NET for Apache Spark</span></span>

<span data-ttu-id="6094c-104">Bu öğreticide, Windows 'da .NET Core kullanarak Apache Spark bir uygulama için nasıl bir .NET çalıştırılacağı öğretilir.</span><span class="sxs-lookup"><span data-stu-id="6094c-104">This tutorial teaches you how to run a .NET for Apache Spark app using .NET Core on Windows.</span></span>

<span data-ttu-id="6094c-105">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="6094c-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="6094c-106">.NET için Windows ortamınızı Apache Spark için hazırlayın</span><span class="sxs-lookup"><span data-stu-id="6094c-106">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="6094c-107">**Microsoft. spark. Worker** 'ı indirin</span><span class="sxs-lookup"><span data-stu-id="6094c-107">Download the **Microsoft.Spark.Worker**</span></span>
> * <span data-ttu-id="6094c-108">Apache Spark uygulama için basit bir .NET oluşturun ve çalıştırın</span><span class="sxs-lookup"><span data-stu-id="6094c-108">Build and run a simple .NET for Apache Spark application</span></span>

## <a name="prepare-your-environment"></a><span data-ttu-id="6094c-109">Ortamınızı hazırlama</span><span class="sxs-lookup"><span data-stu-id="6094c-109">Prepare your environment</span></span>

<span data-ttu-id="6094c-110">Başlamadan önce, komut satırınızdan `dotnet`, `java`, `mvn`, `spark-shell` ' ü çalıştıradığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="6094c-110">Before you begin, make sure you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line.</span></span> <span data-ttu-id="6094c-111">Ortamınız zaten hazırlanmışsa bir sonraki bölüme atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6094c-111">If your environment is already prepared, you can skip to the next section.</span></span> <span data-ttu-id="6094c-112">Komutlardan herhangi birini veya tümünü çalıştıradıysanız aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="6094c-112">If you cannot run any or all of the commands, follow the steps below.</span></span>

1. <span data-ttu-id="6094c-113">[.NET Core 2.1 x SDK 'sını](https://dotnet.microsoft.com/download/dotnet-core/2.1)indirip yükleyin.</span><span class="sxs-lookup"><span data-stu-id="6094c-113">Download and install the [.NET Core 2.1x SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span> <span data-ttu-id="6094c-114">SDK yükleme, yolunuza `dotnet` araç zinciri ekler.</span><span class="sxs-lookup"><span data-stu-id="6094c-114">Installing the SDK adds the `dotnet` toolchain to your PATH.</span></span> <span data-ttu-id="6094c-115">Yüklemeyi doğrulamak için `dotnet --version` PowerShell komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="6094c-115">Use the PowerShell command `dotnet --version` to verify the installation.</span></span>

2. <span data-ttu-id="6094c-116">En son güncelleştirmelerle [Visual studio 2017](https://www.visualstudio.com/downloads/) veya [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/) ' ü yükler.</span><span class="sxs-lookup"><span data-stu-id="6094c-116">Install [Visual Studio 2017](https://www.visualstudio.com/downloads/) or [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/) with the latest updates.</span></span> <span data-ttu-id="6094c-117">Community, Professional veya Enterprise 'u kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6094c-117">You can use Community, Professional, or Enterprise.</span></span> <span data-ttu-id="6094c-118">Topluluk sürümü ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="6094c-118">The Community version is free.</span></span>

   <span data-ttu-id="6094c-119">Yükleme sırasında aşağıdaki iş yüklerini seçin:</span><span class="sxs-lookup"><span data-stu-id="6094c-119">Choose the following workloads during installation:</span></span>
      * <span data-ttu-id="6094c-120">.NET masaüstü geliştirme</span><span class="sxs-lookup"><span data-stu-id="6094c-120">.NET desktop development</span></span>
          * <span data-ttu-id="6094c-121">Tüm gerekli bileşenler</span><span class="sxs-lookup"><span data-stu-id="6094c-121">All required components</span></span>
          * <span data-ttu-id="6094c-122">.NET Framework 4.6.1 geliştirme araçları</span><span class="sxs-lookup"><span data-stu-id="6094c-122">.NET Framework 4.6.1 Development Tools</span></span>
      * <span data-ttu-id="6094c-123">.NET Core platformlar arası geliştirme</span><span class="sxs-lookup"><span data-stu-id="6094c-123">.NET Core cross-platform development</span></span>
          * <span data-ttu-id="6094c-124">Tüm gerekli bileşenler</span><span class="sxs-lookup"><span data-stu-id="6094c-124">All required components</span></span>

3. <span data-ttu-id="6094c-125">[Java 1,8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)' i yükler.</span><span class="sxs-lookup"><span data-stu-id="6094c-125">Install [Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).</span></span>

    * <span data-ttu-id="6094c-126">İşletim sisteminiz için uygun sürümü seçin.</span><span class="sxs-lookup"><span data-stu-id="6094c-126">Select the appropriate version for your operating system.</span></span> <span data-ttu-id="6094c-127">Örneğin, bir Windows x64 makinesi için **JDK-8u201-Windows-x64. exe** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="6094c-127">For example, select **jdk-8u201-windows-x64.exe** for a Windows x64 machine.</span></span>
    * <span data-ttu-id="6094c-128">Yüklemeyi doğrulamak için `java -version` PowerShell komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="6094c-128">Use the PowerShell command `java -version` to verify the installation.</span></span>

4. <span data-ttu-id="6094c-129">[Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi)'yi yükler.</span><span class="sxs-lookup"><span data-stu-id="6094c-129">Install [Apache Maven 3.6.0+](https://maven.apache.org/download.cgi).</span></span>
    * <span data-ttu-id="6094c-130">[Apache Maven 3.6.2](http://mirror.metrocast.net/apache/maven/maven-3/3.6.2/binaries/apache-maven-3.6.2-bin.zip)indirin.</span><span class="sxs-lookup"><span data-stu-id="6094c-130">Download [Apache Maven 3.6.2](http://mirror.metrocast.net/apache/maven/maven-3/3.6.2/binaries/apache-maven-3.6.2-bin.zip).</span></span>
    * <span data-ttu-id="6094c-131">Yerel bir dizine ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="6094c-131">Extract to a local directory.</span></span> <span data-ttu-id="6094c-132">Örneğin, `c:\bin\apache-maven-3.6.2\`.</span><span class="sxs-lookup"><span data-stu-id="6094c-132">For example, `c:\bin\apache-maven-3.6.2\`.</span></span>
    * <span data-ttu-id="6094c-133">[Yol ortam değişkeninizin](https://www.java.com/en/download/help/path.xml)Apache Maven 'i ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6094c-133">Add Apache Maven to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="6094c-134">@No__t_0 çıkardıysanız, yolunuza `c:\bin\apache-maven-3.6.2\bin` eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="6094c-134">If you extracted to `c:\bin\apache-maven-3.6.2\`, you would add `c:\bin\apache-maven-3.6.2\bin` to your PATH.</span></span>
    * <span data-ttu-id="6094c-135">Yüklemeyi doğrulamak için `mvn -version` PowerShell komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="6094c-135">Use the PowerShell command `mvn -version` to verify the installation.</span></span>

5. <span data-ttu-id="6094c-136">[Apache Spark 2.3 +](https://spark.apache.org/downloads.html)' yı yükler.</span><span class="sxs-lookup"><span data-stu-id="6094c-136">Install [Apache Spark 2.3+](https://spark.apache.org/downloads.html).</span></span> <span data-ttu-id="6094c-137">Apache Spark 2,4 + desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="6094c-137">Apache Spark 2.4+ isn't supported.</span></span>
    * <span data-ttu-id="6094c-138">[Apache Spark 2.3 +](https://spark.apache.org/downloads.html) indirin ve [7-zip](https://www.7-zip.org/) veya [WinZip](https://www.winzip.com/)gibi bir araç kullanarak yerel bir klasöre ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="6094c-138">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder using a tool like [7-zip](https://www.7-zip.org/) or [WinZip](https://www.winzip.com/).</span></span> <span data-ttu-id="6094c-139">Örneğin, `c:\bin\spark-2.3.2-bin-hadoop2.7\` ' a ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6094c-139">For example, you might extract it to `c:\bin\spark-2.3.2-bin-hadoop2.7\`.</span></span>
    * <span data-ttu-id="6094c-140">[Path ortam değişkeninizin](https://www.java.com/en/download/help/path.xml)Apache Spark ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6094c-140">Add Apache Spark to your [PATH environment variable](https://www.java.com/en/download/help/path.xml).</span></span> <span data-ttu-id="6094c-141">@No__t_0 çıkardıysanız, yolunuza `c:\bin\spark-2.3.2-bin-hadoop2.7\bin` eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="6094c-141">If you extracted to `c:\bin\spark-2.3.2-bin-hadoop2.7\`, you would add `c:\bin\spark-2.3.2-bin-hadoop2.7\bin` to your PATH.</span></span>
    * <span data-ttu-id="6094c-142">@No__t_1 adlı [Yeni bir ortam değişkeni](https://www.java.com/en/download/help/path.xml) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6094c-142">Add a [new environment variable](https://www.java.com/en/download/help/path.xml) called `SPARK_HOME`.</span></span> <span data-ttu-id="6094c-143">@No__t_0 çıkardıysanız, **değişken değeri**için `C:\bin\spark-2.3.2-bin-hadoop2.7\` kullanın.</span><span class="sxs-lookup"><span data-stu-id="6094c-143">If you extracted to `C:\bin\spark-2.3.2-bin-hadoop2.7\`, use  `C:\bin\spark-2.3.2-bin-hadoop2.7\` for the **Variable value**.</span></span>
    * <span data-ttu-id="6094c-144">Komut satırınızdan `spark-shell` çalıştırabildiğinizi doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="6094c-144">Verify you are able to run `spark-shell` from your command line.</span></span>

6. <span data-ttu-id="6094c-145">[Winutils](https://github.com/steveloughran/winutils)'i ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6094c-145">Set up [WinUtils](https://github.com/steveloughran/winutils).</span></span>
    * <span data-ttu-id="6094c-146">Winutils **. exe** Ikili dosyasını [winutils deposundan](https://github.com/steveloughran/winutils)indirin.</span><span class="sxs-lookup"><span data-stu-id="6094c-146">Download the **winutils.exe** binary from [WinUtils repository](https://github.com/steveloughran/winutils).</span></span> <span data-ttu-id="6094c-147">Spark dağıtımının derlenmiş olduğu Hadoop sürümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="6094c-147">Select the version of Hadoop the Spark distribution was compiled with.</span></span> <span data-ttu-id="6094c-148">Örneğin, **Spark 2.3.2**için **Hadoop-2.7.1** kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="6094c-148">For example, you use **hadoop-2.7.1** for **Spark 2.3.2**.</span></span> <span data-ttu-id="6094c-149">Hadoop sürümü, Spark install klasörünüzün adının sonunda açıklanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6094c-149">The Hadoop version is annotated at the end of your Spark install folder name.</span></span>
    * <span data-ttu-id="6094c-150">**Winutils. exe** ikilisini istediğiniz bir dizine kaydedin.</span><span class="sxs-lookup"><span data-stu-id="6094c-150">Save the **winutils.exe** binary to a directory of your choice.</span></span> <span data-ttu-id="6094c-151">Örneğin, `c:\hadoop\bin`.</span><span class="sxs-lookup"><span data-stu-id="6094c-151">For example, `c:\hadoop\bin`.</span></span>
    * <span data-ttu-id="6094c-152">@No__t_0, `bin` olmadan **winutils. exe** ile dizini yansıtacak şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6094c-152">Set `HADOOP_HOME` to reflect the directory with **winutils.exe** without `bin`.</span></span> <span data-ttu-id="6094c-153">Örneğin, `c:\hadoop`.</span><span class="sxs-lookup"><span data-stu-id="6094c-153">For example, `c:\hadoop`.</span></span>
    * <span data-ttu-id="6094c-154">PATH ortam değişkenini `%HADOOP_HOME%\bin` içerecek şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6094c-154">Set the PATH environment variable to include `%HADOOP_HOME%\bin`.</span></span>

<span data-ttu-id="6094c-155">Bir sonraki bölüme geçmeden önce komut satırınızdan `dotnet`, `java`, `mvn`, `spark-shell` ' ü çalıştırıp çalıştırabileceğinizi iki kez denetleyin.</span><span class="sxs-lookup"><span data-stu-id="6094c-155">Double check that you can run `dotnet`, `java`, `mvn`, `spark-shell` from your command line before you move to the next section.</span></span>

## <a name="download-the-microsoftsparkworker-release"></a><span data-ttu-id="6094c-156">Microsoft. spark. Worker sürümünü indirin</span><span class="sxs-lookup"><span data-stu-id="6094c-156">Download the Microsoft.Spark.Worker release</span></span>

1. <span data-ttu-id="6094c-157">[Microsoft. spark. Worker](https://github.com/dotnet/spark/releases) sürümünü, Apache Spark GitHub yayınları sayfasından yerel makinenize indirin.</span><span class="sxs-lookup"><span data-stu-id="6094c-157">Download the [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) release from the .NET for Apache Spark GitHub Releases page to your local machine.</span></span> <span data-ttu-id="6094c-158">Örneğin, `c:\bin\Microsoft.Spark.Worker\` yoluna indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6094c-158">For example, you might download it to the path, `c:\bin\Microsoft.Spark.Worker\`.</span></span>

2. <span data-ttu-id="6094c-159">@No__t_1 adlı [Yeni bir ortam değişkeni](https://www.java.com/en/download/help/path.xml) oluşturun ve bunu **Microsoft. spark. Worker**' i indirdiğiniz ve ayıkladığınız dizine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6094c-159">Create a [new environment variable](https://www.java.com/en/download/help/path.xml) called `DOTNET_WORKER_DIR` and set it to the directory where you downloaded and extracted the **Microsoft.Spark.Worker**.</span></span> <span data-ttu-id="6094c-160">Örneğin, `c:\bin\Microsoft.Spark.Worker`.</span><span class="sxs-lookup"><span data-stu-id="6094c-160">For example, `c:\bin\Microsoft.Spark.Worker`.</span></span>

## <a name="clone-the-net-for-apache-spark-github-repo"></a><span data-ttu-id="6094c-161">Apache Spark GitHub deposunun .NET kopyasını kopyalama</span><span class="sxs-lookup"><span data-stu-id="6094c-161">Clone the .NET for Apache Spark GitHub repo</span></span>

<span data-ttu-id="6094c-162">Apache Spark deposunu makinenize kopyalamak için aşağıdaki [GitBash](https://gitforwindows.org/) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="6094c-162">Use the following [GitBash](https://gitforwindows.org/) command to clone the .NET for Apache Spark repo to your machine.</span></span>

```bash
git clone https://github.com/dotnet/spark.git c:\github\dotnet-spark
```

## <a name="write-a-net-for-apache-spark-app"></a><span data-ttu-id="6094c-163">Apache Spark uygulaması için .NET yazma</span><span class="sxs-lookup"><span data-stu-id="6094c-163">Write a .NET for Apache Spark app</span></span>

1. <span data-ttu-id="6094c-164">**Visual Studio 'yu** açın ve **Dosya > Yeni Proje > konsol uygulaması (.NET Core) oluştur**' a gidin.</span><span class="sxs-lookup"><span data-stu-id="6094c-164">Open **Visual Studio** and navigate to **File > Create New Project > Console App (.NET Core)**.</span></span> <span data-ttu-id="6094c-165">Uygulamayı **Merhaba Spark**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="6094c-165">Name the application **HelloSpark**.</span></span>

2. <span data-ttu-id="6094c-166">[Microsoft. Spark NuGet paketini](https://www.nuget.org/profiles/spark)yükler.</span><span class="sxs-lookup"><span data-stu-id="6094c-166">Install the [Microsoft.Spark NuGet package](https://www.nuget.org/profiles/spark).</span></span> <span data-ttu-id="6094c-167">NuGet paketlerini yükleme hakkında daha fazla bilgi için bkz. [NuGet paketini yüklemek Için farklı yollar](https://docs.microsoft.com/nuget/consume-packages/ways-to-install-a-package).</span><span class="sxs-lookup"><span data-stu-id="6094c-167">For more information on installing NuGet packages, see [Different ways to install a NuGet Package](https://docs.microsoft.com/nuget/consume-packages/ways-to-install-a-package).</span></span>

3. <span data-ttu-id="6094c-168">**Çözüm Gezgini**' de, **program.cs** açın ve aşağıdaki C# kodu yazın:</span><span class="sxs-lookup"><span data-stu-id="6094c-168">In **Solution Explorer**, open **Program.cs** and write the following C# code:</span></span>

   ```csharp
     var spark = SparkSession.Builder().GetOrCreate();
     var df = spark.Read().Json("people.json");
     df.Show();
   ```

4. <span data-ttu-id="6094c-169">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6094c-169">Build the solution.</span></span>

## <a name="run-your-net-for-apache-spark-app"></a><span data-ttu-id="6094c-170">Apache Spark uygulamanızı .NET için çalıştırın</span><span class="sxs-lookup"><span data-stu-id="6094c-170">Run your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="6094c-171">**PowerShell** 'i açın ve dizini uygulamanızın depolandığı klasöre değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6094c-171">Open **PowerShell** and change the directory to the folder where your app is stored.</span></span>

   ```powershell
   cd <your-app-output-directory>
   ```

2. <span data-ttu-id="6094c-172">Şu içerikle **kişiler. JSON** adlı bir dosya oluşturun:</span><span class="sxs-lookup"><span data-stu-id="6094c-172">Create a file called **people.json** with the following content:</span></span>

   ```json
   {"name":"Michael"}
   {"name":"Andy", "age":30}
   {"name":"Justin", "age":19}
   ```

3. <span data-ttu-id="6094c-173">Uygulamanızı çalıştırmak için aşağıdaki PowerShell komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="6094c-173">Use the following PowerShell command to run your app:</span></span>

   ```powershell
    spark-submit `
    --class org.apache.spark.deploy.dotnet.DotnetRunner `
    --master local `
    microsoft-spark-2.4.x-<version>.jar `
    dotnet HelloSpark.dll
    ```

<span data-ttu-id="6094c-174">Mühendisi!</span><span class="sxs-lookup"><span data-stu-id="6094c-174">Congratulations!</span></span> <span data-ttu-id="6094c-175">Apache Spark uygulaması için bir .NET başarıyla yazıldı ve çalıştırdınız.</span><span class="sxs-lookup"><span data-stu-id="6094c-175">You successfully authored and ran a .NET for Apache Spark app.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6094c-176">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="6094c-176">Next steps</span></span>

<span data-ttu-id="6094c-177">Bu öğreticide, nasıl yapılacağını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="6094c-177">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="6094c-178">.NET için Windows ortamınızı Apache Spark için hazırlayın</span><span class="sxs-lookup"><span data-stu-id="6094c-178">Prepare your Windows environment for .NET for Apache Spark</span></span>
> * <span data-ttu-id="6094c-179">**Microsoft. spark. Worker** 'ı indirin</span><span class="sxs-lookup"><span data-stu-id="6094c-179">Download the **Microsoft.Spark.Worker**</span></span>
> * <span data-ttu-id="6094c-180">Apache Spark uygulama için basit bir .NET oluşturun ve çalıştırın</span><span class="sxs-lookup"><span data-stu-id="6094c-180">Build and run a simple .NET for Apache Spark application</span></span>

<span data-ttu-id="6094c-181">Daha fazla bilgi edinmek için kaynaklar sayfasına göz atın.</span><span class="sxs-lookup"><span data-stu-id="6094c-181">Check out the resources page to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="6094c-182">Apache Spark kaynakları için .NET</span><span class="sxs-lookup"><span data-stu-id="6094c-182">.NET for Apache Spark Resources</span></span>](../resources/index.md)
