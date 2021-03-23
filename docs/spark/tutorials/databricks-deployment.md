---
title: Databricks 'e Apache Spark uygulamasına yönelik bir .NET dağıtımı
description: Databricks 'e Apache Spark uygulamasının bir .NET uygulamasını nasıl dağıtacağınızı öğrenin.
ms.date: 10/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e751953937279a5f9f78f777bac8a5ca510a2f87
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876974"
---
# <a name="tutorial-deploy-a-net-for-apache-spark-application-to-databricks"></a>Öğretici: Databricks 'e Apache Spark uygulamasına yönelik bir .NET dağıtımı

Bu öğreticide, tek tıklamayla kurulum, kolaylaştırılmış iş akışları ve işbirliği sağlayan etkileşimli çalışma alanı ile Apache Spark tabanlı bir analiz platformu olan Azure Databricks aracılığıyla Uygulamanızı buluta nasıl dağıtabileceğiniz öğretilir.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
>
> - Azure Databricks çalışma alanı oluşturun.
> - Apache Spark için .NET uygulamanızı yayımlayın.
> - Spark işi ve Spark kümesi oluşturun.
> - Uygulamanızı Spark kümesinde çalıştırın.

## <a name="prerequisites"></a>Önkoşullar

Başlamadan önce, aşağıdaki görevleri yapın:

* Azure hesabınız yoksa [ücretsiz bir hesap](https://azure.microsoft.com/free/dotnet/)oluşturun.
* [Azure portalında](https://portal.azure.com/) oturum açın.
* [Apache Spark için .net ' i doldurun-10 dakikalık öğreticide kullanmaya başlayın](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) .

## <a name="create-an-azure-databricks-workspace"></a>Azure Databricks çalışma alanı oluşturma

> [!Note]
> Bu öğretici **Azure Ücretsiz deneme aboneliği** kullanılarak gerçekleştirilemez.
> Ücretsiz hesabınız varsa, profilinize gidin ve aboneliğinizi **Kullandıkça Öde** ile değiştirin. Daha fazla bilgi için bkz. [Ücretsiz Azure hesabı](https://azure.microsoft.com/free/dotnet/). Ardından, [harcama limitini kaldırın](/azure/billing/billing-spending-limit#why-you-might-want-to-remove-the-spending-limit)ve bölgenizdeki vCPU 'lar için [bir kota artışı isteyin](/azure/azure-supportability/resource-manager-core-quotas-request) . Azure Databricks çalışma alanınızı oluşturduğunuzda, çalışma alanına 14 gün boyunca ücretsiz Premium Azure Databricks DBUs erişimi sağlamak için **deneme (Premium-14 gün ücretsiz DBUs)** fiyatlandırma katmanını seçebilirsiniz.

Bu bölümde Azure portalını kullanarak bir Azure Databricks çalışma alanı oluşturursunuz.

1. Azure Portal, **kaynak**  >  **Analizi** oluştur  >  **Azure Databricks**' u seçin.

   ![Azure portal Azure Databricks kaynak oluşturma](./media/databricks-deployment/create-databricks-resource.png)

2. **Azure Databricks Hizmeti** bölümünde, Databricks çalışma alanı oluşturmak için değerler sağlayın.

    |Özellik  |Açıklama  |
    |---------|---------|
    |**Çalışma alanı adı**     | Databricks çalışma alanınız için bir ad sağlayın.        |
    |**Abonelik**     | Açılan listeden Azure aboneliğinizi seçin.        |
    |**Kaynak grubu**     | Yeni bir kaynak grubu oluşturmayı veya mevcut bir kaynak grubunu kullanmayı seçin. Kaynak grubu, bir Azure çözümüne ilişkin kaynakları tutan bir kapsayıcıdır. Daha fazla bilgi için bkz. [Azure Kaynak Grubuna genel bakış](/azure/azure-resource-manager/resource-group-overview). |
    |**Konum**     | Tercih ettiğiniz bölgeyi seçin. Kullanılabilir bölgeler hakkında daha fazla bilgi için bkz. [bölgeye göre kullanılabilir Azure hizmetleri](https://azure.microsoft.com/regions/services/).        |
    |**Fiyatlandırma Katmanı**     |  **Standart**, **Premium** veya **deneme** arasında seçim yapın. Bu katmanlar hakkında daha fazla bilgi için bkz. [Databricks fiyatlandırma sayfası](https://azure.microsoft.com/pricing/details/databricks/).       |
    |**Sanal Ağ**     |   Hayır       |

3. **Oluştur**’u seçin. Çalışma alanının oluşturulması birkaç dakika sürer. Çalışma alanı oluşturma sırasında, **Bildirimler**' de dağıtım durumunu görüntüleyebilirsiniz.

## <a name="install-azure-databricks-tools"></a>Azure Databricks araçları 'nı yükler

**Databricks CLI** kullanarak Azure Databricks kümelerine bağlanabilir ve dosyaları yerel makinenizden bunlara yükleyebilirsiniz. Databricks kümeleri, DBFS (Databricks dosya sistemi) üzerinden dosyalara erişim.

1. Databricks CLı, Python 3,6 veya üstünü gerektirir. Zaten Python yüklüyse, bu adımı atlayabilirsiniz.

   **Windows için:**

   [Windows için Python indirin](https://www.python.org/ftp/python/3.7.4/python-3.7.4.exe)

   **Linux için:** Python, çoğu Linux dağıtımlarına önceden yüklenmiş olarak gelir. Hangi sürümü yüklecağınızı görmek için aşağıdaki komutu çalıştırın:

   ```bash
   python3 --version
   ```

2. Databricks CLı 'yı yüklemek için PIP kullanın. Python 3,4 ve üzeri, varsayılan olarak PIP 'yi içerir. Python 3 için pip3 kullanın. Şu komutu çalıştırın:

   ```bash
   pip3 install databricks-cli
   ```

3. Databricks CLı 'yı yükledikten sonra, yeni bir komut istemi açın ve komutunu çalıştırın `databricks` . **' Databricks ' bir iç veya dış komut hatası olarak tanınmazsa**, yeni bir komut istemi açtığınızdan emin olun.

## <a name="set-up-azure-databricks"></a>Azure Databricks ayarlama

Databricks CLı yükleolduğunuza göre, kimlik doğrulama ayrıntılarını ayarlamanız gerekir.

1. Databricks CLı komutunu çalıştırın `databricks configure --token` .

2. Configure komutunu çalıştırdıktan sonra, bir ana bilgisayar girmeniz istenir. Ana bilgisayar URL 'niz şu biçimi kullanır: `https://<Location>.azuredatabricks.net` . Örneğin, Azure Databricks hizmeti oluşturma sırasında **eastus2** ' ı seçtiyseniz, konak olur `https://eastus2.azuredatabricks.net` .

3. Ana bilgisayarınızı girdikten sonra bir belirteç girmeniz istenir. Azure portal, Azure Databricks çalışma alanınızı başlatmak için **çalışma alanını Başlat** ' ı seçin.

   ![Azure Databricks çalışma alanını Başlat](./media/databricks-deployment/launch-databricks-workspace.png)

4. Çalışma alanınızın giriş sayfasında **Kullanıcı ayarları**' nı seçin.

   ![Azure Databricks çalışma alanındaki Kullanıcı ayarları](./media/databricks-deployment/databricks-user-settings.png)

5. Kullanıcı ayarları sayfasında, yeni bir belirteç oluşturabilirsiniz. Oluşturulan belirteci kopyalayın ve komut isteminize geri yapıştırın.

   ![Azure Databricks çalışma alanında yeni erişim belirteci oluştur](./media/databricks-deployment/generate-token.png)

Artık oluşturduğunuz Azure Databricks kümelerine erişebiliyor ve dosyaları DBFS 'ye yükleyeceksiniz.

## <a name="download-worker-dependencies"></a>Çalışan bağımlılıklarını indir

> [!Note]
> Azure ve AWS Databricks, Linux tabanlıdır. Bu nedenle, uygulamanızı Databricks 'e dağıtmaya ilgileniyorsanız, uygulamanızın .NET Standard uyumlu olduğundan ve uygulamanızı derlemek için .NET Core derleyicisi kullandığınızdan emin olun.

1. Microsoft. spark. Worker, yazdığınız kullanıcı tanımlı işlevler (UDF 'ler) gibi uygulamanızı Apache Spark yürütmenize yardımcı olur. [Microsoft. spark. Worker](https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz)öğesini indirin.

2. *İnstall-Worker.sh* , Apache Spark bağımlı dosyaları için .net ' i kümenizin düğümlerine kopyalamanızı sağlayan bir betiktir.

   Yerel bilgisayarınızda **install-Worker.sh** adlı yeni bir dosya oluşturun ve GitHub 'da bulunan [install-Worker.sh içeriğini](https://raw.githubusercontent.com/dotnet/spark/main/deployment/install-worker.sh) yapıştırın.

3. *DB-init.sh* , Databricks Spark kümenize bağımlılıklar yükleyen bir betiktir.

   Yerel bilgisayarınızda **DB-init.sh** adlı yeni bir dosya oluşturun ve GitHub 'da bulunan [DB-init.sh içeriğini](https://github.com/dotnet/spark/blob/main/deployment/db-init.sh) yapıştırın.

   Yeni oluşturduğunuz dosyada, `DOTNET_SPARK_RELEASE` değişkenini olarak ayarlayın `https://github.com/dotnet/spark/releases/download/v1.0.0/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz` . *DB-init.sh* dosyasının kalan kısmını olduğu gibi bırakın.

> [!Note]
> Windows kullanıyorsanız, *install-Worker.sh* ve *DB-init.sh* betiklerinizde yer alan satır SONLARıNı UNIX stili (LF) olduğunu doğrulayın. Satır sonlarını notepad + + ve atom gibi metin düzenleyicilerle değiştirebilirsiniz.

## <a name="publish-your-app"></a>Uygulamanızı yayımlama

Daha sonra, Spark kümenizin uygulamanızı çalıştırmak için gereken tüm dosyalara erişebildiğinden emin olmak için, Apache Spark .NET sürümünde oluşturulan *mySparkApp* [-Get ile çalışmaya](https://dotnet.microsoft.com/learn/data/spark-tutorial/intro) başlayın.

1. *MySparkApp* yayımlamak için aşağıdaki komutları çalıştırın:

   ```dotnetcli
   cd mySparkApp
   dotnet publish -c Release -f netcoreapp3.1 -r ubuntu.16.04-x64
   ```

2. Dosyaları Databricks Spark kümenize kolayca yükleyebilmeniz için, yayımlanan uygulama dosyalarınızı Zip halinde aşağıdaki görevleri yapın.

   **Windows 'da:**

   MySparkApp/bin/Release/netcoreapp 3.1/Ubuntu. 16.04-x64 dizinine gidin. Ardından, **Yayımla** klasörüne sağ tıklayıp **> sıkıştırılmış (daraltılmış) klasöre gönder**' i seçin. Yeni klasörü **publish.zip** olarak adlandırın.

   **Linux 'ta aşağıdaki komutu çalıştırın:**

   ```bash
   zip -r publish.zip .
   ```

## <a name="upload-files"></a>Dosyaları karşıya yükleme

Bu bölümde, kümenizin uygulamanızı bulutta çalıştırması için gereken her şeyin olması için birkaç dosyayı DBFS 'ye yüklersiniz. DBFS 'ye bir dosya yüklediğinizde, dosyanın bilgisayarınızda bulunduğu dizinde olduğunuzdan emin olun.

1. *DB-init.sh*, *install-Worker.sh* ve *Microsoft. spark. Worker* öğesini dBFS 'ye yüklemek için aşağıdaki komutları çalıştırın:

   ```console
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   databricks fs cp Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz dbfs:/spark-dotnet/Microsoft.Spark.Worker.netcoreapp3.1.linux-x64-1.0.0.tar.gz
   ```

2. Geri kalan dosyaları karşıya yüklemek için aşağıdaki komutları çalıştırın: kümenizin uygulamanızı çalıştırması gerekecektir: daraltılmış yayımlama klasörü, *input.txt* ve *Microsoft-Spark-2-4_ 2.11-1.0.0. jar*.

   ```console
   cd mySparkApp
   databricks fs cp input.txt dbfs:/input.txt

   cd mySparkApp\bin\Release\netcoreapp3.1\ubuntu.16.04-x64 directory
   databricks fs cp publish.zip dbfs:/spark-dotnet/publish.zip
   databricks fs cp microsoft-spark-2-4_2.11-1.0.0.jar dbfs:/spark-dotnet/microsoft-spark-2-4_2.11-1.0.0.jar
   ```

## <a name="create-a-job"></a>Bir iş oluşturma

Uygulamanız, Apache Spark işleri için .NET çalıştırmak için kullandığınız komut olan **Spark-gönder** çalıştıran bir iş aracılığıyla Azure Databricks çalışır.

1. Azure Databricks çalışma alanınızda **işler** simgesini ve ardından **+ iş oluştur**' u seçin.

   ![Azure Databricks işi oluşturma](./media/databricks-deployment/create-job.png)

2. İşiniz için bir başlık seçin ve ardından **Spark-gönder**' i seçin.

   ![Databricks için Spark-göndermeyi yapılandırma işi](./media/databricks-deployment/configure-spark-submit.png)

3. Aşağıdaki parametreleri iş yapılandırmasına yapıştırın. Ardından **Onayla**' yı seçin.

   ```
   ["--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/spark-dotnet/microsoft-spark-2-4_2.11-1.0.0.jar","/dbfs/spark-dotnet/publish.zip","mySparkApp"]
   ```

## <a name="create-a-cluster"></a>Küme oluşturma

1. İşinizin kümesini yapılandırmak için işinize gidin ve **Düzenle** ' yi seçin.

2. Kümenizi **Spark 2.4.1** olarak ayarlayın. Ardından **Gelişmiş Seçenekler**  >  **Başlangıç betikleri**' ni seçin. Init betiği yolunu olarak ayarlayın `dbfs:/spark-dotnet/db-init.sh` .

   ![Azure Databricks Spark kümesini yapılandırma](./media/databricks-deployment/cluster-config.png)

3. Küme ayarlarınızı onaylamak için **Onayla** ' yı seçin.

## <a name="run-your-app"></a>Uygulamanızı çalıştırma

1. İşinizi yeni yapılandırılmış Spark kümenizde çalıştırmak için işinize gidin ve **Şimdi Çalıştır** ' ı seçin.

2. İş kümesinin oluşturulması birkaç dakika sürer. Oluşturulduktan sonra işiniz gönderilir ve çıktıyı görüntüleyebilirsiniz.

3. Sol menüden **kümeler** ' ı, sonra da işinizin adını ve çalıştırmayı seçin.

4. İşinizin çıkışını görüntülemek için **sürücü günlükleri** ' ni seçin. Uygulamanız yürütmeyi bitirdiğinde, başlangıç yerel çalıştırmasından standart çıkış konsoluna yazılan aynı sözcük sayısı tablosunu görürsünüz.

   ![Azure Databricks iş çıkış tablosu](./media/databricks-deployment/table-output.png)

   Tebrikler, ilk .NET Apache Spark uygulamanızı Azure Databricks ' de çalıştırırsınız!

## <a name="clean-up-resources"></a>Kaynakları temizleme

Artık Databricks çalışma alanına ihtiyacınız yoksa, Azure portal Azure Databricks kaynağını silebilirsiniz. Kaynak grubu adını seçerek de kaynak grubu sayfasını açabilir ve sonra **Kaynak grubunu sil**’i seçebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, Apache Spark için .NET uygulamanızı Databricks 'e dağıttınız. Databricks hakkında daha fazla bilgi edinmek için Azure Databricks belgelerine ilerleyin.

> [!div class="nextstepaction"]
> [Azure Databricks Belgeleri](/azure/azure-databricks/)
