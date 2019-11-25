---
title: 'Nasıl yapılır: Maksimum Saat Eğriltme Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MaxClockSkew property
- WCF, custom bindings
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
ms.openlocfilehash: 96afa61d32e1ba744c9f3dbbeeb7fb2e55157f4c
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141650"
---
# <a name="how-to-set-a-max-clock-skew"></a><span data-ttu-id="fa3cc-102">Nasıl yapılır: Maksimum Saat Eğriltme Ayarlama</span><span class="sxs-lookup"><span data-stu-id="fa3cc-102">How to: Set a Max Clock Skew</span></span>
<span data-ttu-id="fa3cc-103">İki bilgisayardaki saat ayarları farklıysa, zaman açısından kritik işlevler derlenebilir.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-103">Time-critical functions can be derailed if the clock settings on two computers are different.</span></span> <span data-ttu-id="fa3cc-104">Bu olasılığa karşı azaltmak için `MaxClockSkew` özelliğini bir <xref:System.TimeSpan>olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-104">To mitigate this possibility, you can set the `MaxClockSkew` property to a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="fa3cc-105">Bu özellik iki sınıfta kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="fa3cc-105">This property is available on two classes:</span></span>  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
> <span data-ttu-id="fa3cc-106">Güvenli konuşma için, hizmet veya istemci önyüklendi olduğunda `MaxClockSkew` özelliğindeki değişiklikler yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-106">For a secure conversation, changes to the `MaxClockSkew` property  must be made when the service or client is bootstrapped.</span></span> <span data-ttu-id="fa3cc-107">Bunu yapmak için, <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> özelliği tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement> özelliğini ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-107">To do this, you must set the property on the <xref:System.ServiceModel.Channels.SecurityBindingElement> returned by the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="fa3cc-108">Sistem tarafından belirtilen bağlamalardan birindeki özelliği değiştirmek için, bağlama koleksiyonunda güvenlik bağlama öğesini bulmanız ve `MaxClockSkew` özelliğini yeni bir değere ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-108">To change the property on one of the system-provided bindings, you must find the security binding element in the collection of bindings and set the `MaxClockSkew` property to a new value.</span></span> <span data-ttu-id="fa3cc-109">İki sınıf <xref:System.ServiceModel.Channels.SecurityBindingElement>türetilir: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ve <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-109">Two classes derive from the <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="fa3cc-110">Koleksiyondan güvenlik bağlamasını alırken, `MaxClockSkew` özelliğini doğru bir şekilde ayarlamak için bu türlerden birine dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-110">When retrieving the security binding from the collection, you must cast to one of these types in order to correctly set the `MaxClockSkew` property.</span></span> <span data-ttu-id="fa3cc-111">Aşağıdaki örnek, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>kullanan bir <xref:System.ServiceModel.WSHttpBinding>kullanır.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-111">The following example uses a <xref:System.ServiceModel.WSHttpBinding>, which uses the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="fa3cc-112">Sistem tarafından belirtilen her bağlamada kullanılacak güvenlik bağlamasının türünü belirten bir liste için, bkz. [sistem tarafından sunulan bağlamalar](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="fa3cc-112">For a list that specifies which type of security binding to use in each system-provided binding, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
## <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a><span data-ttu-id="fa3cc-113">Kodda yeni saat eğriltme değeri ile özel bir bağlama oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fa3cc-113">To create a custom binding with a new clock skew value in code</span></span>  
  
> [!WARNING]
> <span data-ttu-id="fa3cc-114">Kodunuzda aşağıdaki ad alanlarına başvurular ekleyin: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>ve <xref:System.ServiceModel.Security.Tokens>.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-114">Add references to the following namespaces in your code: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, and <xref:System.ServiceModel.Security.Tokens>.</span></span>  
  
1. <span data-ttu-id="fa3cc-115"><xref:System.ServiceModel.WSHttpBinding> sınıfının bir örneğini oluşturun ve güvenlik modunu <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-115">Create an instance of a <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>.</span></span>  
  
2. <span data-ttu-id="fa3cc-116"><xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> metodunu çağırarak <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfının yeni bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-116">Create a new instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class by calling the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3. <span data-ttu-id="fa3cc-117">Güvenlik bağlama öğesini bulmak için <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfının <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-117">Use the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method of the <xref:System.ServiceModel.Channels.BindingElementCollection> class to find the security binding element.</span></span>  
  
4. <span data-ttu-id="fa3cc-118"><xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> yöntemi kullanılırken gerçek türe atayın.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-118">When using the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method, cast to the actual type.</span></span> <span data-ttu-id="fa3cc-119">Aşağıdaki örnek <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> türüne yayınlar.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-119">The example below casts to the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> type.</span></span>  
  
5. <span data-ttu-id="fa3cc-120">Güvenlik bağlama öğesindeki <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-120">Set the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> property on the security binding element.</span></span>  
  
6. <span data-ttu-id="fa3cc-121">Uygun hizmet türü ve temel adresi olan bir <xref:System.ServiceModel.ServiceHost> oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-121">Create a <xref:System.ServiceModel.ServiceHost> with an appropriate service type and base address.</span></span>  
  
7. <span data-ttu-id="fa3cc-122">Uç nokta eklemek ve <xref:System.ServiceModel.Channels.CustomBinding>eklemek için <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-122">Use the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method to add an endpoint and include the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
## <a name="to-set-the-maxclockskew-in-configuration"></a><span data-ttu-id="fa3cc-123">Yapılandırmada MaxClockSkew ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="fa3cc-123">To set the MaxClockSkew in configuration</span></span>  
  
1. <span data-ttu-id="fa3cc-124">[\<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesi bölümünde bir [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-124">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) in the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element section.</span></span>  
  
2. <span data-ttu-id="fa3cc-125">[\<bağlama >](../../configure-apps/file-schema/wcf/bindings.md) öğesi oluşturun ve `name` özniteliğini uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-125">Create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="fa3cc-126">Aşağıdaki örnek, `MaxClockSkewBinding`olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-126">The following example sets it to `MaxClockSkewBinding`.</span></span>  
  
3. <span data-ttu-id="fa3cc-127">Bir Encoding öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-127">Add an encoding element.</span></span> <span data-ttu-id="fa3cc-128">Aşağıdaki örnek bir [\<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)ekler.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-128">The example below adds a [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
4. <span data-ttu-id="fa3cc-129">\<bir [güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi ekleyin ve `authenticationMode` özniteliğini uygun bir ayar olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-129">Add a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element and set the `authenticationMode` attribute to an appropriate setting.</span></span> <span data-ttu-id="fa3cc-130">Aşağıdaki örnek, hizmetin Windows kimlik doğrulamasını kullanmasını belirtmek için özniteliğini `Kerberos` olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-130">The following example set the attribute to `Kerberos` to specify that the service use Windows authentication.</span></span>  
  
5. <span data-ttu-id="fa3cc-131">[\<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) ekleyin ve `maxClockSkew` özniteliğini `"##:##:##"`biçimindeki bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-131">Add a [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to a value in the form of `"##:##:##"`.</span></span> <span data-ttu-id="fa3cc-132">Aşağıdaki örnek, 7 dakika olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-132">The following example sets it to 7 minutes.</span></span> <span data-ttu-id="fa3cc-133">İsteğe bağlı olarak, bir [\<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) ekleyin ve `maxClockSkew` özniteliğini uygun bir ayar olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-133">Optionally, add a [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to an appropriate setting.</span></span>  
  
6. <span data-ttu-id="fa3cc-134">Bir Transport öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-134">Add a transport element.</span></span> <span data-ttu-id="fa3cc-135">Aşağıdaki örnek bir [\<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)kullanır.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-135">The following example uses an [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
7. <span data-ttu-id="fa3cc-136">Güvenli bir konuşma için, güvenlik ayarları [\<Securekonuşmayı tionbootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) öğesinde önyükleme sırasında gerçekleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-136">For a secure conversation, the security settings must occur at the bootstrap in the [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element.</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="MaxClockSkewBinding">  
            <textMessageEncoding />  
            <security authenticationMode="Kerberos">  
               <localClientSettings maxClockSkew="00:07:00" />  
               <localServiceSettings maxClockSkew="00:07:00" />  
               <secureConversationBootstrap>  
                  <localClientSettings maxClockSkew="00:30:00" />  
                  <localServiceSettings maxClockSkew="00:30:00" />  
               </secureConversationBootstrap>  
            </security>  
            <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fa3cc-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa3cc-137">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="fa3cc-138">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fa3cc-138">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
