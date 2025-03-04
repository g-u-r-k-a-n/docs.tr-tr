---
title: Tür sıralama-.NET
description: .NET 'in türlerinizi yerel bir gösterimde nasıl sıraladığında öğrenin.
ms.date: 01/18/2019
ms.openlocfilehash: 7fc3dfe950ecd3ed0ff5e4eb0e101c1596a831e1
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94441004"
---
# <a name="type-marshaling"></a>Tür hazırlama

**Sıralama** , yönetilen ve yerel kod arasında çapraz geçiş olmaları gerektiğinde türleri dönüştürme işlemidir.

Yönetilen ve yönetilmeyen koddaki türler farklı olduğundan sıralama gereklidir. Yönetilen kodda, örneğin, `String` yönetilmeyen Uluslararası dizeler Unicode ("geniş"), Unicode olmayan, null ile sonlandırılmış, ASCII vb. olabilir. Varsayılan olarak, P/Invoke alt sistemi, bu makalede açıklanan varsayılan davranışa göre doğru şeyi gerçekleştirmeye çalışır. Ancak, ek denetime ihtiyacınız olan bu durumlar için, yönetilmeyen tarafta beklenen türü ne olduğunu belirtmek üzere [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) özniteliğini kullanabilirsiniz. Örneğin, dizenin null ile sonlandırılmış bir ANSI dizesi olarak gönderilmesini istiyorsanız bunu şöyle yapabilirsiniz:

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

## <a name="default-rules-for-marshaling-common-types"></a>Ortak türleri hazırlama için varsayılan kurallar

Genellikle, çalışma zamanı, sizin için en az iş miktarını gerektirecek şekilde sıralama yaparken "doğru şeyi" gerçekleştirmeye çalışır. Aşağıdaki tablolarda, her türün bir parametre veya alanda kullanıldığında varsayılan olarak nasıl sıralandığına ilişkin bir açıklama verilmiştir. Aşağıdaki tablonun tüm platformlar için doğru olduğundan emin olmak için C99/C++ 11 sabit genişlikli tamsayı ve karakter türleri kullanılır. Aynı hizalama ve Boyut gereksinimlerine sahip herhangi bir yerel türü bu türlerle kullanabilirsiniz.

Bu ilk tabloda, hem P/Invoke hem de alan sıralaması için, sıralama için aynı olan çeşitli türler için eşlemeler açıklanmaktadır.

| .NET türü | Yerel tür  |
|-----------|-------------------------|
| `byte`    | `uint8_t`               |
| `sbyte`   | `int8_t`                |
| `short`   | `int16_t`               |
| `ushort`  | `uint16_t`              |
| `int`     | `int32_t`               |
| `uint`    | `uint32_t`              |
| `long`    | `int64_t`               |
| `ulong`   | `uint64_t`              |
| `char`    | Ya `char` da `char16_t` `CharSet` P/Invoke ya da yapısına bağlı olarak. [Karakter kümesi belgelerine](charset.md)bakın. |
| `string`  | Ya `char*` da `char16_t*` `CharSet` P/Invoke ya da yapısına bağlı olarak. [Karakter kümesi belgelerine](charset.md)bakın. |
| `System.IntPtr` | `intptr_t`        |
| `System.UIntPtr` | `uintptr_t`      |
| .NET Işaretçi türleri (örn. `void*`)  | `void*` |
| Türetilmiş tür `System.Runtime.InteropServices.SafeHandle` | `void*` |
| Türetilmiş tür `System.Runtime.InteropServices.CriticalHandle` | `void*`          |
| `bool`    | Win32 `BOOL` türü       |
| `decimal` | COM `DECIMAL` yapısı |
| .NET temsilcisi | Yerel işlev işaretçisi |
| `System.DateTime` | Win32 `DATE` türü |
| `System.Guid` | Win32 `GUID` türü |

Bir parametre veya yapı olarak sıralama yapıyorsanız, birkaç sıralama kategorisi farklı değerlere sahiptir.

| .NET türü | Yerel tür (parametre) | Yerel tür (alan) |
|-----------|-------------------------|---------------------|
| .NET dizisi | Dizi öğelerinin yerel gösterimlerine ait bir dizi başlangıcına yönelik bir işaretçi. | Özniteliği olmadan izin verilmiyor `[MarshalAs]`|
| Veya içeren bir sınıf `LayoutKind` `Sequential``Explicit` | Sınıfın yerel gösterimine yönelik bir işaretçi | Sınıfın yerel temsili |

Aşağıdaki tablo, yalnızca Windows 'un varsayılan sıralama kurallarını içerir. Windows dışı platformlarda bu türleri sıralayamaz.

| .NET türü | Yerel tür (parametre) | Yerel tür (alan) |
|-----------|-------------------------|---------------------|
| `object`  | `VARIANT`               | `IUnknown*`         |
| `System.Array` | COM arabirimi | Özniteliği olmadan izin verilmiyor `[MarshalAs]` |
| `System.ArgIterator` | `va_list` | İzin verilmiyor |
| `System.Collections.IEnumerator` | `IEnumVARIANT*` | İzin verilmiyor |
| `System.Collections.IEnumerable` | `IDispatch*` | İzin verilmiyor |
| `System.DateTimeOffset` | `int64_t` 1 Ocak 1601 ' de gece yarısından beri geçen onay işareti sayısını temsil etme | `int64_t` 1 Ocak 1601 ' de gece yarısından beri geçen onay işareti sayısını temsil etme |

Bazı türler, alan olarak değil yalnızca parametre olarak sıralanabilir. Bu türler aşağıdaki tabloda listelenmiştir:

| .NET türü | Yerel tür (yalnızca parametre) |
|-----------|------------------------------|
| `System.Text.StringBuilder` | Ya `char*` da `char16_t*` `CharSet` P/Invoke öğesine bağlı olarak.  [Karakter kümesi belgelerine](charset.md)bakın. |
| `System.ArgIterator` | `va_list` (yalnızca Windows x86/x64/arm64 üzerinde) |
| `System.Runtime.InteropServices.ArrayWithOffset` | `void*` |
| `System.Runtime.InteropServices.HandleRef` | `void*` |

Bu varsayılanlar tam olarak istediğiniz şekilde yapamazsa, parametrelerin nasıl sıralanmasını özelleştirebilirsiniz. [Parametre sıralama](customize-parameter-marshaling.md) makalesi, farklı parametre türlerinin nasıl sıralanmasını nasıl özelleştireceğinizi açıklar.

## <a name="default-marshaling-in-com-scenarios"></a>COM senaryolarında varsayılan sıralama

.NET ' te COM nesnelerine Yöntemler çağırırken .NET çalışma zamanı, varsayılan sıralama kurallarını ortak COM semantiklerine uyacak şekilde değiştirir. Aşağıdaki tabloda, .NET çalışma zamanlarının COM senaryolarında kullandığı kurallar listelenmektedir:

| .NET türü | Yerel tür (COM Yöntem çağrıları) |
|-----------|--------------------------------|
| `bool`    | `VARIANT_BOOL`                 |
| `StringBuilder` | `LPWSTR`                 |
| `string`  | `BSTR`                         |
| Temsilci türleri | `_Delegate*` .NET Framework. .NET Core ve .NET 5 + ' da izin verilmez. |
| `System.Drawing.Color` | `OLECOLOR`        |
| .NET dizisi | `SAFEARRAY`                   |
| `string[]` | `SAFEARRAY` / `BSTR` s        |

## <a name="marshaling-classes-and-structs"></a>Sınıfları ve yapıları hazırlama

Bir yapının tür sıralaması, yönetilmeyen bir yönteme nasıl geçmektir. Örneğin, yönetilmeyen yöntemlerin bazıları parametre olarak bir yapı gerektirir. Bu durumlarda, bir parametre olarak kullanmak için, dünyanın yönetilen bölümünde karşılık gelen bir yapı veya bir sınıf oluşturmanız gerekir. Ancak, sınıfı tanımlamak yeterli değildir, Ayrıca, sınıf içindeki alanların yönetilmeyen yapıya nasıl eşlenmediğini de belirlemeniz gerekir. Burada `StructLayout` öznitelik faydalı olur.

```csharp
[DllImport("kernel32.dll")]
static extern void GetSystemTime(SystemTime systemTime);

[StructLayout(LayoutKind.Sequential)]
class SystemTime {
    public ushort Year;
    public ushort Month;
    public ushort DayOfWeek;
    public ushort Day;
    public ushort Hour;
    public ushort Minute;
    public ushort Second;
    public ushort Milsecond;
}

public static void Main(string[] args) {
    SystemTime st = new SystemTime();
    GetSystemTime(st);
    Console.WriteLine(st.Year);
}
```

Önceki kod, işlevine çağırmanın basit bir örneğini gösterir `GetSystemTime()` . İlginç bit 4. satırda. Özniteliği, sınıfın alanlarının diğer (yönetilmeyen) taraftaki yapıya sırayla eşlenmesi gerektiğini belirtir. Bu, alanların adlandırılmasının önemli olmadığı, yönetilmeyen yapısına karşılık gelmesi gerektiğinden, aşağıdaki örnekte gösterildiği gibi, yalnızca kendi sırası önemli değildir.

```c
typedef struct _SYSTEMTIME {
  WORD wYear;
  WORD wMonth;
  WORD wDayOfWeek;
  WORD wDay;
  WORD wHour;
  WORD wMinute;
  WORD wSecond;
  WORD wMilliseconds;
} SYSTEMTIME, *PSYSTEMTIME;
```

Bazen yapınızın varsayılan sıralaması, ihtiyacınız olan şeyi yapmaz. [Yapı sıralamasını özelleştirme](./customize-struct-marshaling.md) makalesi, yapınızın nasıl sıralanmasını nasıl özelleştireceğinizi öğretir.
