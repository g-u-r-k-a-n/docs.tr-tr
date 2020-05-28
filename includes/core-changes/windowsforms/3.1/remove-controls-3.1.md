---
ms.openlocfilehash: 6f494d9376063a7b1219ab37706f4e9d88f68993
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84145002"
---
### <a name="removed-controls"></a><span data-ttu-id="3aee3-101">Kaldırılan denetimler</span><span class="sxs-lookup"><span data-stu-id="3aee3-101">Removed controls</span></span>

<span data-ttu-id="3aee3-102">.NET Core 3,1 ' den başlayarak bazı Windows Forms denetimleri artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3aee3-102">Starting in .NET Core 3.1, some Windows Forms controls are no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3aee3-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="3aee3-103">Change description</span></span>

<span data-ttu-id="3aee3-104">.NET Core 3,1 ile başlayarak, çeşitli Windows Forms denetimleri artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3aee3-104">Starting with .NET Core 3.1, various Windows Forms controls are no longer available.</span></span> <span data-ttu-id="3aee3-105">Daha iyi tasarım ve destek içeren değiştirme denetimleri .NET Framework 2,0 ' de sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="3aee3-105">Replacement controls that have better design and support were introduced in .NET Framework 2.0.</span></span> <span data-ttu-id="3aee3-106">Kullanım dışı bırakılan denetimler daha önce Tasarımcı araç kutularından kaldırılmıştır ancak yine de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3aee3-106">The deprecated controls were previously removed from designer toolboxes but were still available to be used.</span></span>

<span data-ttu-id="3aee3-107">Aşağıdaki türler artık kullanılamaz:</span><span class="sxs-lookup"><span data-stu-id="3aee3-107">The following types are no longer available:</span></span>

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Windows.Forms.DataGrid.HitTestType>
- <xref:System.Windows.Forms.DataGridBoolColumn>
- <xref:System.Windows.Forms.DataGridCell>
- <xref:System.Windows.Forms.DataGridColumnStyle>
- <xref:System.Windows.Forms.DataGridLineStyle>
- <xref:System.Windows.Forms.DataGridParentRowsLabelStyle>
- <xref:System.Windows.Forms.DataGridPreferredColumnWidthTypeConverter>
- <xref:System.Windows.Forms.DataGridTableStyle>
- <xref:System.Windows.Forms.DataGridTextBox>
- <xref:System.Windows.Forms.DataGridTextBoxColumn>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.GridTablesFactory>
- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.IDataGridEditingService>
- <xref:System.Windows.Forms.Design.IMenuEditorService>
- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.Menu.MenuItemCollection>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.ToolBar>
- <xref:System.Windows.Forms.ToolBarAppearance>
- <xref:System.Windows.Forms.ToolBarButton>
- <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection>
- <xref:System.Windows.Forms.ToolBarButtonClickEventArgs>
- <xref:System.Windows.Forms.ToolBarButtonStyle>
- <xref:System.Windows.Forms.ToolBarTextAlign>

#### <a name="version-introduced"></a><span data-ttu-id="3aee3-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="3aee3-108">Version introduced</span></span>

<span data-ttu-id="3aee3-109">3,1</span><span class="sxs-lookup"><span data-stu-id="3aee3-109">3.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3aee3-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="3aee3-110">Recommended action</span></span>

<span data-ttu-id="3aee3-111">Her kaldırılan denetimin önerilen bir değiştirme denetimi vardır.</span><span class="sxs-lookup"><span data-stu-id="3aee3-111">Each removed control has a recommended replacement control.</span></span> <span data-ttu-id="3aee3-112">Aşağıdaki tabloya bakın:</span><span class="sxs-lookup"><span data-stu-id="3aee3-112">Refer to the following table:</span></span>

| <span data-ttu-id="3aee3-113">Kaldırılan denetim (API)</span><span class="sxs-lookup"><span data-stu-id="3aee3-113">Removed control (API)</span></span> | <span data-ttu-id="3aee3-114">Önerilen değiştirme</span><span class="sxs-lookup"><span data-stu-id="3aee3-114">Recommended replacement</span></span> | <span data-ttu-id="3aee3-115">Kaldırılan ilişkili API 'Ler</span><span class="sxs-lookup"><span data-stu-id="3aee3-115">Associated APIs that are removed</span></span> |
|-|-|-|
| <span data-ttu-id="3aee3-116">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="3aee3-116">ContextMenu</span></span> | <span data-ttu-id="3aee3-117">ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="3aee3-117">ContextMenuStrip</span></span> | |
| <span data-ttu-id="3aee3-118">DataGrid</span><span class="sxs-lookup"><span data-stu-id="3aee3-118">DataGrid</span></span> | <span data-ttu-id="3aee3-119">DataGridView</span><span class="sxs-lookup"><span data-stu-id="3aee3-119">DataGridView</span></span> | <span data-ttu-id="3aee3-120">DataGridCell, DataGridRow, DataGridTableCollection, DataGridColumnCollection, DataGridTableStyle, DataGridColumnStyle, DataGridLineStyle, DataGridParentRowsLabel, DataGridParentRowsLabelStyle, DataGridBoolColumn, DataGridTextBox, GridColumnStylesCollection, GridTableStylesCollection, HitTestType</span><span class="sxs-lookup"><span data-stu-id="3aee3-120">DataGridCell, DataGridRow, DataGridTableCollection, DataGridColumnCollection, DataGridTableStyle, DataGridColumnStyle, DataGridLineStyle, DataGridParentRowsLabel, DataGridParentRowsLabelStyle, DataGridBoolColumn, DataGridTextBox, GridColumnStylesCollection, GridTableStylesCollection, HitTestType</span></span> |
| <span data-ttu-id="3aee3-121">MainMenu</span><span class="sxs-lookup"><span data-stu-id="3aee3-121">MainMenu</span></span> | <span data-ttu-id="3aee3-122">MenuStrip</span><span class="sxs-lookup"><span data-stu-id="3aee3-122">MenuStrip</span></span> | |
| <span data-ttu-id="3aee3-123">Menü</span><span class="sxs-lookup"><span data-stu-id="3aee3-123">Menu</span></span> | <span data-ttu-id="3aee3-124">ToolStripDropDown, ToolStripDropDownMenu</span><span class="sxs-lookup"><span data-stu-id="3aee3-124">ToolStripDropDown, ToolStripDropDownMenu</span></span> | <span data-ttu-id="3aee3-125">MenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="3aee3-125">MenuItemCollection</span></span> |
| <span data-ttu-id="3aee3-126">MenuItem</span><span class="sxs-lookup"><span data-stu-id="3aee3-126">MenuItem</span></span> | <span data-ttu-id="3aee3-127">ToolStripMenuItem</span><span class="sxs-lookup"><span data-stu-id="3aee3-127">ToolStripMenuItem</span></span> | |
| <span data-ttu-id="3aee3-128">ToolBar</span><span class="sxs-lookup"><span data-stu-id="3aee3-128">ToolBar</span></span> | <span data-ttu-id="3aee3-129">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="3aee3-129">ToolStrip</span></span> | <span data-ttu-id="3aee3-130">Araç Barappearance</span><span class="sxs-lookup"><span data-stu-id="3aee3-130">ToolBarAppearance</span></span> |
| <span data-ttu-id="3aee3-131">ToolBarButton</span><span class="sxs-lookup"><span data-stu-id="3aee3-131">ToolBarButton</span></span> | <span data-ttu-id="3aee3-132">ToolStripButton</span><span class="sxs-lookup"><span data-stu-id="3aee3-132">ToolStripButton</span></span> | <span data-ttu-id="3aee3-133">Toolbarbuttonkerkeventargs, Toolbarbuttonclick Kerkeventhandler, ToolBarButtonStyle, ToolBarTextAlign</span><span class="sxs-lookup"><span data-stu-id="3aee3-133">ToolBarButtonClickEventArgs, ToolBarButtonClickEventHandler, ToolBarButtonStyle, ToolBarTextAlign</span></span>|

#### <a name="category"></a><span data-ttu-id="3aee3-134">Kategori</span><span class="sxs-lookup"><span data-stu-id="3aee3-134">Category</span></span>

<span data-ttu-id="3aee3-135">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3aee3-135">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3aee3-136">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="3aee3-136">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenu?displayProperty=nameWithType>
- <xref:System.Windows.Forms.GridColumnStylesCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.GridTablesFactory?displayProperty=nameWithType>
- <xref:System.Windows.Forms.GridTableStylesCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.IDataGridEditingService?displayProperty=nameWithType>
- <xref:System.Windows.Forms.MainMenu?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Menu?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Menu.MenuItemCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.MenuItem?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBar?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarAppearance?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarButtonClickEventArgs?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarButtonStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarTextAlign?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGrid?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGrid.HitTestType?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridBoolColumn?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridCell?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridColumnStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridLineStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridParentRowsLabelStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridPreferredColumnWidthTypeConverter?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridTableStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridTextBox?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridTextBoxColumn?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Design.IMenuEditorService?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:System.Windows.Forms.Menu`
- `T:System.Windows.Forms.Menu.MenuItemCollection`
- `T:System.Windows.Forms.MainMenu`
- `T:System.Windows.Forms.ContextMenu`
- `T:System.Windows.Forms.MenuItem`
- `T:System.Windows.Forms.ToolBar`
- `T:System.Windows.Forms.ToolBarAppearance`
- `T:System.Windows.Forms.ToolBarButton`
- `T:System.Windows.Forms.ToolBar.ToolBarButtonCollection`
- `T:System.Windows.Forms.ToolBarButtonClickEventArgs`
- `T:System.Windows.Forms.ToolBarButtonStyle`
- `T:System.Windows.Forms.ToolBarTextAlign`
- `T:System.Windows.Forms.DataGrid`
- `T:System.Windows.Forms.DataGridBoolColumn`
- `T:System.Windows.Forms.DataGridCell`
- `T:System.Windows.Forms.DataGridColumnStyle`
- `T:System.Windows.Forms.DataGridLineStyle`
- `T:System.Windows.Forms.DataGridParentRowsLabelStyle`
- `T:System.Windows.Forms.DataGridPreferredColumnWidthTypeConverter`
- `T:System.Windows.Forms.DataGridTableStyle`
- `T:System.Windows.Forms.DataGridTextBox`
- `T:System.Windows.Forms.DataGridTextBoxColumn`
- `T:System.Windows.Forms.GridColumnStylesCollection`
- `T:System.Windows.Forms.GridTablesFactory`
- `T:System.Windows.Forms.GridTableStylesCollection`
- `T:System.Windows.Forms.IDataGridEditingService`
- `T:System.Windows.Forms.DataGrid.HitTestType`
- `T:System.Windows.Forms.Design.IMenuEditorService`

-->
