---
title: Derleme oluşturma
ms.date: 08/19/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
ms.openlocfilehash: 81fffb2b2e1d56d6068bf6f663a13fad6968a383
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740512"
---
# <a name="create-assemblies"></a><span data-ttu-id="c0933-102">Derleme oluşturma</span><span class="sxs-lookup"><span data-stu-id="c0933-102">Create assemblies</span></span>

<span data-ttu-id="c0933-103">Visual Studio gibi bir IDE veya Windows SDK tarafından sunulan derleyiciler ve araçlar aracılığıyla tek dosyalı veya çok dosyalı derlemeler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0933-103">You can create single-file or multifile assemblies using an IDE, such as Visual Studio, or the compilers and tools provided by the Windows SDK.</span></span> <span data-ttu-id="c0933-104">En basit derleme basit bir ada sahip tek bir dosyadır ve tek bir uygulama etki alanına yüklenir.</span><span class="sxs-lookup"><span data-stu-id="c0933-104">The simplest assembly is a single file that has a simple name and is loaded into a single application domain.</span></span> <span data-ttu-id="c0933-105">Bu derlemeye, uygulama dizini dışındaki diğer derlemeler tarafından başvurulamaz ve sürüm denetimi çalışmıyor.</span><span class="sxs-lookup"><span data-stu-id="c0933-105">This assembly cannot be referenced by other assemblies outside the application directory and does not undergo version checking.</span></span> <span data-ttu-id="c0933-106">Derlemeden oluşan uygulamayı kaldırmak için, bulunduğu dizini silmeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="c0933-106">To uninstall the application made up of the assembly, you simply delete the directory where it resides.</span></span> <span data-ttu-id="c0933-107">Birçok geliştirici için, bu özelliklere sahip bir derleme, bir uygulamanın dağıtılması için gerekli olan bir derlemedir.</span><span class="sxs-lookup"><span data-stu-id="c0933-107">For many developers, an assembly with these features is all that is needed to deploy an application.</span></span>

<span data-ttu-id="c0933-108">Çeşitli kod modüllerinden ve kaynak dosyalarından çok dosyalı bir derleme oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0933-108">You can create a multifile assembly from several code modules and resource files.</span></span> <span data-ttu-id="c0933-109">Ayrıca, birden çok uygulama tarafından paylaşılabilen bir derleme da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0933-109">You can also create an assembly that can be shared by multiple applications.</span></span> <span data-ttu-id="c0933-110">Paylaşılan bir derlemenin tanımlayıcı adı olması ve genel derleme önbelleğinde dağıtılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c0933-110">A shared assembly must have a strong name and can be deployed in the global assembly cache.</span></span>

<span data-ttu-id="c0933-111">Aşağıdaki faktörlere bağlı olarak kod modüllerini ve kaynakları derlemeler halinde gruplandırırken çeşitli seçenekleriniz vardır:</span><span class="sxs-lookup"><span data-stu-id="c0933-111">You have several options when grouping code modules and resources into assemblies, depending on the following factors:</span></span>

- <span data-ttu-id="c0933-112">Sürüm Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c0933-112">Versioning</span></span>

     <span data-ttu-id="c0933-113">Aynı sürüm bilgisine sahip olması gereken grup modülleri.</span><span class="sxs-lookup"><span data-stu-id="c0933-113">Group modules that should have the same version information.</span></span>

- <span data-ttu-id="c0933-114">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="c0933-114">Deployment</span></span>

     <span data-ttu-id="c0933-115">Dağıtım modelinizi destekleyen grup kodu modülleri ve kaynakları.</span><span class="sxs-lookup"><span data-stu-id="c0933-115">Group code modules and resources that support your model of deployment.</span></span>

- <span data-ttu-id="c0933-116">Pencereleri</span><span class="sxs-lookup"><span data-stu-id="c0933-116">Reuse</span></span>

     <span data-ttu-id="c0933-117">Bir amaç için mantıksal olarak birlikte kullanılabilen modülleri gruplandırın.</span><span class="sxs-lookup"><span data-stu-id="c0933-117">Group modules if they can be logically used together for some purpose.</span></span> <span data-ttu-id="c0933-118">Örneğin, program bakımı için seyrek kullanılan türler ve sınıflardan oluşan bir derleme aynı derlemeye yerleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c0933-118">For example, an assembly consisting of types and classes used infrequently for program maintenance can be put in the same assembly.</span></span> <span data-ttu-id="c0933-119">Ayrıca, birden çok uygulamayla paylaşmayı planladığınız türler bir derlemede gruplandırılmalıdır ve derleme tanımlayıcı bir adla imzalanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c0933-119">In addition, types that you intend to share with multiple applications should be grouped into an assembly and the assembly should be signed with a strong name.</span></span>

- <span data-ttu-id="c0933-120">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="c0933-120">Security</span></span>

     <span data-ttu-id="c0933-121">Aynı güvenlik izinleri gerektiren türleri içeren modülleri gruplandırın.</span><span class="sxs-lookup"><span data-stu-id="c0933-121">Group modules containing types that require the same security permissions.</span></span>

- <span data-ttu-id="c0933-122">Kapsamlar</span><span class="sxs-lookup"><span data-stu-id="c0933-122">Scoping</span></span>

     <span data-ttu-id="c0933-123">Görünürlüğü aynı derleme ile kısıtlanması gereken türler içeren modülleri gruplandırın.</span><span class="sxs-lookup"><span data-stu-id="c0933-123">Group modules containing types whose visibility should be restricted to the same assembly.</span></span>

<span data-ttu-id="c0933-124">Yönetilmeyen COM uygulamaları için ortak dil çalışma zamanı derlemeleri kullanılabilir hale getirmeyle ilgili özel durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="c0933-124">There are special considerations when making common language runtime assemblies available to unmanaged COM applications.</span></span> <span data-ttu-id="c0933-125">Yönetilmeyen kodla çalışma hakkında daha fazla bilgi için bkz. [BILEŞENLERI com 'da .NET Framework kullanıma](../../framework/interop/exposing-dotnet-components-to-com.md)sunma.</span><span class="sxs-lookup"><span data-stu-id="c0933-125">For more information about working with unmanaged code, see [Expose .NET Framework components to COM](../../framework/interop/exposing-dotnet-components-to-com.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c0933-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0933-126">See also</span></span>

- [<span data-ttu-id="c0933-127">Derleme sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="c0933-127">Assembly versioning</span></span>](versioning.md)
- [<span data-ttu-id="c0933-128">Nasıl yapılır: tek dosya bütünleştirilmiş kodu derleme</span><span class="sxs-lookup"><span data-stu-id="c0933-128">How to: Build a single-file assembly</span></span>](../../framework/app-domains/build-single-file-assembly.md)
- [<span data-ttu-id="c0933-129">Nasıl yapılır: çok dosyalı bütünleştirilmiş kod derleme</span><span class="sxs-lookup"><span data-stu-id="c0933-129">How to: Build a multifile assembly</span></span>](../../framework/app-domains/build-multifile-assembly.md)
- [<span data-ttu-id="c0933-130">Çalışma zamanının derlemeleri nasıl konumlandırır</span><span class="sxs-lookup"><span data-stu-id="c0933-130">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="c0933-131">Çoklu dosya derlemeleri</span><span class="sxs-lookup"><span data-stu-id="c0933-131">Multifile assemblies</span></span>](../../framework/app-domains/multifile-assemblies.md)
