---
title: 'Nasıl yapılır: Yerel İşlemler Arası İletişim için Anonim Kanallar Kullanma'
description: .NET 'teki yerel bir bilgisayarda yerel işlemler arası iletişim için anonim kanalları nasıl kullanacağınızı öğrenin. Anonim kanallar, adlandırılmış kanallara göre daha az ek yük gerektirir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- anonymous pipes [.NET]
- parent-child communication [.NET]
- pipes [.NET]
- one-way communication [.NET]
- local computer communication [.NET], pipes
ms.assetid: e7773c77-c646-4a01-8a96-a003d59fc4c9
ms.openlocfilehash: 389451d1c6c313ac4a10652c7aa614a5e4e7bf1c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734562"
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a>Nasıl yapılır: Yerel İşlemler Arası İletişim için Anonim Kanallar Kullanma

Anonim kanallar, yerel bir bilgisayarda işlemler arası iletişim sağlar. Adlandırılmış kanallardan daha az işlevsellik sağlarlar, ancak daha az yük gerektirirler. Yerel bir bilgisayarda işlemler arası iletişimi kolaylaştırmak için anonim kanalları kullanabilirsiniz. Bir ağ üzerinden iletişim için anonim kanalları kullanamazsınız.  
  
 Anonim kanalları uygulamak için, <xref:System.IO.Pipes.AnonymousPipeServerStream> ve <xref:System.IO.Pipes.AnonymousPipeClientStream> sınıflarını kullanın.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, bir ana işlemden alt işleme anonim kanalları kullanarak bir dize göndermenin yolunu gösterir. Bu örnek, <xref:System.IO.Pipes.AnonymousPipeServerStream>'in bir <xref:System.IO.Pipes.PipeDirection> değeriyle birlikte ana işlemde bir <xref:System.IO.Pipes.PipeDirection.Out> nesnesi oluşturur. Daha sonra ana işlem, bir <xref:System.IO.Pipes.AnonymousPipeClientStream> nesnesi oluşturmak için bir istemci işleyicisi kullanarak bir alt işlem oluşturur. Alt işlem, <xref:System.IO.Pipes.PipeDirection>'in bir <xref:System.IO.Pipes.PipeDirection.In> değerine sahiptir.  
  
 Ardından ana işlem, alt işleme kullanıcı tarafından sağlanan bir dize gönderir. Dize, alt işlemdeki konsolda görüntülenir.  
  
 Aşağıdaki örnek sunucu işlemini gösterir.  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek istemci işlemini gösterir. Sunucu işlemi istemci işlemini başlatır ve bu işleme bir istemci işleyicisi verir. İstemci kodundan oluşturulan yürütülebilir dosya `pipeClient.exe` olarak adlandırılmalıdır ve sunucu işlemi çalıştırılmadan önce sunucu yürütülebilir dosyası olarak aynı dizine kopyalanmalıdır.  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kanallar](pipe-operations.md)
- [Nasıl yapılır: Ağ İşlemler Arası İletişimi için Adlandırılmış Kanallar Kullanma](how-to-use-named-pipes-for-network-interprocess-communication.md)
