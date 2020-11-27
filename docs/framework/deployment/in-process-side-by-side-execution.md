---
title: Devam Eden Yan Yana Yürütme
description: Tek bir .NET işleminde ortak dil çalışma zamanının (CLR) birçok sürümünü yürütmek için işlem içi yan yana barındırma kullanın.
ms.date: 03/30/2017
helpviewer_keywords:
- in-process side-by-side execution
- side-by-side execution, in-process
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
ms.openlocfilehash: 85d0ec90a8877384517e9de3b56258d294e0c612
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283490"
---
# <a name="in-process-side-by-side-execution"></a>Devam Eden Yan Yana Yürütme

.NET Framework 4 ' te başlayarak, tek bir işlemde ortak dil çalışma zamanının (CLR) birden çok sürümünü çalıştırmak için işlem içi yan yana barındırma kullanabilirsiniz. Varsayılan olarak, yönetilen COM bileşenleri, işlem için yüklenen .NET Framework sürümden bağımsız olarak, ile derlendikleri .NET Framework sürümüyle çalışır.  
  
## <a name="background"></a>Arka plan  

 .NET Framework, yönetilen kod uygulamaları için her zaman yan yana barındırma sağlamıştır, ancak .NET Framework 4 ' den önce, yönetilen COM bileşenleri için bu işlevselliği sağlamadı. Geçmişte, bir işleme yüklenmiş olan yönetilen COM bileşenleri, zaten yüklü olan çalışma zamanının sürümüyle veya .NET Framework en son yüklü sürümüyle çalışır. Bu sürüm COM bileşeniyle uyumlu değilse, bileşen başarısız olur.  
  
 .NET Framework 4, aşağıdakileri sağlayan yan yana barındırma için yeni bir yaklaşım sağlar:  
  
- .NET Framework yeni bir sürümünün yüklenmesi, mevcut uygulamalar üzerinde hiçbir etkiye sahip değildir.  
  
- Uygulamalar, ile derlendikleri .NET Framework sürümüne karşı çalışır. Açıkça yönlendirilmediği takdirde .NET Framework yeni sürümünü kullanmaz. Ancak, uygulamaların .NET Framework yeni bir sürümünü kullanarak geçiş yapması kolaylaşır.  
  
## <a name="effects-on-users-and-developers"></a>Kullanıcılar ve geliştiriciler üzerindeki etkiler  
  
- **Son kullanıcılar ve sistem yöneticileri**. Bu kullanıcılar artık bağımsız çalışma zamanının yeni bir sürümünü (bağımsız olarak ya da bir uygulamayla) yüklediklerinde, bilgisayarlarının üzerinde hiçbir etkisi olmayacaktır. Mevcut uygulamalar, daha önce olduğu gibi çalışmaya devam edecektir.  
  
- **Uygulama geliştiricileri**. Yan yana barındırma, uygulama geliştiricileri üzerinde neredeyse hiçbir etkiye sahip değildir. Uygulamalar, varsayılan olarak her zaman üzerinde derlendikleri .NET Framework sürümüne karşı çalışır; Bu değiştirilmedi. Ancak, geliştiriciler bu davranışı geçersiz kılabilir ve uygulamayı .NET Framework daha yeni bir sürümü altında çalışacak şekilde yönlendirebilir (bkz. [Senaryo 2](#scenarios)).  
  
- **Kitaplık geliştiricileri ve tüketicileri**. Yan yana barındırma, kitaplık geliştiricilerinin karşılaştığı uyumluluk sorunlarını çözmez. Doğrudan başvuru aracılığıyla veya bir çağrı aracılığıyla bir uygulama tarafından doğrudan yüklenen bir kitaplık, ' ın ' a <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yüklendiği çalışma zamanını kullanmaya devam eder <xref:System.AppDomain> . Kitaplıklarınızı, desteklemek istediğiniz tüm .NET Framework sürümlerine karşı test etmelisiniz. Bir uygulama .NET Framework 4 çalışma zamanı kullanılarak derlenirse ancak önceki bir çalışma zamanı kullanılarak oluşturulmuş bir kitaplığı içeriyorsa, bu kitaplık .NET Framework 4 çalışma zamanını da kullanacaktır. Ancak, önceki bir çalışma zamanı ve .NET Framework 4 kullanılarak oluşturulmuş bir kitaplık kullanılarak oluşturulmuş bir uygulamanız varsa, uygulamanızı .NET Framework 4 ' ü (bkz. [Senaryo 3](#scenarios)) de kullanacak şekilde zorlamanız gerekir.  
  
- **YÖNETILEN com bileşeni geliştiricileri**. Geçmişte, yönetilen COM bileşenleri, bilgisayarda yüklü olan çalışma zamanının en son sürümü kullanılarak otomatik olarak çalışır. Artık, yerleşik oldukları çalışma zamanının sürümüne göre COM bileşenlerini yürütebilirsiniz.  
  
     Aşağıdaki tabloda gösterildiği gibi, 1,1 sürümü .NET Framework ile oluşturulmuş bileşenler sürüm 4 bileşenleriyle yan yana çalıştırılabilir, ancak yan yana barındırma bu sürümler için kullanılabilir olmadığından, sürüm 2,0, 3,0 veya 3,5 bileşenleriyle birlikte çalıştırılamaz.  
  
    |.NET Framework sürümü|1.1|2,0-3,5|4|  
    |----------------------------|---------|----------------|-------|  
    |1.1|Uygulanamaz|Hayır|Evet|  
    |2,0-3,5|Hayır|Geçerli değil|Evet|  
    |4|Evet|Evet|Geçerli değil|  
  
> [!NOTE]
> 3,0 ve 3,5 .NET Framework sürümleri artımlı olarak sürüm 2,0 ' de oluşturulmuştur ve yan yana çalıştırılmasına gerek kalmaz. Bunlar, doğal olarak aynı sürümdür.  
  
<a name="scenarios"></a>

## <a name="common-side-by-side-hosting-scenarios"></a>Ortak yan yana barındırma senaryoları  
  
- **Senaryo 1:** .NET Framework önceki sürümleriyle oluşturulmuş COM bileşenlerini kullanan yerel uygulama.  
  
     .NET Framework yüklü sürümler: COM bileşenleri tarafından kullanılan .NET Framework .NET Framework 4 ve diğer tüm sürümleri.  
  
     Yapılacaklar: Bu senaryoda hiçbir şey yapmayın. COM bileşenleri, kayıtlı oldukları .NET Framework sürümüyle çalışacaktır.  
  
- **Senaryo 2**: .NET Framework 2,0 SP1 ile oluşturulmuş, .NET Framework 2,0 ile çalıştırmayı tercih ettiğiniz, ancak sürüm 2,0 mevcut değilse .NET Framework 4 ' te çalıştırmayı tercih ettiğiniz yönetilen uygulama.  
  
     .NET Framework yüklü sürümler: .NET Framework ve .NET Framework 4 ' ün önceki bir sürümü.  
  
     Yapılacaklar: uygulama dizinindeki [uygulama yapılandırma dosyasında](../configure-apps/index.md) , [ \<startup> öğesini](../configure-apps/file-schema/startup/startup-element.md) ve [ \<supportedRuntime> öğesini](../configure-apps/file-schema/startup/supportedruntime-element.md) şu şekilde ayarlayın:  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
- **Senaryo 3:** .NET Framework 4 ile çalıştırmak istediğiniz .NET Framework önceki sürümleriyle oluşturulmuş COM bileşenlerini kullanan yerel uygulama.  
  
     .NET Framework yüklü sürümler: .NET Framework 4.  
  
     Yapılacaklar: uygulama dizinindeki uygulama yapılandırma dosyasında, `<startup>` `useLegacyV2RuntimeActivationPolicy` özniteliği olarak ayarlanmış `true` ve `<supportedRuntime>` öğe kümesi aşağıdaki şekilde olan öğesini kullanın:  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, yönetilen bir COM bileşeni çalıştıran yönetilmeyen bir COM konağını bileşenin kullanmak üzere derlenen .NET Framework sürümünü kullanarak gösterir.  
  
 Aşağıdaki örneği çalıştırmak için .NET Framework 3,5 kullanarak aşağıdaki yönetilen COM bileşenini derleyin ve kaydedin. Bileşeni kaydetmek için, **Proje** menüsünde **Özellikler**' e tıklayın, **derleme** sekmesine tıklayın ve ardından **com birlikte çalışması için kaydol** onay kutusunu seçin.  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Runtime.InteropServices;  
  
namespace BasicComObject  
{  
    [ComVisible(true), Guid("9C99C4B5-CA54-4c58-8988-49B6811BA53B")]  
    public class MyObject : SimpleObjectModel.IPrintInfo  
    {  
        public MyObject()  
        {  
        }  
        public void PrintInfo()  
        {  
            Console.WriteLine("MyObject was activated in {0} runtime in:\n\tAppDomain {1}:{2}", System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion(), AppDomain.CurrentDomain.Id, AppDomain.CurrentDomain.FriendlyName);  
        }  
    }  
}  
```  
  
 Aşağıdaki yönetilmeyen C++ uygulamasını derleyin ve bu, önceki örnek tarafından oluşturulan COM nesnesini etkinleştirir.  
  
```cpp
#include "stdafx.h"  
#include <string>  
#include <iostream>  
#include <objbase.h>  
#include <string.h>  
#include <process.h>  
  
using namespace std;  
  
int _tmain(int argc, _TCHAR* argv[])  
{  
    char input;  
    CoInitialize(NULL) ;  
    CLSID clsid;  
    HRESULT hr;  
    HRESULT clsidhr = CLSIDFromString(L"{9C99C4B5-CA54-4c58-8988-49B6811BA53B}",&clsid);  
    hr = -1;  
    if (FAILED(clsidhr))  
    {  
        printf("Failed to construct CLSID from String\n");  
    }  
    UUID id = __uuidof(IUnknown);  
    IUnknown * pUnk = NULL;  
    hr = ::CoCreateInstance(clsid,NULL,CLSCTX_INPROC_SERVER,id,(void **) &pUnk);  
    if (FAILED(hr))  
    {  
        printf("Failed CoCreateInstance\n");  
    }else  
    {  
        pUnk->AddRef();  
        printf("Succeeded\n");  
    }  
  
    DISPID dispid;  
    IDispatch* pPrintInfo;  
    pUnk->QueryInterface(IID_IDispatch, (void**)&pPrintInfo);  
    OLECHAR FAR* szMethod[1];  
    szMethod[0]=OLESTR("PrintInfo");
    hr = pPrintInfo->GetIDsOfNames(IID_NULL,szMethod, 1, LOCALE_SYSTEM_DEFAULT, &dispid);  
    DISPPARAMS dispparams;  
    dispparams.cNamedArgs = 0;  
    dispparams.cArgs = 0;  
    VARIANTARG* pvarg = NULL;  
    EXCEPINFO * pexcepinfo = NULL;  
    WORD wFlags = DISPATCH_METHOD ;  
;  
    LPVARIANT pvRet = NULL;  
    UINT * pnArgErr = NULL;  
    hr = pPrintInfo->Invoke(dispid,IID_NULL, LOCALE_USER_DEFAULT, wFlags,  
        &dispparams, pvRet, pexcepinfo, pnArgErr);  
    printf("Press Enter to exit");  
    scanf_s("%c",&input);  
    CoUninitialize();  
    return 0;  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<startup> Dosyalarında](../configure-apps/file-schema/startup/startup-element.md)
- [\<supportedRuntime> Dosyalarında](../configure-apps/file-schema/startup/supportedruntime-element.md)
