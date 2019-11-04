---
title: UI Otomasyonu Tablo Denetim Düzenini Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
ms.openlocfilehash: 1fec3671f017ae6c6864537805e6c793b5f9046b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458150"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a><span data-ttu-id="cb6f9-102">UI Otomasyonu Tablo Denetim Düzenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="cb6f9-102">Implementing the UI Automation Table Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="cb6f9-103">Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="cb6f9-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="cb6f9-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="cb6f9-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="cb6f9-105">Bu konuda özellikler, Yöntemler ve olaylar hakkında bilgiler de dahil olmak üzere <xref:System.Windows.Automation.Provider.ITableProvider>uygulamak için yönergeler ve kurallar tanıtılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cb6f9-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="cb6f9-106">Ek başvuruların bağlantıları genel bakış sonunda listelenir.</span><span class="sxs-lookup"><span data-stu-id="cb6f9-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="cb6f9-107"><xref:System.Windows.Automation.TablePattern> denetim deseninin bir alt öğe koleksiyonu için kapsayıcılar olarak davranan denetimleri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cb6f9-107">The <xref:System.Windows.Automation.TablePattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="cb6f9-108">Bu öğenin alt öğeleri <xref:System.Windows.Automation.Provider.ITableItemProvider> uygulamalıdır ve satır ve sütun tarafından çapraz bir şekilde iki boyutlu bir mantıksal koordinat sisteminde düzenlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="cb6f9-108">The children of this element must implement <xref:System.Windows.Automation.Provider.ITableItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="cb6f9-109">Bu denetim deseninin <xref:System.Windows.Automation.Provider.IGridProvider>benzer şekilde, <xref:System.Windows.Automation.Provider.ITableProvider> uygulayan herhangi bir denetimin her alt öğe için bir sütun ve/veya satır üst bilgisi ilişkisi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cb6f9-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridProvider>, with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableProvider> must also expose a column and/or row header relationship for each child element.</span></span> <span data-ttu-id="cb6f9-110">Bu denetim modelini uygulayan denetimlerin örnekleri için bkz. [UI Otomasyonu istemcileri Için denetim model eşlemesi](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="cb6f9-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="cb6f9-111">Uygulama kılavuzları ve kuralları</span><span class="sxs-lookup"><span data-stu-id="cb6f9-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="cb6f9-112">Tablo denetim modelini uygularken aşağıdaki kılavuz ve kurallara göz önünde yer verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cb6f9-112">When implementing the Table control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="cb6f9-113">Tek tek hücrelerin içeriğine erişim iki boyutlu bir mantıksal koordinat sistemi veya <xref:System.Windows.Automation.Provider.IGridProvider>için gereken eşzamanlı uygulama tarafından sağlanmış dizi.</span><span class="sxs-lookup"><span data-stu-id="cb6f9-113">Access to the content of individual cells is through a two-dimensional logical coordinate system or array provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span>  
  
- <span data-ttu-id="cb6f9-114">Bir sütun veya satır üst bilgisi, tablo nesnesi içinde veya tablo nesnesiyle ilişkili ayrı bir üst bilgi nesnesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="cb6f9-114">A column or row header can be contained within a table object or be a separate header object that is associated with a table object.</span></span>  
  
- <span data-ttu-id="cb6f9-115">Sütun ve satır başlıkları hem birincil üstbilgiyi hem de tüm destekleyici üst bilgileri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="cb6f9-115">Column and row headers may include both a primary header as well as any supporting headers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb6f9-116">Bu kavram, bir kullanıcının "Ilk ad" sütunu tanımladığı bir Microsoft Excel elektronik tablosunda görünür hale gelir.</span><span class="sxs-lookup"><span data-stu-id="cb6f9-116">This concept becomes evident in a Microsoft Excel spreadsheet where a user has defined a "First name" column.</span></span> <span data-ttu-id="cb6f9-117">Bu sütunda artık iki üst bilgi vardır: Kullanıcı tarafından tanımlanan "Ilk ad" üstbilgisi ve uygulama tarafından atanan sütun için alfasayısal atama.</span><span class="sxs-lookup"><span data-stu-id="cb6f9-117">This column now has two headers—the "First name" header defined by the user and the alphanumeric designation for that column assigned by the application.</span></span>  
  
- <span data-ttu-id="cb6f9-118">İlgili kılavuz işlevselliği için [UI Otomasyonu kılavuz denetim modelini uygulama](implementing-the-ui-automation-grid-control-pattern.md) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="cb6f9-118">See [Implementing the UI Automation Grid Control Pattern](implementing-the-ui-automation-grid-control-pattern.md) for related grid functionality.</span></span>  
  
 <span data-ttu-id="cb6f9-119">![Karmaşık üstbilgi öğeleri içeren tablo.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span><span class="sxs-lookup"><span data-stu-id="cb6f9-119">![Table with complex header items.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span></span>  
<span data-ttu-id="cb6f9-120">Karmaşık sütun başlıkları içeren bir tablo örneği</span><span class="sxs-lookup"><span data-stu-id="cb6f9-120">Example of a Table with Complex Column Headers</span></span>  
  
 <span data-ttu-id="cb6f9-121">![Belirsiz Roworcolumnana özelliği olan tablo.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span><span class="sxs-lookup"><span data-stu-id="cb6f9-121">![Table with ambiguous RowOrColumnMajor property.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span></span>  
<span data-ttu-id="cb6f9-122">Belirsiz Roworcolumnana özelliği olan bir tablo örneği</span><span class="sxs-lookup"><span data-stu-id="cb6f9-122">Example of a Table with Ambiguous RowOrColumnMajor Property</span></span>  
  
<a name="Required_Members_for_ITableProvider"></a>   
## <a name="required-members-for-itableprovider"></a><span data-ttu-id="cb6f9-123">ITableProvider için gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="cb6f9-123">Required Members for ITableProvider</span></span>  
 <span data-ttu-id="cb6f9-124">ITableProvider arabirimi için aşağıdaki özellikler ve Yöntemler gereklidir.</span><span class="sxs-lookup"><span data-stu-id="cb6f9-124">The following properties and methods are required for the ITableProvider interface.</span></span>  
  
|<span data-ttu-id="cb6f9-125">Gerekli Üyeler</span><span class="sxs-lookup"><span data-stu-id="cb6f9-125">Required members</span></span>|<span data-ttu-id="cb6f9-126">Üye türü</span><span class="sxs-lookup"><span data-stu-id="cb6f9-126">Member type</span></span>|<span data-ttu-id="cb6f9-127">Notlar</span><span class="sxs-lookup"><span data-stu-id="cb6f9-127">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|<span data-ttu-id="cb6f9-128">Özellik</span><span class="sxs-lookup"><span data-stu-id="cb6f9-128">Property</span></span>|<span data-ttu-id="cb6f9-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="cb6f9-129">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|<span data-ttu-id="cb6f9-130">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cb6f9-130">Method</span></span>|<span data-ttu-id="cb6f9-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="cb6f9-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|<span data-ttu-id="cb6f9-132">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cb6f9-132">Method</span></span>|<span data-ttu-id="cb6f9-133">Yok.</span><span class="sxs-lookup"><span data-stu-id="cb6f9-133">None</span></span>|  
  
 <span data-ttu-id="cb6f9-134">Bu denetim deseninin ilişkili olayları yok.</span><span class="sxs-lookup"><span data-stu-id="cb6f9-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="cb6f9-135">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="cb6f9-135">Exceptions</span></span>  
 <span data-ttu-id="cb6f9-136">Bu denetim deseninin ilişkili özel durumları yok.</span><span class="sxs-lookup"><span data-stu-id="cb6f9-136">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb6f9-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb6f9-137">See also</span></span>

- [<span data-ttu-id="cb6f9-138">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cb6f9-138">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="cb6f9-139">UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği</span><span class="sxs-lookup"><span data-stu-id="cb6f9-139">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="cb6f9-140">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="cb6f9-140">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="cb6f9-141">UI Otomasyonu TableItem Denetim Desenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="cb6f9-141">Implementing the UI Automation TableItem Control Pattern</span></span>](implementing-the-ui-automation-tableitem-control-pattern.md)
- [<span data-ttu-id="cb6f9-142">UI Otomasyonu Grid Denetim Desenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="cb6f9-142">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="cb6f9-143">UI Otomasyon Ağacına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cb6f9-143">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="cb6f9-144">UI Otomasyonunda Önbelleğe Almayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="cb6f9-144">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
