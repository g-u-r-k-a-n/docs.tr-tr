---
title: Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler
description: Blittable ve blittable olmayan türler hakkında bilgi edinin. Blittable veri türleri genellikle yönetilen ve yönetilmeyen bellekte temsil edilir ve özel işleme gerektirmez.
ms.date: 03/30/2017
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
ms.openlocfilehash: c9168bd245e10232a798b3e6f3b9448b24996a77
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100436129"
---
# <a name="blittable-and-non-blittable-types"></a>Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler

Çoğu veri türü hem yönetilen hem de yönetilmeyen bellekte ortak bir gösterimine sahiptir ve birlikte çalışma sıralayıcısı tarafından özel işleme gerektirmez. Bu türler, yönetilen ve yönetilmeyen kod arasında geçirildiklerinde dönüştürme gerektirmediğinden *blittable türler* olarak adlandırılır.  
  
 Platform çağırma çağrılarının döndürdüğü yapıların blittable tür olması gerekir. Platform çağırma, dönüş türleri olarak blittable olmayan yapıları desteklemez.  
  
 Ad alanından aşağıdaki türler <xref:System> blittable türleridir:  
  
- <xref:System.Byte?displayProperty=nameWithType>  
  
- <xref:System.SByte?displayProperty=nameWithType>  
  
- <xref:System.Int16?displayProperty=nameWithType>  
  
- <xref:System.UInt16?displayProperty=nameWithType>  
  
- <xref:System.Int32?displayProperty=nameWithType>  
  
- <xref:System.UInt32?displayProperty=nameWithType>  
  
- <xref:System.Int64?displayProperty=nameWithType>  
  
- <xref:System.UInt64?displayProperty=nameWithType>  
  
- <xref:System.IntPtr?displayProperty=nameWithType>  
  
- <xref:System.UIntPtr?displayProperty=nameWithType>  
  
- <xref:System.Single?displayProperty=nameWithType>  
  
- <xref:System.Double?displayProperty=nameWithType>  
  
 Aşağıdaki karmaşık türler de blittable türleridir:  
  
- Bir tamsayılar dizisi gibi, blittable basit türlerin tek boyutlu dizileri. Ancak, blittable türlerin değişken dizisini içeren bir tür kendi blittable değildir.
  
- Yalnızca blittable türlerini içeren biçimlendirilen değer türleri (ve bunları biçimli türler olarak sıralanmış olmaları durumunda sınıflar). Biçimlendirilen değer türleri hakkında daha fazla bilgi için bkz. [değer türleri Için varsayılan sıralama](default-marshaling-behavior.md#default-marshaling-for-value-types).  
  
 Nesne başvuruları blittable değildir. Bu, kendileri tarafından blittable olan nesnelere başvuru dizisi içerir. Örneğin, blittable olan bir yapı tanımlayabilirsiniz, ancak bu yapılara başvuru dizisi içeren bir blittable Türü tanımlayamazsınız.  
  
 En iyi duruma getirme olarak, blittable temel türleri ve yalnızca blittable üyeleri içeren sınıfların dizileri, sıralama sırasında kopyalanmaları yerine [sabitlenmiştir](copying-and-pinning.md) . Çağıran ve çağrılan aynı Apartment olduğunda bu türler ın/out parametreleri olarak sıralanabilen görünebilir. Ancak, bu türler aslında parametrelerde olarak sıralanır ve <xref:System.Runtime.InteropServices.InAttribute> <xref:System.Runtime.InteropServices.OutAttribute> bağımsız değişkeni bir ın/out parametresi olarak sıralamak istiyorsanız ve özniteliklerini uygulamanız gerekir.
  
 Bazı yönetilen veri türleri, yönetilmeyen bir ortamda farklı bir temsil gerektirir. Bu blittable olmayan veri türlerinin sıralanabilen bir forma dönüştürülmesi gerekir. Örneğin, yönetilen dizeler, sıralanmadan önce dize nesnelerine dönüştürülmesi gerektiğinden blittable olmayan türlerdir.  
  
 Aşağıdaki tabloda, ad alanından blittable olmayan türler listelenmektedir <xref:System> . Statik bir yönteme veya bir sınıf örneğine başvuran veri yapıları olan [Temsilciler](default-marshaling-behavior.md#default-marshaling-for-delegates)de blittable değildir.  
  
|Blittable olmayan tür|Description|  
|-------------------------|-----------------|  
|[System. Array](default-marshaling-for-arrays.md)|C stili bir diziye veya öğesine dönüştürür `SAFEARRAY` .|  
|[System. Boolean](/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))|1, 2 veya 4 baytlık bir değere `true` 1 veya-1 ile dönüştürür.|  
|[System. Char](/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))|Unicode veya ANSI karaktere dönüştürür.|  
|[System. Class](/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))|Sınıf arabirimine dönüştürür.|  
|[System.Object](default-marshaling-for-objects.md)|Bir varyanta veya arabirime dönüştürür.|  
|[System. Mdarray](default-marshaling-for-arrays.md)|C stili bir diziye veya öğesine dönüştürür `SAFEARRAY` .|  
|[System. String](default-marshaling-for-strings.md)|Null bir başvuruya veya BSTR 'ye bir dizeye dönüştürür.|  
|[System. ValueType](/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))|Sabit bellek düzenine sahip bir yapıya dönüştürür.|  
|[System. Szarray](default-marshaling-for-arrays.md)|C stili bir diziye veya öğesine dönüştürür `SAFEARRAY` .|  
  
 Sınıf ve nesne türleri yalnızca COM birlikte çalışma tarafından desteklenir. Visual Basic, C# ve C++ ' daki ilgili türler için bkz. [sınıf kitaplığına genel bakış](../../standard/class-library-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Varsayılan Sıralama Davranışı](default-marshaling-behavior.md)
