---
ms.openlocfilehash: 58d1c8cd3aff52703522391c14348bd81c108587
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568124"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a>Özel EncoderFallbackBuffer örnekleri özyinelemeli olarak geri dönemez

Özel <xref:System.Text.EncoderFallbackBuffer> örnekleri yinelemeli olarak geri dönemez. <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> uygulanması, hedef kodlamaya dönüştürülebilir bir karakter sırası ile sonuçlanmalıdır. Aksi takdirde, bir özel durum oluşur.

#### <a name="change-description"></a>Açıklamayı Değiştir

Bir karakterden bayta dönüştürme işlemi sırasında, çalışma zamanı hatalı biçimlendirilmiş veya dönüştürülebilir UTF-16 dizileri algılar ve bu karakterleri <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> yöntemine sağlar. `Fallback` yöntemi, orijinal dönüştürülebilir veriler için hangi karakterlerin yerine geçmeli olduğunu belirler ve bu karakterler bir döngüde <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> çağırarak bu karakterlerin boşaltılır.

Çalışma zamanı daha sonra bu değiştirme karakterlerini hedef kodlamaya dönüştürme girişiminde bulunur. Bu işlem başarılı olursa, çalışma zamanı özgün giriş dizesinde bıraktığınız yerden kodlamaya devam eder.

.NET Core Preview 7 ve önceki sürümlerinde, <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> özel uygulamaları hedef kodlamaya dönüştürülebilir olmayan karakter dizileri döndürebilir. Değiştirilen karakterler hedef kodlamaya dönüştürülemiyorsa, çalışma zamanı <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> yöntemini yeniden değiştirme karakterleriyle çağırır ve <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> yönteminin yeni bir değiştirme sırası döndürmesini bekliyor. Bu işlem, çalışma zamanı sonunda iyi biçimlendirilmiş, dönüştürülebilir bir değiştirme veya en fazla özyineleme sayısına ulaşılana kadar devam eder.

.NET Core 3,0 ile başlayarak, <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> özel uygulamaları hedef kodlamaya dönüştürülebilir karakter dizilerini döndürmelidir. Değiştirilen karakterler hedef kodlamaya dönüştürülemiyorsa bir <xref:System.ArgumentException> oluşturulur. Çalışma zamanı artık <xref:System.Text.EncoderFallbackBuffer> örneğine özyinelemeli çağrılar yapmayacaktır.

Bu davranış yalnızca aşağıdaki koşulların üçü de karşılandığında geçerlidir:

- Çalışma zamanı, hatalı biçimlendirilmiş bir UTF-16 sırası veya hedef kodlamaya dönüştürülemeyen bir UTF-16 sırası algılar.
- Özel bir <xref:System.Text.EncoderFallback> belirtildi.
- Özel <xref:System.Text.EncoderFallback>, yeni bir hatalı oluşturulmuş veya dönüştürülebilir UTF-16 sırasını değiştirme girişiminde bulunur.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

Çoğu geliştirici herhangi bir işlem yapması gerekli değildir.

Bir uygulama özel bir <xref:System.Text.EncoderFallback> ve <xref:System.Text.EncoderFallbackBuffer> sınıfı kullanıyorsa, <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> uygulamasının geri dönüş arabelleğini, <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> yöntemi çalışma zamanı tarafından ilk kez çağrıldığında hedef kodlamaya doğrudan dönüştürülebilir UTF-16 verileriyle doldurmasıdır.

#### <a name="category"></a>Kategori

CoreFx

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
