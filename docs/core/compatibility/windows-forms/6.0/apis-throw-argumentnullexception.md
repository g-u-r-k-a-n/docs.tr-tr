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
# <a name="some-apis-throw-argumentnullexception"></a><span data-ttu-id="074e9-103">Bazı API 'Ler bağımsız değişkenler NullException oluşturur</span><span class="sxs-lookup"><span data-stu-id="074e9-103">Some APIs throw ArgumentNullException</span></span>

<span data-ttu-id="074e9-104">Bazı API 'Ler artık giriş parametrelerini doğrular ve <xref:System.ArgumentNullException> <xref:System.NullReferenceException> giriş bağımsız değişkenleriyle çağrılırsa daha önce oluşturduğu yerleri oluşturur `null` .</span><span class="sxs-lookup"><span data-stu-id="074e9-104">Some APIs now validate input parameters and throw an <xref:System.ArgumentNullException> where previously they threw a <xref:System.NullReferenceException>, if invoked with `null` input arguments.</span></span>

## <a name="change-description"></a><span data-ttu-id="074e9-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="074e9-105">Change description</span></span>

<span data-ttu-id="074e9-106">Önceki .NET sürümlerinde, etkilenen API 'Ler, bir <xref:System.NullReferenceException> bağımsız değişkenle çağrılırsa bir oluşturur `null` .</span><span class="sxs-lookup"><span data-stu-id="074e9-106">In previous .NET versions, the affected APIs throw a <xref:System.NullReferenceException> if invoked with an argument that's `null`.</span></span>

<span data-ttu-id="074e9-107">.NET 6 ' dan itibaren, etkilenen API 'Ler bir <xref:System.ArgumentNullException> bağımsız değişkenle çağrılırsa bir oluşturur `null` .</span><span class="sxs-lookup"><span data-stu-id="074e9-107">Starting in .NET 6, the affected APIs throw an <xref:System.ArgumentNullException> if invoked with an argument that's `null`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="074e9-108">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="074e9-108">Reason for change</span></span>

<span data-ttu-id="074e9-109"><xref:System.ArgumentNullException>.NET çalışma zamanı davranışına uygun şekilde oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="074e9-109">Throwing <xref:System.ArgumentNullException> conforms to .NET Runtime behavior.</span></span> <span data-ttu-id="074e9-110">Özel duruma neden olan bağımsız değişkeni açıkça iletişim kurarak daha iyi bir hata ayıklama deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="074e9-110">It provides a better debug experience by clearly communicating which argument caused the exception.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="074e9-111">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="074e9-111">Version introduced</span></span>

<span data-ttu-id="074e9-112">.NET 6.0</span><span class="sxs-lookup"><span data-stu-id="074e9-112">.NET 6.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="074e9-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="074e9-113">Recommended action</span></span>

- <span data-ttu-id="074e9-114">' Yi gözden geçirin ve gerekirse, `null` giriş bağımsız değişkenlerinin etkilenen API 'lere geçirilmesini engellemek için kodunuzu güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="074e9-114">Review and, if necessary, update your code to prevent passing `null` input arguments to the affected APIs.</span></span>
- <span data-ttu-id="074e9-115">Kodunuz tarafından kullanılıyorsa <xref:System.NullReferenceException> , için ek bir işleyici değiştirin veya ekleyin <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="074e9-115">If your code handles <xref:System.NullReferenceException>, replace or add an additional handler for <xref:System.ArgumentNullException>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="074e9-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="074e9-116">Affected APIs</span></span>

<span data-ttu-id="074e9-117">Aşağıdaki tabloda etkilenen API 'Ler ve belirli parametreler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="074e9-117">The following table lists the affected APIs and specific parameters:</span></span>

| <span data-ttu-id="074e9-118">Metot/Özellik</span><span class="sxs-lookup"><span data-stu-id="074e9-118">Method/property</span></span> | <span data-ttu-id="074e9-119">Parametre adı</span><span class="sxs-lookup"><span data-stu-id="074e9-119">Parameter name</span></span> | <span data-ttu-id="074e9-120">Sürüm değişti</span><span class="sxs-lookup"><span data-stu-id="074e9-120">Version changed</span></span> |
|-|-|-|
| <xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=fullName> | `index` | <span data-ttu-id="074e9-121">Önizleme 1</span><span class="sxs-lookup"><span data-stu-id="074e9-121">Preview 1</span></span> |
| <xref:System.Windows.Forms.DrawTreeNodeEventArgs.%23ctor(System.Drawing.Graphics,System.Windows.Forms.TreeNode,System.Drawing.Rectangle,System.Windows.Forms.TreeNodeStates)> | `graphics` | <span data-ttu-id="074e9-122">Preview 3</span><span class="sxs-lookup"><span data-stu-id="074e9-122">Preview 3</span></span> |
| <xref:System.Windows.Forms.DataGridViewRowStateChangedEventArgs.%23ctor(System.Windows.Forms.DataGridViewRow,System.Windows.Forms.DataGridViewElementStates)> | `dataGridViewRow` | <span data-ttu-id="074e9-123">Preview 4</span><span class="sxs-lookup"><span data-stu-id="074e9-123">Preview 4</span></span> |

## <a name="see-also"></a><span data-ttu-id="074e9-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="074e9-124">See also</span></span>

- [<span data-ttu-id="074e9-125">TreeNodeCollection. Item, düğüm başka bir yere atanırsa özel durum oluşturur</span><span class="sxs-lookup"><span data-stu-id="074e9-125">TreeNodeCollection.Item throws exception if node is assigned elsewhere</span></span>](treenodecollection-item-throws-argumentexception.md)

<!--

### Affected APIs

- `P:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)`
- `M:System.Windows.Forms.DrawTreeNodeEventArgs.#ctor(System.Drawing.Graphics,System.Windows.Forms.TreeNode,System.Drawing.Rectangle,System.Windows.Forms.TreeNodeStates)`
- `M:System.Windows.Forms.DataGridViewRowStateChangedEventArgs.#ctor(System.Windows.Forms.DataGridViewRow,System.Windows.Forms.DataGridViewElementStates)`

### Category

Windows Forms

-->
