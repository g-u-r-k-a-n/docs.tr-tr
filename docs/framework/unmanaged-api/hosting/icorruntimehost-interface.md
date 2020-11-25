---
title: ICorRuntimeHost Arabirimi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost
helpviewer_keywords:
- ICorRuntimeHost interface [.NET Framework hosting]
ms.assetid: 4369533d-7834-4497-bc37-bfea0ad737b1
topic_type:
- apiref
ms.openlocfilehash: 9fcb5e189af9f72de7635aad550a5e8ab5522dbd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720626"
---
# <a name="icorruntimehost-interface"></a><span data-ttu-id="e364e-102">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e364e-102">ICorRuntimeHost Interface</span></span>

<span data-ttu-id="e364e-103">Ana bilgisayarın ortak dil çalışma zamanını (CLR) açık olarak başlatıp durdurmasına, uygulama etki alanlarını oluşturup yapılandırmasına, varsayılan etki alanına erişime ve işlemde çalışan tüm etki alanlarını listelemeye olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e364e-103">Provides methods that enable the host to start and stop the common language runtime (CLR) explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>  
  
 <span data-ttu-id="e364e-104">.NET Framework sürüm 2,0 ' de, bu arabirimin yerini [ICLRRuntimeHost](iclrruntimehost-interface.md)almıştır.</span><span class="sxs-lookup"><span data-stu-id="e364e-104">In the .NET Framework version 2.0, this interface is superceded by [ICLRRuntimeHost](iclrruntimehost-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e364e-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e364e-105">Methods</span></span>  
  
|<span data-ttu-id="e364e-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e364e-106">Method</span></span>|<span data-ttu-id="e364e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e364e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e364e-108">CloseEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e364e-108">CloseEnum Method</span></span>](icorruntimehost-closeenum-method.md)|<span data-ttu-id="e364e-109">Bir etki alanı numaralandırıcısını etki alanı listesinin başına geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="e364e-109">Resets a domain enumerator back to the beginning of the domain list.</span></span>|  
|[<span data-ttu-id="e364e-110">CreateDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e364e-110">CreateDomain Method</span></span>](icorruntimehost-createdomain-method.md)|<span data-ttu-id="e364e-111">Bir uygulama etki alanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e364e-111">Creates an application domain.</span></span> <span data-ttu-id="e364e-112">Çağıran, türünde bir örneğine türünde bir arabirim işaretçisi alır <xref:System._AppDomain> <xref:System.AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e364e-112">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>|  
|[<span data-ttu-id="e364e-113">CreateDomainEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e364e-113">CreateDomainEx Method</span></span>](icorruntimehost-createdomainex-method.md)|<span data-ttu-id="e364e-114">Bir uygulama etki alanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e364e-114">Creates an application domain.</span></span> <span data-ttu-id="e364e-115">Bu yöntem, çağıranın döndürülen örneğin ek özelliklerini yapılandırmak için bir IAppDomainSetup örneği geçişine olanak sağlar <xref:System._AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="e364e-115">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>|  
|[<span data-ttu-id="e364e-116">CreateDomainSetup Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e364e-116">CreateDomainSetup Method</span></span>](icorruntimehost-createdomainsetup-method.md)|<span data-ttu-id="e364e-117">Bir örneğe türün arabirim işaretçisini alır `IAppDomainSetup` <xref:System.AppDomainSetup> .</span><span class="sxs-lookup"><span data-stu-id="e364e-117">Gets an interface pointer of type `IAppDomainSetup` to an <xref:System.AppDomainSetup> instance.</span></span> <span data-ttu-id="e364e-118">`IAppDomainSetup` , bir uygulama etki alanının oluşturulmadan önce özelliklerini yapılandırmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e364e-118">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>|  
|[<span data-ttu-id="e364e-119">CreateEvidence Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e364e-119">CreateEvidence Method</span></span>](icorruntimehost-createevidence-method.md)|<span data-ttu-id="e364e-120"><xref:System.Security.Principal.IIdentity>Konağın, [CreateDomain](icorruntimehost-createdomain-method.md) veya [CreateDomainEx](icorruntimehost-createdomainex-method.md)'e geçiş için güvenlik kanıtı oluşturmasına olanak tanıyan bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="e364e-120">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity>, which allows the host to create security evidence to pass to [CreateDomain](icorruntimehost-createdomain-method.md) or [CreateDomainEx](icorruntimehost-createdomainex-method.md).</span></span>|  
|[<span data-ttu-id="e364e-121">CreateLogicalThreadState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e364e-121">CreateLogicalThreadState Method</span></span>](icorruntimehost-createlogicalthreadstate-method.md)|<span data-ttu-id="e364e-122">Kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="e364e-122">Do not use.</span></span>|  
|[<span data-ttu-id="e364e-123">CurrentDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e364e-123">CurrentDomain Method</span></span>](icorruntimehost-currentdomain-method.md)|<span data-ttu-id="e364e-124"><xref:System._AppDomain>Geçerli iş parçacığında yüklü olan etki alanını temsil eden türün bir arabirim işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="e364e-124">Gets an interface pointer of type <xref:System._AppDomain> that represents the domain loaded on the current thread.</span></span>|  
|[<span data-ttu-id="e364e-125">DeleteLogicalThreadState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e364e-125">DeleteLogicalThreadState Method</span></span>](icorruntimehost-deletelogicalthreadstate-method.md)|<span data-ttu-id="e364e-126">Kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="e364e-126">Do not use.</span></span>|  
|[<span data-ttu-id="e364e-127">EnumDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e364e-127">EnumDomains Method</span></span>](icorruntimehost-enumdomains-method.md)|<span data-ttu-id="e364e-128">Geçerli işlemdeki etki alanları için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="e364e-128">Gets an enumerator for the domains in the current process.</span></span>|  
|[<span data-ttu-id="e364e-129">GetConfiguration yöntemi</span><span class="sxs-lookup"><span data-stu-id="e364e-129">GetConfiguration Method</span></span>](icorruntimehost-getconfiguration-method.md)|<span data-ttu-id="e364e-130">Konağın CLR 'nin geri çağırma yapılandırmasını belirtmesini sağlayan bir nesne alır.</span><span class="sxs-lookup"><span data-stu-id="e364e-130">Gets an object that allows the host to specify the callback configuration of the CLR.</span></span>|  
|[<span data-ttu-id="e364e-131">GetDefaultDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e364e-131">GetDefaultDomain Method</span></span>](icorruntimehost-getdefaultdomain-method.md)|<span data-ttu-id="e364e-132"><xref:System._AppDomain>Geçerli işlem için varsayılan etki alanını temsil eden türün bir arabirim işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="e364e-132">Gets an interface pointer of type <xref:System._AppDomain> that represents the default domain for the current process.</span></span>|  
|[<span data-ttu-id="e364e-133">LocksHeldByLogicalThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e364e-133">LocksHeldByLogicalThread Method</span></span>](icorruntimehost-locksheldbylogicalthread-method.md)|<span data-ttu-id="e364e-134">Kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="e364e-134">Do not use.</span></span>|  
|[<span data-ttu-id="e364e-135">MapFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e364e-135">MapFile Method</span></span>](icorruntimehost-mapfile-method.md)|<span data-ttu-id="e364e-136">Belirtilen dosyayı belleğe eşler.</span><span class="sxs-lookup"><span data-stu-id="e364e-136">Maps the specified file into memory.</span></span> <span data-ttu-id="e364e-137">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="e364e-137">This method is obsolete.</span></span>|  
|[<span data-ttu-id="e364e-138">NextDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e364e-138">NextDomain Method</span></span>](icorruntimehost-nextdomain-method.md)|<span data-ttu-id="e364e-139">Numaralandırmadaki bir sonraki etki alanına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="e364e-139">Gets an interface pointer to the next domain in the enumeration.</span></span>|  
|[<span data-ttu-id="e364e-140">Start yöntemi</span><span class="sxs-lookup"><span data-stu-id="e364e-140">Start Method</span></span>](icorruntimehost-start-method.md)|<span data-ttu-id="e364e-141">CLR 'yi başlatır.</span><span class="sxs-lookup"><span data-stu-id="e364e-141">Starts the CLR.</span></span>|  
|[<span data-ttu-id="e364e-142">Stop yöntemi</span><span class="sxs-lookup"><span data-stu-id="e364e-142">Stop Method</span></span>](icorruntimehost-stop-method.md)|<span data-ttu-id="e364e-143">Geçerli işlem için çalışma zamanındaki kodun yürütülmesini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="e364e-143">Stops the execution of code in the runtime for the current process.</span></span>|  
|[<span data-ttu-id="e364e-144">SwitchInLogicalThreadState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e364e-144">SwitchInLogicalThreadState Method</span></span>](icorruntimehost-switchinlogicalthreadstate-method.md)|<span data-ttu-id="e364e-145">Kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="e364e-145">Do not use.</span></span>|  
|[<span data-ttu-id="e364e-146">SwitchOutLogicalThreadState Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e364e-146">SwitchOutLogicalThreadState Method</span></span>](icorruntimehost-switchoutlogicalthreadstate-method.md)|<span data-ttu-id="e364e-147">Kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="e364e-147">Do not use.</span></span>|  
|[<span data-ttu-id="e364e-148">UnloadDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e364e-148">UnloadDomain Method</span></span>](icorruntimehost-unloaddomain-method.md)|<span data-ttu-id="e364e-149">Belirtilen uygulama etki alanını geçerli işlemden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e364e-149">Unloads the specified application domain from the current process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e364e-150">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e364e-150">Requirements</span></span>  

 <span data-ttu-id="e364e-151">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e364e-151">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e364e-152">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e364e-152">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e364e-153">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="e364e-153">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e364e-154">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="e364e-154">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e364e-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e364e-155">See also</span></span>

- <xref:System.AppDomain>
- [<span data-ttu-id="e364e-156">Hosting</span><span class="sxs-lookup"><span data-stu-id="e364e-156">Hosting</span></span>](index.md)
- [<span data-ttu-id="e364e-157">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e364e-157">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- <span data-ttu-id="e364e-158">[Çalışma zamanı Konakları](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e364e-158">[Runtime Hosts](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span></span>
- [<span data-ttu-id="e364e-159">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e364e-159">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="e364e-160">CorRuntimeHost Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="e364e-160">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
