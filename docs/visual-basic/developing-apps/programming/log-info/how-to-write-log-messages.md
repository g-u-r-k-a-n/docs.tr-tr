---
title: 'Nasıl Yapılır: Günlük İletileri Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messages
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: 38570047db48e009aea2af376304430db1ec29f4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352062"
---
# <a name="how-to-write-log-messages-visual-basic"></a>Nasıl Yapılır: Günlük İletileri Yazma (Visual Basic)

You can use the `My.Application.Log` and `My.Log` objects to log information about your application. This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information.

For logging exception information, use the `My.Application.Log.WriteException` method; see [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).

## <a name="example"></a>Örnek

This example uses the `My.Application.Log.WriteEntry` method to write out the trace information.

[!code-vb[VbVbalrMyApplicationLog#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#11)]

## <a name="net-framework-security"></a>.NET Framework Güvenliği

Make sure the data you write to the log does not include sensitive information such as user passwords. For more information, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Nasıl Yapılır: Günlük Özel Durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [İzlenecek Yol: My.Application.Log Çıktısını Filtreleme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)
