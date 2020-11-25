---
title: Windows Workflow Foundation’da kullanım dışı türler
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: 011f13a56695efdd9e964ef1e6c1099b0acc2710
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713346"
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a><span data-ttu-id="9525c-102">Windows Workflow Foundation’da kullanım dışı türler</span><span class="sxs-lookup"><span data-stu-id="9525c-102">Deprecated types in Windows Workflow Foundation</span></span>
<span data-ttu-id="9525c-103">.NET 4 ' te Iş akışı ekibi, ad alanında yeni bir Iş akışı altyapısı yayımlamıştır <xref:System.Activities> .</span><span class="sxs-lookup"><span data-stu-id="9525c-103">In .NET 4 the Workflow Team released an all new Workflow engine in the <xref:System.Activities> namespace.</span></span> <span data-ttu-id="9525c-104">.NET Framework 4,5 Beta sürümü sayesinde, "WF 3" <xref:System.Workflow.Activities> , ve ad alanlarındaki türlerin çoğunu <xref:System.Workflow.ComponentModel>  <xref:System.Workflow.Runtime> eski olarak işaretliyoruz.</span><span class="sxs-lookup"><span data-stu-id="9525c-104">With the release of .NET Framework 4.5 Beta we are marking most of the types in the "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, and  <xref:System.Workflow.Runtime> namespaces as obsolete.</span></span>

## <a name="obsolete-namespaces-and-tools"></a><span data-ttu-id="9525c-105">Kullanılmayan ad alanları ve araçları</span><span class="sxs-lookup"><span data-stu-id="9525c-105">Obsolete namespaces and tools</span></span>
 <span data-ttu-id="9525c-106">Aşağıdaki derlemeler, kullanım dışı bırakılacak bir veya daha fazla ortak türe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="9525c-106">The following assemblies have one or more public types that will be deprecated:</span></span>

- <span data-ttu-id="9525c-107">System.Workflow.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="9525c-107">System.Workflow.Activities.dll</span></span>

- <span data-ttu-id="9525c-108">System.Workflow.ComponentModel.dll</span><span class="sxs-lookup"><span data-stu-id="9525c-108">System.Workflow.ComponentModel.dll</span></span>

- <span data-ttu-id="9525c-109">System.Workflow.Runtime.dll</span><span class="sxs-lookup"><span data-stu-id="9525c-109">System.Workflow.Runtime.dll</span></span>

- <span data-ttu-id="9525c-110">System.WorkflowServices.dll</span><span class="sxs-lookup"><span data-stu-id="9525c-110">System.WorkflowServices.dll</span></span>

- <span data-ttu-id="9525c-111">Microsoft.Workflow.DebugController.dll</span><span class="sxs-lookup"><span data-stu-id="9525c-111">Microsoft.Workflow.DebugController.dll</span></span>

- <span data-ttu-id="9525c-112">Microsoft.Workflow.Compiler.exe</span><span class="sxs-lookup"><span data-stu-id="9525c-112">Microsoft.Workflow.Compiler.exe</span></span>

- <span data-ttu-id="9525c-113">Wfc.exe</span><span class="sxs-lookup"><span data-stu-id="9525c-113">Wfc.exe</span></span>

 <span data-ttu-id="9525c-114">Sonuç olarak, kullanımdan kaldırılan WF 3 API 'Leri kullanan müşteriler, aşağıdakine benzer bir iletiyle birlikte derleme uyarıları ile karşılaşacaktır:</span><span class="sxs-lookup"><span data-stu-id="9525c-114">As a result, customers who are using the deprecated WF 3 APIs will encounter build warnings with a message similar to the following:</span></span>

 <span data-ttu-id="9525c-115">**Uyarı BC40000: X artık kullanılmıyor: WF 3 türleri kullanım dışıdır. Lütfen bunun yerine WF 4 kullanın.**</span><span class="sxs-lookup"><span data-stu-id="9525c-115">**Warning BC40000: X is obsolete: WF 3 types are deprecated. Please use WF 4 instead.**</span></span> <span data-ttu-id="9525c-116">Gelecekteki bir sürümdeki .NET Framework türleri kaldıracağız, ancak henüz bu zaman dilimini (4,5 ' de değil) belirliyoruz.</span><span class="sxs-lookup"><span data-stu-id="9525c-116">We will remove the types from the .NET Framework in a future release, but we have not yet determined that timeframe (not in 4.5).</span></span> <span data-ttu-id="9525c-117">Bu geçerli adım, müşterilerimiz için yönümüzü iletmemize ve yeni WF4 modeline geçiş yapmak için yeterince zaman sağlar.</span><span class="sxs-lookup"><span data-stu-id="9525c-117">This current step allows us to communicate our direction to our customers and allow them plenty of time to move to the new WF4 model.</span></span> <span data-ttu-id="9525c-118">Tabii ki, [Microsoft desteği yaşam döngüsü ilkesi](/lifecycle/)altında bu WF 3 türlerini desteklemeye devam edeceğiz.</span><span class="sxs-lookup"><span data-stu-id="9525c-118">We will, of course, continue to support these WF 3 types under the [Microsoft Support Lifecycle Policy](/lifecycle/).</span></span> <span data-ttu-id="9525c-119">Mevcut WF3 uygulamaları .NET Framework 4,5 ' de sorun olmadan çalışacaktır ve Visual Studio 2012, yeni ve var olan WF3 tabanlı çözümleri destekleyecektir.</span><span class="sxs-lookup"><span data-stu-id="9525c-119">Existing WF3 applications will run without issue on .NET Framework 4.5, and Visual Studio 2012 will support new and existing WF3-based solutions.</span></span>

 <span data-ttu-id="9525c-120">Ad alanındaki kurallarla ilgili türler <xref:System.Workflow.Activities.Rules> , WF 4,5 ' de değişiklik olmayan, kullanım dışı bırakılmış.</span><span class="sxs-lookup"><span data-stu-id="9525c-120">Rules related types in the <xref:System.Workflow.Activities.Rules> namespace, which do not have a replacement in WF 4.5, have not been deprecated.</span></span>

 <span data-ttu-id="9525c-121">Uygulamalarını WF 4 ' e geçirmek isteyen müşteriler, [Iş akışı 4 geçiş kılavuzunda](migration-guidance.md)yardım bulacaktır.</span><span class="sxs-lookup"><span data-stu-id="9525c-121">Customers who want to migrate their applications to WF 4 will find help in the [Workflow 4 Migration Guidance](migration-guidance.md).</span></span>
