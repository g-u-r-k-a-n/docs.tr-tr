---
title: 'Nasıl yapılır: İzleme Anahtarları Oluşturma ve Başlatma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace switches, configuring
- tracing [.NET Framework], trace switches
- switches, trace
- tracing [.NET Framework], enabling or disabling
- Web.config configuration file, trace switches
ms.assetid: 5a0e41bf-f99c-4692-8799-f89617f5bcf9
ms.openlocfilehash: 358e34b2ce5d896ba02b343ce060604f2d42eeeb
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216484"
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a><span data-ttu-id="67e4f-102">Nasıl yapılır: İzleme Anahtarları Oluşturma ve Başlatma</span><span class="sxs-lookup"><span data-stu-id="67e4f-102">How to: Create, Initialize and Configure Trace Switches</span></span>
<span data-ttu-id="67e4f-103">İzleme anahtarları, izleme çıkışını etkinleştirmenizi, devre dışı bırakmanızı ve filtrelemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="67e4f-103">Trace switches enable you to enable, disable, and filter tracing output.</span></span>  
  
<a name="create"></a>   
## <a name="creating-and-initializing-a-trace-switch"></a><span data-ttu-id="67e4f-104">İzleme anahtarı oluşturma ve başlatma</span><span class="sxs-lookup"><span data-stu-id="67e4f-104">Creating and initializing a trace switch</span></span>  
 <span data-ttu-id="67e4f-105">İzleme anahtarlarını kullanmak için, önce bunları oluşturmanız ve kodunuza yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="67e4f-105">In order to use trace switches, you must first create them and place them in your code.</span></span> <span data-ttu-id="67e4f-106">Anahtar nesneleri oluşturabileceğiniz iki önceden tanımlı sınıf vardır: <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> sınıfı ve <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="67e4f-106">There are two predefined classes from which you can create switch objects: the <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> class and the <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="67e4f-107">Yalnızca bir izleme iletisinin görünüp edilmeyeceğini düşünüyorsanız <xref:System.Diagnostics.BooleanSwitch> kullanırsınız; izleme düzeylerini ayırt etmek istiyorsanız <xref:System.Diagnostics.TraceSwitch> kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="67e4f-107">You would use <xref:System.Diagnostics.BooleanSwitch> if you care only about whether or not a tracing message appears; you would use <xref:System.Diagnostics.TraceSwitch> if you want to discriminate between levels of tracing.</span></span> <span data-ttu-id="67e4f-108"><xref:System.Diagnostics.TraceSwitch>kullanıyorsanız, kendi hata ayıklama iletilerinizi tanımlayabilir ve bunları farklı izleme düzeyleriyle ilişkilendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67e4f-108">If you use a <xref:System.Diagnostics.TraceSwitch>, you can define your own debugging messages and associate them with different trace levels.</span></span> <span data-ttu-id="67e4f-109">İzleme veya hata ayıklama ile her iki anahtar türünü de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67e4f-109">You can use both types of switches with either tracing or debugging.</span></span> <span data-ttu-id="67e4f-110">Varsayılan olarak, bir <xref:System.Diagnostics.BooleanSwitch> devre dışıdır ve <xref:System.Diagnostics.TraceSwitch> düzey <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="67e4f-110">By default, a <xref:System.Diagnostics.BooleanSwitch> is disabled and a <xref:System.Diagnostics.TraceSwitch> is set to level <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="67e4f-111">İzleme anahtarları, kodunuzun bunları kullanan herhangi bir kısmına oluşturulabilir ve eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="67e4f-111">Trace switches can be created and placed in any part of your code that might use them.</span></span>  
  
 <span data-ttu-id="67e4f-112">Koddaki izleme düzeylerini ve diğer yapılandırma seçeneklerini ayarlayabilmenize karşın, anahtarlarınızın durumunu yönetmek için yapılandırma dosyasını kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="67e4f-112">Although you can set trace levels and other configuration options in code, we recommend that you use the configuration file to manage the state of your switches.</span></span> <span data-ttu-id="67e4f-113">Bunun nedeni, yapılandırma sistemindeki anahtarlarınızın yapılandırılmasını yönetmenin daha fazla esneklik sağladığından, uygulamanızı yeniden derlemeden çeşitli anahtarları açıp kapamenize ve seviyelerini değiştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="67e4f-113">This is because managing the configuration of your switches in the configuration system gives you greater flexibility — you can turn on and off various switches and change levels without recompiling your application.</span></span>  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a><span data-ttu-id="67e4f-114">Bir izleme anahtarı oluşturmak ve başlatmak için</span><span class="sxs-lookup"><span data-stu-id="67e4f-114">To create and initialize a trace switch</span></span>  
  
1. <span data-ttu-id="67e4f-115"><xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> tür olarak bir anahtar tanımlayın veya <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> yazın ve anahtarın adını ve açıklamasını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="67e4f-115">Define a switch as either type <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> or type <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> and set the name and description of the switch.</span></span>  
  
2. <span data-ttu-id="67e4f-116">İzleme anahtarını yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="67e4f-116">Configure your trace switch.</span></span> <span data-ttu-id="67e4f-117">Daha fazla bilgi için bkz. [izleme anahtarlarını yapılandırma](#configure).</span><span class="sxs-lookup"><span data-stu-id="67e4f-117">For more information, see [Configuring trace switches](#configure).</span></span>  
  
     <span data-ttu-id="67e4f-118">Aşağıdaki kod, her türden biri olmak üzere iki anahtar oluşturur:</span><span class="sxs-lookup"><span data-stu-id="67e4f-118">The following code creates two switches, one of each type:</span></span>  
  
    ```vb  
    Dim dataSwitch As New BooleanSwitch("Data", "DataAccess module")  
    Dim generalSwitch As New TraceSwitch("General", "Entire application")  
    ```  
  
    ```csharp  
    System.Diagnostics.BooleanSwitch dataSwitch =   
       new System.Diagnostics.BooleanSwitch("Data", "DataAccess module");  
    System.Diagnostics.TraceSwitch generalSwitch =   
       new System.Diagnostics.TraceSwitch("General",   
       "Entire application");  
    ```  
  
<a name="configure"></a>   
## <a name="configuring-trace-switches"></a><span data-ttu-id="67e4f-119">İzleme anahtarlarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="67e4f-119">Configuring trace switches</span></span>  
 <span data-ttu-id="67e4f-120">Uygulamanız dağıtıldıktan sonra, uygulamanızdaki izleme anahtarlarını yapılandırarak izleme çıkışını etkinleştirebilir veya devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67e4f-120">After your application has been distributed, you can still enable or disable trace output by configuring the trace switches in your application.</span></span> <span data-ttu-id="67e4f-121">Bir anahtarı yapılandırmak, başlatıldıktan sonra bir dış kaynaktan değerini değiştirmenin anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="67e4f-121">Configuring a switch means changing its value from an external source after it has been initialized.</span></span> <span data-ttu-id="67e4f-122">Yapılandırma dosyasını kullanarak Switch nesnelerinin değerlerini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67e4f-122">You can change the values of the switch objects using the configuration file.</span></span> <span data-ttu-id="67e4f-123">Bir izleme anahtarını açmak ve kapatmak için ya da düzeyini ayarlamak için, dinleyicilerinin yanı sıra aktardığı iletilerin miktarını ve türünü belirlemek için yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="67e4f-123">You configure a trace switch to turn it on and off, or to set its level, determining the amount and type of messages it passes along to listeners.</span></span>  
  
 <span data-ttu-id="67e4f-124">Anahtarlarınız. config dosyası kullanılarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="67e4f-124">Your switches are configured using the .config file.</span></span> <span data-ttu-id="67e4f-125">Bir Web uygulaması için, bu, projeyle ilişkili Web. config dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="67e4f-125">For a Web application, this is the Web.config file associated with the project.</span></span> <span data-ttu-id="67e4f-126">Bir Windows uygulamasında, bu dosya (uygulama adı). exe. config olarak adlandırılır. Dağıtılan bir uygulamada, bu dosya çalıştırılabilirle aynı klasörde bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="67e4f-126">In a Windows application, this file is named (application name).exe.config. In a deployed application, this file must reside in the same folder as the executable.</span></span>  
  
 <span data-ttu-id="67e4f-127">Uygulamanız bir anahtarın bir örneğini ilk kez oluşturan kodu yürüttüğünde, bu, adlandırılmış anahtarla ilgili izleme düzeyi bilgileri için yapılandırma dosyasını denetler.</span><span class="sxs-lookup"><span data-stu-id="67e4f-127">When your application executes the code that creates an instance of a switch for the first time, it checks the configuration file for trace-level information about the named switch.</span></span> <span data-ttu-id="67e4f-128">İzleme sistemi, uygulama anahtarı ilk kez oluşturduğunda yapılandırma dosyasını belirli bir anahtar için yalnızca bir kez inceler.</span><span class="sxs-lookup"><span data-stu-id="67e4f-128">The tracing system examines the configuration file only once for any particular switch — the first time your application creates the switch.</span></span>  
  
 <span data-ttu-id="67e4f-129">Dağıtılmış bir uygulamada, uygulamanız çalışmadığı zaman geçiş nesnelerini yeniden yapılandırarak izleme kodunu etkinleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67e4f-129">In a deployed application, you enable trace code by reconfiguring switch objects when your application is not running.</span></span> <span data-ttu-id="67e4f-130">Genellikle bu, anahtar nesnelerinin açık ve kapalı olduğunu ya da izleme düzeylerini değiştirerek ve sonra uygulamanızı yeniden başlatarak içerir.</span><span class="sxs-lookup"><span data-stu-id="67e4f-130">Typically this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>  
  
 <span data-ttu-id="67e4f-131">Anahtarın bir örneğini oluşturduğunuzda, iki bağımsız değişken belirterek de başlatabilirsiniz: *DisplayName* bağımsız değişkeni ve bir *Açıklama* bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="67e4f-131">When you create an instance of a switch, you also initialize it by specifying two arguments: a *displayName* argument and a *description* argument.</span></span> <span data-ttu-id="67e4f-132">Oluşturucunun *DisplayName* bağımsız değişkeni, <xref:System.Diagnostics.Switch> sınıf örneğinin <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> özelliğini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="67e4f-132">The *displayName* argument of the constructor sets the <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> property of the <xref:System.Diagnostics.Switch> class instance.</span></span> <span data-ttu-id="67e4f-133">*DisplayName* ,. config dosyasında anahtarı yapılandırmak için kullanılan addır ve *Açıklama* bağımsız değişkeni, anahtarın kısa bir açıklamasını ve hangi iletileri denetlediğini döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="67e4f-133">The *displayName* is the name that is used to configure the switch in the .config file, and the *description* argument should return a brief description of the switch and what messages it controls.</span></span>  
  
 <span data-ttu-id="67e4f-134">Yapılandırılacak anahtarın adını belirtmenin yanı sıra, anahtar için de bir değer belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="67e4f-134">In addition to specifying the name of a switch to configure, you must also specify a value for the switch.</span></span> <span data-ttu-id="67e4f-135">Bu değer bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="67e4f-135">This value is an Integer.</span></span> <span data-ttu-id="67e4f-136"><xref:System.Diagnostics.BooleanSwitch>için 0 değeri **kapalı**ve sıfır dışında bir değer **Açık**öğesine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="67e4f-136">For <xref:System.Diagnostics.BooleanSwitch>, a value of 0 corresponds to **Off**, and any nonzero value corresponds to **On**.</span></span> <span data-ttu-id="67e4f-137"><xref:System.Diagnostics.TraceSwitch>, 0, 1, 2, 3 ve 4 için sırasıyla **kapalı**, **hata**, **Uyarı**, **bilgi**ve **ayrıntılıdır**.</span><span class="sxs-lookup"><span data-stu-id="67e4f-137">For <xref:System.Diagnostics.TraceSwitch>, 0,1,2,3, and 4 correspond **Off**, **Error**, **Warning**, **Info**, and **Verbose**, respectively.</span></span> <span data-ttu-id="67e4f-138">4 ' ten büyük herhangi bir sayı **verbose**olarak değerlendirilir ve sıfırdan küçük herhangi bir sayı **kapalı**olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="67e4f-138">Any number greater than 4 is treated as **Verbose**, and any number less than zero is treated as **Off**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="67e4f-139">.NET Framework sürüm 2,0 ' de, bir anahtarın değerini belirtmek için metin kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67e4f-139">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="67e4f-140">Örneğin, bir <xref:System.Diagnostics.BooleanSwitch> veya bir <xref:System.Diagnostics.TraceSwitch>için `Error` gibi bir numaralandırma değerini temsil eden metin için `true`.</span><span class="sxs-lookup"><span data-stu-id="67e4f-140">For example, `true` for a <xref:System.Diagnostics.BooleanSwitch> or the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="67e4f-141">Satır `<add name="myTraceSwitch" value="Error" />` `<add name="myTraceSwitch" value="1" />`eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="67e4f-141">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
 <span data-ttu-id="67e4f-142">Son kullanıcıların bir uygulamanın izleme anahtarlarını yapılandırabilmesi için uygulamanızdaki anahtarlara ayrıntılı belgeler sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="67e4f-142">In order for end users to be able to configure an application's trace switches, you must provide detailed documentation on the switches in your application.</span></span> <span data-ttu-id="67e4f-143">Hangi anahtarların ne olduğunu, hangilerinin açıp kapanmasını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="67e4f-143">You should detail which switches control what and how to turn them on and off.</span></span> <span data-ttu-id="67e4f-144">Ayrıca son kullanıcıya açıklamalarda uygun yardım bulunan bir. config dosyası sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="67e4f-144">You should also provide your end user with a .config file that has appropriate Help in the comments.</span></span>  
  
#### <a name="to-configure-trace-switches"></a><span data-ttu-id="67e4f-145">İzleme anahtarlarını yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="67e4f-145">To configure trace switches</span></span>  
  
1. <span data-ttu-id="67e4f-146">İzleme anahtarlarını kullanmak için, önce bunları oluşturmanız ve [bir izleme anahtarı oluşturma ve başlatma](#create)bölümünde açıklandığı gibi kodunuza yerleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="67e4f-146">In order to use trace switches, you must first create them and place them in your code as described in the section [Creating and initializing a trace switch](#create).</span></span>  
  
2. <span data-ttu-id="67e4f-147">Projeniz bir yapılandırma dosyası (App. config veya Web. config) içermiyorsa, **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="67e4f-147">If your project does not contain a configuration file (app.config or Web.config), then from the **Project** menu, select **Add New Item**.</span></span>  
  
    - <span data-ttu-id="67e4f-148">**Visual Basic:** **Yeni öğe Ekle** Iletişim kutusunda **uygulama yapılandırma dosyası**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="67e4f-148">**Visual Basic:** In the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
         <span data-ttu-id="67e4f-149">Uygulama yapılandırma dosyası oluşturulup açılır.</span><span class="sxs-lookup"><span data-stu-id="67e4f-149">The application configuration file is created and opened.</span></span> <span data-ttu-id="67e4f-150">Bu, kök öğesi `<configuration>.` olan bir XML belgesidir</span><span class="sxs-lookup"><span data-stu-id="67e4f-150">This is an XML document whose root element is `<configuration>.`</span></span>  
  
    - <span data-ttu-id="67e4f-151">**Görsel C#:** **Yeni öğe Ekle** iletişim kutusunda **XML dosyası**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="67e4f-151">**Visual C#:** In the **Add New Item** dialog box, choose **XML File**.</span></span> <span data-ttu-id="67e4f-152">Bu dosyayı **app. config**olarak adlandırın. XML düzenleyicisinde, XML bildiriminden sonra aşağıdaki XML 'i ekleyin:</span><span class="sxs-lookup"><span data-stu-id="67e4f-152">Name this file **app.config**. In the XML editor, after the XML declaration, add the following XML:</span></span>  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         <span data-ttu-id="67e4f-153">Projeniz derlendiğinde, App. config dosyası proje çıktı klasörüne kopyalanır ve *ApplicationName*. exe. config olarak yeniden adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="67e4f-153">When your project is compiled, the app.config file is copied to the project output folder and is renamed *applicationname*.exe.config.</span></span>  
  
3. <span data-ttu-id="67e4f-154">`<configuration>` etiketinden sonra, ancak `</configuration>` etiketinden önce, anahtarlarınızı yapılandırmak için uygun XML 'i ekleyin.</span><span class="sxs-lookup"><span data-stu-id="67e4f-154">After the `<configuration>` tag but before the `</configuration>` tag, add the appropriate XML to configure your switches.</span></span> <span data-ttu-id="67e4f-155">Aşağıdaki örnekler, `DataMessageSwitch` **DisplayName** özelliğine sahip bir **BooleanSwitch** ve **DisplayName** özelliği `TraceLevelSwitch`olan **TraceSwitch** gösterir.</span><span class="sxs-lookup"><span data-stu-id="67e4f-155">The following examples demonstrate a **BooleanSwitch** with a **DisplayName** property of `DataMessageSwitch` and a **TraceSwitch** with a **DisplayName** property of `TraceLevelSwitch`.</span></span>  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     <span data-ttu-id="67e4f-156">Bu yapılandırmada her iki anahtar de kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="67e4f-156">In this configuration, both switches are off.</span></span>  
  
4. <span data-ttu-id="67e4f-157">Önceki örnekte gösterilen `DataMessagesSwitch` gibi bir **BooleanSwitch**açmanız gerekiyorsa, **değeri** 0 dışında bir tamsayı olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="67e4f-157">If you need to turn on a **BooleanSwitch**, such as `DataMessagesSwitch` shown in the previous example, change the **Value** to any integer other than 0.</span></span>  
  
5. <span data-ttu-id="67e4f-158">Önceki örnekte gösterilen `TraceLevelSwitch` gibi bir **TraceSwitch**açmanız gerekiyorsa, **değeri** uygun düzey ayarı (1 ile 4 arasında) olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="67e4f-158">If you need to turn on a **TraceSwitch**, such as `TraceLevelSwitch` shown in the previous example, change the **Value** to the appropriate level setting (1 to 4).</span></span>  
  
6. <span data-ttu-id="67e4f-159">Son kullanıcının anahtarları uygun şekilde yapılandırmak için hangi değerlerin değiştirileceği hakkında net bir şekilde anlayabilmesi için. config dosyasına Yorumlar ekleyin.</span><span class="sxs-lookup"><span data-stu-id="67e4f-159">Add comments to the .config file so the end user has a clear understanding of what values to change to configure the switches appropriately.</span></span>  
  
     <span data-ttu-id="67e4f-160">Aşağıdaki örnek, açıklamalar dahil olmak üzere son kodun nasıl görünebileceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="67e4f-160">The following example shows how the final code, including comments, might look:</span></span>  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <!-- This switch controls data messages. In order to receive data   
             trace messages, change value="0" to value="1" -->  
          <add name="DataMessagesSwitch" value="0" />  
          <!-- This switch controls general messages. In order to   
             receive general trace messages change the value to the   
             appropriate level. "1" gives error messages, "2" gives errors   
             and warnings, "3" gives more detailed error information, and   
             "4" gives verbose trace information -->  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="67e4f-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67e4f-161">See also</span></span>

- [<span data-ttu-id="67e4f-162">İzleme ve İşaretleme Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="67e4f-162">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="67e4f-163">Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="67e4f-163">How to: Add Trace Statements to Application Code</span></span>](how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="67e4f-164">İzleme Anahtarları</span><span class="sxs-lookup"><span data-stu-id="67e4f-164">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="67e4f-165">İzleme ve Hata Ayıklama Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="67e4f-165">Trace and Debug Settings Schema</span></span>](../configure-apps/file-schema/trace-debug/index.md)
