---
ms.openlocfilehash: d33d75b4c2d9bc18844f66f1fcca1e2efc6f1eee
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496151"
---
### <a name="xslt-style-sheet-exception-message-changed"></a><span data-ttu-id="b8ede-101">XSLT stil sayfası özel durum iletisi değişti</span><span class="sxs-lookup"><span data-stu-id="b8ede-101">XSLT style sheet exception message changed</span></span>

#### <a name="details"></a><span data-ttu-id="b8ede-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b8ede-102">Details</span></span>

<span data-ttu-id="b8ede-103">.NET Framework 4,5 ' de, bir XSLT dosyası çok karmaşık olduğunda hata iletisinin metni, &quot; stil sayfası çok karmaşıktır. &quot; Önceki sürümlerde hata iletisi &quot; XSLT derleme hatası idi. &quot; Hata iletisinin metnine bağlı olan uygulama kodu artık çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="b8ede-103">In the .NET Framework 4.5, the text of the error message when an XSLT file is too complex is &quot;The style sheet is too complex.&quot; In previous versions, the error message was &quot;XSLT compile error.&quot; Application code that depends on the text of the error message will no longer work.</span></span> <span data-ttu-id="b8ede-104">Ancak, özel durum türleri aynı kalır, bu nedenle bu değişikliğin gerçek bir etkisi olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b8ede-104">However, the exception types remain the same, so this change should have no real impact.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b8ede-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="b8ede-105">Suggestion</span></span>

<span data-ttu-id="b8ede-106">Bu hata koşulundaki özel durum iletisine bağlı olarak herhangi bir uygulama kodunu, yeni iletiyi bekliyor veya (daha da iyi) kodu, yalnızca değişmemiş özel durum türüne () göre güncelleştirin <xref:System.Xml.Xsl.XsltException?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="b8ede-106">Update any app code depending on the exception message from this error condition to expect the new message, or (even better) update the code to depend only on the exception type (<xref:System.Xml.Xsl.XsltException?displayProperty=fullName>), which has not changed.</span></span>

| <span data-ttu-id="b8ede-107">Name</span><span class="sxs-lookup"><span data-stu-id="b8ede-107">Name</span></span>    | <span data-ttu-id="b8ede-108">Değer</span><span class="sxs-lookup"><span data-stu-id="b8ede-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b8ede-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="b8ede-109">Scope</span></span>   |<span data-ttu-id="b8ede-110">Edge</span><span class="sxs-lookup"><span data-stu-id="b8ede-110">Edge</span></span>|
|<span data-ttu-id="b8ede-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="b8ede-111">Version</span></span>|<span data-ttu-id="b8ede-112">4,5</span><span class="sxs-lookup"><span data-stu-id="b8ede-112">4.5</span></span>|
|<span data-ttu-id="b8ede-113">Tür</span><span class="sxs-lookup"><span data-stu-id="b8ede-113">Type</span></span>|<span data-ttu-id="b8ede-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="b8ede-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="b8ede-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b8ede-115">Affected APIs</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Type)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Reflection.MethodInfo,System.Byte[],System.Type[])?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.String)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Type)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Reflection.MethodInfo,System.Byte[],System.Type[])`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.String,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)`

-->
