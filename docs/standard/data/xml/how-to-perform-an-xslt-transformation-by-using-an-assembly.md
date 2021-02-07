---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: derleme kullanarak XSLT dönüşümü gerçekleştirme'
title: 'Nasıl yapılır: Derleme Kullanarak XSLT Dönüşümü Gerçekleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76ee440b-d134-4f8f-8262-b917ad6dcbf6
ms.openlocfilehash: d080d8690c8a3a94867d7e2cca0a73bd9410c962
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713812"
---
# <a name="how-to-perform-an-xslt-transformation-by-using-an-assembly"></a><span data-ttu-id="df52a-103">Nasıl yapılır: Derleme Kullanarak XSLT Dönüşümü Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="df52a-103">How to: Perform an XSLT Transformation by Using an Assembly</span></span>

<span data-ttu-id="df52a-104">XSLT derleyicisi (xsltc.exe) XSLT stil sayfalarını derler ve bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="df52a-104">The XSLT compiler (xsltc.exe) compiles XSLT style sheets and generates an assembly.</span></span> <span data-ttu-id="df52a-105">Derleme doğrudan <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> yöntemine geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="df52a-105">The assembly can be passed directly into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span>  
  
### <a name="to-copy-the-xml-and-xslt-files-to-your-local-computer"></a><span data-ttu-id="df52a-106">XML ve XSLT dosyalarını yerel bilgisayarınıza kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="df52a-106">To copy the XML and XSLT files to your local computer</span></span>  
  
- <span data-ttu-id="df52a-107">XSLT dosyasını yerel bilgisayarınıza kopyalayın ve Transform. xsl olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="df52a-107">Copy the XSLT file to your local computer and name it Transform.xsl.</span></span>  
  
    ```xml  
    <xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
      xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
      xmlns:user="urn:my-scripts">  
      <msxsl:script language="C#" implements-prefix="user">  
        <![CDATA[  
      public string discount(string price){  
        char[] trimChars = { '$' };  
        //trim leading $, convert price to type double  
        double discount_value = Convert.ToDouble(price.TrimStart(trimChars));  
        //apply 10% discount and round appropriately  
        discount_value = .9*discount_value;  
        //convert value to decimal and format as currency  
        string discount_price = discount_value.ToString("C");  
        return discount_price;  
      }  
      ]]>  
      </msxsl:script>  
      <xsl:template match="catalog">  
        <html>  
          <head></head>  
          <body>  
            <table border="1">  
              <tr>  
                <th align="left">Title</th>  
                <th align="left">Author</th>  
                <th align="left">Genre</th>  
                <th align="left">Publish Date</th>  
                <th align="left">Price</th>  
              </tr>  
              <xsl:for-each select="book">  
                <tr>  
                  <td>  
                    <xsl:value-of select="title"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="author"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="genre"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="publish_date"/>  
                  </td>  
                  <xsl:choose>  
                    <xsl:when test="genre = 'Fantasy'">  
                      <td>  
                        <xsl:value-of select="user:discount(price)"/>  
                      </td>  
                    </xsl:when>  
                    <xsl:otherwise>  
                      <td>  
                        <xsl:value-of select="price"/>  
                      </td>  
                    </xsl:otherwise>  
                  </xsl:choose>  
                </tr>  
              </xsl:for-each>  
            </table>  
          </body>  
        </html>  
      </xsl:template>  
    </xsl:stylesheet>  
    ```  
  
- <span data-ttu-id="df52a-108">XML dosyasını yerel bilgisayarınıza kopyalayın ve adlandırın `books.xml` .</span><span class="sxs-lookup"><span data-stu-id="df52a-108">Copy the XML file to your local computer and name it `books.xml`.</span></span>  
  
    ```xml  
    <?xml version="1.0"?>  
    <catalog>  
       <book id="bk101">  
          <author>Gambardella, Matthew</author>  
          <title>XML Developer's Guide</title>  
          <genre>Computer</genre>  
          <price>$44.95</price>  
          <publish_date>2000-10-01</publish_date>  
       </book>  
       <book id="bk102">  
          <author>Ralls, Kim</author>  
          <title>Midnight Rain</title>  
          <genre>Fantasy</genre>  
          <price>$5.95</price>  
          <publish_date>2000-12-16</publish_date>  
       </book>  
       <book id="bk103">  
          <author>Corets, Eva</author>  
          <title>Maeve Ascendant</title>  
          <genre>Fantasy</genre>  
          <price>$5.95</price>  
          <publish_date>2000-11-17</publish_date>  
       </book>  
       <book id="bk106">  
          <author>Randall, Cynthia</author>  
          <title>Lover Birds</title>  
          <genre>Romance</genre>  
          <price>$4.95</price>  
          <publish_date>2000-09-02</publish_date>  
       </book>  
       <book id="bk107">  
          <author>Thurman, Paula</author>  
          <title>Splish Splash</title>  
          <genre>Romance</genre>  
          <price>$4.95</price>  
          <publish_date>2000-11-02</publish_date>  
       </book>  
    </catalog>  
    ```  
  
### <a name="to-compile-the-style-sheet-with-the-script-enabled"></a><span data-ttu-id="df52a-109">Komut dosyası etkinken stil sayfasını derlemek için.</span><span class="sxs-lookup"><span data-stu-id="df52a-109">To compile the style sheet with the script enabled.</span></span>  
  
1. <span data-ttu-id="df52a-110">Komut satırından aşağıdaki komutu yürütmek, ve adlı iki derleme oluşturur `Transform.dll` `Transform_Script1.dll` (Bu, varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="df52a-110">Executing the following command from the command line creates two assemblies named `Transform.dll` and `Transform_Script1.dll` (This is the default behavior.</span></span> <span data-ttu-id="df52a-111">Aksi belirtilmedikçe, sınıfın adı ve derleme varsayılan olarak ana stil sayfasının adını alır):</span><span class="sxs-lookup"><span data-stu-id="df52a-111">Unless otherwise specified, the name of the class and the assembly defaults to the name of the main style sheet):</span></span>  
  
    ```console  
    xsltc /settings:script+ Transform.xsl  
    ```
  
    <span data-ttu-id="df52a-112">Aşağıdaki komut, sınıf adını dönüştürmek için açıkça ayarlar:</span><span class="sxs-lookup"><span data-stu-id="df52a-112">The following command explicitly sets the class name to Transform:</span></span>  
  
    ```console  
    xsltc /settings:script+ /class:Transform Transform.xsl  
    ```  
  
### <a name="to-include-the-compiled-assembly-as-a-reference-when-you-compile-your-code"></a><span data-ttu-id="df52a-113">Kodunuzu derlerken derlenmiş derlemeyi başvuru olarak eklemek için.</span><span class="sxs-lookup"><span data-stu-id="df52a-113">To include the compiled assembly as a reference when you compile your code.</span></span>  
  
1. <span data-ttu-id="df52a-114">Çözüm Gezgini veya komut satırından bir başvuru ekleyerek Visual Studio 'da bir derlemeyi dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="df52a-114">You can include an assembly in Visual Studio by adding a reference in the Solution Explorer, or from the command line.</span></span>  
  
2. <span data-ttu-id="df52a-115">C# ile komut satırı için aşağıdakileri kullanın:</span><span class="sxs-lookup"><span data-stu-id="df52a-115">For the command line with C#, use the following:</span></span>  
  
    ```console  
    csc myCode.cs /r:system.dll;system.xml.dll;Transform.dll  
    ```  
  
3. <span data-ttu-id="df52a-116">Visual Basic olan komut satırı için aşağıdakini kullanın</span><span class="sxs-lookup"><span data-stu-id="df52a-116">For the command line with Visual Basic, use the following</span></span>  
  
    ```console  
    vbc myCode.vb /r:system.dll;system.xml.dll;Transform.dll  
    ```  
  
### <a name="to-use-the-compiled-assembly-in-your-code"></a><span data-ttu-id="df52a-117">Kodunuzda derlenen derlemeyi kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="df52a-117">To use the compiled assembly in your code.</span></span>  
  
<span data-ttu-id="df52a-118">Aşağıdaki örnek, derlenmiş stil sayfasını kullanarak XSLT dönüşümünün nasıl yürütüleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="df52a-118">The following example shows how to execute the XSLT transformation by using the compiled style sheet.</span></span>  
  
[!code-csharp[XslTransform_XSLTC#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslTransform_XSLTC/CS/XslTransform_XSLTC.cs#1)]
[!code-vb[XslTransform_XSLTC#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslTransform_XSLTC/VB/XslTransform_XSLTC.vb#1)]  
  
<span data-ttu-id="df52a-119">Derlenmiş derlemeye dinamik olarak bağlanmak için, Değiştir</span><span class="sxs-lookup"><span data-stu-id="df52a-119">To dynamically link to the compiled assembly, replace</span></span>
  
```csharp  
xslt.Load(typeof(Transform));  
```  
  
<span data-ttu-id="df52a-120">örneklerini şununla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="df52a-120">with</span></span>  
  
```csharp
xslt.Load(System.Reflection.Assembly.Load("Transform").GetType("Transform"));  
```
  
<span data-ttu-id="df52a-121">Yukarıdaki örnekte.</span><span class="sxs-lookup"><span data-stu-id="df52a-121">in the example above.</span></span> <span data-ttu-id="df52a-122">Assembly. Load yöntemi hakkında daha fazla bilgi için bkz <xref:System.Reflection.Assembly.Load%2A> ..</span><span class="sxs-lookup"><span data-stu-id="df52a-122">For more information on the Assembly.Load method, see <xref:System.Reflection.Assembly.Load%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df52a-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df52a-123">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="df52a-124">XSLT Derleyicisi (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="df52a-124">XSLT Compiler (xsltc.exe)</span></span>](xslt-compiler-xsltc-exe.md)
- [<span data-ttu-id="df52a-125">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="df52a-125">XSLT Transformations</span></span>](xslt-transformations.md)
- [<span data-ttu-id="df52a-126">csc.exe Kullanarak Komut Satırı Derleme</span><span class="sxs-lookup"><span data-stu-id="df52a-126">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
