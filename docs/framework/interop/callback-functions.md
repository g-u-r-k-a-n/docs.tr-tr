---
title: Geri Çağırma İşlevleri
description: Yönetilmeyen DLL işlevinin bir görevi tamamlarına yardımcı olan, yönetilen bir uygulamayla kod olan geri çağırma işlevleri hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- callback function
- platform invoke, calling unmanaged functions
ms.assetid: c0aa8533-3b3b-42e8-9f60-84919793098c
ms.openlocfilehash: 659f384f7bfc3a2326a40a9536c977d7c41ab076
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283165"
---
# <a name="callback-functions"></a><span data-ttu-id="6161d-103">Geri Çağırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="6161d-103">Callback Functions</span></span>

<span data-ttu-id="6161d-104">Bir geri çağırma işlevi, yönetilmeyen bir DLL işlevinin bir görevi tamammesine yardımcı olan bir yönetilen uygulama içindeki koddur.</span><span class="sxs-lookup"><span data-stu-id="6161d-104">A callback function is code within a managed application that helps an unmanaged DLL function complete a task.</span></span> <span data-ttu-id="6161d-105">Bir geri çağırma işlevine yapılan çağrılar, yönetilen bir uygulamadan, bir DLL işlevi aracılığıyla ve yönetilen uygulamaya geri dönerek dolaylı olarak geçer.</span><span class="sxs-lookup"><span data-stu-id="6161d-105">Calls to a callback function pass indirectly from a managed application, through a DLL function, and back to the managed implementation.</span></span> <span data-ttu-id="6161d-106">Platform çağırma ile çağrılan birçok DLL işlevinden bazıları, yönetilen kodda düzgün şekilde çalışması için bir geri çağırma işlevi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6161d-106">Some of the many DLL functions called with platform invoke require a callback function in managed code to run properly.</span></span>  
  
 <span data-ttu-id="6161d-107">Yönetilen koddan çoğu DLL işlevini çağırmak için, işlevin yönetilen bir tanımını oluşturun ve ardından bunu çağırın.</span><span class="sxs-lookup"><span data-stu-id="6161d-107">To call most DLL functions from managed code, you create a managed definition of the function and then call it.</span></span> <span data-ttu-id="6161d-108">İşlem basittir.</span><span class="sxs-lookup"><span data-stu-id="6161d-108">The process is straightforward.</span></span>  
  
 <span data-ttu-id="6161d-109">Bir geri çağırma işlevi gerektiren DLL işlevinin kullanılması bazı ek adımlara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6161d-109">Using a DLL function that requires a callback function has some additional steps.</span></span> <span data-ttu-id="6161d-110">Önce, işlevin belgelerine bakarak işlevin geri çağırma gerektirip gerektirmediğini belirlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="6161d-110">First, you must determine whether the function requires a callback by looking at the documentation for the function.</span></span> <span data-ttu-id="6161d-111">Ardından, yönetilen uygulamanızda geri çağırma işlevini oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6161d-111">Next, you have to create the callback function in your managed application.</span></span> <span data-ttu-id="6161d-112">Son olarak, DLL işlevini çağırır ve geri çağırma işlevine bir işaretçiyi bir bağımsız değişken olarak geçirerek.</span><span class="sxs-lookup"><span data-stu-id="6161d-112">Finally, you call the DLL function, passing a pointer to the callback function as an argument.</span></span>

 <span data-ttu-id="6161d-113">Aşağıdaki çizim, geri çağırma işlevini ve uygulama adımlarını özetler:</span><span class="sxs-lookup"><span data-stu-id="6161d-113">The following illustration summarizes the callback function and implementation steps:</span></span>  
  
 ![Platform çağırma geri çağırma işlemini gösteren diyagram.](./media/callback-functions/platform-invoke-callback-process.gif)  
  
 <span data-ttu-id="6161d-115">Geri çağırma işlevleri, bir görevin tekrar tekrar gerçekleştirildiği durumlarda kullanım için idealdir.</span><span class="sxs-lookup"><span data-stu-id="6161d-115">Callback functions are ideal for use in situations in which a task is performed repeatedly.</span></span> <span data-ttu-id="6161d-116">Diğer bir yaygın kullanım, Windows API 'sindeki **Enumfontaileleri**, **EnumPrinters** ve **EnumWindows** gibi numaralandırma işlevleridir.</span><span class="sxs-lookup"><span data-stu-id="6161d-116">Another common usage is with enumeration functions, such as **EnumFontFamilies**, **EnumPrinters**, and **EnumWindows** in the Windows API.</span></span> <span data-ttu-id="6161d-117">**EnumWindows** işlevi, her pencerede bir görevi gerçekleştirmek için geri çağırma işlevini çağırarak bilgisayarınızdaki mevcut tüm pencereleri sıralar.</span><span class="sxs-lookup"><span data-stu-id="6161d-117">The **EnumWindows** function enumerates through all existing windows on your computer, calling the callback function to perform a task on each window.</span></span> <span data-ttu-id="6161d-118">Yönergeler ve bir örnek için bkz. [nasıl yapılır: geri çağırma Işlevlerini uygulama](how-to-implement-callback-functions.md).</span><span class="sxs-lookup"><span data-stu-id="6161d-118">For instructions and an example, see [How to: Implement Callback Functions](how-to-implement-callback-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6161d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6161d-119">See also</span></span>

- [<span data-ttu-id="6161d-120">Nasıl yapılır: Geri Çağırma İşlevlerini Uygulama</span><span class="sxs-lookup"><span data-stu-id="6161d-120">How to: Implement Callback Functions</span></span>](how-to-implement-callback-functions.md)
- [<span data-ttu-id="6161d-121">DLL İşlevini Çağırma</span><span class="sxs-lookup"><span data-stu-id="6161d-121">Calling a DLL Function</span></span>](calling-a-dll-function.md)
