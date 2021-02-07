---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir alt görevin kendi üst öğesine Iliştirmesini engelleme'
title: 'Nasıl yapılır: Alt Görevin Üst Göreve Eklenmesini Önleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
ms.openlocfilehash: 93c0b3c1e4ae3ded49b8e66f0e726708d63021d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701787"
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a>Nasıl yapılır: Alt Görevin Üst Göreve Eklenmesini Önleme

Bu belgede, bir alt görevin üst göreve iliştirilmesi nasıl önleneceği gösterilmektedir. Bir alt görevin kendi üst öğesine iliştirmesini önlemek, üçüncü taraf tarafından yazılan ve ayrıca görevleri kullanan bir bileşeni çağırdığınızda yararlıdır. Örneğin, bir veya nesnesi oluşturma seçeneğini kullanan bir üçüncü taraf bileşeni, <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> uzun süre çalışan veya işlenmemiş bir özel durum oluşturursa kodunuzda sorunlara neden olabilir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, varsayılan seçenekleri kullanmanın etkilerini, alt görevin üst öğeye iliştirmesini engellemeye yönelik etkileri ile karşılaştırır. Örnek, <xref:System.Threading.Tasks.Task> bir nesneyi de kullanan bir üçüncü taraf kitaplığına çağıran bir nesnesi oluşturur <xref:System.Threading.Tasks.Task> . Üçüncü taraf kitaplığı, <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> nesneyi oluşturma seçeneğini kullanır <xref:System.Threading.Tasks.Task> . Uygulama, <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> ana görevi oluşturmak için seçeneğini kullanır. Bu seçenek çalışma zamanına <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> alt görevlerin belirtimini kaldırmasını söyler.  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 Bir üst görev tüm alt görevler tamamlanana kadar bitmediğinden, uzun süreli bir alt görev genel uygulamanın kötü bir şekilde çalışmasına neden olabilir. Bu örnekte, uygulama ana görevi oluşturmak için varsayılan seçenekleri kullandığında, üst görev tamamlanmadan önce alt görevin son olması gerekir. Uygulama <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> seçeneğini kullandığında, alt öğe üst öğeye eklenmez. Bu nedenle, uygulama, üst görev bittikten sonra ve alt görevin bitmesini beklemek zorunda olduktan sonra ek iş gerçekleştirebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görev tabanlı zaman uyumsuz programlama](task-based-asynchronous-programming.md)
