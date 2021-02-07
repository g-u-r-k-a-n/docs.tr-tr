---
description: 'Daha fazla bilgi edinin: nasıl yapılır: önceden hesaplanan görevler oluşturma'
title: 'Nasıl yapılır: Önceden Hesaplanan Görevler Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
ms.openlocfilehash: 552ba7381504fa75f1879ee5252dbc748122c582
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702034"
---
# <a name="how-to-create-pre-computed-tasks"></a><span data-ttu-id="c4af9-103">Nasıl yapılır: Önceden Hesaplanan Görevler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c4af9-103">How to: Create Pre-Computed Tasks</span></span>

<span data-ttu-id="c4af9-104">Bu belgede, <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> bir önbellekte tutulan zaman uyumsuz indirme işlemlerinin sonuçlarını almak için yönteminin nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c4af9-104">This document describes how to use the <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> method to retrieve the results of asynchronous download operations that are held in a cache.</span></span> <span data-ttu-id="c4af9-105"><xref:System.Threading.Tasks.Task.FromResult%2A>Yöntemi, <xref:System.Threading.Tasks.Task%601> özelliği olarak belirtilen değeri tutan tamamlanmış bir nesne döndürür <xref:System.Threading.Tasks.Task%601.Result%2A> .</span><span class="sxs-lookup"><span data-stu-id="c4af9-105">The <xref:System.Threading.Tasks.Task.FromResult%2A> method returns a finished <xref:System.Threading.Tasks.Task%601> object that holds the provided value as its <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="c4af9-106">Bu yöntem, bir nesne döndüren zaman uyumsuz bir işlem gerçekleştirirken ve bu <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task%601> nesnenin sonucu zaten hesaplanmışsa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="c4af9-106">This method is useful when you perform an asynchronous operation that returns a <xref:System.Threading.Tasks.Task%601> object, and the result of that <xref:System.Threading.Tasks.Task%601> object is already computed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4af9-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4af9-107">Example</span></span>  

 <span data-ttu-id="c4af9-108">Aşağıdaki örnek dizeleri Web 'den indirir.</span><span class="sxs-lookup"><span data-stu-id="c4af9-108">The following example downloads strings from the web.</span></span> <span data-ttu-id="c4af9-109">`DownloadStringAsync`Yöntemini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c4af9-109">It defines the `DownloadStringAsync` method.</span></span> <span data-ttu-id="c4af9-110">Bu yöntem, dizeleri zaman uyumsuz olarak Web 'den indirir.</span><span class="sxs-lookup"><span data-stu-id="c4af9-110">This method downloads strings from the web asynchronously.</span></span> <span data-ttu-id="c4af9-111">Bu örnek <xref:System.Collections.Concurrent.ConcurrentDictionary%602> , önceki işlemlerin sonuçlarını önbelleğe almak için de bir nesnesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4af9-111">This example also uses a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> object to cache the results of previous operations.</span></span> <span data-ttu-id="c4af9-112">Giriş adresi bu önbellekte tutuluyorsa, bu `DownloadStringAsync` <xref:System.Threading.Tasks.Task.FromResult%2A> adresteki içeriği tutan bir nesne oluşturmak için yöntemini kullanır <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="c4af9-112">If the input address is held in this cache, `DownloadStringAsync` uses the <xref:System.Threading.Tasks.Task.FromResult%2A> method to produce a <xref:System.Threading.Tasks.Task%601> object that holds the content at that address.</span></span> <span data-ttu-id="c4af9-113">Aksi takdirde, `DownloadStringAsync` dosyayı Web 'den indirir ve sonucu önbelleğe ekler.</span><span class="sxs-lookup"><span data-stu-id="c4af9-113">Otherwise, `DownloadStringAsync` downloads the file from the web and adds the result to the cache.</span></span>  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 <span data-ttu-id="c4af9-114">Bu örnek, birden çok dizeyi iki kez indirmek için gereken zamanı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="c4af9-114">This example computes the time that is required to download multiple strings two times.</span></span> <span data-ttu-id="c4af9-115">İkinci indirme işlemleri kümesi, sonuçlar önbellekte tutulduğundan ilk ayarlanan süreden daha az zaman almalıdır.</span><span class="sxs-lookup"><span data-stu-id="c4af9-115">The second set of download operations should take less time than the first set because the results are held in the cache.</span></span> <span data-ttu-id="c4af9-116"><xref:System.Threading.Tasks.Task.FromResult%2A>Yöntemi, `DownloadStringAsync` yönteminin <xref:System.Threading.Tasks.Task%601> Bu önceden hesaplanan sonuçları tutan nesneler oluşturmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4af9-116">The <xref:System.Threading.Tasks.Task.FromResult%2A> method enables the `DownloadStringAsync` method to create <xref:System.Threading.Tasks.Task%601> objects that hold these pre-computed results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4af9-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4af9-117">See also</span></span>

- [<span data-ttu-id="c4af9-118">Görev tabanlı zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="c4af9-118">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
