---
title: Nothing ve Dizeler
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: dfc43748d0754f0a6a29763c42ab82d9937f89f8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344303"
---
# <a name="nothing-and-strings-in-visual-basic"></a>Visual Basic'de Dizeler ve Nothing
The Visual Basic runtime and the .NET Framework evaluate `Nothing` differently when it comes to strings.  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Visual Basic Runtime and the .NET Framework  
 Consider the following example:  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 The Visual Basic runtime usually evaluates `Nothing` as an empty string (""). The .NET Framework does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Introduction to Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
