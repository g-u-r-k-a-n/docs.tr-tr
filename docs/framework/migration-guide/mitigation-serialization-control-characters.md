---
title: 'Risk azaltma: DataContractJsonSerializer ile denetim karakterlerinin serileştirilmesi'
ms.date: 04/07/2017
helpviewer_keywords:
- .NET Framework 4.7 retargeting changes
- retargeting changes
- DataContractJsonSerializer changes
- serialization changes
ms.assetid: e065d458-a128-44f2-9f17-66af9d5be954
ms.openlocfilehash: faa7a32766a3ea1ef9cddcdb8af8fd0dd5a6f287
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457819"
---
# <a name="mitigation-serialization-of-control-characters-with-the-datacontractjsonserializer"></a><span data-ttu-id="7d6fd-102">Risk azaltma: DataContractJsonSerializer ile denetim karakterlerinin serileştirilmesi</span><span class="sxs-lookup"><span data-stu-id="7d6fd-102">Mitigation: Serialization of Control Characters with the DataContractJsonSerializer</span></span>

<span data-ttu-id="7d6fd-103">.NET Framework 4,7 ' den başlayarak, denetim karakterlerinin <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ile serileştirilme yöntemi ECMAScript V6 ve V8 ile uyumlu olacak şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7d6fd-103">Starting with the .NET Framework 4.7, the way in which control characters are serialized with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> has changed to conform to ECMAScript V6 and V8.</span></span> 
 
## <a name="impact"></a><span data-ttu-id="7d6fd-104">Etki</span><span class="sxs-lookup"><span data-stu-id="7d6fd-104">Impact</span></span>

<span data-ttu-id="7d6fd-105">.NET Framework 4.6.2 ve önceki sürümlerde <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, `\b`, `\f`ve `\t`gibi bazı özel denetim karakterlerini ECMAScript V6 ve V8 standartlarıyla uyumlu olacak şekilde serileştirmedi.</span><span class="sxs-lookup"><span data-stu-id="7d6fd-105">In the .NET framework 4.6.2 and earlier versions, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> did not serialize some special control characters, such as `\b`, `\f`, and `\t`, in a way that was compatible with the ECMAScript V6 and V8 standards.</span></span>

<span data-ttu-id="7d6fd-106">.NET Framework 4,7 ' den başlayarak .NET Framework sürümlerini hedefleyen uygulamalar için, bu denetim karakterlerinin serileştirilmesi ECMAScript V6 ve V8 ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="7d6fd-106">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, serialization of these control characters is compatible with ECMAScript V6 and V8.</span></span> <span data-ttu-id="7d6fd-107">Aşağıdaki API 'Ler etkilenir:</span><span class="sxs-lookup"><span data-stu-id="7d6fd-107">The following APIs are affected:</span></span>

- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> 

## <a name="mitigation"></a><span data-ttu-id="7d6fd-108">Azaltma</span><span class="sxs-lookup"><span data-stu-id="7d6fd-108">Mitigation</span></span>

<span data-ttu-id="7d6fd-109">.NET Framework 4,7 ' den başlayarak .NET Framework sürümlerini hedefleyen uygulamalar için, bu davranış varsayılan olarak etkinleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7d6fd-109">For apps that target versions of the .NET Framework starting with the .NET Framework 4.7, this behavior is enabled by default.</span></span>

<span data-ttu-id="7d6fd-110">Bu davranış istenmediğinde, App. config veya Web. config dosyasının `<runtime>` bölümüne aşağıdaki satırı ekleyerek bu özelliği devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7d6fd-110">If this behavior is not desirable, you can opt out of this feature by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false" />
</runtime>
```
 
## <a name="see-also"></a><span data-ttu-id="7d6fd-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d6fd-111">See also</span></span>

- [<span data-ttu-id="7d6fd-112">Uygulama uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="7d6fd-112">Application compatibility</span></span>](application-compatibility.md)
