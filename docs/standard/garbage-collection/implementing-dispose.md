---
title: Dispose metodu uygulama
description: Bu makalede, .NET 'teki kodunuzun kullandığı yönetilmeyen kaynakları serbest bırakarak Dispose yöntemini uygulamayı öğrenin.
ms.date: 04/07/2021
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- garbage collection, Dispose method
ms.assetid: eb4e1af0-3b48-4fbc-ad4e-fc2f64138bf9
ms.openlocfilehash: f14c4979024209fb7e5e6364f0627f4e796799c5
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2021
ms.locfileid: "107260533"
---
# <a name="implement-a-dispose-method"></a>Dispose metodu uygulama

Yöntemi uygulamak, <xref:System.IDisposable.Dispose%2A> öncelikle yönetilmeyen kaynakların serbest bırakılması içindir. Uygulamalar olan örnek üyeleriyle çalışırken <xref:System.IDisposable> , basamaklı <xref:System.IDisposable.Dispose%2A> çağrılar yaygındır. <xref:System.IDisposable.Dispose%2A>Örneğin, ayrılan belleği serbest bırakma, koleksiyona eklenen bir öğeyi kaldırma veya alınan bir kilidin serbest bırakılması sinyali gibi nedenlerle başka nedenler de vardır.

[.Net atık toplayıcısı](index.md) , yönetilmeyen bellek ayırır veya serbest bırakmaz. Dispose düzeni olarak adlandırılan bir nesneyi elden atma düzeni, bir nesnenin kullanım ömrüne göre sıra uygular. Dispose deseninin, arabirimi uygulayan nesneler için kullanılır <xref:System.IDisposable> ve dosya ve kanal tutamaçları, kayıt defteri tutamaçları, bekleme tutamaçları veya yönetilmeyen bellek bloklarına yönelik işaretçilerle etkileşim kurarken yaygındır. Bunun nedeni, çöp toplayıcının yönetilmeyen nesneleri geri kazanmamadır.

Kaynakların her zaman uygun şekilde temizlendiğinden emin olmak için bir <xref:System.IDisposable.Dispose%2A> Yöntem, özel durum oluşturmadan birden çok kez çağrılabilir şekilde ıdempotent olmalıdır. Ayrıca, sonraki çağırmaları <xref:System.IDisposable.Dispose%2A> hiçbir şey yapmaz.

Yöntemi için belirtilen kod örneği, <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> çöp toplamanın bir sonlandırıcının çalışmasına nasıl neden olabileceği, nesneye veya üyelerine yönetilmeyen bir başvuru hala kullanımda olduğunda gösterir. <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType>Nesneyi, geçerli yordamın başından bu yöntemin çağrıldığı noktaya kadar çöp toplama için uygun hale getirmek için kullanılması anlamlı olabilir.

[!INCLUDE [disposables-and-dependency-injection](includes/disposables-and-dependency-injection.md)]

## <a name="safe-handles"></a>Güvenli işleyiciler

Bir nesnenin sonlandırıcısı için kod yazmak, doğru yapılmaması durumunda sorunlara neden olabilecek karmaşık bir görevdir. Bu nedenle, <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> bir Sonlandırıcı uygulamak yerine nesneleri oluşturmanızı öneririz.

<xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>, Yönetilmeyen bir kaynağı tanımlayan bir soyut yönetilen türdür <xref:System.IntPtr?displayProperty=nameWithType> . Windows üzerinde, bir dosya tanımlayıcısı olan UNIX üzerinde bir tanıtıcıyı tanımlayabilir. Bu kaynağın bir kez ve yalnızca bir kez serbest bırakıldığını sağlamak için gereken tüm mantığı sağlar. Bu, ' nin ve ' a `SafeHandle` yapılan tüm başvurular `SafeHandle` atıldıktan sonra ve `SafeHandle` örnek sonlandırıldığında.

, <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> Soyut bir temel sınıftır. Türetilmiş sınıflar, farklı tanıtıcı türleri için belirli örnekler sağlar. Bu türetilmiş sınıflar, için hangi değerlerin <xref:System.IntPtr?displayProperty=nameWithType> geçersiz kabul edildiği ve tanıtıcıyı gerçekten serbest bırakma işlemlerinin nasıl yapıldığını doğrular. Örneğin, <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> `SafeHandle` `IntPtrs` Açık dosya tutamaçlarını/tanımlayıcılarını tanımlayan sarmadan türeyebilir ve <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle?displayProperty=nameWithType> bunu kapatmak için yöntemini geçersiz kılar ( `close` UNIX veya `CloseHandle` Windows üzerinde işlev aracılığıyla). Yönetilmeyen bir kaynağı oluşturan .NET kitaplıklarında API 'Lerin çoğu, bunu bir içinde saracaktır `SafeHandle` ve `SafeHandle` ham işaretçiyi geri almak yerine size gerektiğinde döndürür. Yönetilmeyen bir bileşenle etkileşim kuran ve yönetilmeyen bir kaynak için kullanabileceğiniz durumlarda `IntPtr` , `SafeHandle` onu kaydırmak için kendi türünü de oluşturabilirsiniz. Sonuç olarak, `SafeHandle` bazı tür olmayan işlem sonlandırıcıları uygulamanız gerekir; çoğu atılabilir model uygulaması yalnızca diğer yönetilen kaynakların sarmalanması, bazıları bazı ' `SafeHandle` lar olabilir.

Ad alanındaki aşağıdaki türetilmiş sınıflar, <xref:Microsoft.Win32.SafeHandles> güvenli işleyiciler sağlar:

- <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>, <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle> , Ve <xref:Microsoft.Win32.SafeHandles.SafePipeHandle> sınıfı, dosyalar, bellek eşlemeli dosyalar ve kanallar için.
- <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle>Bellek görünümleri için sınıfı.
- <xref:Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle> <xref:Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle> <xref:Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle> Şifreleme yapıları için, ve sınıfları.
- <xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle>Kayıt defteri anahtarları için sınıfı.
- <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle>Wait tutamaçları için sınıfı.

## <a name="dispose-and-disposebool"></a>Dispose () ve Dispose (bool)

<xref:System.IDisposable>Arabirim, tek parametresiz bir yöntemin uygulanmasını gerektirir <xref:System.IDisposable.Dispose%2A> . Ayrıca, korumalı olmayan herhangi bir sınıfın uygulanması için ek bir `Dispose(bool)` aşırı yükleme yöntemi olmalıdır:

- `public`Parametresi olmayan, sanal olmayan ( `NonInheritable` Visual Basic) bir <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulama.

- `protected virtual`İmzası şu olan bir ( `Overridable` Visual Basic) `Dispose` yöntemi:

  [!code-csharp[Conceptual.Disposable#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#8)]
  [!code-vb[Conceptual.Disposable#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#8)]

  > [!IMPORTANT]
  > `disposing`Parametresi `false` bir Sonlandırıcı 'dan çağrıldığında ve `true` yönteminden çağrıldığında olmalıdır <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> . Diğer bir deyişle, `true` belirleyici olmayan ve belirleyici olmayan bir şekilde `false` çağrılmayan bir değer.

### <a name="the-dispose-method"></a>Dispose () yöntemi

`public`, Sanal olmayan ( `NonInheritable` Visual Basic), parametresiz `Dispose` Yöntem türünün bir tüketicisi tarafından çağrıldığından, amacı yönetilmeyen kaynakları serbest bırakmak, genel temizlik gerçekleştirmek ve bir Sonlandırıcı varsa sonlandırıcının çalışması gerektiğini belirtmek için. Yönetilen bir nesneyle ilişkili gerçek bellek boşaltılırken her zaman [çöp toplayıcının](index.md)etki alanıdır. Bu nedenle, standart bir uygulaması vardır:

[!code-csharp[Conceptual.Disposable#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#7)]
[!code-vb[Conceptual.Disposable#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#7)]

`Dispose`Yöntemi tüm nesne temizleme işlemini gerçekleştirir, bu nedenle çöp toplayıcının artık nesnelerin <xref:System.Object.Finalize%2A?displayProperty=nameWithType> geçersiz kılmasını çağırması gerekmez. Bu nedenle, yöntemine yapılan çağrı <xref:System.GC.SuppressFinalize%2A> çöp toplayıcısının sonlandırıcıyı çalıştırmasını önler. Türün Sonlandırıcı yoksa, çağrısının <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> hiçbir etkisi olmaz. Gerçek temizleme işleminin yöntem aşırı yüklemesi tarafından gerçekleştirildiğini unutmayın `Dispose(bool)` .

### <a name="the-disposebool-method-overload"></a>Dispose (bool) yöntemi aşırı yüklemesi

Aşırı yüklemede `disposing` parametresi, <xref:System.Boolean> yöntem çağrısının bir <xref:System.IDisposable.Dispose%2A> yöntemden (değer `true` ) mi yoksa sonlandırıcının mi (değer) geldiğini belirten bir ' dir `false` .

Yöntemin gövdesi iki kod bloğundan oluşur:

- Yönetilmeyen kaynakları serbest bırakan bir blok. Bu blok, parametrenin değerinden bağımsız olarak yürütülür `disposing` .
- Yönetilen kaynakları serbest bırakan koşullu bir blok. Değeri ise bu blok yürütülür `disposing` `true` . Serbest bıraktığı yönetilen kaynaklar şunları içerebilir:

  - **Uygulayan yönetilen nesneler <xref:System.IDisposable> .** Koşullu blok, uygulamasını çağırmak için kullanılabilir <xref:System.IDisposable.Dispose%2A> (Cascade Dispose). Yönetilmeyen kaynağınızı kaydırmak için türetilmiş bir sınıf kullandıysanız <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> , <xref:System.Runtime.InteropServices.SafeHandle.Dispose?displayProperty=nameWithType> uygulamayı buradan çağırmanız gerekir.

  - **Büyük miktarlarda bellek kullanan veya nadir kaynaklarını tüketen yönetilen nesneler.** ' A büyük yönetilen nesne başvuruları atayarak, `null` ulaşılamaz olma olasılığı yüksektir. Bu, bunları belirleyici olmayan şekilde geri kazanıladıklarından daha hızlı bir şekilde yayınlar ve bu genellikle koşullu bloğun dışında yapılır.

Yöntem çağrısı bir sonlandırıcının geliyorsa, yalnızca yönetilmeyen kaynakları serbest bırakma kodu yürütmelidir. Uygulayıcısı, yanlış yolun, geri kazanılabileceğini yönetilen nesnelerle etkileşimde olmamasını sağlamaktan sorumludur. Bu önemlidir çünkü çöp toplayıcının sonlandırma sırasında yönetilen nesneleri yok sayılamayan sıra belirleyici değildir.

## <a name="cascade-dispose-calls"></a>Basamaklı atma çağrıları

Sınıfınız bir alan veya özelliğe sahipse ve türü uygularsa <xref:System.IDisposable> , kapsayan sınıfın kendisi de uygulamalıdır <xref:System.IDisposable> . Bir uygulamayı örnekleyen <xref:System.IDisposable> ve örnek üye olarak depolayan bir sınıf, temizlemeden de sorumludur. Bu, başvurulan atılabilir türlerine, yöntemi aracılığıyla temizlemeyi kesin bir şekilde gerçekleştirmeyi sağlayan fırsat verilmesini sağlamaya yardımcı olur <xref:System.IDisposable.Dispose%2A> . Bu örnekte, sınıfı `sealed` (veya `NotInheritable` Visual Basic).

[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/disposable1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/disposable1.vb#1)]

## <a name="implement-the-dispose-pattern"></a>Dispose modelini uygulama

Korumalı olmayan tüm sınıflar veya (Visual Basic sınıfları olarak değiştirilmez `NotInheritable` ), devralınabileceğinden, olası bir temel sınıf olarak düşünülmelidir. Herhangi bir olası temel sınıf için Dispose modelini uygularsanız, aşağıdakileri sağlamalısınız:

- <xref:System.IDisposable.Dispose%2A>Yöntemini çağıran bir uygulama `Dispose(bool)` .
- `Dispose(bool)`Gerçek temizleme işlemini gerçekleştiren bir yöntem.
- Öğesinden türetilen bir sınıf <xref:System.Runtime.InteropServices.SafeHandle> , Yönetilmeyen kaynağınızı sarmalanmış (önerilir) veya yöntemine bir geçersiz kılma <xref:System.Object.Finalize%2A?displayProperty=nameWithType> . <xref:System.Runtime.InteropServices.SafeHandle>Sınıfı bir Sonlandırıcı sağlar, bu nedenle kendiniz yazmak zorunda değilsiniz.

> [!IMPORTANT]
> Temel sınıfın yalnızca yönetilen nesnelere başvurması ve Dispose deseninin uygulanması mümkündür. Bu durumlarda, sonlandırıcısı gereksizdir. Sonlandırıcı yalnızca yönetilmeyen kaynaklara doğrudan başvurdıysanız gereklidir.

Aşağıda, güvenli tanıtıcı kullanan bir temel sınıf için Dispose deseninin uygulanması için genel bir model verilmiştir.

[!code-csharp[System.IDisposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base1.cs#3)]
[!code-vb[System.IDisposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base1.vb#3)]

> [!NOTE]
> Önceki örnek, bir <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> nesneyi göstermek için bir nesnesi kullanır; bunun yerine ondan türetilmiş herhangi bir nesne <xref:System.Runtime.InteropServices.SafeHandle> kullanılabilir. Örneğin nesnesinin düzgün şekilde örneklemez olduğunu unutmayın <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> .

Geçersiz kılan bir temel sınıf için Dispose deseninin uygulanması için genel bir model <xref:System.Object.Finalize%2A?displayProperty=nameWithType> .

[!code-csharp[System.IDisposable#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base2.cs#5)]
[!code-vb[System.IDisposable#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base2.vb#5)]

> [!TIP]
> C# dilinde, geçersiz kılarak bir [Sonlandırıcı](../../csharp/programming-guide/classes-and-structs/destructors.md) oluşturursunuz <xref:System.Object.Finalize%2A?displayProperty=nameWithType> . Visual Basic, ile yapılır `Protected Overrides Sub Finalize()` .

## <a name="implement-the-dispose-pattern-for-a-derived-class"></a>Türetilmiş bir sınıf için Dispose modelini uygulama

<xref:System.IDisposable> <xref:System.IDisposable> Temel sınıf uygulaması <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> türetilmiş sınıfları tarafından devralındığından, arabirimini uygulayan bir sınıftan türetilmiş bir sınıf uygulanmamalıdır. Bunun yerine, türetilmiş bir sınıfı temizlemek için şunları sağlarsınız:

- `protected override void Dispose(bool)`Temel sınıf yöntemini geçersiz kılan ve türetilmiş sınıfın gerçek temizleme işlemini gerçekleştiren bir yöntem. Bu yöntem ayrıca `base.Dispose(bool)` `MyBase.Dispose(bool)` temel sınıfın (Visual Basic) metodunu çağırmalıdır ve bağımsız değişkeni için disposing durumunu iletmelidir.
- Öğesinden türetilen bir sınıf <xref:System.Runtime.InteropServices.SafeHandle> , Yönetilmeyen kaynağınızı sarmalanmış (önerilir) veya yöntemine bir geçersiz kılma <xref:System.Object.Finalize%2A?displayProperty=nameWithType> . <xref:System.Runtime.InteropServices.SafeHandle>Sınıfı, sizi kod içine almak zorunda kalmanızı sağlayan bir Sonlandırıcı sağlar. Bir Sonlandırıcı sağlarsanız, `Dispose(bool)` bir bağımsız değişkeniyle aşırı yüklemeyi çağırmalıdır `disposing` `false` .

Güvenli tanıtıcı kullanan bir türetilen sınıf için dispose deseni uygulamada genel düzen aşağıdaki gibidir:

[!code-csharp[System.IDisposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived1.cs#4)]
[!code-vb[System.IDisposable#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived1.vb#4)]

> [!NOTE]
> Önceki örnek, bir <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> nesneyi göstermek için bir nesnesi kullanır; bunun yerine ondan türetilmiş herhangi bir nesne <xref:System.Runtime.InteropServices.SafeHandle> kullanılabilir. Örneğin nesnesinin düzgün şekilde örneklemez olduğunu unutmayın <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> .

Geçersiz kılan türetilmiş bir sınıf için Dispose deseninin uygulanması için genel bir model aşağıda verilmiştir <xref:System.Object.Finalize%2A?displayProperty=nameWithType> :

[!code-csharp[System.IDisposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived2.cs#6)]
[!code-vb[System.IDisposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived2.vb#6)]

## <a name="implement-the-dispose-pattern-with-safe-handles"></a>Güvenli tanıtıcılarla Dispose modelini uygulama

Aşağıdaki örnek, `DisposableStreamResource` yönetilmeyen kaynakları kapsüllemek için güvenli bir tanıtıcı kullanan bir temel sınıf için Dispose modelini göstermektedir. `DisposableStreamResource` <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> Açık bir dosyayı temsil eden bir nesneyi kaydırmak için öğesini kullanan bir sınıfı tanımlar <xref:System.IO.Stream> . Sınıfı ayrıca `Size` , dosya akışındaki toplam bayt sayısını döndüren tek bir özelliğini de içerir.

[!code-csharp[Conceptual.Disposable#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/base1.cs#9)]
[!code-vb[Conceptual.Disposable#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/base1.vb#9)]

## <a name="implement-the-dispose-pattern-for-a-derived-class-with-safe-handles"></a>Güvenli tanıtıcılarla türetilmiş bir sınıf için Dispose modelini uygulama

Aşağıdaki örnek, `DisposableStreamResource2` `DisposableStreamResource` Önceki örnekte sunulan sınıftan devralan türetilmiş bir sınıf için Dispose modelini göstermektedir. Sınıfı ek bir yöntemi ekler, `WriteFileInfo` ve <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> yazılabilir dosyanın tanıtıcısını kaydırmak için bir nesnesi kullanır.

[!code-csharp[Conceptual.Disposable#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/derived1.cs#10)]
[!code-vb[Conceptual.Disposable#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/derived1.vb#10)]

## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetlerin elden çıkarılması](../../core/extensions/dependency-injection-guidelines.md#disposal-of-services)
- <xref:System.GC.SuppressFinalize%2A>
- <xref:System.IDisposable>
- <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>
- <xref:Microsoft.Win32.SafeHandles>
- <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>
- [Sınıfları ve yapıları tanımlama ve kullanma (C++/CLı)](/cpp/dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli)
