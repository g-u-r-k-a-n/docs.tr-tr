---
title: <msxsl:script> Kullanarak XSLT Stil Sayfası Betiğini Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
ms.openlocfilehash: 61538656580878da775d4a42dac40165c7941eee
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818277"
---
# <a name="xslt-stylesheet-scripting-using-msxslscript"></a><span data-ttu-id="46c9b-102">Kullanarak XSLT stil sayfası betiği oluşturma \<msxsl:script></span><span class="sxs-lookup"><span data-stu-id="46c9b-102">XSLT Stylesheet Scripting Using \<msxsl:script></span></span>
<span data-ttu-id="46c9b-103"><xref:System.Xml.Xsl.XslTransform>Sınıfı, öğesini kullanarak gömülü komut dosyalarını destekler `script` .</span><span class="sxs-lookup"><span data-stu-id="46c9b-103">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="46c9b-104"><xref:System.Xml.Xsl.XslTransform>Sınıf .NET Framework 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="46c9b-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="46c9b-105">Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="46c9b-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="46c9b-106">Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="46c9b-106">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="46c9b-107"><xref:System.Xml.Xsl.XslTransform>Sınıfı, öğesini kullanarak gömülü komut dosyalarını destekler `script` .</span><span class="sxs-lookup"><span data-stu-id="46c9b-107">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span> <span data-ttu-id="46c9b-108">Stil sayfası yüklendiğinde, tanımlanmış tüm işlevler bir sınıf tanımına sarmalanarak Microsoft ara dili 'ne (MSIL) derlenir ve sonuç olarak performans kaybı olmaz.</span><span class="sxs-lookup"><span data-stu-id="46c9b-108">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by being wrapped in a class definition and have no performance loss as a result.</span></span>  
  
 <span data-ttu-id="46c9b-109">`<msxsl:script>`Öğe aşağıda tanımlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="46c9b-109">The `<msxsl:script>` element is defined below:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="46c9b-110">, `msxsl` ad alanına göre bir ön ek olur `urn:schemas-microsoft-com:xslt` .</span><span class="sxs-lookup"><span data-stu-id="46c9b-110">where `msxsl` is a prefix bound to the namespace `urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="46c9b-111">`language`Özniteliği zorunlu değildir, ancak belirtilmişse değeri şunlardan biri olmalıdır: `C#` , `VB` ,, `JScript` `JavaScript` , `VisualBasic` veya `CSharp` .</span><span class="sxs-lookup"><span data-stu-id="46c9b-111">The `language` attribute is not mandatory, but if specified, its value must be one of the following: `C#`, `VB`, `JScript`, `JavaScript`, `VisualBasic`, or `CSharp`.</span></span> <span data-ttu-id="46c9b-112">Belirtilmemişse, dil varsayılan olarak JScript olur.</span><span class="sxs-lookup"><span data-stu-id="46c9b-112">If not specified, the language defaults to JScript.</span></span> <span data-ttu-id="46c9b-113">`language-name`Büyük/küçük harfe duyarlı değildir, bu nedenle ' JavaScript ' ve ' JavaScript ' eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="46c9b-113">The `language-name` is not case-sensitive, so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="46c9b-114">`implements-prefix`Özniteliği zorunludur.</span><span class="sxs-lookup"><span data-stu-id="46c9b-114">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="46c9b-115">Bu öznitelik, bir ad alanını bildirmek ve betik bloğu ile ilişkilendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="46c9b-115">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="46c9b-116">Bu özniteliğin değeri, ad alanını temsil eden önekidir.</span><span class="sxs-lookup"><span data-stu-id="46c9b-116">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="46c9b-117">Bu ad alanı, bir stil sayfasında bir yerde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="46c9b-117">This namespace can be defined somewhere in a style sheet.</span></span>  
  
 <span data-ttu-id="46c9b-118">`msxsl:script`Öğesi ad alanına ait olduğundan `urn:schemas-microsoft-com:xslt` , stil sayfası ad alanı bildirimini içermelidir `xmlns:msxsl=urn:schemas-microsoft-com:xslt` .</span><span class="sxs-lookup"><span data-stu-id="46c9b-118">Because the `msxsl:script` element belongs to the namespace `urn:schemas-microsoft-com:xslt`, the style sheet must include the namespace declaration `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="46c9b-119">Komut dosyası çağıranın <xref:System.Security.Permissions.SecurityPermissionFlag> erişim izni yoksa, bir stil sayfasındaki betiği hiçbir şekilde derlenmez ve çağrısı <xref:System.Xml.Xsl.XslTransform.Load%2A> başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="46c9b-119">If the caller of the script does not have <xref:System.Security.Permissions.SecurityPermissionFlag> access permission, then the script in a style sheet will never compile and the call to <xref:System.Xml.Xsl.XslTransform.Load%2A> will fail.</span></span>  
  
 <span data-ttu-id="46c9b-120">Çağıranın `UnmanagedCode` izni varsa, komut dosyası derlenir, ancak izin verilen işlemler, yükleme zamanında sağlanan kanıta bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="46c9b-120">If the caller has `UnmanagedCode` permission, the script compiles, but the operations that are allowed are dependent on the evidence that is supplied at load time.</span></span>  
  
 <span data-ttu-id="46c9b-121"><xref:System.Xml.Xsl.XslTransform.Load%2A> <xref:System.Xml.XmlReader> Stil sayfasını yüklemek veya içeren yöntemlerden birini kullanıyorsanız <xref:System.Xml.XPath.XPathNavigator> , <xref:System.Xml.Xsl.XslTransform.Load%2A> <xref:System.Security.Policy.Evidence> bağımsız değişkenlerinden biri olarak bir parametre alan aşırı yüklemeyi kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="46c9b-121">If you are using one of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlReader> or <xref:System.Xml.XPath.XPathNavigator> to load the style sheet, you need to use the <xref:System.Xml.Xsl.XslTransform.Load%2A> overload that takes an <xref:System.Security.Policy.Evidence> parameter as one of its arguments.</span></span> <span data-ttu-id="46c9b-122">Kanıt sağlamak için çağıranın <xref:System.Security.Permissions.SecurityPermissionFlag> betik derlemesini sağlama izni olması gerekir `Evidence` .</span><span class="sxs-lookup"><span data-stu-id="46c9b-122">To provide evidence, the caller must have <xref:System.Security.Permissions.SecurityPermissionFlag> permission to supply `Evidence` for the script assembly.</span></span> <span data-ttu-id="46c9b-123">Çağıranın bu izni yoksa, `Evidence` parametresini olarak ayarlayabilirler `null` .</span><span class="sxs-lookup"><span data-stu-id="46c9b-123">If the caller does not have this permission, then they can set the `Evidence` parameter to `null`.</span></span> <span data-ttu-id="46c9b-124">Bu, <xref:System.Xml.Xsl.XslTransform.Load%2A> komut dosyası bulursa işlevin başarısız olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="46c9b-124">This causes the <xref:System.Xml.Xsl.XslTransform.Load%2A> function to fail if it finds script.</span></span> <span data-ttu-id="46c9b-125">`ControlEvidence`İzin, yalnızca son derece güvenilen koda verilmesi gereken çok güçlü bir izin olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="46c9b-125">The `ControlEvidence` permission is considered a very powerful permission that should only be granted to highly trusted code.</span></span>  
  
 <span data-ttu-id="46c9b-126">Derlemeinizden kanıt almak için kullanın `this.GetType().Assembly.Evidence` .</span><span class="sxs-lookup"><span data-stu-id="46c9b-126">To get the evidence from your assembly, use `this.GetType().Assembly.Evidence`.</span></span> <span data-ttu-id="46c9b-127">Bir Tekdüzen Kaynak tanımlayıcısından (URI) kanıt almak için kullanın `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)` .</span><span class="sxs-lookup"><span data-stu-id="46c9b-127">To get the evidence from a Uniform Resource Identifier (URI), use `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.</span></span>  
  
 <span data-ttu-id="46c9b-128"><xref:System.Xml.Xsl.XslTransform.Load%2A>Ancak Hayır alan yöntemler kullanıyorsanız <xref:System.Xml.XmlResolver> `Evidence` , derleme için güvenlik bölgesi varsayılan olarak tam güven olur.</span><span class="sxs-lookup"><span data-stu-id="46c9b-128">If you use <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlResolver> but no `Evidence`, the security zone for the assembly defaults to Full Trust.</span></span> <span data-ttu-id="46c9b-129">Daha fazla bilgi için bkz <xref:System.Security.SecurityZone> . ve [adlandırılmış izin kümeleri](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="46c9b-129">For more information, see <xref:System.Security.SecurityZone> and [Named Permission Sets](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span></span>  
  
 <span data-ttu-id="46c9b-130">İşlevler, öğesi içinde bildirilebilecek `msxsl:script` .</span><span class="sxs-lookup"><span data-stu-id="46c9b-130">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="46c9b-131">Aşağıdaki tabloda, varsayılan olarak desteklenen ad alanları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="46c9b-131">The following table shows the namespaces that are supported by default.</span></span> <span data-ttu-id="46c9b-132">Sınıfları listelenen ad alanları dışında kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46c9b-132">You can use classes outside the listed namespaces.</span></span> <span data-ttu-id="46c9b-133">Ancak, bu sınıfların tam nitelikli olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="46c9b-133">However, these classes must be fully qualified.</span></span>  
  
|<span data-ttu-id="46c9b-134">Varsayılan ad alanları</span><span class="sxs-lookup"><span data-stu-id="46c9b-134">Default Namespaces</span></span>|<span data-ttu-id="46c9b-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46c9b-135">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="46c9b-136">Sistem</span><span class="sxs-lookup"><span data-stu-id="46c9b-136">System</span></span>|<span data-ttu-id="46c9b-137">Sistem sınıfı.</span><span class="sxs-lookup"><span data-stu-id="46c9b-137">System class.</span></span>|  
|<span data-ttu-id="46c9b-138">System.Collection</span><span class="sxs-lookup"><span data-stu-id="46c9b-138">System.Collection</span></span>|<span data-ttu-id="46c9b-139">Koleksiyon sınıfları.</span><span class="sxs-lookup"><span data-stu-id="46c9b-139">Collection classes.</span></span>|  
|<span data-ttu-id="46c9b-140">System.Text</span><span class="sxs-lookup"><span data-stu-id="46c9b-140">System.Text</span></span>|<span data-ttu-id="46c9b-141">Metin sınıfları.</span><span class="sxs-lookup"><span data-stu-id="46c9b-141">Text classes.</span></span>|  
|<span data-ttu-id="46c9b-142">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="46c9b-142">System.Text.RegularExpressions</span></span>|<span data-ttu-id="46c9b-143">Normal ifade sınıfları.</span><span class="sxs-lookup"><span data-stu-id="46c9b-143">Regular expression classes.</span></span>|  
|<span data-ttu-id="46c9b-144">System.Xml</span><span class="sxs-lookup"><span data-stu-id="46c9b-144">System.Xml</span></span>|<span data-ttu-id="46c9b-145">Çekirdek XML sınıfları.</span><span class="sxs-lookup"><span data-stu-id="46c9b-145">Core XML classes.</span></span>|  
|<span data-ttu-id="46c9b-146">System.Xml. Xls</span><span class="sxs-lookup"><span data-stu-id="46c9b-146">System.Xml.Xsl</span></span>|<span data-ttu-id="46c9b-147">XSLT sınıfları.</span><span class="sxs-lookup"><span data-stu-id="46c9b-147">XSLT classes.</span></span>|  
|<span data-ttu-id="46c9b-148">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="46c9b-148">System.Xml.XPath</span></span>|<span data-ttu-id="46c9b-149">XML Path Language (XPath) sınıfları.</span><span class="sxs-lookup"><span data-stu-id="46c9b-149">XML Path Language (XPath) classes.</span></span>|  
|<span data-ttu-id="46c9b-150">Microsoft. VisualBasic</span><span class="sxs-lookup"><span data-stu-id="46c9b-150">Microsoft.VisualBasic</span></span>|<span data-ttu-id="46c9b-151">Microsoft Visual Basic betikleri için sınıflar.</span><span class="sxs-lookup"><span data-stu-id="46c9b-151">Classes for Microsoft Visual Basic scripts.</span></span>|  
  
 <span data-ttu-id="46c9b-152">Bir işlev bildirildiğinde, bir betik bloğunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="46c9b-152">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="46c9b-153">Stil sayfaları, her biri diğerinin bağımsız olarak çalışan birden çok betik bloğu içerebilir.</span><span class="sxs-lookup"><span data-stu-id="46c9b-153">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="46c9b-154">Diğer bir deyişle, bir betik bloğunun içinde yürütüyorsunuz, aynı ad alanına ve aynı komut dosyası diline sahip olmak üzere bildirilmeden, başka bir betik bloğunda tanımladığınız bir işlevi çağıramadığınız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="46c9b-154">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="46c9b-155">Her bir betik bloğu kendi dilinde olabileceğinden ve blok söz konusu dil ayrıştırıcısının dilbilgisi kurallarına göre ayrıştırılacağından, kullanımda olan dil için doğru sözdizimini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="46c9b-155">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser, you must use the correct syntax for the language in use.</span></span> <span data-ttu-id="46c9b-156">Örneğin, bir C# komut dosyası bloğunda, bloğunda bir XML açıklama düğümü kullanılması hatadır `<!-- an XML comment -->` .</span><span class="sxs-lookup"><span data-stu-id="46c9b-156">For example, if you are in a C# script block, then it is an error to use an XML comment node `<!-- an XML comment -->` in the block.</span></span>  
  
 <span data-ttu-id="46c9b-157">Sağlanan bağımsız değişkenler ve betik işlevleri tarafından tanımlanan dönüş değerleri World Wide Web Konsorsiyumu (W3C) XPath veya XSLT türlerinden biri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="46c9b-157">The supplied arguments and return values defined by the script functions must be one of the World Wide Web Consortium (W3C) XPath or XSLT types.</span></span> <span data-ttu-id="46c9b-158">Aşağıdaki tabloda karşılık gelen W3C türleri, eşdeğer .NET Framework sınıfları (türü) ve W3C türünün bir XPath türü veya XSLT türü olup olmadığı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="46c9b-158">The following table shows the corresponding W3C types, the equivalent .NET Framework classes (Type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="46c9b-159">Tür</span><span class="sxs-lookup"><span data-stu-id="46c9b-159">Type</span></span>|<span data-ttu-id="46c9b-160">Eşdeğer .NET Framework sınıfı (tür)</span><span class="sxs-lookup"><span data-stu-id="46c9b-160">Equivalent .NET Framework Class (Type)</span></span>|<span data-ttu-id="46c9b-161">XPath türü veya XSLT türü</span><span class="sxs-lookup"><span data-stu-id="46c9b-161">XPath type or XSLT type</span></span>|  
|----------|----------------------------------------------|-----------------------------|  
|<span data-ttu-id="46c9b-162">Dize</span><span class="sxs-lookup"><span data-stu-id="46c9b-162">String</span></span>|<span data-ttu-id="46c9b-163">System. String</span><span class="sxs-lookup"><span data-stu-id="46c9b-163">System.String</span></span>|<span data-ttu-id="46c9b-164">XPath</span><span class="sxs-lookup"><span data-stu-id="46c9b-164">XPath</span></span>|  
|<span data-ttu-id="46c9b-165">Boole</span><span class="sxs-lookup"><span data-stu-id="46c9b-165">Boolean</span></span>|<span data-ttu-id="46c9b-166">System. Boolean</span><span class="sxs-lookup"><span data-stu-id="46c9b-166">System.Boolean</span></span>|<span data-ttu-id="46c9b-167">XPath</span><span class="sxs-lookup"><span data-stu-id="46c9b-167">XPath</span></span>|  
|<span data-ttu-id="46c9b-168">Sayı</span><span class="sxs-lookup"><span data-stu-id="46c9b-168">Number</span></span>|<span data-ttu-id="46c9b-169">System. Double</span><span class="sxs-lookup"><span data-stu-id="46c9b-169">System.Double</span></span>|<span data-ttu-id="46c9b-170">XPath</span><span class="sxs-lookup"><span data-stu-id="46c9b-170">XPath</span></span>|  
|<span data-ttu-id="46c9b-171">Sonuç ağacı parçası</span><span class="sxs-lookup"><span data-stu-id="46c9b-171">Result Tree Fragment</span></span>|<span data-ttu-id="46c9b-172">System.Xml. XPath. XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="46c9b-172">System.Xml.XPath.XPathNavigator</span></span>|<span data-ttu-id="46c9b-173">XSLT</span><span class="sxs-lookup"><span data-stu-id="46c9b-173">XSLT</span></span>|  
|<span data-ttu-id="46c9b-174">Düğüm kümesi</span><span class="sxs-lookup"><span data-stu-id="46c9b-174">Node Set</span></span>|<span data-ttu-id="46c9b-175">System.Xml. XPath. XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="46c9b-175">System.Xml.XPath.XPathNodeIterator</span></span>|<span data-ttu-id="46c9b-176">XPath</span><span class="sxs-lookup"><span data-stu-id="46c9b-176">XPath</span></span>|  
  
 <span data-ttu-id="46c9b-177">Betik işlevi şu sayısal türlerden birini kullanıyorsa: Int16, UInt16, Int32, UInt32, Int64, UInt64, Single veya Decimal, W3C XPath tür numarasıyla eşlenen Double olarak zorlanır.</span><span class="sxs-lookup"><span data-stu-id="46c9b-177">If the script function utilizes one of the following numeric types: Int16, UInt16, Int32, UInt32, Int64, UInt64, Single, or Decimal, they are forced to Double, which maps to the W3C XPath type number.</span></span> <span data-ttu-id="46c9b-178">Tüm diğer türler, yöntemi çağırarak bir dizeye zorlanır `ToString` .</span><span class="sxs-lookup"><span data-stu-id="46c9b-178">All other types are forced to a string by calling the `ToString` method.</span></span>  
  
 <span data-ttu-id="46c9b-179">Betik işlevi yukarıda bahsedilen olanlardan farklı bir tür kullanıyorsa veya işlev, nesne içine yüklendiğinde işlev derlenmezse, <xref:System.Xml.Xsl.XslTransform> bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="46c9b-179">If the script function utilizes a type other than the ones mentioned above, or if the function does not compile when the style sheet is loaded into the <xref:System.Xml.Xsl.XslTransform> object, an exception is thrown.</span></span>  
  
 <span data-ttu-id="46c9b-180">`msxsl:script`Öğesi kullanılırken, dilden bağımsız olarak betiğin BIR CDATA bölümünün içine yerleştirilmesi kesinlikle önerilir.</span><span class="sxs-lookup"><span data-stu-id="46c9b-180">When using the `msxsl:script` element, it is highly recommended that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="46c9b-181">Örneğin, aşağıdaki XML, kodunuzun yerleştirildiği CDATA bölümünün şablonunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="46c9b-181">For example, the following XML shows the template of the CDATA section where your code is placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    <![CDATA[  
    ... your code here ...  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="46c9b-182">Belirli bir dilin işleçleri, tanımlayıcıları veya sınırlandırıcılarının XML olarak yanlış yorumlanmasına sahip olması nedeniyle, tüm betik içeriğinin bir CDATA bölümüne yerleştirilmesi kesinlikle önerilir.</span><span class="sxs-lookup"><span data-stu-id="46c9b-182">It is highly recommended that all script content be placed in a CDATA section, because operators, identifiers, or delimiters for a given language have the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="46c9b-183">Aşağıdaki örnek, komut dosyasında mantıksal AND işlecinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="46c9b-183">The following example shows the use of the logical AND operator in script.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    public string book(string abc, string xyz)  
    {  
        if ((abc == bar) && (abc == xyz)) return bar + xyz;  
        else return null;  
    }  
</msxsl:script>  
```  
  
 <span data-ttu-id="46c9b-184">Bu, ve işaretleri hariç olmadığından bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46c9b-184">This throws an exception because the ampersands are not escaped.</span></span> <span data-ttu-id="46c9b-185">Belge XML olarak yüklenir ve öğe etiketleri arasındaki metne özel bir işleme uygulanmaz `msxsl:script` .</span><span class="sxs-lookup"><span data-stu-id="46c9b-185">The document is loaded as XML, and no special treatment is applied to the text between the `msxsl:script` element tags.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46c9b-186">Örnek</span><span class="sxs-lookup"><span data-stu-id="46c9b-186">Example</span></span>  
 <span data-ttu-id="46c9b-187">Aşağıdaki örnek, yarıçapı verilen bir dairenin çevresini hesaplamak için gömülü bir betiği kullanır.</span><span class="sxs-lookup"><span data-stu-id="46c9b-187">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "calc.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XmlTextWriter to output to the console.
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
    writer.Formatting = Formatting.Indented  
  
    'Transform the file.  
    xslt.Transform(doc, Nothing, writer, Nothing)  
    writer.Close()  
  End Sub
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "number.xml";  
   private const String stylesheet = "calc.xsl";  
  
   public static void Main()  
   {  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XmlTextWriter to output to the console.
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
    writer.Formatting = Formatting.Indented;  
  
    //Transform the file.  
    xslt.Transform(doc, null, writer, null);  
    writer.Close();  
  }  
}  
```  
  
## <a name="input"></a><span data-ttu-id="46c9b-188">Giriş</span><span class="sxs-lookup"><span data-stu-id="46c9b-188">Input</span></span>  
 <span data-ttu-id="46c9b-189">number.xml</span><span class="sxs-lookup"><span data-stu-id="46c9b-189">number.xml</span></span>  
  
```xml  
<?xml version='1.0'?>  
<data>  
  <circle>  
    <radius>12</radius>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
  </circle>  
</data>  
```  
  
 <span data-ttu-id="46c9b-190">Calc. Xsl</span><span class="sxs-lookup"><span data-stu-id="46c9b-190">calc.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
    xmlns:user="urn:my-scripts">  
  
  <msxsl:script language="C#" implements-prefix="user">  
     <![CDATA[  
     public double circumference(double radius)  
     {  
       double pi = 3.14;  
       double circ = pi*radius*2;  
       return circ;  
     }  
      ]]>  
   </msxsl:script>  
  
  <xsl:template match="data">
  <circles>  
  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="user:circumference(radius)"/>
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a><span data-ttu-id="46c9b-191">Çıkış</span><span class="sxs-lookup"><span data-stu-id="46c9b-191">Output</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="46c9b-192">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46c9b-192">See also</span></span>

- [<span data-ttu-id="46c9b-193">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="46c9b-193">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
