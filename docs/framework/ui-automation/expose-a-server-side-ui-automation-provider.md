---
title: Sunucu Tarafı UI Otomasyon Sağlayıcıyı Gösterme
description: Bir System. Windows. Forms. Control penceresinde barındırılan bir sunucu tarafı UI Otomasyon sağlayıcısını açığa çıkarmak için bir örnek görüntüleyin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- expose a server-side UI Automation provider
- UI Automation, server-side provider, exposing
- server-side UI Automation provider, exposing
ms.assetid: 55d419c0-2201-4101-90c9-2888df4dbb47
ms.openlocfilehash: be39130c7a91fc081256bf14a87f503d27f45129
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276535"
---
# <a name="expose-a-server-side-ui-automation-provider"></a>Sunucu Tarafı UI Otomasyon Sağlayıcıyı Gösterme

> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, bir pencerede barındırılan sunucu tarafı UI Otomasyon sağlayıcısını açığa çıkarmak için örnek kodu içerir <xref:System.Windows.Forms.Control?displayProperty=nameWithType> .  
  
 Örnek, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bir istemci uygulaması pencere hakkında bilgi istediğinde çekirdek hizmet tarafından gönderilen ileti olan WM_GETOBJECT yakalamak için pencere yordamını geçersiz kılar.  
  
## <a name="example"></a>Örnek  

 [!code-csharp[UIAFragmentProvider_snip#116](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#116)]
 [!code-vb[UIAFragmentProvider_snip#116](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#116)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Sağlayıcılara Genel Bakış](ui-automation-providers-overview.md)
- [Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama](server-side-ui-automation-provider-implementation.md)
