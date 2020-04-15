---
title: 'Nasıl yapılır: BindingSource ve INotifyPropertyChanged Arabirimini Kullanarak Değişiklik Bildirimleri Verme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- change notifications [Windows Forms], raising
- BindingSource component [Windows Forms], and IPropertyChange
- data sources [Windows Forms], detecting changes
- examples [Windows Forms], BindingSource component
- change notifications
- INotifyPropertyChanged interface [Windows Forms], using with BindingSource
- BindingSource component [Windows Forms], examples
ms.assetid: 7fa2cf51-c09f-4375-adf0-e36c5617f099
ms.openlocfilehash: 07248ec0b8ac4f2356d9c9915b6a904dfad30cb2
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388976"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a><span data-ttu-id="f8f8d-102">Nasıl yapılır: BindingSource ve INotifyPropertyChanged Arabirimini Kullanarak Değişiklik Bildirimleri Verme</span><span class="sxs-lookup"><span data-stu-id="f8f8d-102">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="f8f8d-103">Bileşen, <xref:System.Windows.Forms.BindingSource> veri kaynağında bulunan tür <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi uyguladığında ve özellik değeri değiştirildiğinde olayları yükselttiğinde, <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> veri kaynağındaki değişiklikleri otomatik olarak algılar.</span><span class="sxs-lookup"><span data-stu-id="f8f8d-103">The <xref:System.Windows.Forms.BindingSource> component will automatically detect changes in a data source when the type contained in the data source implements the <xref:System.ComponentModel.INotifyPropertyChanged> interface and raises <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> events when a property value is changed.</span></span> <span data-ttu-id="f8f8d-104">Veri kaynağı değerleri değiştikçe <xref:System.Windows.Forms.BindingSource> will'e bağlı denetimler otomatik olarak güncelleştirilen için bu yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="f8f8d-104">This is useful because controls bound to the <xref:System.Windows.Forms.BindingSource> will then automatically update as the data source values change.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8f8d-105">Veri kaynağınız uygular <xref:System.ComponentModel.INotifyPropertyChanged> ve eşzamanlı işlemler gerçekleştirmektedirseniz, arka plan iş parçacığındaki veri kaynağında değişiklik yapmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="f8f8d-105">If your data source implements <xref:System.ComponentModel.INotifyPropertyChanged> and you are performing asynchronous operations, you should not make changes to the data source on a background thread.</span></span> <span data-ttu-id="f8f8d-106">Bunun yerine, bir arka plan iş parçacığı üzerindeki verileri okumanız ve verileri UI iş parçacığındaki bir listede birleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8f8d-106">Instead, you should read the data on a background thread and merge the data into a list on the UI thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8f8d-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="f8f8d-107">Example</span></span>  
 <span data-ttu-id="f8f8d-108">Aşağıdaki kod <xref:System.ComponentModel.INotifyPropertyChanged> örneği, arabirimin basit bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8f8d-108">The following code example demonstrates a simple implementation of the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="f8f8d-109">Ayrıca, bir <xref:System.Windows.Forms.BindingSource> veri kaynağının <xref:System.ComponentModel.INotifyPropertyChanged> türünün listesine bağlandığında <xref:System.Windows.Forms.BindingSource> bağlı bir denetime nasıl otomatik olarak geçtiğini de gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8f8d-109">It also shows how the <xref:System.Windows.Forms.BindingSource> automatically passes a data source change to a bound control when the <xref:System.Windows.Forms.BindingSource> is bound to a list of the <xref:System.ComponentModel.INotifyPropertyChanged> type.</span></span>  
  
 <span data-ttu-id="f8f8d-110">`CallerMemberName` Öznitelik kullanırsanız, `NotifyPropertyChanged` yönteme yapılan çağrıların özellik adını dize bağımsız değişkeni olarak belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f8f8d-110">If you use the `CallerMemberName` attribute, calls to the `NotifyPropertyChanged` method don't have to specify the property name as a string argument.</span></span> <span data-ttu-id="f8f8d-111">Daha fazla bilgi için [Bkz. Arayan Bilgileri (C#)](../../../csharp/language-reference/attributes/caller-information.md) veya [Arayan Bilgileri (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="f8f8d-111">For more information, see [Caller Information (C#)](../../../csharp/language-reference/attributes/caller-information.md) or [Caller Information (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f8f8d-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f8f8d-112">Compiling the Code</span></span>  
 <span data-ttu-id="f8f8d-113">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f8f8d-113">This example requires:</span></span>  
  
- <span data-ttu-id="f8f8d-114">Sistem, System.Data, System.Drawing ve System.Windows.Forms derlemelerine yapılan atıflar.</span><span class="sxs-lookup"><span data-stu-id="f8f8d-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8f8d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8f8d-115">See also</span></span>

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [<span data-ttu-id="f8f8d-116">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="f8f8d-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="f8f8d-117">Nasıl yapılır: BindingSource ve ResetItem Metodunu Kullanarak Değişiklik Bildirimleri Verme</span><span class="sxs-lookup"><span data-stu-id="f8f8d-117">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
