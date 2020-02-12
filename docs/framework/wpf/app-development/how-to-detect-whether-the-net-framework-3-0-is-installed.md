---
title: Nasıl yapılır .NET Framework 3.0'ın Yüklü Olup Olmadığını Algılama
ms.date: 03/30/2017
helpviewer_keywords:
- WinFX Runtime user-agent string
- presence of WPT [WPF], detecting
- detecting WPF presence [WPF]
ms.assetid: 7f71d652-1749-4379-945a-aa2e3994cb43
ms.openlocfilehash: 41010e615b6b3d10ebf6adc0e3f871873e94f409
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124461"
---
# <a name="how-to-detect-whether-the-net-framework-30-is-installed"></a><span data-ttu-id="626b0-102">Nasıl yapılır .NET Framework 3.0'ın Yüklü Olup Olmadığını Algılama</span><span class="sxs-lookup"><span data-stu-id="626b0-102">How to: Detect Whether the .NET Framework 3.0 Is Installed</span></span>
<span data-ttu-id="626b0-103">Yöneticiler bir sistemde Microsoft .NET Framework uygulamaları dağıtabilmek için önce .NET Framework çalışma zamanının mevcut olduğunu doğrulamamalıdır.</span><span class="sxs-lookup"><span data-stu-id="626b0-103">Before administrators can deploy Microsoft .NET Framework applications on a system, they must first confirm that the .NET Framework runtime is present.</span></span> <span data-ttu-id="626b0-104">Bu konuda, yöneticilerin bir sistemde .NET Framework olup olmadığını belirlemede kullanabilecekleri HTML/JavaScript 'te yazılmış bir komut dosyası sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="626b0-104">This topic provides a script written in HTML/JavaScript that administrators can use to determine whether the .NET Framework is present on a system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="626b0-105">Microsoft .NET çerçevesini yükleme, dağıtma ve algılamayla ilgili daha ayrıntılı bilgi için bkz. [Microsoft .NET Framework sürüm 3,0](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480198(v=msdn.10))' i dağıtma.</span><span class="sxs-lookup"><span data-stu-id="626b0-105">For more detailed information on installing, deploying, and detecting the Microsoft .NET Framework, see the discussion in [Deploying Microsoft .NET Framework Version 3.0](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480198(v=msdn.10)).</span></span>  
  
<a name="content_expiration"></a>   
## <a name="detect-the-net-clr-user-agent-string"></a><span data-ttu-id="626b0-106">".NET CLR" Kullanıcı aracısı dizesini Algıla</span><span class="sxs-lookup"><span data-stu-id="626b0-106">Detect the ".NET CLR" User-Agent String</span></span>  
 <span data-ttu-id="626b0-107">.NET Framework yüklendiğinde, MSI ".NET CLR" ve sürüm numarasını UserAgent dizesine ekler.</span><span class="sxs-lookup"><span data-stu-id="626b0-107">When .NET Framework is installed, the MSI adds ".NET CLR" and the version number to the UserAgent string.</span></span> <span data-ttu-id="626b0-108">Aşağıdaki örnek, basit bir HTML sayfasına eklenmiş bir betiği gösterir.</span><span class="sxs-lookup"><span data-stu-id="626b0-108">The following example shows a script embedded in a simple HTML page.</span></span> <span data-ttu-id="626b0-109">Betik, .NET Framework yüklenip yüklenmediğini ve aramanın sonuçlarında bir durum iletisi görüntüleyip oluşturulmayacağını anlamak için UserAgent dizesini arar.</span><span class="sxs-lookup"><span data-stu-id="626b0-109">The script searches the UserAgent string to determine whether .NET Framework is installed, and displays a status message on the results of the search.</span></span>  
  
```html  
<HTML>  
  <HEAD>  
    <TITLE>Test for the .NET Framework 3.0</TITLE>  
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />  
    <SCRIPT LANGUAGE="JavaScript">  
    <!--  
    var dotNETRuntimeVersion = "3.0.04425.00";  
  
    function window::onload()  
    {  
      if (HasRuntimeVersion(dotNETRuntimeVersion))  
      {  
        result.innerText =   
          "This machine has the correct version of the .NET Framework 3.0: "   
          + dotNETRuntimeVersion  
      }   
      else  
      {  
        result.innerText =   
          "This machine does not have the correct version of the .NET Framework 3.0."  
      }  
      result.innerText += "\n\nThis machine's userAgent string is: " +   
        navigator.userAgent + ".";  
    }  
  
    //  
    // Retrieve the version from the user agent string and   
    // compare with the specified version.  
    //  
    function HasRuntimeVersion(versionToCheck)  
    {  
      var userAgentString =   
        navigator.userAgent.match(/.NET CLR [0-9.]+/g);  
  
      if (userAgentString != null)  
      {  
        var i;  
  
        for (i = 0; i < userAgentString.length; ++i)  
        {  
          if (CompareVersions(GetVersion(versionToCheck),   
            GetVersion(userAgentString[i])) <= 0)  
            return true;  
        }  
      }  
  
      return false;  
    }  
  
    //  
    // Extract the numeric part of the version string.  
    //  
    function GetVersion(versionString)  
    {  
      var numericString =   
        versionString.match(/([0-9]+)\.([0-9]+)\.([0-9]+)/i);  
      return numericString.slice(1);  
    }  
  
    //  
    // Compare the 2 version strings by converting them to numeric format.  
    //  
    function CompareVersions(version1, version2)  
    {  
      for (i = 0; i < version1.length; ++i)  
      {  
        var number1 = new Number(version1[i]);  
        var number2 = new Number(version2[i]);  
  
        if (number1 < number2)  
          return -1;  
  
        if (number1 > number2)  
          return 1;  
      }  
  
      return 0;  
    }  
  
    -->  
    </SCRIPT>  
  </HEAD>  
  
  <BODY>  
    <div id="result" />  
  </BODY>  
</HTML>  
```  
  
 <span data-ttu-id="626b0-110">".NET CLR" sürümü için arama başarılı olursa aşağıdaki tür durum iletisi görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="626b0-110">If the search for the ".NET CLR " version is successful, the following type of status message appears:</span></span>  
  
 `This machine has the correct version of the .NET Framework 3.0: 3.0.04425.00`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727; .NET CLR 3.0.04425.00).`  
  
 <span data-ttu-id="626b0-111">Aksi takdirde, aşağıdaki tür durum iletisi görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="626b0-111">Otherwise, the following type of status message appears:</span></span>  
  
 `This machine does not have correct version of the .NET Framework 3.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727).`
