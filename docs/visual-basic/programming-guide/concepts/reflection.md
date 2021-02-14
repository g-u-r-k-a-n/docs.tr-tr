---
description: 'Daha fazla bilgi edinin: yansıma (Visual Basic)'
title: Yansıma
ms.date: 07/20/2015
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
ms.openlocfilehash: 532087f2ac32242b473d4524a6026519951d96d2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100486816"
---
# <a name="reflection-visual-basic"></a>Yansıma (Visual Basic)

Yansıma <xref:System.Type> derlemeleri, modülleri ve türleri tanımlayan nesneler (türü) sağlar. Bir türün örneğini dinamik olarak oluşturmak, türü var olan bir nesneye bağlamak veya var olan bir nesneden türü almak ya da onun yöntemlerini çağırmak ya da alanları ve özelliklerine erişmek için yansıma kullanabilirsiniz. Kodunuzda öznitelikler kullanıyorsanız, yansıma bunlara erişmenizi sağlar. Daha fazla bilgi için bkz. [öznitelikler](../../../standard/attributes/index.md).  
  
 `GetType` `Object` Bir değişkenin türünü almak için temel sınıftan tüm türler tarafından devralınan statik yöntemi kullanan basit bir yansıma örneği aşağıda verilmiştir:  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 Çıkış şöyle olur:  
  
 `System.Int32`  
  
 Aşağıdaki örnek, yüklü derlemenin tam adını almak için yansıma kullanır.  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 Çıkış şöyle olur:  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a>Yansımaya genel bakış  

 Aşağıdaki durumlarda yansıma yararlı olur:  
  
- Programınızın meta verilerindeki özniteliklere erişmeniz gerektiğinde. Daha fazla bilgi için bkz. [özniteliklerde depolanan bilgileri alma](../../../standard/attributes/retrieving-information-stored-in-attributes.md).  
  
- Bir derlemedeki türleri İnceleme ve örnekleme için.  
  
- Çalışma zamanında yeni türler oluşturmak için. İçinde sınıfları kullanın <xref:System.Reflection.Emit> .  
  
- Geç bağlama gerçekleştirmek için çalışma zamanında oluşturulan türler üzerindeki yöntemlere erişme. [Türleri dinamik olarak yükleme ve kullanma](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md)konusuna bakın.  
  
## <a name="related-sections"></a>İlgili Bölümler  

 Daha fazla bilgi için:  
  
- [Yansıma](../../../framework/reflection-and-codedom/reflection.md)  
  
- [Tür Bilgilerini Görüntüleme](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
- [Yansıma ve Genel Türler](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
- <xref:System.Reflection.Emit>  
  
- [Özniteliklerde Depolanan Bilgileri Alma](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Programlama Kılavuzu](../index.md)
- [.NET’te bütünleştirilmiş kodlar](../../../standard/assembly/index.md)
