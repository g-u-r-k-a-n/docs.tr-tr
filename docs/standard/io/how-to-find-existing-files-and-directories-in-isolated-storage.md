---
title: 'Nasıl yapılır: Yalıtılmış Depolamada Mevcut Dosya ve Dizinleri Bulma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, finding files and directories
- locating files in isolated storage file
- directories [.NET], isolated storage
- isolated storage, finding files and directories
- data storage using isolated storage, finding files and directories
- files [.NET], isolated storage
- data stores, finding files and directories
- locating directories in isolated storage file
- storing data using isolated storage, finding files and directories
ms.assetid: eb28458a-6161-4e7a-9ada-30ef93761b5c
ms.openlocfilehash: 43685a6ecb92510ad8d80c472a1c774d46cbb5f7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734640"
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a><span data-ttu-id="235f2-102">Nasıl yapılır: Yalıtılmış Depolamada Mevcut Dosya ve Dizinleri Bulma</span><span class="sxs-lookup"><span data-stu-id="235f2-102">How to: Find Existing Files and Directories in Isolated Storage</span></span>

<span data-ttu-id="235f2-103">Yalıtılmış depolamada bir dizin aramak için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="235f2-103">To search for a directory in isolated storage, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="235f2-104">Bu yöntem, bir arama modelini temsil eden bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="235f2-104">This method takes a string that represents a search pattern.</span></span> <span data-ttu-id="235f2-105">Arama düzeninde hem tek karakterli (?) hem çok karakterli ( \* ) joker karakterleri kullanabilirsiniz, ancak joker karakterlerin adın son bölümünde görünmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="235f2-105">You can use both single-character (?) and multi-character (\*) wildcard characters in the search pattern, but the wildcard characters must appear in the final portion of the name.</span></span> <span data-ttu-id="235f2-106">Örneğin, `directory1/*ect*` geçerli bir arama dizesidir, ancak `*ect*/directory2` değildir.</span><span class="sxs-lookup"><span data-stu-id="235f2-106">For example, `directory1/*ect*` is a valid search string, but `*ect*/directory2` is not.</span></span>  
  
 <span data-ttu-id="235f2-107">Bir dosya aramak için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="235f2-107">To search for a file, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="235f2-108">İçin geçerli olan arama dizelerindeki joker karakterler için olan kısıtlama, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> için de geçerlidir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> .</span><span class="sxs-lookup"><span data-stu-id="235f2-108">The restriction for wildcard characters in search strings that applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> also applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span></span>  
  
 <span data-ttu-id="235f2-109">Bu yöntemlerin hiçbiri özyinelemeli değildir; <xref:System.IO.IsolatedStorage.IsolatedStorageFile> sınıfı, Deponuzdaki tüm dizinleri veya dosyaları listelemek için herhangi bir yöntem sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="235f2-109">Neither of these methods is recursive; the <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class does not supply any methods for listing all directories or files in your store.</span></span> <span data-ttu-id="235f2-110">Ancak özyinelemeli yöntemler aşağıdaki kod örneğinde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="235f2-110">However, recursive methods are shown in the following code example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="235f2-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="235f2-111">Example</span></span>  

 <span data-ttu-id="235f2-112">Aşağıdaki kod örneği, yalıtılmış bir depoda dosyaların ve dizinlerin nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="235f2-112">The following code example illustrates how to create files and directories in an isolated store.</span></span> <span data-ttu-id="235f2-113">İlk olarak, Kullanıcı, etki alanı ve derleme için yalıtılmış bir mağaza alınır ve `isoStore` değişkenine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="235f2-113">First, a store that is isolated for user, domain, and assembly is retrieved and placed in the `isoStore` variable.</span></span> <span data-ttu-id="235f2-114"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A>Yöntemi birkaç farklı dizin ayarlamak için kullanılır ve <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> Oluşturucu bu dizinlerde bazı dosyalar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="235f2-114">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> method is used to set up a few different directories, and the <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> constructor creates some files in these directories.</span></span> <span data-ttu-id="235f2-115">Kod daha sonra yöntemin sonuçları boyunca döngü yapılır `GetAllDirectories` .</span><span class="sxs-lookup"><span data-stu-id="235f2-115">The code then loops through the results of the `GetAllDirectories` method.</span></span> <span data-ttu-id="235f2-116">Bu yöntem, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> geçerli dizindeki tüm dizin adlarını bulmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="235f2-116">This method uses <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> to find all the directory names in the current directory.</span></span> <span data-ttu-id="235f2-117">Bu adlar bir dizide depolanır ve sonra `GetAllDirectories` bulduğu her bir dizine geçerek kendisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="235f2-117">These names are stored in an array, and then `GetAllDirectories` calls itself, passing in each directory it has found.</span></span> <span data-ttu-id="235f2-118">Sonuç olarak, tüm dizin adları bir dizide döndürülür.</span><span class="sxs-lookup"><span data-stu-id="235f2-118">As a result, all the directory names are returned in an array.</span></span> <span data-ttu-id="235f2-119">Ardından, kod `GetAllFiles` yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="235f2-119">Next, the code calls the `GetAllFiles` method.</span></span> <span data-ttu-id="235f2-120">Bu yöntem, `GetAllDirectories` tüm dizinlerin adlarını bulmak için öğesini çağırır ve sonra yöntemini kullanarak her bir dizini dosyalar için denetler <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> .</span><span class="sxs-lookup"><span data-stu-id="235f2-120">This method calls `GetAllDirectories` to find out the names of all the directories, and then it checks each directory for files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> method.</span></span> <span data-ttu-id="235f2-121">Sonuç, görüntüleme için bir dizide döndürülür.</span><span class="sxs-lookup"><span data-stu-id="235f2-121">The result is returned in an array for display.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="235f2-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="235f2-122">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="235f2-123">Yalıtılmış depolama</span><span class="sxs-lookup"><span data-stu-id="235f2-123">Isolated Storage</span></span>](isolated-storage.md)
