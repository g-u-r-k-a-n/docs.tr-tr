---
ms.openlocfilehash: 07527c247e6ccd53d2a77793946ffc796c3e1cbb
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644035"
---
### <a name="switchsystemwindowsformsuselegacyimages-compatibility-switch-not-supported"></a><span data-ttu-id="d32b8-101">Switch. System. Windows. Forms. UseLegacyImages uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="d32b8-101">Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported</span></span>

<span data-ttu-id="d32b8-102">.NET Framework 4,8 ' de tanıtılan `Switch.System.Windows.Forms.UseLegacyImages` uyumluluk anahtarı .NET Core 3,0 ' de Windows Forms desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="d32b8-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.8, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d32b8-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="d32b8-103">Change description</span></span>

<span data-ttu-id="d32b8-104">.NET Framework 4,8 ' den başlayarak, `Switch.System.Windows.Forms.UseLegacyImages` uyumluluğu anahtarı yüksek DPı ortamlarında ClickOnce senaryolarında olası görüntü ölçeklendirme sorunlarını çözmekteydi.</span><span class="sxs-lookup"><span data-stu-id="d32b8-104">Starting with the .NET Framework 4.8, the `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch addressed possible image scaling issues in ClickOnce scenarios in high DPI environments.</span></span> <span data-ttu-id="d32b8-105">`true`olarak ayarlandığında, anahtar, ölçek %100 ' den büyük olarak ayarlanan yüksek DPı ekranlarda kullanıcının eski görüntü ölçeklendirmesini geri yüklemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="d32b8-105">When set to `true`, the switch allows the user to restore legacy image scaling on high DPI displays whose scale is set to greater than 100%.</span></span> <span data-ttu-id="d32b8-106">Daha fazla bilgi için bkz. GitHub üzerinde [.NET Framework 4,8 sürüm notları](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) .</span><span class="sxs-lookup"><span data-stu-id="d32b8-106">For more information, see [.NET Framework 4.8 Release Notes](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) on GitHub.</span></span>

<span data-ttu-id="d32b8-107">.NET Core 'da `Switch.System.Windows.Forms.UseLegacyImages` anahtarı desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="d32b8-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyImages` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d32b8-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="d32b8-108">Version introduced</span></span>

<span data-ttu-id="d32b8-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="d32b8-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d32b8-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="d32b8-110">Recommended action</span></span>

<span data-ttu-id="d32b8-111">Anahtarı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="d32b8-111">Remove the switch.</span></span> <span data-ttu-id="d32b8-112">Anahtar desteklenmez ve alternatif bir işlev kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d32b8-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="d32b8-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="d32b8-113">Category</span></span>

<span data-ttu-id="d32b8-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d32b8-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d32b8-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="d32b8-115">Affected APIs</span></span>

- <span data-ttu-id="d32b8-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="d32b8-116">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
