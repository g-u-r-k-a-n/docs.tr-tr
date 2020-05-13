---
title: Derlemeler ve yan yana yürütme
description: Aynı bilgisayarda bir uygulamanın veya bileşenin birden çok sürümünü depolamanıza ve çalıştırabilme özelliği olan yan yana yürütme hakkında bilgi edinin.
ms.date: 08/20/2019
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
ms.openlocfilehash: 74b5710c7e8ad60873fb83a3699ce3992ead6e07
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378637"
---
# <a name="assemblies-and-side-by-side-execution"></a><span data-ttu-id="657c9-103">Derlemeler ve yan yana yürütme</span><span class="sxs-lookup"><span data-stu-id="657c9-103">Assemblies and side-by-side execution</span></span>

<span data-ttu-id="657c9-104">Yan yana yürütme, aynı bilgisayarda bir uygulama veya bileşenin birden çok sürümünü saklama ve yürütme olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="657c9-104">Side-by-side execution is the ability to store and execute multiple versions of an application or component on the same computer.</span></span> <span data-ttu-id="657c9-105">Bu da ortak dil çalışma zamanı sürümünün birden çok sürümünün ve çalışma zamanının bir sürümünü kullanan uygulama ve bileşenlerin birden çok sürümünün bir bilgisayar üzerinde aynı anda bulunabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="657c9-105">This means that you can have multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, on the same computer at the same time.</span></span> <span data-ttu-id="657c9-106">Yan yana yürütme olanağı, bir uygulamanın bir bileşenin hangi sürümüne bağlanacağını ve bir uygulamanın hangi çalışma zamanını kullanacağı konusunda daha fazla denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="657c9-106">Side-by-side execution gives you more control over what versions of a component an application binds to, and more control over what version of the runtime an application uses.</span></span>  
  
<span data-ttu-id="657c9-107">Aynı derlemenin farklı sürümlerinin yan yana depolanması ve yürütülmesi için sunulan destek, tanımlayıcı adlandırmanın temel bir parçasıdır ve çalışma zamanının altyapısında yerleşik olarak bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="657c9-107">Support for side-by-side storage and execution of different versions of the same assembly is an integral part of strong naming and is built into the infrastructure of the runtime.</span></span> <span data-ttu-id="657c9-108">Tanımlayıcı ada sahip olan derlemenin sürüm numarası kimliğinin bir parçası olduğundan, çalışma zamanı aynı derlemenin birden çok sürümünü genel derleme önbelleğinde tutabilir ve çalışma zamanında bu derlemeleri yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="657c9-108">Because the strong-named assembly's version number is part of its identity, the runtime can store multiple versions of the same assembly in the global assembly cache and load those assemblies at run time.</span></span>  
  
<span data-ttu-id="657c9-109">Çalışma zamanı size yan yana uygulamalar oluşturma olanağı sağlasa da yan yana yürütme otomatik değildir.</span><span class="sxs-lookup"><span data-stu-id="657c9-109">Although the runtime provides you with the ability to create side-by-side applications, side-by-side execution is not automatic.</span></span> <span data-ttu-id="657c9-110">Yan yana yürütmeye yönelik uygulamalar oluşturma hakkında daha fazla bilgi için bkz. [yan yana yürütme için bileşen oluşturmaya yönelik yönergeler](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span><span class="sxs-lookup"><span data-stu-id="657c9-110">For more information on creating applications for side-by-side execution, see [Guidelines for creating components for side-by-side execution](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="657c9-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="657c9-111">See also</span></span>

- [<span data-ttu-id="657c9-112">Çalışma zamanının derlemeleri nasıl konumlandırır</span><span class="sxs-lookup"><span data-stu-id="657c9-112">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="657c9-113">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="657c9-113">Assemblies in .NET</span></span>](index.md)
