---
title: Adlandırma Kaynakları
description: .NET 'teki kaynaklar için adlandırma kılavuzunu gözden geçirerek adlandırma özelliklerine yönelik yönergelere benzer.
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
ms.openlocfilehash: 08046fb78638546b3dcab856674424c92c03fe83
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706417"
---
# <a name="naming-resources"></a>Adlandırma Kaynakları

Yerelleştirilebilir kaynaklara, özellikler gibi belirli nesneler aracılığıyla başvurulabildiğinden, kaynaklarla ilgili adlandırma yönergeleri Özellik yönergelerine benzer.

 ✔️, kaynak anahtarlarında Pascalbüyük harfleri kullanır.

 ✔️, kısa tanımlayıcılar yerine açıklayıcı bir ad sağlar.

 ❌ Ana CLR dillerinin dile özgü anahtar sözcüklerini kullanmayın.

 ✔️, adlandırma kaynaklarında yalnızca alfasayısal karakterler ve alt çizgi kullanır.

 ✔️, özel durum iletisi kaynakları için aşağıdaki adlandırma kuralını kullanır.

 Kaynak tanımlayıcısı, özel durum türü adı artı özel durumun kısa bir tanımlayıcısı olmalıdır:

 `ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`
 `ArgumentExceptionFileNameIsMalformed`

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
- [Adlandırma yönergeleri](naming-guidelines.md)
