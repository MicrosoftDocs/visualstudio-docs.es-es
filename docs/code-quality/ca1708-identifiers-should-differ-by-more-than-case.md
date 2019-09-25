---
title: 'CA1708: Los identificadores se deben diferenciar en algo más que en el uso de mayúsculas y minúsculas'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7203f7f287ebb5b71ecad6e6ad4a861d63e5cf08
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234212"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708: Los identificadores se deben diferenciar en algo más que en el uso de mayúsculas y minúsculas

|||
|-|-|
|TypeName|IdentifiersShouldDifferByMoreThanCase|
|Identificador de comprobación|CA1708|
|Categoría|Microsoft.Naming|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo

Los nombres de dos tipos, miembros, parámetros o espacios de nombres completos son idénticos cuando se convierten a minúsculas.

De forma predeterminada, esta regla solo examina los tipos, miembros y espacios de nombres visibles externamente, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Los identificadores de los espacios de nombres, miembros y parámetros no puede distinguirse sólo por mayúsculas o minúsculas porque los lenguajes que tienen como destino el Common Language Runtime no necesitan distinguir entre mayúsculas y minúsculas. Por ejemplo, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] es un lenguaje que no distingue mayúsculas de minúsculas.

Esta regla solo se desencadena en miembros visibles públicamente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Seleccione un nombre que sea único cuando se compare con otros identificadores sin distinción entre mayúsculas y minúsculas.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima las advertencias de esta regla. Es posible que la biblioteca no se pueda usar en todos los idiomas disponibles en .NET.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1708.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (nomenclatura). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example-of-a-violation"></a>Ejemplo de una infracción

En el ejemplo siguiente se muestra una infracción de esta regla.

[!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA1709: Los identificadores deben usar mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)