---
title: Stil Sayfası Parametreleri ve Genişletme Nesneleri için XsltArgumentList
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: de2f0dce-6b98-4908-bba7-ed150cc50355
ms.openlocfilehash: 1c69a6e78207e146c8dbd6cdc252f27f36ab37a2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281706"
---
# <a name="xsltargumentlist-for-style-sheet-parameters-and-extension-objects"></a><span data-ttu-id="9310c-102">Stil Sayfası Parametreleri ve Genişletme Nesneleri için XsltArgumentList</span><span class="sxs-lookup"><span data-stu-id="9310c-102">XsltArgumentList for Style Sheet Parameters and Extension Objects</span></span>
<span data-ttu-id="9310c-103"><xref:System.Xml.Xsl.XsltArgumentList>Sınıfı, dönüşümler (XSLT) parametreleri ve XSLT uzantı nesneleri Için Genişletilebilir Stil sayfası dili içerir.</span><span class="sxs-lookup"><span data-stu-id="9310c-103">The <xref:System.Xml.Xsl.XsltArgumentList> class contains Extensible Stylesheet Language for Transformations (XSLT) parameters and XSLT extension objects.</span></span> <span data-ttu-id="9310c-104"><xref:System.Xml.Xsl.XslTransform.Transform%2A>Yöntemine geçirildiğinde, bu parametreler ve uzantı nesneleri stil sayfalarından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="9310c-104">When passed into the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, these parameters and extension objects can be invoked from style sheets.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9310c-105"><xref:System.Xml.Xsl.XslTransform>Ve <xref:System.Xml.Xsl.XsltArgumentList> sınıfları .NET Framework 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="9310c-105">The <xref:System.Xml.Xsl.XslTransform> and <xref:System.Xml.Xsl.XsltArgumentList> classes are obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="9310c-106">Sınıfını kullanarak XSLT dönüştürmeleri yapabilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="9310c-106">You can perform XSLT transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="9310c-107">Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="9310c-107">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="9310c-108"><xref:System.Xml.Xsl.XsltArgumentList>Sınıf xslt parametreleri ve XSLT uzantı nesneleri içerir.</span><span class="sxs-lookup"><span data-stu-id="9310c-108">The <xref:System.Xml.Xsl.XsltArgumentList> class contains XSLT parameters and XSLT extension objects.</span></span> <span data-ttu-id="9310c-109"><xref:System.Xml.Xsl.XslTransform.Transform%2A>Yöntemine geçirildiğinde, bu parametreler ve uzantı nesneleri stil sayfalarından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="9310c-109">When passed into the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, these parameters and extension objects can be invoked from style sheets.</span></span>  
  
 <span data-ttu-id="9310c-110">Bir katıştırılmış betik kullanmak yerine bir nesne geçirmenin avantajları aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9310c-110">The following are advantages to passing an object rather than using an embedded script:</span></span>  
  
- <span data-ttu-id="9310c-111">Sınıfların daha iyi kapsüllemesini ve yeniden kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9310c-111">Provides better encapsulation and reuse of classes.</span></span>  
  
- <span data-ttu-id="9310c-112">Stil sayfalarının daha küçük ve sürdürülebilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9310c-112">Allows style sheets to be smaller and more maintainable.</span></span>  
  
- <span data-ttu-id="9310c-113">Desteklenen ad alanları kümesi içinde tanımlananlardan farklı ad alanlarına ait sınıflarda çağırma yöntemlerini destekler <xref:System> .</span><span class="sxs-lookup"><span data-stu-id="9310c-113">Supports calling methods on classes belonging to namespaces other than those defined within the set of supported <xref:System> namespaces.</span></span>  
  
- <span data-ttu-id="9310c-114">, İle birlikte stil sayfasına sonuç ağacı parçalarının geçirilmesini destekler <xref:System.Xml.XPath.XPathNodeIterator> .</span><span class="sxs-lookup"><span data-stu-id="9310c-114">Supports passing result tree fragments to the style sheet with the use of the <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
## <a name="xslt-style-sheet-parameters"></a><span data-ttu-id="9310c-115">XSLT stil sayfası parametreleri</span><span class="sxs-lookup"><span data-stu-id="9310c-115">XSLT Style Sheet Parameters</span></span>  
 <span data-ttu-id="9310c-116">XSLT parametreleri yöntemi kullanılarak öğesine eklenir <xref:System.Xml.Xsl.XsltArgumentList> <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> .</span><span class="sxs-lookup"><span data-stu-id="9310c-116">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="9310c-117">Tam ad ve ad alanı Tekdüzen Kaynak tanımlayıcısı (URI), parametre nesnesiyle ilişkili zamanda ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="9310c-117">A qualified name and namespace Uniform Resource Identifier (URI) are associated with the parameter object at that time.</span></span>  
  
 <span data-ttu-id="9310c-118">Parameter nesnesi bir World Wide Web Konsorsiyumu (W3C) türüne karşılık gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="9310c-118">The parameter object should correspond to a World Wide Web Consortium (W3C) type.</span></span> <span data-ttu-id="9310c-119">Aşağıdaki tablo, karşılık gelen W3C türlerini, eşdeğer .NET Framework sınıfları (türü) ve W3C türünün bir XML Path Language (XPath) türü ya da XSLT türü olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9310c-119">The following table shows the corresponding W3C types, the equivalent .NET Framework classes (type), and whether the W3C type is an XML Path Language (XPath) type or XSLT type.</span></span>  
  
|<span data-ttu-id="9310c-120">W3C türü</span><span class="sxs-lookup"><span data-stu-id="9310c-120">W3C Type</span></span>|<span data-ttu-id="9310c-121">Eşdeğer .NET Framework sınıfı (tür)</span><span class="sxs-lookup"><span data-stu-id="9310c-121">Equivalent .NET Framework class (type)</span></span>|<span data-ttu-id="9310c-122">XPath türü veya XSLT türü</span><span class="sxs-lookup"><span data-stu-id="9310c-122">XPath type or XSLT type</span></span>|  
|--------------|----------------------------------------------|-----------------------------|  
|<span data-ttu-id="9310c-123">Dize</span><span class="sxs-lookup"><span data-stu-id="9310c-123">String</span></span>|<span data-ttu-id="9310c-124">System. String</span><span class="sxs-lookup"><span data-stu-id="9310c-124">System.String</span></span>|<span data-ttu-id="9310c-125">XPath</span><span class="sxs-lookup"><span data-stu-id="9310c-125">XPath</span></span>|  
|<span data-ttu-id="9310c-126">Boole</span><span class="sxs-lookup"><span data-stu-id="9310c-126">Boolean</span></span>|<span data-ttu-id="9310c-127">System. Boolean</span><span class="sxs-lookup"><span data-stu-id="9310c-127">System.Boolean</span></span>|<span data-ttu-id="9310c-128">XPath</span><span class="sxs-lookup"><span data-stu-id="9310c-128">XPath</span></span>|  
|<span data-ttu-id="9310c-129">Sayı</span><span class="sxs-lookup"><span data-stu-id="9310c-129">Number</span></span>|<span data-ttu-id="9310c-130">System. Double</span><span class="sxs-lookup"><span data-stu-id="9310c-130">System.Double</span></span>|<span data-ttu-id="9310c-131">XPath</span><span class="sxs-lookup"><span data-stu-id="9310c-131">XPath</span></span>|  
|<span data-ttu-id="9310c-132">Sonuç ağacı parçası</span><span class="sxs-lookup"><span data-stu-id="9310c-132">Result Tree Fragment</span></span>|<span data-ttu-id="9310c-133">System. xml. XPath. XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="9310c-133">System.Xml.XPath.XPathNavigator</span></span>|<span data-ttu-id="9310c-134">XSLT</span><span class="sxs-lookup"><span data-stu-id="9310c-134">XSLT</span></span>|  
|<span data-ttu-id="9310c-135">Düğüm kümesi</span><span class="sxs-lookup"><span data-stu-id="9310c-135">Node Set</span></span>|<span data-ttu-id="9310c-136">System. xml. XPath. XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="9310c-136">System.Xml.XPath.XPathNodeIterator</span></span>|<span data-ttu-id="9310c-137">XPath</span><span class="sxs-lookup"><span data-stu-id="9310c-137">XPath</span></span>|  
  
 <span data-ttu-id="9310c-138">Parametre nesnesi yukarıdaki sınıflardan biri değilse, uygun şekilde bir Double veya String öğesine zorlanır.</span><span class="sxs-lookup"><span data-stu-id="9310c-138">If the parameter object is not one of the above classes, it is forced to either a Double or String, as appropriate.</span></span> <span data-ttu-id="9310c-139">Int16, UInt16, Int32, UInt32, Int64, UInt64, tek ve ondalık türler Double 'a zorlanır.</span><span class="sxs-lookup"><span data-stu-id="9310c-139">Int16, UInt16, Int32, UInt32, Int64, UInt64, Single and Decimal types are forced to a Double.</span></span> <span data-ttu-id="9310c-140">Diğer tüm türler yöntemi kullanılarak bir dizeye zorlanır `ToString` .</span><span class="sxs-lookup"><span data-stu-id="9310c-140">All other types are forced to a String using the `ToString` method.</span></span>  
  
#### <a name="to-use-the-xslt-parameter-the-user-needs-to-do-the-following"></a><span data-ttu-id="9310c-141">XSLT parametresini kullanmak için, kullanıcının şunları yapması gerekir:</span><span class="sxs-lookup"><span data-stu-id="9310c-141">To use the XSLT parameter, the user needs to do the following:</span></span>  
  
1. <span data-ttu-id="9310c-142"><xref:System.Xml.Xsl.XsltArgumentList>Kullanarak nesneleri oluşturun ve ekleyin <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> .</span><span class="sxs-lookup"><span data-stu-id="9310c-142">Create an <xref:System.Xml.Xsl.XsltArgumentList> and add the objects using <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.</span></span>  
  
2. <span data-ttu-id="9310c-143">Stil sayfasından parametreleri çağırın.</span><span class="sxs-lookup"><span data-stu-id="9310c-143">Call the parameters from the style sheet.</span></span>  
  
3. <span data-ttu-id="9310c-144"><xref:System.Xml.Xsl.XsltArgumentList> <xref:System.Xml.Xsl.XslTransform.Transform%2A> Yöntemini yöntemine geçirin.</span><span class="sxs-lookup"><span data-stu-id="9310c-144">Pass the <xref:System.Xml.Xsl.XsltArgumentList> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="9310c-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="9310c-145">Example</span></span>  
 <span data-ttu-id="9310c-146">Aşağıdaki örnek, bir <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> hesaplanan indirim tarihini tutacak bir parametre oluşturmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9310c-146">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold a calculated discount date.</span></span> <span data-ttu-id="9310c-147">İndirim tarihi, sipariş tarihinden itibaren 20 gün olacak şekilde hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="9310c-147">The discount date is calculated to be 20 days from the order date.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public class Sample  
  
   Private Const filename As String = "order.xml"  
   Private Const stylesheet As String = "discount.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XsltArgumentList.  
    Dim xslArg As XsltArgumentList = New XsltArgumentList  
  
    'Calculate the discount date.  
    Dim today As DateTime = DateTime.Now  
    Dim d As DateTime = today.AddDays(20)  
    xslArg.AddParam("discount", "", d.ToString())  
  
    'Create an XmlTextWriter to handle the output.  
    Dim writer As XmlTextWriter = New XmlTextWriter("orderout.xml", Nothing)  
  
    'Transform the file.  
    xslt.Transform(doc, xslArg, writer, Nothing)  
  
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
   private const String filename = "order.xml";  
   private const String stylesheet = "discount.xsl";  
  
   public static void Main() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XsltArgumentList.  
    XsltArgumentList xslArg = new XsltArgumentList();  
  
    //Calculate the discount date.  
    DateTime today = DateTime.Now;  
    DateTime d = today.AddDays(20);  
    xslArg.AddParam("discount", "", d.ToString());  
  
    //Create an XmlTextWriter to handle the output.  
    XmlTextWriter writer = new XmlTextWriter("orderout.xml", null);  
  
    //Transform the file.  
    xslt.Transform(doc, xslArg, writer, null);  
    writer.Close();  
  }  
}  
```  
  
### <a name="input"></a><span data-ttu-id="9310c-148">Giriş</span><span class="sxs-lookup"><span data-stu-id="9310c-148">Input</span></span>  
 <span data-ttu-id="9310c-149">Order. xml</span><span class="sxs-lookup"><span data-stu-id="9310c-149">order.xml</span></span>  
  
```xml  
<!--Represents a customer order-->  
<order>  
  <book ISBN='10-861003-324'>  
    <title>The Handmaid's Tale</title>  
    <price>19.95</price>  
  </book>  
  <cd ISBN='2-3631-4'>  
    <title>Americana</title>  
    <price>16.95</price>  
  </cd>  
</order>  
```  
  
 <span data-ttu-id="9310c-150">Discount. Xsl</span><span class="sxs-lookup"><span data-stu-id="9310c-150">discount.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">  
  <xsl:param name="discount"/>  
  <xsl:template match="/">  
    <order>  
      <xsl:variable name="sub-total" select="sum(//price)"/>  
      <total><xsl:value-of select="$sub-total"/></total>  
      15% discount if paid by: <xsl:value-of select="$discount"/>  
    </order>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### <a name="output"></a><span data-ttu-id="9310c-151">Çıktı</span><span class="sxs-lookup"><span data-stu-id="9310c-151">Output</span></span>  
  
```xml  
<order>  
   <total>36.9</total>
   15% discount if paid by: 5/6/2001 5:01:15 PM
</order>  
```  
  
## <a name="xslt-extension-objects"></a><span data-ttu-id="9310c-152">XSLT Genişletme Nesneleri</span><span class="sxs-lookup"><span data-stu-id="9310c-152">XSLT Extension Objects</span></span>  
 <span data-ttu-id="9310c-153">XSLT uzantı nesneleri, <xref:System.Xml.Xsl.XsltArgumentList> yöntemi kullanılarak öğesine eklenir <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> .</span><span class="sxs-lookup"><span data-stu-id="9310c-153">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="9310c-154">Tam ad ve ad alanı URI 'SI, o zaman uzantı nesnesiyle ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="9310c-154">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
 <span data-ttu-id="9310c-155">Bir nesne eklendiğinde, ' ın çağıranı <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> güvenlik ilkesinde tam güvenilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9310c-155">When an object is added, the caller of the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> must be fully trusted in the security policy.</span></span> <span data-ttu-id="9310c-156">Arayan yarı güvenilir ise, ekleme başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="9310c-156">If the caller is semi-trusted, the addition will fail.</span></span>  
  
 <span data-ttu-id="9310c-157">Bir nesne başarıyla eklenirse, yürütmenin başarılı olacağını garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="9310c-157">Though an object is added successfully, it does not guarantee that the execution will be successful.</span></span> <span data-ttu-id="9310c-158"><xref:System.Xml.Xsl.XslTransform.Transform%2A>Yöntemi çağrıldığında, izinler zamanında verilen kanıtla karşı hesaplanır <xref:System.Xml.Xsl.XslTransform.Load%2A> ve bu izin kümesi tüm dönüştürme işlemine atanır.</span><span class="sxs-lookup"><span data-stu-id="9310c-158">When the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is called, permissions are calculated against the evidence provided at <xref:System.Xml.Xsl.XslTransform.Load%2A> time, and that permission set is assigned to the entire transformation process.</span></span> <span data-ttu-id="9310c-159">Uzantı nesnesi, küme içinde bulunamayan izinleri gerektiren bir eylem başlatmaya çalışırsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9310c-159">If an extension object attempts to initiate an action that requires permissions not found in the set, an exception is thrown.</span></span>  
  
 <span data-ttu-id="9310c-160">Uzantı nesnelerinden döndürülen veri türleri, sayı, dize, Boolean ve düğüm kümesinin dört temel XPath veri türünden biridir.</span><span class="sxs-lookup"><span data-stu-id="9310c-160">The data types returned from extension objects are one of the four basic XPath data types of number, string, Boolean, and node set.</span></span>  
  
#### <a name="to-use-the-xslt-extension-object-the-user-needs-to-do-the-following"></a><span data-ttu-id="9310c-161">XSLT Uzantı nesnesini kullanmak için, kullanıcının şunları yapması gerekir:</span><span class="sxs-lookup"><span data-stu-id="9310c-161">To use the XSLT extension object, the user needs to do the following:</span></span>  
  
1. <span data-ttu-id="9310c-162"><xref:System.Xml.Xsl.XsltArgumentList>Kullanarak Uzantı nesnesini oluşturun ve ekleyin <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> .</span><span class="sxs-lookup"><span data-stu-id="9310c-162">Create an <xref:System.Xml.Xsl.XsltArgumentList> and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span></span>  
  
2. <span data-ttu-id="9310c-163">Uzantı nesnesini stil sayfasından çağırın.</span><span class="sxs-lookup"><span data-stu-id="9310c-163">Invoke the extension object from the style sheet.</span></span>  
  
3. <span data-ttu-id="9310c-164"><xref:System.Xml.Xsl.XsltArgumentList> <xref:System.Xml.Xsl.XslTransform.Transform%2A> Yöntemini yöntemine geçirin.</span><span class="sxs-lookup"><span data-stu-id="9310c-164">Pass the <xref:System.Xml.Xsl.XsltArgumentList> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="9310c-165">Örnek</span><span class="sxs-lookup"><span data-stu-id="9310c-165">Example</span></span>  
 <span data-ttu-id="9310c-166">Aşağıdaki örnek, yarıçapı verilen bir dairenin çevresini hesaplar.</span><span class="sxs-lookup"><span data-stu-id="9310c-166">The following example calculates the circumference of a circle given its radius.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "circle.xsl"  
  
   Public Shared Sub Main()  
        Dim test As Sample = New Sample  
   End Sub  
  
  Public Sub New()  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XsltArgumentList.  
    Dim xslArg As XsltArgumentList = New XsltArgumentList  
  
    'Add an object to calculate the circumference of the circle.  
    Dim obj As Calculate = New Calculate  
    xslArg.AddExtensionObject("urn:myObj", obj)  
  
    'Create an XmlTextWriter to output to the console.  
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
  
    'Transform the file.  
    xslt.Transform(doc, xslArg, writer, Nothing)  
    writer.Close()  
  
  End Sub  
  
  'Calculates the circumference of a circle given the radius.  
  Public Class Calculate  
  
    Private circ As double = 0  
  
    Public Function Circumference(radius As Double) As Double  
       circ = Math.PI*2*radius  
       Return circ  
    End Function  
  End Class  
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
   private const String stylesheet = "circle.xsl";  
  
   public static void Main() {  
  
        Sample test = new Sample();  
    }  
  
  public Sample() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XsltArgumentList.  
    XsltArgumentList xslArg = new XsltArgumentList();  
  
    //Add an object to calculate the circumference of the circle.  
    Calculate obj = new Calculate();  
    xslArg.AddExtensionObject("urn:myObj", obj);  
  
    //Create an XmlTextWriter to output to the console.  
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
  
    //Transform the file.  
    xslt.Transform(doc, xslArg, writer, null);  
    writer.Close();  
  
  }  
  
  //Calculates the circumference of a circle given the radius.  
  public class Calculate {  
  
    private double circ = 0;  
  
    public double Circumference(double radius){  
       circ = Math.PI*2*radius;  
       return circ;  
    }  
  }  
}  
```  
  
### <a name="input"></a><span data-ttu-id="9310c-167">Giriş</span><span class="sxs-lookup"><span data-stu-id="9310c-167">Input</span></span>  
 <span data-ttu-id="9310c-168">Number. xml</span><span class="sxs-lookup"><span data-stu-id="9310c-168">number.xml</span></span>  
  
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
  
 <span data-ttu-id="9310c-169">Circle. Xsl</span><span class="sxs-lookup"><span data-stu-id="9310c-169">circle.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:myObj="urn:myObj">  
  
  <xsl:template match="data">  
  <circles>  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="myObj:Circumference(radius)"/>
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### <a name="output"></a><span data-ttu-id="9310c-170">Çıktı</span><span class="sxs-lookup"><span data-stu-id="9310c-170">Output</span></span>  
 `<circles xmlns:myObj="urn:myObj">`  
  
 `<circle>`  
  
 `<radius>12</radius>`  
  
 `<circumference>75.398223686155</circumference>`  
  
 `</circle>`  
  
 `<circle>`  
  
 `<radius>37.5</radius>`  
  
 `<circumference>235.61944901923448</circumference>`  
  
 `</circle>`  
  
 `</circles>`  
  
## <a name="see-also"></a><span data-ttu-id="9310c-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9310c-171">See also</span></span>

- [<span data-ttu-id="9310c-172">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="9310c-172">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
