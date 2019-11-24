---
title: .NET Framework Günlük Kaydını Denetleme
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events, logging
ms.assetid: ce13088e-3095-4f0e-9f6b-fad30bbd3d41
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 924d209cd1177ffc1702ebe958c58bfc29c22c38
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447682"
---
# <a name="controlling-net-framework-logging"></a><span data-ttu-id="0bd12-102">.NET Framework Günlük Kaydını Denetleme</span><span class="sxs-lookup"><span data-stu-id="0bd12-102">Controlling .NET Framework Logging</span></span>

<span data-ttu-id="0bd12-103">Ortak dil çalışma zamanı (CLR) olaylarını izlemek için Windows olay izleme (ETW) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0bd12-103">You can use event tracing for Windows (ETW) to record common language runtime (CLR) events.</span></span> <span data-ttu-id="0bd12-104">Aşağıdaki araçları kullanarak izlemeleri oluşturabilir ve görüntüleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0bd12-104">You can create and view traces by using the following tools:</span></span>

- <span data-ttu-id="0bd12-105">The [Logman](/windows-server/administration/windows-commands/logman) and [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) command-line tools, which are included with the Windows operating system.</span><span class="sxs-lookup"><span data-stu-id="0bd12-105">The [Logman](/windows-server/administration/windows-commands/logman) and [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) command-line tools, which are included with the Windows operating system.</span></span>

- <span data-ttu-id="0bd12-106">The [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) tools in the [Windows Performance Toolkit](/windows-hardware/test/wpt/).</span><span class="sxs-lookup"><span data-stu-id="0bd12-106">The [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) tools in the [Windows Performance Toolkit](/windows-hardware/test/wpt/).</span></span> <span data-ttu-id="0bd12-107">For more information about Xperf, see the [Windows Performance blog](https://blogs.msdn.microsoft.com/pigscanfly/tag/xperf/).</span><span class="sxs-lookup"><span data-stu-id="0bd12-107">For more information about Xperf, see the [Windows Performance blog](https://blogs.msdn.microsoft.com/pigscanfly/tag/xperf/).</span></span>

<span data-ttu-id="0bd12-108">CLR olay bilgilerini yakalamak için, CLR sağlayıcısı bilgisayarınıza yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="0bd12-108">To capture CLR event information, the CLR provider must be installed on your computer.</span></span> <span data-ttu-id="0bd12-109">To confirm that the provider is installed, type `logman query providers` at the command prompt.</span><span class="sxs-lookup"><span data-stu-id="0bd12-109">To confirm that the provider is installed, type `logman query providers` at the command prompt.</span></span> <span data-ttu-id="0bd12-110">Sağlayıcı listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0bd12-110">A list of providers is displayed.</span></span> <span data-ttu-id="0bd12-111">Bu liste, sağlayıcılar gibi CLR sağlayıcısı için bir girdi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="0bd12-111">This list should contain an entry for the CLR provider, as follows.</span></span>

```output
Provider                                 GUID
-------------------------------------------------------------------------------
.NET Common Language Runtime    {E13C0D23-CCBC-4E12-931B-D9CC2EEE27E4}.
```

<span data-ttu-id="0bd12-112">If the CLR provider is not listed, you can install it on Windows Vista and later operating systems by using the Windows [Wevtutil](/windows-server/administration/windows-commands/wevtutil) command-line tool.</span><span class="sxs-lookup"><span data-stu-id="0bd12-112">If the CLR provider is not listed, you can install it on Windows Vista and later operating systems by using the Windows [Wevtutil](/windows-server/administration/windows-commands/wevtutil) command-line tool.</span></span> <span data-ttu-id="0bd12-113">Komut istemi penceresini yönetici olarak açın.</span><span class="sxs-lookup"><span data-stu-id="0bd12-113">Open the Command Prompt window as an administrator.</span></span> <span data-ttu-id="0bd12-114">Change the prompt directory to the .NET Framework 4 folder (%WINDIR%\Microsoft.NET\Framework[64]\v4.\<.NET version>\ ).</span><span class="sxs-lookup"><span data-stu-id="0bd12-114">Change the prompt directory to the .NET Framework 4 folder (%WINDIR%\Microsoft.NET\Framework[64]\v4.\<.NET version>\ ).</span></span> <span data-ttu-id="0bd12-115">Bu klasör, CLE-ETW.man dosyasını içerir.</span><span class="sxs-lookup"><span data-stu-id="0bd12-115">This folder contains the CLR-ETW.man file.</span></span> <span data-ttu-id="0bd12-116">Komut isteminde, CLR sağlayıcısını yüklemek için aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="0bd12-116">At the command prompt, type the following command to install the CLR provider:</span></span>

`wevtutil im CLR-ETW.man`

## <a name="capturing-clr-etw-events"></a><span data-ttu-id="0bd12-117">CLR ETW olaylarını yakalama</span><span class="sxs-lookup"><span data-stu-id="0bd12-117">Capturing CLR ETW Events</span></span>

<span data-ttu-id="0bd12-118">You can use the [Logman](/windows-server/administration/windows-commands/logman) and [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) command-line tools to capture ETW events, and the [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) and [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) tools to decode the trace events.</span><span class="sxs-lookup"><span data-stu-id="0bd12-118">You can use the [Logman](/windows-server/administration/windows-commands/logman) and [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) command-line tools to capture ETW events, and the [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) and [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) tools to decode the trace events.</span></span>

<span data-ttu-id="0bd12-119">Bir kullanıcının, günlüğü etkinleştirmek için üç şeyi belirtmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="0bd12-119">To turn on logging, a user must specify three things:</span></span>

- <span data-ttu-id="0bd12-120">İletişim kurmak için sağlayıcı.</span><span class="sxs-lookup"><span data-stu-id="0bd12-120">The provider to communicate to.</span></span>

- <span data-ttu-id="0bd12-121">64 bitlik bir sayı, bir anahtar kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0bd12-121">A 64-bit number that represents a set of keywords.</span></span> <span data-ttu-id="0bd12-122">Her anahtar, açılabilen sağlayıcının olaylar kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0bd12-122">Each keyword represents a set of events that the provider can turn on.</span></span> <span data-ttu-id="0bd12-123">Sayı, açmak için birleştirilmiş bir anahtar sözcük kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0bd12-123">The number represents a combined set of keywords to turn on.</span></span>

- <span data-ttu-id="0bd12-124">Günlüğe kaydetmek için bir düzeyi (ayrıntılı) temsil eden bir küçük numara.</span><span class="sxs-lookup"><span data-stu-id="0bd12-124">A small number representing the level (verbosity) to log at.</span></span> <span data-ttu-id="0bd12-125">Düzey 1, en az ayrıntılı ve düzey 5, en ayrıntılı düzeydir.</span><span class="sxs-lookup"><span data-stu-id="0bd12-125">Level 1 is the least verbose, and level 5 is the most verbose.</span></span> <span data-ttu-id="0bd12-126">Düzey 0, sağlayıcıya özgü olan anlamında bir varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="0bd12-126">Level 0 is a default whose meaning is provider-specific.</span></span>

### <a name="to-capture-clr-etw-events-using-logman"></a><span data-ttu-id="0bd12-127">Logman kullanarak CLR ETW olaylarını yakalamak için</span><span class="sxs-lookup"><span data-stu-id="0bd12-127">To capture CLR ETW events using Logman</span></span>

1. <span data-ttu-id="0bd12-128">Komut isteminde, şunları yazın:</span><span class="sxs-lookup"><span data-stu-id="0bd12-128">At the command prompt, type:</span></span>

     `logman start clrevents -p {e13c0d23-ccbc-4e12-931b-d9cc2eee27e4} 0x1CCBD 0x5 -ets -ct perf`

     <span data-ttu-id="0bd12-129">burada:</span><span class="sxs-lookup"><span data-stu-id="0bd12-129">where:</span></span>

    - <span data-ttu-id="0bd12-130">The `-p` parameter identifies the provider GUID.</span><span class="sxs-lookup"><span data-stu-id="0bd12-130">The `-p` parameter identifies the provider GUID.</span></span>

    - <span data-ttu-id="0bd12-131">`0x1CCBD` specifies the categories of events that will be raised.</span><span class="sxs-lookup"><span data-stu-id="0bd12-131">`0x1CCBD` specifies the categories of events that will be raised.</span></span>

    - <span data-ttu-id="0bd12-132">`0x5` sets the level of logging (in this case, verbose (5)).</span><span class="sxs-lookup"><span data-stu-id="0bd12-132">`0x5` sets the level of logging (in this case, verbose (5)).</span></span>

    - <span data-ttu-id="0bd12-133">The `-ets` parameter instructs Logman to send commands to event tracing sessions.</span><span class="sxs-lookup"><span data-stu-id="0bd12-133">The `-ets` parameter instructs Logman to send commands to event tracing sessions.</span></span>

    - <span data-ttu-id="0bd12-134">The `-ct perf` parameter specifies that the `QueryPerformanceCounter` function will be used to log the time stamp for each event.</span><span class="sxs-lookup"><span data-stu-id="0bd12-134">The `-ct perf` parameter specifies that the `QueryPerformanceCounter` function will be used to log the time stamp for each event.</span></span>

2. <span data-ttu-id="0bd12-135">Olayları günlüğe kaydetmeyi durdurmak için şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="0bd12-135">To stop logging the events, type:</span></span>

     `logman stop clrevents -ets`

     <span data-ttu-id="0bd12-136">Bu komut, clrevents.etl adlı bir ikili izleme dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0bd12-136">This command creates a binary trace file named clrevents.etl.</span></span>

### <a name="to-capture-clr-etw-events-using-xperf"></a><span data-ttu-id="0bd12-137">Xperf kullanarak CLR ETW olaylarını yakalamak için</span><span class="sxs-lookup"><span data-stu-id="0bd12-137">To capture CLR ETW events using Xperf</span></span>

1. <span data-ttu-id="0bd12-138">Komut isteminde, şunları yazın:</span><span class="sxs-lookup"><span data-stu-id="0bd12-138">At the command prompt, type:</span></span>

     `xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:5 -f clrevents.etl`

     <span data-ttu-id="0bd12-139">where the GUID is the CLR ETW provider GUID, and `0x1CCBD:5` traces everything at and below level 5 (verbose).</span><span class="sxs-lookup"><span data-stu-id="0bd12-139">where the GUID is the CLR ETW provider GUID, and `0x1CCBD:5` traces everything at and below level 5 (verbose).</span></span>

2. <span data-ttu-id="0bd12-140">İzlemeyi durdurmak için aşağıdakileri yazın:</span><span class="sxs-lookup"><span data-stu-id="0bd12-140">To stop tracing, type:</span></span>

     `Xperf -stop clr`

     <span data-ttu-id="0bd12-141">Bu komut, clrevents.etl adlı bir izleme dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0bd12-141">This command creates a trace file named clrevents.etl.</span></span>

## <a name="viewing-clr-etw-events"></a><span data-ttu-id="0bd12-142">CLR ETW olaylarını görüntüleme</span><span class="sxs-lookup"><span data-stu-id="0bd12-142">Viewing CLR ETW Events</span></span>

<span data-ttu-id="0bd12-143">CLR ETW olaylarını görüntülemek için aşağıda listelenen komutları kullanın.</span><span class="sxs-lookup"><span data-stu-id="0bd12-143">Use the commands listed below to view the CLR ETW events.</span></span> <span data-ttu-id="0bd12-144">For a description of the events, see [CLR ETW Events](clr-etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="0bd12-144">For a description of the events, see [CLR ETW Events](clr-etw-events.md).</span></span>

### <a name="to-view-clr-etw-events-using-tracerpt"></a><span data-ttu-id="0bd12-145">Tracerpt kullanarak CLR ETW olaylarını görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="0bd12-145">To view CLR ETW events using Tracerpt</span></span>

- <span data-ttu-id="0bd12-146">Komut isteminde, şunları yazın:</span><span class="sxs-lookup"><span data-stu-id="0bd12-146">At the command prompt, type:</span></span>

     `tracerpt clrevents.etl`

     <span data-ttu-id="0bd12-147">Bu komut iki dosya oluşturur: dumpfile.xml ve summary.txt.</span><span class="sxs-lookup"><span data-stu-id="0bd12-147">This command creates two files: dumpfile.xml and summary.txt.</span></span> <span data-ttu-id="0bd12-148">Dumpfile.xml dosyası tüm olayları listeler ve summary.txt, olayların bir özetini sunar.</span><span class="sxs-lookup"><span data-stu-id="0bd12-148">The dumpfile.xml file lists all the events, and summary.txt provides a summary of the events.</span></span>

### <a name="to-view-clr-etw-events-using-xperf"></a><span data-ttu-id="0bd12-149">Xperf kullanarak CLR ETW olaylarını görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="0bd12-149">To view CLR ETW events using Xperf</span></span>

- <span data-ttu-id="0bd12-150">Komut isteminde, şunları yazın:</span><span class="sxs-lookup"><span data-stu-id="0bd12-150">At the command prompt, type:</span></span>

     `xperf clrevents.etl`

     <span data-ttu-id="0bd12-151">Bu komut Xperf ETL dosya görüntüleyicisini açar.</span><span class="sxs-lookup"><span data-stu-id="0bd12-151">This command opens the Xperf ETL file viewer.</span></span> <span data-ttu-id="0bd12-152">In this viewer, the CLR events show up in the **Generic Events** view.</span><span class="sxs-lookup"><span data-stu-id="0bd12-152">In this viewer, the CLR events show up in the **Generic Events** view.</span></span> <span data-ttu-id="0bd12-153">To display a data grid of events categorized by type, select a region of time in this view, and then right-click and select **Summary**.</span><span class="sxs-lookup"><span data-stu-id="0bd12-153">To display a data grid of events categorized by type, select a region of time in this view, and then right-click and select **Summary**.</span></span>

### <a name="to-convert-the-etl-file-to-a-comma-separated-value-file"></a><span data-ttu-id="0bd12-154">.etl dosyasını, virgülle ayrılmış değerler dosyasına dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="0bd12-154">To convert the .etl file to a comma-separated value file</span></span>

- <span data-ttu-id="0bd12-155">Komut isteminde, şunları yazın:</span><span class="sxs-lookup"><span data-stu-id="0bd12-155">At the command prompt, type:</span></span>

     `xperf -i clrevents.etl -f clrevents.csv`

     <span data-ttu-id="0bd12-156">Bu komut, olayları görüntüleyebileceğiniz bir virgülle ayrılmış değer (CSV) dosyası olarak dökeceğiniz XPerf'e neden olur.</span><span class="sxs-lookup"><span data-stu-id="0bd12-156">This command causes XPerf to dump the events as a comma separated value (CSV) file that you can view.</span></span> <span data-ttu-id="0bd12-157">Çünkü farklı olaylar farklı alanlara sahiptir, bu CSV dosyası veriden önce birden fazla üstbilgi satırını içerir.</span><span class="sxs-lookup"><span data-stu-id="0bd12-157">Because different events have different fields, this CSV file is contains more than one header line before the data.</span></span> <span data-ttu-id="0bd12-158">Her satırın ilk alanı, hangi üstbilginin geri kalan alanları belirlemek için kullanılması gerektiğini gösteren olay türüdür.</span><span class="sxs-lookup"><span data-stu-id="0bd12-158">The first field of every line is the event type, which indicates which header should be used to determine the rest of the fields.</span></span>

## <a name="see-also"></a><span data-ttu-id="0bd12-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0bd12-159">See also</span></span>

- [<span data-ttu-id="0bd12-160">Windows Performance Toolkit</span><span class="sxs-lookup"><span data-stu-id="0bd12-160">Windows Performance Toolkit</span></span>](/windows-hardware/test/wpt/)
- [<span data-ttu-id="0bd12-161">Ortak Dil Çalışma Zamanı Modülünde ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="0bd12-161">ETW Events in the Common Language Runtime</span></span>](etw-events-in-the-common-language-runtime.md)
