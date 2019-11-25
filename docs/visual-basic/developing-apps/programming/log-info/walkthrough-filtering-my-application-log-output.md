---
title: My.Application.Log Çıktısını Filtreleme
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
ms.openlocfilehash: f18556bbe1ca2d77925482319246d403892d31ef
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353598"
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a><span data-ttu-id="2c0e0-102">İzlenecek Yol: My.Application.Log Çıktısını Filtreleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c0e0-102">Walkthrough: Filtering My.Application.Log Output (Visual Basic)</span></span>

<span data-ttu-id="2c0e0-103">This walkthrough demonstrates how to change the default log filtering for the `My.Application.Log` object, to control what information is passed from the `Log` object to the listeners and what information is written by the listeners.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-103">This walkthrough demonstrates how to change the default log filtering for the `My.Application.Log` object, to control what information is passed from the `Log` object to the listeners and what information is written by the listeners.</span></span> <span data-ttu-id="2c0e0-104">You can change the logging behavior even after building the application, because the configuration information is stored in the application's configuration file.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-104">You can change the logging behavior even after building the application, because the configuration information is stored in the application's configuration file.</span></span>

## <a name="getting-started"></a><span data-ttu-id="2c0e0-105">Başlarken</span><span class="sxs-lookup"><span data-stu-id="2c0e0-105">Getting Started</span></span>

<span data-ttu-id="2c0e0-106">Each message that `My.Application.Log` writes has an associated severity level, which filtering mechanisms use to control the log output.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-106">Each message that `My.Application.Log` writes has an associated severity level, which filtering mechanisms use to control the log output.</span></span> <span data-ttu-id="2c0e0-107">This sample application uses `My.Application.Log` methods to write several log messages with different severity levels.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-107">This sample application uses `My.Application.Log` methods to write several log messages with different severity levels.</span></span>

#### <a name="to-build-the-sample-application"></a><span data-ttu-id="2c0e0-108">To build the sample application</span><span class="sxs-lookup"><span data-stu-id="2c0e0-108">To build the sample application</span></span>

1. <span data-ttu-id="2c0e0-109">Open a new Visual Basic Windows Application project.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-109">Open a new Visual Basic Windows Application project.</span></span>

2. <span data-ttu-id="2c0e0-110">Add a button named Button1 to Form1.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-110">Add a button named Button1 to Form1.</span></span>

3. <span data-ttu-id="2c0e0-111">In the <xref:System.Windows.Forms.Control.Click> event handler for Button1, add the following code:</span><span class="sxs-lookup"><span data-stu-id="2c0e0-111">In the <xref:System.Windows.Forms.Control.Click> event handler for Button1, add the following code:</span></span>

     [!code-vb[VbVbcnMyApplicationLogFiltering#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyApplicationLogFiltering/VB/Form1.vb#1)]

4. <span data-ttu-id="2c0e0-112">Run the application in the debugger.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-112">Run the application in the debugger.</span></span>

5. <span data-ttu-id="2c0e0-113">Press **Button1**.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-113">Press **Button1**.</span></span>

     <span data-ttu-id="2c0e0-114">The application writes the following information to the application's debug output and log file.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-114">The application writes the following information to the application's debug output and log file.</span></span>

     `DefaultSource Information: 0 : In Button1_Click`

     `DefaultSource Error: 2 : Error in the application.`

6. <span data-ttu-id="2c0e0-115">Close the application.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-115">Close the application.</span></span>

     <span data-ttu-id="2c0e0-116">For information on how to view the application's debug output window, see [Output Window](/visualstudio/ide/reference/output-window).</span><span class="sxs-lookup"><span data-stu-id="2c0e0-116">For information on how to view the application's debug output window, see [Output Window](/visualstudio/ide/reference/output-window).</span></span> <span data-ttu-id="2c0e0-117">For information on the location of the application's log file, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="2c0e0-117">For information on the location of the application's log file, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="2c0e0-118">By default, the application flushes the log-file output when the application closes.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-118">By default, the application flushes the log-file output when the application closes.</span></span>

     <span data-ttu-id="2c0e0-119">In the example above, the second call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> method and the call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> method produces log output, while the first and last calls to the `WriteEntry` method do not.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-119">In the example above, the second call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> method and the call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> method produces log output, while the first and last calls to the `WriteEntry` method do not.</span></span> <span data-ttu-id="2c0e0-120">This is because the severity levels of `WriteEntry` and `WriteException` are "Information" and "Error", both of which are allowed by the `My.Application.Log` object's default log filtering.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-120">This is because the severity levels of `WriteEntry` and `WriteException` are "Information" and "Error", both of which are allowed by the `My.Application.Log` object's default log filtering.</span></span> <span data-ttu-id="2c0e0-121">However, events with "Start" and "Stop" severity levels are prevented from producing log output.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-121">However, events with "Start" and "Stop" severity levels are prevented from producing log output.</span></span>

## <a name="filtering-for-all-myapplicationlog-listeners"></a><span data-ttu-id="2c0e0-122">Filtering for All My.Application.Log Listeners</span><span class="sxs-lookup"><span data-stu-id="2c0e0-122">Filtering for All My.Application.Log Listeners</span></span>

<span data-ttu-id="2c0e0-123">The `My.Application.Log` object uses a <xref:System.Diagnostics.SourceSwitch> named `DefaultSwitch` to control which messages it passes from the `WriteEntry` and `WriteException` methods to the log listeners.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-123">The `My.Application.Log` object uses a <xref:System.Diagnostics.SourceSwitch> named `DefaultSwitch` to control which messages it passes from the `WriteEntry` and `WriteException` methods to the log listeners.</span></span> <span data-ttu-id="2c0e0-124">You can configure `DefaultSwitch` in the application's configuration file by setting its value to one of the <xref:System.Diagnostics.SourceLevels> enumeration values.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-124">You can configure `DefaultSwitch` in the application's configuration file by setting its value to one of the <xref:System.Diagnostics.SourceLevels> enumeration values.</span></span> <span data-ttu-id="2c0e0-125">By default, its value is "Information".</span><span class="sxs-lookup"><span data-stu-id="2c0e0-125">By default, its value is "Information".</span></span>

<span data-ttu-id="2c0e0-126">This table shows the severity level required for Log to write a message to the listeners, given a particular `DefaultSwitch` setting.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-126">This table shows the severity level required for Log to write a message to the listeners, given a particular `DefaultSwitch` setting.</span></span>

|<span data-ttu-id="2c0e0-127">DefaultSwitch Value</span><span class="sxs-lookup"><span data-stu-id="2c0e0-127">DefaultSwitch Value</span></span>|<span data-ttu-id="2c0e0-128">Message severity required for output</span><span class="sxs-lookup"><span data-stu-id="2c0e0-128">Message severity required for output</span></span>|
|---|---|
|`Critical`|`Critical`|
|`Error`|<span data-ttu-id="2c0e0-129">`Critical` or `Error`</span><span class="sxs-lookup"><span data-stu-id="2c0e0-129">`Critical` or `Error`</span></span>|
|`Warning`|<span data-ttu-id="2c0e0-130">`Critical`, `Error`, or `Warning`</span><span class="sxs-lookup"><span data-stu-id="2c0e0-130">`Critical`, `Error`, or `Warning`</span></span>|
|`Information`|<span data-ttu-id="2c0e0-131">`Critical`, `Error`, `Warning`, or `Information`</span><span class="sxs-lookup"><span data-stu-id="2c0e0-131">`Critical`, `Error`, `Warning`, or `Information`</span></span>|
|`Verbose`|<span data-ttu-id="2c0e0-132">`Critical`, `Error`, `Warning`, `Information`, or `Verbose`</span><span class="sxs-lookup"><span data-stu-id="2c0e0-132">`Critical`, `Error`, `Warning`, `Information`, or `Verbose`</span></span>|
|`ActivityTracing`|<span data-ttu-id="2c0e0-133">`Start`, `Stop`, `Suspend`, `Resume`, or `Transfer`</span><span class="sxs-lookup"><span data-stu-id="2c0e0-133">`Start`, `Stop`, `Suspend`, `Resume`, or `Transfer`</span></span>|
|`All`|<span data-ttu-id="2c0e0-134">All messages are allowed.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-134">All messages are allowed.</span></span>|
|`Off`|<span data-ttu-id="2c0e0-135">All messages are blocked.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-135">All messages are blocked.</span></span>|

> [!NOTE]
> <span data-ttu-id="2c0e0-136">The `WriteEntry` and `WriteException` methods each have an overload that does not specify a severity level.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-136">The `WriteEntry` and `WriteException` methods each have an overload that does not specify a severity level.</span></span> <span data-ttu-id="2c0e0-137">The implicit severity level for the `WriteEntry` overload is "Information", and the implicit severity level for the `WriteException` overload is "Error".</span><span class="sxs-lookup"><span data-stu-id="2c0e0-137">The implicit severity level for the `WriteEntry` overload is "Information", and the implicit severity level for the `WriteException` overload is "Error".</span></span>

<span data-ttu-id="2c0e0-138">This table explains the log output shown in the previous example: with the default `DefaultSwitch` setting of "Information", only the second call to the `WriteEntry` method and the call to the `WriteException` method produce log output.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-138">This table explains the log output shown in the previous example: with the default `DefaultSwitch` setting of "Information", only the second call to the `WriteEntry` method and the call to the `WriteException` method produce log output.</span></span>

#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="2c0e0-139">To log only activity tracing events</span><span class="sxs-lookup"><span data-stu-id="2c0e0-139">To log only activity tracing events</span></span>

1. <span data-ttu-id="2c0e0-140">Right-click app.config in the **Solution Explorer** and select **Open**.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-140">Right-click app.config in the **Solution Explorer** and select **Open**.</span></span>

     <span data-ttu-id="2c0e0-141">veya</span><span class="sxs-lookup"><span data-stu-id="2c0e0-141">-or-</span></span>

     <span data-ttu-id="2c0e0-142">If there is no app.config file:</span><span class="sxs-lookup"><span data-stu-id="2c0e0-142">If there is no app.config file:</span></span>

    1. <span data-ttu-id="2c0e0-143">On the **Project** menu, choose **Add New Item**.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-143">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="2c0e0-144">From the **Add New Item** dialog box, choose **Application Configuration File**.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-144">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="2c0e0-145">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-145">Click **Add**.</span></span>

2. <span data-ttu-id="2c0e0-146">Locate the `<switches>` section, which is in the `<system.diagnostics>` section, which is in the top-level `<configuration>` section.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-146">Locate the `<switches>` section, which is in the `<system.diagnostics>` section, which is in the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="2c0e0-147">Find the element that adds `DefaultSwitch` to the collection of switches.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-147">Find the element that adds `DefaultSwitch` to the collection of switches.</span></span> <span data-ttu-id="2c0e0-148">It should look similar to this element:</span><span class="sxs-lookup"><span data-stu-id="2c0e0-148">It should look similar to this element:</span></span>

     `<add name="DefaultSwitch" value="Information" />`

4. <span data-ttu-id="2c0e0-149">Change the value of the `value` attribute to "ActivityTracing".</span><span class="sxs-lookup"><span data-stu-id="2c0e0-149">Change the value of the `value` attribute to "ActivityTracing".</span></span>

5. <span data-ttu-id="2c0e0-150">The content of the app.config file should be similar to the following XML:</span><span class="sxs-lookup"><span data-stu-id="2c0e0-150">The content of the app.config file should be similar to the following XML:</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.diagnostics>
        <sources>
          <!-- This section configures My.Application.Log -->
          <source name="DefaultSource" switchName="DefaultSwitch">
            <listeners>
              <add name="FileLog"/>
            </listeners>
          </source>
        </sources>
        <switches>
          <add name="DefaultSwitch" value="ActivityTracing" />
        </switches>
        <sharedListeners>
          <add name="FileLog"
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
                     Microsoft.VisualBasic, Version=8.0.0.0,
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,
                     processorArchitecture=MSIL"
               initializeData="FileLogWriter"/>
        </sharedListeners>
      </system.diagnostics>
    </configuration>
    ```

6. <span data-ttu-id="2c0e0-151">Run the application in the debugger.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-151">Run the application in the debugger.</span></span>

7. <span data-ttu-id="2c0e0-152">Press **Button1**.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-152">Press **Button1**.</span></span>

     <span data-ttu-id="2c0e0-153">The application writes the following information to the application's debug output and log file:</span><span class="sxs-lookup"><span data-stu-id="2c0e0-153">The application writes the following information to the application's debug output and log file:</span></span>

     `DefaultSource Start: 4 : Entering Button1_Click`

     `DefaultSource Stop: 5 : Leaving Button1_Click`

8. <span data-ttu-id="2c0e0-154">Close the application.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-154">Close the application.</span></span>

9. <span data-ttu-id="2c0e0-155">Change the value of the `value` attribute back to "Information".</span><span class="sxs-lookup"><span data-stu-id="2c0e0-155">Change the value of the `value` attribute back to "Information".</span></span>

    > [!NOTE]
    > <span data-ttu-id="2c0e0-156">The `DefaultSwitch` switch setting controls only `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-156">The `DefaultSwitch` switch setting controls only `My.Application.Log`.</span></span> <span data-ttu-id="2c0e0-157">It does not change how the .NET Framework <xref:System.Diagnostics.Trace?displayProperty=nameWithType> and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes behave.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-157">It does not change how the .NET Framework <xref:System.Diagnostics.Trace?displayProperty=nameWithType> and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes behave.</span></span>

## <a name="individual-filtering-for-myapplicationlog-listeners"></a><span data-ttu-id="2c0e0-158">Individual Filtering For My.Application.Log Listeners</span><span class="sxs-lookup"><span data-stu-id="2c0e0-158">Individual Filtering For My.Application.Log Listeners</span></span>

<span data-ttu-id="2c0e0-159">The previous example shows how to change the filtering for all `My.Application.Log` output.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-159">The previous example shows how to change the filtering for all `My.Application.Log` output.</span></span> <span data-ttu-id="2c0e0-160">This example demonstrates how to filter an individual log listener.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-160">This example demonstrates how to filter an individual log listener.</span></span> <span data-ttu-id="2c0e0-161">By default, an application has two listeners that write to the application's debug output and the log file.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-161">By default, an application has two listeners that write to the application's debug output and the log file.</span></span>

<span data-ttu-id="2c0e0-162">The configuration file controls the behavior of the log listeners by allowing each one to have a filter, which is similar to a switch for `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-162">The configuration file controls the behavior of the log listeners by allowing each one to have a filter, which is similar to a switch for `My.Application.Log`.</span></span> <span data-ttu-id="2c0e0-163">A log listener will output a message only if the message's severity is allowed by both the log's `DefaultSwitch` and the log listener's filter.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-163">A log listener will output a message only if the message's severity is allowed by both the log's `DefaultSwitch` and the log listener's filter.</span></span>

<span data-ttu-id="2c0e0-164">This example demonstrates how to configure filtering for a new debug listener and add it to the `Log` object.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-164">This example demonstrates how to configure filtering for a new debug listener and add it to the `Log` object.</span></span> <span data-ttu-id="2c0e0-165">The default debug listener should be removed from the `Log` object, so it is clear that the debug messages come from the new debug listener.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-165">The default debug listener should be removed from the `Log` object, so it is clear that the debug messages come from the new debug listener.</span></span>

#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="2c0e0-166">To log only activity-tracing events</span><span class="sxs-lookup"><span data-stu-id="2c0e0-166">To log only activity-tracing events</span></span>

1. <span data-ttu-id="2c0e0-167">Right-click app.config in the **Solution Explorer** and choose **Open**.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-167">Right-click app.config in the **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="2c0e0-168">\-or-</span><span class="sxs-lookup"><span data-stu-id="2c0e0-168">\-or-</span></span>

     <span data-ttu-id="2c0e0-169">If there is no app.config file:</span><span class="sxs-lookup"><span data-stu-id="2c0e0-169">If there is no app.config file:</span></span>

    1. <span data-ttu-id="2c0e0-170">On the **Project** menu, choose **Add New Item**.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-170">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="2c0e0-171">From the **Add New Item** dialog box, choose **Application Configuration File**.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-171">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="2c0e0-172">**Ekle**'yi tıklatın.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-172">Click **Add**.</span></span>

2. <span data-ttu-id="2c0e0-173">Right-click app.config in **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-173">Right-click app.config in **Solution Explorer**.</span></span> <span data-ttu-id="2c0e0-174">Choose **Open**.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-174">Choose **Open**.</span></span>

3. <span data-ttu-id="2c0e0-175">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", which is under the `<sources>` section.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-175">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", which is under the `<sources>` section.</span></span> <span data-ttu-id="2c0e0-176">The `<sources>` section is under the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-176">The `<sources>` section is under the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

4. <span data-ttu-id="2c0e0-177">Add this element to the `<listeners>` section:</span><span class="sxs-lookup"><span data-stu-id="2c0e0-177">Add this element to the `<listeners>` section:</span></span>

    ```xml
    <!-- Remove the default debug listener. -->
    <remove name="Default"/>
    <!-- Add a filterable debug listener. -->
    <add name="NewDefault"/>
    ```

5. <span data-ttu-id="2c0e0-178">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-178">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

6. <span data-ttu-id="2c0e0-179">Add this element to that `<sharedListeners>` section:</span><span class="sxs-lookup"><span data-stu-id="2c0e0-179">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="NewDefault"
         type="System.Diagnostics.DefaultTraceListener,
               System, Version=2.0.0.0, Culture=neutral,
               PublicKeyToken=b77a5c561934e089,
               processorArchitecture=MSIL">
        <filter type="System.Diagnostics.EventTypeFilter"
                initializeData="Error" />
    </add>
    ```

     <span data-ttu-id="2c0e0-180">The <xref:System.Diagnostics.EventTypeFilter> filter takes one of the <xref:System.Diagnostics.SourceLevels> enumeration values as its `initializeData` attribute.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-180">The <xref:System.Diagnostics.EventTypeFilter> filter takes one of the <xref:System.Diagnostics.SourceLevels> enumeration values as its `initializeData` attribute.</span></span>

7. <span data-ttu-id="2c0e0-181">The content of the app.config file should be similar to the following XML:</span><span class="sxs-lookup"><span data-stu-id="2c0e0-181">The content of the app.config file should be similar to the following XML:</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.diagnostics>
        <sources>
          <!-- This section configures My.Application.Log -->
          <source name="DefaultSource" switchName="DefaultSwitch">
            <listeners>
              <add name="FileLog"/>
              <!-- Remove the default debug listener. -->
              <remove name="Default"/>
              <!-- Add a filterable debug listener. -->
              <add name="NewDefault"/>
            </listeners>
          </source>
        </sources>
        <switches>
          <add name="DefaultSwitch" value="Information" />
        </switches>
        <sharedListeners>
          <add name="FileLog"
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
                     Microsoft.VisualBasic, Version=8.0.0.0,
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,
                     processorArchitecture=MSIL"
               initializeData="FileLogWriter"/>
          <add name="NewDefault"
               type="System.Diagnostics.DefaultTraceListener,
                     System, Version=2.0.0.0, Culture=neutral,
                     PublicKeyToken=b77a5c561934e089,
                     processorArchitecture=MSIL">
            <filter type="System.Diagnostics.EventTypeFilter"
                    initializeData="Error" />
          </add>
        </sharedListeners>
      </system.diagnostics>
    </configuration>
    ```

8. <span data-ttu-id="2c0e0-182">Run the application in the debugger.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-182">Run the application in the debugger.</span></span>

9. <span data-ttu-id="2c0e0-183">Press **Button1**.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-183">Press **Button1**.</span></span>

     <span data-ttu-id="2c0e0-184">The application writes the following information to the application's log file:</span><span class="sxs-lookup"><span data-stu-id="2c0e0-184">The application writes the following information to the application's log file:</span></span>

     `Default Information: 0 : In Button1_Click`

     `Default Error: 2 : Error in the application.`

     <span data-ttu-id="2c0e0-185">The application writes less information to the application's debug output because of the more restrictive filtering.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-185">The application writes less information to the application's debug output because of the more restrictive filtering.</span></span>

     `Default Error   2   Error`

10. <span data-ttu-id="2c0e0-186">Close the application.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-186">Close the application.</span></span>

<span data-ttu-id="2c0e0-187">For more information about changing log settings after deployment, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="2c0e0-187">For more information about changing log settings after deployment, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2c0e0-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c0e0-188">See also</span></span>

- [<span data-ttu-id="2c0e0-189">İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="2c0e0-189">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="2c0e0-190">İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="2c0e0-190">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="2c0e0-191">İzlenecek Yol: Özel Günlük Dinleyicileri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2c0e0-191">Walkthrough: Creating Custom Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)
- [<span data-ttu-id="2c0e0-192">Nasıl Yapılır: Günlük İletileri Yazma</span><span class="sxs-lookup"><span data-stu-id="2c0e0-192">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="2c0e0-193">İzleme Anahtarları</span><span class="sxs-lookup"><span data-stu-id="2c0e0-193">Trace Switches</span></span>](../../../../framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="2c0e0-194">Uygulamadan Günlüğe Bilgi Kaydetme</span><span class="sxs-lookup"><span data-stu-id="2c0e0-194">Logging Information from the Application</span></span>](../../../../visual-basic/developing-apps/programming/log-info/index.md)
