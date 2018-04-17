---
title: 'CA1709: Los identificadores deben ser minúsculas correctamente | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5c010019c2ae5d1044d11c02c22428dda4197fcd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente
|||  
|-|-|  
|TypeName|IdentifiersShouldBeCasedCorrectly|  
|Identificador de comprobación|CA1709|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático: cuando se genera en los ensamblados, espacios de nombres, tipos, miembros y parámetros.<br /><br /> Poco problemático: cuando se desencadena en parámetros de tipo genérico.|  
  
## <a name="cause"></a>Motivo  
 El nombre de un identificador no es las mayúsculas y minúsculas correctamente.  
  
 \- o -  
  
 El nombre de un identificador contiene un acrónimo de dos letras y la segunda letra en minúscula.  
  
 \- o -  
  
 El nombre de un identificador contiene un acrónimo de tres o más letras mayúsculas.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.  
  
 Por convención, los nombres de parámetro utilizan mayúsculas y minúsculas camel; los nombres de espacio de nombres, tipo y miembro utilizan la convención Pascal mayúsculas y minúsculas. En un nombre de la grafía camel, la primera letra es minúscula y la primera letra de las demás palabras en el nombre está en mayúsculas. Ejemplos de nombres de grafía de camel son "packetSniffer", "ioFile" y "fatalErrorCode". En un nombre de la grafía Pascal, la primera letra es mayúscula y la primera letra de las demás palabras en el nombre está en mayúsculas. Ejemplos de nombres de la grafía Pascal son "PacketSniffer", "IOFile" y "FatalErrorCode".  
  
 Esta regla divide el nombre en palabras según las mayúsculas y minúsculas y comprueba las palabras de dos letras con una lista de palabras comunes de dos letras, por ejemplo, "In" o "Mi". Si no se encuentra una coincidencia, se supone que la palabra es un acrónimo. Además, esta regla supone que ha encontrado un acrónimo cuando el nombre contiene cuatro letras mayúsculas seguidas o tres letras en mayúsculas en una fila al final del nombre.  
  
 Por convención, los acrónimos de dos letras utilizan todas las letras mayúsculas y acrónimos de tres o más caracteres utilizan la convención Pascal mayúsculas y minúsculas. Los ejemplos siguientes usan esta convención de nomenclatura: 'DB', 'CR', 'Cpa' y 'Ecma'. Los ejemplos siguientes infringen la convención: 'Io', 'XML' y 'DoD' y para los nombres de nonparameter, 'xp' y 'cpl'.  
  
 'Identificador' es usar la grafía especial que provoca una infracción de esta regla. 'Identificador' no es un acrónimo pero es una abreviatura de 'identificación'.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Cambie el nombre para que lo es mayúsculas y minúsculas correctamente.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Es seguro suprimir esta advertencia si tiene sus propias convenciones de nomenclatura, o si el identificador representa un nombre propio, por ejemplo, el nombre de una empresa o una tecnología.  
  
 También puede agregar términos específicos, abreviaturas y acrónimos que a un diccionario personalizado de análisis de código. Condiciones especificadas en el diccionario personalizado no hará que las infracciones de esta regla. Para obtener más información, vea [Cómo: personalizar el diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1708: Los identificadores se deberían diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)