---
title: Azure HDInsight 'a Apache Spark iş için .NET gönderme
description: Spark-gönder ve Apache Livy kullanarak Azure HDInsight 'a Apache Spark iş için .NET gönderme hakkında bilgi edinin.
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: cb99cd8028d504924d2dd69910efed0065d0a2e2
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91954925"
---
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a><span data-ttu-id="68f1f-103">Azure HDInsight 'a Apache Spark iş için .NET gönderme</span><span class="sxs-lookup"><span data-stu-id="68f1f-103">Submit a .NET for Apache Spark job to Azure HDInsight</span></span>

<span data-ttu-id="68f1f-104">Apache Spark iş için .NET uygulamanızı HDInsight 'a dağıtmanın iki yolu vardır: `spark-submit` ve Apache Livy.</span><span class="sxs-lookup"><span data-stu-id="68f1f-104">There are two ways to deploy your .NET for Apache Spark job to HDInsight: `spark-submit` and Apache Livy.</span></span>

## <a name="deploy-using-spark-submit"></a><span data-ttu-id="68f1f-105">Spark-gönder kullanarak dağıtma</span><span class="sxs-lookup"><span data-stu-id="68f1f-105">Deploy using spark-submit</span></span>

<span data-ttu-id="68f1f-106">Azure HDInsight 'a Apache Spark işleri için .NET göndermek için [Spark-gönder](https://spark.apache.org/docs/latest/submitting-applications.html) komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68f1f-106">You can use the [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command to submit .NET for Apache Spark jobs to Azure HDInsight.</span></span>

1. <span data-ttu-id="68f1f-107">Azure portal HDInsight Spark kümenize gidin ve ardından **SSH + küme oturumu aç**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="68f1f-107">Navigate to your HDInsight Spark cluster in Azure portal, and then select **SSH + Cluster login**.</span></span>

2. <span data-ttu-id="68f1f-108">SSH oturum açma bilgilerini kopyalayın ve oturumu bir terminale yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="68f1f-108">Copy the ssh login information and paste the login into a terminal.</span></span> <span data-ttu-id="68f1f-109">Küme oluşturma sırasında ayarladığınız parolayı kullanarak kümenizde oturum açın.</span><span class="sxs-lookup"><span data-stu-id="68f1f-109">Sign in to your cluster using the password you set during cluster creation.</span></span> <span data-ttu-id="68f1f-110">Sizi Ubuntu ve Spark 'a yönlendiren iletiler görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="68f1f-110">You should see messages welcoming you to Ubuntu and Spark.</span></span>

3. <span data-ttu-id="68f1f-111">Uygulamanızı HDInsight kümenizde çalıştırmak için **Spark-gönder** komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="68f1f-111">Use the **spark-submit** command to run your app on your HDInsight cluster.</span></span> <span data-ttu-id="68f1f-112">Örnek betikteki **myContainer** ve **mystorageaccount** ' ın blob Kapsayıcınızın ve depolama hesabınızın gerçek adlarıyla değiştirilmesini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="68f1f-112">Remember to replace **mycontainer** and **mystorageaccount** in the example script with the actual names of your blob container and storage account.</span></span> <span data-ttu-id="68f1f-113">Ayrıca, `microsoft-spark-2.3.x-0.6.0.jar` dağıtım için kullanmakta olduğunuz uygun jar dosyası ile değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="68f1f-113">Also, be sure to replace `microsoft-spark-2.3.x-0.6.0.jar` with the appropriate jar file you're using for deployment.</span></span> <span data-ttu-id="68f1f-114">`2.3.x` Apache Spark sürümünü temsil eder ve `0.6.0` [Apache Spark Worker için .net](https://github.com/dotnet/spark/releases)sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="68f1f-114">`2.3.x` represents the version of Apache Spark, and `0.6.0` represents the version of the [.NET for Apache Spark worker](https://github.com/dotnet/spark/releases).</span></span>

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a><span data-ttu-id="68f1f-115">Apache Livy kullanarak dağıtma</span><span class="sxs-lookup"><span data-stu-id="68f1f-115">Deploy using Apache Livy</span></span>

<span data-ttu-id="68f1f-116">Apache Spark işlerini bir Azure HDInsight Spark kümesine göndermek için Apache Spark REST API [Apache Livy](https://livy.incubator.apache.org/)'ı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68f1f-116">You can use [Apache Livy](https://livy.incubator.apache.org/), the Apache Spark REST API, to submit .NET for Apache Spark jobs to an Azure HDInsight Spark cluster.</span></span> <span data-ttu-id="68f1f-117">Daha fazla bilgi için bkz. [Apache Livy Ile uzak işler](/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span><span class="sxs-lookup"><span data-stu-id="68f1f-117">For more information, see [Remote jobs with Apache Livy](/azure/hdinsight/spark/apache-spark-livy-rest-interface).</span></span>

<span data-ttu-id="68f1f-118">Linux 'ta aşağıdaki komutu kullanarak çalıştırabilirsiniz `curl` :</span><span class="sxs-lookup"><span data-stu-id="68f1f-118">You can run the following command on Linux using `curl`:</span></span>

```bash
curl -k -v -X POST "https://<your spark cluster>.azurehdinsight.net/livy/batches" \
-u "<hdinsight username>:<hdinsight password>" \
-H "Content-Type: application/json" \
-H "X-Requested-By: <hdinsight username>" \
-d @- << EOF
{
    "file":"abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar",
    "className":"org.apache.spark.deploy.dotnet.DotnetRunner",
    "files":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<udf assembly>", "abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<file>"],
    "args":["abfss://<your-file-system-name>@<your-storage-account-name>.dfs.core.windows.net/<some dir>/<your app>.zip","<your app>","<app arg 1>","<app arg 2>,"...","<app arg n>"]
}
EOF
```

## <a name="next-steps"></a><span data-ttu-id="68f1f-119">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="68f1f-119">Next steps</span></span>

* [<span data-ttu-id="68f1f-120">Apache Spark için .NET ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="68f1f-120">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="68f1f-121">Azure HDInsight 'a bir .NET Apache Spark uygulaması dağıtma</span><span class="sxs-lookup"><span data-stu-id="68f1f-121">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="68f1f-122">HDInsight belgeleri</span><span class="sxs-lookup"><span data-stu-id="68f1f-122">HDInsight Documentation</span></span>](/azure/hdinsight/)
