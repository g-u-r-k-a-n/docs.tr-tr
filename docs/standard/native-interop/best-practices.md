---
title: Yerel birlikte çalışabilirlik en iyi uygulamaları-.NET
description: .NET 'teki yerel bileşenlerle arabirimlendirme için en iyi uygulamaları öğrenin.
ms.date: 01/18/2019
ms.openlocfilehash: e5d96471e796dca712d25d2d9e2609508180d83f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391227"
---
# <a name="native-interoperability-best-practices"></a>Yerel birlikte çalışabilirlik en iyi uygulamaları

.NET, yerel birlikte çalışabilirlik kodunuzu özelleştirmek için kullanabileceğiniz çeşitli yollar sunar. Bu makale, Microsoft 'un .NET ekiplerinin yerel birlikte çalışabilirlik için izlediği yönergeleri içerir.

## <a name="general-guidance"></a>Genel kılavuz

Bu bölümdeki kılavuz tüm birlikte çalışma senaryoları için geçerlidir.

- ✔️, yöntemlerinizi ve parametreleriniz için, çağırmak istediğiniz yerel yöntem olarak aynı adlandırma ve büyük harfleri kullanır.
- ✔️ sabit değerler için aynı adlandırma ve büyük harfleri kullanmayı düşünün.
- ✔️, yerel türe en yakın eşleme olan .NET türlerini kullanır. Örneğin, C# ' de, yerel `uint` tür olduğunda kullanın `unsigned int`.
- ✔️ yalnızca, istediğiniz `[In]` davranış `[Out]` varsayılan davranıştan farklı olduğunda ve özniteliklerini kullanır.
- ✔️, yerel <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> dizi arabelleklerinizi havuza almak IÇIN kullanmayı düşünün.
- ✔️, P/Invoke bildirimlerinizi yerel kitaplığınız ile aynı ada ve büyük harfe sahip bir sınıfta sarmalamanızı düşünün.
  - Bu, özniteliklerinizin `[DllImport]` yerel kitaplığın adını geçirmek `nameof` için C# dil özelliğini kullanmasını sağlar ve yerel kitaplığın adını yanlış yazmadığınızdan emin olun.

## <a name="dllimport-attribute-settings"></a>DllImport öznitelik ayarları

| Ayar | Varsayılan | Öneri | Ayrıntılar |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  Varsayılanı tut  | Bu açık olarak yanlış olarak ayarlandığında, başarısız HRESULT dönüş değerleri özel durumlara açılır (ve tanımdaki dönüş değeri sonuç olarak null olur).|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | API 'ye bağlıdır  | API GetLastError kullanıyorsa bunu true olarak ayarlayın ve değeri almak için Marshal. GetLastWin32Error kullanın. API bir hata olduğunu bildiren bir koşul ayarlarsa, yanlışlıkla üzerine yazılmasını önlemek için başka çağrılar yapmadan önce hatayı alın.|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | `CharSet.None`, `CharSet.Ansi` davranışa geri döner  | Tanımda `CharSet.Unicode` dizeler `CharSet.Ansi` veya karakterler varsa, açıkça kullanın | Bu, dizelerin sıralama davranışını ve ne zaman `ExactSpelling` `false`yapılacağını belirtir. `CharSet.Ansi` Bunun aslında UNIX üzerinde UTF8 olduğunu unutmayın. _Çoğu_ zaman Windows Unicode kullanır, ancak UNIX UTF8 kullanır. [Değiştirmeye belgeleri](./charset.md)hakkında daha fazla bilgi için bkz.. |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | Bunu true olarak ayarlayın ve çalışma zamanı, `CharSet` ayarın değerine bağlı olarak bir "a" veya "w" sonekiyle (Için `CharSet.Ansi` `CharSet.Unicode`"a" ve "w") farklı işlev adlarını araymaz. |

## <a name="string-parameters"></a>Dize parametreleri

Karakter kümesi Unicode olduğunda veya bağımsız değişken açıkça `[MarshalAs(UnmanagedType.LPWSTR)]` olarak işaretlenmişse _ve_ dize değer ile geçirildiğinde (değil `ref` `out`), dize sabitlenir ve doğrudan yerel kod tarafından kullanılır (kopyalanmaktansa).

Dizelerinizin ANSI düzeltmesini `[DllImport]` açıkça `Charset.Unicode` istemediğiniz sürece, işaretini işaretlemeyi unutmayın.

❌Parametreleri kullanmayın `[Out] string` . Değer tarafından `[Out]` özniteliği ile geçirilen dize parametreleri, dize bir dizilmiş dize ise çalışma zamanının kararlılığını bozabilir. İçin <xref:System.String.Intern%2A?displayProperty=nameWithType>belgelerde dize oluşturma hakkında daha fazla bilgi görüntüleyin.

❌Parametrelerden `StringBuilder` kaçının. `StringBuilder`hazırlama *her zaman* yerel bir arabellek kopyası oluşturur. Bu nedenle, son derece verimsiz olabilir. Bir dize alan bir Windows API 'SI çağırmanın tipik senaryosunu gerçekleştirin:

1. İstenen kapasiteyi (yönetilen kapasiteyi ayırır) bir SB oluşturun**{1}**
2. Çağır
   1. Yerel bir arabellek ayırır**{2}**
   2. `[In]` _(Bir `StringBuilder` parametre için varsayılan)_ içeriğini kopyalar
   3. Yerel arabelleği yeni ayrılmış bir yönetilen diziye `[Out]` **{3}** _(Ayrıca için `StringBuilder`varsayılan)_ kopyalar
3. `ToString()`henüz başka bir yönetilen diziyi ayırır**{4}**

Bu, *{4}* yerel koddan bir dizeyi almak için ayırmaların bir dizesidir. Bunu sınırlamak için en iyi yöntem, `StringBuilder` başka bir çağrıda öğesini yeniden kullanmak olacaktır ancak yalnızca *1* ayırmayı kaydeder. ' Den `ArrayPool`bir karakter arabelleğini kullanmak ve önbelleğe almak çok daha iyidir. daha sonra, `ToString()` sonraki çağrılar için yalnızca ayırmaya erişebilirsiniz.

İle ilgili `StringBuilder` diğer sorun, geri dönüş arabelleğini her zaman ilk null değere kopyasın. Geçilen geri dize sonlandırılmazsa veya çift null ile sonlandırılmış bir dize ise, P/Invoke uygulamanız en iyi şekilde yanlış olur.

*Kullanıyorsanız* `StringBuilder`, bir adet son Gotcha, kapasitenin birlikte çalışma içinde her zaman hesaba katılmış bir gizli null değer **içermemelidir** . Çoğu API 'nin, null değeri *de dahil olmak üzere* arabellek boyutunu istediği için bu, insanların bu yanlış alması yaygındır. Bu, harcanan/gereksiz ayırmalara neden olabilir. Ayrıca, bu Gotcha, çalışma zamanının kopyaları en `StringBuilder` aza indirmek için sıralama iyileştirmesine engel olur.

✔️ içinden ' `char[]`i kullanmayı düşünün `ArrayPool`.

Dize sıralaması hakkında daha fazla bilgi için bkz. [dizeler Için varsayılan sıralama](../../framework/interop/default-marshaling-for-strings.md) ve [dize sıralamasını özelleştirme](customize-parameter-marshaling.md#customizing-string-parameters).

> __Windows 'A özgü__ CLR `[Out]` 'nin varsayılan olarak boş dizeler `CoTaskMemFree` veya `SysStringFree` olarak `UnmanagedType.BSTR`işaretlenen dizeler için kullanacağı dizeler.
> **Çıkış dizesi arabelleğine sahip çoğu API için:** Geçirilen karakter sayısı null içermelidir. Döndürülen değer geçilen karakter sayısından küçükse, çağrı başarılı olur ve değer sondaki null *olmayan* karakter sayısıdır. Aksi takdirde, sayı null karakter *dahil olmak üzere* arabelleğin gerekli boyutudur.
>
> - 5 ' te geçiş yapın, 4 ' ü alın: dize sonunda null olan 4 karakter uzunluğundadır.
> - 5 ' te geçiş yapın, 6: dize 5 karakter uzunluğundadır, null tutmak için 6 karakterlik bir arabellek gerekir.
> [Dizeler için Windows veri türleri](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a>Boole parametreleri ve alanları

Boole değerleri daha kolay. Varsayılan olarak, .NET `bool` , 4 baytlık bir değer olan `BOOL`bir Windows için sıralanır. `_Bool`Ancak, ve `bool` C ve C++ içindeki türler *tek* bir bayttır. Bu, dönüş değerinin atıldığı ve yalnızca *büyük olasılıkla* sonucu değiştirecek olan hataları takip etmek zor olabilir. .NET `bool` değerlerini C veya C++ `bool` türlerine hazırlama hakkında daha fazla bilgi için, [Boole alanı sıralamasını özelleştirme](customize-struct-marshaling.md#customizing-boolean-field-marshaling)hakkındaki belgelere bakın.

## <a name="guids"></a>Yapılamıyor

GUID 'Ler doğrudan imzalarda kullanılabilir. Birçok Windows API 'si `GUID&` , gibi `REFIID`tür diğer adlarını alır. Ref tarafından geçirildiğinde, `ref` ya da `[MarshalAs(UnmanagedType.LPStruct)]` özniteliğiyle geçirilebilir.

| GUID | -Başvuru GUID 'SI |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

❌GUID parametrelerinden başka bir şey için kullanmayın `[MarshalAs(UnmanagedType.LPStruct)]` `ref`

## <a name="blittable-types"></a>Blittable türleri

Blittable türleri, yönetilen ve yerel kodda aynı bit düzeyi gösterimine sahip olan türlerdir. Bu şekilde, yerel koda ve yerel koddan sıralanmaları için başka bir biçime dönüştürülmesi gerekmez ve bu da performansı artırdığı için tercih edilmelidir.

**Blittable türleri:**

- `byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`
- blittable türlerin iç içe olmayan tek boyutlu dizileri (örneğin, `int[]`)
- örnek alanlar için yalnızca blittable değer türlerine sahip sabit düzenine sahip yapılar ve sınıflar
  - Sabit düzen için `[StructLayout(LayoutKind.Sequential)]` veya`[StructLayout(LayoutKind.Explicit)]`
  - yapılar varsayılan `LayoutKind.Sequential` olarak, sınıflardır`LayoutKind.Auto`

**Blittable DEĞIL:**

- `bool`

**Bazen blittable:**

- `char`, `string`

Blittable türleri başvuru ile geçirildiğinde, bir ara belleğe kopyalamak yerine yalnızca hazırlayıcısı tarafından sabitlenmiştir. (Sınıflar kendiliğinden başvuruya göre geçirilir, yapılar veya `ref` `out`ile kullanıldığında başvuruya göre geçirilir.)

`char`tek boyutlu bir dizide **veya** ile birlikte `[StructLayout]` açık olarak işaretlenen bir türün parçasıysa blittable `CharSet = CharSet.Unicode`.

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

`string`blittable, başka bir türde yoksa ve ile `[MarshalAs(UnmanagedType.LPWStr)]` `[DllImport]` `CharSet = CharSet.Unicode` işaretlenmiş bir bağımsız değişken olarak geçirilir.

Bir türün blittable olup olmadığını, sabitlenmiş `GCHandle`bir oluşturma girişiminde görebilirsiniz. Tür bir dize değilse veya blittable `GCHandle.Alloc` olarak kabul edilir. `ArgumentException`

✔️ yapılarınızı mümkün olduğunca blittable yapın.

Daha fazla bilgi için bkz.

- [Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler](../../framework/interop/blittable-and-non-blittable-types.md)
- [Tür sıralaması](type-marshaling.md)

## <a name="keeping-managed-objects-alive"></a>Yönetilen nesneleri canlı tutma

`GC.KeepAlive()`bir nesnenin, KeepAlive yöntemi vurana kadar kapsamda kalmasını güvence altına alınır.

[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef)hazırlayıcısı 'in bir P/Invoke süresince bir nesneyi canlı tutmaya izin verir. Yöntemi, yöntem imzaları yerine `IntPtr` kullanılabilir. `SafeHandle`Bu sınıfın yerini etkin bir şekilde değiştirir ve bunun yerine kullanılmalıdır.

[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle)yönetilen bir nesnenin sabitlenmesini ve yerel işaretçisine alınmasını sağlar. Temel model:

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

Sabitleme için `GCHandle`varsayılan değer değildir. Diğer büyük model, yerel kod aracılığıyla yönetilen bir nesneye başvuru geçirmek ve genellikle bir geri çağırma ile yönetilen koda geri dönmek içindir. Bu, şu şekildedir:

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

Bellek sızıntılarını `GCHandle` önlemek için açıkça serbest bırakılmış olması gerektiğini unutmayın.

## <a name="common-windows-data-types"></a>Ortak Windows veri türleri

Aşağıda, Windows API 'Lerinde yaygın olarak kullanılan ve Windows koduna çağrılırken hangi C# türlerinin kullanılacağı veri türlerinin bir listesi verilmiştir.

Aşağıdaki türler, adlarına rağmen 32-bit ve 64-bit Windows üzerinde aynı boyutlardır.

| Genişlik | Windows          | C (Windows)          | C#       | Yapıyı                          |
|:------|:-----------------|:---------------------|:---------|:-------------------------------------|
| 32    | `BOOL`           | `int`                | `int`    | `bool`                               |
| 8     | `BOOLEAN`        | `unsigned char`      | `byte`   | `[MarshalAs(UnmanagedType.U1)] bool` |
| 8     | `BYTE`           | `unsigned char`      | `byte`   |                                      |
| 8     | `CHAR`           | `char`               | `sbyte`  |                                      |
| 8     | `UCHAR`          | `unsigned char`      | `byte`   |                                      |
| 16    | `SHORT`          | `short`              | `short`  |                                      |
| 16    | `CSHORT`         | `short`              | `short`  |                                      |
| 16    | `USHORT`         | `unsigned short`     | `ushort` |                                      |
| 16    | `WORD`           | `unsigned short`     | `ushort` |                                      |
| 16    | `ATOM`           | `unsigned short`     | `ushort` |                                      |
| 32    | `INT`            | `int`                | `int`    |                                      |
| 32    | `LONG`           | `long`               | `int`    |                                      |
| 32    | `ULONG`          | `unsigned long`      | `uint`   |                                      |
| 32    | `DWORD`          | `unsigned long`      | `uint`   |                                      |
| 64    | `QWORD`          | `long long`          | `long`   |                                      |
| 64    | `LARGE_INTEGER`  | `long long`          | `long`   |                                      |
| 64    | `LONGLONG`       | `long long`          | `long`   |                                      |
| 64    | `ULONGLONG`      | `unsigned long long` | `ulong`  |                                      |
| 64    | `ULARGE_INTEGER` | `unsigned long long` | `ulong`  |                                      |
| 32    | `HRESULT`        | `long`               | `int`    |                                      |
| 32    | `NTSTATUS`       | `long`               | `int`    |                                      |

Aşağıdaki türler, işaretçiler olması, platformun genişliğini izler. Bunlar `IntPtr` / `UIntPtr` için kullanın.

| İmzalı Işaretçi türleri (kullanım `IntPtr`) | İşaretsiz Işaretçi türleri (kullanım `UIntPtr`) |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

`PVOID` C `void*` olan bir Windows ya `IntPtr` `UIntPtr`da olarak sıralanabilir, ancak mümkün olduğunda tercih `void*` edilebilir.

[Windows veri türleri](/windows/desktop/WinProg/windows-data-types)

[Veri türü aralıkları](/cpp/cpp/data-type-ranges)

## <a name="structs"></a>Yapılar

Yönetilen yapılar yığında oluşturulur ve Yöntem dönene kadar kaldırılmaz. Daha sonra, tanım olarak "sabitlenmiş" olur (GC tarafından taşınmaz). Ayrıca, yerel kod geçerli yöntemin sonundan sonra işaretçiyi kullanmayacaksa, güvenli olmayan kod bloklarıyla adresi de alabilirsiniz.

Blittable yapılar, doğrudan hazırlama katmanı tarafından yalnızca kullanılabilecek şekilde daha fazla performanızdır. Yapıları blittable yapmayı deneyin (örneğin, kullanmaktan kaçının `bool`). Daha fazla bilgi için [blittable Types](#blittable-types) bölümüne bakın.

Yapı *blittable ise,* daha iyi performans `sizeof()` `Marshal.SizeOf<MyStruct>()` için yerine kullanın. Yukarıda da belirtildiği gibi, sabitlenmiş bir sabitlenmiş `GCHandle`oluşturma girişiminde, türün blittable olduğunu doğrulayabilirsiniz. Tür bir dize değilse veya blittable olarak kabul edilir, `GCHandle.Alloc` bir `ArgumentException`oluşturur.

Tanımlarda yapıların işaretçilerine ya da `ref` `unsafe` ile `*`geçirilmesi gerekir.

✔️, resmi platform belgelerinde veya üstbilgisinde kullanılan şekle ve adlara göre, yönetilen yapı ile mümkün olduğunca yakından eşleşir.

✔️ performansı artırmak için blittable `sizeof()` yapıları yerine `Marshal.SizeOf<MyStruct>()` C# kullanın.

❌Yapılardaki `System.Delegate` işlev `System.MulticastDelegate` işaretçisi alanlarını temsil etmek IÇIN veya alanlarını kullanmaktan kaçının.

<xref:System.Delegate?displayProperty=fullName> Gerekli bir imzaya sahip olmadığından, geçirilen temsilcinin yerel kodun beklediği imzayla eşleşeceğini garanti <xref:System.MulticastDelegate?displayProperty=fullName> etmez. Ayrıca, .NET Framework ve .NET Core ' da, yerel temsilindeki alanın `System.Delegate` değeri `System.MulticastDelegate` yönetilen bir temsilciyi sarmalayan bir işlev işaretçisi değilse, bir veya yerel gösteriminden yönetilen bir nesne içeren bir yapının sıralaması çalışma zamanının kararlılığını bozabilir. .NET 5 ve sonraki sürümlerde, bir `System.Delegate` veya `System.MulticastDelegate` alanını yerel gösterimden yönetilen bir nesneye sıralama desteklenmez. `System.Delegate` Veya `System.MulticastDelegate`yerine belirli bir temsilci türü kullanın.

### <a name="fixed-buffers"></a>Sabit arabellekler

Benzer `INT_PTR Reserved1[2]` bir dizi iki `IntPtr` alan için sıralanmalıdır `Reserved1a` ve. `Reserved1b` Yerel dizi basit bir tür olduğunda, `fixed` anahtar sözcüğünü kullanarak biraz daha düzgün bir şekilde yazabilirsiniz. Örneğin, `SYSTEM_PROCESS_INFORMATION` yerel üst bilgisinde şöyle görünür:

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

C# ' de, bunu şöyle yazalım:

```csharp
internal unsafe struct SYSTEM_PROCESS_INFORMATION
{
    internal uint NextEntryOffset;
    internal uint NumberOfThreads;
    private fixed byte Reserved1[48];
    internal Interop.UNICODE_STRING ImageName;
    ...
}
```

Ancak, sabit arabelleklerle bazı tuzakları vardır. Blittable olmayan türlerin sabit arabellekleri doğru sıralanmayacak, bu nedenle yerinde dizinin birden çok ayrı alana genişletilmesi gerekir. Ayrıca, .NET Framework ve .NET Core 'da 3,0 öncesinde, sabit bir arabellek alanı içeren bir struct, blittable olmayan bir yapı içinde iç içe geçmişse, sabit arabellek alanı yerel koda doğru şekilde sıralanmayacaktır.
