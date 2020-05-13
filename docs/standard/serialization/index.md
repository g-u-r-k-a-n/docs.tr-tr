---
title: Serileştirme-.NET
description: Bu makalede ikili serileştirme, XML ve SOAP serileştirme ve JSON serileştirme dahil .NET serileştirme teknolojileri hakkında bilgi sağlanır.
ms.date: 09/02/2019
helpviewer_keywords:
- JSON serialization
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: b3d76c14dc9180a5f19781122d1a42bcae603e76
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377242"
---
# <a name="serialization-in-net"></a>.NET içinde serileştirme

Serileştirme, bir nesnenin durumunu kalıcı veya taşınan bir biçime dönüştürme işlemidir. Serileştirme tamamlayıcısı, bir akışı nesnesine dönüştüren seri hale getirme ' dir. Birlikte, bu süreçler verilerin depolanmasını ve aktarılmasını sağlar.  
  
.NET özellikleri aşağıdaki serileştirme teknolojilerine sahiptir:  
  
- [İkili serileştirme](binary-serialization.md) , bir uygulamanın farklı etkinleştirmeleri arasında bir nesnenin durumunu korumak için yararlı olan tür aslına uygunluk düzeyini korur. Örneğin, bir nesne panoya serileştirmek tarafından farklı uygulamalar arasında paylaşabilirsiniz. Bir nesneyi bir akışa, diske, belleğe, ağ üzerinden, vb. olarak seri hale getirebilirsiniz. Uzaktan iletişim serileştirme "değeri tarafından" nesnelerini geçirmek için bir bilgisayar veya uygulama etki alanından diğerine kullanır.  
  
- [XML ve SOAP serileştirme](xml-and-soap-serialization.md) yalnızca ortak özellikleri ve alanları serileştirir ve tür aslına uygunluk koruması yapmaz. Bu, verileri kullanan uygulamayı kısıtlamadan verileri sağlamak veya kullanmak istediğinizde faydalıdır. XML açık bir standart olduğundan, verileri Web genelinde paylaşmak için çekici bir seçimdir. SOAP aynı şekilde bir açık standarttır ve bu da etkileyici bir seçenek sunar.  
  
- [JSON serileştirme](system-text-json-overview.md) yalnızca ortak özellikleri serileştirir ve tür uygunluğa sahip değildir. JSON, web genelinde veri paylaşımı için çekici bir seçim olan açık bir standarttır.

## <a name="reference"></a>Başvuru

<xref:System.Runtime.Serialization>  
Serileştirme ve seri kaldırma nesneler için kullanılan sınıfları içerir.
  
<xref:System.Xml.Serialization>  
Nesneleri XML biçimli belge veya akışlara seri hale getirmek için kullanılabilecek sınıfları içerir.

<xref:System.Text.Json>  
Nesneleri JSON biçimli belgeler veya akışlara seri hale getirmek için kullanılabilecek sınıfları içerir.
