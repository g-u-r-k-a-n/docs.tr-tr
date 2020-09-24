---
title: System.Object Yöntemleri
ms.date: 03/30/2017
ms.assetid: 5397fca0-689e-443e-802f-e1cbdc866427
ms.openlocfilehash: d2b96ca9e7bedd0e0438b47698d4b963844c92f3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155646"
---
# <a name="systemobject-methods"></a><span data-ttu-id="14140-102">System.Object Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="14140-102">System.Object Methods</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="14140-103">Aşağıdaki yöntemleri destekler <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="14140-103">supports the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="14140-104">Aşağıdaki <xref:System.Object> yöntemleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="14140-104">does not support the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<span data-ttu-id="14140-105"><xref:System.Object.ToString?displayProperty=nameWithType> ,, ve gibi ikili türler için `BINARY` `VARBINARY` `IMAGE` `TIMESTAMP` .</span><span class="sxs-lookup"><span data-stu-id="14140-105"><xref:System.Object.ToString?displayProperty=nameWithType> for binary types such as `BINARY`, `VARBINARY`, `IMAGE`, and `TIMESTAMP`.</span></span>||  
  
## <a name="differences-from-net"></a><span data-ttu-id="14140-106">.NET farklılıkları</span><span class="sxs-lookup"><span data-stu-id="14140-106">Differences from .NET</span></span>  

 <span data-ttu-id="14140-107"><xref:System.Object.ToString?displayProperty=nameWithType>Double için ÇıKıŞı `CONVERT` SQL 'de SQL (nvarchar (30), @x , 2) kullanır.</span><span class="sxs-lookup"><span data-stu-id="14140-107">The output of <xref:System.Object.ToString?displayProperty=nameWithType> for double uses SQL `CONVERT`(NVARCHAR(30), @x, 2) on SQL.</span></span> <span data-ttu-id="14140-108">SQL her zaman bu durumda 16 basamak ve bilimsel gösterim kullanır (örneğin, "0.000000000000000 e + 000" 0).</span><span class="sxs-lookup"><span data-stu-id="14140-108">SQL always uses 16 digits and scientific notation in this case (for example, "0.000000000000000e+000" for 0).</span></span> <span data-ttu-id="14140-109">Sonuç olarak, <xref:System.Object.ToString?displayProperty=nameWithType> dönüştürme .NET Framework aynı dizeyi oluşturmaz <xref:System.Convert.ToString%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="14140-109">As a result, <xref:System.Object.ToString?displayProperty=nameWithType> conversion does not produce the same string as <xref:System.Convert.ToString%2A?displayProperty=nameWithType> in the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14140-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14140-110">See also</span></span>

- [<span data-ttu-id="14140-111">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="14140-111">Data Types and Functions</span></span>](data-types-and-functions.md)
