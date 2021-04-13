---
title: Model Oluşturucu 'da GPU desteği nasıl yüklenir
description: Model Oluşturucu 'da GPU desteğini yüklemeyi öğrenin
ms.date: 04/08/2021
author: luisquintanilla
ms.author: luquinta
ms.topic: how-to
ms.openlocfilehash: 81f84a17429fd03506bbce30f5646941e4e80b3b
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255434"
---
# <a name="how-to-install-gpu-support-in-model-builder"></a><span data-ttu-id="0db1b-103">Model Oluşturucu 'da GPU desteği nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="0db1b-103">How to install GPU support in Model Builder</span></span>

<span data-ttu-id="0db1b-104">Model Oluşturucu ile GPU 'yu kullanarak GPU sürücülerini yüklemeyi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="0db1b-104">Learn how to install the GPU drivers to use your GPU with Model Builder.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0db1b-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="0db1b-105">Prerequisites</span></span>

- <span data-ttu-id="0db1b-106">Model Oluşturucu Visual Studio uzantısı.</span><span class="sxs-lookup"><span data-stu-id="0db1b-106">Model Builder Visual Studio extension.</span></span> <span data-ttu-id="0db1b-107">Uzantı, 16.6.1 sürümü itibariyle Visual Studio 'da yerleşik olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="0db1b-107">The extension is built into Visual Studio as of version 16.6.1.</span></span>
- <span data-ttu-id="0db1b-108">[Model Oluşturucu Visual STUDIO GPU desteği uzantısı](https://marketplace.visualstudio.com/items?itemName=MLNET.ModelBuilderGPU).</span><span class="sxs-lookup"><span data-stu-id="0db1b-108">[Model Builder Visual Studio GPU support extension](https://marketplace.visualstudio.com/items?itemName=MLNET.ModelBuilderGPU).</span></span>
- <span data-ttu-id="0db1b-109">En az bir CUDA uyumlu GPU.</span><span class="sxs-lookup"><span data-stu-id="0db1b-109">At least one CUDA compatible GPU.</span></span> <span data-ttu-id="0db1b-110">Uyumlu GPU 'ların listesi için bkz. [NVIDIA Kılavuzu](https://developer.nvidia.com/cuda-gpus).</span><span class="sxs-lookup"><span data-stu-id="0db1b-110">For a list of compatible GPUs, see [NVIDIA's guide](https://developer.nvidia.com/cuda-gpus).</span></span>
- <span data-ttu-id="0db1b-111">NVıDıA geliştirici hesabı.</span><span class="sxs-lookup"><span data-stu-id="0db1b-111">NVIDIA developer account.</span></span> <span data-ttu-id="0db1b-112">Aboneliğiniz yoksa [ücretsiz bir hesap](https://developer.nvidia.com/developer-program) oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0db1b-112">If you don't have one, [create a free account](https://developer.nvidia.com/developer-program).</span></span>

## <a name="install-dependencies"></a><span data-ttu-id="0db1b-113">Bağımlılıkları yükleme</span><span class="sxs-lookup"><span data-stu-id="0db1b-113">Install dependencies</span></span>

1. <span data-ttu-id="0db1b-114">[CUDA v 10.1](https://developer.nvidia.com/cuda-10.1-download-archive-update2)' i yükler.</span><span class="sxs-lookup"><span data-stu-id="0db1b-114">Install [CUDA v10.1](https://developer.nvidia.com/cuda-10.1-download-archive-update2).</span></span> <span data-ttu-id="0db1b-115">Daha yeni bir sürümü değil CUDA v 10.1 ' yi yüklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="0db1b-115">Make sure you install CUDA v10.1, not any other newer version.</span></span> <span data-ttu-id="0db1b-116">CUDA 'nin birden çok sürümü yüklü olamaz.</span><span class="sxs-lookup"><span data-stu-id="0db1b-116">You cannot have multiple versions of CUDA installed.</span></span>
1. <span data-ttu-id="0db1b-117">[CUDA 10,1 Için Cudnn v 7.6.4](https://developer.nvidia.com/rdp/cudnn-download)'yi yükler.</span><span class="sxs-lookup"><span data-stu-id="0db1b-117">Install [cuDNN v7.6.4 for CUDA 10.1](https://developer.nvidia.com/rdp/cudnn-download).</span></span> <span data-ttu-id="0db1b-118">Birden fazla cuDNN sürümü yüklü olamaz.</span><span class="sxs-lookup"><span data-stu-id="0db1b-118">You cannot have multiple versions of cuDNN installed.</span></span> <span data-ttu-id="0db1b-119">CuDNN v 7.6.4 ZIP dosyasını indirdikten ve yeniden paketten çıktıktan sonra `<CUDNN_zip_files_path>\cuda\bin\cudnn64_7.dll` öğesine kopyalayın `<YOUR_DRIVE>\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.1\bin` .</span><span class="sxs-lookup"><span data-stu-id="0db1b-119">After downloading cuDNN v7.6.4 zip file and unpacking it, copy `<CUDNN_zip_files_path>\cuda\bin\cudnn64_7.dll` to `<YOUR_DRIVE>\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.1\bin`.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="0db1b-120">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="0db1b-120">Troubleshooting</span></span>

<span data-ttu-id="0db1b-121">**Nasıl yaparım? hangi GPU 'YU öğrendim?**</span><span class="sxs-lookup"><span data-stu-id="0db1b-121">**How do I know what GPU I have?**</span></span>

<span data-ttu-id="0db1b-122">Belirtilen yönergeleri izleyin:</span><span class="sxs-lookup"><span data-stu-id="0db1b-122">Follow instructions provided:</span></span>

1. <span data-ttu-id="0db1b-123">Masaüstüne sağ tıklayın</span><span class="sxs-lookup"><span data-stu-id="0db1b-123">Right-click on desktop</span></span>
1. <span data-ttu-id="0db1b-124">Açılır pencerede "NVıDıA Denetim Masası" veya "NVıDıA ekran" görürseniz, NVıDıA GPU 'SU vardır</span><span class="sxs-lookup"><span data-stu-id="0db1b-124">If you see "NVIDIA Control Panel" or "NVIDIA Display" in the pop-up window, you have an NVIDIA GPU</span></span>
1. <span data-ttu-id="0db1b-125">Açılır pencerede "NVıDıA Denetim Masası" veya "NVıDıA ekran" seçeneğine tıklayın</span><span class="sxs-lookup"><span data-stu-id="0db1b-125">Click on "NVIDIA Control Panel" or "NVIDIA Display" in the pop-up window</span></span>
1. <span data-ttu-id="0db1b-126">"Grafik kartı bilgileri" bölümüne bakın</span><span class="sxs-lookup"><span data-stu-id="0db1b-126">Look at "Graphics Card Information"</span></span>
1. <span data-ttu-id="0db1b-127">NVıDıA GPU adını görürsünüz</span><span class="sxs-lookup"><span data-stu-id="0db1b-127">You will see the name of your NVIDIA GPU</span></span>

<span data-ttu-id="0db1b-128">**NVıDıA Denetim Masası 'Nı görmüyorum (veya açılamıyor), ancak NVıDıA GPU sahibim var.**</span><span class="sxs-lookup"><span data-stu-id="0db1b-128">**I don't see NVIDIA Control Panel (or it fails to open) but I know I have an NVIDIA GPU.**</span></span>

1. <span data-ttu-id="0db1b-129">Cihaz Yöneticisi’ni açın</span><span class="sxs-lookup"><span data-stu-id="0db1b-129">Open Device Manager</span></span>
1. <span data-ttu-id="0db1b-130">Görüntü bağdaştırıcılarına bakın</span><span class="sxs-lookup"><span data-stu-id="0db1b-130">Look at Display adapters</span></span>
1. <span data-ttu-id="0db1b-131">GPU 'larınız için uygun [sürücüyü](https://www.nvidia.com/drivers) yükleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="0db1b-131">Install appropriate [driver](https://www.nvidia.com/drivers) for your GPU.</span></span>
