---
title: TextMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
ms.openlocfilehash: 551761af255681dd2c2dbb9e40b7103c95cd2e0a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267227"
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="2dabd-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="2dabd-102">TextMessageEncodingBindingElement</span></span>

<span data-ttu-id="2dabd-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="2dabd-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dabd-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="2dabd-104">Syntax</span></span>  
  
```csharp
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2dabd-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2dabd-105">Methods</span></span>  

 <span data-ttu-id="2dabd-106">TextMessageEncodingBindingElement sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="2dabd-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2dabd-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2dabd-107">Properties</span></span>  

 <span data-ttu-id="2dabd-108">TextMessageEncodingBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="2dabd-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="2dabd-109">Encoding</span><span class="sxs-lookup"><span data-stu-id="2dabd-109">Encoding</span></span>  

 <span data-ttu-id="2dabd-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="2dabd-110">Data type: string</span></span>  
  
 <span data-ttu-id="2dabd-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="2dabd-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2dabd-112">Bağlamadaki iletileri yayma için kullanılacak karakter kümesi kodlaması.</span><span class="sxs-lookup"><span data-stu-id="2dabd-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="2dabd-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="2dabd-113">MaxReadPoolSize</span></span>  

 <span data-ttu-id="2dabd-114">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="2dabd-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="2dabd-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="2dabd-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2dabd-116">Yeni okuyucular ayırmadan aynı anda okunabilecek ileti sayısını tanımlayan bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="2dabd-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="2dabd-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="2dabd-117">MaxWritePoolSize</span></span>  

 <span data-ttu-id="2dabd-118">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="2dabd-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="2dabd-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="2dabd-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2dabd-120">Yeni yazıcı ayırmadan aynı anda gönderilebilecek ileti sayısını tanımlayan bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="2dabd-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="2dabd-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="2dabd-121">ReaderQuotas</span></span>  

 <span data-ttu-id="2dabd-122">Veri türü: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="2dabd-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="2dabd-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="2dabd-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2dabd-124">Okuyucuların kotaları.</span><span class="sxs-lookup"><span data-stu-id="2dabd-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2dabd-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2dabd-125">Requirements</span></span>  
  
|<span data-ttu-id="2dabd-126">MOF</span><span class="sxs-lookup"><span data-stu-id="2dabd-126">MOF</span></span>|<span data-ttu-id="2dabd-127">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2dabd-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2dabd-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="2dabd-128">Namespace</span></span>|<span data-ttu-id="2dabd-129">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="2dabd-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2dabd-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2dabd-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
