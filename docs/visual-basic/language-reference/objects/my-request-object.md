---
description: ': My. Request nesnesi hakkında daha fazla bilgi edinin'
title: My.Request Nesnesi
ms.date: 07/20/2015
f1_keywords:
- My.MyWebExtension.Request
- My.Request
helpviewer_keywords:
- My.Request object
ms.assetid: 93d5f0e2-6b60-4a2c-8652-d90216f6ad10
ms.openlocfilehash: 0b72252e261cd033bfc35c546de5c53a4f3cfe2c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640660"
---
# <a name="myrequest-object"></a><span data-ttu-id="eadff-103">My.Request Nesnesi</span><span class="sxs-lookup"><span data-stu-id="eadff-103">My.Request Object</span></span>

<span data-ttu-id="eadff-104"><xref:System.Web.HttpRequest>İstenen sayfa için nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="eadff-104">Gets the <xref:System.Web.HttpRequest> object for the requested page.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eadff-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eadff-105">Remarks</span></span>  

 <span data-ttu-id="eadff-106">`My.Request`Nesne, GEÇERLI HTTP isteğiyle ilgili bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="eadff-106">The `My.Request` object contains information about the current HTTP request.</span></span>  
  
 <span data-ttu-id="eadff-107">`My.Request`Nesne yalnızca ASP.NET uygulamaları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eadff-107">The `My.Request` object is available only for ASP.NET applications.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eadff-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="eadff-108">Example</span></span>  

 <span data-ttu-id="eadff-109">Aşağıdaki örnek, nesnesinden üstbilgi koleksiyonunu alır `My.Request` ve `My.Response` nesneyi ASP.NET sayfasına yazmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="eadff-109">The following example gets the header collection from the `My.Request` object and uses the `My.Response` object to write it to the ASP.NET page.</span></span>  
  
 [!code-aspx-vb[VbVbalrMyWeb#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWeb/VB/Default.aspx#1)]  
  
## <a name="see-also"></a><span data-ttu-id="eadff-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eadff-110">See also</span></span>

- <xref:System.Web.HttpRequest>
- [<span data-ttu-id="eadff-111">My.Response Nesnesi</span><span class="sxs-lookup"><span data-stu-id="eadff-111">My.Response Object</span></span>](my-response-object.md)
