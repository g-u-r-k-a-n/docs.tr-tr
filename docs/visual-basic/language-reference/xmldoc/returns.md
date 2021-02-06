---
description: 'Aşağıdakiler hakkında daha fazla bilgi edinin: <returns> (Visual Basic)'
title: <returns>
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: ba5f1e231502a67e86ffbb92cf8868c3aecb05d2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640387"
---
# <a name="returns-visual-basic"></a><span data-ttu-id="5aac5-103">\<returns> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5aac5-103">\<returns> (Visual Basic)</span></span>

<span data-ttu-id="5aac5-104">Özelliğin veya işlevin dönüş değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5aac5-104">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5aac5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5aac5-105">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a><span data-ttu-id="5aac5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5aac5-106">Parameters</span></span>  

 `description`  
 <span data-ttu-id="5aac5-107">Dönüş değerinin açıklaması.</span><span class="sxs-lookup"><span data-stu-id="5aac5-107">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5aac5-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5aac5-108">Remarks</span></span>  

 <span data-ttu-id="5aac5-109">`<returns>`Dönüş değerini anlatmak için bir yöntem bildirimi açıklamasında etiketini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5aac5-109">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="5aac5-110">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="5aac5-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5aac5-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="5aac5-111">Example</span></span>  

 <span data-ttu-id="5aac5-112">Bu örnek, `<returns>` işlevin ne döndürdüğünü açıklamak için etiketini kullanır `DoesRecordExist` .</span><span class="sxs-lookup"><span data-stu-id="5aac5-112">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="5aac5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5aac5-113">See also</span></span>

- [<span data-ttu-id="5aac5-114">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="5aac5-114">XML Comment Tags</span></span>](index.md)
