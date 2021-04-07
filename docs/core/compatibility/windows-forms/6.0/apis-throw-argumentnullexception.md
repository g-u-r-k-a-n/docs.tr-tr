---
title: "Son değişiklik: bazı API 'Ler bağımsız değişkenler NullException oluşturur"
description: .NET 6 ' daki Son değişiklik hakkında bilgi edinmek için bazı API 'Lerin bağımsız değişkenleri doğruladığını ve şimdi bir ArgumentNullException oluşturacağı
ms.date: 01/29/2021
ms.openlocfilehash: 1c7b41bf5e367dca394130da66360e660173ba14
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106496858"
---
# <a name="some-apis-throw-argumentnullexception"></a>Bazı API 'Ler bağımsız değişkenler NullException oluşturur

Bazı API 'Ler artık giriş parametrelerini doğrular ve <xref:System.ArgumentNullException> <xref:System.NullReferenceException> giriş bağımsız değişkenleriyle çağrılırsa daha önce oluşturduğu yerleri oluşturur `null` .

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, etkilenen API 'Ler, bir <xref:System.NullReferenceException> bağımsız değişkenle çağrılırsa bir oluşturur `null` .

.NET 6 ' dan itibaren, etkilenen API 'Ler bir <xref:System.ArgumentNullException> bağımsız değişkenle çağrılırsa bir oluşturur `null` .

## <a name="reason-for-change"></a>Değişiklik nedeni

<xref:System.ArgumentNullException>.NET çalışma zamanı davranışına uygun şekilde oluşturuluyor. Özel duruma neden olan bağımsız değişkeni açıkça iletişim kurarak daha iyi bir hata ayıklama deneyimi sağlar.

## <a name="version-introduced"></a>Sunulan sürüm

.NET 6.0

## <a name="recommended-action"></a>Önerilen eylem

- ' Yi gözden geçirin ve gerekirse, `null` giriş bağımsız değişkenlerinin etkilenen API 'lere geçirilmesini engellemek için kodunuzu güncelleştirin.
- Kodunuz tarafından kullanılıyorsa <xref:System.NullReferenceException> , için ek bir işleyici değiştirin veya ekleyin <xref:System.ArgumentNullException> .

## <a name="affected-apis"></a>Etkilenen API’ler

Aşağıdaki tabloda etkilenen API 'Ler ve belirli parametreler listelenmektedir:

| Metot/Özellik | Parametre adı | Sürüm değişti |
|-|-|-|
| <xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=fullName> | `index` | Önizleme 1 |
| <xref:System.Windows.Forms.DrawTreeNodeEventArgs.%23ctor(System.Drawing.Graphics,System.Windows.Forms.TreeNode,System.Drawing.Rectangle,System.Windows.Forms.TreeNodeStates)> | `graphics` | Preview 3 |
| <xref:System.Windows.Forms.DataGridViewRowStateChangedEventArgs.%23ctor(System.Windows.Forms.DataGridViewRow,System.Windows.Forms.DataGridViewElementStates)> | `dataGridViewRow` | Preview 4 |

## <a name="see-also"></a>Ayrıca bkz.

- [TreeNodeCollection. Item, düğüm başka bir yere atanırsa özel durum oluşturur](treenodecollection-item-throws-argumentexception.md)

<!--

### Affected APIs

- `P:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)`
- `M:System.Windows.Forms.DrawTreeNodeEventArgs.#ctor(System.Drawing.Graphics,System.Windows.Forms.TreeNode,System.Drawing.Rectangle,System.Windows.Forms.TreeNodeStates)`
- `M:System.Windows.Forms.DataGridViewRowStateChangedEventArgs.#ctor(System.Windows.Forms.DataGridViewRow,System.Windows.Forms.DataGridViewElementStates)`

### Category

Windows Forms

-->
