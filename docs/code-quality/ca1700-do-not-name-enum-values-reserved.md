---
title: 'CA1700: No nombrar valores de enumeración &#39;reservado&#39;'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 27372856d8984a1c16741142a4affec757670b32
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914639"
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700: No nombrar valores de enumeración &#39;reservado&#39;

|||
|-|-|
|TypeName|DoNotNameEnumValuesReserved|
|Identificador de comprobación|CA1700|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo

El nombre de un miembro de enumeración contiene la palabra "reserved".

## <a name="rule-description"></a>Descripción de la regla

Esta regla supone que un miembro de la enumeración con un nombre que contiene la palabra "reserved" no se utiliza actualmente pero hace de marcador de posición para que se pueda quitar o cambiar el nombre en una versión posterior. Quitar o cambiar el nombre de un miembro es un cambio importante. No debe esperar a los usuarios omitir a un miembro solo porque su nombre contiene "reservada", ni se puede confiar en los usuarios lean o atenerse a la documentación. Además, dado que reservada miembros aparecen en los exploradores de objetos y entornos de desarrollo integrado inteligente, pueden provocar confusión sobre qué miembros se usan en realidad.

En lugar de un miembro reservado, agregue a un nuevo miembro a la enumeración en la versión futura. En la mayoría de los casos la adición del nuevo miembro no es un cambio importante, como la adición no hace que los valores de los miembros originales a cambiar.

En un número limitado de los casos la adición de un miembro es un cambio importante incluso cuando los miembros originales se conservan sus valores originales. Principalmente, el nuevo miembro no se puede devolver desde rutas de acceso de código existente sin interrumpir los llamadores que usen un `switch` (`Select` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) instrucción en el valor devuelto que abarca la lista de miembros completo y que produce una excepción el caso predeterminado. Una preocupación secundaria es que el código de cliente no puede controlar el cambio de comportamiento de los métodos de reflexión como <xref:System.Enum.IsDefined%2A?displayProperty=fullName>. En consecuencia, si el nuevo miembro se va a devolver desde los métodos existentes o se produce una incompatibilidad de aplicaciones conocidos debido al uso de reflexión deficiente, la única solución de no separación es:

1. Agregue una nueva enumeración que contiene a los miembros originales y nuevos.

2. Marque la enumeración original con el <xref:System.ObsoleteAttribute?displayProperty=fullName> atributo.

   Siga el mismo procedimiento para los tipos visibles externamente o miembros que exponen la enumeración original.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, quite o cambie el nombre del miembro.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Es seguro suprimir una advertencia de esta regla para un miembro que se usa actualmente o para bibliotecas que se han enviado anteriormente.

## <a name="related-rules"></a>Reglas relacionadas

[CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

[CA1712: No utilizar prefijos en valores de enumeración con el nombre de tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

[CA1028: Almacenamiento de enum debe ser Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

[CA1008: Las enumeraciones deben tener el valor cero](../code-quality/ca1008-enums-should-have-zero-value.md)

[CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)