---
title: 'CA1709: Los identificadores deben utilizar las mayúsculas y minúsculas correctamente'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f692218cd051338a6bd4e83a07d985bb52f907e6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55932084"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709: Los identificadores deben utilizar las mayúsculas y minúsculas correctamente

|||
|-|-|
|TypeName|IdentifiersShouldBeCasedCorrectly|
|Identificador de comprobación|CA1709|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático: cuando se desencadena en los ensamblados, espacios de nombres, tipos, miembros y parámetros.<br /><br /> Indivisible - cuando se desencadena en los parámetros de tipo genérico.|

## <a name="cause"></a>Motivo
 El nombre de un identificador no utilizando las mayúsculas correctamente.

 \- o -

 El nombre de un identificador contiene un acrónimo de dos letras y la segunda letra es minúscula.

 \- o -

 El nombre de un identificador contiene un acrónimo de tres o más letras mayúsculas.

## <a name="rule-description"></a>Descripción de la regla
 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esta coherencia reduce la curva de aprendizaje necesario para las nuevas bibliotecas de software y aumenta la confianza del cliente que la biblioteca fue desarrollada por alguien que tenga experiencia en desarrollo de código administrado.

 Por convención, los nombres de parámetro utilizan camel de mayúsculas y minúsculas y espacio de nombres, el tipo y los nombres de miembro utilizan la convención Pascal mayúsculas y minúsculas. En un nombre con grafía camel, la primera letra es minúscula y la primera letra de las demás palabras en el nombre está en mayúscula. Ejemplos de nombres con grafía camel `packetSniffer`, `ioFile`, y `fatalErrorCode`. En un nombre con grafía Pascal, está en mayúscula la primera letra, y la primera letra de las demás palabras en el nombre en mayúscula. Ejemplos de nombres con grafía Pascal `PacketSniffer`, `IOFile`, y `FatalErrorCode`.

 Esta regla divide el nombre en palabras según las mayúsculas y minúsculas y comprueba las palabras de dos letras con una lista de palabras comunes de dos letras, por ejemplo, "In" o "My". Si no se encuentra una coincidencia, la palabra se supone que un acrónimo. Además, esta regla supone que ha encontrado un acrónimo cuando el nombre contiene cuatro letras mayúsculas seguidas o tres letras mayúsculas en una fila al final del nombre.

 Por convención, los acrónimos de dos letras utilizan todas las letras en mayúscula y acrónimos de tres o más caracteres use casillas Pascal mayúsculas y minúsculas. Los ejemplos siguientes utilizan esta convención de nomenclatura: 'DB', 'CR', 'Cpa' y 'Ecma'. Los ejemplos siguientes infringen la convención: 'Io', 'XML' y 'DoD' y para los nombres no es de parámetro, 'xp' y 'cpl'.

 'Identificador' es con la grafía especial que provoca una infracción de esta regla. 'Identificador' no es un acrónimo pero es una abreviatura de 'identificación'.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Cambie el nombre por lo que es con grafía correctamente.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir esta advertencia si tiene sus propias convenciones de nomenclatura, o si el identificador representa un nombre propio, por ejemplo, el nombre de una empresa u otra tecnología.

 También puede agregar términos específicos, abreviaturas y acrónimos que a un diccionario personalizado del análisis de código. Condiciones especificadas en el diccionario no hará que las infracciones de esta regla. Para obtener más información, vea [Cómo: Personalizar el diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

## <a name="related-rules"></a>Reglas relacionadas
 [CA1708: Los identificadores deben diferenciarse por algo más que el caso](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)