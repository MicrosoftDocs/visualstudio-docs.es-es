---
title: 'CA1709: los identificadores deben usar mayúsculas o minúsculas correctamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 14c50ed94f05401cc5575af9f8b98472c35b261d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544006"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709: Los identificadores deben utilizar las mayúsculas y minúsculas correctamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente sobre Visual Studio, vea [CA1709: los identificadores deben tener mayúsculas y minúsculas correctamente](/visualstudio/code-quality/ca1709-identifiers-should-be-cased-correctly).

|Elemento|Value|
|-|-|
|TypeName|IdentifiersShouldBeCasedCorrectly|
|Identificador de comprobación|CA1709|
|Category|Microsoft.Naming|
|Cambio problemático|Problemático: cuando se produce en ensamblados, espacios de nombres, tipos, miembros y parámetros.<br /><br /> No problemático: cuando se activa en parámetros de tipo genérico.|

## <a name="cause"></a>Causa
 El nombre de un identificador no tiene mayúsculas y minúsculas correctamente.

 \- o -

 El nombre de un identificador contiene un acrónimo de dos letras y la segunda letra es minúscula.

 \- o -

 El nombre de un identificador contiene un acrónimo de tres o más letras mayúsculas.

## <a name="rule-description"></a>Descripción de la regla
 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.

 Por Convención, los nombres de parámetro usan mayúsculas y minúsculas Camel; los nombres de espacio de nombres, tipo y miembro usan mayúsculas y minúsculas Pascal. En un nombre con grafía Camel, la primera letra es minúscula y la primera letra de las demás palabras del nombre está en mayúsculas. Algunos ejemplos de nombres con mayúsculas y minúsculas Camel son "packetSniffer", "ioFile" y "fatalErrorCode". En un nombre con mayúsculas y minúsculas Pascal, la primera letra está en mayúsculas y la primera letra de las demás palabras del nombre está en mayúsculas. Algunos ejemplos de nombres con grafía Pascal son "PacketSniffer", "IOFile" y "FatalErrorCode".

 Esta regla divide el nombre en palabras según el uso de mayúsculas y minúsculas y comprueba las palabras de dos letras en una lista de palabras comunes de dos letras, como "en" o "mi". Si no se encuentra ninguna coincidencia, se supone que la palabra es un acrónimo. Además, esta regla presupone que ha encontrado un acrónimo cuando el nombre contiene cuatro letras mayúsculas en una fila o tres letras mayúsculas en una fila al final del nombre.

 Por Convención, los acrónimos de dos letras usan todas las letras mayúsculas y los acrónimos de tres o más caracteres usan mayúsculas y minúsculas Pascal. En los ejemplos siguientes se usa esta Convención de nomenclatura: ' DB ', ' CR ', ' CPA ' y ' ECMA '. En los ejemplos siguientes se infringe la Convención: ' io ', ' XML ' y ' DoD ', y para los nombres que no son de parámetros, ' XP ' y ' CPL '.

 ' ID ' tiene mayúsculas y minúsculas especiales para provocar una infracción de esta regla. ' ID ' no es un acrónimo, pero es una abreviatura de ' identificación '.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Cambie el nombre para que sea correcto.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir esta advertencia si tiene sus propias convenciones de nomenclatura, o si el identificador representa un nombre adecuado, por ejemplo, el nombre de una empresa o una tecnología.

 También puede Agregar términos, abreviaturas y acrónimos específicos a un diccionario personalizado de análisis de código. Los términos especificados en el diccionario personalizado no producirán infracciones de esta regla. Para obtener más información, vea [Cómo: personalizar el Diccionario de análisis de código.](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

## <a name="related-rules"></a>Reglas relacionadas
 [CA1708: Los identificadores se deben diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
