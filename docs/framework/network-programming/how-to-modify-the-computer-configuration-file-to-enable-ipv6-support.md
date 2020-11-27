---
title: 'Nasıl yapılır: IPv6 Desteğini Etkinleştirmek için Bilgisayar Yapılandırma Dosyasını Değiştirme'
description: machine.config, .NET Framework IPv6 desteğini etkinleştirmek için bilgisayar yapılandırma dosyasını nasıl değiştireceğinizi öğrenin.
ms.date: 03/30/2017
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
ms.openlocfilehash: 2c5e3e094eca480a7cab4f7c25cc0fedba196338
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269606"
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a><span data-ttu-id="c32c1-103">Nasıl yapılır: IPv6 Desteğini Etkinleştirmek için Bilgisayar Yapılandırma Dosyasını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="c32c1-103">How to: Modify the Computer Configuration File to Enable IPv6 Support</span></span>

<span data-ttu-id="c32c1-104">Aşağıdaki kod örneği, IPv6 desteğinin etkinleştirilmesi için *machine.config*, bilgisayar yapılandırma dosyasının nasıl değiştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c32c1-104">The following code example shows how to modify the computer configuration file, *machine.config*, to enable IPv6 support.</span></span> <span data-ttu-id="c32c1-105">*machine.config* dosyası, Windows 'un yüklendiği dizindeki *%windir%\Microsoft.NET\Framework* klasöründe depolanır.</span><span class="sxs-lookup"><span data-stu-id="c32c1-105">The *machine.config* file is stored in the *%Windir%\Microsoft.NET\Framework* folder in the directory where Windows was installed.</span></span> <span data-ttu-id="c32c1-106">Bilgisayarda yüklü olan .NET Framework her sürümü için *%windir%\Microsoft.NET\Framework* altındaki klasörlerde ayrı bir *machine.config* dosyası vardır (örneğin, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).</span><span class="sxs-lookup"><span data-stu-id="c32c1-106">There is a separate *machine.config* file in the folders under *%Windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer (for example, *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).</span></span>  
  
 <span data-ttu-id="c32c1-107">Bu ayarlar, bilgisayarın yapılandırma dosyasında öncelikli olan uygulamanın bilgisayar yapılandırma dosyasında da yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="c32c1-107">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="c32c1-108">.NET Framework sürüm 1,1 ve önceki sürümlerde **IPv6 etkin** yapılandırma anahtarının değeri, <xref:System.Net.Dns?displayProperty=nameWithType> sınıfın üyelerinin IPv6 adresleri döndürmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c32c1-108">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="c32c1-109">.NET Framework sürüm 2,0 ve üzeri için, Windows IPv6 'yı destekliyorsa, sınıfın tüm üyeleri <xref:System.Net.Dns?displayProperty=nameWithType> (örneğin, <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> yöntemi) bir sınırlamaya sahip IPv6 adreslerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="c32c1-109">For .NET Framework version 2.0 and later, if Windows supports IPv6, then all members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="c32c1-110">Sınıfın kullanılmayan üyeleri <xref:System.Net.Dns?displayProperty=nameWithType> (örneğin, <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> yöntemi) yapılandırma dosyasındaki değeri okur ve tanır.</span><span class="sxs-lookup"><span data-stu-id="c32c1-110">Obsolete members of the <xref:System.Net.Dns?displayProperty=nameWithType> class (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c32c1-111">.NET Framework sürüm 2,0 ve üzeri için IPv6 varsayılan olarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="c32c1-111">For .NET Framework version 2.0 and later, IPv6 is enabled by default.</span></span> <span data-ttu-id="c32c1-112">.NET Framework sürüm 1,1 ve önceki sürümlerde IPv6 varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="c32c1-112">For .NET Framework version 1.1 and earlier, IPv6 is disabled by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c32c1-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="c32c1-113">Example</span></span>  
  
```xml  
<system.net>  
    …………  
    <settings>  
        …………  
        <ipv6 enabled="true"/>
    ……………  
    </settings>  
    ………………  
</system.net>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c32c1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c32c1-114">See also</span></span>

- [<span data-ttu-id="c32c1-115">IPv6 Adresleme</span><span class="sxs-lookup"><span data-stu-id="c32c1-115">IPv6 Addressing</span></span>](ipv6-addressing.md)
- [<span data-ttu-id="c32c1-116">Ağ ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="c32c1-116">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="c32c1-117">\<ipv6> Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="c32c1-117">\<ipv6> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
