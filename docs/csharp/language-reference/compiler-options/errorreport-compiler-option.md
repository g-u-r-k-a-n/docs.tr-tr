---
description: -errorreport (C# derleyici seçenekleri)
title: -errorreport (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
ms.openlocfilehash: 6238ac392ff99d18d9cc7ea07e23b08ff235c14f
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "91173236"
---
# <a name="-errorreport-c-compiler-options"></a>-errorreport (C# derleyici seçenekleri)

Bu seçenek, C# iç derleyici hatasını Microsoft 'a bildirmenin kolay bir yolunu sağlar.

> [!NOTE]
> Windows Vista ve Windows Server 2008 ' de, Visual Studio için yaptığınız hata raporlama ayarları Windows Hata Bildirimi (WER) ile yapılan ayarları geçersiz kılmaz. WER ayarları her zaman Visual Studio hata raporlama ayarlarından önceliklidir.

## <a name="syntax"></a>Söz dizimi

```console
-errorreport:{ none | prompt | queue | send }
```

## <a name="arguments"></a>Bağımsız değişkenler

 **yok**  
 İç derleyici hataları hakkında raporlar toplanmayacak veya Microsoft 'a gönderilmez.

 **komut istemi** İç derleyici hatası aldığınızda rapor göndermenizi ister. geliştirme ortamında bir uygulama derlerken varsayılan değer, **istem** varsayılandır.

 **kuyruk** Hata raporunu sıralar. Yönetici kimlik bilgileriyle oturum açtığınızda, son oturum açtığınız zamandan bu yana tüm sorunları bildirebilirsiniz. Her üç günde birden çok kez rapor göndermeniz istenmez. komut satırında bir uygulama derlerken varsayılan **kuyruk** varsayılandır.

 **Gönder** , İç derleyici hatalarının raporlarını otomatik olarak Microsoft 'a gönderir. Bu seçeneği etkinleştirmek için öncelikle Microsoft veri toplama ilkesini kabul etmelisiniz. Bir bilgisayarda **-errorreport: Send** ' i ilk kez belirttiğinizde, bir derleyici Iletisi sizi Microsoft veri toplama ilkesini Içeren bir Web sitesine başvuracaktır.

## <a name="remarks"></a>Açıklamalar

 Derleyici bir kaynak kodu dosyasını işleyeişce bir iç derleyici hatası (ıCE) oluşur. Bir buz gerçekleştiğinde, derleyici bir çıkış dosyası ya da kodunuzu onarmak için kullanabileceğiniz yararlı bir tanılama üretmez.

 Önceki sürümlerde, bir buz aldığınızda sorunu bildirmek için Microsoft Ürün Destek Hizmetleri 'ne başvurmanız önerilir. **-Errorreport** kullanarak, Visual C# EKIBINE Ice bilgisi sağlayabilirsiniz. Hata raporlarınız, gelecekteki derleyici sürümlerinin artırılmasına yardımcı olabilir.

 Kullanıcının raporları gönderebilme özelliği bilgisayar ve Kullanıcı ilkesi izinlerine bağlıdır.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için

1. Projenin **Özellikler** sayfasını açın. Daha fazla bilgi için bkz. [derleme sayfası, proje Tasarımcısı (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).

2. **Yapı** özelliği sayfasına tıklayın.

3. **Gelişmiş** düğmesine tıklayın.

4. **Iç derleyici hata raporlama** özelliğini değiştirin.

 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A> ..

## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
