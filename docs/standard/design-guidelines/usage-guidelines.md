---
title: Kullanım yönergeleri
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
ms.openlocfilehash: d6ea7c7b9ada95e3d0c425aaea18be6cdbb4ce35
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828510"
---
# <a name="usage-guidelines"></a><span data-ttu-id="d685c-102">Kullanım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="d685c-102">Usage guidelines</span></span>

<span data-ttu-id="d685c-103">Bu bölüm, genel olarak erişilebilen API 'lerde ortak türleri kullanmayla ilgili yönergeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d685c-103">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="d685c-104">Yerleşik çerçeve türlerinin doğrudan kullanımı (örn. serileştirme öznitelikleri) ve ortak işleçleri aşırı yükleme ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="d685c-104">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>
  
<span data-ttu-id="d685c-105"><xref:System.IDisposable?displayProperty=nameWithType>Arabirim bu bölümde ele alınmıyor, ancak [Dispose deseninin](../garbage-collection/implementing-dispose.md) bölümünde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="d685c-105">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../garbage-collection/implementing-dispose.md) section.</span></span>

> [!NOTE]
> <span data-ttu-id="d685c-106">Diğer yaygın, yerleşik .NET Framework türleri hakkında yönergeler ve ek bilgiler için, şunlar için başvuru konularına bakın:,,,, <xref:System.DateTime?displayProperty=nameWithType> , <xref:System.DateTimeOffset?displayProperty=nameWithType> <xref:System.ICloneable?displayProperty=nameWithType> <xref:System.IComparable%601?displayProperty=nameWithType> <xref:System.IEquatable%601?displayProperty=nameWithType> <xref:System.Nullable%601?displayProperty=nameWithType> , <xref:System.Object?displayProperty=nameWithType> , <xref:System.Uri?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d685c-106">For guidelines and additional information about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d685c-107">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="d685c-107">In this section</span></span>

[<span data-ttu-id="d685c-108">Diziler</span><span class="sxs-lookup"><span data-stu-id="d685c-108">Arrays</span></span>](arrays.md)  
[<span data-ttu-id="d685c-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d685c-109">Attributes</span></span>](attributes.md)  
[<span data-ttu-id="d685c-110">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="d685c-110">Collections</span></span>](guidelines-for-collections.md)  
[<span data-ttu-id="d685c-111">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="d685c-111">Serialization</span></span>](serialization.md)  
[<span data-ttu-id="d685c-112">System.Xml kullanımı</span><span class="sxs-lookup"><span data-stu-id="d685c-112">System.Xml Usage</span></span>](system-xml-usage.md)  
[<span data-ttu-id="d685c-113">Eşitlik Işleçleri</span><span class="sxs-lookup"><span data-stu-id="d685c-113">Equality Operators</span></span>](equality-operators.md)  

<span data-ttu-id="d685c-114">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="d685c-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="d685c-115">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="d685c-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d685c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d685c-116">See also</span></span>

- [<span data-ttu-id="d685c-117">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="d685c-117">Framework Design Guidelines</span></span>](index.md)
