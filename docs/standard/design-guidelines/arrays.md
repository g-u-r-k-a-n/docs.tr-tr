---
title: Diziler
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: c3545c609b6544e6528bbae08889d0ef20473802
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821612"
---
# <a name="arrays"></a><span data-ttu-id="5143e-102">Diziler</span><span class="sxs-lookup"><span data-stu-id="5143e-102">Arrays</span></span>
<span data-ttu-id="5143e-103">✔️ ortak API 'lerde diziler üzerinde koleksiyonları kullanmayı tercih eder.</span><span class="sxs-lookup"><span data-stu-id="5143e-103">✔️ DO prefer using collections over arrays in public APIs.</span></span> <span data-ttu-id="5143e-104">[Koleksiyonlar](guidelines-for-collections.md) bölümü koleksiyonlar ve diziler arasında nasıl seçim yapılacağı hakkında ayrıntılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="5143e-104">The [Collections](guidelines-for-collections.md) section provides details about how to choose between collections and arrays.</span></span>

 <span data-ttu-id="5143e-105">❌ Salt okunurdur dizi alanlarını kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="5143e-105">❌ DO NOT use read-only array fields.</span></span> <span data-ttu-id="5143e-106">Alanın kendisi salt okunurdur ve değiştirilemez, ancak dizideki öğeler değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5143e-106">The field itself is read-only and can't be changed, but elements in the array can be changed.</span></span>

 <span data-ttu-id="5143e-107">✔️ çok boyutlu diziler yerine pürüzlü Diziler kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="5143e-107">✔️ CONSIDER using jagged arrays instead of multidimensional arrays.</span></span>

 <span data-ttu-id="5143e-108">Sivri dizi öğeleri de diziler olan bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="5143e-108">A jagged array is an array with elements that are also arrays.</span></span> <span data-ttu-id="5143e-109">Öğeleri oluşturan diziler farklı boyutlarda olabilir ve çok boyutlu dizilere kıyasla bazı veri kümeleri (örn. seyrek matris) için daha az harcanan alana sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5143e-109">The arrays that make up the elements can be of different sizes, leading to less wasted space for some sets of data (e.g., sparse matrix) compared to multidimensional arrays.</span></span> <span data-ttu-id="5143e-110">Ayrıca, CLR, basit diziler üzerinde dizin işlemlerini iyileştirir, bu nedenle bazı senaryolarda çalışma zamanı daha iyi bir performans sergilebilirler.</span><span class="sxs-lookup"><span data-stu-id="5143e-110">Furthermore, the CLR optimizes index operations on jagged arrays, so they might exhibit better runtime performance in some scenarios.</span></span>

 <span data-ttu-id="5143e-111">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="5143e-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="5143e-112">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="5143e-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="5143e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5143e-113">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="5143e-114">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="5143e-114">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="5143e-115">Kullanım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="5143e-115">Usage Guidelines</span></span>](usage-guidelines.md)
