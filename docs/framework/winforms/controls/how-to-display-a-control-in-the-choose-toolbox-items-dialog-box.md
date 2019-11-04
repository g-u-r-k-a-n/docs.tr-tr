---
title: 'Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme'
ms.date: 08/23/2019
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: db4b3ac020e967a6a0c291103d825ac71cebda23
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458274"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="124de-102">Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="124de-102">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>

<span data-ttu-id="124de-103">Denetimleri geliştirip dağıtırken, **araç** kutusunu sağ tıklayıp **öğeleri seç**' i seçtiğinizde görüntülenen Visual Studio 'Nun **araç kutusu öğelerini Seç** iletişim kutusunda bu denetimlerin görünmesini isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="124de-103">As you develop and distribute controls, you may want those controls to appear in the **Choose Toolbox Items** dialog box of Visual Studio, which is displayed when you right-click the **Toolbox** and select **Choose Items**.</span></span> <span data-ttu-id="124de-104">AssemblyFoldersEx kayıt yordamını kullanarak denetiminizin bu iletişim kutusunda görünmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="124de-104">You can enable your control to appear in this dialog box by using the AssemblyFoldersEx registration procedure.</span></span>

<span data-ttu-id="124de-105">Denetiminizi araç kutusu öğelerini Seç iletişim kutusunda göstermek için:</span><span class="sxs-lookup"><span data-stu-id="124de-105">To display your control in the Choose Toolbox Items dialog box:</span></span>

- <span data-ttu-id="124de-106">Denetim derlemenizi genel bütünleştirilmiş kod önbelleğine yükler.</span><span class="sxs-lookup"><span data-stu-id="124de-106">Install your control assembly to the global assembly cache.</span></span> <span data-ttu-id="124de-107">Daha fazla bilgi için bkz. [nasıl yapılır: bir derlemeyi genel derleme önbelleğine yüklemek](../../app-domains/install-assembly-into-gac.md).</span><span class="sxs-lookup"><span data-stu-id="124de-107">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../app-domains/install-assembly-into-gac.md).</span></span>

  <span data-ttu-id="124de-108">veya</span><span class="sxs-lookup"><span data-stu-id="124de-108">-or-</span></span>

- <span data-ttu-id="124de-109">AssemblyFoldersEx kayıt yordamını kullanarak denetiminizi ve onunla ilişkili tasarım zamanı derlemelerini kaydedin.</span><span class="sxs-lookup"><span data-stu-id="124de-109">Register your control and its associated design-time assemblies by using the AssemblyFoldersEx registration procedure.</span></span> <span data-ttu-id="124de-110">AssemblyFoldersEx, üçüncü taraf satıcıların destekledikleri her bir sürüm için yolları depolayacağı bir kayıt defteri konumudur.</span><span class="sxs-lookup"><span data-stu-id="124de-110">AssemblyFoldersEx is a registry location where third-party vendors store paths for each version of the framework that they support.</span></span> <span data-ttu-id="124de-111">Tasarım zamanı çözümlemesi, başvuru derlemelerini bulmak için bu kayıt defteri konumuna bakabilir.</span><span class="sxs-lookup"><span data-stu-id="124de-111">Design-time resolution can look in this registry location to find reference assemblies.</span></span> <span data-ttu-id="124de-112">Kayıt defteri betiği, araç kutusunda görünmesini istediğiniz denetimleri belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="124de-112">The registry script can specify the controls you want to appear in the Toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="124de-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="124de-113">See also</span></span>

- [<span data-ttu-id="124de-114">Tasarım Zamanında Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="124de-114">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="124de-115">Nasıl yapılır: Bir Bütünleştirilmiş Kodu Genel Derleme Önbelleğine Yükleme</span><span class="sxs-lookup"><span data-stu-id="124de-115">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../app-domains/install-assembly-into-gac.md)
- [<span data-ttu-id="124de-116">İzlenecek yol: Araç Kutusunu Otomatik Olarak Özel Bileşenlerle Doldurma</span><span class="sxs-lookup"><span data-stu-id="124de-116">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
