---
description: 'Hakkında daha fazla bilgi edinin: DataView değiştirme'
title: DataView Değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: e0f62c0b8553cd4b83c28da99b8bdec316c8a91d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651840"
---
# <a name="modifying-dataviews"></a>DataView Değiştirme

<xref:System.Data.DataView>Temel tablodaki veri satırlarını eklemek, silmek veya değiştirmek için öğesini kullanabilirsiniz. Temel tablodaki verileri değiştirmek için **DataView** kullanma özelliği, **DataView**'ın üç Boole özelliğinden biri ayarlanarak denetlenir. Bu özellikler <xref:System.Data.DataView.AllowNew%2A> , <xref:System.Data.DataView.AllowEdit%2A> ve ' dir <xref:System.Data.DataView.AllowDelete%2A> . Varsayılan olarak **true** olarak ayarlanmıştır.  
  
 **AllowNew** **true** ise, <xref:System.Data.DataView.AddNew%2A> Yeni bir oluşturmak için **DataView** yöntemini kullanabilirsiniz <xref:System.Data.DataRowView> . Yeni bir satırın, <xref:System.Data.DataTable> <xref:System.Data.DataRowView.EndEdit%2A> **DataRowView** 'ın yöntemi çağrılana kadar temeldeki temel içine eklenmediğini unutmayın. <xref:System.Data.DataRowView.CancelEdit%2A> **DataRowView** 'ın yöntemi çağrılırsa, yeni satır atılır. Aynı anda yalnızca bir **DataRowView** öğesini düzenleyebileceğinizi unutmayın. Bekleyen bir satır varken **DataRowView** 'ın **AddNew** veya **BeginEdit** metodunu çağırırsanız, **EndEdit** , bekleyen satırda örtük olarak çağırılır. **EndEdit** çağrıldığında, değişiklikler temel alınan **DataTable** 'a uygulanır ve daha sonra **DataTable**, **DataSet** veya **DataRow** nesnesinin **AcceptChanges** veya **RejectChanges** yöntemleri kullanılarak gerçekleştirilebilir veya reddedilebilir. **AllowNew** **yanlış** Ise, **DataRowView**'ın **AddNew** metodunu çağırdığınızda bir özel durum oluşturulur.  
  
 **AllowEdit** **true** ise, bir **DataRow** 'ın içeriğini **DataRowView** aracılığıyla değiştirebilirsiniz. **DataRowView. EndEdit** kullanarak temel alınan satırdaki değişiklikleri doğrulayabilirsiniz veya **DataRowView. CancelEdit** kullanarak değişiklikleri reddedebilirsiniz. Tek seferde yalnızca bir satırın düzenlenebileceğini unutmayın. Bekleyen bir satır varken **DataRowView** 'ın **AddNew** veya **BeginEdit** yöntemlerini çağırırsanız, **EndEdit** , bekleyen satırda örtük olarak çağırılır. **EndEdit** çağrıldığında, önerilen değişiklikler temel alınan **DataRow** 'ın **geçerli** satır sürümüne yerleştirilir ve daha sonra **DataTable**, **DataSet** veya **DataRow** nesnesinin **AcceptChanges** veya **RejectChanges** yöntemleri kullanılarak uygulanabilir veya reddedilebilir. **AllowEdit** **false** ise, **DataView** içindeki bir değeri değiştirmeye çalışırsanız bir özel durum oluşturulur.  
  
 Varolan bir **DataRowView** düzenlenirken, temel alınan **DataTable** olayları, önerilen değişikliklerle yine de oluşturulur. Temel alınan **DataRow** üzerinde **EndEdit** veya **CancelEdit** çağırırsanız, bekleyen değişikliklerin, **DataRowView** üzerinde **EndEdit** veya **CancelEdit** çağrılıp çağrılmadığına bakılmaksızın uygulanacağını veya iptal edildiğini unutmayın.  
  
 **AllowDelete** **true** ise **DataView veya** **DataRowView** nesnesinin **Delete** yöntemini kullanarak **DataView** nesnesinden satırları silebilirsiniz ve satırlar temeldeki **DataTable**'dan silinir. Daha sonra, sırasıyla **AcceptChanges** veya **RejectChanges** kullanarak silmeleri kaydedebilir veya reddedebilirsiniz. **AllowDelete** **false** Ise, **DataView** veya **DataRowView**'ın **Delete** yöntemini çağırdığınızda bir özel durum oluşturulur.  
  
 Aşağıdaki kod örneği, satırları silmek için **DataView** kullanımını devre dışı bırakır ve **DataView** kullanarak temel tabloya yeni bir satır ekler.  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custView As DataView = custTable.DefaultView  
custView.Sort = "CompanyName"  
  
custView.AllowDelete = False  
  
Dim newDRV As DataRowView = custView.AddNew()  
newDRV("CustomerID") = "ABCDE"  
newDRV("CompanyName") = "ABC Products"  
newDRV.EndEdit()  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
DataView custView = custTable.DefaultView;  
custView.Sort = "CompanyName";  
  
custView.AllowDelete = false;  
  
DataRowView newDRV = custView.AddNew();  
newDRV["CustomerID"] = "ABCDE";  
newDRV["CompanyName"] = "ABC Products";  
newDRV.EndEdit();  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [DataViews](dataviews.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
