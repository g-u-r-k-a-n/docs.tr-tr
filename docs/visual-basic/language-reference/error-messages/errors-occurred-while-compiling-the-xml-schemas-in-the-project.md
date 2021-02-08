---
description: 'Hakkında daha fazla bilgi edinin: BC36810: Projedeki XML şemaları derlenirken hatalar oluştu'
title: Projedeki XML şemaları derlenirken hataları oluştu
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 78e88208c0d3df12e7bad8ab46b1d91bce559923
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796489"
---
# <a name="bc36810-errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a>BC36810: Projedeki XML şemaları derlenirken hatalar oluştu

Projedeki XML şemaları derlenirken hatalar oluştu. Bu nedenle, XML IntelliSense kullanılamıyor.

 Projeye dahil edilen bir XML şema tanımı (XSD) şemasında bir hata var. Bu hata, proje için mevcut XSD şema kümesiyle çakışan bir XSD şeması (. xsd) dosyası eklediğinizde oluşur.

 **Hata kimliği:** BC36810

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- **Hatalar Listesi** penceresinde uyarıya çift tıklayın. Visual Basic, sizi uyarının kaynağı olan XSD dosyasındaki konuma götürür. XSD şemasında hatayı düzeltin.

- Tüm gerekli XSD şeması (. xsd) dosyalarının projeye eklendiğinden emin olun. . Xsd dosyalarınızı **Çözüm Gezgini** görmek için **Proje** menüsündeki **tüm dosyaları göster** ' e tıklamanız gerekebilir. Bir. xsd dosyasına sağ tıklayın ve dosyayı projenize dahil etmek için **projeye dahil et** ' e tıklayın.

- XML 'yi şema Sihirbazı ' nı kullanıyorsanız, şemaları aynı kaynaktan birden çok kez çıkarmanız durumunda bu hata ortaya çıkabilir. Bu durumda, var olan XSD şema dosyalarını projeden kaldırabilir, şema öğe şablonuna yeni bir XML ekleyebilir ve sonra projenize yönelik tüm geçerli XML kaynaklarıyla XML 'e şema Sihirbazı sağlayabilirsiniz.

- XSD şemanızda herhangi bir hata tanımlanmamışsa, XML derleyicisi ayrıntılı bir hata iletisi sağlamak için yeterli bilgiye sahip olmayabilir. Projenize dahil edilen. xsd dosyaları için XML ad alanlarının, Visual Studio 'da XML şeması kümesi için tanımlanan XML ad alanları ile eşleştiğinden emin olmanız durumunda daha ayrıntılı hata bilgileri alabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Listesi penceresi](/visualstudio/ide/reference/error-list-window)
- [XML](../../programming-guide/language-features/xml/index.md)
