---
title: Standart Denetimler İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 314526c1164f70e6b261df1a6f11ddce2b5fa240
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960069"
---
# <a name="ui-automation-support-for-standard-controls"></a><span data-ttu-id="5d00c-102">Standart Denetimler İçin UI Otomasyon Desteği</span><span class="sxs-lookup"><span data-stu-id="5d00c-102">UI Automation Support for Standard Controls</span></span>
> [!NOTE]
> <span data-ttu-id="5d00c-103">Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="5d00c-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5d00c-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="5d00c-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="5d00c-105">Bu konu, [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]ve [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] çerçeveleri için geliştirilen uygulamalardaki standart denetimler için [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] desteği hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="5d00c-105">This topic contains information about [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] support for standard controls in applications developed for the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], and [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] frameworks.</span></span>  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a><span data-ttu-id="5d00c-106">Windows Presentation Foundation denetimleri</span><span class="sxs-lookup"><span data-stu-id="5d00c-106">Windows Presentation Foundation Controls</span></span>  
 <span data-ttu-id="5d00c-107">Kullanıcı etkileşimi için bilgi veya destek sağlayan tüm [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] denetim öğelerinin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]tam yerel desteği vardır.</span><span class="sxs-lookup"><span data-stu-id="5d00c-107">All [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] control elements that provide information or support for user interaction have full native support for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="5d00c-108">Paneller gibi diğer öğeler [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]görünmüyor.</span><span class="sxs-lookup"><span data-stu-id="5d00c-108">Other elements, such as panels, are not visible to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span>  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a><span data-ttu-id="5d00c-109">Win32 denetimleri</span><span class="sxs-lookup"><span data-stu-id="5d00c-109">Win32 Controls</span></span>  
 <span data-ttu-id="5d00c-110">[!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] denetimlerinin çoğu, UIAutomationClientsideProviders. dll içindeki istemci tarafı sağlayıcılar aracılığıyla [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kullanıma sunulur.</span><span class="sxs-lookup"><span data-stu-id="5d00c-110">Most [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="5d00c-111">Bu derleme, UI Otomasyonu istemci uygulamalarıyla kullanılmak üzere otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="5d00c-111">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="5d00c-112">Tam destek yalnızca *ComCtrl32. dll*sürüm 6 ' dan denetimler için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="5d00c-112">Full support is provided only for controls from version 6 of *ComCtrl32.dll*.</span></span>  
  
 <span data-ttu-id="5d00c-113">Aşağıdaki denetimler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5d00c-113">The following controls are supported.</span></span>  
  
|<span data-ttu-id="5d00c-114">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="5d00c-114">Class name</span></span>|<span data-ttu-id="5d00c-115">Kontrol Türü</span><span class="sxs-lookup"><span data-stu-id="5d00c-115">Control Type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="5d00c-116">Düğme</span><span class="sxs-lookup"><span data-stu-id="5d00c-116">Button</span></span>|<span data-ttu-id="5d00c-117">Düğme</span><span class="sxs-lookup"><span data-stu-id="5d00c-117">Button</span></span>|  
|<span data-ttu-id="5d00c-118">Düğme</span><span class="sxs-lookup"><span data-stu-id="5d00c-118">Button</span></span>|<span data-ttu-id="5d00c-119">RadioButton</span><span class="sxs-lookup"><span data-stu-id="5d00c-119">RadioButton</span></span>|  
|<span data-ttu-id="5d00c-120">Düğme</span><span class="sxs-lookup"><span data-stu-id="5d00c-120">Button</span></span>|<span data-ttu-id="5d00c-121">Grup</span><span class="sxs-lookup"><span data-stu-id="5d00c-121">Group</span></span>|  
|<span data-ttu-id="5d00c-122">Düğme</span><span class="sxs-lookup"><span data-stu-id="5d00c-122">Button</span></span>|<span data-ttu-id="5d00c-123">CheckBox</span><span class="sxs-lookup"><span data-stu-id="5d00c-123">CheckBox</span></span>|  
|<span data-ttu-id="5d00c-124">Düğme</span><span class="sxs-lookup"><span data-stu-id="5d00c-124">Button</span></span>|<span data-ttu-id="5d00c-125">Köprü</span><span class="sxs-lookup"><span data-stu-id="5d00c-125">Hyperlink</span></span>|  
|<span data-ttu-id="5d00c-126">Düğme</span><span class="sxs-lookup"><span data-stu-id="5d00c-126">Button</span></span>|<span data-ttu-id="5d00c-127">SplitButton</span><span class="sxs-lookup"><span data-stu-id="5d00c-127">SplitButton</span></span>|  
|<span data-ttu-id="5d00c-128">Düğme</span><span class="sxs-lookup"><span data-stu-id="5d00c-128">Button</span></span>|<span data-ttu-id="5d00c-129">CheckBox</span><span class="sxs-lookup"><span data-stu-id="5d00c-129">CheckBox</span></span>|  
|<span data-ttu-id="5d00c-130">ComboBoxEx32</span><span class="sxs-lookup"><span data-stu-id="5d00c-130">ComboBoxEx32</span></span>|<span data-ttu-id="5d00c-131">ComboBox</span><span class="sxs-lookup"><span data-stu-id="5d00c-131">ComboBox</span></span>|  
|<span data-ttu-id="5d00c-132">ComboBox</span><span class="sxs-lookup"><span data-stu-id="5d00c-132">ComboBox</span></span>|<span data-ttu-id="5d00c-133">ComboBox</span><span class="sxs-lookup"><span data-stu-id="5d00c-133">ComboBox</span></span>|  
|<span data-ttu-id="5d00c-134">Düzenle</span><span class="sxs-lookup"><span data-stu-id="5d00c-134">Edit</span></span>|<span data-ttu-id="5d00c-135">Belge</span><span class="sxs-lookup"><span data-stu-id="5d00c-135">Document</span></span>|  
|<span data-ttu-id="5d00c-136">Düzenle</span><span class="sxs-lookup"><span data-stu-id="5d00c-136">Edit</span></span>|<span data-ttu-id="5d00c-137">Düzenle</span><span class="sxs-lookup"><span data-stu-id="5d00c-137">Edit</span></span>|  
|<span data-ttu-id="5d00c-138">SysLink</span><span class="sxs-lookup"><span data-stu-id="5d00c-138">SysLink</span></span>|<span data-ttu-id="5d00c-139">Köprü</span><span class="sxs-lookup"><span data-stu-id="5d00c-139">Hyperlink</span></span>|  
|<span data-ttu-id="5d00c-140">Statik</span><span class="sxs-lookup"><span data-stu-id="5d00c-140">Static</span></span>|<span data-ttu-id="5d00c-141">Metin</span><span class="sxs-lookup"><span data-stu-id="5d00c-141">Text</span></span>|  
|<span data-ttu-id="5d00c-142">Statik</span><span class="sxs-lookup"><span data-stu-id="5d00c-142">Static</span></span>|<span data-ttu-id="5d00c-143">Görüntü</span><span class="sxs-lookup"><span data-stu-id="5d00c-143">Image</span></span>|  
|<span data-ttu-id="5d00c-144">SysIPAddress32</span><span class="sxs-lookup"><span data-stu-id="5d00c-144">SysIPAddress32</span></span>|<span data-ttu-id="5d00c-145">Özel</span><span class="sxs-lookup"><span data-stu-id="5d00c-145">Custom</span></span>|  
|<span data-ttu-id="5d00c-146">SysHeader32</span><span class="sxs-lookup"><span data-stu-id="5d00c-146">SysHeader32</span></span>|<span data-ttu-id="5d00c-147">Üstbilgi/HeaderItem</span><span class="sxs-lookup"><span data-stu-id="5d00c-147">Header/HeaderItem</span></span>|  
|<span data-ttu-id="5d00c-148">SysListView32</span><span class="sxs-lookup"><span data-stu-id="5d00c-148">SysListView32</span></span>|<span data-ttu-id="5d00c-149">DataGrid</span><span class="sxs-lookup"><span data-stu-id="5d00c-149">DataGrid</span></span>|  
|<span data-ttu-id="5d00c-150">SysListView32</span><span class="sxs-lookup"><span data-stu-id="5d00c-150">SysListView32</span></span>|<span data-ttu-id="5d00c-151">List</span><span class="sxs-lookup"><span data-stu-id="5d00c-151">List</span></span>|  
|<span data-ttu-id="5d00c-152">ListBox</span><span class="sxs-lookup"><span data-stu-id="5d00c-152">ListBox</span></span>|<span data-ttu-id="5d00c-153">List</span><span class="sxs-lookup"><span data-stu-id="5d00c-153">List</span></span>|  
|<span data-ttu-id="5d00c-154">ListBox</span><span class="sxs-lookup"><span data-stu-id="5d00c-154">ListBox</span></span>|<span data-ttu-id="5d00c-155">Liste</span><span class="sxs-lookup"><span data-stu-id="5d00c-155">ListItem</span></span>|  
|<span data-ttu-id="5d00c-156">#32768</span><span class="sxs-lookup"><span data-stu-id="5d00c-156">#32768</span></span>|<span data-ttu-id="5d00c-157">Menü</span><span class="sxs-lookup"><span data-stu-id="5d00c-157">Menu</span></span>|  
|<span data-ttu-id="5d00c-158">#32768</span><span class="sxs-lookup"><span data-stu-id="5d00c-158">#32768</span></span>|<span data-ttu-id="5d00c-159">MenuItem</span><span class="sxs-lookup"><span data-stu-id="5d00c-159">MenuItem</span></span>|  
|<span data-ttu-id="5d00c-160">msctls_progress32</span><span class="sxs-lookup"><span data-stu-id="5d00c-160">msctls_progress32</span></span>|<span data-ttu-id="5d00c-161">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="5d00c-161">ProgressBar</span></span>|  
|<span data-ttu-id="5d00c-162">RichEdit</span><span class="sxs-lookup"><span data-stu-id="5d00c-162">RichEdit</span></span>|<span data-ttu-id="5d00c-163">Belgedeki.</span><span class="sxs-lookup"><span data-stu-id="5d00c-163">Document.</span></span> <span data-ttu-id="5d00c-164">Bkz. Note.</span><span class="sxs-lookup"><span data-stu-id="5d00c-164">See note.</span></span>|  
|<span data-ttu-id="5d00c-165">RichEdit20A</span><span class="sxs-lookup"><span data-stu-id="5d00c-165">RichEdit20A</span></span>|<span data-ttu-id="5d00c-166">Belge</span><span class="sxs-lookup"><span data-stu-id="5d00c-166">Document</span></span>|  
|<span data-ttu-id="5d00c-167">RichEdit20W</span><span class="sxs-lookup"><span data-stu-id="5d00c-167">RichEdit20W</span></span>|<span data-ttu-id="5d00c-168">Belge</span><span class="sxs-lookup"><span data-stu-id="5d00c-168">Document</span></span>|  
|<span data-ttu-id="5d00c-169">RichEdit50W</span><span class="sxs-lookup"><span data-stu-id="5d00c-169">RichEdit50W</span></span>|<span data-ttu-id="5d00c-170">Belge</span><span class="sxs-lookup"><span data-stu-id="5d00c-170">Document</span></span>|  
|<span data-ttu-id="5d00c-171">ScrollBar</span><span class="sxs-lookup"><span data-stu-id="5d00c-171">ScrollBar</span></span>|<span data-ttu-id="5d00c-172">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="5d00c-172">Slider</span></span>|  
|<span data-ttu-id="5d00c-173">msctls_trackbar32</span><span class="sxs-lookup"><span data-stu-id="5d00c-173">msctls_trackbar32</span></span>|<span data-ttu-id="5d00c-174">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="5d00c-174">Slider</span></span>|  
|<span data-ttu-id="5d00c-175">msctls_updown32</span><span class="sxs-lookup"><span data-stu-id="5d00c-175">msctls_updown32</span></span>|<span data-ttu-id="5d00c-176">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="5d00c-176">Spinner</span></span>|  
|<span data-ttu-id="5d00c-177">msctls_statusbar32</span><span class="sxs-lookup"><span data-stu-id="5d00c-177">msctls_statusbar32</span></span>|<span data-ttu-id="5d00c-178">StatusBar</span><span class="sxs-lookup"><span data-stu-id="5d00c-178">StatusBar</span></span>|  
|<span data-ttu-id="5d00c-179">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="5d00c-179">SysTabControl32</span></span>|<span data-ttu-id="5d00c-180">Tab</span><span class="sxs-lookup"><span data-stu-id="5d00c-180">Tab</span></span>|  
|<span data-ttu-id="5d00c-181">SysTabControl32</span><span class="sxs-lookup"><span data-stu-id="5d00c-181">SysTabControl32</span></span>|<span data-ttu-id="5d00c-182">TabItem</span><span class="sxs-lookup"><span data-stu-id="5d00c-182">TabItem</span></span>|  
|<span data-ttu-id="5d00c-183">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="5d00c-183">ToolbarWindow32</span></span>|<span data-ttu-id="5d00c-184">ToolBar</span><span class="sxs-lookup"><span data-stu-id="5d00c-184">ToolBar</span></span>|  
|<span data-ttu-id="5d00c-185">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="5d00c-185">ToolbarWindow32</span></span>|<span data-ttu-id="5d00c-186">MenuItem</span><span class="sxs-lookup"><span data-stu-id="5d00c-186">MenuItem</span></span>|  
|<span data-ttu-id="5d00c-187">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="5d00c-187">ToolbarWindow32</span></span>|<span data-ttu-id="5d00c-188">Düğme</span><span class="sxs-lookup"><span data-stu-id="5d00c-188">Button</span></span>|  
|<span data-ttu-id="5d00c-189">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="5d00c-189">ToolbarWindow32</span></span>|<span data-ttu-id="5d00c-190">CheckBox</span><span class="sxs-lookup"><span data-stu-id="5d00c-190">CheckBox</span></span>|  
|<span data-ttu-id="5d00c-191">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="5d00c-191">ToolbarWindow32</span></span>|<span data-ttu-id="5d00c-192">RadioButton</span><span class="sxs-lookup"><span data-stu-id="5d00c-192">RadioButton</span></span>|  
|<span data-ttu-id="5d00c-193">ToolbarWindow32</span><span class="sxs-lookup"><span data-stu-id="5d00c-193">ToolbarWindow32</span></span>|<span data-ttu-id="5d00c-194">Ayırıcı</span><span class="sxs-lookup"><span data-stu-id="5d00c-194">Separator</span></span>|  
|<span data-ttu-id="5d00c-195">tooltips_class32</span><span class="sxs-lookup"><span data-stu-id="5d00c-195">tooltips_class32</span></span>|<span data-ttu-id="5d00c-196">ToolTip</span><span class="sxs-lookup"><span data-stu-id="5d00c-196">ToolTip</span></span>|  
|<span data-ttu-id="5d00c-197">#32774</span><span class="sxs-lookup"><span data-stu-id="5d00c-197">#32774</span></span>|<span data-ttu-id="5d00c-198">ToolTip</span><span class="sxs-lookup"><span data-stu-id="5d00c-198">ToolTip</span></span>|  
|<span data-ttu-id="5d00c-199">ReBarWindow32</span><span class="sxs-lookup"><span data-stu-id="5d00c-199">ReBarWindow32</span></span>|<span data-ttu-id="5d00c-200">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="5d00c-200">Toolbar</span></span>|  
|<span data-ttu-id="5d00c-201">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="5d00c-201">SysTreeView32</span></span>|<span data-ttu-id="5d00c-202">Ağaç</span><span class="sxs-lookup"><span data-stu-id="5d00c-202">Tree</span></span>|  
|<span data-ttu-id="5d00c-203">SysTreeView32</span><span class="sxs-lookup"><span data-stu-id="5d00c-203">SysTreeView32</span></span>|<span data-ttu-id="5d00c-204">TreeItem</span><span class="sxs-lookup"><span data-stu-id="5d00c-204">TreeItem</span></span>|  
  
 <span data-ttu-id="5d00c-205">**Göz önünde** RichEdit denetimi yalnızca Windows Vista ile birlikte gelen sürümler için desteklenir (RichEd20. dll sürümü 3,1 ve üzeri ve MsftEdit. dll sürüm 4,1 ve üzeri).</span><span class="sxs-lookup"><span data-stu-id="5d00c-205">**Note** The RichEdit control is supported only for versions shipped with Windows Vista (in RichEd20.dll version 3.1 and later, and MsftEdit.dll version 4.1 and later).</span></span>  
  
 <span data-ttu-id="5d00c-206">Aşağıdaki denetimler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="5d00c-206">The following controls are not supported.</span></span>  
  
|<span data-ttu-id="5d00c-207">Sınıf adı</span><span class="sxs-lookup"><span data-stu-id="5d00c-207">Class name</span></span>|<span data-ttu-id="5d00c-208">Denetim türü</span><span class="sxs-lookup"><span data-stu-id="5d00c-208">Control type</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="5d00c-209">SysAnimate32</span><span class="sxs-lookup"><span data-stu-id="5d00c-209">SysAnimate32</span></span>|<span data-ttu-id="5d00c-210">Görüntü</span><span class="sxs-lookup"><span data-stu-id="5d00c-210">Image</span></span>|  
|<span data-ttu-id="5d00c-211">SysPager</span><span class="sxs-lookup"><span data-stu-id="5d00c-211">SysPager</span></span>|<span data-ttu-id="5d00c-212">Değer Değiştirici</span><span class="sxs-lookup"><span data-stu-id="5d00c-212">Spinner</span></span>|  
|<span data-ttu-id="5d00c-213">SysDateTimePick32</span><span class="sxs-lookup"><span data-stu-id="5d00c-213">SysDateTimePick32</span></span>|<span data-ttu-id="5d00c-214">Özel</span><span class="sxs-lookup"><span data-stu-id="5d00c-214">Custom</span></span>|  
|<span data-ttu-id="5d00c-215">SysMonthCal32</span><span class="sxs-lookup"><span data-stu-id="5d00c-215">SysMonthCal32</span></span>|<span data-ttu-id="5d00c-216">Takvim</span><span class="sxs-lookup"><span data-stu-id="5d00c-216">Calendar</span></span>|  
|<span data-ttu-id="5d00c-217">MS_WINNOTE</span><span class="sxs-lookup"><span data-stu-id="5d00c-217">MS_WINNOTE</span></span>|<span data-ttu-id="5d00c-218">Araç ipucu</span><span class="sxs-lookup"><span data-stu-id="5d00c-218">Tooltip</span></span>|  
|<span data-ttu-id="5d00c-219">Vbkabarcık</span><span class="sxs-lookup"><span data-stu-id="5d00c-219">VBBubble</span></span>|<span data-ttu-id="5d00c-220">Araç ipucu</span><span class="sxs-lookup"><span data-stu-id="5d00c-220">Tooltip</span></span>|  
|<span data-ttu-id="5d00c-221">Kaydırma çubuğu (tek başına denetim olarak kullanıldığında)</span><span class="sxs-lookup"><span data-stu-id="5d00c-221">ScrollBar (when used as a standalone control)</span></span>|<span data-ttu-id="5d00c-222">Kaydırıcı</span><span class="sxs-lookup"><span data-stu-id="5d00c-222">Slider</span></span>|  
|<span data-ttu-id="5d00c-223">SuperGrid</span><span class="sxs-lookup"><span data-stu-id="5d00c-223">SuperGrid</span></span>|<span data-ttu-id="5d00c-224">Özel</span><span class="sxs-lookup"><span data-stu-id="5d00c-224">Custom</span></span>|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a><span data-ttu-id="5d00c-225">Windows Forms Denetimleri</span><span class="sxs-lookup"><span data-stu-id="5d00c-225">Windows Forms Controls</span></span>  
 <span data-ttu-id="5d00c-226">Windows Forms denetimleri, UIAutomationClientsideProviders. dll içindeki istemci tarafı sağlayıcılar aracılığıyla [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kullanıma sunulur.</span><span class="sxs-lookup"><span data-stu-id="5d00c-226">Windows Forms controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] through client-side providers in UIAutomationClientsideProviders.dll.</span></span> <span data-ttu-id="5d00c-227">Bu derleme, UI Otomasyonu istemci uygulamalarıyla kullanılmak üzere otomatik olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="5d00c-227">This assembly is automatically registered for use with UI Automation client applications.</span></span>  
  
 <span data-ttu-id="5d00c-228">Genellikle, [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ortak denetimleri için yönetilen sarmalayıcılarla Windows Forms denetimler [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5d00c-228">Typically, Windows Forms controls that are managed wrappers for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] common controls are supported by [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].</span></span> <span data-ttu-id="5d00c-229">Aşağıdaki denetimler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5d00c-229">The following controls are supported.</span></span>  
  
|<span data-ttu-id="5d00c-230">Sınıf Adı</span><span class="sxs-lookup"><span data-stu-id="5d00c-230">Class Name</span></span>|  
|----------------|  
|<span data-ttu-id="5d00c-231">Düğme</span><span class="sxs-lookup"><span data-stu-id="5d00c-231">Button</span></span>|  
|<span data-ttu-id="5d00c-232">CheckBox</span><span class="sxs-lookup"><span data-stu-id="5d00c-232">CheckBox</span></span>|  
|<span data-ttu-id="5d00c-233">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="5d00c-233">CheckedListBox</span></span>|  
|<span data-ttu-id="5d00c-234">ColorDialog</span><span class="sxs-lookup"><span data-stu-id="5d00c-234">ColorDialog</span></span>|  
|<span data-ttu-id="5d00c-235">ComboBox</span><span class="sxs-lookup"><span data-stu-id="5d00c-235">ComboBox</span></span>|  
|<span data-ttu-id="5d00c-236">FolderBrowser</span><span class="sxs-lookup"><span data-stu-id="5d00c-236">FolderBrowser</span></span>|  
|<span data-ttu-id="5d00c-237">FontDialog</span><span class="sxs-lookup"><span data-stu-id="5d00c-237">FontDialog</span></span>|  
|<span data-ttu-id="5d00c-238">GroupBox</span><span class="sxs-lookup"><span data-stu-id="5d00c-238">GroupBox</span></span>|  
|<span data-ttu-id="5d00c-239">HscrollBar</span><span class="sxs-lookup"><span data-stu-id="5d00c-239">HscrollBar</span></span>|  
|<span data-ttu-id="5d00c-240">'I</span><span class="sxs-lookup"><span data-stu-id="5d00c-240">ImageList</span></span>|  
|<span data-ttu-id="5d00c-241">Etiketle</span><span class="sxs-lookup"><span data-stu-id="5d00c-241">Label</span></span>|  
|<span data-ttu-id="5d00c-242">ListBox</span><span class="sxs-lookup"><span data-stu-id="5d00c-242">ListBox</span></span>|  
|<span data-ttu-id="5d00c-243">ListView</span><span class="sxs-lookup"><span data-stu-id="5d00c-243">ListView</span></span>|  
|<span data-ttu-id="5d00c-244">MainMenu/ContextMenu</span><span class="sxs-lookup"><span data-stu-id="5d00c-244">MainMenu/ContextMenu</span></span>|  
|<span data-ttu-id="5d00c-245">MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="5d00c-245">MonthCalendar</span></span>|  
|<span data-ttu-id="5d00c-246">NotifyIcon</span><span class="sxs-lookup"><span data-stu-id="5d00c-246">NotifyIcon</span></span>|  
|<span data-ttu-id="5d00c-247">OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="5d00c-247">OpenFileDialog</span></span>|  
|<span data-ttu-id="5d00c-248">PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="5d00c-248">PageSetupDialog</span></span>|  
|<span data-ttu-id="5d00c-249">PrintDialog</span><span class="sxs-lookup"><span data-stu-id="5d00c-249">PrintDialog</span></span>|  
|<span data-ttu-id="5d00c-250">ProgressBar</span><span class="sxs-lookup"><span data-stu-id="5d00c-250">ProgressBar</span></span>|  
|<span data-ttu-id="5d00c-251">RadioButton</span><span class="sxs-lookup"><span data-stu-id="5d00c-251">RadioButton</span></span>|  
|<span data-ttu-id="5d00c-252">RichTextBox</span><span class="sxs-lookup"><span data-stu-id="5d00c-252">RichTextBox</span></span>|  
|<span data-ttu-id="5d00c-253">SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="5d00c-253">SaveFileDialog</span></span>|  
|<span data-ttu-id="5d00c-254">ScrollableControl</span><span class="sxs-lookup"><span data-stu-id="5d00c-254">ScrollableControl</span></span>|  
|<span data-ttu-id="5d00c-255">SoundPlayer</span><span class="sxs-lookup"><span data-stu-id="5d00c-255">SoundPlayer</span></span>|  
|<span data-ttu-id="5d00c-256">StatusBar</span><span class="sxs-lookup"><span data-stu-id="5d00c-256">StatusBar</span></span>|  
|<span data-ttu-id="5d00c-257">TabControl/TabPage</span><span class="sxs-lookup"><span data-stu-id="5d00c-257">TabControl/TabPage</span></span>|  
|<span data-ttu-id="5d00c-258">TextBox</span><span class="sxs-lookup"><span data-stu-id="5d00c-258">TextBox</span></span>|  
|<span data-ttu-id="5d00c-259">Zamanlayıcı</span><span class="sxs-lookup"><span data-stu-id="5d00c-259">Timer</span></span>|  
|<span data-ttu-id="5d00c-260">Araç Çubuğu</span><span class="sxs-lookup"><span data-stu-id="5d00c-260">Toolbar</span></span>|  
|<span data-ttu-id="5d00c-261">ToolTip</span><span class="sxs-lookup"><span data-stu-id="5d00c-261">ToolTip</span></span>|  
|<span data-ttu-id="5d00c-262">TrackBar</span><span class="sxs-lookup"><span data-stu-id="5d00c-262">TrackBar</span></span>|  
|<span data-ttu-id="5d00c-263">TreeView</span><span class="sxs-lookup"><span data-stu-id="5d00c-263">TreeView</span></span>|  
|<span data-ttu-id="5d00c-264">VscrollBar</span><span class="sxs-lookup"><span data-stu-id="5d00c-264">VscrollBar</span></span>|  
|<span data-ttu-id="5d00c-265">'A</span><span class="sxs-lookup"><span data-stu-id="5d00c-265">WebBrowser</span></span>|  
  
 <span data-ttu-id="5d00c-266">Aşağıdaki denetimler yalnızca Microsoft Etkin Erişilebilirlik desteğiyle [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] açıktır.</span><span class="sxs-lookup"><span data-stu-id="5d00c-266">The following controls are exposed to [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] only through their support for Microsoft Active Accessibility.</span></span> <span data-ttu-id="5d00c-267">Bazı işlevler kullanılamayabilir.</span><span class="sxs-lookup"><span data-stu-id="5d00c-267">Some functionality may not be available.</span></span>  
  
|<span data-ttu-id="5d00c-268">Denetim Adı</span><span class="sxs-lookup"><span data-stu-id="5d00c-268">Control Name</span></span>|  
|------------------|  
|<span data-ttu-id="5d00c-269">BindingSource</span><span class="sxs-lookup"><span data-stu-id="5d00c-269">BindingSource</span></span>|  
|<span data-ttu-id="5d00c-270">DataGrid</span><span class="sxs-lookup"><span data-stu-id="5d00c-270">DataGrid</span></span>|  
|<span data-ttu-id="5d00c-271">DataGridView</span><span class="sxs-lookup"><span data-stu-id="5d00c-271">DataGridView</span></span>|  
|<span data-ttu-id="5d00c-272">DataNavigator</span><span class="sxs-lookup"><span data-stu-id="5d00c-272">DataNavigator</span></span>|  
|<span data-ttu-id="5d00c-273">DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="5d00c-273">DomainUpDown</span></span>|  
|<span data-ttu-id="5d00c-274">Bileþeni</span><span class="sxs-lookup"><span data-stu-id="5d00c-274">ErrorProvider</span></span>|  
|<span data-ttu-id="5d00c-275">FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="5d00c-275">FlowLayoutPanel</span></span>|  
|<span data-ttu-id="5d00c-276">Form</span><span class="sxs-lookup"><span data-stu-id="5d00c-276">Form</span></span>|  
|<span data-ttu-id="5d00c-277">LinkLabel</span><span class="sxs-lookup"><span data-stu-id="5d00c-277">LinkLabel</span></span>|  
|<span data-ttu-id="5d00c-278">HelpProvider</span><span class="sxs-lookup"><span data-stu-id="5d00c-278">HelpProvider</span></span>|  
|<span data-ttu-id="5d00c-279">MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="5d00c-279">MaskedTextBox</span></span>|  
|<span data-ttu-id="5d00c-280">MenuStrip/ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="5d00c-280">MenuStrip/ContextMenuStrip</span></span>|  
|<span data-ttu-id="5d00c-281">NumericUpDown</span><span class="sxs-lookup"><span data-stu-id="5d00c-281">NumericUpDown</span></span>|  
|<span data-ttu-id="5d00c-282">Panel</span><span class="sxs-lookup"><span data-stu-id="5d00c-282">Panel</span></span>|  
|<span data-ttu-id="5d00c-283">PictureBox</span><span class="sxs-lookup"><span data-stu-id="5d00c-283">PictureBox</span></span>|  
|<span data-ttu-id="5d00c-284">Öniz</span><span class="sxs-lookup"><span data-stu-id="5d00c-284">PrintDocument</span></span>|  
|<span data-ttu-id="5d00c-285">PrintPreview-denetim</span><span class="sxs-lookup"><span data-stu-id="5d00c-285">PrintPreview-Control</span></span>|  
|<span data-ttu-id="5d00c-286">PrintPreview-Iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="5d00c-286">PrintPreview-Dialog</span></span>|  
|<span data-ttu-id="5d00c-287">'In</span><span class="sxs-lookup"><span data-stu-id="5d00c-287">PropertyGrid</span></span>|  
|<span data-ttu-id="5d00c-288">UserControl</span><span class="sxs-lookup"><span data-stu-id="5d00c-288">UserControl</span></span>|  
|<span data-ttu-id="5d00c-289">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="5d00c-289">ToolStrip</span></span>|  
|<span data-ttu-id="5d00c-290">Ekleyecek</span><span class="sxs-lookup"><span data-stu-id="5d00c-290">TableLayoutPanel</span></span>|  
|<span data-ttu-id="5d00c-291">SplitContainer/SplitterPanel</span><span class="sxs-lookup"><span data-stu-id="5d00c-291">SplitContainer/SplitterPanel</span></span>|  
|<span data-ttu-id="5d00c-292">Bölümlendirici</span><span class="sxs-lookup"><span data-stu-id="5d00c-292">Splitter</span></span>|  
|<span data-ttu-id="5d00c-293">RaftingContainer</span><span class="sxs-lookup"><span data-stu-id="5d00c-293">RaftingContainer</span></span>|  
|<span data-ttu-id="5d00c-294">StatusStrip</span><span class="sxs-lookup"><span data-stu-id="5d00c-294">StatusStrip</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5d00c-295">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d00c-295">See also</span></span>

- [<span data-ttu-id="5d00c-296">UI Otomasyonu Denetim Türleri</span><span class="sxs-lookup"><span data-stu-id="5d00c-296">UI Automation Control Types</span></span>](ui-automation-control-types.md)
