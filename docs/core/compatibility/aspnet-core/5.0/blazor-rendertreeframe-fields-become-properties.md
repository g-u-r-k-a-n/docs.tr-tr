---
title: 'Son değişiklik: Blazor: RenderTreeFrame ReadOnly ortak alanları özellikler haline geldi'
description: "Blazor başlıklı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: RenderTreeFrame ReadOnly ortak alanları özellikler haline geldi"
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c4d70279b4280b079570099b82b056299405508b
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498171"
---
# <a name="blazor-rendertreeframe-readonly-public-fields-have-become-properties"></a>Blazor: RenderTreeFrame ReadOnly ortak alanları özellikler haline geldi

ASP.NET Core 3,0 ve 3,1 ' de, <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame> Yapı, `readonly public` <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.FrameType> ve diğer gibi çeşitli alanları kullanıma sunuldu <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.Sequence> . ASP.NET Core 5,0 RC1 ve sonraki sürümlerinde, tüm `readonly public` alanlar özellikler olarak değiştirilmiştir `readonly public` .

Bu değişiklik birçok geliştirici etkilemez, çünkü:

* `.razor`Bileşenlerini tanımlamak için dosyaları (veya hatta el ile çağrıları) kullanan herhangi bir uygulama veya kitaplık <xref:Microsoft.AspNetCore.Components.Rendering.RenderTreeBuilder> , bu türe doğrudan başvurmaz.
* `RenderTreeFrame`Türün kendisi, Framework dışında kullanılması amaçlanmayan bir uygulama ayrıntısı olarak kabul edilir. ASP.NET Core 3,0 ve üzeri, tür doğrudan kullanılıyorsa Derleyici uyarıları veren bir çözümleyici içerir.
* Doğrudan başvursanız bile `RenderTreeFrame` Bu değişiklik ikili bir değer değildir ancak kaynak bölünmez. Diğer bir deyişle, var olan kaynak kodunuz doğru şekilde derlenir ve davranacaktır. Yalnızca bir .NET Core 3. x çerçevesinde derleme yaptıysanız ve daha sonra bu ikili dosyaları .NET 5,0 RC1 ve sonraki bir çerçeveye karşı çalıştırmak için bir sorunla karşılaşacaksınız.

Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 25727](https://github.com/dotnet/aspnetcore/issues/25727).

## <a name="version-introduced"></a>Sunulan sürüm

5,0 RC1

## <a name="old-behavior"></a>Eski davranış

Ortak Üyeler `RenderTreeFrame` alan olarak tanımlanır. Örneğin `renderTreeFrame.Sequence` ve `renderTreeFrame.ElementName`.

## <a name="new-behavior"></a>Yeni davranış

Ortak Üyeler `RenderTreeFrame` , önceki ile aynı adlara sahip özellikler olarak tanımlanmıştır. Örneğin `renderTreeFrame.Sequence` ve `renderTreeFrame.ElementName`.

Daha önceden derlenmiş kod bu değişiklikten bu yana yeniden derlenmemişse, MissingFieldException şuna benzer bir özel durum oluşturabilir: *alan bulunamadı: ' Microsoft. AspNetCore. components. RenderTree. RenderTreeFrame. FrameType '*.

## <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, ASP.NET Core 5,0 ' de Blazor bileşeni işlemede yüksek etkili performans iyileştirmeleri uygulamak için gereklidir. Aynı güvenlik ve kapsülleme düzeyleri korunur.

## <a name="recommended-action"></a>Önerilen eylem

Çoğu Blazor geliştiricisi bu değişiklikten etkilenmez. Bu değişiklik, kitaplığı ve paket yazarlarını yalnızca nadir bir durumda etkilemekle daha olasıdır. Geliştirmekte olduğunuz özel olarak:

* Bir uygulama ve ASP.NET Core 3. x veya 5,0 RC1 veya sonraki bir sürüme yükseltme yapmak için kendi kodunuzu değiştirmeniz gerekmez. Ancak, bu değişiklik için hesaba yükseltilen bir kitaplığa bağlı değilseniz, bu kitaplığın daha yeni bir sürümüne güncelleştirmeniz gerekir.
* Bir kitaplık ve yalnızca ASP.NET Core 5,0 RC1 veya üstünü desteklemek istiyorsanız, herhangi bir eylem gerekmez. Yalnızca proje dosyanızın bir `<TargetFramework>` değeri `net5.0` veya daha sonraki bir sürümü bildirdiğinden emin olun.
* Bir kitaplık ve ASP.NET Core 3. x *ve* 5,0 ' i desteklemek istiyorsanız, kodunuzun herhangi bir üyeyi okuyup okumadığını saptayın `RenderTreeFrame` . Örneğin, değerlendirme `someRenderTreeFrame.FrameType` .
  * Çoğu kitaplık `RenderTreeFrame` , bileşenleri içeren kitaplıklar da dahil olmak üzere, üyeleri okummaz `.razor` . Bu durumda, hiçbir eylem gerekmez.
  * Ancak, kitaplığınız bunu destekliyorsa, hem hem de desteklemek için birden çok hedef gerekir `netstandard2.1` `net5.0` . Proje dosyanıza aşağıdaki değişiklikleri uygulayın:
    * Var olan `<TargetFramework>` öğeyi ile değiştirin `<TargetFrameworks>netstandard2.0;net5.0</TargetFrameworks>` .
    * `Microsoft.AspNetCore.Components`Desteklemek istediğiniz her iki sürümü de hesaba eklemek için koşullu paket başvurusu kullanın. Örnek:

        ```xml
        <PackageReference Include="Microsoft.AspNetCore.Components" Version="3.0.0" Condition="'$(TargetFramework)' == 'netstandard2.0'" />
        <PackageReference Include="Microsoft.AspNetCore.Components" Version="5.0.0-rc.1.*" Condition="'$(TargetFramework)' != 'netstandard2.0'" />
        ```

Daha fazla açıklama için, [ @jsakamoto `Toolbelt.Blazor.HeadElement` kitaplığın zaten nasıl yükseltildiğini gösteren bu fark](https://github.com/jsakamoto/Toolbelt.Blazor.HeadElement/commit/090df430ba725f9420d412753db8104e8c32bf51)bölümüne bakın.

## <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame`

-->
