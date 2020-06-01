---
title: Dosyalar, klasörler ve sürücüler hakkında bilgi edinme-C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: 32aced17634a1406e2fce0af9c2a92f7a5eb9b40
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241623"
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a>Dosyalar, klasörler ve sürücüler hakkında bilgi alma (C# Programlama Kılavuzu)
.NET ' te aşağıdaki sınıfları kullanarak dosya sistemi bilgilerine erişebilirsiniz:  
  
- <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.Directory?displayProperty=nameWithType>  
  
- <xref:System.IO.File?displayProperty=nameWithType>  
  
 <xref:System.IO.FileInfo>Ve <xref:System.IO.DirectoryInfo> sınıfları bir dosya veya dizini temsil eder ve NTFS dosya sistemi tarafından desteklenen dosya özniteliklerinin çoğunu açığa çıkaran özellikler içerir. Ayrıca dosya ve klasörleri açma, kapatma, taşıma ve silme yöntemleri de bulunur. Oluşturucuya dosya, klasör veya sürücü adını temsil eden bir dize geçirerek, bu sınıfların örneklerini oluşturabilirsiniz:  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 Ayrıca, ve için yapılan çağrıları kullanarak dosyaların, klasörlerin veya sürücülerin adlarını elde edebilirsiniz <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType> <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType> <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType> .  
  
 <xref:System.IO.Directory?displayProperty=nameWithType>Ve <xref:System.IO.File?displayProperty=nameWithType> sınıfları, dizinler ve dosyalar hakkında bilgi almak için statik yöntemler sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek dosya ve klasörlerle ilgili bilgilere erişmek için çeşitli yollar gösterir.  
  
 [!code-csharp[csFilesandFolders#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#6)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Kullanıcı tarafından belirtilen yol dizelerini işlerken aşağıdaki koşullarda özel durumları da işlemeniz gerekir:  
  
- Dosya adı hatalı biçimlendirilmiş. Örneğin, geçersiz karakterler veya yalnızca boşluk içeriyor.  
  
- Dosya adı null.  
  
- Dosya adı sistem tarafından tanımlanan uzunluk üst sınırından daha uzun.  
  
- Dosya adı iki nokta üst üste (:)) sahiptir.  
  
 Uygulama, belirtilen dosyayı okumak için yeterli izinlere sahip değilse, `Exists` Yöntem `false` bir yolun var olup olmadığına bakılmaksızın döndürülür; Yöntem bir özel durum oluşturmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IO?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](../index.md)
- [Dosya Sistemi ve Kayıt Defteri (C# Programlama Kılavuzu)](./index.md)
