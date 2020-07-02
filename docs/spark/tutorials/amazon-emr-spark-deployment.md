---
title: Amazon EMR Spark için bir .NET Apache Spark uygulaması dağıtma
description: Apache Spark uygulamasının bir .NET uygulamasını Amazon EMR Spark 'a dağıtmayı öğrenin.
ms.date: 06/25/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c6cf26044693c5d923d11e1bbc72232e7009fe73
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618265"
---
# <a name="deploy-a-net-for-apache-spark-application-to-amazon-emr-spark"></a><span data-ttu-id="cf575-103">Amazon EMR Spark için bir .NET Apache Spark uygulaması dağıtma</span><span class="sxs-lookup"><span data-stu-id="cf575-103">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>

<span data-ttu-id="cf575-104">Bu öğreticide, Amazon EMR Spark 'a Apache Spark uygulamasına yönelik bir .NET dağıtımı öğretilir.</span><span class="sxs-lookup"><span data-stu-id="cf575-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Amazon EMR Spark.</span></span>

<span data-ttu-id="cf575-105">Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="cf575-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="cf575-106">Microsoft. spark. Worker 'ı hazırla</span><span class="sxs-lookup"><span data-stu-id="cf575-106">Prepare Microsoft.Spark.Worker</span></span>
> * <span data-ttu-id="cf575-107">Spark .NET uygulamanızı yayımlama</span><span class="sxs-lookup"><span data-stu-id="cf575-107">Publish your Spark .NET app</span></span>
> * <span data-ttu-id="cf575-108">Uygulamanızı Amazon EMR Spark 'a dağıtın</span><span class="sxs-lookup"><span data-stu-id="cf575-108">Deploy your app to Amazon EMR Spark</span></span>
> * <span data-ttu-id="cf575-109">Uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="cf575-109">Run your app</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a><span data-ttu-id="cf575-110">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="cf575-110">Prerequisites</span></span>

<span data-ttu-id="cf575-111">Başlamadan önce aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="cf575-111">Before you start, do the following:</span></span>

* <span data-ttu-id="cf575-112">[AWS CLI](https://aws.amazon.com/cli/)'yi indirin.</span><span class="sxs-lookup"><span data-stu-id="cf575-112">Download the [AWS CLI](https://aws.amazon.com/cli/).</span></span>
* <span data-ttu-id="cf575-113">[İnstall-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) 'i yerel makinenize indirin.</span><span class="sxs-lookup"><span data-stu-id="cf575-113">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="cf575-114">Bu, daha sonra Apache Spark bağımlı dosyaları için .NET 'i Spark kümenizin çalışan düğümlerine kopyalamak için kullandığınız bir yardımcı betiktir.</span><span class="sxs-lookup"><span data-stu-id="cf575-114">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="cf575-115">Çalışan bağımlılıklarını hazırlama</span><span class="sxs-lookup"><span data-stu-id="cf575-115">Prepare worker dependencies</span></span>

<span data-ttu-id="cf575-116">**Microsoft. spark. Worker** , Spark kümenizin ayrı çalışan düğümlerinde bulunan bir arka uç bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="cf575-116">**Microsoft.Spark.Worker** is a backend component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="cf575-117">Bir C# UDF (Kullanıcı tanımlı işlev) yürütmek istediğinizde Spark 'ın, UDF 'yi yürütmek için .NET CLR 'yi nasıl başlatacağınızı anlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf575-117">When you want to execute a C# UDF (user-defined function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="cf575-118">**Microsoft. spark. Worker** , bu Işlevi etkinleştiren Spark için bir sınıf koleksiyonu sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf575-118">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="cf575-119">Kümenize dağıtılacak bir [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp sürümü seçin.</span><span class="sxs-lookup"><span data-stu-id="cf575-119">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="cf575-120">Örneğin, `.NET for Apache Spark v0.1.0` kullanmak Istiyorsanız `netcoreapp2.1` [Microsoft. spark. Worker. netcoreapp 2.1. Linux-x64-0.1.0. tar. gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz)dosyasını indirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf575-120">For example, if you want `.NET for Apache Spark v0.1.0` using `netcoreapp2.1`, you'd download [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span></span>

2. <span data-ttu-id="cf575-121">`Microsoft.Spark.Worker.<release>.tar.gz`Kümenizin erişimi olan bir dağıtılmış dosya sistemine (ör. S3) yükleyin ve [install-Worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) .</span><span class="sxs-lookup"><span data-stu-id="cf575-121">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (e.g., S3) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="cf575-122">Apache Spark uygulamanızı .NET 'e hazırlama</span><span class="sxs-lookup"><span data-stu-id="cf575-122">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="cf575-123">Uygulamanızı derlemek için [Başlarken](get-started.md) öğreticisini izleyin.</span><span class="sxs-lookup"><span data-stu-id="cf575-123">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="cf575-124">Spark .NET uygulamanızı kendi kendine dahil olarak yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="cf575-124">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="cf575-125">Linux üzerinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cf575-125">Run the following command on Linux.</span></span>

   ```dotnetcli
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="cf575-126">`<your app>.zip`Yayımlanan dosyalar için üretin.</span><span class="sxs-lookup"><span data-stu-id="cf575-126">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="cf575-127">Kullanarak Linux üzerinde aşağıdaki komutu çalıştırın `zip` .</span><span class="sxs-lookup"><span data-stu-id="cf575-127">Run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="cf575-128">Aşağıdaki öğeleri, kümenizin erişimi olan bir dağıtılmış dosya sistemine (ör. S3) yükleyin:</span><span class="sxs-lookup"><span data-stu-id="cf575-128">Upload the following items to a distributed file system (e.g., S3) that your cluster has access to:</span></span>

   * <span data-ttu-id="cf575-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Bu jar, [Microsoft. Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet paketinin bir parçası olarak dahil edilmiştir ve uygulamanızın derleme çıkış dizininde birlikte bulunur.</span><span class="sxs-lookup"><span data-stu-id="cf575-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   * `<your app>.zip`
   * <span data-ttu-id="cf575-130">Her bir yürütücünün çalışma dizinine yerleştirilmesi için dosyalar (bağımlılık dosyaları veya her çalışan tarafından erişilebilen genel veriler gibi) veya derlemeler (Kullanıcı tanımlı işlevlerinizi veya kitaplıklarınızı içeren dll 'Ler gibi).</span><span class="sxs-lookup"><span data-stu-id="cf575-130">Files (like dependency files or common data accessible to every worker) or assemblies (like DLLs that contain your user-defined functions or libraries that your app depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-amazon-emr-spark"></a><span data-ttu-id="cf575-131">Amazon EMR Spark 'a dağıtın</span><span class="sxs-lookup"><span data-stu-id="cf575-131">Deploy to Amazon EMR Spark</span></span>

<span data-ttu-id="cf575-132">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) , AWS 'de büyük veri çerçevelerini çalıştırmayı kolaylaştıran bir yönetilen küme platformudur.</span><span class="sxs-lookup"><span data-stu-id="cf575-132">[Amazon EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html) is a managed cluster platform that simplifies running big data frameworks on AWS.</span></span>

> [!NOTE]
> <span data-ttu-id="cf575-133">Amazon EMR Spark, Linux tabanlıdır.</span><span class="sxs-lookup"><span data-stu-id="cf575-133">Amazon EMR Spark is Linux-based.</span></span> <span data-ttu-id="cf575-134">Bu nedenle, uygulamanızı Amazon EMR Spark 'a dağıtmaya ilgileniyorsanız, uygulamanızın .NET Standard uyumlu olduğundan ve uygulamanızı derlemek için [.NET Core derleyicisini](https://dotnet.microsoft.com/download) kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="cf575-134">Therefore, if you are interested in deploying your app to Amazon EMR Spark, make sure your app is .NET Standard compatible and that you use the [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="cf575-135">Microsoft. spark. Worker 'ı dağıtma</span><span class="sxs-lookup"><span data-stu-id="cf575-135">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="cf575-136">Bu adım yalnızca küme oluşturulurken gereklidir.</span><span class="sxs-lookup"><span data-stu-id="cf575-136">This step is only required at cluster creation.</span></span>

<span data-ttu-id="cf575-137">`install-worker.sh` [Önyükleme eylemlerini](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html)kullanarak küme oluşturma sırasında çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cf575-137">Run `install-worker.sh` during cluster creation using [Bootstrap Actions](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-plan-bootstrap.html).</span></span>

<span data-ttu-id="cf575-138">AWS CLı kullanarak Linux üzerinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cf575-138">Run the following command on Linux using AWS CLI.</span></span>

```bash
aws emr create-cluster \
--name "Test cluster" \
--release-label emr-5.23.0 \
--use-default-roles \
--ec2-attributes KeyName=myKey \
--applications Name=Spark \
--instance-count 3 \
--instance-type m1.medium \
--bootstrap-actions Path=s3://mybucket/<some dir>/install-worker.sh,Name="Install Microsoft.Spark.Worker",Args=["aws","s3://mybucket/<some dir>/Microsoft.Spark.Worker.<release>.tar.gz","/usr/local/bin"]
```

## <a name="run-your-app"></a><span data-ttu-id="cf575-139">Uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="cf575-139">Run your app</span></span>

<span data-ttu-id="cf575-140">Bu uygulamayı Amazon EMR Spark: Spark-gönderme ve Amazon EMR adımlarında çalıştırmanın iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="cf575-140">There are two ways to run your app in Amazon EMR Spark: spark-submit and Amazon EMR Steps.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="cf575-141">Spark-gönder kullan</span><span class="sxs-lookup"><span data-stu-id="cf575-141">Use spark-submit</span></span>

<span data-ttu-id="cf575-142">[Spark-gönder](https://spark.apache.org/docs/latest/submitting-applications.html) komutunu kullanarak, Amazon emr spark 'a Apache Spark işleri için .net gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf575-142">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Amazon EMR Spark.</span></span>

1. <span data-ttu-id="cf575-143">`ssh`Kümedeki düğümlerden birine.</span><span class="sxs-lookup"><span data-stu-id="cf575-143">`ssh` into one of the nodes in the cluster.</span></span>

2. <span data-ttu-id="cf575-144">`spark-submit` öğesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cf575-144">Run `spark-submit`.</span></span>

   ```bash
   spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --files <comma-separated list of assemblies that contain UDF definitions, if any> \
   s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar \
   s3://mybucket/<some dir>/<your app>.zip <your app> <app args>
   ```

### <a name="use-amazon-emr-steps"></a><span data-ttu-id="cf575-145">Amazon EMR adımlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="cf575-145">Use Amazon EMR Steps</span></span>

<span data-ttu-id="cf575-146">[Amazon emr adımları](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) , BIR ışı emr kümesinde yüklü Spark çerçevesine göndermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cf575-146">[Amazon EMR Steps](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-spark-submit-step.html) can be used to submit jobs to the Spark framework installed on the EMR cluster.</span></span>

<span data-ttu-id="cf575-147">AWS CLı kullanarak Linux üzerinde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cf575-147">Run the following command on Linux using AWS CLI.</span></span>

```bash
aws emr add-steps \
--cluster-id j-xxxxxxxxxxxxx \
--steps Type=spark,Name="Spark Program",Args=[--master,yarn,--files,s3://mybucket/<some dir>/<udf assembly>,--class,org.apache.spark.deploy.dotnet.DotnetRunner,s3://mybucket/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar,s3://mybucket/<some dir>/<your app>.zip,<your app>,<app arg 1>,<app arg 2>,...,<app arg n>],ActionOnFailure=CONTINUE
```

## <a name="next-steps"></a><span data-ttu-id="cf575-148">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="cf575-148">Next steps</span></span>

<span data-ttu-id="cf575-149">Bu öğreticide, Apache Spark için .NET uygulamanızı Amazon EMR Spark 'a dağıttınız.</span><span class="sxs-lookup"><span data-stu-id="cf575-149">In this tutorial, you deployed your .NET for Apache Spark application to Amazon EMR Spark.</span></span> <span data-ttu-id="cf575-150">Apache Spark örnek projelerine yönelik .NET için GitHub ' a devam edin.</span><span class="sxs-lookup"><span data-stu-id="cf575-150">For .NET for Apache Spark example projects, continue to GitHub.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cf575-151">Apache Spark örnekleri için .NET</span><span class="sxs-lookup"><span data-stu-id="cf575-151">.NET for Apache Spark samples</span></span>](https://github.com/dotnet/spark/tree/master/examples)
