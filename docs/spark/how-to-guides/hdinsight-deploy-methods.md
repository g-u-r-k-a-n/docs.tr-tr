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
# <a name="submit-a-net-for-apache-spark-job-to-azure-hdinsight"></a>Azure HDInsight 'a Apache Spark iş için .NET gönderme

Apache Spark iş için .NET uygulamanızı HDInsight 'a dağıtmanın iki yolu vardır: `spark-submit` ve Apache Livy.

## <a name="deploy-using-spark-submit"></a>Spark-gönder kullanarak dağıtma

Azure HDInsight 'a Apache Spark işleri için .NET göndermek için [Spark-gönder](https://spark.apache.org/docs/latest/submitting-applications.html) komutunu kullanabilirsiniz.

1. Azure portal HDInsight Spark kümenize gidin ve ardından **SSH + küme oturumu aç**' ı seçin.

2. SSH oturum açma bilgilerini kopyalayın ve oturumu bir terminale yapıştırın. Küme oluşturma sırasında ayarladığınız parolayı kullanarak kümenizde oturum açın. Sizi Ubuntu ve Spark 'a yönlendiren iletiler görmeniz gerekir.

3. Uygulamanızı HDInsight kümenizde çalıştırmak için **Spark-gönder** komutunu kullanın. Örnek betikteki **myContainer** ve **mystorageaccount** ' ın blob Kapsayıcınızın ve depolama hesabınızın gerçek adlarıyla değiştirilmesini unutmayın. Ayrıca, `microsoft-spark-2.3.x-0.6.0.jar` dağıtım için kullanmakta olduğunuz uygun jar dosyası ile değiştirdiğinizden emin olun. `2.3.x` Apache Spark sürümünü temsil eder ve `0.6.0` [Apache Spark Worker için .net](https://github.com/dotnet/spark/releases)sürümünü temsil eder.

   ```bash
   $SPARK_HOME/bin/spark-submit \
   --master yarn \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/microsoft-spark-2.3.x-0.6.0.jar \
   wasbs://mycontainer@mystorageaccount.blob.core.windows.net/publish.zip mySparkApp
   ```

## <a name="deploy-using-apache-livy"></a>Apache Livy kullanarak dağıtma

Apache Spark işlerini bir Azure HDInsight Spark kümesine göndermek için Apache Spark REST API [Apache Livy](https://livy.incubator.apache.org/)'ı kullanabilirsiniz. Daha fazla bilgi için bkz. [Apache Livy Ile uzak işler](/azure/hdinsight/spark/apache-spark-livy-rest-interface).

Linux 'ta aşağıdaki komutu kullanarak çalıştırabilirsiniz `curl` :

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

## <a name="next-steps"></a>Sonraki adımlar

* [Apache Spark için .NET ile çalışmaya başlama](../tutorials/get-started.md)
* [Azure HDInsight 'a bir .NET Apache Spark uygulaması dağıtma](../tutorials/hdinsight-deployment.md)
* [HDInsight belgeleri](/azure/hdinsight/)
