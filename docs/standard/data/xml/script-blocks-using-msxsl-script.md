---
title: msxsl:script Kullanan Betik Blokları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fde6f43f-c594-486f-abcb-2211197fae20
ms.openlocfilehash: 3cb65142243d1f910ffd0fb85750ba62786d79f0
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824707"
---
# <a name="script-blocks-using-msxslscript"></a><span data-ttu-id="78def-102">msxsl:script Kullanan Betik Blokları</span><span class="sxs-lookup"><span data-stu-id="78def-102">Script Blocks Using msxsl:script</span></span>
<span data-ttu-id="78def-103"><xref:System.Xml.Xsl.XslCompiledTransform>Sınıfı, öğesini kullanarak katıştırılmış betikleri destekler `msxsl:script` .</span><span class="sxs-lookup"><span data-stu-id="78def-103">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports embedded scripts using the `msxsl:script` element.</span></span> <span data-ttu-id="78def-104">Stil sayfası yüklendiğinde, tanımlanmış tüm işlevler Kod Belge Nesne Modeli (CodeDOM) tarafından Microsoft ara dili (MSIL) ile derlenir ve çalışma zamanında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="78def-104">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by the Code Document Object Model (CodeDOM) and are executed during run time.</span></span> <span data-ttu-id="78def-105">Katıştırılmış betik bloğundan oluşturulan derleme, stil sayfası için oluşturulan derlemeden ayrıdır.</span><span class="sxs-lookup"><span data-stu-id="78def-105">The assembly generated from the embedded script block is separate than the assembly generated for the style sheet.</span></span>  
  
## <a name="enable-xslt-script"></a><span data-ttu-id="78def-106">XSLT betiğini etkinleştir</span><span class="sxs-lookup"><span data-stu-id="78def-106">Enable XSLT Script</span></span>  
 <span data-ttu-id="78def-107">Katıştırılmış betikler için destek, sınıf üzerinde isteğe bağlı bir XSLT ayarıdır <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="78def-107">Support for embedded scripts is an optional XSLT setting on the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="78def-108">Komut dosyası desteği varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="78def-108">Script support is disabled by default.</span></span> <span data-ttu-id="78def-109">Betik desteğini etkinleştirmek için, <xref:System.Xml.Xsl.XsltSettings> <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> özelliği olarak ayarlanmış bir nesne oluşturun `true` ve nesneyi <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemine geçirin.</span><span class="sxs-lookup"><span data-stu-id="78def-109">To enable script support, create an <xref:System.Xml.Xsl.XsltSettings> object with the <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> property set to `true` and pass the object to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78def-110">XSLT betiği oluşturma yalnızca betik desteğine ihtiyacınız varsa ve tamamen güvenilir bir ortamda çalışıyorsanız etkinleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="78def-110">XSLT scripting should be enabled only if you require script support and you are working in a fully trusted environment.</span></span>  
  
## <a name="msxslscript-element-definition"></a><span data-ttu-id="78def-111">msxsl: betik öğesi tanımı</span><span class="sxs-lookup"><span data-stu-id="78def-111">msxsl:script Element Definition</span></span>  
 <span data-ttu-id="78def-112">`msxsl:script`Öğesi, XSLT 1,0 önerisi için bir Microsoft uzantısıdır ve aşağıdaki tanıma sahiptir:</span><span class="sxs-lookup"><span data-stu-id="78def-112">The `msxsl:script` element is a Microsoft extension to the XSLT 1.0 recommendation and has the following definition:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="78def-113">`msxsl`Ön ek, `urn:schemas-microsoft-com:xslt` ad alanı URI 'sine bağlanır.</span><span class="sxs-lookup"><span data-stu-id="78def-113">The `msxsl` prefix is bound to the `urn:schemas-microsoft-com:xslt` namespace URI.</span></span> <span data-ttu-id="78def-114">Stil sayfası, `xmlns:msxsl=urn:schemas-microsoft-com:xslt` ad alanı bildirimini içermelidir.</span><span class="sxs-lookup"><span data-stu-id="78def-114">The style sheet must include the `xmlns:msxsl=urn:schemas-microsoft-com:xslt` namespace declaration.</span></span>  
  
 <span data-ttu-id="78def-115">`language`Özniteliği isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="78def-115">The `language` attribute is optional.</span></span> <span data-ttu-id="78def-116">Değeri, gömülü kod bloğunun kod dilidir.</span><span class="sxs-lookup"><span data-stu-id="78def-116">Its value is the code language of the embedded code block.</span></span> <span data-ttu-id="78def-117">Dil, yöntemi kullanılarak uygun CodeDOM derleyicisi ile eşleştirilir <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="78def-117">The language is mapped to the appropriate CodeDOM compiler using the <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="78def-118"><xref:System.Xml.Xsl.XslCompiledTransform>Sınıfı, uygun sağlayıcının makinede yüklü olduğunu varsayarak ve machine.config dosyasının System. CodeDom bölümünde kayıtlı olan tüm Microsoft .net dillerini destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="78def-118">The <xref:System.Xml.Xsl.XslCompiledTransform> class can support any Microsoft .NET language, assuming the appropriate provider is installed on the machine and is registered in the system.codedom section of the machine.config file.</span></span> <span data-ttu-id="78def-119">Bir `language` öznitelik belirtilmemişse, dil varsayılan olarak JScript olur.</span><span class="sxs-lookup"><span data-stu-id="78def-119">If a `language` attribute is not specified, the language defaults to JScript.</span></span> <span data-ttu-id="78def-120">Dil adı büyük/küçük harfe duyarlı değildir, bu nedenle ' JavaScript ' ve ' JavaScript ' eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="78def-120">The language name is not case-sensitive so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="78def-121">`implements-prefix`Özniteliği zorunludur.</span><span class="sxs-lookup"><span data-stu-id="78def-121">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="78def-122">Bu öznitelik, bir ad alanını bildirmek ve betik bloğu ile ilişkilendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="78def-122">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="78def-123">Bu özniteliğin değeri, ad alanını temsil eden önekidir.</span><span class="sxs-lookup"><span data-stu-id="78def-123">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="78def-124">Bu ön ek, bir stil sayfasında bir yerde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="78def-124">This prefix can be defined somewhere in a style sheet.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78def-125">`msxsl:script`Öğesi kullanılırken, dilden bağımsız olarak betiğin BIR CDATA bölümünün içine yerleştirilmesi önemle önerilir.</span><span class="sxs-lookup"><span data-stu-id="78def-125">When using the `msxsl:script` element, we strongly recommend that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="78def-126">Komut dosyası belirli bir dil için işleç, tanımlayıcı veya sınırlayıcılar içerebildiğinden, CDATA bölümünde yoksa, XML olarak yanlış yorumlanmakta olma olasılığı vardır.</span><span class="sxs-lookup"><span data-stu-id="78def-126">Because the script can contain operators, identifiers, or delimiters for a given language, if it is not contained within a CDATA section, it has the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="78def-127">Aşağıdaki XML, kodun yerleştirilebileceği CDATA bölümünün bir şablonunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="78def-127">The following XML shows a template of the CDATA section where code can be placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='your-prefix' language='CSharp'>  
<![CDATA[  
// Code block.  
]]>  
</msxsl:script>  
```  
  
## <a name="script-functions"></a><span data-ttu-id="78def-128">Betik Işlevleri</span><span class="sxs-lookup"><span data-stu-id="78def-128">Script Functions</span></span>  
 <span data-ttu-id="78def-129">İşlevler, öğesi içinde bildirilebilecek `msxsl:script` .</span><span class="sxs-lookup"><span data-stu-id="78def-129">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="78def-130">Bir işlev bildirildiğinde, bir betik bloğunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="78def-130">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="78def-131">Stil sayfaları, her biri diğerinin bağımsız olarak çalışan birden çok betik bloğu içerebilir.</span><span class="sxs-lookup"><span data-stu-id="78def-131">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="78def-132">Diğer bir deyişle, bir betik bloğunun içinde yürütüyorsunuz, aynı ad alanına ve aynı komut dosyası diline sahip olmak üzere bildirilmeden, başka bir betik bloğunda tanımladığınız bir işlevi çağıramadığınız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="78def-132">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="78def-133">Her bir betik bloğu kendi dilinde olabileceğinden ve blok söz konusu dil ayrıştırıcısının dilbilgisi kurallarına göre ayrıştırılacağından, kullanımda olan dil için doğru sözdizimini kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="78def-133">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser we recommend that you use the correct syntax for the language in use.</span></span> <span data-ttu-id="78def-134">Örneğin, bir Microsoft C# komut dosyası bloğunda, C# açıklama sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="78def-134">For example, if you are in a Microsoft C# script block, use the C# comment syntax.</span></span>  
  
 <span data-ttu-id="78def-135">Sağlanan bağımsız değişkenler ve işlevin dönüş değerleri herhangi bir türde olabilir.</span><span class="sxs-lookup"><span data-stu-id="78def-135">The supplied arguments and return values to the function can be of any type.</span></span> <span data-ttu-id="78def-136">W3C XPath türleri ortak dil çalışma zamanı (CLR) türlerinin bir alt kümesi olduğundan, bir XPath türü olarak kabul etmeyen türler için tür dönüştürme gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="78def-136">Because the W3C XPath types are a subset of the common language runtime (CLR) types, type conversion takes place on types that are not considered to be an XPath type.</span></span> <span data-ttu-id="78def-137">Aşağıdaki tabloda karşılık gelen W3C türleri ve eşdeğer CLR türü gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="78def-137">The following table shows the corresponding W3C types and the equivalent CLR type.</span></span>  
  
|<span data-ttu-id="78def-138">W3C türü</span><span class="sxs-lookup"><span data-stu-id="78def-138">W3C type</span></span>|<span data-ttu-id="78def-139">CLR türü</span><span class="sxs-lookup"><span data-stu-id="78def-139">CLR type</span></span>|  
|--------------|--------------|  
|`String`|<xref:System.String>|  
|`Boolean`|<xref:System.Boolean>|  
|`Number`|<xref:System.Double>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator>|  
  
 <span data-ttu-id="78def-140">CLR sayısal türleri öğesine dönüştürülür <xref:System.Double> .</span><span class="sxs-lookup"><span data-stu-id="78def-140">CLR numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="78def-141"><xref:System.DateTime>Tür öğesine dönüştürülür <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="78def-141">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="78def-142"><xref:System.Xml.XPath.IXPathNavigable> türler öğesine dönüştürülür <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="78def-142"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="78def-143">**XPathNavigator []** , öğesine dönüştürüldü <xref:System.Xml.XPath.XPathNodeIterator> .</span><span class="sxs-lookup"><span data-stu-id="78def-143">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="78def-144">Diğer tüm türler bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="78def-144">All other types throw an error.</span></span>  
  
### <a name="importing-namespaces-and-assemblies"></a><span data-ttu-id="78def-145">Ad alanları ve derlemeler içeri aktarılıyor</span><span class="sxs-lookup"><span data-stu-id="78def-145">Importing Namespaces and Assemblies</span></span>  
 <span data-ttu-id="78def-146"><xref:System.Xml.Xsl.XslCompiledTransform>Sınıfı, varsayılan olarak öğesi tarafından desteklenen derleme ve ad alanları kümesini önceden tanımlar `msxsl:script` .</span><span class="sxs-lookup"><span data-stu-id="78def-146">The <xref:System.Xml.Xsl.XslCompiledTransform> class predefines a set of assemblies and namespaces that are supported by default by the `msxsl:script` element.</span></span> <span data-ttu-id="78def-147">Ancak, derleme ve ad alanını bloğunda içeri aktararak önceden tanımlanmış listede olmayan bir ad alanına ait sınıfları ve üyeleri kullanabilirsiniz `msxsl:script` .</span><span class="sxs-lookup"><span data-stu-id="78def-147">However, you can use classes and members belonging to a namespace that is not on the predefined list by importing the assembly and namespace in `msxsl:script` block.</span></span>  
  
#### <a name="assemblies"></a><span data-ttu-id="78def-148">Bütünleştirilmiş Kodlar</span><span class="sxs-lookup"><span data-stu-id="78def-148">Assemblies</span></span>  
 <span data-ttu-id="78def-149">Aşağıdaki iki derlemeye varsayılan olarak başvurulur:</span><span class="sxs-lookup"><span data-stu-id="78def-149">The following two assemblies are referenced by default:</span></span>  
  
- <span data-ttu-id="78def-150">System.dll</span><span class="sxs-lookup"><span data-stu-id="78def-150">System.dll</span></span>  
  
- <span data-ttu-id="78def-151">System.Xml.dll</span><span class="sxs-lookup"><span data-stu-id="78def-151">System.Xml.dll</span></span>  
  
- <span data-ttu-id="78def-152">Microsoft.VisualBasic.dll (komut dosyası dili VB olduğunda)</span><span class="sxs-lookup"><span data-stu-id="78def-152">Microsoft.VisualBasic.dll (when the script language is VB)</span></span>  
  
 <span data-ttu-id="78def-153">Öğesini kullanarak ek derlemeleri içeri aktarabilirsiniz `msxsl:assembly` .</span><span class="sxs-lookup"><span data-stu-id="78def-153">You can import the additional assemblies using the `msxsl:assembly` element.</span></span> <span data-ttu-id="78def-154">Bu, stil sayfası derlendiğinde derlemeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="78def-154">This includes the assembly when the style sheet is compiled.</span></span> <span data-ttu-id="78def-155">`msxsl:assembly`Öğesi aşağıdaki tanıma sahiptir:</span><span class="sxs-lookup"><span data-stu-id="78def-155">The `msxsl:assembly` element has the following definition:</span></span>  
  
```xml  
<msxsl:script>  
  <msxsl:assembly name="system.assemblyName" />  
  <msxsl:assembly href="path-name" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="78def-156">`name`Öznitelik, derlemenin adını içerir ve `href` özniteliği derlemenin yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="78def-156">The `name` attribute contains the name of the assembly and the `href` attribute contains the path to the assembly.</span></span> <span data-ttu-id="78def-157">Derleme adı "System. Data, Version = 2.0.3600.0, Culture = neutral, PublicKeyToken = b77a5c561934e089" gibi bir tam ad veya "System. Web" gibi kısa bir ad olabilir.</span><span class="sxs-lookup"><span data-stu-id="78def-157">The assembly name can be a full name, such as "System.Data, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b77a5c561934e089", or a short name, such as "System.Web".</span></span>  
  
#### <a name="namespaces"></a><span data-ttu-id="78def-158">Ad alanları</span><span class="sxs-lookup"><span data-stu-id="78def-158">Namespaces</span></span>  
 <span data-ttu-id="78def-159">Aşağıdaki ad alanları varsayılan olarak dahil edilmiştir:</span><span class="sxs-lookup"><span data-stu-id="78def-159">The following namespaces are included by default:</span></span>  
  
- <span data-ttu-id="78def-160">Sistem</span><span class="sxs-lookup"><span data-stu-id="78def-160">System</span></span>  
  
- <span data-ttu-id="78def-161">System.Collection</span><span class="sxs-lookup"><span data-stu-id="78def-161">System.Collection</span></span>  
  
- <span data-ttu-id="78def-162">System.Text</span><span class="sxs-lookup"><span data-stu-id="78def-162">System.Text</span></span>  
  
- <span data-ttu-id="78def-163">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="78def-163">System.Text.RegularExpressions</span></span>  
  
- <span data-ttu-id="78def-164">System.Xml</span><span class="sxs-lookup"><span data-stu-id="78def-164">System.Xml</span></span>  
  
- <span data-ttu-id="78def-165">System.Xml. Xls</span><span class="sxs-lookup"><span data-stu-id="78def-165">System.Xml.Xsl</span></span>  
  
- <span data-ttu-id="78def-166">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="78def-166">System.Xml.XPath</span></span>  
  
- <span data-ttu-id="78def-167">Microsoft. VisualBasic (komut dosyası dili VB olduğunda)</span><span class="sxs-lookup"><span data-stu-id="78def-167">Microsoft.VisualBasic (when the script language is VB)</span></span>  
  
 <span data-ttu-id="78def-168">Özniteliğini kullanarak ek ad alanları için destek ekleyebilirsiniz `namespace` .</span><span class="sxs-lookup"><span data-stu-id="78def-168">You can add support for additional namespaces using the `namespace` attribute.</span></span> <span data-ttu-id="78def-169">Öznitelik değeri, ad alanının adıdır.</span><span class="sxs-lookup"><span data-stu-id="78def-169">The attribute value is the name of the namespace.</span></span>  
  
```xml  
<msxsl:script>  
  <msxsl:using namespace="system.namespaceName" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
## <a name="example"></a><span data-ttu-id="78def-170">Örnek</span><span class="sxs-lookup"><span data-stu-id="78def-170">Example</span></span>  
 <span data-ttu-id="78def-171">Aşağıdaki örnek, yarıçapı verilen bir dairenin çevresini hesaplamak için gömülü bir betiği kullanır.</span><span class="sxs-lookup"><span data-stu-id="78def-171">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
 [!code-csharp[XSLT_Script#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Script/CS/xslt_script.cs#1)]
 [!code-vb[XSLT_Script#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Script/VB/xslt_script.vb#1)]  
  
#### <a name="numberxml"></a><span data-ttu-id="78def-172">number.xml</span><span class="sxs-lookup"><span data-stu-id="78def-172">number.xml</span></span>  
 [!code-xml[XSLT_Script#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/number.xml#2)]  
  
#### <a name="calcxsl"></a><span data-ttu-id="78def-173">Calc. Xsl</span><span class="sxs-lookup"><span data-stu-id="78def-173">calc.xsl</span></span>  
 [!code-xml[XSLT_Script#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/calc.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="78def-174">Çıkış</span><span class="sxs-lookup"><span data-stu-id="78def-174">Output</span></span>  
  
```xml  
<circles xmlns:msxsl="urn:schemas-microsoft-com:xslt" xmlns:user="urn:my-scripts">  
  <circle>  
    <radius>12</radius>  
    <circumference>75.36</circumference>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
    <circumference>235.5</circumference>  
  </circle>  
</circles>  
```  
  
## <a name="see-also"></a><span data-ttu-id="78def-175">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78def-175">See also</span></span>

- [<span data-ttu-id="78def-176">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="78def-176">XSLT Transformations</span></span>](xslt-transformations.md)
- [<span data-ttu-id="78def-177">Dinamik kaynak kodu oluşturma ve derleme</span><span class="sxs-lookup"><span data-stu-id="78def-177">Dynamic Source Code Generation and Compilation</span></span>](../../../framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)
