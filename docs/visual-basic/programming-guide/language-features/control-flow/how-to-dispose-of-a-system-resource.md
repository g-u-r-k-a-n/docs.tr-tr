---
description: ': Nasıl yapılır: sistem kaynağını atma (Visual Basic) hakkında daha fazla bilgi edinin'
title: 'Nasıl yapılır: Bir Sistem Kaynağını Atma'
ms.date: 07/20/2015
helpviewer_keywords:
- Using statement [Visual Basic], disposing of system resources
- Visual Basic code, control flow
- system resources, disposing of
- resources [Visual Basic], disposing of system
- system resources
- Using statement [Visual Basic], Using...End Using
- Using block
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
ms.openlocfilehash: 6594c9e2eedf756cc7a46c2c17deab58fcba3a8c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100480667"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a>Nasıl yapılır: Bir Sistem Kaynağını Atma (Visual Basic)

`Using`Kodunuzun bloğundan çıkış yaparken sistemin bir kaynağı ortadan kaldırabileceğini güvence altına almak için bir bloğu kullanabilirsiniz. Bu, büyük miktarda bellek tüketen bir sistem kaynağı kullanıyorsanız veya diğer bileşenlerin de kullanılmasını istiyorsanız kullanışlıdır.  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a>Kodunuz ile işiniz bittiğinde bir veritabanı bağlantısını atmak için  
  
1. Kaynak dosyanızın başlangıcında (Bu durumda,) veritabanı bağlantısı için uygun [Içeri aktarmalar ifadesini (.net ad alanı ve türü)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) eklediğinizden emin olun <xref:System.Data.SqlClient> .  
  
2. `Using` `Using` Ve deyimleriyle bir blok oluşturun `End Using` . Bloğun içinde, veritabanı bağlantısıyla ilgilenen kodu koyun.  
  
3. Bağlantıyı bildirin ve deyimin bir parçası olarak bir örneğini oluşturun `Using` .  
  
    ```vb  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     İşlenmeyen bir özel durum da dahil olmak üzere bloğundan çıktığınızda sistem kaynağı ortadan kaldırsın.  
  
     `sqc` `Using` Kapsamı bloğuyla sınırlı olduğundan bloğunun dışından erişemediğini unutmayın.  
  
     Bu tekniği, bir dosya tanıtıcısı veya bir COM sarmalayıcı gibi bir sistem kaynağı üzerinde kullanabilirsiniz. `Using`Bloğundan çıktıktan sonra kaynağı diğer bileşenler için kullanılabilir durumda bırakmaya emin olmak istediğinizde bir blok kullanırsınız `Using` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.SqlClient.SqlConnection>
- [Denetim akışı](index.md)
- [Karar Yapıları](decision-structures.md)
- [Döngü Yapıları](loop-structures.md)
- [Diğer Denetim Yapıları](other-control-structures.md)
- [İç İçe Geçmiş Denetim Yapıları](nested-control-structures.md)
- [Using deyimleri](../../../language-reference/statements/using-statement.md)
