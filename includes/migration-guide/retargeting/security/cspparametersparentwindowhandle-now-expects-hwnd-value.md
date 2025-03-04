---
ms.openlocfilehash: 12ba3bd3c9e9e00b88cab0e568a1ce0f4f8bbb05
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606800"
---
### <a name="cspparametersparentwindowhandle-now-expects-hwnd-value"></a>CspParameters. ParentWindowHandle artık HWND değerini bekliyor

#### <a name="details"></a>Ayrıntılar

<xref:System.Security.Cryptography.CspParameters.ParentWindowHandle>.NET Framework 2,0 ' de tanıtılan değer, bir uygulamanın, anahtara erişmek için gerekli olan herhangi bir kullanıcı arabirimi (örneğin, BIR PIN istemi veya onay iletişim kutusu) belirtilen pencerede kalıcı bir alt öğe olarak açılmasıyla bir üst pencere tanıtıcı değerini kaydetmesini sağlar. .NET Framework 4,7 ' i hedefleyen uygulamalarla başlayarak, Windows Forms bir uygulama <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> özelliği aşağıdaki gibi kodla ayarlayabilir:

```csharp
cspParameters.ParentWindowHandle = form.Handle;
```

.NET Framework önceki sürümlerinde, değerin <xref:System.IntPtr?displayProperty=fullName> [HWND](/windows/desktop/WinProg/windows-data-types#HWND) değerinin bulunduğu bellekteki bir konumu temsil eden bir konum olması bekleniyordu. Özelliği form olarak ayarlanıyor. Windows 7 ve önceki sürümlerde tanıtıcı hiçbir etkiye sahip değildir, ancak Windows 8 ve sonraki sürümlerde, bir ile sonuçlanır &quot; <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> : parametre yanlış.&quot;

#### <a name="suggestion"></a>Öneri

Ana pencere ilişkisini kaydetmek için .NET Framework 4,7 veya üzeri hedefleme uygulamalarının Basitleştirilmiş formu kullanması önerilir:

```csharp
cspParameters.ParentWindowHandle = form.Handle;
```

Doğru değerin geçirilecek olduğunu belirledik kullanıcılar, `form.Handle` AppContext anahtarını şu şekilde ayarlayarak, değeri tutulan bir bellek konumunun adresidir `Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle` `true` :

- [Burada](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46)açıklandığı gibi, AppContext üzerinde uyumluluk anahtarlarını programlı olarak ayarlayarak.
- `<runtime>`app.config dosyanın bölümüne aşağıdaki satırı ekleyerek:

```xml
<runtime>
 <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true"/>
</runtime>
```

Buna karşılık, uygulama daha eski .NET Framework sürümler altında yüklenirken .NET Framework 4,7 çalışma zamanının yeni davranışını kabul etmek isteyen kullanıcılar AppContext anahtarını olarak ayarlayabilir `false` .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4,7         |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle?displayProperty=nameWithType>
