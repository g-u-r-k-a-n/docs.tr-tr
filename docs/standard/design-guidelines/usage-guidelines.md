---
description: 'Daha fazla bilgi edinin: Kullanım yönergeleri'
title: Kullanım yönergeleri
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
ms.openlocfilehash: a435fab2adb00f671dfde1619a3c1f8db719d9df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641804"
---
# <a name="usage-guidelines"></a><span data-ttu-id="ea4cc-103">Kullanım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ea4cc-103">Usage guidelines</span></span>

<span data-ttu-id="ea4cc-104">Bu bölüm, genel olarak erişilebilen API 'lerde ortak türleri kullanmayla ilgili yönergeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ea4cc-104">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="ea4cc-105">Yerleşik çerçeve türlerinin doğrudan kullanımı (örn. serileştirme öznitelikleri) ve ortak işleçleri aşırı yükleme ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="ea4cc-105">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>
  
<span data-ttu-id="ea4cc-106"><xref:System.IDisposable?displayProperty=nameWithType>Arabirim bu bölümde ele alınmıyor, ancak [Dispose deseninin](../garbage-collection/implementing-dispose.md) bölümünde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="ea4cc-106">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../garbage-collection/implementing-dispose.md) section.</span></span>

> [!NOTE]
> <span data-ttu-id="ea4cc-107">Diğer yaygın, yerleşik .NET Framework türleri hakkında yönergeler ve ek bilgiler için, şunlar için başvuru konularına bakın:,,,, <xref:System.DateTime?displayProperty=nameWithType> , <xref:System.DateTimeOffset?displayProperty=nameWithType> <xref:System.ICloneable?displayProperty=nameWithType> <xref:System.IComparable%601?displayProperty=nameWithType> <xref:System.IEquatable%601?displayProperty=nameWithType> <xref:System.Nullable%601?displayProperty=nameWithType> , <xref:System.Object?displayProperty=nameWithType> , <xref:System.Uri?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ea4cc-107">For guidelines and additional information about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="ea4cc-108">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="ea4cc-108">In this section</span></span>

[<span data-ttu-id="ea4cc-109">Diziler</span><span class="sxs-lookup"><span data-stu-id="ea4cc-109">Arrays</span></span>](arrays.md)  
[<span data-ttu-id="ea4cc-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ea4cc-110">Attributes</span></span>](attributes.md)  
[<span data-ttu-id="ea4cc-111">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="ea4cc-111">Collections</span></span>](guidelines-for-collections.md)  
[<span data-ttu-id="ea4cc-112">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="ea4cc-112">Serialization</span></span>](serialization.md)  
[<span data-ttu-id="ea4cc-113">System.Xml kullanımı</span><span class="sxs-lookup"><span data-stu-id="ea4cc-113">System.Xml Usage</span></span>](system-xml-usage.md)  
[<span data-ttu-id="ea4cc-114">Eşitlik Işleçleri</span><span class="sxs-lookup"><span data-stu-id="ea4cc-114">Equality Operators</span></span>](equality-operators.md)  

<span data-ttu-id="ea4cc-115">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="ea4cc-115">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="ea4cc-116">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="ea4cc-116">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ea4cc-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea4cc-117">See also</span></span>

- [<span data-ttu-id="ea4cc-118">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ea4cc-118">Framework Design Guidelines</span></span>](index.md)
