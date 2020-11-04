---
title: .NET 'teki temel dize Işlemeleri
description: Birçok dize yöntemini çağıran bir örneğe bakın.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [.NET], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
ms.openlocfilehash: 659f01cc1d7ae03e12e83329e4fd2446b7512475
ms.sourcegitcommit: ffd4d5e824db6c5f0c3521c0e802fd9e8f0edcbe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93342624"
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a>Nasıl yapılır: .NET 'te temel dize Işlemeleri gerçekleştirme

Aşağıdaki örnek, [temel dize işlemleri](basic-string-operations.md) konularında açıklanan yöntemlerin bazılarını kullanarak, bir gerçek dünya uygulamasında bulunabilir bir şekilde dize düzenlemeleri gerçekleştiren bir sınıf oluşturur. `MailToData`Sınıfı, bir bireyin adı ve adresini ayrı özelliklerde depolar ve `City` ,, `State` ve `Zip` alanlarını kullanıcıya görüntüleme için tek bir dize olarak birleştirmek için bir yol sağlar. Ayrıca, sınıfı kullanıcının şehir, eyalet ve ZIP kodu bilgilerini tek bir dize olarak girmesine izin verir. Uygulama, tek dizeyi otomatik olarak ayrıştırır ve ilgili özelliğe uygun bilgileri girer.

Kolaylık olması için bu örnek, bir komut satırı arabirimi ile bir konsol uygulaması kullanır.

## <a name="example"></a>Örnek

[!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
[!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]

Yukarıdaki kod yürütüldüğünde, kullanıcıdan ad ve adreslerini girmesi istenir. Uygulama, bilgileri uygun özelliklere koyar ve bu bilgileri, şehir, eyalet ve ZIP kodu bilgilerini görüntüleyen tek bir dize oluşturarak kullanıcıya geri görüntüler.

## <a name="see-also"></a>Ayrıca bkz.

- [Temel dize Işlemleri](basic-string-operations.md)
