---
title: -Doc (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- FileProperties.BuildAction
- /doc
helpviewer_keywords:
- comments, C# code
- XML documentation [C#], comments in source files
- doc compiler option [C#]
- Visual C#, XML documentation for
- -doc compiler option [C#]
- /doc compiler option [C#]
ms.assetid: 849eea59-c936-4311-bad8-d07404480f2a
ms.openlocfilehash: 7b22bbf75b29fdffd9927110ebe5b4e5309cd778
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73191840"
---
# <a name="-doc-c-compiler-options"></a>-Doc (C# derleyici seçenekleri)
**-Doc** seçeneği, belge AÇıKLAMALARıNı bir XML dosyasına eklemenizi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Derlemenin kaynak kodu dosyalarındaki yorumlarla doldurulan XML için çıkış dosyası.  
  
## <a name="remarks"></a>Açıklamalar  
 Kaynak kodu dosyalarında, aşağıdakilerden önce gelen belge açıklamaları işlenebilir ve XML dosyasına eklenebilir:  
  
- Bir [sınıf](../keywords/class.md), [temsilci](../keywords/delegate.md)veya [arabirim](../keywords/interface.md) olarak Kullanıcı tanımlı türler  
  
- Alan, [olay](../keywords/event.md), [özellik](../../programming-guide/classes-and-structs/using-properties.md)veya yöntem olarak bu Üyeler  
  
 Main içeren kaynak kodu dosyası ilk olarak XML 'e çıktı.  
  
 [IntelliSense](/visualstudio/ide/using-intellisense) özelliğiyle kullanılmak üzere oluşturulan. xml dosyasını kullanmak için,. xml dosyasının dosya adının desteklemek istediğiniz derlemeyle aynı olmasına izin verin ve. xml dosyasının derlemeyle aynı dizinde olduğundan emin olun. Bu nedenle, Visual Studio projesinde derlemeye başvuruluyorsa. xml dosyası da bulunur. Bkz. [kod açıklamaları sağlama](/visualstudio/ide/reference/generate-xml-documentation-comments) ve daha fazla bilgi.  
  
 [-Target: Module](./target-module-compiler-option.md)ile derlenmediğiniz takdirde `file`, derlemenin çıkış dosyası için derleme bildirimini içeren dosyanın adını belirten \<bütünleştirilmiş kod >\</assembly > etiketleri içerecektir.  
  
> [!NOTE]
> -Doc seçeneği tüm giriş dosyaları için geçerlidir; veya proje ayarları 'nda ayarlandıysa, projedeki tüm dosyalar. Belirli bir dosyanın veya kod bölümünün belge açıklamalarıyla ilgili uyarıları devre dışı bırakmak için [#pragma uyarı](../preprocessor-directives/preprocessor-pragma-warning.md)kullanın.  
  
 Kodunuzda açıklamalardan belge oluşturma yolları için bkz. [belge açıklamaları Için önerilen Etiketler](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) .  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikler** sayfasını açın.  
  
2. **Derleme** sekmesine tıklayın.  
  
3. **XML belge dosyası** özelliğini değiştirin.  
  
 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
