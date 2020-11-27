---
title: UI Otomasyon Sağlayıcıları İstemci Programına Uygulama
description: Bir uygulamada istemci tarafı UI Otomasyon sağlayıcısının nasıl uygulanacağını gösteren bir örnek görürsünüz. Bunun yaygın olmayan bir senaryo olduğunu unutmayın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client-side UI Automation provider, implementation within applications
- UI Automation, implementing client-side provider within application
ms.assetid: f325f0d8-1715-41ea-85ca-45b82ffea8bc
ms.openlocfilehash: 486e05f9080b686c48454dfcfceaaa666fa57f67
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269593"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a><span data-ttu-id="df0bf-104">UI Otomasyon Sağlayıcıları İstemci Programına Uygulama</span><span class="sxs-lookup"><span data-stu-id="df0bf-104">Implement UI Automation Providers in a Client Application</span></span>

> [!NOTE]
> <span data-ttu-id="df0bf-105">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="df0bf-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="df0bf-106">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="df0bf-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="df0bf-107">Bu konu, bir uygulama içinde bir istemci tarafı UI Otomasyon sağlayıcısının nasıl uygulanacağını gösteren örnek kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="df0bf-107">This topic contains example code that shows how to implement a client-side UI Automation provider within an application.</span></span>  
  
 <span data-ttu-id="df0bf-108">Bu, yaygın olmayan bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="df0bf-108">This is an uncommon scenario.</span></span> <span data-ttu-id="df0bf-109">Çoğu zaman, bir UI Otomasyonu istemci uygulaması, sunucu tarafı sağlayıcıları veya bir DLL içinde bulunan istemci tarafı sağlayıcıları kullanır.</span><span class="sxs-lookup"><span data-stu-id="df0bf-109">Most often, a UI Automation client application uses server-side providers, or client-side providers that reside in a DLL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df0bf-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="df0bf-110">Example</span></span>  

 <span data-ttu-id="df0bf-111">Aşağıdaki örnek kod, bir konsol penceresi için basit bir sağlayıcı uygular.</span><span class="sxs-lookup"><span data-stu-id="df0bf-111">The following example code implements a simple provider for a console window.</span></span> <span data-ttu-id="df0bf-112">Kod, yararlı bir işlevselliğe sahip değildir, ancak istemci kodu içinde sağlayıcıyı ayarlama ve kullanarak kaydetme konusunda temel adımları göstermeye yöneliktir <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A> .</span><span class="sxs-lookup"><span data-stu-id="df0bf-112">The code does not have any useful functionality, but is intended to demonstrate the basic steps in setting up a provider within client code and registering it by using <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a><span data-ttu-id="df0bf-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df0bf-113">See also</span></span>

- [<span data-ttu-id="df0bf-114">UI Otomasyon Sağlayıcılara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="df0bf-114">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="df0bf-115">İstemci Tarafı Sağlayıcı Derlemesini Kaydetme</span><span class="sxs-lookup"><span data-stu-id="df0bf-115">Register a Client-Side Provider Assembly</span></span>](register-a-client-side-provider-assembly.md)
- [<span data-ttu-id="df0bf-116">İstemci Tarafı UI Otomasyon Sağlayıcı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="df0bf-116">Create a Client-Side UI Automation Provider</span></span>](create-a-client-side-ui-automation-provider.md)
- [<span data-ttu-id="df0bf-117">İstemci Tarafı UI Otomasyon Sağlayıcıyı Uygulama</span><span class="sxs-lookup"><span data-stu-id="df0bf-117">Client-Side UI Automation Provider Implementation</span></span>](client-side-ui-automation-provider-implementation.md)
