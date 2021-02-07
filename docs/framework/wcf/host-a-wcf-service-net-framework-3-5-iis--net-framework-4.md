---
description: "Hakkında daha fazla bilgi edinin: nasıl yapılır: .NET Framework 4 altında çalışan IIS 'de .NET Framework 3,5 ile yazılmış bir WCF hizmetini barındırma"
title: 'Nasıl yapılır: .NET Framework 4 Altında Çalışan IIS .NET Framework 3.5 ile Yazılmış Bir WCF Hizmetini Barındırma'
ms.date: 03/30/2017
ms.assetid: 9aabc785-068d-4d32-8841-3ef39308d8d6
ms.openlocfilehash: 3ea46b589df293b39369521a133cf9facad97d93
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755973"
---
# <a name="how-to-host-a-wcf-service-written-with-net-framework-35-in-iis-running-under-net-framework-4"></a>Nasıl yapılır: .NET Framework 4 Altında Çalışan IIS .NET Framework 3.5 ile Yazılmış Bir WCF Hizmetini Barındırma

.NET Framework 4 çalıştıran bir makinede .NET Framework 3,5 ile yazılmış bir Windows Communication Foundation (WCF) hizmetini barındırırken <xref:System.ServiceModel.ProtocolException> aşağıdaki metinle karşılaşabilirsiniz.
  
```output  
Unhandled Exception: System.ServiceModel.ProtocolException: The content type text/html; charset=utf-8 of the response message does not match the content type of the binding (application/soap+xml; charset=utf-8). If using a custom encoder, be sure that the IsContentTypeSupported method is implemented properly. The first 1024 bytes of the response were: '<html>    <head>        <title>The application domain or application pool is currently running version 4.0 or later of the .NET Framework. This can occur if IIS settings have been set to 4.0 or later for this Web application, or if you are using version 4.0 or later of the ASP.NET Web Development Server. The <compilation> element in the Web.config file for this Web application does not contain the required 'targetFrameworkMoniker' attribute for this version of the .NET Framework (for example, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">'). Update the Web.config file with this attribute, or configure the Web application to use a different version of the .NET Framework.</title>...  
```  
  
 Ya da hizmetin. svc dosyasına gözatmaya çalışırsanız, aşağıdaki metinle bir hata sayfası görebilirsiniz.  
  
```output  
The application domain or application pool is currently running version 4.0 or later of the .NET Framework. This can occur if IIS settings have been set to 4.0 or later for this Web application, or if you are using version 4.0 or later of the ASP.NET Web Development Server. The <compilation> element in the Web.config file for this Web application does not contain the required 'targetFrameworkMoniker' attribute for this version of the .NET Framework (for example, '<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">'). Update the Web.config file with this attribute, or configure the Web application to use a different version of the .NET Framework.  
```  
  
 Bu hatalar, IIS 'nin içinde çalıştığı uygulama etki alanı .NET Framework 4 ' ün çalıştığı ve WCF hizmetinin .NET Framework 3,5 altında çalıştırılmasını beklediği için oluşur. Bu konuda hizmeti çalıştırmak için gereken değişiklikler açıklanmaktadır.
  
 Ardından <`compilers`> öğesini bulun ve CompilerVersion sağlayıcısı seçeneğini 4,0 değerine sahip olacak şekilde değiştirin. Varsayılan olarak, `compiler` <> öğesi altında iki <> öğesi vardır `compilers` . Aşağıdaki örnekte gösterildiği gibi, CompilerVersion sağlayıcı seçeneğini her ikisi için de güncelleştirmeniz gerekir.  
  
```xml  
<system.codedom>  
      <compilers>  
        <compiler language="c#;cs;csharp" extension=".cs" warningLevel="4"  
                  type="Microsoft.CSharp.CSharpCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
          <providerOption name="CompilerVersion" value="v3.5"/>  
          <providerOption name="WarnAsError" value="false"/>  
        </compiler>  
        <compiler language="vb;vbs;visualbasic;vbscript" extension=".vb" warningLevel="4"  
                  type="Microsoft.VisualBasic.VBCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
          <providerOption name="CompilerVersion" value="v3.5"/>  
          <providerOption name="OptionInfer" value="true"/>  
          <providerOption name="WarnAsError" value="false"/>  
        </compiler>  
      </compilers>  
    </system.codedom>  
```  
  
### <a name="add-the-required-targetframework-attribute"></a>Gerekli targetFramework özniteliğini ekleyin  
  
1. Hizmetin Web.config dosyasını açın ve <`compilation`> öğesini arayın.  
  
2. `targetFramework` `compilation` Aşağıdaki örnekte gösterildiği gibi özniteliği <> öğesine ekleyin.  
  
    ```xml  
    <compilation debug="false"  
            targetFramework="4.0">  
  
            <assemblies>  
              <add assembly="System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
              <add assembly="System.Xml.Linq, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
              <add assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31BF3856AD364E35"/>  
              <add assembly="System.Data.DataSetExtensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
            </assemblies>  
  
          </compilation>  
    ```  
  
3. <`compilers`> öğesini bulun ve CompilerVersion sağlayıcısı seçeneğini 4,0 değerine sahip olacak şekilde değiştirin. Varsayılan olarak, `compiler` <> öğesi altında iki <> öğesi vardır `compilers` . Aşağıdaki örnekte gösterildiği gibi, CompilerVersion sağlayıcı seçeneğini her ikisi için de güncelleştirmeniz gerekir.  
  
    ```xml  
    <system.codedom>  
          <compilers>  
            <compiler language="c#;cs;csharp" extension=".cs" warningLevel="4"  
                      type="Microsoft.CSharp.CSharpCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
              <providerOption name="CompilerVersion" value="v3.5"/>  
              <providerOption name="WarnAsError" value="false"/>  
            </compiler>  
            <compiler language="vb;vbs;visualbasic;vbscript" extension=".vb" warningLevel="4"  
                      type="Microsoft.VisualBasic.VBCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
              <providerOption name="CompilerVersion" value="v3.5"/>  
              <providerOption name="OptionInfer" value="true"/>  
              <providerOption name="WarnAsError" value="false"/>  
            </compiler>  
          </compilers>  
        </system.codedom>  
    ```
