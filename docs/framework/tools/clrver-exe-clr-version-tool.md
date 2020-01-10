---
title: Clrver.exe (CLR Sürüm Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- Clrver.exe
- CLR Version tool
ms.assetid: cbc2ee86-bdc8-4a65-a8f1-ba23bce3a699
ms.openlocfilehash: bfc612ef5455e1b4a03d15fd99a8a1873d2c7c08
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715793"
---
# <a name="clrverexe-clr-version-tool"></a><span data-ttu-id="36716-102">Clrver.exe (CLR Sürüm Aracı)</span><span class="sxs-lookup"><span data-stu-id="36716-102">Clrver.exe (CLR Version Tool)</span></span>
<span data-ttu-id="36716-103">CLR Sürüm aracı (Clrver.exe) ortak dil çalışma zamanının (CLR) bilgisayarda yüklü tüm sürümlerini bildirir.</span><span class="sxs-lookup"><span data-stu-id="36716-103">The CLR Version tool (Clrver.exe) reports all the installed versions of the common language runtime (CLR) on the computer.</span></span>  
  
 <span data-ttu-id="36716-104">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="36716-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="36716-105">Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="36716-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="36716-106">Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="36716-106">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="36716-107">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="36716-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36716-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36716-108">Syntax</span></span>  
  
```console  
clrver [option]  
```  
  
## <a name="options"></a><span data-ttu-id="36716-109">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="36716-109">Options</span></span>  
  
|<span data-ttu-id="36716-110">Seçenek</span><span class="sxs-lookup"><span data-stu-id="36716-110">Option</span></span>|<span data-ttu-id="36716-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36716-111">Description</span></span>|  
|------------|-----------------|  
|`-all`|<span data-ttu-id="36716-112">Bilgisayarda CLR'yi kullanan tüm işlemleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="36716-112">Displays all processes on the computer that are using the CLR.</span></span>|  
|<span data-ttu-id="36716-113">*Kişisel*</span><span class="sxs-lookup"><span data-stu-id="36716-113">*pid*</span></span>|<span data-ttu-id="36716-114">Belirtilen işlem kimliğine (PID) sahip işlem tarafından kullanılan CLR'nin sürümlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="36716-114">Displays the version(s) of the CLR used by the process that has the specified process ID (PID).</span></span>|  
|`-?`|<span data-ttu-id="36716-115">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="36716-115">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36716-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="36716-116">Remarks</span></span>  
 <span data-ttu-id="36716-117">Clrver.exe'yi hiçbir seçenek olmadan çağırırsanız, yüklü tüm CLR sürümlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="36716-117">If you call Clrver.exe with no options, it displays all installed CLR versions.</span></span> <span data-ttu-id="36716-118">Başka bir kullanıcı için bir PID belirtirseniz, sürüm bilgisi elde etmek için yönetici izinlerinizin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="36716-118">If you specify a PID for another user, you must have administrative permissions to obtain the version information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36716-119">Windows Vista ve sonraki sürümlerde, Kullanıcı Hesabı Denetimi (UAC) bir kullanıcının ayrıcalıkları belirler.</span><span class="sxs-lookup"><span data-stu-id="36716-119">In Windows Vista and later, User Account Control (UAC) determines the privileges of a user.</span></span> <span data-ttu-id="36716-120">Yerleşik Yöneticiler grubunun bir üyesi iseniz, size iki çalışma zamanı erişim belirteci atanır: Standart kullanıcı erişim belirteci ve yönetici erişim belirteci.</span><span class="sxs-lookup"><span data-stu-id="36716-120">If you are a member of the Built-in Administrators group, you are assigned two run-time access tokens: a standard user access token and an administrator access token.</span></span> <span data-ttu-id="36716-121">Varsayılan olarak, standart kullanıcı rolünde olursunuz.</span><span class="sxs-lookup"><span data-stu-id="36716-121">By default, you are in the standard user role.</span></span> <span data-ttu-id="36716-122">Yönetici izni gerektiren kodları yürütmek için önce ayrıcalıklarınızı standart kullanıcıdan yöneticiye yükseltmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="36716-122">To execute code that requires administrative permission, you must first elevate your privileges from standard user to administrator.</span></span> <span data-ttu-id="36716-123">Komut istemi simgesini sağ tıklatıp komut istemini başlattıktan sonra, yönetici olarak çalıştırmak istediğinizi belirterek bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36716-123">You can do this when you start the command prompt by right-clicking the command prompt icon and indicating that you want to run as an administrator.</span></span>  
  
 <span data-ttu-id="36716-124">SYSTEM, LOCAL SERVICE ve NETWORK SERVICE işlemlerinin CLR sürümünü belirlemeye çalışmak PID'in varolmadığını belirten bir ileti alınmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="36716-124">Attempting to determine the CLR version for SYSTEM, LOCAL SERVICE, and NETWORK SERVICE processes results in a message indicating that the PID doesn't exist.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="36716-125">Örnekler</span><span class="sxs-lookup"><span data-stu-id="36716-125">Examples</span></span>  
 <span data-ttu-id="36716-126">Aşağıdaki komut bilgisayarda yüklü tüm CLR sürümlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="36716-126">The following command displays all the versions of the CLR installed on the computer.</span></span>  
  
 `clrver`  
  
 <span data-ttu-id="36716-127">Aşağıdaki komut, işlem 128 tarafından kullanılan CLR sürümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="36716-127">The following command displays the version of the CLR used by process 128.</span></span>  
  
 `clrver 128`  
  
 <span data-ttu-id="36716-128">Aşağıdaki komut, yönetilen tüm işlemleri ve kullanmakta oldukları CLR sürümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="36716-128">The following command displays all the managed processes and the version of the CLR they are using.</span></span>  
  
 `Clrver -all`  
  
## <a name="see-also"></a><span data-ttu-id="36716-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36716-129">See also</span></span>

- [<span data-ttu-id="36716-130">Araçlar</span><span class="sxs-lookup"><span data-stu-id="36716-130">Tools</span></span>](index.md)
- [<span data-ttu-id="36716-131">Komut İstemleri</span><span class="sxs-lookup"><span data-stu-id="36716-131">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
