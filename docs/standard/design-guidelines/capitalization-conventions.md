---
title: Büyük/Küçük Harf Kuralları
description: Tanımlayıcılar, bileşik sözcükler ve genel terimler için büyük harfe çevirme kuralları uygulayın. .NET 'ta büyük/küçük harf duyarlılığı 'nın nasıl çalıştığını anlayın.
ms.date: 10/22/2008
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
ms.openlocfilehash: e416a8346952a41d9c89f526bfce990dfc277fc1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701269"
---
# <a name="capitalization-conventions"></a><span data-ttu-id="b08e2-104">Büyük/Küçük Harf Kuralları</span><span class="sxs-lookup"><span data-stu-id="b08e2-104">Capitalization Conventions</span></span>

<span data-ttu-id="b08e2-105">Bu bölümdeki yönergeler, tutarlı bir şekilde uygulandığında, türler, Üyeler ve parametreler için tanımlayıcıların kolay okunmasını sağlamak üzere basit bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="b08e2-105">The guidelines in this chapter lay out a simple method for using case that, when applied consistently, make identifiers for types, members, and parameters easy to read.</span></span>

## <a name="capitalization-rules-for-identifiers"></a><span data-ttu-id="b08e2-106">Tanımlayıcılar için büyük harfe dönüştürme kuralları</span><span class="sxs-lookup"><span data-stu-id="b08e2-106">Capitalization Rules for Identifiers</span></span>

 <span data-ttu-id="b08e2-107">Bir Tanımlayıcıdaki sözcükleri ayırt etmek için, Tanımlayıcıdaki her sözcüğün ilk harfini büyük harfle yapın.</span><span class="sxs-lookup"><span data-stu-id="b08e2-107">To differentiate words in an identifier, capitalize the first letter of each word in the identifier.</span></span> <span data-ttu-id="b08e2-108">Sözcükleri ayırt etmek için alt çizgi kullanmayın veya bu konuyla ilgili olarak tanımlayıcılardan herhangi bir yerde.</span><span class="sxs-lookup"><span data-stu-id="b08e2-108">Do not use underscores to differentiate words, or for that matter, anywhere in identifiers.</span></span> <span data-ttu-id="b08e2-109">Tanımlayıcının kullanılmasına bağlı olarak, tanımlayıcıları büyük harfle almanın iki uygun yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="b08e2-109">There are two appropriate ways to capitalize identifiers, depending on the use of the identifier:</span></span>

- <span data-ttu-id="b08e2-110">Pascalbüyük harf</span><span class="sxs-lookup"><span data-stu-id="b08e2-110">PascalCasing</span></span>

- <span data-ttu-id="b08e2-111">Camelbüyük harf</span><span class="sxs-lookup"><span data-stu-id="b08e2-111">camelCasing</span></span>

 <span data-ttu-id="b08e2-112">Parametre adları hariç tüm tanımlayıcılar için kullanılan Pascalas kuralı, aşağıdaki örneklerde gösterildiği gibi her sözcüğün ilk karakterini (uzunluğunun iki harfli kısaltmalarla birlikte) büyük harfe dönüştürür:</span><span class="sxs-lookup"><span data-stu-id="b08e2-112">The PascalCasing convention, used for all identifiers except parameter names, capitalizes the first character of each word (including acronyms over two letters in length), as shown in the following examples:</span></span>

 `PropertyDescriptor`
 `HtmlTag`

 <span data-ttu-id="b08e2-113">Aşağıdaki tanımlayıcıda gösterildiği gibi, iki harfli kısaltmalar için her iki harf de büyük harfli olan özel bir durum yapılır:</span><span class="sxs-lookup"><span data-stu-id="b08e2-113">A special case is made for two-letter acronyms in which both letters are capitalized, as shown in the following identifier:</span></span>

 `IOStream`

 <span data-ttu-id="b08e2-114">Yalnızca parametre adları için kullanılan Camelas kuralı, aşağıdaki örneklerde gösterildiği gibi ilk sözcük hariç her sözcüğün ilk karakterini büyük harfe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="b08e2-114">The camelCasing convention, used only for parameter names, capitalizes the first character of each word except the first word, as shown in the following examples.</span></span> <span data-ttu-id="b08e2-115">Örnekte de gösterildiği gibi, Camel bir tanımlayıcıya başlayan iki harfli kısaltmalar her ikisi de küçük harftir.</span><span class="sxs-lookup"><span data-stu-id="b08e2-115">As the example also shows, two-letter acronyms that begin a camel-cased identifier are both lowercase.</span></span>

 `propertyDescriptor`
 `ioStream`
 `htmlTag`

 <span data-ttu-id="b08e2-116">✔️, birden çok sözcükten oluşan tüm ortak üye, tür ve ad alanı adları için Pascalbüyük harfleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="b08e2-116">✔️ DO use PascalCasing for all public member, type, and namespace names consisting of multiple words.</span></span>

 <span data-ttu-id="b08e2-117">✔️ parametre adları için Camelum kullanın.</span><span class="sxs-lookup"><span data-stu-id="b08e2-117">✔️ DO use camelCasing for parameter names.</span></span>

 <span data-ttu-id="b08e2-118">Aşağıdaki tabloda, farklı türlerde tanımlayıcılar için büyük/küçük harf kuralları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b08e2-118">The following table describes the capitalization rules for different types of identifiers.</span></span>

|<span data-ttu-id="b08e2-119">Tanımlayıcı</span><span class="sxs-lookup"><span data-stu-id="b08e2-119">Identifier</span></span>|<span data-ttu-id="b08e2-120">Büyük/Küçük Harf Kullanımı</span><span class="sxs-lookup"><span data-stu-id="b08e2-120">Casing</span></span>|<span data-ttu-id="b08e2-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="b08e2-121">Example</span></span>|
|----------------|------------|-------------|
|<span data-ttu-id="b08e2-122">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="b08e2-122">Namespace</span></span>|<span data-ttu-id="b08e2-123">Pascal</span><span class="sxs-lookup"><span data-stu-id="b08e2-123">Pascal</span></span>|`namespace System.Security { ... }`|
|<span data-ttu-id="b08e2-124">Tür</span><span class="sxs-lookup"><span data-stu-id="b08e2-124">Type</span></span>|<span data-ttu-id="b08e2-125">Pascal</span><span class="sxs-lookup"><span data-stu-id="b08e2-125">Pascal</span></span>|`public class StreamReader { ... }`|
|<span data-ttu-id="b08e2-126">Arabirim</span><span class="sxs-lookup"><span data-stu-id="b08e2-126">Interface</span></span>|<span data-ttu-id="b08e2-127">Pascal</span><span class="sxs-lookup"><span data-stu-id="b08e2-127">Pascal</span></span>|`public interface IEnumerable { ... }`|
|<span data-ttu-id="b08e2-128">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b08e2-128">Method</span></span>|<span data-ttu-id="b08e2-129">Pascal</span><span class="sxs-lookup"><span data-stu-id="b08e2-129">Pascal</span></span>|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|
|<span data-ttu-id="b08e2-130">Özellik</span><span class="sxs-lookup"><span data-stu-id="b08e2-130">Property</span></span>|<span data-ttu-id="b08e2-131">Pascal</span><span class="sxs-lookup"><span data-stu-id="b08e2-131">Pascal</span></span>|`public class String {` <br />  `public int Length { get; }` <br /> `}`|
|<span data-ttu-id="b08e2-132">Olay</span><span class="sxs-lookup"><span data-stu-id="b08e2-132">Event</span></span>|<span data-ttu-id="b08e2-133">Pascal</span><span class="sxs-lookup"><span data-stu-id="b08e2-133">Pascal</span></span>|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|
|<span data-ttu-id="b08e2-134">Alan</span><span class="sxs-lookup"><span data-stu-id="b08e2-134">Field</span></span>|<span data-ttu-id="b08e2-135">Pascal</span><span class="sxs-lookup"><span data-stu-id="b08e2-135">Pascal</span></span>|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|
|<span data-ttu-id="b08e2-136">Sabit listesi değeri</span><span class="sxs-lookup"><span data-stu-id="b08e2-136">Enum value</span></span>|<span data-ttu-id="b08e2-137">Pascal</span><span class="sxs-lookup"><span data-stu-id="b08e2-137">Pascal</span></span>|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|
|<span data-ttu-id="b08e2-138">Parametre</span><span class="sxs-lookup"><span data-stu-id="b08e2-138">Parameter</span></span>|<span data-ttu-id="b08e2-139">Ortası büyük harf</span><span class="sxs-lookup"><span data-stu-id="b08e2-139">Camel</span></span>|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|

## <a name="capitalizing-compound-words-and-common-terms"></a><span data-ttu-id="b08e2-140">Bileşik sözcüklerin ve ortak koşulların büyük bir olması</span><span class="sxs-lookup"><span data-stu-id="b08e2-140">Capitalizing Compound Words and Common Terms</span></span>

 <span data-ttu-id="b08e2-141">Çoğu bileşik terim, büyük küçük harf amaçlarıyla tek sözcük olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="b08e2-141">Most compound terms are treated as single words for purposes of capitalization.</span></span>

 <span data-ttu-id="b08e2-142">❌ Bu nedenle, kapalı biçimli bileşik sözcükler olarak adlandırılan her sözcüğü büyük harfle kaldırmayın.</span><span class="sxs-lookup"><span data-stu-id="b08e2-142">❌ DO NOT capitalize each word in so-called closed-form compound words.</span></span>

 <span data-ttu-id="b08e2-143">Bunlar, uç nokta gibi tek bir kelime olarak yazılmış olan Birleşik sözcüklerdir.</span><span class="sxs-lookup"><span data-stu-id="b08e2-143">These are compound words written as a single word, such as endpoint.</span></span> <span data-ttu-id="b08e2-144">Büyük/küçük harf yönergeleri için kapalı biçimli bir bileşik sözcüğü tek bir sözcük olarak değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="b08e2-144">For the purpose of casing guidelines, treat a closed-form compound word as a single word.</span></span> <span data-ttu-id="b08e2-145">Bileşik bir sözcüğün kapalı biçimde yazılıp yazılmadığını öğrenmek için geçerli bir sözlük kullanın.</span><span class="sxs-lookup"><span data-stu-id="b08e2-145">Use a current dictionary to determine if a compound word is written in closed form.</span></span>

|<span data-ttu-id="b08e2-146">Pascal</span><span class="sxs-lookup"><span data-stu-id="b08e2-146">Pascal</span></span>|<span data-ttu-id="b08e2-147">Ortası büyük harf</span><span class="sxs-lookup"><span data-stu-id="b08e2-147">Camel</span></span>|<span data-ttu-id="b08e2-148">Not</span><span class="sxs-lookup"><span data-stu-id="b08e2-148">Not</span></span>|
|------------|-----------|---------|
|`BitFlag`|`bitFlag`|`Bitflag`|
|`Callback`|`callback`|`CallBack`|
|`Canceled`|`canceled`|`Cancelled`|
|`DoNot`|`doNot`|`Don't`|
|`Email`|`email`|`EMail`|
|`Endpoint`|`endpoint`|`EndPoint`|
|`FileName`|`fileName`|`Filename`|
|`Gridline`|`gridline`|`GridLine`|
|`Hashtable`|`hashtable`|`HashTable`|
|`Id`|`id`|`ID`|
|`Indexes`|`indexes`|`Indices`|
|`LogOff`|`logOff`|`LogOut`|
|`LogOn`|`logOn`|`LogIn`|
|`Metadata`|`metadata`|`MetaData, metaData`|
|`Multipanel`|`multipanel`|`MultiPanel`|
|`Multiview`|`multiview`|`MultiView`|
|`Namespace`|`namespace`|`NameSpace`|
|`Ok`|`ok`|`OK`|
|`Pi`|`pi`|`PI`|
|`Placeholder`|`placeholder`|`PlaceHolder`|
|`SignIn`|`signIn`|`SignOn`|
|`SignOut`|`signOut`|`SignOff`|
|`UserName`|`userName`|`Username`|
|`WhiteSpace`|`whiteSpace`|`Whitespace`|
|`Writable`|`writable`|`Writeable`|

## <a name="case-sensitivity"></a><span data-ttu-id="b08e2-149">Büyük/küçük harf duyarlılığı</span><span class="sxs-lookup"><span data-stu-id="b08e2-149">Case Sensitivity</span></span>

 <span data-ttu-id="b08e2-150">CLR üzerinde çalışabilen dillerin, büyük/küçük harf duyarlılığı desteklemek için gerekli değildir, ancak bazıları.</span><span class="sxs-lookup"><span data-stu-id="b08e2-150">Languages that can run on the CLR are not required to support case-sensitivity, although some do.</span></span> <span data-ttu-id="b08e2-151">Diliniz destekliyorsa bile, çerçeve'nize erişebilen diğer diller değildir.</span><span class="sxs-lookup"><span data-stu-id="b08e2-151">Even if your language supports it, other languages that might access your framework do not.</span></span> <span data-ttu-id="b08e2-152">Bu nedenle dışarıdan erişilebilen tüm API 'Ler, aynı bağlamdaki iki ad arasında ayrım yapmak için tek başına bir durum kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="b08e2-152">Any APIs that are externally accessible, therefore, cannot rely on case alone to distinguish between two names in the same context.</span></span>

 <span data-ttu-id="b08e2-153">❌ Tüm programlama dillerinin büyük/küçük harfe duyarlı olduğunu varsaymayın.</span><span class="sxs-lookup"><span data-stu-id="b08e2-153">❌ DO NOT assume that all programming languages are case sensitive.</span></span> <span data-ttu-id="b08e2-154">Bunlar değildir.</span><span class="sxs-lookup"><span data-stu-id="b08e2-154">They are not.</span></span> <span data-ttu-id="b08e2-155">Adlar tek başına büyük/küçük harf bakımından farklı olamaz.</span><span class="sxs-lookup"><span data-stu-id="b08e2-155">Names cannot differ by case alone.</span></span>

 <span data-ttu-id="b08e2-156">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="b08e2-156">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="b08e2-157">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="b08e2-157">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="b08e2-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b08e2-158">See also</span></span>

- [<span data-ttu-id="b08e2-159">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="b08e2-159">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="b08e2-160">Adlandırma yönergeleri</span><span class="sxs-lookup"><span data-stu-id="b08e2-160">Naming Guidelines</span></span>](naming-guidelines.md)
