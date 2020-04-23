---
title: 'Nasıl Yapılır: Windows Hizmetini Duraklatma (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- ServiceController.Pause
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: eddb9409-942b-46b6-a2ce-fbd4c65f2790
author: ghogen
ms.openlocfilehash: 166eda4a9348188fa6e5048fd3ce41645cde4816
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053591"
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a><span data-ttu-id="dfdde-102">Nasıl Yapılır: Windows Hizmetini Duraklatma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dfdde-102">How to: Pause a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="dfdde-103">Bu örnek, <xref:System.ServiceProcess.ServiceController> bileşeni yerel bilgisayardaki IIS Yöneticisi hizmetini duraklatmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="dfdde-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to pause the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfdde-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="dfdde-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 <span data-ttu-id="dfdde-105">Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dfdde-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="dfdde-106">Kod parçacığı seçicide, Windows **Işletim sistemi > Windows Hizmetleri**' nde bulunur.</span><span class="sxs-lookup"><span data-stu-id="dfdde-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="dfdde-107">Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="dfdde-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dfdde-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="dfdde-108">Compiling the Code</span></span>  
 <span data-ttu-id="dfdde-109">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="dfdde-109">This example requires:</span></span>  
  
- <span data-ttu-id="dfdde-110">System. ServiceProcess. dll dosyasına bir proje başvurusu.</span><span class="sxs-lookup"><span data-stu-id="dfdde-110">A project reference to System.serviceprocess.dll.</span></span>  
  
- <span data-ttu-id="dfdde-111"><xref:System.ServiceProcess> Ad alanının üyelerine erişin.</span><span class="sxs-lookup"><span data-stu-id="dfdde-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="dfdde-112">Kodunuzda üye `Imports` adlarını tam olarak nitedıysanız bir ifade ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dfdde-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="dfdde-113">Daha fazla bilgi için bkz. [Imports açıklaması (.net ad alanı ve türü)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="dfdde-113">For more information, see [Imports Statement (.NET Namespace and Type)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="dfdde-114">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="dfdde-114">Robust Programming</span></span>  
 <span data-ttu-id="dfdde-115"><xref:System.ServiceProcess.ServiceController> Sınıfının <xref:System.ServiceProcess.ServiceController.MachineName%2A> özelliği, varsayılan olarak yerel bilgisayardır.</span><span class="sxs-lookup"><span data-stu-id="dfdde-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="dfdde-116">Başka bir bilgisayardaki Windows hizmetlerine başvurmak için, <xref:System.ServiceProcess.ServiceController.MachineName%2A> özelliği bu bilgisayarın adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="dfdde-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="dfdde-117">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="dfdde-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="dfdde-118">Hizmet duraklatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="dfdde-118">The service cannot be paused.</span></span> <span data-ttu-id="dfdde-119">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="dfdde-119">(<xref:System.InvalidOperationException>)</span></span>  
  
- <span data-ttu-id="dfdde-120">Sistem API 'sine erişirken bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="dfdde-120">An error occurred when accessing a system API.</span></span> <span data-ttu-id="dfdde-121">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="dfdde-121">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="dfdde-122">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="dfdde-122">.NET Framework Security</span></span>  
 <span data-ttu-id="dfdde-123">Bilgisayardaki hizmetlerin denetimi, içindeki izinleri ayarlamak <xref:System.ServiceProcess.ServiceControllerPermissionAccess> için kullanılarak kısıtlanabilir. <xref:System.ServiceProcess.ServiceControllerPermission></span><span class="sxs-lookup"><span data-stu-id="dfdde-123">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission>.</span></span>  
  
 <span data-ttu-id="dfdde-124">Hizmet bilgilerine erişim, içindeki izinleri ayarlamak <xref:System.Security.Permissions.PermissionState> için kullanılarak kısıtlanabilir. <xref:System.Security.Permissions.SecurityPermission></span><span class="sxs-lookup"><span data-stu-id="dfdde-124">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> to set permissions in the <xref:System.Security.Permissions.SecurityPermission>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfdde-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfdde-125">See also</span></span>

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>
- [<span data-ttu-id="dfdde-126">Nasıl Yapılır: Windows Hizmetini Devam Ettirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dfdde-126">How to: Continue a Windows Service (Visual Basic)</span></span>](how-to-continue-a-windows-service-visual-basic.md)
