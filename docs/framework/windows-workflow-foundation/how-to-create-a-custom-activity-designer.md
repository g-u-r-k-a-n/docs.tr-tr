---
title: 'Nasıl Yapılır: Özel Etkinlik Tasarımcısı Oluşturma'
description: Bu makalede, rastgele bir etkinliğin yerleştirilebileceği bir bırakma bölgesine sahip bir Workflow Foundation özel etkinlik Tasarımcısı oluşturma işlemi açıklanmaktadır.
ms.date: 03/30/2017
ms.assetid: 2f3aade6-facc-44ef-9657-a407ef8b9b31
ms.openlocfilehash: 015efd1e482e2b531d28b9caec411c76116c9653
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419791"
---
# <a name="how-to-create-a-custom-activity-designer"></a><span data-ttu-id="26b6c-103">Nasıl Yapılır: Özel Etkinlik Tasarımcısı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="26b6c-103">How to: Create a Custom Activity Designer</span></span>

<span data-ttu-id="26b6c-104">Özel etkinlik tasarımcıları, genellikle kendileriyle tasarım yüzeyine uygulanabilen diğer etkinliklerle ilişkili etkinliklerin birleştirilebilmesi için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="26b6c-104">Custom activity designers are typically implemented so that their associated activities are composable with other activities whose designers can be dropped on to the design surface with them.</span></span> <span data-ttu-id="26b6c-105">Bu işlevsellik, bir özel etkinlik tasarımcısının rastgele bir etkinliğin yerleştirilebileceği "bırakma bölgesi" ve ayrıca tasarım yüzeyinde oluşturulan öğe koleksiyonunu yönetme anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="26b6c-105">This functionality requires that a custom activity designer provide a "drop zone" where an arbitrary activity can be placed and also the means to manage the resulting collection of elements on the design surface.</span></span> <span data-ttu-id="26b6c-106">Bu konu, böyle bir bırakma bölgesi içeren özel bir etkinlik tasarımcısının ve tasarımcı öğelerinin toplanmasını yönetmek için gerekli olan bu işlevselliği sağlayan özel bir etkinlik tasarımcısının nasıl oluşturulacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="26b6c-106">This topic describes how to create a custom activity designer that contains such a drop zone and how to create a custom activity designer that provides that editing functionality needed to manage the collection of designer elements.</span></span>

<span data-ttu-id="26b6c-107">Özel etkinlik tasarımcıları genellikle <xref:System.Activities.Presentation.ActivityDesigner> , belirli bir tasarımcı olmadan herhangi bir etkinlik için varsayılan temel etkinlik Tasarımcısı türü olan öğesinden devralınır.</span><span class="sxs-lookup"><span data-stu-id="26b6c-107">Custom activity designers typically inherit from <xref:System.Activities.Presentation.ActivityDesigner> which is the default base activity designer type for any activities without a specific designer.</span></span> <span data-ttu-id="26b6c-108">Bu tür, Özellik kılavuzuyla etkileşim kurma ve renkleri ve simgeleri yönetme gibi temel yönleri yapılandırma gibi tasarım zamanı deneyimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="26b6c-108">This type provides the design-time experience of interacting with the property grid and configuring basic aspects such as managing colors and icons.</span></span>

<span data-ttu-id="26b6c-109"><xref:System.Activities.Presentation.ActivityDesigner>iki yardımcı denetim kullanır <xref:System.Activities.Presentation.WorkflowItemPresenter> ve <xref:System.Activities.Presentation.WorkflowItemsPresenter> özel etkinlik tasarımcıları geliştirmeyi kolaylaştırmak için.</span><span class="sxs-lookup"><span data-stu-id="26b6c-109"><xref:System.Activities.Presentation.ActivityDesigner> uses two helper controls, <xref:System.Activities.Presentation.WorkflowItemPresenter> and <xref:System.Activities.Presentation.WorkflowItemsPresenter> to make it easier to develop custom activity designers.</span></span> <span data-ttu-id="26b6c-110">Alt öğeleri sürükleme ve bırakma, silme, seçme ve bu alt öğelerin eklenmesi gibi yaygın işlevleri ele alırlar.</span><span class="sxs-lookup"><span data-stu-id="26b6c-110">They handle common functionality like dragging and dropping of child elements, deletion, selection, and addition of those child elements.</span></span> <span data-ttu-id="26b6c-111">, <xref:System.Activities.Presentation.WorkflowItemPresenter> "Bırakma bölgesi" sağlayan içinde tek bir alt Kullanıcı arabirimi öğesine izin verir, ancak, <xref:System.Activities.Presentation.WorkflowItemsPresenter> alt öğeleri sıralama, taşıma, silme ve ekleme gibi ek işlevler de dahil olmak üzere bırden çok UI öğesini destekler.</span><span class="sxs-lookup"><span data-stu-id="26b6c-111">The <xref:System.Activities.Presentation.WorkflowItemPresenter> allows a single child UI element inside, providing the "drop zone", it while the <xref:System.Activities.Presentation.WorkflowItemsPresenter> can provide support multiple UI elements, including additional functionality like the ordering, moving, deleting, and adding of child elements.</span></span>

<span data-ttu-id="26b6c-112">Hikayenin özel bir etkinlik Tasarımcısı uygulamasında vurgulanması gereken diğer anahtar bölümü görsel düzenlemelerin, tasarımcıda düzenlemekte olduğumuz bellekte depolanan örneğe WPF veri bağlama kullanılarak nasıl ilişkili olduğu konusunda kaygılara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="26b6c-112">The other key part of the story that needs highlighting in the implementation of a custom activity designer concerns the way in which the visual edits are bound using WPF data binding to the instance stored in memory of what we are editing in the designer.</span></span> <span data-ttu-id="26b6c-113">Bu, değişiklik bildirimini etkinleştirme ve durumlardaki değişiklikler gibi olayların izlenmesini de sorumlu olan model öğe ağacı tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="26b6c-113">This is accomplished by the Model Item tree, which is also responsible for enabling change notification and the tracking of events like changes in states.</span></span>

<span data-ttu-id="26b6c-114">Bu konuda iki yordam özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="26b6c-114">This topic outlines two procedures.</span></span>

1. <span data-ttu-id="26b6c-115">İlk yordam, <xref:System.Activities.Presentation.WorkflowItemPresenter> diğer etkinlikleri alan bırakma bölgesini sağlayan, ile özel bir etkinlik tasarımcısının nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="26b6c-115">The first procedure describes how to create a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter> that provides the drop zone that receives other activities.</span></span> <span data-ttu-id="26b6c-116">Bu yordam, [özel bileşik tasarımcılar-Iş akışı öğe sunum](./samples/custom-composite-designers-workflow-item-presenter.md) örneğine dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="26b6c-116">This procedure is based on the [Custom Composite Designers - Workflow Item Presenter](./samples/custom-composite-designers-workflow-item-presenter.md) sample.</span></span>

2. <span data-ttu-id="26b6c-117">İkinci yordam, <xref:System.Activities.Presentation.WorkflowItemsPresenter> içerilen öğelerin bir koleksiyonunu düzenlemek için gereken işlevselliği sağlayan, ile özel bir etkinlik tasarımcısının nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="26b6c-117">The second procedure describes how to create a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter> that provides the functionality needed to edit of a collection of contained elements.</span></span> <span data-ttu-id="26b6c-118">Bu yordam, [özel bileşik tasarımcılar-Iş akışı öğeleri sunan](./samples/custom-composite-designers-workflow-items-presenter.md) örneğine dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="26b6c-118">This procedure is based on the [Custom Composite Designers - Workflow Items Presenter](./samples/custom-composite-designers-workflow-items-presenter.md) sample.</span></span>

## <a name="to-create-a-custom-activity-designer-with-a-drop-zone-using-workflowitempresenter"></a><span data-ttu-id="26b6c-119">Workflowwıtempresenter kullanarak bir bırakma bölgesi ile özel bir etkinlik Tasarımcısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="26b6c-119">To create a custom activity designer with a drop zone using WorkflowItemPresenter</span></span>

1. <span data-ttu-id="26b6c-120">Visual Studio 2010 ' i başlatın.</span><span class="sxs-lookup"><span data-stu-id="26b6c-120">Start Visual Studio 2010.</span></span>

2. <span data-ttu-id="26b6c-121">**Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **proje...** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="26b6c-121">On the **File** menu, point to **New**, and then select **Project…**.</span></span>

     <span data-ttu-id="26b6c-122">**Yeni proje** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="26b6c-122">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="26b6c-123">**Yüklü şablonlar** bölmesinde, tercih ettiğiniz dil kategorisinden **Windows** ' u seçin.</span><span class="sxs-lookup"><span data-stu-id="26b6c-123">In the **Installed Templates** pane, select **Windows** from your preferred language category.</span></span>

4. <span data-ttu-id="26b6c-124">**Şablonlar** bölmesinde **WPF uygulaması**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="26b6c-124">In the **Templates** pane, select **WPF Application**.</span></span>

5. <span data-ttu-id="26b6c-125">**Ad** kutusuna girin `UsingWorkflowItemPresenter` .</span><span class="sxs-lookup"><span data-stu-id="26b6c-125">In the **Name** box, enter `UsingWorkflowItemPresenter`.</span></span>

6. <span data-ttu-id="26b6c-126">**Konum** kutusunda, projenizi kaydetmek istediğiniz dizini girin veya git ' e tıklayarak bu dosyayı **gösterin** .</span><span class="sxs-lookup"><span data-stu-id="26b6c-126">In the **Location** box, enter the directory in which you want to save your project, or click **Browse** to navigate to it.</span></span>

7. <span data-ttu-id="26b6c-127">**Çözüm** kutusunda, varsayılan değeri kabul edin.</span><span class="sxs-lookup"><span data-stu-id="26b6c-127">In the **Solution** box, accept the default value.</span></span>

8. <span data-ttu-id="26b6c-128">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="26b6c-128">Click **OK**.</span></span>

9. <span data-ttu-id="26b6c-129">**Çözüm Gezgini** *MainWindows. xaml* dosyasına sağ tıklayın, **sil** ' i seçin ve **Microsoft Visual Studio** iletişim kutusunda **Tamam** ' ı onaylayın.</span><span class="sxs-lookup"><span data-stu-id="26b6c-129">Right-click the *MainWindows.xaml* file in the **Solution Explorer**, select **Delete** and confirm **OK** in the **Microsoft Visual Studio** dialog box.</span></span>

10. <span data-ttu-id="26b6c-130">**Çözüm Gezgini**' de Usingworkflowwitempresenter projesine sağ tıklayın, **Ekle**' yi ve ardından **Yeni öğe...** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="26b6c-130">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="26b6c-131">**Yeni öğe Ekle** iletişim kutusunu açmak için sol taraftaki **yüklü şablonlar** bölümünden **WPF** kategorisini seçin.</span><span class="sxs-lookup"><span data-stu-id="26b6c-131">to bring up the **Add New Item** dialog and select the **WPF** category from the **Installed Templates** section on the left.</span></span>

11. <span data-ttu-id="26b6c-132">**Pencere (WPF)** şablonunu seçin, adlandırın `RehostingWFDesigner` ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="26b6c-132">Select the  **Window (WPF)** template, name it `RehostingWFDesigner`, and click **Add**.</span></span>

12. <span data-ttu-id="26b6c-133">*RehostingWFDesigner. xaml* dosyasını açın ve uygulama için Kullanıcı arabirimini tanımlamak üzere aşağıdaki kodu buraya yapıştırın:</span><span class="sxs-lookup"><span data-stu-id="26b6c-133">Open the *RehostingWFDesigner.xaml* file and paste the following code into it to define the UI for the application:</span></span>

    ```xaml
    <Window x:Class=" UsingWorkflowItemPresenter.RehostingWFDesigner"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:sapt="clr-namespace:System.Activities.Presentation.Toolbox;assembly=System.Activities.Presentation"
            xmlns:sys="clr-namespace:System;assembly=mscorlib"
            Title="Window1" Height="600" Width="900">
        <Window.Resources>
            <sys:String x:Key="AssemblyName">System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</sys:String>
        </Window.Resources>
        <Grid>
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="2*"/>
                <ColumnDefinition Width="7*"/>
                <ColumnDefinition Width="3*"/>
            </Grid.ColumnDefinitions>
            <Border Grid.Column="0">
                <sapt:ToolboxControl Name="Toolbox">
                    <sapt:ToolboxCategory CategoryName="Basic">
                        <sapt:ToolboxItemWrapper AssemblyName="{StaticResource AssemblyName}" >
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.Sequence
                            </sapt:ToolboxItemWrapper.ToolName>
                           </sapt:ToolboxItemWrapper>
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.WriteLine
                            </sapt:ToolboxItemWrapper.ToolName>

                        </sapt:ToolboxItemWrapper>
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.If
                            </sapt:ToolboxItemWrapper.ToolName>

                        </sapt:ToolboxItemWrapper>
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.While
                            </sapt:ToolboxItemWrapper.ToolName>

                        </sapt:ToolboxItemWrapper>
                    </sapt:ToolboxCategory>
                </sapt:ToolboxControl>
            </Border>
            <Border Grid.Column="1" Name="DesignerBorder"/>
            <Border Grid.Column="2" Name="PropertyBorder"/>
        </Grid>
    </Window>
    ```

13. <span data-ttu-id="26b6c-134">Etkinlik tasarımcısını bir etkinlik türüyle ilişkilendirmek için, bu etkinlik tasarımcısını meta veri deposu ile kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="26b6c-134">To associate an activity designer with an activity type, you must register that activity designer with the metadata store.</span></span> <span data-ttu-id="26b6c-135">Bunu yapmak için `RegisterMetadata` yöntemini `RehostingWFDesigner` sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="26b6c-135">To do this, add the `RegisterMetadata` method to the `RehostingWFDesigner` class.</span></span> <span data-ttu-id="26b6c-136">Yönteminin kapsamı içinde `RegisterMetadata` , bir <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> nesnesi oluşturun ve <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> öznitelikleri eklemek için yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="26b6c-136">Within the scope of the  `RegisterMetadata` method, create an <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> object and call the <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> method to add the attributes to it.</span></span> <span data-ttu-id="26b6c-137"><xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A>Meta veri deposuna eklemek için yöntemini çağırın <xref:System.Activities.Presentation.Metadata.AttributeTable> .</span><span class="sxs-lookup"><span data-stu-id="26b6c-137">Call the <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> method to add the <xref:System.Activities.Presentation.Metadata.AttributeTable> to the metadata store.</span></span> <span data-ttu-id="26b6c-138">Aşağıdaki kod, tasarımcı için yeniden barındırma mantığını içerir.</span><span class="sxs-lookup"><span data-stu-id="26b6c-138">The following code contains the rehosting logic for the designer.</span></span> <span data-ttu-id="26b6c-139">Meta verileri kaydeder, `SimpleNativeActivity` araç kutusuna koyar ve iş akışını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="26b6c-139">It registers the metadata, puts the `SimpleNativeActivity` into the toolbox, and creates the workflow.</span></span> <span data-ttu-id="26b6c-140">Bu kodu *RehostingWFDesigner.xaml.cs* dosyasına koyun.</span><span class="sxs-lookup"><span data-stu-id="26b6c-140">Put this code into the *RehostingWFDesigner.xaml.cs* file.</span></span>

    ```csharp
    using System;
    using System.Activities.Core.Presentation;
    using System.Activities.Presentation;
    using System.Activities.Presentation.Metadata;
    using System.Activities.Presentation.Toolbox;
    using System.Activities.Statements;
    using System.ComponentModel;
    using System.Windows;

    namespace UsingWorkflowItemPresenter
    {
        // Interaction logic for RehostingWFDesigner.xaml
        public partial class RehostingWFDesigner
        {
            public RehostingWFDesigner()
            {
                InitializeComponent();
            }

            protected override void OnInitialized(EventArgs e)
            {
                base.OnInitialized(e);
                // Register metadata.
                (new DesignerMetadata()).Register();
                RegisterCustomMetadata();
                // Add custom activity to toolbox.
                Toolbox.Categories.Add(new ToolboxCategory("Custom activities"));
                Toolbox.Categories[1].Add(new ToolboxItemWrapper(typeof(SimpleNativeActivity)));

                // Create the workflow designer.
                var wd = new WorkflowDesigner();
                wd.Load(new Sequence());
                DesignerBorder.Child = wd.View;
                PropertyBorder.Child = wd.PropertyInspectorView;

            }

            void RegisterCustomMetadata()
            {
                var builder = new AttributeTableBuilder();
                builder.AddCustomAttributes(typeof(SimpleNativeActivity), new DesignerAttribute(typeof(SimpleNativeDesigner)));
                MetadataStore.AddAttributeTable(builder.CreateTable());
            }
        }
    }
    ```

14. <span data-ttu-id="26b6c-141">Çözüm Gezgini ' deki başvurular dizinine sağ tıklayın ve **Başvuru Ekle...** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="26b6c-141">Right-click the References directory in Solution Explorer and select **Add Reference …**</span></span> <span data-ttu-id="26b6c-142">**Başvuru Ekle** iletişim kutusunu açmak için.</span><span class="sxs-lookup"><span data-stu-id="26b6c-142">to bring up the **Add Reference** dialog.</span></span>

15. <span data-ttu-id="26b6c-143">**.Net** sekmesine tıklayın, **System. Activities. Core. Presentation**adlı derlemeyi bulun, seçin ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="26b6c-143">Click the **.NET** tab, locate the assembly named **System.Activities.Core.Presentation**, select it and click **OK**.</span></span>

16. <span data-ttu-id="26b6c-144">Aynı yordamı kullanarak, aşağıdaki derlemelere başvurular ekleyin:</span><span class="sxs-lookup"><span data-stu-id="26b6c-144">Using the same procedure, add references to the following assemblies:</span></span>

    1. <span data-ttu-id="26b6c-145">System. Data. Datase, sions. dll</span><span class="sxs-lookup"><span data-stu-id="26b6c-145">System.Data.DataSetExtensions.dll</span></span>

    2. <span data-ttu-id="26b6c-146">System. Activities. Presentation. dll</span><span class="sxs-lookup"><span data-stu-id="26b6c-146">System.Activities.Presentation.dll</span></span>

    3. <span data-ttu-id="26b6c-147">System. ServiceModel. Activities. dll</span><span class="sxs-lookup"><span data-stu-id="26b6c-147">System.ServiceModel.Activities.dll</span></span>

17. <span data-ttu-id="26b6c-148">*App. xaml* dosyasını açın ve StartupUri değerini "RehostingWFDesigner. xaml" olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="26b6c-148">Open the *App.xaml* file and change the value of the StartUpUri to "RehostingWFDesigner.xaml".</span></span>

18. <span data-ttu-id="26b6c-149">**Çözüm Gezgini**' de Usingworkflowwitempresenter projesine sağ tıklayın, **Ekle**' yi ve ardından **Yeni öğe...** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="26b6c-149">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="26b6c-150">**Yeni öğe Ekle** iletişim kutusunu açmak için sol taraftaki **yüklü şablonlar** bölümüne **iş akışı** kategorisi formunu seçin.</span><span class="sxs-lookup"><span data-stu-id="26b6c-150">to bring up the **Add New Item** dialog and select the **Workflow** category form the **Installed Templates** section on the left.</span></span>

19. <span data-ttu-id="26b6c-151">**Etkinlik Tasarımcısı** şablonunu seçin, adlandırın `SimpleNativeDesigner` ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="26b6c-151">Select the **Activity Designer** template, name it `SimpleNativeDesigner`, and click **Add**.</span></span>

20. <span data-ttu-id="26b6c-152">*SimpleNativeDesigner. xaml* dosyasını açın ve aşağıdaki kodu içine yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="26b6c-152">Open the *SimpleNativeDesigner.xaml* file and paste the following code into it.</span></span> <span data-ttu-id="26b6c-153">Bu kod <xref:System.Activities.Presentation.ActivityDesigner> , kök öğesi olarak kullanır ve <xref:System.Activities.Presentation.WorkflowItemPresenter> bileşik etkinlik tasarımcısında bir alt türün görüntülenebilmesi için bir bağlamanın tasarımcı ile tümleştirme için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="26b6c-153">Note this code uses <xref:System.Activities.Presentation.ActivityDesigner> as your root element and shows how binding is used to integrate <xref:System.Activities.Presentation.WorkflowItemPresenter> into your designer so a child type can be displayed in your composite activity designer.</span></span>

    > [!NOTE]
    > <span data-ttu-id="26b6c-154">Şeması, <xref:System.Activities.Presentation.ActivityDesigner> özel etkinlik Tasarımcısı tanımınıza yalnızca bir alt öğe eklenmesini sağlar; ancak, bu öğe bir `StackPanel` , `Grid` veya başka bir bileşik Kullanıcı arabirimi öğesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="26b6c-154">The schema for <xref:System.Activities.Presentation.ActivityDesigner> allows the addition of only one child element to your custom activity designer definition; however, this element could be a `StackPanel`, `Grid`, or some other composite UI element.</span></span>

    ```xaml
    <sap:ActivityDesigner x:Class=" UsingWorkflowItemPresenter.SimpleNativeDesigner"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
        <sap:ActivityDesigner.Resources>
            <DataTemplate x:Key="Collapsed">
                <StackPanel>
                    <TextBlock>This is the collapsed view</TextBlock>
                </StackPanel>
            </DataTemplate>
            <DataTemplate x:Key="Expanded">
                <StackPanel>
                    <TextBlock>Custom Text</TextBlock>
                    <sap:WorkflowItemPresenter Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"
                                            HintText="Please drop an activity here" />
                </StackPanel>
            </DataTemplate>
            <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
                <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
                <Style.Triggers>
                    <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">
                        <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
                    </DataTrigger>
                </Style.Triggers>
            </Style>
        </sap:ActivityDesigner.Resources>
        <Grid>
            <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}" />
        </Grid>
    </sap:ActivityDesigner>
    ```

21. <span data-ttu-id="26b6c-155">**Çözüm Gezgini**' de Usingworkflowwitempresenter projesine sağ tıklayın, **Ekle**' yi ve ardından **Yeni öğe...** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="26b6c-155">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="26b6c-156">**Yeni öğe Ekle** iletişim kutusunu açmak için sol taraftaki **yüklü şablonlar** bölümüne **iş akışı** kategorisi formunu seçin.</span><span class="sxs-lookup"><span data-stu-id="26b6c-156">to bring up the **Add New Item** dialog and select the **Workflow** category form the **Installed Templates** section on the left.</span></span>

22. <span data-ttu-id="26b6c-157">**Kod etkinlik** şablonunu seçin, adlandırın `SimpleNativeActivity` ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="26b6c-157">Select the  **Code Activity** template, name it `SimpleNativeActivity`, and click **Add**.</span></span>

23. <span data-ttu-id="26b6c-158">`SimpleNativeActivity` *SimpleNativeActivity.cs* dosyasına aşağıdaki kodu girerek sınıfı uygulayın:</span><span class="sxs-lookup"><span data-stu-id="26b6c-158">Implement the `SimpleNativeActivity` class by entering the following code into the *SimpleNativeActivity.cs* file:</span></span>

    ```csharp
    using System.Activities;

    namespace UsingWorkflowItemPresenter
    {
        public sealed class SimpleNativeActivity : NativeActivity
        {
            // this property contains an activity that will be scheduled in the execute method
            // the WorkflowItemPresenter in the designer is bound to this to enable editing
            // of the value
            public Activity Body { get; set; }

            protected override void CacheMetadata(NativeActivityMetadata metadata)
            {
               metadata.AddChild(Body);
               base.CacheMetadata(metadata);

            }

            protected override void Execute(NativeActivityContext context)
            {
                context.ScheduleActivity(Body);
            }
        }
    }
    ```

24. <span data-ttu-id="26b6c-159">**Build** menüsünden **Build Solution** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="26b6c-159">Select **Build Solution** from the **Build** menu.</span></span>

25. <span data-ttu-id="26b6c-160">Yeniden barındırılan özel tasarım penceresini açmak için **hata ayıklama** menüsünden **hata ayıklama olmadan Başlat** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="26b6c-160">Select **Start Without Debugging** from the **Debug** menu to open the rehosted custom design window.</span></span>

### <a name="to-create-a-custom-activity-designer-using-workflowitemspresenter"></a><span data-ttu-id="26b6c-161">Workflowwitemspresenter kullanarak özel bir etkinlik Tasarımcısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="26b6c-161">To create a custom activity designer using WorkflowItemsPresenter</span></span>

1. <span data-ttu-id="26b6c-162">İkinci özel etkinlik tasarımcısına yönelik yordam, ilki ikinci uygulamayı ilk kez adlandırmak olan birkaç değişiklik ile ilk olarak paraleldir `UsingWorkflowItemsPresenter` .</span><span class="sxs-lookup"><span data-stu-id="26b6c-162">The procedure for the second custom activity designer is the parallels the first with a few modifications, the first of which is to name the second application `UsingWorkflowItemsPresenter`.</span></span> <span data-ttu-id="26b6c-163">Ayrıca, bu uygulama yeni bir özel etkinlik tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="26b6c-163">Also this application does not define a new custom activity.</span></span>

2. <span data-ttu-id="26b6c-164">Önemli farklılıklar, *CustomParallelDesigner. xaml* ve *RehostingWFDesigner.xaml.cs* dosyalarında yer alır.</span><span class="sxs-lookup"><span data-stu-id="26b6c-164">Key differences are contained in the *CustomParallelDesigner.xaml* and *RehostingWFDesigner.xaml.cs* files.</span></span> <span data-ttu-id="26b6c-165">Kullanıcı arabirimini tanımlayan *CustomParallelDesigner. xaml* dosyasındaki kod aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="26b6c-165">Here is the code from the *CustomParallelDesigner.xaml* file that defines the UI:</span></span>

    ```xaml
    <sap:ActivityDesigner x:Class=" UsingWorkflowItemsPresenter.CustomParallelDesigner"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
        <sap:ActivityDesigner.Resources>
            <DataTemplate x:Key="Collapsed">
                <TextBlock>This is the Collapsed View</TextBlock>
            </DataTemplate>
            <DataTemplate x:Key="Expanded">
                <StackPanel>
                    <TextBlock HorizontalAlignment="Center">This is the</TextBlock>
                    <TextBlock HorizontalAlignment="Center">extended view</TextBlock>
                    <sap:WorkflowItemsPresenter HintText="Drop Activities Here"
                                        Items="{Binding Path=ModelItem.Branches}">
                        <sap:WorkflowItemsPresenter.SpacerTemplate>
                            <DataTemplate>
                                <Ellipse Width="10" Height="10" Fill="Black"/>
                            </DataTemplate>
                        </sap:WorkflowItemsPresenter.SpacerTemplate>
                        <sap:WorkflowItemsPresenter.ItemsPanel>
                            <ItemsPanelTemplate>
                                <StackPanel Orientation="Horizontal"/>
                            </ItemsPanelTemplate>
                        </sap:WorkflowItemsPresenter.ItemsPanel>
                    </sap:WorkflowItemsPresenter>
                </StackPanel>
            </DataTemplate>
            <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
                <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
                <Style.Triggers>
                    <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">
                        <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
                    </DataTrigger>
                </Style.Triggers>
            </Style>
        </sap:ActivityDesigner.Resources>
        <Grid>
            <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}"/>
        </Grid>
    </sap:ActivityDesigner>
    ```

3. <span data-ttu-id="26b6c-166">Yeniden barındırma mantığını sağlayan *RehostingWFDesigner.xaml.cs* dosyasındaki kod aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="26b6c-166">Here is the code from the *RehostingWFDesigner.xaml.cs* file that provides the rehosting logic:</span></span>

    ```csharp
    using System;
    using System.Activities.Core.Presentation;
    using System.Activities.Presentation;
    using System.Activities.Presentation.Metadata;
    using System.Activities.Statements;
    using System.ComponentModel;
    using System.Windows;

    namespaceUsingWorkflowItemsPresenter
    {
        public partial class RehostingWfDesigner : Window
        {
            public RehostingWfDesigner()
            {
                InitializeComponent();
            }

            protected override void OnInitialized(EventArgs e)
            {
                base.OnInitialized(e);
                // Register metadata.
                (new DesignerMetadata()).Register();
                RegisterCustomMetadata();

                // Create the workflow designer.
                var wd = new WorkflowDesigner();
                wd.Load(new Sequence());
                DesignerBorder.Child = wd.View;
                PropertyBorder.Child = wd.PropertyInspectorView;

            }

            void RegisterCustomMetadata()
            {
                var builder = new AttributeTableBuilder();
                builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));
                MetadataStore.AddAttributeTable(builder.CreateTable());
            }
        }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="26b6c-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26b6c-167">See also</span></span>

- <xref:System.Activities.Presentation.ActivityDesigner>
- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- <xref:System.Activities.Presentation.WorkflowViewElement>
- <xref:System.Activities.Presentation.Model.ModelItem>
- [<span data-ttu-id="26b6c-168">İş Akışı Tasarım Deneyimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="26b6c-168">Customizing the Workflow Design Experience</span></span>](customizing-the-workflow-design-experience.md)
