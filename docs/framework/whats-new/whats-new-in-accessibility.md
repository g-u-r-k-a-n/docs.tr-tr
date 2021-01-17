---
title: .NET Framework erişilebilirlik yenilikleri
titleSuffix: ''
description: .NET Framework 4.7.1 ile başlayarak .NET erişilebilirlik yenilikleri bölümüne bakın. Erişilebilirlik özellikleri, bir uygulamanın yardımcı teknoloji kullanıcıları için doğru deneyimi sağlamasına imkan tanır.
ms.date: 01/05/2021
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.openlocfilehash: c2ebaed8bf347eb8d8764f4bdf76dcc33db86bad
ms.sourcegitcommit: 3a8f1979a98c6c19217a1930e0af5908988eb8ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2021
ms.locfileid: "98536170"
---
# <a name="whats-new-in-accessibility-in-net-framework"></a><span data-ttu-id="72c76-104">.NET Framework erişilebilirlik yenilikleri</span><span class="sxs-lookup"><span data-stu-id="72c76-104">What's new in accessibility in .NET Framework</span></span>

<span data-ttu-id="72c76-105">Kullanıcılarınızın kullanıcılarınız için daha erişilebilir olmasını sağlamak için amaçlar .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="72c76-105">.NET Framework aims to make applications more accessible for your users.</span></span> <span data-ttu-id="72c76-106">Erişilebilirlik özellikleri, bir uygulamanın yardımcı teknoloji kullanıcıları için uygun bir deneyim sağlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="72c76-106">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="72c76-107">.NET Framework 4.7.1 ile başlayarak .NET Framework, geliştiricilerin erişilebilir uygulamalar oluşturmalarına izin veren çok sayıda erişilebilirlik geliştirmesi de vardır.</span><span class="sxs-lookup"><span data-stu-id="72c76-107">Starting with .NET Framework 4.7.1, .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span>

## <a name="accessibility-switches"></a><span data-ttu-id="72c76-108">Erişilebilirlik anahtarları</span><span class="sxs-lookup"><span data-stu-id="72c76-108">Accessibility switches</span></span>

<span data-ttu-id="72c76-109">Uygulamanızı, .NET Framework 4,7 veya önceki bir sürümü hedefliyorsa ancak .NET Framework 4.7.1 veya üzeri sürümlerde çalışıyorsa erişilebilirlik özelliklerini kabul etmek üzere yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72c76-109">You can configure your app to opt into accessibility features if it targets .NET Framework 4.7 or an earlier version but is running on .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="72c76-110">Ayrıca, .NET Framework 4.7.1 veya üstünü hedeflerse, uygulamanızı eski özellikleri (ve erişilebilirlik özelliklerinden faydalanmaz) kullanacak şekilde de yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72c76-110">You can also configure your app to use legacy features (and not take advantage of accessibility features) if it targets .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="72c76-111">Erişilebilirlik özelliklerini içeren her bir .NET Framework sürümü, [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) [`<runtime>`](../configure-apps/file-schema/runtime/index.md) uygulamanın yapılandırma dosyasının bölümündeki öğesine eklediğiniz sürüme özgü bir erişilebilirlik anahtarına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="72c76-111">Each .NET Framework version that includes accessibility features has a version-specific accessibility switch, which you add to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> <span data-ttu-id="72c76-112">Aşağıdakiler desteklenen anahtarlardır:</span><span class="sxs-lookup"><span data-stu-id="72c76-112">The following are the supported switches:</span></span>

|<span data-ttu-id="72c76-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="72c76-113">Version</span></span>|<span data-ttu-id="72c76-114">Anahtar</span><span class="sxs-lookup"><span data-stu-id="72c76-114">Switch</span></span>|
|---|---|
|<span data-ttu-id="72c76-115">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="72c76-115">.NET Framework 4.7.1</span></span>|<span data-ttu-id="72c76-116">"Switch. UseLegacyAccessibilityFeatures"</span><span class="sxs-lookup"><span data-stu-id="72c76-116">"Switch.UseLegacyAccessibilityFeatures"</span></span>|
|<span data-ttu-id="72c76-117"> .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="72c76-117">.NET Framework 4.7.2</span></span>|<span data-ttu-id="72c76-118">"Switch. UseLegacyAccessibilityFeatures. 2"</span><span class="sxs-lookup"><span data-stu-id="72c76-118">"Switch.UseLegacyAccessibilityFeatures.2"</span></span>|
|<span data-ttu-id="72c76-119"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="72c76-119">.NET Framework 4.8</span></span>|<span data-ttu-id="72c76-120">"Switch. UseLegacyAccessibilityFeatures. 3"</span><span class="sxs-lookup"><span data-stu-id="72c76-120">"Switch.UseLegacyAccessibilityFeatures.3"</span></span>|
|<span data-ttu-id="72c76-121">11 Ağustos 2020-KB4569746 .NET Framework 4,8 toplu güncelleştirmesi</span><span class="sxs-lookup"><span data-stu-id="72c76-121">August 11, 2020-KB4569746 Cumulative Update for .NET Framework 4.8</span></span>|<span data-ttu-id="72c76-122">"Switch. UseLegacyAccessibilityFeatures. 4"</span><span class="sxs-lookup"><span data-stu-id="72c76-122">"Switch.UseLegacyAccessibilityFeatures.4"</span></span>|

### <a name="taking-advantage-of-accessibility-enhancements"></a><span data-ttu-id="72c76-123">Erişilebilirlik geliştirmelerinden yararlanma</span><span class="sxs-lookup"><span data-stu-id="72c76-123">Taking advantage of accessibility enhancements</span></span>

<span data-ttu-id="72c76-124">Yeni erişilebilirlik özellikleri, .NET Framework 4.7.1 veya üstünü hedefleyen uygulamalar için varsayılan olarak etkinleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="72c76-124">The new accessibility features are enabled by default for applications that target .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="72c76-125">Ayrıca, .NET Framework önceki bir sürümünü hedefleyen, ancak .NET Framework 4.7.1 veya üzeri sürümlerde çalışan uygulamalar, [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) [`<runtime>`](../configure-apps/file-schema/runtime/index.md) uygulamanın yapılandırma dosyasının bölümündeki öğeye anahtar ekleyerek ve değerlerini olarak ayarlayarak eski erişilebilirlik davranışlarını (ve dolayısıyla erişilebilirlik geliştirmelerinden faydalanabilir) devre dışı bırakabilirsiniz `false` .</span><span class="sxs-lookup"><span data-stu-id="72c76-125">In addition, applications that target an earlier version of the .NET Framework but are running on .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby take advantage of accessibility improvements) by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `false`.</span></span> <span data-ttu-id="72c76-126">Aşağıdaki kod parçacığında, .NET Framework 4.7.1 ' de tanıtılan erişilebilirlik geliştirmelerinin nasıl kabul edildiği gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="72c76-126">The following snippet shows how to opt in to the accessibility enhancements that were introduced in .NET Framework 4.7.1:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="72c76-127">Daha sonraki bir .NET Framework sürümünde erişilebilirlik özelliklerini kullanmayı tercih ederseniz, önceki sürümlerden özellikleri de açıkça kabul etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="72c76-127">If you choose to opt in to accessibility features in a later .NET Framework version, you must also explicitly opt in to the features from earlier versions.</span></span> <span data-ttu-id="72c76-128">Uygulamanızı, hem .NET Framework 4.7.1 hem de 4.7.2 içindeki erişilebilirlik geliştirmelerinden faydalanmak üzere yapılandırmak için aşağıdaki [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğeyi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="72c76-128">To configure your app to take advantage of accessibility improvements in both .NET Framework 4.7.1 and 4.7.2, add the the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

<span data-ttu-id="72c76-129">Uygulamanızı, .NET Framework 4,8 için .NET Framework 4.7.1, 4.7.2, 4,8 ve 2020 Ağustos Toplu Güncelleştirmesi ' nde erişilebilirlik geliştirmelerinden faydalanmak üzere yapılandırmak için aşağıdaki [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğeyi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="72c76-129">To configure your app to take advantage of accessibility improvements in .NET Framework 4.7.1, 4.7.2, 4.8, and the August 2020 cumulative update for .NET Framework 4.8, add the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value=Switch.UseLegacyAccessibilityFeatures=false|Switch.UseLegacyAccessibilityFeatures.2=false|Switch.UseLegacyAccessibilityFeatures.3=false|Switch.UseLegacyAccessibilityFeatures.4=false"/>
</runtime>
```

### <a name="restoring-legacy-behavior"></a><span data-ttu-id="72c76-130">Eski davranışı geri yükleme</span><span class="sxs-lookup"><span data-stu-id="72c76-130">Restoring legacy behavior</span></span>

<span data-ttu-id="72c76-131">4.7.1 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar, [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) [`<runtime>`](../configure-apps/file-schema/runtime/index.md) uygulamanın yapılandırma dosyasının bölümündeki öğesine anahtar ekleyerek ve değerlerini olarak ayarlayarak erişilebilirlik özelliklerini devre dışı bırakabilir `true` .</span><span class="sxs-lookup"><span data-stu-id="72c76-131">Applications that target versions of .NET Framework starting with 4.7.1 can disable accessibility features by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `true`.</span></span> <span data-ttu-id="72c76-132">Örneğin, aşağıdaki yapılandırma .NET Framework 4.7.2 ' de tanıtılan erişilebilirlik özelliklerinden fazlasını giderir:</span><span class="sxs-lookup"><span data-stu-id="72c76-132">For example, the following configuration opts out of accessibility features introduced in .NET Framework 4.7.2:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-august-11-2020-cumulative-update-for-net-framework-48"></a><span data-ttu-id="72c76-133">11 Ağustos 2020 ' de erişilebilirlik yenilikleri, .NET Framework 4,8 için toplu güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="72c76-133">What's new in accessibility in the August 11, 2020 Cumulative Update for .NET Framework 4.8</span></span>

<span data-ttu-id="72c76-134">11 Ağustos 2020-KB4569746 toplu güncelleştirmesi, .NET Framework 4,8 için Windows Forms yeni erişilebilirlik özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="72c76-134">The August 11, 2020-KB4569746 Cumulative Update for .NET Framework 4.8 includes new accessibility features in Windows Forms:</span></span>

- <span data-ttu-id="72c76-135">`PropertyGrid`Ekran okuyucular tarafından denetim öğeleri ve bir kategorinin Genişletilmiş/daraltılmış durumuyla ilgili bir sorun ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="72c76-135">Addresses an issue with announcing `PropertyGrid` control items and a category's expanded/collapsed state by screen readers.</span></span>

- <span data-ttu-id="72c76-136">`PropertyGrid`Denetimin ve iç öğelerinin erişilebilir düzenlerini günceller.</span><span class="sxs-lookup"><span data-stu-id="72c76-136">Updates the accessible patterns of the `PropertyGrid` control and its inner elements.</span></span>

- <span data-ttu-id="72c76-137">Denetim iç öğelerinin erişilebilir adlarını, `PropertyGrid` ekran okuyucular tarafından doğru duyurulacak şekilde güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="72c76-137">Updates the accessible names of the `PropertyGrid` control inner elements so they're correctly announced by screen readers.</span></span>

- <span data-ttu-id="72c76-138">Denetimler için sınırlayıcı dikdörtgende erişilebilir özellikleri adresleyen `PropertyGridView` .</span><span class="sxs-lookup"><span data-stu-id="72c76-138">Addresses bounding rectangle accessible properties for the `PropertyGridView` controls.</span></span>

- <span data-ttu-id="72c76-139">Ekran okuyucularının `DataGridView` Birleşik giriş kutusu hücrelerinin Genişletilmiş/daraltılmış durumunu doğru şekilde duyurmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="72c76-139">Enables screen readers to correctly announce the expanded/collapsed state of `DataGridView` combo box cells.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-48"></a><span data-ttu-id="72c76-140">.NET Framework 4,8 ' de erişilebilirlik yenilikleri</span><span class="sxs-lookup"><span data-stu-id="72c76-140">What's new in accessibility in .NET Framework 4.8</span></span>

<span data-ttu-id="72c76-141">.NET Framework 4,8 aşağıdaki alanlarda yeni erişilebilirlik özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="72c76-141">.NET Framework 4.8 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="72c76-142">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="72c76-142">Windows Forms</span></span>](#winforms48)

- [<span data-ttu-id="72c76-143">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="72c76-143">Windows Presentation Foundation (WPF)</span></span>](#wpf48)

- [<span data-ttu-id="72c76-144">Windows Workflow Foundation (WF) iş akışı Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="72c76-144">Windows Workflow Foundation (WF) workflow designer</span></span>](#wf48)

<a name="winforms48"></a>

### <a name="windows-forms"></a><span data-ttu-id="72c76-145">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="72c76-145">Windows Forms</span></span>

<span data-ttu-id="72c76-146">.NET Framework 4,8 ' de Windows Forms, yaygın olarak kullanılan birçok denetime Ligegions ve Notification olayları için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="72c76-146">In .NET Framework 4.8, Windows Forms adds support for LiveRegions and Notification Events to many commonly used controls.</span></span> <span data-ttu-id="72c76-147">Ayrıca, bir Kullanıcı klavyeyi kullanarak bir denetime gittiğinde araç Ipuçları için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="72c76-147">It also adds support for ToolTips when a user navigates to a control by using the keyboard.</span></span>

<span data-ttu-id="72c76-148">**Etiketler ve Durumlarlar için UııA LiveRegions desteği**</span><span class="sxs-lookup"><span data-stu-id="72c76-148">**UIA LiveRegions Support in Labels and StatusStrips**</span></span>

<span data-ttu-id="72c76-149">UIA Ligegions, uygulama geliştiricilerinin, kullanıcının çalıştığı konumdan ayrı olarak bulunan bir denetimdeki metin değişikliğini ekran okuyucularına bildirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="72c76-149">UIA LiveRegions allow application developers to notify screen readers of a text change in a control that is located apart from the location where the user is working.</span></span> <span data-ttu-id="72c76-150">Bu, örneğin, <xref:System.Windows.Forms.StatusStrip> bağlantı durumunu gösteren bir denetim için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="72c76-150">This is useful, for example, for a <xref:System.Windows.Forms.StatusStrip> control that shows a connection status.</span></span> <span data-ttu-id="72c76-151">Bağlantı bırakılır ve durum değişirse geliştirici, ekran okuyucuyu bilgilendirmek isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-151">If the connection is dropped and the status changes, the developer might want to notify the screen reader.</span></span>

<span data-ttu-id="72c76-152">.NET Framework 4,8 ' den başlayarak, Windows Forms hem hem de denetimleri için UııA LiveRegions uygular <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.StatusStrip> .</span><span class="sxs-lookup"><span data-stu-id="72c76-152">Starting with .NET Framework 4.8, Windows Forms implements UIA LiveRegions for both the <xref:System.Windows.Forms.Label> and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="72c76-153">Örneğin, aşağıdaki kod adlı bir denetimde LiveRegion kullanır <xref:System.Windows.Forms.Label> `label1` :</span><span class="sxs-lookup"><span data-stu-id="72c76-153">For example, the following code uses the LiveRegion in a <xref:System.Windows.Forms.Label> control named `label1`:</span></span>

```csharp
public Form1()
{
   InitializeComponent();
   label1.AutomationLiveSetting = AutomationLiveSetting.Polite;
}

…
Label1.Text = “Ready!”;
```

<span data-ttu-id="72c76-154">Ekran okuyucusu, kullanıcının uygulamayla etkileşime geçen yere bakılmaksızın "Ready" duyurur.</span><span class="sxs-lookup"><span data-stu-id="72c76-154">Narrator announces “Ready” regardless of where the user is interacting with the application.</span></span>

<span data-ttu-id="72c76-155">Ayrıca, hesabınızı <xref:System.Windows.Forms.UserControl> bir LiveRegion olarak da uygulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="72c76-155">You can also implement your <xref:System.Windows.Forms.UserControl> as a LiveRegion:</span></span>

```csharp
using System;
using System.Windows.Forms;
using System.Windows.Forms.Automation;

namespace WindowsFormsApplication
{
   public partial class UserControl1 : UserControl, IAutomationLiveRegion
   {
      public UserControl1()
      {
         InitializeComponent();
      }

      public AutomationLiveSetting AutomationLiveSetting { get; set; }
      private AutomationLiveSetting IAutomationLiveRegion.GetLiveSetting()
      {
         return this.AutomationLiveSetting;
      }

      protected override void OnTextChanged(EventArgs e)
      {
         base.OnTextChanged(e);
         AutomationNotifications.UiaRaiseLiveRegionChangedEvent(this.AccessibilityObject);
      }
   }
}
```

<span data-ttu-id="72c76-156">**UıA bildirim olayları**</span><span class="sxs-lookup"><span data-stu-id="72c76-156">**UIA notification events**</span></span>

<span data-ttu-id="72c76-157">Windows 10 Fall Creators Update 'te tanıtılan UıA bildirim olayı, uygulamanızın kullanıcı arabiriminde ilgili bir denetime sahip olması gerekmeden, yalnızca olayla sağladığınız metni temel alan bir duyuru oluşturmak için bir UıA olayı tetiklenmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="72c76-157">The UIA Notification event, introduced in Windows 10 Fall Creators Update, allows your app to raise a UIA event, which leads to Narrator simply making an announcement based on text you supply with the event, without the need to have a corresponding control in the UI.</span></span> <span data-ttu-id="72c76-158">Bazı senaryolarda bu, uygulamanızın erişilebilirliğini önemli ölçüde artırmanın kolay bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="72c76-158">In some scenarios, this is a straightforward way to dramatically improve the accessibility of your app.</span></span> <span data-ttu-id="72c76-159">' De, uzun sürebilecek bazı işlemlerin ilerlemesini bilgilendirmek için de yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-159">In can also be useful to notify of the progress of some process that may take a long time.</span></span> <span data-ttu-id="72c76-160">UııA Notification olayları hakkında daha fazla bilgi için, bkz. [masaüstü uygulamanız yenı UI bildirimi olayından mi yararlanabilir?](/archive/blogs/winuiautomation/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need).</span><span class="sxs-lookup"><span data-stu-id="72c76-160">For more information about UIA Notification Events, see [Can your desktop app leverage the new UI Notification event?](/archive/blogs/winuiautomation/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need).</span></span>

<span data-ttu-id="72c76-161">Aşağıdaki örnek [bildirim olayını](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A)oluşturur:</span><span class="sxs-lookup"><span data-stu-id="72c76-161">The following example raises the [Notification event](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):</span></span>

```csharp
MethodInfo raiseMethod = typeof(AccessibleObject).GetMethod("RaiseAutomationNotification");
if (raiseMethod != null) {
   raiseMethod.Invoke(progressBar1.AccessibilityObject, new object[3] {/*Other*/ 4, /*All*/ 2, "The progress is 50%." });
}
```

<span data-ttu-id="72c76-162">**Klavye erişiminde araç Ipuçları**</span><span class="sxs-lookup"><span data-stu-id="72c76-162">**ToolTips on keyboard access**</span></span>

<span data-ttu-id="72c76-163">.NET Framework 4.7.2 ve önceki sürümleri hedefleyen uygulamalarda, bir denetim [araç ipucu](xref:System.Windows.Forms.ToolTip) yalnızca bir fare işaretçisi denetime taşınarak açılan menü için tetiklenebilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-163">In applications that target .NET Framework 4.7.2 and earlier versions, a control [tooltip](xref:System.Windows.Forms.ToolTip) can only be triggered to pop up by moving a mouse pointer into the control.</span></span> <span data-ttu-id="72c76-164">.NET Framework 4,8 ' den itibaren klavye kullanıcısı, değiştirici tuşları olan veya içermeyen bir sekme tuşu veya ok tuşlarını kullanarak Denetim araç ipucunu tetikleyebilirler.</span><span class="sxs-lookup"><span data-stu-id="72c76-164">Starting with .NET Framework 4.8, a keyboard user can trigger a control's tooltip by focusing the control using a Tab key or arrow keys with or without modifier keys.</span></span> <span data-ttu-id="72c76-165">Bu belirli erişilebilirlik geliştirmesi ek bir [AppContext anahtarı](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)gerektirir:</span><span class="sxs-lookup"><span data-stu-id="72c76-165">This particular accessibility enhancement requires an additional [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1"/>
   </startup>
   <runtime>
      <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false  -->
      <!-- Please note that disabling Switch.UseLegacyAccessibilityFeatures, Switch.UseLegacyAccessibilityFeatures.2 and Switch.UseLegacyAccessibilityFeatures.3 is required to disable Switch.System.Windows.Forms.UseLegacyToolTipDisplay -->
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false"/>
   </runtime>
</configuration>
```

<span data-ttu-id="72c76-166">Aşağıdaki şekilde, Kullanıcı klavyeyle bir düğme seçtiğinde araç ipucunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="72c76-166">The following figure shows the tooltip when the user has selected a button with the keyboard.</span></span>

![Kullanıcı klavyeden düğmeye gittiğinde araç ipucunun ekran görüntüsü.](./media/whats-new-in-accessibility/select-tooltip-with-keyboard.png)

<a name="wpf48"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="72c76-168">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="72c76-168">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="72c76-169">.NET Framework 4,8 ' den başlayarak WPF bir dizi erişilebilirlik geliştirmesi içerir.</span><span class="sxs-lookup"><span data-stu-id="72c76-169">Starting with .NET Framework 4.8, WPF includes a number of accessibility improvements.</span></span>

<span data-ttu-id="72c76-170">**Ekran anlayıcıları artık daraltılmış veya gizli görünürlüğe sahip öğeleri duyurmayacak**</span><span class="sxs-lookup"><span data-stu-id="72c76-170">**Screen narrators no longer announce elements with Collapsed or Hidden visibility**</span></span>

<span data-ttu-id="72c76-171">Daraltılmış veya gizli görünürlüğe sahip öğeler artık ekran okuyucu tarafından duyurulmaz.</span><span class="sxs-lookup"><span data-stu-id="72c76-171">Elements with collapsed or hidden visibility are no longer announced by screen reader.</span></span> <span data-ttu-id="72c76-172">Görünürlüğü olan öğeleri içeren kullanıcı arabirimleri <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> , kullanıcıya duyurulacak olmaları durumunda ekran okuyucular tarafından yanlış temsil edilebilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-172">User interfaces that contain elements with a Visibility of <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> or <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> can be misrepresented by screen readers if they are announced to the user.</span></span> <span data-ttu-id="72c76-173">.NET Framework 4,8 ' den itibaren, WPF artık UIAutomation ağacının denetim görünümünde daraltılmış veya gizli öğeleri içermez, bu nedenle ekran okuyucular artık bu öğeleri duyurabilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-173">Starting with .NET Framework 4.8, WPF no longer includes collapsed or hidden elements in the Control View of the UIAutomation tree, so the screen readers can no longer announce these elements.</span></span>

<span data-ttu-id="72c76-174">**Adorner tabanlı metin seçimiyle kullanılacak SelectionTextBrush özelliği**</span><span class="sxs-lookup"><span data-stu-id="72c76-174">**SelectionTextBrush property for use with non-Adorner based text selection**</span></span>

<span data-ttu-id="72c76-175">.NET Framework 4.7.2 ' de, WPF, <xref:System.Windows.Controls.TextBox> donatıcı katmanını kullanmadan çizim ve <xref:System.Windows.Controls.PasswordBox> metin seçme özelliği ekledi.</span><span class="sxs-lookup"><span data-stu-id="72c76-175">In .NET Framework 4.7.2, WPF added the ability to draw <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox> text selection without using the Adorner layer.</span></span> <span data-ttu-id="72c76-176">Bu senaryodaki seçili metnin ön plan rengi tarafından dikte edildi <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="72c76-176">The foreground color of the selected text in this scenario was dictated by <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="72c76-177">.NET Framework 4,8 yeni bir özellik ekler, `SelectionTextBrush` Bu, geliştiricilerin, donatıcı olmayan tabanlı metin seçimi kullanılırken seçili metin için belirli fırçayı seçmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="72c76-177">.NET Framework 4.8 adds a new property, `SelectionTextBrush`, that allows developers to select the specific brush for the selected text when using non-Adorner based text selection.</span></span> <span data-ttu-id="72c76-178">Bu özellik yalnızca <xref:System.Windows.Controls.Primitives.TextBoxBase> , <xref:System.Windows.Controls.PasswordBox> donatıcı tabanlı olmayan metin seçimi ETKIN olan WPF uygulamalarında yalnızca türetilmiş denetimleri ve denetimi işe yarar.</span><span class="sxs-lookup"><span data-stu-id="72c76-178">This property works only on <xref:System.Windows.Controls.Primitives.TextBoxBase>-derived controls and the <xref:System.Windows.Controls.PasswordBox> control in WPF applications with non-Adorner-based text selection enabled.</span></span> <span data-ttu-id="72c76-179">Denetim üzerinde çalışmaz <xref:System.Windows.Controls.RichTextBox> .</span><span class="sxs-lookup"><span data-stu-id="72c76-179">It does not work on the <xref:System.Windows.Controls.RichTextBox> control.</span></span> <span data-ttu-id="72c76-180">Adorner tabanlı olmayan metin seçimi etkinleştirilmemişse, bu özellik yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="72c76-180">If non-Adorner-based text selection is not enabled, this property is ignored.</span></span>

<span data-ttu-id="72c76-181">Bu özelliği kullanmak için XAML kodunuza eklemeniz ve uygun fırçayı ya da bağlamayı kullanmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="72c76-181">To use this property, simply add it to your XAML code and use the appropriate brush or binding.</span></span> <span data-ttu-id="72c76-182">Ortaya çıkan metin seçimi şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="72c76-182">The resulting text selection looks like this:</span></span>

![Merhaba Dünya sözcüklerle çalışan uygulamanın ekran görüntüsü seçili.](./media/whats-new-in-accessibility/selectiontextbrush-property.png)

<span data-ttu-id="72c76-184">`SelectionBrush`Ve özelliklerinin kullanımını, `SelectionTextBrush` uygun olmayan bir arka plan ve ön plan renk kombinasyonu oluşturmak için birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72c76-184">You can combine the use of the `SelectionBrush` and `SelectionTextBrush` properties to generate any background and foreground color combination that you deem appropriate.</span></span>

<span data-ttu-id="72c76-185">**Özelliği Için UIAutomation Controllersupport desteği**</span><span class="sxs-lookup"><span data-stu-id="72c76-185">**Support for the UIAutomation ControllerFor property**</span></span>

<span data-ttu-id="72c76-186">UIAutomation `ControllerFor` özelliği, bu özelliği destekleyen Otomasyon öğesi tarafından yönetilen bir Otomasyon öğeleri dizisi döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="72c76-186">UIAutomation’s `ControllerFor` property returns an array of automation elements that are manipulated by the automation element that supports this property.</span></span> <span data-ttu-id="72c76-187">Bu özellik genellikle otomatik öneri erişilebilirliği için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="72c76-187">This property is commonly used for Auto-suggest accessibility.</span></span> <span data-ttu-id="72c76-188">`ControllerFor` bir Otomasyon öğesi uygulama kullanıcı arabirimi veya masaüstünün bir veya daha fazla kesimini etkiliyorsa kullanılır.</span><span class="sxs-lookup"><span data-stu-id="72c76-188">`ControllerFor` is used when an automation element affects one or more segments of the application UI or the desktop.</span></span> <span data-ttu-id="72c76-189">Aksi takdirde, denetim işleminin etkisini UI öğeleriyle ilişkilendirmek zordur.</span><span class="sxs-lookup"><span data-stu-id="72c76-189">Otherwise, it is hard to associate the impact of the control operation with UI elements.</span></span> <span data-ttu-id="72c76-190">Bu özellik, denetimlerin özellik için bir değer sağlama yeteneğini ekler `ControllerFor` .</span><span class="sxs-lookup"><span data-stu-id="72c76-190">This feature adds the ability for controls to provide a value for the `ControllerFor` property.</span></span>

<span data-ttu-id="72c76-191">.NET Framework 4,8 yeni bir sanal yöntem ekler <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="72c76-191">.NET Framework 4.8 adds a new virtual method, <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>.</span></span> <span data-ttu-id="72c76-192">Özelliği için bir değer sağlamak için `ControllerFor` , bu yöntemi geçersiz kılın ve `List<AutomationPeer>` bunun tarafından geçirilmekte olan denetimler için bir döndürür <xref:System.Windows.Automation.Peers.AutomationPeer> :</span><span class="sxs-lookup"><span data-stu-id="72c76-192">To provide a value for the `ControllerFor` property, simply override this method and return a `List<AutomationPeer>` for the controls being manipulated by this <xref:System.Windows.Automation.Peers.AutomationPeer>:</span></span>

```csharp
public class AutoSuggestTextBox: TextBox
{
   protected override AutomationPeer OnCreateAutomationPeer()
   {
      return new AutoSuggestTextBoxAutomationPeer(this);
   }

   public ListBox SuggestionListBox;
}

internal class AutoSuggestTextBoxAutomationPeer : TextBoxAutomationPeer
{
   public AutoSuggestTextBoxAutomationPeer(AutoSuggestTextBox owner) : base(owner)
   {
   }

   protected override List<AutomationPeer> GetControlledPeersCore()
   {
      List<AutomationPeer> controlledPeers = new List<AutomationPeer>();
      AutoSuggestTextBox owner = Owner as AutoSuggestTextBox;
      controlledPeers.Add(UIElementAutomationPeer.CreatePeerForElement(owner.SuggestionListBox));
      return controlledPeers;
   }
}
```

<span data-ttu-id="72c76-193">**Klavye erişiminde araç ipuçları**</span><span class="sxs-lookup"><span data-stu-id="72c76-193">**Tooltips on keyboard access**</span></span>

<span data-ttu-id="72c76-194">.NET Framework 4.7.2 ve önceki sürümlerde araç ipuçları yalnızca Kullanıcı fare imlecini bir denetim üzerine getirdiğinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="72c76-194">In .NET Framework 4.7.2 and earlier versions, tooltips display only when the user hovers the mouse cursor over a control.</span></span> <span data-ttu-id="72c76-195">.NET Framework 4,8 ' de araç ipuçları klavye odağında ve klavye kısayoluyla de görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="72c76-195">In .NET Framework 4.8, tooltips also display on keyboard focus, as well as via a keyboard shortcut.</span></span>

<span data-ttu-id="72c76-196">Bu özelliği etkinleştirmek için bir uygulamanın, `Switch.UseLegacyAccessibilityFeatures.3` ve `Switch.UseLegacyToolTipDisplay` [appcontext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) anahtarlarını kullanarak .NET Framework 4,8 veya katılımı hedeflemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="72c76-196">To enable this feature, an application needs to target .NET Framework 4.8 or opt-in by using the `Switch.UseLegacyAccessibilityFeatures.3` and `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switches.</span></span> <span data-ttu-id="72c76-197">Aşağıda örnek bir uygulama yapılandırma dosyası verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="72c76-197">The following is a sample application configuration file:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />
   </startup>
   <runtime>
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.UseLegacyToolTipDisplay=false" />
   </runtime>
</configuration>
```

<span data-ttu-id="72c76-198">Etkinleştirildikten sonra, araç ipucu içeren tüm denetimler, denetim klavye odağını aldıktan sonra bunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="72c76-198">Once enabled, all controls that contain a tooltip display it once the control receives keyboard focus.</span></span> <span data-ttu-id="72c76-199">Araç ipucu zaman içinde veya klavye odağı değiştiğinde kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-199">The tooltip can be dismissed over time or when the keyboard focus changes.</span></span> <span data-ttu-id="72c76-200">Kullanıcılar araç ipucunu, CTRL + SHIFT + F10 yeni klavye kısayolunu kullanarak el ile de kapatabilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-200">Users can also dismiss the tooltip manually by using a new keyboard shortcut, Ctrl + Shift + F10.</span></span> <span data-ttu-id="72c76-201">Araç ipucu kapatıldıktan sonra, aynı klavye kısayolu kullanılarak yeniden görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-201">Once the tooltip has been dismissed it can be displayed again by using the same keyboard shortcut.</span></span>

> [!NOTE]
> <span data-ttu-id="72c76-202">Denetimlerde [Şerit Araç ipuçları](xref:System.Windows.Controls.Ribbon.RibbonToolTip) <xref:System.Windows.Controls.Ribbon.Ribbon> klavye odağında gösterilmez; yalnızca klavye kısayolu aracılığıyla gösterilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-202">[Ribbon tooltips](xref:System.Windows.Controls.Ribbon.RibbonToolTip) on <xref:System.Windows.Controls.Ribbon.Ribbon> controls won’t show on keyboard focus; they only show via the keyboard shortcut.</span></span>

<span data-ttu-id="72c76-203">**SizeOfSet ve Positionınset UIAutomation özellikleri için destek eklendi**</span><span class="sxs-lookup"><span data-stu-id="72c76-203">**Added Support for SizeOfSet and PositionInSet UIAutomation properties**</span></span>

<span data-ttu-id="72c76-204">Windows 10, iki yeni UIAutomation özelliği sunmuştur `SizeOfSet` ve `PositionInSet` uygulamalar tarafından bir küme içindeki öğelerin sayısını açıklayan uygulamalar tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="72c76-204">Windows 10 introduced two new UIAutomation properties, `SizeOfSet` and `PositionInSet`, which are used by applications to describe the count of items in a set.</span></span> <span data-ttu-id="72c76-205">Ekran okuyucular gibi UIAutomation istemci uygulamaları, bu özellikler için bir uygulamayı sorgulayabilir ve uygulamanın kullanıcı arabiriminin doğru bir temsilini duyurur.</span><span class="sxs-lookup"><span data-stu-id="72c76-205">UIAutomation client applications such as screen readers can then query an application for these properties and announce an accurate representation of the application’s UI.</span></span>

<span data-ttu-id="72c76-206">.NET Framework 4,8 ' den başlayarak WPF, WPF uygulamalarında UIAutomation için bu iki özelliği kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="72c76-206">Starting with .NET Framework 4.8, WPF  exposes these two properties to UIAutomation in WPF applications.</span></span> <span data-ttu-id="72c76-207">Bu, iki şekilde gerçekleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="72c76-207">This can be accomplished in two ways:</span></span>

- <span data-ttu-id="72c76-208">Bağımlılık özelliklerini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="72c76-208">By using dependency properties.</span></span>

  <span data-ttu-id="72c76-209">WPF iki yeni bağımlılık özelliği ekler <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> ve <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="72c76-209">WPF adds two new dependency properties, <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>.</span></span> <span data-ttu-id="72c76-210">Geliştirici, değerlerini ayarlamak için XAML kullanabilir:</span><span class="sxs-lookup"><span data-stu-id="72c76-210">A developer can use XAML to set their values:</span></span>

  ```xaml
  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="1">Button 1</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="2">Button 2</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="3">Button 3</Button>
  ```

- <span data-ttu-id="72c76-211">AutomationPeer sanal yöntemlerini geçersiz kılarak.</span><span class="sxs-lookup"><span data-stu-id="72c76-211">By overriding AutomationPeer virtual methods.</span></span>

  <span data-ttu-id="72c76-212"><xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore>Ve <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> sanal yöntemleri AutomationPeer sınıfına eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="72c76-212">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> and <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> virtual methods been added to the AutomationPeer class.</span></span> <span data-ttu-id="72c76-213">Bir geliştirici `SizeOfSet` `PositionInSet` , aşağıdaki örnekte gösterildiği gibi bu yöntemleri geçersiz kılarak ve için değerler verebilir:</span><span class="sxs-lookup"><span data-stu-id="72c76-213">A developer can provide values for `SizeOfSet` and `PositionInSet` by overriding these methods, as shown in the following example:</span></span>

  ```csharp
  public class MyButtonAutomationPeer : ButtonAutomationPeer
  {
    protected override int GetSizeOfSetCore()
    {
        // Call into your own logic to provide a value for SizeOfSet
        return CalculateSizeOfSet();
    }

    protected override int GetPositionInSetCore()
    {
        // Call into your own logic to provide a value for PositionInSet
        return CalculatePositionInSet();
    }
  }
  ```

<span data-ttu-id="72c76-214">Ayrıca, <xref:System.Windows.Controls.ItemsControl> örneklerdeki öğeler, geliştiriciden ek işlem yapılmadan bu özellikler için otomatik olarak bir değer sağlar.</span><span class="sxs-lookup"><span data-stu-id="72c76-214">In addition, items in <xref:System.Windows.Controls.ItemsControl> instances provide a value for these properties automatically without additional action from the developer.</span></span> <span data-ttu-id="72c76-215">Bir <xref:System.Windows.Controls.ItemsControl> gruplandırılmışsa, gruplar koleksiyonu bir küme olarak temsil edilir ve her bir grup içindeki her bir öğe, bu grubun içindeki konumunu ve grubun boyutunu sunan grubun içindeki her bir öğe ile ayrı bir küme olarak sayılır.</span><span class="sxs-lookup"><span data-stu-id="72c76-215">If an <xref:System.Windows.Controls.ItemsControl> is grouped, the collection of groups is represented as a set, and each group is counted as a separate set, with each item inside that group providing its position inside that group as well as the size of the group.</span></span> <span data-ttu-id="72c76-216">Otomatik değerler sanallaştırmadan etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="72c76-216">Automatic values are not affected by virtualization.</span></span> <span data-ttu-id="72c76-217">Bir öğe gerçekleştirilmese de, bu, denetimin toplam boyutuna doğru sayılır ve eşdüzey öğelerinin kümesindeki konumu etkiler.</span><span class="sxs-lookup"><span data-stu-id="72c76-217">Even if an item is not realized, it is still counted toward the total size of the set and affects the position in the set of its sibling items.</span></span>

<span data-ttu-id="72c76-218">Otomatik değerler yalnızca uygulama .NET Framework 4,8 ' i hedefliyorsa sağlanır.</span><span class="sxs-lookup"><span data-stu-id="72c76-218">Automatic values are only provided if the application targets .NET Framework 4.8.</span></span> <span data-ttu-id="72c76-219">.NET Framework önceki bir sürümünü hedefleyen uygulamalar için, `Switch.UseLegacyAccessibilityFeatures.3` aşağıdaki App.config dosyasında gösterildiği gibi [AppContext anahtarını](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="72c76-219">For applications that target an earlier version of the .NET Framework, you can set the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), as shown in the following App.config file:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />
   </startup>
   <runtime>
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
   </runtime>
</configuration>
```

<a name="wf48"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="72c76-220">Windows Workflow Foundation (WF) iş akışı Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="72c76-220">Windows Workflow Foundation (WF) workflow designer</span></span>

<span data-ttu-id="72c76-221">İş akışı Tasarımcısı .NET Framework 4,8 ' de aşağıdaki değişiklikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="72c76-221">The workflow designer includes the following changes in .NET Framework 4.8:</span></span>

- <span data-ttu-id="72c76-222">Ekran okuyucusu kullanan kullanıcılar, FlowSwitch durum etiketlerindeki geliştirmeleri görür.</span><span class="sxs-lookup"><span data-stu-id="72c76-222">Users using Narrator will see improvements in FlowSwitch case labels.</span></span>

- <span data-ttu-id="72c76-223">Ekran okuyucusu kullanan kullanıcılar, düğme açıklamalarındaki geliştirmeleri görür.</span><span class="sxs-lookup"><span data-stu-id="72c76-223">Users using Narrator will see improvements in button descriptions.</span></span>

- <span data-ttu-id="72c76-224">Yüksek Karşıtlık Temaları seçen kullanıcılar, öğeler arasında daha iyi kontrast oranları ve odak öğeleri için kullanılan daha belirgin seçim kutuları gibi İş Akışı Tasarımcısı ve denetimlerinin görünürlüğünde geliştirmeler görür.</span><span class="sxs-lookup"><span data-stu-id="72c76-224">Users who choose High Contrast themes will see improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

<span data-ttu-id="72c76-225">Uygulamanız .NET Framework 4.7.2 veya önceki bir sürümü hedefliyorsa, `Switch.UseLegacyAccessibilityFeatures.3` uygulama yapılandırma dosyanızda [AppContext anahtarını](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) olarak ayarlayarak bu değişiklikleri kabul edebilirsiniz `false` .</span><span class="sxs-lookup"><span data-stu-id="72c76-225">If your application targets .NET Framework 4.7.2 or an earlier version, you can opt into these changes by setting the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to `false` in your application configuration file.</span></span> <span data-ttu-id="72c76-226">Daha fazla bilgi için bu makaledeki [Erişilebilirlik geliştirmelerinden yararlanma](#taking-advantage-of-accessibility-enhancements) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="72c76-226">For more information, see the [Taking advantage of accessibility enhancements](#taking-advantage-of-accessibility-enhancements) section in this article.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-472"></a><span data-ttu-id="72c76-227">.NET Framework 4.7.2 ' deki erişilebilirlik yenilikleri</span><span class="sxs-lookup"><span data-stu-id="72c76-227">What's new in accessibility in .NET Framework 4.7.2</span></span>

<span data-ttu-id="72c76-228">.NET Framework 4.7.2, aşağıdaki alanlarda yeni erişilebilirlik özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="72c76-228">.NET Framework 4.7.2 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="72c76-229">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="72c76-229">Windows Forms</span></span>](#winforms472)

- [<span data-ttu-id="72c76-230">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="72c76-230">Windows Presentation Foundation (WPF)</span></span>](#wpf472)

<a name="winforms472"></a>

### <a name="windows-forms"></a><span data-ttu-id="72c76-231">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="72c76-231">Windows Forms</span></span>

<span data-ttu-id="72c76-232">**Yüksek Karşıtlık temalarda işletim sistemi tanımlı renkler**</span><span class="sxs-lookup"><span data-stu-id="72c76-232">**OS-defined colors in High Contrast themes**</span></span>

<span data-ttu-id="72c76-233">.NET Framework 4.7.2 ile başlayarak, Windows Forms Yüksek Karşıtlık temalarda işletim sistemi tarafından tanımlanan renkleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="72c76-233">Starting with .NET Framework 4.7.2, Windows Forms uses colors defined by the operating system in High Contrast themes.</span></span> <span data-ttu-id="72c76-234">Bu, aşağıdaki denetimleri etkiler:</span><span class="sxs-lookup"><span data-stu-id="72c76-234">This affects the following controls:</span></span>

- <span data-ttu-id="72c76-235">Denetimin aşağı açılan oku <xref:System.Windows.Forms.ToolStripDropDownButton> .</span><span class="sxs-lookup"><span data-stu-id="72c76-235">The drop-down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> control.</span></span>

- <span data-ttu-id="72c76-236"><xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> Ve, <xref:System.Windows.Forms.CheckBox> <xref:System.Windows.Forms.ButtonBase.FlatStyle> veya olarak ayarlanan denetimleri <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="72c76-236">The <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span></span> <span data-ttu-id="72c76-237">Daha önce, seçilen metin ve arka plan renkleri çok sevmiyor ve okunması zor.</span><span class="sxs-lookup"><span data-stu-id="72c76-237">Previously, selected text and background colors were not contrasting and were hard to read.</span></span>

- <span data-ttu-id="72c76-238">Öğesinin <xref:System.Windows.Forms.GroupBox> özelliği olarak ayarlanmış olan içinde bulunan denetimler <xref:System.Windows.Forms.Control.Enabled> `false` .</span><span class="sxs-lookup"><span data-stu-id="72c76-238">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="72c76-239"><xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolStripComboBox> <xref:System.Windows.Forms.ToolStripDropDownButton> Yüksek karşıtlık modunda daha fazla parlaklık karşıtlığı oranına sahip, ve denetimleri.</span><span class="sxs-lookup"><span data-stu-id="72c76-239">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls, which have an increased luminosity contrast ratio in High Contrast Mode.</span></span>

- <span data-ttu-id="72c76-240"><xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor>Öğesinin özelliği <xref:System.Windows.Forms.DataGridViewLinkCell> .</span><span class="sxs-lookup"><span data-stu-id="72c76-240">The <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> property of the <xref:System.Windows.Forms.DataGridViewLinkCell>.</span></span>

<span data-ttu-id="72c76-241">**Ekran okuyucusu geliştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="72c76-241">**Narrator improvements**</span></span>

<span data-ttu-id="72c76-242">.NET Framework 4.7.2 ile başlayarak, ekran okuyucusu desteği aşağıdaki şekilde geliştirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="72c76-242">Starting with .NET Framework 4.7.2, Narrator support is enhanced as follows:</span></span>

- <span data-ttu-id="72c76-243"><xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType>Bir ' ın metnini duyurdığınızda özelliğin değerini duyurur <xref:System.Windows.Forms.ToolStripMenuItem> .</span><span class="sxs-lookup"><span data-stu-id="72c76-243">It announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

- <span data-ttu-id="72c76-244">Bir <xref:System.Windows.Forms.ToolStripMenuItem> öğesinin <xref:System.Windows.Forms.Control.Enabled> özelliği olarak ayarlandığı zaman gösterir `false` .</span><span class="sxs-lookup"><span data-stu-id="72c76-244">It indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="72c76-245">Özelliği olarak ayarlandığında onay kutusunun durumu hakkında geri bildirim sağlar <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> `true` .</span><span class="sxs-lookup"><span data-stu-id="72c76-245">It gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span></span>

- <span data-ttu-id="72c76-246">Ekran okuyucusu 'nun tarama modu odak sırası, ClickOnce indirme iletişim kutusu penceresindeki denetimlerin görsel sırasıyla tutarlıdır.</span><span class="sxs-lookup"><span data-stu-id="72c76-246">Narrator's Scan Mode focus order is consistent with the visual order of the controls on the ClickOnce download dialog window.</span></span>

<span data-ttu-id="72c76-247">**DataGridView geliştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="72c76-247">**DataGridView improvements**</span></span>

<span data-ttu-id="72c76-248">.NET Framework 4.7.2 ile başlayarak, <xref:System.Windows.Forms.DataGridView> Denetim aşağıdaki erişilebilirlik geliştirmelerini sunmuştur:</span><span class="sxs-lookup"><span data-stu-id="72c76-248">Starting with .NET Framework 4.7.2, the <xref:System.Windows.Forms.DataGridView> control has introduced the following accessibility improvements:</span></span>

- <span data-ttu-id="72c76-249">Satırlar klavye kullanılarak sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-249">Rows can be sorted using the keyboard.</span></span> <span data-ttu-id="72c76-250">Kullanıcı, geçerli sütuna göre sıralamak için F3 tuşunu kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-250">A user can use the F3 key in order to sort by the current column.</span></span>

- <span data-ttu-id="72c76-251">, <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> ' A ayarlandığında <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> , sütun üst bilgisi, geçerli satırdaki hücreler aracılığıyla geçerli sütunu Kullanıcı sekmeleri olarak gösterecek şekilde renkle değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-251">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header changes color to indicate the current column as the user tabs through the cells in the current row.</span></span>

- <span data-ttu-id="72c76-252"><xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType>Öğesinin özelliği <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> doğru üst denetimi döndürür.</span><span class="sxs-lookup"><span data-stu-id="72c76-252">The <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> property of a  <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> returns the correct parent control.</span></span>

<span data-ttu-id="72c76-253">**Geliştirilmiş görsel ipuçları**</span><span class="sxs-lookup"><span data-stu-id="72c76-253">**Improved visual cues**</span></span>

- <span data-ttu-id="72c76-254"><xref:System.Windows.Forms.RadioButton> <xref:System.Windows.Forms.CheckBox> Boş bir özelliği olan ve denetimleri, <xref:System.Windows.Forms.ButtonBase.Text> odağı alırken bir odak göstergesi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="72c76-254">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property  display a focus indicator when they receive the focus.</span></span>

<span data-ttu-id="72c76-255">**Geliştirilmiş özellik Kılavuzu desteği**</span><span class="sxs-lookup"><span data-stu-id="72c76-255">**Improved Property Grid Support**</span></span>

- <span data-ttu-id="72c76-256"><xref:System.Windows.Forms.PropertyGrid>Denetim alt öğeleri artık `true` <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> yalnızca bir PropertyGrid öğesi etkinleştirildiğinde özelliği için bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="72c76-256">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span></span>

- <span data-ttu-id="72c76-257"><xref:System.Windows.Forms.PropertyGrid>Denetim alt öğeleri, `false` <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> yalnızca bir PropertyGrid öğesi Kullanıcı tarafından değiştirilebiliyorsa özelliği için bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="72c76-257">The <xref:System.Windows.Forms.PropertyGrid> control child elements return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span></span>

<span data-ttu-id="72c76-258">**Geliştirilmiş Klavye gezintisi**</span><span class="sxs-lookup"><span data-stu-id="72c76-258">**Improved keyboard navigation**</span></span>

- <span data-ttu-id="72c76-259"><xref:System.Windows.Forms.ToolStripButton>Denetim, özelliği, özelliği olan bir <xref:System.Windows.Forms.ToolStripPanel> öğesine dahil edildiğinde odağa izin verir <xref:System.Windows.Forms.ToolStripPanel.TabStop>`true`</span><span class="sxs-lookup"><span data-stu-id="72c76-259">The <xref:System.Windows.Forms.ToolStripButton> control allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`</span></span>

<a name="wpf472"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="72c76-260">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="72c76-260">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="72c76-261">**CheckBox ve RadioButton denetimlerinde yapılan değişiklikler**</span><span class="sxs-lookup"><span data-stu-id="72c76-261">**Changes to the CheckBox and RadioButton controls**</span></span>

<span data-ttu-id="72c76-262">.NET Framework 4.7.1 ve önceki sürümlerde, WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWithType> ve <xref:System.Windows.Controls.RadioButton?displayProperty=nameWithType> denetimler tutarsız ve klasik ve yüksek karşıtlık temalarında hatalı odak görselleri.</span><span class="sxs-lookup"><span data-stu-id="72c76-262">In .NET Framework 4.7.1 and earlier versions, the WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWithType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWithType> controls have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="72c76-263">Bu sorunlar, denetimlerin hiçbir içerik kümesi olmadığı durumlarda oluşur.</span><span class="sxs-lookup"><span data-stu-id="72c76-263">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="72c76-264">Bu, Temalar kafa karıştırıcı ve odak görselindeki geçişleri görebilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-264">This can make the transition between themes confusing and the focus visual hard to see.</span></span>

<span data-ttu-id="72c76-265">.NET Framework 4.7.2 ' de, bu görseller artık Temalar arasında daha tutarlıdır ve klasik ve Yüksek Karşıtlık temalarda daha kolay görünür.</span><span class="sxs-lookup"><span data-stu-id="72c76-265">In .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

<span data-ttu-id="72c76-266">**WPF uygulamasında barındırılan WinForms denetimleri**</span><span class="sxs-lookup"><span data-stu-id="72c76-266">**WinForms controls hosted in a WPF application**</span></span>

<span data-ttu-id="72c76-267">.NET Framework 4.7.1 ve önceki sürümlerde bulunan bir WPF uygulamasında barındırılan WinForms denetimi için, söz konusu katmandaki ilk veya son denetim WPF denetimi ise, kullanıcılar WinForms katmanının dışına sekmesine dönüştüremedik <xref:System.Windows.Forms.Integration.ElementHost> .</span><span class="sxs-lookup"><span data-stu-id="72c76-267">For WinForms control hosted in a WPF application in .NET Framework 4.7.1 and earlier versions, users couldn't tab out of the WinForms layer if the first or last control in that layer is the WPF <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span> <span data-ttu-id="72c76-268">.NET Framework 4.7.2 ' de, kullanıcılar artık WinForms katmanının dışına sekme verebilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-268">In .NET Framework 4.7.2, users are now able to tab out of the WinForms layer.</span></span>

<span data-ttu-id="72c76-269">Ancak, odağa dayanan otomatikleştirilmiş uygulamalar artık WinForms katmanını hiçbir şekilde yok etmeyebilir ve beklendiği gibi çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-269">However, automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-471"></a><span data-ttu-id="72c76-270">.NET Framework 4.7.1 ' deki erişilebilirlik yenilikleri</span><span class="sxs-lookup"><span data-stu-id="72c76-270">What's new in accessibility in .NET Framework 4.7.1</span></span>

<span data-ttu-id="72c76-271">.NET Framework 4.7.1, aşağıdaki alanlarda yeni erişilebilirlik özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="72c76-271">.NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="72c76-272">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="72c76-272">Windows Presentation Foundation (WPF)</span></span>](#wpf471)

- [<span data-ttu-id="72c76-273">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="72c76-273">Windows Forms</span></span>](#winforms471)

- [<span data-ttu-id="72c76-274">ASP.NET Web denetimleri</span><span class="sxs-lookup"><span data-stu-id="72c76-274">ASP.NET web controls</span></span>](#aspnet471)

- [<span data-ttu-id="72c76-275">.NET SDK Tools</span><span class="sxs-lookup"><span data-stu-id="72c76-275">.NET SDK Tools</span></span>](#tools471)

- [<span data-ttu-id="72c76-276">Windows Workflow Foundation (WF) İş Akışı Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="72c76-276">Windows Workflow Foundation (WF) Workflow Designer</span></span>](#wf471)

<a name="wpf471"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="72c76-277">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="72c76-277">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="72c76-278">**Ekran okuyucu iyileştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="72c76-278">**Screen reader improvements**</span></span>

<span data-ttu-id="72c76-279">Erişilebilirlik iyileştirmeleri etkinleştirilmişse, .NET Framework 4.7.1, ekran okuyucularını etkileyen aşağıdaki geliştirmeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="72c76-279">If accessibility improvements are enabled, .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="72c76-280">.NET Framework 4,7 ve önceki sürümlerde, <xref:System.Windows.Controls.Expander> denetimler ekran okuyucular tarafından düğme olarak duyurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="72c76-280">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="72c76-281">.NET Framework 4.7.1 ile başlayarak, Genişletilebilir/daraltılabilir gruplar olarak doğru duyurulur.</span><span class="sxs-lookup"><span data-stu-id="72c76-281">Starting with .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="72c76-282">.NET Framework 4,7 ve önceki sürümlerde, <xref:System.Windows.Controls.DataGridCell> denetimler ekran okuyucular tarafından "özel" olarak duyurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="72c76-282">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="72c76-283">.NET Framework 4.7.1 başlayarak, artık veri kılavuzu hücresi (yerelleştirilmiş) olarak doğru duyurulur.</span><span class="sxs-lookup"><span data-stu-id="72c76-283">Starting with .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>

- <span data-ttu-id="72c76-284">.NET Framework 4.7.1 'den başlayarak ekran okuyucular düzenlenebilir bir adı duyurur <xref:System.Windows.Controls.ComboBox> .</span><span class="sxs-lookup"><span data-stu-id="72c76-284">Starting with .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="72c76-285">.NET Framework 4,7 ve önceki sürümlerde denetimler, <xref:System.Windows.Controls.PasswordBox> "görünümde hiçbir öğe yok" veya başka türlü yanlış davranışa sahip olarak duyurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="72c76-285">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="72c76-286">Bu sorun, .NET Framework 4.7.1 ile başlayarak düzeltilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-286">This issue is fixed starting with .NET Framework 4.7.1.</span></span>

<span data-ttu-id="72c76-287">**UIAutomation LiveRegion desteği**</span><span class="sxs-lookup"><span data-stu-id="72c76-287">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="72c76-288">Okuyucu gibi ekran okuyucular, kullanıcıların, genellikle odağa sahip kullanıcı arabirimi içeriğinin metinden konuşmaya çıkışıyla bir uygulamanın kullanıcı arabirimi içeriğini okumasına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="72c76-288">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="72c76-289">Ancak, bir UI öğesi değişirse ve odağa sahip değilse, kullanıcıya bildirimde bulunulmayabilir ve önemli bilgileri kaçırmayabilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-289">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="72c76-290">Canlı bölgeler bu sorunu çözmeye hedeflenir.</span><span class="sxs-lookup"><span data-stu-id="72c76-290">Live regions aim at solving this problem.</span></span> <span data-ttu-id="72c76-291">Geliştirici, ekran okuyucuyu veya başka bir UIAutomation istemcisini, bir kullanıcı arabirimi öğesine önemli bir değişikliğin yapıldığını bilgilendirmek için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-291">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="72c76-292">Ekran okuyucu daha sonra bu değişikliğin kullanıcısına nasıl ve ne zaman bilgi verileceğine karar verebilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-292">The screen reader can then decide how and when to inform the user of this change.</span></span>

<span data-ttu-id="72c76-293">Canlı bölgeleri desteklemek için WPF 'e aşağıdaki API 'Ler eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="72c76-293">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="72c76-294"><xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> **Livesetting** özelliğini ve **liveregionchanged** olayını tanımlayan ve alanları.</span><span class="sxs-lookup"><span data-stu-id="72c76-294">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="72c76-295">XAML kullanılarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-295">They can be set by using XAML.</span></span>

- <span data-ttu-id="72c76-296">Kullanıcı ARABIRIMININ önem derecesine sahip ekran okuyucuyu kullanıcıya bildiren **AutomationProperties. LiveSetting** iliştirilmiş özelliği.</span><span class="sxs-lookup"><span data-stu-id="72c76-296">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="72c76-297"><xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> **AutomationProperties. livesetting** ekli özelliğini tanımlayan özelliği.</span><span class="sxs-lookup"><span data-stu-id="72c76-297">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>

- <span data-ttu-id="72c76-298"><xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType>Bir **livesetting** değeri sağlamak için geçersiz kılınabilen yöntemi.</span><span class="sxs-lookup"><span data-stu-id="72c76-298">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="72c76-299"><xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType>Ve <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> , bir **livesetting** değeri alır ve ayarlar.</span><span class="sxs-lookup"><span data-stu-id="72c76-299">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>

- <span data-ttu-id="72c76-300"><xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType>Aşağıdaki olası **livesetting** değerlerini tanımlayan sabit listesi:</span><span class="sxs-lookup"><span data-stu-id="72c76-300">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

  - <span data-ttu-id="72c76-301"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="72c76-301"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="72c76-302">Canlı bölgenin içeriği değiştiyse öğe bildirim göndermez.</span><span class="sxs-lookup"><span data-stu-id="72c76-302">The element does not send notifications if the content of the live region has changed.</span></span>
  - <span data-ttu-id="72c76-303"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="72c76-303"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="72c76-304">Canlı bölgenin içeriği değiştiyse, öğesi interruptive olmayan bildirimler gönderir.</span><span class="sxs-lookup"><span data-stu-id="72c76-304">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>

  - <span data-ttu-id="72c76-305"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="72c76-305"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="72c76-306">Canlı bölgenin içeriği değiştiyse, öğesi interruptive bildirimleri gönderir.</span><span class="sxs-lookup"><span data-stu-id="72c76-306">The element sends interruptive notifications if the content of the live region has changed.</span></span>

<span data-ttu-id="72c76-307">Aşağıdaki örnekte gösterildiği gibi, ilgilendiğiniz öğe üzerinde **AutomationProperties. livesetting** özelliğini ayarlayarak bir LiveRegion oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="72c76-307">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="72c76-308">Canlı bölgedeki veriler değiştiğinde ve bir ekran okuyucuyu bilgilendirmeniz gerektiğinde, aşağıdaki örnekte gösterildiği gibi, açıkça bir olay oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="72c76-308">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```

```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="72c76-309">**High contrast**</span><span class="sxs-lookup"><span data-stu-id="72c76-309">**High contrast**</span></span>

<span data-ttu-id="72c76-310">.NET Framework 4.7.1 ile başlayarak, çeşitli WPF denetimlerinde yüksek karşıtlıklı geliştirmeler yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="72c76-310">Starting with .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="72c76-311">Artık <xref:System.Windows.SystemParameters.HighContrast%2A> Tema ayarlandığında görünür olur.</span><span class="sxs-lookup"><span data-stu-id="72c76-311">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="72c76-312">Bunlar:</span><span class="sxs-lookup"><span data-stu-id="72c76-312">These include:</span></span>

- <span data-ttu-id="72c76-313"><xref:System.Windows.Controls.Expander> denetimle</span><span class="sxs-lookup"><span data-stu-id="72c76-313"><xref:System.Windows.Controls.Expander> control</span></span>

  <span data-ttu-id="72c76-314">Denetim için odak görseli  <xref:System.Windows.Controls.Expander> artık görülebilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-314">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="72c76-315"><xref:System.Windows.Controls.ComboBox>, Ve denetimlerinin klavye görselleri <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.RadioButton> de görünür.</span><span class="sxs-lookup"><span data-stu-id="72c76-315">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="72c76-316">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="72c76-316">For example:</span></span>

  <span data-ttu-id="72c76-317">Önce:</span><span class="sxs-lookup"><span data-stu-id="72c76-317">Before:</span></span>

  ![Odak içeren genişleticiye ve odak görselinle kumanda ekran görüntüsü.](./media/whats-new-in-accessibility/expander-control-before.png)

  <span data-ttu-id="72c76-319">Sonra:</span><span class="sxs-lookup"><span data-stu-id="72c76-319">After:</span></span>

  ![Odak ile denetimin metninin etrafında noktalı bir çizgi gösteren genişleticiyle ilgili ekran görüntüsü.](./media/whats-new-in-accessibility/expander-control-after.png)

- <span data-ttu-id="72c76-321"><xref:System.Windows.Controls.CheckBox> ve <xref:System.Windows.Controls.RadioButton> denetimler</span><span class="sxs-lookup"><span data-stu-id="72c76-321"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>

  <span data-ttu-id="72c76-322"><xref:System.Windows.Controls.CheckBox>Ve <xref:System.Windows.Controls.RadioButton> denetimlerindeki metin artık yüksek karşıtlık temalarında seçildiğinde daha kolay görülebilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-322">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="72c76-323">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="72c76-323">For example:</span></span>

  <span data-ttu-id="72c76-324">Önce:</span><span class="sxs-lookup"><span data-stu-id="72c76-324">Before:</span></span>

  ![Yüksek karşıtlık temalarda kötü metin görünürlüğüne sahip radyo ve denetim düğmelerinin ekran görüntüsü.](./media/whats-new-in-accessibility/high-contrast-radio-button-before.png)

  <span data-ttu-id="72c76-326">Sonra:</span><span class="sxs-lookup"><span data-stu-id="72c76-326">After:</span></span>

  ![Yüksek karşıtlık temalarda daha iyi metin görünürlüğü olan radyo ve denetim düğmelerinin ekran görüntüsü.](./media/whats-new-in-accessibility/high-contrast-radio-button-after.png)

- <span data-ttu-id="72c76-328"><xref:System.Windows.Controls.ComboBox> denetimle</span><span class="sxs-lookup"><span data-stu-id="72c76-328"><xref:System.Windows.Controls.ComboBox> control</span></span>

  <span data-ttu-id="72c76-329">.NET Framework 4.7.1 ile başlayarak, devre dışı bir denetimin kenarlığı <xref:System.Windows.Controls.ComboBox> devre dışı metinle aynı renktedir.</span><span class="sxs-lookup"><span data-stu-id="72c76-329">Starting with .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="72c76-330">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="72c76-330">For example:</span></span>

  <span data-ttu-id="72c76-331">Önce:</span><span class="sxs-lookup"><span data-stu-id="72c76-331">Before:</span></span>

  ![Farklı renklerde kenarlık ve denetim metni olan devre dışı bir ComboBox 'ın ekran görüntüsü.](./media/whats-new-in-accessibility/combo-disabled-before.png)

  <span data-ttu-id="72c76-333">Sonra:</span><span class="sxs-lookup"><span data-stu-id="72c76-333">After:</span></span>

  ![Denetim metniyle aynı renge sahip devre dışı bir ComboBox 'ın ekran görüntüsü.](./media/whats-new-in-accessibility/combo-disabled-after.png)

  <span data-ttu-id="72c76-335">Ayrıca, devre dışı bırakılmış ve odaklanmış düğmeler doğru tema rengini kullanır.</span><span class="sxs-lookup"><span data-stu-id="72c76-335">In addition, disabled and focused buttons use the correct theme color.</span></span>

  <span data-ttu-id="72c76-336">Önce:</span><span class="sxs-lookup"><span data-stu-id="72c76-336">Before:</span></span>

  ![Renkli gri metinli siyah bir düğmenin ekran görüntüsü.](./media/whats-new-in-accessibility/button-theme-colors-before.png)

  <span data-ttu-id="72c76-338">Sonra:</span><span class="sxs-lookup"><span data-stu-id="72c76-338">After:</span></span>

  ![Siyah metin ile mavi bir düğmenin, odağı bana söyleyen ekran görüntüsü.](./media/whats-new-in-accessibility/button-theme-colors-after.png)

  <span data-ttu-id="72c76-340">Son olarak, .NET Framework 4,7 ve önceki sürümlerde, <xref:System.Windows.Controls.ComboBox> `Toolbar.ComboBoxStyleKey` açılır okun görünmez olması nedeniyle bir denetimin stilini ayarlama.</span><span class="sxs-lookup"><span data-stu-id="72c76-340">Finally, in .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="72c76-341">Bu sorun, .NET Framework 4.7.1 ile başlayarak düzeltilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-341">This issue is fixed starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="72c76-342">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="72c76-342">For example:</span></span>

  <span data-ttu-id="72c76-343">Önce:</span><span class="sxs-lookup"><span data-stu-id="72c76-343">Before:</span></span>

  ![Görünmeyen açılan oka sahip ComboBox denetiminin ekran görüntüsü.](./media/whats-new-in-accessibility/combo-box-style-key-before.png)

  <span data-ttu-id="72c76-345">Sonra:</span><span class="sxs-lookup"><span data-stu-id="72c76-345">After:</span></span>

  ![Açılan oku görüntüleyen bir ComBoxBox denetiminin ekran görüntüsü.](./media/whats-new-in-accessibility/combo-box-style-key-after.png)

- <span data-ttu-id="72c76-347"><xref:System.Windows.Controls.DataGrid> denetimle</span><span class="sxs-lookup"><span data-stu-id="72c76-347"><xref:System.Windows.Controls.DataGrid> control</span></span>

  <span data-ttu-id="72c76-348">.NET Framework 4.7.1 başlayarak, denetimlerde sıralama göstergesi oku <xref:System.Windows.Controls.DataGrid> artık doğru Tema renklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="72c76-348">Starting with .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="72c76-349">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="72c76-349">For example:</span></span>

  <span data-ttu-id="72c76-350">Önce:</span><span class="sxs-lookup"><span data-stu-id="72c76-350">Before:</span></span>

  ![Geliştirmeden önce sıralama göstergesi okunun ekran görüntüsü.](./media/whats-new-in-accessibility/sort-indicator-before.png)

  <span data-ttu-id="72c76-352">Sonra:</span><span class="sxs-lookup"><span data-stu-id="72c76-352">After:</span></span>

  ![İyileştirmeler sonrasında sıralama göstergesi okunun ekran görüntüsü.](./media/whats-new-in-accessibility/sort-indicator-after.png)

  <span data-ttu-id="72c76-354">Ayrıca, .NET Framework 4,7 ve önceki sürümlerde, varsayılan bağlantı stili, fare üzerinde yüksek karşıtlık modlarında yanlış bir renge değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="72c76-354">In addition, in .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="72c76-355">Bu, .NET Framework 4.7.1 ile başlayarak çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="72c76-355">This is resolved starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="72c76-356">Benzer şekilde, <xref:System.Windows.Controls.DataGrid> CheckBox sütunları .NET Framework 4.7.1 ile başlayan klavye odağı geri bildirimi için beklenen renkleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="72c76-356">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with .NET Framework 4.7.1.</span></span>

  <span data-ttu-id="72c76-357">Önce:</span><span class="sxs-lookup"><span data-stu-id="72c76-357">Before:</span></span>

  ![Bağlantının ekran görüntüsü bana tıklayın!](./media/whats-new-in-accessibility/default-link-style-before.png)

  <span data-ttu-id="72c76-360">Sonra:</span><span class="sxs-lookup"><span data-stu-id="72c76-360">After:</span></span>

  ![Bağlantının ekran görüntüsü bana tıklayın!](./media/whats-new-in-accessibility/default-link-style-after.png)

<span data-ttu-id="72c76-363">.NET Framework 4.7.1 ' deki WPF Erişilebilirlik iyileştirmeleri hakkında daha fazla bilgi için bkz. [WPF 'de erişilebilirlik geliştirmeleri](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span><span class="sxs-lookup"><span data-stu-id="72c76-363">For more information on WPF accessibility improvements in .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

<a name="winforms471"></a>

### <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="72c76-364">Windows Forms erişilebilirlik geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="72c76-364">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="72c76-365">.NET Framework 4.7.1, Windows Forms (WinForms), aşağıdaki alanlardaki erişilebilirlik değişikliklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="72c76-365">In .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="72c76-366">**Yüksek Karşıtlık modunda iyileştirilmiş ekran**</span><span class="sxs-lookup"><span data-stu-id="72c76-366">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="72c76-367">.NET Framework 4.7.1 ile başlayarak, çeşitli WinForms denetimleri işletim sisteminde bulunan üst karşıtlık modlarında geliştirilmiş işleme sunar.</span><span class="sxs-lookup"><span data-stu-id="72c76-367">Starting with .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="72c76-368">Windows 10, bazı yüksek karşıtlıklı sistem renklerinin değerlerini değiştirdi ve Windows Forms Windows 10 Win32 çerçevesini temel alır.</span><span class="sxs-lookup"><span data-stu-id="72c76-368">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="72c76-369">En iyi deneyim için, Windows 'un en son sürümünde çalıştırın ve bir test uygulamasına bir App. manifest dosyası ekleyerek en son işletim sistemi değişikliklerini kabul edin ve Windows 10 desteklenen işletim sistemi satırını, aşağıdakileri içerecek şekilde not edin:</span><span class="sxs-lookup"><span data-stu-id="72c76-369">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!-- Windows 10 -->
<supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
```

<span data-ttu-id="72c76-370">Yüksek karşıtlıklı değişikliklere örnek olarak şunlar verilebilir:</span><span class="sxs-lookup"><span data-stu-id="72c76-370">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="72c76-371">Öğelerin içindeki onay işaretlerinin <xref:System.Windows.Forms.MenuStrip> görünümü daha kolay.</span><span class="sxs-lookup"><span data-stu-id="72c76-371">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="72c76-372">Seçildiğinde, devre dışı bırakılan <xref:System.Windows.Forms.MenuStrip> öğeler daha kolay görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="72c76-372">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="72c76-373">Seçili <xref:System.Windows.Forms.Button> denetimdeki metin seçim rengiyle karşıttır.</span><span class="sxs-lookup"><span data-stu-id="72c76-373">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="72c76-374">Devre dışı bırakılan metin daha kolay okunabilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-374">Disabled text is easier to read.</span></span> <span data-ttu-id="72c76-375">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="72c76-375">For example:</span></span>

  <span data-ttu-id="72c76-376">Önce:</span><span class="sxs-lookup"><span data-stu-id="72c76-376">Before:</span></span>

  ![Erişilebilirlik geliştirmelerinden önce yüksek karşıtlıklı modda çalışan farklı denetimleri kullanan bir uygulamanın ekran görüntüsü.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-before.png)

  <span data-ttu-id="72c76-378">Sonra:</span><span class="sxs-lookup"><span data-stu-id="72c76-378">After:</span></span>

  ![Erişilebilirlik iyileştirmelerinden sonra yüksek karşıtlıklı modda çalışan farklı denetimleri kullanan bir uygulamanın ekran görüntüsü.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-after.png)

- <span data-ttu-id="72c76-380">Iş parçacığı özel durumu Iletişim kutusunda yüksek karşıtlık geliştirmeleri.</span><span class="sxs-lookup"><span data-stu-id="72c76-380">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="72c76-381">**İyileştirilmiş ekran okuyucusu desteği**</span><span class="sxs-lookup"><span data-stu-id="72c76-381">**Improved Narrator support**</span></span>

<span data-ttu-id="72c76-382">.NET Framework 4.7.1 Windows Forms, ekran okuyucusu için aşağıdaki erişilebilirlik geliştirmelerini içerir:</span><span class="sxs-lookup"><span data-stu-id="72c76-382">Windows Forms in .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="72c76-383"><xref:System.Windows.Forms.MonthCalendar>Denetime, DIĞER UI Otomasyon Araçları ile birlikte ekran okuyucusu tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-383">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="72c76-384">Denetim, bir <xref:System.Windows.Forms.CheckedListBox> öğenin denetim durumu değiştiğinde kullanıcıya bir liste öğesinin değerini değiştirdikleri bildirilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-384">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>

- <span data-ttu-id="72c76-385"><xref:System.Windows.Forms.DataGridViewCell>Denetim, doğru salt okuma durumunu ekran okuyucusuna bildirir.</span><span class="sxs-lookup"><span data-stu-id="72c76-385">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>

- <span data-ttu-id="72c76-386">Ekran okuyucusu artık devre dışı bırakılan <xref:System.Windows.Forms.ToolStripMenuItem> metni okuyabilir, ancak daha önce devre dışı menü öğelerini atlar.</span><span class="sxs-lookup"><span data-stu-id="72c76-386">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="72c76-387">**UIAutomation erişilebilirlik desenleri için gelişmiş destek**</span><span class="sxs-lookup"><span data-stu-id="72c76-387">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="72c76-388">.NET Framework 4.7.1 ile başlayarak, erişilebilirlik teknolojisi araçları geliştiricileri, çeşitli WinForms denetimleri için ortak API erişilebilirlik desenlerinden ve özelliklerinden faydalanabilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-388">Starting with .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="72c76-389">Bu erişilebilirlik geliştirmeleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="72c76-389">These accessibility improvements include:</span></span>

- <span data-ttu-id="72c76-390"><xref:System.Windows.Forms.ComboBox>Ve <xref:System.Windows.Forms.ToolStripSplitButton> artık [genişletme/daraltma düzenlerini](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)destekliyor.</span><span class="sxs-lookup"><span data-stu-id="72c76-390">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="72c76-391"><xref:System.Windows.Forms.DataGridViewCheckBoxCell>Artık [geçişli stili](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md)destekliyor.</span><span class="sxs-lookup"><span data-stu-id="72c76-391">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>

- <span data-ttu-id="72c76-392"><xref:System.Windows.Forms.ToolStripItem>Denetim, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> özelliği ve [Genişlet/Daralt düzenlerini](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)destekler.</span><span class="sxs-lookup"><span data-stu-id="72c76-392">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="72c76-393"><xref:System.Windows.Forms.NumericUpDown>Ve <xref:System.Windows.Forms.DomainUpDown> denetimleri <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> özelliği destekler.</span><span class="sxs-lookup"><span data-stu-id="72c76-393">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="72c76-394">**Geliştirilmiş özellik tarayıcı deneyimi**</span><span class="sxs-lookup"><span data-stu-id="72c76-394">**Improved property browser experience**</span></span>

<span data-ttu-id="72c76-395">.NET Framework 4.7.1 ile başlayarak, Windows Forms şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="72c76-395">Starting with .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="72c76-396">Çeşitli açılan seçim pencereleri aracılığıyla daha iyi klavye gezintisi.</span><span class="sxs-lookup"><span data-stu-id="72c76-396">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="72c76-397">Gereksiz sekme duraklarının azaltılması.</span><span class="sxs-lookup"><span data-stu-id="72c76-397">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="72c76-398">Denetim türlerinin daha iyi raporlaması.</span><span class="sxs-lookup"><span data-stu-id="72c76-398">Better reporting of control types.</span></span>
- <span data-ttu-id="72c76-399">İyileştirilmiş ekran okuyucusu davranışı.</span><span class="sxs-lookup"><span data-stu-id="72c76-399">Improved narrator behavior.</span></span>

<a name="aspnet471"></a>

### <a name="aspnet-web-controls"></a><span data-ttu-id="72c76-400">ASP.NET Web denetimleri</span><span class="sxs-lookup"><span data-stu-id="72c76-400">ASP.NET web controls</span></span>

<span data-ttu-id="72c76-401">.NET Framework 4.7.1 ve Visual Studio 2017 sürüm 15,3 ' den başlayarak, ASP.NET ASP.NET Web denetimlerinin Visual Studio 'da erişilebilirlik teknolojisiyle nasıl çalıştığını geliştirir.</span><span class="sxs-lookup"><span data-stu-id="72c76-401">Starting with .NET Framework 4.7.1 and Visual Studio 2017 version 15.3, ASP.NET improves how ASP.NET web controls work with accessibility technology in Visual Studio.</span></span> <span data-ttu-id="72c76-402">Değişiklikler şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="72c76-402">Changes include the following:</span></span>

- <span data-ttu-id="72c76-403">**Ayrıntılar görünümü** sihirbazındaki **alan Ekle** Iletişim kutusu ya da **ListView** sihirbazının **LISTVIEW yapılandırma** iletişim kutusu gibi denetimlerde eksik UI erişilebilirlik düzenlerini uygulamak için değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="72c76-403">Changes to implement missing UI accessibility patterns in controls, like the **Add Field** dialog in the **Details View** wizard, or the **Configure ListView** dialog of the **ListView** wizard.</span></span>

- <span data-ttu-id="72c76-404">**Veri sayfalayıcı alanları Düzenleyicisi** gibi yüksek karşıtlık modunda görüntüyü geliştirmek için değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="72c76-404">Changes to improve the display in High Contrast mode, like the **Data Pager Fields Editor**.</span></span>

- <span data-ttu-id="72c76-405">DataPager denetiminin **sayfalayıcı alanlarını Düzenle** Sihirbazı 'ndaki **alanlar** **iletişim kutusu gibi** denetimler için klavye gezinti deneyimlerini geliştirmek üzere yapılan değişiklikler veya **veri kaynağını yapılandırma** Sihirbazı 'Nın veri kaynağını yapılandırma Sihirbazı ' nın **veri seçimini Yapılandır** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="72c76-405">Changes to improve the keyboard navigation experiences for controls, like the **Fields** dialog in the **Edit Pager Fields** wizard of the DataPager control, the **Configure ObjectContext** dialog, or the **Configure Data Selection** dialog of the **Configure Data Source** wizard.</span></span>

<a name="tools471"></a>

### <a name="net-sdk-tools"></a><span data-ttu-id="72c76-406">.NET SDK Tools</span><span class="sxs-lookup"><span data-stu-id="72c76-406">.NET SDK Tools</span></span>

<span data-ttu-id="72c76-407">[Yapılandırma Düzenleyicisi aracı (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) ve [hizmet izleme görüntüleyicisi Aracı (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) , değişen erişilebilirlik sorunları düzeltilirken geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="72c76-407">The [Configuration Editor Tool (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) and [Service Trace Viewer Tool (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="72c76-408">Bunların çoğu, bir ad tanımlanmadığında veya belirli Kullanıcı Arabirimi Otomasyonu desenlerinin doğru uygulanmadığından küçük sorunlardır.</span><span class="sxs-lookup"><span data-stu-id="72c76-408">Most of these were small issues, like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="72c76-409">Birçok kullanıcı bu hatalı değerleri bilmez, ancak ekran okuyucular gibi yardımcı teknolojiler kullanan müşteriler bu SDK araçlarını daha erişilebilir bulacaktır.</span><span class="sxs-lookup"><span data-stu-id="72c76-409">While many users won’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span>

<span data-ttu-id="72c76-410">Bu geliştirmeler, klavye odağı sırası gibi önceki bazı davranışları değiştirir.</span><span class="sxs-lookup"><span data-stu-id="72c76-410">These enhancements change some previous behaviors, such as keyboard focus order.</span></span>

<a name="wf471"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="72c76-411">Windows Workflow Foundation (WF) İş Akışı Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="72c76-411">Windows Workflow Foundation (WF) Workflow Designer</span></span>

<span data-ttu-id="72c76-412">İş Akışı Tasarımcısı erişilebilirlik değişiklikleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="72c76-412">Accessibility changes in the Workflow Designer include the following:</span></span>

- <span data-ttu-id="72c76-413">Sekme sırası, bazı denetimlerde soldan sağa ve yukarıdan aşağıya değişir:</span><span class="sxs-lookup"><span data-stu-id="72c76-413">The tab order changes to left to right and top to bottom in some controls:</span></span>

  - <span data-ttu-id="72c76-414">Etkinlik için bağıntı verileri ayarlamaya yönelik bağıntı Başlat penceresi <xref:System.ServiceModel.Activities.InitializeCorrelation> .</span><span class="sxs-lookup"><span data-stu-id="72c76-414">The initialize correlation window for setting correlation data for the <xref:System.ServiceModel.Activities.InitializeCorrelation> activity.</span></span>

  - <span data-ttu-id="72c76-415"><xref:System.ServiceModel.Activities.Receive>,, <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> Ve etkinlikleri için içerik tanımı penceresi <xref:System.ServiceModel.Activities.ReceiveReply> .</span><span class="sxs-lookup"><span data-stu-id="72c76-415">The content definition window for the <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply> activities.</span></span>

- <span data-ttu-id="72c76-416">Klavye aracılığıyla daha fazla işlev mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="72c76-416">More functions are available via the keyboard:</span></span>

  - <span data-ttu-id="72c76-417">Bir etkinliğin özelliklerini düzenlediğinizde, özellik grupları ilk odaklandığında klavye tarafından daraltılabilirler.</span><span class="sxs-lookup"><span data-stu-id="72c76-417">When editing the properties of an activity, property groups can be collapsed by keyboard the first time they are focused.</span></span>

  - <span data-ttu-id="72c76-418">Uyarı simgeleri klavye tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-418">Warning icons are accessible by keyboard.</span></span>

  - <span data-ttu-id="72c76-419">**Özellikler** penceresindeki **daha fazla Özellikler** düğmesine klavye tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="72c76-419">The **More Properties** button in the **Properties** window is accessible by keyboard.</span></span>

  - <span data-ttu-id="72c76-420">Klavye kullanıcıları İş Akışı Tasarımcısı **bağımsız değişkenler** ve **değişkenler** bölmelerinde üst bilgi öğelerine erişebilirler.</span><span class="sxs-lookup"><span data-stu-id="72c76-420">Keyboard users can access the header items in the **Arguments** and **Variables** panes of the Workflow Designer.</span></span>

- <span data-ttu-id="72c76-421">Odaklanılmış öğelerin şu durumlarda geliştirilmiş görünürlüğü:</span><span class="sxs-lookup"><span data-stu-id="72c76-421">Improved visibility of items with focus, such as when:</span></span>

  - <span data-ttu-id="72c76-422">İş Akışı Tasarımcısı ve etkinlik tasarımcıları tarafından kullanılan veri kılavuzlarına satır ekleme.</span><span class="sxs-lookup"><span data-stu-id="72c76-422">Adding rows to data grids used by the Workflow Designer and activity designers.</span></span>

  - <span data-ttu-id="72c76-423"><xref:System.ServiceModel.Activities.ReceiveReply>Ve etkinliklerindeki alanlar arasında sekme <xref:System.ServiceModel.Activities.SendReply> .</span><span class="sxs-lookup"><span data-stu-id="72c76-423">Tabbing through fields in the <xref:System.ServiceModel.Activities.ReceiveReply> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>

  - <span data-ttu-id="72c76-424">Değişkenler veya bağımsız değişkenler için varsayılan değerleri ayarlama</span><span class="sxs-lookup"><span data-stu-id="72c76-424">Setting default values for variables or arguments</span></span>

- <span data-ttu-id="72c76-425">Ekran okuyucular artık doğru şekilde tanıyabilir:</span><span class="sxs-lookup"><span data-stu-id="72c76-425">Screen readers can now correctly recognize:</span></span>

  - <span data-ttu-id="72c76-426">İş akışı tasarımcısında ayarlanan kesme noktaları.</span><span class="sxs-lookup"><span data-stu-id="72c76-426">Breakpoints set in the workflow designer.</span></span>

  - <span data-ttu-id="72c76-427"><xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision> Ve <xref:System.ServiceModel.Activities.CorrelationScope> etkinlikleri.</span><span class="sxs-lookup"><span data-stu-id="72c76-427">The <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, and <xref:System.ServiceModel.Activities.CorrelationScope> activities.</span></span>
  - <span data-ttu-id="72c76-428"><xref:System.ServiceModel.Activities.Receive>Etkinliğin içeriği.</span><span class="sxs-lookup"><span data-stu-id="72c76-428">The contents of the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

  - <span data-ttu-id="72c76-429">Etkinliğin hedef türü <xref:System.Activities.Statements.InvokeMethod> .</span><span class="sxs-lookup"><span data-stu-id="72c76-429">The Target Type for the <xref:System.Activities.Statements.InvokeMethod> activity.</span></span>

  - <span data-ttu-id="72c76-430">Etkinliğin özel durum açılan kutusu ve son bölümü <xref:System.Activities.Statements.TryCatch> .</span><span class="sxs-lookup"><span data-stu-id="72c76-430">The Exception combo box and the Finally section in the <xref:System.Activities.Statements.TryCatch> activity.</span></span>

  - <span data-ttu-id="72c76-431">İleti türü açılan kutusu, bağıntı başlatıcı ekleme penceresinde, içerik tanımı penceresinde ve CorrelatesOn tanımı penceresinde, ileti etkinliklerinin ( <xref:System.ServiceModel.Activities.Receive> ,, <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> ve <xref:System.ServiceModel.Activities.ReceiveReply> ).</span><span class="sxs-lookup"><span data-stu-id="72c76-431">The Message Type combo box, the splitter in the Add Correlation Initializers window, the Content Definition window, and the CorrelatesOn Definition window in the messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>

  - <span data-ttu-id="72c76-432">Durum makinesi geçişleri ve geçiş hedefleri.</span><span class="sxs-lookup"><span data-stu-id="72c76-432">State machine transitions and transitions destinations.</span></span>

  - <span data-ttu-id="72c76-433">Etkinlikler üzerinde ek açıklamalar ve bağlayıcılar <xref:System.Activities.Statements.FlowDecision> .</span><span class="sxs-lookup"><span data-stu-id="72c76-433">Annotations and connectors on <xref:System.Activities.Statements.FlowDecision> activities.</span></span>

  - <span data-ttu-id="72c76-434">Etkinlikler için bağlam (sağ tıklama) menüleri.</span><span class="sxs-lookup"><span data-stu-id="72c76-434">The context (right-click) menus for activities.</span></span>

  - <span data-ttu-id="72c76-435">Özellik değeri düzenleyicileri, aramayı temizle düğmesi, kategoriye ve alfabetik sıralama düğmelerine göre ve Özellikler kılavuzundaki Ifade Düzenleyicisi iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="72c76-435">The property value editors, the Clear Search button, the By Category and Alphabetical sort buttons, and the Expression Editor dialog in the properties grid.</span></span>

  - <span data-ttu-id="72c76-436">İş Akışı Tasarımcısı yakınlaştırma yüzdesi.</span><span class="sxs-lookup"><span data-stu-id="72c76-436">The zoom percentage in the Workflow Designer.</span></span>

  - <span data-ttu-id="72c76-437"><xref:System.Activities.Statements.Parallel>Ve <xref:System.Activities.Statements.Pick> etkinliklerindeki ayırıcı.</span><span class="sxs-lookup"><span data-stu-id="72c76-437">The separator in <xref:System.Activities.Statements.Parallel> and <xref:System.Activities.Statements.Pick> activities.</span></span>

  - <span data-ttu-id="72c76-438"><xref:System.Activities.Statements.InvokeDelegate>Etkinlik.</span><span class="sxs-lookup"><span data-stu-id="72c76-438">The <xref:System.Activities.Statements.InvokeDelegate> activity.</span></span>

  - <span data-ttu-id="72c76-439">Sözlük Etkinlikleri ( `Microsoft.Activities.AddToDictionary<TKey,TValue>` , `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>` , vb.) Için türleri seçin penceresi.</span><span class="sxs-lookup"><span data-stu-id="72c76-439">The Select Types window for dictionary activities (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, etc.).</span></span>

  - <span data-ttu-id="72c76-440">.NET tür araştır ve Seç penceresi.</span><span class="sxs-lookup"><span data-stu-id="72c76-440">The Browse and Select .NET Type window.</span></span>

  - <span data-ttu-id="72c76-441">İş Akışı Tasarımcısı içerik haritaları.</span><span class="sxs-lookup"><span data-stu-id="72c76-441">Breadcrumbs in the Workflow Designer.</span></span>

- <span data-ttu-id="72c76-442">Yüksek Karşıtlık Temaları seçen kullanıcılar, öğeler arasında daha iyi kontrast oranları ve odak öğeleri için kullanılan daha belirgin seçim kutuları gibi İş Akışı Tasarımcısı ve denetimlerinin görünürlüğünde birçok geliştirme görür.</span><span class="sxs-lookup"><span data-stu-id="72c76-442">Users who choose High Contrast themes will see many improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="72c76-443">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72c76-443">See also</span></span>

- [<span data-ttu-id="72c76-444">.NET Framework’teki yenilikler</span><span class="sxs-lookup"><span data-stu-id="72c76-444">What's new in the .NET Framework</span></span>](index.md)
