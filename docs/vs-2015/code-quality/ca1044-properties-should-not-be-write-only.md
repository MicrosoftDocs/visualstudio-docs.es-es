---
title: 'CA1044: Las propiedades no deberían ser de solo escritura | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 444081d1e55bd76b67162add508d4f78415e4b3b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68143195"
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: Las propiedades no deben ser de solo escritura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PropertiesShouldNotBeWriteOnly|
|Identificador de comprobación|CA1044|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 La propiedad pública o protegida tiene un descriptor de acceso, pero no tiene un descriptor de acceso get.

## <a name="rule-description"></a>Descripción de la regla
 Obtenga los descriptores de acceso proporcionan acceso de lectura a una propiedad y descriptores de acceso set proporcionan acceso de escritura. Aunque es aceptable y a menudo necesario tener una propiedad de solo lectura, las directrices de diseño prohíben el uso de propiedades de solo escritura. Esto se debe permitir que un usuario establecer un valor y, a continuación, impide que el usuario vea el valor no proporciona ninguna seguridad. Además, sin acceso de lectura, no se puede ver el estado de los objetos compartidos, lo que limita su utilidad.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue un descriptor de acceso get a la propiedad. Como alternativa, si es necesario el comportamiento de una propiedad de solo escritura, considere la posibilidad de convertir esta propiedad en un método.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Se recomienda encarecidamente que no suprima una advertencia de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, `BadClassWithWriteOnlyProperty` es un tipo con una propiedad de solo escritura. `GoodClassWithReadWriteProperty` contiene el código corregido.

 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/cs/FxCop.Design.PropertiesNotWriteOnly.cs#1)]
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/vb/PropertiesNotWriteOnly.vb#1)]
