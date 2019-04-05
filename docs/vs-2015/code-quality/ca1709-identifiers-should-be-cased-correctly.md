---
title: 'CA1709: Los identificadores deberían escribirse correctamente | Documentos de Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4f2fff418e8d791898a4e5db00fe639b5d524d95
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2019
ms.locfileid: "59003085"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709: Los identificadores deben utilizar las mayúsculas y minúsculas correctamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente de Visual Studio, consulte [CA1709: Los identificadores deberían escribirse correctamente](https://docs.microsoft.com/visualstudio/code-quality/ca1709-identifiers-should-be-cased-correctly) en docs.microsoft.com.  
  
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
 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.  
  
 Por convención, los nombres de parámetro utilizan la grafía tipo camel; los nombres de espacio de nombres, tipo y miembro utilizan la convención Pascal mayúsculas y minúsculas. En un nombre con grafía camel, la primera letra es minúscula y la primera letra de las demás palabras del nombre es mayúscula. Ejemplos de nombres con grafía camel son "packetSniffer", "ioFile" y "fatalErrorCode". En un nombre con grafía Pascal, la primera letra es mayúscula y la primera letra de las demás palabras del nombre es mayúscula. Ejemplos de nombres con grafía Pascal son "PacketSniffer", "IOFile" y "FatalErrorCode".  
  
 Esta regla divide el nombre en palabras según las mayúsculas y minúsculas y comprueba las palabras de dos letras con una lista de palabras comunes de dos letras, por ejemplo, "In" o "My". Si no se encuentra una coincidencia, la palabra se supone que un acrónimo. Además, esta regla supone que ha encontrado un acrónimo cuando el nombre contiene cuatro letras mayúsculas seguidas o tres letras mayúsculas en una fila al final del nombre.  
  
 Por convención, los acrónimos de dos letras utilizan todas las letras en mayúscula y acrónimos de tres o más caracteres use casillas Pascal mayúsculas y minúsculas. Los ejemplos siguientes utilizan esta convención de nomenclatura: 'DB', 'CR', 'Cpa' y 'Ecma'. Los ejemplos siguientes infringen la convención: 'Io', 'XML' y 'DoD' y para los nombres nonparameter, 'xp' y 'cpl'.  
  
 'Identificador' es con la grafía especial que provoca una infracción de esta regla. 'Identificador' no es un acrónimo pero es una abreviatura de 'identificación'.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Cambie el nombre por lo que es con grafía correctamente.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Es seguro suprimir esta advertencia si tiene sus propias convenciones de nomenclatura, o si el identificador representa un nombre propio, por ejemplo, el nombre de una empresa u otra tecnología.  
  
 También puede agregar términos específicos, abreviaturas y acrónimos que a un diccionario personalizado del análisis de código. Condiciones especificadas en el diccionario no hará que las infracciones de esta regla. Para obtener más información, vea [Cómo: Personalizar el diccionario de análisis de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1708: Los identificadores deben diferenciarse por algo más que el caso](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
