---
ms.openlocfilehash: 9fd4e570d9476f5ac4c310759113d72b354a3060
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606279"
---
### <a name="tls-1x-by-default-passes-the-sch_send_aux_record-flag-to-the-underlying-schannel-api"></a><span data-ttu-id="6faa5-101">TLS 1. x varsayılan olarak SCH_SEND_AUX_RECORD bayrağını temel SCHANNEL API 'sine geçirir</span><span class="sxs-lookup"><span data-stu-id="6faa5-101">TLS 1.x by default passes the SCH_SEND_AUX_RECORD flag to the underlying SCHANNEL API</span></span>

#### <a name="details"></a><span data-ttu-id="6faa5-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="6faa5-102">Details</span></span>

<span data-ttu-id="6faa5-103">TLS 1. x kullanırken, .NET Framework temeldeki Windows SCHANNEL API 'sine dayanır.</span><span class="sxs-lookup"><span data-stu-id="6faa5-103">When using TLS 1.x, the .NET Framework relies on the underlying Windows SCHANNEL API.</span></span> <span data-ttu-id="6faa5-104">.NET Framework 4,6 ' den itibaren [SCH_SEND_AUX_RECORD](/windows/win32/api/schannel/ns-schannel-schannel_cred) bayrağı varsayılan olarak SChannel ' a geçirilir.</span><span class="sxs-lookup"><span data-stu-id="6faa5-104">Starting with .NET Framework 4.6, the [SCH_SEND_AUX_RECORD](/windows/win32/api/schannel/ns-schannel-schannel_cred) flag is passed by default to SCHANNEL.</span></span> <span data-ttu-id="6faa5-105">Bu, SCHANNEL 'ın verileri iki ayrı kayıt halinde, ilki tek bir bayt ve ikinciden <em>n</em>-1 bayt olarak şifrelemesine neden olur. Nadir durumlarda, bu durum istemciler ve mevcut sunucular arasındaki iletişimi, verilerin tek bir kayıtta bulunduğu varsayımını yapan bir şekilde keser.</span><span class="sxs-lookup"><span data-stu-id="6faa5-105">This causes SCHANNEL to split data to be encrypted into two separate records, the first as a single byte and the second as <em>n</em>-1 bytes.In rare cases, this breaks communication between clients and existing servers that make the assumption that the data resides in a single record.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6faa5-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="6faa5-106">Suggestion</span></span>

<span data-ttu-id="6faa5-107">Bu değişiklik mevcut bir sunucuyla iletişimi kopararsa, [SCH_SEND_AUX_RECORD](/windows/win32/api/schannel/ns-schannel-schannel_cred) [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyanızın bölümündeki öğesine aşağıdaki anahtarı ekleyerek SCH_SEND_AUX_RECORD bayrağını göndermeyi devre dışı bırakabilir ve verileri ayrı kayıtlara bölmemek için önceki davranışı geri yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6faa5-107">If this change breaks communication with an existing server, you can disable sending the [SCH_SEND_AUX_RECORD](/windows/win32/api/schannel/ns-schannel-schannel_cred) flag and restore the previous behavior of not splitting data into separate records by adding the following switch to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchSendAuxRecord=true" />
</runtime>
```

> [!IMPORTANT]
> <span data-ttu-id="6faa5-108">Bu ayar yalnızca geriye dönük uyumluluk için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6faa5-108">This setting is provided for backward compatibility only.</span></span> <span data-ttu-id="6faa5-109">Aksi takdirde kullanılması önerilmez.</span><span class="sxs-lookup"><span data-stu-id="6faa5-109">Its use is otherwise not recommended.</span></span>

| <span data-ttu-id="6faa5-110">Name</span><span class="sxs-lookup"><span data-stu-id="6faa5-110">Name</span></span>    | <span data-ttu-id="6faa5-111">Değer</span><span class="sxs-lookup"><span data-stu-id="6faa5-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6faa5-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="6faa5-112">Scope</span></span>   | <span data-ttu-id="6faa5-113">Edge</span><span class="sxs-lookup"><span data-stu-id="6faa5-113">Edge</span></span>        |
| <span data-ttu-id="6faa5-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="6faa5-114">Version</span></span> | <span data-ttu-id="6faa5-115">4.6</span><span class="sxs-lookup"><span data-stu-id="6faa5-115">4.6</span></span>         |
| <span data-ttu-id="6faa5-116">Tür</span><span class="sxs-lookup"><span data-stu-id="6faa5-116">Type</span></span>    | <span data-ttu-id="6faa5-117">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="6faa5-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="6faa5-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="6faa5-118">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.ServicePointManager?displayProperty=nameWithType>
- <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
