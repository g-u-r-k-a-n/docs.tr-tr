---
title: 'Risk azaltma: yol normalleştirme'
description: .NET Framework 'teki yol normalleştirmesini .NET Framework 4.6.2 hedefleyen uygulamalarla başlayarak nasıl değiştiğini öğrenin.
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
ms.openlocfilehash: 6f7e07690ab06fc7ef03344556c045405a63c374
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253602"
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="8f113-103">Risk azaltma: yol normalleştirme</span><span class="sxs-lookup"><span data-stu-id="8f113-103">Mitigation: Path Normalization</span></span>

<span data-ttu-id="8f113-104">.NET Framework 4.6.2 hedeflenen uygulamalarla başlayarak .NET Framework yol normalleştirme değişmiştir.</span><span class="sxs-lookup"><span data-stu-id="8f113-104">Starting with apps that target .NET Framework 4.6.2, path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="8f113-105">Yol normalleştirme nedir?</span><span class="sxs-lookup"><span data-stu-id="8f113-105">What is path normalization?</span></span>  

 <span data-ttu-id="8f113-106">Bir yolun normalleştirilmesi, bir yolu veya dosyayı tanımlayan dizeyi, hedef işletim sisteminde geçerli bir yola uygun olacak şekilde değiştirmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="8f113-106">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="8f113-107">Normalleştirme genellikle şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="8f113-107">Normalization typically involves:</span></span>  
  
- <span data-ttu-id="8f113-108">Standart hale getirme bileşeni ve Dizin ayırıcıları.</span><span class="sxs-lookup"><span data-stu-id="8f113-108">Canonicalizing component and directory separators.</span></span>  
  
- <span data-ttu-id="8f113-109">Geçerli dizin göreli bir yola uygulanıyor.</span><span class="sxs-lookup"><span data-stu-id="8f113-109">Applying the current directory to a relative path.</span></span>  
  
- <span data-ttu-id="8f113-110">Bir yoldaki göreli dizin ( `.` ) veya üst dizin ( `..` ) değerlendiriliyor.</span><span class="sxs-lookup"><span data-stu-id="8f113-110">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
- <span data-ttu-id="8f113-111">Belirtilen karakterler kırpılırken.</span><span class="sxs-lookup"><span data-stu-id="8f113-111">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="8f113-112">Değişiklikler</span><span class="sxs-lookup"><span data-stu-id="8f113-112">The changes</span></span>  

 <span data-ttu-id="8f113-113">.NET Framework 4.6.2 hedefleyen uygulamalarla başlayarak, yol normalleştirme aşağıdaki yollarla değiştirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="8f113-113">Starting with apps that target the .NET Framework 4.6.2, path normalization has changed in the following ways:</span></span>  
  
- <span data-ttu-id="8f113-114">Çalışma zamanı, yolları normalleştirmek için işletim sisteminin [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) işlevine erteler.</span><span class="sxs-lookup"><span data-stu-id="8f113-114">The runtime defers to the operating system's [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) function to normalize paths.</span></span>  
  
- <span data-ttu-id="8f113-115">Normalleştirme artık Dizin segmentlerinin bitmesini (Dizin adının sonundaki bir boşluk gibi) kırpmasını kapsar.</span><span class="sxs-lookup"><span data-stu-id="8f113-115">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
- <span data-ttu-id="8f113-116">`\\.\`mscorlib.dll ' deki dosya g/ç API 'leri için ve dahil olmak üzere tam güvende cihaz yolu söz dizimi desteği `\\?\` .</span><span class="sxs-lookup"><span data-stu-id="8f113-116">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
- <span data-ttu-id="8f113-117">Çalışma zamanı, cihaz sözdizimi yollarını doğrulamaz.</span><span class="sxs-lookup"><span data-stu-id="8f113-117">The runtime does not validate device syntax paths.</span></span>  
  
- <span data-ttu-id="8f113-118">Alternatif veri akışlarına erişmek için cihaz sözdiziminin kullanılması desteklenir.</span><span class="sxs-lookup"><span data-stu-id="8f113-118">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="8f113-119">Etki</span><span class="sxs-lookup"><span data-stu-id="8f113-119">Impact</span></span>  

<span data-ttu-id="8f113-120">.NET Framework 4.6.2 veya üstünü hedefleyen uygulamalar için bu değişiklikler varsayılan olarak açık.</span><span class="sxs-lookup"><span data-stu-id="8f113-120">For apps that target the .NET Framework 4.6.2 or later, these changes are on  by default.</span></span> <span data-ttu-id="8f113-121">Daha önce erişilemeyen yollara erişme yöntemlerine izin verirken performansı artırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8f113-121">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
<span data-ttu-id="8f113-122">.NET Framework 4.6.1 ve önceki sürümlerini hedefleyen ancak .NET Framework 4.6.2 veya üzeri sürümlerde çalışan uygulamalar bu değişiklikten etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="8f113-122">Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="8f113-123">Risk azaltma</span><span class="sxs-lookup"><span data-stu-id="8f113-123">Mitigation</span></span>  

 <span data-ttu-id="8f113-124">.NET Framework 4.6.2 veya üstünü hedefleyen uygulamalar bu değişikliği devre dışı bırakabilirsiniz ve [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyasının bölümüne aşağıdakini ekleyerek eski normalleştirmeyi kullanabilir:</span><span class="sxs-lookup"><span data-stu-id="8f113-124">Apps that target the .NET Framework 4.6.2 or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>  
```  
  
<span data-ttu-id="8f113-125">.NET Framework 4.6.1 veya önceki sürümlerini hedefleyen ancak .NET Framework 4.6.2 veya üzeri sürümlerde çalışan uygulamalar, [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) uygulama. yapılandırma dosyasının bölümüne aşağıdaki satırı ekleyerek yol normalleştirmede yapılan değişiklikleri etkinleştirebilir:</span><span class="sxs-lookup"><span data-stu-id="8f113-125">Apps that target the .NET Framework 4.6.1 or earlier but are running on the .NET Framework 4.6.2 or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8f113-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f113-126">See also</span></span>

- [<span data-ttu-id="8f113-127">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="8f113-127">Application compatibility</span></span>](application-compatibility.md)
