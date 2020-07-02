---
title: 'Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme'
description: Windows Forms denetimlerinizin satırlarını ve sütunlarını düzenlemek için sütun ve satır stilleri iletişim kutusunu nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
ms.openlocfilehash: cfd2ca4be5d5a2658a9a129d911f1dba9670ccfd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619357"
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme

<xref:System.Windows.Forms.TableLayoutPanel>Denetimlerinizin satırlarını ve sütunlarını düzenlemek için, **sütun ve satır stilleri** iletişim kutusu adlı denetimin koleksiyon düzenleyicisini kullanabilirsiniz.

> [!NOTE]
> Bir denetimin birden çok satır veya sütunu yaymasına isterseniz, `RowSpan` `ColumnSpan` Denetim üzerindeki ve özelliklerini ayarlayın. Daha fazla bilgi için bkz. [Izlenecek yol: Windows Forms denetimleri bir TableLayoutPanel kullanarak düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).
>
> Bir hücrenin içindeki bir denetimi hizalamak istiyorsanız veya bir denetimin bir hücrede Esnetme olmasını istiyorsanız denetimin <xref:System.Windows.Forms.Control.Anchor%2A> özelliğini kullanın. Daha fazla bilgi için bkz. [Izlenecek yol: Windows Forms denetimleri bir TableLayoutPanel kullanarak düzenleme](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).

## <a name="to-edit-rows-and-columns"></a>Satırları ve sütunları düzenlemek için

1. <xref:System.Windows.Forms.TableLayoutPanel> **Araç kutusu** ' ndan formunuza bir denetim sürükleyin.

2. <xref:System.Windows.Forms.TableLayoutPanel>Denetimin tasarımcı eylemleri glifi ' ne ( ![ küçük siyah ok ](./media/designer-actions-glyph.gif) ) tıklayın ve **sütun ve satır stilleri** iletişim kutusunu açmak için **satırları ve sütunları Düzenle** ' yi seçin. Ayrıca denetime sağ tıklayıp <xref:System.Windows.Forms.TableLayoutPanel> kısayol menüsünden **satırları ve sütunları Düzenle** ' yi seçebilirsiniz.

3. Sütun eklemek veya kaldırmak için **üye türü** açılan liste kutusundan **sütunlar** ' ı seçin.

4. Satır eklemek veya kaldırmak için **üye türü** açılan liste kutusundan **Satırlar** ' ı seçin.

5. **Üye** listesinin sonuna bir satır veya sütun eklemek için **Ekle** düğmesine tıklayın.

6. Listede seçili olan öğeden önce bir satır veya sütun eklemek için **Ekle** düğmesine tıklayın.

7. Bir satır veya sütun ekliyorsanız, yeni satır veya sütun için **Boyut türünü** seçin. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.SizeType>.

8. Bir satırı veya sütunu kaldırmak için **Kaldır** düğmesine tıklayarak **üye** listesinde o anda seçili olan öğeyi silin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.SizeType>
- [TableLayoutPanel Denetimi](tablelayoutpanel-control-windows-forms.md)
