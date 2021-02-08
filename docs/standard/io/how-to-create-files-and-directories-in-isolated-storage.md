---
description: 'Daha fazla bilgi edinin: nasıl yapılır: yalıtılmış depolamada dosya ve dizinler oluşturma'
title: 'Nasıl yapılır: Yalıtılmış Depolamada Dosya ve Dizinler Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directories [.NET], isolated storage
- files [.NET], isolated storage
- isolated storage, creating files and directories
- data stores, creating files and directories
- data storage using isolated storage, creating files and directories
- stores, creating files and directories
- storing data using isolated storage, creating files and directories
ms.assetid: 2ca4d2a4-809b-4f00-bc08-bf4a64d3a5c3
ms.openlocfilehash: dd258c38c1a02771fdd677448854c34c9014a530
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775701"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a><span data-ttu-id="a02e2-103">Nasıl yapılır: Yalıtılmış Depolamada Dosya ve Dizinler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a02e2-103">How to: Create Files and Directories in Isolated Storage</span></span>

<span data-ttu-id="a02e2-104">Yalıtılmış bir mağaza elde ettikten sonra, verileri depolamak için dizin ve dosya oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a02e2-104">After you've obtained an isolated store, you can create directories and files for storing data.</span></span> <span data-ttu-id="a02e2-105">Bir mağaza içinde, dosya ve Dizin adları, sanal dosya sisteminin köküne göre belirtilir.</span><span class="sxs-lookup"><span data-stu-id="a02e2-105">Within a store, file and directory names are specified with respect to the root of the virtual file system.</span></span>  
  
 <span data-ttu-id="a02e2-106">Bir dizin oluşturmak için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> örnek yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="a02e2-106">To create a directory, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="a02e2-107">Mevcut olmayan bir dizinin alt dizinini belirtirseniz, her iki dizin de oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a02e2-107">If you specify a subdirectory of a directory that doesn't exist, both directories are created.</span></span> <span data-ttu-id="a02e2-108">Zaten var olan bir dizin belirtirseniz, yöntem bir dizin oluşturmadan geri döner ve hiçbir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="a02e2-108">If you specify a directory that already exists, the method returns without creating a directory, and no exception is thrown.</span></span> <span data-ttu-id="a02e2-109">Ancak, geçersiz karakterler içeren bir dizin adı belirtirseniz, bir <xref:System.IO.IsolatedStorage.IsolatedStorageException> özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a02e2-109">However, if you specify a directory name that contains invalid characters, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown.</span></span>  
  
 <span data-ttu-id="a02e2-110">Bir dosya oluşturmak için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a02e2-110">To create a file, use  the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="a02e2-111">Windows işletim sisteminde, yalıtılmış depolama dosyası ve Dizin adları büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="a02e2-111">In the Windows operating system, isolated storage file and directory names are case-insensitive.</span></span> <span data-ttu-id="a02e2-112">Diğer bir deyişle, adlı bir dosya oluşturup `ThisFile.txt` daha sonra adlı başka bir dosya oluşturursanız `THISFILE.TXT` , yalnızca bir dosya oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a02e2-112">That is, if you create a file named `ThisFile.txt`, and then create another file named `THISFILE.TXT`, only one file is created.</span></span> <span data-ttu-id="a02e2-113">Dosya adı, görüntü amaçlarıyla orijinal büyük küçük harf durumunu korur.</span><span class="sxs-lookup"><span data-stu-id="a02e2-113">The file name keeps its original casing for display purposes.</span></span>  

 <span data-ttu-id="a02e2-114">Yalıtılmış depolama dosyası oluşturma <xref:System.IO.IsolatedStorage.IsolatedStorageException> yolu, mevcut olmayan bir dizin içeriyorsa, bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a02e2-114">Isolated storage file creation will throw an <xref:System.IO.IsolatedStorage.IsolatedStorageException> if the path contains a directory that does not exist.</span></span>
  
## <a name="example"></a><span data-ttu-id="a02e2-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="a02e2-115">Example</span></span>  

 <span data-ttu-id="a02e2-116">Aşağıdaki kod örneği, yalıtılmış bir depoda dosyaların ve dizinlerin nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a02e2-116">The following code example illustrates how to create files and directories in an isolated store.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a02e2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a02e2-117">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- [<span data-ttu-id="a02e2-118">Yalıtılmış depolama</span><span class="sxs-lookup"><span data-stu-id="a02e2-118">Isolated Storage</span></span>](isolated-storage.md)
