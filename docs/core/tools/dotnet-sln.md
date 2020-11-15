---
title: DotNet sln komutu
description: DotNet-sln komutu bir çözüm dosyasındaki projeleri eklemek, kaldırmak ve listelemek için kullanışlı bir seçenek sağlar.
ms.date: 02/14/2020
ms.openlocfilehash: 898c53772a28b8cc3b65532dfc3d9bd6e73d467c
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634376"
---
# <a name="dotnet-sln"></a>dotnet sln

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri

## <a name="name"></a>Name

`dotnet sln` -Bir .NET çözüm dosyasındaki projeleri listeler veya değiştirir.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command]

dotnet sln [command] -h|--help
```

## <a name="description"></a>Açıklama

`dotnet sln`Komut, bir çözüm dosyasındaki projeleri listelemek ve değiştirmek için kullanışlı bir yol sağlar.

Komutunu kullanmak için `dotnet sln` , çözüm dosyası zaten var olmalıdır. Bir tane oluşturmanız gerekiyorsa, aşağıdaki örnekte olduğu gibi [DotNet New](dotnet-new.md) komutunu kullanın:

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  Kullanılacak çözüm dosyası. Bu bağımsız değişken atlanırsa, komut geçerli dizinde bir arar. Çözüm dosyası veya birden çok çözüm dosyası bulursa, komut başarısız olur.

## <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komutunun nasıl kullanılacağına ilişkin bir açıklama yazdırır.

## <a name="commands"></a>Komutlar

### `list`

Bir çözüm dosyasındaki tüm projeleri listeler.

#### <a name="synopsis"></a>Özeti

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  Kullanılacak çözüm dosyası. Bu bağımsız değişken atlanırsa, komut geçerli dizinde bir arar. Çözüm dosyası veya birden çok çözüm dosyası bulursa, komut başarısız olur.

#### <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komutunun nasıl kullanılacağına ilişkin bir açıklama yazdırır.
  
### `add`

Çözüm dosyasına bir veya daha fazla proje ekler.

#### <a name="synopsis"></a>Özeti

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder <PATH>] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  Kullanılacak çözüm dosyası. Belirtilmemişse, komut geçerli dizinde bir arar ve birden çok çözüm dosyası varsa başarısız olur.

- **`PROJECT_PATH`**

  Çözüme eklenecek projenin veya projelerin yolu. UNIX/Linux kabuğu [Glob model](https://en.wikipedia.org/wiki/Glob_(programming)) genişletmeleri, komut tarafından doğru şekilde işlenir `dotnet sln` .

#### <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komutunun nasıl kullanılacağına ilişkin bir açıklama yazdırır.

- **`--in-root`**

  Bir çözüm klasörü oluşturmak yerine, projeleri çözümün köküne koyar. .NET Core 3,0 SDK 'dan beri kullanılabilir.

- **`-s|--solution-folder <PATH>`**

  Projelerin ekleneceği hedef çözüm klasörünün yolu. .NET Core 3,0 SDK 'dan beri kullanılabilir.

### `remove`

Çözüm dosyasından bir projeyi veya birden çok projeyi kaldırır.

#### <a name="synopsis"></a>Özeti

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  Kullanılacak çözüm dosyası. Belirtilmemişse, komut geçerli dizinde bir arar ve birden çok çözüm dosyası varsa başarısız olur.

- **`PROJECT_PATH`**

  Çözüme eklenecek projenin veya projelerin yolu. UNIX/Linux kabuğu [Glob model](https://en.wikipedia.org/wiki/Glob_(programming)) genişletmeleri, komut tarafından doğru şekilde işlenir `dotnet sln` .

#### <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komutunun nasıl kullanılacağına ilişkin bir açıklama yazdırır.

## <a name="examples"></a>Örnekler

- Bir çözümdeki projeleri listeleyin:

  ```dotnetcli
  dotnet sln todo.sln list
  ```

- Bir çözüme C# projesi ekleyin:

  ```dotnetcli
  dotnet sln add todo-app/todo-app.csproj
  ```

- Bir C# projesini çözümden kaldırma:

  ```dotnetcli
  dotnet sln remove todo-app/todo-app.csproj
  ```

- Bir çözümün köküne birden çok C# projesi ekleyin:

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj --in-root
  ```

- Bir çözüme birden çok C# projesi ekleyin:

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- Bir çözümden birden çok C# projesini kaldırma:

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- Bir glob deseninin (yalnızca Unix/Linux) kullanıldığı bir çözüme birden çok C# projesi ekleme:

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- Glob deseninin kullanıldığı bir çözüme birden çok C# projesi ekleme (yalnızca Windows PowerShell):

  ```dotnetcli
  dotnet sln todo.sln add (ls -r **/*.csproj)
  ```

- Bir glob deseninin (yalnızca Unix/Linux) kullanıldığı bir çözümden birden çok C# projesini kaldırma:

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```

- Glob deseninin kullanıldığı bir çözümden birden çok C# projesini kaldırma (yalnızca Windows PowerShell):

  ```dotnetcli
  dotnet sln todo.sln remove (ls -r **/*.csproj)
  ```
