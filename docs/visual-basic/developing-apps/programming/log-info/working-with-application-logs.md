---
title: Uygulama Günlükleriyle Çalışma
ms.date: 07/20/2015
helpviewer_keywords:
- logs, application
- application event logs, Visual Basic
- application event logs
ms.assetid: 2581afd1-5791-4bc4-86b2-46244e9fe468
ms.openlocfilehash: 617b940d2cf15779ae3c10e4663b63c9771d44b6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345894"
---
# <a name="working-with-application-logs-in-visual-basic"></a><span data-ttu-id="a923b-102">Visual Basic'te Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="a923b-102">Working with Application Logs in Visual Basic</span></span>

<span data-ttu-id="a923b-103">The `My.Application.Log` and `My.Log` objects make it easy to write logging and tracing information to logs.</span><span class="sxs-lookup"><span data-stu-id="a923b-103">The `My.Application.Log` and `My.Log` objects make it easy to write logging and tracing information to logs.</span></span>

## <a name="how-messages-are-logged"></a><span data-ttu-id="a923b-104">How Messages are Logged</span><span class="sxs-lookup"><span data-stu-id="a923b-104">How Messages are Logged</span></span>

<span data-ttu-id="a923b-105">First, the severity of the message is checked with the <xref:System.Diagnostics.TraceSource.Switch%2A> property of the log's <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> property.</span><span class="sxs-lookup"><span data-stu-id="a923b-105">First, the severity of the message is checked with the <xref:System.Diagnostics.TraceSource.Switch%2A> property of the log's <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> property.</span></span> <span data-ttu-id="a923b-106">By default, only messages of severity "Information" and higher are passed on to the trace listeners, specified in the log's `TraceListener` collection.</span><span class="sxs-lookup"><span data-stu-id="a923b-106">By default, only messages of severity "Information" and higher are passed on to the trace listeners, specified in the log's `TraceListener` collection.</span></span> <span data-ttu-id="a923b-107">Then, each listener compares the severity of the message to the listener's <xref:System.Diagnostics.TraceSource.Switch%2A> property.</span><span class="sxs-lookup"><span data-stu-id="a923b-107">Then, each listener compares the severity of the message to the listener's <xref:System.Diagnostics.TraceSource.Switch%2A> property.</span></span> <span data-ttu-id="a923b-108">If the message's severity is high enough, the listener writes out the message.</span><span class="sxs-lookup"><span data-stu-id="a923b-108">If the message's severity is high enough, the listener writes out the message.</span></span>

<span data-ttu-id="a923b-109">The following diagram shows how a message written to the `WriteEntry` method gets passed to the `WriteLine` methods of the log's trace listeners:</span><span class="sxs-lookup"><span data-stu-id="a923b-109">The following diagram shows how a message written to the `WriteEntry` method gets passed to the `WriteLine` methods of the log's trace listeners:</span></span>

![Diagram that shows My log call.](./media/working-with-application-logs/my-log-call-messages.png)

<span data-ttu-id="a923b-111">You can change the behavior of the log and the trace listeners by changing the application's configuration file.</span><span class="sxs-lookup"><span data-stu-id="a923b-111">You can change the behavior of the log and the trace listeners by changing the application's configuration file.</span></span> <span data-ttu-id="a923b-112">The following diagram shows the correspondence between the parts of the log and the configuration file.</span><span class="sxs-lookup"><span data-stu-id="a923b-112">The following diagram shows the correspondence between the parts of the log and the configuration file.</span></span>

![Diagram that shows My log configuration.](./media/working-with-application-logs/my-log-configuration.png)

## <a name="where-messages-are-logged"></a><span data-ttu-id="a923b-114">Where Messages are Logged</span><span class="sxs-lookup"><span data-stu-id="a923b-114">Where Messages are Logged</span></span>

<span data-ttu-id="a923b-115">If the assembly has no configuration file, the `My.Application.Log` and `My.Log` objects write to the application's debug output (through the <xref:System.Diagnostics.DefaultTraceListener> class).</span><span class="sxs-lookup"><span data-stu-id="a923b-115">If the assembly has no configuration file, the `My.Application.Log` and `My.Log` objects write to the application's debug output (through the <xref:System.Diagnostics.DefaultTraceListener> class).</span></span> <span data-ttu-id="a923b-116">In addition, the `My.Application.Log` object writes to the assembly's log file (through the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class), while the `My.Log` object writes to the ASP.NET Web page's output (through the <xref:System.Web.WebPageTraceListener> class).</span><span class="sxs-lookup"><span data-stu-id="a923b-116">In addition, the `My.Application.Log` object writes to the assembly's log file (through the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class), while the `My.Log` object writes to the ASP.NET Web page's output (through the <xref:System.Web.WebPageTraceListener> class).</span></span>

<span data-ttu-id="a923b-117">The debug output can be viewed in the Visual Studio **Output** window when running your application in debug mode.</span><span class="sxs-lookup"><span data-stu-id="a923b-117">The debug output can be viewed in the Visual Studio **Output** window when running your application in debug mode.</span></span> <span data-ttu-id="a923b-118">To open the **Output** window, click the **Debug** menu item, point to **Windows**, and then click **Output**.</span><span class="sxs-lookup"><span data-stu-id="a923b-118">To open the **Output** window, click the **Debug** menu item, point to **Windows**, and then click **Output**.</span></span> <span data-ttu-id="a923b-119">In the **Output** window, select **Debug** from the **Show output from** box.</span><span class="sxs-lookup"><span data-stu-id="a923b-119">In the **Output** window, select **Debug** from the **Show output from** box.</span></span>

<span data-ttu-id="a923b-120">By default, `My.Application.Log` writes the log file in the path for the user's application data.</span><span class="sxs-lookup"><span data-stu-id="a923b-120">By default, `My.Application.Log` writes the log file in the path for the user's application data.</span></span> <span data-ttu-id="a923b-121">You can get the path from the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> property of the <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> object.</span><span class="sxs-lookup"><span data-stu-id="a923b-121">You can get the path from the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> property of the <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> object.</span></span> <span data-ttu-id="a923b-122">The format of that path is as follows:</span><span class="sxs-lookup"><span data-stu-id="a923b-122">The format of that path is as follows:</span></span>

`BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`

<span data-ttu-id="a923b-123">A typical value for `BasePath` is as follows.</span><span class="sxs-lookup"><span data-stu-id="a923b-123">A typical value for `BasePath` is as follows.</span></span>

<span data-ttu-id="a923b-124">C:\Documents and Settings\\`username`\Application Data</span><span class="sxs-lookup"><span data-stu-id="a923b-124">C:\Documents and Settings\\`username`\Application Data</span></span>

<span data-ttu-id="a923b-125">The values of `CompanyName`, `ProductName`, and `ProductVersion` come from the application's assembly information.</span><span class="sxs-lookup"><span data-stu-id="a923b-125">The values of `CompanyName`, `ProductName`, and `ProductVersion` come from the application's assembly information.</span></span> <span data-ttu-id="a923b-126">The form of the log file name is *AssemblyName*.log, where *AssemblyName* is the file name of the assembly without the extension.</span><span class="sxs-lookup"><span data-stu-id="a923b-126">The form of the log file name is *AssemblyName*.log, where *AssemblyName* is the file name of the assembly without the extension.</span></span> <span data-ttu-id="a923b-127">If more than one log file is needed, such as when the original log is unavailable when the application attempts to write to the log, the form for the log file name is *AssemblyName*-*iteration*.log, where `iteration` is a positive `Integer`.</span><span class="sxs-lookup"><span data-stu-id="a923b-127">If more than one log file is needed, such as when the original log is unavailable when the application attempts to write to the log, the form for the log file name is *AssemblyName*-*iteration*.log, where `iteration` is a positive `Integer`.</span></span>

<span data-ttu-id="a923b-128">You can override the default behavior by adding or changing the computer's and the application's configuration files.</span><span class="sxs-lookup"><span data-stu-id="a923b-128">You can override the default behavior by adding or changing the computer's and the application's configuration files.</span></span> <span data-ttu-id="a923b-129">For more information, see [Walkthrough: Changing Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="a923b-129">For more information, see [Walkthrough: Changing Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md).</span></span>

## <a name="configuring-log-settings"></a><span data-ttu-id="a923b-130">Configuring Log Settings</span><span class="sxs-lookup"><span data-stu-id="a923b-130">Configuring Log Settings</span></span>

<span data-ttu-id="a923b-131">The `Log` object has a default implementation that works without an application configuration file, app.config. To change the defaults, you must add a configuration file with the new settings.</span><span class="sxs-lookup"><span data-stu-id="a923b-131">The `Log` object has a default implementation that works without an application configuration file, app.config. To change the defaults, you must add a configuration file with the new settings.</span></span> <span data-ttu-id="a923b-132">For more information, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="a923b-132">For more information, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>

<span data-ttu-id="a923b-133">The log configuration sections are located in the `<system.diagnostics>` node in the main `<configuration>` node of the app.config file.</span><span class="sxs-lookup"><span data-stu-id="a923b-133">The log configuration sections are located in the `<system.diagnostics>` node in the main `<configuration>` node of the app.config file.</span></span> <span data-ttu-id="a923b-134">Log information is defined in several nodes:</span><span class="sxs-lookup"><span data-stu-id="a923b-134">Log information is defined in several nodes:</span></span>

- <span data-ttu-id="a923b-135">The listeners for the `Log` object are defined in the `<sources>` node named DefaultSource.</span><span class="sxs-lookup"><span data-stu-id="a923b-135">The listeners for the `Log` object are defined in the `<sources>` node named DefaultSource.</span></span>

- <span data-ttu-id="a923b-136">The severity filter for the `Log` object is defined in the `<switches>` node named DefaultSwitch.</span><span class="sxs-lookup"><span data-stu-id="a923b-136">The severity filter for the `Log` object is defined in the `<switches>` node named DefaultSwitch.</span></span>

- <span data-ttu-id="a923b-137">The log listeners are defined in the `<sharedListeners>` node.</span><span class="sxs-lookup"><span data-stu-id="a923b-137">The log listeners are defined in the `<sharedListeners>` node.</span></span>

 <span data-ttu-id="a923b-138">Examples of `<sources>`, `<switches>`, and `<sharedListeners>` nodes are shown in the following code:</span><span class="sxs-lookup"><span data-stu-id="a923b-138">Examples of `<sources>`, `<switches>`, and `<sharedListeners>` nodes are shown in the following code:</span></span>

```xml
<configuration>
  <system.diagnostics>
    <sources>
      <source name="DefaultSource" switchName="DefaultSwitch">
        <listeners>
          <add name="FileLog"/>
        </listeners>
      </source>
    </sources>
    <switches>
      <add name="DefaultSwitch" value="Information" />
    </switches>
    <sharedListeners>
      <add name="FileLog"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
          Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
          PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL"
        initializeData="FileLogWriter"
      />
    </sharedListeners>
  </system.diagnostics>
</configuration>
```

## <a name="changing-log-settings-after-deployment"></a><span data-ttu-id="a923b-139">Changing Log Settings after Deployment</span><span class="sxs-lookup"><span data-stu-id="a923b-139">Changing Log Settings after Deployment</span></span>

<span data-ttu-id="a923b-140">When you develop an application, its configuration settings are stored in the app.config file, as shown in the examples above.</span><span class="sxs-lookup"><span data-stu-id="a923b-140">When you develop an application, its configuration settings are stored in the app.config file, as shown in the examples above.</span></span> <span data-ttu-id="a923b-141">After you deploy your application, you can still configure the log by editing the configuration file.</span><span class="sxs-lookup"><span data-stu-id="a923b-141">After you deploy your application, you can still configure the log by editing the configuration file.</span></span> <span data-ttu-id="a923b-142">In a Windows-based application, this file's name is *applicationName*.exe.config, and it must reside in the same folder as the executable file.</span><span class="sxs-lookup"><span data-stu-id="a923b-142">In a Windows-based application, this file's name is *applicationName*.exe.config, and it must reside in the same folder as the executable file.</span></span> <span data-ttu-id="a923b-143">For a Web application, this is the Web.config file associated with the project.</span><span class="sxs-lookup"><span data-stu-id="a923b-143">For a Web application, this is the Web.config file associated with the project.</span></span>

<span data-ttu-id="a923b-144">When your application executes the code that creates an instance of a class for the first time, it checks the configuration file for information about the object.</span><span class="sxs-lookup"><span data-stu-id="a923b-144">When your application executes the code that creates an instance of a class for the first time, it checks the configuration file for information about the object.</span></span> <span data-ttu-id="a923b-145">For the `Log` object, this happens the first time the `Log` object is accessed.</span><span class="sxs-lookup"><span data-stu-id="a923b-145">For the `Log` object, this happens the first time the `Log` object is accessed.</span></span> <span data-ttu-id="a923b-146">The system examines the configuration file only once for any particular object—the first time your application creates the object.</span><span class="sxs-lookup"><span data-stu-id="a923b-146">The system examines the configuration file only once for any particular object—the first time your application creates the object.</span></span> <span data-ttu-id="a923b-147">Therefore, you may need to restart the application for the changes to take effect.</span><span class="sxs-lookup"><span data-stu-id="a923b-147">Therefore, you may need to restart the application for the changes to take effect.</span></span>

<span data-ttu-id="a923b-148">In a deployed application, you enable trace code by reconfiguring switch objects before your application starts.</span><span class="sxs-lookup"><span data-stu-id="a923b-148">In a deployed application, you enable trace code by reconfiguring switch objects before your application starts.</span></span> <span data-ttu-id="a923b-149">Typically, this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span><span class="sxs-lookup"><span data-stu-id="a923b-149">Typically, this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>

## <a name="security-considerations"></a><span data-ttu-id="a923b-150">Güvenlik Değerlendirmeleri</span><span class="sxs-lookup"><span data-stu-id="a923b-150">Security Considerations</span></span>

<span data-ttu-id="a923b-151">Consider the following when writing data to the log:</span><span class="sxs-lookup"><span data-stu-id="a923b-151">Consider the following when writing data to the log:</span></span>

- <span data-ttu-id="a923b-152">**Avoid leaking user information.**</span><span class="sxs-lookup"><span data-stu-id="a923b-152">**Avoid leaking user information.**</span></span> <span data-ttu-id="a923b-153">Ensure that your application writes only approved information to the log.</span><span class="sxs-lookup"><span data-stu-id="a923b-153">Ensure that your application writes only approved information to the log.</span></span> <span data-ttu-id="a923b-154">For example, it may be acceptable for the application log to contain user names, but not user passwords.</span><span class="sxs-lookup"><span data-stu-id="a923b-154">For example, it may be acceptable for the application log to contain user names, but not user passwords.</span></span>

- <span data-ttu-id="a923b-155">**Make log locations secure.**</span><span class="sxs-lookup"><span data-stu-id="a923b-155">**Make log locations secure.**</span></span> <span data-ttu-id="a923b-156">Any log that contains potentially sensitive information should be stored in a secure location.</span><span class="sxs-lookup"><span data-stu-id="a923b-156">Any log that contains potentially sensitive information should be stored in a secure location.</span></span>

- <span data-ttu-id="a923b-157">**Avoid misleading information.**</span><span class="sxs-lookup"><span data-stu-id="a923b-157">**Avoid misleading information.**</span></span> <span data-ttu-id="a923b-158">In general, your application should validate all data entered by a user before using that data.</span><span class="sxs-lookup"><span data-stu-id="a923b-158">In general, your application should validate all data entered by a user before using that data.</span></span> <span data-ttu-id="a923b-159">This includes writing data to the application log.</span><span class="sxs-lookup"><span data-stu-id="a923b-159">This includes writing data to the application log.</span></span>

- <span data-ttu-id="a923b-160">**Avoid denial of service.**</span><span class="sxs-lookup"><span data-stu-id="a923b-160">**Avoid denial of service.**</span></span> <span data-ttu-id="a923b-161">If your application writes too much information to the log, it could fill the log or make finding important information difficult.</span><span class="sxs-lookup"><span data-stu-id="a923b-161">If your application writes too much information to the log, it could fill the log or make finding important information difficult.</span></span>

## <a name="see-also"></a><span data-ttu-id="a923b-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a923b-162">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="a923b-163">Uygulamadan Günlüğe Bilgi Kaydetme</span><span class="sxs-lookup"><span data-stu-id="a923b-163">Logging Information from the Application</span></span>](../../../../visual-basic/developing-apps/programming/log-info/index.md)
