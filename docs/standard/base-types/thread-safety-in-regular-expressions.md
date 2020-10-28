---
title: Normal İfadelerde İş Parçacığı Güvenliği
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET regular expressions, threads
- regular expressions, threads
- searching with regular expressions, threads
- parsing text with regular expressions, threads
- pattern-matching with regular expressions, threads
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
ms.openlocfilehash: 29ff647d623c047c63c52732a3e8bce5f0e95d6c
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889289"
---
# <a name="thread-safety-in-regular-expressions"></a>Normal İfadelerde İş Parçacığı Güvenliği
<xref:System.Text.RegularExpressions.Regex>Sınıfın kendisi iş parçacığı güvenlidir ve sabittir (salt okunurdur). Diğer bir deyişle, **Regex** nesneleri herhangi bir iş parçacığında oluşturulabilir ve iş parçacıkları arasında paylaşılabilir; eşleşen Yöntemler herhangi bir iş parçacığından çağrılabilir ve hiçbir şekilde hiçbir genel durumu değiştirmez.  
  
 Ancak, **Regex** tarafından döndürülen sonuç nesneleri ( **Match** ve **MatchCollection** ) tek bir iş parçacığında kullanılmalıdır. Bu nesnelerin birçoğu mantıksal olarak sabit olsa da, uygulamaları performansı artırmak için bazı sonuçların hesaplamasını erteleyebilir ve sonuç olarak, arayanların bunlara erişimi serileştirmesi gerekir.  
  
 Birden çok iş parçacığında **Regex** sonuç nesnelerini paylaşma gereksinimi varsa, bu nesneler eşitlenmiş yöntemleri çağırarak iş parçacığı açısından güvenli örneklere dönüştürülebilir. Numaralandırıcılar hariç, tüm normal ifade sınıfları iş parçacığı açısından güvenlidir veya eşitlenmiş bir yöntem tarafından iş parçacığı güvenli nesnelerine dönüştürülebilir.  
  
 Numaralandırıcılar tek istisnadır. Uygulama, çağrıları koleksiyon numaralandırıcılara serileştirmelidir. Kural, bir koleksiyonun birden fazla iş parçacığında aynı anda numaralandırılabilir olması, Numaralandırıcı tarafından geçilen koleksiyonun kök nesnesindeki Numaralandırıcı yöntemlerini eşitlemeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET normal Ifadeleri](regular-expressions.md)
