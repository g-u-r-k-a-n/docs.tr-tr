---
title: 'Nasıl Yapılır: Seri Bağlantı Noktalarına Dizeler Gönderme'
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: b2051451142a7818a3b7d1bc564c5ae36b2579fe
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345581"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Seri Bağlantı Noktalarına Dizeler Gönderme

This topic describes how to use `My.Computer.Ports` to send strings to the computer's serial ports in Visual Basic.  
  
## <a name="example"></a>Örnek  

 This example sends a string to the COM1 serial port. You may need to use a different serial port on your computer.  
  
 Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port. Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
 The `Using` block allows the application to close the serial port even if it generates an exception. All code that manipulates the serial port should appear within this block or within a `Try...Catch...Finally` block.  
  
 The <xref:System.IO.Ports.SerialPort.WriteLine%2A> method sends the data to the serial port.  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- This example assumes the computer is using `COM1`.  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 This example assumes the computer is using `COM1`; for more flexibility, the code should allow the user to select the desired serial port from a list of available ports. For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 This example uses a `Using` block to make sure that the application closes the port even if it throws an exception. For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Nasıl Yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Nasıl Yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
