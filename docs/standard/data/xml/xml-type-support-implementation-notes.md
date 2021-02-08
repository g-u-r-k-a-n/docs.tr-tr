---
description: 'Hakkında daha fazla bilgi edinin: XML türü desteği uygulama notları'
title: XML Tür Desteği Uygulama Notları
ms.date: 03/30/2017
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
ms.openlocfilehash: 52a014f0056b1f78b297ec9289e9748ec7dd392e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782682"
---
# <a name="xml-type-support-implementation-notes"></a><span data-ttu-id="e8e52-103">XML Tür Desteği Uygulama Notları</span><span class="sxs-lookup"><span data-stu-id="e8e52-103">XML Type Support Implementation Notes</span></span>

<span data-ttu-id="e8e52-104">Bu konuda, farkında olmak istediğiniz bazı uygulama ayrıntıları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e8e52-104">This topic describes some implementation details that you want to be aware of.</span></span>  
  
## <a name="list-mappings"></a><span data-ttu-id="e8e52-105">Eşlemeleri Listele</span><span class="sxs-lookup"><span data-stu-id="e8e52-105">List Mappings</span></span>  

 <span data-ttu-id="e8e52-106"><xref:System.Collections.IList>,, <xref:System.Collections.ICollection> , <xref:System.Collections.IEnumerable> **Türü []** ve <xref:System.String> türleri XML şeması tanım dili (xsd) liste türlerini temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e8e52-106">The <xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **Type[]**, and <xref:System.String> types are used to represent XML Schema definition language (XSD) list types.</span></span>  
  
## <a name="union-mappings"></a><span data-ttu-id="e8e52-107">Birleşim eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="e8e52-107">Union Mappings</span></span>  

 <span data-ttu-id="e8e52-108">Birleşim türleri veya türü kullanılarak temsil <xref:System.Xml.Schema.XmlAtomicValue> edilir <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="e8e52-108">Union types are represented using the <xref:System.Xml.Schema.XmlAtomicValue> or <xref:System.String> type.</span></span> <span data-ttu-id="e8e52-109">Bu nedenle, kaynak türü veya hedef türü her zaman ya da <xref:System.String> olmalıdır <xref:System.Xml.Schema.XmlAtomicValue> .</span><span class="sxs-lookup"><span data-stu-id="e8e52-109">The source type or the destination type must therefore always be either <xref:System.String> or <xref:System.Xml.Schema.XmlAtomicValue>.</span></span>  
  
 <span data-ttu-id="e8e52-110"><xref:System.Xml.Schema.XmlSchemaDatatype>Nesne bir liste türünü temsil ediyorsa, nesne giriş dize değerini bir veya daha fazla nesne listesine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="e8e52-110">If the <xref:System.Xml.Schema.XmlSchemaDatatype> object represents a list type the object converts the input string value to a list of one or more objects.</span></span> <span data-ttu-id="e8e52-111">Eğer <xref:System.Xml.Schema.XmlSchemaDatatype> bir birleşim türünü temsil ediyorsa, giriş değerini birleşimin üye türü olarak ayrıştırmaya yönelik bir girişim yapılır.</span><span class="sxs-lookup"><span data-stu-id="e8e52-111">If the <xref:System.Xml.Schema.XmlSchemaDatatype> represents a union type then an attempt is made to parse the input value as a member type of the union.</span></span> <span data-ttu-id="e8e52-112">Ayrıştırma denemesi başarısız olursa, dönüştürme işleminin bir sonraki üyesi ile denenir ve dönüştürme başarılı olana kadar ya da denenecek başka hiçbir üye türü yoksa, bu durumda bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e8e52-112">If the parse attempt fails then the conversion is attempted with the next member of the union and so on until the conversion is successful, or there are no other member types to try, in which case an exception is thrown.</span></span>  
  
## <a name="differences-between-clr-and-xml-data-types"></a><span data-ttu-id="e8e52-113">CLR ve XML veri türleri arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="e8e52-113">Differences Between CLR and XML Data Types</span></span>  

 <span data-ttu-id="e8e52-114">Aşağıda, CLR türleri ve XML veri türleri arasında oluşabilecek bazı uyuşmazlıklar ve bunların nasıl işlendiği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e8e52-114">The following describes certain mismatches that can occur between CLR types and XML data types and how they are handled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8e52-115">`xs`Ön ek <https://www.w3.org/2001/XMLSchema> ve ad alanı URI 'sine eşlenir.</span><span class="sxs-lookup"><span data-stu-id="e8e52-115">The `xs` prefix is mapped to the <https://www.w3.org/2001/XMLSchema> and namespace URI.</span></span>
  
### <a name="systemtimespan-and-xsduration"></a><span data-ttu-id="e8e52-116">System. TimeSpan ve xs: Duration</span><span class="sxs-lookup"><span data-stu-id="e8e52-116">System.TimeSpan and xs:duration</span></span>  

 <span data-ttu-id="e8e52-117">`xs:duration`Tür, farklı ancak eşdeğer olan belirli Duration değerleri olacak şekilde kısmen sıralanır.</span><span class="sxs-lookup"><span data-stu-id="e8e52-117">The `xs:duration` type is partially ordered in that there are certain duration values that are different but equivalent.</span></span> <span data-ttu-id="e8e52-118">Bu, `xs:duration` 1 ay (P1M) gibi tür değeri için 32 günden (p32d), 27 günden (P27D) daha büyük ve 28, 29 veya 30 güne eşit olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e8e52-118">This means that for the `xs:duration` type value such as 1 month (P1M) is less than 32 days (P32D), larger than 27 days (P27D) and equivalent to 28, 29 or 30 days.</span></span>  
  
 <span data-ttu-id="e8e52-119"><xref:System.TimeSpan>Sınıfı bu kısmi sıralamayı desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="e8e52-119">The <xref:System.TimeSpan> class does not support this partial ordering.</span></span> <span data-ttu-id="e8e52-120">Bunun yerine, 1 yıl ve 1 ay için belirli sayıda gün seçer; 365 gün ve 30 gün sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="e8e52-120">Instead, it picks a specific number of days for 1 year and 1 month; 365 days and 30 days respectively.</span></span>  
  
 <span data-ttu-id="e8e52-121">Tür hakkında daha fazla bilgi için `xs:duration` bkz. W3C [XML şeması Bölüm 2: veri türleri önerisi](https://www.w3.org/TR/xmlschema-2/).</span><span class="sxs-lookup"><span data-stu-id="e8e52-121">For more information on the `xs:duration` type, see the W3C [XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/).</span></span>
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a><span data-ttu-id="e8e52-122">xs: Time, Gregoryen tarih türleri ve System. DateTime</span><span class="sxs-lookup"><span data-stu-id="e8e52-122">xs:time, Gregorian Date Types, and System.DateTime</span></span>  

 <span data-ttu-id="e8e52-123">Bir `xs:time` değer bir <xref:System.DateTime> nesneyle eşlendiğinde, <xref:System.DateTime.MinValue> nesnenin tarih özelliklerini <xref:System.DateTime> (örneğin <xref:System.DateTime.Year%2A> , <xref:System.DateTime.Month%2A> ve <xref:System.DateTime.Day%2A> ) en küçük olası <xref:System.DateTime> değere başlatmak için alanı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e8e52-123">When an `xs:time` value is mapped to a <xref:System.DateTime> object, the <xref:System.DateTime.MinValue> field is used to initialize the date properties of the <xref:System.DateTime> object (such as <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, and <xref:System.DateTime.Day%2A>) to the smallest possible <xref:System.DateTime> value.</span></span>  
  
 <span data-ttu-id="e8e52-124">Benzer şekilde,, `xs:gMonth` , `xs:gDay` `xs:gYear` ve örnekleri `xs:gYearMonth` `xs:gMonthDay` de bir <xref:System.DateTime> nesneye eşlenir.</span><span class="sxs-lookup"><span data-stu-id="e8e52-124">Similarly, instances of `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` and `xs:gMonthDay` are also mapped to a <xref:System.DateTime> object.</span></span> <span data-ttu-id="e8e52-125">Nesnedeki kullanılmayan özellikler, <xref:System.DateTime> öğesinden bu bilgisayarlara başlatılır <xref:System.DateTime.MinValue> .</span><span class="sxs-lookup"><span data-stu-id="e8e52-125">Unused properties on the <xref:System.DateTime> object are initialized to those from <xref:System.DateTime.MinValue>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8e52-126"><xref:System.DateTime.Year%2A?displayProperty=nameWithType>İçerik olarak yazıldığında değere güvenebilirsiniz `xs:gMonthDay` .</span><span class="sxs-lookup"><span data-stu-id="e8e52-126">You cannot rely on the <xref:System.DateTime.Year%2A?displayProperty=nameWithType> value when the content is typed as `xs:gMonthDay`.</span></span> <span data-ttu-id="e8e52-127"><xref:System.DateTime.Year%2A?displayProperty=nameWithType>Bu durumda değer her zaman 1904 olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e8e52-127">The <xref:System.DateTime.Year%2A?displayProperty=nameWithType> value is always set to 1904 in this case.</span></span>  
  
### <a name="xsanyuri-and-systemuri"></a><span data-ttu-id="e8e52-128">xs: anyURI ve System. Uri</span><span class="sxs-lookup"><span data-stu-id="e8e52-128">xs:anyURI and System.Uri</span></span>  

 <span data-ttu-id="e8e52-129">`xs:anyURI`Göreli BIR URI 'yi temsil eden öğesinin bir örneği bir ile eşlendiğinde <xref:System.Uri> , <xref:System.Uri> nesnenin temel URI 'si yoktur.</span><span class="sxs-lookup"><span data-stu-id="e8e52-129">When an instance of `xs:anyURI` that represents a relative URI is mapped to a <xref:System.Uri>, the <xref:System.Uri> object does not have a base URI.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8e52-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8e52-130">See also</span></span>

- [<span data-ttu-id="e8e52-131">System.Xml Sınıflarında Tür Desteği</span><span class="sxs-lookup"><span data-stu-id="e8e52-131">Type Support in the System.Xml Classes</span></span>](type-support-in-the-system-xml-classes.md)
