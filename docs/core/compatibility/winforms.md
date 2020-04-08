---
title: Windows Formlar değişiklikleri kırma
description: .NET Core için Windows Formlarında çığır açan değişiklikleri listeler.
ms.date: 01/08/2020
ms.openlocfilehash: 25c568a8a0092a9c4874419c64c7dcebea4dce9e
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888156"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="d3e67-103">Windows Formlarında değişiklik kırma</span><span class="sxs-lookup"><span data-stu-id="d3e67-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="d3e67-104">Windows Forms desteği 3.0 sürümünde .NET Core'a eklendi.</span><span class="sxs-lookup"><span data-stu-id="d3e67-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="d3e67-105">Bu makalede, windows formları için son dakika değişiklikleri tanıtıldıkları .NET Core sürümüne göre listelenir.</span><span class="sxs-lookup"><span data-stu-id="d3e67-105">This article lists breaking changes for Windows Forms by the .NET Core version in which they were introduced.</span></span> <span data-ttu-id="d3e67-106">Bir Windows Forms uygulamasını .NET Framework'den veya .NET Core'un önceki sürümünden (3.0 veya sonraki) yükseltiyorsanız, bu makale sizin için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d3e67-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article is applicable to you.</span></span>

<span data-ttu-id="d3e67-107">Aşağıdaki kesme değişiklikleri bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="d3e67-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="d3e67-108">Son dakika değişikliği</span><span class="sxs-lookup"><span data-stu-id="d3e67-108">Breaking change</span></span> | <span data-ttu-id="d3e67-109">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="d3e67-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="d3e67-110">WinForms API'ler şimdi ArgumentNullException atmak</span><span class="sxs-lookup"><span data-stu-id="d3e67-110">WinForms APIs now throw ArgumentNullException</span></span>](#winforms-apis-now-throw-argumentnullexception) | <span data-ttu-id="d3e67-111">5.0</span><span class="sxs-lookup"><span data-stu-id="d3e67-111">5.0</span></span> |
| [<span data-ttu-id="d3e67-112">Kaldırılan denetimler</span><span class="sxs-lookup"><span data-stu-id="d3e67-112">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="d3e67-113">3.1</span><span class="sxs-lookup"><span data-stu-id="d3e67-113">3.1</span></span> |
| [<span data-ttu-id="d3e67-114">Araç ipucu gösterilirse CellFormatting olayı yükseltilmez</span><span class="sxs-lookup"><span data-stu-id="d3e67-114">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="d3e67-115">3.1</span><span class="sxs-lookup"><span data-stu-id="d3e67-115">3.1</span></span> |
| [<span data-ttu-id="d3e67-116">Control.DefaultFont Segoe UI 9 pt olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="d3e67-116">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="d3e67-117">3,0</span><span class="sxs-lookup"><span data-stu-id="d3e67-117">3.0</span></span> |
| [<span data-ttu-id="d3e67-118">FolderBrowserDialog modernizasyonu</span><span class="sxs-lookup"><span data-stu-id="d3e67-118">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="d3e67-119">3,0</span><span class="sxs-lookup"><span data-stu-id="d3e67-119">3.0</span></span> |
| [<span data-ttu-id="d3e67-120">SerializableAttribute bazı Windows Forms türlerinden kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="d3e67-120">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="d3e67-121">3,0</span><span class="sxs-lookup"><span data-stu-id="d3e67-121">3.0</span></span> |
| [<span data-ttu-id="d3e67-122">AllowUpdateChildControlIndexForTabControls uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="d3e67-122">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="d3e67-123">3,0</span><span class="sxs-lookup"><span data-stu-id="d3e67-123">3.0</span></span> |
| [<span data-ttu-id="d3e67-124">DomainUpDown.UseLegacyScrolling uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="d3e67-124">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="d3e67-125">3,0</span><span class="sxs-lookup"><span data-stu-id="d3e67-125">3.0</span></span> |
| [<span data-ttu-id="d3e67-126">DoNotLoadLatestRichEditControl uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="d3e67-126">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="d3e67-127">3,0</span><span class="sxs-lookup"><span data-stu-id="d3e67-127">3.0</span></span> |
| [<span data-ttu-id="d3e67-128">DoNotSupportSelectAllShortcutInMultilineTextBox uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="d3e67-128">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="d3e67-129">3,0</span><span class="sxs-lookup"><span data-stu-id="d3e67-129">3.0</span></span> |
| [<span data-ttu-id="d3e67-130">DontSupportReentrantFilterMessage uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="d3e67-130">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="d3e67-131">3,0</span><span class="sxs-lookup"><span data-stu-id="d3e67-131">3.0</span></span> |
| [<span data-ttu-id="d3e67-132">EtkinleştirVisualStyleValidation uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="d3e67-132">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="d3e67-133">3,0</span><span class="sxs-lookup"><span data-stu-id="d3e67-133">3.0</span></span> |
| [<span data-ttu-id="d3e67-134">UseLegacyContextMenuStripSourceControlValue uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="d3e67-134">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="d3e67-135">3,0</span><span class="sxs-lookup"><span data-stu-id="d3e67-135">3.0</span></span> |
| [<span data-ttu-id="d3e67-136">UseLegacyImages uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="d3e67-136">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="d3e67-137">3,0</span><span class="sxs-lookup"><span data-stu-id="d3e67-137">3.0</span></span> |
| [<span data-ttu-id="d3e67-138">ErişilebilirObject.RuntimeIDFirstItem için erişim değişikliği</span><span class="sxs-lookup"><span data-stu-id="d3e67-138">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem) | <span data-ttu-id="d3e67-139">3,0</span><span class="sxs-lookup"><span data-stu-id="d3e67-139">3.0</span></span> |
| [<span data-ttu-id="d3e67-140">Windows Formlarından Kaldırılan Yinelenen API'ler</span><span class="sxs-lookup"><span data-stu-id="d3e67-140">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms) | <span data-ttu-id="d3e67-141">3,0</span><span class="sxs-lookup"><span data-stu-id="d3e67-141">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="d3e67-142">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="d3e67-142">.NET 5.0</span></span>

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

***

## <a name="net-core-31"></a><span data-ttu-id="d3e67-143">.NET Çekirdek 3.1</span><span class="sxs-lookup"><span data-stu-id="d3e67-143">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="d3e67-144">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="d3e67-144">.NET Core 3.0</span></span>

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9pt](~/includes/core-changes/windowsforms/3.0/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/3.0/modernized-folderbrowserdialog.md)]

***

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/3.0/remove-serializationattribute.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyscrolling.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotloadlatestricheditcontrol.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-dontsupportreentrantfiltermessage.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyimages.md)]

***

[!INCLUDE[Change of access for AccessibleObject.RuntimeIDFirstItem](~/includes/core-changes/windowsforms/3.0/changed-access-for-runtimeidfirstitem.md)]

***

[!INCLUDE[Duplicated APIs removed from Windows Forms](~/includes/core-changes/windowsforms/3.0/remove-duplicated-apis.md)]

***

## <a name="see-also"></a><span data-ttu-id="d3e67-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3e67-145">See also</span></span>

- [<span data-ttu-id="d3e67-146">Windows Forms uygulamasını .NET Core'a taşıma</span><span class="sxs-lookup"><span data-stu-id="d3e67-146">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
