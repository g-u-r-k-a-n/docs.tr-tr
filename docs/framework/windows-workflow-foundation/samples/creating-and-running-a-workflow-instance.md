---
title: İş Akışı Örneği Oluşturma ve Çalıştırma
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: d895cfa9e924ecf4d1571cf67f1c1e7069e25da5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715197"
---
# <a name="creating-and-running-a-workflow-instance"></a><span data-ttu-id="e36f8-102">İş Akışı Örneği Oluşturma ve Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="e36f8-102">Creating and Running a Workflow Instance</span></span>

<span data-ttu-id="e36f8-103">Bu örnek, bir iş akışı örneğinin nasıl çalıştırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e36f8-103">This sample shows how to run a workflow instance.</span></span> <span data-ttu-id="e36f8-104">Bu, zaman uyumlu ve zaman uyumsuz olarak nasıl yürütüleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e36f8-104">It shows how to execute it synchronously and asynchronously.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="e36f8-105">Gösterir</span><span class="sxs-lookup"><span data-stu-id="e36f8-105">Demonstrates</span></span>

<span data-ttu-id="e36f8-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="e36f8-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span></span>

## <a name="discussion"></a><span data-ttu-id="e36f8-107">Tartışma</span><span class="sxs-lookup"><span data-stu-id="e36f8-107">Discussion</span></span>

<span data-ttu-id="e36f8-108">Örneğin ilk bölümü <xref:System.Activities.WorkflowInvoker.Invoke%2A>kullanır.</span><span class="sxs-lookup"><span data-stu-id="e36f8-108">The first part of the sample uses <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span> <span data-ttu-id="e36f8-109">Bu, bir iş akışını yürütmek için en temel yoldur.</span><span class="sxs-lookup"><span data-stu-id="e36f8-109">This is the most basic way to execute a workflow.</span></span> <span data-ttu-id="e36f8-110"><xref:System.Activities.WorkflowInvoker.Invoke%2A> ile yürütülen iş akışları zaman uyumlu olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="e36f8-110">Workflows executed with <xref:System.Activities.WorkflowInvoker.Invoke%2A> are executed synchronously.</span></span>

<span data-ttu-id="e36f8-111">Örneğin ikinci bölümü <xref:System.Activities.WorkflowApplication> sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="e36f8-111">The second part of the sample uses the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="e36f8-112"><xref:System.Activities.WorkflowApplication>, çalışan iş akışıyla etkileşim kurma ve iş akışını zaman uyumsuz olarak çalıştırma özelliği de dahil olmak üzere her bir örnek üzerinde daha fazla denetime sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e36f8-112"><xref:System.Activities.WorkflowApplication> enables you to have more control over each instance, including the ability to interact with the running workflow and to run the workflow asynchronously.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e36f8-113">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="e36f8-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e36f8-114">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e36f8-114">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="e36f8-115">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="e36f8-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e36f8-116">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="e36f8-116">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`

## <a name="see-also"></a><span data-ttu-id="e36f8-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e36f8-117">See also</span></span>

- [<span data-ttu-id="e36f8-118">WorkflowInvoker ve WorkflowApplication Kullanma</span><span class="sxs-lookup"><span data-stu-id="e36f8-118">Using WorkflowInvoker and WorkflowApplication</span></span>](../using-workflowinvoker-and-workflowapplication.md)
