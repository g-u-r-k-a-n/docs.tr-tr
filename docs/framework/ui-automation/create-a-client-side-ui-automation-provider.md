---
title: İstemci Tarafı UI Otomasyon Sağlayıcı Oluşturma
description: İstemci tarafı UI Otomasyon sağlayıcısı oluşturma hakkında bir örnek görüntüleyin. Örnek, bir konsol penceresi için basit bir istemci tarafı sağlayıcı uygular.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, creating client-side provider
- client-side UI Automation provider, creating
ms.assetid: d91edaf2-be28-41ec-a508-af421cb43c3d
ms.openlocfilehash: 17a6deca2efc67d1409e89f7accf7a3b89a27807
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276548"
---
# <a name="create-a-client-side-ui-automation-provider"></a><span data-ttu-id="08c72-104">İstemci Tarafı UI Otomasyon Sağlayıcı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="08c72-104">Create a Client-Side UI Automation Provider</span></span>

> [!NOTE]
> <span data-ttu-id="08c72-105">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="08c72-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="08c72-106">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="08c72-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="08c72-107">Bu konu, bir istemci tarafı UI Otomasyon sağlayıcısının nasıl uygulanacağını gösteren örnek kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="08c72-107">This topic contains example code that shows how to implement a client-side UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08c72-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="08c72-108">Example</span></span>  

 <span data-ttu-id="08c72-109">Aşağıdaki örnek kod, bir konsol penceresi için çok basit bir istemci tarafı sağlayıcı uygulayan bir dinamik bağlantı kitaplığı (DLL) içinde oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="08c72-109">The following example code can be built into a dynamic-link library (DLL) that implements a very simple client-side provider for a console window.</span></span> <span data-ttu-id="08c72-110">Kod yararlı bir işlevselliğe sahip değildir, ancak bir UI Otomasyonu istemci uygulaması tarafından kaydedilebileceği bir sağlayıcı derlemesini ayarlamaya yönelik temel adımları göstermeye yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="08c72-110">The code does not have any useful functionality, but is intended to demonstrate the basic steps in setting up a provider assembly that can be registered by a UI Automation client application.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSProviderProgram.cs#101)]
 [!code-vb[UIAClientSideProvider_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csproviderprogram.vb#101)]  
  
## <a name="see-also"></a><span data-ttu-id="08c72-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08c72-111">See also</span></span>

- [<span data-ttu-id="08c72-112">UI Otomasyon Sağlayıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="08c72-112">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="08c72-113">İstemci Tarafı Sağlayıcı Derlemesini Kaydetme</span><span class="sxs-lookup"><span data-stu-id="08c72-113">Register a Client-Side Provider Assembly</span></span>](register-a-client-side-provider-assembly.md)
