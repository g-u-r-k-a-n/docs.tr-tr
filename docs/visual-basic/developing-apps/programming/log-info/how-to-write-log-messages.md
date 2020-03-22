---
title: 'Nasıl Yapılır: Günlük İletileri Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messages
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: 38570047db48e009aea2af376304430db1ec29f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352062"
---
# <a name="how-to-write-log-messages-visual-basic"></a><span data-ttu-id="39fbd-102">Nasıl Yapılır: Günlük İletileri Yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39fbd-102">How to: Write Log Messages (Visual Basic)</span></span>

<span data-ttu-id="39fbd-103">Uygulamanızla ilgili `My.Application.Log` `My.Log` bilgileri günlüğe kaydetmek için nesneleri ve nesneleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39fbd-103">You can use the `My.Application.Log` and `My.Log` objects to log information about your application.</span></span> <span data-ttu-id="39fbd-104">Bu örnek, izleme `My.Application.Log.WriteEntry` bilgilerini günlüğe kaydetmek için yöntemin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="39fbd-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information.</span></span>

<span data-ttu-id="39fbd-105">Özel durum bilgilerini günlüğe kaydetmek için `My.Application.Log.WriteException` yöntemi kullanın; bkz. [Nasıl yapılır: Özel Durumları Günlüğe](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)Kaydedin.</span><span class="sxs-lookup"><span data-stu-id="39fbd-105">For logging exception information, use the `My.Application.Log.WriteException` method; see [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>

## <a name="example"></a><span data-ttu-id="39fbd-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="39fbd-106">Example</span></span>

<span data-ttu-id="39fbd-107">Bu örnek, `My.Application.Log.WriteEntry` izleme bilgilerini yazmak için yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="39fbd-107">This example uses the `My.Application.Log.WriteEntry` method to write out the trace information.</span></span>

[!code-vb[VbVbalrMyApplicationLog#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#11)]

## <a name="net-framework-security"></a><span data-ttu-id="39fbd-108">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="39fbd-108">.NET Framework Security</span></span>

<span data-ttu-id="39fbd-109">Günlük lere yazdığınız verilerin kullanıcı parolaları gibi hassas bilgileri içermediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="39fbd-109">Make sure the data you write to the log does not include sensitive information such as user passwords.</span></span> <span data-ttu-id="39fbd-110">Daha fazla bilgi için bkz: [Uygulama Günlükleriyle Çalışma.](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)</span><span class="sxs-lookup"><span data-stu-id="39fbd-110">For more information, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="39fbd-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39fbd-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="39fbd-112">Uygulama Günlükleriyle Çalışma</span><span class="sxs-lookup"><span data-stu-id="39fbd-112">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="39fbd-113">Nasıl Yapılır: Günlük Özel Durumları</span><span class="sxs-lookup"><span data-stu-id="39fbd-113">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="39fbd-114">İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme</span><span class="sxs-lookup"><span data-stu-id="39fbd-114">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="39fbd-115">İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="39fbd-115">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="39fbd-116">İzlenecek Yol: My.Application.Log Çıktısını Filtreleme</span><span class="sxs-lookup"><span data-stu-id="39fbd-116">Walkthrough: Filtering My.Application.Log Output</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)
