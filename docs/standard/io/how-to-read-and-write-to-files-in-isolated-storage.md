---
title: 'Nasıl yapılır: Yalıtılmış Depolamadaki Dosyaları Okuma ve Yazma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- files, isolated storage
- reading data
- storing data using isolated storage, reading and writing to files
- writing to files within store
- data storage using isolated storage, reading and writing to files
- reading files within store
- isolated storage, reading and writing to files
- data stores, reading and writing to files
- stores, reading and writing to files
ms.assetid: f977ebdc-1b55-475a-bc3d-3376470b08ae
ms.openlocfilehash: 3a8b783cf2cce93cb26b11823d9f565961376ca3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734601"
---
# <a name="how-to-read-and-write-to-files-in-isolated-storage"></a>Nasıl yapılır: Yalıtılmış Depolamadaki Dosyaları Okuma ve Yazma

Yalıtılmış bir depodaki bir dosyayı okumak veya yazmak için, <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> Stream Reader ( <xref:System.IO.StreamReader> nesne) veya Stream Writer (nesne) ile bir nesne kullanın <xref:System.IO.StreamWriter> .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod örneği yalıtılmış bir depo edinir ve TestStore.txt adlı bir dosyanın depoda mevcut olup olmadığını denetler. Yoksa, dosyayı oluşturur ve dosyaya "Hello yalıtılmış depolama" yazar. TestStore.txt zaten varsa, örnek kod dosyadan okur.  
  
 [!code-csharp[Conceptual.IsolatedStorage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source5.cs#5)]
 [!code-vb[Conceptual.IsolatedStorage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source5.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- <xref:System.IO.FileMode?displayProperty=nameWithType>
- <xref:System.IO.FileAccess?displayProperty=nameWithType>
- <xref:System.IO.StreamReader?displayProperty=nameWithType>
- <xref:System.IO.StreamWriter?displayProperty=nameWithType>
- [Dosya ve akış g/ç](index.md)
- [Yalıtılmış depolama](isolated-storage.md)
