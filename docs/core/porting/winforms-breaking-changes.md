---
title: .NET Core 'a .NET Framework WinForms için son değişiklikler
description: Windows Forms uygulamalar için .NET Framework son değişiklikleri .NET Core 'a listeler.
ms.date: 11/27/2019
ms.openlocfilehash: cc1f319dcc83a633c81c49195d743784fe5916d9
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643979"
---
# <a name="breaking-changes-in-windows-forms-net-framework-to-net-core"></a><span data-ttu-id="ad3e2-103">Windows Forms (.NET Framework .NET Core 'a) son değişiklikler</span><span class="sxs-lookup"><span data-stu-id="ad3e2-103">Breaking changes in Windows Forms (.NET Framework to .NET Core)</span></span>

<span data-ttu-id="ad3e2-104">WPF ve Windows Forms desteği sürüm 3,0 ' de .NET Core 'a eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="ad3e2-104">WPF and Windows Forms support were added to .NET Core in version 3.0.</span></span> <span data-ttu-id="ad3e2-105">.NET Framework bir Windows Forms veya Windows Presentation Foundation uygulamasını .NET Core 'a geçiriyorsanız, bu makalede listelenen son değişiklikler uygulamanızı etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="ad3e2-105">If you're migrating a Windows Forms or Windows Presentation Foundation app from .NET Framework to .NET Core, the breaking changes listed in this article may affect your app.</span></span>

<span data-ttu-id="ad3e2-106">Son değişiklikler, tanıtıldıkları .NET Core sürümüne göre gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="ad3e2-106">Breaking changes are grouped by the .NET Core version in which they were introduced.</span></span>

## <a name="net-core-31"></a><span data-ttu-id="ad3e2-107">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="ad3e2-107">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

## <a name="net-core-30"></a><span data-ttu-id="ad3e2-108">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ad3e2-108">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ad3e2-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad3e2-109">See also</span></span>

- [<span data-ttu-id="ad3e2-110">.NET Core 'daki kırılmaya karşı değişiklikleri değerlendir</span><span class="sxs-lookup"><span data-stu-id="ad3e2-110">Evaluate breaking changes in .NET Core</span></span>](../compatibility/index.md)
- [<span data-ttu-id="ad3e2-111">Windows Forms (.NET Core 'dan .NET Core 'a) son değişiklikler</span><span class="sxs-lookup"><span data-stu-id="ad3e2-111">Breaking changes in Windows Forms (.NET Core to .NET Core)</span></span>](../compatibility/winforms.md)
