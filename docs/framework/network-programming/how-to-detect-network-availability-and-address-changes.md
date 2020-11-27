---
title: 'Nasıl yapılır: Ağ Kullanılabilirliğini Algılama ve Adres Değişiklikleri'
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: d4377115-4a76-4848-ab23-4898d65c771c
ms.openlocfilehash: 8f5eef7b6ba41f1ac4050fbc9168fafea31b103f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287325"
---
# <a name="how-to-detect-network-availability-and-address-changes"></a><span data-ttu-id="8514e-102">Nasıl yapılır: Ağ Kullanılabilirliğini Algılama ve Adres Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="8514e-102">How to: Detect Network Availability and Address Changes</span></span>

<span data-ttu-id="8514e-103">Bu örnek, bir arabirimin ağ adresindeki değişikliklerin nasıl algılanacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="8514e-103">This sample shows how to detect changes in the network address of an interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8514e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8514e-104">Example</span></span>  
  
```csharp
using System;  
using System.Net;  
using System.Net.NetworkInformation;  
  
namespace Examples.Net.AddressChanges  
{  
    public class NetworkingExample  
    {  
        public static void Main()  
        {  
            NetworkChange.NetworkAddressChanged += new
             NetworkAddressChangedEventHandler(AddressChangedCallback);  
            Console.WriteLine("Listening for address changes. Press any key to exit.");  
            Console.ReadLine();  
        }  
        static void AddressChangedCallback(object sender, EventArgs e)  
        {  
  
            NetworkInterface[] adapters = NetworkInterface.GetAllNetworkInterfaces();  
            foreach(NetworkInterface n in adapters)  
            {  
                Console.WriteLine("   {0} is {1}", n.Name, n.OperationalStatus);  
            }  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8514e-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="8514e-105">Compiling the Code</span></span>  

 <span data-ttu-id="8514e-106">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="8514e-106">This example requires:</span></span>  
  
- <span data-ttu-id="8514e-107">**System.net** ad alanına başvurular.</span><span class="sxs-lookup"><span data-stu-id="8514e-107">References to the **System.Net** namespace.</span></span>
