---
description: 'Daha fazla bilgi edinin: Tanılama sembol deposu arabirimleri'
title: Tanılama Sembol Deposu Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
ms.openlocfilehash: 253a6e5eaa97c91332bca62f8fc47ad2945bf741
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800441"
---
# <a name="diagnostics-symbol-store-interfaces"></a>Tanılama Sembol Deposu Arabirimleri

Bu konuda, bir derleyicinin hata ayıklayıcı tarafından kullanılmak üzere sembol bilgisi oluşturmasını sağlayan yönetilmeyen arabirimler açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [IBindingDisplay Arabirimi](ibindingdisplay-interface.md)  
 Çalışan uygulamayla ilgili geçerli bağlama bilgilerini görüntüleyen yöntemler sağlar.  
  
 [IDebugAutoAttach Arabirimi](idebugautoattach-interface.md)  
 Sunucu tarafından çağrılan bir hata ayıklayıcı otomatik iliştirme arabirimini tanımlar.  
  
 [INotifyConnection2 Arabirimi](inotifyconnection2-interface.md)  
 Bağlantı bildirim kaynağını kaydetme ve kaydını silme yöntemlerini bildirir.  
  
 [INotifySink2 Arabirimi](inotifysink2-interface.md)  
 Havuz bildirimi için yöntemler bildirir.  
  
 [INotifySource2 Arabirimi](inotifysource2-interface.md)  
 Bildirim filtrelerini ayarlamak için bir yöntem bildirir.  
  
 [ISymENCUnmanagedMethod Arabirimi](isymencunmanagedmethod-interface.md)  
 Düzenle ve devam et özelliği hakkında bilgi sağlar.  
  
 [ISymUnmanagedAsyncMethod Arabirimi](isymunmanagedasyncmethod-interface.md)  
 Bu arabirim, [ıvmunmanagedasyncmethodpropertieswriter arabirimini](isymunmanagedasyncmethodpropertieswriter-interface.md)tamamlayan okuma işlemi.  
  
 [ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi](isymunmanagedasyncmethodpropertieswriter-interface.md)  
 Yöntem simgesi başına isteğe bağlı zaman uyumsuz yöntem bilgilerinin tanımına izin verir. , Bir açık yöntemle kullanılmalıdır (diğer bir deyişle, [OpenMethod yöntemi](isymunmanagedwriter-openmethod-method.md)ve [CloseMethod yöntemi](isymunmanagedwriter-closemethod-method.md)çağrıları arasında).  
  
 [ISymUnmanagedBinder Arabirimi](isymunmanagedbinder-interface.md)  
 Yönetilmeyen kod için bir sembol cildi temsil eder.  
  
 [ISymUnmanagedBinder2 Arabirimi](isymunmanagedbinder2-interface.md)  
 Yönetilmeyen kod için bir sembol cildi temsil eder ve arabirimi genişletir `ISymUnmanagedBinder` .  
  
 [ISymUnmanagedBinder3 Arabirimi](isymunmanagedbinder3-interface.md)  
 Yönetilmeyen kod için bir sembol cildi temsil eder ve arabirimi genişletir `ISymUnmanagedBinder` .  
  
 [ISymUnmanagedConstant Arabirimi](isymunmanagedconstant-interface.md)  
 Yönetilmeyen sabitlere erişim sağlar.  
  
 [ISymUnmanagedDispose Arabirimi](isymunmanageddispose-interface.md)  
 Yönetilmeyen kaynakları ortadan kaldırın.  
  
 [ISymUnmanagedDocument Arabirimi](isymunmanageddocument-interface.md)  
 Bir sembol deposu tarafından başvurulan bir belgeyi temsil eder.  
  
 [ISymUnmanagedDocumentWriter Arabirimi](isymunmanageddocumentwriter-interface.md)  
 Sembol deposu tarafından başvurulan bir belgeye yazmak için yöntemler sağlar.  
  
 [ISymUnmanagedENCUpdate Arabirimi](isymunmanagedencupdate-interface.md)  
 Düzenle ve devam et özelliği için yöntemler sağlar.  
  
 [ISymUnmanagedMethod Arabirimi](isymunmanagedmethod-interface.md)  
 Sembol deposu içindeki bir yöntemi temsil eder.  
  
 [ISymUnmanagedNamespace Arabirimi](isymunmanagednamespace-interface.md)  
 Bir ad alanını temsil eder.  
  
 [ISymUnmanagedReader Arabirimi](isymunmanagedreader-interface.md)  
 Bir sembol deposu içindeki belgelere, yöntemlere ve değişkenlere erişim sağlayan bir sembol okuyucuyu temsil eder.  
  
 [ISymUnmanagedReader2 Arabirimi](isymunmanagedreader2-interface.md)  
 Bir yöntem belirteci ve bir düzenleme ve kopyalama sürümü numarası verilen bir sembol okuyucu yöntemini alır.  
  
 [ISymUnmanagedReaderSymbolSearchInfo Arabirimi](isymunmanagedreadersymbolsearchinfo-interface.md)  
 Sembol arama bilgilerini alan yöntemler sağlar.  
  
 [ISymUnmanagedScope Arabirimi](isymunmanagedscope-interface.md)  
 Bir yöntem içindeki bir sözcük temelli kapsamı temsil eder.  
  
 [ISymUnmanagedScope2 Arabirimi](isymunmanagedscope2-interface.md)  
 Bir yöntem içindeki bir sözcük temelli kapsamı temsil eder ve `ISymUnmanagedScope` arabirimi, kapsam içinde tanımlanan sabitler hakkında bilgi alan yöntemlerle genişletir.  
  
 [ISymUnmanagedSourceServerModule Arabirimi](isymunmanagedsourceservermodule-interface.md)  
 Bir modül için kaynak sunucu verisi sağlar.  
  
 [ISymUnmanagedSymbolSearchInfo Arabirimi](isymunmanagedsymbolsearchinfo-interface.md)  
 Arama yolu hakkında bilgi almak için yöntemler sağlar.  
  
 [ISymUnmanagedVariable Arabirimi](isymunmanagedvariable-interface.md)  
 Bir parametre, yerel değişken veya bir alan gibi bir değişkeni temsil eder.  
  
 [ISymUnmanagedWriter Arabirimi](isymunmanagedwriter-interface.md)  
 Bir sembol yazıcısını temsil eder ve belgeleri, dizi noktalarını, sözcük temelli kapsamları ve değişkenleri tanımlamak için yöntemler sağlar.  
  
 [ISymUnmanagedWriter2 Arabirimi](isymunmanagedwriter2-interface.md)  
 Bir sembol yazıcısını temsil eder ve belgeleri, dizi noktalarını, sözcük temelli kapsamları ve değişkenleri tanımlamak için yöntemler sağlar. Arabirimini genişletir `ISymUnmanagedWriter` .  
  
 [ISymUnmanagedWriter3 Arabirimi](isymunmanagedwriter3-interface.md)  
 Bir sembol yazıcısını temsil eder ve belgeleri, dizi noktalarını, sözcük temelli kapsamları ve değişkenleri tanımlamak için yöntemler sağlar. Arabirimini genişletir `ISymUnmanagedWriter` .  
  
 [ISymUnmanagedWriter4 Arabirimi](isymunmanagedwriter4-interface.md)  
 ISymUnmanagedWriter4 arabirimi.  
  
 [ISymUnmanagedWriter5 Arabirimi](isymunmanagedwriter5-interface.md)  
 ISymUnmanagedWriter5 arabirimi.  
  
## <a name="related-sections"></a>İlgili Bölümler  

 [Tanılama Sembol Deposu Numaralandırmaları](diagnostics-symbol-store-enumerations.md)  
  
 [Tanılama Sembol Deposu Yapıları](diagnostics-symbol-store-structures.md)  
  
 [Hata Ayıklama](../debugging/index.md)
