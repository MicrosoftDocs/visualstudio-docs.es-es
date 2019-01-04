---
title: 'CA1044: Las propiedades no deben ser de solo escritura'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e9d543c915cecbaa4f37a694786e80876bdf06cd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53959097"
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: Las propiedades no deben ser de solo escritura

|||
|-|-|
|TypeName|PropertiesShouldNotBeWriteOnly|
|Identificador de comprobación|CA1044|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 La propiedad pública o protegida tiene un descriptor de acceso, pero no tiene un descriptor de acceso get.

## <a name="rule-description"></a>Descripción de la regla
 Obtenga los descriptores de acceso proporcionan acceso de lectura a una propiedad y descriptores de acceso set proporcionan acceso de escritura. Aunque es aceptable y a menudo necesario tener una propiedad de solo lectura, las directrices de diseño prohíben el uso de propiedades de solo escritura. Esto se debe permitir que un usuario establecer un valor y, a continuación, impide que el usuario vea el valor no proporciona ninguna seguridad. Además, sin acceso de lectura, no se puede ver el estado de los objetos compartidos, lo que limita su utilidad.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue un descriptor de acceso get a la propiedad. Como alternativa, si es necesario el comportamiento de una propiedad de solo escritura, considere la posibilidad de convertir esta propiedad en un método.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Se recomienda que no suprima una advertencia de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, `BadClassWithWriteOnlyProperty` es un tipo con una propiedad de solo escritura. `GoodClassWithReadWriteProperty` contiene el código corregido.

 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]