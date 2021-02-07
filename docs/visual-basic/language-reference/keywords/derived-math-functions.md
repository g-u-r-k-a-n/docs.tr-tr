---
description: 'Daha fazla bilgi edinin: türetilmiş matematik Işlevleri (Visual Basic)'
title: Türetilen Matematik İşlevleri
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operations, derived math functions
- cosecant function
- arcsecant function
- arccotangent function
- functions [Visual Basic], derived math functions
- inverse functions
- math functions, derived
- derived math functions
- cotangent function
- angles
- secant function
- trigonometric functions
- logarithms
- arccosecant function
- hyperbolic functions
- arcsine function
- degrees
- arccosine function
ms.assetid: 63e449d8-9444-44fb-8db1-6d9cf346e2aa
ms.openlocfilehash: daaed1312f08cecc0c68af0e36d574424fc526a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730778"
---
# <a name="derived-math-functions-visual-basic"></a>Türetilen Matematik İşlevleri (Visual Basic)

Aşağıdaki tabloda, nesnenin iç matematik işlevlerinden türetilebilecek iç olmayan matematik işlevleri gösterilmektedir <xref:System.Math?displayProperty=nameWithType> . Dosyanıza veya projenize ekleyerek iç matematik işlevlerine erişebilirsiniz `Imports System.Math` .  
  
|İşlev|Türetilmiş eşdeğerleri|  
|--------------|-------------------------|  
|Sekant (sn (x))|1/cos (x)|  
|Kosekant (CSC (x))|1/sin (x)|  
|Kotanjant (Ctan (x))|1/tan (x)|  
|Ters Sinüs (asin (x))|Atan (x/sqrt (-x * x + 1))|  
|Ters kosinüs (ACOS (x))|Atan (-x/sqrt (-x * x + 1)) + 2 \* atan (1)|  
|Ters Sekant (ASEC (x))|2 * atan (1) – atan (Imzala (x)/sqrt (x \* x – 1))|  
|Ters kosekant (ACSC (x))|Atan (x)/sqrt (x * x – 1))|  
|Ters Kotanjant (ACOT (x))|2 * atan (1)-atan (x)|  
|Hiperbolik sinüs (sinh (x))|(EXP (x) – exp (-x))/2|  
|Hiperbolik kosinüs (cosh (x))|(EXP (x) + exp (-x))/2|  
|Hiperbolik tanjant (tanh (x))|(EXP (x) – exp (-x))/(EXP (x) + exp (-x))|  
|Hiperbolik Sekant (sech (x))|2/(EXP (x) + exp (-x))|  
|Hiperbolik kosekant (Csch (x))|2/(EXP (x) – exp (-x))|  
|Hiperbolik Kotanjant (Coth (x))|(EXP (x) + exp (-x))/(EXP (x) – exp (-x))|  
|Ters hiperbolik sinüs (ASİNH (x))|Günlük (x + sqrt (x * x + 1))|  
|Ters hiperbolik kosinüs (ACOSH (x))|Günlük (x + sqrt (x * x – 1))|  
|Ters hiperbolik tanjant (ATANH (x))|Günlük ((1 + x)/(1 – x))/2|  
|Ters Hiperbolik Sekant (AsecH (x))|Günlük ((sqrt (-x * x + 1) + 1)/x)|  
|Ters hiperbolik kosekant (Acsch (x))|Log (((x) * sqrt (x \* x + 1) + 1)/x)|  
|Ters hiperbolik Kotanjant (Acoth (x))|Günlük ((x + 1)/(x – 1))/2|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Matematik Işlevleri](../functions/math-functions.md)
