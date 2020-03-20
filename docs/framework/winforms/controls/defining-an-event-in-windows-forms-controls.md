---
title: Denetimlerde bir olay tanımlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- events [Windows Forms], defining within Windows Forms custom controls
- custom controls [Windows Forms], events using code
ms.assetid: d89f1096-8061-42e2-a855-a1f053f1940a
ms.openlocfilehash: 6799b229de8e8eb49dd3b8bbaffe0d08a32b7208
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142296"
---
# <a name="defining-an-event-in-windows-forms-controls"></a>Windows Forms Denetimlerinde Olay Tanımlama
Özel olayları tanımlama hakkında ayrıntılı bilgi için [Etkinlikler'e](../../../standard/events/index.md)bakın. İlişkili verisi olmayan bir olay tanımlarsanız, olay verileri <xref:System.EventArgs>için temel <xref:System.EventHandler> türü kullanın ve olay temsilcisi olarak kullanın. Geriye kalan tek şey bir olay üyesi ve `On`olayı yükselten korumalı bir *EventName* yöntemi tanımlamaktır.  
  
 Aşağıdaki kod parçası, `FlashTrackBar` özel denetimin özel bir `ValueChanged`olayı nasıl tanımladığını gösterir. `FlashTrackBar` Örneğin tam kodu [için, Nasıl Yapılır: İlerlemeyi Gösteren Bir Windows Formları Denetimi Oluşturun'](how-to-create-a-windows-forms-control-that-shows-progress.md)a bakın.  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.Windows.Forms  
Imports System.Drawing  
  
Public Class FlashTrackBar  
   Inherits Control  
  
   ' The event does not have any data, so EventHandler is adequate
   ' as the event delegate.
   ' Define the event member using the event keyword.  
   ' In this case, for efficiency, the event is defined
   ' using the event property construct.  
   Public Event ValueChanged As EventHandler  
   ' The protected method that raises the ValueChanged
   ' event when the value has actually
   ' changed. Derived controls can override this method.
   Protected Overridable Sub OnValueChanged(e As EventArgs)  
      RaiseEvent ValueChanged(Me, e)  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Windows.Forms;  
using System.Drawing;  
  
public class FlashTrackBar : Control {  
   // The event does not have any data, so EventHandler is adequate
   // as the event delegate.  
   private EventHandler onValueChanged;  
   // Define the event member using the event keyword.  
   // In this case, for efficiency, the event is defined
   // using the event property construct.  
   public event EventHandler ValueChanged {  
            add {  
                onValueChanged += value;  
            }  
            remove {  
                onValueChanged -= value;  
            }  
        }  
   // The protected method that raises the ValueChanged  
   // event when the value has actually
   // changed. Derived controls can override this method.
   protected virtual void OnValueChanged(EventArgs e)
   {  
       ValueChanged?.Invoke(this, e);  
   }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Denetimlerindeki Olaylar](events-in-windows-forms-controls.md)
- [Olaylar](../../../standard/events/index.md)
