---
title: 'İzlenecek yol: WPF İçeriği için Stil Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Designer [Windows Forms], styling WPF content
- interoperability [WDF]
- styles [Windows Forms], WPF content
ms.assetid: e574aac7-7ea4-4cdb-8034-bab541f000df
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 581fcbfdfd7806b8f0f70347ac96f1bf09fa9098
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460940"
---
# <a name="walkthrough-style-wpf-content"></a><span data-ttu-id="7a978-102">İzlenecek yol: biçim WPF içeriği</span><span class="sxs-lookup"><span data-stu-id="7a978-102">Walkthrough: Style WPF content</span></span>

<span data-ttu-id="7a978-103">Bu makalede, bir Windows formunda barındırılan bir Windows Presentation Foundation (WPF) denetimine stil uygulamayı nasıl uygulayacağınız gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7a978-103">This article show you how to apply styling to a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7a978-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="7a978-104">Prerequisites</span></span>

<span data-ttu-id="7a978-105">Bu yönergeyi tamamlamak için Visual Studio gerekir.</span><span class="sxs-lookup"><span data-stu-id="7a978-105">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="7a978-106">Projeyi oluşturma</span><span class="sxs-lookup"><span data-stu-id="7a978-106">Create the project</span></span>

<span data-ttu-id="7a978-107">Visual Studio 'Yu açın ve Visual Basic veya görsel C# adlı `StylingWpfContent`Windows Forms uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7a978-107">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `StylingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="7a978-108">WPF içeriği barındırırken yalnızca C# ve Visual Basic projeleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="7a978-108">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="7a978-109">WPF denetim türlerini oluşturma</span><span class="sxs-lookup"><span data-stu-id="7a978-109">Create the WPF control types</span></span>

<span data-ttu-id="7a978-110">Projeye bir WPF denetim türü ekledikten sonra, bunu bir <xref:System.Windows.Forms.Integration.ElementHost> denetiminde barındırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a978-110">After you add a WPF control type to the project, you can host it in an <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span>

1. <span data-ttu-id="7a978-111">Çözüme yeni bir WPF <xref:System.Windows.Controls.UserControl> projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7a978-111">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="7a978-112">Denetim türü için varsayılan adı kullanın, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="7a978-112">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="7a978-113">Daha fazla bilgi için bkz. [Izlenecek yol: tasarım zamanında Windows Forms yenı WPF Içeriği oluşturma](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="7a978-113">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="7a978-114">Tasarım görünümü ' de `UserControl1` ' nin seçili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="7a978-114">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="7a978-115">**Özellikler** penceresinde <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerinin değerini **200**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7a978-115">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="7a978-116"><xref:System.Windows.Controls.UserControl> <xref:System.Windows.Controls.Button?displayProperty=nameWithType> bir denetim ekleyin ve <xref:System.Windows.Controls.ContentControl.Content%2A> özelliğinin değerini **iptal**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7a978-116">Add a <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **Cancel**.</span></span>

5. <span data-ttu-id="7a978-117"><xref:System.Windows.Controls.UserControl> ikinci bir <xref:System.Windows.Controls.Button?displayProperty=nameWithType> denetimi ekleyin ve <xref:System.Windows.Controls.ContentControl.Content%2A> özelliğinin değerini **Tamam**olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7a978-117">Add a second <xref:System.Windows.Controls.Button?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.ContentControl.Content%2A> property to **OK**.</span></span>

6. <span data-ttu-id="7a978-118">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7a978-118">Build the project.</span></span>

## <a name="apply-a-style-to-a-wpf-control"></a><span data-ttu-id="7a978-119">WPF denetimine stil uygulama</span><span class="sxs-lookup"><span data-stu-id="7a978-119">Apply a Style to a WPF Control</span></span>

<span data-ttu-id="7a978-120">Görünümünü ve davranışını değiştirmek için WPF denetimine farklı stil uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7a978-120">You can apply different styling to a WPF control to change its appearance and behavior.</span></span>

1. <span data-ttu-id="7a978-121">Windows Form Tasarımcısı `Form1` açın.</span><span class="sxs-lookup"><span data-stu-id="7a978-121">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="7a978-122">**Araç kutusunda**`UserControl1` ' ye çift tıklayarak formda `UserControl1` bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7a978-122">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

   <span data-ttu-id="7a978-123">`UserControl1` örneği, `elementHost1`adlı yeni bir <xref:System.Windows.Forms.Integration.ElementHost> denetiminde barındırılır.</span><span class="sxs-lookup"><span data-stu-id="7a978-123">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

1. <span data-ttu-id="7a978-124">`elementHost1`için akıllı etiket panelinde, açılan listeden **barındırılan Içeriği Düzenle** ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7a978-124">In the smart tag panel for `elementHost1`, click **Edit Hosted Content** from the drop-down list.</span></span>

   <span data-ttu-id="7a978-125">`UserControl1` WPF tasarımcısında açılır.</span><span class="sxs-lookup"><span data-stu-id="7a978-125">`UserControl1` opens in the WPF Designer.</span></span>

1. <span data-ttu-id="7a978-126">XAML görünümü ' nde, `<UserControl>` açýlýþ etiketinden sonra aşağıdaki XAML 'yi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7a978-126">In XAML view, insert the following XAML after the `<UserControl>` opening tag.</span></span> <span data-ttu-id="7a978-127">Bu XAML, çakışan gradyan kenarlığı olan bir gradyan oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7a978-127">This XAML creates a gradient with a contrasting gradient border.</span></span> <span data-ttu-id="7a978-128">Denetime tıklandığında degradeler, basılan düğme görünümü oluşturacak şekilde değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="7a978-128">When the control is clicked, the gradients are changed to generate a pressed button look.</span></span> <span data-ttu-id="7a978-129">Daha fazla bilgi için bkz. [Stil oluşturma ve şablon](../../wpf/controls/styling-and-templating.md)oluşturma.</span><span class="sxs-lookup"><span data-stu-id="7a978-129">For more information, see [Styling and Templating](../../wpf/controls/styling-and-templating.md).</span></span>

   ```xaml
   <UserControl.Resources>
    <LinearGradientBrush x:Key="NormalBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#FFF" Offset="0.0"/>
        <GradientStop Color="#CCC" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="PressedBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#BBB" Offset="0.0"/>
        <GradientStop Color="#EEE" Offset="0.1"/>
        <GradientStop Color="#EEE" Offset="0.9"/>
        <GradientStop Color="#FFF" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="NormalBorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#CCC" Offset="0.0"/>
        <GradientStop Color="#444" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="BorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#CCC" Offset="0.0"/>
        <GradientStop Color="#444" Offset="1.0"/>
    </LinearGradientBrush>
    <LinearGradientBrush x:Key="PressedBorderBrush" EndPoint="0,1" StartPoint="0,0">
        <GradientStop Color="#444" Offset="0.0"/>
        <GradientStop Color="#888" Offset="1.0"/>
    </LinearGradientBrush>

    <Style x:Key="SimpleButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="Background" Value="{StaticResource NormalBrush}"/>
        <Setter Property="BorderBrush" Value="{StaticResource NormalBorderBrush}"/>
        <Setter Property="Template">
            <Setter.Value>
                <ControlTemplate TargetType="{x:Type Button}">
                    <Grid x:Name="Grid">
                        <Border x:Name="Border" Background="{TemplateBinding Background}" BorderBrush="{TemplateBinding BorderBrush}" BorderThickness="{TemplateBinding BorderThickness}" Padding="{TemplateBinding Padding}"/>
                        <ContentPresenter HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="{TemplateBinding Padding}" VerticalAlignment="{TemplateBinding VerticalContentAlignment}" RecognizesAccessKey="True"/>
                    </Grid>
                    <ControlTemplate.Triggers>
                        <Trigger Property="IsPressed" Value="true">
                            <Setter Property="Background" Value="{StaticResource PressedBrush}" TargetName="Border"/>
                            <Setter Property="BorderBrush" Value="{StaticResource PressedBorderBrush}" TargetName="Border"/>
                        </Trigger>
                    </ControlTemplate.Triggers>
                </ControlTemplate>
            </Setter.Value>
        </Setter>
    </Style>
   </UserControl.Resources>
   ```

1. <span data-ttu-id="7a978-130">Aşağıdaki XAML 'yi **iptal** düğmesinin `<Button>` etiketine ekleyerek, önceki adımda tanımlanan `SimpleButton` stilini iptal düğmesine uygulayın.</span><span class="sxs-lookup"><span data-stu-id="7a978-130">Apply the `SimpleButton` style defined in the previous step to the Cancel button by inserting the following XAML in the `<Button>` tag of the **Cancel** button.</span></span>

   ```xaml
   Style="{StaticResource SimpleButton}
   ```

   <span data-ttu-id="7a978-131">Düğme bildirimidir aşağıdaki XAML 'ye benzeyecektir:</span><span class="sxs-lookup"><span data-stu-id="7a978-131">Your button declaration will resemble the following XAML:</span></span>

   ```xaml
   <Button Height="23" Margin="41,52,98,0" Name="button1" VerticalAlignment="Top"
                Style="{StaticResource SimpleButton}">Cancel</Button>
   ```

1. <span data-ttu-id="7a978-132">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7a978-132">Build the project.</span></span>

1. <span data-ttu-id="7a978-133">Windows Form Tasarımcısı `Form1` açın.</span><span class="sxs-lookup"><span data-stu-id="7a978-133">Open `Form1` in the Windows Forms Designer.</span></span>

1. <span data-ttu-id="7a978-134">Yeni stil düğme denetimine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7a978-134">The new style is applied to the button control.</span></span>

1. <span data-ttu-id="7a978-135">**Hata Ayıkla** menüsünde, **hata ayıklamayı Başlat** ' ı seçerek uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7a978-135">From the **Debug** menu, select **Start Debugging** to run the application.</span></span>

1. <span data-ttu-id="7a978-136">**Tamam** ve **iptal** düğmelerini tıklatın ve farkları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="7a978-136">Click the **OK** and **Cancel** buttons and view the differences.</span></span>

## <a name="see-also"></a><span data-ttu-id="7a978-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a978-137">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="7a978-138">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="7a978-138">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="7a978-139">WPF Denetimlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="7a978-139">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="7a978-140">Visual Studio’da XAML tasarlama</span><span class="sxs-lookup"><span data-stu-id="7a978-140">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="7a978-141">XAML'ye Genel Bakış (WPF)</span><span class="sxs-lookup"><span data-stu-id="7a978-141">XAML Overview (WPF)</span></span>](../../wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="7a978-142">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7a978-142">Styling and Templating</span></span>](../../wpf/controls/styling-and-templating.md)
