---
title: Object-Oriented programlama (C#)
description: C#; soyutlama, kapsülleme, devralma ve çok biçimlilik dahil olmak üzere nesne odaklı programlama için tam destek sağlar.
ms.date: 09/30/2020
ms.openlocfilehash: 75646a62722e6f2e24ef5bc1315c92164f3340fa
ms.sourcegitcommit: bbc724b72fb6c978905ac715e4033efa291f84dc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107369705"
---
# <a name="object-oriented-programming-c"></a>Object-Oriented programlama (C#)

C#, nesne odaklı bir programlama dilidir. Nesne odaklı programlama için dört temel ilke şunlardır:

- *Kapsülleme* Sistemin iç karmaşıklıklarını tek nesnelere göre düzenleme özelliği.
- *Soyutlama* Özelliklere, yöntemlere veya kapsüllenmiş bir şeyin üyelerine erişim veya erişimi kısıtlama özelliği.
- *Devralma* Var olan soyutlamaları temel alan yeni soyutlamalar oluşturma yeteneği.
- Çok *biçimlilik* Devralınan özellikleri veya yöntemleri birden çok soyutlamalar arasında farklı şekillerde uygulayabilme.

Önceki öğreticide, hem *soyutlamayı* hem de *kapsüllemeyi* gördüğünüz [sınıflara giriş](introduction-to-classes.md) . `BankAccount`Sınıf, bir banka hesabı kavramı için bir soyutlama sağladı. Sınıfını kullanan herhangi bir kodu etkilemeden uygulamasını değiştirebilirsiniz `BankAccount` . Hem `BankAccount` hem de `Transaction` sınıfları, koddaki bu kavramları anlatmak için gereken bileşenlerin kapsüllemesini sağlar.

Bu öğreticide, yeni özellikler eklemek için bu uygulamayı *Devralma* ve çok *biçimlilik* kullanımını kullanacak şekilde genişleteceksiniz. Ayrıca, `BankAccount` önceki öğreticide öğrendiğiniz *soyutlama* ve *kapsülleme* tekniklerinden yararlanarak sınıfa özellikler ekleyeceksiniz.

## <a name="create-different-types-of-accounts"></a>Farklı türlerde hesaplar oluşturun

Bu programı oluşturduktan sonra, ona özellik ekleme istekleri alırsınız. Yalnızca bir banka hesabı türü olduğu durumlarda harika bir şekilde çalışmaktadır. Zaman içinde, gereken değişiklik ve ilgili hesap türleri istenir:

- Her ayın sonunda ilgi çekici bir ilgi çekici hesap.
- Negatif bakiyesi olan bir kredi satırı, ancak bir bakiye söz konusu olduğunda, her ay bir faiz ücreti vardır.
- Tek bir depozito ile başlayan ve yalnızca ücret ödemekte olan ön ödemeli bir hediye kartı hesabı. Her ayın başlangıcında bir kez daha doldurulabilir.

Bu farklı hesapların tümü, `BankAccount` önceki öğreticide tanımlanan sınıfa benzerdir. Bu kodu kopyalayabilir, sınıfları yeniden adlandırabilir ve değişiklikler yapabilirsiniz. Bu teknik, kısa vadede çalışır, ancak zaman içinde daha fazla iş olur. Tüm değişiklikler etkilenen sınıfların üzerine kopyalanabilir.

Bunun yerine, `BankAccount` önceki öğreticide oluşturulan sınıftan yöntemleri ve verileri miras alan yeni banka hesap türleri oluşturabilirsiniz. Bu yeni sınıflar, her bir `BankAccount` tür için gereken belirli davranışla sınıfı genişletebilir:

```csharp
public class InterestEarningAccount : BankAccount
{
}

public class LineOfCreditAccount : BankAccount
{
}

public class GiftCardAccount : BankAccount
{
}
```

Bu sınıfların her biri paylaşılan davranışı paylaşılan *temel sınıfından*, sınıfından *devralır* `BankAccount` . *Türetilmiş sınıfların* her birinde yeni ve farklı işlevlere yönelik uygulamalar yazın.  Bu türetilmiş sınıfların, sınıfında tanımlanmış tüm davranışları zaten var `BankAccount` .

Her yeni sınıfı farklı bir kaynak dosyasında oluşturmak iyi bir uygulamadır. [Visual Studio](https://visualstudio.com)'da projeye sağ tıklayıp *Sınıf Ekle* ' yi seçerek yeni bir dosyaya yeni bir sınıf ekleyebilirsiniz. [Visual Studio Code](https://code.visualstudio.com), yeni bir kaynak dosya oluşturmak için *Dosya* ' yı ve ardından *Yeni* ' yi seçin. Her iki araçta de, " *. cs*, *lineofalacaklı taccount. cs*" ve *gıtcardaccount. cs* sınıfıyla eşleşecek dosyayı adlandırın.

Önceki örnekte gösterildiği gibi sınıfları oluşturduğunuzda, türetilmiş sınıflarınızın derlenmediği fark edeceksiniz. Bir Oluşturucu, bir nesne başlatmaktan sorumludur. Türetilmiş sınıf oluşturucusunun türetilmiş sınıfını başlatması ve türetilmiş sınıfta bulunan temel sınıf nesnesinin nasıl başlatılacağını gösteren yönergeler sağlaması gerekir. Uygun başlatma normalde herhangi bir ek kod olmadan gerçekleşir. `BankAccount`Sınıfı, aşağıdaki imzaya sahip bir ortak Oluşturucu bildirir:

```csharp
public BankAccount(string name, decimal initialBalance)
```

Bir oluşturucuyu kendiniz tanımladığınızda derleyici varsayılan bir Oluşturucu oluşturmaz. Yani, her türetilmiş sınıfın bu oluşturucuyu açıkça çağırması gerekir. Bağımsız değişkenleri temel sınıf oluşturucusuna geçirebilen bir Oluşturucu bildirirsiniz.  Aşağıdaki kod, için yapıcısını göstermektedir `InterestEarningAccount` :

:::code language="csharp" source="./snippets/object-oriented-programming/InterestEarningAccount.cs" ID="DerivedConstructor":::

Bu yeni oluşturucuya yönelik parametreler, parametre türü ve temel sınıf oluşturucusunun adlarıyla eşleşir. `: base()`Bir temel sınıf oluşturucusuna yapılan çağrıyı göstermek için söz dizimini kullanın. Bazı sınıflar birden çok Oluşturucu tanımlar ve bu sözdizimi, hangi temel sınıf oluşturucuyu çağıracağınızı seçmenizi sağlar. Oluşturucuları güncelleştirdikten sonra, türetilmiş sınıfların her biri için kodu geliştirebilirsiniz. Yeni sınıfların gereksinimleri aşağıdaki gibi belirtilebilir:

- Bir faiz kazanç hesabı:
  - Aylık son Bakiyenin %2 ' inin kredisi alınır.
- Kredi satırı:
  - Negatif bir bakiyeye sahip olabilir, ancak kredi limitinden mutlak değerde daha büyük olamaz.
  - Aylık bakiye 0 olmadığı her ay bir faiz ücreti alınacaktır.
  - Kredi sınırının üzerinde geçen her çekme al üzerinden bir ücret uygulanır.
- Bir hediye kartı hesabı:
  - Ayın son gününde her ay bir kez belirtilen miktarda yeniden doldurulabilir.

Bu hesap türlerinin üçü de her ayın sonunda yer alan bir eyleme sahip olduğunu görebilirsiniz. Ancak, her hesap türü farklı görevler yapar. Bu kodu uygulamak için çok *biçimlilik* kullanıyorsunuz. Sınıfında tek bir `virtual` Yöntem oluşturun `BankAccount` :

:::code language="csharp" source="./snippets/object-oriented-programming/BankAccount.cs" ID="DeclareMonthEndTransactions":::

Yukarıdaki kod, `virtual` türetilmiş bir sınıfın farklı bir uygulama sağlayabileceği temel sınıfta bir yöntemi bildirmek için anahtar sözcüğünü nasıl kullanacağınızı gösterir. `virtual`Yöntemi, türetilmiş herhangi bir sınıfın yeniden uygulanmasını seçebileceği bir yöntemdir. Türetilmiş sınıflar, `override` Yeni uygulamayı tanımlamak için anahtar sözcüğünü kullanır. Genellikle bunu "temel sınıf uygulamasını geçersiz kılma" olarak ifade edersiniz. `virtual`Anahtar sözcüğü, türetilmiş sınıfların davranışı geçersiz kılabileceği belirtir. Ayrıca, `abstract` türetilmiş sınıfların davranışı geçersiz kılması gereken yöntemleri de bildirebilirsiniz. Temel sınıf, bir yöntem için uygulama sağlamıyor `abstract` . Daha sonra, oluşturduğunuz yeni sınıfların ikisi için uygulamayı tanımlamanız gerekir. İle başlayın `InterestEarningAccount` :

:::code language="csharp" source="./snippets/object-oriented-programming/InterestEarningAccount.cs" ID="ApplyMonthendInterest":::

Aşağıdaki kodu öğesine ekleyin `LineOfCreditAccount` . Kod, hesaptan alınmış pozitif bir faiz ücreti hesaplamak için bakiyeyi geçersiz kılar:

:::code language="csharp" source="./snippets/object-oriented-programming/LineOfCreditAccount.cs" ID="ApplyMonthendInterest":::

`GiftCardAccount`Sınıfın ay sonu işlevlerini uygulamak için iki değişiklik yapması gerekir. İlk olarak, oluşturucuyu her ay eklenecek isteğe bağlı bir miktar içerecek şekilde değiştirin:

:::code language="csharp" source="./snippets/object-oriented-programming/GiftCardAccount.cs" ID="GiftCardAccountConstruction":::

Oluşturucu, bir değer için varsayılan değer sağlar, `monthlyDeposit` böylece çağıranlar `0` aylık depozito olmaması için bunu atlayabilir. Sonra, `PerformMonthEndTransactions` Oluşturucu içinde sıfır olmayan bir değere ayarlandıysa, aylık depozito eklemek için yöntemini geçersiz kılın:

:::code language="csharp" source="./snippets/object-oriented-programming/GiftCardAccount.cs" ID="AddMonthlyDeposit":::

Geçersiz kılma, oluşturucuda aylık depozito kümesini uygular. `Main`Ve için bu değişiklikleri test etmek üzere yöntemine aşağıdaki kodu ekleyin `GiftCardAccount` `InterestEarningAccount` :

:::code language="csharp" source="./snippets/object-oriented-programming/Program.cs" ID="FirstTests":::

Sonuçları doğrulayın. Şimdi, için benzer bir test kodu kümesi ekleyin `LineOfCreditAccount` :

```
    var lineOfCredit = new LineOfCreditAccount("line of credit", 0);
    // How much is too much to borrow?
    lineOfCredit.MakeWithdrawal(1000m, DateTime.Now, "Take out monthly advance");
    lineOfCredit.MakeDeposit(50m, DateTime.Now, "Pay back small amount");
    lineOfCredit.MakeWithdrawal(5000m, DateTime.Now, "Emergency funds for repairs");
    lineOfCredit.MakeDeposit(150m, DateTime.Now, "Partial restoration on repairs");
    lineOfCredit.PerformMonthEndTransactions();
    Console.WriteLine(lineOfCredit.GetAccountHistory());
 ```

Yukarıdaki kodu eklediğinizde ve programı çalıştırdığınızda aşağıdaki hata gibi bir şey görürsünüz:

```console
Unhandled exception. System.ArgumentOutOfRangeException: Amount of deposit must be positive (Parameter 'amount')
   at OOProgramming.BankAccount.MakeDeposit(Decimal amount, DateTime date, String note) in BankAccount.cs:line 42
   at OOProgramming.BankAccount..ctor(String name, Decimal initialBalance) in BankAccount.cs:line 31
   at OOProgramming.LineOfCreditAccount..ctor(String name, Decimal initialBalance) in LineOfCreditAccount.cs:line 9
   at OOProgramming.Program.Main(String[] args) in Program.cs:line 29
```

> [!NOTE]
> Gerçek çıktı, projenin bulunduğu klasörün tam yolunu içerir. Dosya adları, breçekimi için atlandı. Ayrıca, kod biçimlerinize bağlı olarak, satır numaraları biraz farklı olabilir.

Bu kod, `BankAccount` ilk Bakiyenin 0 ' dan büyük olması gerektiğini varsaydığından başarısız olur. Sınıfa yönelik başka bir varsayım, `BankAccount` Bakiyenin negatif gidemez. Bunun yerine, hesabı fazla çizen tüm çekme al reddedilir. Bu varsayımlar her ikisinin de değiştirilmesi gerekir. Kredi hesabı satırı 0 ' dan başlar ve genellikle negatif bir bakiyeye sahip olur. Ayrıca, bir müşteri çok fazla para alıyorsa, ücretlendirilir. İşlem kabul edilir, yalnızca daha fazla maliyetde olur. İlk kural, `BankAccount` oluşturucuya en düşük dengeyi belirten isteğe bağlı bir bağımsız değişken eklenerek uygulanabilir. Varsayılan değer: `0`. İkinci kural, türetilmiş sınıfların varsayılan algoritmayı değiştirmesini sağlayan bir mekanizmayı gerektirir. Bir anlamda, temel sınıf "ister" türetilmiş türü, aşırı taslak olduğunda ne olması gerektiğini ifade etmelidir. Varsayılan davranış, bir özel durum oluşturarak işlemi reddetmektir.

İsteğe bağlı bir parametre içeren ikinci bir Oluşturucu ekleyerek başlayalım `minimumBalance` . Bu yeni Oluşturucu, mevcut Oluşturucu tarafından gerçekleştirilen tüm işlemleri yapar. Ayrıca, Minimum bakiye özelliğini ayarlar. Var olan oluşturucunun gövdesini kopyalayabilirsiniz. Ancak bu, gelecekte değiştirilecek iki konum anlamına gelir. Bunun yerine, bir oluşturucunun başka bir oluşturucuyu aramasını sağlamak için *Oluşturucu zincirlemeyi* kullanabilirsiniz. Aşağıdaki kod iki Oluşturucusu ve yeni ek alanı göstermektedir:

 :::code language="csharp" source="./snippets/object-oriented-programming/BankAccount.cs" ID="ConstructorModifications":::

Yukarıdaki kodda iki yeni teknik gösterilmektedir. İlk olarak, `minimumBalance` alan olarak işaretlenir `readonly` . Diğer bir deyişle, nesne oluşturulduktan sonra değer değiştirilemez. Bir, oluşturulduktan sonra `BankAccount` `minimumBalance` değiştirilemez. İkincisi, iki parametre alan Oluşturucu `: this(name, initialBalance, 0) { }` uygulama olarak kullanır. `: this()`İfade, üç parametreli diğeri olan diğer oluşturucuyu çağırır. Bu teknik, istemci kodu birçok oluşturucudan birini seçebilse bile, bir nesneyi başlatmak için tek bir uygulamaya sahip etmenize olanak tanır.

Bu uygulama `MakeDeposit` yalnızca ilk bakiye şundan büyükse çağrılır `0` . Bu, mevduonun pozitif olması gereken kuralı koruyan, ancak kredi hesabının bir `0` bakiyeyle açılmasını sağlar.

Artık `BankAccount` sınıfın Minimum bakiye için salt bir salt okunurdur alanı olduğuna göre, Son değişiklik, bu durumda sabit kodu yönteminde olarak değiştirmektedir `0` `minimumBalance` `MakeWithdrawal` :

```csharp
if (Balance - amount < minimumBalance)
```

Sınıfı genişlettikten sonra `BankAccount` , `LineOfCreditAccount` aşağıdaki kodda gösterildiği gibi oluşturucuyu yeni temel oluşturucuyu çağırmak üzere değiştirebilirsiniz:

:::code language="csharp" source="./snippets/object-oriented-programming/LineOfCreditAccount.cs" ID="ConstructLineOfCredit":::

Oluşturucunun, parametrenin bir `LineOfCreditAccount` `creditLimit` anlamı ile eşleşecek şekilde parametre işaretini değiştirdiğine dikkat edin `minimumBalance` .

## <a name="different-overdraft-rules"></a>Farklı fazla taslak kuralları

Eklenecek son özellik, `LineOfCreditAccount` bir ücreti, işlemin yerine geçen kredi sınırının üzerinde hareket etmesini sağlar.

Bir yöntem, gerekli davranışı uyguladığınız sanal bir işlevi tanımlamaktır. `BankAccount`Sınıfı `MakeWithdrawal` iki yönteme şunların. Yeni yöntem, çekme al değeri en düşük değerin altına alırsa belirtilen eylemi gerçekleştirir. Mevcut `MakeWithdrawal` Yöntem aşağıdaki koda sahiptir:

```csharp
public void MakeWithdrawal(decimal amount, DateTime date, string note)
{
    if (amount <= 0)
    {
        throw new ArgumentOutOfRangeException(nameof(amount), "Amount of withdrawal must be positive");
    }
    if (Balance - amount < minimumBalance)
    {
        throw new InvalidOperationException("Not sufficient funds for this withdrawal");
    }
    var withdrawal = new Transaction(-amount, date, note);
    allTransactions.Add(withdrawal);
}
```

Aşağıdaki kodla değiştirin:

:::code language="csharp" source="./snippets/object-oriented-programming/BankAccount.cs" ID="RefactoredMakeWithdrawal":::

Eklenen yöntem, `protected` yalnızca türetilmiş sınıflardan çağrılabilecek anlamına gelir. Bu bildirim, diğer istemcilerin yöntemi aramasını engeller. Ayrıca `virtual` , türetilmiş sınıfların davranışı değiştirebilmesini sağlayacak. Dönüş türü bir `Transaction?` . `?`Ek açıklama, yöntemin dönebileceğini belirtir `null` . `LineOfCreditAccount`Çekme sınırı aşıldığında bir ücret ücreti almak için ' de aşağıdaki uygulamayı ekleyin:

:::code language="csharp" source="./snippets/object-oriented-programming/LineOfCreditAccount.cs" ID="AddOverdraftFee":::

Geçersiz kılma, hesap fazla çizilmiş olduğunda bir ücret işlemi döndürür. Çekme al, sınırın üzerinde değilse, yöntem bir `null` işlem döndürür. Bu, ücretsiz olduğunu gösterir. Aşağıdaki kodu sınıfındaki yöntemine ekleyerek bu değişiklikleri test edin `Main` `Program` :

:::code language="csharp" source="./snippets/object-oriented-programming/Program.cs" ID="TestLineOfCredit":::

Programı çalıştırın ve sonuçları denetleyin.

## <a name="summary"></a>Özet

Çıkdıysanız, Bu öğreticinin kaynağını [GitHub](https://github.com/dotnet/docs/tree/main/docs/csharp/tutorials/intro-to-csharp/snippets/object-oriented-programming)deponuzda görebilirsiniz.

Bu öğretici Object-Oriented programlamada kullanılan birçok tekniği göstermiştir:

- Farklı hesap türlerinin her biri için sınıfları tanımladığınızda *Özet* kullandınız. Bu sınıflar, bu hesap türünün davranışını açıklandı.
- Her sınıfta çok sayıda ayrıntı sakladığınızda *kapsülleme* kullandınız `private` .
- Kodu kaydetmek için sınıfında önceden oluşturulmuş uygulamayı yararlanılabilir kullandığınızda *devralmayı* kullandınız `BankAccount` .
-  `virtual` Türetilmiş sınıfların bu hesap türü için belirli davranışlar oluşturmak üzere geçersiz kılabileceği Yöntemler oluşturduğunuzda çok biçimlilik kullandınız.

Tebrikler, C# öğreticilerine giriş yaptığımızı tamamladınız. Daha fazla bilgi edinmek için [öğreticilerimizi](introduction-to-classes.md)deneyin.
