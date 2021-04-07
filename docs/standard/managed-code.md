---
title: Yönetilen kod nedir?
description: Yönetilen kodun, yürütmesi, ortak dil çalışma zamanı (CLR) olan bir çalışma zamanı tarafından yönetilen kod olduğunu öğrenin.
ms.date: 06/20/2016
ms.assetid: 20bb7ea8-192e-4a96-8ef3-e10e1950fd3d
ms.openlocfilehash: 10036ab92718aa56a068c7515dec4302a5c3ac9c
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498534"
---
# <a name="what-is-managed-code"></a>“Yönetilen kod” nedir?

.NET ile çalışırken, genellikle "yönetilen kod" terimiyle karşılaşırsınız. Bu belgede, bu terimin ne anlama geldiğini ve bunun etrafında ek bilgiler açıklanmaktadır.

Çok basit bir şekilde koymak için, yönetilen kod yalnızca bir çalışma zamanı tarafından yönetilen kod olur. Bu durumda, söz konusu çalışma zamanına uygulamadan bağımsız olarak **ortak dil çalışma zamanı** veya clr adı verilir (örneğin, [mono](https://www.mono-project.com/), .NET Framework veya .NET Core/. NET 5 +). CLR, yönetilen kodu alma, makine kodunda derleme ve daha sonra yürütme aşamasında olduğundan ücretsizdir. Bunun üzerine, çalışma zamanı otomatik bellek yönetimi, güvenlik sınırları, tür güvenliği vb. gibi çeşitli önemli hizmetler sağlar.

Bunu, "yönetilmeyen kod" olarak da adlandırılan bir C/C++ programını çalıştırdığınız şekilde kontrast. Yönetilmeyen dünyada, programcı çok sayıda her şeyin üzerinden ücretlendirilir. Gerçek program temelde, işletim sisteminin (OS) belleğe yüklediği ve başladığı bir ikili dosya olur. Bellek yönetiminden güvenlik 'e kadar olan diğer her şey programcı 'nin bir yükünden oluşur.

Yönetilen kod, C#, Visual Basic, F # ve diğerleri gibi .NET üzerinde çalıştırılabilen üst düzey dillerden birinde yazılır. Bu dillerde yazılmış kodu kendi derleyicisinden derlerken, makine kodu almaz. Çalışma zamanının daha sonra derleyen ve yürütülen **ara dil** kodunu alırsınız. C++, Windows üzerinde çalışan yerel, yönetilmeyen ikili dosyalar da oluşturabildiği için bu kuralın tek istisnası olur.

## <a name="intermediate-language--execution"></a>Ara dil & yürütme

"Ara dil" (veya kısa için Il) nedir? Bu, üst düzey .NET dillerde yazılmış kodların derlenmesi ürünüdür. Bu dillerden birinde yazılan kodunuzu derledikten sonra Il 'den çıkan bir ikiliye sahip olursunuz. Il 'nin çalışma zamanının üzerinde çalışan herhangi bir dilden bağımsız olduğunu unutmamak önemlidir; Bu durumda, daha fazla saysanız okuyabilmeniz için ayrı bir belirtim de vardır.

Üst düzey kodınızdan Il 'yi oluşturduktan sonra büyük olasılıkla çalıştırmak istersiniz. Bu, CLR 'nin **tam zamanında** derleme işlemini nereden aldığını ve başlattığı veya bir CPU üzerinde gerçekten ÇALıŞTıRıLABILECEK şekilde Il 'den makine koduna kodlalama işleminin bulunduğu yerdir.  Bu şekilde, CLR kodunuzun ne yaptığını tam olarak bilir ve onu etkili bir şekilde _yönetebilir_ .

Ara dil bazen ortak ara dil (CıL) veya Microsoft ara dili (MSIL) olarak da adlandırılır.

## <a name="unmanaged-code-interoperability"></a>Yönetilmeyen kod birlikte çalışabilirliği

Kuşkusuz, CLR yönetilen ve yönetilmeyen dünya arasındaki sınırları geçirmeyi sağlar ve [temel sınıf kitaplıklarında](framework-libraries.md)bile bu şekilde çok sayıda kod vardır. Bu, **birlikte çalışabilirlik** veya kısa bir şekilde **birlikte** çalışabilirlik olarak adlandırılır. Bu hükümler, örneğin, yönetilmeyen bir kitaplığı kaydırabilmeniz ve buna çağrı yapmanıza olanak sağlar. Ancak, bunu yaptığınızda, kod çalışma zamanının sınırlarını geçtiğinde, yürütmenin gerçek yönetiminin, yönetilmeyen kodun yanında yeniden olduğunu ve bu nedenle aynı kısıtlamaların altına düştüğünü unutmayın.

Buna benzer şekilde C#, yürütmenin CLR tarafından yönetilmediği bir kod parçasını atayan, **güvenli olmayan bağlam** olarak bilinerek doğrudan kodda işaretçiler gibi yönetilmeyen yapıları kullanmanıza olanak tanıyan bir dildir.

## <a name="more-resources"></a>Diğer kaynaklar

* [.NET Framework’e Genel Bakış](../framework/get-started/overview.md)
* [Güvenli Olmayan Kod ve İşaretçiler](../csharp/language-reference/unsafe-code.md)
* [Native ile birlikte çalışma](./native-interop/index.md)
